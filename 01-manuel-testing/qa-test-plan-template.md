# QA Test Plan

> **Purpose:** Define the scope, approach, resources, environments, and completion criteria for a test cycle. Detailed test cases and execution evidence are in the companion **QA Test Cases & Execution Records** document or test-management tool.

> **Draft status:** Items marked **[TBC]** are not yet known and have deliberately not been filled in.

## 1. Document control

| Field | Value |
|---|---|
| Project / product | E-commerce QA portfolio |
| Release / test cycle | N.V.T. |
| Feature / module | Login & registration; catalogue, search & product details; cart & promotions; checkout, payment & orders |
| Test Plan ID | TP-ECOMQA-001 |
| Version / status | 0.1 / Draft |
| QA owner | Angelica Soete |
| Prepared / updated | 2026-11-06 |
| Related requirements | Draft requirements derived from the shop's visible behaviour: see section 5 of the Test Cases & Execution Records document (REQ-001…) |
| Test case repository | https://github.com/ctrl-angelica/ecommerce-qa-portfolio.git |

## 2. Objective and scope

**Objective**
Build a portfolio project that demonstrates end-to-end QA skills on a public demo e-commerce shop: manual functional testing, API testing, SQL data checks, and Playwright test automation. The project runs over 6 weeks (4 Nov – 15 Dec 2026) at about 8–10 hours per week.

