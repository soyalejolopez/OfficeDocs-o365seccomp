---
title: "Supervision Policies in Office 365"
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- 'ms.o365.cc.SupervisoryReview'
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
ms.assetid: d14ae7c3-fcb0-4a03-967b-cbed861bb086
description: "Understanding supervision policies in Office 365"
---

# Supervision policies in Office 365

Supervision policies in Office 365 allow you to capture employee communications for examination by designated reviewers. You can define specific policies that capture internal and external email or 3rd-party communications in your organization, and then have reviewers classify the messages to make sure they are compliant with your organization's message standards. These policies can also help you overcome many modern compliance challenges, including monitoring increasing types of communication channels, increasing volume of message data, and regulatory enforcement & the risk of fines.

# Scenarios for supervision policies

Supervision policies can assist your organization in several areas:

- **Regulatory compliance:** most organizations have to comply with some type of regulatory compliance standards as part of their normal operating procedures. These regulations often require organizations to implement some type of supervisory or oversight process for messaging that is appropriate for their industry. Supervision policies can help your organization meet these requirements by providing a process to both monitor and report on corporate communications.
- **Risk management:** organizations are responsible to all communications distrubuted throughout their infrastructure and corporate network systems. Using supervision policies to help identify and manage potential legal exposure and risk can help minimize risks before they can damage corporate operations.
- **Corporate policies:** employees must comply with acceptable use, ethical standards, and other corporate policies in all their business-related communications. Supervision policies can detect policy violations and help you take corrective actions to help mitigate these types of incidents.

# Supervision policies

## Supervision policy

You'll create supervision policies in the Security &amp; Compliance Center. These policies define which communications are subject to review in your organization, define custon conditions that the communications must meet, and specifies who should perform reviews. Users included in the Supervisory Review role group can set up policies and anyone who has this role assigned can access the Supervision page under Data Governance in the Office 365 Security & Compliance Center.

## Supervised users and supervised groups

