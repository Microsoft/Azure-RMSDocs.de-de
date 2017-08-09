---
title: "PowerShell für benutzerdefinierte Azure RMS-Vorlagen – AIP"
description: "Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Rechteverwaltungsvorlagen ausführen können, können Sie auch mithilfe von PowerShell über die Befehlszeile durchführen. Darüber hinaus können Sie Vorlagen exportieren und importieren, sodass Sie Vorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften in Vorlagen, z. B. von mehrsprachigen Namen und Beschreibungen, ausführen können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: c3b1662275b051ea75dcc104c4f09b5db53dbe3e
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2017
---
# <a name="powershell-reference-for-custom-templates"></a>PowerShell-Referenz für benutzerdefinierte Vorlagen

>*Gilt für: Azure Information Protection, Office 365*

Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Vorlagen ausführen können, können Sie auch mithilfe von PowerShell über die Befehlszeile durchführen. Darüber hinaus können Sie Vorlagen exportieren und importieren, sodass Sie Vorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften in Vorlagen, z. B. von mehrsprachigen Namen und Beschreibungen, ausführen können.

Sie können das Exportieren und Importieren auch zum Sichern und Wiederherstellen der benutzerdefinierten Vorlagen verwenden. Als bewährte Methode wird empfohlen, regelmäßig eine Sicherungskopie der benutzerdefinierten Vorlagen zu erstellen. So können Sie jederzeit leicht zur vorherigen Version zurückwechseln, falls Sie einmal eine unbeabsichtigte Änderung vornehmen sollten.

> [!IMPORTANT]
> Um PowerShell zum Erstellen und Verwalten von Azure Rights Management-Vorlagen zu verwenden, benötigen Sie mindestens Version 2.0.0.0 des [Windows PowerShell-Moduls für Azure RMS](https://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Wenn Sie dieses PowerShell-Modul bereits zuvor installiert hatten, führen Sie den folgenden Befehl in einem PowerShell-Fenster aus, um die Versionsnummer zu überprüfen: `(Get-Module aadrm -ListAvailable).Version`

Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).

Die Cmdlets, die das Erstellen und Verwalten von Vorlagen unterstützen:

- [Add-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate)

- [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate)

- [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate)

- [Get-AadrmTemplateProperty](/powershell/module/aadrm/get-aadrmtemplateproperty)

- [Import-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate)

- [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition)

- [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate)

- [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty)



## <a name="see-also"></a>Siehe auch
[Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]