---
title: PowerShell für Schutzvorlagen (Azure Information Protection)
description: Verwenden Sie PowerShell-Cmdlets, um Schutz Vorlagen für Azure Information Protection hinzuzufügen, zu exportieren, zu importieren, zu entfernen und zu konfigurieren.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ROBOTS: NOINDEX
ms.reviewer: esaggese
ms.subservice: azurerms
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: c8e4c54dee7494aaecadb6de943544e7a1f6c109
ms.sourcegitcommit: b32c16e41ba36167b5a3058b56a73183bdd4306d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/29/2020
ms.locfileid: "97806361"
---
# <a name="powershell-reference-for-protection-templates"></a>PowerShell-Referenz für Schutzvorlagen

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified Label-Client finden Sie in der Microsoft 365-Dokumentation unter Informationen [zu Sensitivitäts Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) . *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
>

Die Schutzeinstellungen für Azure Information Protection werden in Projektvorlagen gespeichert. Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Schutzeinstellungen ausführen können, lassen sich auch mithilfe von PowerShell über die Befehlszeile starten. 

Darüber hinaus haben Sie die Möglichkeit, Schutzvorlagen zu exportieren und zu importieren. Mit diesen zwei Aktionen können Sie Schutzvorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften durchführen, z.B. mehrsprachige Namen und Beschreibungen.

Sie können Export- und Importvorgänge auch zum Speichern und Wiederherstellen Ihrer Schutzvorlagen verwenden. Sie sollten Ihre Vorlagen regelmäßig sichern. So können Sie unbeabsichtigte Änderungen an den Schutzeinstellungen ganz einfach rückgängig machen, indem Sie zu einer früheren Version wechseln.

Installationsanweisungen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](install-powershell.md).

Die folgenden Cmdlets unterstützen das Erstellen und Verwalten von Schutzvorlagen:

- [Add-aipservicetemplate](/powershell/module/aipservice/add-aipservicetemplate)

- [Export-aipservicetemplate](/powershell/module/aipservice/export-aipservicetemplate)

- [Get-aipservicetemplate](/powershell/module/aipservice/get-aipservicetemplate)

- [Get-aipservicetemplateproperty](/powershell/module/aipservice/get-aipservicetemplateproperty)

- [Import-aipservicetemplate](/powershell/module/aipservice/import-aipservicetpd)

- [New-aipservicerighzdefinition](/powershell/module/aipservice/new-aipservicerightsdefinition)

- [Remove-aipservicetemplate](/powershell/module/aipservice/remove-aipservicetemplate)

- [Set-aipservicetemplateproperty](/powershell/module/aipservice/set-aipservicetemplateproperty)

## <a name="see-also"></a>Weitere Informationen
[Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md)

