---
description: >-
  Some useful detection scripts I have used that might be useful for people
  doing the same thing as me.
---

# Intune Detection Scripts



### MS Teams Detection

MS teams is changing from Classic to the "new Teams" therefore if your solution is deploying via Intune, there is a requirement for adding a custom detection rule as the new client does not install the same way in which the previous .msi packages would install. Therefore a different method of detection is required.

```powershell
$AppXPackageName = "MSTeams"

# Get the security identifier (SID) for the current user.
$sid = [System.Security.Principal.WindowsIdentity]::GetCurrent().User.Value

if ($sid -eq 'S-1-5-18') {
    $TeamsInstalled = Get-ProvisionedAppPackage -Online | Where-Object { $_.DisplayName -match $AppXPackageName }
} else {
    $TeamsInstalled = Get-AppxPackage -Name $AppXPackageName
}

if ($TeamsInstalled) {
    Write-Host "Installed"
}
```



### MS Teamsbootstrapper.exe wrapper package

```powershell
#Copies the file and deploys to the endpoint machine
copy-Item .\teamsbootstrapper.exe -Destination "C:\Windows\Temp" -Force
 
#Provisons the new teams for installation
./teamsbootstrapper -p
 
#Removes old teams if it exists
./teamsbootstrapper -u
 
#Remove Teams machine-wide installer xxxxxx
MsiExec.exe /qn /norestart /X{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}

#Removes teamsbootstrapper
remove-Item .\teamsbootstrapper.exe -Destination "C:\Windows\Temp\teamsbootstrapper.exe" -Force
```

note: replace the teams machine-wider installer with your currently deployed package version.

