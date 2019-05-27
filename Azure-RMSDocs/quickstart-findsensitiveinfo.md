---
title: 'Schnellstart: Suchen nach vertraulichen Informationen mit dem Azure Information Protection-Scanner'
description: Verwenden Sie den Azure Information Protection-Scanner, um nach vertraulichen Informationen in lokal gespeicherten Dateien zu suchen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.openlocfilehash: 657d85e90ffe4192514101595815f5110564d761
ms.sourcegitcommit: fe23bc3e24eb09b7450548dc32b4ef09c8970615
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2019
ms.locfileid: "64767795"
---
# <a name="quickstart-find-what-sensitive-information-you-have-in-files-stored-on-premises"></a>Schnellstart: Suchen nach vertraulichen Informationen in lokal gespeicherten Dateien

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

In dieser Schnellstartanleitung installieren und konfigurieren Sie den Azure Information Protection-Scanner, um nach vertraulichen Informationen in Dateien zu suchen, die sich in einem lokalen Datenspeicher befinden. Beispiel: Ein lokaler Ordner, eine Netzwerkfreigabe oder SharePoint Server.

Hinweis: Für diese Schnellstartanleitung wird die aktuelle, allgemein verfügbare Version des Scanners verwendet, bei der die Konfiguration über das Azure-Portal erfolgt, nicht wie in vorherigen Versionen über PowerShell-Cmdlets.

Für diese Konfiguration benötigen Sie maximal 10 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

1. Ein Abonnement, das Azure Information Protection-Plan 1 oder -Plan 2 beinhaltet.
    
    Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

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

## <a name="configure-a-profile-for-the-scanner"></a>Konfigurieren eines Profils für den Scanner

Bevor Sie den Scanner installieren, erstellen Sie im Azure-Portal ein Profil dafür. Dieses Profil enthält Scannereinstellungen sowie Speicherorte der zu scannenden Datenrepositorys.

1. Öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal). Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
2. Suchen Sie die **Scanner**-Menüoptionen, und wählen Sie **Profile** aus.

3. Wählen Sie auf dem Blatt **Azure Information Protection – Profile** die Option **Hinzufügen** aus:
    
    ![Hinzufügen eines Profils für den Azure Information Protection-Scanner](./media/scanner-add-profile.png)

4. Geben Sie auf dem Blatt **Neues Profil hinzufügen** einen Namen für den Scanner ein, der zum Erkennen der Konfigurationseinstellungen und der Datenrepositorys verwendet wird, die überprüft werden sollen. Für diese Schnellstartanleitung können Sie z.B. **Schnellstart** eingeben. Diesen Profilnamen müssen Sie angeben, wenn Sie den Scanner später installieren.
    
    Optional können Sie eine Beschreibung für administrative Zwecke eingeben, damit Sie den Profilnamen des Scanners leichter erkennen.

5. Wählen Sie für diese Schnellstartanleitung nur eine Einstellung aus: Legen Sie die **Richtlinienerzwingung** auf die Einstellung **aus** fest. Klicken Sie dann auf **Speichern**, aber schließen Sie das Blatt nicht.
    
    Die Einstellungen konfigurieren den Scanner so, dass eine einmalige Ermittlung aller Dateien in Ihrem angegebenen Datenrepository durchgeführt wird. Dieser Scan sucht nach allen bekannten vertraulichen Informationstypen. Es ist dabei nicht erforderlich, dass Sie zuerst Ihre Azure Information Protection-Bezeichnungen oder -Richtlinieneinstellungen konfigurieren.

6. Nachdem Sie das Profil erstellt und gespeichert haben, können Sie zur Option **Repositorys konfigurieren** zurückkehren, um Ihren lokalen Ordner als den Datenspeicher anzugeben, der überprüft werden soll.
    
    Wählen Sie auf dem Blatt **Neues Profil hinzufügen** die Option **Repositorys konfigurieren** aus, um das Blatt **Repositorys** zu öffnen:
    
    ![Konfigurieren von Datenrepositorys für den Azure Information Protection-Scanner](./media/scanner-repositories-bar.png)

7. Wählen Sie auf dem Blatt **Repositorys** die Option **Hinzufügen** aus:
    
    ![Hinzufügen eines Datenrepositorys für den Azure Information Protection-Scanner](./media/scanner-repository-add.png)

8. Geben Sie auf dem Blatt **Repository** Ihren lokalen Ordner an, den Sie im ersten Schritt erstellt haben. Beispiel: `C:\TestScanner`
    
    Nehmen Sie keine Änderungen an den restlichen Einstellungen auf diesem Blatt vor, sondern behalten Sie diese als **Profilstandard** bei. So werden die Einstellungen vom Datenrepository aus dem Scannerprofil übernommen. 
    
    Wählen Sie **Speichern** aus.

9. Sie können das Blatt **Neues Profil hinzufügen** jetzt schließen. Daraufhin werden auf dem Blatt **Azure Information Protection – Profile** Ihr Profilname sowie die Spalte **ZEITPLAN** mit der Einstellung **Manuell** und die leere Spalte **ERZWINGEN** angezeigt.

Nun können Sie den Scanner mit dem Scannerprofil installieren, das Sie eben erstellt haben.

## <a name="install-the-scanner"></a>Installieren der Überprüfung

1. Starten Sie eine PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

2. Verwenden Sie den folgenden Befehl, um den Scanner zu installieren und dabei den Namen Ihres eigenen Computers sowie den Profilnamen anzugeben, den Sie im Azure-Portal gespeichert haben:
    
        Install-AIPScanner -SqlServerInstance <your computer name>\SQLEXPRESS -Profile <profile name>
    
    Wenn Sie aufgefordert werden, geben Sie Ihre Anmeldeinformationen für den Scanner im Format \<Domänen-/Benutzername> und dann Ihr Kennwort an. 

