# QA Test Cases & Execution Records

> **Purpose:** Maintain the executable test cases, traceability, run results, and concise test-cycle summary for a feature or release. This document complements the **QA Test Plan**; it does not replace the defect tracker or store credentials.

> **Draft status:** Items marked **[TBC]** are not yet known. No test cases, results, or metrics have been written yet; nothing has been executed.

## 1. Document control

| Field | Value |
|---|---|
| Project / product | E-commerce QA portfolio (Practice Software Testing – Toolshop, https://practicesoftwaretesting.com) |
| Release / feature | N/A |
| Related Test Plan ID | TP-ECOMQA-001 |
| Test case set version | 0.1 |
| QA owner | Angelica Soete |
| Repository / tracker | https://github.com/ctrl-angelica/ecommerce-qa-portfolio.git (defect tracker: GitHub Issues) |

## 2. Test case conventions

**Suggested ID format:** `TC-[MODULE]-[NNN]` (for example, `TC-CART-001`). Keep IDs stable when test steps change.

**Priority:**
- **P0 – Critical:** Core business flow, high business / data / security risk.
- **P1 – High:** Important functionality with significant user impact.
- **P2 – Medium:** Standard functionality or moderate impact.
- **P3 – Low:** Low-risk or cosmetic coverage.

**Execution status:** `Not Run` · `Pass` · `Fail` · `Blocked` · `Not Applicable`
Use **Blocked** when execution cannot proceed; include the reason. Use **Not Applicable** only with a brief explanation.

**Modules in scope (from the Test Plan):** Login & registration · Catalogue, search & product details · Cart & promotions · Checkout, payment & orders. Module codes for IDs: [TBC: e.g. AUTH, CAT, CART, CHK].

## 3. Test case template

Copy this section once per test case. *(No test cases written yet.)*

### TC-[MODULE]-[NNN] — [Short scenario name]

| Field | Details |
|---|---|
| Requirement / user story | [Requirement ID or link] |
| Module | [e.g. Checkout] |
| Priority | [P0 / P1 / P2 / P3] |
| Test type | [Functional / Integration / Regression / UI / etc.] |
| Preconditions | [Required account state, cart state, configuration] |
| Test data | [Named data set or safe test values; no secrets] |
| Environment | [Environment / build, if test-specific] |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | [Action] | [Observable expected result] |
| 2 | [Action] | [Observable expected result] |
| 3 | [Action] | [Observable expected result] |

**Postconditions / cleanup:** [Required cleanup, reset, or resulting state.]  
**Automation:** [Manual / Automated / Candidate]  
**Notes:** [Optional boundary cases or variations.]

## 4. E-commerce starter coverage

Use this as a prompt for designing test cases, not as proof that the feature is fully covered. Add cases based on requirements, risks, supported markets, payment methods, and business rules.

Areas selected for this project are marked **In scope**; shipping, returns/refunds and account are **Out of scope**.

| Area | Starter scenarios | Suggested priority | Project scope |
|---|---|---|---|
| Registration / login | Valid and invalid login; registration validation; password reset; session expiry | P1 | In scope |
| Catalogue / search | Product listing; search terms; no results; filters; sorting; pagination | P1–P2 | In scope |
| Product details | Price; images; stock; variants; unavailable products | P1 | In scope |
| Cart | Add / remove item; update quantity; stock changes; totals; persistence | P0–P1 | In scope |
| Promotions | Valid / invalid / expired code; eligibility; stacking; calculation | P1–P2 | In scope |
| Checkout | Guest and signed-in checkout; required fields; address validation; shipping options | P0 | In scope |
| Payment | Approved, declined, cancelled, timed-out, and duplicate submission cases | P0 | In scope |
| Orders | Order creation; confirmation; order history; status updates | P0–P1 | In scope |
| Shipping | Shipping methods and fees; restricted destinations; tracking information | P1 | Out of scope |
| Returns / refunds | Eligibility; return request; partial and full refund; status updates | P1 | Out of scope |
| Account | Profile updates; saved addresses; consent and preferences | P1–P2 | Out of scope |

## 5. Requirements traceability

Link each in-scope requirement to one or more test cases. This helps identify requirements with no coverage and test cases with no clear purpose.

| Requirement / story ID | Requirement summary | Test case IDs | Coverage status | Notes |
|---|---|---|---|---|
| REQ-001 | Product listing shows each product's name and price | | Not covered | Draft; observed on the home page 2026-11-06 |
| REQ-002 | Product listing is paginated | | Not covered | Draft; observed: 5 pages |
| REQ-003 | Out-of-stock products are labelled as such in the listing | | Not covered | Draft; observed on "Long Nose Pliers" (label shown in Dutch because of browser language) |
| REQ-004 | A filter control is available on the listing | | Not covered | Draft; filter options not yet explored |
| REQ-005 – REQ-0xx | Login/registration, search, product details, cart, promotions, checkout, payment, orders | | Not covered | To be added by Angelica after her exploratory session (and from the API Swagger documentation). No behaviour assumed. |

## 6. Test execution log

Create a new run identifier for each build, cycle, or environment. Record one row per executed test case; retain history rather than overwriting earlier results.

| Run ID | Test Case ID | Build / environment | Tester | Date | Status | Defect ID | Evidence link / notes |
|---|---|---|---|---|---|---|---|
| | | | | | | | |

**Execution notes:** No tests executed yet.

## 7. Defect references

Keep full defect details in the team's issue tracker. Use this table only as a quick reference from test execution.

| Defect ID | Related test case | Summary | Severity | Status | Tracker link |
|---|---|---|---|---|---|
| | | | | | |

## 8. Test-cycle summary

*To be completed after the first test cycle. No figures have been entered so none are invented.*

**Run ID:** [RUN-XXX]  
**Build / environment:** [Build and environment]  
**Execution period:** [Start date – end date]  
**Scope executed:** [Modules / test types]

| Metric | Count |
|---|---:|
| Total planned | [N] |
| Passed | [N] |
| Failed | [N] |
| Blocked | [N] |
| Not run | [N] |
| Not applicable | [N] |
| Open defects — Critical / High | [N] |
| Open defects — Medium / Low | [N] |

**Pass rate:** `[Passed ÷ (Passed + Failed)] × 100` = [N%]  
*Report the denominator with the rate. Exclude Blocked, Not Run, and Not Applicable from this calculation; do not use the rate as the only release decision criterion.*

**Key findings:**
- [Important result or regression concern]
- [Known limitation or coverage gap]
- [Residual risk / accepted defect]

**QA recommendation:** [Ready for acceptance / Not ready / Ready with stated risks]  
**Decision owner:** [Name / role]  
**Decision date:** [YYYY-MM-DD]

## 9. Evidence checklist

- [ ] Relevant screenshots, recordings, logs, or API responses are linked to the execution record or defect.
- [ ] Evidence identifies the build and environment where practical.
- [ ] Sensitive customer data, credentials, tokens, and payment data are not included.
- [ ] Failed and blocked tests have a defect link or a documented reason.
- [ ] Test data and environment are identified sufficiently for reproduction.

---

## Change history

| Version | Date | Author | Change |
|---|---|---|---|
| 0.1 | 2026-11-06 | Angelica Soete | Initial draft |