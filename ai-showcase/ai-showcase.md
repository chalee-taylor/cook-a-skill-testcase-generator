# AI Showcase — Test Case Generator Skill

**Project:** Cook A Skill – QC Team
**Skill:** Test Case Generator
**Author:** QC Team
**Date:** 2026-02-25

---

## Overview

This file showcases the most compelling AI prompt/conversation examples produced during the development and testing of the **Test Case Generator** Skill. It demonstrates how Claude was used to:

1. Iteratively design and refine `SKILL.md`
2. Generate high-quality test cases from real spec files
3. Handle edge cases, validation, and PII masking

---

## Conversation 1 — Building the Skill Prompt (Development Phase)

**Context:** Early prompt used to bootstrap the SKILL.md logic. This conversation shows how the system prompt was crafted to produce stable, non-vague outputs.

---

### Prompt sent to Claude

```
You are helping me design an AI Skill for QC teams.
The skill must read a product feature spec and generate test cases.
The main problem is that QC-generated test cases are often vague —
steps like "enter valid data and submit" or expected results like "system should work".

I need the skill to enforce:
1. Concrete test data (real values, not placeholders)
2. Executable steps (what the tester must DO exactly)
3. Verifiable expected results (what the tester must SEE)
4. All 4 types: Happy Path, Negative, Edge Case, Security
5. A traceability matrix mapping business rules to test cases

Can you draft a system prompt for this skill?
```

---

### Claude's Response (excerpt)

```
Here's a draft system prompt for your Test Case Generator skill:

---
You are a Senior QC Engineer specializing in test case design.
When provided with a feature spec, read deeply, analyze the logic, and
produce a set of COMPLETE, STRUCTURED, NON-VAGUE, NON-DUPLICATE test cases.

RULES:
1. Every TC must include: ID, Title, Type, Priority, Rule Ref,
   Precondition, Test Data, Steps (numbered), Expected Result.
2. Steps must be specific and executable —
   NEVER write "verify the system works".
   Write exactly what the tester must DO.
3. Expected Result must be verifiable —
   NEVER write "should work correctly".
   Write exactly what the tester must SEE.
4. Test Data must contain concrete values —
   NEVER write "enter valid data".
   Write exact values (e.g., email: user@test.com, password: Pass@1234).
5. Cover ALL 4 types: Happy Path, Negative, Edge Case, Security.
6. Each business rule must be referenced in at least 1 TC (rule_ref field).
7. Do NOT generate duplicate TCs. Merge overlapping scenarios.
8. Assign priority: P1 for core paths and all security, P2 for validation
   and boundaries, P3 for UI/messaging, P4 for cosmetic.
---

This prompt, combined with few-shot examples and an anti-pattern guard,
gives you stable outputs across different spec inputs.

Would you like me to add the edge case checklist and the traceability matrix section?
```

---

**Why this conversation matters:**
The above exchange directly shaped the 7-step workflow in `SKILL.md`.
The final skill version includes the anti-pattern guard, few-shot examples,
and the complete edge case checklist — all born from iterating on this prompt.

---

## Conversation 2 — Skill in Action: User Login Spec (Standard Output)

**Context:** The skill was given the User Login spec from `SPEC.md` with `coverage_level: standard` to generate a real test case suite.

---

### Input Prompt

````
Generate test cases for the following spec.

Parameters:
- output_format: markdown
- coverage_level: standard
- enable_security: true

---

## Feature: User Login

### Description
Users can log in to the system using email + password.

### Business Rules
- BR-001: Email must be valid format
- BR-002: Password must be at least 8 characters
- BR-003: After 5 failed attempts, account is locked for 15 minutes
- BR-004: On success, redirect to Dashboard

### User Flow
1. User opens /login
2. User enters email + password
3. User clicks "Login"
4. System validates credentials
5. On success → redirect to /dashboard
6. On failure → show error message
````

---

### Claude's Output

