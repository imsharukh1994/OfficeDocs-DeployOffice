---
title: "Policy Management"
ms.author: janellem
author: JanelleMcIntosh-MSFT
manager: triciag
audience: ITPro
ms.topic: overview
ms.service: outlook
ms.collection:
- Tier3
- deploy-new-outlook
ms.localizationpriority: medium
ms.custom: intro-overview
recommendations: true
description: "Provides guidelines for configuring and managing mailbox accounts and features in Microsoft 365 using Exchange PowerShell cmdlets and Cloud Policy."
ms.date: 02/24/2025
---

# Policy Management in new Outlook for Windows

Admins provide Windows users in your organization with standard policies for new Outlook. These policies maintain security, productivity, and data integrity by using Exchange PowerShell cmdlets and Cloud Policy.

Most policies configure the features that are available for the mailbox accounts in their organization and help protect company data and customize the user experience. These policies affect the configuration of any Outlook app where the organization mailbox is present.

You can manage most features with Exchange PowerShell cmdlets. However, for features that span multiple Microsoft 365 experiences, like Loop and in-product Feedback, as well as settings for Diagnostic Data and Connected Experiences, you should use Cloud Policy.

> [!IMPORTANT]
> Several App-wide settings, including Theme, Text Size and Spacing, and Diagnostic Data and Connected Experiences are associated with the first account added in new Outlook. This account is considered as the primary account.
>
> While policies can be applied to any organization account in new Outlook, management of app-wide settings requires the designated account to be set as primary. For example, Theme, Diagnostic Data, and Connected Experiences.
>
> Most features like Focused Inbox and Loop are specific to each account. If you disable these features, they turn off only for that account. However, in new Outlook, other features are disabled at the organization level, for example, if any account has in-product feedback disabled, the feature becomes unavailable for all accounts.
>
> Most of the mailbox policies apply to both Outlook on the web (formerly known as Outlook Web App or OWA) and Monarch, so you can't enable them on one client but not the other.

## Allow only corporate mailboxes to be added

Admins should use the following parameters on the **Set-OwaMailboxPolicy** cmdlet to allow only corporate mailboxes to be added to the new Outlook:

- The `AllowedOrganizationAccountDomains` parameter specifies one or more account domains that can be added in Outlook. Check the syntax at [Set-OwaMailboxPolicy -AllowedOrganizationAccountDomains](/powershell/module/exchange/set-owamailboxpolicy#-allowedorganizationaccountdomains).

- The `PersonalAccountsEnabled` parameter specifies whether users are allowed to add their personal email accounts. Check the syntax at [Set-OwaMailboxPolicy -PersonalAccountsEnabled](/powershell/module/exchange/set-owamailboxpolicy#-personalaccountsenabled).

## Set Primary Account

Users can change the primary account in **Settings** \> **Accounts** \> **Email accounts** \> **Manage** for the account they want to designate as primary.

:::image type="content" source="../manage/media/policy-management/policy-email-accounts-settings.png" alt-text="Screenshot that shows how to change the primary account in Email accounts Settings." lightbox="../manage/media/policy-management/policy-email-accounts-settings-lb.png":::

The `ChangeSettingsAccountEnabled` parameter on the **Set-OwaMailboxPolicy** cmdlet allows admins to set the organization account as primary to ensure their policies are applied. Check the syntax at [Set-OwaMailboxPolicy -ChangeSettingsAccountEnabled](/powershell/module/exchange/set-owamailboxpolicy#-changesettingsaccountenabled).

## Disable automatic updating of weather location

The `WeatherEnabled` parameter on the **Set-OwaMailboxPolicy** cmdlet enables or disables weather information in the calendar in Outlook on the web. Check the syntax at [Set-OwaMailboxpolicy -WeatherEnabled](/powershell/module/exchange/set-owamailboxpolicy#-weatherenabled).

## Disable Focused Inbox

The `FocusedInboxOn` parameter on the **Set-OrganizationConfig** cmdlet turns off Focused Inbox in your organization. However, it doesn't block the availability of the feature for users. They can still re-enable Focused Inbox in their email clients. For more information, see [Configure Focused Inbox for everyone in your organization](/microsoft-365/admin/setup/configure-focused-inbox).

## Configure Junk settings

Admins can use the **Set-JunkEmailConfiguration** cmdlet to foster an agile and adaptable IT infrastructure that's well-equipped to meet the diverse needs of a modern workforce. Admins can use that cmdlet to manage the *safelist collection* (Safe Senders list, Safe Recipients list, and Blocked Senders list) on individual mailboxes. For more information, see [Set-MailboxJunkEmailConfiguration](/defender-office-365/configure-junk-email-settings-on-exo-mailboxes).

> [!TIP]
> We typically recommend that organizations use the [Standard and Strict preset security policies](/defender-office-365/preset-security-policies#appendix). But admins can [modify the default ant-spam policy](/defender-office-365/anti-spam-policies-configure#use-the-microsoft-defender-portal-to-modify-anti-spam-policies) or [create custom anti-spam policies](/defender-office-365/anti-spam-policies-configure#use-the-microsoft-defender-portal-to-create-anti-spam-policies) to adjust [bulk email thresholds](/defender-office-365/anti-spam-protection-about#bulk-complaint-threshold-bcl-in-anti-spam-policies) or create [global allow and block lists](/defender-office-365/anti-spam-protection-about#allow-and-block-lists-in-anti-spam-policies).

## Disable signatures

Admins can use either of the following methods to prevent Outlook on the web users from manually creating email signatures:

- **Exchange PowerShell**: Use the `SignaturesEnabled` parameter with the value `$false` on the **Set-OwaMailboxPolicy** cmdlet. Check the syntax at [Set-OwaMailboxPolicy -SignaturesEnabled)](/powershell/module/exchange/set-owamailboxpolicy#-signaturesenabled).

- **Exchange admin center (EAC)** On the **Outlook web app policies** page at <https://admin.exchange.microsoft.com/#/owapolicies>, click on the name of the policy \> select **Manage Features** in the **Features** section \> expand the **User experience** section \> uncheck **Email signature**, and then select **Save changes**.

For more information, see [Create a mailbox policy in Exchange Online for Outlook on the web and the new Outlook for Windows](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy).

## Specify calendar first day of week

**Set-MailboxCalendarConfiguration** is another cmdlet for managing various features and capabilities for Calendar, including: Working Hours, Work Week, Shorten appointments and meetings, and more.

For more information, see [Set-MailboxCalendarConfiguration](/powershell/module/exchange/set-mailboxcalendarconfiguration).

## Automatically configure account based on Active Directory Primary SMTP address

We recommend that admins configure the new policy for easier account set up on managed devices and to guarantee that company policies are always respected. This policy setting allows admins to control the Primary Account in Outlook for Windows.

Admins can set the policy *Require the Primary Account to match the Windows signed-in account* through the [Microsoft Intune admin center](https://intune.microsoft.com/) \> **Apps** \> **Policies for Office Apps**.

If this policy is enabled, the primary SMTP address used to sign in to Windows is suggested the first time a user adds their account to new Outlook for Windows and the user can't change it.

If you disable or don't configure this policy setting, users aren't restricted in their choice of Primary Account.

By default, no default email address is suggested.

If the user already added their personal accounts before this policy was enabled, the personal accounts are disabled when this policy is detected.

Admins can use this setting with the `PersonalAccountsEnabled` parameter value `$false` on the **Set-OwaMailboxPolicy** to block users from adding their personal accounts to new Outlook.

> [!IMPORTANT]
> This feature uses OneAuth. Therefore, Microsoft Entra ID, Workplace join, or Office activation on Local Active Directory Join environments is required.

## Specify what attachments can be downloaded

By default, new Outlook for Windows allows you to open attached Word, Excel, PowerPoint, text files, and many media files directly. The files you open vary depending on the account settings. Admins can configure the list of allowed filename extensions using the `AllowedFileTypes` and `BlockedFileTypes` parameters on the **Set-OwaMailboxPolicy** cmdlet. Check the syntax at [Set-OwaMailboxPolicy -AllowedFileTypes](/powershell/module/exchange/set-owamailboxpolicy#-allowedfiletypes) and [Set-OwaMailboxPolicy -BlockedFileTypes](/powershell/module/exchange/set-owamailboxpolicy#-blockedfiletypes).

## Disable non-Microsoft online attachments

The `AdditionalStorageProvidersAvailable` parameter on the **Set-OwaMailboxPolicy** cmdlet specifies other storage providers (for example, Box, Dropbox, Facebook, Google Drive, Egnyte, personal OneDrive) for attachments in Outlook on the web. Check the syntax at [Set-OwaMailboxPolicy -AdditionalStorageProvidersAvailable](/powershell/module/exchange/set-owamailboxpolicy#-additionalstorageprovidersavailable).

## Disable Offline mode

The `OfflineEnabledWin` parameter on the **Set-OwaMailboxPolicy** cmdlet allows or blocks the new Outlook for Windows from being used offline. Check the syntax at [Set-OwaMailboxPolicy -OfflineEnabledWin](/powershell/module/exchange/set-owamailboxpolicy#-offlineenabledwin).

## Enable Location Suggestions

The `PlacesEnabled` parameter on the **Set-OwaMailboxPolicy** cmdlet enables or disables Places in Outlook on the web. Places in Microsoft 365 lets users search, share, and map location details by using Bing. Check the syntax at [Set-OwaMailboxPolicy -PlacesEnabled](/powershell/module/exchange/set-owamailboxpolicy#-placesenabled).

## Enable a default Theme

A theme defines the colors, fonts, and images that are displayed to users in Outlook on the web and new Outlook for Windows. Admins can use the list of default themes from [Default Outlook on the web themes in Exchange Server](/exchange/clients/outlook-on-the-web/themes#default-outlook-on-the-web-themes-in-exchange-server) to find and select a default theme. Check the syntax at [Set-OwaMailboxPolicy -DefaultTheme](/powershell/module/exchange/set-owamailboxpolicy#-defaulttheme).

## Disable Suggested Replies

The `WebSuggestedRepliesDisabled` parameter on the **Set-OrganizationConfig** enables or disables Suggested Replies in Outlook on the web and new Outlook for Windows. Check the syntax at [Set-OrganizationConfig -WebSuggestedRepliesDisabled](/powershell/module/exchange/set-organizationconfig#-websuggestedrepliesdisabled).

## Disable Microsoft Loop

[Loop components in Outlook](https://support.microsoft.com/office/use-loop-components-in-outlook-9b47c279-011d-4042-bd7f-8bbfca0cb136) are portable, editable pieces of content that stay in sync across all the places they're shared.

For more information, see [Manage Loop components in OneDrive and SharePoint](/microsoft-365/loop/loop-components-configuration).

## Disable Diagnostic Data and Connected Experiences

Organizations can control whether connected experiences or diagnostic data can be sent from the new Outlook for Windows. This capability is part of our commitment to giving you the information and controls over your privacy.

:::image type="content" source="../manage/media/policy-management/policy-privacy-settings.png" alt-text="Screenshot that shows how to turn on optional connected experiences in privacy settings." lightbox="../manage/media/policy-management/policy-privacy-settings-lb.png":::

For more information, see [Use policy settings to manage privacy controls for Microsoft 365 Apps for enterprise](/microsoft-365-apps/privacy/manage-privacy-controls).

## Disable In-product feedback

New Outlook provides [in-product feedback](/microsoft-365/admin/misc/feedback-user-control#in-product-feedback) that can be managed as part of Microsoft 365 wide settings for Feedback in Cloud Policy:

:::image type="content" source="../manage/media/policy-management/policy-feeback.png" alt-text="Screenshot that shows how to provide in-product feedback through Feedback to Microsoft." lightbox="../manage/media/policy-management/policy-feeback-lb.png":::

For more information, see [Manage Microsoft feedback for your organization](/microsoft-365/admin/manage/manage-feedback-ms-org).

## Disable Contact Support in the new Outlook for Windows

Disable contact support is configured via [Cloud Policy](../../admin-center/overview-cloud-policy.md) for a Microsoft 365 organization from the [Microsoft 365 Apps admin center](https://config.office.com), specifically on the [Office Policies](https://config.office.com/officeSettings/officePolicies) page.

:::image type="content" source="../manage/media/policy-management/policy-configure-setting.png" alt-text="Screenshot of the Configure Settings page in the Microsoft 365 Apps admin center. It shows the policy management process with steps for Basics, Scope, Policies, and Review and publish. The Policies section lists five policies related to the new Outlook, including their platforms, applications, and status, all marked as Not configured." lightbox="../manage/media/policy-management/policy-configure-setting-lb.png":::

When you create a policy, after providing a name and setting a scope, you can search for *new outlook* from the Policies screen. It brings up all the available policies for new Outlook for Windows. One of those policies is *Allow access to Contact Support in the new Outlook*. This policy can be configured as **Disabled** to disable the **Contact Support** option under the Help menu in new Outlook.

:::image type="content" source="../manage/media/policy-management/policy-allow-access-contact-small.png" alt-text="Screenshot of Allow access to Contact Support in the new Outlook policy settings, showing default, enabled, and disabled configurations, and a note on diagnostic troubleshooting. The configuration setting is shown as Disabled." lightbox="../manage/media/policy-management/policy-allow-access-contact-lb.png":::

## Disable toggle from classic Outlook for Windows

Some organizations could use a policy to block the toggle from appearing in the classic Outlook for Windows until they're ready to migrate. For guidance on this policy, see [Enable or disable access to the new Outlook for Windows](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/enable-disable-employee-access-new-outlook#use-the-registry-to-enable-or-disable-the-new-outlook-toggle-in-outlook-desktop).

While this policy hides the toggle within the application, it doesn't block the mailbox from being added to the new Outlook for Windows. A separate Exchange policy can be used to block organization mailboxes from being added to new Outlook. For guidance on this policy, see [Enable or disable access to the new Outlook for Windows](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/enable-disable-employee-access-new-outlook#enable-or-disable-the-new-outlook-for-windows-for-an-individual-mailbox).

Users can enable new Outlook via the toggle from the built-in Mail and Calendar application in Windows. To block new Outlook from these applications, organizations can block users from downloading and/or installing new Outlook using Intune or other management solutions.

Admins can use the `UniversalOutlookEnabled` parameter value `$false` on the **CASMailbox** cmdlet to block organization accounts from using the built-in Mail and Calendar app in Windows. Check the syntax at [Set-CASMailbox -UniversalOutlookEnabled](/powershell/module/exchange/set-casmailbox#-universaloutlookenabled).

> [!IMPORTANT]
> For more detailed information on mapping classic Outlook policies to the new Outlook, please refer to our comprehensive guide [Map classic Outlook policies to new Outlook](/outlook/troubleshoot/installation/map-classic-outlook-policies-to-new-outlook).

## Disable Outlook Data File (.pst) support in the new Outlook for Windows

Admins can disable or limit Outlook Data File (.pst) support in the new Outlook for Windows. It can be done with the [OutlookDataFile mailbox policy](https://learn.microsoft.com/en-us/powershell/module/exchange/set-owamailboxpolicy?view=exchange-ps#-outlookdatafile). The new Outlook for Windows only enforces the [OutlookDataFile mailbox policy](https://learn.microsoft.com/en-us/powershell/module/exchange/set-owamailboxpolicy?view=exchange-ps#-outlookdatafile) of the primary account. For more information on enabling the policy, refer to the [OutlookDataFile parameter in Set-OwaMailboxPolicy](https://learn.microsoft.com/en-us/powershell/module/exchange/set-owamailboxpolicy?view=exchange-ps#-outlookdatafile).

> [!IMPORTANT]
> Outlook Data File (.pst) support is enabled by default.
