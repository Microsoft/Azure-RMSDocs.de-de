---
title: 'Schnellstart: Suchen nach vertraulichen Informationen mit dem Azure Information Protection-Scanner'
description: Verwenden Sie den Azure Information Protection-Scanner, um nach vertraulichen Informationen in lokal gespeicherten Dateien zu suchen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/01/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.custom: admin
ms.subservice: aiplabels
ms.openlocfilehash: 82900a08a630987c52b2352725f3542e50b9c50a
ms.sourcegitcommit: 223e26b0ca4589317167064dcee82ad0a6a8d663
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86048407"
---
# <a name="quickstart-find-what-sensitive-information-you-have-in-files-stored-on-premises"></a>Schnellstart: Suchen nach vertraulichen Informationen in lokal gespeicherten Dateien

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

In dieser Schnellstartanleitung erteilen Sie SharePoint die Berechtigung, Überprüfungen zu erlauben, und Sie installieren und konfigurieren die Azure Information Protection-Überprüfung, um nach vertraulichen Informationen in Dateien zu suchen, die sich in einem lokalen Datenspeicher befinden, zum Beispiel in der Netzwerkfreigabe oder in einem SharePoint-Server.

> [!NOTE]
> Sie können diese Schnellstartanleitung mit der aktuellen allgemein verfügbaren Version des Azure Information Protection-Clients (klassisch) oder des Azure Information Protection-Clients für einheitliche Bezeichnungen verwenden, der den Scanner enthält.
>  
> Wenn Sie nicht sicher sind, was der Unterschied zwischen diesen Clients ist, sehen Sie sich diese [FAQ](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients) an.

Für diese Konfiguration benötigen Sie maximal 15 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

1. Ein Abonnement, das Azure Information Protection-Plan 1 oder -Plan 2 beinhaltet.
    
    Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

2. Einer der folgenden Azure Information Protection-Clients ist auf Ihrem Computer installiert:
    
    - Der klassische Client: Um diesen Client zu installieren, navigieren Sie auf der Azure Information Protection-Seite zum [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018), und laden Sie **AzInfoProtection.exe** herunter.
    
    - Der Client für einheitliche Bezeichnungen: Um diesen Client zu installieren, navigieren Sie auf der Azure Information Protection-Seite zum [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018), und laden Sie **AzInfoProtection_UL.exe** herunter.
    
