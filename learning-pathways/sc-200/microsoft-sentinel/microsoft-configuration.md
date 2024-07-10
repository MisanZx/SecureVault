---
description: Configure your Microsoft Sentinel environment
---

# Microsoft Configuration

#### Intro

In its simplest form, a SIEM system allows you to:

* Collect and query logs.
* Do some form of correlation or anomaly detection.
* Create alerts and incidents based on your findings.

You may have used or have seen SIEM's in the past such as Darktrace and Splunk.

A SIEM system might offer functionality such as:

* **Log management**: The ability to collect, store, and query the log data from resources within your environment.
* **Alerting**: A proactive look inside the log data for potential security incidents and anomalies.
* **Visualization**: Graphs and dashboards that provide visual insights into your log data.
* **Incident management**: The ability to create, update, assign, and investigate incidents that have been identified.
* **Querying data**: A rich query language, similar to that for log management, that you can use to query and understand your data.

But Overall what is Sentinel?

Microsoft Sentinel gives you an end-to-end solution for security operations.&#x20;

The solution includes:

* Visibility,&#x20;
* Analytics,&#x20;
* Hunting,&#x20;
* Incident management
* Automation.

#### How does Sentinel work?

1. Data Connectors ( Get your data ingested into MS Sentinel )

Examples of these are:

* syslog
* Common Event Format (CEF)
* Trusted Automated eXchange of Indicator Information (TAXII) (for threat intelligence)
* Azure
* AWS services

Other things to know.

Workbooks - use workbooks to visualize your data within Microsoft Sentinel. Think of workbooks as dashboards.

Analytical Alerts - alert you with the suspicious alerts to check

Threat hunting - Analysts can create their own queries to hunt for suspicious activity.

Incidents and investigations - an incident is created when an alert is triggered.

Automation Playbooks - With the ability to respond to incidents automatically, you can automate some of your security operations and make your SOC more productive.
