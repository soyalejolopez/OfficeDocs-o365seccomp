---
title: "Add Custodians to a Case"
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

# Add Custodians to a Case

Using Advanced eDiscovery, you can leverage the built-in Custodian Management tool to coordinate your workflows around managing custodians and identifying relevant, custodial data sources within a case. When you add a custodian, the system can automatically identify, and place holds on their primary Exchange mailbox and OneDrive for Business site. As you conduct your discovery, you might also uncover and map additional mailboxes or sites that a custodian accessed in the past or Teams that a custodian is a member of today

To add custodians and their data sources to an existing Advanced eDiscovery case: 
 1. Navigate to the Custodians tab and select Add Custodian. 
  
 1. Start typing to search & select the users within your Azure Active Directory.  Identify the custodians that you would like to add to your case and click Next.

 1. Based on the selected custodians, the system will automatically identify the primary Exchange Mailbox and OneDrive site for each custodian. Finalize the custodial data sources that you would like to add to your case and click Next.

 1. In addition to the system identified data sources, you may have additional custodial sources that you would like to assign to a user. Select Update to assign content locations, like mailboxes, sites, and Teams to a custodian. Once you have finalized the data sources relevant for a specific custodian, this mapping will be maintained and extend to the eDiscovery collection, processing, and review workflows.
    1. **Exchange Mailboxes** - Click Choose users, groups, or Teams and then click Choose users, groups, or teams again. To specify mailboxes to assign to the selected custodian, use the search box to find user mailboxes and distribution groups. You can also assign the associated mailbox for an Office 365 Group or a Microsoft Team. Select the user, group, team check box, click Choose, and then click Done.
    1. **SharePoint Sites** - Click Choose sites and then click Choose sites again to specify additional SharePoint and OneDrive for Business sites that you would like to assign to the selected custodian. You can also add the URL for the SharePoint site for an Office 365 Group or a Microsoft Team. Type the URL for each site that you want to assign. Click Choose, and then click Done.
    1. **Microsoft Teams** – The system will automatically identify Microsoft Teams that the custodian is a member of today. Once a Team is selected, the system will automatically identify & select the associated SharePoint site and Group Mailbox. Select the teams, click Choose, and then click Done.
    
      To add Teams not identified, you will need to separately add the Mailbox and SharePoint site as shown above. See the More information section for tips on putting additional Office 365 Groups and Microsoft Teams on hold.

1. Finalize your selection to place the selected custodians & data sources on hold, if needed. Once a custodian is placed on hold, a custodian hold policy containing all custodial sources will automatically be created.
    
 [!NOTE]

When you click Choose users, groups, or teams to specify mailboxes, the mailbox picker that's displayed is empty. This is by design to enhance performance. To add people to this list, type a name (a minimum of 3 characters) in the search box.
    