3. SQL Server Express ist ebenfalls auf Ihrem Computer installiert.
    
    Wenn diese SQL Server-Edition noch nicht installiert ist, können Sie sie über das [Microsoft Download Center](https://www.microsoft.com/sql-server/sql-server-editions-express) herunterladen und die Standardinstallation auswählen.

4. Ihr Domänenkonto ist mit Azure AD synchronisiert.

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

5. Die SharePoint-Richtlinie berechtigt zum Zugriff, wenn Sie die Berechtigung für eine SharePoint-Überprüfung erteilen.

## <a name="prepare-a-test-folder-and-file"></a>Vorbereiten eines Testordners und einer Testdatei

Führen Sie als ersten Test, um zu bestätigen, dass der Scanner ausgeführt wird, folgende Schritte durch:

1. Erstellen Sie einen neuen Ordner auf einer zugänglichen Netzwerkfreigabe. Nennen Sie diesen Ordner z. B. **TestScanner**.

2. Erstellen und speichern Sie ein Word-Dokument in diesem Ordner, das den Text **Credit card: 4242-4242-4242-4242** enthält.

## <a name="permission-users-to-scan-sharepoint-repositories"></a>Berechtigung für Benutzer zum Überprüfen von SharePoint-Repositorys

Sie können den Scanner für mehrere SharePoint-Repositorys verwenden, indem Sie die Website-URL angeben. Azure Information Protection ermittelt alle Websites, die zu dieser URL gehören, und führt eine Überprüfung durch.

Um repositoryübergreifende Überprüfungen zu ermöglichen, fügen Sie die folgenden SharePoint-Berechtigungen dem Benutzer hinzu, der die Überprüfung durchführen soll:

1. Öffnen Sie SharePoint, und wählen Sie nacheinander **Berechtigungsrichtlinie** und **Richtlinienstufe für Berechtigungen hinzufügen** aus. 

    ![Erstellen einer neuen Richtlinienstufe für Berechtigungen für einen bestimmten Benutzer](./media/aip-quick-set-sp-permissions.png)


2. Wählen Sie unter **Berechtigungen der Websitesammlung** die Option **Websitesammlungsauditor** aus.   

3. Wählen Sie unter **Berechtigungen** die Option **Erteilen** für **Anwendungsseiten anzeigen** aus, und **speichern** Sie Ihre Änderungen.  

    ![Auswählen von Websitesammlungsauditor und Berechtigungsoptionen für einen bestimmten Benutzer](./media/aip-quick-set-site-permissions.png)

4. Klicken Sie nach dem Bestätigen Ihrer Änderungen im Hinweis **Richtlinie für Webanwendung** auf **OK**.   

5. Fügen Sie auf der Seite **Benutzer hinzufügen** im Feld **Benutzer auswählen** den Benutzer hinzu, der die Überprüfung ausführen soll. Wählen Sie unter **Berechtigungen auswählen** die Option **Websitesammlung** aus, und klicken Sie dann auf **Fertig stellen**, um dem hinzugefügten oder ausgewählten Benutzer die erstellten Berechtigungen zu erteilen. 

    ![Optionen beim Hinzufügen eines Benutzers zu neuen Berechtigungen](./media/aip-quick-set-user-permissions.png)

## <a name="configure-a-profile-for-the-scanner"></a>Konfigurieren eines Profils für den Scanner

Bevor Sie den Scanner installieren, erstellen Sie im Azure-Portal ein Profil dafür. Dieses Profil enthält Scannereinstellungen sowie Speicherorte der zu scannenden Datenrepositorys.

1. Öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal). Navigieren Sie anschließend zum Bereich **Azure Information Protection**. 
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.
    
2. Suchen Sie im linken Bereich die **Scanneroptionen**, und klicken Sie auf **Profile**.

3. Klicken Sie im Bereich **Azure Information Protection – Profile** auf die Option **Hinzufügen**:
    
    ![Hinzufügen eines Profils für den Azure Information Protection-Scanner](./media/scanner-add-profile.png)

4. Geben Sie im Bereich **Neues Profil hinzufügen** einen Namen für den Scanner ein, der zum Erkennen der Konfigurationseinstellungen und der Datenrepositorys verwendet wird, die überprüft werden sollen. Für diese Schnellstartanleitung können Sie z.B. **Schnellstart** eingeben. Diesen Profilnamen müssen Sie angeben, wenn Sie den Scanner später installieren.
    
    Optional können Sie eine Beschreibung für administrative Zwecke eingeben, damit Sie den Profilnamen des Scanners leichter erkennen.

5. Suchen Sie den Abschnitt **Richtlinienerzwingung**, und wählen Sie für diese Schnellstartanleitung nur eine Einstellung aus: Wählen Sie für **Erzwingen** die Option **Aus**. Klicken Sie dann auf **Speichern**, aber schließen Sie den Bereich nicht.
    
    Die Einstellungen konfigurieren den Scanner so, dass eine einmalige Ermittlung aller Dateien in Ihrem angegebenen Datenrepository durchgeführt wird. Bei dieser Überprüfung wird nach allen bekannten vertraulichen Informationstypen gesucht. Sie müssen dabei nicht zuerst Ihre Azure Information Protection-Bezeichnungen oder Einstellungen konfigurieren.

6. Nachdem Sie das Profil erstellt und gespeichert haben, können Sie zur Option **Repositorys konfigurieren** zurückkehren, um Ihren Netzwerkordner als den Datenspeicher anzugeben, der überprüft werden soll.
    
    Klicken Sie im Bereich **Neues Profil hinzufügen** auf die Option **Repositorys konfigurieren**, um das den Bereich **Repositorys** zu öffnen:
    
    ![Konfigurieren von Datenrepositorys für den Azure Information Protection-Scanner](./media/scanner-repositories-bar.png)

