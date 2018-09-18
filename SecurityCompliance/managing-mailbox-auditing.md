---
title: "Managing mailbox auditing in Office 365"
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 9/17/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid: 
- MOE150
- MET150
ms.assetid: 
description: "Staring in the second half of 2018, mailbox audit logging will be enabled by default for Office 365 organizations. This allows you to search the Office 365 audit log for activities performed on the mailbox without having to specifically enable auditing for each mailbox."
---

# Managing mailbox auditing in Office 365

Enabling mailbox auditing by default addresses a specific pain-point with mailbox audit administration today, as Exchange administrators must configure the AuditEnabled setting on each mailbox to be audited after it is provisioned.  In support of Microsoft's commitment to providing our customers with an easy-to-use set of security features, Customers will no longer be required to configure mailbox auditing on a per-mailbox basis, and instead will be able rely on a tenant-wide configuration to enable or disable mailbox audit event collection.  Mailbox events will be stored on the all user mailboxes automatically without required action.

we will enable the default-auditing configuration on all tenants with a steady ramp-up with all commercial customers to be covered by the end of the calendar year.  At that time, there is nothing you need to do for the service to begin storing your user's audit events. And if you have already enabled mailbox auditing in Exchange on your user's mailboxes and are doing so for all new mailboxes - great! Mailboxes that are configured to audit today will continue to do so.

## Mailbox actions logged by default

Similar to table here: https://docs.microsoft.com/en-us/office365/securitycompliance/enable-mailbox-auditing#mailbox-auditing-actions ) 


## Verifying default mailbox auditing for your organization

In the default setting, the -AuditDisabled value will be False.

```
Get-OrganizationConfig | FL AuditDisabled
```

The value of False indicates that mailbox auditing is enabled for your orgnaization.

## Enabling mailbox auditing for a subset of users

Set-MailboxAuditBypassAssociation for all users except the ones they want audited

## Disabling mailbox auditing for specific users

When your tenancy begins auditing all mailboxes by default, the per-mailbox AuditEnabled setting will be overridden. However, you may still choose to disable mailbox auditing for some users if there is a business need. You can elect this option by configuring audit bypass associations on the identities you intend to ignore with the Set-MailboxAuditBypassAssociation cmdlet.

```
Set-MailboxAuditBypassAssociation -Identity <user mailbox> -AuditBypassEnabled $true
```


## Disabling mailbox auditing for your entire organization

How can I opt-out of default mailbox auditing?
As we begin rolling out the default-on configuration to tenants worldwide, a tenant administrator has the capability to pre-emptively override and disable all mailbox audits within their tenancy with the Set-OrganizationConfig cmdlet. You may choose to proactively prevent your tenancy's mailboxes from being audited as part of this feature introduction with this setting. If the tenant-wide AuditDisabled setting is true, all settings for mailbox audit will be overridden to ignore audits. We don't recommend you use this - but is available should your business require it.

When your organization begins auditing all mailboxes by default, you may disable all mailbox auditing with this command:

```
Set-OrganizationConfig -AuditDisabled $true
```

To re-enable all mailbox audits, run:

```
Set-OrganizationConfig -AuditDisabled $false
```



