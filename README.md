# 🟠 OrangeHRM — Manual Testing Project

![Project](https://img.shields.io/badge/Project-OrangeHRM%20v5.0-orange?style=flat-square)
![Test Cases](https://img.shields.io/badge/Test%20Cases-75-blue?style=flat-square)
![Modules](https://img.shields.io/badge/Modules%20Covered-7-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Baselined%20v3.0-brightgreen?style=flat-square)
![Security TCs](https://img.shields.io/badge/Security%20TCs-11-red?style=flat-square)
![Maturity](https://img.shields.io/badge/QA%20Maturity-Level%204-purple?style=flat-square)

---

## Project Overview

This repository contains the complete **Manual Testing Suite** for **OrangeHRM Version 5.0**, an open-source Human Resource Management System (HRIS).

The testing suite is designed to an **enterprise-grade, Level 4 QA Maturity** standard — covering functional workflows, security vulnerabilities, role-based access control, negative/boundary conditions, and cross-browser validation.

**Application Under Test:**
> `https://opensource-demo.orangehrmlive.com/web/index.php/auth/login`

---

## User Roles Tested

| Role | Username | Password | Access Level |
|---|---|---|---|
| **Admin** | `Admin` | `admin123` | Full system control |
| **ESS (Employee Self-Service)** | `jdoe_ess` | `Test@1234` | Own data only |
| **Supervisor** | `sup_test` | `Sup@1234` | Team data + approvals |

---

## Project File Structure

```
OrangeHRM-Manual-Testing/
│
├── README.md                           ← Project overview and execution guide
│
├── OrangeHRM_Test_Plan.docx            ← Official Test Plan (Word document)
├── OrangeHRM_Test_Plan.md              ← Test Plan (Markdown source)
│
├── OrangeHRM_Manual_Test_Cases.xlsx    ← Test Cases (Excel — Primary execution file)
├── OrangeHRM_Manual_Test_Cases.md      ← Test Cases (Markdown source)
│
└── OrangeHRM_Test Case.xlsx            ← Reference file (original format)
```

---

## Test Suite Summary

| Module | Total TCs | Smoke | Functional | Security | Regression |
|---|---|---|---|---|---|
| Login / Password Management | 14 | 2 | 7 | 5 | 0 |
| Admin | 13 | 0 | 10 | 3 | 0 |
| PIM (Personnel Information) | 13 | 1 | 9 | 3 | 0 |
| Leave Management | 14 | 2 | 12 | 0 | 0 |
| Time and Attendance | 8 | 1 | 6 | 0 | 1 |
| Dashboard and Directory | 6 | 1 | 5 | 0 | 0 |
| Cross-Browser Smoke (Firefox) | 7 | 7 | 0 | 0 | 0 |
| **TOTAL** | **75** | **14** | **49** | **11** | **1** |

---

## File Descriptions

### 1. Test Plan (`OrangeHRM_Test_Plan.docx`)

The governing test plan document. Contains:

- Test objectives and scope (in-scope + explicitly out-of-scope)
- 8 Assumptions and 7 external Dependencies
- Test strategy: risk-based black-box, role rotation, exploratory sessions
- Design techniques: BVA, EP, State Transition, Error Guessing, Role Matrix
- Regression strategy: Full vs Partial triggers clearly defined
- Entry, Exit, and Closure criteria (separate sections)
- 10 Test Metrics and KPIs with formulas and targets
- Communication Plan: daily/weekly reporting + escalation path
- Defect Management: lifecycle, SLAs, full report template
- Risk and Mitigation: 8 risks with probability %, impact, and risk scores
- 14-day Schedule with effort estimates (90 person-hours total)
- Requirements Traceability Matrix (RTM)
- Appendix A: Smoke Suite Quick Reference
- Appendix B: Defect Priority Decision Matrix
- Appendix C: Effort Summary by role
- Appendix D: Full Glossary

---

### 2. Test Cases (`OrangeHRM_Manual_Test_Cases.xlsx`)

The primary test execution workbook. Sheets:

| Sheet | Contents |
|---|---|
| Summary | Execution dashboard — total counts by type and module |
| Legend | Column definitions |
| 1. Login, Logout and Password | 14 TCs — login flows, session, security, change password |
| 2. Admin Module | 13 TCs — user CRUD, job/org config, access control, SMTP |
| 3. PIM Module | 13 TCs — employee CRUD, tabs, IDOR, termination, search filters |
| 4. Leave Module | 14 TCs — apply, approve, reject, cancel, entitlement, calendar |
| 5. Time Module | 8 TCs — timesheets, attendance, 24hr boundary, project reports |
| 6. Dashboard and Directory | 6 TCs — widgets, directory, quick launch, role-based views |
| 7. Cross-Browser Smoke (Firefox) | 7 TCs — Smoke suite re-executed in Firefox |
| Test Execution Summary Tracker | Final roll-up table with Pass/Fail/Blocked counts |

**Column Reference:**

| Column | Description |
|---|---|
| TC ID | Unique identifier (e.g., TC_LOG_01) |
| Req. ID | Linked Test Scenario ID (TS_001 to TS_006) |
| Test Case Title | What is being verified |
| Pre-requisites | System state required before execution |
| Test Steps | Numbered, step-by-step instructions |
| Test Data | Exact values to enter |
| Expected Result (ER) | Precise outcome with exact UI message text |
| Priority | High / Medium / Low |
| Test Type | Smoke / Functional / Regression / Security |
| Smoke Suite | Y = Run on every new build first; N = Full cycle only |
| Test Environment | Browser + OS (e.g., Chrome 118 / Win 11) |
| Version Tested | OrangeHRM build version during execution |
| Date Tested | Date of execution |
| Tested By | Tester who executed this TC |
| Actual Result | Observed behavior during execution |
| Defect ID | Defect ticket ID if TC status is Fail |
| Pass/Fail/Not Executed/Deferred | Final execution status |
| Comments / Notes | Blockers, partial results, environment notes |

---

## How to Execute

### Step 1 — Verify Environment

Before starting any testing, confirm:

```
Application URL: https://opensource-demo.orangehrmlive.com

Accounts active:
  Admin      → admin / admin123
  ESS User   → jdoe_ess / Test@1234
  Supervisor → sup_test / Sup@1234

Test data preloaded per each module's "Module Setup" section in the TC file.
Browser: Chrome v118+ on Windows 11 (primary).
```

### Step 2 — Run Smoke Suite First

Filter Excel by **Smoke Suite = Y** and execute all 14 TCs.

- All 14 Pass → proceed to full execution
- Any Fail → log defect, notify Dev, do NOT start full cycle until resolved

### Step 3 — Full Functional Execution

Execute TCs by module in order:

```
1. Login / Password       TC_LOG_01 → TC_LOG_14
2. Admin                  TC_ADM_01 → TC_ADM_13
3. PIM                    TC_PIM_01 → TC_PIM_13
4. Leave                  TC_LEV_01 → TC_LEV_14
5. Time                   TC_TIM_01 → TC_TIM_08
6. Dashboard              TC_DSH_01 → TC_DSH_06
7. Cross-Browser Smoke    TC_FF_01  → TC_FF_07
```

### Step 4 — Security Testing (QA Lead)

Execute all TCs where **Test Type = Security** (11 TCs).
Requires browser DevTools open for TC_LOG_11 (password-in-URL check).

### Step 5 — Record Results

For every executed TC, fill in the Excel row:

```
Date Tested     → today's date
Tested By       → your name
Actual Result   → observed behavior (copy screen message exactly)
Status          → Pass / Fail / Blocked / Deferred
Defect ID       → paste defect ticket ID if Failed
Comments        → any partial result or blocker info
```

### Step 6 — Log Defects

If a TC fails:
1. Screenshot the failure
2. Log a defect using the template in Test Plan Section 16.3
3. Enter the Defect ID in the TC row
4. Notify QA Lead and Developer within 30 minutes for P0/P1

---

## Entry and Exit Criteria

### Entry Criteria (Testing may BEGIN when)

| # | Gate |
|---|---|
| 1 | App URL accessible and responsive |
| 2 | All test accounts active and unlocked |
| 3 | Test data preloaded per all Module Setup sections |
| 4 | TCs reviewed and signed off by Business Analyst |
| 5 | Defect tracking Excel workbook ready and shared |

### Exit Criteria (Testing is COMPLETE when)

| # | Condition |
|---|---|
| 1 | 100% of Smoke TCs = Pass |
| 2 | 95% or more of all 75 TCs executed |
| 3 | 95% or more pass rate on executed TCs |
| 4 | Zero open P0 or P1 defects |
| 5 | UAT sign-off received from Product Owner |
| 6 | Test Summary Report delivered |

---

## Security Testing Coverage

| Attack Type | TC ID | What is Verified |
|---|---|---|
| SQL Injection | TC_LOG_10 | `admin' OR '1'='1` in username field — access must be denied |
| XSS | TC_ADM_07 | `<script>alert('XSS')</script>` in role name — must not execute |
| Session Timeout | TC_LOG_09 | 30-min idle → forced re-login |
| URL Bypass | TC_ADM_06 | ESS user direct URL to Admin routes → Access Denied |
| Back-button Attack | TC_LOG_07 | Browser Back after logout → cannot restore session |
| Password in URL | TC_LOG_11 | Credentials never visible in URL, query string, or browser history |
| IDOR | TC_PIM_12 | ESS changes `empNumber` in URL to access another user → blocked |
| Financial Data Isolation | TC_PIM_11 | ESS cannot access another employee's Direct Deposit via URL |

---

## Defect Severity Reference

| Priority | Fix SLA | Example |
|---|---|---|
| P0 — Critical | < 24 hours | Cannot login, data loss, security breach |
| P1 — High | < 48 hours | Leave approval fails, timesheet not saving |
| P2 — Medium | 3–5 business days | Search returns partial results, UI form issue |
| P3 — Low | Next release | Button misalignment, tooltip typo |

---

## Quality Metrics Targets

| Metric | Formula | Target |
|---|---|---|
| TC Execution Rate | Executed / Total x 100 | 95% or more |
| TC Pass Rate | Passed / Executed x 100 | 95% or more |
| Defect Density | Total Defects / Total TCs | Less than 0.3 |
| Defect Leakage (to UAT) | UAT Bugs / All Bugs x 100 | Less than 5% |
| Defect Reopen Rate | Reopened / Fixed x 100 | Less than 10% |

---

## Modules Covered

| Module | Key Features Tested |
|---|---|
| Login / Password | Valid/invalid login, masking, case-sensitivity, forgot/change password, session expiry, SQL injection, back-button attack |
| Admin | User CRUD, bulk delete, username validation, access restriction, XSS, SMTP, Job Titles, Locations, Pay Grades, user group privileges |
| PIM | Add employee, photo upload limits, duplicate ID, edit details, emergency contacts, dependants, immigration, termination, IDOR, search filters |
| Leave | Full-day/half-day apply, balance check, holiday exclusion, weekend date, past date, overlap, approve, reject, cancel pending/approved, entitlement, calendar |
| Time | Timesheet submit, 24hr boundary, empty activity lock, read-only on submit, supervisor approval, punch-in/out context, attendance history, project reports |
| Dashboard | Widget rendering, leave counter accuracy, directory search, quick launch routing, ESS vs Admin view difference |

---

## Tools Used

| Tool | Purpose |
|---|---|
| Microsoft Excel | Test execution tracker and defect log |
| Microsoft Word | Test Plan documentation |
| Google Chrome v118+ | Primary test browser |
| Mozilla Firefox v118+ | Cross-browser smoke validation |
| Browser DevTools (F12) | Network tab — security TC verification |
| OrangeHRM Demo | Application Under Test |

---

## Contributing — TC Naming Convention

When adding new test cases, follow these rules:

| Rule | Detail |
|---|---|
| TC ID format | `TC_[MODULE]_[NUMBER]` e.g., `TC_LOG_15`, `TC_ADM_14` |
| Req. ID | Always map to a TS ID (`TS_001` to `TS_006`) |
| Expected Result | Must include exact UI text — no vague phrases like "system shows error" |
| Test Type | Set correctly: Smoke / Functional / Regression / Security |
| Smoke Suite | Set Y only for truly critical TCs — keep to max 15 total |
| Summary Tracker | Update the tracker sheet after adding new TCs |

---

## Test Schedule at a Glance

| Phase | Days | Effort |
|---|---|---|
| Planning and Setup | 1–2 | 8 hrs |
| Smoke Testing | 3 | 4 hrs |
| Functional Testing Cycle 1 | 3–7 | 40 hrs |
| Defect Triage | 8 | 4 hrs |
| Security Testing | 9–10 | 6 hrs |
| Regression Cycle 2 | 10–11 | 12 hrs |
| UAT | 12–13 | 8 hrs |
| Closure and Sign-off | 14 | 4 hrs |
| **Total** | **14 days** | **86 hrs** |

---

## Version History

| Version | Date | Changes |
|---|---|---|
| v1.0 | 2026-04-18 | Initial creation — 19 TCs across 5 modules |
| v2.0 | 2026-04-18 | Level 4 upgrade — 48 TCs, Req. ID, Test Type, Test Environment, Security TCs, precise ERs |
| v3.0 | 2026-04-18 | Final enterprise grade — 75 TCs, new columns (Smoke Suite, Tested By, Defect ID, Comments), Change Password, Admin Job/Org config, IDOR, back-button, leave negatives, cross-browser suite |

---

## License

This testing project is created for educational and QA practice purposes using the publicly available OrangeHRM demo environment.

> OrangeHRM is an open-source HRMS — https://www.orangehrm.com

---

*OrangeHRM AI-Assisted Manual Testing Project | QA Maturity Level 4 | v3.0*
