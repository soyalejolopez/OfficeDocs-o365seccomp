---
title: "Get ready for Microsoft 365 Security and Compliance"
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 01/04/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
description: "Get ready for the all-new Microsoft 365 Security Center and Compliance Center"
---

# Plan for security &amp; compliance in Office 365

## Get ready for the all-new Microsoft 365 Security Center and Compliance Center

As we're adding features to Security & Compliance capabilities for your organization, **we are pleased to announce the all-new Microsoft 365 Security Center and Microsoft 365 Compliance Center, rolling out beginning in early February 2019 and through March 2019**. Read this article to get an overview of the new Security Center and Compliance Center.

## Security Center

Your new Microsoft 365 Security Center includes a dashboard to help you monitor and manage security across your identities, data, devices, apps, and infrastructure. You will also have easy access to your all-new Microsoft 365 Secure Score, device threat reports, identity threat reports, and Cloud App Security reports. 

![New Microsoft 365 Security Center](media/m365-security-center.png)

To view the new Security Center, go to [https://security.microsoft.com](https://security.microsoft.com) and sign in. (When your new Security Center is rolled out, links to security features in your previous [Office 365 Security & Compliance Center](https://protection.office.com) will redirect automatically.) 

When you use the Security Center for the first time, you'll see information across the top of the screen to help you get started. And you'll see how to navigate easily to the security features you're most interested in exploring.

> [!NOTE]
> You must be assigned a valid Azure Active Directory role in order to access the Security Center. To learn more, see the [permissions needed](#permissions-needed-to-access-the-new-security-center-and-the-new-compliance-center) section (in this article).

## Compliance Center

Your new Compliance Center includes Compliance Manager and integrated solutions for classification, data governance, case management, and more. You'll have easy access to Sensitivity and Retention labels, Data Loss Prevention reports, Cloud App Security reports, alerts, and compliance policies.

![Microsoft 365 Compliance Center](media/m365-compliance-center.png)

To view the new Compliance Center, go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and sign in. (When your new Compliance Center is rolled out, links to compliance features in your previous [Office 365 Security & Compliance Center](https://protection.office.com) will redirect automatically.) 

When you use the Compliance Center for the first time, you'll see information across the top of the screen to help you get started. And you'll see how to navigate easily to the compliance features you're most interested in exploring.

> [!NOTE]
> You must be assigned a valid Azure Active Directory role in order to access the Compliance Center. To learn more, see the [permissions needed](#permissions-needed-to-access-the-new-security-center-and-the-new-compliance-center) section (in this article).

## Permissions needed to access the new Security Center and the new Compliance Center

In order to access the new Security Center or the new Compliance Center, you must be assigned the Global Administrator, Compliance Administrator, or Security Administrator role in Azure Active Directory.

- A Global Administrator can access both the Security Center and the Compliance Center

- A Compliance Administrator can access the Compliance Center

- A Security Administrator can access the Security Center

The following table summarizes who can access various portals across Azure, Office 365, and Windows:

|Portal  |Global<br/>Administrator  |Security <br/>Administrator  |Compliance<br/>Administrator  |
|---------|---------|---------|---------|
|Office 365 Security & Compliance Center |Yes |Yes  |Yes |
|Security Center     |Yes  | Yes  | No        |
|Compliance Center     | Yes | No | Yes |
|Azure Information Protection     |Yes |Yes |No |
|Azure Security Center     |Yes |Yes |No |
|Azure ATP     |Yes |Yes |No |
|Windows Defender ATP / EDR     |Yes |Yes |No |
|Identity Protection     |Yes |Yes |No |
|Privileged Identity Management     |Yes |Yes |No |
|Intune     |Yes |Yes |Yes |
|Cloud App Security     |Yes |Yes |Yes |
|Secure Score     |Yes |Yes |No |
|Exchange     |Yes |Yes |Yes |
|Compliance Manager     |Yes | No |Yes  |

