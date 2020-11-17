---
title: 'Tutorial: Erkennen vertraulicher Inhalte mit dem Azure Information Protection-Scanner (AIP)'
description: Verwenden Sie den AIP-Scanner, um nach riskanten Repositorys zu suchen. Anschließend können Sie einen Drilldown durchführen, um diese Dateifreigaben auf vertrauliche Inhalte zu überprüfen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/09/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.service: information-protection
ms.custom: admin
ms.subservice: aiplabels
ms.openlocfilehash: 82f8e2a9566379318f0a41ed625048a0036b0a62
ms.sourcegitcommit: d4ac18506e3f0e7b39466eb811d3129100512a78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94423447"
---
# <a name="tutorial-discovering-your-sensitive-content-with-the-azure-information-protection-aip-scanner"></a>Tutorial: Erkennen vertraulicher Inhalte mit dem Azure Information Protection-Scanner (AIP)

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection-Client für einheitliche Bezeichnungen für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Der Azure Information Protection-Client bietet einen lokalen Scanner mit dem Administratoren ihre Netzwerke und Dateifreigaben nach vertraulichen Inhalten durchsuchen können. 

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Erstellen eines Auftrags zur Netzwerküberprüfung und Suchen nach riskanten Repositorys
> * Hinzufügen der gefundenen riskanten Repositorys zu einem Auftrag zur Inhaltsüberprüfung
> * Überprüfen der Inhaltsfreigaben auf vertrauliche Inhalte und Analysieren der Ergebnisse

