# Improvement Analysis Report
## OrangeHRM — Test Cases & Test Plan
*Reviewed as a QA Lead with 20+ years of experience*

---

## Current State Scorecard

| Document | Current Score | Target Score | Gap |
|---|---|---|---|
| **Manual Test Cases** | 7.8 / 10 | 9.5 / 10 | 1.7 |
| **Test Plan** | 8.5 / 10 | 9.5 / 10 | 1.0 |

---

## Part 1 — Test Cases Improvements

### 🔴 CRITICAL — Must Fix

#### 1. Missing Test Case: Change Password (Logged In)
- **What:** There is no TC that tests changing the password from *inside* the application (via Profile > Change Password), only the "Forgot Password" external reset flow.
- **Why:** This is a core user workflow tested in any HR system. Major coverage gap.
- **Add:**
  - TC: Verify password change with correct current password → success
  - TC: Verify password change fails if current password is wrong
  - TC: Verify new password and confirm password mismatch validation

---

#### 2. Missing Test Cases: Admin — Job & Organization Configuration
- **What:** No TCs exist for Admin sub-menus: Job Titles, Pay Grades, Locations, Employment Status, Company Structure.
- **Why:** These are foundational data that PIM, Leave, and Time modules depend on. If Pay Grades aren't tested, salary data could be misconfigured.
- **Add:**
  - TC: Add a new Job Title and verify it appears in PIM dropdown
  - TC: Add a new Location and assign it to an employee
  - TC: Define a Pay Grade with min/max salary and currency

---

#### 3. No TC for Leave: ESS Cancelling a *Pending* (not Approved) Leave
- **What:** TC_LEV_08 only tests cancelling an *Approved* leave. Cancelling a *Pending* leave is a separate, distinct workflow.
- **Why:** The system may behave differently for Pending vs Approved cancellations (no supervisor action needed for Pending).
- **Add:** TC: ESS user cancels their own Pending leave → Status = Cancelled, balance restored immediately.

---

#### 4. No TC for Time: ESS Views Their Own Attendance Records
- **What:** After punching in/out, there is no TC verifying the employee can view their own attendance history.
- **Add:** TC: Navigate to Time > Attendance > My Records → verify punch-in/out timestamps are listed accurately.

---

#### 5. No Negative TC for PIM: Duplicate Employee ID
- **What:** Currently TC_PIM_01 tests auto-generated IDs. There is no TC for what happens if a tester enters a manually typed duplicate Employee ID.
- **Add:** TC: Enter an already-existing Employee ID manually → system rejects with "Employee Id Already Exists".

---

### 🟡 HIGH IMPACT — Should Add

#### 6. Add "Test Case Priority" Execution Filter Column
- **What:** Add a `Smoke Suite` boolean column (`Yes`/`No`) so testers can instantly filter just the 7 Smoke TCs without reading every row.
- **Why:** Saves time during quick regression runs and environment validation.

---

#### 7. Expand Security TCs
- **Current coverage:** SQL Injection (login), XSS (admin field), Session timeout, URL bypass, Financial data
- **Missing:**
  - TC: **IDOR (Insecure Direct Object Reference)** — Can ESS User change URL from `empNumber=3` to `empNumber=4` to see another employee's personal details?
  - TC: **CSRF basics** — Verify state-changing actions (delete user, approve leave) require a valid authenticated session.
  - TC: **Password in URL** — Verify login never passes credentials as query string parameters (visible in browser history).
  - TC: **Autocomplete off** — Verify password field has `autocomplete="off"` or `autocomplete="new-password"` attribute (prevents browser saving passwords in enterprise context).

---

#### 8. Add Multi-browser TC Execution Rows
- **What:** Currently all TCs say `Chrome 118 / Win 11`. The Test Plan defines Firefox and Safari as P1. The TC sheet should have separate execution rows for each browser for at least the Smoke suite.
- **Add:** Duplicate the 7 Smoke TCs and mark them for Firefox execution. This creates a lightweight cross-browser smoke matrix.

---

#### 9. Add `Tested By` Column
- **What:** When multiple testers execute the same TC sheet, there is no column capturing *who* executed which TC.
- **Why:** Audit trails and defect ownership disputes require this. Critical for any enterprise handover.

---

#### 10. Add `Defect ID` Column
- **What:** When a TC fails, the linked defect ticket ID should be recorded directly on the TC row.
- **Why:** Eliminates manual cross-referencing between TC sheet and defect sheet. RTM completeness requires this link.

---

