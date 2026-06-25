# Test Plan: NovaCart Checkout Module

| Field | Value |
|-------|-------|
| **Document ID** | TP-NC-CHK-001 |
| **Version** | 1.0 |
| **Author** | QA Team |
| **Date** | 2026-06-25 |
| **Status** | Approved |

---

## 1. Introduction

### 1.1 Purpose

This document defines the test approach, scope, resources, and schedule for validating the NovaCart checkout module. NovaCart is a B2C e-commerce web application modeled after industry-standard demo platforms used for QA training and portfolio demonstration.

### 1.2 Scope

**In Scope**

- Shopping cart review and item quantity updates
- Guest and registered user checkout flows
- Shipping address validation
- Payment method selection (credit card, PayPal)
- Order summary and confirmation
- Tax and shipping cost calculation

**Out of Scope**

- Product catalog browsing (covered in TP-NC-CAT-001)
- User registration and password reset
- Third-party payment gateway internals
- Mobile native applications

### 1.3 References

| Document | ID |
|----------|-----|
| Checkout Functional Specification | FS-NC-CHK-002 |
| Requirements Traceability Matrix | RTM-NC-001 |
| API Specification - Orders | API-NC-ORD-001 |

---

## 2. Test Strategy

### 2.1 Test Levels

| Level | Approach | Tools |
|-------|----------|-------|
| Functional | Manual and automated UI testing | Playwright, Manual |
| Integration | API contract validation | Postman, Newman |
| Regression | Automated smoke suite on each build | GitHub Actions, Playwright |
| Exploratory | Session-based testing for edge cases | Manual |

### 2.2 Test Types

- Positive and negative functional testing
- Boundary value analysis for quantity and pricing fields
- Cross-browser compatibility (Chrome, Firefox, Edge)
- Accessibility spot checks (WCAG 2.1 Level A)

### 2.3 Entry Criteria

- Checkout module deployed to staging environment
- Test data seeded (products, user accounts, payment stubs)
- Test cases reviewed and baselined
- Defect triage process confirmed with development team

### 2.4 Exit Criteria

- 100% of P1 and P2 test cases executed
- No open Critical or High severity defects
- Regression suite pass rate >= 95%
- RTM updated with execution status

---

## 3. Test Environment

| Component | Details |
|-----------|---------|
| Application URL | https://staging.novacart-demo.io |
| Browsers | Chrome 125+, Firefox 126+, Edge 125+ |
| Test Accounts | qa_user_01, qa_guest |
| API Base URL | https://api.staging.novacart-demo.io/v1 |

---

## 4. Test Schedule

| Phase | Activity | Duration |
|-------|----------|----------|
| Week 1 | Test case design and peer review | 3 days |
| Week 2 | Functional test execution | 4 days |
| Week 3 | Regression and defect retest | 3 days |
| Week 4 | Sign-off and report | 1 day |

---

## 5. Risks and Mitigations

| Risk | Impact | Mitigation |
|------|--------|------------|
| Payment sandbox instability | High | Maintain mock payment service fallback |
| Late requirement changes | Medium | Change control via RTM version updates |
| Limited staging data | Low | Automated seed scripts before each run |

---

## 6. Deliverables

- Executed test cases with evidence
- Defect reports logged in issue tracker
- Test summary report
- Updated Requirements Traceability Matrix

---

## 7. Approvals

| Role | Name | Signature | Date |
|------|------|-----------|------|
| QA Lead | | | |
| Project Manager | | | |
| Development Lead | | | |