**In scope**
- Login & registration
- Catalogue, search & product details
- Cart & promotions
- Checkout, payment & orders
- Test types: functional (manual), API, SQL / data checks, Playwright automation
- Application under test: Practice Software Testing – Toolshop (https://practicesoftwaretesting.com), a public demo shop with a UI and a REST API
- Platforms, devices, browsers: desktop; Google Chrome, on Windows
- User roles and business rules: guest vs. signed-in customer [TO CONFIRM after exploring the shop]

**Out of scope**
- Shipping (methods, fees, tracking): not selected for this project
- Returns / refunds: not selected for this project
- Account management (profile, saved addresses, preferences): not selected for this project
- Performance and load testing; security testing beyond basic authentication/authorisation checks; formal accessibility audit; mobile devices; admin back-office; contact form (confirmed 2026-11-06). Reason: with a single tester and roughly 48–60 hours in total (6 weeks × 8–10 h), depth in the four chosen modules is worth more than breadth.

## 3. Test approach

**Approach:** Hybrid (manual + automated)
**Test levels:** System; API / integration [TBC]
**Design techniques:** Equivalence partitioning with boundary value analysis (primary, used to build the data sets for login/registration and form inputs); exploratory testing (session-based, used to learn the shop and derive requirements)

| Test type | In scope? | Coverage / notes |
|---|---|---|
| Functional | Yes | Manual testing of login/registration, catalogue/search/product details, cart/promotions, checkout/payment/orders |
| UI / usability | [TBC] | |
| API / integration | Yes | REST API of the Toolshop (Swagger documentation at api.practicesoftwaretesting.com/api/documentation). Tools: Playwright API testing (primary, automated, version-controlled in the repo); Postman optional for manual exploration (proposed) |
| Regression | Yes | Playwright suite re-run on the critical flows |
| Compatibility | No | Chrome only; no cross-browser testing |
| Performance | No | See out of scope |
| Security | No | Only basic authentication/authorisation checks (see out of scope) |
| Accessibility | No | See out of scope |
| Data / SQL checks | Yes | SQL validation of data created by the app. The hosted shop's database is probably not reachable, so this likely requires running the app locally from its open-source code. Angelica will check whether this is possible; fallback options are in section 8 |

**Prioritization:** Risk-based approach. The starter coverage list rates checkout and payment, orders, and cart as P0–P1, so these would be the natural highest priority. 
**Automation notes:** Playwright for automated UI tests (requires Node.js, still to be installed). Flows chosen for automation:
1. End-to-end (log in, find a product, add to cart, check out, order confirmation)
2. Login and registration, data-driven with several data sets (valid and invalid)
3. API-assisted setup with UI checks (create data through the API, verify in the UI and, where possible, with SQL)

All other flows (e.g. search/filter/sort, cart totals and promotions) stay manual for now. [TBC: whether any of these should be automated later if time allows.]

## 4. Test environment and data

| Item | Configuration / reference |
|---|---|
| Environment | Public hosted demo: https://practicesoftwaretesting.com (a deliberately buggy version also exists) |
| Application build | Page title "Toolshop - v5.0"; footer on 2026-11-06: "v2.5 | Built 2026-10-11 | Angular 20.0.5". Re-check and record at the start of each run. |
| Browser / device / OS | Google Chrome (desktop); Windows |
| Accounts and roles | Customer test account listed in the shop's public documentation (customer@practicesoftwaretesting.com); passwords are not stored here. |
| Test data | [TBC: data set, source, reset process] |
| External services | [TBC: payment sandbox / mocks, if any] |
| Monitoring / logs | [TBC: e.g. browser dev tools, Playwright traces] |

## 5. Entry and exit criteria

### Entry criteria
- [ ] Approved or sufficiently stable requirements and acceptance criteria are available.
- [ ] Test build is deployed to the agreed environment.
- [ ] Environment and required integrations are accessible.
- [ ] Test data and accounts are prepared.
- [ ] Smoke checks pass and no known blocker prevents testing.

### Exit criteria
- [ ] Planned tests have been executed, or remaining tests are explicitly documented as not run.
- [ ] Critical workflows and agreed risk areas have sufficient coverage.
- [ ] No open release-blocking defects remain, unless formally accepted by the accountable owner.
- [ ] Failed and blocked tests have linked defect records or documented reasons.
- [ ] Regression testing is complete to the agreed scope.
- [ ] Results, residual risks, and QA recommendation are communicated.

> Agree measurable thresholds before execution where needed (for example, minimum pass rate or maximum number of open defects). Do not use a pass rate alone as a release criterion.
> [TO CONFIRM: any measurable thresholds you want to set.]

## 6. Roles and responsibilities

| Role | Responsibility | Owner |
|---|---|---|
| QA owner / lead | Test planning, coordination, reporting, recommendation | Angelica Soete |
| Tester(s) | Design, execution, evidence, defect reporting | Angelica Soete |
| Developer / engineering | Fixes, technical support, unit and integration evidence | N/A |
| Product owner / business | Requirement clarification and acceptance decisions | N/A |
| Release owner | Release decision and risk acceptance | N/A |

## 7. Defect management

**Tracking tool:** GitHub Issues (repository ctrl-angelica/ecommerce-qa-portfolio)
**Workflow:** New → Triaged → In Progress → Fixed → Retest → Closed. In GitHub Issues this is done with status labels, plus severity labels (Critical / High / Medium / Low) as defined below; the issue is closed only after retest.

| Severity | Definition |
|---|---|
| Critical | Blocks a core business flow, causes major data loss, or creates a severe security / payment risk. |
| High | Major functionality is unusable or materially incorrect; no acceptable workaround. |
| Medium | Functionality is impaired, but a reasonable workaround exists. |
| Low | Minor, cosmetic, or low-impact issue. |

Record each defect in the tracking tool with: summary, environment/build, preconditions, reproducible steps, expected and actual result, severity, priority, evidence, and linked test case / requirement. Keep the authoritative defect details in the tracker rather than duplicating them here.

## 8. Risks, assumptions, and dependencies

| Item | Likelihood / impact | Mitigation / owner |
|---|---|---|
| Limited time: 6 weeks at about 8–10 hours per week (4 Nov – 15 Dec 2026) | [TBC] | [TBC: e.g. prioritise P0 areas first] |
| Node.js not yet installed and repo not yet cloned (needed for Playwright) | [TBC] | Install Node.js and clone the repo — Angelica |
| SQL checks may not be possible: the hosted shop's database is probably not accessible | [TBC] | Angelica checks if the shop can be run locally from its source code (then query its database). Fallbacks: (a) read the same data back through the API as a proxy, clearly labelled as not SQL; (b) practise SQL on a separate sample e-commerce database, documented as separate from the shop |
| Other risks (e.g. demo shop availability, shared data resets) | [TBC] | [TBC] |

## 9. Deliverables

- [ ] Approved test plan
- [ ] Test scenarios and test cases
- [ ] Test execution records and evidence
- [ ] Defect records in the tracking tool
- [ ] Test summary and QA recommendation

## 10. Approval and sign-off

| Role | Name | Decision / date | Notes or accepted risks |
|---|---|---|---|
| QA lead | Angelica Soete | [Approved / Rejected / YYYY-MM-DD] | |
| Product owner | N/A | N/A | |
| Release owner | N/A | N/A | |

---

## Change history

| Version | Date | Author | Change |
|---|---|---|---|
| 0.1 | 2026-11-06 | Angelica Soete | Initial draft |