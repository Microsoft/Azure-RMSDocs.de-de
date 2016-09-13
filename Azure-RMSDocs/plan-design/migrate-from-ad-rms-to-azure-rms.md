---
title: Migration von AD RMS zu Azure Rights Management | Azure RMS
description: "Anweisungen zum Migrieren Ihrer AD RMS-Bereitstellung (Active Directory Rights Management Services) zu Azure Rights Management (Azure RMS). Nach der Migration haben Benutzer weiter Zugriff auf Dokumente und E-Mail-Nachrichten, die Ihre Organisation mithilfe von AD RMS geschützt hat. Für neue zu schützende Inhalte wird Azure RMS verwendet."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ada00b6f6298e7d359c73eb38dfdac169eacb708
ms.openlocfilehash: 6aa75f5e6b326068951b3d4d65f337c15a475029


---

# Migration von AD RMS zu Azure Rights Management

>*Gilt für: Active Directory Rights Management Services, Azure Rights Management*

Befolgen Sie die nachstehenden Anweisungen, um Ihre AD RMS-Bereitstellung (Active Directory Rights Management Services) zu Azure Rights Management (Azure RMS) zu migrieren. Nach der Migration haben Benutzer weiter Zugriff auf Dokumente und E-Mail-Nachrichten, die Ihre Organisation mithilfe von AD RMS geschützt hat. Für neue zu schützende Inhalte wird Azure RMS verwendet.

Nicht sicher, ob diese Migration von AD RMS für Ihre Organisation geeignet ist?

-   Eine Einführung in Azure RMS, die geschäftlichen Probleme, die damit gelöst werden können, die Benutzeroberfläche für Administratoren und Benutzer sowie die Funktionsweise werden unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md) vorgestellt.

-   Einen Vergleich von Azure RMS mit AD RMS finden Sie unter [Vergleich zwischen Azure Rights Management und AD RMS](../understand-explore/compare-azure-rms-ad-rms.md).

## Voraussetzungen für die Migration von AD RMS zu Azure RMS
Stellen Sie vor der Migration zu Azure RMS sicher, dass die folgenden Voraussetzungen erfüllt sind und Sie alle etwaigen Einschränkungen kennen.


