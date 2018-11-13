---
title: 'Schnellstart: Suchen nach vertraulichen Informationen in lokal gespeicherten Dateien mithilfe des Azure Information Protection-Scanners'
description: Verwenden Sie den Azure Information Protection-Scanner, um nach vertraulichen Informationen in lokal gespeicherten Dateien zu suchen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: a69972ec4371c808b7a295bfc993a257e440d1e1
ms.sourcegitcommit: 227f54a8e90aa57d778ab60c646179c10e5edb44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2018
ms.locfileid: "51272396"
---
# <a name="quickstart-find-what-sensitive-information-you-have-in-files-stored-on-premises"></a>Schnellstart: Suchen nach vertraulichen Informationen in lokal gespeicherten Dateien

In dieser Schnellstartanleitung installieren und konfigurieren Sie den Azure Information Protection-Scanner, um nach vertraulichen Informationen in Dateien zu suchen, die sich in einem lokalen Datenspeicher befinden. Beispiel: Ein lokaler Ordner, eine Netzwerkfreigabe oder SharePoint Server. 

Für diese Konfiguration benötigen Sie maximal 10 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

1. Ein Abonnement, das Azure Information Protection-Plan 1 oder -Plan 2 beinhaltet.
    
    Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

2. Der Azure Information Protection-Client ist auf Ihrem Computer installiert. 
    
    Um den Client zu installieren, navigieren Sie auf der Azure Information Protection-Seite zum [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018), und laden Sie **AzInfoProtection.exe** herunter.
    
