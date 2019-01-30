---
title: "Tune anti-phishing protection in Exchange Online"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 
ms.audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
description: "Admins can learn the order of steps to take as they progressively harden their Exchange Online organizations against phishing attacks."
---

# Tune anti-phishing protection in Exchange Online

Although Microsoft Office 365 comes with a variety of anti-phishing protections that are enabled by default, some phishing emails might still get through to your mailboxes. This topic describes a methodical approach to finding out why a phishing message got through, and what you can do to adjust the anti-phishing settings in your Exchange Online organization _without accidentally making things worse_.

## Step 1: Report the phishing message to Microsoft

To report the phishing message to us, it's important that you use the Report Message add-in for Outlook and Outlook on the web (formerly known as Outlook Web App). Using the add-in preserves the original message header fields in the message. Don't forward the message to us, because the original message headers aren't included in a forwarded message.

ATP or TI required?

Ask Denise

To enable and use the Report Message add-in, see [Enable the Report Message add-in](enable-the-report-message-add-in.md).

## Step 2: Learn why you got the phishing message by inspecting the message headers

a.	Reading Headers and what they mean

SPF/DKIM/DMARC header information not Send-To/To

SKI (Skipped) Spoofed; looks real fails on final phishing filter

b.	Header tool 

[Message Header Analyzer](https://testconnectivity.microsoft.com/MHA/Pages/mha.aspx)

Message released from quarantine?.

## Step 3: Block these phishing messages

a.	Sku related or CFA (?)

ATP: Antiphishing policies Brendon, Denise

b.	Dealing with compromised accounts – MFA, forwarding rules, restricted users etc.

Sam Workman



## Step 4: Best practices to stay protected

a.	Allow lists/ETRs that cause problems
    i.	Your own domain on the allow list.

rules to go around phishing (?)

b.	Authentication 
    i.	Dkim (and SPF and DMARC)
    ii.	Spoof intelligence
c.	Bulk
