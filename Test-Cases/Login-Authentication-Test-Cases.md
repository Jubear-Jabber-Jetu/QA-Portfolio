# Test Cases: User Login and Authentication

| Field | Value |
|-------|-------|
| **Module** | Authentication |
| **Application** | NovaCart Demo Platform |
| **Version** | 1.0 |
| **Author** | QA Team |
| **Date** | 2026-06-25 |

---

## TC-AUTH-001: Successful login with valid credentials

| Attribute | Detail |
|-----------|--------|
| **Priority** | P1 |
| **Requirement** | REQ-AUTH-001 |
| **Preconditions** | User account `standard_user` exists and is active. Application is accessible at login page. |

**Test Steps**

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Navigate to `/login` | Login page displays username and password fields |
| 2 | Enter username `standard_user` | Username accepted in input field |
| 3 | Enter valid password | Password masked in input field |
| 4 | Click **Sign In** | User redirected to dashboard; session token issued |
| 5 | Verify header | Logged-in username displayed; logout option visible |

**Postconditions:** User session active. Cart state preserved if applicable.

---

## TC-AUTH-002: Login rejected with invalid password

| Attribute | Detail |
|-----------|--------|
| **Priority** | P1 |
| **Requirement** | REQ-AUTH-002 |
| **Preconditions** | Valid username exists. User is on login page. |

**Test Steps**

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Enter valid username | Field accepts input |
| 2 | Enter incorrect password | Field accepts input |
| 3 | Click **Sign In** | Login denied; error message displayed |
| 4 | Verify session | User remains on login page; no session created |

**Expected Error Message:** "Invalid username or password."

---

## TC-AUTH-003: Login blocked for locked account

| Attribute | Detail |
|-----------|--------|
| **Priority** | P2 |
| **Requirement** | REQ-AUTH-003 |
| **Preconditions** | Account `locked_out_user` exists with locked status. |

**Test Steps**

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Enter username `locked_out_user` | Field accepts input |
| 2 | Enter valid password for account | Field accepts input |
| 3 | Click **Sign In** | Access denied with account locked message |

**Expected Error Message:** "Account has been locked. Contact support."

---

## TC-AUTH-004: Empty field validation

| Attribute | Detail |
|-----------|--------|
| **Priority** | P2 |
| **Requirement** | REQ-AUTH-004 |
| **Preconditions** | User is on login page. |

**Test Steps**

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Leave username and password empty | Fields remain empty |
| 2 | Click **Sign In** | Client-side validation prevents submission |
| 3 | Verify messages | Required field indicators shown for both fields |

---

## TC-AUTH-005: Session timeout after inactivity

| Attribute | Detail |
|-----------|--------|
| **Priority** | P2 |
| **Requirement** | REQ-AUTH-005 |
| **Preconditions** | User logged in. Session timeout configured to 15 minutes. |

**Test Steps**

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Log in successfully | Dashboard displayed |
| 2 | Remain inactive for 15 minutes | No user interaction |
| 3 | Attempt to navigate to protected page | Session expired; redirect to login |
| 4 | Verify message | "Your session has expired. Please sign in again." |

---

## Test Execution Summary

| Test Case ID | Status | Executed By | Date | Build |
|--------------|--------|-------------|------|-------|
| TC-AUTH-001 | | | | |
| TC-AUTH-002 | | | | |
| TC-AUTH-003 | | | | |
| TC-AUTH-004 | | | | |
| TC-AUTH-005 | | | | |
