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

- [See what kinds of malware were detected in email](#see-malware-detected-in-email-by-technology), and by threat protection technology (anti-malware protection, ATP Safe Attachments, etc.)

- View data about phishing links (URLs), and what the click verdicts were (URLs blocked, allowed, or visited despite warnings)

- Review email messages that were reported by using the [Report Message add-in for Outlook and Outlook on the web](enable-the-report-message-add-in.md), and identify any trends (such as a larger than usual number of messages reported as Phish) 


## See malware detected in email by technology

Suppose you want to see malware that was detected in email, and by what technology in Office 365. To do this, use the [Email > Malware](threat-explorer-views.md#email--malware) view of Explorer.

1. In the Office 365 Security & Compliance Center ([https://protection.office.com](https://protection.office.com)), choose **Threat management** > **Explorer**.
2. In the **View** menu, choose **Email** > **Malware**.<br/>![View menu for Explorer](media/ExplorerViewEmailMalwareMenu.png)<br/>
3. Click **Sender**, and then choose **Basic** > **Detection technology**.<br/>Your detection technologies are now available as filters for the report.<br/>![Malware detection technologies](media/ExplorerEmailMalwareDetectionTech.png)<br/> 
4. Select an option, and then click the Refresh button to apply that filter.<br/>![Selected detection technology](media/ExplorerEmailMalwareDetectionTechATP.png)<br/> 

The report refreshes to show the results malware detected in email, using the technology option you selected. From here, you can conduct further analysis.

## View data about phishing URLs and click verdict

Suppose you want to see phishing attempts through URLs in email, including a list of URLs that were allowed, blocked, and overridden. To do this, use the [Email > Phish](threat-explorer-views.md#email--phish) view of Explorer.

1. In the Office 365 Security & Compliance Center ([https://protection.office.com](https://protection.office.com)), choose **Threat management** > **Explorer**.
2. In the **View** menu, choose **Email** > **Phish**.<br/>![View menu for Explorer](media/ExplorerViewEmailPhishMenu.png)<br/>
3. Click **Sender**, and then choose **URLs** > **Click vedict**.
4. Select an option, such as **Blocked**, and then click the **Refresh** button to apply that filter.<br/>![URLs and click verdicts](media/ThreatExplorerEmailPhishClickVerdictOptions.png)<br/>

The report refreshes to show detected phishing URLs in email that were blocked, along with email delivery status. From here, you can conduct further analysis. 

## Review email messages reported by users

CONTENT

## There's more...

See the following articles to do even more with Explorer:

- [Find and investigate malicious email that was delivered](investigate-malicious-email-that-was-delivered.md)

- [View malicious files detected in SharePoint Online, OneDrive, and Microsoft Teams](malicious-files-detected-in-spo-odb-or-teams.md)

- [Check out the Threat Explorer views](threat-explorer-views.md)

## How to get Explorer

Explorer is included in [Office 365 Advanced Threat Protection Plan 2](office-365-ti.md). 

To view and use Explorer, you must have appropriate permissions, such as those granted to a security administrator or security reader. 

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

- [Automated Investigation and Response (AIR)](automated-investigation-response-office.md)

- [Threat Explorer views](threat-explorer-views.md)

- [View reports for Office 365 Advanced Threat Protection](view-reports-for-atp.md)
