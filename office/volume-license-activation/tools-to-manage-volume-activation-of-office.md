---
title: "Tools to manage volume activation of Office"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: office-perpetual-itpro
ms.localizationpriority: medium
ms.collection: Tier2
description: "Provides Office admins with information about the ospp.vbs and the slmgr.vbs scripts, and the Volume Activation Management Tool (VAMT)."
ms.date: 04/25/2025
---

# Tools to manage volume activation of Office

[!INCLUDE [Office 2016 and 2019 end of support notification](../includes/office-2016-2019-eos.md)]

[!INCLUDE [applies-to](../includes/applies-to.md)]

The Office Software Protection Platform script (ospp.vbs), the Software License Manager script (slmgr.vbs), and the Volume Activation Management Tool (VAMT) help you configure and test volume licensed versions of Office, including Project and Visio. Before reading this article, review the following articles:
- [Overview of volume activation of Office](plan-volume-activation-of-office.md)
- [Activate volume licensed versions of Office by using MAK](activate-office-by-using-mak.md)
- [Activate volume licensed versions of Office by using Active Directory](activate-office-by-using-active-directory.md).

## The ospp.vbs script

The Office Software Protection Platform script (ospp.vbs) lets you configure volume licensed versions of Office products, including Project and Visio. You can find the ospp.vbs script in the `Program Files\Microsoft Office\Office16` folder. If you installed the 32-bit version of Office on a 64-bit operating system, go to the `Program Files (x86)\Microsoft Office\Office16` folder.

> [!NOTE]
> The ospp.vbs script doesn't work for Microsoft 365 Apps or subscription versions of Project and Visio. Instead, you can use a PowerShell script named vnextdiag.ps1. For more information, see [Check the license and activation status for Microsoft 365 Apps](/microsoft-365-apps/licensing-activation/vnextdiag).

Running ospp.vbs requires the cscript.exe script engine. To see the Help file, type the following command and press ENTER:

```console
cscript ospp.vbs /?
```

The general syntax is as follows:

```console
cscript ospp.vbs [Option:Value] [ComputerName] [User] [Password]
```

***Option***  
Specifies the option and value to activate a product, install or uninstall a product key, install and display license information, set the Key Management Service (KMS) host name and port, and remove the KMS host name and port. The options and values appear in the tables in this section.

***ComputerName***  
Name of the remote computer. If you don't provide a computer name, the command uses the local computer.

***User***  
Account that has the required permission on the remote computer.

***Password***  
Password for the account. If you don't provide a user account and password, the command uses your current credentials.

> [!IMPORTANT]
> Before you run ospp.vbs, ensure that:
> - If you run the script on a remote computer, confirm that the Windows Firewall allows Windows Management Instrumentation (WMI) traffic on that computer.
> - Use a user account that belongs to the Administrators group on the computer where you run the script.
> - Run the ospp.vbs script from an elevated command prompt.
  
### Global options for ospp.vbs

| **Global option** | **Description** |
|:------------------|:----------------|
| /act              | Activates installed Office product keys. |
| /inpkey:*value*   | Installs a product key (replaces existing key) with a user-provided product key. A value is required. |
| /unpkey:*value*   | Uninstalls an installed product key using the last five digits of the product key to uninstall (as displayed by the /dstatus option). A value is required. |
| /inslic:*value*   | Installs a license using the path of the user-provided .xrm-ms license. A value is required. |
| /dstatus          | Displays license information for installed product keys. |
| /dstatusall       | Displays license information for all installed licenses. |
| /dhistoryacterr   | Displays the failure history for MAK/retail activation. |
| /dinstid          | Displays the Installation ID for offline activation. |
| /actcid:*value*   | Activates a product using a user-provided Confirmation ID. A value is required. |
| /rearm            | Resets the licensing status for all installed Office product keys. |
| /rearm:*value*    | Resets the licensing status for an Office license using a user-provided SKU ID value. A value is required. <br/><br/>Use this option with the SKU ID specified by the /dstatus option if you run out of rearms and activated Office through KMS or Active Directory-based activation to gain another rearm. |
| /ddescr:*value*   | Displays the description for a user-provided error code. A value is required. |
   
