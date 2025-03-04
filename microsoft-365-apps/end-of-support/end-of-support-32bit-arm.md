---
title: End of Support for 32-bit Microsoft 365 Apps on Windows Arm-based PCs
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: reference
ms.service: o365-proplus-itpro
ms.localizationpriority: medium
ms.collection: Tier1
description: Support for the 32-bit edition of Microsoft 365 Apps on Windows Arm-based devices is ending. Feature updates stop in October 2025, and security updates end in December 2026.
ms.date: 03/04/2025
---

# 32-bit Windows Arm-based devices end of support for Microsoft 365 Apps

Support for the 32-bit edition of Microsoft 365 Apps on Windows Arm-based devices is ending. Feature updates stop in October 2025, and security updates end in December 2026.

If your organization has Windows Arm-based devices running the 32-bit edition of Microsoft 365 Apps, upgrade to the 64-bit edition to continue receiving feature and security updates. Upgrading doesn't require purchasing a new license.

> [!NOTE]
> The 64-bit edition of Microsoft 365 Apps for Windows Arm-based PCs requires Windows 11.

## For End Users

Users can follow the detailed instructions in [SMC article link].  

## For Managed Deployments

For managed deployments, installing Microsoft 365 Apps with the Office Deployment Tool, Intune, or Configuration Manager removes the 32-bit edition on Windows Arm-based PCs and installs the 64-bit edition.

For advanced detection, the following registry value can determine whether a Microsoft 365 Apps installation is 32-bit or 64-bit:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Inventory\Office\OfficePackageArchitecture
```

If this key is present with a value of `x86` on a Windows Arm-based PC, the device should be upgraded to the 64-bit edition.
