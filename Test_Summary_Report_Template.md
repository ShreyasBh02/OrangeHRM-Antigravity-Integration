# Test Summary Report Template
**OrangeHRM Manual Testing — Post-Execution Report**

---

## Report Details

| Field | Value |
|---|---|
| **Project** | OrangeHRM v5.0 Manual Testing |
| **Report Version** | [e.g., Cycle 1 / Cycle 2 / Final] |
| **Test Cycle** | [Cycle 1 — Functional / Cycle 2 — Regression / UAT] |
| **Reporting Period** | [Start Date] to [End Date] |
| **Prepared By** | [QA Lead Name] |
| **Report Date** | [YYYY-MM-DD] |
| **Reviewed By** | [Project Manager / BA] |

---

## 1. Executive Summary

> A 3–5 sentence non-technical summary for project stakeholders.

[e.g., "The Cycle 1 functional testing of OrangeHRM v5.0 has been completed. 72 of 75 test cases were executed, achieving a 96% pass rate. Three defects were identified — one High (P1) and two Medium (P2). The P1 defect is resolved and verified. The system is recommended for regression testing and UAT."]

---

## 2. Scope of This Cycle

| Module | TCs Planned | TCs Executed | Skipped / Blocked |
|---|---|---|---|
| Login / Password | 14 | | |
| Admin | 13 | | |
| PIM | 13 | | |
| Leave | 14 | | |
| Time | 8 | | |
| Dashboard | 6 | | |
| Cross-Browser Smoke | 7 | | |
| **TOTAL** | **75** | | |

---

## 3. Test Execution Summary

| Metric | Count | Percentage |
|---|---|---|
| Total TCs Planned | 75 | 100% |
| TCs Executed | | |
| TCs Passed | | |
| TCs Failed | | |
| TCs Blocked | | |
| TCs Deferred | | |
| **TC Execution Rate** | | **Target: ≥ 95%** |
| **TC Pass Rate** | | **Target: ≥ 95%** |

---

## 4. Defect Summary

| Severity | Total Found | Open | Fixed | Verified/Closed | Deferred |
|---|---|---|---|---|---|
| P0 — Critical | | | | | |
| P1 — High | | | | | |
| P2 — Medium | | | | | |
| P3 — Low | | | | | |
| **TOTAL** | | | | | |

**Defect Density:** [Total Defects / Total TCs] = [value] (Target: < 0.3)

---

## 5. Module-wise Pass/Fail Breakdown

| Module | Executed | Pass | Fail | Blocked | Pass Rate |
|---|---|---|---|---|---|
| Login / Password | | | | | |
| Admin | | | | | |
| PIM | | | | | |
| Leave | | | | | |
| Time | | | | | |
| Dashboard | | | | | |
| Cross-Browser | | | | | |
| **TOTAL** | | | | | |

---

## 6. Open / Critical Defect Details

> List only P0 and P1 open defects. P2/P3 can be summarized.

| Bug ID | Module | Summary | Severity | Status | Assigned To | Target Fix Date |
|---|---|---|---|---|---|---|
| BUG-001 | | | | | | |
| BUG-002 | | | | | | |

---

## 7. Blocked Test Cases

| TC ID | Reason Blocked | Blocked Since | Owner for Resolution |
|---|---|---|---|
| | | | |

---

## 8. Test Environment Used

| Property | Details |
|---|---|
| Application URL | `https://opensource-demo.orangehrmlive.com` |
| App Version | OrangeHRM 5.0 |
| Primary Browser | Chrome 118 / Windows 11 |
| Secondary Browser | Firefox 118 / Windows 11 |
| Execution Period | [Dates] |

---

## 9. Key Observations & Risks

> Notes from test execution that are important for the team to know.

1. [Observation 1 — e.g., "Leave module balance calculation was inconsistent across 2 TCs — under investigation."]
2. [Observation 2 — e.g., "Demo environment was reset on Day 5, requiring full test data reload."]
3. [Risk — e.g., "If BUG-001 is not resolved before UAT, the Leave Approval workflow cannot be validated."]

---

## 10. Metrics vs Targets

| Metric | Target | Actual | Status |
|---|---|---|---|
| TC Execution Rate | ≥ 95% | | Pass / Fail |
| TC Pass Rate | ≥ 95% | | Pass / Fail |
| Defect Density | < 0.3 | | Pass / Fail |
| Open P0 Defects | 0 | | Pass / Fail |
| Open P1 Defects | 0 | | Pass / Fail |

---

## 11. Recommendation

> Provide a clear go/no-go recommendation based on the data above.

- [ ] **GO** — All exit criteria met. System approved to proceed to [Regression / UAT / Production].
- [ ] **CONDITIONAL GO** — Minor open items remain. Proceeding with the following conditions: [List conditions]
- [ ] **NO-GO** — Exit criteria NOT met. Reason: [Specify]. Testing must continue until P0/P1 defects are resolved.

---

## 12. Next Steps

| Action | Owner | Due Date |
|---|---|---|
| Fix and re-verify open P1 defects | Developer + QA | |
| Execute Regression Cycle 2 | QA Team | |
| Conduct UAT with business stakeholders | Product Owner + BA | |
| Deliver Final Test Summary Report | QA Lead | |

---

## 13. Sign-off

| Role | Name | Signature | Date |
|---|---|---|---|
| QA Lead | | | |
| Project Manager | | | |
| Product Owner | | | |

---

*OrangeHRM Manual Testing — Test Summary Report Template v1.0*
