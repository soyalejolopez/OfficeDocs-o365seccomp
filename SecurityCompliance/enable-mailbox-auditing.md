---
title: "Manage default mailbox auditing"
ms.author: markjjo
author: markjjo
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: 
- Strat_O365_IP
- M365-security-compliance
search.appverid: 
- MOE150
- MET150
ms.assetid: aaca8987-5b62-458b-9882-c28476a66918
description: "Mailbox audit logging is turned on by default in Office 365. This means that certain actions performed by mailbox owners, delegates, and administrators are automatically logged in the Office 365 audit log, where you can search for activities performed on the mailbox."
---

# Manage default mailbox auditing
  
Starting in January of 2019, mailbox audit logging is turned on by default for all Microsoft 365 organizations. This means that certain actions performed by mailbox owners, delegates, and administrator are automatically logged, and that mailbox audit records will be available when you search for them in the audit log. Before mailbox auditing was turned on by default, you had to enable mailbox auditing for every user mailbox in your organization. Here are some benefits of "on-by-default" mailbox auditing:

- Auditing will be enabled by default when you create a new mailbox. You won't have explicitly enable it for new users. 

- You won't have manage the mailbox actions that are audited. A set of mailbox actions are audited by default for each type of logon. Types of logon include Admin, Delegate, and Owner.

- New mailbox actions will be audited by default. When Microsoft releases new mailbox actions (particularly those that will help protect your organization and help you with forensic investigations) they will automatically be added to the list of mailbox actions audited by default. This means you don't have to add (or remove) actions to the list of mailbox actions performed by owners, delegates, or admins. 

- Ensure that you're auditing the same actions for all mailboxes so you have a consistent mailbox auditing policy across your organization.

> [!TIP]
> Maybe the most important thing to keep in mind is that with this new release, you don't have to do anything to manage mailbox auditing. It just works. However, if you want to learn more, change the behavior from the default settings, or turn it off altogether, this article can help you with that.

## Verify that default mailbox auditing is turned on

To verify that default mailbox auditing is turned on for your organization, run the following command in  [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell):

```
Get-OrganizationConfig | FL AuditDisabled
``` 

A value of **False** indicates that default mailbox auditing is enabled for your organization. 

When default mailbox auditing is enabled for your organization (when the *AuditDisabled* property is set to **False**), the organizational setting will override the mailbox auditing setting for a specific mailbox. For example, if the *AuditEnabled* property for a mailbox is set to **False**, but default mailbox auditing is enabled for your organization, the default mailbox actions (describe in the previous section) will be audited for that mailbox. So if you explicitly disabled mailbox auditing for a specific mailbox, you will have to manually exclude that mailbox from default mailbox auditing. See the 


## Mailbox actions logged by default

The following table lists the mailbox actions that are currently logged by default for each logon type.


|Admin actions|Delegate actions|Owner actions|
|:---------|:---------|:---------|
|Create    |Create       | HardDelete        |
|HardDelete    |HardDelete        |MoveToDeletedItems       |
|MoveToDeletedItems    |MoveToDeletedItems         |SoftDelete         |
|SendAs    |SendAs      |    Update     |
|SendOnBehalf    |SendOnBehalf       |UpdateCalendarDelegation        |
|SoftDelete     |SoftDelete      | UpdateFolderPermissions        |
|Update    |Update       |UpdateInboxRules         |
|UpdateCalendarDelegation    | UpdateFolderPermissions        |         |
|UpdateFolderPermissions     | UpdateInboxRules        |         |
|UpdateInboxRules     |         |         |
||||

The following tables describes each of these mailbox actions:

