---
title: "Tag documents in a working set"
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

# Tag documents in a working set

## Tag Overview

Organizing content within a working set is important in order to complete various workflows including culling unnecessary content, identifying relevant content, identifying content that needs review by an expert/attorney, etc. As users are understanding the content, their opinions related to the content can be captured using tags. For example, if the intent is to cull unnecessary content, a user can tag documents with a tag such as “non-responsive” and later a search can be created to exclude any content tagged as “non-responsive” thereby eliminating that content from the next step in the flow. Tag panels can be customized for every case so that it supports the intended review workflow.

## Tag Types

Advanced eDiscovery provides two different tag types. Single choice tags will restrict users to select a single tag within a group. This can be useful to ensure users don’t select conflicting tags such as “responsive” and “nonresponsive”. Multiple choice tags allow users to select multiple tags within a group.

## Tag Structure

Beyond the tag types, structure can also be used to make tagging document more intuitive. Tags are grouped by sections. Working set search supports the ability to search by tag **and** section meaning a search can be created to retrieve documents tagged with any tag within a section.

![A screenshot of a cell phone
Description automatically generated](../media/Tagtypes.png)

Along with sections, tags can be organized with nesting. For example, if the intent is to identify privileged content and record the type of privilege, nesting can be used to make it clear that a user can tag a document as “Privileged” and select the type of privilege by checking the appropriate nested tags.

![A screenshot of a cell phone
Description automatically generated](../media/Nestingtags.png)

## Applying Tags

There are several ways to apply a tag to content:

### 

### Tagging a single document

When viewing a document in a working set, the tag panel can be viewed by ensuring Tag Panel is selected

![A screenshot of a computer
Description automatically generated](../media/Singledoctag.png)

This method will apply tags to the file in the viewer.

### Bulk tagging

Bulk tagging can be done by selecting multiple files in the results grid and interacting with the panel similar to tagging single documents. Bulk un-tagging can be done by selecting tags twice; the first click will apply the tag, the second selection will ensure that tag is clear for all selected files.

![A screenshot of a cell phone
Description automatically generated](../media/Bulktag.png)

Note: When bulk tagging, the tag panel will display a count of files for each tag in the panel.

### Tagging in the related panel

The related panel will display various forms of related content including email family, email threading, near duplicates and hash duplicates. Often times review time can be reduced significantly by bulk tagging related content. For example, an email has several attachments and you want to ensure that the entire family is tagged consistently.

1.  With the related panel open displaying the list of related content, click the “Tag documents” button within the related panel.

2.  This will generate a pop-up with the tag panel allowing you to tag the entire family at once.

![A screenshot of a social media post
Description automatically generated](../media/Relatedtag.png)
