---
title: Vorbereiten der Umgebung für Azure RMS und AD RMS
description: Leitfaden für Administratoren, wenn Sie Azure Rights Management und AD RMS bereitgestellt haben.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 572806eefd9207a2d3d6bbcab12ad274c116f49f
ms.sourcegitcommit: f9077101a974459a4252e763b5fafe51ff15a16f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64767654"
---
# <a name="prepare-the-environment-for-azure-rights-management-when-you-have-ad-rms"></a>Vorbereiten der Umgebung für Azure Rights Management, wenn Sie über AD RMS verfügen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> Anleitung für die Verwendung der Active Directory Rights Management Services (AD RMS)

Die Kombination aus Azure Rights Management-Dienst aktiviert und Azure Rights Management Services (AD RMS) ist nicht kompatibel. Ohne zusätzliche Schritte werden einige Computer eventuell automatisch mithilfe des Azure Rights Management-Diensts gestartet und mit Ihrem AD RMS-Cluster verbunden. Dieses Szenario wird nicht unterstützt und hat unzuverlässige Ergebnisse zur Folge. Es ist daher wichtig, dass Sie weitere Schritte ausführen. 

**So prüfen Sie, ob Sie AD RMS bereitgestellt haben**:

1. Obwohl dies optional ist, veröffentlichen die meisten AD RMS-Bereitstellungen den Dienstverbindungspunkt in Active Directory, sodass Domänencomputer den AD RMS-Cluster erkennen können. 
    
    Verwenden Sie ADSI Edit, um festzustellen, ob in Active Directory ein Dienstverbindungspunkt veröffentlicht wurde: `CN=Configuration [server name], CN=Services, CN=RightsManagementServices, CN=SCP`