|Mailbox action|Description|
|:---------|:---------|
|**Create** <br/> |An item is created in the Calendar, Contacts, Notes, or Tasks folder in the mailbox; for example, a new meeting request is created. Note that creating, sending, or receiving a message isn't audited. Also, creating a mailbox folder is not audited.  <br/> |
|**HardDelete** <br/> |A message was purged from the Recoverable Items folder.  <br/> |
|**MoveToDeletedItems** <br/> |A message was deleted and moved to the Deleted Items folder.  <br/> |
|**SendAs** <br/> |A message was sent using the SendAs permission. This means another user sent the message as though it came from the mailbox owner.  <br/> |
|**SendOnBehalf** <br/> |A message was sent using the SendOnBehalf permission. This means another user sent the message on behalf of the mailbox owner. The message indicates to the recipient who the message was sent on behalf of and who actually sent the message.  <br/> |
|**SoftDelete** <br/> |A message was permanently deleted or deleted from the Deleted Items folder. Soft-deleted items are moved to the Recoverable Items folder.  <br/> |
|**Update** <br/> |A message or its properties was changed.  <br/> |
|**UpdateCalendarDelegation** <br/> |A calendar delegation was assigned to a mailbox. Calendar delegation gives someone else in the same organization permissions to manage the mailbox owner's calendar.  <br/> |
|**UpdateFolderPermissions** <br/> |A folder permission was changed. Folder permissions control which users in your organization can access folders in a mailbox and the messages located in those folders.  <br/> |
|**UpdateInboxRules** <br/> |An inbox rule has been added, removed, or changed. Inbox rules are used to process messages in the user's Inbox based on the specified conditions and take actions when the conditions of a rule are met, such as moving a message to a specified folder or deleting a message.  <br/> |
|||

### Display a list of mailbox actions logged by default

You can run the following commands in Exchange Online PowerShell to display the list of mailbox actions that are audited by default for each logon type:

**Admin actions**

```
Get-Mailbox <username> | Select-Object -ExpandProperty AuditAdmin
```

**Delegate actions**

```
Get-Mailbox <username> | Select-Object -ExpandProperty AuditDelegate
```

**Owner actions**

```
Get-Mailbox <username> | Select-Object -ExpandProperty AuditOwner
```

### Verify that default mailbox actions are being logged for each logon type

With the release of default mailbox auditing, a new mailbox property named *DefaultAuditSet* has been added. This property indicates whether or not the default mailbox actions (managed by Microsoft) are being audited for each logon type for the specified mailbox. You can run the following command to display the values of this property:

```
Get-Mailbox <username> | FL DefaultAuditSet
```

A value of `Admin, Delegate, Owner` indicates that the default mailbox actions for all three logon types are being audit; this is the default state after default mailbox auditing was initially provisioned in your organization. Alternatively, a value of `Owner` indicates that the only the default mailbox actions for the mailbox owner are being audited; a value of `Delegate` or `Admin` indicates that only the default mailbox actions for delegates or admins, respectively, are being audited. If all three values aren't displayed, then the default an administrator has changed the default mailbox actions for one or more of the logon types. If there are no values displayed for the *DefaultAuditSet* property (also called a *null* value) then the mailbox actions for all three logon types have been changed.

