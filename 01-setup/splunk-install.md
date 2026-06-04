# Splunk Installation Guide

## Download
- URL: https://www.splunk.com/en_us/download/splunk-enterprise.html
- Version: Splunk Enterprise Free
- Platform: Windows 64-bit MSI

## Installation Steps
1. Run MSI installer as Administrator
2. Accept license agreement
3. Set username: khan88
4. Set password: (strong password)
5. Install on local system

## Post-Installation Configuration

### Enable Receiving Port
```
Settings → Forwarding and Receiving
→ Configure Receiving → New Receiving Port
→ Port: 9997 → Save
```

### Create Index
```
Settings → Indexes → New Index
→ Index Name: wineventlog
→ Save
```

## Access
- URL: http://192.168.74.128:8000
- Username: admin

## Screenshot
See `04-screenshots/02-splunk-dashboard-login.png`