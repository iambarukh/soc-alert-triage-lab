# Suspicious PowerShell Encoded Command

## What is it?
Attackers encode PowerShell commands in Base64 to bypass antivirus.
The -EncodedCommand flag is a major red flag for SOC analysts.

## Simulation Script
```powershell
$cmd = "Write-Host 'This is a suspicious encoded command test'"
$encoded = [Convert]::ToBase64String([Text.Encoding]::Unicode.GetBytes($cmd))
powershell.exe -EncodedCommand $encoded
```

## Why Suspicious?
- Legitimate software rarely uses -EncodedCommand
- Commonly used by malware and attackers
- Sysmon logs full CommandLine (Event ID 1)

## Detection Query
See `06-User Added to Group Detection.png`