The following table describes the ospp.vbs options for configuring the KMS client.
  
### KMS client options for ospp.vbs

| **KMS client option** | **Description** |
|:----------------------|:----------------|
| /dhistorykms          | Displays KMS client activation history. |
| /dcmid                | Displays the KMS client computer ID (CMID). |
| /sethst:*value*       | Sets a KMS host name using a user-provided host name. A value is required. <br/><br/>This command sets `HKLM\Software\Microsoft\OfficeSoftwareProtectionPlatform\KeyManagementServiceName` (REG_SZ). |
| /setprt:*value*       | Sets a KMS port using a user-provided port number. The default port number is 1688. A value is required. <br/><br/>This command sets `HKLM\Software\Microsoft\OfficeSoftwareProtectionPlatform\KeyManagementServicePort` (REG_SZ). |
| /remhst               | Removes the KMS host name and resets the port to the default (1688). |
| /cachst:*value*       | Allows or denies KMS host caching. A value is required (TRUE or FALSE). |
| /actype:*value*       | *(Windows 8.1 and later versions only)* Sets the volume activation type. A value is required. <br/><br/>Values: 1 (for Active Directory-based), 2 (for KMS), 0 (for both). |
| /skms-domain:*value*  | *(Windows 8.1 and later versions only)* Sets the specific DNS domain in which all KMS Service (SRV) records appear. This setting doesn't affect auto-discovery if a single KMS host name is set using the /sethst option. The value must be the Fully Qualified Domain Name (FQDN). |
| /ckms-domain         | *(Windows 8.1 and later versions only)* Clears the specific DNS domain in which all KMS SRV records appear. If no single KMS host name is set using /sethst, auto-discovery finds the KMS host. |

### Scenarios that use ospp.vbs

These scenarios assume that you run ospp.vbs from an elevated command prompt.
  
