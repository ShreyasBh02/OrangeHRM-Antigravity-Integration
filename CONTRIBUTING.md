# Contributing to OrangeHRM Manual Testing Project

Thank you for contributing to this project! Please follow these guidelines to keep the test suite consistent and professional.

---

## How to Contribute

### 1. Fork and Branch
- Fork this repository
- Create a branch named after what you're adding:
  - `feature/add-recruitment-module-tcs`
  - `fix/update-leave-tc-expected-result`
  - `docs/update-readme`

### 2. Adding New Test Cases

Follow the TC naming convention strictly:

| Module | Prefix | Example |
|---|---|---|
| Login / Password | `TC_LOG_` | `TC_LOG_15` |
| Admin | `TC_ADM_` | `TC_ADM_14` |
| PIM | `TC_PIM_` | `TC_PIM_14` |
| Leave | `TC_LEV_` | `TC_LEV_15` |
| Time | `TC_TIM_` | `TC_TIM_09` |
| Dashboard | `TC_DSH_` | `TC_DSH_07` |
| Cross-Browser | `TC_FF_` | `TC_FF_08` |

### 3. Required Fields for Every TC

Every new TC must have ALL of the following filled in:

- [ ] TC ID (sequential, no gaps)
- [ ] Req. ID mapped to TS_001–TS_006 (or new TS if adding a new module)
- [ ] Test Case Title — action verb + what is being verified
- [ ] Pre-requisites — exact system state before execution
- [ ] Test Steps — numbered, action-by-action
- [ ] Test Data — exact values, NOT "enter valid data"
- [ ] Expected Result — exact UI message text in **bold**, NOT vague phrases
- [ ] Priority — High / Medium / Low
- [ ] Test Type — Smoke / Functional / Regression / Security
- [ ] Smoke Suite — Y or N only
- [ ] Test Environment — e.g., Chrome 118 / Win 11

### 4. Expected Result Quality Standard

**BAD (do NOT use):**
> "System shows an error message"

**GOOD (always use):**
> System displays inline error: **"Leave Balance Exceeded"**. The Apply button remains disabled. No record is created.

### 5. After Adding TCs

- Update the **Test Execution Summary Tracker** sheet in the Excel file
- Update the **RTM** section in the Test Plan if a new Test Scenario (TS) is introduced
- Update **CHANGELOG.md** under the next version

### 6. Submitting a Pull Request

- PR title format: `[Module] Add TC for [feature]` e.g., `[Leave] Add TC for back-dated leave restriction`
- PR description must list: module, TC IDs added, reason/gap being covered
- All new TCs must follow the quality standard above — PRs with vague ERs will be rejected

---

## Adding a Bug Report

Use the `Bug_Report_Template.md` file. Fill all fields. Never submit a bug report without a screenshot.

---

## Questions

Open a GitHub Issue with the tag `question` if you need clarification on scope, module behavior, or expected results.

---

*OrangeHRM Manual Testing Project — Contributing Guide v1.0*
