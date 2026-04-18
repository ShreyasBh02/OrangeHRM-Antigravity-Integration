# Changelog
All notable changes to this project are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [v3.0] — 2026-04-18 — Final Enterprise Grade (Current)

### Added
- 4 new columns in TC sheet: `Smoke Suite (Y/N)`, `Tested By`, `Defect ID`, `Comments / Notes`
- 7 new Login TCs: Change Password (correct/wrong/mismatch), Password in URL, Back-button attack after logout
- 3 new Admin TCs: Job Title creation, Location creation, Pay Grade configuration
- 1 new Admin TC: Custom User Group — View-only privilege enforcement
- 2 new PIM TCs: Duplicate Employee ID, IDOR (URL empNumber manipulation)
- 2 new PIM TCs: Edit employee email + Marital Status
- 3 new Leave TCs: Weekend date, Past date, Reverse date range (From > To)
- 1 new Leave TC: Cancel a Pending (not yet approved) leave — distinct from cancel Approved
- 1 new Time TC: ESS user views own attendance records
- 2 new Dashboard TCs: ESS vs Admin widget differentiation
- New Sheet: Cross-Browser Smoke Suite — 7 Smoke TCs re-executed in Firefox
- Test Plan v2.0: Communication Plan, Test Metrics/KPIs, Closure Criteria, Regression Strategy, Assumptions, Dependencies, Effort column in Schedule, 4 new Appendices
- README.md — complete project documentation
- CHANGELOG.md (this file)
- CONTRIBUTING.md
- Bug_Report_Template.md
- Test_Summary_Report_Template.md
- .gitignore
- LICENSE

### Changed
- TC count: 48 → 75 total test cases
- Priority corrected: TC_ADM_04 (delete) elevated from Medium to High
- Security TC count increased from 7 → 11

---

## [v2.0] — 2026-04-18 — Level 4 Upgrade

### Added
- `Req. ID` column for full requirement traceability (TS_001–TS_006)
- `Test Type` column: Smoke / Functional / Regression / Security
- `Test Environment` column: Browser + OS
- 7 Security TCs: SQL Injection, XSS, session timeout, URL bypass, financial data isolation
- 3 new Leave TCs: Cancel approved leave, Admin assign entitlement, Holiday calendar
- 2 new Admin TCs: XSS validation, Admin password reset for ESS
- 2 new PIM TCs: Employee termination block, Direct Deposit access control
- Module-level Test Data Setup blocks in all sections
- Test Plan v1.0: Full 15-section enterprise test plan

### Changed
- TC count: 19 → 48 total test cases
- Expected Results now include exact UI error/success message text
- Priorities corrected across Admin, PIM, Dashboard modules

### Fixed
- Vague Expected Results replaced with precise UI message text
- Missing Pre-conditions made explicit per TC

---

## [v1.0] — 2026-04-18 — Initial Release

### Added
- 19 Manual Test Cases across 5 modules (Admin, PIM, Leave, Time, Dashboard)
- Basic columns: TC ID, Test Scenario, Test Case Title, Pre-requisites, Test Steps, Test Data, Expected Result, Priority
- Initial OrangeHRM_Test Case.xlsx (reference format)
