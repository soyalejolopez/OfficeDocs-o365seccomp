---
title: "Manage mailbox auditing"
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
description: "Mailbox audit logging is turned on by default in Microsoft 365 (also called default mailbox auditing or on-by-default mailbox auditing). This means that certain actions performed by mailbox owners, delegates, and administrators are automatically logged in a mailbox audit log, where you can search for activities performed on the mailbox."
---

# Manage mailbox auditing
  
Starting in January of 2019, mailbox audit logging is being turned on by default for all Microsoft 365 organizations. This means that certain actions performed by mailbox owners, delegates, and administrators are automatically logged, and that the corresponding mailbox audit records will be available when you search for them in the audit log. Before mailbox auditing was turned on by default, you had to manually enable it for every user mailbox in your organization. 

Here are some benefits of "on-by-default" mailbox auditing:

- Auditing will be enabled by default when you create a new mailbox. You won't have to manually enable it for new users. 

- You won't have manage the mailbox actions that are audited. A defined set of mailbox actions are audited by default for each type of logon. These [logon types](#mailbox-actions-logged-by-default) are Owner, Delegate, and Admin.

- New mailbox actions released by Microsoft will be audited by default. When Microsoft releases a new mailbox action (particularly one that will help protect your organization and help with forensic investigations), it will automatically be added to the list of mailbox actions audited by default. This means you don't have to add new actions to the list of mailbox actions performed by owners, delegates, or admins. 

- Ensure that you're auditing the same actions for all mailboxes so you have a consistent mailbox auditing policy across your organization.

> [!TIP]
> The important thing to remember is that with this new release, you don't have to do anything to manage mailbox auditing. However, if you want to learn more, change the behavior from the default settings, or turn it off altogether, this article can help you with that.

## Verify default mailbox auditing

To verify that default mailbox auditing is turned on for your organization, run the following command in  [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell):

```
Get-OrganizationConfig | FL AuditDisabled
``` 

A value of **False** indicates that default mailbox auditing is enabled for your organization. 

When default mailbox auditing is enabled for your organization (when the *AuditDisabled* property is set to **False**), the organizational setting will override the mailbox auditing setting for a specific mailbox. For example, if the *AuditEnabled* property for a mailbox is set to **False**, but default mailbox auditing is enabled for your organization, the default mailbox actions (describe in the previous section) will be audited for that mailbox. So if you explicitly disabled mailbox auditing for a specific mailbox, you will have to manually exclude that mailbox from default mailbox auditing. See the 


## Mailbox actions logged by default