#### 11. Add `Comments / Notes` Column
- **What:** A free-text column for testers to note partial executions, environment issues, or out-of-scope behavior observed during testing.
- **Why:** Prevents information loss that currently lives only in testers' heads or chat messages.

---

#### 12. Expand Leave Module — Negative Scenarios
- **Missing TCs:**
  - TC: Apply leave on a **weekend date** — does system block or allow?
  - TC: Apply leave with **From Date > To Date** — reverse date range validation
  - TC: Apply leave with **past dates** — should system allow or reject back-dated leave?
  - TC: Supervisor tries to **approve their own leave** — conflict of interest scenario

---

#### 13. PIM — Edit Existing Employee Details
- **What:** Existing TCs only *add* data to profiles. There is no TC for *editing* existing personal details.
- **Add:**
  - TC: Edit employee's existing email address and verify update persists after page refresh
  - TC: Edit Marital Status and verify the change is visible in the summary view

---

#### 14. Admin — Verify User Group Privilege Restriction
- **What:** No TC verifies that a custom user group with limited privileges (e.g., `View Only` on PIM) actually *prevents* write access.
- **Add:** TC: Create user group with `View` only on PIM. Log in as that user, attempt to edit an employee record → Save button disabled or Access Denied.

---

### 🟢 MEDIUM / LOW — Nice to Have

#### 15. Add Test Data in a Separate Sheet (Data-Driven Approach)
Isolate test data (usernames, passwords, dates) into a separate "Test Data" Excel sheet. TCs reference the row by ID instead of embedding raw values. Enables easy data refresh without modifying TCs.

#### 16. Add Screenshot Reference Column
- A column `Screenshot Path` where the tester pastes the relative path to the evidence screenshot taken during execution. Improves audit quality significantly.

#### 17. Pagination & List Sorting TCs
- TC: Navigate to Employee List with 50+ employees → verify pagination controls work correctly.
- TC: Sort Employee List by First Name A→Z and Z→A → verify sort order is accurate.

#### 18. Dashboard: Verify ESS vs Admin Widget Difference
- TC: Log in as ESS user → Dashboard shows only individual widgets (no team pending actions).
- TC: Log in as Admin → Dashboard shows system-wide pending leave count and actions.

#### 19. Logout Security: Back-button Attack
- Separate dedicated TC (not merged with TC_LOG_06): After logout, press browser Back button → should redirect to Login page, NOT show cached dashboard data.

---

## Part 2 — Test Plan Improvements

### 🔴 CRITICAL — Must Fix

#### 1. Missing: Communication Plan
- **What:** Enterprise test plans always include a Communication Plan defining:
  - Who gets daily test status? (PM, BA, Dev Lead)
  - In what format? (Email, Excel report, Standup)
  - At what frequency? (Daily by EOD, Weekly summary)
  - Escalation path for P0 blockers?
- **Why:** Without this, stakeholders don't know where to find status, causing unnecessary interruptions to the QA team.

---

#### 2. Missing: Test Metrics / KPIs Section
- **What:** The plan defines exit criteria but never defines how quality will be *measured* throughout testing.
- **Add a Metrics section with:**

  | Metric | Formula | Target |
  |---|---|---|
  | TC Execution Rate | Executed / Total × 100 | ≥ 95% |
  | TC Pass Rate | Passed / Executed × 100 | ≥ 95% |
  | Defect Density | Defects / TC Count | < 0.3 |
  | Defect Leakage | Bugs found in UAT / Total bugs | < 5% |
  | Reopen Rate | Reopened defects / Total fixed | < 10% |

---

#### 3. Missing: Test Closure Criteria (Distinct from Exit Criteria)
- **What:** Exit criteria says *when to stop testing*. Closure criteria says *when the entire QA engagement is formally closed*.
- **Add:**
  - All deliverables submitted and acknowledged
  - Test Summary Report approved by QA Lead and PM
  - All defects dispositioned (Closed / Deferred / Rejected)
  - Lessons Learned session conducted
  - QA sign-off email sent

---

### 🟡 HIGH IMPACT — Should Add

#### 4. Expand Section 5 (Test Strategy) — Regression Strategy
- **What:** The Test Plan says "Run regression after each fix" but doesn't define:
  - What IS the regression suite? (Which TCs? All 48? Just Smoke?)
  - What triggers a full regression vs partial regression?
  - How are new TCs added to the regression suite?
- **Add:**
  > Full Regression (all 48 TCs) is triggered when: major new build, > 3 P1 defects resolved in one batch.
  > Partial Regression (Smoke + impacted module TCs) is triggered when: isolated bug fix in one module.

---

