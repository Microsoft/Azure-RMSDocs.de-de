---
title: Migrieren von AD RMS-Azure Information Protection
description: Anweisungen zum Migrieren Ihrer AD RMS-Bereitstellung (Active Directory Rights Management Services) zu Azure Information Protection. Nach der Migration haben Benutzer weiterhin Zugriff auf Dokumente und e-Mail-Nachrichten, die Ihre Organisation mithilfe von AD RMS geschützt hat.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/11/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.subservice: migration
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 04534d6bce6c0db554a30b3690957c8aeeae433d
ms.sourcegitcommit: f6d536b6a3b5e14e24f0b9e58d17a3136810213b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98809438"
---
# <a name="migrating-from-ad-rms-to-azure-information-protection"></a>Migrieren von AD RMS zu Azure Information Protection

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Befolgen Sie die nachstehenden Anweisungen, um Ihre AD RMS-Bereitstellung (Active Directory Rights Management Services) zu Azure Information Protection zu migrieren. 

Nach der Migration werden Ihre AD RMS-Server nicht mehr verwendet, aber Benutzer haben weiter Zugriff auf Dokumente und E-Mail-Nachrichten, die Ihre Organisation mithilfe von AD RMS geschützt hat. Für neue zu schützende Inhalte wird Azure Rights Management Service (Azure RMS) von Azure Information Protection verwendet.

Nicht sicher, ob diese Migration von AD RMS für Ihre Organisation geeignet ist?

- Eine Einführung in Azure Information Protection finden Sie unter [Was ist Azure Information Protection?](./what-is-information-protection.md).

- Einen Vergleich von Azure Information Protection mit AD RMS finden Sie unter [Vergleich von Azure Information Protection und AD RMS](./compare-on-premise.md).

## <a name="recommended-reading-before-you-migrate-to-azure-information-protection"></a>Empfohlene Lektüre vor der Migration zu Azure Information Protection

Die folgende Dokumentation ist zwar nicht zwingend erforderlich – es empfiehlt sich dennoch, sie zu lesen, bevor Sie mit der Migration beginnen. Sie werden besser verstehen, wie die für Ihre Migration relevante Technologie funktioniert.

- [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](./plan-implement-tenant-key.md): Machen Sie sich mit den Schlüsselverwaltungsoptionen für Ihren Azure Information Protection-Mandanten vertraut. Die Entsprechung Ihres SLC-Schlüssels (Server Licensor Certificate, lizenzgebendes Serverzertifikat) wird entweder von Microsoft (Standard) oder Ihnen („Bring Your Own Key“- oder BYOK-Konfiguration) verwaltet. 

