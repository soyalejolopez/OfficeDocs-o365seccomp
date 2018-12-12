---
title: "Configure supervision policies for your organization"
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
description: "Set up a supervisory review policies to capture employee communications for review."
---

# Configure supervision policies for your organization

Use supervision policies to capture employee communications for examination by internal or external reviewers. For more information about how supervision policies can help you monitor communications in your organization, see [Supervision policies in Office 365](supervision-policies.md).
  
Follow these steps to set up and use supervision in your Office 365 organization:
  
- **Step 1 (Optional)** - [Set up groups for Supervision](configure-supervision-policies.md#exampledist)
    
    Before you start using supervision, determine who will have their communications reviewed and who will perform those reviews. If you want to get started with just a few users to see how supervision works, you can skip setting up groups for now.
    
- **Step 2 (Required)** - [Make supervision available in your organization](configure-supervision-policies.md#MakeAvailable)
    
    Add yourself to the Supervisory Review role group so you can set up policies. Anyone who has this role assigned can access the **Supervision** page under **Data Governance** in the Security & Compliance Center.
    
- **Step 3 (Optional)** - [Configure custom sensitive information types or custom keyword dictionaries](configure-supervision-policies.md#sensitiveinfo)

    If you need to use a custom sensitive info type or a custom keyword dictionary for your supervision policy, you'll need to create it before starting the supervision wizard.

- **Step 4 (Required)** - [Set up a supervision policy](configure-supervision-policies.md#setupsuper)
    
    You'll create supervision policies in the Security & Compliance Center. These policies define which communications are subject to review in your organization, and specifies who should perform reviews. Communications include email and Microsoft Teams communications, as well as 3rd-party platform communications (such as Facebook, Twitter, etc.)
    
- **Step 5 - (Optional)** [Test your new supervision policy]()

- **Step 6 - (Optional)** [Set up Outlook add-in for reviewers who do not want to use Office 365 supervision dashboard or OWA to review supervised communications](configure-supervision-policies.md#UseOutlook)
    
    The Supervision add-in gives reviewers access to the supervision functionality right within Outlook web app so they can assess and categorize each item. Support for the desktop version of Outlook is coming soon.
    
## Step 1 - Set up groups for Supervision
<a name="exampledist"> </a>

 When you create a supervision policy, you'll determine who will have their communications reviewed and who will perform those reviews. In the policy, you'll use email addresses to identify individuals or groups of people. To simplify your setup, create groups for people who will have their communication reviewed and groups for people who will review those communications. If you're using groups, you might need several—for example, if you want to monitor communications between two distinct groups of people, or if you want to specify a group that isn't going to be supervised. See [Example distribution groups](configure-supervision-policies.md#GroupExample) for details about how this works.
  
To supervise communications between or within groups in your organization, set up distribution groups in the Exchange admin center (go to **recipients** \> **groups**). For more information about setting up distribution groups, see [Manage distribution groups](http://go.microsoft.com/fwlink/?LinkId=613635)
  
> [!NOTE]
> You can also use dynamic distribution groups or security groups for supervision if you prefer. To help you decide if these better fit your organization needs, see [Manage mail-enabled security groups](http://go.microsoft.com/fwlink/?LinkId=627033), and [Manage dynamic distribution groups](http://go.microsoft.com/fwlink/?LinkId=627058).
  
### Example distribution groups
<a name="GroupExample"> </a>

This example includes a distribution group that has been set up for a financial organization called Contoso Financial International.
  
In Contoso Financial International, a sampling of communications between brokers in the United States must be supervised. However, compliance officers within that group do not require supervision. For this example, we can create the following groups:
  
|**Set up this distribution group**|**Group address (alias)**|**Description**|
|:-----|:-----|:-----|
|All US brokers | US_Brokers@Contoso.com | This group includes email addresses for all US-based brokers who work for Contoso. |
| All US compliance officers | US_Compliance@Contoso.com  | This group includes email addresses for all US-based compliance officers who work for Contoso. Because this group is a subset of all US-based brokers, you can use this alias to exempt compliance officers from a supervision policy. |
  
## Step 2 - Make supervision available in your organization
<a name="MakeAvailable"> </a>

To make **Supervision** available as a menu option in the Security & Compliance Center, you must be assigned the Supervisory Review Administrator role.
  
To do this, you can either add yourself as a member of the Supervisory Review role group, or you can create a new role group.
  
### Add members to the Supervisory Review role group

1. Sign into [https://protection.office.com](https://protection.office.com) using credentials for an admin account in your Office 365 organization.
    
2. In the Security & Compliance Center, go to **Permissions**.
    
3. Select the **Supervisory Review** role group and then click the Edit icon.
   
4. In the **Members** section, add the people who you want to manage supervision for your organization.
    
### Create a new role group

1. Sign into [https://protection.office.com](https://protection.office.com) using credentials for an admin account in your Office 365 organization.
    
2. In the Security & Compliance Center, go to **Permissions** and then click Add ( **+**).
    
3. In the **Roles** section, click Add ( **+**) and scroll down to **Supervisory Review Administrator**. Add this role to the role group.
    
4. In the **Members** section, add the people who you want to manage supervision for your organization.
    
For more information about role groups and permissions, see [Permissions in the Office 365 Security &amp; Compliance Center](permissions-in-the-security-and-compliance-center.md).
  
## Step 3 - Create custom sensitive information types or custom keyword dictionaries
<a name="sensitiveinfo"> </a>

In order to pick from existing custom sensitive information types or custom keyword dictionaries in the supervision policy wizard, you first need to create these items if needed.

### Create custom sensitive information types


### Create custom keyword dictionary

1. Using a text editor (like Notepad), create a new file that includes the keyword terms you'd like to monitor in a supervision policy. Make sure each term is on a separate line and save the file in any of the Unicode formats.
2. Import the keyword file into your Office 365 tenant using PowerShell. To connect to Office 365 with PowerShell, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

    After you've connected to Office 365 with PowerShell, run the following commands to import your keyword dictionary:

    ```
    $fileData = Get-Content "your keyword path and file name" -Encoding Byte -ReadCount 0

    New-DlpKeywordDictionary -Name "Name for your keyword dictionary" -Description "optional description for your keyword dictionary" -FileData $fileData
    ```
    For more detailed information, see [Create a keyword dictionary](create-a-keyword-dictionary.md).

3. Create a new sensitive information type in the Office 365 Security & Compliance Center. Navigate to **Classifications** \> **Sensitive info types** and follow the steps in the **New sensitive info type wizard**. Here you will:

    - Define a name and description for the sensitive info type
    - Add your custom dictionary as a requirement for matching
    - Review your selections and create the sensitive info type

    For more detailed information, see [Create a custom sensitive information type](create-a-custom-sensitive-information-type.md).

## Step 4 - Set up a supervision policy
<a name="setupsuper"> </a>
  
1. Sign into [https://protection.office.com](https://protection.office.com) using credentials for an admin account in your Office 365 organization.
    
2. In the Security & Compliance Center, go to select **Data governance** \> **Supervision**.
  
3. Select **Create** and then follow the wizard to set up the following pages of the policy. Using the wizard your will:

    - Give the policy a name and description.
    - Choose the users or groups to supervise, including choosing users or groups you'd like to exclude.
    - Define the supervision policy conditions.
    - Choose if you'd like to include sensitive information types. This is where you can select default and custom sensitive info types. 
    - Define the percentage of communications to review.
    - Choose the reviewers for the policy.
    - Review you policy selections and create the policy.

## Step 5 - Test your supervision policy

After you create a supervision policy, it's a good idea to test to make sure that the conditions you defined are being properly enforced by the policy. Follow the steps below to test your supervision policy:

1. Open an email client or Microsoft Teams logged in as a supervised user defined in the policy you want to test.
2. Send an email or Microsoft Teams chat that meets the criteria you've defined in the supervision policy. This can be a keyword, attachment size, domain, etc.
3. Log into your Office 365 tenant as a reviewer designated in the supervision policy. Navigate to **Data governance** > **Supervision** > *Your Custom Policy* > **Open** to view the report for the policy.

## Step 6 - Set up Outlook add-in for reviewers who do not want to use Office 365 supervision dashboard or OWA to review supervised communications
<a name="UseOutlook"> </a>

Reviewers that do want to use the Supervision dashboard in Office 365 or Outlook web app to review communications must install the Supervision add-in for their Outlook client.

### Step 1: Copy the address for the supervision mailbox

To install the add-in for Outlook desktop, you'll need the address for the supervision mailbox that was created as part of the supervision policy setup.
  
> [!NOTE]
> If someone else created the policy, you'll need to get this address from them to install the add-in.
 
 **To find the supervision mailbox address**
  
1. Sign into the [Security &amp; Compliance Center](https://protection.office.com) using credentials for an admin account in your Office 365 organization.
    
2. Go to **Data governance** \> **Supervision**.
    
3. Click the supervision policy that's gathering the communications you want to review.
    
4. In the policy details flyout, under ** Supervision mailbox **, copy the address.<br/>![The 'Supervision Mailbox' section of a supervision policy's details flyout showing the supervision mailbox address highlighted](media/71779d0e-4f01-4dd3-8234-5f9c30eeb067.jpg)
  
### Step 2: Configure the supervision mailbox for Outlook desktop access

Next, reviewers will need to run a couple Exchange Online PowerShell commands so they can connect Outlook to the supervision mailbox.
  
1. Connect to Exchange Online PowerShell. [How do I do this?](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
    
2. Run the following commands, where  *SupervisoryReview{GUID}@domain.onmicrosoft.com*  is the address you copied in Step 1 above, and  *User*  is the name of the reviewer who will be connecting to the supervision mailbox in Step 3.
    - ```Add-MailboxPermission "SupervisoryReview{GUID}@domain.onmicrosoft.com" -User <alias or email address of the account that has reviewer permissions to the supervision mailbox> -AccessRights FullAccess```<br/>
    - ```Set-Mailbox "<SupervisoryReview{GUID}@domain.onmicrosoft.com>" -HiddenFromAddressListsEnabled: $false```
    
3. Wait at least an hour before moving on to Step 3 below.
    
### Step 3: Create an Outlook profile to connect to the supervision mailbox

For the final step, reviewers will need to create an Outlook profile to connect to the supervision mailbox.
 
> [!NOTE]
> To create a new Outlook profile, you'll use the Mail settings in the Windows Control Panel. The path you take to get to these settings might depend on which Windows operating system (Windows 7, Windows 8, or Windows 10) you're using and which version of Outlook is installed.
  
1. Open the Control Panel, and in the **Search** box at the top of the window, type **Mail**.<br/>(Not sure how to get to the Control Panel? See [Where is Control Panel?](https://support.microsoft.com/help/13764/windows-where-is-control-panel))
  
2. Open the **Mail** app.
    
3. In **Mail Setup - Outlook**, click **Show Profiles**.<br/>![The 'Mail Setup - Outlook' dialog box with the 'Show Profiles' button highlighted](media/28b5dae9-d10c-4f2b-926a-294c857d555c.jpg)
  
4. In **Mail**, click **Add**. Then, in **New Profile**, enter a name for the supervision mailbox (such as **Supervision**).<br/>![The 'New Profile' dialog showing the name 'Supervision' in the 'Profile Name' box](media/d02ae181-b541-4ec6-8f51-698f30033204.jpg)
  
5. In **Connect Outlook to Office 365**, click **Connect to a different account**.<br/>![The 'Connect Outlook to Office 365' message with the 'Connect to a different account' link highlighted](media/fac49ff8-a7f0-4e82-a271-9ec045a95de1.jpg)
  
6. In **Auto Account Setup**, choose **Manual setup or additional server types**, and then click **Next**.
    
7. In **Choose Your Account Type**, choose **Office 365**. Then, in the **Email Address** box, enter the address of the supervision mailbox you copied previously.<br/>![The 'Choose Your Account Type' page of the 'Add Account' dialog in Outlook showing the 'Email Address' box highlighted.](media/4f601236-9f69-4cf6-a58c-0b91204aa8cb.jpg)
  
8. When prompted, enter your Office 365 credentials.
    
9. If successful, you'll see the **Supervision - \<policy name\>** folder listed in the Folder List view in Outlook.