#### 5. Add: Test Independence Principle
- **What:** Explicitly state that test execution is independent of development — QA team does not get "pre-briefed" on which features are fixed to avoid bias.

---

#### 6. Expand Risk Table — Add Probability Score
- **What:** Current risk table rates `Probability` as High/Medium/Low text only. Add a numeric probability (%) and Risk Score (Probability × Impact) for proper risk prioritization.
- **Example:**
  | Risk | Prob % | Impact | Risk Score | Mitigation |
  |---|---|---|---|---|
  | Demo environment reset | 70% | High (3) | 2.1 | Re-create data each session |

---

#### 7. Add: Assumptions Section (Distinct from Scope)
- **What:** Many assumptions are scattered through the document. Consolidate into a dedicated Assumptions section:
  - The demo environment closely mirrors a production deployment
  - Defect fixes won't require changes to approved test cases
  - Business Analysts will respond to queries within 1 business day
  - No major requirement changes will occur after test cases are signed off

---

#### 8. Add: Dependencies Section
- **What:** Explicitly list what the QA team is *waiting on* from other teams before they can proceed:
  - Dev Team: Stable build deployed to QA environment
  - BA Team: FSD finalized and signed off
  - Environment Team: Test accounts and data pre-loaded
  - PM: Sprint schedule and milestone dates confirmed

---

#### 9. Strengthen Section 14 (Schedule) — Add Effort Estimates
- **What:** Current schedule gives duration but not effort (person-hours).
- **Add an Effort column:**
  | Phase | Duration | Effort |
  |---|---|---|
  | Planning & Setup | 2 days | 8 person-hours |
  | Smoke Testing | 1 day | 4 person-hours |
  | Functional Testing | 5 days | 40 person-hours |
  | Security Testing | 1 day | 6 person-hours |
  | Regression | 2 days | 12 person-hours |
  | UAT Support | 2 days | 8 person-hours |
  | Closure | 1 day | 4 person-hours |
  | **Total** | **14 days** | **82 person-hours** |

---

#### 10. Add: Non-Functional Test Approach (even if out-of-scope)
- **What:** Even if performance testing is out-of-scope, the Test Plan should acknowledge it and state that a separate Non-Functional Test Plan will be created for Phase 2.
- **Why:** Auditors and stakeholders expect this acknowledgment. Its absence suggests the team hasn't thought about it.

---

### 🟢 MEDIUM — Nice to Have

#### 11. Add a Test Plan Version Control Table
- Track changes between versions: v0.1 Draft → v1.0 Baselined → v1.1 (post first cycle update)

#### 12. Glossary — Add OrangeHRM-specific Terms
- Add: HRIS, Entitlement, Punch-In/Out, Timesheet Cycle, ESS workflow

#### 13. Appendix: Smoke Test Suite Quick Reference
- Add a 1-page Appendix listing just the 7 Smoke TC IDs with Title and Expected Result for quick field use.

#### 14. Appendix: Defect Priority Decision Matrix
- A 2×2 grid mapping Severity vs Business Impact to Priority. Eliminates tester/dev disagreements about defect priority.

---

## Suggested Action Plan

| Priority | Action | Owner | Effort |
|---|---|---|---|
| P0 | Add missing Change Password TCs | QA Engineer | 1 hour |
| P0 | Add IDOR, CSRF, back-button security TCs | QA Lead | 2 hours |
| P0 | Add Communication Plan to Test Plan | QA Lead | 1 hour |
| P0 | Add Test Metrics / KPIs section | QA Lead | 1 hour |
| P1 | Add `Defect ID`, `Tested By`, `Comments` columns to TC sheet | QA Engineer | 30 min |
| P1 | Add Smoke boolean filter column | QA Engineer | 15 min |
| P1 | Add Admin — Job/Org config TCs | QA Engineer | 2 hours |
| P1 | Add Leave negative TCs (weekend, past date, reverse range) | QA Engineer | 1.5 hours |
| P1 | Expand Regression Strategy in Test Plan | QA Lead | 1 hour |
| P2 | Add Effort column to Schedule | QA Lead | 30 min |
| P2 | Add Assumptions & Dependencies sections | QA Lead | 1 hour |
| P2 | Multi-browser Smoke matrix rows in TC sheet | QA Engineer | 1 hour |
| P3 | Appendix: Smoke quick reference, Defect matrix | QA Lead | 1 hour |

**Total estimated improvement effort: ~14 person-hours**
**Expected quality uplift: Test Cases 7.8 → 9.5 | Test Plan 8.5 → 9.5**

---

*Analysis by QA Lead — April 2026*
