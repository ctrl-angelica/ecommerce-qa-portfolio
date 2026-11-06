# QA Test Plan

> **Purpose:** Define the scope, approach, resources, environments, and completion criteria for a test cycle. Detailed test cases and execution evidence are in the companion **QA Test Cases & Execution Records** document or test-management tool.

## 1. Document control

| Field | Value |
|---|---|
| Project / product | [Name] |
| Release / test cycle | [Release or cycle] |
| Feature / module | [Feature or module] |
| Test Plan ID | TP-[PROJECT]-[NNN] |
| Version / status | [Version] / [Draft, In review, Approved] |
| QA owner | [Name / role] |
| Prepared / updated | [YYYY-MM-DD] |
| Related requirements | [Links or IDs] |
| Test case repository | [Link or location] |

## 2. Objective and scope

**Objective**
[What needs to be validated, and why? Keep this to a few sentences.]

**In scope**
- [Feature, workflow, or requirement to validate]
- [Platforms, devices, browsers, or integrations included]
- [Relevant user roles or business rules]

**Out of scope**
- [Explicit exclusions and, where useful, the reason]

## 3. Test approach

**Approach:** [Manual / Automated / Hybrid]
**Test levels:** [System / Integration / Acceptance / Other]
**Design techniques:** [Equivalence partitioning, boundary value analysis, decision tables, state transitions, exploratory testing, as applicable]

| Test type | In scope? | Coverage / notes |
|---|---|---|
| Functional | [Yes / No] | [Key workflows and rules] |
| UI / usability | [Yes / No] | [Layouts, interactions, content] |
| API / integration | [Yes / No] | [Services and interfaces] |
| Regression | [Yes / No] | [Impacted and critical existing flows] |
| Compatibility | [Yes / No] | [Browsers, devices, operating systems] |
| Performance | [Yes / No] | [Load, response time, or capacity targets] |
| Security | [Yes / No] | [Relevant security checks] |
| Accessibility | [Yes / No] | [Applicable accessibility standard / criteria] |

**Prioritization:** [Risk-based approach and the areas receiving highest priority.]
**Automation notes:** [What will be automated, what remains manual, and any constraints.]

## 4. Test environment and data

| Item | Configuration / reference |
|---|---|
| Environment | [QA / Staging / UAT; URL] |
| Application build | [Version / build number] |
| Browser / device / OS | [Supported configurations] |
| Accounts and roles | [Test account references; do not store passwords here] |
| Test data | [Data set, source, reset process] |
| External services | [Sandbox endpoints, mocks, dependencies] |
| Monitoring / logs | [Where to find relevant logs and diagnostics] |

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

## 6. Roles and responsibilities

| Role | Responsibility | Owner |
|---|---|---|
| QA owner / lead | Test planning, coordination, reporting, recommendation | [Name] |
| Tester(s) | Design, execution, evidence, defect reporting | [Name(s)] |
| Developer / engineering | Fixes, technical support, unit and integration evidence | [Name / team] |
| Product owner / business | Requirement clarification and acceptance decisions | [Name] |
| Release owner | Release decision and risk acceptance | [Name] |

## 7. Defect management

**Tracking tool:** [Jira / Azure DevOps / other]  
**Workflow:** [For example: New → Triaged → In Progress → Fixed → Retest → Closed]

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
| [Risk, assumption, or dependency] | [Low / Medium / High] | [Mitigation and owner] |
| [Example: payment sandbox unavailable] | [High] | [Use approved mock; confirm coverage limitation] |

## 9. Deliverables

- [ ] Approved test plan
- [ ] Test scenarios and test cases
- [ ] Test execution records and evidence
- [ ] Defect records in the tracking tool
- [ ] Test summary and QA recommendation

## 10. Approval and sign-off

| Role | Name | Decision / date | Notes or accepted risks |
|---|---|---|---|
| QA lead | [Name] | [Approved / Rejected / YYYY-MM-DD] | [Notes] |
| Product owner | [Name] | [Accepted / Rejected / YYYY-MM-DD] | [Notes] |
| Release owner | [Name] | [Go / No-go / YYYY-MM-DD] | [Notes] |

---

## Change history

| Version | Date | Author | Change |
|---|---|---|---|
| 0.1 | [YYYY-MM-DD] | [Name] | Initial draft |
