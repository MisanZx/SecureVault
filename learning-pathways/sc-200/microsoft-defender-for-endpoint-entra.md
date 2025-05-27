# Microsoft Defender for Endpoint (Entra)

Intro

Microsoft Defender for Endpoint is a cloud-native endpoint security platform that provides visibility, cyberthreat protection, and EDR capabilities to stop cyberattacks across Windows, macOS, Linux, Android, iOS, and IoT devices.



MS Learn Topics:

* Introduction to Microsoft Defender for Endpoint (✔)
* Deploy the Microsoft Defender for Endpoint environment (✔)
* Implement Windows security enhancements with Microsoft Defender for Endpoint (✔)
* Perform device investigation in Microsoft Defender for Endpoint (✔)
* Perform actions on a device using Microsoft Defender for Endpoint (✔)
* Perform evidence and entities investigations using Microsoft Defender for Endpoint (✔)
* Configure and manage automation using Microsoft Defender for Endpoint (✔)
* Configure for alerts and detections in Microsoft Defender for Endpoint (✔)
* Utilise Vulnerability Management in Microsoft Defender for Endpoint (✔)



#### Getting Started

You need a subscription to the Microsoft Defender for Endpoint online service so that it can be managed.

Threat hunting: You can proactively inspect events in your network using a powerful search and query tool.



#### Deploy Defender for Endpoint

You need to firstly onboard your devices from settings > endpoint

For the network configuration Autodiscovery methods:

* Transparent proxy
* Web Proxy Autodiscovery Protocol (WPAD)

Default data retention is 6 months.

The Manage portal system settings permission allows the configuration of storage settings.



#### Attack Surface Reduction (ASR)

Attack Surface Reduction is the hardening of places threat is likely to attack



| Solution                       | Description                                                                                                                                                                                                                              | My Recommendations |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| Attack surface reduction rules | Reduce vulnerabilities (attack surfaces) in your applications with intelligent rules that help stop malware. (Requires Microsoft Defender Antivirus).Hardware-based isolation                                                            |                    |
| Hardware-based isolation       | Protect and maintain the integrity of a system as it starts and while it's running. Validate system integrity through local and remote attestation. Use container isolation for Microsoft Edge to help guard against malicious websites. |                    |
| Application control            | Use application control so that your applications must earn trust in order to run.                                                                                                                                                       |                    |
| Exploit protection             | Help protect operating systems and apps your organization uses from being exploited. Exploit protection also works with third-party antivirus solutions.                                                                                 |                    |
| Network protection             | Extend protection to your network traffic and connectivity on your organization's devices. (Requires Microsoft Defender Antivirus)                                                                                                       |                    |
| Web protection                 | Secure your devices against web threats and help you regulate unwanted content.                                                                                                                                                          |                    |
| Controlled folder access       | Help prevent malicious or suspicious apps (including file-encrypting ransomware malware) from making changes to files in your key system folders (Requires Microsoft Defender Antivirus)                                                 |                    |
| Device control                 | Protects against data loss by monitoring and controlling media used on devices, such as removable storage and USB drives, in your organization.                                                                                          |                    |



#### Live Response

Make sure the advanced option is turned on before starting.

One of the main reasons you may use this is to check after MS have removed a malicous file is to check the file has been removed.

library command only works after you have uploaded your .ps1 script

then you can use the run "scriptname" to run the script.

fileinfo "path" to get more info

getfile "path"

You can use the command log to show your history.

All of the data is audited and any actions will be put in the actions and remeditations center.

#### Vulnerability Management

In the Vulnerable Device Report, the Exploit availability graph shows each device counted once only of the known exploit.

Threat analytics - This dashboard provides a list of the most recently published threats.
