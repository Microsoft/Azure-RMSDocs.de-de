---
title: Migrieren von AD RMS-Azure Information Protection
description: "Anweisungen zum Migrieren Ihrer AD RMS-Bereitstellung (Active Directory Rights Management Services) zu Azure Information Protection. Nach der Migration haben Benutzer weiter Zugriff auf Dokumente und E-Mail-Nachrichten, die Ihre Organisation mithilfe von AD RMS geschützt hat. Für neue zu schützende Inhalte wird Azure Information Protection verwendet."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 12bd5b89cf9957521c7d7b4fb573e4ffcd6c865d
ms.lasthandoff: 02/24/2017


---

# <a name="migrating-from-ad-rms-to-azure-information-protection"></a>Migrieren von AD RMS zu Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Befolgen Sie die nachstehenden Anweisungen, um Ihre AD RMS-Bereitstellung (Active Directory Rights Management Services) zu Azure Information Protection zu migrieren. Nach der Migration haben Benutzer weiter Zugriff auf Dokumente und E-Mail-Nachrichten, die Ihre Organisation mithilfe von AD RMS geschützt hat. Für neue zu schützende Inhalte wird der Azure Rights Management-Dienst von Azure Information Protection verwendet.

Nicht sicher, ob diese Migration von AD RMS für Ihre Organisation geeignet ist?

-   Eine Einführung in Azure Information Protection finden Sie unter [Was ist Azure Information Protection?](../understand-explore/what-is-information-protection.md).

-   Einen Vergleich von Azure Information Protection mit AD RMS finden Sie unter [Vergleich von Azure Information Protection und AD RMS](../understand-explore/compare-azure-rms-ad-rms.md).

## <a name="recommended-reading-before-you-migrate-to-azure-information-protection"></a>Empfohlene Lektüre vor der Migration zu Azure Information Protection

Wenngleich nicht erforderlich, kann es hilfreich sein, die folgenden Dokumente zu lesen, ehe Sie mit der Migration beginnen, damit Sie besser verstehen, wie die Technologie funktioniert, sobald dies in Ihrem Migrationsschritt relevant ist:

- [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md): Machen Sie sich mit den Schlüsselverwaltungsoptionen für Ihren Azure Information Protection-Mandanten vertraut. Die Entsprechung Ihres SLC-Schlüssels (Server Licensor Certificate, lizenzgebendes Serverzertifikat) wird entweder von Microsoft (Standard) oder Ihnen („Bring Your Own Key“- oder BYOK-Konfiguration) verwaltet. 

