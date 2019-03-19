---
title: "Overview of Data Investigations in Microsoft 365"
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

description: "This article describes the new Data Investigations tool in Microsoft 365."
---

# Overview of Data Investigations in Microsoft 365

A data spill is when a document containing confidential, sensitive or malicious information is released into an untrusted environment. When a data spill is detected, it's important to quickly contain the environment, assess the size and locations of the spillage, examine user activities around it, and then delete the spilled data from the system. Using Data investigations, you can search for sensitive, malicious or misplaced data across Office 365, investigate to find out what happened and take appropriate remedial actions.  

This article describes the capabilities in the new Data Investigations tool.

## Search for sensitive, malicious or misplaced data

Use the **Searches** tab to create searches to discover Office 365 for data that you want to remediate. You can create and run query-based searches (using keywords and conditions such as date range and sensitive data types) to identify a set email messages and documents, collect them as evidence to review and analyze. Additionally, you can use the search tool to preview sample documents and view search statistics that may help refine and improve the search results. Once you're satisfied that the search results contain the all the data relevant to the investigation, you add the search results to the **evidence** for further review, assess impact and take remedial actions. For more information, see [Search for data in an investigation](search-for-data.md).

## Review and investigate evidence

Use the **Evidence** tab to investigate the data that you've collected from the live system. The data in the and evidence set is a snapshot of search results that you collected. When you add search results to evidence, a process is triggered to extract files, metadata, and text. When this process is complete, the system builds a new index of all the data and adds to **Evidence**. For any time-sensitive incidents, this allows you to quickly contain the environment by deleting data at original locations while investigating re-created evidence in a quarantined environment. Once evidence is collected, you can run additional queries to narrow the data by time range, file types, data owners, and many other condition cards. Using Author/Sender/Recipient condition cards, you can quickly examine who are involved in the spill and if there have been any external shares. 

You can also run advanced analytics on the evidence that you collected. After you run analysis, you can see general themes of the data and also organize data by email threads, exact duplicates and near duplicates to facilitate your investigation. You can review data in extracted text view or in the native file format, and tag them with investigation result. For more information, see:

  - [Review data in evidence](review-data-in-evidence.md)

  - [Run analytics to investigate faster](run-analytics-to-investigate-faster.md)


## Managing people of interest

Use the **People of interest** tab to add and manage the people that you've identified as persons of interest during your investigation. When you add people of interest, their data sources, such as their mailboxes and OneDrive account, are identified and mapped. Then, you can scope your searches by them. When scoped down by people of interest, searches are more efficient and accurate because the tool re-processes any unindexed data such as images or unsupported file types. On **People of interest** tab, you can also view and search their activity log to investigate further. You can add more people of interest throughout your investigation. For more information, see [Work with people of interest in Data investigations (Preview)](manage-people-of-interest.md).

## Indexing the data of people of interest

Adding a person of interest re-indexes any partially indexed item from the person's data source (by a process called *Advanced indexing*). This re-processes data such as images, unsupported file types, to be fully discoverable when you run searches to collect data that's relevant to the investigation. Use the **Processing** tab to monitor the status of Advanced indexing and fix processing errors (using a process called *error remediation*.) For more information, see [Error remediation when processing data for an investigation](error-remediation.md).

## Exporting data

If you want to export data, use the **Exports** tab to manage an export job and download data from the evidence. When you export the evidence, the data is uploaded to an Azure storage location and then is available to be downloaded to a local computer. You can obtain the location and storage assess key necessary to download the exported data on the **Exports** tab. For more information, see [Export data from an investigation](export-data.md).

## Managing jobs

Use the **Jobs** tab to monitor long-running processes for tasks related to investigation or remediation that you've initiated such as re-indexing data, searches, analysis and exports. For example, you might create a new search on the **Searches** tab that includes a large number of data sources. The status of this search process is displayed on the **Jobs** tab. For more information, see [Manage jobs in a data investigation](manage-jobs.md).

## Configuring investigation settings

Use the **Settings** tab for configure investigation-wide settings. This includes adding members to a investigation, closing or deleting a investigation, and configuring search and analytics behavior. For more information, see [Configure case settings in Advanced eDiscovery (Preview)](configure-settings-datainvestigations.md).