```
## Test Cases — User Login

### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-001 | Login with valid email and password | Happy Path | P1 - Critical | BR-001, BR-002, BR-004 | User account user@test.com exists and is active. Login page /login is open. | email: user@test.com / password: Pass@1234 | 1. Navigate to /login 2. Enter email: user@test.com 3. Enter password: Pass@1234 4. Click "Login" button | User is redirected to /dashboard. Welcome message "Hello, User" is displayed in the header. |

### 🔴 Negative

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-002 | Login rejected when password is incorrect | Negative | P2 - High | BR-001, BR-002 | User account user@test.com exists and is active. Login page /login is open. | email: user@test.com / password: WrongPass999 | 1. Navigate to /login 2. Enter email: user@test.com 3. Enter password: WrongPass999 4. Click "Login" button | Login fails. Error message "Invalid email or password" is displayed below the form. User remains on /login. No session cookie is set. |
| TC-003 | Login rejected when email format is invalid | Negative | P2 - High | BR-001 | Login page /login is open. No active session. | email: notanemail / password: Pass@1234 | 1. Navigate to /login 2. Enter: notanemail in the email field 3. Enter password: Pass@1234 4. Click "Login" | Form validation error displayed: "Please enter a valid email address." Form is not submitted. User stays on /login. |
| TC-004 | Login rejected when password field is empty | Negative | P2 - High | BR-002 | Login page /login is open. No active session. | email: user@test.com / password: (empty) | 1. Navigate to /login 2. Enter email: user@test.com 3. Leave password field empty 4. Click "Login" | Validation error displayed: "Password is required." Login is not submitted. User stays on /login. |

### 🔒 Security

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-005 | Account locked after 5 consecutive failed login attempts | Edge Case | P1 - Critical | BR-003 | User account locked@test.com exists. User has already failed login 4 times in the current 15-minute window. | email: locked@test.com / password: WrongPass99 | 1. Navigate to /login 2. Enter email: locked@test.com 3. Enter password: WrongPass99 4. Click "Login" | System displays: "Your account has been locked for 15 minutes due to too many failed attempts." Login button is disabled. No redirect occurs. |
| TC-006 | SQL injection in email field does not expose database errors | Security | P1 - Critical | BR-001 | Login page is accessible. No active session. | email: ' OR '1'='1'-- / password: anything | 1. Navigate to /login 2. Enter in email field: ' OR '1'='1'-- 3. Enter password: anything 4. Click "Login" | System returns "Invalid email or password" error. No SQL error, stack trace, or database output is displayed. Request is logged as suspicious in server logs. |
| TC-007 | XSS payload in email field is not executed | Security | P1 - Critical | BR-001 | Login page is accessible. No active session. | email: <script>alert('XSS')</script> / password: Pass@1234 | 1. Navigate to /login 2. Enter in email field: <script>alert('XSS')</script> 3. Enter password: Pass@1234 4. Click "Login" | System sanitizes the input. No alert box appears. Error message "Invalid email or password" is displayed. Raw HTML is not rendered in the DOM. |
| TC-008 | Brute force protection: 100 rapid login requests are rate-limited | Security | P1 - Critical | BR-003 | Login page is accessible. Automated test environment. | email: user@test.com / password: (varied wrong passwords) | 1. Send 100 POST /login requests within 10 seconds using different wrong passwords 2. Observe server response | After 5 failed attempts: account is locked. Server returns 429 Too Many Requests or equivalent lockout response. No successful bypass occurs. |

---

## Traceability Matrix

| Rule ID | Rule Description | Covered By | Status |
|---|---|---|---|
| BR-001 | Email must be valid format | TC-001, TC-002, TC-003, TC-006, TC-007 | Covered |
| BR-002 | Password must be at least 8 characters | TC-001, TC-002, TC-004 | Covered |
| BR-003 | After 5 failed attempts, account locked 15 min | TC-005, TC-008 | Covered |
| BR-004 | On success, redirect to Dashboard | TC-001 | Covered |

## Coverage Summary

| Type | Count |
|---|---|
| Happy Path | 1 |
| Negative | 3 |
| Edge Case | 1 |
| Security | 3 |
| **Total** | **8** |

Coverage: 4/4 rules covered (100%)
```

---

**Why this is a strong example:**

- Every test case has concrete test data (`email: locked@test.com`, `password: WrongPass99`)
- Steps are fully executable — no vague language
- Security cases specify exact exploit vectors (SQL injection string, XSS payload)
- Traceability matrix shows 100% rule coverage
- Anti-pattern guard would pass: no vague steps, no missing test data

---

## Conversation 3 — Spec Quality Warning Triggered (Error Handling Demo)

**Context:** Testing the skill's input validation when given a low-quality spec.

---

### Input Prompt

```
Generate test cases for this spec:

## Feature: User Settings

Users can change their settings.
```

---

### Claude's Output

