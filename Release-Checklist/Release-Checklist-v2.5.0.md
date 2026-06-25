# Release Checklist: NovaCart v2.5.0

| Field | Value |
|-------|-------|
| **Release** | v2.5.0 |
| **Release Date** | 2026-07-01 |
| **Release Manager** | |
| **QA Sign-off** | |
| **Document Version** | 1.0 |

---

## 1. Pre-Release Verification

### 1.1 Code and Build

| # | Item | Owner | Status | Notes |
|---|------|-------|--------|-------|
| 1.1.1 | All features merged to `release/2.5.0` branch | Dev Lead | [ ] | |
| 1.1.2 | Build pipeline green on release branch | DevOps | [ ] | |
| 1.1.3 | Version number updated in application config | Dev Lead | [ ] | Target: 2.5.0 |
| 1.1.4 | Release notes drafted and reviewed | PM | [ ] | |
| 1.1.5 | Database migration scripts reviewed and tested | DBA | [ ] | |

### 1.2 Quality Assurance

| # | Item | Owner | Status | Notes |
|---|------|-------|--------|-------|
| 1.2.1 | All P1 test cases executed and passed | QA Lead | [ ] | |
| 1.2.2 | All P2 test cases executed (pass or accepted waiver) | QA Lead | [ ] | |
| 1.2.3 | Regression suite pass rate >= 95% | QA Lead | [ ] | |
| 1.2.4 | No open Critical or High severity defects | QA Lead | [ ] | BUG-0042 must be resolved |
| 1.2.5 | RTM updated and signed off | QA Lead | [ ] | RTM-NC-001 v1.0 |
| 1.2.6 | API test scenarios executed in staging | QA | [ ] | |
| 1.2.7 | Cross-browser smoke test completed | QA | [ ] | Chrome, Firefox, Edge |
| 1.2.8 | Accessibility spot check completed | QA | [ ] | WCAG 2.1 Level A |

### 1.3 Security and Compliance

| # | Item | Owner | Status | Notes |
|---|------|-------|--------|-------|
| 1.3.1 | Dependency vulnerability scan reviewed | Security | [ ] | |
| 1.3.2 | No hardcoded secrets in release build | Security | [ ] | |
| 1.3.3 | SSL/TLS certificates valid on production | DevOps | [ ] | |

---

## 2. Deployment Checklist

| # | Item | Owner | Status | Notes |
|---|------|-------|--------|-------|
| 2.1 | Production deployment window confirmed | Release Manager | [ ] | |
| 2.2 | Rollback plan documented and tested | DevOps | [ ] | |
| 2.3 | Database backup completed before deploy | DBA | [ ] | |
| 2.4 | Feature flags configured for gradual rollout | Dev Lead | [ ] | |
| 2.5 | Monitoring and alerting dashboards verified | DevOps | [ ] | |
| 2.6 | On-call rotation confirmed for release window | Release Manager | [ ] | |

---

## 3. Post-Release Verification

| # | Item | Owner | Status | Notes |
|---|------|-------|--------|-------|
| 3.1 | Smoke test executed on production | QA | [ ] | |
| 3.2 | Health check endpoints returning 200 | DevOps | [ ] | |
| 3.3 | Error rate within baseline (Sentry/Datadog) | DevOps | [ ] | |
| 3.4 | Payment flow verified with test transaction | QA | [ ] | |
| 3.5 | Stakeholders notified of successful deployment | PM | [ ] | |

---

## 4. Rollback Criteria

Initiate rollback if any of the following occur within 2 hours of deployment:

- Production error rate exceeds 5% of baseline
- Critical user flow (login, checkout, payment) is non-functional
- Data integrity issue confirmed
- Unresolved Critical defect discovered in production

---

## 5. Sign-off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| QA Lead | | | |
| Development Lead | | | |
| Release Manager | | | |
| Product Owner | | | |

**Release Decision:** [ ] Go  [ ] No-Go

**Comments:**

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-06-25 | QA Team | Initial checklist for v2.5.0 |
