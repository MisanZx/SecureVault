---
description: Update 7-zip the latest version and remove other version
---

# 7-Zip

## Intro

7-Zip is common package that is used around the world by which many devices.

Software mangement is an important part of the SDLC so makes this very important to update and patch accordingly.

## Other Useful Info

* **Better control:** The .exe installer gives the developers more flexibility to manage the installation steps compared to the .msi format.&#x20;
* **Official recommendation:** The 7zip website advises users to download and use the .exe version.&#x20;
* **MSI limitations:** Some users report issues with the .msi installer, like less customization options and potential conflicts with other software.&#x20;

## Requirements

7-Zip for some reason installs (patch only) which keeps the old version still installed on the end users'  machine by which could be open the vulnerabilities so there is a requirement to patch it and REMOVE the old versions.



## The Script

This Poweshell script will install the version you place int he variable.

Happy scripting



Last tested and confirmed wokring 09/02/2025

```powershell
#Welcome to MisanZX Powershell Script

# Define the 7-Zip download URL for the latest version (64-bit version in this case)
$downloadUrl = "https://www.7-zip.org/a/7z2409-x64.exe" # replace url if new version

# Define the download and installation paths
$installerPath = "$env:TEMP\7z_installer.exe"

# Function to uninstall all versions of 7-Zip
function Uninstall-7Zip {
    # Get all installed programs with "7-Zip" in their name
    $installedPrograms = Get-WmiObject -Class Win32_Product | Where-Object { $_.Name -like "*7-Zip*" }

    foreach ($program in $installedPrograms) {
        Write-Host "Uninstalling: $($program.Name)"
        $program.Uninstall() | Out-Null
    }
}

# Uninstall all existing versions of 7-Zip
Uninstall-7Zip

# Download the latest 7-Zip installer
Write-Host "Downloading the latest 7-Zip installer..."
Invoke-WebRequest -Uri $downloadUrl -OutFile $installerPath

# Install the latest version of 7-Zip
Write-Host "Installing the latest version of 7-Zip..."
Start-Process -FilePath $installerPath -ArgumentList "/S" -Wait

# Clean up the installer
Remove-Item -Path $installerPath

Write-Host "7-Zip installation completed."
```



