---
title: Verwenden von PowerShell mit dem Azure Information Protection unified bezeichnungs-client
description: Anweisungen und Informationen für Administratoren des Azure Information Protection unified bezeichnungs-Clients mithilfe von PowerShell verwalten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 05/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: a7e7ad68a5b7ce6c465b990b15bbef6824fadf75
ms.sourcegitcommit: c0d8b7239fc16e66b51f736636da7f7212f72dd6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837803"
---
# <a name="admin-guide-using-powershell-with-the-azure-information-protection-unified-client"></a>Administratorhandbuch: Mithilfe von PowerShell mit dem einheitlichen Azure Information Protection-client

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Wenn Sie den Azure Information Protection unified bezeichnungs-Client installieren, werden PowerShell-Befehle automatisch installiert. Dadurch können Sie den Client durch Ausführen von Befehlen, die Sie in Skripts zur Automatisierung einfügen können, verwalten.

Die Cmdlets sind mit dem PowerShell-Modul installiert **"azureinformationprotection"**, das Cmdlets für die Bezeichnung wurde. Zum Beispiel:

|Cmdlet für die Bezeichnung|Beispielsyntax|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)|Für einen freigegebenen Ordner werden alle Dateien mit einer bestimmten Bezeichnung ermittelt.|
|[Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification)|Überprüfen Sie bei einem freigegebenen Ordner die Dateiinhalte, und versehen Sie Dateien ohne Bezeichnung automatisch gemäß den von Ihnen festgelegten Bedingungen mit Bezeichnungen.|
|[Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)|Für einen freigegebenen Ordner wird eine bestimmte Bezeichnung auf alle Dateien ohne Bezeichnung angewendet.|
|[Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)|Bezeichnen Sie Dateien interaktiv mit einem anderen Benutzerkonto auf Ihre eigenen.|

> [!TIP]
> Um Cmdlets mit Pfadlängen zu verwenden, die mehr als 260 Zeichen umfassen, können Sie die folgende [Gruppenrichtlinieneinstellung](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/) verwenden, die ab Windows 10, Version 1607 verfügbar ist:<br /> **Lokale Computerrichtlinie** > **Computerkonfiguration** > **Administrative Vorlagen** > **alle Einstellungen**  >  **Ermöglichen Win32 lange Pfade** 
> 
> Bei Windows Server 2016 können Sie die gleiche Gruppenrichtlinieneinstellung verwenden, wenn Sie die neuesten administrativen Vorlagen (ADMX-Dateien) für Windows 10 installieren.
>
> Weitere Informationen finden Sie im Abschnitt [Maximum Path Length Limitation (Einschränkung der Pfadlänge)](https://docs.microsoft.com/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Entwicklerdokumentation für Windows 10.

Dieses Modul installiert **\ProgramFiles (x86) \Microsoft Azure Information Protection** und fügt diesen Ordner der Systemvariablen **PSModulePath** hinzu. Die DLL-Datei für dieses Modul lautet **AIP.dll**.

### <a name="prerequisites-for-using-the-azureinformationprotection-module"></a>Voraussetzungen für die Verwendung des Moduls "azureinformationprotection"

Zusätzlich zu den Voraussetzungen für die Installation des Moduls "azureinformationprotection" gibt es zusätzliche Anforderungen an, wenn Sie die bezeichnungs-Cmdlets für Azure Information Protection verwenden:

1. Der Azure Rights Management-Dienst muss aktiviert werden.

2. So entfernen Sie den Schutz von Dateien für andere mithilfe Ihres eigenen Kontos: 

    - Die Administratorfunktion muss für Ihre Organisation aktiviert werden. Zudem muss Ihr Konto als Administrator für Azure Rights Management konfiguriert sein.

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>Voraussetzung 1: Der Azure Rights Management-Dienst muss aktiviert sein

Wenn es sich bei Ihrem Azure Information Protection-Mandanten nicht aktiviert ist, um den Schutz anzuwenden, lesen Sie die Anweisungen für [Aktivieren von Azure Rights Management](../activate-service.md).

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>Voraussetzung 2: Sie entfernen den Schutz von Dateien für andere mithilfe Ihres eigenen Kontos

Typische Szenarien für das Entfernen des Schutzes von Dateien für andere Benutzer umfassen die Datenermittlung oder Datenwiederherstellung. Wenn Sie den Schutz mithilfe von Bezeichnungen anwenden, können Sie den Schutz durch Festlegen einer neuen Bezeichnung entfernen, durch die kein Schutz angewendet wird. Sie können dazu aber auch die Bezeichnung entfernen.

Sie müssen über ein Rights Management-Nutzungsrecht verfügen oder Administrator sein, um den Schutz von Dateien zu entfernen. Für die Datenermittlung oder Datenwiederherstellung wird in der Regel die Administratorfunktion verwendet. Informationen zum Aktivieren dieses Feature und zum Konfigurieren Ihres Kontos als Administrator finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder Datenwiederherstellung](../configure-super-users.md).


## <a name="next-steps"></a>Nächste Schritte
Für ein Cmdlet-Hilfe, wenn Sie in einer PowerShell-Sitzung sind `Get-Help <cmdlet name> -online`. Zum Beispiel: 

    Get-Help Set-AIPFileLabel -online

Weitere Informationen, die möglicherweise zur Unterstützung des Azure Information Protection-Clients erforderlich sind, finden Sie unter den folgenden Themen:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)
