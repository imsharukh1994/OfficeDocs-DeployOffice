---
title: "Microsoft Search in Bing and Microsoft 365 Apps for enterprise"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: o365-proplus-itpro
ms.collection: Tier2
ms.localizationpriority: medium
recommendations: false
description: "This guide informs Office admins about an optional Microsoft Search in Bing extension for Google Chrome. The extension relies on a background service installed with Microsoft 365 Apps for enterprise."
ms.date: 04/21/2025
---

# Microsoft Search in Bing and Microsoft 365 Apps for enterprise

> [!IMPORTANT]  
> As of March 31, 2025, Microsoft365.com, Office.com, and SharePoint Online are the new homes for Microsoft Search. Microsoft Search in Bing is no longer available. We encourage Microsoft Search in Bing users to update their bookmarks. For more information, see [Guidance for retiring Microsoft Search in Bing for your organization](/microsoftsearch/retirement-microsoft-search-bing).

Microsoft Search in Bing helps users in your organization quickly find work-related information, including people, files, and internal sites. Searching for this information is as easy as searching the web. For more information, see [Overview of Microsoft Search in Bing](/microsoftsearch/overview-microsoft-search-bing).

To help your users take advantage of Microsoft Search in Bing, you can deploy an optional extension for the Google Chrome web browser. If you deploy this extension, it sets Bing as the default search engine for Google Chrome and provides easier access to Microsoft Search features.

Deploying this optional extension requires a background service included with Microsoft 365 Apps for enterprise Version 2005 or later. Even with the background service installed, you control the deployment of the extension. For example, the extension doesn't install on devices in your organization unless you opt in. You can opt in from the Microsoft Search section of the Microsoft 365 admin center. For more information, see [How does the Microsoft Search in Bing extension for Google Chrome get installed?](#how-does-the-microsoft-search-in-bing-extension-for-google-chrome-get-installed)

