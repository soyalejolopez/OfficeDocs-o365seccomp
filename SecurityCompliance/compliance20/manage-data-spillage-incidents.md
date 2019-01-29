---
title: "Managing a data spillage incident in Microsoft 365"
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

description: "This article describes using the new Data investigations (Preview) tool in the Office 365 Security & Compliance Center to manage a data spillage incident."
---

# Managing a data spillage incident in Microsoft 365 

Data spillage is when a confidential document is released into an untrusted environment. When a data spillage incident is detected, it's important to quickly assess the size and locations of the spillage, examine user activities around it, and then permanently purge the spilled data from the system.

## Scope of this article

This article provides a list of instructions on how to permanently remove items from Office 365 mailboxes so they are no longer accessible or recoverable by users or admins. 

> [!NOTE]
> When you delete items located in a SharePoint or OneDrive for Business site, they are retained for 93 days from the time you delete them from their original location.

## Scenario

You're informed of a data spillage incident where an employee unknowingly shared a highly-confidential document with multiple people through email. You want to quickly assess who received this document, both inside and outside of your organization. After you've investigate the incident, you plan to share your findings with other investigators to review, and then permanently remove the spilled data from Office 365. After the investigation is complete, you want to remove all evidence. 

## Workflow

Here's the workflow for using Data Investigations (Preview) to manage a data spillage incident:

1.	Create a data investigation in the Office 365 Security & Compliance Center. 

2.	Search for the spilled data.

3.	Review and investigate the incident.

4.	Permanently delete the spilled data 

5.	Close or delete the investigation


## Before you begin

- You will use Data Investigations in in the Office 365 Security & Compliance Center to search and analyze, and Security & Compliance Center PowerShell to delete data. 
- To create an investigation, you have to be a member of the Data investigator role group.
- To delete messages, you have to be a member of the Organization Management role group or be assigned the Search and Purge management role. For information about adding users to a role group, see Give users access to the Office 365 Security & Compliance Center. 
- To control which user mailboxes an investigator can search, your administrator can set up compliance boundaries which is described in [this article](https://docs.microsoft.com/en-us/office365/securitycompliance/set-up-compliance-boundaries). 

## Step 1: Create a data investigation

In Data investigations, click on "Create new investigation". Consider establishing a naming convention for investigations and provide as much information as you can in the name and description so you can locate and refer to in the future if necessary. You can add users or role groups as members to an investigation to manage access. 

## Step 2: Search for the spilled data 
 
If you know which users you want to search for spilled data, you can add them as people of interest to map their data sources and use them to scope your searches. To add people of interest, go to “People of interest” tab, and click on “Add people”. 

In search tab, you can create searches to find the spilled data. You will use the same search query that you used to find the email messages to delete those same messages in [Step 4](##step-4:-permanently-delete-the-spilled-data)

Click on "Create new search" and specify data you are looking for. [Learn more](https://docs.microsoft.com/en-us/office365/securitycompliance/content-search)

Preview samples of search results and statistics to evaluate your search query. Once you identify search results that you want to delete from your system, you can create an incident and add search results. In the incident, you can review individual documents, investigate who had access and export to a different environment. If you want to simply delete them instead, you can skip [Step 3](##step-3:-review-and-investigate) and go to [Step 4](##step-4:-permanently-delete-the-spilled-data). 

**Important:** The keywords that you use in the search query may contain the actual spilled data that you're searching for. For example, if you searching for documents containing a social security number and you use the it as search keyword, you must delete the query afterwards to avoid further spillage. You can delete search or entire investigation in [Step 5](##step-5:-close-or-delete-investigation). 

## Step 3: Review and investigate 

Click on the search that you want to investigate. In the information panel, click on “Add to incident” and follow instructions. Go to “Incidents” tab and click on the incident that you just created. Once processing job is completed, you can review individual documents in native, text, and near-native. You can also create queries to filter the list and tag documents to mark with investigation findings. 

To group documents together and get more assistance in review, click “Analyze” in “Incident configuration”. This will run advanced analytics such as email threading, duplication and theme analysis. 

To find out which users are involved, create a new query in the incident and select sender/author and recipients condition cards. This lists out all senders, recipients and authors found in collected data in this incident. Examine if there are any external domains in the list. 

## Step 4: Permanently delete the spilled data

### How do delete EXO items

After you review and validate that the search results contain only the messages that must be deleted, you can now delete the messages using SCC cmdlet and the search query. 
You can connect to Security & Compliance Center PowerShell and delete messages following step 2 and step 3 in [this article](https://docs.microsoft.com/en-us/office365/securitycompliance/search-for-and-delete-messages-in-your-organization)

If single item recovery is enabled, purged message will be retained in Recoverable items folder that is only accessible by admins until retention period ends (default is 14 days). If any of mailboxes are on a legal hold, purged message will be retained in Recoverable items folder until the legal hold is lifted. If you want to hard delete messages from mailboxes with these configurations immediately, you need to use EXO cmdlets to prepare the mailboxes before you can permanently delete email messages. See [this article](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-1-collect-information-about-the-mailbox) for detailed instructions. 

**Important:** Check with your records management or legal departments before removing a hold or retention policy. Your organization may have a policy that defines whether a mailbox on hold or a data spillage incident takes priority. 

### How to delete ODSP sites
Manually delete sites following instructions on [this article](https://docs.microsoft.com/en-us/sharepoint/delete-site-collection)

## Step 5: Close or delete investigation

You deleted documents at source, but you still have copies of them in your incident as evidence. You can delete entire investigation to avoid further spillage. In **Settings** tab, select **Investigation information** and **Delete**. If deletion is not needed, change case status to **Closed**. 

