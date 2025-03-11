---
title: End of Support for the Microsoft Store installation type of Microsoft 365 Apps
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: reference
ms.service: o365-proplus-itpro
ms.localizationpriority: medium
ms.collection: Tier1
description: Support for the Microsoft Store installation type of Microsoft 365 Apps is ending. Feature updates will stop after October 2025, and security updates will end in December 2026.
ms.date: 03/11/2025
---

# Microsoft Store Installation Type end of support for Microsoft 365 Apps

Support for the Microsoft Store installation type of Microsoft 365 Apps is ending. Feature updates stop after October 2025, and security updates end in December 2026.

If your organization has devices using this installation type, upgrade to the Click-to-Run installation to continue receiving feature and security updates. Upgrading doesn't require purchasing a new license.

## For End Users

Users can follow the detailed instructions in [End of support for the Microsoft Store installation type of Microsoft 365 Apps](https://support.microsoft.com/office/81e9fa8d-e903-4a27-9399-b69155267228).  

## For Managed Deployments

For managed deployment, Microsoft 365 Apps installations through the Office Deployment Tool - including deployments via Intune and Configuration Manager - will automatically detect and remove the Microsoft Store installation type, and install the Click-to-Run type.

For advanced detection, use the following PowerShell command to determine if the Microsoft Store installation type is installed:

```powershell
Get-AppxPackage -Name Microsoft.Office.Desktop
```

If this command returns information, the Microsoft Store installation type is installed, and the device should be upgraded to the Click-to-Run installation type.