- [RMS-Dienst](./rms-client/client-deployment-notes.md#rms-service-discovery)Ermittlung: in diesem Abschnitt der RMS-Client Bereitstellungs Hinweise wird erläutert, dass die Reihenfolge für die Dienst Ermittlung **Registry** lautet, dann **Dienst Verbindungspunkt (SCP)** und **Cloud**. Wenn der Dienstverbindungspunkt während des Migrationsvorgangs noch installiert ist, konfigurieren Sie Clients mit Registrierungseinstellungen für Ihren Azure Information Protection-Mandanten so, dass sie nicht den vom Dienstverbindungspunkt zurückgegebenen AD RMS-Cluster verwenden.

- [Übersicht über den Microsoft Rights Management-Connector](./deploy-rms-connector.md#overview-of-the-microsoft-rights-management-connector): In diesem Abschnitt der Dokumentation zum RMS-Connector wird erläutert, wie Ihre lokalen Server sich mit dem Azure Rights Management-Dienst verbinden können, um Dokumente und E-Mails zu schützen.

Wenn Sie nicht mit der Funktionsweise von AD RMS vertraut sind, ist es möglicherweise hilfreich, zu erfahren, [wie Azure RMS funktioniert? Im](./how-does-it-work.md) Hintergrund können Sie ermitteln, welche Technologie Prozesse für die cloudversion identisch oder unterschiedlich sind.

## <a name="prerequisites-for-migrating-ad-rms-to-azure-information-protection"></a>Voraussetzungen für die Migration von AD RMS zu Azure Information Protection

Stellen Sie vor der Migration zu Azure Information Protection sicher, dass die folgenden Voraussetzungen erfüllt sind und Sie alle etwaigen Einschränkungen kennen.

- **Eine unterstützte RMS-Bereitstellung**:
    
  - Die folgenden AD RMS-Versionen unterstützen die Migration zu Azure Information Protection:
           
      - Windows Server 2012 (x64)
        
      - Windows Server 2012 R2 (x64)
        
      - Windows Server 2016 (x64)
        
  - Alle gültigen AD RMS-Topologien werden unterstützt:
    
      - Einzelne Gesamtstruktur, einzelner RMS-Cluster
        
      - Einzelne Gesamtstruktur, mehrere reine RMS-Lizenzierungscluster
        
      - Mehrere Gesamtstrukturen, mehrere RMS-Cluster
        
    > [!NOTE]
    > Mehrere AD RMS-Cluster werden standardmäßig zu einem einzelnen Azure Information Protection-Mandanten migriert. Wenn Sie separate Azure Information Protection-Mandanten wünschen, müssen Sie sie als getrennte Migrationen behandeln. Ein Schlüssel von einem RMS-Cluster kann nur in einen einzigen Mandanten importiert werden.
    >
 
- **Alle Anforderungen, die Azure Information Protection ausgeführt werden müssen, einschließlich eines Abonnements für Azure Information Protection (der Azure-Rights Management Dienst ist nicht aktiviert)**:

    Siehe [Anforderungen für Azure Information Protection](./requirements.md).

    Der Azure Information Protection *Client ist für* die Klassifizierung und Bezeichnung und *optional, aber empfohlen,* Wenn Sie nur Daten schützen möchten. 

    Weitere Informationen finden Sie in den Administrator Handbüchern für den [Azure Information Protection Unified Bezeichnung-Client](./rms-client/clientv2-admin-guide.md).

    Obwohl Sie ein Azure Information Protection-Abonnement benötigen, bevor Sie von AD RMS aus migrieren können, empfehlen wir, den Rights Management-Dienst für Ihren Mandanten nicht vor dem Start der Migration zu aktivieren. 

    Sie führen diesen Aktivierungsschritt während der Migration aus, nachdem Sie die Schlüssel und Vorlagen aus AD RMS exportiert und in Ihren Azure Information Protection-Mandanten importiert haben. Wenn der Rights Management-Dienst jedoch schon aktiviert wurde, können Sie immer noch von AD RMS migrieren. Dafür sind zusätzliche Schritte notwendig.

    **Nur Office 2010**: 

    Wenn Sie über Computer verfügen, auf denen Office 2010 ausgeführt wird, müssen Sie den [Azure Information Protection-Client](rms-client/use-client.md) installieren, um die Authentifizierung von Benutzern bei Clouddiensten zu ermöglichen. 

    > [!IMPORTANT]
    > Der erweiterte Support für Office 2010 endete am 13. Oktober 2020. Weitere Informationen finden Sie unter [AIP und ältere Windows- und Office-Versionen](known-issues.md#aip-and-legacy-windows-and-office-versions).
    >  
    


- **Vorbereitung für Azure Information Protection**:

  - Verzeichnissynchronisierung zwischen Ihrem lokalen Verzeichnis und Azure Active Directory

  - E-Mail-aktivierte Gruppen in Azure Active Directory

    Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

- **Wenn Sie die IRM-Funktionalität (Information Rights Management) von Exchange Server** (zum Beispiel Transportregeln und Outlook Web Access) oder SharePoint Server mit AD RMS verwendet haben:

  - Planen Sie einen kurzen Zeitraum ein, in dem IRM nicht auf diesen Servern zur Verfügung steht.
 
    Nach der Migration können Sie IRM weiterhin auf diesen Servern verwenden. Allerdings wird in einem der Migrationsschritte der IRM-Dienst vorübergehend deaktiviert, um einen Verbindungsdienst zu installieren und zu konfigurieren und die Server neu zu konfigurieren. Danach wird IRM wieder aktiviert.

    Dies ist die einzige Dienstunterbrechung während der Migration.

- **Wenn Sie Ihren eigenen Azure Information Protection-Mandantenschlüssel mithilfe eines HSM-geschützten Schlüssels verwalten möchten:**

    - Für diese optionale Konfiguration sind Azure Key Vault und ein Azure-Abonnement erforderlich, das Key Vault mit HSM-geschützten Schlüsseln unterstützt. Weitere Informationen finden Sie auf der [Seite Azure Key Vault Preise](https://azure.microsoft.com/pricing/details/key-vault/). 


### <a name="cryptographic-mode-considerations"></a>Überlegungen zum Kryptografiemodus

Wenn Ihr Cluster von AD RMS sich aktuell im Kryptografiemodus 1 befindet, aktualisieren Sie das Cluster nicht auf Kryptografiemodus 2, bevor Sie mit der Migration beginnen. Migrieren Sie stattdessen im Kryptografiemodus 1, und dann können Sie Ihren Mandantenschlüssel am Ende der Migration im Rahmen der Aufgaben nach der Migration neu erstellen.

So bestätigen Sie den AD RMS Kryptografiemodus für Windows Server 2012 R2 und Windows 2012: **AD RMS Cluster** Eigenschaften > Registerkarte " **Allgemein** ". 

### <a name="migration-limitations"></a>Einschränkungen bei der Migration

- Wenn Sie Software und Clients verwenden, die nicht vom Rights Management-Dienst von Azure Information Protection unterstützt werden, können diese weder Inhalte schützen noch Inhalte nutzen, die durch Azure Rights Management geschützt sind. Überprüfen Sie die Abschnitte unterstützte Anwendungen und Clients unter [Anforderungen für Azure Information Protection](./requirements.md).

- Wenn Ihre AD RMS-Bereitstellung so konfiguriert ist, um mit externen Partnern zusammenzuarbeiten (z.B. mithilfe von vertrauenswürdigen Benutzerdomänen oder in einem Verbund), müssen diese ebenfalls zu Azure Information Protection migrieren – entweder zur gleichen Zeit wie Sie oder so bald wie möglich danach. Damit der Zugriff auf Inhalte, die Ihre Organisation zuvor mit Azure Information Protection geschützt hat, weiterhin möglich ist, müssen Ihre Partner ähnliche Änderungen an der Clientkonfiguration wie Sie vornehmen (in diesem Dokument erläutert).
    
    Aufgrund der möglichen Konfigurationsvarianten Ihrer Partner können in diesem Dokument keine genauen Anweisungen für diese Neukonfiguration gegeben werden. Sehen Sie sich jedoch den nächsten Abschnitt an, in dem Sie Unterstützung beim Planen finden. Um zusätzliche Hilfe zu erhalten, [wenden Sie sich an den Microsoft-Support](./information-support.md#support-options-and-community-resources).

## <a name="migration-planning-if-you-collaborate-with-external-partners"></a>Migrationsplanung, wenn Sie mit externen Partnern zusammenarbeiten

Schließen Sie Ihre AD RMS-Partner in Ihre Planungsphase für die Migration ein, da sie ebenfalls zu Azure Information Protection migrieren müssen. Bevor Sie die folgenden Schritte für die Migration ausführen, stellen Sie sicher, dass Folgendes vorhanden ist:

- Ihre Partner verfügen über einen Azure Active Directory-Mandanten, der den Azure Rights Management-Dienst unterstützt.  
    
    Sie haben beispielsweise ein Office 365 E3- oder E5-Abonnement oder ein Enterprise Mobility + Security-Abonnement oder ein eigenständiges Abonnement für Azure Information Protection.

- Der Azure Rights Management-Dienst ist noch nicht aktiviert, jedoch kennen sie die Azure Rights Management-Dienst-URL.

    Sie erhalten diese Informationen, indem Sie das Azure Rights Management-Tool installieren, eine Verbindung mit dem Dienst herstellen ([Connect-aipservice](/powershell/module/aipservice/connect-aipservice)) und anschließend Ihre Mandanten Informationen für den Azure Rights Management-Dienst ([Get-aipserviceconfiguration](/powershell/module/aipservice/get-aipserviceconfiguration)) anzeigen.

- Ihnen werden die URLs für ihre AD RMS-Cluster und die Azure Rights Management-Dienst-URL bereitgestellt, damit Sie Ihre migrierten Clients so konfigurieren können, dass sie Anfragen für ihren von AD RMS geschützten Inhalt an den Azure Rights Management-Dienst ihres Mandanten umleiten können. Hinweise zum Konfigurieren von Clientumleitungen finden Sie in Schritt 7.

- Sie importieren ihre AD RMS-Clusterstammschlüssel (SLC) in ihren Mandanten, bevor Sie beginnen, Ihre Benutzer zu migrieren. Auf ähnliche Weise müssen Sie Ihre AD RMS-Clusterstammschlüssel importieren, bevor Ihre Partner beginnen, ihre Benutzer zu migrieren. Anweisungen zum Importieren des Schlüssels werden in diesem Migrationsprozess ( [Schritt 4) behandelt. Exportieren Sie Konfigurationsdaten aus AD RMS, und importieren Sie Sie in Azure Information Protection](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection). 

## <a name="overview-of-the-steps-for-migrating-ad-rms-to-azure-information-protection"></a>Übersicht über die Schritte zur Migration von AD RMS zu Azure Information Protection

Die Migrationsschritte können in fünf Phasen unterteilt werden, die zu unterschiedlichen Zeiten und von verschiedenen Administratoren ausgeführt werden können.

### <a name="phase-1-migration-preparation"></a>Phase 1: Vorbereiten der Migration

Weitere Informationen finden Sie unter [**Phase 1: Migrations Vorbereitung**](migrate-from-ad-rms-phase1.md).

**Schritt 1: Installieren des aipservice-PowerShell-Moduls und identifizieren ihrer Mandanten-URL**

Der Migrationsprozess erfordert, dass Sie mindestens ein PowerShell-Cmdlet aus dem aipservice-Modul ausführen. Sie müssen die Azure Rights Management-Dienst-URL Ihres Mandanten kennen, um viele der Migrationsschritte abschließen zu können. Sie können diesen Wert mithilfe von PowerShell identifizieren.

**Schritt 2: Vorbereiten der Client Migration**

Wenn Sie nicht alle Clients auf einmal migrieren können, sondern die Migration in Batches ausführen werden, verwenden Sie Onboardingsteuerelemente, und stellen Sie ein Skript zur Ausführung vor der Migration bereit. Wenn Sie allerdings alles gleichzeitig migrieren, anstatt die Migration in Phasen abzuwickeln, können Sie diesen Schritt überspringen.

**Schritt 3: Vorbereiten Ihrer Exchange-Bereitstellung für die Migration**

Dieser Schritt ist erforderlich, wenn Sie derzeit die IRM-Funktion von Exchange Online oder Exchange lokal zum Schutz von E-Mails nutzen. Wenn Sie allerdings alles gleichzeitig migrieren, anstatt die Migration in Phasen abzuwickeln, können Sie diesen Schritt überspringen.

### <a name="phase-2-server-side-configuration-for-ad-rms"></a>Phase 2: Server seitige Konfiguration für AD RMS

Weitere Informationen finden Sie unter [**Phase 2: Server seitige Konfiguration für AD RMS**](migrate-from-ad-rms-phase2.md).

**Schritt 4: Exportieren Sie Konfigurationsdaten aus AD RMS, und importieren Sie Sie in Azure Information Protection**

Sie exportieren die Konfigurationsdaten (Schlüssel, Vorlagen, URLs) aus AD RMS in eine XML-Datei und laden dann diese Datei mithilfe des Import-AipServiceTpd PowerShell-Cmdlets aus Azure Information Protection in den Azure Rights Management-Dienst hoch. Danach ermitteln Sie, welcher importierte SLC-Schlüssel (Server Licensor Certificate) als Mandantenschlüssel für den Azure Rights Management-Dienst verwendet werden soll. Je nach AD RMS-Schlüsselkonfiguration sind möglicherweise weitere Schritte erforderlich:

- **Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln**:

    Zentral verwaltete, kennwortbasierte Schlüssel in AD RMS zu einem von Microsoft verwalteten Azure Information Protection-Mandantenschlüssel. Dies ist der einfachste Migrationspfad, bei dem keine weiteren Schritte erforderlich sind.

- **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln:**

    Schlüssel, die von einem HSM für AD RMS in einem vom Kunden verwalteten Azure Information Protection-Mandantenschlüssel gespeichert werden (das „Bring Your Own Key“- oder BYOK-Szenario). Dies erfordert zusätzliche Schritte zum Übertragen des Schlüssels aus Ihrem lokalen nchiffre-HSM in Azure Key Vault und Autorisieren des Azure Rights Management-Dienstanbieter, diesen Schlüssel zu verwenden. Ihre vorhandenen HSM-geschützten Schlüssel müssen modulgeschützt sein. OCS-geschützte Schlüssel werden von den Rights Management-Services nicht unterstützt.

- **Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln**:

    Zentral verwaltete, kennwortbasierte Schlüssel in AD RMS zu einem kundenverwalteten Azure Information Protection-Mandantenschlüssel (das „Bring Your Own Key“- oder BYOK-Szenario). Dies erfordert die meisten Konfigurationsschritte, da Sie zunächst den Software Schlüssel extrahieren und in ein lokales HSM importieren und dann die zusätzlichen Schritte ausführen müssen, um den Schlüssel aus Ihrem lokalen nchiffre-HSM in ein Azure Key Vault HSM zu übertragen und den Azure Rights Management-Dienst zu autorisieren, den Schlüssel Tresor zu verwenden, in dem der Schlüssel gespeichert wird.

**Schritt 5: Aktivieren des Azure-Rights Management Dienstanbieter**

Falls möglich, führen Sie diesen Schritt nach dem Importvorgang und nicht davor aus. Wenn der Dienst vor dem Import aktiviert wurde, sind zusätzliche Schritte erforderlich.

**Schritt 6: Konfigurieren importierter Vorlagen**

Wenn Sie Ihre Vorlagen für Benutzerrechterichtlinien importieren, lautet deren Status "Archiviert". Falls Benutzer in der Lage sein sollen, diese anzuzeigen und zu verwenden, müssen Sie den Vorlagenstatus im klassischen Azure-Portal in „Veröffentlicht“ ändern.


### <a name="phase-3-client-side-configuration"></a>Phase 3: Client seitige Konfiguration

Weitere Informationen finden Sie unter [**Phase 3: Client seitige Konfiguration**](migrate-from-ad-rms-phase3.md).

**Schritt 7: Erneutes Konfigurieren von Windows-Computern zur Verwendung von Azure Information Protection**

Vorhandene Windows-Computer müssen neu konfiguriert werden, um den Azure Rights Management-Dienst anstelle von AD RMS zu verwenden. Dieser Schritt gilt für Computer in Ihrer Organisation und für Computer in Partnerorganisationen, wenn Sie mit diesen zusammengearbeitet haben, während AS RMS ausgeführt wurde.

### <a name="phase-4-supporting-services-configuration"></a>Phase 4: unterstützen der Dienst Konfiguration

Weitere Informationen finden Sie [**unter Phase 4: unterstützen der Dienst Konfiguration**](migrate-from-ad-rms-phase4.md).

**Schritt 8: Konfigurieren der IRM-Integration mit Exchange Online**

Dieser Schritt schließt die AD RMS-Migration für Exchange Online ab, damit der Dienst nun den Azure Rights Management-Dienst verwenden kann.

**Schritt 9: Konfigurieren der IRM-Integration für Exchange Server und SharePoint Server**

Dieser Schritt schließt die AD RMS-Migration für Exchange oder SharePoint lokal ab, und diese Dienste können nun den Azure Rights Management-Dienst verwenden, der die Bereitstellung des Rights Management-Connectors erfordert.

### <a name="phase-5-post-migration-tasks"></a>Phase 5: Aufgaben nach der Migration

Weitere Informationen finden Sie unter [**Phase 5: Aufgaben nach der Migration**](migrate-from-ad-rms-phase5.md).

**Schritt 10: Aufheben der Bereitstellung von AD RMS**

Wenn sichergestellt ist, dass alle Windows-Computer den Azure Rights Management-Dienst verwenden und nicht mehr auf die AD RMS-Server zugreifen, können Sie Ihre AD RMS-Bereitstellung außer Betrieb setzen.

**Schritt 11: Durchführen von Clientmigrationstasks**

Wenn Sie die [Erweiterungen für mobile Geräte](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574(v=ws.11)) zur Unterstützung mobiler Geräte wie iOS-Telefonen und iPads, Android-Telefonen und Tablets, Windows-Smartphones und -Tablets und Mac-Computern bereitgestellt haben, müssen Sie die SRV-Einträge im DNS entfernen, mit denen diese Clients zu AD RMS umgeleitet wurden. 
    
Die Onboarding-Steuerelemente, die Sie während der Vorbereitungsphase konfiguriert haben, werden nicht länger benötigt. Wenn Sie allerdings keine Onboarding-Steuerelemente verwendet haben, weil Sie sich dafür entschieden haben, alles gleichzeitig zu migrieren, anstatt die Migration in Phasen abzuwickeln, können Sie die Anweisungen zum Entfernen von Onboarding-Steuerelementen überspringen.
    
Wenn Office 2010 auf Ihren Windows-Computern ausgeführt wird, überprüfen Sie, ob Sie den Task **Verwaltung der AD RMS-Vorlagen für Benutzerrechterichtlinien (Automatisiert)** deaktivieren müssen.

> [!IMPORTANT]
> Der erweiterte Support für Office 2010 endete am 13. Oktober 2020. Weitere Informationen finden Sie unter [AIP und ältere Windows- und Office-Versionen](known-issues.md#aip-and-legacy-windows-and-office-versions).

**Schritt 12: neuschlüssel Ihres Azure Information Protection Mandanten Schlüssels**

Dieser Schritt wird empfohlen, wenn Sie sich vor der Migration nicht im Kryptografiemodus 2 befunden haben.

## <a name="next-steps"></a>Nächste Schritte
Um die Migration zu starten, wechseln Sie zu [Phase 1: Vorbereitung](migrate-from-ad-rms-phase1.md).