---
title: Migrieren von AD RMS-Azure Information Protection
description: Anweisungen zum Migrieren Ihrer AD RMS-Bereitstellung (Active Directory Rights Management Services) zu Azure Information Protection. Nach der Migration haben Benutzer weiter Zugriff auf Dokumente und E-Mail-Nachrichten, die Ihre Organisation mithilfe von AD RMS geschützt hat. Für neue zu schützende Inhalte wird Azure Information Protection verwendet.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/11/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 714d5ca28df5ab47fa66ca59a21929bcd7b69d9c
ms.sourcegitcommit: b1e08bc29d50187532f00dc215ab331e0a7dbebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2019
ms.locfileid: "55146773"
---
# <a name="migrating-from-ad-rms-to-azure-information-protection"></a>Migrieren von AD RMS zu Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Befolgen Sie die nachstehenden Anweisungen, um Ihre AD RMS-Bereitstellung (Active Directory Rights Management Services) zu Azure Information Protection zu migrieren. 

Nach der Migration werden Ihre AD RMS-Server nicht mehr verwendet, aber Benutzer haben weiter Zugriff auf Dokumente und E-Mail-Nachrichten, die Ihre Organisation mithilfe von AD RMS geschützt hat. Für neue zu schützende Inhalte wird Azure Rights Management Service (Azure RMS) von Azure Information Protection verwendet.

Nicht sicher, ob diese Migration von AD RMS für Ihre Organisation geeignet ist?

- Eine Einführung in Azure Information Protection finden Sie unter [Was ist Azure Information Protection?](./what-is-information-protection.md).

- Einen Vergleich von Azure Information Protection mit AD RMS finden Sie unter [Vergleich von Azure Information Protection und AD RMS](./compare-on-premise.md).

## <a name="recommended-reading-before-you-migrate-to-azure-information-protection"></a>Empfohlene Lektüre vor der Migration zu Azure Information Protection

Die folgende Dokumentation ist zwar nicht zwingend erforderlich – es empfiehlt sich dennoch, sie zu lesen, bevor Sie mit der Migration beginnen. Sie werden besser verstehen, wie die für Ihre Migration relevante Technologie funktioniert.

- [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](./plan-implement-tenant-key.md): Machen Sie sich mit den Schlüsselverwaltungsoptionen für Ihren Azure Information Protection-Mandanten vertraut. Die Entsprechung Ihres SLC-Schlüssels (Server Licensor Certificate, lizenzgebendes Serverzertifikat) wird entweder von Microsoft (Standard) oder Ihnen („Bring Your Own Key“- bzw. BYOK-Konfiguration) verwaltet. 

