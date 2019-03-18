---
title: "Search for data in an investigation"
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

# Search for data in an investigation

In **Search** tab, you can search for misplaced, confidential or sensitive data across Office 365 in the live system using keywords and various condition cards. 

After you run a search, you will be able to view statistics on the retrieved items such as the locations that had the most items that matched the search query. You can also preview a subset of the results. When you've identified the set of documents that want to further investigate, you can collect the search results as **Evidence** to further process and analyze. 

## Create a search

1. Clicking **New search** on the **Searches** tab will start a wizard that guides you through creating a search. 

2. Each search with a case should have a unique name. You can optionally provide a description for your search.

3. Define your search criteria. You can define the conditions for your search using the pre-built condition cards or using Keyword Query Language (KQL). For more information, see [Build search queries](building-search-queries.md).

4. Once you have defined your conditions, you need to choose which locations you want to search. One way to do it is scoping it by selecting people of interest if you added any. If you know whom you want to scope down your search but haven't added them to people of interest, you can do so following instructions in [Add people of interest to investigation](add-people-of-interest-to-investigation.md).

5. In some cases, you may wish to search across tenant or data sources across that are not mapped to a person. In this case, you can specify the locations you would like to search, or choose to search all content locations for a specific Office 365 service (such as searching all Exchange mailboxes or all SharePoint and OneDrive for Business sites).

After a search is created, a flyout page with details is displayed. Note that the **Statistics** and **Preview** buttons are initially grayed out because the search has not completed yet. You can keep track of the progress of the search on the **Searches** tab.

## View search results and statistics
There are two components of a content search: Statistics (Estimates) and Preview. As each of these components complete, you will see the status displayed in the corresponding columns on the **Searches** tab change from from **Submitted** to **In progress** to **Completed**.

Once the search estimate is completed, click the search to display the flyout page, which will display some high-level statistics about the results of the search. At this point, the **Statistics** button will be active. You can click it to see search statistics, such as:

- Summary
- Top locations
- Queries
- Refiners

For more information about search statistics, see [Search statistics](search-statistics.md).

Once preview is completed, the **Preview** button will be active. Click it to preview a sampled subset of the results.

## Collecting search results to evidence

When you are ready to investigate and remediate the search results, you can do so by adding it to evidence. When you add data to **Evidence** it extracts and re-indexes files, metadata, and text in a quarantined environment. For time-sensitive incidents, this allows you to quickly contain the environment by deleting data at original locations, and investigate re-created evidence afterwards in a quarantined environment. This also allows lightning fast search results and advanced analysis such as themes detection, email thread identification and near duplicate detection to facilitate your investigation. You can also add data from Non-Office 365 data sources to live side by side with the data you collect from Office 365.

To add data to **Evidence**, start by selecting a search, in the search results fly out, click the *+ Add results to evidence* button.

Adding data to evidence is a long running process, you can either track the progress in the Jobs tab or in the *Evidence status* column in the *Searches* tab.  The process includes gathering items from Office 365 and finally Ingestion & Indexing.  Once evidence processing is completed, you can navigate to the working set by clicking on the *Working Sets* tab and then clicking on the working set.  You can then move on to searching, reviewing, tagging and exporting any relevant data.