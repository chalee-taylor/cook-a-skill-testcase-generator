# Test Cases — Unsplash.com (Generated from SPEC_UNFLASH.md)

## PII Masking Report
- Emails in test data use synthetic `example.com` accounts (no real PII).

### Flow 1 — Search & Discovery

#### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-001 | BR-001 - The search bar is accessible on all pages (header navigation) — authenti... | Happy Path | P1 - Critical | BR-001 | User/API client is in Flow 1 — Search & Discovery context and can access target screen/endpoint. | keyword: mountain, email: user1@example.com, password: Pass@1234, photo_id: photo-001, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | The search bar is accessible on all pages (header navigation) — authenticated and unauthenticated users |
| TC-002 | BR-002 - Search results are filtered into 3 tabs: Photos, Collections, Users | Happy Path | P1 - Critical | BR-002 | User/API client is in Flow 1 — Search & Discovery context and can access target screen/endpoint. | keyword: mountain, email: user2@example.com, password: Pass@1234, photo_id: photo-002, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Search results are filtered into 3 tabs: Photos, Collections, Users |
| TC-003 | BR-003 - Each search result page displays a set of relevant tag suggestions at th... | Happy Path | P1 - Critical | BR-003 | User/API client is in Flow 1 — Search & Discovery context and can access target screen/endpoint. | keyword: mountain, email: user3@example.com, password: Pass@1234, photo_id: photo-003, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Each search result page displays a set of relevant tag suggestions at the top to guide users toward related searches |
| TC-006 | BR-006 - If the search returns 0 results, the system must display an empty-state ... | Happy Path | P1 - Critical | BR-006 | User/API client is in Flow 1 — Search & Discovery context and can access target screen/endpoint. | keyword: mountain, email: user6@example.com, password: Pass@1234, photo_id: photo-006, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | If the search returns 0 results, the system must display an empty-state message: "We couldn't find anything for [keyword]" along with suggested alternative search terms |
| TC-007 | BR-007 - Trending/popular searches are displayed below the search bar on the home... | Happy Path | P1 - Critical | BR-007 | User/API client is in Flow 1 — Search & Discovery context and can access target screen/endpoint. | keyword: mountain, email: user7@example.com, password: Pass@1234, photo_id: photo-007, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Trending/popular searches are displayed below the search bar on the homepage to assist discovery |
| TC-008 | BR-008 - Category navigation links (e.g., "Nature", "Travel", "Architecture") are... | Happy Path | P1 - Critical | BR-008 | User/API client is in Flow 1 — Search & Discovery context and can access target screen/endpoint. | keyword: mountain, email: user8@example.com, password: Pass@1234, photo_id: photo-008, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Category navigation links (e.g., "Nature", "Travel", "Architecture") are available in the header and filter the photo grid by category |
| TC-009 | BR-009 - Users can sort search results by: Relevance (default) or Latest | Happy Path | P1 - Critical | BR-009 | User/API client is in Flow 1 — Search & Discovery context and can access target screen/endpoint. | keyword: mountain, email: user9@example.com, password: Pass@1234, photo_id: photo-009, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can sort search results by: Relevance (default) or Latest |

#### 🔴 Negative

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-010 | BR-010 - Search keyword must be between 1 and 200 characters | Negative | P2 - High | BR-010 | User/API client is in Flow 1 — Search & Discovery context and can access target screen/endpoint. | keyword: mountain, email: user10@example.com, password: Pass@1234, photo_id: photo-010, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Search keyword must be between 1 and 200 characters |

#### 🟡 Edge Cases

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-004 | BR-004 - The homepage features an infinite-scroll photo grid — new photos load au... | Edge Case | P2 - High | BR-004 | User/API client is in Flow 1 — Search & Discovery context and can access target screen/endpoint. | keyword: mountain, email: user4@example.com, password: Pass@1234, photo_id: photo-004, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | The homepage features an infinite-scroll photo grid — new photos load automatically when the user scrolls to the bottom |
| TC-005 | BR-005 - Search results must return at most 20 photos per page by default; pagina... | Edge Case | P2 - High | BR-005 | User/API client is in Flow 1 — Search & Discovery context and can access target screen/endpoint. | keyword: mountain, email: user5@example.com, password: Pass@1234, photo_id: photo-005, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Search results must return at most 20 photos per page by default; pagination is supported |

### Flow 2 — Download

#### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-011 | BR-011 - Guest users (unauthenticated) can download free photos without an accoun... | Happy Path | P1 - Critical | BR-011 | User/API client is in Flow 2 — Download context and can access target screen/endpoint. | keyword: mountain, email: user11@example.com, password: Pass@1234, photo_id: photo-011, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Guest users (unauthenticated) can download free photos without an account |
| TC-012 | BR-012 - Free photo downloads do not require attribution (but attribution to phot... | Happy Path | P1 - Critical | BR-012 | User/API client is in Flow 2 — Download context and can access target screen/endpoint. | keyword: mountain, email: user12@example.com, password: Pass@1234, photo_id: photo-012, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Free photo downloads do not require attribution (but attribution to photographer is appreciated) |
| TC-013 | BR-013 - Download button is labeled "Download free" for free photos and shows a l... | Happy Path | P1 - Critical | BR-013 | User/API client is in Flow 2 — Download context and can access target screen/endpoint. | keyword: mountain, email: user13@example.com, password: Pass@1234, photo_id: photo-013, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Download button is labeled "Download free" for free photos and shows a lock icon for Unsplash+ premium photos |
| TC-014 | BR-014 - Users can select download size: Small, Medium, Large, or Original (for f... | Happy Path | P1 - Critical | BR-014 | User/API client is in Flow 2 — Download context and can access target screen/endpoint. | keyword: mountain, email: user14@example.com, password: Pass@1234, photo_id: photo-014, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can select download size: Small, Medium, Large, or Original (for free photos) |
| TC-015 | BR-015 - Unsplash+ photos require an active Unsplash+ subscription to download wi... | Happy Path | P1 - Critical | BR-015 | User/API client is in Flow 2 — Download context and can access target screen/endpoint. | keyword: mountain, email: user15@example.com, password: Pass@1234, photo_id: photo-015, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Unsplash+ photos require an active Unsplash+ subscription to download without watermark |
| TC-016 | BR-016 - Downloading a photo triggers a download count increment on the photo's s... | Happy Path | P1 - Critical | BR-016 | User/API client is in Flow 2 — Download context and can access target screen/endpoint. | keyword: mountain, email: user16@example.com, password: Pass@1234, photo_id: photo-016, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Downloading a photo triggers a download count increment on the photo's stats |
| TC-017 | BR-017 - Downloaded photos are provided in JPEG format at the selected resolution | Happy Path | P1 - Critical | BR-017 | User/API client is in Flow 2 — Download context and can access target screen/endpoint. | keyword: mountain, email: user17@example.com, password: Pass@1234, photo_id: photo-017, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Downloaded photos are provided in JPEG format at the selected resolution |
| TC-018 | BR-018 - The platform tracks download events for analytics (no user account linka... | Happy Path | P1 - Critical | BR-018 | User/API client is in Flow 2 — Download context and can access target screen/endpoint. | keyword: mountain, email: user18@example.com, password: Pass@1234, photo_id: photo-018, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | The platform tracks download events for analytics (no user account linkage for guest downloads) |

#### 🔴 Negative

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-019 | BR-019 - Users cannot resell downloaded photos as-is on competing stock photo pla... | Negative | P2 - High | BR-019 | User/API client is in Flow 2 — Download context and can access target screen/endpoint. | keyword: mountain, email: user19@example.com, password: Pass@1234, photo_id: photo-019, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users cannot resell downloaded photos as-is on competing stock photo platforms |
| TC-020 | BR-020 - Users cannot redistribute downloaded photos as part of a competing stock... | Negative | P2 - High | BR-020 | User/API client is in Flow 2 — Download context and can access target screen/endpoint. | keyword: mountain, email: user20@example.com, password: Pass@1234, photo_id: photo-020, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users cannot redistribute downloaded photos as part of a competing stock photo service |

### Flow 3 — Registration & Login

#### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-021 | BR-021 - Email must be a valid format (RFC 5321 compliant) | Happy Path | P1 - Critical | BR-021 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user21@example.com, password: Pass@1234, photo_id: photo-021, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Email must be a valid format (RFC 5321 compliant) |
| TC-022 | BR-022 - Password must be at least 8 characters long | Happy Path | P1 - Critical | BR-022 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user22@example.com, password: Pass@1234, photo_id: photo-022, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Password must be at least 8 characters long |
| TC-023 | BR-023 - Password must contain at least one uppercase letter, one lowercase lette... | Happy Path | P1 - Critical | BR-023 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user23@example.com, password: Pass@1234, photo_id: photo-023, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Password must contain at least one uppercase letter, one lowercase letter, and one number |
| TC-024 | BR-024 - Email address must be unique — no two accounts can share the same email | Happy Path | P1 - Critical | BR-024 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user24@example.com, password: Pass@1234, photo_id: photo-024, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Email address must be unique — no two accounts can share the same email |
| TC-025 | BR-025 - Username must be unique across the platform (first-come, first-served ba... | Happy Path | P1 - Critical | BR-025 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user25@example.com, password: Pass@1234, photo_id: photo-025, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Username must be unique across the platform (first-come, first-served basis) |
| TC-027 | BR-027 - Username can only contain letters, numbers, and underscores — no spaces,... | Happy Path | P1 - Critical | BR-027 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user27@example.com, password: Pass@1234, photo_id: photo-027, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Username can only contain letters, numbers, and underscores — no spaces, special characters, or URLs |
| TC-031 | BR-031 - Users can sign up/login via Google OAuth or Facebook OAuth as alternativ... | Happy Path | P1 - Critical | BR-031 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user31@example.com, password: Pass@1234, photo_id: photo-031, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can sign up/login via Google OAuth or Facebook OAuth as alternative methods |
| TC-032 | BR-032 - Upon successful registration, the system sends a confirmation email to t... | Happy Path | P1 - Critical | BR-032 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user32@example.com, password: Pass@1234, photo_id: photo-032, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Upon successful registration, the system sends a confirmation email to the registered address |
| TC-035 | BR-035 - Users must agree to Terms of Service and Privacy Policy before completin... | Happy Path | P1 - Critical | BR-035 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user35@example.com, password: Pass@1234, photo_id: photo-035, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users must agree to Terms of Service and Privacy Policy before completing registration |

#### 🔴 Negative

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-026 | BR-026 - Username must be between 3 and 30 characters | Negative | P2 - High | BR-026 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user26@example.com, password: Pass@1234, photo_id: photo-026, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Username must be between 3 and 30 characters |
| TC-028 | BR-028 - Username cannot be a trademarked brand name | Negative | P2 - High | BR-028 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user28@example.com, password: Pass@1234, photo_id: photo-028, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Username cannot be a trademarked brand name |
| TC-029 | BR-029 - Username cannot impersonate another person or public figure | Negative | P2 - High | BR-029 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user29@example.com, password: Pass@1234, photo_id: photo-029, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Username cannot impersonate another person or public figure |
| TC-030 | BR-030 - After 5 consecutive failed login attempts, the account is temporarily lo... | Negative | P2 - High | BR-030 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user30@example.com, password: Pass@1234, photo_id: photo-030, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | After 5 consecutive failed login attempts, the account is temporarily locked for 15 minutes |
| TC-034 | BR-034 - Login error message must be generic: "Invalid email or password" | Negative | P2 - High | BR-034 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user34@example.com, password: Pass@1234, photo_id: photo-034, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Login error message must be generic: "Invalid email or password" |

#### 🔒 Security

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-033 | BR-033 - The system must not reveal whether an email address is registered when r... | Security | P1 - Critical | BR-033 | User/API client is in Flow 3 — Registration & Login context and can access target screen/endpoint. | keyword: mountain, email: user33@example.com, password: Pass@1234, photo_id: photo-033, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20, payload: ' OR 1=1 -- | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | The system must not reveal whether an email address is registered when returning login error messages (anti-enumeration) |

### Flow 4 — Upload

#### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-036 | BR-036 - Only registered (authenticated) users can upload photos | Happy Path | P1 - Critical | BR-036 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user36@example.com, password: Pass@1234, photo_id: photo-036, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Only registered (authenticated) users can upload photos |
| TC-038 | BR-038 - Accepted file formats: JPEG and PNG only | Happy Path | P1 - Critical | BR-038 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user38@example.com, password: Pass@1234, photo_id: photo-038, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Accepted file formats: JPEG and PNG only |
| TC-041 | BR-041 - By uploading, contributors grant Unsplash and users a royalty-free, irre... | Happy Path | P1 - Critical | BR-041 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user41@example.com, password: Pass@1234, photo_id: photo-041, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | By uploading, contributors grant Unsplash and users a royalty-free, irrevocable license to use the photo |
| TC-042 | BR-042 - Contributors must own the rights to the uploaded image or have permissio... | Happy Path | P1 - Critical | BR-042 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user42@example.com, password: Pass@1234, photo_id: photo-042, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Contributors must own the rights to the uploaded image or have permission from the rights holder |
| TC-043 | BR-043 - Photos must not contain: nudity, violence, hate content, personally iden... | Happy Path | P1 - Critical | BR-043 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user43@example.com, password: Pass@1234, photo_id: photo-043, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Photos must not contain: nudity, violence, hate content, personally identifiable information (PII) of individuals without consent, copyrighted logos or trademarked brand elements |
| TC-044 | BR-044 - Photos depicting identifiable people in editorial or commercial contexts... | Happy Path | P1 - Critical | BR-044 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user44@example.com, password: Pass@1234, photo_id: photo-044, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Photos depicting identifiable people in editorial or commercial contexts require a valid model release |
| TC-046 | BR-046 - Upon successful upload, the photo appears on the contributor's profile w... | Happy Path | P1 - Critical | BR-046 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user46@example.com, password: Pass@1234, photo_id: photo-046, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Upon successful upload, the photo appears on the contributor's profile with status "Under Review" until approved |
| TC-047 | BR-047 - Contributors can add a description, alt text, and location to their uplo... | Happy Path | P1 - Critical | BR-047 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user47@example.com, password: Pass@1234, photo_id: photo-047, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Contributors can add a description, alt text, and location to their uploaded photos |

#### 🔴 Negative

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-037 | BR-037 - Uploaded photos must have a minimum resolution of 5 megapixels (e.g., 25... | Negative | P2 - High | BR-037 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user37@example.com, password: Pass@1234, photo_id: photo-037, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Uploaded photos must have a minimum resolution of 5 megapixels (e.g., 2500 × 2000 pixels minimum) |
| TC-039 | BR-039 - Maximum file size per upload: 50 MB | Negative | P2 - High | BR-039 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user39@example.com, password: Pass@1234, photo_id: photo-039, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Maximum file size per upload: 50 MB |
| TC-040 | BR-040 - Users can upload up to 10 photos per day (daily limit for non-verified a... | Negative | P2 - High | BR-040 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user40@example.com, password: Pass@1234, photo_id: photo-040, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can upload up to 10 photos per day (daily limit for non-verified accounts) |
| TC-045 | BR-045 - Submitted photos are subject to review — non-compliant photos are reject... | Negative | P2 - High | BR-045 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user45@example.com, password: Pass@1234, photo_id: photo-045, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Submitted photos are subject to review — non-compliant photos are rejected with an explanatory email to the contributor |

#### 🟡 Edge Cases

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-048 | BR-048 - Contributors can add up to 30 tags per photo for discoverability | Edge Case | P2 - High | BR-048 | User/API client is in Flow 4 — Upload context and can access target screen/endpoint. | keyword: mountain, email: user48@example.com, password: Pass@1234, photo_id: photo-048, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Contributors can add up to 30 tags per photo for discoverability |

### Flow 5 — Collections

#### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-049 | BR-049 - Only authenticated users can create collections | Happy Path | P1 - Critical | BR-049 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user49@example.com, password: Pass@1234, photo_id: photo-049, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Only authenticated users can create collections |
| TC-053 | BR-053 - Users can add any photo (free or Unsplash+) to their collections — addin... | Happy Path | P1 - Critical | BR-053 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user53@example.com, password: Pass@1234, photo_id: photo-053, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can add any photo (free or Unsplash+) to their collections — adding a premium photo does not require a subscription |
| TC-055 | BR-055 - The photo contributor receives a notification when their photo is added ... | Happy Path | P1 - Critical | BR-055 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user55@example.com, password: Pass@1234, photo_id: photo-055, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | The photo contributor receives a notification when their photo is added to another user's collection |
| TC-056 | BR-056 - Collections containing offensive content are removed by admins immediate... | Happy Path | P1 - Critical | BR-056 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user56@example.com, password: Pass@1234, photo_id: photo-056, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Collections containing offensive content are removed by admins immediately, and an email is sent to the collection creator |
| TC-057 | BR-057 - Users can delete their collections — deleting a collection does not dele... | Happy Path | P1 - Critical | BR-057 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user57@example.com, password: Pass@1234, photo_id: photo-057, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can delete their collections — deleting a collection does not delete the photos |
| TC-058 | BR-058 - Users can reorder photos within a collection | Happy Path | P1 - Critical | BR-058 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user58@example.com, password: Pass@1234, photo_id: photo-058, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can reorder photos within a collection |
| TC-059 | BR-059 - A collection displays a cover photo (by default: the first photo added; ... | Happy Path | P1 - Critical | BR-059 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user59@example.com, password: Pass@1234, photo_id: photo-059, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | A collection displays a cover photo (by default: the first photo added; user can change this) |
| TC-060 | BR-060 - Other users can follow public collections to receive updates | Happy Path | P1 - Critical | BR-060 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user60@example.com, password: Pass@1234, photo_id: photo-060, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Other users can follow public collections to receive updates |

#### 🔴 Negative

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-050 | BR-050 - A user can create an unlimited number of collections | Negative | P2 - High | BR-050 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user50@example.com, password: Pass@1234, photo_id: photo-050, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | A user can create an unlimited number of collections |
| TC-051 | BR-051 - Collection names must be between 1 and 60 characters | Negative | P2 - High | BR-051 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user51@example.com, password: Pass@1234, photo_id: photo-051, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Collection names must be between 1 and 60 characters |
| TC-052 | BR-052 - Collections can be set as Public (visible to all) or Private (visible on... | Negative | P2 - High | BR-052 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user52@example.com, password: Pass@1234, photo_id: photo-052, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Collections can be set as Public (visible to all) or Private (visible only to the owner) |
| TC-054 | BR-054 - A user cannot add the same photo to the same collection twice (duplicate... | Negative | P2 - High | BR-054 | User/API client is in Flow 5 — Collections context and can access target screen/endpoint. | keyword: mountain, email: user54@example.com, password: Pass@1234, photo_id: photo-054, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | A user cannot add the same photo to the same collection twice (duplicate prevention) |

### Flow 6 — Like/Save

#### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-061 | BR-061 - Only authenticated users can like a photo | Happy Path | P1 - Critical | BR-061 | User/API client is in Flow 6 — Like/Save context and can access target screen/endpoint. | keyword: mountain, email: user61@example.com, password: Pass@1234, photo_id: photo-061, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Only authenticated users can like a photo |
| TC-062 | BR-062 - A user can like any photo (free or Unsplash+) without a subscription | Happy Path | P1 - Critical | BR-062 | User/API client is in Flow 6 — Like/Save context and can access target screen/endpoint. | keyword: mountain, email: user62@example.com, password: Pass@1234, photo_id: photo-062, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | A user can like any photo (free or Unsplash+) without a subscription |
| TC-063 | BR-063 - A user can only like a photo once — the like button toggles (click again... | Happy Path | P1 - Critical | BR-063 | User/API client is in Flow 6 — Like/Save context and can access target screen/endpoint. | keyword: mountain, email: user63@example.com, password: Pass@1234, photo_id: photo-063, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | A user can only like a photo once — the like button toggles (click again to unlike) |
| TC-064 | BR-064 - The photo contributor receives a notification when their photo is liked | Happy Path | P1 - Critical | BR-064 | User/API client is in Flow 6 — Like/Save context and can access target screen/endpoint. | keyword: mountain, email: user64@example.com, password: Pass@1234, photo_id: photo-064, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | The photo contributor receives a notification when their photo is liked |
| TC-065 | BR-065 - A user's liked photos are visible on their profile under the "Likes" tab... | Happy Path | P1 - Critical | BR-065 | User/API client is in Flow 6 — Like/Save context and can access target screen/endpoint. | keyword: mountain, email: user65@example.com, password: Pass@1234, photo_id: photo-065, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | A user's liked photos are visible on their profile under the "Likes" tab (public by default) |
| TC-066 | BR-066 - The like count on each photo is displayed publicly | Happy Path | P1 - Critical | BR-066 | User/API client is in Flow 6 — Like/Save context and can access target screen/endpoint. | keyword: mountain, email: user66@example.com, password: Pass@1234, photo_id: photo-066, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | The like count on each photo is displayed publicly |
| TC-067 | BR-067 - Unlike does not notify the contributor | Happy Path | P1 - Critical | BR-067 | User/API client is in Flow 6 — Like/Save context and can access target screen/endpoint. | keyword: mountain, email: user67@example.com, password: Pass@1234, photo_id: photo-067, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Unlike does not notify the contributor |

### Flow 7 — Profile

#### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-068 | BR-068 - Profile URL format: `https://unsplash.com/@{username}` | Happy Path | P1 - Critical | BR-068 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user68@example.com, password: Pass@1234, photo_id: photo-068, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Profile URL format: `https://unsplash.com/@{username}` |
| TC-069 | BR-069 - Profile page is publicly visible (no login required to view) | Happy Path | P1 - Critical | BR-069 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user69@example.com, password: Pass@1234, photo_id: photo-069, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Profile page is publicly visible (no login required to view) |
| TC-070 | BR-070 - Profile displays: avatar, name, bio, location, website, social links, fo... | Happy Path | P1 - Critical | BR-070 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user70@example.com, password: Pass@1234, photo_id: photo-070, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Profile displays: avatar, name, bio, location, website, social links, followers/following count |
| TC-071 | BR-071 - Profile tabs: Photos, Likes, Collections | Happy Path | P1 - Critical | BR-071 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user71@example.com, password: Pass@1234, photo_id: photo-071, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Profile tabs: Photos, Likes, Collections |
| TC-072 | BR-072 - Users can edit: name, username, bio, location, website, portfolio URL, s... | Happy Path | P1 - Critical | BR-072 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user72@example.com, password: Pass@1234, photo_id: photo-072, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can edit: name, username, bio, location, website, portfolio URL, social links (Twitter/Instagram) |
| TC-075 | BR-075 - Website URL must be a valid URL format (starting with http:// or https:/... | Happy Path | P1 - Critical | BR-075 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user75@example.com, password: Pass@1234, photo_id: photo-075, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Website URL must be a valid URL format (starting with http:// or https://) |
| TC-077 | BR-077 - Profile stats are visible: total photos uploaded, total downloads receiv... | Happy Path | P1 - Critical | BR-077 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user77@example.com, password: Pass@1234, photo_id: photo-077, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Profile stats are visible: total photos uploaded, total downloads received, total views received |
| TC-078 | BR-078 - Admins can suspend or deactivate accounts violating community guidelines | Happy Path | P1 - Critical | BR-078 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user78@example.com, password: Pass@1234, photo_id: photo-078, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Admins can suspend or deactivate accounts violating community guidelines |

#### 🔴 Negative

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-073 | BR-073 - Username changes are allowed but limited to once per 30 days | Negative | P2 - High | BR-073 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user73@example.com, password: Pass@1234, photo_id: photo-073, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Username changes are allowed but limited to once per 30 days |
| TC-074 | BR-074 - Bio max length: 200 characters | Negative | P2 - High | BR-074 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user74@example.com, password: Pass@1234, photo_id: photo-074, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Bio max length: 200 characters |
| TC-076 | BR-076 - Users can upload an avatar image (JPEG or PNG, max 5 MB, minimum 200×200... | Negative | P2 - High | BR-076 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user76@example.com, password: Pass@1234, photo_id: photo-076, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can upload an avatar image (JPEG or PNG, max 5 MB, minimum 200×200 px) |

#### 🟡 Edge Cases

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-079 | BR-079 - Inactive accounts with 0 photos may have their username reclaimed after ... | Edge Case | P2 - High | BR-079 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user79@example.com, password: Pass@1234, photo_id: photo-079, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Inactive accounts with 0 photos may have their username reclaimed after 12 months of inactivity |
| TC-080 | BR-080 - Inactive accounts with 1+ photos may have their username reclaimed after... | Edge Case | P2 - High | BR-080 | User/API client is in Flow 7 — Profile context and can access target screen/endpoint. | keyword: mountain, email: user80@example.com, password: Pass@1234, photo_id: photo-080, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Inactive accounts with 1+ photos may have their username reclaimed after 24 months of inactivity |

### Flow 8 — Unsplash+ Subscription

#### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-081 | BR-081 - Unsplash+ is a paid subscription with a monthly or annual billing option | Happy Path | P1 - Critical | BR-081 | User/API client is in Flow 8 — Unsplash+ Subscription context and can access target screen/endpoint. | keyword: mountain, email: user81@example.com, password: Pass@1234, photo_id: photo-081, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Unsplash+ is a paid subscription with a monthly or annual billing option |
| TC-082 | BR-082 - Unsplash+ photos are identified by a lock icon overlay on the thumbnail | Happy Path | P1 - Critical | BR-082 | User/API client is in Flow 8 — Unsplash+ Subscription context and can access target screen/endpoint. | keyword: mountain, email: user82@example.com, password: Pass@1234, photo_id: photo-082, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Unsplash+ photos are identified by a lock icon overlay on the thumbnail |
| TC-085 | BR-085 - Unsplash+ subscription is auto-renewed at the end of each billing cycle ... | Happy Path | P1 - Critical | BR-085 | User/API client is in Flow 8 — Unsplash+ Subscription context and can access target screen/endpoint. | keyword: mountain, email: user85@example.com, password: Pass@1234, photo_id: photo-085, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Unsplash+ subscription is auto-renewed at the end of each billing cycle unless cancelled |
| TC-086 | BR-086 - Users can cancel the Unsplash+ subscription at any time; access remains ... | Happy Path | P1 - Critical | BR-086 | User/API client is in Flow 8 — Unsplash+ Subscription context and can access target screen/endpoint. | keyword: mountain, email: user86@example.com, password: Pass@1234, photo_id: photo-086, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can cancel the Unsplash+ subscription at any time; access remains until the end of the current billing period |
| TC-088 | BR-088 - Payment is processed securely via Stripe; Unsplash does not store raw ca... | Happy Path | P1 - Critical | BR-088 | User/API client is in Flow 8 — Unsplash+ Subscription context and can access target screen/endpoint. | keyword: mountain, email: user88@example.com, password: Pass@1234, photo_id: photo-088, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Payment is processed securely via Stripe; Unsplash does not store raw card data |
| TC-089 | BR-089 - Upon successful subscription activation, the user receives a confirmatio... | Happy Path | P1 - Critical | BR-089 | User/API client is in Flow 8 — Unsplash+ Subscription context and can access target screen/endpoint. | keyword: mountain, email: user89@example.com, password: Pass@1234, photo_id: photo-089, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Upon successful subscription activation, the user receives a confirmation email with billing details |
| TC-090 | BR-090 - Users can view and download their invoices from the billing settings pag... | Happy Path | P1 - Critical | BR-090 | User/API client is in Flow 8 — Unsplash+ Subscription context and can access target screen/endpoint. | keyword: mountain, email: user90@example.com, password: Pass@1234, photo_id: photo-090, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can view and download their invoices from the billing settings page |

#### 🔴 Negative

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-083 | BR-083 - Only active Unsplash+ subscribers can download premium (locked) photos w... | Negative | P2 - High | BR-083 | User/API client is in Flow 8 — Unsplash+ Subscription context and can access target screen/endpoint. | keyword: mountain, email: user83@example.com, password: Pass@1234, photo_id: photo-083, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Only active Unsplash+ subscribers can download premium (locked) photos without watermark |
| TC-084 | BR-084 - A non-subscriber clicking a locked photo is redirected to the Unsplash+ ... | Negative | P2 - High | BR-084 | User/API client is in Flow 8 — Unsplash+ Subscription context and can access target screen/endpoint. | keyword: mountain, email: user84@example.com, password: Pass@1234, photo_id: photo-084, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | A non-subscriber clicking a locked photo is redirected to the Unsplash+ subscription page |
| TC-087 | BR-087 - Unsplash+ photos cannot be downloaded after subscription expires — acces... | Negative | P2 - High | BR-087 | User/API client is in Flow 8 — Unsplash+ Subscription context and can access target screen/endpoint. | keyword: mountain, email: user87@example.com, password: Pass@1234, photo_id: photo-087, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Unsplash+ photos cannot be downloaded after subscription expires — access reverts to free content only |

### Flow 9 — Visual Search

#### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-091 | BR-091 - Visual Search is available to all users (authenticated and unauthenticat... | Happy Path | P1 - Critical | BR-091 | User/API client is in Flow 9 — Visual Search context and can access target screen/endpoint. | keyword: mountain, email: user91@example.com, password: Pass@1234, photo_id: photo-091, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Visual Search is available to all users (authenticated and unauthenticated) |
| TC-092 | BR-092 - Users can initiate Visual Search by uploading an image (JPEG, PNG) or by... | Happy Path | P1 - Critical | BR-092 | User/API client is in Flow 9 — Visual Search context and can access target screen/endpoint. | keyword: mountain, email: user92@example.com, password: Pass@1234, photo_id: photo-092, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Users can initiate Visual Search by uploading an image (JPEG, PNG) or by entering a public image URL |
| TC-095 | BR-095 - Visual Search results can be further refined by keyword after the initia... | Happy Path | P1 - Critical | BR-095 | User/API client is in Flow 9 — Visual Search context and can access target screen/endpoint. | keyword: mountain, email: user95@example.com, password: Pass@1234, photo_id: photo-095, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Visual Search results can be further refined by keyword after the initial image-based search |
| TC-096 | BR-096 - Visual Search is powered by an AI/ML image similarity engine — results a... | Happy Path | P1 - Critical | BR-096 | User/API client is in Flow 9 — Visual Search context and can access target screen/endpoint. | keyword: mountain, email: user96@example.com, password: Pass@1234, photo_id: photo-096, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Visual Search is powered by an AI/ML image similarity engine — results are ranked by visual similarity score |
| TC-097 | BR-097 - If no visually similar photos are found, the system displays: "No simila... | Happy Path | P1 - Critical | BR-097 | User/API client is in Flow 9 — Visual Search context and can access target screen/endpoint. | keyword: mountain, email: user97@example.com, password: Pass@1234, photo_id: photo-097, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | If no visually similar photos are found, the system displays: "No similar photos found. Try a different image." |

#### 🟡 Edge Cases

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-093 | BR-093 - Uploaded images for Visual Search must be at most 20 MB | Edge Case | P2 - High | BR-093 | User/API client is in Flow 9 — Visual Search context and can access target screen/endpoint. | keyword: mountain, email: user93@example.com, password: Pass@1234, photo_id: photo-093, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Uploaded images for Visual Search must be at most 20 MB |
| TC-094 | BR-094 - Visual Search returns the top 20 most visually similar photos from the U... | Edge Case | P2 - High | BR-094 | User/API client is in Flow 9 — Visual Search context and can access target screen/endpoint. | keyword: mountain, email: user94@example.com, password: Pass@1234, photo_id: photo-094, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Visual Search returns the top 20 most visually similar photos from the Unsplash library |

### Flow 10 — API Access

#### 🟢 Happy Path

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-098 | BR-098 - To use the API, developers must register a free Unsplash developer accou... | Happy Path | P1 - Critical | BR-098 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user98@example.com, password: Pass@1234, photo_id: photo-098, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | To use the API, developers must register a free Unsplash developer account |
| TC-100 | BR-100 - Production API access requires an application review and approval by the... | Happy Path | P1 - Critical | BR-100 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user100@example.com, password: Pass@1234, photo_id: photo-100, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Production API access requires an application review and approval by the Unsplash team |
| TC-103 | BR-103 - API calls must include a valid `Authorization: Client-ID {ACCESS_KEY}` h... | Happy Path | P1 - Critical | BR-103 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user103@example.com, password: Pass@1234, photo_id: photo-103, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | API calls must include a valid `Authorization: Client-ID {ACCESS_KEY}` header |
| TC-106 | BR-106 - API applications must display attribution ("Photo by [Photographer Name]... | Happy Path | P1 - Critical | BR-106 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user106@example.com, password: Pass@1234, photo_id: photo-106, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | API applications must display attribution ("Photo by [Photographer Name] on Unsplash") for each photo used |
| TC-107 | BR-107 - API applications must call the Unsplash download endpoint to trigger a d... | Happy Path | P1 - Critical | BR-107 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user107@example.com, password: Pass@1234, photo_id: photo-107, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | API applications must call the Unsplash download endpoint to trigger a download event when a user downloads/uses a photo |

#### 🔴 Negative

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-102 | BR-102 - API responses for list endpoints return 10 items per page by default; ma... | Negative | P2 - High | BR-102 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user102@example.com, password: Pass@1234, photo_id: photo-102, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20 | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | API responses for list endpoints return 10 items per page by default; max 30 items per page |

#### 🔒 Security

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-099 | BR-099 - Each app starts in Demo mode with a rate limit of 50 requests per hour | Security | P1 - Critical | BR-099 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user99@example.com, password: Pass@1234, photo_id: photo-099, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20, payload: ' OR 1=1 -- | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Each app starts in Demo mode with a rate limit of 50 requests per hour |
| TC-101 | BR-101 - Production rate limit: up to 5,000 requests per hour | Security | P1 - Critical | BR-101 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user101@example.com, password: Pass@1234, photo_id: photo-101, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20, payload: ' OR 1=1 -- | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Production rate limit: up to 5,000 requests per hour |
| TC-104 | BR-104 - Unauthenticated API calls return HTTP 401 Unauthorized | Security | P1 - Critical | BR-104 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user104@example.com, password: Pass@1234, photo_id: photo-104, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20, payload: ' OR 1=1 -- | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Unauthenticated API calls return HTTP 401 Unauthorized |
| TC-105 | BR-105 - Rate-limited API calls return HTTP 429 Too Many Requests with a `X-Ratel... | Security | P1 - Critical | BR-105 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user105@example.com, password: Pass@1234, photo_id: photo-105, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20, payload: ' OR 1=1 -- | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Rate-limited API calls return HTTP 429 Too Many Requests with a `X-Ratelimit-Remaining: 0` header |
| TC-108 | BR-108 - Applications violating API terms may have their API keys revoked without... | Security | P1 - Critical | BR-108 | User/API client is in Flow 10 — API Access context and can access target screen/endpoint. | keyword: mountain, email: user108@example.com, password: Pass@1234, photo_id: photo-108, api_key: demo_key_ABC123XYZ, page: 1, per_page: 20, payload: ' OR 1=1 -- | 1. Navigate to the exact screen/endpoint for this rule. 2. Submit the listed test data. 3. Observe returned UI/API status and side effects (counter/email/notification/log). | Applications violating API terms may have their API keys revoked without notice |

## Traceability Matrix

| Rule ID | Covered By | Status |
|---|---|---|
| BR-001 | TC-001 | Covered |
| BR-002 | TC-002 | Covered |
| BR-003 | TC-003 | Covered |
| BR-004 | TC-004 | Covered |
| BR-005 | TC-005 | Covered |
| BR-006 | TC-006 | Covered |
| BR-007 | TC-007 | Covered |
| BR-008 | TC-008 | Covered |
| BR-009 | TC-009 | Covered |
| BR-010 | TC-010 | Covered |
| BR-011 | TC-011 | Covered |
| BR-012 | TC-012 | Covered |
| BR-013 | TC-013 | Covered |
| BR-014 | TC-014 | Covered |
| BR-015 | TC-015 | Covered |
| BR-016 | TC-016 | Covered |
| BR-017 | TC-017 | Covered |
| BR-018 | TC-018 | Covered |
| BR-019 | TC-019 | Covered |
| BR-020 | TC-020 | Covered |
| BR-021 | TC-021 | Covered |
| BR-022 | TC-022 | Covered |
| BR-023 | TC-023 | Covered |
| BR-024 | TC-024 | Covered |
| BR-025 | TC-025 | Covered |
| BR-026 | TC-026 | Covered |
| BR-027 | TC-027 | Covered |
| BR-028 | TC-028 | Covered |
| BR-029 | TC-029 | Covered |
| BR-030 | TC-030 | Covered |
| BR-031 | TC-031 | Covered |
| BR-032 | TC-032 | Covered |
| BR-033 | TC-033 | Covered |
| BR-034 | TC-034 | Covered |
| BR-035 | TC-035 | Covered |
| BR-036 | TC-036 | Covered |
| BR-037 | TC-037 | Covered |
| BR-038 | TC-038 | Covered |
| BR-039 | TC-039 | Covered |
| BR-040 | TC-040 | Covered |
| BR-041 | TC-041 | Covered |
| BR-042 | TC-042 | Covered |
| BR-043 | TC-043 | Covered |
| BR-044 | TC-044 | Covered |
| BR-045 | TC-045 | Covered |
| BR-046 | TC-046 | Covered |
| BR-047 | TC-047 | Covered |
| BR-048 | TC-048 | Covered |
| BR-049 | TC-049 | Covered |
| BR-050 | TC-050 | Covered |
| BR-051 | TC-051 | Covered |
| BR-052 | TC-052 | Covered |
| BR-053 | TC-053 | Covered |
| BR-054 | TC-054 | Covered |
| BR-055 | TC-055 | Covered |
| BR-056 | TC-056 | Covered |
| BR-057 | TC-057 | Covered |
| BR-058 | TC-058 | Covered |
| BR-059 | TC-059 | Covered |
| BR-060 | TC-060 | Covered |
| BR-061 | TC-061 | Covered |
| BR-062 | TC-062 | Covered |
| BR-063 | TC-063 | Covered |
| BR-064 | TC-064 | Covered |
| BR-065 | TC-065 | Covered |
| BR-066 | TC-066 | Covered |
| BR-067 | TC-067 | Covered |
| BR-068 | TC-068 | Covered |
| BR-069 | TC-069 | Covered |
| BR-070 | TC-070 | Covered |
| BR-071 | TC-071 | Covered |
| BR-072 | TC-072 | Covered |
| BR-073 | TC-073 | Covered |
| BR-074 | TC-074 | Covered |
| BR-075 | TC-075 | Covered |
| BR-076 | TC-076 | Covered |
| BR-077 | TC-077 | Covered |
| BR-078 | TC-078 | Covered |
| BR-079 | TC-079 | Covered |
| BR-080 | TC-080 | Covered |
| BR-081 | TC-081 | Covered |
| BR-082 | TC-082 | Covered |
| BR-083 | TC-083 | Covered |
| BR-084 | TC-084 | Covered |
| BR-085 | TC-085 | Covered |
| BR-086 | TC-086 | Covered |
| BR-087 | TC-087 | Covered |
| BR-088 | TC-088 | Covered |
| BR-089 | TC-089 | Covered |
| BR-090 | TC-090 | Covered |
| BR-091 | TC-091 | Covered |
| BR-092 | TC-092 | Covered |
| BR-093 | TC-093 | Covered |
| BR-094 | TC-094 | Covered |
| BR-095 | TC-095 | Covered |
| BR-096 | TC-096 | Covered |
| BR-097 | TC-097 | Covered |
| BR-098 | TC-098 | Covered |
| BR-099 | TC-099 | Covered |
| BR-100 | TC-100 | Covered |
| BR-101 | TC-101 | Covered |
| BR-102 | TC-102 | Covered |
| BR-103 | TC-103 | Covered |
| BR-104 | TC-104 | Covered |
| BR-105 | TC-105 | Covered |
| BR-106 | TC-106 | Covered |
| BR-107 | TC-107 | Covered |
| BR-108 | TC-108 | Covered |

## Coverage Summary

| Type | Count |
|---|---|
| Happy Path | 72 |
| Negative | 23 |
| Edge Case | 7 |
| Security | 6 |
| **Total** | **108** |

Coverage: 108/108 rules covered (100%).

## Test Execution Report

- Feature: Unsplash.com Core Features
- Tester: ___________
- Date: ___________
- Environment: ___________
- Build/Version: ___________

| Total TCs | Pass | Fail | Blocked | Not Run |
|---|---|---|---|---|
| | | | | |