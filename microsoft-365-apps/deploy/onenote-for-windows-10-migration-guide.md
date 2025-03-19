---
title: "OneNote for Windows 10 migration guidance"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.collection: Tier1
ms.localizationpriority: medium
recommendations: false
hideEdit: false
description: "Provides migration guidance for OneNote for Windows 10"
ms.date: 03/11/2025
---

# OneNote for Windows 10 migration guidance

<!--Using include for adding OneNote for Windows 10 eos-->
[!INCLUDE [OneNote Windows 10 eos](../includes/onenote-win10-eos.md)]

This article provides guidance for migrating your organization from OneNote for Windows 10 to OneNote for Windows. It includes instructions for identifying users, customizing migration scripts, and ensuring data integrity throughout the process. You find troubleshooting steps and best practices to help minimize disruption and safeguard user data during the migration.

## Identifying users on OneNote for Windows 10:

To identify users or devices in your organization using OneNote for Windows 10 via Microsoft Intune, follow these steps to run a report:

- In Intune, navigate to: **All Services** > **Apps | Monitor** > **Monitor** > **Discovered apps**, then search for "Office.OneNote."
- Look for the application version starting with `16001.xxxxx.xxxxx.x`, to identify OneNote for Windows 10 users. The latest version is `16001.14326.22094.0`
  > [!NOTE]
  > The sample migration script works only with OneNote for Windows 10 devices on version `16001.14326.22094.0`

## Sample script customization

Before running the sample script, install OneNote on Windows on user devices if the app has not been installed. For more information, see [Deployment guide for OneNote](deployment-guide-onenote.md)

To ensure a smooth migration to OneNote for Windows, organizations must customize the following sample script to complete these steps in order:

1. Check if OneNote for Windows 10 is installed and if the path to the AppData folder for the app exists (which indicates if the user has opened the app before) to verify if migration is necessary.
2. Check if OneNote for Windows is installed by verifying if the executable file exists on the device.
3. Check the version of OneNote for Windows 10 to ensure it’s on the latest version with important features to prevent data loss during migration.

> [!NOTE]
> This script does not function for devices with OneNote for Windows 10 versions below 16001.14326.22094. IT admins must upgrade these devices according to their organization's policy.  
>  
> To upgrade users to the latest version via Appx download, run the following command:  
> `WinGet download 9wzdncrfhvjl --skip-license`

4. Terminate all OneNote for Windows 10 processes.
5. Back up any unsynced sections to the sandbox folder using the `onenote-uwp://backup:` command.
6. Store the backups within the sandbox in:  
   `$localAppDataPath\Packages\Microsoft.Office.OneNote_8wekyb3d8bbwe\AppData\Local\OneNote\16.0\BackUp\`.
7. Ensure only sections with unsynced content are backed up and organized in folders where each folder corresponds to a notebook.
8. Parse through the `UWPBackUpStatus.json` to validate that the backup was successful.

> [!WARNING]
> Uninstalling with a failed backup can lead to data loss.

9. Move the backup files to a location outside of the sandbox:  
   `$localAppDataPath\Packages\Microsoft.Office.OneNote_8wekyb3d8bbwe\`  
   since the sandbox path will be deleted once the OneNote for Windows 10 app is uninstalled.
10. Uninstall OneNote for Windows 10.
11. Ensure OneNote for Windows 10 is uninstalled on a per-user basis and not on a per-device basis.  
    This process helps mitigate scenarios where shared devices have unsynced notes removed for all accounts.


> [!IMPORTANT]
> Before using the sample script, you must customize it to fit your organization's specific deployment and migration requirements.

:::code language="powershell" source="../snippets/deployment-guide-onenote/uninstall-onenote-win10.ps1":::

## Accessing migrated notes

After migration, users can retrieve their notes by:
1. Opening the new **OneNote on Windows** application.
2. Signing into their account.
3. Opening their notebooks.

If any notes are missing, check the backup folder that was created in the previous steps.

To review backups through OneNote on Windows:
- Navigate to **File -> Open Backups -> Navigate to the backup file path.**

## Troubleshooting

- Review the `UWPBackupStatus.json` and `UWPSyncStatus.json` files in the user’s backup folder for detailed information on the backup and sync statuses.

- For errors encountered during migration, refer to the log file located in the backup generated previously (step 1.d).

If the `onenote-uwp://backup:` command fails:
- Ensure that the OneNote for Windows 10 app is the default app linked to the `onenote-uwp` protocol.
- Consult the relevant support article to ensure correct protocol attachment to OneNote for Windows 10.

> [!CAUTION]
> Be cautious when using commands found online. Always test commands in a controlled environment before deploying them organization-wide to avoid unintended consequences, such as those resulting from the Remove-AppxPackage command. 

For more assistance or inquiries, contact Microsoft Support.

## Related articles

- [Frequently Asked Questions about OneNote in Office 2019 and Microsoft 365](https://support.microsoft.com/office/6582c7ae-2ec6-408d-8b7a-3ed71a3c2103)
- [OneNote help & learning](https://support.microsoft.com/OneNote)
- [OneNote info for developers](https://developer.microsoft.com/onenote)
- [Deployment guide for OneNote](deployment-guide-onenote.md)