3. SQL Server Express ist ebenfalls auf Ihrem Computer installiert.
    
    Wenn diese SQL Server-Edition noch nicht installiert ist, können Sie sie über das [Microsoft Download Center](https://www.microsoft.com/en-us/sql-server/sql-server-editions-express) herunterladen und die Standardinstallation auswählen.

4. Ihr Domänenkonto ist mit Azure AD synchronisiert.

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

## <a name="prepare-a-test-folder-and-file"></a>Vorbereiten eines Testordners und einer Testdatei

Führen Sie als ersten Test, um zu bestätigen, dass der Scanner ausgeführt wird, folgende Schritte durch:

1. Erstellen Sie auf Ihrem Computer einen lokalen Ordner. Beispiel: **TestScanner** auf Ihrem lokalen C-Laufwerk.

2. Erstellen und speichern Sie ein Word-Dokument in diesem Ordner, das den Text **4242-4242-4242-4242** enthält (eine bekannte Kreditkartennummer für Testzwecke).

## <a name="install-the-scanner"></a>Installieren der Überprüfung

1. Starten Sie eine PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

2. Installieren Sie den Scanner mit dem folgenden Befehl, und geben Sie dabei Ihren Computernamen an:
    
        Install-AIPScanner -SqlServerInstance <your computer name>\SQLEXPRESS
    
    Wenn Sie aufgefordert werden, geben Sie Ihre Anmeldeinformationen für den Scanner im Format \<Domänen-/Benutzername> und dann Ihr Kennwort an. 

## <a name="specify-your-test-data-store"></a>Angeben eines Testdatenspeichers

Geben Sie in Ihrer PowerShell-Sitzung den folgenden Befehl ein:

    Add-AIPScannerRepository -Path C:\TestScanner

## <a name="configure-the-scanner-to-discover-all-information-types"></a>Konfigurieren des Scanners für die Erkennung aller Informationstypen

Geben Sie in Ihrer PowerShell-Sitzung den folgenden Befehl ein:

    Set-AIPScannerConfiguration -Enforce Off -Schedule Manual -DiscoverInformationTypes All

Dieser Befehl konfiguriert den Scanner, um eine einmalige Ermittlung aller Dateien in Ihrem angegebenen Datenrepository durchzuführen. Bei dieser Überprüfung wird nach allen bekannten vertraulichen Informationstypen gesucht. Sie müssen dabei nicht zuerst Ihre Azure Information Protection-Bezeichnungen oder Einstellungen konfigurieren.

## <a name="start-the-scan-and-confirm-it-finished"></a>Starten der Überprüfung und Überprüfen des erfolgreichen Abschlusses

1. Geben Sie in Ihrer PowerShell-Sitzung den folgenden Befehl zum Starten des Scanners ein:
    
        Start-AIPScan
    
    Nur eine kleine Datei ist zu untersuchen, damit diese erste Testüberprüfung rasch ausgeführt wird. 

2. Navigieren Sie zu Ihrem Ereignisprotokoll unter **Windows-Ereignisanzeige** > **Anwendungen und Dienste** > **Azure Information Protection**. 
    
    Vergewissern Sie sich, dass Azure Information Protection die Informationsereignis-ID **911** für den Prozess **MSIP.Scanner** anzeigt. Der Ereignisprotokolleintrag enthält darüber hinaus eine Zusammenfassung der Ergebnisse der Überprüfung.

## <a name="see-detailed-results"></a>Anzeigen detaillierter Ergebnisse

Suchen Sie mit dem Datei-Explorer die Scannerberichte unter „%*localappdata*%\Microsoft\MSIP\Scanner\Reports“. Öffnen Sie die detaillierten Berichtsdatei im CSV-Format.

In Excel zeigen die ersten beiden Spalten Ihr Datenspeicherrepository und den Dateinamen an. Beim Durchgehen der Spalten werden Sie eine Spalte mit dem Namen **Name des Informationstyps** sehen – die Spalte, die für Sie von großem Interesse sein wird. Für unseren ersten Test wird **Kreditkartennummer** angezeigt, eine von vielen Typen vertraulicher Informationen, die der Scanner erkennen kann.

## <a name="scan-your-own-data"></a>Überprüfen eigener Daten

1. Führen Sie erneut „Add-AIPScannerRepository“ aus, geben Sie jedoch diesmal Ihren eigenen lokalen Datenspeicher an, der auf vertrauliche Informationen geprüft werden soll. 
    
    Sie können einen lokalen Ordner, eine Netzwerkfreigabe (UNC-Pfad) oder eine SharePoint Server-URL für eine SharePoint-Website oder -Bibliothek angeben. 
    
    - Beispiel für einen lokalen Ordner:
        
            Add-AIPScannerRepository -Path D:\Data\Finance
    
    - Beispiel für eine Netzwerkfreigabe
        
            Add-AIPScannerRepository -Path \\NAS\HR
    
    - Beispiel für einen SharePoint-Ordner:
        
            Add-AIPScannerRepository -Path "http://sp2016/Shared Documents"

2. Starten Sie erneut den Scanner:
    
        Start-AIPScan

3. Wenn die Überprüfung abgeschlossen ist, sehen Sie sich die neuen Ergebnisse an. 
    
    Die Dauer dieser Überprüfung hängt davon ab, wie viele Dateien in Ihrem Datenspeicher vorhanden sind, wie groß diese Dateien sind sowie vom Typ der Datei. 

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

In einer Produktionsumgebung würden Sie den Scanner auf einem Windows-Server über ein Dienstkonto ausführen, das im Hintergrund beim Azure Information Protection-Dienst authentifiziert wird. Außerdem würden Sie eine Unternehmensversion von SQL Server verwenden und wahrscheinlich mehrere Datenrepositorys angeben. 

Um Ressourcen zu bereinigen, die für diese Produktionsbereitstellung bereit sind, führen Sie in der PowerShell-Sitzung den folgenden Befehl aus, um den Scanner zu deinstallieren:

    Uninstall-AIPScanner

Starten Sie den Computer neu.

Mit diesem Befehl werden die folgenden Elemente nicht entfernt, weshalb Sie sie manuell entfernen müssen, wenn Sie sie nach Abschluss dieser Schnellstartanleitung nicht mehr benötigen:

- Die SQL Server-Datenbank mit dem Namen **AzInfoProtection**, die bei der Installation des Azure Information Protection-Scanners mit dem Cmdlet „Install-AIPScanner“ erstellt wurde 

- Die Scannerberichte unter „%*localappdata*%\Microsoft\MSIP\Scanner\Reports“

- Die Zuweisung des Benutzerrechts **Als Dienst anmelden**, das Ihrem Domänenkonto für Ihren lokalen Computer erteilt wurde


## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung wird die Mindestkonfiguration beschrieben, sodass Sie schnell sehen können, wie mit dem Scanner nach vertraulichen Informationen in einer Netzwerkfreigabe gesucht werden kann. Informationen zum Installieren des Scanners in einer Produktionsumgebung finden Sie unter [Bereitstellen des Azure Information Protection-Scanners zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md).

Wenn Sie die Dateien klassifizieren und schützen möchten, die vertrauliche Informationen enthalten, müssen Sie Azure Information Protection-Bezeichnungen für die automatische Klassifizierung und den automatischen Schutz konfigurieren:

- [Gewusst wie: Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)

- [How to configure a label for Rights Management protection (Konfigurieren einer Bezeichnung für Rights Management-Schutz)](configure-policy-protection.md)