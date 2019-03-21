---
title: "Troubleshooting tips for AzCopy in Advanced eDiscovery (Preview)"
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

# Troubleshooting tips for AzCopy in Advanced eDiscovery (Preview)
When loading Non-Office 365 data or documents for Error Remediation into Advanced eDiscovery, the user interface supplies a command that takes into account where the files are stored.  In most cases, the command should work, but there may be cases when the command is incorrectly generated.

![Upload files](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

## AzCopy is not installed on the local machine or incorrect path
If AzCopy is not installed in the location we are expecting or is not installed at all, you may receive the following error:

- The system cannot find the path specified.

If AzCopy was not installed, you can install from here: https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy

If the path to AzCopy was not in *%ProgramFiles(x86)%*, but instead, installed to the x64 directory, change *%ProgramFiles(x86)%* to *%ProgramFiles%*

