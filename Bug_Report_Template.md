# Bug Report Template

**Use this template every time a TC status = FAIL.**
Copy and fill this into the Defect Tracking Excel workbook.

---

## Bug Report

| Field | Value |
|---|---|
| **Bug ID** | BUG-[auto-number] |
| **Module** | [Login / Admin / PIM / Leave / Time / Dashboard] |
| **Req. ID** | [TS_001 / TS_002 / TS_003 / TS_004 / TS_005 / TS_006] |
| **Linked TC ID** | [e.g., TC_LEV_03] |
| **Bug Summary** | [Action] causes [Error] when [Condition] |
| **Severity** | [Critical / High / Medium / Low] |
| **Priority** | [P0 / P1 / P2 / P3] |
| **Status** | New |
| **Environment** | [Chrome 118 / Win 11] |
| **App Version** | 5.0 |
| **Reported By** | [Your Name] |
| **Date Reported** | [YYYY-MM-DD] |
| **Assigned To** | [Developer Name] |

---

## Pre-requisites

> Describe the system state that must exist BEFORE the steps below can be reproduced.

- [ ] User logged in as: [Admin / ESS / Supervisor]
- [ ] [Other relevant state...]

---

## Steps to Reproduce

1. Navigate to [Module > Sub-menu]
2. [Action taken]
3. [Input entered]
4. [Button clicked]
5. [Result observed]

---

## Expected Result

> Paste the exact Expected Result from the TC's ER column.

```
[Exact expected behavior or exact UI message text]
```

---

## Actual Result

> What actually happened — be as specific as possible. Include exact error messages.

```
[Observed behavior / exact error shown]
```

---

## Impact

> What is the business impact of this bug? Which workflows are blocked?

[e.g., ESS users cannot apply for leave — core HR workflow completely broken]

---

## Attachments

| File | Description |
|---|---|
| `screenshot_01.png` | Screenshot of the failure state |
| `recording.mp4` | Screen recording of reproduction steps (optional) |
| `console_log.txt` | Browser console errors (for JS/Security bugs) |

---

## Fix Verification Steps

> To be filled by QA when re-testing after the developer marks the bug as Fixed.

- [ ] Fix deployed to QA environment on [Date]
- [ ] Reproduced the original steps above
- [ ] Expected result now matches — bug resolved
- [ ] Regression check: [Related TCs re-run — all Pass]
- [ ] Status updated to: **Closed / Reopened**

---

## Defect Lifecycle Quick Reference

```
New → Open → In Progress → Fixed → Verified → Closed
                                 ↘ Reopened → In Progress
                    ↘ Deferred / Rejected (Product Owner approval required)
```

---

## Severity / Priority Matrix

| Severity vs Impact | High Business Impact | Low Business Impact |
|---|---|---|
| High Severity | P0 — Critical | P1 — High |
| Low Severity | P2 — Medium | P3 — Low |

---

*OrangeHRM Manual Testing Project — Bug Report Template v1.0*
