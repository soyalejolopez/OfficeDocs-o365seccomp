---
title: "Office 365 Advanced Threat Protection"
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 02/08/2019
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: e100fe7c-f2a1-4b7d-9e08-622330b83653
description: "Office 365 Advanced Threat Protection includes safe attachments, safe links, advanced anti-phishing tools, reporting tools and threat intelligence capabilities."
---
>[!IMPORTANT] This article is intended for business customers. If you are a home user looking for information about Safe Links in Outlook, see [Advanced Outlook.com security](https://support.office.com/en-us/article/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

Office 365 Advanced Threat Protection (ATP) safeguards your organization against malicious threats posed by emails, links and collaboration tools. 

ATP includes:

- [Configuration tools](#configure-atp-policies): Define threat-protection policies to set the appropriate level of protection for your organization. 

- [Reports](#view-atp-reports): View real-time reports to monitor ATP performance in your organization. 

- [Threat intelligence capabilities](#utilize-threat-intelligence-capabilities): Utilize leading-edge tools to investigate, understand, simulate, and prevent threats. 
 

## Configure ATP policies

Office 365 ATP provides numerous tools to set the appropriate level of protection for your organization. 

You need to define policies within each ATP tool in the Office 365 Security & Compliance Center. Go to **Threat management > Policy > _ATP tool_** to access the policy options. 

The policies you select for your organization determine the behavior and protection level for predefined threats. The options are extremely flexible and you can, for example, set fine-grained threat protection on a user, organization, recipient, and domain level. It is important to review your policies regularly because new threats and challenges emerge daily.  

ATP features these configurable tools:

- [ATP Safe Attachments](atp-safe-attachments.md): Provides zero-day protection to safeguard your messaging system, by checking email attachments for malicious content. It routes all messages and attachments that do not have a virus/malware signature to a special environment, and then uses machine learning and analysis techniques to detect malicious intent. If no suspicious activity is found, the message is forwarded to the mailbox. See [Set up Office 365 ATP Safe Attachments policies](set-up-atp-safe-attachments-policies.md) for more.

- [ATP Safe Links](atp-safe-links.md): Provides time-of-click verification of URLs in emails messages and Office files. Protection is ongoing and applies across your messaging and Office environment. Links are scanned for each click: safe links remain accessible and malicious links are dynamically blocked. See [Set up Office 365 ATP Safe Links policies](https://docs.microsoft.com/en-us/office365/securitycompliance/set-up-atp-safe-links-policies) for more. 


- [ATP for SharePoint, OneDrive, and Microsoft Teams](atp-for-spo-odb-and-teams.md): Protects your organization when users collaborate and share files, by identifying and blocking malicious files in team sites and document libraries. See [Turn on Office 365 ATP for SharePoint, OneDrive, and Microsoft Teams](turn-on-atp-for-spo-odb-and-teams.md) for more. 


- [ATP anti-phishing protection](atp-anti-phishing.md): Detects attempts to impersonate your users and custom domains. It applies machine learning models and advanced impersonation-detection algorithms to avert phishing attacks. See [Set up Office 365 ATP anti-phishing and anti-phishing policies](set-up-anti-phishing-policies.md) for more.


## View ATP reports

Office 365 ATP includes an advanced [reporting dashboard](view-reports-for-atp.md) to monitor your ATP performance. You can access it at **Reports > Dashboard** in the Security & Compliance Center. 

Reports update in real-time, providing you with the latest insights. They also provide recommendations and alert you to imminent threats. Predefined reports include the [Threat Protection Status report](view-reports-for-atp.md#threat-protection-status-report), [ATP File Types report](view-reports-for-atp.md#atp-file-types-report), [ATP Message Disposition report](view-reports-for-atp.md#atp-message-disposition-report) and more. 

## Utilize threat intelligence capabilities

Office 365 ATP includes best-of-class [threat intelligence tools](office-365-ti.md) that allow you to anticipate, understand, and prevent malicious attacks:

- [Threat trackers](threat-trackers.md) provide the latest intelligence on prevailing cybersecurity issues. For example, you can view information about the latest malware, and take countermeasures before it becomes an actual threat to your organization. Available trackers include [Noteworthy trackers](threat-trackers.md#notey), [Trending trackers](threat-trackers.md#trending), [Tracked queries](threat-trackers.md#trackedq), and [Saved queries](threat-trackers.md#savedq).

- [Explorer](use-explorer-in-security-and-compliance.md) is a real-time report that allows you to identify and analyze recent threats. You can configure Explorer to show data for custom periods.

- [Attack Simulator](attack-simulator.md) allows you to run realistic attack scenarios in your organization to identify vulnerabilites. Simulations of current types of attacks are available, including a [display name spear-phishing attack](attack-simulator#spearphish), a [password-spray attack](attack-simulator#passwordspray.md), a [brute-force password attack](attack-simulator#bruteforce), and more.
    
  
## Permissions required to use ATP features

To access the Security & Compliance Center, you must be assigned one of these roles:

|Role  |Where/how assigned  |
|---------|---------|
|Office 365 Global Administrator |See [About Office 365 admin roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles) for more.|
|Security Administrator |See [Administrator role permissions in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-assign-admin-roles) for more.|
|Exchange Online Organization Management |[Permissions in Exchange Online](https://docs.microsoft.com/en-us/exchange/permissions-exo/permissions-exo) and [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps).|

For more, see:

- [Permissions in the Office 365 Security & Compliance Center](permissions-in-the-security-and-compliance-center.md) 
- [Give users access to the Office 365 Security & Compliance Center](grant-access-to-the-security-and-compliance-center.md).


## Get Office 365 ATP

Office 365 ATP is available as two plans (Plan 1 and 2). ATP forms part of many Exchange Online and Office 365 subscriptions, and is also available as a stand-alone service. See:

- [Feature availability across Advanced Threat Protection (ATP) plans](https://docs.microsoft.com/en-us/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) for a list of features included in Plan 1 and 2.

- [Office 365 Advanced Threat Protection (ATP) availability](https://docs.microsoft.com/en-us/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) for a list of subscriptions that include ATP plans.

- [Get the right Office 365 Advanced Threat Protection](https://products.office.com/en-us/exchange/advance-threat-protection#pmg-allup-content) to compare plans and purchase Office 365 ATP.


## New features in Office 365 ATP

New features are added to Office 365 ATP continually. Monitor the [Microsoft 365 Roadmap](https://www.microsoft.com/en-us/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) to stay up to date.