This optional extension is available only in specific [locations](#which-locations-receive-the-microsoft-search-in-bing-extension) for domain-joined devices running Windows. If Bing is already the default search engine, the extension doesn't install. Even after the extension installs, an [On/Off](#change-the-default-search-engine-for-google-chrome-from-the-extension) toggle lets your users stop using Bing as the default search engine.

> [!NOTE]
> If you don't want the background service installed on devices in your organization or if you don't want Bing set automatically as the default search engine, use this alternative:
> - Use the Microsoft Search extension [available from the Chrome Web Store](https://chrome.google.com/webstore/detail/microsoft-search/fahnnnailfccbjpdjeafekniiaflekca).
> - This extension lets users perform workplace search in the Chrome web browser.
> - Users can install this extension themselves or you can deploy it for them by using the [ExtensionInstallForcelist](https://chromeenterprise.google/policies/#ExtensionInstallForcelist) policy.
> - This extension doesn't change default browser settings or search engine settings on users' devices.  

## How does the Microsoft Search in Bing extension for Google Chrome get installed?

Several things must happen for the Microsoft Search in Bing extension to install for Google Chrome on the user's device.

- You must opt in to install the Microsoft Search extension by going to the Microsoft Search section of the Microsoft 365 admin center.
- A background service for Microsoft Search in Bing must install on the user's device. This background service is included when you install or update to Version 2005 or later of Microsoft 365 Apps for enterprise.
- The device must meet specific criteria for the extension to install.

For more information, see the following sections.

### Configure the setting in the Microsoft 365 admin center to allow the extension to be installed

To allow the extension to install, sign in to the Microsoft 365 admin center with your admin account. Then, go to **Show all** > **Settings** > **Search & intelligence** > **Configurations**, and then choose **Edit**.

> [!NOTE]
> **Search & intelligence** was previously named **Microsoft Search**.

You see the **Install extension and set Bing as the default search engine** check box. The check box isn't selected by default, as shown in the following screenshot.

:::image type="content" source="../media/microsoft-search-bing/search-intelligence-config.png" alt-text="Screenshot of Microsoft 365 admin center settings for configuring Microsoft Search in Bing, including extension settings and search results configurations.":::

To allow the extension to install, select the check box, and then choose **Save**.

If the extension installs on devices in your organization, and you clear the check box and choose **Save**, the extension removes and Bing is no longer the default search engine on those devices. These changes can take up to 24 hours to take effect on those devices.

#### Assign the extension to groups of users

You can provide the extension to everyone in your organization or to specific groups of users. Providing the extension only to specific groups lets you:

- Pilot Microsoft Search in Bing with a subset of users before deploying more broadly.
- Deploy the extension only to groups that benefit most from Microsoft Search in Bing.

Changes you make to which users get the extension can take up to 24 hours to take effect on their devices.

### Install the background service for Microsoft Search in Bing on the user's device

Another requirement is that a background service for Microsoft Search in Bing installs on the user's device. Microsoft 365 Apps for enterprise includes this background service starting with Version 2005. For more information, [review this table](#which-versions-of-microsoft-365-apps-for-enterprise-include-the-background-service-for-microsoft-search-in-bing).

Once the background service installs, it checks whether the setting in the Microsoft 365 admin center is selected. That check happens once a day.

This background service installs automatically on the user's device only if all these criteria are met:

- You're installing or updating to Version 2005 or later of Microsoft 365 Apps for enterprise.
- The device runs Windows.
- The device joins an Active Directory Domain Services (AD DS) domain in Windows Server.

> [!NOTE]
> The background service doesn't install if the device joins only a Microsoft Entra domain.
>
> Also, the background service isn't included with any of these types of Office:
> - Microsoft 365 Apps for business
> - Office for Mac
> - Volume licensed versions of Office 2019, such as Office Professional Plus 2019
> - Office LTSC Professional Plus 2021 or Office LTSC Standard 2021

You can also [manually download and install the background service](#manually-download-and-install-the-background-service).

If you don't want the background service installed, see [How to prevent the background service for Microsoft Search in Bing from being installed](#how-to-prevent-the-background-service-for-microsoft-search-in-bing-from-being-installed-with-microsoft-365-apps-for-enterprise).

### Criteria that need to be met to install the extension

When you select the check box in the Microsoft 365 admin center, the background service checks if it installs on the user's device and meets these criteria:

- The device is in one of the specified [locations](#which-locations-receive-the-microsoft-search-in-bing-extension).
- Google Chrome is installed on the device.
- Bing isn't already the default search engine for Google Chrome.

If the criteria are met, the extension installs on the user's device and sets Bing as the default search engine in Google Chrome, providing easier access to Microsoft Search features.

> [!NOTE]
> The extension doesn't install on the user's device if Microsoft 365 Apps for enterprise is deployed in an Office 365 (or Microsoft 365) GCC, GCC High, or DoD environment.

> [!TIP]
> If you expect the extension to install, but it doesn't, check to make sure you haven't done anything to prevent the background service from installing with Microsoft 365 Apps for enterprise. Also, using a policy setting to enforce a different default search engine or to control extensions on Google Chrome prevents the extension from installing. For example, if you use the [ExtensionInstallForceList](#extensioninstallforcelist-policy-for-google-chrome) policy.

## Which versions of Microsoft 365 Apps for enterprise include the background service for Microsoft Search in Bing?

Version 2005 is the first version of Microsoft 365 Apps for enterprise that installs this background service on domain-joined devices running Windows. The background service is included with new installations and with updates to existing installations of Microsoft 365 Apps for enterprise.

The following table shows, for each update channel, the initial version of Microsoft 365 Apps for enterprise that includes the background service.

|Update channel      | Version  | Release date  |
|---------|---------|---------|
|Current Channel (Preview) |Version 2005   | May 14, 2020  |
|Current Channel   | Version 2005  | June 2, 2020  |
|Monthly Enterprise Channel | Version 2008  | October 13, 2020   |
|Semi-Annual Enterprise Channel (Preview) | Version 2008  | September 8, 2020  |
|Semi-Annual Enterprise Channel | Version 2008   |January 12, 2021   |

## Which locations receive the Microsoft Search in Bing extension?

At this time, the Microsoft Search in Bing extension for Google Chrome installs only on devices in these locations, based on the device's IP address:

- Australia
- Canada
- France
- Germany
- India
- United Kingdom
- United States

The device's location is checked once every month. If the device is in a listed location and you selected the setting in the Microsoft 365 admin center, the extension for Google Chrome installs and Bing becomes the default search engine.

We notify you through the Message Center in the Microsoft 365 admin center and update the list of locations before adding any new locations.

## How to prevent the background service for Microsoft Search in Bing from being installed with Microsoft 365 Apps for enterprise

If you don't want the background service for Microsoft Search in Bing to install with Microsoft 365 Apps for enterprise, use the Office Deployment Tool or Group Policy. You can also prevent the background service from installing if you use Microsoft Configuration Manager (current branch) or Microsoft Intune.

Make sure you implement your chosen method before you install or update to a version of Microsoft 365 Apps for enterprise that includes the background service. If you implement the method after the background service installs, the background service doesn't remove from the device. To remove the background service, see [How to remove the background service for Microsoft Search in Bing after it's been installed](#how-to-remove-the-background-service-for-microsoft-search-in-bing-after-its-been-installed).

### Office Deployment Tool

If you use the Office Deployment Tool, use the ExcludeApp element in your configuration.xml file, as shown in this example. This method works best for new installations of Microsoft 365 Apps for enterprise.

```xml
<Configuration>
   <Add OfficeClientEdition="64" Channel="Current">
      <Product ID="O365ProPlusRetail">
       <Language ID="en-us" />
       <ExcludeApp ID="Bing" />
      </Product>
   </Add>
</Configuration>
```

> [!NOTE]
> - Be sure to [download](https://www.microsoft.com/download/details.aspx?id=49117) the most current version of the Office Deployment Tool.
> - Use the [Office Customization Tool](../admin-center/overview-office-customization-tool.md) to help you create your configuration.xml file with the appropriate settings.

### Group Policy

If you use Group Policy in your organization, enable the *Don't install a background service for Microsoft Search in Bing* policy setting. This method works best for existing installations of Microsoft 365 Apps for enterprise.

You can find this policy setting under Computer Configuration\Policies\Administrative Templates\Microsoft Office 2016 (Machine)\Updates. This policy setting is available in the [Administrative Template files (ADMX/ADML) download](https://www.microsoft.com/download/details.aspx?id=49030) starting with version 5011.1000, released on May 5, 2020.

> [!NOTE]
> In previous releases of the Administrative Template files, this policy setting was named *Don't install extension for Microsoft Search in Bing that makes Bing the default the search engine*.
>
> If you configured the previously named policy setting, your chosen setting still applies.

### Configuration Manager (current branch)

If you deploy Microsoft 365 Apps for enterprise by using the Office 365 Client Installation wizard in Configuration Manager, set the **Background service for Microsoft Search in Bing** toggle to **Off** in the **Features** section.

:::image type="content" source="../media/microsoft-search-bing/apps-features-settings.png" alt-text="Screenshot of Configuration settings for apps and features in Microsoft 365, showing various apps and the background service for Microsoft Search in Bing.":::

### Microsoft Intune

If you deploy Microsoft 365 Apps for enterprise by using Intune, on the **Configure app suite** page, set the **Install background service for Microsoft Search in Bing** toggle to **No** in the **Properties** section.

:::image type="content" source="../media/microsoft-search-bing/intune-toggle-bing.png" alt-text="Screenshot of Intune properties settings showing options for shared computer activation, Microsoft Software License terms, and background service for Microsoft Search in Bing.":::

## Change the default search engine for Google Chrome from the extension

If your users want to revert to their previous default search engine, they can select the magnifying glass icon next to the address bar in Google Chrome and move the **Use Bing as your default search engine** toggle to the **Off** position. For the change to take effect, they need to close Google Chrome and then open it again. Selecting **Off** doesn't remove the extension. This lets your users still search work content through the extension flyout.

:::image type="content" source="../media/microsoft-search-bing/flyout-toggle-chrome.png" alt-text="Screenshot of Microsoft Search flyout in Chrome showing suggested searches and an option to use Bing as the default search engine.":::

If your users want to go back to using Bing as their default search engine and access Microsoft Search features, they can move the toggle in Google Chrome to the **On** position. For the change to take effect, they need to close Google Chrome and then open it again.

## How to remove the background service for Microsoft Search in Bing after it's been installed

You don't need to remove the background service to revert to the original search engine settings. Your users can use the [On/Off](#change-the-default-search-engine-for-google-chrome-from-the-extension) toggle or you can [clear the setting in the Microsoft 365 admin center](#configure-the-setting-in-the-microsoft-365-admin-center-to-allow-the-extension-to-be-installed) that affects all users in your organization.

But if you want, you can remove the background service from the device. If the extension installs on the device, uninstalling the background service also removes the extension. Bing is no longer set as the default search engine. Also, the background service doesn't install again in a future update of Microsoft 365 Apps for enterprise.

To remove the background service from an individual device, go to **Control Panel** > **Programs** > **Programs and Features**. Then, under the list of installed programs, right-select **Microsoft Search in Bing** and choose **Uninstall**.

If you want to remove the background service from multiple devices in your organization, run this command as an administrator in a script:

```console
"%ProgramData%\Microsoft\DefaultPackMSI\MainBootStrap.exe" uninstallAll
```

## More information about Microsoft Search in Bing and Microsoft 365 Apps for enterprise

### Manually download and install the background service

You can manually [download](https://aka.ms/AA6im0l) the background service for Microsoft Search in Bing and then deploy it to devices in your organization. For example, use this on devices running a version of Microsoft 365 Apps for enterprise earlier than Version 2005 or on devices with Microsoft 365 Apps for business. Even if you manually deploy the background service, it uses the same [criteria](#criteria-that-need-to-be-met-to-install-the-extension) to determine whether to install the extension on the device.

### ExtensionInstallForceList policy for Google Chrome

If you use the [Configure the list of force-installed apps and extensions (ExtensionInstallForcelist)](https://chromeenterprise.google/policies/?policy=ExtensionInstallForcelist) policy to restrict Chrome extensions in your organization, include this value when configuring the policy:

`obdappnhkfoejojnmcohppfnoeagadna;https://clients2.google.com/service/update2/crx`

If you don't include this value, the extension for Microsoft Search in Bing removes from devices.
