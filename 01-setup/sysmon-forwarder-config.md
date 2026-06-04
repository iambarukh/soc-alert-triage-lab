# Sysmon + Universal Forwarder Configuration

## Sysmon Installation

### Download
- URL: https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon
- Config: https://github.com/SwiftOnSecurity/sysmon-config

### Install Command
```cmd
cd C:\Tools\Sysmon
sysmon64.exe -accepteula -i sysmonconfig.xml
```

### Verify
```cmd
sc query sysmon64
```
Expected: STATE: 4 RUNNING

## Universal Forwarder Configuration

### inputs.conf Location
```
C:\Program Files\SplunkUniversalForwarder\etc\system\local\inputs.conf
```

### inputs.conf Content
```ini
[WinEventLog://Security]
disabled = 0
index = wineventlog

[WinEventLog://System]
disabled = 0
index = wineventlog

[WinEventLog://Application]
disabled = 0
index = wineventlog

[WinEventLog://Microsoft-Windows-Sysmon/Operational]
disabled = 0
index = wineventlog
sourcetype = XmlWinEventLog:Microsoft-Windows-Sysmon/Operational
```

### Restart Forwarder
```cmd
net stop SplunkForwarder
net start SplunkForwarder
```

## Screenshot
See 02-sysmon-installed-running.png
