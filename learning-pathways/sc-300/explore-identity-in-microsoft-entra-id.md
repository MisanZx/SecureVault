---
description: 16 units
---

# Explore identity in Microsoft Entra ID

## Intro

My current knowledge of Entra ID is varied as i have implemented changes within the business but would like to explore all the features it has to offer.

## Explain the identity landscape <a href="#module-unit-title" id="module-unit-title"></a>

The main focus is around Zero Trust:

* Verify Explicitly - verify every access request is expected for the function.
* Use Least Privilege
* Assume Breach



Other things to consider as there are might be other people and services that require access to your systems:

* Identity - Business to Business, Consumer
* Authentication systems
* Usage
* Secure - Cryptography
* Licenses
* Maintain - Protect - Detect - Respond.

## The changing in landscape

Before, everything is kept behind a firewall. Submit a username and password to get through the doorway into the system was considered fine. However, in the modern world, with the large number of cyber-attacks secure just the network is no longer applicable due to new methods of actors getting through systems. With Zero Trust, you provide extra layers of protection for your assets to reduce the likin-hood of a cyber-attack.

<div align="center" data-full-width="false"><figure><img src="../../.gitbook/assets/image (18).png" alt="" width="188"><figcaption></figcaption></figure></div>

## Zero Trust guidance principles for architecture design

* Minimise blast radius for breaches and prevent lateral movement
* Just-in-time access, segmenting access by network, user, devices and app awareness.
* Risk-based adaptive policies, analytics for threat detection, posture visibility and improving defenses.

## Identity provider (IdP)

A system that creates, manages and stores digital Identities. Entra ID is one of these.

SSO for example enhances usability by reducing password fatigue.



## Common identity protocols

OpenID provider - OAuth2, JSON-formatted identity tokens to OIDC relying parties via a RESTful HTTP API. (Newer and better support for mobile and has more scalability)&#x20;

SAML provider - Security Assertion Markup Language is an XML-based markup language for security assertions.

* **SAML** is often considered more secure in **highly controlled enterprise environments**, especially when paired with strong certificate management and HTTPS.
* **OIDC** is more secure for **modern, internet-facing applications**, thanks to its flexibility, token-based architecture, and better support for mobile and API-driven ecosystems.

