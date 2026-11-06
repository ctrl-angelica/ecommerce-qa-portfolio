# QA Test Cases & Execution Records

> **Purpose:** Maintain the executable test cases, traceability, run results, and concise test-cycle summary for a feature or release. This document complements the **QA Test Plan**; it does not replace the defect tracker or store credentials.

## 1. Document control

| Field | Value |
|---|---|
| Project / product | [Name] |
| Release / feature | [Name] |
| Related Test Plan ID | [TP-PROJECT-NNN] |
| Test case set version | [Version] |
| QA owner | [Name] |
| Repository / tracker | [Link] |

## 2. Test case conventions

**Suggested ID format:** `TC-[MODULE]-[NNN]` (for example, `TC-CART-001`). Keep IDs stable when test steps change.

**Priority:**
- **P0 – Critical:** Core business flow, high business / data / security risk.
- **P1 – High:** Important functionality with significant user impact.
- **P2 – Medium:** Standard functionality or moderate impact.
- **P3 – Low:** Low-risk or cosmetic coverage.

**Execution status:** `Not Run` · `Pass` · `Fail` · `Blocked` · `Not Applicable`  
Use **Blocked** when execution cannot proceed; include the reason. Use **Not Applicable** only with a brief explanation.

## 3. Test case template

Copy this section once per test case.

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

| Area | Starter scenarios | Suggested priority |
|---|---|---|
| Registration / login | Valid and invalid login; registration validation; password reset; session expiry | P1 |
| Catalogue / search | Product listing; search terms; no results; filters; sorting; pagination | P1–P2 |
| Product details | Price; images; stock; variants; unavailable products | P1 |
| Cart | Add / remove item; update quantity; stock changes; totals; persistence | P0–P1 |
| Promotions | Valid / invalid / expired code; eligibility; stacking; calculation | P1–P2 |
| Checkout | Guest and signed-in checkout; required fields; address validation; shipping options | P0 |
| Payment | Approved, declined, cancelled, timed-out, and duplicate submission cases | P0 |
| Orders | Order creation; confirmation; order history; status updates | P0–P1 |
| Shipping | Shipping methods and fees; restricted destinations; tracking information | P1 |
| Returns / refunds | Eligibility; return request; partial and full refund; status updates | P1 |
| Account | Profile updates; saved addresses; consent and preferences | P1–P2 |

## 5. Requirements traceability

Link each in-scope requirement to one or more test cases. This helps identify requirements with no coverage and test cases with no clear purpose.

| Requirement / story ID | Requirement summary | Test case IDs | Coverage status | Notes |
|---|---|---|---|---|
| [REQ-001] | [Summary] | [TC-...] | [Covered / Partial / Not covered] | [Gap or note] |

## 6. Test execution log

Create a new run identifier for each build, cycle, or environment. Record one row per executed test case; retain history rather than overwriting earlier results.

| Run ID | Test Case ID | Build / environment | Tester | Date | Status | Defect ID | Evidence link / notes |
|---|---|---|---|---|---|---|---|
| [RUN-001] | [TC-...] | [Build / QA] | [Name] | [YYYY-MM-DD] | [Status] | [BUG-...] | [Link / note] |

**Execution notes:** [Record run-specific constraints, data resets, interruptions, or deviations.]

## 7. Defect references

Keep full defect details in the team's issue tracker. Use this table only as a quick reference from test execution.

| Defect ID | Related test case | Summary | Severity | Status | Tracker link |
|---|---|---|---|---|---|
| [BUG-001] | [TC-...] | [Short summary] | [Critical / High / Medium / Low] | [Open / In progress / Fixed / Closed] | [Link] |

## 8. Test-cycle summary

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
| 0.1 | [YYYY-MM-DD] | [Name] | Initial draft |
