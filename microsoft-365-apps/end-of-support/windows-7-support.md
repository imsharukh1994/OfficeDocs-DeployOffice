---
title: "Windows 7 end of support and Microsoft 365 Apps"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.collection: Tier1
ms.localizationpriority: medium
recommendations: true
description: "Provides Office admins with information about the implications of Windows 7 end of support on Microsoft 365 Apps."
ms.date: 04/01/2025
---

# Windows 7 end of support and Microsoft 365 Apps

> [!IMPORTANT]
> - Support for Windows 7 ended on January 14, 2020. [Learn more](https://support.microsoft.com/windows/b75d4580-2cc7-895a-2c9c-1466d9a53962)
> - Microsoft 365 Apps is no longer supported on Windows 7.
> - Home user running Microsoft 365 or Office on Windows 7, [read this article](https://support.microsoft.com/office/34e28be4-1e4f-4928-b210-3f45d8215595) instead of reading the following article.

Microsoft 365 is governed by the [Modern Lifecycle Policy](/lifecycle/policies/modern), which requires customers to stay current as per the servicing and [system requirements](https://support.microsoft.com/topic/13eda659-3dfc-448e-b2cd-70ebb989be47) for the product or service. These requirements include using Microsoft 365 Apps on a Windows operating system that is currently in support.

Using Microsoft 365 Apps on older, unsupported operating systems could cause performance and reliability issues over time. Therefore, if your organization is using Microsoft 365 Apps on devices running Windows 7, we strongly recommend your organization moves those devices to Windows 11 or Windows 10.

## Security updates for Microsoft 365 Apps on Windows 7

> [!IMPORTANT]
> Security updates Microsoft 365 Apps on Windows 7 ended on January 10, 2023.

Even though Windows 7 is no longer supported, we decided to provide you with security updates for Microsoft 365 Apps for three years, until January 2023. This change gives you more time to transition devices running Microsoft 365 Apps from Windows 7 to a supported operating system, such as Windows 11 or Windows 10. However, devices still running Windows 7 won't receive new feature updates for Microsoft 365 Apps.

> [!IMPORTANT]
> - Even with these security updates, Microsoft 365 Apps is no longer supported on Windows 7.
> - This information applies even if you purchased [Extended Security Updates (ESU) for Windows 7](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq). ESU for Windows 7 ended on January 10, 2023.

## How to manage Microsoft 365 Apps on Windows 7

Version 2002 is the last version of Microsoft 365 Apps that's available for devices running Windows 7.

To use Microsoft 365 Apps on devices running Windows 7, install Version 2002. If you try to install a newer version, such as Version 2201, on a Windows 7 device, an error message appears.

> [!IMPORTANT]
> - As of January 2022, attempting to do a new installation of Version 2002 fails.
> - Performing an Online Repair of an existing installation of Version 2002 fails.
> - Updating an existing installation of Version 2002 will work until January 10, 2023, after which no more updates will be available.

To update an existing installation of Version 2002, you can keep using the same management tools that you're currently using, such as the Office Deployment Tool or Configuration Manager. Also, Microsoft 365 Apps can remain on the same update channel as before.

If you configure Microsoft 365 Apps to get updates directly from the Office Content Delivery Network (CDN) on the internet, devices running Windows 7 automatically receive updates to the most current release of Version 2002 for that update channel.

## Guidance when using Configuration Manager for updates

> [!IMPORTANT]
> Security updates for Microsoft 365 Apps on Windows 7 ended on January 10, 2023.

If you use Configuration Manager and the Software Update management workflow to update Microsoft 365 Apps installations, create a separate collection for your Windows 7 devices. Then, use a query rule to add members to the collection.

On the second Tuesday of each month, a new update package for Version 2002 that is only for devices running Windows 7 is available in the Microsoft Update Catalog. There's an update package for each architecture (x86 or x64). That update package can be used with whichever update channel of Microsoft 365 Apps you deployed. There are no separate update packages of Version 2002 for each update channel. For example, the same update package can be used to update a Current Channel or a Semi-Annual Enterprise Channel installation of Microsoft 365 Apps on devices running Windows 7.

In the Office 365 Updates node, you see entries like the following examples. The placeholder ##### represents the most current build number:

- Microsoft 365 Apps Update for Windows 7 – Version 2002 for x64 based Edition (Build 12527.#####)
- Microsoft 365 Apps Update for Windows 7 – Version 2002 for x86 based Edition (Build 12527.#####)

These update packages are configured to apply ***only*** to devices running Windows 7. These update packages can't be used to update Microsoft 365 Apps on devices running other supported operating systems, such as Windows 11 or Windows 10.

If you use an automatic deployment rule (ADR), you should create a new rule for these update packages. Then, use the new rule for your collection that contains your Windows 7 devices. We recommend using the "Title" property and searching for "Microsoft 365 Apps Update for Windows 7" and the architecture you support. If you support both x86 and x64, you can include both updates in one Software Update Package as clients apply the appropriate update. You should also check other existing ADRs to make sure they don't incorrectly try to apply these update packages, which are only for devices running Windows 7, to devices running other operating systems.

## After moving Microsoft 365 Apps to a supported Windows operating system

After you move Microsoft 365 Apps to a supported Windows operating system, you can configure Microsoft 365 Apps to receive new versions and feature updates again. Updates for Microsoft 365 Apps are cumulative, so you get all the feature updates missed while your device ran Windows 7.

If you get updates directly from the Office CDN on the internet, after you move the device to a supported operating system, Microsoft 365 Apps automatically updates to the latest version available for that update channel and starts receiving new features again.

## What about other versions of Office on Windows 7?

Nonsubscription versions of Office used by organizations continue to be supported based on the [Fixed Lifecycle Policy](/lifecycle/policies/fixed). To see specific end of support dates for nonsubscription versions of Office, go to [Search Product and Services Lifecycle Information](/lifecycle/products/).

Even if your version of Office is still supported, Windows 7 no longer receives security updates, leaving it vulnerable to security threats. We recommend that you move to a [supported operating system](https://support.microsoft.com/topic/13eda659-3dfc-448e-b2cd-70ebb989be47), such as Windows 11 or Windows 10.

## Additional information

- This information also applies to the following products:
  - The subscription versions of the Project and Visio desktop apps. For example, if you have Planner and Project Plan 5 or Visio Plan 2.
  - Microsoft 365 Apps for business, which is the version of Office that comes with some Microsoft 365 business plans, such as Microsoft 365 Business Premium.
- For end of support dates for different versions of Office on various versions of Windows, see the [Windows and Office configuration support matrix (PDF)](https://aka.ms/windows-office-support-matrix).
- Other Microsoft resources are available to help you make the transition to using Microsoft 365 Apps on devices running Windows 11 or Windows 10, including [Microsoft FastTrack](https://www.microsoft.com/fasttrack) and [App Assure](https://www.microsoft.com/fasttrack/microsoft-365/app-assure).
- To discuss or learn more about end of support for Office versions, visit [Microsoft Office End of Support](https://techcommunity.microsoft.com/t5/microsoft-office-end-of-support/ct-p/OfficeEOS) on the Microsoft Tech Community.