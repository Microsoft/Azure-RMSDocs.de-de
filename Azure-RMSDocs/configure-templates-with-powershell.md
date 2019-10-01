---
title: PowerShell für Schutzvorlagen (Azure Information Protection)
description: Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Schutzvorlagen ausführen können, lassen sich auch mithilfe von PowerShell über die Befehlszeile starten. Außerdem können Sie Vorlagen zwischen Mandanten kopieren oder eine Massenbearbeitung komplexer Eigenschaften in Vorlagen, z. b. mehrsprachige Namen und Beschreibungen, ausführen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 09/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.subservice: azurerms
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 0cd34533f1042668b79f540dd6066f600be445f2
ms.sourcegitcommit: 319c0691509748e04aecf839adaeb3b5cac2d2cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2019
ms.locfileid: "71683584"
---
# <a name="powershell-reference-for-protection-templates"></a>PowerShell-Referenz für Schutzvorlagen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Die Schutzeinstellungen für Azure Information Protection werden in Projektvorlagen gespeichert. Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Schutzeinstellungen ausführen können, lassen sich auch mithilfe von PowerShell über die Befehlszeile starten. 

Darüber hinaus haben Sie die Möglichkeit, Schutzvorlagen zu exportieren und zu importieren. Mit diesen zwei Aktionen können Sie Schutzvorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften durchführen, z.B. mehrsprachige Namen und Beschreibungen.

Sie können Export- und Importvorgänge auch zum Speichern und Wiederherstellen Ihrer Schutzvorlagen verwenden. Sie sollten Ihre Vorlagen regelmäßig sichern. So können Sie unbeabsichtigte Änderungen an den Schutzeinstellungen ganz einfach rückgängig machen, indem Sie zu einer früheren Version wechseln.

Installationsanweisungen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](install-powershell.md).

Die folgenden Cmdlets unterstützen das Erstellen und Verwalten von Schutzvorlagen:

- [Add-aipservicetemplate](/powershell/module/aipservice/add-aipservicetemplate)

- [Export-aipservicetemplate](/powershell/module/aipservice/export-aipservicetemplate)

- [Get-AipServiceTemplate](/powershell/module/aipservice/get-aipservicetemplate)

- [Get-AipServiceTemplateProperty](/powershell/module/aipservice/get-aipservicetemplateproperty)

- [Import-AipServiceTemplate](/powershell/module/aipservice/import-aipservicetpd)

- [New-AipServiceRightsDefinition](/powershell/module/aipservice/new-aipservicerightsdefinition)

- [Remove-aipservicetemplate](/powershell/module/aipservice/remove-aipservicetemplate)

- [Set-AipServiceTemplateProperty](/powershell/module/aipservice/set-aipservicetemplateproperty)



## <a name="see-also"></a>Siehe auch
[Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md)