> [!NOTE]
> Any changes you make affect only Office client products. Configure the Windows client separately by using the [slmgr.vbs script](#the-slmgrvbs-script).
  
#### To change the product key to a MAK key on a remote computer

1. If the remote computer is named contoso1, run the following command to enter the product key. This command assumes you have administrator credentials on the remote computer. If your credentials differ from your sign in name and password, type your sign in name and password at the command line and press ENTER:

   ```console
   cscript ospp.vbs /inpkey:xxxxx-xxxxx-xxxxx-xxxxx-xxxxx contoso1
   ```

2. To activate the remote computer, type the following command and press ENTER:

   ```console
   cscript ospp.vbs /act contoso1
   ```

#### To diagnose KMS activation errors

1. If the computer has the KMS client key installed, check the licensing status by typing the following command and pressing ENTER:

   ```console
   cscript ospp.vbs /dstatusall
   ```

2. To view the KMS activation history, type the following command and press ENTER:

   ```console
   cscript ospp.vbs /dhistorykms
   ```

3. To trigger activation, type the following command and press ENTER:

   ```console
   cscript ospp.vbs /act
   ```

4. Check the error message for error code 0xC004F042. If you see an error code in the notification dialog boxes, use that code to check the error message. To do so, type the following command and press ENTER:

   ```console
   cscript ospp.vbs /ddescr:0xC004F042
   ```

#### To turn on or off KMS host caching on the KMS client

1. On the KMS client computer, to turn on caching, type the following command and press ENTER:

   ```console
   cscript ospp.vbs /cachst:TRUE
   ```

2. On the KMS client computer, to turn off caching, type the following command and press ENTER:

   ```console
   cscript ospp.vbs /cachst:FALSE
   ```

#### To test a KMS host name and then set auto-discovery

1. If you test a KMS host named kmstest.contoso.com and want to specify it in the KMS client, type the following command and press ENTER:

   ```console
   cscript ospp.vbs /sethst:kmstest.contoso.com
   ```

> [!NOTE]
> If you change the default port on the KMS host computer, run ospp.vbs with the /setprt option. For example: `cscript ospp.vbs /setprt:1750`
  
2. To trigger activation, type the following command and press ENTER:

   ```console
   cscript ospp.vbs /act
   ```

3. To check the KMS activation history and confirm the host contacted successfully, type the following command and press ENTER:

   ```console
   cscript ospp.vbs /dhistorykms
   ```

4. To enable auto-discovery of the production KMS host using Domain Name System (DNS), remove the specified KMS host name by typing the following command and pressing ENTER:

   ```console
   cscript ospp.vbs /remhst
   ```

## The slmgr.vbs script

The Software License Manager (slmgr.vbs) script, located in the `Windows\system32` folder, configures and retrieves volume activation details for the Office KMS host and the Windows host. For more information, see [Configuring KMS Hosts](/previous-versions/tn-archive/ff793407(v=technet.10)) for Windows.
  
You can run the script locally on the target computer or remotely from another computer. You must use an administrator account to run the script. If a standard user runs slmgr.vbs, some license data might be missing or incorrect, and many operations become prohibited.
  
The slmgr.vbs script uses either the Windows-based script host (`wscript.exe`) or the command-based script host (`cscript.exe`). Administrators can specify the script engine. If you don't specify a script engine, slmgr.vbs uses the default, `wscript.exe`. Use the `cscript.exe` script engine.
  
You must restart the Software Licensing Service for any changes to take effect. To restart the Software Licensing Service, use the Microsoft Management Console (MMC) Services snap-in or type the following command:

```console
net stop sppsvc && net start sppsvc
```

Run slmgr.vbs with at least one parameter. Running the script without any parameters displays Help information. The following table lists slmgr.vbs command-line options and describes each one. Most parameters configure the KMS host computer. However, the parameters `/sai` and `/sri` pass to KMS clients after they contact the KMS host computer. The general syntax of slmgr.vbs is as follows (assuming you use the `cscript.exe` script engine):

```console
cscript slmgr.vbs [ComputerName] [User] [Password] [Option]
```

***ComputerName***  
Name of the remote computer. If you don't provide a computer name, the command uses the local computer.

***User***  
Account with required permission on the remote computer.

***Password***  
Password for the account. If you don't provide a user account and password, the command uses your current credentials.

***Option***  
Options appear in the following table.
  
### Slmgr.vbs command options

| **Option** | **Description** |
|:-----------|:----------------|
| /ipk *ProductKey* | Installs the product key for Windows (default) or another application identified by the product key. |
| /ato *ActivationID* | Activates the KMS host for Windows (default) or the application identified by the provided Activation ID. |
| /dti *ActivationID* | Displays the Installation ID used for telephone activation of the KMS host computer for Windows (default) or the application identified by the provided Activation ID. Enter the Installation ID into the telephone to receive the Confirmation ID, which activates the KMS host computer using the `/atp` parameter. |
| /atp *ConfirmationID* *ActivationID* | After you receive the Confirmation ID, activates the KMS host for Windows (default) or the application identified by the provided Activation ID. |
| /dlv *ActivationID* | Displays detailed license information for Windows (default) or the application identified by the provided Activation ID. <br/><br/>For example, run the following command at an elevated command prompt in the `Windows\system32` folder to get the status of the Office KMS host: <br/><br/> `cscript slmgr.vbs /dlv 70512334-47B4-44DB-A233-BE5EA33B914C` |
| /dli *ActivationID* | Displays license information for Windows (default) or the application identified by the provided Activation ID. |
| /upk *ActivationID* | Uninstalls the product key for Windows (default) or the application identified by the provided Activation ID. <br/><br/>**CAUTION:** If you intend to uninstall the product key for Office and omit the Activation ID, the command uninstalls all installed product keys, including the Windows product key. |
| /xpr *ActivationID* | Displays the expiration date for the current license state. |
| /sprt *PortNumber* | Sets the TCP communications port on a KMS host computer. Replace *PortNumber* with the TCP port number to use. The default is 1688. |
| /cdns | Disables automatic DNS publishing by a KMS host computer. |
| /sdns | Enables automatic DNS publishing by the KMS host computer. |
| /cpri | Lowers the priority of KMS host computer processes. |
| /sai *ActivationInterval* | Changes how often a KMS client tries to activate itself when it can't find a KMS host computer. Replace *ActivationInterval* with a value expressed in minutes. The default is 120 minutes. |
| /sri *RenewalInterval* | Changes how often a KMS client tries to renew its activation by contacting a KMS host computer. Replace *RenewalInterval* with a value expressed in minutes. The default is 10080 minutes (seven days). This setting overrides the local KMS client settings. |

> [!NOTE]
> - Activation ID for Office LTSC 2024: F3D89BBF-C0EC-47CE-A8FA-E5A5F97E447F  
> - Activation ID for Office LTSC 2021: 47F3B983-7C53-4D45-ABC6-BCD91E2DD90A  
> - Activation ID for Office 2019: 70512334-47B4-44DB-A233-BE5EA33B914C  
> - Activation ID for Office 2016: 98EBFE73-2084-4C97-932C-C0CD1643BEA7
  
### Slmgr.vbs command options (Active Directory–based activation)

The following table shows the command options for activating an Active Directory Domain Services (AD DS) forest using Active Directory–based activation.

| **Option** | **Description** |
|:-----------|:----------------|
| /ad-activation-online *ProductKey* | Activates an AD DS forest using the user-provided product key. |
| /ad-activation-apply-get-iid *ProductKey* | Displays the installation ID for an AD DS forest. |
| /ad-activation-apply-cid *ProductKey* *ConfirmationID* | Activates an AD DS forest using the user-provided product key and Confirmation ID. |

## Volume Activation Management Tool (VAMT)

Volume Activation Management Tool (VAMT) gives you a graphical interface to manage volume activation. For more information, see [Volume Activation Management Tool (VAMT) technical reference](/windows/deployment/volume-activation/volume-activation-management-tool).

> [!NOTE]
> - Office LTSC 2024, Office LTSC 2021, and Office 2019 require at least VAMT 3.1.

### Manage volume activation for Office LTSC 2024 using VAMT

To manage volume activation for Office LTSC 2024 using VAMT, follow these steps:

1. Identify the installation folder for VAMT—for example, `C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\VAMT3`.
2. Download Office LTSC 2024 support files from the [Office VAMT download link](https://download.microsoft.com/download/f/1/8/f181a628-aa2c-49ec-be5c-236bbcfa1368/OfficeVAMT.zip).
3. Copy the `pkeyconfig-office24-client.xrm-ms`, `pkeyconfig-office24-kmshost.xrm-ms`, and `Office24.cilx` files to the appropriate VAMT directories:
   - Copy the .xrm-ms files into the `VAMT3\pkconfig` folder.
   - Copy the .cilx file to a location where you can easily access it for import.

To import Office LTSC 2024 data into VAMT:

1. Open VAMT.
2. In the Actions pane, choose **Import list** to open the **Import List** dialog box.
3. In the **Import List** dialog box, navigate to the location of the `Office24.cilx` file, select the file, and choose **Open**.
4. In the Volume Activation Management Tool dialog box, select **OK** to begin the import. VAMT shows a progress message while it imports the file. Select **OK** when a confirmation message appears that the import completed successfully.
  
## Related articles

- [Overview of volume activation of Office](plan-volume-activation-of-office.md)
- [Activate volume licensed versions of Office by using MAK](activate-office-by-using-mak.md)
- [Activate volume licensed versions of Office by using Active Directory](activate-office-by-using-active-directory.md)
