---
title: Installieren und Konfigurieren des Azure Information Protection (AIP) Scanner
description: Anweisungen zum Installieren und Konfigurieren des Azure Information Protection Scanners zum ermitteln, klassifizieren und schützen von Dateien in Daten speichern.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 02/01/2021
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ROBOTS: NOINDEX
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 46655ef7da2d8670ef3fced105b3d471bb05a8f9
ms.sourcegitcommit: caf2978ab03e4893b59175ce753791867793dcfe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2021
ms.locfileid: "100524760"
---
# <a name="configuring-and-installing-the-azure-information-protection-classic-scanner"></a>Konfigurieren und Installieren des Azure Information Protection klassischen Scanner

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 *
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified-Bezeichnungs Client finden Sie unter [Installieren und Konfigurieren des AIP Unified-Beschriftungs Scanners](deploy-aip-scanner-configure-install.md). *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Vergewissern Sie sich vor dem Konfigurieren und Installieren des Azure Information Protection Scanners, dass Ihr System die [erforderlichen Voraussetzungen](deploy-aip-scanner-prereqs.md)erfüllt.

Wenn Sie fertig sind, fahren Sie mit den folgenden Schritten fort:

1. [Konfigurieren des Scanners im Azure-Portal](#configure-the-scanner-in-the-azure-portal)

1. [Installieren der Überprüfung](#install-the-scanner)

1. [Abrufen eines Azure AD-Tokens für die Überprüfung](#get-an-azure-ad-token-for-the-scanner)

1. [Konfigurieren der Überprüfung zum Anwenden von Klassifizierung und Schutz](#configure-the-scanner-to-apply-classification-and-protection)

Führen Sie die folgenden zusätzlichen Konfigurationsverfahren aus, die für Ihr System erforderlich sind:

|Verfahren  |BESCHREIBUNG  |
|---------|---------|
|[Ändern der zu schützenden Dateitypen](#change-which-file-types-to-protect) |Möglicherweise möchten Sie verschiedene Dateitypen Scannen, klassifizieren oder schützen als die Standardwerte. Weitere Informationen finden Sie unter [AIP-Scanvorgang](deploy-aip-scanner.md#aip-scanning-process). |
|[Aktualisieren Ihres Scanners](#upgrading-your-scanner) | Aktualisieren Sie Ihren Scanner, um die neuesten Features und Verbesserungen zu nutzen.|
|[Bearbeiten von Datenrepository-Einstellungen in einem Massen Vorgang](#editing-data-repository-settings-in-bulk)| Verwenden Sie Import-und Exportoptionen, um für mehrere Daten Depots Massen Änderungen vorzunehmen.|
|[Verwenden des Scanners mit alternativen Konfigurationen](#using-the-scanner-with-alternative-configurations)| Verwenden Sie den Scanner, ohne Bezeichnungen mit Bedingungen zu konfigurieren. |
|[Optimieren der Leistung](#optimizing-scanner-performance)| Leitfaden zur Optimierung der Leistung des Scanners|
| | |

Weitere Informationen finden Sie auch [in der Liste der Cmdlets für den Scanner](#list-of-cmdlets-for-the-scanner).

## <a name="configure-the-scanner-in-the-azure-portal"></a>Konfigurieren des Scanners im Azure-Portal

Bevor Sie die Überprüfung installieren oder von einer älteren Version der Überprüfung mit allgemeiner Verfügbarkeit aktualisieren, erstellen Sie einen Cluster-und Inhalts Scanauftrag für die Überprüfung in der Azure-Portal.

Konfigurieren Sie anschließend den Auftrag für Cluster-und Inhalts Scans mit den Überprüfungs Einstellungen und den zu überprüfenden Daten Depots.

So konfigurieren Sie Ihren Scanner:

1. [Melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), und navigieren Sie zum Bereich **Azure Information Protection** .

    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

1. Suchen Sie die Menü Optionen **Scanner** , und wählen Sie **Cluster** aus.

1. Wählen Sie im Bereich **Azure Information Protection-Cluster** die Option **Hinzufügen** aus:

    :::image type="content" source="media/scanner-add-profile.png" alt-text="Inhalts Überprüfungs Auftrag zum Azure Information Protection Scanner hinzufügen":::

1. Im Bereich **neuen Cluster hinzufügen** :

    1. Geben Sie einen aussagekräftigen Namen für die Überprüfung an. Dieser Name wird verwendet, um die Konfigurationseinstellungen des Scanners und die zu überprüfenden Daten Depots zu identifizieren.

        Sie können beispielsweise **Europa** angeben, um den geografischen Standort der Datenrepositorys anzugeben, für die Ihr Scanner zuständig ist. Wenn Sie den Scanner später installieren oder aktualisieren, müssen Sie denselben Cluster Namen angeben.

    2. Optional können Sie eine Beschreibung für administrative Zwecke angeben, damit Sie den Cluster Namen des Scanners leichter identifizieren können.

    3. Wählen Sie **Speichern**.
1. Suchen Sie die Menü Optionen **Scanner** , und wählen Sie **Inhalts Scanaufträge** aus.
1. Wählen Sie im Bereich **Azure Information Protection-Inhalts Scanaufträge** die Option **Hinzufügen** aus.

1. Konfigurieren Sie für diese Erstkonfiguration die folgenden Einstellungen, und wählen Sie dann **Speichern** aus, aber schließen Sie den Bereich nicht:

    |`Section`  |Einstellungen  |
    |---------|---------|
    |**Einstellungen für den Content Scan-Auftrag**     |    - **Zeitplan**: behalten Sie den Standardwert **manuell** bei. </br>- **Zu ermittelnde Informationstypen**: **nur in Richtlinie** ändern </br>- **Repository konfigurieren**: Konfigurieren Sie zu diesem Zeitpunkt nicht, da der Inhalts Überprüfungs Auftrag zuerst gespeichert werden muss.         |
    |**Vertraulichkeitsrichtlinie**     | - **Erzwingen**: SELECT **Off** </br>- Bezeichnungs **Dateien basierend auf dem Inhalt**: behalten Sie die Standardeinstellung **bei** . </br>- **Standard Bezeichnung**: Standardwert der Standard **Richtlinie für Richtlinie** beibehalten </br>- **Dateien** neu bezeichnen: Standardwert " **aus** " beibehalten        |
    |**Konfigurieren von Datei Einstellungen**     | - **"Datum geändert", "zuletzt geändert" und "geändert von**" beibehalten: behalten Sie die Standardeinstellung **bei** . </br>- **Zu überprüfende Dateitypen**: Standard Dateitypen für **Ausschluss** beibehalten </br>- **Standard Besitzer**: behalten Sie die Standardeinstellung **Scanner-Konto** bei.        |
    | | |

1. Nachdem der Auftrag für die Inhalts Überprüfung erstellt und gespeichert wurde, können Sie zur Option " **Depots konfigurieren** " zurückkehren, um die Datenspeicher anzugeben, die gescannt werden sollen.

    Geben Sie UNC-Pfade und SharePoint-Server-URLs für lokale SharePoint-Dokument Bibliotheken und-Ordner an.

    > [!NOTE]
    > SharePoint Server 2019, SharePoint Server 2016 und SharePoint Server 2013 werden für SharePoint unterstützt. Ferner wird SharePoint Server 2010 unterstützt, wenn Sie über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.
    >
    Wenn Sie den ersten Datenspeicher hinzufügen möchten, wählen Sie im Bereich **neuen Inhalts Überprüfungs Auftrag hinzufügen** die Option **Repository konfigurieren** aus, um den Bereich **Depots** zu öffnen:

    :::image type="content" source="media/scanner-repositories-bar.png" alt-text="Konfigurieren von Datenrepositorys für den Azure Information Protection-Scanner":::

1. Klicken Sie im Bereich **Repositorys** auf die Option **Hinzufügen**:

    :::image type="content" source="media/scanner-repository-add.png" alt-text="Hinzufügen von Data Repository für den Azure Information Protection Scanner":::

1. Geben Sie im Bereich **Repository** den Pfad für das Datenrepository an, und klicken Sie dann auf **Speichern**.

    Beispiel: 

    - Verwenden Sie für eine Netzwerkfreigabe `\\Server\Folder` . 
    - Verwenden Sie für eine SharePoint-Bibliothek `http://sharepoint.contoso.com/Shared%20Documents/Folder` .

    > [!NOTE]
    > Platzhalter und WebDav-Speicherorte werden nicht unterstützt.
    >     

    Verwenden Sie die folgende Syntax, wenn Sie SharePoint-Pfade hinzufügen:
    
    |Pfad  |Syntax  |
    |---------|---------|
    |**Stammpfad**     | `http://<SharePoint server name>` </br></br>Scannt alle Websites, einschließlich sämtlicher Site Sammlungen, die für den scannerbenutzer zulässig sind. </br>Erfordert [zusätzliche Berechtigungen](quickstart-findsensitiveinfo.md#permission-users-to-scan-sharepoint-repositories) zum automatischen ermitteln von Stamm Inhalten        |
    |**Bestimmte SharePoint-unter Website oder-Sammlung**     | Einer der folgenden: </br>- `http://<SharePoint server name>/<subsite name>` </br>- `http://SharePoint server name>/<site collection name>/<site name>` </br></br>Erfordert [zusätzliche Berechtigungen](quickstart-findsensitiveinfo.md#permission-users-to-scan-sharepoint-repositories) zum automatischen ermitteln von Website Sammlungs Inhalten         |
    |**Bestimmte SharePoint-Bibliothek**     | Einer der folgenden: </br>- `http://<SharePoint server name>/<library name>` </br>- `http://SharePoint server name>/.../<library name>`       |
    |**Bestimmter SharePoint-Ordner**     | `http://<SharePoint server name>/.../<folder name>`        |
    | | |

    Für die restlichen Einstellungen in diesem Bereich sollten Sie diese nicht für diese anfängliche Konfiguration ändern, sondern als Standardwert für den **inhaltscanauftrag** beibehalten. Die Standardeinstellung bedeutet, dass das Datenrepository die Einstellungen vom Inhalts Überprüfungs Auftrag erbt.


1. Wenn Sie ein weiteres Datenrepository hinzufügen möchten, wiederholen Sie die Schritte 8 und 9.

1. Schließen Sie den Bereich " **Depots** " und den Bereich " **Inhalts Überprüfungs Auftrag** ".

Im Bereich **Azure Information Protection Inhalts** Überprüfung wird der Name Ihres Inhalts Scans angezeigt, und die Spalte " **Zeitplan** " zeigt " **manuell** " an, und die Spalte " **erzwingen** " ist leer.

Nun können Sie den Scanner mit dem von Ihnen erstellten Inhalts Überprüfungs Auftrag installieren. Fahren Sie mit [der Installation des Scanners](#install-the-scanner)fort.

## <a name="install-the-scanner"></a>Installieren der Überprüfung

Nachdem Sie [den Azure Information Protection Scanner im Azure-Portal konfiguriert](#configure-the-scanner-in-the-azure-portal)haben, führen Sie die folgenden Schritte aus, um die Überprüfung zu installieren:

1. Melden Sie sich bei dem Windows Server-Computer an, auf dem die Überprüfung ausgeführt werden soll. Verwenden Sie ein Konto mit lokalen Administratorrechten und den Berechtigungen zum Schreiben in die SQL Server-Masterdatenbank.

    > [!IMPORTANT]
    > Weitere Informationen finden Sie unter [Voraussetzungen für die Installation und Bereitstellung der Azure Information Protection Scanner](deploy-aip-scanner-prereqs.md).
    >

1. Starten Sie eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

1. Führen Sie das Cmdlet [install-aipscanner](/powershell/module/azureinformationprotection/Install-AIPScanner) aus, und geben Sie dabei die SQL Server Instanz an, auf der eine Datenbank für den Azure Information Protection Scanner erstellt werden soll, und den Namen des scannerclusters, den Sie im vorherigen Abschnitt angegeben haben:

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Profile <cluster name>
    ```

    Beispiele, in denen der Profilname **Europa** verwendet wird:

    - Für eine Standardinstanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1 -Profile Europe`

    - Für eine benannte Instanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER -Profile Europe`

    - Für SQL Server Express: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS -Profile Europe`

    Wenn Sie dazu aufgefordert werden, geben Sie die Anmelde Informationen für das Überprüfungs Dienst Konto ( `\<domain\user name>` ) und das Kennwort an.

1. Vergewissern Sie sich, dass der Dienst jetzt mithilfe der Dienste **Verwaltung** installiert ist  >  .

    Der installierte Dienst heißt **Azure Information Protection-Überprüfung** und ist für die Ausführung mithilfe des von Ihnen erstellten Überprüfungsdienstkontos konfiguriert.

Nachdem Sie den Scanner installiert haben, müssen Sie [ein Azure AD Token für das](#get-an-azure-ad-token-for-the-scanner) Überprüfungs Dienst Konto für die Authentifizierung erhalten, damit die Überprüfung unbeaufsichtigt ausgeführt werden kann.

## <a name="get-an-azure-ad-token-for-the-scanner"></a>Abrufen eines Azure AD-Tokens für die Überprüfung

Ein Azure AD Token ermöglicht es dem Scanner, sich beim Azure Information Protection-Dienst zu authentifizieren.

So erhalten Sie ein Azure AD Token:

1. Kehren Sie zum Azure-Portal zurück, um zwei Azure AD Anwendungen zu erstellen und ein Zugriffs Token für die Authentifizierung anzugeben. Mit diesem Token kann der Scanner nicht interaktiv ausgeführt werden.

    Weitere Informationen finden Sie unter [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](./rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection).

2. Wenn Ihrem Überprüfungs Dienst Konto auf dem Windows Server-Computer die Berechtigung zum **lokalen anmelden** für die Installation erteilt wurde, melden Sie sich mit diesem Konto an, und starten Sie eine PowerShell-Sitzung.

    Führen Sie [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) aus, und geben Sie die Werte an, die Sie aus dem vorherigen Schritt kopiert haben:

    ```PowerShell
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application> -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application>
    ```

    Wenn Sie dazu aufgefordert werden, geben Sie das Kennwort für Ihr Azure AD-Dienstkonto an, und klicken Sie dann auf **Akzeptieren**.

    Beispiel:

    ```PowerShell
    Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f").token | clip
    Acquired application access token on behalf of the user
    ```

> [!TIP]
> Wenn Ihrem Überprüfungs Dienst Konto die Berechtigung " **Lokal anmelden** " nicht erteilt werden kann, [Geben Sie an, und verwenden Sie den tokenparameter für "Set-aipauthentication](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)".
>

Der Scanner verfügt jetzt über ein Token zum Authentifizieren bei Azure AD, das ein Jahr, zwei Jahre oder nie ist, gemäß ihrer Konfiguration der **Web-App/API** in Azure AD.

Wenn das Token abgelaufen ist, müssen Sie die Schritte 1 und 2 wiederholen.

Nun können Sie den ersten Scanvorgang im Ermittlungsmodus ausführen. Weitere Informationen finden Sie unter [Ausführen eines Ermittlungs Zyklen und Anzeigen von Berichten für die](deploy-aip-scanner-manage.md#run-a-discovery-cycle-and-view-reports-for-the-scanner)Überprüfung.

Wenn Sie bereits eine Ermittlungs Überprüfung ausgeführt haben, fahren Sie mit [Konfigurieren des Scanners zum Anwenden der Klassifizierung und des Schutzes](#configure-the-scanner-to-apply-classification-and-protection)fort.

## <a name="configure-the-scanner-to-apply-classification-and-protection"></a>Konfigurieren der Überprüfung zum Anwenden von Klassifizierung und Schutz

Mit den Standardeinstellungen wird die Überprüfung so konfiguriert, dass Sie einmalig ausgeführt wird, und im Bericht Erstellungs Modus.

Um diese Einstellungen zu ändern, bearbeiten Sie den Auftrag für die Inhalts Überprüfung:

1. Wählen Sie im Azure-Portal im Bereich **Azure Information Protection-Inhalts Scanaufträge** den Auftrag Cluster und Inhalts Überprüfung aus, um ihn zu bearbeiten.

2. Ändern Sie im Bereich Inhalts Überprüfungs Auftrag die folgenden Einstellungen, und wählen Sie dann **Speichern** aus:

   - Im Abschnitt **Content Scan Job** : Ändern des **Zeitplans** in **Always**
   - Aus dem Abschnitt **Sensitivitäts Richtlinie** : Ändern von **erzwingen** **in ein**

    > [!TIP]
    > Möglicherweise möchten Sie andere Einstellungen in diesem Bereich ändern, z. b. ob Dateiattribute geändert werden und ob der Scanner Dateien neu bezeichnen kann. Weitere Informationen zu den einzelnen Konfigurationseinstellungen finden Sie in der Popuphilfe mit Informationen.

3. Notieren Sie sich die aktuelle Uhrzeit, und starten Sie die Überprüfung erneut über den Bereich **Azure Information Protection-Inhalts Scanaufträge** :

    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)

    Alternativ können Sie den folgenden Befehl in der PowerShell-Sitzung ausführen:

    ```PowerShell
    Start-AIPScan
    ```

4. Überwachen Sie das Ereignisprotokoll auf den Informationstyp **911** und den letzten Zeitstempel, um Berichte zu den gekennzeichneten Dateien anzuzeigen, welche Klassifizierung angewendet wurde und ob der Schutz angewendet wurde.

    Überprüfen Sie die Berichte auf Details, oder verwenden Sie die Azure-Portal, um diese Informationen zu finden.

Der Scanner ist jetzt für die kontinuierliche Ausführung geplant. Wenn die Überprüfung alle konfigurierten Dateien durchläuft, wird automatisch ein neuer Zeitraum gestartet, sodass neue und geänderte Dateien ermittelt werden.

## <a name="change-which-file-types-to-protect"></a>Ändern der zu schützenden Dateitypen

Standardmäßig schützt der AIP-Scanner nur Office-Dateitypen und PDF-Dateien. Bearbeiten Sie die Registrierung wie folgt, um dieses Verhalten zu ändern, z. b. zum Konfigurieren der Überprüfung, um alle Dateitypen zu schützen, ebenso wie der Client, oder um bestimmte zusätzliche Dateitypen zu schützen:

- Geben Sie die zusätzlichen Dateitypen an, die Sie schützen möchten.
- Geben Sie den Typ des Schutzes an, den Sie anwenden möchten (System eigen oder generisch).

Allgemeiner Schutz wird in dieser Dokumentation für Entwickler als „PFile“ bezeichnet.

So richten Sie die unterstützten Dateitypen mit dem Client aus, wobei alle Dateien automatisch durch nativen oder generischen Schutz geschützt werden:

1. Angeben:

    - Der Platzhalter `*` als Registrierungsschlüssel.
    - `Encryption` als Wert (REG_SZ)
    - `Default` als Wertdaten

1. Überprüfen Sie, ob die Schlüssel **msipc** und **File Protection** vorhanden sind. Erstellen Sie Sie manuell, wenn dies nicht der Fall ist, und erstellen Sie dann einen Unterschlüssel für jede Dateinamenerweiterung.

    Damit der Scanner z. b. TIFF-Bilder zusätzlich zu Office-Dateien und-PDF-Dateien schützen kann, sieht die Registrierung in etwa wie folgt aus, nachdem Sie sie bearbeitet haben:

    ![Bearbeiten der Registrierung für die Überprüfung zum Anwenden von Schutz](./media/editregistry-scanner.png)

    > [!NOTE]
    > Als Bilddatei unterstützen TIFF-Dateien den systemeigenen Schutz und die resultierende Dateinamenerweiterung **. ptiff**.
    >

    Geben Sie für Dateien, die den nativen Schutz nicht unterstützten, die Erweiterung als einen neuen Schlüssel und **PFILE** für den generischen Schutz an. Die resultierende Dateinamenerweiterung für die geschützte Datei lautet " **Pfile**".

Eine Liste mit Text-und Bild Dateitypen, die auf ähnliche Weise systemeigenen Schutz unterstützen, aber in der Registrierung angegeben werden müssen, finden Sie [unter Unterstützte Dateitypen für Klassifizierung und Schutz](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection).

## <a name="upgrading-your-scanner"></a>Aktualisieren Ihres Scanners

Wenn Sie den Scanner bereits installiert haben und ein Upgrade durchführen möchten, finden Sie weitere Informationen unter [Aktualisieren der Azure Information Protection Scanner](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).

[Konfigurieren](deploy-aip-scanner-configure-install-classic.md) und verwenden Sie dann wie gewohnt [Ihren Scanner](deploy-aip-scanner-manage-classic.md) , und überspringen Sie die Schritte zur Installation des Scanners.

>[!NOTE]
> Wenn Sie über eine Version des Scanners verfügen, die älter als 1.48.204.0 ist und Sie nicht zur Aktualisierung bereit sind, finden Sie weitere Informationen unter Bereitstellen [vorheriger Versionen des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner-previousversions.md).

## <a name="editing-data-repository-settings-in-bulk"></a>Bearbeiten von Datenrepository-Einstellungen in einem Massen Vorgang

Verwenden Sie die Schaltflächen **exportieren** und **importieren** , um Änderungen für Ihren Scanner in mehreren Depots durchführen zu können.

Auf diese Weise müssen Sie die gleichen Änderungen nicht mehrmals manuell im Azure-Portal vornehmen.

Wenn Sie z. b. einen neuen Dateityp in mehreren SharePoint-Daten Depots haben, können Sie die Einstellungen für diese Depots in einem Massen Vorgang aktualisieren.

So führen Sie Massen Änderungen in mehreren Depots durch:

1. Wählen Sie im Bereich für die Azure-Portal im Bereich " **Depots** " die Option **exportieren** aus. Beispiel:

    :::image type="content" source="media/export-scanner-repositories.png" alt-text="Exportieren der Datenrepositoryeinstellungen für den Scanner":::

1. Bearbeiten Sie die exportierte Datei manuell, um die Änderung vorzunehmen.

1. Verwenden Sie die **Import** -Option auf der gleichen Seite, um die Aktualisierungen in ihren Depots wieder zu importieren.

## <a name="using-the-scanner-with-alternative-configurations"></a>Verwenden der Überprüfung mit alternativen Konfigurationen

Der Azure Information Protection Scanner sucht in der Regel nach Bedingungen, die für ihre Bezeichnungen angegeben sind, um Ihre Inhalte nach Bedarf zu klassifizieren und zu schützen.

In den folgenden Szenarien kann der Azure Information Protection Scanner auch Ihre Inhalte Scannen und Bezeichnungen verwalten, ohne dass Bedingungen konfiguriert sind:

- [Anwenden einer Standard Bezeichnung auf alle Dateien in einem Datenrepository](#apply-a-default-label-to-all-files-in-a-data-repository)
- [Alle benutzerdefinierten Bedingungen und bekannten sensiblen Informationstypen identifizieren](#identify-all-custom-conditions-and-known-sensitive-information-types)

### <a name="apply-a-default-label-to-all-files-in-a-data-repository"></a>Anwenden einer Standard Bezeichnung auf alle Dateien in einem Datenrepository

In dieser Konfiguration werden alle nicht gekennzeichneten Dateien im Repository mit der Standard Bezeichnung gekennzeichnet, die für das Repository oder den Inhaltsüberprüfungs Auftrag angegeben ist. Dateien werden ohne Untersuchung bezeichnet.

Konfigurieren Sie die folgenden Einstellungen:

- Bezeichnungs **Dateien basierend auf dem Inhalt**: auf **Off** festgelegt
- **Standard Bezeichnung**: Legen Sie auf **Custom** fest, und wählen Sie dann die zu verwendende Bezeichnung aus.

### <a name="identify-all-custom-conditions-and-known-sensitive-information-types"></a>Alle benutzerdefinierten Bedingungen und bekannten sensiblen Informationstypen identifizieren

Mit dieser Konfiguration können Sie vertrauliche Informationen, die Sie möglicherweise nicht bemerkt haben, auf Kosten der Scan Raten für den Scanner finden.

Legen Sie die zu **ermittelnden Informationstypen** auf **alle** fest.

Zum Identifizieren von Bedingungen und Informationstypen für die Bezeichnung verwendet der Scanner benutzerdefinierte Bedingungen, die für Bezeichnungen angegeben sind, sowie die Liste der Informationstypen, die zur Angabe für Bezeichnungen verfügbar sind, wie in der Azure Information Protection Richtlinie aufgeführt.

Weitere Informationen [finden Sie unter Schnellstart: finden Sie heraus, welche sensiblen Informationen Sie besitzen](quickstart-findsensitiveinfo.md).

## <a name="optimizing-scanner-performance"></a>Optimieren der Scanner-Leistung

> [!NOTE]
> Wenn Sie die Reaktionsfähigkeit des Scanner-Computers anstelle der Überprüfungs Leistung verbessern möchten, verwenden Sie eine erweiterte Client Einstellung, um [die Anzahl der von der Überprüfung verwendeten Threads einzuschränken](./rms-client/client-admin-guide-customizations.md#limit-the-number-of-threads-used-by-the-scanner).
>

Verwenden Sie die folgenden Optionen und Anleitungen, um die Leistung der Scanner zu optimieren:

|Option  |Beschreibung  |
|---------|---------|
|**Verwenden Sie eine schnelle und zuverlässige Netzwerkverbindung zwischen dem Überprüfungscomputer und dem überprüften Datenspeicher**     |  Platzieren Sie z. b. den Überprüfungs Computer im selben LAN oder vorzugsweise im selben Netzwerksegment wie der gescannte Datenspeicher. </br></br>Die Qualität der Netzwerkverbindung wirkt sich auf die Überprüfungs Leistung aus, da der Scanner zum Überprüfen der Dateien den Inhalt der Dateien auf den Computer überträgt, auf dem der Überprüfungs Dienst ausgeführt wird. </br></br>Durch das reduzieren oder eliminieren der Netzwerk Hops, die für die zu übertragenden Daten erforderlich sind, wird auch die Auslastung Ihres Netzwerks reduziert.      |
|**Achten Sie darauf, dass der überprüfende Computer verfügbare Prozessorressourcen aufweist**     | Die Untersuchung der Dateiinhalte und das Verschlüsseln und Entschlüsseln von Dateien sind prozessorintensive Aktionen. </br></br>Überwachen Sie die üblichen Überprüfungszyklen für die angegebenen Datenspeicher, um zu ermitteln, ob sich die Leistung der Überprüfung durch fehlende Prozessorressourcen beeinträchtigt.        |
|**Installieren mehrerer Instanzen des Scanners** | Der Azure Information Protection Scanner unterstützt mehrere Konfigurations Datenbanken auf derselben SQL Server-Instanz, wenn Sie einen benutzerdefinierten Cluster Namen (Profil) für die Überprüfung angeben. |
|**Erteilen spezifischer Rechte und Deaktivieren der Ebene mit niedriger Integrität**|Vergewissern Sie sich, dass das Dienst Konto, unter dem die Überprüfung ausgeführt wird, nur über die unter [Dienst Kontoanforderungen](deploy-aip-scanner-prereqs.md#service-account-requirements)dokumentierten Rechte verfügt </br></br>Konfigurieren Sie dann die [Erweiterte Client Einstellung](./rms-client/client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) , um die Ebene mit niedriger Integrität für die Überprüfung zu deaktivieren.|
|**Überprüfen Sie Ihre alternative Konfigurations Verwendung** |Die Überprüfung wird schneller ausgeführt, wenn Sie die [alternative Konfiguration](#using-the-scanner-with-alternative-configurations) verwenden, bei der eine Standardbezeichnung auf alle Dateien angewendet wird, ohne dass die Dateiinhalte überprüft werden. <br/></br>Die Überprüfung wird langsamer ausgeführt, wenn Sie die [alternative Konfiguration](#using-the-scanner-with-alternative-configurations) verwenden, bei der alle benutzerdefinierten Bedingungen und bekannten vertraulichen Informationstypen identifiziert werden.|
|**Überprüfungs Timeouts verringern** | Verringern Sie die Überprüfungs Timeouts mit [erweiterten Client Einstellungen](./rms-client/client-admin-guide-customizations.md#change-the-timeout-settings-for-the-scanner). Reduzierte Überprüfungs Timeouts bieten bessere Scan Raten und einen geringeren Speicherverbrauch. </br></br>**Hinweis**: das Verringern von Überprüfungs Timeouts bedeutet, dass einige Dateien möglicherweise ausgelassen werden.
| | |


### <a name="additional-factors-that-affect-performance"></a>Weitere Faktoren, die die Leistung beeinträchtigen

Weitere Faktoren, die sich auf die Scanner-Leistung auswirken, sind:

|Faktor  |BESCHREIBUNG  |
|---------|---------|
|**Lade-/Antwort-Zeiten**     |Die aktuellen Lade-und Antwortzeiten der Datenspeicher, die die zu überprüfenden Dateien enthalten, wirken sich auch auf die Leistung des Scanners aus.         |
|**Scanmodus** (Ermittlung/erzwingen)    | Der Ermittlungs Modus hat normalerweise eine höhere Scanrate als der Erzwingungs Modus. </br></br>Die Ermittlung erfordert eine einzelne Datei Leseaktion, während der Erzwingungs Modus Lese-und Schreib Aktionen erfordert.        |
|**Richtlinienänderungen**     |Die Leistung Ihres Scanners kann beeinträchtigt werden, wenn Sie Änderungen an den Bedingungen in der Azure Information Protection Richtlinie vorgenommen haben. </br></br>Der erste Scan Zyklus, bei dem der Scanner jede Datei überprüfen muss, dauert länger als nachfolgende Überprüfungszyklen, die standardmäßig nur neue und geänderte Dateien untersuchen. </br></br>Wenn Sie die Bedingungen ändern, werden alle Dateien erneut gescannt. Weitere Informationen finden Sie unter [erneutanup von Dateien](deploy-aip-scanner-manage-classic.md#rescanning-files).|
|**Regex-Konstruktionen**    | Die Leistung des Scanners ist von der Erstellung der Regex-Ausdrücke für benutzerdefinierte Bedingungen betroffen. </br></br> Überprüfen Sie Ihre regulären Ausdrücke für einen effizienten Musterabgleich, um eine hohe Arbeitsspeichernutzung und das Risiko von Timeouts (15 Minuten pro Datei) zu vermeiden. </br></br>Beispiel: </br>-Vermeiden [gieriger quantifiziererer](/dotnet/standard/base-types/quantifiers-in-regular-expressions) </br>-Verwenden Sie nicht Erfassungs Gruppen wie z. b. `(?:expression)` anstelle von. `(expression)`    |
|**Protokollebene**     |  Optionen auf Protokollebene umfassen **Debug**, **Info**, **Error** und **Off** für die scannerberichte.</br></br>- **Off** führt zu einer optimalen Leistung. </br>- Das **Debuggen** verlangsamt den Scanner erheblich und sollte nur zur Problembehandlung verwendet werden. </br></br>Weitere Informationen finden Sie beim Parameter *ReportLevel* für das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration).       |
|**Dateien, die gescannt werden**     |-Mit Ausnahme von Excel-Dateien werden Office-Dateien schneller gescannt als PDF-Dateien. </br></br>-Ungeschützte Dateien sind schneller zu scannen als geschützte Dateien. </br></br>-Die Überprüfung großer Dateien dauert offensichtlich länger als bei kleinen Dateien.         |
| | |

## <a name="list-of-cmdlets-for-the-scanner"></a>Auflisten der Cmdlets für die Überprüfung

In diesem Abschnitt werden die für den Azure Information Protection Scanner unterstützten PowerShell-Cmdlets aufgeführt.

> [!NOTE]
> Der Azure Information Protection Scanner wird vom Azure-Portal konfiguriert. Aus diesem Grund sind Cmdlets, die in früheren Versionen verwendet wurden, um Daten Depots und die Liste der überprüften Dateitypen zu konfigurieren, mittlerweile veraltet.
>

Zu den unterstützten Cmdlets für den Scanner gehören:

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus)

- [Import-aipscannerconfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Start-aipscandiagnostics](/powershell/module/azureinformationprotection/Start-AIPScanDiagnostics)

- [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan)

- ["Beendet-aipscan"](/powershell/module/azureinformationprotection/Stop-AIPScan)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)

- [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihren Scanner installiert und konfiguriert haben, können Sie mit [dem Scannen der Dateien](deploy-aip-scanner-manage.md)beginnen.

Siehe auch: bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner.md).

**Weitere Informationen**:

Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

Vielleicht Fragen Sie sich: [worin besteht der Unterschied zwischen der Windows Server-FCI und der Azure Information Protection Scanner?](faqs-classic.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).