Before you start using supervision, you'll need to determine who will have their communications reviewed. All users monitored by supervision policies must have either an Office 365 Enterprise E3 license with the Advanced Compliance add-on or be included in an Office 365 Enterprise E5 subscription. If you don't have an existing Enterprise E5 plan and want to try supervision, you can [sign up for a trial of Office 365 Enterprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

## Reviewers and review groups

## Supported communication types


## Policy settings

### Direction
- **Inbound** - Choose **Inbound** to review communications that are sent **to** the people you chose to supervise **from** people not included in the policy.
- **Outbound** - Choose **Outbound** if you want to review communications that are sent **from** the people you chose to supervise ** to ** people not included in the policy.
- **Internal** - Choose **Internal** to review communications sent **between** the people you identified in the policy.

### Conditional settings

The conditions you choose will apply to communications from both email and 3rd-party sources in your organization (like from Facebook or DropBox). For details about importing 3rd-party communications into your Office 365 organization, see [Archiving third-party data in Office 365](https://technet.microsoft.com/EN-US/library/mt621583.aspx).
  
The following table explains more about each condition.
  
|**Condition**|**How to use this condition**|
|:-----|:-----|
|Message is received from any of these domains  <br><br> Message is not received from any of these domains | need description |
|Message is sent to any of these domains  <br><br> Message is not sent to  any of these domains | need description |
|Message is classified with any of these labels  <br><br> Message is not classified with any of these labels | need description |
|Message contains any of these words  <br><br> Message contains none of these words | To apply the policy when certain words or phrases are included or excluded in a message, enter each word or phrase on a separate line. Each line of words you enter will be applied separately (only one of these lines must apply for the policy to apply to the message). For more information about entering words or phrases, see the next section [Matching words and phrases to emails or attachments](configure-supervision-policies.md#Matchwords).|
|Attachment contains any of these words  <br><br> Attachment contains none of these words | To apply the policy when certain words or phrases are included or excluded in a message attachment (such as a Word document), enter each word or phrase on a separate line. Each line of words you enter will be applied separately (only one line must apply for the policy to apply to the attachment). For more information about entering words or phrases, see the next section [Matching words and phrases to emails or attachments](configure-supervision-policies.md#Matchwords).|
|Attachment is any of these file types  <br><br> Attachment is none of these file types | To supervise communications that include or exclude specific types of attachments, enter the file extensions (such as .exe or .pdf). If you want to include or exclude multiple file extensions, enter these on separate lines. Only one attachment extension needs to match for the policy to apply.|
|Message size is larger than  <br><br> Message size is not larger than | To review messages based on a certain size, use these conditions to specify the maximum or minimum size a message can be before it is subject to review. For example, if you specify **Message size is larger than** \> **1.0 MB**, all messages that are 1.01 MB and larger will be subject to review. You can choose bytes, kilobytes, megabytes, or gigabytes for this condition.|
|Attachment is larger than  <br><br> Attachment is not larger than | To review messages based on the size of their attachments, specify the maximum or minimum size an attachment can be before the message and its attachments are subject to review. For example, if you specify **Attachment is larger than** \> **2.0 MB**, all messages with attachments 2.01 MB and over will be subject to review. You can choose bytes, kilobytes, megabytes, or gigabytes for this condition.|
   
#### Matching words and phrases to emails or attachments
<a name="Matchwords"> </a>

Each line of words you enter will be applied separately (only one line must apply for the policy condition to apply to the email or attachment). For example, let's use the condition, **Message contains any of these words**, with the keywords "banker" and "insider trading" on separate lines. The policy will apply to any messages that includes the word "banker" or the phrase "insider trading". Only one of these words or phrases must occur for this policy condition to apply. Words in the message or attachment must exactly match what you enter.
  
#### Entering multiple conditions
<a name="Matchwords"> </a>

If you enter multiple conditions, Office 365 uses all the conditions together to determine when to apply the policy to communication items. When you set up multiple conditions, they must all be met for the policy to apply, unless you enter an exception. For example, let's say you need to create a policy that should apply if a message contains the word "trade", and is larger than 2MB. However, if the message also contains the words "Approved by Contoso financial", the policy should not apply. Thus, in this case, the three conditions would be as follows:
  
- **Message contains any of these words**, with the keywords "trade"
    
- **Message size is larger than**, with the value 2 MB
    
- **Message contains none of these words**, with the keywords "Approved by Contoso financial team".

### Review percentage

You can specify a percentage of all the communications governed by a supervision policy if you want to reduce the amount of content to review. We'll randomly select that amount of content from the total percentage that matched the conditions you chose. If you want reviewers to review all items,you can enter **100%** in a supervision policy.

### Exclusions

### Retention labels

### Sensitive information types

- Default types: Financial, Medical and health, Privacy, Custom
- Options for regions

### Custom keyword dictionaries

# Monitoring

## Dashboard management in Office 365

## Message review & tagging

## Filtering & exporting

## Other ways to review messages

# Reporting
Supervision policies define which communications in your organization need review for compliance, and who will perform those reviews. Use the supervision reports to see the review activity at the policy and reviewer level. For each policy, you can also view live statistics on the current state of review activity. [Learn more about supervision policies](configure-supervision-policies.md).

You can use the supervision reports to:
  
- Verify that your policies are working as you intended.
- Find out how many emails are being identified for review.
- Find out how many emails aren't compliant and which ones are passing review. This information can help you decide whether to fine-tune your policies or change the number of reviewers.

## View the Supervision report

1. Sign into the [Security &amp; Compliance Center](https://protection.office.com/) using the credentials for an admin account in your Office 365 organization that has permissions to view supervision reports.
2. Go to **Reports** \> **Dashboard**. You'll see a reporting widget for supervision and other reports you have access to.
3. Click the **Supervision** widget to open the detailed report page.

> [!NOTE]
> If you aren't able to access the **Reports** page, check that you're a member of the Supervisory Review role group, as described in [Make supervision available in your organization](configure-supervision-policies.md#SRavailable). Being included in this role group lets you create and manage supervision polices and run the report.
  
## How to use the report

When a supervision policy identifies an email for review, the email is delivered to the reviewer's Supervision folder in Outlook and Outlook web app. This report lists each policy's name and the number of communications at each stage in the review process.
  
Use the report to:
  
- View data for all or specific policies.
- View data grouped by tag type (such as Compliant, Questionable, etc.), reviewer, or message type.
- Export data to a CSV file.
- Filter data based on review activity date, tag type, reviewer, message type.
    
Here's a breakdown of the values you might see in the **Tag type** column.
  
|**Tag type**|**What it means**|
|:-----|:-----|
|Not Reviewed | The number of emails that have not been reviewed yet. These emails are awaiting review in the reviewer's supervision folder in Outlook.|
|Compliant | The number of emails reviewed and marked as compliant. No further action is needed. |
|Questionable | The number of emails reviewed and marked questionable. This acts as a flag; other reviewers can help check whether an email needs investigation for compliance. |
|Non-Compliant (Active) | The number of non-compliant emails that reviewers are currently investigating. |
|Non-Compliant (Resolved) | The number of non-compliant emails that reviewers investigated and resolved. |
   
## More details

- Supervision policies must first be provisioned before they will appear in this report.
- If policies are deleted, historical data is still shown. However, they're indicated as a "Non-existent policy", and the **Export** function isn't available.
- If the report doesn't show any data by default, it might be because the current date range doesn't have any data to show. In these cases, use the **Filters** control to change the date range.