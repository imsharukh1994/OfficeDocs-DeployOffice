---
title: Newsletters in Outlook (Preview)
description: Describes how to configure and manage the Newsletters experience in Outlook
author: nicholasswhite
ms.author: caithart
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: outlook
ms.collection:
- Tier3
- deploy-new-outlook
ms.localizationpriority: medium
ms.custom: intro-overview
recommendations: true
ms.date: 02/24/2025
---
# Newsletters in Outlook (Preview)

Newsletters in Outlook let you create and send structured, professional newsletters quickly within Outlook. This feature helps you keep your team informed and engaged. While in Preview, admins can enable it for some or all users in an organization. Users without access can't use this feature.

End user support documentation: [Newsletters](https://support.microsoft.com/topic/b35566e6-d319-450d-8930-86e483cda3ee)

## Managing access

Access to Outlook Newsletters is managed using the OwaMailboxPolicy.OutlookNewslettersAccessLevel property. This property can be set using the `Set-OwaMailboxPolicy` cmdlet available in the Exchange Management Shell. There are four values for this property:

`ReadWrite` – user has full authoring permissions to create pages and newsletters in the Outlook Newsletters module.  
`ReadOnly` – user can read newsletters and browse pages in the Outlook Newsletters module. 
`NoAccess` – user can't access the Outlook Newsletters module in the New Outlook for Windows or Outlook for the Web. They can still read any email messages sent or forwarded to them in Mail.  
`Undefined` – if the value is undefined (never explicitly set by your organization's administrator), the Microsoft 365 service defaults to NoAccess while Outlook Newsletters is in Preview and to ReadWrite when it reaches global availability.

> [!NOTE]
> All users can read the email messages generated when publishing a newsletter to mail recipients, regardless of the `ReadOnly` permission level.  

### Licensing requirements
Newsletters is available to be enabled for any users who have both an Exchange Online mailbox and access to SharePoint. This includes all Microsoft 365 and Office 365 plans for Enterprise, Education, and Business. Exchange Online standalone plans that do not have access to SharePoint are excluded, as SharePoint is needed for storing the data. Government cloud support is not yet available.

## Managing features

### Reactions and comments

Outlook Newsletters include features that let readers engage with published content. Readers can react to individual sections of a newsletter and the entire newsletter, similar to a typical Outlook email. They can also comment using integrated controls at the end of the newsletter.

Authors can disable these engagement features when publishing a newsletter. Administrators can also disable them for the organization using the `OwaMailboxPolicy.OutlookNewslettersReactions` property.

### Recommended newsletters

Newsletter editions by default include recommendations to other content published with Outlook Newsletters to encourage greater readership in your organization. Such recommendations are included in the footer of published newsletter editions. Authors can disable these recommendations for each individual newsletter edition as they're published, or the administrator can disable these recommendations for a set of users or the entire organization using the `OwaMailboxPolicy.OutlookNewslettersShowMore` property. 

## Other tasks

### Admin view

Newsletters include a simple administrator console accessible via the **Admin** link in the navigation panel. This view only shows up for users in your organization with the ExchangeServiceAdmin or GlobalServiceAdmin roles assigned. 

This Admin view can be used to view the Newsletter pages in your organization and their owners. It includes a filter to identify Newsletter pages without owners, such as when a user leaves your organization, or pages with only one owner if your organization requires multiple owners for shared resources. Clicking on the name of the page in the admin view navigates to its page view where the admin can remediate ownership issues. 

### Audit logging

As an administrator, you can use the audit-logging tools from Microsoft Purview to monitor and audit Newsletters activities in your tenant. The logging tools allow you to filter, search, export, and analyze the log data for various newsletter events.
To access the logging tools, follow these steps:

1. Select **Audit** from the Purview tools.
2. Under **Workload**, select **SharePoint**, and apply any relevant filters, such as user or date.

When logs are available, they appear in a table. To export the results, select **Export**.

Newsletter logs include a field in **AppAccessContext** labeled `ClientAppName`, with the value *OutlookNewsletters*. 

If a logging event refers to a *SiteCollection*, it corresponds to a Newsletters page. Logs referring to a folder represent a newsletter, while logs related to specific files correspond to individual sections or images within a newsletter.

### Legal hold and discovery

An administrator with the *SharePoint Embedded Administrator* and *Compliance Data Administrator* roles can use Microsoft Purview to perform an eDiscovery search. The administrator can search for Outlook Newsletters content in two ways, depending on the location of the content:

- Sent Newsletters appear as emails in recipients' inboxes. A sent Newsletter functions like any other email, so the administrator can use Purview tools to search for these emails the same way they would search for any other email.
- Draft Newsletters and comments on Newsletters are stored in **SharePoint Embedded**. To find this content, select **Sites** as the data source.