> [!NOTE]
> Die Netzwerkerkennung ist erst ab Version [2.8.85.0](rms-client/unifiedlabelingclient-version-release-history.md#version-28850) des Clients für einheitliche Bezeichnungen verfügbar und befindet sich derzeit in der VORSCHAU. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind.
>
> Wenn Sie diese Version des Clients und Scanners nicht installiert haben, lesen Sie die [Voraussetzungen für das Tutorial](#tutorial-prerequisites) und wechseln Sie dann direkt zu [Definieren und Ausführen Ihres Auftrags zur Inhaltsüberprüfung](#define-and-run-your-content-scan-job).


**Benötigte Zeit:** Für diese Konfiguration benötigen Sie 15 Minuten.

## <a name="tutorial-prerequisites"></a>Voraussetzungen für das Lernprogramm

|Anforderung  |Beschreibung  |
|---------|---------|
|**Ein unterstützendes Abonnement**     |  Sie benötigen ein Azure-Abonnement, das [Azure Information Protection-Plan 1 oder -Plan 2](https://azure.microsoft.com/pricing/details/information-protection/) umfasst. <br /><br />Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.       |
|**Administratorzugriff auf das Azure-Portal** |Stellen Sie sicher, dass Sie sich mit einem unterstützten Administratorkonto beim [Azure-Portal](https://portal.azure.com/) anmelden können, und aktivieren Sie den Schutz. Zu den unterstützten Administratorkonten gehören: <br /><br />- **Complianceadministrator**<br />- **Compliancedatenadministrator**<br />- **Sicherheitsadministrator**<br />- **Globaler Administrator**   |
|**AIP-Client, Scanner und Netzwerkerkennungsdienst**   |   Um dieses Tutorial vollständig abzuschließen, müssen Sie den Azure Information Protection-Client für einheitliche Bezeichnungen mit dem Scanner sowie den Netzwerkerkennungsdienst (Public Preview) installiert haben. <br /><br />Weitere Informationen finden Sie in folgenden Quellen: <br /><br />- [Schnellstart: Bereitstellen des Azure Information Protection-Clients (AIP) für einheitliche Bezeichnungen](quickstart-deploy-client.md) <br />- [Tutorial: Installieren des Azure Information Protection-Scanners (AIP) für einheitliche Bezeichnungen](tutorial-install-scanner.md) |
|**Ein Auftrag zur Inhaltsüberprüfung** | Stellen Sie sicher, dass Sie über einen grundlegenden Auftrag zur Inhaltsüberprüfung verfügen, den Sie für Tests verwenden können. Möglicherweise haben Sie einen bei der [Installation des Scanners](tutorial-install-scanner.md) erstellt.<br /><br />Wenn Sie jetzt einen erstellen müssen, folgen Sie den Anweisungen in [Konfigurieren von Azure Information Protection im Azure-Portal](tutorial-install-scanner.md#configure-azure-information-protection-in-the-azure-portal). Sobald Sie über einen grundlegenden Auftrag zur Inhaltsüberprüfung verfügen, kehren Sie hierher zurück, um dieses Tutorial abzuschließen. |
|**SQL Server**     | Damit der Scanner ausgeführt werden kann, muss SQL Server auf dem Scannercomputer installiert sein. <br /><br /> Wechseln Sie zur Installation zum [Microsoft Download Center](https://www.microsoft.com/sql-server/sql-server-editions-express), und wählen Sie unter der Option, die Sie installieren möchten, **Jetzt herunterladen** aus. Wählen Sie im Installationsprogramm den Installationstyp **Standard** aus. <br /><br />**Hinweis**: Für Produktionsumgebungen wird die Installation von SQL Server Enterprise und für Testzwecke nur Express empfohlen.    |
|**Azure Active Directory-Konto**     |  Wenn Sie mit einer standardmäßigen, mit der Cloud verbundenen Umgebung arbeiten, muss Ihr Domänenkonto mit [Azure Active Directory](https://azure.microsoft.com/services/active-directory/) synchronisiert werden. Dies ist nicht erforderlich, wenn Sie offline arbeiten. <br /><br />Wenn Sie sich bezüglich des Kontos nicht sicher sind, wenden Sie sich an einen Ihrer Systemadministratoren, um den Synchronisierungsstatus zu überprüfen. Weitere Informationen finden Sie unter [Bereitstellen der Überprüfung mit alternativen Konfigurationen](deploy-aip-scanner-prereqs.md#deploying-the-scanner-with-alternative-configurations).  |
|**Vertraulichkeitsbezeichnungen und eine veröffentlichte Richtlinie** |Sie müssen Vertraulichkeitsbezeichnungen erstellt und eine Richtlinie mit mindestens einer Bezeichnung für das Scannerdienstkonto im Admin Center für die Bezeichnungen veröffentlicht haben. <br /><br />Konfigurieren Sie Vertraulichkeitsbezeichnungen in ihrem Admin Center für Bezeichnungen, zum Beispiel im Microsoft 365 Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Security & Compliance Center. Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels). |
| | | 


Wenn Sie bereit sind, fahren Sie mit [Erstellen eines Auftrags zur Netzwerküberprüfung](#create-a-network-scan-job) fort.

## <a name="create-a-network-scan-job"></a>Erstellen eines Auftrags zur Netzwerküberprüfung

Erstellen Sie einen Auftrag zur Netzwerküberprüfung, um eine bestimmte IP-Adresse oder einen IP-Adressbereich auf riskante Repositorys hin zu überprüfen.

> [!NOTE]
> Dieses Feature ist nur ab Version [2.8.85.0](rms-client/unifiedlabelingclient-version-release-history.md#version-28850) verfügbar und befindet sich derzeit in der VORSCHAU. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind.
> 

**So erstellen Sie einen Auftrag zur Netzwerküberprüfung:**

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) als [unterstützter Administrator](#tutorial-prerequisites) an, und navigieren Sie zum Bereich **Azure Information Protection**.
        
1. Wählen Sie auf der linken Seite im Menü **Scanner** die Option :::image type="icon" source="media/qs-tutor/i-network-scan-jobs.png" border="false"::: **Aufträge zur Netzwerküberprüfung (Vorschau)** aus.

1. Wählen Sie :::image type="icon" source="media/i-add.PNG" border="false"::: **Hinzufügen** aus, um einen neuen Auftrag hinzuzufügen. Geben Sie im Bereich **Neuen Auftrag zur Netzwerküberprüfung hinzufügen** die folgenden Details ein:
    
    |Option  |BESCHREIBUNG  |
    |---------|---------|
    |**Name des Auftrags zur Netzwerküberprüfung** und **Beschreibung**     |Geben Sie einen aussagekräftigen Namen, z. B. `Quickstart`, und eine optionale Beschreibung ein.         |
    |**Wählen Sie den Cluster aus.**     | Wählen Sie in der Dropdownliste den Clusternamen aus.<br /><br /> Wenn Sie z. B. das [Tutorial: Installieren des Azure Information Protection-Scanners (AIP) für einheitliche Bezeichnungen](tutorial-install-scanner.md) abgeschlossen haben und der Cluster noch verfügbar ist, wählen Sie **Schnellstart** aus.       |
    |**Zu ermittelnde IP-Adressbereiche konfigurieren**     | Wählen Sie die Zeile aus, um den Bereich **IP-Adressbereiche auswählen** zu öffnen. Geben Sie eine IP-Adresse oder einen IP-Adressbereich für die Überprüfung ein. <br /><br />**Hinweis**: Stellen Sie sicher, dass IP-Adressen eingegeben werden, auf die vom Computer des Scanners aus zugegriffen werden kann.      |
    |**Zeitplan festlegen**     | Behalten Sie den Standardwert **Einmalig** bei.        |
    |**Startzeit (UTC) festlegen**     |  Berechnen Sie die aktuelle UTC-Zeit unter Berücksichtigung Ihrer aktuellen Zeitzone, und stellen Sie die Startzeit so ein, dass sie in 5 Minuten ab jetzt läuft.     |
    |     |         |

    Beispiel: 

    :::image type="content" source="media/qs-tutor/network-scan-job.png" alt-text="Eingeben von Details für den Auftrag zur Netzwerküberprüfung":::

1. Wählen Sie im oberen Bereich der Seite :::image type="icon" source="media/qs-tutor/save-icon.png" border="false"::: **Speichern** aus.

1. Kehren Sie zum Raster :::image type="icon" source="media/qs-tutor/i-network-scan-jobs.png" border="false"::: **Aufträge zur Netzwerküberprüfung (Vorschau)** zurück, und warten Sie, bis die Überprüfung gestartet wird.

Die Rasterdaten werden aktualisiert, wenn die Überprüfung abgeschlossen ist. Beispiel:

:::image type="content" source="media/qs-tutor/scanned-network.png" alt-text="Aktualisierte Aufträge zur Netzwerküberprüfung":::

> [!TIP]
> Wenn Ihr Auftrag zur Netzwerküberprüfung nicht ausgeführt wird, stellen Sie sicher, dass der [Netzwerkerkennungsdienst auf dem Scannercomputer korrekt installiert ist](tutorial-install-scanner.md#install-the-network-discovery-service).

Fahren Sie mit [Hinzufügen der riskanten Repositorys zu einem Auftrag zur Inhaltsüberprüfung](#add-risky-repositories-to-a-content-scan-job) fort.

## <a name="add-risky-repositories-to-a-content-scan-job"></a>Hinzufügen der riskanten Repositorys zu einem Auftrag zur Inhaltsüberprüfung

Nach dem der Auftrag zur Netzwerküberprüfung abgeschlossen ist, können Sie sich die gefundenen riskanten Repositorys ansehen. 

Wenn z. B. festgestellt wird, dass der öffentliche Zugriff auf ein Repository sowohl Lesen als auch Schreiben zulässt, sollten Sie eine weitere Überprüfung durchführen und bestätigen, dass dort keine vertraulichen Daten gespeichert sind.

> [!NOTE]
> Dieses Feature ist nur ab Version [2.8.85.0](rms-client/unifiedlabelingclient-version-release-history.md#version-28850) verfügbar und befindet sich derzeit in der VORSCHAU. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind.
> 

**So fügen Sie riskante Repositorys zu Ihrem Auftrag zur Inhaltsüberprüfung hinzu:**

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) als [unterstützter Administrator](#tutorial-prerequisites) an, und navigieren Sie zum Bereich **Azure Information Protection**.
        
1. Wählen Sie auf der linken Seite im Menü **Scanner** die Option :::image type="icon" source="media/qs-tutor/i-repos.png" border="false"::: **Repositorys (Vorschau)** aus.

    :::image type="content" source="media/small/risky-repos-small.png" alt-text="Anzeigen der vom Auftrag zur Netzwerküberprüfung gefundenen Repositorys" lightbox="media/qs-tutor/risky-repos.png":::

1. Suchen Sie in dem Raster unter den Diagrammen ein Repository, das noch nicht vom Scanner erfasst wird. Wenn sie nicht vom Scanner erfasst werden, bedeutet dies, dass sie nicht in einen Auftrag zur Inhaltsüberprüfung einbezogen und auch nicht auf vertrauliche Inhalte überprüft werden.

    > [!TIP]
    > Beispielsweise sind Repositorys, die über **effektiven öffentlichen Zugriff verfügen** mit **R** (Lesezugriff) oder **RW** (Lese-/Schreibzugriff), öffentlich verfügbar und können vertrauliche Inhalte enthalten.
    > 

1. Wählen Sie die Zeile aus, und wählen Sie dann oberhalb des Rasters :::image type="icon" source="media/i-add.PNG" border="false"::: **Ausgewählte Elemente zuweisen** aus. 

1. Wählen Sie im rechts angezeigten Bereich **Dem Auftrag zur Inhaltsüberprüfung zuweisen** in der Dropdownliste Ihren Auftrag zur Inhaltsüberprüfung aus, und wählen Sie dann :::image type="icon" source="media/qs-tutor/save-icon.png" border="false"::: **Speichern** aus.

    Beispiel:

    :::image type="content" source="media/qs-tutor/assign-content-scan-job.png" alt-text="Zuweisen eines riskanten Repositorys zu einem Auftrag zur Inhaltsüberprüfung":::

Beim nächsten Ausführen des Auftrags zur Inhaltsüberprüfung wird dieser nun dieses neu entdeckte Repository mit einbeziehen und alle gefundenen vertraulichen Inhalte gemäß der Konfiguration in Ihrer Richtlinie identifizieren, bezeichnen, klassifizieren und schützen.

Fahren Sie mit [Definieren und Ausführen Ihres Auftrags zur Inhaltsüberprüfung](#define-and-run-your-content-scan-job) fort.

## <a name="define-and-run-your-content-scan-job"></a>Definieren und Ausführen Ihres Auftrags zur Inhaltsüberprüfung

Verwenden Sie den Auftrag zur Inhaltsüberprüfung, den Sie mit den [Voraussetzungen für das Tutorial](#tutorial-prerequisites) vorbereitet haben, um Ihre Inhalte zu überprüfen. 

Wenn Sie noch keinen Auftrag zur Inhaltsüberprüfung haben, führen Sie die Schritte unter [Konfigurieren der anfänglichen Einstellungen im Azure-Portal](tutorial-install-scanner.md#configure-initial-scanner-settings-in-the-azure-portal) durch, und kehren Sie dann hierher zurück, um fortzufahren.


1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) als [unterstützter Administrator](#tutorial-prerequisites) an, und navigieren Sie zum Bereich **Azure Information Protection**.
        
1. Wählen Sie links im Menü **Scanner** die Option :::image type="icon" source="media/i-content-scan-jobs.png" border="false"::: **Aufträge zur Inhaltsüberprüfung** aus, und wählen Sie dann den Auftrag zur Inhaltsüberprüfung aus.
 
1. Bearbeiten Sie die Einstellungen für den Auftrag zur Inhaltsüberprüfung. Stellen Sie sicher, dass Sie einen aussagekräftigen Namen und eine optionale Beschreibung angegeben haben. 

    Behalten Sie die Standardwerte für die meisten Einstellungen bei, mit Ausnahme der folgenden Änderungen:

    -  **Empfohlene Bezeichnung als automatisch festlegen**. Setzen Sie diese Option auf **Ein**.
    
    - **Repositorys konfigurieren**. Stellen Sie sicher, dass mindestens ein Repository definiert ist. 
    
        > [!TIP]
        > Wenn Sie Ihrem Auftrag zur Inhaltsüberprüfung zusätzliche Repositorys hinzugefügt haben, nachdem Sie Ihr Netzwerk in [Hinzufügen von riskanten Repository zu einem Auftrag zur Inhaltsüberprüfung](#add-risky-repositories-to-a-content-scan-job) überprüft haben, können Sie diese hier anzeigen. 

    - **Erzwingen**. Setzen Sie diese Option auf **Ein**.
    
1. Wählen Sie :::image type="icon" source="media/qs-tutor/save-icon.png" border="false"::: **Speichern** aus, und kehren Sie dann zum Raster :::image type="icon" source="media/i-content-scan-jobs.PNG" border="false"::: **Aufträge zur Inhaltsüberprüfung** zurück.

1. Gehen Sie zur Inhaltsüberprüfung zurück zum Bereich :::image type="icon" source="media/i-content-scan-jobs.png" border="false"::: **Aufträge zur Inhaltsüberprüfung**, und wählen Sie Ihren Auftrag zur Inhaltsüberprüfung aus.

    Wählen Sie in der Symbolleiste oberhalb des Rasters :::image type="icon" source="media/i-scan-now.PNG" border="false"::: **Jetzt überprüfen** aus, um die Überprüfung zu starten.

    Wenn die Überprüfung abgeschlossen ist, fahren Sie mit [Anzeigen der Überprüfungsergebnisse](#view-scan-results) fort.

### <a name="view-scan-results"></a>Anzeigen der Überprüfungsergebnisse

Sehen Sie nach Abschluss der Überprüfung die Berichte im Bereich **Azure Information Protection > Analysen** des Azure-Portals durch.

Beispiel:

:::image type="content" source="media/qs-tutor/content-scan-job-data-discovery.PNG" alt-text="Bericht mit den Überprüfungsergebnissen zur Analyse der erkannten Daten":::
    
> [!TIP]
> Wenn keine Ergebnisse vorhanden sind und Sie eine aussagekräftige Überprüfung durchführen möchten, erstellen Sie eine Datei mit dem Namen **Zahlungsinfo** in einem der Repositorys, die in Ihrem Auftrag zur Inhaltsüberprüfung enthalten sind. Speichern Sie die Datei mit folgendem Inhalt:
> 
> **Kreditkarte:** 2384 2328 5436 3489
>
> Führen Sie die Überprüfung erneut aus, um den Unterschied in den Ergebnissen anzuzeigen.
> 

Weitere Informationen finden Sie unter [Zentrale Berichterstellung für Azure Information Protection (Public Preview)](reports-aip.md).

#### <a name="local-scanner-reports"></a>Berichte für lokale Scanner

Protokolle werden auch lokal im **Verzeichnis „%localappdata%\Microsoft\MSIP\Scanner\Reports“** auf dem Scannercomputer gespeichert und umfassen Folgendes:

|Typ  |BESCHREIBUNG  |
|---------|---------|
|**TXT-Zusammenfassungsdateien**     |  Enthalten die zum Überprüfen benötigte Zeit, die Anzahl der überprüften Dateien sowie die Anzahl der Dateien mit übereinstimmenden Informationstypen.       |
|**CSV-Detaildateien.**     | Enthalten ausführliche Beschreibungen für jede überprüfte Datei. Das Verzeichnis kann bis zu 60 Berichte für jeden Überprüfungszyklus enthalten.         |
|     |         |

## <a name="next-steps"></a>Nächste Schritte

Weitere Tutorials finden Sie unter:

- [Tutorial: Verhindern übermäßiger Freigaben mit Azure Information Protection (AIP)](tutorial-preventing-oversharing.md)
- [Tutorial: Migrieren vom klassischen Azure Information Protection-Client (AIP) zum Client für einheitliche Bezeichnungen](tutorial-migrating-to-ul.md)

**Weitere Informationen:**

- [Was ist der Azure Information Protection-Scanner für einheitliche Bezeichnungen?](deploy-aip-scanner.md)
- [Voraussetzungen für das Installieren und Bereitstellen des Azure Information Protection-Scanners für einheitliche Bezeichnungen](deploy-aip-scanner-prereqs.md)
- [Konfigurieren und Installieren des Azure Information Protection-Scanners für einheitliche Bezeichnungen](deploy-aip-scanner-configure-install.md)
- [Ausführen des Azure Information Protection-Scanners](deploy-aip-scanner-manage.md)
