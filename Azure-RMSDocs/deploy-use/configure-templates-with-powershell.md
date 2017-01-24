---
title: "PowerShell-Referenz für benutzerdefinierte Vorlagen | Azure Information Protection"
description: "Alle Vorgänge, die Sie im klassischen Azure-Portal zum Erstellen und Verwalten von Rechteverwaltungsvorlagen ausführen können, können Sie auch mithilfe von PowerShell über die Befehlszeile durchführen. Darüber hinaus können Sie Vorlagen exportieren und importieren, sodass Sie Vorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften in Vorlagen, z. B. von mehrsprachigen Namen und Beschreibungen, ausführen können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 6a62cb54fcf6129a66c4be23f2270ce56967d5e4


---



# <a name="powershell-reference-for-custom-templates"></a>PowerShell-Referenz für benutzerdefinierte Vorlagen

>*Gilt für: Azure Information Protection, Office 365*

Alle Vorgänge, die Sie im klassischen Azure-Portal zum Erstellen und Verwalten von Rechteverwaltungsvorlagen ausführen können, können Sie auch mithilfe von PowerShell über die Befehlszeile durchführen. Darüber hinaus können Sie Vorlagen exportieren und importieren, sodass Sie Vorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften in Vorlagen, z. B. von mehrsprachigen Namen und Beschreibungen, ausführen können.

Sie können das Exportieren und Importieren auch zum Sichern und Wiederherstellen der benutzerdefinierten Vorlagen verwenden. Als bewährte Methode wird empfohlen, regelmäßig eine Sicherungskopie der benutzerdefinierten Vorlagen zu erstellen. So können Sie jederzeit leicht zur vorherigen Version zurückwechseln, falls Sie einmal eine unbeabsichtigte Änderung vornehmen sollten.

> [!IMPORTANT]
> Um Windows PowerShell zum Erstellen und Verwalten von Azure Rights Management-Vorlagen zu verwenden, benötigen Sie mindestens Version 2.0.0.0 des [Windows PowerShell-Moduls für Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Wenn Sie dieses PowerShell-Modul bereits zuvor installiert hatten, führen Sie den folgenden Befehl in einem PowerShell-Fenster aus, um die Versionsnummer zu überprüfen: `(Get-Module aadrm -ListAvailable).Version`

Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).

Die Cmdlets, die das Erstellen und Verwalten von Vorlagen unterstützen:

-   [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Remove-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)



## <a name="see-also"></a>Siehe auch
[Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](configure-custom-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


