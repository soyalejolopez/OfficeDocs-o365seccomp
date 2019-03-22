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
description: "Admins can learn to identify the reasons why and how a phishing messages got through, and what to do to prevent more phishing messages in the future."
---

# Tune anti-phishing protection in Exchange Online

Although Microsoft Office 365 comes with a variety of anti-phishing features that are enabled by default, it's possible that some phishing messages could still get through to your mailboxes. This topic describes what you can do to discover why a phishing message got through, and what you can do to adjust the anti-phishing settings in your Exchange Online organization _without accidentally making things worse_.

## First things first: deal with any compromised accounts and make sure you block any more phishing messages from getting through

If a recipient's account was compromised as a result of the phishing message, follow the steps in [Responding to a compromised email account in Office 365](responding-to-a-compromised-email-account.md).

If your subscription includes Advanced Threat Protection (ATP), you can use [Office 365 Threat Intelligence](office-365-ti.md) to identify other users who also received the phishing message. You have additional options to block phishing messages:

- [ATP Safe Links](set-up-atp-safe-links-policies.md)

- [ATP Safe Attachments](set-up-atp-safe-attachments-policies.md)

- [ATP anti-phishing policies](set-up-anti-phishing-policies.md). Note that you can temporarily increase the **Advanced phishing thresholds** in the policy from **Standard** to **Aggressive**, **More aggressive**, or **Most aggressive**.

Verify these settings are turned on.

## Report the phishing message to Microsoft

Reporting phishing messages is helpful in tuning the filters that are used to protect all customers in Office 365.

