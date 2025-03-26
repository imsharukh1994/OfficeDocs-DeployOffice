---
title: Dealing with Outlook search in non-persistent RDS environments
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.collection: Tier2
ms.localizationpriority: medium
recommendations: false
description: Learn about your options for managing Outlook data stored to a user profile disk.
ms.date: 03/26/2025
---

# Dealing with Outlook search in non-persistent Remote Desktop Services (RDS) environments

*Applies To: Windows Server (Semi-Annual Channel), Windows Server 2016*

A common issue customers face with their non-persistent (pooled) Remote Desktop Services environments is handling users' Outlook data. When Outlook is running in cached exchange mode, the .OST storing a user's Outlook data must follow the user as they roam from host to host. Windows Search Service indexes the .OST and creates an index catalog to enable search functionality in Outlook. In non-persistent RDS environments, the index catalog doesn't roam with user data. Users must rebuild the catalog each time they sign in to a new PC, which could occur with every sign-in. Until the Windows Search Service finishes indexing the .OST, users get limited or incomplete search functionality. 

FSLogix offers a solution that solves this issue: The FSLogix Office 365 Container roams a user's Outlook data and search index catalog. Users can access their email and search in Outlook, even when they roam between sessions on different hosts in a collection.  

FSLogix Office 365 Container provides significant benefits for Outlook search functionality compared to the native User Profile Disk (UPD) roaming solution in RDS. With UPD, search typically doesn't return results or returns incomplete results while Windows Search Service indexes the .OST. This indexing must occur each time a user connects to a new host in the collection.

The key advantage of FSLogix's solution is that it roams the search index catalog along with the user data. This means users see search results immediately when they sign in, without waiting for Windows Search Service to rebuild the index. The result is a consistent and responsive search experience in Outlook regardless of which host in the collection a user connects to.

For more information about FSLogix, see [What is FSLogix?](/fslogix/overview-what-is-fslogix).