---
title: "Review data in evidence"
ms.author: sepa
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

# Review data in evidence

**Evidence** is a snapshot of search results that you collected. When you add search results to evidence, a process is triggered to extract files, metadata, and text. Then, the system builds a new index of all the data and adds to **Evidence**. 

For any time-sensitive incidents, this allows you to quickly contain the environment by deleting data at original locations while investigating re-created evidence in a quarantined environment. Once evidence is collected, you can review individual documents in their native format, text format, or a near-native format. Additionally, you can run queries to narrow the data by time range, file types, data owners, and many other condition cards. Using Author/Sender/Recipient condition cards, you can quickly examine who are involved in the spill and if there have been any external shares. For more information, see:

  - [Query the data in evidence](evidence-query.md)

To group documents and get more assistance for your review, click **Manage evidence**. In the **Analytics** tile, click **Analyze**. This will run advanced analytics such as duplicate detection, email threading, and theme analysis. Afterwards, you can see the general themes of the data and also organize documents by email threads, exact duplicates and near duplicates to facilitate your investigation. For more information, see:

  - [Run analytics to investigate faster](run-analytics-to-investigate-faster.md)

## More information

The following table lists the limits for evidence in Data investigations (Preview).  Any items that exceed the single file maximums will show up as processing errors.
    
  |**Description of limit**|**Limit**|
  |:-----|:-----|
  |Maximum number of evidence collections  <br/> |50  <br/> |
  |Total number of documents that can be ingested into a case (for all evidence collections in the investigation)  <br/> |1 million  <br/> |
  |Total file size per load  <br/> |100 GB  <br/> |
  |Maximum size of single file   <br/> |100 MB  <br/> |
  |Maximum number of characters extracted from a single file  <br/> |10 million  <br/> |
  |Depth of embedded items in a document  <br/> |25  <br/> |
  