See the [Change or restore mailbox actions logged by default](#change-or-restore-mailbox-actions-logged-by-default) section in this article for information about changing the mailbox actions that are audited.

## Enable or disable mailbox auditing for specific users

When default mailbox auditing is enabled for your organization, all mailboxes are audited for the mailbox actions listed in the previous section. However, there may be situations where an organization only wants some mailboxes to be audited. You can do this by using the **Set-MailboxAuditBypassAssociation** cmdlet in Exchange Online PowerShell to exclude mailboxes from being audited. The following sections show how to use this cmdlet to exclude a specific user or exclude a most of the users in your organization.

### Exclude a specific user

Run the following command in Exchange Online PowerShell to disable mailbox auditing for a specific user when default mailbox audit logging is enabled for your organization.

```
Set-MailboxAuditBypassAssociation -Identity <username> -AuditByPassEnabled $true
```

To verify that auditing is bypassed for the specified user, run the following command:

```
Get-MailboxAuditBypassAssociation -Identity <username> | FL AuditByPassEnabled
```

A value of **True** indicates that mailbox auditing is disabled for the specified user. 

### Exclude most users

Your organization may have reasons to disable default mailbox auditing for most users in the organization, but you still what to audit a small number of users. In this scenario, you have to leave default mailbox auditing enabled for your organization, and then use the **Set-MailboxAuditBypassAssociation** cmdlet to disable mailbox auditing for everyone except those users that you need to audit. 

The easiest way to do this is to use (or define) a mailbox property for the users that you don't want to exclude from default mailbox auditing. Then you run the **Set-MailboxAuditBypassAssociation** cmdlet and bypass auditing for all users except the ones that are assigned the specific mailbox property. For example, let say you want to disable mailbox auditing for all users except those in the Accounting department. After you ensure that the Department property for users in the Accounting department is populated with the value *Accounting*, you can run the following command in Exchange Online PowerShell:

```
Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'Department -ne "Accounting"' | Set-MailboxAuditBypassAssociation -AuditByPassEnabled $true
```

Here are some examples of using the **Get-Mailbox** and **Get-Recipient** cmdlets to return a subset of mailboxes based on common user or mailbox properties. These examples assume that relevant mailbox properties (such as  _CustomAttributeN_ or  _Department_) have been populated.
    
  `
  Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'CustomAttribute15 -ne "AuditEnabled"'
  `

  `
  Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'PostalCode -ne "98052"'
  `

  `
  Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'StateOrProvince -ne "WA"'
  `

You can use other user mailbox properties in a filter to include or exclude mailboxes. For details, see [Filterable Properties for the -Filter Parameter](http://technet.microsoft.com/library/b02b0005-2fb6-4bc2-8815-305259fa5432.aspx).


## Change or restore mailbox actions logged by default

As previously explained, one of the key benefits of default mailbox auditing is that you don't have to manage the mailboxes actions that are audited. Microsoft does this for you, and will automatically add new mailbox actions to be audited by default when they are released. However, your organization may have reasons to audit mailbox actions that are different than the set of default ones. This section shows you how to change the mailbox actions that are audited for each of the logon type, and how to revert back to the Microsoft-managed mailbox actions.

> [!IMPORTANT]
> If you make any change to the mailbox actions that are logged by default (as described in the next section) for one or more mailboxes, then any new mailbox actions released by Microsoft in the future will not audited for the mailboxes. You will have to explicitly add the new mailbox action to the list of actions that are audited for a logon type.

### Change the mailbox actions to audit

You can use the **Set-Mailbox** cmdlet with the *AuditAdmin*, *AuditDelegate*, or *AuditOwner* parameters to change the mailbox actions that are audited, depending on the logon type. Because these auditing-related parameters are multi-value parameters (meaning they can have more than one value), there are two different methods to change them.

- You can specify multiple mailbox actions that overwrite the existing actions by using the following syntax: `action1,action2,...actionN`.

- You can add or remove one or more mailbox action without affecting any existing entries by using the following syntax: `@{Add="action1","value2"}` or `@{Remove="action1","action2"}`.

Regardless of which method you use to change the mailbox actions that are audited, the mailbox actions audited by default (for the logon type that you changed) will no longer be managed by Microsoft. 

Here are some examples of using one of these methods to change the mailbox actions to audit for each of the different logon types. 

This example changes the admin mailbox actions by overwriting the default actions with SoftDelete and HardDelete. 

```
Set-Mailbox <username> -AuditAdmin HardDelete,SoftDelete
```

This example adds the MailboxLogin owner action. 

```
Set-Mailbox <username> -AuditOwner @{Add="MailboxLogin"}
```

This example removes the MoveToDeletedItems delegate action.

```
Set-Mailbox <username> -AuditDelegate @{Remove="MoveToDeletedItems"}
```


#### Checking the DefaultAuditSet property

After the first time you change the default mailbox actions for a logon type, the *DefaultAuditSet* property on the mailbox will be automatically updated to reflect this change. For example, if you run `Get-Mailbox <username> | FL DefaultAuditSet` after adding a mailbox owner action, the command will only return a value of `Admin, Delegate`. This indicates that the default mailbox actions for the owner have been changed This also means that any new mailbox owner actions released by Microsoft will not be automatically added to this mailbox.

### Restore the default mailbox actions 

If you make changes to the mailbox actions that are audited for a logon type, you can restore the default mailbox actions that are audited by running the `Set-Mailbox -DefaultAuditSet` command. When you do this, then new mailbox actions released by Microsoft (after you reverted back) will be audited for the specified mailbox.

To restore the default mailbox actions for all logon types, run the following command:

```
Set-Mailbox <username> -DefaultAuditSet Admin,Delegate,Owner
```

You can use this command to restore the default mailbox actions for any of the logon types (by using the Admin, Delegate, or Owner values for the DefaultAuditSet parameter.)

## Turn off default mailbox auditing for your organization

If for some reason your organization decides that it doesn't want to audit mailbox actions, you can turn off default mailbox auditing for your entire organization by running the following command in Exchange Online PowerShell:

```
Set-OrganizationConfig -AuditDisabled $true
```

When default mailbox auditing is turned off (the *AuditDisabled* property is set to **True**) for the organization, the following things occur:

- No mailbox actions will be audited (started from the time when auditing is disabled for the organization), even if the *AuditEnabled* property on a mailbox is set to **True**.

- Mailbox auditing won't be enabled for new mailboxes, and setting the *AuditEnabled* property on a new (or existing) mailbox to **True** will be ignored.

- Any mailbox audit bypass association settings (configured by using the **Set-MailboxAuditBypassAssociation** cmdlet) will be ignored.

To turn mailbox auditing back on for your organization, simply run the following command in Exchange Online PowerShell:

```
Set-OrganizationConfig -AuditDisabled $false
```


## Key points about default mailbox auditing

Here's a summary of key points to keep in mind about default mailbox audit logging:

- 




## Before you begin
  
- You have to use Exchange Online PowerShell to enable mailbox audit logging. You can't use the Office 365 Security &amp; Compliance Center or the Exchange admin center.
    
- You can't enable mailbox audit logging for the mailbox that's associated with an Office 365 Group or a team in Microsoft Teams.
    
- An administrator who has been assigned the Full Access permission to a user's mailbox is considered a delegate user.
  

  

## Step 3: Specify owner actions to audit

When you enable auditing for a mailbox, some actions performed by the mailbox owner are audited by default. You have to specify other owner actions to audit. See the table in the [Mailbox auditing actions](#mailbox-auditing-actions) section for a list and description of owner actions that are logged by default and the other actions that can be audited. 
  
This example adds the **MailboxLogin** and **HardDelete** owner actions to mailbox auditing for Pilar Pinilla's mailbox. This example assumes that mailbox auditing has already been enabled for this mailbox. 

```
Set-Mailbox "Pilar Pinilla" -AuditOwner @{Add="MailboxLogin","HardDelete"}
```

This example enables mailbox audit logging for Don Hall's mailbox and specifies that only the **MailboxLogin** action performed by the mailbox owner will be logged. Note that this example overwrites the default UpdateFolderPermissions action. 
  
```
Set-Mailbox "Don Hall" -AuditEnabled $true -AuditOwner MailboxLogin
```
   
This example adds the **MailboxLogin**, **HardDelete**, and **SoftDelete** owner actions to all mailboxes in the organization. This example assumes that mailbox auditing has already been enabled for all mailboxes. 
  
```
Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"} | Set-Mailbox -AuditOwner @{Add="MailboxLogin","HardDelete","SoftDelete"}
```
  
## How do you know this worked?

To verify that you have successfully enabled mailbox audit logging for a mailbox, use the **Get-Mailbox** cmdlet to retrieve the auditing settings for that mailbox. 
  
This example retrieves the auditing settings for Pilar Pinilla.

```
Get-Mailbox "Pilar Pinilla"| FL Audit*
```
   
This example retrieves the auditing settings for all user mailboxes in your organization.

```
Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"} | FL Name,Audit*
```
   
A value of **True** for the **AuditEnabled** property verifies that mailbox audit logging is enabled. 
    
## Mailbox auditing actions
  
The following table lists the actions that can be logged by mailbox audit logging. The table includes which action can be logged for the different user logon types. In the table, a **No** indicates that an action can't be logged for that logon type. An asterisk ( **\*** ) indicates that the action is logged by default. Note that an administrator who has been assigned the Full Access permission to a user's mailbox is considered a delegate user. 
  
|**Action**|**Description**|**Admin**|**Delegate**|**Owner**|
|:-----|:-----|:-----|:-----|:-----|
|**Copy** <br/> |A message was copied to another folder.  <br/> |Yes  <br/> |No  <br/> |No  <br/> |
|**Create** <br/> |An item is created in the Calendar, Contacts, Notes, or Tasks folder in the mailbox; for example, a new meeting request is created. Note that creating, sending, or receiving a message isn't audited. Also, creating a mailbox folder is not audited.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes  <br/> |
|**FolderBind** <br/> |A mailbox folder was accessed. This action is also logged when the admin or delegate opens the mailbox.  <br/> |Yes  <br/> |Yes\*\*  <br/> |No  <br/> |
|**HardDelete** <br/> |A message was purged from the Recoverable Items folder.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**MailboxLogin** <br/> |The user signed in to their mailbox.  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|**MessageBind** <br/> |A message was viewed in the preview pane or opened.  <br/> |Yes  <br/> |No  <br/> |No  <br/> |
|**Move** <br/> |A message was moved to another folder.  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|**MoveToDeletedItems** <br/> |A message was deleted and moved to the Deleted Items folder.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**SendAs** <br/> |A message was sent using the SendAs permission. This means another user sent the message as though it came from the mailbox owner.  <br/> |Yes\*  <br/> |Yes\*  <br/> |No  <br/> |
|**SendOnBehalf** <br/> |A message was sent using the SendOnBehalf permission. This means another user sent the message on behalf of the mailbox owner. The message indicates to the recipient who the message was sent on behalf of and who actually sent the message.  <br/> |Yes\*  <br/> |Yes\*  <br/> |No  <br/> |
|**SoftDelete** <br/> |A message was permanently deleted or deleted from the Deleted Items folder. Soft-deleted items are moved to the Recoverable Items folder.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**Update** <br/> |A message or its properties was changed.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**UpdateCalendarDelegation** <br/> |A calendar delegation was assigned to a mailbox. Calendar delegation gives someone else in the sa-mailboxme organization permissions to manage the mailbox owner's calendar.  <br/> |Yes\*  <br/> |No  <br/> |Yes\*  <br/> |
|**UpdateFolderPermissions** <br/> |A folder permission was changed. Folder permissions control which users in your organization can access folders in a mailbox and the messages located in those folders.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**UpdateInboxRules** <br/> |An inbox rule has been added, removed, or changed. Inbox rules are used to process messages in the user's Inbox based on the specified conditions and take actions when the conditions of a rule are met, such as moving a message to a specified folder or deleting a message.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
   
> [!NOTE]
> <sup>\*</sup> Audited by default. <br/><br/>  <sup>\*\*</sup> Entries for folder bind actions performed by delegates are consolidated. One log entry is generated for individual folder access within a time span of 24 hours.
  
If you no longer require certain types of mailbox actions to be audited, you should modify the mailbox's audit logging configuration to disable those actions. Existing log entries aren't purged until the retention age limit for audit log entries is reached. For more information about the retention age for audit log entries, see the "Before you begin" section in [Search the audit log in the Office 365 Security & Compliance Center](search-the-audit-log-in-security-and-compliance.md#before-you-begin).
  
## More info
  
- Use the Office 365 audit log to search for mailbox activity that have been logged. You can search for activity for a specific user mailbox. The following screenshot shows a list of mailbox activities that you can search for in the Office 365 audit log. Note that these activities are the same actions that are described in the "Mailbox auditing actions" section in this topic.
    
    ![You can search the Office 365 audit log for mailbox audit actions by selecting "Exchange mailbox activities" in Activities drop-down list](media/fadc34f8-9de2-4688-8b1a-bc5540e69a23.png)
  
    The following table describes each mailbox activity that you can search for and shows the corresponding mailbox auditing action.
    
    |**Activity in the audit log**|**Mailbox auditing action**|
    |:-----|:-----|
    |Created mailbox item  <br/> |Create  <br/> |
    |Copied messages to another folder  <br/> |Copy  <br/> |
    |User signed in to mailbox  <br/> |MailboxLogin  <br/> |
    |Sent message using Send On Behalf permissions  <br/> |SendOnBehalf  <br/> |
    |Purged messages from the mailbox  <br/> |HardDelete  <br/> |
    |Moved messages to Deleted Items folder  <br/> |MoveToDeletedItems  <br/> |
    |Moved messages to another folder  <br/> |Move  <br/> |
    |Sent message using Send As permissions  <br/> |SendAs  <br/> |
    |Updated message  <br/> |Update  <br/> |
    |Deleted messages from Deleted Items folder  <br/> |SoftDelete  <br/> |
    |Added permissions to folder  <br/> |UpdateFolderPermissions  <br/> |
    |Modified permissions of folder  <br/> |UpdateFolderPermissions  <br/> |
    |Removed permissions from folder  <br/> |UpdateFolderPermissions  <br/> |
    |Added or removed user with delegate access to calendar folder  <br/> |UpdateCalendarDelegation  <br/> |
   
    Note that the **Added delegate mailbox permissions** and **Removed delegate mailbox permissions** activities shown in the previous screenshot aren't related to mailbox auditing actions. They indicate whether an administrator assigned or removed the FullAccess mailbox permission. 
    
    For information about the Office 365 audit log, see [Search the audit log in the Office 365 Security &amp; Compliance Center](search-the-audit-log-in-security-and-compliance.md).
    
- Mailboxes are considered to be accessed by an administrator only in the following scenarios:
    
  - In-Place eDiscovery in Exchange Online or Content Search in Office 365 is used to search a mailbox.
    
  - [Microsoft Exchange Server MAPI Editor](https://go.microsoft.com/fwlink/p/?linkId=204086) is used to access the mailbox. 
    
- When you enable audit logging for a mailbox, you can also specify which user actions (for example, accessing, moving, or deleting a message) will be logged for each logon type (admin, delegate, or owner).
    
- To disable mailbox audit logging, run the following command:

  ```
  Set-Mailbox -Identity <identity of mailbox> -AuditEnabled $false
   ```

- The actions that are audited for each type of user aren't displayed when you run the **Get-Mailbox** cmdlet. But you can run the following commands to display all the audited actions for a specific user logon type. 

    ```
    Get-Mailbox <identity of mailbox> | Select-Object -ExpandProperty AuditAdmin
    ```

    ```
    Get-Mailbox <identity of mailbox> | Select-Object -ExpandProperty AuditDelegate
    ```

    ```
    Get-Mailbox <identity of mailbox> | Select-Object -ExpandProperty AuditOwner
    ```

- You can also export a mailbox audit log and specify the entries to include for one or more users. Each entry in the report and the audit log includes information about who performed the action and when, the action performed , and whether the action was successful. For more information, see [Export mailbox audit logs](https://go.microsoft.com/fwlink/p/?LinkID=404104).
