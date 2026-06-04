# Incident Report — SOC Alert Triage Lab

## Incident Summary
- **Date:** 06/04/2026
- **Analyst:** Barukh Aswad
- **Severity:** High
- **Status:** Resolved 

## Timeline
| Time | Event |
|------|-------|
| T+00 | Multiple failed login attempts detected (Event ID 4625) |
| T+05 | Brute force alert triggered 10 failed logins in 5 min |
| T+10 | New user "HackerUser" created and added to Administrators |
| T+15 | Suspicious encoded PowerShell command executed |
| T+20 | Scheduled task "WindowsUpdateHelper" created for persistence |
| T+25 | Registry Run key modified for persistence |

## Detection Details

### Alert 1 — Brute Force Attack
- **Event ID:** 4625
- **Account Targeted:** FakeUser
- **Failed Attempts:** 10
- **Timeframe:** 5 minutes
- **Verdict:** True Positive

### Alert 2 — Backdoor User Created
- **Event ID:** 4720, 4732
- **New Account:** HackerUser
- **Group Added To:** Administrators
- **Verdict:** True Positive

### Alert 3 — Suspicious PowerShell
- **Event ID:** Sysmon 1
- **Command:** Encoded command (-EncodedCommand flag)
- **Verdict:** True Positive

### Alert 4 — Persistence via Scheduled Task
- **Event ID:** 4698
- **Task Name:** WindowsUpdateHelper
- **Trigger:** On Logon
- **Verdict:** True Positive

### Alert 5 — Registry Persistence
- **Event ID:** Sysmon 13
- **Registry Key:** HKCU\...\CurrentVersion\Run
- **Verdict:** True Positive

## IOCs (Indicators of Compromise)
- Username: HackerUser
- Scheduled Task: WindowsUpdateHelper
- Registry Key: HKCU\Software\Microsoft\Windows\CurrentVersion\Run\WindowsHelper
- PowerShell flag: -EncodedCommand

## False Positive vs True Positive Analysis
| Alert | Classification | Reason |
|-------|---------------|--------|
| Multiple failed logins | True Positive | 10 failures in 5 min — not normal |
| New admin user | True Positive | Unexpected account creation |
| Encoded PowerShell | True Positive | Legitimate software rarely uses -EncodedCommand |
| Scheduled task | Investigate | Could be legitimate check task content |
| Registry Run key | True Positive | Hidden PowerShell in Run key is suspicious |

## Recommendations
1. Disable HackerUser account immediately
2. Remove WindowsUpdateHelper scheduled task
3. Remove registry Run key entry
4. Reset credentials of targeted accounts
5. Enable PowerShell Script Block Logging

## Escalation Decision
- Escalate to L2: YES
- Reason: Multiple persistence mechanisms found, possible full compromise
