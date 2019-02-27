---
title: "Automated Investigation and Response (AIR) with Office 365 Threat Intelligence"
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 02/27/2019
ms.audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: "Learn about Automated Investigation and Response capabilities in Office 365 Advanced Threat Protection."
---

# Automated Investigation and Response (AIR) with Office 365 Threat Intelligence

Automated Investigation and Response (AIR) within [Office 365 Threat Intelligence](office-365-ti.md) capabilities allows you to run automated investigation and remediation to well-known threats that exist today. Read this article to get an overview of AIR and how it can help your organization more effectively mitigate threats.

## Security playbooks

Security playbooks are back-end policies that admins can select as part of security policies. At the heart of automation in Microsoft Threat Protection, the security playbooks provided in [Office 365 Advanced Threat Protection](office-365-atp.md) are based on common real-world security scenarios. 

A Security playbook is kicks off when an alert is triggered within your organization. Once the alert triggers, the associated playbook is run automatically. The playbook runs an investigation, looking at all the associated metadata (including email messages, users, subjects, senders, etc.) and, based on its findings, recommends a set of actions the security team can take to control and mitigate the threat. 

Based on extensive experience, the security playbooks are designed to tackle the most frequent threats our customers face.

### Security playbooks are rolling out in phases

- **Phase 1**: Recommended actions to take will require a security administrator to approve.

- **Phase 2**: Security administrators will have the option to allow security playbooks to automatically take action without administration interaction.


## The playbooks

The following five playbooks will be offered:

|Initial release  |Coming soon after |
|---------|---------|
|User-submitted message<br>URL verdict change<br>Manual investigation |Zapped malware<br>Zapped phish|

Each playbook will include a root investigation, steps to hunt down other potential threats, and threat remediation. Each high-level step includes many sub-steps that are executed to provide a deep, detailed, and exhaustive response to threats.

### Example: User-submitted message

Suppose that a user submits an email message by using the [Report Message add-in](enable-the-report-message-add-in.md). 

## Getting started

## 
  
## Related topics

[Reports and insights in the Office 365 Security &amp; Compliance Center](reports-and-insights-in-security-and-compliance.md)
  
[Use Explorer in the Security &amp; Compliance Center](use-explorer-in-security-and-compliance.md)

