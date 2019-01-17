---
title: "Error remediation when processing data"
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

# Error remediation when processing data

Error remediation allows eDiscovery administrators the ability to rectify data issues which prevent Microsoft 365 Advanced eDiscovery from properly processing the content. For example, files that are password protected cannot be processed since the files are locked or encrypted. Using error remediation, eDiscovery administrators can download files with such errors, remove the password protection and upload the remediated files.

// BUGBUG: Need to add walkthrough of Error Remediation.

When remediated files are uploaded, the original metadata is preserved with the exception of the following fields. For a definition of all Advanced eDiscovery metadata fields, click here.

- Text
- HasText
- ExtractedTextSize
- DocumentExtractedUrl
- ItemExtractedUrl
- IsParentExtractedUrl
- LoadId
- ProcessingStatus
- ProcessingErrorMessage
- IsErrorRemediate
- WordCount
- WorkingsetId