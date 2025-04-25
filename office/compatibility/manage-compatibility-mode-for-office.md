---
title: "Manage compatibility mode for Office"
ms.author: nwhite
author: nicholasswhite
manager: dougeby
audience: ITPro
ms.topic: conceptual
ms.service: office-perpetual-itpro
ms.localizationpriority: medium
ms.collection: Tier2
description: "Provides an overview of compatibility mode in Office and how to set the default behavior for Word."
ms.date: 04/25/2025
---

# Manage compatibility mode for Office

[!INCLUDE [Office 2016 and 2019 end of support notification](../includes/office-2016-2019-eos.md)]

***Applies to:*** *Office 2019, Office 2016*

Office automatically uses compatibility mode to open Word, Excel, and PowerPoint documents created in earlier versions of these apps. Compatibility mode makes sure users don't see new or improved features in Office while working with a document. This way, people using earlier versions of Office can fully edit the document. Compatibility mode also keeps the document's layout the same.
  
## How Office uses compatibility mode

Word, Excel, and PowerPoint use compatibility mode to open binary Office documents created in Office 2003 or earlier versions. Word also uses compatibility mode to open OpenXML documents created in Word 2007 and Word 2010.
  
## Set default compatibility mode on file creation for Word

If you use Group Policy, you can use the **Set default compatibility mode on file creation** policy setting to manage the default compatibility mode Word uses to create new documents. You might need this setting if you use add-ins or macros that rely on layout functions from Word 2007 or Word 2010. When you enable this policy setting, you can specify which versions of Word new documents are compatible with. The following configuration options are available for this setting:

- **Word 2003**: Disables features in Word that aren't compatible with Word 2003.
- **Word 2007**: Disables features in Word that aren't compatible with Word 2007.
- **Word 2010**: Disables features in Word that aren't compatible with Word 2010.
- **Full functionality mode**: Keeps all new features enabled. This mode is the default setting for Word.

If you choose the Word 2003 option, Word creates new Open XML files with Word 2007 and later features disabled. This configuration makes sure Word 2003 users can edit the files. However, Office 2003 users still need the Compatibility Pack installed to edit Word Open XML files compatible with Word 2003.

If you select **Full functionality mode**, Word 2007 and Word 2010 users can open and edit Word 2019, Word 2016, and Word 2013 documents. The only difference is that new features in Word 2013 and later aren't available in Word 2007 or Word 2010.

You can download the Group Policy Administrative Templates files (ADMX/ADML) for Office from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49030). The **Set default compatibility mode on file creation** policy setting is under User Configuration\\Policies\\Administrative Templates\\Microsoft Word 2016\\Word Options\\Save.
  
## Related articles

- [Assess Office compatibility](assess-office-compatibility.md)
- [Guide to Office Telemetry Dashboard resources](compatibility-and-telemetry-in-office.md)

