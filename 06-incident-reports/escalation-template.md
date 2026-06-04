# Escalation Template — L1 to L2 Handoff

## Escalation Details
- **From:** L1 Analyst — Barukh Aswad
- **To:** L2 Analyst / Incident Responder
- **Priority:** HIGH
- **Date/Time:** 0/04/2026

## Reason for Escalation
Multiple attack stages detected on host — brute force followed
by privilege escalation and persistence. Full compromise suspected.

## What I Found 
1. Brute force attack — 10 failed logins on FakeUser
2. New admin account created — HackerUser
3. Encoded PowerShell executed
4. Two persistence mechanisms installed

## Evidence Collected
- Splunk search: index=wineventlog EventCode=4625
- Dashboard: SOC Alert Triage Overview
- Screenshots: attached

## Immediate Actions Taken
-  Alert acknowledged in Splunk
-  Incident report created
-  Escalated to L2

## Recommended Next Steps for L2
- Full memory forensics on affected host
- Check lateral movement to other systems
- Investigate HackerUser login history
