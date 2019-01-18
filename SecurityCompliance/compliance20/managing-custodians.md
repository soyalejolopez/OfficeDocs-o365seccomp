---
title: "Working with Custodians"
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
Often times, when an organization is responding to a legal investigation, the workflow around identifying, preserving, and collecting potentially relevant content is based off people or data custodians within their organization. In eDiscovery, these individuals are called data custodians and are defined as “persons having administrative control of a document or electronic file”. For example, the data custodian of an email could be the owner of the mailbox which contains the relevant message.  

When an investigation begins, the eDiscovery team must quickly identify all the relevant custodians and data sources related to the case. Over time, the lists of custodians and their data sources may expand or contract. As a result, organizations must maintain a controlled process around identifying, preserving, and collecting custodial content throughout the lifecycle of a case.

Within an Office 365 Advanced eDiscovery case, Legal teams can add individuals within their organization as data custodians and automatically identify & preserve custodial sources such as Exchange, OneDrive, SharePoint, and Teams sites. By using the built-in and in-place Custodian Management tool, organizations can secure electronically stored information (ESI) from inadvertent deletion and say goodbye to manual, time consuming, and error-prone legal hold processes. 

This set contains the following sections:
  - Roles & Permissions
  - Adding Custodians
  - Managing Custodians
  - Viewing Custodian Activities 
  - Updating Existing Custodians
  - Releasing Custodians 

# Roles and Permissions
Legal teams can control and segment their case activity using eDiscovery related RBAC roles in the Security and Compliance Center. In Advanced eDiscovery, you can leverage the built-in eDiscovery Manager and eDiscovery administrator role groups to allow users to manage the end-to-end eDiscovery workflow.

In addition to the built-in role groups, you can configure and define your own roles by assigning a subset of permissions to a specific role. To manage custodians within a case, your role group must have the following permissions:  

  1. Case Management: Lets users create, edit, delete, and control access to eDiscovery cases in the Security & Compliance Center.
  2. Hold: Lets users place content in mailboxes, public folders, sites, Skype for Business conversations, and Office 365 groups on hold. When content is on hold, content owners will still be able to modify or delete the original content, but the content will be preserved until the hold is removed or until the hold duration expires.


