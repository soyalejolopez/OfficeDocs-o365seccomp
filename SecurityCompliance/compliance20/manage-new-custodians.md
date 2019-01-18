---
title: "Managing Custodians"
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
# Managing Custodians in an Advanced eDiscovery Case
sdfa
## Viewing Custodian Details
The Custodians tab contains a sortable list of all the custodians in the case. Once added, the custodian details will automatically be collected from Active Directory.

The Custodian details flyout appears once you have added a custodian to case and selected them from the landing page. From here, you can view all the details related to that custodian. The Custodial tab and detail flyout contain the following fields:
  - Basic Contact Details
    - **Display Name**: The name displayed in the address book for the custodian. This is usually the combination of the custodian’s first name, middle initial and last name.
    - **Mail/SMTP**: The SMTP address for the custodian, for example, jeff@contoso.onmicrosoft.com.  
    - **Title**: The custodian’s job title.
    - **Department**: The name for the department in which the custodian works
    - **Manager**: the custodian’s manager. The designated manager will receive any Escalation communications for this custodian.
  - Case Information
    - **Hold Status**: Indicates if the custodian has been placed on hold. 
    - **Communication Status**: Indicates if the custodian has been issued a hold notice. If the custodian has been issued a notice, then this will be marked as *Published*. If the custodian has not been issued a notice, then this status will be *Un-Published*. 
    - **Case Status**: The status of the custodian within the case. This will be *Active* if the custodian is still on hold for the case. Once a custodian is removed from a case, their status will change to *Released*. 
  - Processing Status
    - **Indexing Status**: Indicates the status of the deep indexing job.  
    - **Indexing Last Updated Time**: Indicates the datestamp of when the deep indexing job was last triggered.
    - **Data Sources**: Shows the count of Mailboxes, Sites, and Teams that have been selected for the custodian.
  - Location Details
    - **City**: The city in which the custodian is located.
    - **State**: The state or province in the custodian’s address.
    - **Country/Region**: The country/region in which the custodian’s is located; for example, “US” or “UK”.
    - **Office**: The office location in the custodian’s place of business.


## Update Custodian
As your case progresses, you may discover that there may be additional data sources relevant to a specific custodian & your case. In other scenarios, you may want to remove certain data sources that have been reviewed and deemed as not relevant.
 
To update a custodian and the selected data sources:
  1. Select an existing case from the **Security and Compliance Center > Advanced eDiscovery**.
  2. From your case, navigate to the **Custodians** tab.
  3. Select the custodian(s) from the list and click **Edit Sources**.
  4. Update selections for Exchange & OneDrive locations by navigating to Choose Data Sources.
  5. Add or remove Teams, SharePoint, or Exchange mailboxes mapped the user by navigating to Select Additional Data Sources. *See the Add Custodian Documentation to learn more about how you can map data sources to a custodian*.
  6. Update custodian hold status by selecting Place Custodial Holds.

[!TIP]
 You can select multiple custodians at once to perform bulk actions, like re-indexing, releasing, or editing a set of custodians.

## Resolving Custodian Processing Errors
In most Legal workflows, after custodians are added for a specific investigation, a subset of the users’ data will be searched. Due to large file sizes or possible corruption, some items within the custodians’ data sources may be partially indexed. Using the Advanced eDiscovery deep indexing capability, these partially indexed items can be automatically remediated by re-crawling and re-indexing these items on demand. 

When a custodian is added to a case, their data will automatically be "deep indexed”, allowing users to leave these partially indexed items in place instead of having to download, remediate and re-run searches outside of Office 365. During the lifecycle of a case, a user may remediate items or add new data sources for a given custodian. This may require the Custodian Index to be updated. 

A user can trigger a re-index to address partially indexed items by the following steps:
1. Select an existing case from the **Security and Compliance Center > Advanced eDiscovery**.
2. Once you have selected a case, navigate to the **Custodians tab**. 
2.	Select the custodian(s) that need to be re-indexed and then click **Update Index**.
3.	Check the status of the Custodian Index by selecting the Job Status link on the Custodians tab landing page.  
4.	The status for this re-indexing process can also be tracked in the Jobs tab.

[!NOTE]
 Learn more about the re-indexing and remediating partially indexed items in the Error Remediation section.

## Releasing a Custodian from a Case
A custodian is released in situations where a case is closed, a custodian is no longer under obligation to preserve content for a case, or when a custodian is deemed to no longer be relevant to a particular case. 

If you release a custodian after a hold notice was published, a release notice will be sent to the custodian. In addition, any custodial holds attributed to the released custodian(s) will also be removed.

If the custodial was placed on a silent hold, where they were not issued any legal hold notifications, then any custodial holds attributed to the released custodian(s) will be removed.  

To release a custodian: 
1.	Navigate to the Custodians tab.
2.	Select the custodian from the list and click Release.
3.	The status of the custodian on the Custodian Tab should now be Released and the Hold Status should be changed to Inactive. 

[!TIP]
A custodian may simultaneously be involved in several legal hold matters. When a custodian is released from a case, holds and notifications across other matters will not be impacted. 

##Related Content
 - User Attributes in Active Directory 
 - Error Remediation 
 - Hold Notifications 

