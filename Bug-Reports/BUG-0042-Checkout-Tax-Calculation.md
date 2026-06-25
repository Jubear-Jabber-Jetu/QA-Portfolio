# Bug Report: Incorrect Tax Calculation on Multi-Item Orders

| Field | Value |
|-------|-------|
| **Bug ID** | BUG-0042 |
| **Severity** | High |
| **Priority** | P1 |
| **Status** | Open |
| **Reported By** | QA Team |
| **Reported Date** | 2026-06-20 |
| **Assigned To** | Backend Team |
| **Environment** | Staging |
| **Build** | v2.4.1-staging.87 |

---

## Summary

Order tax amount is calculated on the subtotal of the first line item only when the cart contains three or more items with different tax categories.

---

## Requirement Reference

- REQ-CHK-018: System shall calculate order tax as the sum of applicable tax per line item based on product category and shipping region.

---

## Steps to Reproduce

1. Log in as `standard_user` on staging environment.
2. Add the following items to cart:
   - NovaCart Backpack (taxable, 8.25%) — $29.99
   - Fleece Jacket (taxable, 8.25%) — $49.99
   - Gift Card (non-taxable) — $25.00
3. Proceed to checkout with shipping address in Texas (TX).
4. Review the **Order Summary** panel before payment submission.

---

## Expected Result

| Line Item | Tax Rate | Tax Amount |
|-----------|----------|------------|
| Backpack | 8.25% | $2.47 |
| Fleece Jacket | 8.25% | $4.12 |
| Gift Card | 0% | $0.00 |
| **Total Tax** | | **$6.59** |

---

## Actual Result

Total tax displayed: **$2.47** (tax applied to first item only).

Screenshot evidence: `evidence/BUG-0042-order-summary.png`

---

## Impact

- Customers undercharged on multi-item taxable orders
- Financial reconciliation discrepancies
- Potential compliance risk in regulated jurisdictions

**Affected Users:** All registered and guest checkout users with multi-item carts.

---

## Workaround

None available for end users. Manual tax adjustment required post-order in admin panel.

---

## Additional Information

| Attribute | Value |
|-----------|-------|
| Browser | Chrome 125.0.6422.112 |
| OS | Windows 11 |
| Reproducibility | 100% (5/5 attempts) |
| Related Test Case | TC-CHK-014 |
| API Endpoint | `POST /v1/orders/calculate` |

**Network Response Snippet:**

```json
{
  "subtotal": 104.98,
  "tax": 2.47,
  "shipping": 5.99,
  "total": 113.44
}
```

Expected `tax` value: `6.59`

---

## Defect History

| Date | Action | By | Notes |
|------|--------|-----|-------|
| 2026-06-20 | Created | QA Team | Initial report |
| 2026-06-21 | Triaged | QA Lead | Confirmed reproducible; assigned to Backend |
| 2026-06-22 | In Progress | Dev Team | Root cause under investigation |

---

## Root Cause (Pending)

Preliminary analysis suggests the tax aggregation loop in `TaxCalculatorService` exits after the first taxable item when `cart.items.length > 2`.
