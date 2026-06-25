# Requirements Traceability Matrix

| Field | Value |
|-------|-------|
| **Project** | NovaCart E-Commerce Platform |
| **Document ID** | RTM-NC-001 |
| **Version** | 1.0 |
| **Author** | QA Team |
| **Date** | 2026-06-25 |
| **Status** | Active |

---

## Purpose

This matrix maps business requirements to test cases and defect records, ensuring full coverage and auditability across the NovaCart release cycle.

---

## Traceability Matrix

| Req ID | Requirement Description | Priority | Test Case ID | Test Type | Execution Status | Defect ID | Notes |
|--------|-------------------------|----------|--------------|-----------|------------------|-----------|-------|
| REQ-AUTH-001 | User shall authenticate with valid credentials | P1 | TC-AUTH-001 | Functional | Pass | — | Automated in CI |
| REQ-AUTH-002 | System shall reject invalid credentials | P1 | TC-AUTH-002 | Functional | Pass | — | |
| REQ-AUTH-003 | Locked accounts shall be denied access | P2 | TC-AUTH-003 | Functional | Pass | — | |
| REQ-AUTH-004 | Login form shall validate required fields | P2 | TC-AUTH-004 | Functional | Pass | — | |
| REQ-AUTH-005 | Session shall expire after 15 min inactivity | P2 | TC-AUTH-005 | Functional | Not Run | — | Pending env config |
| REQ-CAT-001 | User shall view product listing with images and prices | P1 | TC-CAT-001 | Functional | Pass | — | |
| REQ-CAT-002 | User shall sort products by price and name | P2 | TC-CAT-003 | Functional | Pass | — | |
| REQ-CHK-001 | User shall add items to cart from product page | P1 | TC-CHK-001 | Functional | Pass | — | |
| REQ-CHK-002 | User shall update item quantity in cart | P1 | TC-CHK-005 | Functional | Pass | — | |
| REQ-CHK-003 | User shall remove items from cart | P2 | TC-CHK-006 | Functional | Pass | — | |
| REQ-CHK-010 | Checkout shall collect valid shipping address | P1 | TC-CHK-010 | Functional | Pass | — | |
| REQ-CHK-012 | Order summary shall display itemized costs | P1 | TC-CHK-012 | Functional | Pass | — | |
| REQ-CHK-018 | Tax shall be calculated per line item by category | P1 | TC-CHK-014 | Functional | Fail | BUG-0042 | High severity |
| REQ-CHK-020 | User shall receive order confirmation on success | P1 | TC-CHK-020 | Functional | Pass | — | |
| REQ-API-001 | GET /users/{id} shall return user profile | P1 | API-USER-001 | API | Pass | — | |
| REQ-API-002 | POST /orders shall create order with 201 status | P1 | API-ORD-001 | API | Pass | — | |
| REQ-API-003 | Invalid auth token shall return 401 | P1 | API-AUTH-002 | API | Pass | — | |
| REQ-API-004 | Order payload validation shall return 400 | P2 | API-ORD-003 | API | Pass | — | |

---

## Coverage Summary

| Metric | Value |
|--------|-------|
| Total Requirements | 18 |
| Requirements with Test Cases | 18 |
| Coverage | 100% |
| Test Cases Executed | 17 |
| Test Cases Passed | 16 |
| Test Cases Failed | 1 |
| Open Defects (linked) | 1 |

---

## Requirement Status Legend

| Status | Definition |
|--------|------------|
| Pass | All linked test cases passed |
| Fail | One or more linked test cases failed |
| Not Run | Test cases not yet executed |
| Blocked | Testing blocked by environment or dependency |
| N/A | Requirement deferred or out of current release scope |

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-06-25 | QA Team | Initial baseline for Sprint 12 release |
