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

|Initial release  |Following soon |
|---------|---------|
|User-submitted message<br>URL verdict change<br>Manual investigation |Zapped malware<br>Zapped phish|

Each playbook includes: 
- a root investigation, 
- steps to hunt down other potential threats, and 
- threat remediation.

Each high-level step includes many sub-steps that are executed to provide a deep, detailed, and exhaustive response to threats.

### Example: User-submitted message scenario

Suppose that a user submits an email message by using the [Report Message add-in for Outlook](enable-the-report-message-add-in.md). This triggers the **User-submitted message** playbook.

During the root investigation phase, various aspects of the email are assessed. These include:
- A determination about what type of threat it might be,
- Who sent it,
- Whether other instances of the email were removed by the [ZAP feature](zero-hour-auto-purge.md),
- An assessment from our analysts,
- Whether the email is associated with any known campaigns,
- ... and more.

After the root investigation is complete, the playbook provides a list of recommended actions to take.
  
Next, several hunting steps are executed:

- Similar email messages in other email clusters are searched.
- The signal is shared with other platforms, such as [WDATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection).
- A determination on whether any users have clicked-through on the suspicious email message.
- A check is done to see if [Office 365 ATP Safe Links](atp-safe-links.md) may have missed any instance of the email which was submitted.
- A check is done to see if the user has been compromised.  

During the hunting phase, risks and threats are assigned to various hunting steps.  

Remediation is the final phase of the playbook. Remediation steps are carried out, based on the results from the investigation and hunting phases.  


## Getting started

## 
  
## Related topics

[Reports and insights in the Office 365 Security &amp; Compliance Center](reports-and-insights-in-security-and-compliance.md)
  
[Use Explorer in the Security &amp; Compliance Center](use-explorer-in-security-and-compliance.md)

