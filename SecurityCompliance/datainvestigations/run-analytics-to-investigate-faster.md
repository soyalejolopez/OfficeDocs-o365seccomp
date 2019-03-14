---
title: "Run analytics to investigate faster"
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 
ms.audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance 
search.appverid: 
- MOE150
- MET150
ms.assetid: 

description: ""
---

# Run analytics to investigate faster

When an evidence collection is large, it can be difficult to review them all. Often times, it includes multiple copies of the same or similar emails or documents. Data investigations (Preview) provides a number of analytics tools to reduce the volume of documents that needs to be reviewed without any loss in information. To learn more about these capabilities, see:

- [Near duplicate detection](near-duplicates.md)
- [Email threading](email-threading.md)
- [Themes](themes.md)

To analyze data in evidence:

1. Configure analytics settings for your investigation. For more information, see [Configure search and analytics settings](configure-search-analytics-settings.md).
2. Open the evidence.
3. Go to "Manage evidence".
4. Click "Analyze".

You can check the progress of analysis in the Jobs tab in your investigation.

 Once analysis is completed, you can see a list of exact duplicates or near-duplicates of the document that you're reviewing located on the panel to the right. To select all duplicates of the document you're viewing, you can easily do so using this panel. To learn more about other features on this panel, see [Review data in evidence](review-data-in-evidence.md) You can also run additional queries within your evidence using the outputs of the analysis such as themes (for more information see [Query within your evidence](working-set-search.md)).

## Analytics report

To view a analytics report for your evidence:

1. Open your evidence.
2. Go to "Manage evidence".
3. Click "Report".

The report has four components from analysis:

- **Breakdown** - Number of raw emails, attachments, and documents found in the evidence.

- **Emails** - Number of emails that are inclusives, inclusive minuses, inclusive copies, or none of the above.
        Inclusives: The last email in the email thread that contains all previous history and requires review.
        Inclusive minuses: The email in the thread that contains one or more different attachments that requires review. 
        Inclusive copies: The email that is a copy of another inclusive or inclusive minus email (subject and body).

- **Attachments** - Number of email attachments that are unique or duplicates of a different email attachment within the evidence.

- **Documents (excluding email attachments)** - Number of unique documents that require review (e.g. The most representative document of the near-duplicate set, or an exact duplicate of another document).