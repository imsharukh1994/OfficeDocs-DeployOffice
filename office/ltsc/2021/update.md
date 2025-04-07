---
title: "Update Office LTSC 2021"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: office-perpetual-itpro
ms.localizationpriority: medium
ms.collection: Tier2
recommendations: false
description: "Provides IT admins with information on how to update Office LTSC 2021."
ms.date: 04/07/2025
---

# Update Office Long Term Service Channel (LTSC) 2021
 
After you deploy Office LTSC 2021, including Project and Visio, you need to keep it updated. Microsoft releases security and quality updates, such as updates that improve stability or performance, approximately once a month, usually on the second Tuesday of the month.

> [!NOTE]
> Office LTSC 2021 doesn't receive new features after release. To get new Office features regularly, consider moving to a Microsoft 365 (or Office 365) plan that includes Office.

Office LTSC 2021 uses Click-to-Run, instead of Windows Installer (MSI), to install and update Office.

## How Office LTSC 2021 gets updated

<!--Using include for how-office-updates-->
[!INCLUDE[how-office-updates.md](../../includes/how-office-updates.md)]

## How updates are different in Office LTSC 2021

Click-to-Run handles updates differently than Windows Installer (MSI). Here are some important differences:

- Security and quality updates aren't separate downloads. These updates come included in each new build of Office LTSC 2021 available on the Office CDN.
- Updates are cumulative. The latest version of Office LTSC 2021 on the Office CDN includes all previous security and quality updates.
- When you download and install Office LTSC 2021 from the Office CDN, it's already up to date. You don't need to apply other updates or service packs before using Office LTSC 2021.
- Because updates are cumulative and included in the latest Office LTSC 2021 version on the Office CDN, you don't use Microsoft Updates or Windows Server Updates Services (WSUS) alone to update Office LTSC 2021. You can use Microsoft Configuration Manager to deploy and manage updates, including controlling when and from where updates apply.

<a id="update-location"></a>
## Configure where Office LTSC 2021 gets updates from

<!--Using include for how-office-updates-->
[!INCLUDE[where-office-updates-from.md](../../includes/where-office-updates-from.md)]

For more information, see [Deploy Office LTSC 2021](deploy.md).

## Check for updates for Office LTSC 2021

<!--Using include for check-for-office-updates-->
[!INCLUDE[check-for-office-updates.md](../../includes/check-for-office-updates.md)]

## Size of updates for Office LTSC 2021

<!--Using include for office-update-size-->
[!INCLUDE[office-update-size.md](../../includes/office-update-size.md)]

## Use Group Policy to specify update settings

<!--Using include for ad-ds-group-policy-->
[!INCLUDE[ad-ds-group-policy.md](../../includes/ad-ds-group-policy.md)]

## Update channel for Office LTSC 2021

Office uses update channels to determine which updates an installed version of Office receives. Update channel is a device-wide setting, meaning all Office products, including Project and Visio, installed on a device must use the same update channel.

"PerpetualVL2021" is the only update channel available for Office LTSC Professional Plus 2021 and Office LTSC Standard 2021. The PerpetualVL2021 update channel is also available for volume licensed versions of Project 2021 and Visio LTSC 2021.

Volume licensed versions of Project 2021 and Visio LTSC 2021 can use other update channels, such as Current Channel, Monthly Enterprise Channel, or Semi-Annual Enterprise Channel. Project and Visio can use other update channels to install alongside Microsoft 365 Apps, which supports those channels. Even if Project and Visio use these other update channels, they still only receive security and quality updates each month, not new features.

For more information, see [Overview of update channels for Microsoft 365 Apps](/microsoft-365-apps/updates/overview-update-channels).

## Related articles

- [Overview of Office LTSC 2021](overview.md)
- [Deploy Office LTSC 2021](deploy.md)
