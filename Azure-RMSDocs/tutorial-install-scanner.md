---
title: 'Tutorial: Installieren des Azure Information Protection-Scanners (AIP) für einheitliche Bezeichnungen'
description: Installieren Sie den Azure Information Protection-Scanner (AIP) für einheitliche Bezeichnungen, um vertrauliche Daten zu ermitteln, die in Ihren lokalen Netzwerkfreigaben gespeichert sind.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/09/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.service: information-protection
ms.custom: admin
ms.subservice: aiplabels
ms.openlocfilehash: 73bcb5e636b8a5e4456ad80f8435a27dfc898339
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97384773"
---
# <a name="tutorial-installing-the-azure-information-protection-aip-unified-labeling-scanner"></a>Tutorial: Installieren des Azure Information Protection-Scanners (AIP) für einheitliche Bezeichnungen

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> ***Relevant für:** [Azure Information Protection-Client für einheitliche Bezeichnungen für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

In diesem Tutorial wird beschrieben, wie Sie den lokalen Azure Information Protection-Scanner (AIP) installieren. Mit dem Scanner können AIP-Administratoren ihre Netzwerke und Inhaltsfreigaben auf vertrauliche Daten überprüfen und Klassifizierungs- und Schutzbezeichnungen anwenden, wie Sie in der Richtlinie ihrer Organisation konfiguriert sind.

**Benötigte Zeit**: Sie können dieses Tutorial innerhalb von 30 Minuten abschließen.

## <a name="tutorial-prerequisites"></a>Voraussetzungen für das Lernprogramm

Zum Installieren des Scanners für einheitliche Bezeichnungen und zum Durchführen dieses Tutorials benötigen Sie Folgendes:

|Anforderung  |Beschreibung  |
|---------|---------|
|**Ein unterstützendes Abonnement**     |  Sie benötigen ein Azure-Abonnement, das [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) umfasst. <br /><br />Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.       |
|**Administratorzugriff auf das Azure-Portal** |Stellen Sie sicher, dass Sie sich mit einem der folgenden Administratorkonten beim [Azure-Portal](https://portal.azure.com/) anmelden können: <br /><br />- **Complianceadministrator**<br />- **Compliancedatenadministrator**<br />- **Sicherheitsadministrator**<br />- **Globaler Administrator** |
|**Client installiert**    |   Installieren Sie den AIP-Client für einheitliche Bezeichnungen auf Ihrem Computer, um auf die Scannerinstallation zuzugreifen. <br /><br />Laden Sie die Datei **AzInfoProtection_UL.exe** aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018) herunter, und führen Sie sie aus. <br /><br />Wenn die Installation beendet ist, werden Sie möglicherweise aufgefordert, den Computer oder die Office-Software neu zu starten. Starten Sie bei Bedarf neu, um fortzufahren. <br /><br />Weitere Informationen finden Sie unter [Schnellstart: Bereitstellen des Azure Information Protection-Clients (AIP) für einheitliche Bezeichnungen](quickstart-deploy-client.md).|
|**SQL Server**     | Damit der Scanner ausgeführt werden kann, muss SQL Server auf dem Scannercomputer installiert sein. <br /><br /> Wechseln Sie zur Installation zur [Downloadseite für SQL Server](https://www.microsoft.com/sql-server/sql-server-downloads), und wählen Sie unter der Option, die Sie installieren möchten, **Jetzt herunterladen** aus. Wählen Sie im Installationsprogramm den Installationstyp **Standard** aus. <br /><br />**Hinweis**: Für Produktionsumgebungen wird die Installation von SQL Server Enterprise und für Testumgebungen nur Express empfohlen.       |
|**Azure Active Directory-Konto**     |  Wenn Sie mit einer standardmäßigen, mit der Cloud verbundenen Umgebung arbeiten, muss Ihr Domänendienstkonto, dass Sie für den Scanner verwenden möchten, mit [Azure Active Directory](https://azure.microsoft.com/services/active-directory/) synchronisiert werden. Dies ist nicht erforderlich, wenn Sie offline arbeiten. <br /><br />Wenn Sie sich bezüglich des Kontos nicht sicher sind, wenden Sie sich an einen Ihrer Systemadministratoren, um den Synchronisierungsstatus zu überprüfen.   |
|**Vertraulichkeitsbezeichnungen und eine veröffentlichte Richtlinie** |Sie müssen Vertraulichkeitsbezeichnungen erstellt und eine Richtlinie mit mindestens einer Bezeichnung für das Scannerdienstkonto im Admin Center für die Bezeichnungen veröffentlicht haben. <br /><br />Konfigurieren Sie Vertraulichkeitsbezeichnungen in ihrem Admin Center für Bezeichnungen, zum Beispiel im Microsoft 365 Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Security & Compliance Center. Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels). |
| | |

Nachdem Sie die Voraussetzungen überprüft haben, [konfigurieren Sie Azure Information Protection im Azure-Portal](#configure-azure-information-protection-in-the-azure-portal).

## <a name="configure-azure-information-protection-in-the-azure-portal"></a>Konfigurieren von Azure Information Protection im Azure-Portal

Azure Information Protection ist möglicherweise im Azure-Portal nicht verfügbar, oder der Schutz ist derzeit nicht aktiviert. 

Führen Sie ggf. einen oder beide der folgenden Schritte aus:

- [Hinzufügen von Azure Information Protection zum Azure-Portal](#add-azure-information-protection-to-the-azure-portal)
- [Überprüfen, ob der Schutz aktiviert ist](#confirm-that-protection-is-activated)

Fahren Sie dann mit [Konfigurieren der anfänglichen Scannereinstellungen im Azure-Portal](#configure-initial-scanner-settings-in-the-azure-portal) fort.

### <a name="add-azure-information-protection-to-the-azure-portal"></a>Hinzufügen von Azure Information Protection zum Azure-Portal

1. Melden Sie sich mit einem [unterstützten Administratorkonto](#tutorial-prerequisites) beim [Azure-Portal](https://portal.azure.com) an.

1. Wählen Sie **+ Ressource erstellen**. Geben Sie im Suchfeld **Azure Information Protection** ein, und wählen Sie dann den entsprechenden Eintrag. Klicken Sie auf der Azure Information Protection-Seite auf **Erstellen** und dann erneut auf **Erstellen**.

    :::image type="content" source="media/gifs/quickstart-add-aip-to-portal.gif" alt-text="Hinzufügen von Azure Information Protection zum Azure-Portal":::

    > [!TIP]
    > Wenn Sie diesen Schritt zum ersten Mal durchführen, wird neben dem Namen des Bereichs das Symbol **An Dashboard anheften** ![Symbol „An Dashboard anheften“](media/qs-tutor/pin-to-dashboard.png "Symbol „An Dashboard anheften“") angezeigt. Wählen Sie das Symbol „Anheften“ aus, um eine Kachel auf Ihrem Dashboard zu erstellen, sodass Sie beim nächsten Mal direkt hierher navigieren können.

Fahren Sie mit dem Abschnitt [Überprüfen, ob der Schutz aktiviert ist](#confirm-that-protection-is-activated) fort.

### <a name="confirm-that-protection-is-activated"></a>Überprüfen, ob der Schutz aktiviert ist

Wenn Azure Information Protection bereits für Sie verfügbar ist, stellen Sie sicher, dass der Schutz aktiviert ist:

1. Wählen Sie im Bereich „Azure Information Protection“ links unter **Verwalten** die Option **Schutzaktivierung** aus.

1. Überprüfen Sie, ob der Schutz für Ihren Mandanten aktiviert ist. Beispiel:

    :::image type="content" source="media/qs-tutor/confirm-activation.PNG" alt-text="AIP-Aktivierung bestätigen":::

Wenn der Schutz noch nicht aktiviert ist, klicken Sie auf ![AIP aktivieren](media/qs-tutor/activate.png "AIP aktivieren") **Aktivieren**. Wenn die Aktivierung abgeschlossen ist, zeigt die Informationsleiste **Activation finished successfully** (Aktivierung erfolgreich) an.

Fahren Sie mit [Konfigurieren der anfänglichen Scannereinstellungen im Azure-Portal](#configure-initial-scanner-settings-in-the-azure-portal) fort.

### <a name="configure-initial-scanner-settings-in-the-azure-portal"></a>Konfigurieren der anfänglichen Scannereinstellungen im Azure-Portal

Bereiten Sie vor der Installation des Scanners auf Ihrem Computer die anfänglichen Scannereinstellungen im Azure-Portal vor.

1. Wählen Sie im Bereich „Azure Information Protection“ links unter **Scanner** die Option :::image type="icon" source="media/i-clusters.png" border="false"::: **Cluster** aus.

1. Wählen Sie auf der Seite „Cluster“ die Option :::image type="icon" source="media/i-add.PNG" border="false"::: **Hinzufügen**  aus, um einen neuen Cluster zum Verwalten Ihres Scanners zu erstellen.

1. Geben Sie im sich rechts öffnenden Fenster **Neuen Cluster hinzufügen** einen aussagekräftigen Clusternamen und eine optionale Beschreibung ein.

    > [!IMPORTANT]
    > Sie benötigen den Namen dieses Clusters, wenn Sie den Scanner installieren.
    > 
    
    Beispiel:

    :::image type="content" source="media/qs-tutor/qs-add-new-cluster.png" alt-text="Hinzufügen eines neuen Clusters für das Tutorial":::

1. Erstellen Sie einen ersten Auftrag zur Inhaltsüberprüfung. Wählen Sie links im Menü **Scanner** die Option :::image type="icon" source="media/i-content-scan-jobs.png" border="false"::: **Aufträge zur Inhaltsüberprüfung** aus, und wählen Sie dann :::image type="icon" source="media/i-add.PNG" border="false"::: **Hinzufügen** aus.

1. Geben Sie im Bereich **Neuen Auftrag zur Inhaltsüberprüfung hinzufügen** einen aussagekräftigen Namen für Ihren Auftrag zur Inhaltsprüfung und eine optionale Beschreibung ein.

    Scrollen Sie dann auf der Seite nach unten zu **Richtlinienerzwingen**, und wählen Sie **Aus**.

    Speichern Sie Ihre Änderungen, wenn Sie fertig sind. 

    Dieser Standardauftrag überprüft alle bekannten Typen von vertraulichen Daten.

1. Schließen Sie den Detailbereich für Ihren Auftrag zur Inhaltsüberprüfung, und kehren Sie zum Raster :::image type="icon" source="media/i-content-scan-jobs.png" border="false"::: **Aufträge zur Inhaltsüberprüfung** zurück. 

    Wählen Sie in der neuen Zeile, die für Ihren Auftrag zur Inhaltsüberprüfung angezeigt wird, in der Spalte **Clustername** die Option **+ Dem Cluster zuweisen** aus. Anschließend wählen Sie im rechts angezeigten Bereich **Cluster zuweisen** Ihren Cluster aus. 

    :::image type="content" source="media/qs-tutor/assign-cluster-all.png" alt-text="Cluster zuweisen":::

Jetzt können Sie den [AIP-Scanner für einheitliche Bezeichnungen installieren](#install-the-aip-unified-labeling-scanner).

## <a name="install-the-aip-unified-labeling-scanner"></a>Installieren des AIP-Scanners für einheitliche Bezeichnungen

Nachdem Sie die [grundlegenden Scannereinstellungen im Azure-Portal](#configure-azure-information-protection-in-the-azure-portal) konfiguriert haben, installieren Sie den Scanner für einheitliche Bezeichnungen auf dem AIP-Clientcomputer.

1. Starten Sie auf dem Clientcomputer eine PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

1. Verwenden Sie zum Installieren des Scanners den folgenden Befehl: Geben Sie in Ihrem Befehl an, wo Sie den Scanner installieren möchten, sowie den Namen des [Clusters, den Sie im Azure-Portal](#configure-initial-scanner-settings-in-the-azure-portal) erstellt haben.

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <your SQL installation location>\SQLEXPRESS -Cluster <cluster name>
    ```
    Beispiel:

    ```powershell
    Install-AIPScanner -SqlServerInstance localhost\SQLEXPRESS -Cluster Quickstart
    ```

    Wenn Sie von PowerShell zur Eingabe der Anmeldeinformationen aufgefordert werden, geben Sie den Benutzernamen und das Kennwort ein. 

    Verwenden Sie für das Feld **Benutzername** die folgende Syntax: `<domain\user name>`. Ein Beispiel für die Camel-Case-Schreibweise lautet: `emea\contososcanner`.

1. Kehren Sie zum Azure-Portal zurück. Wählen Sie auf der linken Seite im Menü **Scanner** die Option :::image type="icon" source="media/qs-tutor/i-nodes.png" border="false"::: **Knoten** aus. 

    Der Scanner sollte nun im Raster angezeigt werden. Beispiel:

    :::image type="content" source="media/qs-tutor/qs-post-install-scanner.png" alt-text="Neu installierter Scanner wird im Raster „Knoten“ angezeigt":::

Fahren Sie mit [Abrufen eines Azure Active Directory-Tokens für den Scanner](#get-an-azure-active-directory-token-for-the-scanner) fort, damit Ihr Scannerdienstkonto ohne Benutzereingriff ausgeführt werden kann.

## <a name="get-an-azure-active-directory-token-for-the-scanner"></a>Abrufen eines Azure Active Directory-Tokens für den Scanner

Führen Sie diese Schritte aus, wenn Sie mit einer standardmäßigen, mit der Cloud verbundenen Umgebung arbeiten, damit der Scanner beim AIP-Dienst authentifiziert und der Dienst ohne Benutzereingriff ausgeführt werden kann.

Dies ist nicht erforderlich, wenn Sie nur offline arbeiten.

Weitere Informationen finden Sie unter [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](rms-client/clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection).

**So rufen Sie ein Azure AD-Token für den Scanner ab**:

1. Erstellen Sie im Azure-Portal eine Azure AD-Anwendung, um ein Zugriffstokens für die Authentifizierung anzugeben.

1. Melden Sie sich auf Ihrem Scannercomputer mit einem Scannerdienstkonto an, das über die Berechtigung **Lokales Anmelden** verfügt, und starten Sie eine PowerShell-Sitzung.

1. Starten Sie eine PowerShell-Sitzung, und führen Sie den folgenden Befehl aus, wobei Sie die aus der Azure AD-Anwendung kopierten Werte verwenden.

    ```PowerShell
    Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
    ```

    Beispiel:

    ```PowerShell
    $pscreds = Get-Credential CONTOSO\scanner
    Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds

    Acquired application access token on behalf of CONTOSO\scanner.
    ``` 

    > [!TIP]
    > Wenn Ihrem Scannerdienstkonto die Berechtigung **Lokales Anmelden** für die Installation nicht gewährt werden kann, verwenden Sie den Parameter **OnBehalfOf** mit **Set-AIPAuthentication** anstelle des Parameters **DelegatedUser**.

Der Scanner verfügt jetzt über ein Token zum Authentifizieren bei Azure AD. Dieses Token ist solange gültig, wie Sie in Azure Active Directory festgelegt haben. Wenn das Token abgelaufen ist, müssen Sie den Vorgang wiederholen.

Fahren Sie mit [Installieren des Netzwerkerkennungsdiensts](#install-the-network-discovery-service) fort, damit Sie Ihre Netzwerkrepositorys nach möglicherweise riskanten Inhalten durchsuchen und diese Repositorys dann zu einem Auftrag zur Inhaltsüberprüfung hinzufügen können.

## <a name="install-the-network-discovery-service"></a>Installieren des Netzwerkerkennungsdiensts

Ab Version [2.8.85.0](rms-client/unifiedlabelingclient-version-release-history.md#version-28850) des AIP-Clients für einheitliche Bezeichnungen können Administratoren mithilfe des AIP-Scanners ihre Netzwerkrepositorys überprüfen und anschließend alle Repositorys, die möglicherweise riskant sind, zu einem Auftrag zur Inhaltsüberprüfung hinzufügen.

Aufträge zur Netzwerküberprüfung zeigen auf, *wo* sich riskante Inhalte befinden. Hierzu versuchen Sie, sowohl als Administrator als auch als öffentlicher Benutzer auf konfigurierte Repositorys zuzugreifen.

Wenn z. B. festgestellt wird, dass der öffentliche Zugriff auf ein Repository sowohl Lesen als auch Schreiben zulässt, sollten Sie eine weitere Überprüfung durchführen und bestätigen, dass dort keine vertraulichen Daten gespeichert sind.

> [!NOTE]
> Dieses Feature befindet sich derzeit in der VORSCHAU. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind.

**So installieren Sie den Netzwerkerkennungsdienst**:

1. Starten Sie auf dem Scannercomputer als Administrator eine PowerShell-Sitzung.

1. Legen Sie die Anmeldeinformationen fest, die AIP beim Ausführen des Netzwerkerkennungsdiensts sowie bei der Simulation des Zugriffs als Administrator bzw. öffentlicher Benutzer verwenden soll. 

    Geben Sie für jeden Befehl bei Aufforderung die Anmeldeinformationen mit der folgenden Syntax ein: `domain\user`. Beispiel: `emea\msanchez`

    Führen Sie Folgendes aus: 

    **Anmeldeinformationen zum Ausführen des Netzwerkerkennungsdiensts:**

    ``` PowerShell 
    $serviceacct= Get-Credential 
    ``` 

    **Anmeldeinformationen zum Simulieren des Administratorzugriffs:**

    ``` PowerShell 
    $shareadminacct= Get-Credential 
    ``` 

    **Anmeldeinformationen zum Simulieren des Zugriffs als öffentlicher Benutzer:**

    ``` PowerShell  
    $publicaccount= Get-Credential 
    ``` 

1. Zum Installieren des Netzwerkerkennungsdiensts führen Sie Folgendes aus:

    ```PowerShell
    Install-MIPNetworkDiscovery [-ServiceUserCredentials] <PSCredential> [[-StandardDomainsUserAccount] <PSCredential>] [[-ShareAdminUserAccount] <PSCredential>] [-SqlServerInstance] <String> -Cluster <String> [-WhatIf] [-Confirm] [<CommonParameters>]

    For example:

    ```PowerShell
    Install-MIPNetworkDiscovery -SqlServerInstance SQLSERVER1\SQLEXPRESS -Cluster Quickstart -ServiceUserCredentials $serviceacct  -ShareAdminUserAccount $shareadminacct -StandardDomainsUserAccount $publicaccount
 
    ```

Sobald die Installation beendet ist, wird eine Bestätigungsmeldung angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Nachdem der Scanner und der Netzwerkerkennungsdienst installiert sind, können Sie mit der Überprüfung beginnen. 

Weitere Informationen finden Sie unter [Tutorial: Erkennen vertraulicher Inhalte mit dem Azure Information Protection-Scanner (AIP)](tutorial-scan-networks-and-content.md).

> [!TIP]
> Wenn Sie [Version 2.8.85.0](rms-client/unifiedlabelingclient-version-release-history.md#version-28850) installiert haben, wird die Überprüfung Ihres Netzwerk empfohlen, um Repositorys mit möglicherweise riskanten Inhalten zu ermitteln. 
>
>Um Ihre riskanten Repositorys auf vertrauliche Daten zu überprüfen und diese Daten dann zu klassifizieren und vor externen Benutzern zu schützen, aktualisieren Sie Ihren Auftrag zur Inhaltsüberprüfung mit den Details der gefundenen Repositorys.
>

**Siehe auch**:

- [Was ist der Azure Information Protection-Scanner für einheitliche Bezeichnungen?](deploy-aip-scanner.md)
- [Voraussetzungen für das Installieren und Bereitstellen des Azure Information Protection-Scanners für einheitliche Bezeichnungen](deploy-aip-scanner-prereqs.md)
- [Tutorial: Verhindern übermäßiger Freigaben mit Azure Information Protection (AIP)](tutorial-preventing-oversharing.md)
- [Tutorial: Migrieren vom klassischen Azure Information Protection-Client (AIP) zum Client für einheitliche Bezeichnungen](tutorial-migrating-to-ul.md)