## <a name="start-the-scan-and-confirm-it-finished"></a>Starten der Überprüfung und Überprüfen des erfolgreichen Abschlusses

1. Kehren Sie im Azure-Portal zu Azure Information Protection zurück, um den Scanner zu starten. Wählen Sie im Menü **Scanner** die Option **Knoten** aus. Wählen Sie Ihren Computernamen und dann die Option **Jetzt überprüfen** aus:
    
    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)

2. Es ist nur eine kleine Datei ist zu untersuchen, daher wird diese erste Testüberprüfung sehr schnell ausgeführt:
    
    - Auf dem Blatt **Azure Information Protection – Knoten** ändert sich der Wert für die Spalte **STATUS** von **Scannen** in **Im Leerlauf**.
    
    - Überprüfen Sie alternativ dazu das lokale Windows-Ereignisprotokoll **Anwendungen und Dienste** – **Azure Information Protection**. Bestätigen Sie die ID **911** des Informationsereignisses für den Prozess **MSIP.Scanner**. Der Ereignisprotokolleintrag enthält darüber hinaus eine Zusammenfassung der Ergebnisse der Überprüfung.

## <a name="see-detailed-results"></a>Anzeigen detaillierter Ergebnisse

Suchen Sie mit dem Datei-Explorer die Scannerberichte unter „%*localappdata*%\Microsoft\MSIP\Scanner\Reports“. Öffnen Sie die detaillierten Berichtsdatei im CSV-Format.

In Excel zeigen die ersten beiden Spalten Ihr Datenspeicherrepository und den Dateinamen an. Beim Durchgehen der Spalten werden Sie eine Spalte mit dem Namen **Name des Informationstyps** sehen – die Spalte, die für Sie von großem Interesse sein wird. Für unseren ersten Test wird **Kreditkartennummer** angezeigt, eine von vielen Typen vertraulicher Informationen, die der Scanner erkennen kann.

## <a name="scan-your-own-data"></a>Überprüfen eigener Daten

1. Bearbeiten Sie Ihr Scannerprofil, und fügen Sie ein neues Datenrepository hinzu, geben Sie jedoch diesmal Ihren eigenen lokalen Datenspeicher an, der auf vertrauliche Informationen geprüft werden soll. 
    
    Sie können einen lokalen Ordner, eine Netzwerkfreigabe (UNC-Pfad) oder eine SharePoint Server-URL für eine SharePoint-Website oder -Bibliothek angeben. 
    
    - Beispiel für einen lokalen Ordner:
        
            D:\Data\Finance
    
    - Beispiel für eine Netzwerkfreigabe
        
            \\NAS\HR
    
    - Beispiel für einen SharePoint-Ordner:
        
            http://sp2016/Shared Documents

2. Starten Sie den Scanner erneut: Wählen Sie im **Scanner**-Menü die Option **Knoten** aus, und wählen Sie dann Ihren Computernamen und die Option **Jetzt überprüfen** aus:
    
    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)

3. Wenn die Überprüfung abgeschlossen ist, sehen Sie sich die neuen Ergebnisse an. 
    
    Die Dauer dieser Überprüfung hängt davon ab, wie viele Dateien in Ihrem Datenspeicher vorhanden sind, wie groß diese Dateien sind sowie vom Typ der Datei. 

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

In einer Produktionsumgebung würden Sie den Scanner auf einem Windows-Server über ein Dienstkonto ausführen, das im Hintergrund beim Azure Information Protection-Dienst authentifiziert wird. Außerdem würden Sie eine Unternehmensversion von SQL Server verwenden und wahrscheinlich mehrere Datenrepositorys angeben. 

Um Ressourcen zu bereinigen, die für diese Produktionsbereitstellung bereit sind, führen Sie in der PowerShell-Sitzung den folgenden Befehl aus, um den Scanner zu deinstallieren:

    Uninstall-AIPScanner

Starten Sie den Computer neu.

Mit diesem Befehl werden die folgenden Elemente nicht entfernt, weshalb Sie sie manuell entfernen müssen, wenn Sie sie nach Abschluss dieser Schnellstartanleitung nicht mehr benötigen:

- Die SQL Server-Datenbank mit dem Namen **AIPScanner_\<Profil>** , die während der Installation des Azure Information Protection-Scanners mit dem Cmdlet „Install-AIPScanner“ erstellt wurde 

- Die Scannerberichte unter „%*localappdata*%\Microsoft\MSIP\Scanner\Reports“

- Die Zuweisung des Benutzerrechts **Als Dienst anmelden**, das Ihrem Domänenkonto für Ihren lokalen Computer erteilt wurde


## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung wird die Mindestkonfiguration beschrieben, sodass Sie schnell sehen können, wie mit dem Scanner nach vertraulichen Informationen in einer Netzwerkfreigabe gesucht werden kann. Informationen zum Installieren des Scanners in einer Produktionsumgebung finden Sie unter [Bereitstellen des Azure Information Protection-Scanners zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md).

Wenn Sie die Dateien klassifizieren und schützen möchten, die vertrauliche Informationen enthalten, müssen Sie Azure Information Protection-Bezeichnungen für die automatische Klassifizierung und den automatischen Schutz konfigurieren:

- [Gewusst wie: Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)

- [How to configure a label for Rights Management protection (Konfigurieren einer Bezeichnung für Rights Management-Schutz)](configure-policy-protection.md)
