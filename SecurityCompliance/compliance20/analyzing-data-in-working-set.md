---
title: "Analyzing data in a working set in eDiscovery 2.0"
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: 
search.appverid: 
- MOE150
- MET150
ms.assetid: 

description: ""
---

# Analyzing data in a working set in eDiscovery 2.0
When the number of collected documents is large, it can be quite difficult to review them all. Advanced eDiscovery provides a number of tools to analyze the documents to reduce the volume of documents to be reviewed without any loss in information, and to help you organize the documents in a coherent manner. To learn more about these capabilities, please refer to:
- [Near duplicate detection](near-duplicates.md)
- [Email threading](email-threading.md)
- [Themes](themes.md)
To analyze your working set:
1. Configure analytics settings for your case. For more informationm, please refer to [Configure search and analytics settings](configure-search-analytics-settings.md).
2. Open the working set you wish to analyze.
3. Go to "Manage working set".
4. Click "Analyze".

You can check the progress of analysis in the Jobs tab in your case.

 Once analysis is completed, you can view analytics report, run queries within your working set on outputs of the analysis (for more information see [Query within your working set](working-set-search.md)), and see related documents of a given document (for more information see [Reviewing data in working set](reviewing-data-in-working-set.md)).

## Report
To view analytics report for your working set:
1. Open your working set.
2. Go to "Manage working set".
3. Click "Report".
The report has four componets from analysis:
- Breakdown: How many emails, attachments, and loose documents were found in your working set
- Documents (excluding attachments): how many loose documents were pivots, unique near duplicates of a pivot, or an exact duplicate of another document.
- Emails: how many emails were inclusives, inclusive copies, inclusive minuses, or none of them above.
- Attachments: how many email attachments were unique or duplicates of a different email attachment within the working set.