A separate set of mailbox actions are logged by default for each of the following logon types:  

   - **Owner** - The mailbox owner. 
   - **Delegate** - Another user who's been assigned the SendAs, SendOnBehalf, or FullAccess permission to a person's mailbox. Note that an administrator who's been assigned the FullAccess permission to a user's mailbox is also considered a delegate user.
   - **Admin** - Mailboxes are considered to be accessed by an admin logon type only in the following scenarios:
    
     - When a mailbox is searched with one of the following Microsoft eDiscovery tools: 

       - Content Search in the Compliance center.
       - eDiscovery or Advanced eDiscovery in the Compliance center.
       - In-Place eDiscovery in Exchange Online.
     - When [Microsoft Exchange Server MAPI Editor](https://go.microsoft.com/fwlink/p/?linkId=204086) is used to access the mailbox.     

The following table lists the mailbox actions that are currently logged by default for each of the previous logon types.

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

Here are descriptions for each of these mailbox actions. 

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

For a complete list of mailbox actions, including actions that are available but aren't included in the set of default actions, see the [Mailbox auditing actions](#mailbox-auditing-actions) section in this article.

### Verify that default mailbox actions are being logged for each logon type

With the release of default mailbox auditing, a new mailbox property named *DefaultAuditSet* has been added. This property indicates whether or not the default mailbox actions (managed by Microsoft) are being audited for each logon type for the specified mailbox. You can run the following command to display the values of this property:

```
Get-Mailbox <username> | FL DefaultAuditSet
```

A value of `Admin, Delegate, Owner` indicates that the default mailbox actions for all three logon types are being audited and that an administrator in your organization *has not* changed the actions for any logon type. Note this is the default state after default mailbox auditing is initially provisioned in your organization. 

If an administrator in your organization has changed the mailbox actions that are audited for a logon type (by using the **Set-Mailbox** cmdlet with the *AuditAdmin*, *AuditDelegate*, or *AuditOwner* parameters), then the value for the DefaultAuditSet property will be different that the default. For example, a value of `Owner` indicates that the only the default mailbox actions for the mailbox owner are being audited, and that the actions for `Delegate` and  `Admin` have been changed. If there are no values displayed for the DefaultAuditSet property (also called a *null* value) then the mailbox actions for all three logon types have been changed.

See the [Change or restore mailbox actions logged by default](#change-or-restore-mailbox-actions-logged-by-default) section in this article for more information about changing the mailbox actions that are audited.

### Display a list of mailbox actions logged by default

You can run the following commands in Exchange Online PowerShell to display the list of mailbox actions that are currently being for a mailbox for each logon type:

**Owner actions**

```
Get-Mailbox <username> | Select-Object -ExpandProperty AuditOwner
```

**Delegate actions**

```
Get-Mailbox <username> | Select-Object -ExpandProperty AuditDelegate
```

**Admin actions**

```
Get-Mailbox <username> | Select-Object -ExpandProperty AuditAdmin
```



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

As previously explained, one of the key benefits of default mailbox auditing is that you don't have to manage the mailboxes actions that are audited. Microsoft does this for you and will automatically add new mailbox actions to be audited by default when they are released. However, your organization may have reasons to audit a set of mailbox actions that are different than the default ones. This section shows you how to change the mailbox actions that are audited for each of the logon type, and how to revert back to the Microsoft-managed default actions.

> [!IMPORTANT]
> If you make any change to the mailbox actions for a user that are logged by default (as described in the next section), then any new mailbox actions released by Microsoft will not be audited for those mailboxes. You'll have to explicitly add new mailbox action to the list of actions that are audited for a logon type.

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

After you change the default mailbox actions for a logon type, the *DefaultAuditSet* property on the mailbox will be automatically updated to reflect this change. For example, if you run `Get-Mailbox <username> | FL DefaultAuditSet` after the first time you add or remove a mailbox owner action, the command will only return a value of `Admin, Delegate`. This indicates that the default mailbox actions for the owner have been changed This also means that any new mailbox owner actions released by Microsoft will not be automatically added to this mailbox. The same is true for changing the mailbox actions for the admin or delegate logon type.

### Restore the default mailbox actions

If you made changes to the mailbox actions that are audited for a logon type, you can restore the default mailbox actions that are audited by running the `Set-Mailbox -DefaultAuditSet` command. When you do this, the following things will happen:

- The current list of mailbox actions will be replaced with the default mailbox actions for the appropriate logon type.

- Any new mailbox actions released by Microsoft will be automatically added to the list for the appropriate logon type.

- The [DefaultAuditSet mailbox property](#checking-the-defaultauditset-property) will be updated to include the appropriate logon type.

To restore the default mailbox actions for all logon types, run the following command:

```
Set-Mailbox <username> -DefaultAuditSet Admin,Delegate,Owner
```

You can use this command to restore the default mailbox actions for any of the logon types (by using the **Admin**, **Delegate**, or **Owner** values for the *DefaultAuditSet* parameter.)

## Turn off default mailbox auditing for your organization

If for some reason your organization decides that it doesn't want to audit mailbox actions, you can turn off default mailbox auditing for your entire organization by running the following command in Exchange Online PowerShell:

```
Set-OrganizationConfig -AuditDisabled $true
```

When default mailbox auditing is turned off (the *AuditDisabled* property is set to **True**) for the organization, the following things occur:

- No mailbox actions will be audited (started from the time when auditing is disabled for the organization), even if the *AuditEnabled* property on a mailbox is set to **True**.

- Mailbox auditing won't be enabled for new mailboxes and setting the *AuditEnabled* property on a new (or existing) mailbox to **True** will be ignored.

- Any mailbox audit bypass association settings (configured by using the **Set-MailboxAuditBypassAssociation** cmdlet) will be ignored.

To turn mailbox auditing back on for your organization, simply run the following command in Exchange Online PowerShell:

```
Set-OrganizationConfig -AuditDisabled $false
```

## Mailbox auditing actions
  
The following table summarizes the actions that are audited for each user logon type. In the table, an asterisk ( **\*** ) indicates that the action is logged by default. A **No** indicates that an action can't be logged for that logon type. Note that an administrator who has been assigned the Full Access permission to a user's mailbox is considered a delegate user. 
  
|**Action**|**Description**|**Admin**|**Delegate**|**Owner**|
|:-----|:-----|:-----|:-----|:-----|
|**Copy** <br/> |A message was copied to another folder.  <br/> |Yes  <br/> |No  <br/> |No  <br/> |
|**Create** <br/> |An item is created in the Calendar, Contacts, Notes, or Tasks folder in the mailbox; for example, a new meeting request is created. Note that creating, sending, or receiving a message isn't audited. Also, creating a mailbox folder is not audited.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes  <br/> |
|**FolderBind**\** <br/> |A mailbox folder was accessed. This action is also logged when the admin or delegate opens the mailbox.  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|**HardDelete** <br/> |A message was purged from the Recoverable Items folder.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**MailboxLogin** <br/> |The user signed into their mailbox.  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|**MessageBind**\*** <br/> |A message was viewed in the preview pane or opened.  <br/> |Yes  <br/> |No  <br/> |No  <br/> |
|**Move** <br/> |A message was moved to another folder.  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|**MoveToDeletedItems** <br/> |A message was deleted and moved to the Deleted Items folder.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**SendAs** <br/> |A message was sent using the SendAs permission. This means another user sent the message as though it came from the mailbox owner.  <br/> |Yes\*  <br/> |Yes\*  <br/> |No  <br/> |
|**SendOnBehalf** <br/> |A message was sent using the SendOnBehalf permission. This means another user sent the message on behalf of the mailbox owner. The message indicates to the recipient who the message was sent on behalf of and who actually sent the message.  <br/> |Yes\*  <br/> |Yes\*  <br/> |No  <br/> |
|**SoftDelete** <br/> |A message was permanently deleted or deleted from the Deleted Items folder. Soft-deleted items are moved to the Recoverable Items folder.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**Update** <br/> |A message or its properties was changed.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**UpdateCalendarDelegation** <br/> |A calendar delegation was assigned to a mailbox. Calendar delegation gives someone else in the organization permissions to manage the mailbox owner's calendar.  <br/> |Yes\*  <br/> |No  <br/> |Yes\*  <br/> |
|**UpdateFolderPermissions** <br/> |A folder permission was changed. Folder permissions control which users in your organization can access folders in a mailbox and the messages located in those folders.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**UpdateInboxRules** <br/> |An inbox rule has been added, removed, or changed. Inbox rules are used to process messages in the user's Inbox based on the specified conditions and take actions when the conditions of a rule are met, such as moving a message to a specified folder or deleting a message.  <br/> |Yes\*  <br/> |Yes\*  <br/> |Yes\*  <br/> |
   
> [!NOTE]
> <sup>\*</sup> Audited by default when default mailbox auditing is enabled for the logon type. <br/><br/>  <sup>\*\*</sup> Entries for folder bind actions performed by delegates are consolidated. One log entry is generated for individual folder access within a time span of 24 hours. <br/><br/> <sup>\*\*\* </sup> The MessageBind action has been deprecated, and it is no longer available to add to the list of mailbox actions for the admin logon type. 

