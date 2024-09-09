---
description: >-
  Provision to MS Teams 2.0 and remove all traces of Teams classic and
  machine-wide installer
---

# MS Teams

Hopefully the script is useful for someone that have the same issue as it took some time as the uninstaller switches provided by Microsoft does not fully tidy up correctly.

Therefore this will locate the areas and clean up.

If this was useful, give me a like and follow me.



{% code overflow="wrap" lineNumbers="true" fullWidth="true" %}
```powershell
# Misan's Teams 2.0
# https://github.com/MisanZx

$PackageName = "MicrosoftTeamsNEW"
$LogPath = "$env:ProgramData\Microsoft\IntuneManagementExtension\Logs\$PackageName-install.log"

# Start transcript logging
Start-Transcript -Path $LogPath -Force

###########################################################
# Teams Classic cleanup
###########################################################

# Function to uninstall Teams Classic
function Uninstall-TeamsClassic($TeamsPath) {
    try {
        $process = Start-Process -FilePath "$TeamsPath\Update.exe" -ArgumentList "--uninstall /s" -PassThru -Wait -ErrorAction STOP

        if ($process.ExitCode -ne 0) {
            Write-Error "Uninstallation failed with exit code $($process.ExitCode)."
        }
    }
    catch {
        Write-Error $_.Exception.Message
    }
}

# Remove Teams Machine-Wide Installer
Write-Host "Removing Teams Machine-wide Installer"

#Windows Uninstaller Registry Path
$registryPath = "HKLM:\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\*"

# Get all subkeys and match the subkey that contains "Teams Machine-Wide Installer" DisplayName.
$MachineWide = Get-ItemProperty -Path $registryPath | Where-Object -Property DisplayName -eq "Teams Machine-Wide Installer"

if ($MachineWide) {
    Start-Process -FilePath "msiexec.exe" -ArgumentList "/x ""$($MachineWide.PSChildName)"" /qn" -NoNewWindow -Wait
}
else {
    Write-Host "Teams Machine-Wide Installer not found"
}

# Get all Users
$AllUsers = Get-ChildItem -Path "$($ENV:SystemDrive)\Users"

# Process all Users
foreach ($User in $AllUsers) {
    Write-Host "Processing user: $($User.Name)"

    # Locate installation folder
    $localAppData = "$($ENV:SystemDrive)\Users\$($User.Name)\AppData\Local\Microsoft\Teams"
    $programData = "$($env:ProgramData)\$($User.Name)\Microsoft\Teams"

    if (Test-Path "$localAppData\Current\Teams.exe") {
        Write-Host "  Uninstall Teams for user $($User.Name)"
        Uninstall-TeamsClassic -TeamsPath $localAppData
    }
    elseif (Test-Path "$programData\Current\Teams.exe") {
        Write-Host "  Uninstall Teams for user $($User.Name)"
        Uninstall-TeamsClassic -TeamsPath $programData
    }
    else {
        Write-Host "  Teams installation not found for user $($User.Name)"
    }
}

# Remove old Teams folders and icons
$TeamsFolder_old = "$($ENV:SystemDrive)\Users\*\AppData\Local\Microsoft\Teams"
$TeamsIcon_old = "$($ENV:SystemDrive)\Users\*\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Microsoft Teams*.lnk"
Get-Item $TeamsFolder_old | Remove-Item -Force -Recurse
Get-Item $TeamsIcon_old | Remove-Item -Force -Recurse

###########################################################
# Registry Cleaner for Teams Classic
###########################################################

# Regex pattern for SIDs
$PatternSID = 'S-1-5-21-\d+-\d+\-\d+\-\d+$'

# Get Username, SID, and location of ntuser.dat for all users
$ProfileList = gp 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList\*' | Where-Object {$_.PSChildName -match $PatternSID} | 
    Select  @{name="SID";expression={$_.PSChildName}}, 
            @{name="UserHive";expression={"$($_.ProfileImagePath)\ntuser.dat"}}, 
            @{name="Username";expression={$_.ProfileImagePath -replace '^(.*[\\\/])', ''}}

# Get all user SIDs found in HKEY_USERS (ntuder.dat files that are loaded)
$LoadedHives = gci Registry::HKEY_USERS | ? {$_.PSChildname -match $PatternSID} | Select @{name="SID";expression={$_.PSChildName}}

# Get all users that are not currently logged
$UnloadedHives = Compare-Object $ProfileList.SID $LoadedHives.SID | Select @{name="SID";expression={$_.InputObject}}, UserHive, Username

# Loop through each profile on the machine
Foreach ($item in $ProfileList) {
    # Load User ntuser.dat if it's not already loaded
    IF ($item.SID -in $UnloadedHives.SID) {
        reg load HKU\$($Item.SID) $($Item.UserHive) | Out-Null
    }

    #####################################################################
    # This is where you can read/modify a users portion of the registry 

    # This example lists the Uninstall keys for each user registry hive
    "{0}" -f $($item.Username) | Write-Output
    Remove-Item -Path registry::HKEY_USERS\$($Item.SID)\software\Microsoft\Windows\CurrentVersion\Uninstall\Teams | 
        Foreach {"{0} {1}" -f "   Program:", $($_.DisplayName) | Write-Output}

    #####################################################################

    # Unload ntuser.dat        
    IF ($item.SID -in $UnloadedHives.SID) {
        ### Garbage collection and closing of ntuser.dat ###
        [gc]::Collect()
        reg unload HKU\$($Item.SID) | Out-Null
    }
}

Write-Host "Removed from each registry path" -ForegroundColor Yellow

###########################################################
# New Teams installation
###########################################################

Write-Host "Installing new Teams"
& '.\teamsbootstrapper.exe' -p

# Stop transcript logging
Stop-Transcript
```
{% endcode %}