7. Klicken Sie im Bereich **Repositorys** auf die Option **Hinzufügen**:
    
    ![Hinzufügen eines Datenrepositorys für den Azure Information Protection-Scanner](./media/scanner-repository-add.png)

8. Geben Sie im Bereich **Repository** den Ordner an, den Sie im ersten Schritt erstellt haben. Beispiel: `\\server\TestScanner`
    
    Nehmen Sie keine Änderungen an den restlichen Einstellungen in diesem Bereich vor, sondern behalten Sie diese als **Profilstandard** bei. So werden die Einstellungen vom Datenrepository aus dem Scannerprofil übernommen. 
    
    Wählen Sie **Speichern** aus.

9. Wenn Sie zum Bereich **Azure Information Protection – Profile** zurückkehren, werden dort jetzt Ihr Profilname sowie die Spalte **ZEITPLAN** mit der Einstellung **Manuell** und die leere Spalte **ERZWINGEN** angezeigt. 
    
    Die Spalte **KNOTEN** zeigt **0** an, weil Sie die Überprüfung für dieses Profil noch nicht installiert haben.

Nun können Sie den Scanner mit dem Scannerprofil installieren, das Sie eben erstellt haben.

## <a name="install-the-scanner"></a>Installieren der Überprüfung

1. Starten Sie eine PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

2. Verwenden Sie den folgenden Befehl, um den Scanner zu installieren und dabei den Namen Ihrer Netzwerkfreigabe sowie den Profilnamen anzugeben, den Sie im Azure-Portal gespeichert haben:

    ```ps
    Install-AIPScanner -SqlServerInstance <your network share name>\SQLEXPRESS -Profile <profile name>
    ```

    Wenn Sie aufgefordert werden, geben Sie Ihre Anmeldeinformationen für den Scanner im Format \<domain\user name> und dann Ihr Kennwort an. 

## <a name="start-the-scan-and-confirm-it-finished"></a>Starten der Überprüfung und Überprüfen des erfolgreichen Abschlusses

1. Im Azure-Portal aktualisieren Sie den Bereich **Azure Information Protection – Profile**. In der Spalte **KNOTEN** wird jetzt **1** angezeigt.

2. Wählen Sie Ihren Profilnamen und dann die Option **Jetzt überprüfen** aus:
    
    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)
    
    Wenn diese Option nicht verfügbar ist, nachdem Sie Ihr Profil ausgewählt haben, ist die Überprüfung nicht mit Azure Information Protection verbunden. Überprüfen Sie die Konfiguration und die Internetkonnektivität.

3. Es ist nur eine kleine Datei ist zu untersuchen, daher wird diese erste Testüberprüfung sehr schnell ausgeführt:
    
    Warten Sie, bis die Werte für die Spalten **LETZTE ÜBERPRÜFUNGSERGEBNISSE** und **LETZTE ÜBERPRÜFUNG (ENDZEIT)** angezeigt werden.
    
    Alternativ gilt für den Scanner des klassischen Clients Folgendes: Überprüfen Sie das lokale Ereignisprotokoll **Anwendungen und Dienste**, **Azure Information Protection**. Bestätigen Sie die ID **911** des Informationsereignisses für den Prozess **MSIP.Scanner**. Der Ereignisprotokolleintrag enthält darüber hinaus eine Zusammenfassung der Ergebnisse der Überprüfung.

## <a name="see-detailed-results"></a>Anzeigen detaillierter Ergebnisse

Suchen Sie mit dem Datei-Explorer die Scannerberichte unter „%*localappdata*%\Microsoft\MSIP\Scanner\Reports“. Öffnen Sie die detaillierten Berichtsdatei im CSV-Format.

In Excel zeigen die ersten beiden Spalten Ihr Datenspeicherrepository und den Dateinamen an. Beim Durchgehen der Spalten werden Sie eine Spalte mit dem Namen **Name des Informationstyps** sehen – die Spalte, die für Sie von großem Interesse sein wird. Für unseren ersten Test wird **Kreditkartennummer** angezeigt, eine von vielen Typen vertraulicher Informationen, die der Scanner erkennen kann.

