---
title: "PowerShell für Schutzvorlagen (Azure Information Protection)"
description: "Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Schutzvorlagen ausführen können, können Sie auch mithilfe von PowerShell über die Befehlszeile durchführen. Darüber hinaus können Sie Vorlagen exportieren und importieren, sodass Sie Vorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften in Vorlagen, z. B. von mehrsprachigen Namen und Beschreibungen, ausführen können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 051144562b1c26a22953f6e83a41b4902404fd2f
ms.sourcegitcommit: 85250f5ea80c2ee22197058ff2f65a79503b0f0c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2018
---
# <a name="powershell-reference-for-protection-templates"></a>PowerShell-Referenz für Schutzvorlagen

>*Gilt für: Azure Information Protection, Office 365*

Die Schutzeinstellungen für Azure Information Protection werden in Projektvorlagen gespeichert. Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Schutzeinstellungen ausführen können, können Sie auch mithilfe von PowerShell über die Befehlszeile durchführen. 

Darüber hinaus können Sie Schutzvorlagen exportieren und importieren. Mit diesen zwei Aktionen können Sie Schutzvorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften, z.B. mehrsprachige Namen und Beschreibungen, durchführen.

Sie können auch Export- und Importvorgänge zum Speichern und Wiederherstellen Ihrer Schutzvorlagen verwenden. Es wird empfohlen, dass Sie Ihre Vorlagen regelmäßig sichern. Wenn Sie anschließend eine Änderung an den Projekteinstellungen vornehmen möchten, die nicht vorgesehen war, können Sie einfach zurück zu einer vorherigen Version wechseln.

Installationsanweisungen finden Sie unter [Installieren des AADRM-PowerShell-Moduls](install-powershell.md).

Die Cmdlets, die das Erstellen und Verwalten von Schutzvorlagen unterstützen:

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
