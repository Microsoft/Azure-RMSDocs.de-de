---
title: PowerShell für Schutzvorlagen (Azure Information Protection)
description: Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Schutzvorlagen ausführen können, lassen sich auch mithilfe von PowerShell über die Befehlszeile starten. Darüber hinaus können Sie Vorlagen exportieren und importieren, sodass Sie Vorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften in Vorlagen, z. B. von mehrsprachigen Namen und Beschreibungen, ausführen können.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 30dbfbe2cd9ef7d8acd89a9a76cd1108d7c03ab2
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "30205719"
---
# <a name="powershell-reference-for-protection-templates"></a>PowerShell-Referenz für Schutzvorlagen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Die Schutzeinstellungen für Azure Information Protection werden in Projektvorlagen gespeichert. Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Schutzeinstellungen ausführen können, lassen sich auch mithilfe von PowerShell über die Befehlszeile starten. 

Darüber hinaus haben Sie die Möglichkeit, Schutzvorlagen zu exportieren und zu importieren. Mit diesen zwei Aktionen können Sie Schutzvorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften durchführen, z.B. mehrsprachige Namen und Beschreibungen.

Sie können Export- und Importvorgänge auch zum Speichern und Wiederherstellen Ihrer Schutzvorlagen verwenden. Sie sollten Ihre Vorlagen regelmäßig sichern. So können Sie unbeabsichtigte Änderungen an den Schutzeinstellungen ganz einfach rückgängig machen, indem Sie zu einer früheren Version wechseln.

Installationsanweisungen finden Sie unter [Installieren des AADRM-PowerShell-Moduls](install-powershell.md).

Die folgenden Cmdlets unterstützen das Erstellen und Verwalten von Schutzvorlagen:

- [Add-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate)

- [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate)

- [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate)

- [Get-AadrmTemplateProperty](/powershell/module/aadrm/get-aadrmtemplateproperty)

- [Import-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate)

- [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition)

- [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate)

- [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty)



## <a name="see-also"></a>Weitere Informationen
[Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
