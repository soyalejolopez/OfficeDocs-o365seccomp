---
title: "Security dashboard overview"
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 01/04/2019
ms.audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: fe0b9b8f-faa9-44ff-8095-4d1b2f507b74
description: "Use the new Security Dashboard to review Office 365 Threat Protection Status, and view and act on security alerts."
---

# Security Dashboard

## Overview

The [Security &amp; Compliance Center](go-to-the-securitycompliance-center.md) enables your organization to manage data protection and compliance. Assuming you have the necessary permissions, the Security Dashboard enables you to review your Threat Protection Status, as well as view and act on security alerts. 
  
Watch the video to get an overview, and then read this article to learn more.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/3540b1f8-62d2-47fa-a07d-d7ad76f55b0f?autoplay=false]
  
Depending on what your organization's Office 365 subscription includes, the Security Dashboard includes several widgets, such as Threat Management Summary, Threat Protection Status, Global Weekly Threat Detections, Malware, and more, as described in the following sections.
  
To view the Security Dashboard, in the [Office 365 Security &amp; Compliance Center](go-to-the-securitycompliance-center.md), go to **Threat management** \> **Dashboard**.
  
> [!NOTE]
> You must be an Office 365 global administrator, a security administrator, or a security reader to view the Security Dashboard. See [Permissions in the Office 365 Security &amp; Compliance Center](permissions-in-the-security-and-compliance-center.md). 
  
## Threat Management Summary

The Threat Management Summary widget tells you at a glance how your organization was protected from threats over the past seven (7) days.

![Security Dashboard - Threat Management Summary widget](media/SecDash-ThreatMgmtSummary.png)

The information you'll see in the Threat Management Summary depends on what you subscription includes. The following table describes what information is included for Office 365 Enterprise E3 and Office 365 Enterprise E5.


|Office 365 Enterprise E3  |Office 365 Enterprise E5  |
|---------|---------|
|Malware messages blocked<br/>Phishing messages blocked<br>Messages reported by users<br><br><br><br> |Malware messages blocked<br>Phishing messages blocked<br>Messages reported by users<br>Zero-day malware blocked<br>Advanced phishing messages detected<br>Malicious URLs blocked |


## Threat Protection Status

In the upper left corner of the Security Dashboard is a Threat Protection Status widget that shows threat protection effectiveness. This widget tells you at a glance how many threats were blocked by [Office 365 Exchange Online Protection](anti-spam-protection.md) and [Office 365 Advanced Threat Protection](office-365-atp.md) (if configured) over the last seven days. This widget also shows the number of email messages detected as misclassified and reported by using the [Use the Report Message add-in](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2). Review your anti-spam, anti-malware, and anti-phishing policies to improve your configuration.
  
![Threat protection widgets across the top of the Security Dashboard](media/5c7c644e-6b01-4bf8-b991-f6ba0fdc5717.png)
  
In addition, Malware reports can be used to track recent trends in malicious content targeted at your organization. Click a tile to view more information in the report.
  
## Insights

Insights not only surface key issues you should review, they also include recommendations and actions to consider. For example, you might see that phishing email messages are being delivered because some users have disabled their junk mail options. To learn more about how insights work, see [Reports and insights in the Office 365 Security &amp; Compliance Center](reports-and-insights-in-security-and-compliance.md).
  
## Threat intelligence

If your organization has [Office 365 Threat Intelligence](office-365-ti.md), your Security Dashboard has a **Threat Intelligence** section that includes advanced tools. Your organization's security team can use the information in this section to understand emerging campaigns, investigate threats and manage incidents. 
  
![Threat intelligence helps you understand attacks targeted at your organization](media/6ce67cf2-3bbb-4008-9c55-1b4c7af0471f.png)
  
> [!TIP]
> Office 365 Threat Intelligence is included with Office 365 Enterprise E5; however, if your organization is using another Office 365 Enterprise subscription, Office 365 Threat Intelligence can be purchased as an add-on. For more information, see [Office 365 Threat Intelligence](office-365-ti.md). 
  
## Trends

Near the bottom of the Security Dashboard is a **Trends** section, which summarizes email flow trends for your organization. Reports provide information about email categorized as spam, malware, phishing attempts, and good email. Click a tile to view more detailed information in the report. 
  
![The Trends section summarizes email flow trends for the organization](media/edec55c0-59f4-4510-ae91-4a50b7b3cd93.png)
  
And, if your organization's Office 365 subscription includes [Office 365 Threat Intelligence](office-365-ti.md), you will also have a **Recent threat management alerts** report in this section that enables your security team to view and take action on high-priority security alerts. 
  
## Related topics

[View email security reports in the Security &amp; Compliance Center](view-email-security-reports.md)
  
[View reports for Office 365 Advanced Threat Protection](view-reports-for-atp.md)
  
[Office 365 Advanced Threat Protection](office-365-atp.md)
  
[Office 365 Threat Intelligence](office-365-ti.md)
  