- [RMS-Dienstermittlung](../rms-client/client-deployment-notes.md#rms-service-discovery): In diesem Abschnitt des RMS-Client-Bereitstellungshinweises wird erklärt, dass die Reihenfolge für die Dienstermittlung **Registrierung** > **Dienstverbindungspunkt** > **Cloud** ist. Wenn der Dienstverbindungspunkt während des Migrationsvorgangs noch installiert ist, konfigurieren Sie Clients mit Registrierungseinstellungen für Ihren Azure Information Protection-Mandanten so, dass sie nicht den vom Dienstverbindungspunkt zurückgegebenen AD RMS-Cluster verwenden.

- [Übersicht über den Microsoft Rights Management-Connector](../deploy-use/deploy-rms-connector.md#overview-of-the-microsoft-rights-management-connector): In diesem Abschnitt der Dokumentation zum RMS-Connector wird erläutert, wie Ihre lokalen Server sich mit dem Azure Rights Management-Dienst verbinden können, um Dokumente und E-Mails zu schützen.

Wenn Sie mit der Funktionsweise von AD RMS vertraut sind, kann es hilfreich sein, [Funktionsweise von Azure RMS: Hinter den Kulissen](../understand-explore/how-does-it-work.md) zu lesen, um zu bestimmen, welche Technologieprozesse für die Cloudversion gleich oder unterschiedlich sind.

## <a name="prerequisites-for-migrating-ad-rms-to-azure-information-protection"></a>Voraussetzungen für die Migration von AD RMS zu Azure Information Protection
Stellen Sie vor der Migration zu Azure Information Protection sicher, dass die folgenden Voraussetzungen erfüllt sind und Sie alle etwaigen Einschränkungen kennen.

- **Unterstützte RMS-Bereitstellung:**
    
    - Die folgenden AD RMS-Versionen unterstützen die Migration zu Azure Information Protection:
    
        - Windows Server 2008 R2 (x64)
        
        - Windows Server 2012 (x64)
        
        - Windows Server 2012 R2 (x64)
        
        - Windows Server 2016 (x64)
        
    - Kryptografiemodus 2:

        - Die AD RMS-Server und -Clients müssen vor Beginn der Migration zu Azure Information Protection im Kryptografiemodus 2 ausgeführt werden.
        
        Obwohl das aktuelle lizenzgebende Serverzertifikat (Server Licensor Certificate, SLC) den Kryptografiemodus 2 verwenden muss, werden vorherige Schlüssel, die für den Kryptografiemodus 1 konfiguriert wurden, von Azure Information Protection als archivierte Schlüssel unterstützt. Weitere Informationen zu den Kryptografiemodi sowie zum Wechsel zu Kryptografiemodus 2, finden Sie unter [AD RMS-Kryptografiemodi](https://technet.microsoft.com/library/hh867439(v=ws.10).aspx).
        
    - Alle gültigen AD RMS-Topologien werden unterstützt:
    
        - Einzelne Gesamtstruktur, einzelner RMS-Cluster
        
        - Einzelne Gesamtstruktur, mehrere reine RMS-Lizenzierungscluster
        
        - Mehrere Gesamtstrukturen, mehrere RMS-Cluster
        
    Hinweis: Mehrere RMS-Cluster werden standardmäßig zu einem einzelnen Azure Information Protection-Mandanten migriert. Wenn Sie separate Azure Information Protection-Mandanten wünschen, müssen Sie sie als getrennte Migrationen behandeln. Ein Schlüssel von einem RMS-Cluster kann nur in einen einzigen Azure Information Protection-Mandanten importiert werden.

- **Alle Anforderungen für die Ausführung von Azure Information Protection, einschließlich eines Azure Information Protection-Mandanten (nicht aktiviert):**

    Siehe [Anforderungen für Azure Information Protection](../get-started/requirements-azure-rms.md).

    Obwohl Sie einen Azure Information Protection-Mandanten benötigen, damit Sie von AD RMS aus migrieren können, empfehlen wir, den Rights Management-Dienst nicht vor der Migration zu aktivieren. Sie führen diesen Schritt während der Migration aus, nachdem Sie die Schlüssel und Vorlagen aus AD RMS exportiert und in Azure Information Protection importiert haben. Wenn der Rights Management-Dienst jedoch schon aktiviert wurde, können Sie immer noch von AD RMS migrieren.


- **Vorbereitung für Azure Information Protection:**

    - Verzeichnissynchronisierung zwischen Ihrem lokalen Verzeichnis und Azure Active Directory

    - E-Mail-aktivierte Gruppen in Azure Active Directory

    Siehe [Vorbereiten für Azure Information Protection](prepare.md).


- **Wenn Sie die IRM-Funktionalität (Information Rights Management) von Exchange Server** (zum Beispiel Transportregeln und Outlook Web Access) oder SharePoint Server mit AD RMS verwendet haben:

    - Planen Sie einen kurzen Zeitraum ein, in dem IRM nicht auf diesen Servern zur Verfügung steht.
 
    Nach der Migration können Sie IRM weiterhin auf diesen Servern mit dem Azure Rights Management-Dienst verwenden. Allerdings wird in einem der Migrationsschritte der IRM-Dienst vorübergehend deaktiviert, um einen Verbindungsdienst zu installieren und zu konfigurieren und die Server neu zu konfigurieren. Danach wird IRM wieder aktiviert.

    Dies ist die einzige Dienstunterbrechung während der Migration.

- **Wenn Sie Ihren eigenen Azure Information Protection-Mandantenschlüssel mithilfe eines HSM-geschützten Schlüssels verwalten möchten:**

    - Für diese optionale Konfiguration sind Azure Key Vault und ein Azure-Abonnement erforderlich, das Key Vault mit HSM-geschützten Schlüsseln unterstützt. Weitere Informationen finden Sie auf der [Seite mit den Azure Key Vault-Preisen](https://azure.microsoft.com/en-us/pricing/details/key-vault/). 


Einschränkungen:

-   Obwohl der Migrationsvorgang die Migration des Schlüssels Ihres lizenzgebenden Serverzertifikats (SLC) zu einem Hardwaresicherheitsmodul (HSM) für Azure Information Protection unterstützt, wird diese Konfiguration derzeit von Exchange Online für den von Azure Information Protection verwendeten Rights Management-Dienst nicht unterstützt. Wenn Sie nach der Migration zu Azure Information Protection die vollständige IRM-Funktionalität mit Exchange Online nutzen möchten, muss Ihr Azure Information Protection-Mandantenschlüssel [von Microsoft verwaltet](../plan-design/plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok) werden. Sie können IRM auch mit eingeschränkter Funktionalität in Exchange Online ausführen, wenn Ihr Azure Information Protection-Mandant von Ihnen verwaltet wird (BYOK). Weitere Informationen zur Verwendung von Exchange Online mit dem Azure Rights Management-Dienst finden Sie unter [Schritt 6. Konfigurieren der IRM-Integration mit Exchange Online](migrate-from-ad-rms-phase3.md#step-6-configure-irm-integration-for-exchange-online) in diesen Anweisungen.

-   Wenn Sie Software und Clients verwenden, die nicht vom Rights Management-Dienst von Azure Information Protection unterstützt werden, können diese weder Inhalte schützen noch Inhalte nutzen, die durch Azure Rights Management geschützt sind. Überprüfen Sie unbedingt den Abschnitt zu den unterstützten Anwendungen und Clients des Artikels [Voraussetzungen für Azure Rights Management](../get-started/requirements-azure-rms.md).

-   Wenn Sie Ihren lokalen Schlüssel in Azure Information Protection als archiviert importieren (indem Sie die vertrauenswürdige Veröffentlichungsdomäne während des Importvorgangs nicht als aktiv festlegen) und Benutzer in einer phasenweisen Migration in Batches migrieren, sind neu von den migrierten Benutzern geschützte Inhalte nicht für Benutzer verfügbar, die in AD RMS bleiben. Halten Sie in diesem Szenario die Migrationszeit möglichst kurz, und migrieren Sie Benutzer in logischen Gruppen, d. h. wenn Benutzer zusammen arbeiten, sollten sie gemeinsam migriert werden.

    Diese Einschränkung gilt nicht, wenn Sie die vertrauenswürdige Veröffentlichungsdomäne während des Importvorgangs auf aktiv festlegen, da alle Benutzer Inhalte mit dem gleichen Schlüssel schützen werden. Diese Konfiguration wird empfohlen, da sie alle Benutzer unabhängig voneinander und in Ihrem eigenen Tempo migrieren können.

-   Wenn Sie mit externen Partnern zusammenarbeiten (z.B. mithilfe von vertrauenswürdigen Benutzerdomänen oder in einem Verbund), müssen diese ebenfalls zu Azure Information Protection migrieren – entweder zur gleichen Zeit wie Sie oder so bald wie möglich danach. Damit der Zugriff auf Inhalte, die Ihre Organisation zuvor mit Azure Information Protection geschützt hat, weiterhin möglich ist, müssen Ihre Partner ähnliche Änderungen an der Clientkonfiguration wie Sie vornehmen (in diesem Dokument erläutert).

    Aufgrund der möglichen Konfigurationsvarianten Ihrer Partner können in diesem Dokument keine genauen Anweisungen für diese Neukonfiguration gegeben werden. Wenden Sie sich an den [Microsoft Support](../get-started/information-support.md#support-options-and-community-resources), um Hilfe zu erhalten.

## <a name="overview-of-the-steps-for-migrating-ad-rms-to-azure-information-protection"></a>Übersicht über die Schritte zur Migration von AD RMS zu Azure Information Protection


Die Migrationsschritte können in vier Phasen unterteilt werden, die zu unterschiedlichen Zeiten und von verschiedenen Administratoren ausgeführt werden können.

[**PHASE 1: SERVERSEITIGE KONFIGURATION FÜR AD RMS**](migrate-from-ad-rms-phase1.md)

- **Schritt 1: Herunterladen der Azure RMS-Verwaltungstools**

    Während der Migration müssen Sie eine oder mehrere der Windows PowerShell-Cmdlets aus dem Azure RMS-Modul ausgeführt, das mit dem Azure RMS-Verwaltungstool installiert wurde.

- **Schritt 2: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure Information Protection**

    Sie exportieren die Konfigurationsdaten (Schlüssel, Vorlagen, URLs) aus AD RMS in eine XML-Datei und laden dann diese Datei mithilfe des Windows PowerShell-Cmdlets Import-AadrmTpd in den Azure Rights Management-Dienst von Azure Information Protection hoch. Je nach AD RMS-Schlüsselkonfiguration sind möglicherweise weitere Schritte erforderlich:

    - **Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln**:

        Zentral verwaltete, kennwortbasierte Schlüssel in AD RMS zu einem von Microsoft verwalteten Azure Information Protection-Mandantenschlüssel. Dies ist der einfachste Migrationspfad, bei dem keine weiteren Schritte erforderlich sind.

    - **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln:**

        Schlüssel, die von einem HSM für AD RMS in einem vom Kunden verwalteten Azure Information Protection-Mandantenschlüssel gespeichert werden (das „Bring Your Own Key“- oder BYOK-Szenario). Hier sind zusätzliche Schritte zum Übertragen des Schlüssels aus Ihrem lokalen Thales-HSM an Azure Key Vault und zum Autorisieren des Azure Rights Management-Diensts für die Verwendung dieses Schlüssels erforderlich. Ihre vorhandenen HSM-geschützten Schlüssel müssen modulgeschützt sein. OCS-geschützte Schlüssel werden von den Rights Management-Services nicht unterstützt.

    - **Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln**:

        Zentral verwaltete, kennwortbasierte Schlüssel in AD RMS zu einem kundenverwalteten Azure Information Protection-Mandantenschlüssel (das „Bring Your Own Key“- oder BYOK-Szenario). Dieses Szenario erfordert die meisten Konfigurationsschritte, da Sie zunächst den Softwareschlüssel extrahieren und in ein lokales HSM importieren und dann zusätzliche Schritte zum Übertragen des Schlüssels aus Ihrem lokalen Thales-HSM in das Azure Key Vault-HSM und zur Autorisierung des Azure Rights Management-Diensts für die Verwendung des Schlüsseltresors, in dem der Schlüssel gespeichert wird, ausführen müssen.

- **Schritt 3: Aktivieren Ihres Azure Information Protection-Mandanten**

    Falls möglich, führen Sie diesen Schritt nach dem Importvorgang und nicht davor aus.

- **Schritt 4: Konfigurieren importierter Vorlagen**

    Wenn Sie Ihre Vorlagen für Benutzerrechterichtlinien importieren, lautet deren Status "Archiviert". Falls Benutzer in der Lage sein sollen, diese anzuzeigen und zu verwenden, müssen Sie den Vorlagenstatus im klassischen Azure-Portal in „Veröffentlicht“ ändern.


[**PHASE 2: CLIENTSEITIGE KONFIGURATION**](migrate-from-ad-rms-phase2.md)


- **Schritt 5: Neukonfigurieren von Clients zur Verwendung von Azure Information Protection**

    Vorhandene Windows-Computer müssen neu konfiguriert werden, um den Azure Information Protection-Dienst anstelle von AD RMS zu verwenden. Dieser Schritt gilt für Computer in Ihrer Organisation und für Computer in Partnerorganisationen, wenn Sie mit diesen zusammengearbeitet haben, während AS RMS ausgeführt wurde.

    Außerdem müssen Sie, wenn Sie die [Erweiterungen für mobile Geräte](http://technet.microsoft.com/library/dn673574.aspx) zur Unterstützung mobiler Geräte wie iOS-Telefone und iPads, Android-Telefone und Tablets, Windows Phone und Mac-Computer bereitgestellt haben, die SRV-Einträge im DNS entfernen, mit denen diese Clients zu AD RMS umgeleitet wurden.


[**PHASE 3: UNTERSTÜTZUNG DER DIENSTEKONFIGURATION**](migrate-from-ad-rms-phase3.md)


- **Schritt 6: Konfigurieren der IRM-Integration mit Exchange Online**

    Dieser Schritt ist erforderlich, wenn Sie Exchange Online mit dem Azure Rights Management-Dienst von Azure Information Protection verwenden möchten.


- **Schritt 7: Bereitstellen des RMS-Verbindungsdiensts**

    Dieser Schritt ist erforderlich, wenn Sie einen der folgenden lokalen Dienste mit dem Azure Rights Management-Dienst verwenden möchten, um Office-Dokumente und E-Mails zu schützen:

    - Exchange Server (z. B. Transportregeln und Outlook Web Access)

    - SharePoint Server

    - Windows Server mit Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)


[**PHASE 4: AUFGABEN NACH DER MIGRATION**](migrate-from-ad-rms-phase4.md )

- **Schritt 8: Außerbetriebsetzung von AD RMS**

    Wenn sichergestellt ist, dass alle Clients Azure Information Protection verwenden und nicht mehr auf die AD RMS-Server zugreifen, können Sie Ihre AD RMS-Bereitstellung außer Betrieb setzen.


- **Schritt 9: Erneuern Ihres Azure Information Protection-Mandantenschlüssels**

    Dieser Schritt ist optional, wird jedoch empfohlen, wenn Ihre in Schritt 2 ausgewählte Azure Information Protection-Mandantenschlüsseltopologie „von Microsoft verwaltet“ ist. Dieser Schritt ist nicht anwendbar, wenn die ausgewählte Azure Information Protection-Mandantenschlüsseltopologie „vom Kunden verwaltet“ (BYOK) ist.


## <a name="next-steps"></a>Nächste Schritte
Um die Migration zu starten, wechseln Sie zu [Phase 1: Serverseitige Konfiguration](migrate-from-ad-rms-phase1.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