2. Wenn Sie keinen Dienstverbindungspunkt verwenden, müssen Windows-Computer, die eine Verbindung mit einem AD RMS-Cluster herstellen, für die clientseitige Diensterkennung oder die Lizenzierungsumleitung konfiguriert werden. Dies erfolgt in der Windows-Registrierung: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation` oder `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`.
    
    Weitere Informationen zu diesen Registrierungskonfigurationen finden Sie unter [Aktivieren der clientseitigen Diensterkennung mithilfe der Windows-Registrierung](./rms-client/client-deployment-notes.md#enabling-client-side-service-discovery-by-using-the-windows-registry) und [Umleiten des Datenverkehrs des Lizenzierungsservers](./rms-client/client-deployment-notes.md#redirecting-licensing-server-traffic).   

Wenn AD RMS für Ihre Organisation bereitgestellt ist, überlegen Sie, ob Sie zu Azure Information Protection migrieren können. Azure Information Protection bietet viele Vorteile gegenüber AD RMS. Hierzu gehören z.B. eine bessere Unterstützung für mobile Geräte und die Integration in Office 365-Dienste sowie Exchange Server und SharePoint Server. Weitere Informationen finden Sie unter [Vergleich von Azure Information Protection und AD RMS](compare-on-premise.md).

Wenn Sie zu Azure Information Protection migrieren, geht weder der Zugriff auf zuvor geschützte Inhalte verloren noch müssen Sie den Schutz Ihrer Inhalte aufheben und die Inhalte erneut schützen. Dokumente und E-Mails, die durch AD RMS geschützt wurden, können weiterhin geöffnet werden, nachdem die Bereitstellung von AD RMS aufgehoben wurde.

Unabhängig davon, ob Sie sich für eine Migration zu Azure Information Protection entscheiden oder die Einschränkungen Ihrer aktuellen AD RMS-Bereitstellung akzeptieren, müssen Sie zuerst sicherstellen, dass der Azure Rights Management-Dienst deaktiviert ist. Führen Sie die Schritte für das Szenario aus, das auf Sie zutrifft:

- [Ihr Abonnement mit Azure Rights Management wurde im Februar 2018 oder danach erworben](#your-subscription-was-purchased-during-or-after-february-2018)

- [Ihr Abonnement wurde im Februar 2018 oder davor erworben, und Sie verfügen über Exchange Online](#your-subscription-was-purchased-before-or-during-february-2018-and-you-have-exchange-online)

- [Eine Option zum Aktivieren des Schutzes wird angezeigt, wenn Sie die Azure Information Protection-Richtlinie im Azure-Portal konfigurieren.](#you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection)


## <a name="your-subscription-was-purchased-during-or-after-february-2018"></a>Ihr Abonnement wurde im Februar 2018 oder danach erworben

Ab Ende Februar 2018 ist Azure Rights Management in neuen Abonnements mit Azure Information Protection standardmäßig aktiviert. Wenn dieser Dienst automatisch für Sie aktiviert wurde und Sie auch Active Directory Rights Management Services (AD RMS) verwenden, ist diese Kombination nicht kompatibel. Es ist daher sehr wichtig, dass Sie den Azure Rights Management-Dienst so schnell wie möglich deaktivieren. 

### <a name="step-1-deactivate-azure-rights-management"></a>Schritt 1: Deaktivieren Sie Azure Rights Management
Verwenden Sie eine der folgenden Vorgehensweisen, um Azure Rights Management zu deaktivieren.

> [!TIP]
> Sie können auch das Windows PowerShell-Cmdlet [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm) zum Deaktivieren des Azure Rights Management-Diensts verwenden.

#### <a name="to-deactivate-rights-management-from-the-microsoft-365-admin-center"></a>So deaktivieren Sie Rights Management über das Microsoft 365 Admin Center

1. Wechseln Sie zur [Rights Management-Seite](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) für Office 365-Administratoren.
    
    Wenn Sie aufgefordert werden, sich anzumelden, verwenden Sie das Konto eines globalen Administrators für Office 365.

2. Klicken Sie auf der Seite **Rights Management** auf **Deaktivieren**.

3.  Wenn die Aufforderung **Möchten Sie Rights Management deaktivieren?** angezeigt wird, klicken Sie auf **Deaktivieren**.

Es sollte jetzt die Meldung **Rights Management ist nicht aktiviert** sowie die Option zum Aktivieren angezeigt werden.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>So deaktivieren Sie Rights Management über das Azure-Portal

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
    Wenn Sie zuvor noch nie auf das Blatt „Azure Information Protection“ zugegriffen haben, sehen Sie sich die einmaligen [zusätzlichen Schritte](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time) an, um dieses Blatt dem Portal hinzuzufügen.

2. Wählen Sie in den Menüoptionen die Option **Schutzaktivierung** aus. 

3.  Wählen Sie auf dem Blatt **„Protection activation“ (Schutzaktivierung) von Azure Information Protection** **Deaktivieren** aus. Klicken Sie zum Bestätigen Ihrer Auswahl auf **Ja**.

Die Informationsleiste zeigt daraufhin **Deactivation finished successfully** (Deaktivierung erfolgreich ausgeführt) an, und **Deaktivieren** wird nun durch **Aktivieren** ersetzt. 

### <a name="step-2-start-planning-for-migration"></a>Schritt 2: Beginnen Sie mit der Planung der Migration

Weitere Informationen finden Sie im Leitfaden zur Migration: [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)


## <a name="your-subscription-was-purchased-before-or-during-february-2018-and-you-have-exchange-online"></a>Ihr Abonnement wurde im Februar 2018 oder davor erworben, und Sie verfügen über Exchange Online

Microsoft beginnt damit, den Azure Rights Management-Dienst für Abonnements zu aktivieren, die Azure Rights Management oder Azure Information Protection umfassen und deren Mandanten Exchange Online verwenden. Für diese Mandanten beginnt die automatische Aktivierung am 1. August 2018.

Wenn der Dienst automatisch für Sie aktiviert wird und Sie auch AD RMS verwenden, ist diese Kombination nicht kompatibel. Es ist daher wichtig, dass Ihr Mandant vom automatischen Dienstupdate ausgenommen wird. 

### <a name="step-1-opt-out-from-the-automatic-service-update"></a>Schritt 1: Deaktivieren Sie das automatische Dienstupdate

Verwenden Sie den folgenden Exchange Online PowerShell-[Set-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/set-irmconfiguration)-Befehl:`Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false`

[Weitere Informationen](https://support.office.com/article/protection-features-in-azure-information-protection-rolling-out-to-existing-office-365-tenants-7ad6f58e-65d7-4c82-8e65-0b773666634d) 

### <a name="step-2-start-planning-for-migration"></a>Schritt 2: Beginnen Sie mit der Planung der Migration

Weitere Informationen finden Sie im Leitfaden zur Migration: [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)


## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Eine Option zum Aktivieren des Schutzes wird angezeigt, wenn Sie Azure Information Protection konfigurieren.

Das Blatt **Azure Information Protection – Schutzaktivierung** bietet eine Option zum Aktivieren des Azure Rights Management-Diensts.  

Wenn Sie auch AD RMS verwenden, wählen Sie nicht die Option **Aktivieren** aus. Wenn der Azure Rights Management-Dienst nicht aktiviert ist, können Sie Azure Information Protection weiterhin für Bezeichnungen verwenden, die nur für die Klassifizierung gelten. Eine spezielle Standardrichtlinie wurde für Sie erstellt, die den Datenschutz nicht einschließt, und diese Konfigurationsoptionen bleiben nicht verfügbar, bis der Azure Rights Management-Dienst aktiviert ist.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Schritt 1: Konfigurieren Sie Ihre Azure Information Protection-Richtlinie für die Klassifizierung und Bezeichnung – ohne Schutz

Auf dem Blatt **Azure Information Protection – Bezeichnungen** können Sie die Bezeichnungen anzeigen und konfigurieren, die keine Optionen für den Datenschutz umfassen. Weitere Informationen zum Konfigurieren der Bezeichnungen und Richtlinieneinstellungen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Schritt 2: Beginnen Sie mit der Planung der Migration

Weitere Informationen finden Sie im Leitfaden zur Migration: [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)

### <a name="step-3-configure-labels-for-protection"></a>Schritt 3: Konfigurieren Sie die Bezeichnungen für den Schutz

Nachdem Sie den Azure Rights Management-Dienst im Rahmen des Migrationsprozesses aktiviert haben, können Sie Bezeichnungen für den Schutz von Daten konfigurieren. Wenn Sie jedoch Benutzer in Batches migrieren, sollten Sie sicherstellen, dass Bezeichnungen, die Schutz anwenden, nur auf die migrierten Benutzer ausgerichtet sind.


