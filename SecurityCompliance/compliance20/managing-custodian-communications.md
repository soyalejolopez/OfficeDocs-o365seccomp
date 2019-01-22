---
title: "Working with communications in Advanced eDiscovery"
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

# Overview
Office 365 Advanced eDiscovery allows legal departments to simplify their processes around tracking and distributing legal hold notifications. The Custodian Communications feature enables legal departments to manage and automate their entire legal hold processes – from notifications, reminders, and escalations –all in one place.

## What is a Legal Hold Notification?
A legal hold notice (also known as a litigation hold) is a notification sent from an organization’s legal department to employees, contingent staff, or other data custodians. These notifications instruct custodians to preserve electronically stored information (ESI) as well as any material that may be relevant to an active or imminent legal matter. Legal teams must know that each custodian has received, read, and understood, and agreed to comply with the given instructions.

## The Legal Hold Notification Process
An organization has a duty to preserve relevant information when it learns about an impending litigation or regulatory investigation. In order to comply with its preservation requirements, the organization should immediately inform potential custodians about their duty to preserve relevant information. 

With Advanced eDiscovery, legal teams can create and customize their legal hold notification workflow. The Custodian Communications feature allows legal teams to configure the following notices and workflows:

1. Issuance Notice: A legal hold notice is issued (or initiated) by a notification from the legal department to custodians who might have relevant information about the case matter. This notice instructs those custodians to preserve any information that might be needed for discovery. 
   
2.	Re-Issuance Notice: During a case, custodians may be required to preserve additional or less information than was previously instructed. For this scenario, you can update the existing hold notice and re-issue it to your custodians.

3.	Release Notice: Once a matter is resolved and the custodian is no longer subject to a preservation duty, the custodian can be released so that information is no longer retained if not needed. In addition, your custodian will be notified that they are no longer under preservation duty and with outstanding instructions on how to resume their activity.


In some instances, just issuing a notice is not enough to satisfy legal discovery requirements. With each notification, Legal teams can schedule a set of reminders and escalations workflows to automatically follow-up with unresponsive custodians.

1.	Reminders:  After a legal hold notice has been issued or re-issued to a set of custodians, an organization may set up reminders to alert unresponsive custodians. 

2.	Escalations: In some cases, if a custodian remains unresponsive even after a set of reminders, the legal team can set up an escalation workflow to notify the custodian and his/her manager.

## Roles and Permissions 
Legal teams can control and segment their case activity using eDiscovery related RBAC roles in the Security and Compliance Center. 

To create and manage legal hold notifications, a user must be part of the following role groups:
- eDiscovery Manager - Members of this role group can create and manage eDiscovery cases. They can add and remove members, place custodians and content locations on hold, manage legal hold notifications, create and edit Content Searches associated with a case, export the results of a Content Search, and prepare search results for analysis in Advanced eDiscovery. There are two sub-groups in this role group. The difference between these subgroups is based on scope.
  - eDiscovery Manager - Can view and manage the eDiscovery cases they create or are a member of. If another eDiscovery Manager creates a case but doesn't add a second eDiscovery Manager as a member of that case, the second eDiscovery Manager won't be able to view or open the case on the eDiscovery page in the Security & Compliance Center. eDiscovery Managers can also access their cases in Advanced eDiscovery to perform analysis tasks.
  - eDiscovery Administrator - Can perform all case management tasks that an eDiscovery Manager can do. Additionally, an eDiscovery Administrator can:
    - View all cases that are listed on the eDiscovery page.
    - Manage any case in the organization after they add themself as a member of the case.
    - Access case data in Advanced eDiscovery for any case in the organization.


You can learn more on how to configure your own role groups on the Roles and Permissions documentation.