Send the phishing messages _as attachments_ in a new, otherwise empty message to **phish@office365.microsoft.com**. Don't just forward the original message; otherwise, we can't examine the original message headers. Or, you can use the [Report Message](https://docs.microsoft.com/office365/securitycompliance/enable-the-report-message-add-in) add-in in Outlook or Outlook on the web (formerly known as Outlook Web App).

For more information, see [Submit spam, non-spam, and phishing scam messages to Microsoft for analysis](submit-spam-non-spam-and-phishing-scam-messages-to-microsoft-for-analysis.md).

## Inspect the message headers

You can examine the headers of the phishing message to see if there's anything that you can do yourself to prevent more phishing messages from coming through. In other words, examining the messages headers can help you identify any settings in your organization that were responsible for allowing the phishing messages in.

Specifically, you you should check the **X-Forefront-Antispam-Report** header field in the message headers for indications of skipped spam or phish filtering in the Spam Filtering Verdict (SFV) or IP Filter Verdict (IPV) values.

In Outlook, you can view the message headers in an open message by clicking **File** \> **Properties**. The message headers are shown in the **Internet headers** field. For ease of reading, you can click anywhere in the **Internet headers** field, press Ctrl+A, and then Ctrl+C to copy everything to the clipboard.

You can paste the raw results in Notepad, or you can paste them into the [Message Header Analyzer](https://testconnectivity.microsoft.com/MHA/Pages/mha.aspx) or the [Message Header Analyzer app for Office](http://go.microsoft.com/?linkid=9842186) to get a formatted, friendly view of the message headers.

The important values that indicate skipped filtering and the causes of skipped filtering are described in the following table:

|**Value**|**Description**|
|:-----|:-----|
|`IPV:CAL`|The message was allowed through the spam filters because the IP address was specified in an IP Allow list in the connection filter. <br/><br/> zzIs this bad? Should this result be part of the conversation here? <br/><br/> For more information, see [Configure the connection filter policy](configure-the-connection-filter-policy.md).|
|`SFV:SFE`|Filtering was skipped and the message was allowed through because it was sent from an email address (not an entire domain) in a user's Safe Sender List in Outlook. <br/><br/> zzWhat's the remedy here? Can an admin see individual Safe Senders? <br/><br/> For more information, see [Add recipients of my email messages to the Safe Senders List](https://support.office.com/article/BE1BAEA0-BEAB-4A30-B968-9004332336CE).|
|`SFV:SKA`|The message skipped filtering and was delivered to the inbox because it matched an allow list in the spam filter policy. <br/><br/> Under no circumstances should you configure your own domain in **Allowed domains** in a spam filter policy. This is an open invitation to received spoofed messages from anywhere on the internet. Likewise, you should be very careful configuring specific internal email addresses in **Allowed senders** in a spam filter policy. Although the risk isn't as great as the entire domain, you can still receive spoofed email messages from these allowed senders. <br/><br/> For more information, see [Configure your spam filter policies](configure-your-spam-filter-policies.md).|
|`SFV:SKN`|The message was marked as non-spam prior to being processed by the content filter. This includes messages affected by mail flow rule (also known as transport rule) matches that allow messages to bypass all spam filtering. <br/><br/> The rule action that allows messages to skip filtering is: **Set the spam confidence level (SCL) to** \> **-1** (or `-SetSCL "-1"` in PowerShell). The rule conditions that are most dangerous when paired with this action identify messages from senders in your domain (all senders or specific senders), or specific recipients in your domain. Rules that contain this combination of conditions and actions are an open invitation to received spoofed messages from anywhere on the internet. <br/><br/> For more information, see [Mail flow rule actions in Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)|
|`SFV:SKI`|Similar to `SFV:SKN`, the message skipped filtering for another reason such as being intra-organizational email within your organization. <br/><br/> Messages with this result are likely not the result of a dangerous or misconfigured setting in your organization. The message was from a spoofed sender, but it looks completely legitimate to the phishing filters.<br/><br/> The best thing to do with these messages is [report the phishing message to Microsoft](#report-the-phishing-message-to-microsoft) and (if necessary) follow the steps in [Responding to a compromised email account in Office 365](responding-to-a-compromised-email-account.md).|
|`SFV:SKQ`|The message was released from the quarantine and was sent to the intended recipients. <br/><br/> Admins and users need to be careful releasing messages from quarantine. You don't want to accidentally release phishing messages. <br/><br/> For more information, see [Find and release quarantined messages as an administrator](find-and-release-quarantined-messages-as-an-administrator.md) and [Find and release quarantined messages as a user in Office 365](find-and-release-quarantined-messages-as-a-user.md).|

## Best practices to stay protected

- Periodically run [Office 365 Secure Score](office-365-secure-score.md) to assess your Office 365 organization's security settings.

- Periodically review the [Spoof intelligence report](learn-about-spoof-intelligence.md) and [enable anti-spoofing protection in the anti-phishing policy](learn-about-spoof-intelligence.md#configuring-the-anti-spoofing-policy) to **quarantine** suspicious messages instead of delivering them to the user's Junk Email folder.

- Periodically review the [Threat Protection Status report](view-reports-for-atp.md#threat-protection-status-report).

- Some customers inadvertently allow phishing messages through by putting their own domain or domains in the Allow sender or Allow domain list in anti-spam policies. You should use extreme caution because doing this will allow some legitimate messages through, but it will also allow malicious messages that would normally be blocked by the Office 365 spam and/or phish filters.

- The best way to deal with legitimate messages that are blocked by Office 365 (false positives) that involve senders in your domain is to fully and completely configure the SPF, DKIM, and DMARC records in DNS for _all_ of your email domains in Office 365:

  - Verify that your SPF record identifies _all_ sources of email for senders in your domain (don't forget third-party services!).

  zzAnything else specific here?

  For configuration instructions, see:
  
  - [Set up SPF in Office 365 to help prevent spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  - [Use DKIM to validate outbound email sent from your custom domain in Office 365](use-dkim-to-validate-outbound-email.md)

  - [Use DMARC to validate email in Office 365](use-dmarc-to-validate-email.md)

- Whenever possible, we recommend that you deliver email for your domain directly to Office 365. In other words, point your domain's MX record to Office 365.

  zzIf not, mention connector intelligence here?

- Multi factor authentication (MFA) is a really good way to prevent compromised accounts. You should strongly consider enabling MFA for all of your users. For a phased approach, start by enabling MFA for your most sensitive users (admins, executives, etc.) before you enable MFA for everyone. For instructions, see [Set up multi-factor authentication](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).

- Forwarding rules to external recipients are often used by attackers to extract data. Use the **Review mailbox forwarding rules** information in [Office 365 Secure Score](office-365-secure-score.md) to find and even prevent forwarding rules to external recipients. For more information, see [Mitigating Client External Forwarding Rules with Secure Score](https://blogs.technet.microsoft.com/office365security/mitigating-client-external-forwarding-rules-with-secure-score/).

- zzOne-button ATP setup?
