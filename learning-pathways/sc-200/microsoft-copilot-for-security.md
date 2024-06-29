# Microsoft Copilot for Security

#### Intro

Microsoft Copilot for security can be a very powerful tool added to your current tool box. It helps your investigations with ML and AI.

However, to remember the successes of the technology has to be made with "good sets" of data else it would be outputting incorrect or inaccurate results.

#### MS Learn Topics

* Fundamentals of Generative AI (✔)
* Describe Microsoft Copilot for Security (✔)
* Describe the core features of Microsoft Copilot for Security (✔)
* Describe the embedded experiences of Microsoft Copilot for Security (✔)



#### General knowledge of MS Copilot:

There are many types of Copilots that Microsoft offers such as:

* Copilot for Security
* Copilot for Dynamics 365 Sales

For developers they are created within Azure AI Studio where they will add the language models and being the copilot.

Best Practices is to keep it simple and once it has been created and working, then slowly expand.

#### Provisioning Microsoft Copilot for Security

Firstly you need to be one of the two admin roles to setup the Copilot:

* Global administrator
* Security administrator

Provision SCUs, set up the default environment, and assign role permission.

Provisioning capacity within Copilot for Security is recommended and guided by a wizard for ease of set up.

Some useful terminology:

* Session – A particular conversation within Copilot. Copilot maintains context within a session.
* Prompt – A specific statement or question within a session. A user enters a prompt in the prompt bar.
* Capability – A function Copilot uses to solve part of a problem. A capability may sometimes be referred to as a skill.
* Plugin – A collection of capabilities by a particular resource.
* Orchestrator – Copilot’s system for composing capabilities together to answer a user’s prompt.

In other copilots you may also need to assign permissions for operations, assign accordingly

The Microsoft Entra ID roles are:

* Global administrator
* Security administrator
* Security operator
* Security reader

The Microsoft Copilot for Security roles are:

* Copilot owner
* Copilot contributor

#### Copilot Features

You create prompts to make possible promptbooks which can be selected from the "create Promptbook" icon, where they can name, tag, and further customise the promptbook.

Toggle the plugin to ensure your file is included.

Intergrations such as ServiceNow plugin offers a Basic sign-in or OAuth authorization for authentication.

Previous sessions can be found from the My sessions option from the home menu.

To use the capability to remediate code with Copilot for Security, you must connect your Azure DevOps environment to Defender for Cloud, configure the Microsoft Security DevOps Azure DevOps extension, and meet the DevOps security support and prerequisites requirements.

When creating a new policy, Copilot can be used to learn more about individual settings, their impact, and recommended values.&#x20;

The 'Summarize' tab displays the Copilot generated summary of the user's risk level.

To use Copilot for Security functionality with Microsoft Purview eDiscovery, the organization must be licensed for Microsoft Purview eDiscovery (Premium). (Still in preview at the moment of me writing this documentation)

The Summarize incidents feature provides an overview of the attack, including the timeline and assets involved.