```
⚠️ WARN-001: SPEC QUALITY WARNING

The provided spec is missing critical information needed to generate reliable test cases.

Missing elements detected:
- [ ] No user flow or action sequence found
      (e.g., "User clicks X → System does Y")
- [ ] No business rules or validation conditions found
      (e.g., "Email must be valid format", "Name max 50 characters")

Recommendation — add the following to your spec before re-running:
1. At least one user flow (step-by-step: "User does X → System does Y")
2. At least one business rule or validation condition
3. Expected system behavior for both success and failure scenarios

Example of a valid spec addition:
---
### User Flow
1. User navigates to /settings
2. User updates display name
3. User clicks "Save"
4. System validates: name must be 1–50 characters
5. On success → success toast displayed
6. On failure → inline validation error shown

### Business Rules
- BR-001: Display name must be 1–50 characters
- BR-002: Changes are saved immediately upon clicking "Save"
---

Test case generation has been paused. No output produced.
Please refine your spec and try again.
```

---

**Why this matters:**
This demonstrates the skill's **defensive design** — it doesn't generate garbage test cases from a garbage spec. The WARN-001 mechanism forces QC to produce a quality spec first, which improves downstream output quality.

---

## Conversation 4 — Complex Real-World Spec: Unsplash Photo Upload

**Context:** The skill was tested on the `SPEC_UNSPLASH.md` Photo Upload feature with `coverage_level: full` to show its ability to handle complex, multi-rule specs.

---

### Input Prompt

```
Generate test cases for the following spec.

Parameters:
- feature_name: Photo Upload (Contributors)
- output_format: markdown
- coverage_level: full
- enable_security: true
- mask_pii: true

[SPEC content: Feature 5 — Photo Upload from SPEC_UNSPLASH.md pasted here]
```

---

### Claude's Output (selected test cases)