- **Unterstützte RMS-Bereitstellung:**
    
    - Die folgenden AD RMS-Versionen unterstützen die Migration zu Azure RMS:
    
        - Windows Server 2008 R2 (x64)
        
        - Windows Server 2012 (x64)
        
        - Windows Server 2012 R2 (x64)
        
    - Kryptografiemodus 2:
    
        - Die AD RMS-Server und Clients müssen vor Beginn der Migration zu Azure RMS im Kryptografiemodus 2 ausgeführt werden. Weitere Informationen finden Sie unter [AD RMS-Kryptografiemodi](https://technet.microsoft.com/library/hh867439(v=ws.10).aspx).
        
    - Alle gültigen AD RMS-Topologien werden unterstützt:
    
        - Einzelne Gesamtstruktur, einzelner RMS-Cluster
        
        - Einzelne Gesamtstruktur, mehrere reine RMS-Lizenzierungscluster
        
        - Mehrere Gesamtstrukturen, mehrere RMS-Cluster
        
    Hinweis: Mehrere RMS-Cluster werden standardmäßig zu einem einzelnen Azure RMS-Mandanten migriert. Wenn Sie getrennte Azure RMS-Mandanten wünschen, müssen Sie sie als weitere Migrationen behandeln. Ein Schlüssel von einem RMS-Cluster kann nur in einen einzigen Azure RMS-Mandanten importiert werden.

- **Alle Anforderungen zum Ausführen von Azure RMS, einschließlich eines Azure RMS-Mandanten (nicht aktiviert):**

    Informationen finden Sie unter [Voraussetzungen für Azure Rights Management](../get-started/requirements-azure-rms.md).

    Obwohl Sie einen Azure RMS-Mandanten benötigen, damit Sie von AD RMS aus migrieren können, empfehlen wir, dass die den Rights Management-Dienst nicht vor der Migration aktivieren. Sie führen diesen Schritt während der Migration aus, nachdem Sie die Schlüssel und Vorlagen aus AD RMS exportiert und in Azure RMS importiert haben. Wenn Azure RMS jedoch schon aktiviert wurde, können Sie immer noch von AD RMS migrieren.


- **Vorbereitung für Azure RMS:**

    - Verzeichnissynchronisierung zwischen Ihrem lokalen Verzeichnis und Azure Active Directory

    - E-Mail-aktivierte Gruppen in Azure Active Directory

    Informationen finden Sie unter [Vorbereiten für Azure Rights Management](prepare.md).


- **Wenn Sie die IRM-Funktionalität (Information Rights Management) von Exchange Server** (zum Beispiel Transportregeln und Outlook Web Access) oder SharePoint Server mit AD RMS verwendet haben:

    - Planen Sie einen kurzen Zeitraum ein, in dem IRM nicht auf diesen Servern zur Verfügung steht.
 
    Nach der Migration können Sie IRM weiterhin auf diesen Servern mit Azure RMS verwenden. Allerdings wird in einem der Migrationsschritte der IRM-Dienst vorübergehend deaktiviert, um einen Verbindungsdienst zu installieren und zu konfigurieren und die Server neu zu konfigurieren. Danach wird IRM wieder aktiviert.

    Dies ist die einzige Dienstunterbrechung während der Migration.

- **Wenn Sie Ihren eigenen Azure RMS-Mandantenschlüssel mithilfe eines HSM-geschützten Schlüssels verwalten möchten**:

    - Für diese optionale Konfiguration sind Azure Key Vault und ein Azure-Abonnement erforderlich, das Key Vault mit HSM-geschützten Schlüsseln unterstützt. Weitere Informationen finden Sie auf der [Seite mit den Azure Key Vault-Preisen](https://azure.microsoft.com/en-us/pricing/details/key-vault/). 


Einschränkungen:

-   Obwohl der Migrationsvorgang die Migration des Schlüssels Ihres lizenzgebenden Serverzertifikats (SLC) zu einem Hardwaresicherheitsmodul (HSM) für Azure RMS unterstützt, wird diese Konfiguration derzeit von Exchange Online nicht unterstützt. Wenn Sie die vollständige IRM-Funktionalität mit Exchange Online nutzen möchten, nachdem Sie zu Azure RMS migriert haben, muss Ihr Azure RMS-Mandantenschlüssel [von Microsoft verwaltet werden](../plan-design/plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok). Alternativ können Sie IRM mit eingeschränkter Funktionalität in Exchange Online ausführen, wenn Ihr Azure RMS-Mandant von Ihnen verwaltet wird (BYOK). Weitere Informationen zur Verwendung von Exchange Online mit Azure RMS finden Sie unter [Schritt 6. Konfigurieren der IRM-Integration mit Exchange Online](migrate-from-ad-rms-phase3.md#step-6-configure-irm-integration-for-exchange-online) in diesen Anweisungen.

-   Falls Sie Software und Clients besitzen, die nicht in Azure RMS unterstützt werden, können diese den durch Azure RMS geschützten Inhalt nicht schützen oder nutzen. Überprüfen Sie unbedingt den Abschnitt zu den unterstützten Anwendungen und Clients des Artikels [Voraussetzungen für Azure Rights Management](../get-started/requirements-azure-rms.md).

-   Wenn Sie Ihren lokalen Schlüssel in Azure RMS als archiviert importieren (indem Sie die vertrauenswürdige Veröffentlichungsdomäne während des Importvorgangs nicht als aktiv festlegen) und Benutzer in einer phasenweisen Migration in Batches migrieren, sind neu von den migrierten Benutzern geschützte Inhalte nicht für Benutzer verfügbar, die in AD RMS bleiben. Halten Sie in diesem Szenario die Migrationszeit möglichst kurz, und migrieren Sie Benutzer in logischen Gruppen, d. h. wenn Benutzer zusammen arbeiten, sollten sie gemeinsam migriert werden.

    Diese Einschränkung gilt nicht, wenn Sie die vertrauenswürdige Veröffentlichungsdomäne während des Importvorgangs auf aktiv festlegen, da alle Benutzer Inhalte mit dem gleichen Schlüssel schützen werden. Diese Konfiguration wird empfohlen, da sie alle Benutzer unabhängig voneinander und in Ihrem eigenen Tempo migrieren können.

-   Wenn Sie mit externen Partnern zusammenarbeiten (z. B. mithilfe von vertrauenswürdigen Benutzerdomänen oder Verbund), müssen diese ebenfalls auf Azure RMS migrieren, entweder zur gleichen Zeit wie Sie oder so bald wie möglich danach. Damit der Zugriff auf Inhalte, die Ihre Organisation zuvor mit AD RMS geschützt hat, weiterhin möglich ist, müssen Ihre Partner ähnliche Änderungen an der Clientkonfiguration wie Sie vornehmen (in diesem Dokument erläutert).

    Aufgrund der möglichen Konfigurationsvarianten Ihrer Partner können in diesem Dokument keine genauen Anweisungen für diese Neukonfiguration gegeben werden. Wenden Sie sich an den [Microsoft Support](../get-started/information-support.md#support-options-and-community-resources), um Hilfe zu erhalten.

## Übersicht über die Schritte zum Migrieren von AD RMS zu Azure RMS


Die Migrationsschritte können in vier Phasen unterteilt werden, die zu unterschiedlichen Zeiten und von verschiedenen Administratoren ausgeführt werden können.

[**PHASE 1: SERVERSEITIGE KONFIGURATION FÜR AD RMS**](migrate-from-ad-rms-phase1.md)

- **Schritt 1: Herunterladen der Azure RMS-Verwaltungstools**

    Während der Migration müssen Sie eine oder mehrere der Windows PowerShell-Cmdlets aus dem Azure RMS-Modul ausgeführt, das mit dem Azure RMS-Verwaltungstool installiert wurde.

- **Schritt 2. Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS**

    Sie exportieren die Konfigurationsdaten (Schlüssel, Vorlagen, URLs) aus AD RMS in eine XML-Datei und laden dann diese Datei mithilfe des Windows PowerShell-Cmdlets "Import-AadrmTPD" in Azure RMS hoch. Je nach AD RMS-Schlüsselkonfiguration sind möglicherweise weitere Schritte erforderlich:

    - **Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln**:

        Zentral verwaltete, kennwortbasierte Schlüssel in AD RMS zu einem Microsoft-verwalteten Azure RMS-Mandantenschlüssel. Dies ist der einfachste Migrationspfad, bei dem keine weiteren Schritte erforderlich sind.

    - **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln**:

        Schlüssel, die von einem HSM für AD RMS in einem vom Kunden verwalteten Azure RMS-Mandantenschlüssel gespeichert werden (das "Bring Your Own Key"- oder BYOK-Szenario). Hier sind zusätzliche Schritte zum Übertragen des Schlüssels aus Ihrem lokalen Thales-HSM an Azure Key Vault und zur Autorisierung von Azure RMS für die Verwendung dieses Schlüssels erforderlich. Ihre vorhandenen HSM-geschützten Schlüssel müssen modulgeschützt sein. OCS-geschützte Schlüssel werden von den Rights Management-Services nicht unterstützt.

    - **Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln**:

        Zentral verwaltete, kennwortbasierte Schlüssel in AD RMS zu einem kundenverwalteten Azure RMS-Mandantenschlüssel (das "Bring Your Own Key"- oder BYOK-Szenario). Dieses Szenario erfordert die meisten Konfigurationsschritte, da Sie zunächst den Softwareschlüssel extrahieren und in ein lokales HSM importieren und dann zusätzliche Schritte zum Übertragen des Schlüssels aus Ihrem lokalen Thales-HSM in das Azure Key Vault-HSM und zur Autorisierung von Azure RMS für die Verwendung des Schlüsseltresors, der den Schlüssel speichert, ausführen müssen.

- **Schritt 3: Aktivieren Ihres Azure RMS-Mandanten**

    Falls möglich, führen Sie diesen Schritt nach dem Importvorgang und nicht davor aus.

- **Schritt 4: Konfigurieren importierter Vorlagen**

    Wenn Sie Ihre Vorlagen für Benutzerrechterichtlinien importieren, lautet deren Status "Archiviert". Falls Benutzer in der Lage sein sollen, diese anzuzeigen und zu verwenden, müssen Sie den Vorlagenstatus im klassischen Azure-Portal in „Veröffentlicht“ ändern.


[**PHASE 2: CLIENTSEITIGE KONFIGURATION**](migrate-from-ad-rms-phase2.md)


- **Schritt 5. Neukonfigurieren von Clients zur Verwendung von Azure RMS**

    Vorhandene Windows-Computer müssen neu konfiguriert werden, um den Azure RMS-Dienst anstelle von AD RMS zu verwenden. Dieser Schritt gilt für Computer in Ihrer Organisation und für Computer in Partnerorganisationen, wenn Sie mit diesen zusammengearbeitet haben, während AS RMS ausgeführt wurde.

    Außerdem müssen Sie, wenn Sie die [Erweiterungen für mobile Geräte](http://technet.microsoft.com/library/dn673574.aspx) zur Unterstützung mobiler Geräte wie iOS-Telefone und iPads, Android-Telefone und Tablets, Windows Phone und Mac-Computer bereitgestellt haben, die SRV-Einträge im DNS entfernen, mit denen diese Clients zu AD RMS umgeleitet wurden.


[**PHASE 3: UNTERSTÜTZUNG DER DIENSTEKONFIGURATION**](migrate-from-ad-rms-phase3.md)


- **Schritt 6: Konfigurieren der IRM-Integration mit Exchange Online**

    Dieser Schritt ist erforderlich, wenn Sie Exchange Online mit Azure RMS verwenden möchten.


- **Schritt 7: Bereitstellen des RMS-Verbindungsdiensts**

    Dieser Schritt ist erforderlich, wenn Sie einen der folgenden lokalen Dienste mit Azure RMS verwenden möchten:

    - Exchange Server (z. B. Transportregeln und Outlook Web Access)

    - SharePoint Server

    - Windows Server mit Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)


[**PHASE 4: AUFGABEN NACH DER MIGRATION**](migrate-from-ad-rms-phase4.md )

- **Schritt 8: Außerbetriebsetzung von AD RMS**

    Wenn sichergestellt ist, dass alle Clients Azure RMS verwenden und nicht mehr auf die AD RMS-Server zugreifen, können Sie Ihre AD RMS-Bereitstellung außer Betrieb setzen.


- **Schritt 9: Ändern des Azure RMS-Mandantenschlüssels**

    Dieser Schritt ist optional, wird jedoch empfohlen, wenn Ihre in Schritt 2 gewählte Azure RMS-Mandantenschlüsseltopologie von Microsoft verwaltet wird. Dieser Schritt ist nicht anwendbar, wenn die gewählte Azure RMS-Mandantenschlüsseltopologie kundenverwaltet (BYOK) ist.


## Nächste Schritte
Um die Migration zu starten, wechseln Sie zu [Phase 1: Serverseitige Konfiguration](migrate-from-ad-rms-phase1.md).




<!--HONumber=Aug16_HO4-->


