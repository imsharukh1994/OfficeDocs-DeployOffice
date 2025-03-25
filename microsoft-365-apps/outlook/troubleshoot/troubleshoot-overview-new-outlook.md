---
title: "New Outlook for Windows troubleshooting overview"
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
description: "Overview of troubleshooting issues with new Outlook for Windows"
ms.date: 11/22/2024
---

# Troubleshoot new Outlook

Some of the common steps users took to troubleshoot issues in classic Outlook are no longer needed in new Outlook. For example, creating a new profile or starting Outlook in safe mode is no longer necessary because of the underlying architecture changes in new Outlook.

## Changes to profile experience

Creating a new profile in classic Outlook was a common troubleshooting step to help resolve various issues such as startup problems, synchronization errors, or slow performance. The underlying architecture change in New Outlook means users only need one Outlook profile, and eliminates the need for the profile picker. By removing the ability to create multiple profiles, new Outlook provides a more seamless and less frustrating experience when dealing with email-related issues in Outlook.

The change to the profile experience is part of a broader effort by Microsoft to streamline the user experience and improve the stability and reliability of Outlook. The architecture in new Outlook integrates more robust error-handling mechanisms, offers improved support for modern email protocols, reduces the complexity of maintaining and configuring the application, and eliminates the need to create new profiles.

## Safe mode
 
Safe mode in classic Outlook was a frequently used troubleshooting mode due to the COM extensibility model which created instability. In new Outlook, the extensibility architecture with web add-ins is designed to protect Outlook from crashing if an add-in misbehaves. The new Outlook architecture, with automatic updates and a built-in safety net, has significantly reduced the need for the new Outlook to use a manual switch like Safe Mode as a default troubleshooting step. However, there may still be scenarios where it could be required.

Safe Mode in the new Outlook for Windows is a troubleshooting feature that allows users to launch the application with minimal functionality. It provides a temporary, isolated session where users can access essential features like email and calendar while addressing issues or seeking support. Safe Mode preserves user settings and restores them upon returning to normal mode. These sessions are intended as a transitional state to help users return to the complete experience.

Safe mode excludes some functionality including PST, S/MIME, offline usage, non-default client configurations, and Web add-ins.

Syntax: 
```
olk.exe --safe
```

If you need to run Outlook with the -safe syntax, we recommend working with Microsoft support to identify opportunities for product improvements. 
 
## Recovery mode

Outlook may enter recovery mode if it fails to start five consecutive times. Similar to safe mode, in recovery mode Outlook will operate with minimal functionality, such as excluding support for PST, S/MIME, offline usage, non-default client configurations, and Web add-ins. 

While in this mode, the client will check for updates, download them if available, and apply them accordingly. These measures are intended to restore the client to a healthy state and allow the user to resume their tasks. If the application successfully launches into recovery mode, manually restarting the client will revert it to the regular startup sequence with all functionalities fully restored.

In the unlikely event that the client continues to start in recovery mode, we recommend contacting Microsoft Support.