```
PII Masking Report:
  Fields redacted: 0
  No PII detected in this spec.
  Spec sent to AI: [clean version — no redactions needed]

---

## Test Cases — Photo Upload (Contributors)

### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-001 | Authenticated user uploads a valid JPEG photo | Happy Path | P1 - Critical | BR-036, BR-037, BR-038, BR-039, BR-046 | User is authenticated. User navigates to https://unsplash.com/submit. | File: photo.jpg (JPEG, 8 MB, 3000×2500 px = 7.5 MP) | 1. Navigate to /submit 2. Click "Choose file" 3. Select photo.jpg 4. Verify preview appears 5. Enter description: "Mountain sunrise" 6. Add tags: "mountain, sunrise, landscape" 7. Click "Submit" | System uploads the photo. Confirmation notification is displayed. Photo appears on user's profile with status "Under Review". |

### 🔴 Negative

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-002 | Upload rejected when file format is GIF | Negative | P2 - High | BR-038 | User is authenticated. User is on /submit. | File: animation.gif (GIF, 5 MB) | 1. Navigate to /submit 2. Click "Choose file" 3. Select animation.gif 4. Attempt to submit | System rejects the file immediately. Error displayed: "Only JPEG and PNG files are accepted." File is not uploaded. |
| TC-003 | Upload rejected when file size exceeds 50 MB | Negative | P2 - High | BR-039 | User is authenticated. User is on /submit. | File: large_photo.jpg (JPEG, 55 MB, valid resolution) | 1. Navigate to /submit 2. Click "Choose file" 3. Select large_photo.jpg | System rejects the file. Error displayed: "File size exceeds the 50 MB limit." No upload is initiated. |
| TC-004 | Upload rejected when resolution is below 5 megapixels | Negative | P2 - High | BR-037 | User is authenticated. User is on /submit. | File: small_photo.jpg (JPEG, 2 MB, 1200×900 px = 1.08 MP) | 1. Navigate to /submit 2. Select small_photo.jpg 3. Attempt to submit | System rejects the file. Error displayed: "Image resolution must be at least 5 megapixels (2500 × 2000 px minimum)." |
| TC-005 | Upload rejected for unauthenticated guest user | Negative | P1 - Critical | BR-036 | User is NOT authenticated (guest). | None required | 1. Navigate to /submit without logging in | System redirects to /login or /join. Access to /submit is denied. No upload form is shown to guest users. |
| TC-006 | Upload rejected when daily limit of 10 photos is reached | Negative | P2 - High | BR-040 | User is authenticated (non-verified account). User has already uploaded 10 photos today. | File: photo11.jpg (JPEG, valid size and resolution) | 1. Navigate to /submit 2. Select photo11.jpg 3. Click "Submit" | System blocks the upload. Error displayed: "You have reached your daily upload limit of 10 photos. Please try again tomorrow." |

### 🟡 Edge Cases

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-007 | Upload with exactly 50 MB file (boundary — maximum valid) | Edge Case | P2 - High | BR-039 | User is authenticated. | File: exact_limit.jpg (JPEG, exactly 50.00 MB, valid resolution) | 1. Navigate to /submit 2. Select exact_limit.jpg 3. Submit | System accepts the file. Upload proceeds normally. Preview is displayed. |
| TC-008 | Upload with exactly 30 tags (boundary — maximum valid) | Edge Case | P2 - High | BR-048 | User is authenticated. Photo already uploaded and preview displayed. | 30 unique tags: "tag1, tag2, ... tag30" | 1. After photo preview 2. Enter 30 tags in the tag field 3. Click "Submit" | System accepts all 30 tags. Upload succeeds. Photo shows all 30 tags after review approval. |
| TC-009 | Adding 31st tag is prevented | Edge Case | P2 - High | BR-048 | User is on /submit with photo preview displayed. 30 tags already entered. | 31st tag: "extratag" | 1. After 30 tags are entered 2. Attempt to add tag: "extratag" | System prevents adding the 31st tag. UI may disable the tag input field or display: "Maximum 30 tags allowed." Existing 30 tags remain. |
| TC-010 | Upload the 10th photo on the daily limit boundary | Edge Case | P2 - High | BR-040 | User is authenticated (non-verified). User has uploaded exactly 9 photos today. | File: photo10.jpg (valid JPEG, 8 MB) | 1. Navigate to /submit 2. Select photo10.jpg 3. Click "Submit" | System accepts the upload (10th photo is within limit). Confirmation notification shown. Photo shows status "Under Review". |
| TC-011 | Description field at maximum 500 characters is accepted | Edge Case | P3 - Medium | BR-047 | User is authenticated. Photo preview displayed on /submit. | description: string of exactly 500 characters | 1. Paste 500-character description into description field 2. Click "Submit" | System accepts the description. Upload proceeds. No truncation warning. |
| TC-012 | Description field at 501 characters is rejected or truncated | Edge Case | P3 - Medium | BR-047 | User is authenticated. Photo preview displayed on /submit. | description: string of 501 characters | 1. Paste 501-character description into description field | System either: (a) prevents input beyond 500 chars, or (b) displays inline error: "Description cannot exceed 500 characters." Upload is not submitted with the oversized description. |

### 🔒 Security

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-013 | XSS payload in description field is sanitized | Security | P1 - Critical | BR-047 | User is authenticated. Photo preview displayed. | description: <script>alert('XSS')</script> | 1. Enter <script>alert('XSS')</script> in description 2. Submit photo | System sanitizes the input. No alert box executes. Description is stored as plain text or HTML-encoded. No script is rendered in the UI. |
| TC-014 | SQL injection in tags field does not expose errors | Security | P1 - Critical | BR-048 | User is authenticated. Photo preview displayed. | tags: '; DROP TABLE photos;-- | 1. Enter '; DROP TABLE photos;-- in the tags field 2. Submit | System rejects or sanitizes the input. No SQL error or stack trace is returned. Database is not affected. Request is logged as suspicious. |
| TC-015 | IDOR: user cannot access another user's draft upload | Security | P1 - Critical | BR-036 | Two users exist: User A (authenticated) and User B (has draft upload ID: draft-9999). | URL: /submit/draft/9999 accessed by User A | 1. Log in as User A 2. Navigate to /submit/draft/9999 (User B's draft) | System returns HTTP 403 Forbidden or redirects to /submit. User A cannot view or modify User B's draft. |
| TC-016 | Polyglot file bypass: file with .jpg extension but GIF content is rejected | Security | P2 - High | BR-038 | User is authenticated. | File: fake.jpg (file header is GIF89a, extension is .jpg) | 1. Navigate to /submit 2. Select fake.jpg (GIF content disguised as JPEG) 3. Submit | System inspects MIME type (not only extension). File is rejected with: "Only JPEG and PNG files are accepted." Upload does not proceed. |

---

## Traceability Matrix

| Rule ID | Rule Description | Covered By | Status |
|---|---|---|---|
| BR-036 | Only authenticated users can upload | TC-001, TC-005, TC-015 | Covered |
| BR-037 | Minimum 5 megapixel resolution | TC-001, TC-004 | Covered |
| BR-038 | JPEG and PNG only | TC-001, TC-002, TC-016 | Covered |
| BR-039 | Max 50 MB file size | TC-003, TC-007 | Covered |
| BR-040 | 10 photos/day limit | TC-006, TC-010 | Covered |
| BR-041 | Royalty-free irrevocable license | — | ⚠️ COVERAGE GAP |
| BR-042 | Contributor must own rights | — | ⚠️ COVERAGE GAP |
| BR-043 | No prohibited content | — | ⚠️ COVERAGE GAP |
| BR-044 | Model release for identifiable people | — | ⚠️ COVERAGE GAP |
| BR-045 | Photos reviewed before publishing | TC-001 | Covered |
| BR-046 | Status "Under Review" after upload | TC-001, TC-010 | Covered |
| BR-047 | Description, alt text, location fields | TC-011, TC-012, TC-013 | Covered |
| BR-048 | Up to 30 tags per photo | TC-008, TC-009, TC-014 | Covered |

⚠️ COVERAGE GAP: BR-041, BR-042, BR-043, BR-044
  Reason: These rules describe legal/policy obligations, not testable UI behavior.
  Action: These require manual review by a legal/compliance QC, not automated functional testing.
  Recommend: Document as out-of-scope for functional testing. Mark as "Policy — Manual Review".

## Coverage Summary

| Type | Count |
|---|---|
| Happy Path | 1 |
| Negative | 5 |
| Edge Case | 6 |
| Security | 4 |
| **Total** | **16** |

Functional coverage: 9/13 rules (69%)
Policy-only rules (not functionally testable): 4/13
Effective functional coverage: 9/9 testable rules (100%)
```

