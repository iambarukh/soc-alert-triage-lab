# Brute Force Login Simulation

## What is Brute Force?
An attacker repeatedly tries wrong passwords to gain access.
Windows logs each failed attempt as Event ID 4625.

## Simulation Script (PowerShell)
```powershell
$username = "FakeUser"
$password = "wrongpass"

for ($i = 1; $i -le 10; $i++) {
    $secpass = ConvertTo-SecureString $password -AsPlainText -Force
    $cred = New-Object System.Management.Automation.PSCredential($username, $secpass)
    try {
        Start-Process cmd -Credential $cred -ArgumentList "/c echo test" -ErrorAction Stop
    } catch {
        Write-Host "Failed attempt $i"
    }
}
Write-Host "Brute force simulation complete!"
```

## Expected Windows Event
- Event ID: 4625
- Log: Security
- Meaning: Failed login attempt

## Detection Query
See `04-brute-force-detection.png`