- [RMS-Diensterkennung](./rms-client/client-deployment-notes.md#rms-service-discovery): In diesem Abschnitt des RMS-Clientbereitstellungshinweises wird erläutert, dass die Reihenfolge für die Dienstermittlung **Registrierung**, dann **SCP** und dann **Cloud** lautet. Wenn der Dienstverbindungspunkt während des Migrationsvorgangs noch installiert ist, konfigurieren Sie Clients mit Registrierungseinstellungen für Ihren Azure Information Protection-Mandanten so, dass sie nicht den vom Dienstverbindungspunkt zurückgegebenen AD RMS-Cluster verwenden.

- [Übersicht über den Microsoft Rights Management-Connector](./deploy-rms-connector.md#overview-of-the-microsoft-rights-management-connector): In diesem Abschnitt der Dokumentation zum RMS-Connector wird erläutert, wie sich Ihre lokalen Server mit dem Azure Rights Management-Dienst verbinden können, um Dokumente und E-Mails zu schützen.

Wenn Sie mit der Funktionsweise von AD RMS vertraut sind, kann es hilfreich sein, [Funktionsweise von Azure RMS: Hinter den Kulissen](./how-does-it-work.md) zu lesen, um zu bestimmen, welche Technologieprozesse für die Cloudversion gleich oder unterschiedlich sind.

## <a name="prerequisites-for-migrating-ad-rms-to-azure-information-protection"></a>Voraussetzungen für die Migration von AD RMS zu Azure Information Protection

Stellen Sie vor der Migration zu Azure Information Protection sicher, dass die folgenden Voraussetzungen erfüllt sind und Sie alle etwaigen Einschränkungen kennen.

- **Unterstützte RMS-Bereitstellung:**
    
  - Die folgenden AD RMS-Versionen unterstützen die Migration zu Azure Information Protection:
    
      - Windows Server 2008 R2 (x64)
        
      - Windows Server 2012 (x64)
        
      - Windows Server 2012 R2 (x64)
        
      - Windows Server 2016 (x64)
        
  - Alle gültigen AD RMS-Topologien werden unterstützt:
    
      - Einzelne Gesamtstruktur, einzelner RMS-Cluster
        
      - Einzelne Gesamtstruktur, mehrere reine RMS-Lizenzierungscluster
        
      - Mehrere Gesamtstrukturen, mehrere RMS-Cluster
        
    Hinweis: Mehrere AD RMS-Cluster werden standardmäßig zu einem einzelnen Azure Information Protection-Mandanten migriert. Wenn Sie separate Azure Information Protection-Mandanten wünschen, müssen Sie sie als getrennte Migrationen behandeln. Ein Schlüssel von einem RMS-Cluster kann nur in einen einzigen Mandanten importiert werden.

- **Alle Anforderungen für die Ausführung von Azure Information Protection, einschließlich eines Azure Information Protection-Abonnements (Azure Rights Management Service ist nicht aktiviert):**

    Siehe [Anforderungen für Azure Information Protection](./requirements.md).

    Beachten Sie Folgendes: Wenn Sie über Computer verfügen, auf denen Office 2010 ausgeführt wird, müssen Sie den Azure Information Protection-Client installieren, da dieser Client die Möglichkeit bietet, Benutzer für Clouddienste zu authentifizieren. Für neuere Versionen von Office ist der Azure Information Protection-Client für die Klassifizierung und Bezeichnung erforderlich und ist optional, wird aber empfohlen, wenn Sie nur Daten schützen möchten. Weitere Informationen finden Sie unter [Azure Information Protection-Client – Administratorhandbuch](./rms-client/client-admin-guide.md).

    Sie benötigen zwar ein Azure Information Protection-Abonnement, bevor Sie von AD RMS aus migrieren können, aber wir empfehlen, den Rights Management-Dienst für Ihren Mandanten nicht vor dem Start der Migration zu aktivieren. Sie führen diesen Aktivierungsschritt während der Migration aus, nachdem Sie die Schlüssel und Vorlagen aus AD RMS exportiert und in Ihren Azure Information Protection-Mandanten importiert haben. Wenn der Rights Management-Dienst bereits aktiviert wurde, können Sie dennoch von AD RMS migrieren, aber es sind einige zusätzliche Schritte notwendig.


- **Vorbereitung für Azure Information Protection:**

  - Verzeichnissynchronisierung zwischen Ihrem lokalen Verzeichnis und Azure Active Directory

  - E-Mail-aktivierte Gruppen in Azure Active Directory

    Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

- **Wenn Sie die IRM-Funktionalität (Information Rights Management) von Exchange Server** (zum Beispiel Transportregeln und Outlook Web Access) oder SharePoint Server mit AD RMS verwendet haben:

  - Planen Sie einen kurzen Zeitraum ein, in dem IRM nicht auf diesen Servern zur Verfügung steht.
 
    Nach der Migration können Sie IRM weiterhin auf diesen Servern verwenden. Allerdings wird in einem der Migrationsschritte der IRM-Dienst vorübergehend deaktiviert, um einen Verbindungsdienst zu installieren und zu konfigurieren und die Server neu zu konfigurieren. Danach wird IRM wieder aktiviert.

    Dies ist die einzige Dienstunterbrechung während der Migration.

- **Wenn Sie Ihren eigenen Azure Information Protection-Mandantenschlüssel mithilfe eines HSM-geschützten Schlüssels verwalten möchten:**

    - Für diese optionale Konfiguration sind Azure Key Vault und ein Azure-Abonnement erforderlich, das Key Vault mit HSM-geschützten Schlüsseln unterstützt. Weitere Informationen finden Sie auf der [Seite mit den Azure Key Vault-Preisen](https://azure.microsoft.com/pricing/details/key-vault/). 


### <a name="cryptographic-mode-considerations"></a>Überlegungen zum Kryptografiemodus

Wenn Ihr Cluster von AD RMS sich aktuell im Kryptografiemodus 1 befindet, aktualisieren Sie das Cluster nicht auf Kryptografiemodus 2, bevor Sie mit der Migration beginnen. Migrieren Sie stattdessen im Kryptografiemodus 1, und dann können Sie Ihren Mandantenschlüssel am Ende der Migration im Rahmen der Aufgaben nach der Migration neu erstellen.

So bestätigen Sie den AD RMS-Kryptografiemodus:
 
- In Windows Server 2012 R2 und Windows 2012: AD RMS-Clustereigenschaften > Registerkarte **Allgemein**. 

- In Windows Server 2008 R2: Prüfen Sie, ob der Hotfix [RSA key length is increased to 2008 bits for AD RMS in Windows Server 2008 R2 and in Windows Server 2008](https://support.microsoft.com/help/2627272/rsa-key-length-is-increased-to-2048-bits-for-ad-rms-in-windows-server ) (RSA-Schlüssellänge für AD RMS wurde in Windows Server 2008 R2 und Windows Server 2008 auf 2048 Bit erhöht) installiert wurde. Andernfalls wird Ihr AD RMS-Cluster im Kryptografiemodus 1 ausgeführt.

### <a name="migration-limitations"></a>Einschränkungen bei der Migration

- Wenn Sie Softwareanwendungen und Clients verwenden, die nicht vom Rights Management-Dienst von Azure Information Protection unterstützt werden, können diese die Inhalte, die durch Azure Rights Management geschützt sind, weder schützen noch nutzen. Überprüfen Sie unbedingt den Abschnitt zu den unterstützten Anwendungen und Clients unter [Voraussetzungen für Azure Rights Management](./requirements.md).

- Wenn Ihre AD RMS-Bereitstellung so konfiguriert ist, um mit externen Partnern zusammenzuarbeiten (z.B. mithilfe von vertrauenswürdigen Benutzerdomänen oder in einem Verbund), müssen diese ebenfalls zu Azure Information Protection migrieren – entweder zur gleichen Zeit wie Sie oder so bald wie möglich danach. Damit der Zugriff auf Inhalte, die Ihre Organisation zuvor mit Azure Information Protection geschützt hat, weiterhin möglich ist, müssen Ihre Partner ähnliche Änderungen an der Clientkonfiguration wie Sie vornehmen (in diesem Dokument erläutert).
    
    Aufgrund der möglichen Konfigurationsvarianten Ihrer Partner können in diesem Dokument keine genauen Anweisungen für diese Neukonfiguration gegeben werden. Sehen Sie sich jedoch den nächsten Abschnitt an, in dem Sie Unterstützung beim Planen finden. Um zusätzliche Hilfe zu erhalten, [wenden Sie sich an den Microsoft-Support](./information-support.md#support-options-and-community-resources).

## <a name="migration-planning-if-you-collaborate-with-external-partners"></a>Migrationsplanung, wenn Sie mit externen Partnern zusammenarbeiten

Schließen Sie Ihre AD RMS-Partner in Ihre Planungsphase für die Migration ein, da sie ebenfalls zu Azure Information Protection migrieren müssen. Bevor Sie die folgenden Schritte für die Migration ausführen, stellen Sie sicher, dass Folgendes vorhanden ist:

- Ihre Partner verfügen über einen Azure Active Directory-Mandanten, der den Azure Rights Management-Dienst unterstützt.  
    
    Sie haben beispielsweise ein Office 365 E3- oder E5-Abonnement oder ein Enterprise Mobility + Security-Abonnement oder ein eigenständiges Abonnement für Azure Information Protection.

- Der Azure Rights Management-Dienst ist noch nicht aktiviert, jedoch kennen sie die Azure Rights Management-Dienst-URL.

    Sie erhalten diese Informationen, indem sie das Azure Rights Management-Tool installieren, eine Verbindung mit dem Dienst herstellen ([Connect-Aadrmservice](/powershell/aadrm/vlatest/connect-aadrmservice)) und anschließend ihre Mandanteninformationen für den Azure Rights Management-Dienst anzeigen ([Get-AadrmConfiguration](/powershell/aadrm/vlatest/get-aadrmconfiguration)).

- Ihnen werden die URLs für ihre AD RMS-Cluster und die Azure Rights Management-Dienst-URL bereitgestellt, damit Sie Ihre migrierten Clients so konfigurieren können, dass sie Anfragen für ihren von AD RMS geschützten Inhalt an den Azure Rights Management-Dienst ihres Mandanten umleiten können. Hinweise zum Konfigurieren von Clientumleitungen finden Sie in Schritt 7.

- Sie importieren ihre AD RMS-Clusterstammschlüssel (SLC) in ihren Mandanten, bevor Sie beginnen, Ihre Benutzer zu migrieren. Auf ähnliche Weise müssen Sie Ihre AD RMS-Clusterstammschlüssel importieren, bevor Ihre Partner beginnen, ihre Benutzer zu migrieren. Anweisungen für das Importieren des Schlüssels werden in diesem Migrationsprozess erläutert: [Schritt 4: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure Information Protection](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection). 

## <a name="overview-of-the-steps-for-migrating-ad-rms-to-azure-information-protection"></a>Übersicht über die Schritte zur Migration von AD RMS zu Azure Information Protection

Die Migrationsschritte können in fünf Phasen unterteilt werden, die zu unterschiedlichen Zeiten und von verschiedenen Administratoren ausgeführt werden können.

[**PHASE 1: VORBEREITUNG DER MIGRATION**](migrate-from-ad-rms-phase1.md)

- **Schritt 1: Installieren des AADRM-PowerShell-Moduls und Identifizieren Ihrer Mandanten-URL**

    Sie müssen eines oder mehrere der PowerShell-Cmdlets aus dem AADRM-Modul für den Migrationsvorgang ausführen. Sie müssen die Azure Rights Management-Dienst-URL Ihres Mandanten kennen, um viele der Migrationsschritte abschließen zu können. Sie können diesen Wert mithilfe von PowerShell identifizieren.

- **Schritt 2: Vorbereitung für die Clientmigration**

    Wenn Sie nicht alle Clients auf einmal migrieren können, sondern die Migration in Batches ausführen werden, verwenden Sie Onboardingsteuerelemente, und stellen Sie ein Skript zur Ausführung vor der Migration bereit. Wenn Sie allerdings alles gleichzeitig migrieren, anstatt die Migration in Phasen abzuwickeln, können Sie diesen Schritt überspringen.

- **Schritt 3: Vorbereiten Ihrer Exchange-Bereitstellung für die Migration**

    Dieser Schritt ist erforderlich, wenn Sie derzeit die IRM-Funktion von Exchange Online oder Exchange lokal zum Schutz von E-Mails nutzen. Wenn Sie allerdings alles gleichzeitig migrieren, anstatt die Migration in Phasen abzuwickeln, können Sie diesen Schritt überspringen.

[**PHASE 2: SERVERSEITIGE KONFIGURATION FÜR AD RMS**](migrate-from-ad-rms-phase2.md)

- **Schritt 4: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure Information Protection**

    Sie exportieren die Konfigurationsdaten (Schlüssel, Vorlagen, URLs) aus AD RMS in eine XML-Datei und laden dann diese Datei mithilfe des PowerShell-Cmdlets Import-AadrmTpd in den Azure Rights Management-Dienst von Azure Information Protection hoch. Danach ermitteln Sie, welcher importierte SLC-Schlüssel (Server Licensor Certificate) als Mandantenschlüssel für den Azure Rights Management-Dienst verwendet werden soll. Je nach AD RMS-Schlüsselkonfiguration sind möglicherweise weitere Schritte erforderlich:

    - **Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln**:

        Zentral verwaltete, kennwortbasierte Schlüssel in AD RMS zu einem von Microsoft verwalteten Azure Information Protection-Mandantenschlüssel. Dies ist der einfachste Migrationspfad, bei dem keine weiteren Schritte erforderlich sind.

    - **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln:**

        Schlüssel, die von einem HSM für AD RMS in einem vom Kunden verwalteten Azure Information Protection-Mandantenschlüssel gespeichert werden (das „Bring Your Own Key“- oder BYOK-Szenario). Hier sind zusätzliche Schritte zum Übertragen des Schlüssels aus Ihrem lokalen Thales-HSM an Azure Key Vault und zum Autorisieren des Azure Rights Management-Diensts für die Verwendung dieses Schlüssels erforderlich. Ihre vorhandenen HSM-geschützten Schlüssel müssen modulgeschützt sein. OCS-geschützte Schlüssel werden von den Rights Management-Services nicht unterstützt.

    - **Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln**:

        Zentral verwaltete, kennwortbasierte Schlüssel in AD RMS zu einem kundenverwalteten Azure Information Protection-Mandantenschlüssel (das „Bring Your Own Key“- oder BYOK-Szenario). Dieses Szenario erfordert die meisten Konfigurationsschritte, da Sie zunächst den Softwareschlüssel extrahieren und in ein lokales HSM importieren und dann zusätzliche Schritte zum Übertragen des Schlüssels aus Ihrem lokalen Thales-HSM in das Azure Key Vault-HSM und zur Autorisierung des Azure Rights Management-Diensts für die Verwendung des Schlüsseltresors, in dem der Schlüssel gespeichert wird, ausführen müssen.

- **Schritt 5: Aktivieren des Azure Rights Management-Diensts**

    Falls möglich, führen Sie diesen Schritt nach dem Importvorgang und nicht davor aus. Wenn der Dienst vor dem Import aktiviert wurde, sind zusätzliche Schritte erforderlich.

- **Schritt 6: Konfigurieren importierter Vorlagen**

    Wenn Sie Ihre Vorlagen für Benutzerrechterichtlinien importieren, lautet deren Status "Archiviert". Falls Benutzer in der Lage sein sollen, diese anzuzeigen und zu verwenden, müssen Sie den Vorlagenstatus im klassischen Azure-Portal in „Veröffentlicht“ ändern.


[**PHASE 3: CLIENTSEITIGE KONFIGURATION**](migrate-from-ad-rms-phase3.md)

- **Schritt 7: Neukonfigurieren von Windows-Computern zur Verwendung von Azure Information Protection**

    Vorhandene Windows-Computer müssen neu konfiguriert werden, um den Azure Rights Management-Dienst anstelle von AD RMS zu verwenden. Dieser Schritt gilt für Computer in Ihrer Organisation und für Computer in Partnerorganisationen, wenn Sie mit diesen zusammengearbeitet haben, während AS RMS ausgeführt wurde.

[**PHASE 4: UNTERSTÜTZUNG DER DIENSTEKONFIGURATION**](migrate-from-ad-rms-phase4.md)

- **Schritt 8: Konfigurieren der IRM-Integration für Exchange Online**

    Dieser Schritt schließt die AD RMS-Migration für Exchange Online ab, damit der Dienst nun den Azure Rights Management-Dienst verwenden kann.

- **Schritt 9: Konfigurieren der IRM-Integration für Exchange Server und SharePoint Server**

    Dieser Schritt schließt die AD RMS-Migration für Exchange oder SharePoint lokal ab, und diese Dienste können nun den Azure Rights Management-Dienst verwenden, der die Bereitstellung des Rights Management-Connectors erfordert.


[**PHASE 5: AUFGABEN NACH DER MIGRATION**](migrate-from-ad-rms-phase5.md )

- **Schritt 10: Aufheben der Bereitstellung von AD RMS**

    Wenn sichergestellt ist, dass alle Windows-Computer den Azure Rights Management-Dienst verwenden und nicht mehr auf die AD RMS-Server zugreifen, können Sie Ihre AD RMS-Bereitstellung außer Betrieb setzen.

- **Schritt 11: Durchführen der Clientmigrationstasks**

    Wenn Sie die [Erweiterungen für mobile Geräte](https://technet.microsoft.com/library/dn673574.aspx) zur Unterstützung mobiler Geräte wie iOS-Telefonen und iPads, Android-Telefonen und Tablets, Windows-Smartphones und -Tablets und Mac-Computern bereitgestellt haben, müssen Sie die SRV-Einträge im DNS entfernen, mit denen diese Clients zu AD RMS umgeleitet wurden. 
    
    Die Onboarding-Steuerelemente, die Sie während der Vorbereitungsphase konfiguriert haben, werden nicht länger benötigt. Wenn Sie allerdings keine Onboarding-Steuerelemente verwendet haben, weil Sie sich dafür entschieden haben, alles gleichzeitig zu migrieren, anstatt die Migration in Phasen abzuwickeln, können Sie die Anweisungen zum Entfernen von Onboarding-Steuerelementen überspringen.
    
    Wenn Office 2010 auf Ihren Windows-Computern ausgeführt wird, überprüfen Sie, ob Sie den Task **Verwaltung der AD RMS-Vorlagen für Benutzerrechterichtlinien (Automatisiert)** deaktivieren müssen.

- **Schritt 12: Neuerstellen Ihres Azure Information Protection-Mandantenschlüssels**

    Dieser Schritt wird empfohlen, wenn Sie sich vor der Migration nicht im Kryptografiemodus 2 befunden haben.


## <a name="next-steps"></a>Nächste Schritte
Um die Migration zu starten, wechseln Sie zu [Phase 1: Vorbereitung](migrate-from-ad-rms-phase1.md).

