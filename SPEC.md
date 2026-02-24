# SPEC: Skill — Test Case Generator + Report Template

> **Version**: 1.0.0
> **Last updated**: 2026-02-24
> **Author**: QA Team
> **Status**: QC-Ready

---

## Table of Contents

1. [Overview](#1-overview)
2. [Scope](#2-scope)
3. [Rules](#3-rules)
4. [User Flow](#4-user-flow)
5. [Business Logic](#5-business-logic)
6. [Edge Cases](#6-edge-cases)
7. [Test Data](#7-test-data)
8. [Output Format](#8-output-format)

---

## 1. Overview

### 1.1 Skill Name
**Test Case Generator + Report Template**

### 1.2 Actor
QC / QA Manager

### 1.3 Problem Statement
After generating test cases, QC teams still need to manually write test reports — a redundant, time-consuming step that introduces inconsistency across projects.

### 1.4 What This Skill Does
A single-input, two-output pipeline:

```
[Input: SPEC.md file]
        │
        ▼
┌─────────────────────────────────┐
│   Test Case Generator + Report  │
│           Template Skill        │
└─────────────────────────────────┘
        │
        ├──► Output A: Structured Test Cases (with IDs, steps, expected results)
        │
        └──► Output B: Report Template (QC fills Pass/Fail/Blocked)
                              │
                              ▼
                  [QC submits filled report]
                              │
                              ▼
                  Output C: Aggregated Test Summary Report
```

### 1.5 Business Value
- Full pipeline: Spec → Test Cases → Report in one skill invocation
- Eliminates manual test case writing and report formatting
- Standardizes QC output across all projects
- Reduces manual effort by ~70% on test documentation

### 1.6 MVP Scope
Input **one SPEC.md file** → Output **test cases + report template** ready to use.

---

## 2. Scope

### 2.1 In Scope

| # | Feature | Description |
|---|---------|-------------|
| 1 | Spec Parsing | Read and understand a `.md` spec file provided by the user |
| 2 | Test Case Generation | Auto-generate test cases covering Happy Path, Negative, Edge, and Boundary scenarios |
| 3 | Test Case ID Assignment | Assign unique, traceable test case IDs (format: `TC-XXX-NNN`) |
| 4 | Report Template Generation | Produce a fillable report template with Pass/Fail/Blocked/Skip columns |
| 5 | Result Aggregation | Aggregate QC-filled results into a final test summary report |
| 6 | Coverage Tagging | Tag each test case with scenario type (Happy Path / Negative / Edge / Boundary) |
| 7 | Priority Labeling | Mark each test case as Critical / High / Medium / Low |

### 2.2 Out of Scope (MVP)

| # | Feature | Reason |
|---|---------|--------|
| 1 | Automated test execution | Manual QC review is required by design |
| 2 | Multi-file spec input | MVP supports single spec file only |
| 3 | Integration with JIRA/TestRail | Post-MVP roadmap item |
| 4 | AI-powered defect prediction | Out of MVP |
| 5 | Screenshot/video evidence upload | Post-MVP |

---

## 3. Rules

### 3.1 Input Rules

| Rule ID | Rule | Violation Behavior |
|---------|------|--------------------|
| R-IN-01 | Input MUST be a `.md` file | Skill returns error: `"Input must be a Markdown (.md) file"` |
| R-IN-02 | Spec file MUST contain at least one functional requirement | Skill returns warning: `"No requirements found. Please check spec content."` |
| R-IN-03 | Spec file size MUST NOT exceed 500KB | Skill returns error: `"File too large. Max size is 500KB."` |
| R-IN-04 | Spec file content MUST be UTF-8 encoded | Skill returns error: `"Unsupported encoding. Use UTF-8."` |
| R-IN-05 | Spec file MUST NOT be empty | Skill returns error: `"Empty file detected. Please provide spec content."` |

### 3.2 Test Case Generation Rules

| Rule ID | Rule |
|---------|------|
| R-TC-01 | Every functional requirement MUST produce at least 1 Happy Path test case |
| R-TC-02 | Every input field MUST produce at least 1 Negative test case |
| R-TC-03 | Every boundary value MUST have a Boundary test case (min, max, min-1, max+1) |
| R-TC-04 | Every business rule in the spec MUST map to at least 1 test case |
| R-TC-05 | Test case IDs MUST follow format: `TC-[FEATURE_CODE]-[3-digit sequence]` (e.g., `TC-AUTH-001`) |
| R-TC-06 | Each test case MUST include: ID, Title, Preconditions, Steps, Expected Result, Priority, Tags |
| R-TC-07 | Priority assignment MUST follow: Critical (auth/payment/data loss), High (core flows), Medium (secondary), Low (UI/cosmetic) |
| R-TC-08 | Duplicate test cases (same steps + expected result) MUST be deduplicated |

### 3.3 Report Template Rules

| Rule ID | Rule |
|---------|------|
| R-RP-01 | Report template MUST include all generated test case IDs pre-populated |
| R-RP-02 | Result column MUST only accept: `Pass`, `Fail`, `Blocked`, `Skip`, `N/A` |
| R-RP-03 | Report MUST include columns: TC ID, Title, Priority, Result, Actual Result (if Fail), Tester, Date |
| R-RP-04 | Summary section MUST auto-calculate: Total, Pass%, Fail%, Blocked%, Skip% |
| R-RP-05 | Report template MUST be in Markdown table format for easy editing |

### 3.4 Aggregation Rules

| Rule ID | Rule |
|---------|------|
| R-AG-01 | A test run is `PASSED` only if Pass% = 100% of non-skipped, non-N/A test cases |
| R-AG-02 | Any `Critical` test case with result `Fail` MUST trigger overall status = `BLOCKED — DO NOT RELEASE` |
| R-AG-03 | Any `High` test case with result `Fail` → overall status = `FAIL` |
| R-AG-04 | All `Fail` results MUST list the TC ID and Actual Result in the summary |
| R-AG-05 | `Skip` and `N/A` results are excluded from Pass% calculation |

---

## 4. User Flow

### 4.1 Primary Flow (Happy Path)

```
Step 1: QC opens Skill prompt
Step 2: QC uploads or pastes SPEC.md content
Step 3: Skill validates input (format, size, encoding, content)
Step 4: Skill parses spec → extracts features, rules, inputs, boundaries
Step 5: Skill generates test cases with IDs, steps, expected results
Step 6: Skill generates report template pre-filled with TC IDs
Step 7: QC downloads/copies test cases and report template
Step 8: QC executes tests manually and fills in Pass/Fail/Blocked/Skip
Step 9: QC submits filled report back to Skill
Step 10: Skill aggregates results → generates Test Summary Report
Step 11: QC downloads Test Summary Report
```

### 4.2 Alternate Flow — Spec Has No Requirements

```
Step 1-2: Same as primary flow
Step 3: Skill validates → finds no parseable requirements
Step 4: Skill returns: "Warning: No testable requirements detected.
         Please ensure your spec contains functional descriptions."
Step 5: Skill suggests spec template for user to fill
```

### 4.3 Alternate Flow — Invalid File Type

```
Step 1: QC uploads a .pdf or .docx file
Step 2: Skill detects non-.md format
Step 3: Skill returns: "Error: Only .md files are supported.
         Please convert your spec to Markdown format."
Step 4: Flow ends — no test cases generated
```

### 4.4 Alternate Flow — Re-run with Updated Spec

```
Step 1: QC re-uploads updated SPEC.md
Step 2: Skill detects new/changed requirements vs previous run (if session context available)
Step 3: Skill generates delta test cases for new/changed requirements
Step 4: Existing test case IDs are preserved; new TCs get next sequence number
Step 5: Merged test suite + new report template generated
```

---

## 5. Business Logic

### 5.1 Feature Code Extraction

The skill MUST derive a `FEATURE_CODE` from the spec:
- Use the first H1/H2 heading as the feature name
- Convert to uppercase alphanumeric, max 6 characters
- Example: `# User Authentication` → `AUTH`

### 5.2 Test Case Priority Matrix

| Scenario Type | Feature Area | Assigned Priority |
|---------------|-------------|-------------------|
| Login / Auth | Any | Critical |
| Payment / Checkout | Any | Critical |
| Data deletion / irreversible action | Any | Critical |
| Core CRUD operations | Any | High |
| Search / Filter | Any | High |
| Form validation | Any | Medium |
| UI display / Responsive | Any | Low |
| Error messages wording | Any | Low |

### 5.3 Test Case Type Coverage Requirements

For each requirement, the skill MUST generate:

| Type | Trigger Condition | Minimum Count |
|------|------------------|---------------|
| Happy Path | Any functional requirement | 1 per requirement |
| Negative | Any input field or action | 1 per input field |
| Boundary | Numeric or length-limited fields | 4 per field (min, max, min-1, max+1) |
| Edge Case | Boolean states, empty states, concurrent actions | 1+ per identified edge |

### 5.4 Aggregation Formula

```
Total TCs        = count of all test cases
Executed TCs     = Total - Skip - N/A
Pass%            = (Pass / Executed TCs) × 100
Fail%            = (Fail / Executed TCs) × 100
Blocked%         = (Blocked / Executed TCs) × 100

Overall Status:
  IF any Critical TC = Fail  → "BLOCKED — DO NOT RELEASE"
  ELSE IF any High TC = Fail → "FAIL"
  ELSE IF Pass% = 100%       → "PASS"
  ELSE                        → "PARTIAL PASS — REVIEW REQUIRED"
```

### 5.5 Test Case ID Sequencing

```
Format : TC-[FEATURE_CODE]-[NNN]
Example: TC-AUTH-001, TC-AUTH-002, ... TC-AUTH-099, TC-AUTH-100

Rules:
- Sequence resets per feature code
- IDs are never reused within a spec run
- Deleted/skipped TCs leave a gap (no renumbering)
```

---

## 6. Edge Cases

| EC ID | Scenario | Expected Behavior |
|-------|----------|-------------------|
| EC-01 | Spec file has only headings, no body content | Warning returned; no test cases generated; template spec provided |
| EC-02 | Spec has 100+ requirements | All requirements processed; TCs generated up to TC-XXX-999; overflow flagged as warning |
| EC-03 | Spec contains duplicate requirements (identical text) | Deduplicated before processing; only 1 set of TCs generated |
| EC-04 | Spec is written in a language other than English | Test cases generated in same language as spec |
| EC-05 | Spec has no input fields (read-only feature) | No Negative/Boundary TCs generated; only Happy Path and display verification TCs |
| EC-06 | Spec contains conflicting rules (e.g., "must be > 0" and "can be 0") | Conflict flagged in output: `"Conflicting rules detected at [line X] — manual review required"` |
| EC-07 | User submits report with all results blank | Aggregation blocked; error: `"Report has no filled results. Please complete at least 1 test case."` |
| EC-08 | User submits report with result values other than the allowed set | Row rejected with inline error: `"Invalid result '[value]' at TC-XXX-NNN. Allowed: Pass, Fail, Blocked, Skip, N/A"` |
| EC-09 | Spec has nested features (H1 > H2 > H3) | Each heading level parsed as a sub-feature; TC IDs namespaced accordingly (e.g., TC-AUTH-LOGIN-001) |
| EC-10 | Spec file contains code blocks or tables | Code/table content extracted as context; not treated as standalone requirements |
| EC-11 | QC re-submits a previously submitted report | Second submission overwrites first; updated summary generated; change log appended |
| EC-12 | All test cases are marked `Skip` or `N/A` | Aggregation result = `"NO EXECUTION — All cases skipped or not applicable"` |
| EC-13 | Spec contains external links or references | Links preserved as-is in TC preconditions/context; not followed or validated |
| EC-14 | Boundary field has no defined max (e.g., "enter any text") | Skill applies default text boundary: min=1 char, max=255 chars, and flags assumption |

---

## 7. Test Data

### 7.1 Valid Input Specs

| TD ID | Spec Content Summary | Expected TC Count | Notes |
|-------|---------------------|-------------------|-------|
| TD-V-01 | Single feature, 3 requirements, 2 input fields | 12–16 TCs | Happy path + negative + boundary |
| TD-V-02 | Auth feature: Login with email/password | 14–18 TCs | Includes Critical priority TCs |
| TD-V-03 | Search feature: keyword filter, 0–200 char limit | 10–14 TCs | Boundary on char limit |
| TD-V-04 | Read-only dashboard spec (no input fields) | 4–6 TCs | Happy path + display edge cases |
| TD-V-05 | 50-requirement spec | 150–250 TCs | Stress test; all requirements covered |

### 7.2 Invalid Input Specs

| TD ID | Input | Expected Error |
|-------|-------|---------------|
| TD-I-01 | Empty file (0 bytes) | `"Empty file detected."` |
| TD-I-02 | `.pdf` extension | `"Input must be a Markdown (.md) file"` |
| TD-I-03 | 600KB `.md` file | `"File too large. Max size is 500KB."` |
| TD-I-04 | File with only `# Title` heading, no body | `"No testable requirements detected."` |
| TD-I-05 | Non-UTF-8 encoded file (e.g., ISO-8859-1) | `"Unsupported encoding. Use UTF-8."` |

### 7.3 Sample Spec for Testing (Canonical Test Input)

```markdown
# User Authentication

## Login
- User enters email and password
- Email must be valid format (contain @)
- Password must be 8–64 characters
- After 5 failed attempts, account is locked for 15 minutes
- Successful login redirects to Dashboard

## Logout
- User can logout from any page
- Session is invalidated on logout
- User is redirected to Login page
```

**Expected output for this sample:**

| TC ID | Title | Type | Priority |
|-------|-------|------|----------|
| TC-AUTH-001 | Login with valid email and password | Happy Path | Critical |
| TC-AUTH-002 | Login with invalid email format | Negative | Critical |
| TC-AUTH-003 | Login with password below 8 chars (7 chars) | Boundary | Critical |
| TC-AUTH-004 | Login with password at min (8 chars) | Boundary | Critical |
| TC-AUTH-005 | Login with password at max (64 chars) | Boundary | Critical |
| TC-AUTH-006 | Login with password above max (65 chars) | Boundary | Critical |
| TC-AUTH-007 | Login with empty email | Negative | Critical |
| TC-AUTH-008 | Login with empty password | Negative | Critical |
| TC-AUTH-009 | Account locked after 5 failed attempts | Business Rule | Critical |
| TC-AUTH-010 | Locked account cannot login within 15 mins | Edge Case | Critical |
| TC-AUTH-011 | Account unlocks after 15 minutes | Edge Case | Critical |
| TC-AUTH-012 | Redirect to Dashboard on successful login | Happy Path | High |
| TC-AUTH-013 | Logout from Dashboard | Happy Path | High |
| TC-AUTH-014 | Logout from any non-dashboard page | Happy Path | High |
| TC-AUTH-015 | Session invalidated after logout | Business Rule | Critical |
| TC-AUTH-016 | Redirect to Login page after logout | Happy Path | High |

### 7.4 Sample Report Template Output

```markdown
## Test Report — User Authentication
**Run Date**: ___________   **Tester**: ___________   **Build/Version**: ___________

| TC ID       | Title                                          | Priority | Result | Actual Result (if Fail) | Notes |
|-------------|------------------------------------------------|----------|--------|--------------------------|-------|
| TC-AUTH-001 | Login with valid email and password            | Critical |        |                          |       |
| TC-AUTH-002 | Login with invalid email format                | Critical |        |                          |       |
| TC-AUTH-003 | Login with password below 8 chars              | Critical |        |                          |       |
...

### Summary
| Metric      | Count | % |
|-------------|-------|---|
| Total TCs   |  16   |   |
| Executed    |       |   |
| Pass        |       |   |
| Fail        |       |   |
| Blocked     |       |   |
| Skip / N/A  |       |   |

**Overall Status**: ___________
```

### 7.5 Sample Aggregated Summary Report Output

```markdown
## Test Summary Report — User Authentication
**Run Date**: 2026-02-24   **Tester**: Jane QA   **Build**: v2.1.0

### Results
| Metric      | Count | %      |
|-------------|-------|--------|
| Total TCs   |  16   | 100%   |
| Executed    |  14   |        |
| Pass        |  12   | 85.7%  |
| Fail        |   2   | 14.3%  |
| Blocked     |   0   | 0%     |
| Skip / N/A  |   2   |        |

**Overall Status**: ⛔ FAIL

### Failed Test Cases
| TC ID       | Title                               | Actual Result                              |
|-------------|-------------------------------------|--------------------------------------------|
| TC-AUTH-009 | Account locked after 5 failed attempts | Lock not triggered — user could still log in |
| TC-AUTH-015 | Session invalidated after logout    | Old session token still valid after logout |

### Recommendation
- 2 failed test cases must be resolved before release
- TC-AUTH-009 and TC-AUTH-015 are Critical priority — release is blocked
```

---

## 8. Output Format

### 8.1 Output A — Generated Test Cases

Each test case MUST be rendered in the following structure:

```markdown
### TC-[FEATURE_CODE]-[NNN]: [Title]
- **Type**: Happy Path | Negative | Boundary | Edge Case | Business Rule
- **Priority**: Critical | High | Medium | Low
- **Tags**: [feature area, e.g., auth, login, form-validation]

**Preconditions**:
- [List all conditions that must be true before executing this test]

**Test Steps**:
1. [Step 1]
2. [Step 2]
3. [Step N]

**Expected Result**:
- [What should happen after the final step]

**Notes** *(optional)*:
- [Any known limitations, related TCs, or test data references]
```

### 8.2 Output B — Report Template

- Format: Markdown table (`.md`)
- Pre-populated with all TC IDs and Titles from Output A
- Result column: empty cells for QC to fill
- Allowed result values: `Pass`, `Fail`, `Blocked`, `Skip`, `N/A`
- Summary section: auto-formula notation for QC to calculate manually OR auto-filled by Skill on re-submission

### 8.3 Output C — Aggregated Test Summary

- Format: Markdown report
- Includes: run metadata (date, tester, build), results table, pass/fail breakdown, failed TC list with actual results, overall status verdict
- Overall status values:
  - `PASS` — all executed TCs pass
  - `FAIL` — one or more High priority TCs fail
  - `BLOCKED — DO NOT RELEASE` — one or more Critical TCs fail
  - `PARTIAL PASS — REVIEW REQUIRED` — no Critical/High failures but Pass% < 100%
  - `NO EXECUTION` — all TCs are Skip or N/A

### 8.4 File Naming Convention

| Output | Suggested Filename |
|--------|-------------------|
| Test Cases | `TC-[FEATURE_CODE]-[YYYY-MM-DD].md` |
| Report Template | `REPORT-TEMPLATE-[FEATURE_CODE]-[YYYY-MM-DD].md` |
| Aggregated Summary | `SUMMARY-[FEATURE_CODE]-[YYYY-MM-DD]-[BUILD].md` |

---

## Appendix A: QC Checklist

Use this checklist to validate the Skill's outputs before sign-off.

### A.1 Test Case Generation Checklist

- [ ] Every requirement in the spec has at least 1 Happy Path TC
- [ ] Every input field has at least 1 Negative TC
- [ ] All boundary fields have 4 Boundary TCs (min, max, min-1, max+1)
- [ ] Business rules each have at least 1 dedicated TC
- [ ] No duplicate TCs (same steps + expected result)
- [ ] All TC IDs follow format `TC-[CODE]-[NNN]`
- [ ] All TCs have: ID, Title, Preconditions, Steps, Expected Result, Priority, Tags
- [ ] Priority assignments match the priority matrix (Section 5.2)
- [ ] Coverage includes: Happy Path, Negative, Boundary, Edge Case types

### A.2 Report Template Checklist

- [ ] All generated TC IDs appear in the report template
- [ ] Result column is blank (not pre-filled)
- [ ] Allowed result values are documented in the template
- [ ] Tester name, date, and build fields are present
- [ ] Summary section is present with correct metric labels

### A.3 Aggregated Report Checklist

- [ ] Pass%, Fail%, Blocked% calculated correctly (excluding Skip/N/A)
- [ ] All Fail results listed with Actual Result notes
- [ ] Overall status verdict matches the aggregation logic (Section 5.4)
- [ ] `BLOCKED — DO NOT RELEASE` triggered for any Critical TC failure
- [ ] Report includes run metadata (date, tester, build)

---

## Appendix B: Glossary

| Term | Definition |
|------|-----------|
| Spec | Markdown file describing the feature's requirements, rules, and behavior |
| TC | Test Case |
| Happy Path | Test where all inputs are valid and the expected success flow is verified |
| Negative Test | Test using invalid inputs to verify error handling |
| Boundary Test | Test at the exact min/max values and just outside them |
| Edge Case | Test for unusual but valid states (empty, concurrent, overflow) |
| Business Rule | A TC that maps directly to a stated rule in the spec |
| Blocked | A TC that could not be executed due to an upstream defect or dependency |
| Pass% | Percentage of executed (non-Skip/N/A) TCs that passed |
| Overall Status | Final release-readiness verdict based on aggregation rules |
