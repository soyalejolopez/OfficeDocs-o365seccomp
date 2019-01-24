---
title: "Create a legal hold notice"
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

# Creating a Legal Hold Notice
Using Advanced eDiscovery Custodian Communications, organizations can manage their  workflows around communicating with custodians. Through the Communications tool, legal teams can systematically send, collect, and track legal hold notifications. The flexible creation process also allows teams to customize hold notification workflows and content. 

**To create a Legal Hold Notice:**
## Step 1: Specify Communication Details
The first step is to specify the appropriate details for your communication or legal hold notice.

1. In the Security & Compliance Center, click **eDiscovery > Advanced eDiscovery** to display the list of cases in your organization.
   
2. Navigate to the **Communications** tab and click **Create Communication**.
   
3. Specify the communication details.
    - **Communication Name**: This is the name for the communication.
    - **Issuing Officer**: The dropdown will show you a list of a case members. Each notice sent to the custodians will be sent on behalf of the specified issuing officer.
   
   Note, these fields are required to move to the next step.

## Step 2: Define the Portal Content
Next, you can create and add your hold notice content. On the **Define Portal Content** step, specify the contents of your hold notice. This content will automatically be appended to the Issuance, Re-Issue, Reminder, and Escalation notices.In addition, this content will appear in the custodian's Compliance Portal. 

To create the Portal Content:
1. Enter your hold notice into the textbox for the portal content. 
2. Insert Merge variables into your notice to customize the notice and share the Custodian Compliance Portal.
3. Click **Next**

  [!Tip]
  Learn more about how you can customize your content and format by viewing the [Using the Communications Editor](~compliance20\using-communications-editor.md) documentation. 

## Step 3: Set the Required Notifications
Once you have defined the contents of your hold notice, you can set up your workflows around sending and managing your notification process. The notifications are emails that are sent to notify and follow-up with custodians. Every custodian added to the communication will receive the same notification. 

In order to set up and send a hold notice, the following notifications are required:

### Issuance Notification 
Once the communication is created, the **Issuance Notification** is initiated by the specified Issuing Officer. The Issuance notification is the first communication sent to the custodian to inform them about their preservation obligations. 

To create an issuance notification:
   1. Select **Edit** next to the **Issuance** section.
   2. If needed,  you can add additional case members or staff to the **CC** and **BCC** fields. To add multiple users to the CC and BCC fields, separate the email addresses with a semi-colon.
   3. (Required) Specify the **subject** for the emailed notice. 
   4. (Required) Specify the contents or additional instructions that you would like to share with the custodian.
       - Note that the content from *Step 2* is added to the end of the Issuance notification. 
   5. Click **Save** 

### Re-Issuance Notification 
As the case progresses, custodians may be required to preserve additional or less data than was previously instructed. Once you update the contents of your hold notice, the re-issuance notification alerts the corresponding custodians regarding changes to their preservatin obligations. 

To create a re-issuance notification: 
   1. Select **Edit** next to the **Re-Issuance** section.
   2. If needed,  you can add additional case members or staff to the **CC** and **BCC** fields. To add multiple users to the CC and BCC fields, separate the email addresses with a semi-colon.
   3. (Required) Specify the **subject** for the emailed notice. 
   4. (Required) Specify the contents or additional instructions that you would like to share with the custodian.
       - Note that the content from *Step 2* is added to the end of the Re-Issuance notification.
   5. Click **Save** 

  [!Tip]
  If a hold notification is modified, the re-issue notification will automatically be sent to the all the custodians assigned to the notice. Once sent, custodians will be asked to re-acknowledge their hold notice. If you have set up any reminder or escalation workflows, these will re-start as well. 

### Release Notice
Once a matter is resolved or if a custodian is no longer subject to preservation duty, you can release a custodian from a case. If the custodian was previously issued a hold notice, the release notification can be used to alert custodians that they have been released from their obligation.

To create a release notification: 
   1. Select **Edit** next to the **Release** section.
   2. If needed,  you can add additional case members or staff to the **CC** and **BCC** fields. To add multiple users to the CC and BCC fields, separate the email addresses with a semi-colon.
   3. (Required) Specify the **subject** for the emailed notification. 
   4. (Required) Specify the content or additional instructions that you would like to share with the custodian.
   5. Click **Save** and move to the next step. 

## (Optional) Step 4: Set the Optional Notifications
Optionally, you can simplify your working around following up with unresponsive custodians by creating and scheduling automated reminder and escalation workflows.

### Reminder
After you have sent a hold notification, you can follow-up with unresponsive custodians by defining a reminder workflow. 

To schedule reminders:
   1. Select **Edit** next to the **Reminder** section.
   2. Enable the **Reminder** workflow by moving the **Status** toggle to **On**.
   3. (Required) Specify the **Reminder Interval (in days)**. This is how many days you would like to wait before sending the first and follow-up reminder notifications. For example, if you set the reminder interval to 7 days, then the first reminder would be sent 7 days after the hold was initially issued. All subsequent reminders would also be sent every 7 days. 
   4. (Required) Specify the **Number of Reminders**. This field specifies how many reminders you would like to send to un-responsive custodians. For example, if you set the number of reminders to 3, then a custodian would receive a maximum of 3 reminders. Once a custodian acknowledges their hold notice, the reminders will terminate for that user. 
   5. (Required) Specify the **subject** for the emailed notification. 
   6. (Required) Specify the contents or additional instructions that you would like to share with the custodian.
       - Note that the content from *Step 2* is added to the end of the reminder notification.
   7. Click **Save** and move the the next step.

### Escalation 
In some scenarios, you may need additional ways to follow up with unresponsive custodians. If a custodian does not acknowledge his or her hold notice after receiving the specified number of reminders, the legal team can specify a workflow to automatically send an escalation notice to the custodian and his or her manager. 

To schedule escalations:
   1. Select **Edit** next to the **Escalation** section.
   2. Enable the **Escalation** workflow by moving the **Status** toggle to **On**.
   3. (Required) Specify the **Escalation Interval (in days)**. 
   4. (Required) Specify the **Number of Escalation**. This field specifies how many escalations you would like to send to un-responsive custodians. For example, if you set the number of escalations to 3, then an escalation notice would be sent to the custodian and their manager a maximum of 3 times. Once a custodian acknowledges their hold notice, the escalations will terminate for that user. 
   5. (Required) Specify the **subject** for the emailed notification. 
   6. (Required) Specify the contents or additional instructions that you would like to share with the custodian.
       - Note that the content from *Step 2* is added to the end of the escalation notification.
   7. Click **Save** and move the the next step.
   
## Step 5: Assign Custodians 
Once you have finalized your content, select the custodians that you would like to send the communications. 

To add custodians:
   1. Assign custodians to the communication by selecting them from the checkboxes on the left.
   2. Once the communication is created, your notification workflow will automatically apply to the selected custodians.
   3. Click **Next** to review your settings and communication details.

## Step 6: Review Settings
Once completed, the system will automatically start your communication workflow by sending the Issuance Notice. 

>[!NOTE]
>You can only add custodians who have been added to the case and have not already been issued another notice within the case.
