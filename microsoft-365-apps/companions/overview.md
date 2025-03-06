---
title: "Microsoft 365 companions apps overview"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: overview
ms.service: o365-proplus-itpro
ms.collection:
- tier1
- essentials-overview
ms.localizationpriority: medium
ms.custom: intro-overview
recommendations: true
description: "Learn about Microsoft 365 companions, including availability, opt-out options, and feedback mechanisms."
ms.date: 03/06/2025
---

# Overview of Microsoft 365 companion apps (preview)

Microsoft 365 companions is a suite of apps designed to enhance productivity by providing users with quick access to key tools directly from the Windows 11 taskbar. The first two apps are:

- [People companion](people.md): Allows users to quickly look up anybody in their enterprise and browse organizational charts, view contact information, and easily communicate with colleagues.
- [File Search companion](file-search.md): Enables users to quickly find Microsoft 365 files, preview file contents, send files to colleagues, and easily access recently used documents.

These lightweight apps integrate seamlessly with Microsoft 365, allowing users to efficiently look up contacts, locate files, and streamline workflows without interrupting their tasks. The People companion and File Search companion help users find colleagues, access recent documents, and navigate organizational charts to work smarter and stay connected.

## Who is eligible to receive Microsoft 365 companion apps?

Microsoft 365 companion apps are available to users who:

- Are part of the [Microsoft 365 Insider Program for Business](../insider/overview.md) (Beta Channel)
- Have Microsoft 365 desktop apps installed
- Are running Windows 11

For a full list of Office 365 and Microsoft 365 plans, see [Product IDs supported by the Office Deployment Tool for Click-to-Run](/office365/troubleshoot/installation/product-ids-supported-office-deployment-click-to-run).

> [!NOTE]
> The People companion requires a Microsoft 365 plan that includes Teams. If Teams isn't included, the app remains available, but calling and instant messaging are disabled.

## How are Microsoft 365 companion apps deployed?

Microsoft 365 companion apps automatically deploy to eligible users according to the [deployment schedule](#what-is-the-deployment-schedule). This deployment is part of the Microsoft 365 update process.

### How to opt out

If you don’t want Microsoft 365 companion apps to be installed automatically, follow these steps:

1. Sign in to the [Microsoft 365 apps admin center](https://config.office.com/) with an admin account.
2. Go to **Customize** > **Device Configuration** > **Modern Apps Settings**.
3. Select **Microsoft 365 companions apps (preview)**, then clear the checkbox for **Enable automatic installation of Microsoft 365 companion apps**.

> [!NOTE]
> Clearing the checkbox doesn't remove Microsoft 365 companion apps from devices where they're already installed. While there's no dedicated Group Policy or Cloud Policy setting to disable automatic installation, administrators can manage deployment through the Microsoft 365 apps admin center.

## What is the deployment schedule?

| Channel      | Date                   |
| ------------ | ---------------------- |
| Beta Channel | Refer to Roadmap ID XX |

## What do users see?

Once Microsoft 365 companions are installed, the People companion and File Search companion automatically launch on startup. Users can disable autolaunch through the app settings. For the best experience, users can choose to pin the apps to the taskbar; admins can configure to pin the apps to the taskbar via the Start Layout policy.

For more information, see [Customize the Start layout](/windows/configuration/start/layout).

:::image type="content" source="media/taskbar-people-file-search.png" alt-text="The Windows 11 taskbar showing the search bar, OneNote, Word, and Microsoft 365 companion apps, including People companion and File Search companion.":::

## Feature and quality updates

After installation, Microsoft 365 companion apps receive periodic updates with new features and quality improvements. The update process for People companion and File Search companion is different from the update process for other Microsoft 365 apps, such as Word and Excel.

Join the [Microsoft Community Hub](https://techcommunity.microsoft.com/) to connect with other users, ask questions, share insights, and stay informed about the latest updates.

## Related articles

- [People companion](people.md)
- [File Search companion](file-search.md)