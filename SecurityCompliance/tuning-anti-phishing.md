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

## Report the phishing message to Microsoft

Reporting phishing messages is helpful in tuning the filters that are used to protect all customers in Office 365.

Send the phishing messages _as attachments_ in a new, otherwise empty message to **phish@office365.microsoft.com**. Don't just forward the original message; otherwise, we can't examine the original message headers. Or, you can use the [Report Message](https://docs.microsoft.com/office365/securitycompliance/enable-the-report-message-add-in) add-in in Outlook or Outlook on the web (formerly known as Outlook Web App).

**More information**:

[Submit spam, non-spam, and phishing scam messages to Microsoft for analysis](submit-spam-non-spam-and-phishing-scam-messages-to-microsoft-for-analysis.md).

## Inspect the message headers

In Outlook, you can view the message headers in an open message by clicking **File** \> **Properties**. The message headers are shown in the **Internet headers** field. For ease of reading, you can click anywhere in the **Internet headers** field, press Ctrl+A, then Ctrl+C, and then you can paste the results in Notepad.

The first header field you should check is **X-Forefront-Antispam-Report**. Specifically, you are looking for indications of skipped spam or phish filtering in the Spam Filtering Verdict (SFV) or IP Filter Verdict (IPV) fields. The values to look for are described in the following table:

|**Value**|**Description**|
|:-----|:-----|
|`IPV:CAL`|The message was allowed through the spam filters because the IP address was specified in an IP Allow list in the connection filter. For more information, see [Configure the connection filter policy](configure-the-connection-filter-policy.md).|
|`SFV:SFE`|Filtering was skipped and the message was allowed through because it was sent from an email address (not an entire domain) in a user's Safe Sender List in Outlook. For more information, see [Add recipients of my email messages to the Safe Senders List](https://support.office.com/article/BE1BAEA0-BEAB-4A30-B968-9004332336CE).|
|`SFV:SKA`|The message skipped filtering and was delivered to the inbox because it matched an allow list in the spam filter policy, such as the **Sender allow** list. For more information, see [Configure your spam filter policies](configure-your-spam-filter-policies.md).|
|`SFV:SKN`|The message was marked as non-spam prior to being processed by the content filter. This includes messages where the message matched a mail flow rule (also known as a transport rule) to automatically mark it as non-spam and bypass all additional filtering (**Set the spam confidence level (SCL) to** \> **-1**). For more information, see [Mail flow rule actions in Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)|
|`SFV:SKI`|Similar to `SFV:SKN`, the message skipped filtering for another reason such as being intra-organizational email within a tenant.|
|`SFV:SKQ`|The message was released from the quarantine and was sent to the intended recipients.|


**IPV:CAL**: Verify that you aren't allowing your own domain in the connection filter policy! This is an open invitation to received spoofed messages from anywhere.

`SFV:SE`: This sounds like Safelist Aggregation. Is this even available?

Looking for skips in the protection stack

SKA/SKN/SKI whitelisted

SPF/DKIM/DMARC header information not Send-To/To

SKI (Skipped) Spoofed; looks real fails on final phishing filter



b.	Header tool 

[Message Header Analyzer](https://testconnectivity.microsoft.com/MHA/Pages/mha.aspx)

[Message Header Analyzer app for Office](http://go.microsoft.com/?linkid=9842186)

Message released from quarantine?. or message trace

## Step 3: Block these phishing messages

a.	Sku related or CFA (?)

Standard: Block specific senders, submit problem messages to MS; we'll take care of it.

ATP: Antiphishing policies Brendon, Denise Safelinks. SafeAttachments

**For more information**:

[View internet message headers](https://support.office.com/article/cd039382-dc6e-4264-ac74-c048563d212c)

[Message Header Analyzer](https://testconnectivity.microsoft.com/MHA/Pages/mha.aspx)


## Step 4: Dealing with compromised accounts – MFA, forwarding rules, restricted users etc.

Dealing with compromised article

ATP: Threat explorer, etc.

1-4: existing articles



## Step 5: Best practices to stay protected

a.	Allow lists/ETRs that cause problems
    i.	Your own domain on the allow list. IP/Domain allows in ETRs, SCL -1 on ETRs

MX records point to O365; turn on quarantine (keep messages from Junk folder)

One-button ATP setup

ATP: AntiPhish Threshold levers (standard to something higher aggressive, more aggressive, most aggressive), enable stuff (SafeLinks, SafeAttachments Impersonation)

b.	Authentication 
    i.	Dkim (and SPF and DMARC) turn on for custom domains
    ii.	Review Spoof intelligence reports

Report message plug-in

MFA

c.	Bulk thresholds (tune down)

Impersonation or zero day stuff requires ATP