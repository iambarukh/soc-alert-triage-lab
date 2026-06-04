# SOC Alert Triage Lab — Splunk SIEM Project

## Overview
A hands-on Security Operations Center (SOC) lab built to simulate
real-world L1 analyst work — ingesting Windows logs, detecting
attacks, triaging alerts, and documenting incidents.

## Architecture
Windows VM → Sysmon → Universal Forwarder → Splunk SIEM → Analyst

## Tools Used
| Tool | Purpose |
|------|---------|
| Splunk Free | SIEM — log ingestion and detection |
| Sysmon | Deep Windows event logging |
| Universal Forwarder | Log shipping to Splunk |
| VMware | Lab virtualization |
| Windows 10 VM | Attack target |

## Attack Scenarios Simulated
1. Brute force login attack (Event ID 4625)
2. Suspicious encoded PowerShell execution
3. Backdoor admin user creation (Event ID 4720/4732)
4. Scheduled task persistence (Event ID 4698)
5. Registry Run key persistence (Sysmon Event ID 13)
6. Reconnaissance commands (whoami, net user)

## Detection Rules (SPL Queries)
All queries are in `03-spl-queries/` folder.

| Detection | File |
|-----------|------|
| Brute force | brute-force-detection.spl |
| PowerShell | powershell-detection.spl |
| New admin user | new-admin-user-detection.spl |
| Persistence | persistence-detection.spl |

## Screenshots
10 key screenshots in `04-screenshots/` showing:
- Lab setup and configuration
- Attack simulations
- Splunk detections and dashboard

## Skills Demonstrated
- SIEM configuration and log ingestion
- Windows event log analysis
- SPL query writing
- Alert triage (True Positive vs False Positive)
- Incident documentation and escalation
