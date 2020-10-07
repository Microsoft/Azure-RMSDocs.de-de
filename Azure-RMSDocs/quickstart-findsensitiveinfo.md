---
title: 'Schnellstart: Suchen nach vertraulichen Informationen mit dem Azure Information Protection-Scanner'
description: Verwenden Sie den Azure Information Protection-Scanner, um nach vertraulichen Informationen in lokal gespeicherten Dateien zu suchen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/19/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.custom: admin
ms.subservice: aiplabels
ms.openlocfilehash: 04e114e6b719288a26663bd5534af4b1f1b73ac8
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91587880"
---
# <a name="quickstart-find-what-sensitive-information-you-have-in-files-stored-on-premises"></a>Schnellstart: Suchen nach vertraulichen Informationen in lokal gespeicherten Dateien

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection-Clients für Windows – klassischer Client oder Client für einheitliche Bezeichnungen](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

In dieser Schnellstartanleitung erteilen Sie SharePoint die Berechtigung, Überprüfungen zu erlauben, und Sie installieren und konfigurieren den Azure Information Protection-Scanner, um nach vertraulichen Daten zu suchen, die sich in einem lokalen Datenspeicher befinden.

**Benötigte Zeit:** Für diese Konfiguration benötigen Sie maximal 15 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Für die Durchführung dieses Schnellstarts benötigen Sie Folgendes:

|Anforderung  |Beschreibung  |
|---------|---------|
|**Ein unterstützendes Abonnement**     |  Sie benötigen ein Abonnement, das [**Azure Information Protection-Plan 1 oder -Plan 2**](https://azure.microsoft.com/pricing/details/information-protection/) umfasst. </br></br>Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.       |
|**Client installiert**    |   Auf Ihrem Computer muss der klassische Client oder der Client für einheitliche Bezeichnungen installiert sein. </br></br>– Um den Client für einheitliche Bezeichnungen zu installieren, navigieren Sie auf der Azure Information Protection-Seite zum [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018) und laden **AzInfoProtection_UL.exe** herunter. </br>– Zum Bereitstellen des klassischen AIP-Clients eröffnen Sie ein Supportticket, um Zugriff auf den Download zu erhalten.       |
|**SQL Server Express**     | SQL Server Express muss ebenfalls auf Ihrem Computer installiert sein. </br></br> Wechseln Sie zur Installation zum [Microsoft Download Center](https://www.microsoft.com/sql-server/sql-server-editions-express), und wählen Sie unter der Option „Express“ **Jetzt herunterladen** aus. Wählen Sie im Installationsprogramm den Installationstyp **Standard** aus.        |
|**Azure AD**     |  Ihr Domänenkonto muss mit Azure AD synchronisiert sein. </br></br>Wenn Sie sich bezüglich des Kontos nicht sicher sind, wenden Sie sich an einen Ihrer Systemadministratoren.      |
|**SharePoint-Zugriff**     | Um eine SharePoint-Überprüfung zu ermöglichen, benötigen Sie Zugriff auf und Berechtigungen für Ihre SharePoint-Richtlinie. |
| | |

## <a name="prepare-a-test-folder-and-file"></a>Vorbereiten eines Testordners und einer Testdatei

Führen Sie als ersten Test, um zu bestätigen, dass der Scanner ausgeführt wird, folgende Schritte durch:

1. Erstellen Sie einen neuen Ordner auf einer zugänglichen Netzwerkfreigabe. Nennen Sie diesen Ordner z. B. **TestScanner**.

1. Erstellen und speichern Sie ein Word-Dokument in diesem Ordner, das den Text **Credit card: 4242-4242-4242-4242** enthält.

## <a name="permission-users-to-scan-sharepoint-repositories"></a>Berechtigung für Benutzer zum Überprüfen von SharePoint-Repositorys

Um den Scanner für mehrere SharePoint-Repositorys zu verwenden, geben Sie die Website-URL an, damit Azure Information Protection alle zu dieser URL gehörenden Websites ermittelt und überprüft.

Um repositoryübergreifende Überprüfungen zu ermöglichen, fügen Sie die folgenden SharePoint-Berechtigungen dem Benutzer hinzu, der die Überprüfung durchführen soll:

1. Öffnen Sie SharePoint, und wählen Sie nacheinander **Berechtigungsrichtlinie** und **Richtlinienstufe für Berechtigungen hinzufügen** aus.

    ![Erstellen einer neuen Richtlinienstufe für Berechtigungen für einen bestimmten Benutzer](./media/aip-quick-set-sp-permissions.png)

1. Wählen Sie unter **Berechtigungen der Websitesammlung** die Option **Websitesammlungsauditor** aus.

1. Wählen Sie unter **Berechtigungen** die Option **Erteilen** für **Anwendungsseiten anzeigen** aus, und **speichern** Sie Ihre Änderungen.  

    ![Auswählen von Websitesammlungsauditor und Berechtigungsoptionen für einen bestimmten Benutzer](./media/aip-quick-set-site-permissions.png)

1. Klicken Sie nach dem Bestätigen Ihrer Änderungen in der angezeigten Meldung **Richtlinie für Webanwendung** auf **OK**.

1. Fügen Sie auf der Seite **Benutzer hinzufügen** im Feld **Benutzer auswählen** den Benutzer hinzu, der die Überprüfung ausführen soll. Wählen Sie unter **Berechtigungen auswählen** die Option **Websitesammlung** aus, und klicken Sie dann auf **Fertig stellen**, um dem hinzugefügten oder ausgewählten Benutzer die erstellten Berechtigungen zu erteilen.

    ![Optionen beim Hinzufügen eines Benutzers zu neuen Berechtigungen](./media/aip-quick-set-user-permissions.png)

## <a name="configure-a-profile-for-the-scanner"></a>Konfigurieren eines Profils für den Scanner

Bevor Sie den Scanner installieren, erstellen Sie im Azure-Portal ein Profil dafür. Dieses Profil enthält Scannereinstellungen sowie Speicherorte der zu scannenden Datenrepositorys.

1. Öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal). Navigieren Sie anschließend zum Bereich **Azure Information Protection**.

    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

1. Suchen Sie im linken Bereich die **Scanneroptionen**, und klicken Sie auf **Profile**.

1. Klicken Sie im Bereich **Azure Information Protection – Profile** auf die Option **Hinzufügen**:

    :::image type="content" source="media/scanner-add-profile.png" alt-text="Hinzufügen eines Profils für den Azure Information Protection-Scanner":::

1. Geben Sie im Bereich **Neues Profil hinzufügen** einen Namen für den Scanner ein, der zum Erkennen der Konfigurationseinstellungen und der Datenrepositorys verwendet wird, die überprüft werden sollen. Für diese Schnellstartanleitung können Sie z.B. **Schnellstart** eingeben. Diesen Profilnamen müssen Sie angeben, wenn Sie den Scanner später installieren.

    Optional können Sie eine Beschreibung für administrative Zwecke eingeben, damit Sie den Profilnamen des Scanners leichter erkennen.

1. Suchen Sie den Abschnitt **Richtlinienerzwingung**, und wählen Sie für diese Schnellstartanleitung nur eine Einstellung aus: Wählen Sie für **Erzwingen** die Option **Aus**. Klicken Sie dann auf **Speichern**, aber schließen Sie den Bereich nicht.

    Die Einstellungen konfigurieren den Scanner so, dass eine einmalige Ermittlung aller Dateien in Ihrem angegebenen Datenrepository durchgeführt wird. Bei dieser Überprüfung wird nach allen bekannten vertraulichen Informationstypen gesucht. Sie müssen dabei nicht zuerst Ihre Azure Information Protection-Bezeichnungen oder Einstellungen konfigurieren.

1. Nachdem Sie das Profil erstellt und gespeichert haben, können Sie zur Option **Repositorys konfigurieren** zurückkehren, um Ihren Netzwerkordner als den Datenspeicher anzugeben, der überprüft werden soll.

    Klicken Sie im Bereich **Neues Profil hinzufügen** auf die Option **Repositorys konfigurieren**, um das den Bereich **Repositorys** zu öffnen:

    :::image type="content" source="./media/scanner-repositories-bar.png" alt-text="Hinzufügen eines Profils für den Azure Information Protection-Scanner":::

1. Klicken Sie im Bereich **Repositorys** auf die Option **Hinzufügen**:

    :::image type="content" source="media/scanner-repository-add.png" alt-text="Hinzufügen eines Profils für den Azure Information Protection-Scanner":::

1. Geben Sie im Bereich **Repository** den Ordner an, den Sie zuvor erstellt haben. Beispiel: `\\server\TestScanner`

    Behalten Sie für die verbleibenden Einstellungen in diesem Bereich die vorhandenen **Profilstandardwerte** bei. Das bedeutet, dass das Datenrepository die Einstellungen vom Scannerprofil erbt.

    Wählen Sie **Speichern** aus.

1. Wenn Sie zum Bereich **Azure Information Protection – Profile** zurückkehren, werden dort jetzt Ihr Profilname sowie die Spalte **ZEITPLAN** mit der Einstellung **Manuell** und die leere Spalte **ERZWINGEN** angezeigt.

    Die Spalte **KNOTEN** zeigt **0** an, weil Sie die Überprüfung für dieses Profil noch nicht installiert haben.

Jetzt können Sie den Scanner mit dem Scannerprofil installieren, das Sie erstellt haben.

## <a name="install-the-scanner"></a>Installieren der Überprüfung

1. Starten Sie eine PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

1. Verwenden Sie den folgenden Befehl, um den Scanner zu installieren und dabei den Namen Ihrer Netzwerkfreigabe sowie den Profilnamen anzugeben, den Sie im Azure-Portal gespeichert haben:

    ```ps
    Install-AIPScanner -SqlServerInstance <your network share name>\SQLEXPRESS -Profile <profile name>
    ```

    Wenn Sie aufgefordert werden, geben Sie Ihre Anmeldeinformationen für den Scanner im Format \<domain\user name> und dann Ihr Kennwort an.

## <a name="start-the-scan-and-confirm-it-finished"></a>Starten der Überprüfung und Überprüfen des erfolgreichen Abschlusses

1. Im Azure-Portal aktualisieren Sie den Bereich **Azure Information Protection – Profile**. In der Spalte **KNOTEN** wird jetzt **1** angezeigt.

1. Wählen Sie Ihren Profilnamen und dann die Option **Jetzt überprüfen** aus:

    :::image type="content" source="media/scanner-scan-now.png" alt-text="Hinzufügen eines Profils für den Azure Information Protection-Scanner":::

    Wenn diese Option nicht verfügbar ist, nachdem Sie Ihr Profil ausgewählt haben, ist die Überprüfung nicht mit Azure Information Protection verbunden. Überprüfen Sie die Konfiguration und die Internetkonnektivität.

1. Es ist nur eine kleine Datei zu untersuchen, daher erfolgt diese erste Testüberprüfung schnell:

    Warten Sie, bis die Werte für die Spalten **LETZTE ÜBERPRÜFUNGSERGEBNISSE** und **LETZTE ÜBERPRÜFUNG (ENDZEIT)** angezeigt werden.

> [!TIP]
> Alternativ gilt für den Scanner des klassischen Clients Folgendes:
>
> Überprüfen Sie das lokale Ereignisprotokoll **Anwendungen und Dienste**, **Azure Information Protection**. Bestätigen Sie die ID **911** des Informationsereignisses für den Prozess **MSIP.Scanner**. Der Ereignisprotokolleintrag enthält darüber hinaus eine Zusammenfassung der Ergebnisse der Überprüfung.
>
## <a name="see-detailed-results"></a>Anzeigen detaillierter Ergebnisse

Suchen Sie im Datei-Explorer die Scannerberichte unter **%*localappdata*%\Microsoft\MSIP\Scanner\Reports**. Öffnen Sie die detaillierten Berichtsdatei im **CSV**-Format.

In Excel gilt Folgendes:

- Die ersten beiden Spalten zeigen Ihr Datenspeicherrepository und den Dateinamen an.
- Beim Durchgehen der Spalten werden Sie eine Spalte mit dem Namen **Name des Informationstyps** sehen – die Spalte, die für Sie von großem Interesse sein wird.

    Für unseren ersten Test wird **Kreditkartennummer** angezeigt, eine von vielen Typen vertraulicher Informationen, die der Scanner erkennen kann.

## <a name="scan-your-own-data"></a>Überprüfen eigener Daten

1. Bearbeiten Sie Ihr Scannerprofil, und fügen Sie ein neues Datenrepository hinzu, geben Sie jedoch diesmal Ihren eigenen lokalen Datenspeicher an, der auf vertrauliche Informationen geprüft werden soll.

    Geben Sie eine Netzwerkfreigabe (UNC-Pfad) oder eine SharePoint Server-URL für eine SharePoint-Website oder -Bibliothek an.

    Beispiel:

    - **Für eine Netzwerkfreigabe**: `\\NAS\HR`
    - **Für einen SharePoint-Ordner**: `http://sp2016/Shared Documents`

1. Starten Sie den Scanner erneut.

    Stellen Sie im Bereich **Azure Information Protection – Profile** sicher, dass Ihr Profil ausgewählt ist, und klicken Sie dann auf die Option **Jetzt scannen**:

    :::image type="content" source="media/scanner-scan-now.png" alt-text="Hinzufügen eines Profils für den Azure Information Protection-Scanner":::

1. Wenn die Überprüfung abgeschlossen ist, sehen Sie sich die neuen Ergebnisse an.

    Die Dauer dieser Überprüfung hängt davon ab, wie viele Dateien in Ihrem Datenspeicher vorhanden sind, wie groß diese Dateien sind sowie vom Typ der Datei.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

In einer Produktionsumgebung würden Sie den Scanner auf einem Windows-Server über ein Dienstkonto ausführen, das im Hintergrund beim Azure Information Protection-Dienst authentifiziert wird. Außerdem würden Sie eine Unternehmensversion von SQL Server verwenden und wahrscheinlich mehrere Datenrepositorys angeben.

Um Ressourcen zu bereinigen und Ihr System auf die Produktionsbereitstellung vorzubereiten, führen Sie in der PowerShell-Sitzung den folgenden Befehl aus, um den Scanner zu deinstallieren:

```ps
Uninstall-AIPScanner
```

Starten Sie den Computer neu.

Mit diesem Befehl werden die folgenden Elemente nicht entfernt, weshalb Sie sie manuell entfernen müssen, wenn Sie sie nach Abschluss dieser Schnellstartanleitung nicht mehr benötigen:

- Die SQL Server-Datenbank, die bei der Installation des Azure Information Protection-Scanners mit dem Cmdlet „Install-AIPScanner“ erstellt wurde:

    - Für den klassischen Client: **AIPScanner_\<profile>**
    - Für den Client für einheitliche Bezeichnungen: **AIPScannerUL_\<profile_name>**

- Die Scannerberichte unter **%*localappdata*%\Microsoft\MSIP\Scanner\Reports**.

- Die Zuweisung des Benutzerrechts **Als Dienst anmelden**, das Ihrem Domänenkonto für Ihren lokalen Computer erteilt wurde

## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung wird die Mindestkonfiguration beschrieben, sodass Sie schnell sehen können, wie mit der Überprüfung in lokalen Datenspeichern nach vertraulichen Informationen gesucht werden kann. Informationen zum Installieren des Scanners in einer Produktionsumgebung finden Sie unter [Bereitstellen des Azure Information Protection-Scanners zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md).

Wenn Sie die Dateien klassifizieren und schützen möchten, die vertrauliche Informationen enthalten, müssen Sie Bezeichnungen für die automatische Klassifizierung und den automatischen Schutz konfigurieren:

**Für den klassischen Client**:

- [Gewusst wie: Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)
- [How to configure a label for Rights Management protection (Konfigurieren einer Bezeichnung für Rights Management-Schutz)](configure-policy-protection.md)

**Für den Client für einheitliche Bezeichnungen**:

- [Automatisches Anwenden einer Vertraulichkeitsbezeichnung auf Inhalte](/microsoft-365/compliance/apply-sensitivity-label-automatically)
- [Einschränken des Zugriffs auf Inhalte mithilfe der Verschlüsselung in Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/encryption-sensitivity-labels)