# SPEC.md — AI Skill: Test Case Generator

**Version:** 1.0.0
**Author:** QC Team — Cook A Skill
**Last Updated:** 2026-02-24

---

## 1. Skill Overview

**Skill Name:** Test Case Generator
**Goal:** Automatically generate a complete, standardized list of test cases from a product feature spec file (`.md`), covering Happy Path, Negative Cases, and Edge Cases, along with a ready-to-use test report template.

**Problem it solves:**
- QC manually reads specs and writes test cases → slow, inconsistent, prone to missing edge cases
- Different QC members produce different formats → hard to review and merge
- This skill reads the spec, analyzes logic, and generates structured test cases instantly

---

## 2. Input

### 2.1 Primary Input

| Field | Type | Required | Description |
|---|---|---|---|
| `spec_content` | `string` (Markdown) | Yes | Full content of the feature spec file |
| `feature_name` | `string` | No | Name of the feature being tested (auto-extracted from spec if not provided) |
| `output_format` | `enum` | No | `markdown` (default) \| `csv` \| `table` |
| `coverage_level` | `enum` | No | `basic` \| `standard` (default) \| `full` |

### 2.2 Accepted Spec Formats

The `spec_content` can come from any of these document types:

- **PRD** (Product Requirements Document)
- **BRS** (Business Requirements Specification)
- **User Story** + Acceptance Criteria
- **Feature Description** (free-form markdown)

### 2.3 Minimum Spec Quality Requirements

For the skill to produce meaningful output, the spec MUST contain at least:

- [ ] A description of what the feature does
- [ ] At least one user action or flow (e.g., "user clicks X → system does Y")
- [ ] At least one business rule or validation condition

If the spec does not meet this minimum, the skill returns a **Spec Quality Warning** (see Section 6).

### 2.4 Input Example

```markdown
## Feature: User Login

### Description
Users can log in to the system using email + password.

### Business Rules
- Email must be valid format
- Password must be at least 8 characters
- After 5 failed attempts, account is locked for 15 minutes
- On success, redirect to Dashboard

### User Flow
1. User opens /login
2. User enters email + password
3. User clicks "Login"
4. System validates credentials
5. On success → redirect to /dashboard
6. On failure → show error message
```

---

## 3. Output

### 3.1 Test Case List

Each test case follows this schema:

| Field | Type | Description |
|---|---|---|
| `id` | `string` | Sequential ID — e.g., `TC-001`, `TC-002` |
| `title` | `string` | Short, action-oriented title — e.g., "Login with valid credentials" |
| `type` | `enum` | `Happy Path` \| `Negative` \| `Edge Case` |
| `priority` | `enum` | `P1 - Critical` \| `P2 - High` \| `P3 - Medium` \| `P4 - Low` |
| `precondition` | `string` | System state required before executing the test |
| `test_data` | `string` | Specific data values to use (emails, passwords, amounts, etc.) |
| `steps` | `list[string]` | Numbered steps to execute the test |
| `expected_result` | `string` | What the system must do upon completion |
| `actual_result` | `string` | Blank — to be filled by QC during execution |
| `status` | `enum` | `Pass` \| `Fail` \| `Blocked` \| `N/A` — blank by default |
| `notes` | `string` | Optional — edge case context or known limitations |

### 3.2 Coverage Summary

After the test case list, the skill generates a summary table:

| Type | Count |
|---|---|
| Happy Path | N |
| Negative | N |
| Edge Case | N |
| **Total** | **N** |

### 3.3 Test Report Template

Appended at the end of the output, ready for QC to fill in:

```
## Test Execution Report

- Feature: [feature_name]
- Tester: ___________
- Date: ___________
- Environment: ___________
- Build/Version: ___________

## Summary

| Total TCs | Pass | Fail | Blocked | Not Run |
|---|---|---|---|---|
| | | | | |

## Defects Found

| Bug ID | TC ID | Description | Severity | Status |
|---|---|---|---|---|
| | | | | |

## Sign-off

- [ ] QC Lead Review: ___________
- [ ] Ready for Release
```

### 3.4 Output Example (Markdown)

```markdown
## Test Cases — User Login

| ID | Title | Type | Priority | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|
| TC-001 | Login with valid email and password | Happy Path | P1 | User is registered. Login page is open. | email: user@test.com / password: Pass@1234 | 1. Go to /login 2. Enter email 3. Enter password 4. Click Login | Redirected to /dashboard. Welcome message shown. |
| TC-002 | Login with incorrect password | Negative | P1 | User is registered. Login page is open. | email: user@test.com / password: wrongpass | 1. Go to /login 2. Enter valid email 3. Enter wrong password 4. Click Login | Error: "Invalid credentials". Stay on /login. |
| TC-003 | Login after 5 failed attempts | Edge Case | P1 | User has failed 4 times already. | email: user@test.com / password: wrongpass | 1. Attempt 5th failed login | Account locked. Error: "Account locked for 15 minutes." |
| TC-004 | Login with invalid email format | Negative | P2 | Login page is open. | email: notanemail / password: Pass@1234 | 1. Enter invalid email 2. Click Login | Validation error: "Invalid email format". |
| TC-005 | Login with blank email field | Negative | P2 | Login page is open. | email: (empty) / password: Pass@1234 | 1. Leave email blank 2. Click Login | Validation error: "Email is required". |
| TC-006 | Login with password under 8 characters | Edge Case | P2 | Login page is open. | email: user@test.com / password: 123 | 1. Enter short password 2. Click Login | Validation error: "Password must be at least 8 characters". |
```

