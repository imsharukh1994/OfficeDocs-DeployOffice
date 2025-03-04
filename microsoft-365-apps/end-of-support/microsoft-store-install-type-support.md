---
title: End of Support for the Microsoft Store Installation Type of Microsoft 365 Apps
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: reference
ms.service: o365-proplus-itpro
ms.localizationpriority: medium
ms.collection: Tier1
description: Support for the Microsoft Store installation type of Microsoft 365 Apps is ending. Feature updates will stop after October 2025, and security updates will end in December 2026.
ms.date: 03/04/2025
---

# Microsoft Store Installation Type end of support for Microsoft 365 Apps

Support for the Microsoft Store installation type of Microsoft 365 Apps is ending. Feature updates will stop after October 2025, and security updates will end in December 2026.

If your organization has devices using this installation type, upgrade to the Click-to-Run installation to continue receiving feature and security updates. Upgrading doesn't require purchasing a new license.

## For End Users

Users can follow the detailed instructions in [SMC article link].  

## For Managed Deployments

For managed deployments, installing Microsoft 365 Apps with the Office Deployment Tool, Intune, or Configuration Manager removes the Microsoft Store installation type and replaces it with the Click-to-Run version.

For advanced detection, use the following PowerShell command to determine if the Microsoft Store installation type is installed:

```powershell
Get-AppxPackage -Name Microsoft.Office.Desktop
```

If this command returns information, the Microsoft Store installation type is installed, and the device should be upgraded to the Click-to-Run installation type.