---

**Why this is the strongest example:**

- Handles a 13-rule spec with 16 test cases across all 4 types
- Coverage gap detection correctly identifies non-testable policy rules (BR-041–044) and explains why
- Security case TC-016 (polyglot file bypass) demonstrates deep security reasoning — checking MIME type, not just file extension
- Edge cases cover all boundaries: file size (±1 byte), tags (30 vs 31), description (500 vs 501 chars)
- Effective 100% functional coverage achieved

---

## Conversation 5 — Iteration: Improving a Flagged Test Case

**Context:** The anti-pattern guard flagged a TC from an early run. This shows how the skill self-corrects.

---

### Flagged Output (Before)

```
⚠️ QC REVIEW REQUIRED
The following test cases were flagged as potentially low quality:
- TC-003: Vague expected result — "system should display an error"
- TC-007: Missing test data — no specific values provided
```

---

### Follow-up Prompt

```
Please revise TC-003 and TC-007 to fix the anti-pattern violations.
```

---

### Claude's Revised Output

```
Revised TC-003:
Expected Result: System displays an inline error message below the email field:
"Please enter a valid email address." The form is NOT submitted.
The user remains on the /login page. No network request is sent to the server.

Revised TC-007:
Test Data: email: boundary@test.com / password: Abcd1234 (exactly 8 characters,
contains 1 uppercase [A], 1 lowercase [bcd], 1 number [1234])
Expected Result: Registration succeeds. System redirects to /dashboard.
No validation error is shown for the password field.
```

---

**What this demonstrates:**
The skill's built-in anti-pattern guard enables an **iterative quality loop** — not just generating test cases, but actively detecting and fixing quality issues in its own output.

---

## Summary: Key Metrics

| Metric | Result |
|---|---|
| Spec → Test Cases turnaround | ~30 seconds |
| User Login spec (4 rules) | 8 TCs, 100% rule coverage |
| Photo Upload spec (13 rules) | 16 TCs, 100% functional coverage |
| Vague test cases generated | 0 (anti-pattern guard enforced) |
| Security test cases per run | 3–4 minimum (enable_security=true) |
| WARN-001 catches low-quality spec | Yes — stops generation, asks for better spec |

---

## Files Referenced

| File | Purpose |
|---|---|
| [`SKILL.md`](../SKILL.md) | The AI Skill prompt (v1.1.0) — used in all conversations above |
| [`SPEC.md`](../SPEC.md) | Skill specification — defines all rules the skill follows |
| [`SPEC_UNSPLASH.md`](../SPEC_UNSPLASH.md) | Real-world test spec used in Conversation 4 |
| [`skill-card.md`](../skill-card.md) | One-page summary of the skill for the judges |
| [`README.md`](../README.md) | Project overview |
