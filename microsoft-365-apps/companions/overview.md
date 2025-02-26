---
title: "Microsoft 365 companions apps overview (preview)"
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
description: "Learn about the Microsoft 365 companions apps, including availability, opt-out options, and feedback mechanisms."
ms.date: 02/18/2025
---

# Overview of Microsoft 365 companion apps

Microsoft 365 companion apps are designed to enhance productivity by providing users with quick access to key tools directly from the Windows 11 taskbar. These lightweight apps integrate seamlessly with Microsoft 365, allowing users to efficiently look up contacts, locate files, and streamline workflows without interrupting their tasks. Whether searching for colleagues, retrieving recently used documents, or navigating organizational charts, the People app and File Search app help users work smarter and stay connected.

## What are Microsoft 365 companion apps?

Microsoft 365 companions is a suite of apps designed to enhance productivity directly from the Windows 11 taskbar. The first two apps are:

- People app: Allows users to quickly browse organizational charts, view contact information, and easily communicate with colleagues.
- File Search app: Enables users to quickly find Microsoft 365 files, preview file contents, send files to colleagues, and easily access recently used documents.

## Who is eligible to receive Microsoft 365 companion apps?

Microsoft 365 companion apps is available to users who have an existing installation of Microsoft 365 desktop apps, are part of the [Microsoft 365 Insider Program for Business](../insider/overview.md)(Beta Channel) and are running Windows 11.

For a full list of Office 365 and Microsoft 365 plans, see [Product IDs that are supported by the Office Deployment Tool for Click-to-Run](/office365/troubleshoot/installation/product-ids-supported-office-deployment-click-to-run).


> [!NOTE]
> People app requires the user to have an eligible Teams SKU. If the user is not eligible for a Teams SKU, the app will display the following error:  
> `<Insert License Error XX>`

## How will these apps be made available to the user?

MMicrosoft 365 companion apps will be deployed to eligible users starting in March.

### How to opt out

If you don’t want Microsoft 365 companion apps to be installed, follow these steps:

1. Sign in to the [Microsoft 365 Apps admin center](https://config.office.com/) with an admin account.
2. Go to **Customize** > **Device Configuration** > **Modern Apps Settings**.
3. Select **Microsoft 365 companion apps**, then clear the checkbox for **Enable automatic installation of Microsoft 365 companion apps**.

> [!NOTE]
> Clearing the checkbox will not remove Microsoft 365 companion apps from devices where they’ve already been installed.  While there is no dedicated Group Policy or Cloud Policy setting to disable automatic installation, administrators can manage deployment through the Microsoft 365 Apps admin center.

## When will Microsoft 365 companion Apps be available?

| Channel       | Date                     |
|--------------|--------------------------|
| Beta Channel | Refer to Roadmap ID XX   |

## What will users see?

Once Microsoft 365 companions are installed, the People app and File Search app will automatically launch on startup. Users can disable auto-launch on startup via the App settings. For the best experience, users can choose to pin the apps to the taskbar; admins can configure to pin the apps to the taskbar via the Start Layout policy. 

For more information, see [Customized the Start layout](/windows/configuration/start/layout).

:::image type="content" source="media/taskbar-people-file-search.png" alt-text="The Windows 11 taskbar showing the search bar, OneNote, Word, and Microsoft 365 Companion apps, including People and File Search.":::

## Feature and Quality Updates for companion Apps

After installation, Microsoft 365 companion apps receive periodic updates with new features and quality improvements. The update process for People app and File Search app is different from the update process for other Microsoft 365 apps, such as Word and Excel.

## Related Articles:

- [People app](people.md)
- [File Search app](file-search.md)
