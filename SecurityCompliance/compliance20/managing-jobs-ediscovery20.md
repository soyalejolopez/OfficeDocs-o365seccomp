---
title: "Manage jobs in Advanced eDiscovery (Preview)"
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

# Manage jobs in Advanced eDiscovery (Preview)

Here's a list and description of the jobs (which are typically long-running processes) that are tracked on the **Jobs** tab of a case in Advanced eDiscovery (Preview).

| Job type           | Description     |
| :----------------- | :----------     |
|Adding data to a working set | The results of a search are added to a working set.  For more information on managing working sets, see [Manage working sets](managing-working-sets.md). |
|Adding data to another working set | A user copies documents from one working set and adds them to another working set. |
|Adding non-Office 365 data to a working set | A user uploads non-Office 365 data (that may be relevant to a case) to a working set; the data is also indexed during this process. For example, files from an on-premises file share or a client computer are copied to a working set.  For more information, see [Load non-Office 365 data into a working set](load-non-office365-data.md).| 
|Adding remediated data to a working set | Data with processing errors are remediated and loaded back into a working set. For more information, see [Error remediation when processing data](error-remediation.md). | 
|Comparing load sets | When a user can look at the differences between different load sets in a working sets. For more information, see [Manage load sets](manage-load-sets.md). |
|Converting redacted documents to PDF|When a user adds an annotation to a document in a working set, the annotated document is converted to a PDF file. |
|Estimating search results | Results when a user creates and runs (or re-runs an existing search) a search against data sources such as Exchange, SharePoint, and OneDrive for Business.  Search estimates include statistics such as number of items returned by the search and total size of all items.  For more information, see [Collect data for a case in Advanced eDiscovery](collecting-data-for-ediscovery.md). | 
|Preparing data for export | Results when data is exported from a from a working set. When the export is complete, a user can download the exported data. For more information, see [Export case data](exporting-data-ediscover20.md). | 
|Preparing for error resolution |  | 
|Preparing search preview | Preparing search preview jobs are the result of creating and running a search against workloads such as Exchange, SharePoint and OneDrive for Business.  A preview of the search results are available to help determine the efficacy of the search.  For more information on search, see [Collect data for a case in Advanced eDiscovery](collecting-data-for-ediscovery.md). | 
|Re-indexing custodian data | When a custodian is added to a case, all partially indexed items are re-indexed with Advanced eDiscovery indexing, for more information, see [Advanced indexing of custodian data](indexing-custodian-data.md).
|Running analytics | Running analytics jobs refer to processing jobs including Near Duplicate Identification, Email thread analysis and Themes Analysis, for more information on analytics, see [Analyze data in a working set in Advanced eDiscovery](analyzing-data-in-working-set.md). | 
|Tagging documents | Tagging documents jobs occur when multiple documents in a working set are tagged.  For more information, see [Tag documents in a working set](tagging-documents.md). | 
|||
