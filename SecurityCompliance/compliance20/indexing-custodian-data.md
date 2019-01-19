---
title: "Advanced indexing of custodian data"
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

# Advanced indexing of custodian data

## Overview

When a custodian is added to an Advanced eDiscovery case, any content in Office 365 that was deemed as partially indexed is re-processed to make it fully searchable.  Content can be partially indexed for a number of reasons including the existence of images, unsupported file types or when indexing file size limits are encountered.  To learn more about partially indexed items, refer to [Partially indexed items in Content Search in Office 365](https://docs.microsoft.com/en-us/office365/securitycompliance/partially-indexed-items-in-content-search).

## Viewing Advanced indexing results

After the Advanced indexing process is completed, you can get an understanding of the effectiveness of re-processing.  In the Custodian Indexing view, the graph lists all items added to the hybrid index.  The hybrid index is where Advanced eDiscovery stores the re-processed content.

The graph also includes the number of items that require remediation and another graph of Errors by file type, refer to [Create a new error remediation](processing-error-types.md) for more information on that topic.

## Updating Advanced indexes for custodians

When a custodian is added to an Advanced eDiscovery case, all partially indexed items are re-processed, however, as time passes, more partially indexed items may be added to a users mailbox or OneDrive for business site.  When needed, you can update the indexes.

> [!NOTE]
> Updating custodian indexes is a long running process, therefore, it is recommended that you do not update indexes more than once per day in a case.
