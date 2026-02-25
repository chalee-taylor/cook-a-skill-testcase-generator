# Test Cases — Unsplash.com Core Features

Generated from `SPEC_UNSPLASH.md` on 2026-02-25 using `SKILL.md` structure.

| ID | Title | Type | Priority | Rule Ref | Precondition | Test Data | Steps | Expected Result |
|---|---|---|---|---|---|---|---|---|
| TC-001 | Validate BR-001 | Happy Path | P1 - Critical | BR-001 | User is on the relevant Search & Discovery page/flow. | sample_user: user1@example.com; sample_value: case-1 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | The search bar is accessible on all pages (header navigation) — authenticated and unauthenticated users |
| TC-002 | Validate BR-002 | Happy Path | P1 - Critical | BR-002 | User is on the relevant Search & Discovery page/flow. | sample_user: user2@example.com; sample_value: case-2 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Search results are filtered into 3 tabs: Photos, Collections, Users |
| TC-003 | Validate BR-003 | Happy Path | P1 - Critical | BR-003 | User is on the relevant Search & Discovery page/flow. | sample_user: user3@example.com; sample_value: case-3 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Each search result page displays a set of relevant tag suggestions at the top to guide users toward related searches |
| TC-004 | Validate BR-004 | Edge Case | P2 - High | BR-004 | User is on the relevant Search & Discovery page/flow. | sample_user: user4@example.com; sample_value: case-4 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | The homepage features an infinite-scroll photo grid — new photos load automatically when the user scrolls to the bottom |
| TC-005 | Validate BR-005 | Edge Case | P2 - High | BR-005 | User is on the relevant Search & Discovery page/flow. | sample_user: user5@example.com; sample_value: case-5 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Search results must return at most 20 photos per page by default; pagination is supported |
| TC-006 | Validate BR-006 | Happy Path | P1 - Critical | BR-006 | User is on the relevant Search & Discovery page/flow. | sample_user: user6@example.com; sample_value: case-6 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | If the search returns 0 results, the system must display an empty-state message: "We couldn't find anything for [keyword]" along with suggested alternative search terms |
| TC-007 | Validate BR-007 | Happy Path | P1 - Critical | BR-007 | User is on the relevant Search & Discovery page/flow. | sample_user: user7@example.com; sample_value: case-7 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Trending/popular searches are displayed below the search bar on the homepage to assist discovery |
| TC-008 | Validate BR-008 | Happy Path | P1 - Critical | BR-008 | User is on the relevant Search & Discovery page/flow. | sample_user: user8@example.com; sample_value: case-8 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Category navigation links (e.g., "Nature", "Travel", "Architecture") are available in the header and filter the photo grid by category |
| TC-009 | Validate BR-009 | Happy Path | P1 - Critical | BR-009 | User is on the relevant Search & Discovery page/flow. | sample_user: user9@example.com; sample_value: case-9 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can sort search results by: Relevance (default) or Latest |
| TC-010 | Validate BR-010 | Negative | P2 - High | BR-010 | User is on the relevant Search & Discovery page/flow. | sample_user: user10@example.com; sample_value: case-10 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Search keyword must be between 1 and 200 characters |
| TC-011 | Validate BR-011 | Happy Path | P1 - Critical | BR-011 | User is on the relevant Download page/flow. | sample_user: user11@example.com; sample_value: case-11 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Guest users (unauthenticated) can download free photos without an account |
| TC-012 | Validate BR-012 | Happy Path | P1 - Critical | BR-012 | User is on the relevant Download page/flow. | sample_user: user12@example.com; sample_value: case-12 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Free photo downloads do not require attribution (but attribution to photographer is appreciated) |
| TC-013 | Validate BR-013 | Happy Path | P1 - Critical | BR-013 | User is on the relevant Download page/flow. | sample_user: user13@example.com; sample_value: case-13 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Download button is labeled "Download free" for free photos and shows a lock icon for Unsplash+ premium photos |
| TC-014 | Validate BR-014 | Happy Path | P1 - Critical | BR-014 | User is on the relevant Download page/flow. | sample_user: user14@example.com; sample_value: case-14 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can select download size: Small, Medium, Large, or Original (for free photos) |
| TC-015 | Validate BR-015 | Happy Path | P1 - Critical | BR-015 | User is on the relevant Download page/flow. | sample_user: user15@example.com; sample_value: case-15 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Unsplash+ photos require an active Unsplash+ subscription to download without watermark |
| TC-016 | Validate BR-016 | Happy Path | P1 - Critical | BR-016 | User is on the relevant Download page/flow. | sample_user: user16@example.com; sample_value: case-16 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Downloading a photo triggers a download count increment on the photo's stats |
| TC-017 | Validate BR-017 | Happy Path | P1 - Critical | BR-017 | User is on the relevant Download page/flow. | sample_user: user17@example.com; sample_value: case-17 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Downloaded photos are provided in JPEG format at the selected resolution |
| TC-018 | Validate BR-018 | Happy Path | P1 - Critical | BR-018 | User is on the relevant Download page/flow. | sample_user: user18@example.com; sample_value: case-18 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | The platform tracks download events for analytics (no user account linkage for guest downloads) |
| TC-019 | Validate BR-019 | Negative | P2 - High | BR-019 | User is on the relevant Download page/flow. | sample_user: user19@example.com; sample_value: case-19 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users cannot resell downloaded photos as-is on competing stock photo platforms |
| TC-020 | Validate BR-020 | Negative | P2 - High | BR-020 | User is on the relevant Download page/flow. | sample_user: user20@example.com; sample_value: case-20 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users cannot redistribute downloaded photos as part of a competing stock photo service |
| TC-021 | Validate BR-021 | Happy Path | P1 - Critical | BR-021 | User is on the relevant Registration & Login page/flow. | sample_user: user21@example.com; sample_value: case-21 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Email must be a valid format (RFC 5321 compliant) |
| TC-022 | Validate BR-022 | Happy Path | P1 - Critical | BR-022 | User is on the relevant Registration & Login page/flow. | sample_user: user22@example.com; sample_value: case-22 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Password must be at least 8 characters long |
| TC-023 | Validate BR-023 | Happy Path | P1 - Critical | BR-023 | User is on the relevant Registration & Login page/flow. | sample_user: user23@example.com; sample_value: case-23 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Password must contain at least one uppercase letter, one lowercase letter, and one number |
| TC-024 | Validate BR-024 | Happy Path | P1 - Critical | BR-024 | User is on the relevant Registration & Login page/flow. | sample_user: user24@example.com; sample_value: case-24 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Email address must be unique — no two accounts can share the same email |
| TC-025 | Validate BR-025 | Happy Path | P1 - Critical | BR-025 | User is on the relevant Registration & Login page/flow. | sample_user: user25@example.com; sample_value: case-25 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Username must be unique across the platform (first-come, first-served basis) |
| TC-026 | Validate BR-026 | Negative | P2 - High | BR-026 | User is on the relevant Registration & Login page/flow. | sample_user: user26@example.com; sample_value: case-26 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Username must be between 3 and 30 characters |
| TC-027 | Validate BR-027 | Happy Path | P1 - Critical | BR-027 | User is on the relevant Registration & Login page/flow. | sample_user: user27@example.com; sample_value: case-27 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Username can only contain letters, numbers, and underscores — no spaces, special characters, or URLs |
| TC-028 | Validate BR-028 | Negative | P2 - High | BR-028 | User is on the relevant Registration & Login page/flow. | sample_user: user28@example.com; sample_value: case-28 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Username cannot be a trademarked brand name |
| TC-029 | Validate BR-029 | Negative | P2 - High | BR-029 | User is on the relevant Registration & Login page/flow. | sample_user: user29@example.com; sample_value: case-29 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Username cannot impersonate another person or public figure |
| TC-030 | Validate BR-030 | Negative | P2 - High | BR-030 | User is on the relevant Registration & Login page/flow. | sample_user: user30@example.com; sample_value: case-30 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | After 5 consecutive failed login attempts, the account is temporarily locked for 15 minutes |
| TC-031 | Validate BR-031 | Happy Path | P1 - Critical | BR-031 | User is on the relevant Registration & Login page/flow. | sample_user: user31@example.com; sample_value: case-31 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can sign up/login via Google OAuth or Facebook OAuth as alternative methods |
| TC-032 | Validate BR-032 | Happy Path | P1 - Critical | BR-032 | User is on the relevant Registration & Login page/flow. | sample_user: user32@example.com; sample_value: case-32 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Upon successful registration, the system sends a confirmation email to the registered address |
| TC-033 | Validate BR-033 | Security | P1 - Critical | BR-033 | User is on the relevant Registration & Login page/flow. | sample_user: user33@example.com; sample_value: case-33 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | The system must not reveal whether an email address is registered when returning login error messages (anti-enumeration) |
| TC-034 | Validate BR-034 | Negative | P2 - High | BR-034 | User is on the relevant Registration & Login page/flow. | sample_user: user34@example.com; sample_value: case-34 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Login error message must be generic: "Invalid email or password" |
| TC-035 | Validate BR-035 | Happy Path | P1 - Critical | BR-035 | User is on the relevant Registration & Login page/flow. | sample_user: user35@example.com; sample_value: case-35 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users must agree to Terms of Service and Privacy Policy before completing registration |
| TC-036 | Validate BR-036 | Happy Path | P1 - Critical | BR-036 | User is on the relevant Upload page/flow. | sample_user: user36@example.com; sample_value: case-36 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Only registered (authenticated) users can upload photos |
| TC-037 | Validate BR-037 | Negative | P2 - High | BR-037 | User is on the relevant Upload page/flow. | sample_user: user37@example.com; sample_value: case-37 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Uploaded photos must have a minimum resolution of 5 megapixels (e.g., 2500 × 2000 pixels minimum) |
| TC-038 | Validate BR-038 | Happy Path | P1 - Critical | BR-038 | User is on the relevant Upload page/flow. | sample_user: user38@example.com; sample_value: case-38 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Accepted file formats: JPEG and PNG only |
| TC-039 | Validate BR-039 | Negative | P2 - High | BR-039 | User is on the relevant Upload page/flow. | sample_user: user39@example.com; sample_value: case-39 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Maximum file size per upload: 50 MB |
| TC-040 | Validate BR-040 | Negative | P2 - High | BR-040 | User is on the relevant Upload page/flow. | sample_user: user40@example.com; sample_value: case-40 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can upload up to 10 photos per day (daily limit for non-verified accounts) |
| TC-041 | Validate BR-041 | Happy Path | P1 - Critical | BR-041 | User is on the relevant Upload page/flow. | sample_user: user41@example.com; sample_value: case-41 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | By uploading, contributors grant Unsplash and users a royalty-free, irrevocable license to use the photo |
| TC-042 | Validate BR-042 | Happy Path | P1 - Critical | BR-042 | User is on the relevant Upload page/flow. | sample_user: user42@example.com; sample_value: case-42 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Contributors must own the rights to the uploaded image or have permission from the rights holder |
| TC-043 | Validate BR-043 | Happy Path | P1 - Critical | BR-043 | User is on the relevant Upload page/flow. | sample_user: user43@example.com; sample_value: case-43 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Photos must not contain: nudity, violence, hate content, personally identifiable information (PII) of individuals without consent, copyrighted logos or trademarked brand elements |
| TC-044 | Validate BR-044 | Happy Path | P1 - Critical | BR-044 | User is on the relevant Upload page/flow. | sample_user: user44@example.com; sample_value: case-44 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Photos depicting identifiable people in editorial or commercial contexts require a valid model release |
| TC-045 | Validate BR-045 | Negative | P2 - High | BR-045 | User is on the relevant Upload page/flow. | sample_user: user45@example.com; sample_value: case-45 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Submitted photos are subject to review — non-compliant photos are rejected with an explanatory email to the contributor |
| TC-046 | Validate BR-046 | Happy Path | P1 - Critical | BR-046 | User is on the relevant Upload page/flow. | sample_user: user46@example.com; sample_value: case-46 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Upon successful upload, the photo appears on the contributor's profile with status "Under Review" until approved |
| TC-047 | Validate BR-047 | Happy Path | P1 - Critical | BR-047 | User is on the relevant Upload page/flow. | sample_user: user47@example.com; sample_value: case-47 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Contributors can add a description, alt text, and location to their uploaded photos |
| TC-048 | Validate BR-048 | Edge Case | P2 - High | BR-048 | User is on the relevant Upload page/flow. | sample_user: user48@example.com; sample_value: case-48 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Contributors can add up to 30 tags per photo for discoverability |
| TC-049 | Validate BR-049 | Happy Path | P1 - Critical | BR-049 | User is on the relevant Collections page/flow. | sample_user: user49@example.com; sample_value: case-49 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Only authenticated users can create collections |
| TC-050 | Validate BR-050 | Negative | P2 - High | BR-050 | User is on the relevant Collections page/flow. | sample_user: user50@example.com; sample_value: case-50 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | A user can create an unlimited number of collections |
| TC-051 | Validate BR-051 | Negative | P2 - High | BR-051 | User is on the relevant Collections page/flow. | sample_user: user51@example.com; sample_value: case-51 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Collection names must be between 1 and 60 characters |
| TC-052 | Validate BR-052 | Negative | P2 - High | BR-052 | User is on the relevant Collections page/flow. | sample_user: user52@example.com; sample_value: case-52 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Collections can be set as Public (visible to all) or Private (visible only to the owner) |
| TC-053 | Validate BR-053 | Happy Path | P1 - Critical | BR-053 | User is on the relevant Collections page/flow. | sample_user: user53@example.com; sample_value: case-53 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can add any photo (free or Unsplash+) to their collections — adding a premium photo does not require a subscription |
| TC-054 | Validate BR-054 | Negative | P2 - High | BR-054 | User is on the relevant Collections page/flow. | sample_user: user54@example.com; sample_value: case-54 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | A user cannot add the same photo to the same collection twice (duplicate prevention) |
| TC-055 | Validate BR-055 | Happy Path | P1 - Critical | BR-055 | User is on the relevant Collections page/flow. | sample_user: user55@example.com; sample_value: case-55 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | The photo contributor receives a notification when their photo is added to another user's collection |
| TC-056 | Validate BR-056 | Happy Path | P1 - Critical | BR-056 | User is on the relevant Collections page/flow. | sample_user: user56@example.com; sample_value: case-56 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Collections containing offensive content are removed by admins immediately, and an email is sent to the collection creator |
| TC-057 | Validate BR-057 | Happy Path | P1 - Critical | BR-057 | User is on the relevant Collections page/flow. | sample_user: user57@example.com; sample_value: case-57 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can delete their collections — deleting a collection does not delete the photos |
| TC-058 | Validate BR-058 | Happy Path | P1 - Critical | BR-058 | User is on the relevant Collections page/flow. | sample_user: user58@example.com; sample_value: case-58 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can reorder photos within a collection |
| TC-059 | Validate BR-059 | Happy Path | P1 - Critical | BR-059 | User is on the relevant Collections page/flow. | sample_user: user59@example.com; sample_value: case-59 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | A collection displays a cover photo (by default: the first photo added; user can change this) |
| TC-060 | Validate BR-060 | Happy Path | P1 - Critical | BR-060 | User is on the relevant Collections page/flow. | sample_user: user60@example.com; sample_value: case-60 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Other users can follow public collections to receive updates |
| TC-061 | Validate BR-061 | Happy Path | P1 - Critical | BR-061 | User is on the relevant Like/Save page/flow. | sample_user: user61@example.com; sample_value: case-61 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Only authenticated users can like a photo |
| TC-062 | Validate BR-062 | Happy Path | P1 - Critical | BR-062 | User is on the relevant Like/Save page/flow. | sample_user: user62@example.com; sample_value: case-62 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | A user can like any photo (free or Unsplash+) without a subscription |
| TC-063 | Validate BR-063 | Happy Path | P1 - Critical | BR-063 | User is on the relevant Like/Save page/flow. | sample_user: user63@example.com; sample_value: case-63 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | A user can only like a photo once — the like button toggles (click again to unlike) |
| TC-064 | Validate BR-064 | Happy Path | P1 - Critical | BR-064 | User is on the relevant Like/Save page/flow. | sample_user: user64@example.com; sample_value: case-64 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | The photo contributor receives a notification when their photo is liked |
| TC-065 | Validate BR-065 | Happy Path | P1 - Critical | BR-065 | User is on the relevant Like/Save page/flow. | sample_user: user65@example.com; sample_value: case-65 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | A user's liked photos are visible on their profile under the "Likes" tab (public by default) |
| TC-066 | Validate BR-066 | Happy Path | P1 - Critical | BR-066 | User is on the relevant Like/Save page/flow. | sample_user: user66@example.com; sample_value: case-66 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | The like count on each photo is displayed publicly |
| TC-067 | Validate BR-067 | Happy Path | P1 - Critical | BR-067 | User is on the relevant Like/Save page/flow. | sample_user: user67@example.com; sample_value: case-67 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Unlike does not notify the contributor |
| TC-068 | Validate BR-068 | Happy Path | P1 - Critical | BR-068 | User is on the relevant Profile page/flow. | sample_user: user68@example.com; sample_value: case-68 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Profile URL format: https://unsplash.com/@{username} |
| TC-069 | Validate BR-069 | Happy Path | P1 - Critical | BR-069 | User is on the relevant Profile page/flow. | sample_user: user69@example.com; sample_value: case-69 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Profile page is publicly visible (no login required to view) |
| TC-070 | Validate BR-070 | Happy Path | P1 - Critical | BR-070 | User is on the relevant Profile page/flow. | sample_user: user70@example.com; sample_value: case-70 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Profile displays: avatar, name, bio, location, website, social links, followers/following count |
| TC-071 | Validate BR-071 | Happy Path | P1 - Critical | BR-071 | User is on the relevant Profile page/flow. | sample_user: user71@example.com; sample_value: case-71 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Profile tabs: Photos, Likes, Collections |
| TC-072 | Validate BR-072 | Happy Path | P1 - Critical | BR-072 | User is on the relevant Profile page/flow. | sample_user: user72@example.com; sample_value: case-72 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can edit: name, username, bio, location, website, portfolio URL, social links (Twitter/Instagram) |
| TC-073 | Validate BR-073 | Negative | P2 - High | BR-073 | User is on the relevant Profile page/flow. | sample_user: user73@example.com; sample_value: case-73 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Username changes are allowed but limited to once per 30 days |
| TC-074 | Validate BR-074 | Negative | P2 - High | BR-074 | User is on the relevant Profile page/flow. | sample_user: user74@example.com; sample_value: case-74 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Bio max length: 200 characters |
| TC-075 | Validate BR-075 | Happy Path | P1 - Critical | BR-075 | User is on the relevant Profile page/flow. | sample_user: user75@example.com; sample_value: case-75 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Website URL must be a valid URL format (starting with http:// or https://) |
| TC-076 | Validate BR-076 | Negative | P2 - High | BR-076 | User is on the relevant Profile page/flow. | sample_user: user76@example.com; sample_value: case-76 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can upload an avatar image (JPEG or PNG, max 5 MB, minimum 200×200 px) |
| TC-077 | Validate BR-077 | Happy Path | P1 - Critical | BR-077 | User is on the relevant Profile page/flow. | sample_user: user77@example.com; sample_value: case-77 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Profile stats are visible: total photos uploaded, total downloads received, total views received |
| TC-078 | Validate BR-078 | Happy Path | P1 - Critical | BR-078 | User is on the relevant Profile page/flow. | sample_user: user78@example.com; sample_value: case-78 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Admins can suspend or deactivate accounts violating community guidelines |
| TC-079 | Validate BR-079 | Edge Case | P2 - High | BR-079 | User is on the relevant Profile page/flow. | sample_user: user79@example.com; sample_value: case-79 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Inactive accounts with 0 photos may have their username reclaimed after 12 months of inactivity |
| TC-080 | Validate BR-080 | Edge Case | P2 - High | BR-080 | User is on the relevant Profile page/flow. | sample_user: user80@example.com; sample_value: case-80 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Inactive accounts with 1+ photos may have their username reclaimed after 24 months of inactivity |
| TC-081 | Validate BR-081 | Happy Path | P1 - Critical | BR-081 | User is on the relevant Unsplash+ page/flow. | sample_user: user81@example.com; sample_value: case-81 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Unsplash+ is a paid subscription with a monthly or annual billing option |
| TC-082 | Validate BR-082 | Happy Path | P1 - Critical | BR-082 | User is on the relevant Unsplash+ page/flow. | sample_user: user82@example.com; sample_value: case-82 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Unsplash+ photos are identified by a lock icon overlay on the thumbnail |
| TC-083 | Validate BR-083 | Negative | P2 - High | BR-083 | User is on the relevant Unsplash+ page/flow. | sample_user: user83@example.com; sample_value: case-83 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Only active Unsplash+ subscribers can download premium (locked) photos without watermark |
| TC-084 | Validate BR-084 | Negative | P2 - High | BR-084 | User is on the relevant Unsplash+ page/flow. | sample_user: user84@example.com; sample_value: case-84 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | A non-subscriber clicking a locked photo is redirected to the Unsplash+ subscription page |
| TC-085 | Validate BR-085 | Happy Path | P1 - Critical | BR-085 | User is on the relevant Unsplash+ page/flow. | sample_user: user85@example.com; sample_value: case-85 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Unsplash+ subscription is auto-renewed at the end of each billing cycle unless cancelled |
| TC-086 | Validate BR-086 | Happy Path | P1 - Critical | BR-086 | User is on the relevant Unsplash+ page/flow. | sample_user: user86@example.com; sample_value: case-86 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can cancel the Unsplash+ subscription at any time; access remains until the end of the current billing period |
| TC-087 | Validate BR-087 | Negative | P2 - High | BR-087 | User is on the relevant Unsplash+ page/flow. | sample_user: user87@example.com; sample_value: case-87 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Unsplash+ photos cannot be downloaded after subscription expires — access reverts to free content only |
| TC-088 | Validate BR-088 | Happy Path | P1 - Critical | BR-088 | User is on the relevant Unsplash+ page/flow. | sample_user: user88@example.com; sample_value: case-88 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Payment is processed securely via Stripe; Unsplash does not store raw card data |
| TC-089 | Validate BR-089 | Happy Path | P1 - Critical | BR-089 | User is on the relevant Unsplash+ page/flow. | sample_user: user89@example.com; sample_value: case-89 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Upon successful subscription activation, the user receives a confirmation email with billing details |
| TC-090 | Validate BR-090 | Happy Path | P1 - Critical | BR-090 | User is on the relevant Unsplash+ page/flow. | sample_user: user90@example.com; sample_value: case-90 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can view and download their invoices from the billing settings page |
| TC-091 | Validate BR-091 | Happy Path | P1 - Critical | BR-091 | User is on the relevant Visual Search page/flow. | sample_user: user91@example.com; sample_value: case-91 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Visual Search is available to all users (authenticated and unauthenticated) |
| TC-092 | Validate BR-092 | Happy Path | P1 - Critical | BR-092 | User is on the relevant Visual Search page/flow. | sample_user: user92@example.com; sample_value: case-92 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Users can initiate Visual Search by uploading an image (JPEG, PNG) or by entering a public image URL |
| TC-093 | Validate BR-093 | Edge Case | P2 - High | BR-093 | User is on the relevant Visual Search page/flow. | sample_user: user93@example.com; sample_value: case-93 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Uploaded images for Visual Search must be at most 20 MB |
| TC-094 | Validate BR-094 | Edge Case | P2 - High | BR-094 | User is on the relevant Visual Search page/flow. | sample_user: user94@example.com; sample_value: case-94 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Visual Search returns the top 20 most visually similar photos from the Unsplash library |
| TC-095 | Validate BR-095 | Happy Path | P1 - Critical | BR-095 | User is on the relevant Visual Search page/flow. | sample_user: user95@example.com; sample_value: case-95 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Visual Search results can be further refined by keyword after the initial image-based search |
| TC-096 | Validate BR-096 | Happy Path | P1 - Critical | BR-096 | User is on the relevant Visual Search page/flow. | sample_user: user96@example.com; sample_value: case-96 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Visual Search is powered by an AI/ML image similarity engine — results are ranked by visual similarity score |
| TC-097 | Validate BR-097 | Happy Path | P1 - Critical | BR-097 | User is on the relevant Visual Search page/flow. | sample_user: user97@example.com; sample_value: case-97 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | If no visually similar photos are found, the system displays: "No similar photos found. Try a different image." |
| TC-098 | Validate BR-098 | Happy Path | P1 - Critical | BR-098 | User is on the relevant API page/flow. | sample_user: user98@example.com; sample_value: case-98 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | To use the API, developers must register a free Unsplash developer account |
| TC-099 | Validate BR-099 | Security | P1 - Critical | BR-099 | User is on the relevant API page/flow. | sample_user: user99@example.com; sample_value: case-99 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Each app starts in Demo mode with a rate limit of 50 requests per hour |
| TC-100 | Validate BR-100 | Happy Path | P1 - Critical | BR-100 | User is on the relevant API page/flow. | sample_user: user100@example.com; sample_value: case-100 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Production API access requires an application review and approval by the Unsplash team |
| TC-101 | Validate BR-101 | Security | P1 - Critical | BR-101 | User is on the relevant API page/flow. | sample_user: user101@example.com; sample_value: case-101 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Production rate limit: up to 5,000 requests per hour |
| TC-102 | Validate BR-102 | Negative | P2 - High | BR-102 | User is on the relevant API page/flow. | sample_user: user102@example.com; sample_value: case-102 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | API responses for list endpoints return 10 items per page by default; max 30 items per page |
| TC-103 | Validate BR-103 | Happy Path | P1 - Critical | BR-103 | User is on the relevant API page/flow. | sample_user: user103@example.com; sample_value: case-103 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | API calls must include a valid Authorization: Client-ID {ACCESS_KEY} header |
| TC-104 | Validate BR-104 | Security | P1 - Critical | BR-104 | User is on the relevant API page/flow. | sample_user: user104@example.com; sample_value: case-104 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Unauthenticated API calls return HTTP 401 Unauthorized |
| TC-105 | Validate BR-105 | Security | P1 - Critical | BR-105 | User is on the relevant API page/flow. | sample_user: user105@example.com; sample_value: case-105 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Rate-limited API calls return HTTP 429 Too Many Requests with a X-Ratelimit-Remaining: 0 header |
| TC-106 | Validate BR-106 | Happy Path | P1 - Critical | BR-106 | User is on the relevant API page/flow. | sample_user: user106@example.com; sample_value: case-106 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | API applications must display attribution ("Photo by [Photographer Name] on Unsplash") for each photo used |
| TC-107 | Validate BR-107 | Happy Path | P1 - Critical | BR-107 | User is on the relevant API page/flow. | sample_user: user107@example.com; sample_value: case-107 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | API applications must call the Unsplash download endpoint to trigger a download event when a user downloads/uses a photo |
| TC-108 | Validate BR-108 | Security | P1 - Critical | BR-108 | User is on the relevant API page/flow. | sample_user: user108@example.com; sample_value: case-108 | 1. Open the associated feature flow. 2. Execute action tied to the rule. 3. Capture visible response or API status. | Applications violating API terms may have their API keys revoked without notice |

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