---

## 4. Workflow

The skill executes in the following sequential steps:

```
[INPUT]
  Spec content (.md)
       │
       ▼
[STEP 1] Spec Parsing
  - Extract: feature name, description, user flows, business rules,
    validations, boundary conditions, roles, integrations
       │
       ▼
[STEP 2] Quality Check
  - Does spec meet minimum requirements?
  - If NO → return Spec Quality Warning + stop
  - If YES → continue
       │
       ▼
[STEP 3] Logic Analysis
  - Identify all branches: success paths, failure paths
  - Identify all validation rules → each rule = at least 1 test case
  - Identify numeric/string boundaries → boundary value test cases
  - Identify role-based access (if any) → permission test cases
       │
       ▼
[STEP 4] Test Case Generation
  - Generate Happy Path cases (all required fields valid → success)
  - Generate Negative cases (invalid input, missing fields, wrong state)
  - Generate Edge Cases (boundaries, locked states, concurrency hints)
  - Assign ID, priority, test data to each case
       │
       ▼
[STEP 5] Coverage Check
  - Ensure every business rule is covered by at least 1 test case
  - Ensure every user flow step is exercised
  - Flag any spec sections with no test case generated (ambiguity warning)
       │
       ▼
[STEP 6] Output Assembly
  - Format test case table (Markdown / CSV / table)
  - Append Coverage Summary
  - Append Test Report Template
       │
       ▼
[OUTPUT]
  Complete test case list + report template
```

---

## 5. Priority Assignment Rules

| Scenario | Priority |
|---|---|
| Core happy path — feature cannot work without this | P1 - Critical |
| Security rules (auth, permission, account lock) | P1 - Critical |
| All validation rules that block the main flow | P2 - High |
| Boundary values, edge inputs | P2 - High |
| UI/UX messaging (error messages, empty states) | P3 - Medium |
| Optional fields, non-blocking validations | P3 - Medium |
| Cosmetic / low-impact flows | P4 - Low |

---

## 6. Error Handling & Spec Quality Warning

If the spec does not meet minimum quality requirements, the skill returns:

```
⚠️ SPEC QUALITY WARNING

The provided spec is missing critical information needed to generate reliable test cases.

Missing elements detected:
- [ ] No user flow or action sequence found
- [ ] No business rules or validation conditions found
- [ ] Description is too vague to extract testable behavior

Recommendation:
Please add the following to your spec before re-running:
1. At least one user flow (step-by-step actions)
2. At least one validation or business rule
3. Expected system behavior on success and failure

Test case generation has been paused. No output produced.
```

---

## 7. Coverage Levels

| Level | What's included |
|---|---|
| `basic` | Happy path only — minimal test cases for quick smoke checks |
| `standard` | Happy path + Negative cases for all validations (default) |
| `full` | Happy + Negative + Edge Cases + boundary values + role/permission tests |

---

## 8. Constraints & Assumptions

- **Constraint:** The skill only generates **functional / manual test cases**. It does not generate automation scripts, performance tests, or security penetration tests.
- **Constraint:** Test cases are generated based on what is **explicitly stated** in the spec. Implicit business logic not written in the spec will not be inferred.
- **Assumption:** The spec is written in English or Vietnamese. Mixed-language specs are supported.
- **Assumption:** QC will review and edit the generated test cases before execution. The skill is an accelerator, not a replacement for QC judgment.
- **Assumption:** Each run generates test cases for **one feature at a time**. Multi-feature specs should be split before input.

---

## 9. Out of Scope

The following are explicitly NOT produced by this skill:

- Selenium / Playwright / Cypress automation scripts
- API test scripts (Postman, REST Assured)
- Performance / load test plans
- Security / penetration test cases
- Bug reports or defect logs
- Integration with Jira, TestRail, or any external tool (handled separately)

---

## 10. Success Criteria

The skill output is considered successful when:

- [ ] Every business rule in the spec maps to at least 1 test case
- [ ] Every user flow step is exercised in at least 1 test case
- [ ] All 3 test types are represented (Happy, Negative, Edge) — for `standard` and `full` levels
- [ ] All test cases have: ID, Title, Type, Priority, Precondition, Steps, Expected Result
- [ ] Test report template is appended and ready to fill in
- [ ] QC requires only minor edits before using the output
