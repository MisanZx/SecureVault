# AD (Active Directory)

#### Usage

A Powershell script to find users that have the "Password Never Expire" attribute enabled.

#### Script

<pre class="language-powershell"><code class="lang-powershell"><strong># script to find users that have the "Password Never Expire" attribute enabled
</strong>
#Import AD module to the session

Import-Module ActiveDirectory

#Search for users and export to CSV

Get-ADUser -Filter * -Properties Name, PasswordNeverExpires | where {
$_.passwordNeverExpires -eq "true" } | Select-Object UserPrincipalName, Name, Enabled | Export-Csv -Path C:\Temp\PwdNeverExpires.csv -NoTypeInformation
cd C:\Temp
start .
</code></pre>

