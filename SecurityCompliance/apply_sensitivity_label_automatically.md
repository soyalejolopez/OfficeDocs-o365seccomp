---
title: "Apply a sensitivity label to content automatically"
ms.author: stephow
author: stephow-MSFT
manager: laurawi
ms.date: 
ms.audience: Admin
ms.service: o365-administration
localization_priority: Priority
ms.collection: Strat_O365_IP
search.appverid: 
- MOE150
- MET150
description: "When you create a sensitivity label, you can automatically assign a label to a document or email, or you can prompt users to select the label that you recommend."
---

# Apply a sensitivity label to content automatically

When you create a sensitivity label, you can choose what types of sensitive information that you want labeled, and the label can either be applied automatically, or you can prompt users to apply the label that you recommend.

The ability to apply sensitivity labels to content automatically is important because:

- You don't need to train your users on all of your classifications.

- You don't need to rely on users to classify all content correctly.

- Users no longer need to know about your policies - they can instead focus on their work.

> [!NOTE]
> The capability to apply labels automatically requires an Office 365 Enterprise E5 license for each user who has permissions to edit content that's been automatically labeled in a site or mailbox. Users who simply have read-only access do not require a license.

Note - Only for Office apps on Windows 10. Info and link to AIPv2 install

![Auto labeling options for sensitivity labels](media/Sensitivity_labels_Auto_labeling_options.png)

# How automatic or recommended labels are applied

- Automatic classification applies to Word, Excel, and PowerPoint when documents are saved, and apply to Outlook when emails are sent. These conditions apply to the body text in documents and emails, and to headers and footers.

    You cannot use automatic classification for documents and emails that were previously manually labeled, or previously automatically labeled with a higher classification.

- Recommended classification applies to Word, Excel, and PowerPoint when documents are saved. You cannot use recommended classification for Outlook unless you configure an advanced client setting that is currently in preview.

    You cannot use recommended classification for documents that were previously labeled with a higher classification.

You can change this behavior so that the Azure Information Protection client periodically checks documents for the condition rules that you specify. This configuration requires an advanced client setting that is currently in preview.

# How multiple conditions are evaluated when they apply to more than one label

1. The labels are ordered for evaluation, according to their position that you specify in the policy: The label positioned first has the lowest position (least sensitive) and the label positioned last has the highest position (most sensitive).

1. The most sensitive label is applied.

1. The last sublabel is applied.

# Apply a sensitivity label automatically based on conditions

One of the most powerful features of sensitivity labels is the ability to apply them automatically to content that matches certain conditions. In this case, people in your organization don't need to apply the sensitivity labels - Office 365 does the work for them.
   
You can choose to apply sensitivity labels to content automatically when that content contains specific types of sensitive information. When you configure a sensitivity label to be applied automatically, you see the same list of sensitive information types as when you create a data loss prevention (DLP) policy. 

![Options for instance count and match accuracy](media/Sensitivity_labels_instance_count_match_accuracy.png)

After you choose your sensitive informaton types, you can refine your condition by changing the instance count or match accuracy. For more inforamtion, see [Tuning rules to make them easier or harder to match](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

Further, you can choose whether a condition must detect all of the sensitive infromation types, or just one of them. And to make your conditions more flexible or complex, you can addd groups and use logical operators between the groups. For more information, see [Grouping and logical operators](data-loss-prevention-policies.md#grouping-and-logical-operators).

When a sensitivity label is automatically applied, the user sees a notification in their Office app. They can choose **OK** to dismiss the notificaiton.

NEED IMAGE OF OK NOTIFICATION AFTER AUTO LABEL

# Recommend that the user apply a sensitivity label

If you prefer, instead of applying a sensitivity label automatically to content, you can recommend to your users that they apply the label. This option provides your users the flexibility of accepting the classification and any associated protection, or dismissing the recommendation if the label is not suitable for their document or email.

![Option for reccommending a sensitivity label to users](media/Sensitivity_labels_Recommended_label_option.png)

Here's an example prompt for when you configure a condition to apply a label as a recommended action, with a custom policy tip. You can choose what text is displayed in the policy tip.

![Prompt to apply a recommended label](media/Sensitivity_label_Prompt_for_required_label.png)
