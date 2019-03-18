---
title: "Use Threat Explorer in the Security &amp; Compliance Center"
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 03/12/2019
ms.audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 82ac9922-939c-41be-9c8a-7c75b0a4e27d
ms.collection: 
- M365-security-compliance
description: "Learn about Explorer (also called Threat Explorer) in the Security &amp; Compliance Center."
---

# Use Threat Explorer in the Security &amp; Compliance Center

## Explorer overview

If your organization has [Office 365 Advanced Threat Protection Plan 2](office-365-ti.md), and you have the necessary permissions, you can use Threat Explorer (also referred to as Explorer) to identify and analyze threats. 

![Go to Threat management \> Explorer](media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)
  
To use Threat Explorer, in the Security &amp; Compliance Center, go to **Threat management** \> **Explorer**.

Here are a few things you can do with Explorer (there are many more possibilities):

- See what kinds of malware were detected, and by which threat protection technologies (anti-malware protection, ATP Safe Attachments, etc.)

- View data about phishing links (URLs), and what actions were taken (URLs blocked, allowed, or visited despite warnings)

- Review email messages that were reported by using the [Report Message add-in for Outlook and Outlook on the web](enable-the-report-message-add-in.md), and identify any trends (such as a larger than usual number of messages reported as Phish) 

- [View information about malicious files](malicious-files-detected-in-spo-odb-or-teams.md) detected in your organization's SharePoint, OneDrive, and Teams libraries

## See detected malware by technology

CONTENT

## View data about phishing URLs and actions taken

CONTENT

## Review email messages reported by users

CONTENT


## How do I get Explorer?

Explorer is included in [Office 365 Advanced Threat Protection Plan 2](office-365-ti.md). 

To view and use Explorer, you must have appropriate permissions, such as those granted to a security administrator or security reader, in order to view and use Explorer. 

- For the Security &amp; Compliance Center, you must have one of the following roles assigned:
    - Organization Management
    - Security Administrator (this can be assigned in the Azure Active Directory admin center ([https://aad.portal.azure.com](https://aad.portal.azure.com)))
    - Security Reader

- For Exchange Online, you must have one of the following roles assigned in either the Exchange admin center ([https://outlook.office365.com/ecp](https://outlook.office365.com/ecp)) or with PowerShell cmdlets (See [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps)):
    - Organization Management
    - View-only Organization Management
    - View-Only Recipients role
    - Compliance Management

To learn more, see the following resources:

- [Permissions in the Office 365 Security &amp; Compliance Center](permissions-in-the-security-and-compliance-center.md)

- [Feature permissions in Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/feature-permissions)
  
## Related topics

[Threat Explorer views](threat-explorer-views.md)