## <a name="scan-your-own-data"></a>Überprüfen eigener Daten

1. Bearbeiten Sie Ihr Scannerprofil, und fügen Sie ein neues Datenrepository hinzu, geben Sie jedoch diesmal Ihren eigenen lokalen Datenspeicher an, der auf vertrauliche Informationen geprüft werden soll.     
    Sie können eine Netzwerkfreigabe (UNC-Pfad) oder eine SharePoint Server-URL für eine SharePoint-Website oder -Bibliothek angeben. 
    
    - **Beispiel für eine Netzwerkfreigabe**
        ```sh        
        \\NAS\HR
        ```
    - **Beispiel für einen SharePoint-Ordner**
        ```sh
        http://sp2016/Shared Documents
        ```

2. Starten Sie den Scanner erneut: Stellen Sie im Bereich **Azure Information Protection – Profile** sicher, dass Ihr Profil ausgewählt ist, und klicken Sie dann auf die Option **Jetzt scannen**:
    
    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)

3. Wenn die Überprüfung abgeschlossen ist, sehen Sie sich die neuen Ergebnisse an. 
    
    Die Dauer dieser Überprüfung hängt davon ab, wie viele Dateien in Ihrem Datenspeicher vorhanden sind, wie groß diese Dateien sind sowie vom Typ der Datei. 

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

In einer Produktionsumgebung würden Sie den Scanner auf einem Windows-Server über ein Dienstkonto ausführen, das im Hintergrund beim Azure Information Protection-Dienst authentifiziert wird. Außerdem würden Sie eine Unternehmensversion von SQL Server verwenden und wahrscheinlich mehrere Datenrepositorys angeben. 

Um Ressourcen zu bereinigen, die für diese Produktionsbereitstellung bereit sind, führen Sie in der PowerShell-Sitzung den folgenden Befehl aus, um den Scanner zu deinstallieren:

```ps
Uninstall-AIPScanner
```

Starten Sie den Computer neu.

Mit diesem Befehl werden die folgenden Elemente nicht entfernt, weshalb Sie sie manuell entfernen müssen, wenn Sie sie nach Abschluss dieser Schnellstartanleitung nicht mehr benötigen:

- Die SQL Server-Datenbank, die bei der Installation des Azure Information Protection-Scanners mit dem Cmdlet „Install-AIPScanner“ erstellt wurde:
    - Für den klassischen Client: **AIPScanner_\<profile>**
    - Für den Client für einheitliche Bezeichnungen: **AIPScannerUL_\<profile_name>**

- Die Scannerberichte unter „%*localappdata*%\Microsoft\MSIP\Scanner\Reports“

- Die Zuweisung des Benutzerrechts **Als Dienst anmelden**, das Ihrem Domänenkonto für Ihren lokalen Computer erteilt wurde


## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung wird die Mindestkonfiguration beschrieben, sodass Sie schnell sehen können, wie mit der Überprüfung in lokalen Datenspeichern nach vertraulichen Informationen gesucht werden kann. Informationen zum Installieren des Scanners in einer Produktionsumgebung finden Sie unter [Bereitstellen des Azure Information Protection-Scanners zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md).

Wenn Sie die Dateien klassifizieren und schützen möchten, die vertrauliche Informationen enthalten, müssen Sie Bezeichnungen für die automatische Klassifizierung und den automatischen Schutz konfigurieren:

- Für den klassischen Client:
    - [Gewusst wie: Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)
    - [How to configure a label for Rights Management protection (Konfigurieren einer Bezeichnung für Rights Management-Schutz)](configure-policy-protection.md)

- Für den Client für einheitliche Bezeichnungen:
    - [Automatisches Anwenden einer Vertraulichkeitsbezeichnung auf Inhalte](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically)
    - [Einschränken des Zugriffs auf Inhalte mithilfe der Verschlüsselung in Vertraulichkeitsbezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)
