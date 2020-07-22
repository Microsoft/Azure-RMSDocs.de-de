---
title: Vorbereiten der Umgebung für Azure RMS und AD RMS
description: Leitfaden für Administratoren, wenn Sie Azure Rights Management mit AD RMS bereitgestellt haben.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 11/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 9196f02e63f7eb433237613fe44c43cf74ab3262
ms.sourcegitcommit: 6d10435c67434bdbbdd51b4a3535d0efaf8307da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86869027"
---
# <a name="prepare-the-environment-for-azure-rights-management-when-you-have-ad-rms"></a>Vorbereiten der Umgebung für Azure Rights Management bei AD RMS

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

Wenn Sie zu Azure Information Protection migrieren, verlieren Sie nicht den Zugriff auf zuvor geschützte Inhalte, und Sie müssen Ihre Inhalte nicht schützen oder erneut schützen. Dokumente und e-Mails, die durch AD RMS geschützt wurden, können auch nach der Aufhebung der Bereitstellung von AD RMS geöffnet werden.

Unabhängig davon, ob Sie sich für eine Migration zu Azure Information Protection entscheiden oder die Einschränkungen Ihrer aktuellen AD RMS-Bereitstellung akzeptieren, müssen Sie zuerst sicherstellen, dass der Azure Rights Management-Dienst deaktiviert ist. Führen Sie die Schritte für das Szenario aus, das auf Sie zutrifft:

- [Ihr Abonnement, das Azure Rights Management umfasst, wurde während oder nach dem 2018. Februar erworben.](#your-subscription-was-purchased-during-or-after-february-2018)

- [Ihr Abonnement wurde im Februar 2018 oder davor erworben, und Sie verfügen über Exchange Online](#your-subscription-was-purchased-before-or-during-february-2018-and-you-have-exchange-online)

- [Eine Option zum Aktivieren des Schutzes wird angezeigt, wenn Sie die Azure Information Protection-Richtlinie im Azure-Portal konfigurieren.](#you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection)


## <a name="your-subscription-was-purchased-during-or-after-february-2018"></a>Ihr Abonnement wurde im Februar 2018 oder danach erworben

Ab Ende Februar 2018 ist Azure Rights Management in neuen Abonnements mit Azure Information Protection standardmäßig aktiviert. Wenn dieser Dienst automatisch für Sie aktiviert wurde und Sie auch Active Directory Rights Management Services (AD RMS) verwenden, ist diese Kombination nicht kompatibel. Es ist daher sehr wichtig, dass Sie den Azure Rights Management-Dienst so schnell wie möglich deaktivieren. 

### <a name="step-1-deactivate-azure-rights-management"></a>Schritt 1: Deaktivieren Sie Azure Rights Management
Verwenden Sie eine der folgenden Vorgehensweisen, um Azure Rights Management zu deaktivieren.

> [!TIP]
> Sie können auch das Windows PowerShell-Cmdlet " [Deaktivieren-aipservice](/powershell/module/aipservice/disable-aipservice)" verwenden, um den Azure Rights Management-Dienst zu deaktivieren.

#### <a name="to-deactivate-rights-management-from-the-microsoft-365-admin-center"></a>So deaktivieren Sie Rights Management über das Microsoft 365 Admin Center

1. Wechseln Sie zur [Rights Management-Seite](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) für Office 365-Administratoren.
    
    Wenn Sie aufgefordert werden, sich anzumelden, verwenden Sie das Konto eines globalen Administrators für Office 365.

2. Klicken Sie auf der Seite **Rechteverwaltung** auf **Deaktivieren**.

3.  Wenn die Aufforderung **Möchten Sie Rights Management deaktivieren?** angezeigt wird, klicken Sie auf **Deaktivieren**.

Es sollten jetzt **Rights Management ist nicht aktiviert** und die Option zum Aktivieren angezeigt werden.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>So deaktivieren Sie Rights Management über das Azure-Portal

1. Wenn Sie dies nicht bereits getan haben, öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal). Navigieren Sie anschließend zum Bereich **Azure Information Protection**.
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.
    
    Wenn Sie noch nicht auf den Azure Information Protection Bereich zugegriffen haben, lesen Sie die einmaligen [zusätzlichen Schritte](configure-policy.md#to-access-the-azure-information-protection-pane-for-the-first-time) zum Hinzufügen dieses Bereichs zum Portal.

2. Wählen Sie in den Menüoptionen die Option **Schutzaktivierung** aus. 

3.  Wählen Sie im Bereich **Azure Information Protection-Schutz Aktivierung** die Option **Deaktivieren**aus. Klicken Sie zum Bestätigen Ihrer Auswahl auf **Ja**.

Die Informationsleiste zeigt daraufhin **Deactivation finished successfully** (Deaktivierung erfolgreich ausgeführt) an, und **Deaktivieren** wird nun durch **Aktivieren** ersetzt. 

### <a name="step-2-start-planning-for-migration"></a>Schritt 2: Beginnen mit der Planung für die Migration

Informationen hierzu finden Sie im Migrationsleitfaden [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).


## <a name="your-subscription-was-purchased-before-or-during-february-2018-and-you-have-exchange-online"></a>Ihr Abonnement wurde im Februar 2018 oder davor erworben, und Sie verfügen über Exchange Online

Microsoft beginnt damit, den Azure Rights Management-Dienst für Abonnements zu aktivieren, die Azure Rights Management oder Azure Information Protection umfassen und deren Mandanten Exchange Online verwenden. Für diese Mandanten beginnt die automatische Aktivierung am 1. August 2018.

Wenn der Dienst automatisch für Sie aktiviert wird und Sie auch AD RMS verwenden, ist diese Kombination nicht kompatibel. Es ist daher wichtig, dass Ihr Mandant vom automatischen Dienstupdate ausgenommen wird. 

### <a name="step-1-opt-out-from-the-automatic-service-update"></a>Schritt 1: Deaktivieren Sie das automatische Dienstupdate

Verwenden Sie den folgenden Exchange Online PowerShell-[Set-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/set-irmconfiguration)-Befehl:`Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false`

[Weitere Informationen](https://support.office.com/article/protection-features-in-azure-information-protection-rolling-out-to-existing-office-365-tenants-7ad6f58e-65d7-4c82-8e65-0b773666634d) 

### <a name="step-2-start-planning-for-migration"></a>Schritt 2: Beginnen mit der Planung für die Migration

Informationen hierzu finden Sie im Migrationsleitfaden [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).


## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Eine Option zum Aktivieren des Schutzes wird angezeigt, wenn Sie Azure Information Protection konfigurieren.

Der Aktivierungs Bereich für den **Azure Information Protection Schutz** verfügt über eine Option zum Aktivieren des Azure Rights Management-Dienstanbieter.  

Wenn Sie auch AD RMS verwenden, wählen Sie nicht die Option **Aktivieren** aus. Wenn der Azure Rights Management-Dienst nicht aktiviert ist, können Sie dennoch Azure Information Protection für Bezeichnungen verwenden, die nur für die Klassifizierung gelten. Eine spezielle Standardrichtlinie wird für Sie erstellt, die keinen Schutz von Daten beinhaltet, und diese Konfigurationsoptionen sind bis zur Aktivierung des Azure Rights Management-Diensts nicht verfügbar.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Schritt 1: Konfigurieren der Azure Information Protection-Richtlinie für die Klassifizierung und Bezeichnung – ohne Schutz

Im Bereich **Azure Information Protection-Bezeichnungen** können Sie die Bezeichnungen anzeigen und konfigurieren, die keine Optionen für den Datenschutz enthalten. Weitere Informationen zum Konfigurieren der Bezeichnungen und Richtlinieneinstellungen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Schritt 2: Beginnen mit der Planung für die Migration

Informationen hierzu finden Sie im Migrationsleitfaden [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

### <a name="step-3-configure-labels-for-protection"></a>Schritt 3: Konfigurieren Sie die Bezeichnungen für den Schutz

Nachdem Sie den Azure Rights Management-Dienst im Rahmen der Migration aktiviert haben, können Sie Bezeichnungen für den Schutz von Daten konfigurieren. Wenn Sie jedoch Benutzer in Batches migrieren, sollten Sie sicherstellen, dass Bezeichnungen, die Schutz anwenden, nur auf die migrierten Benutzer ausgerichtet sind.


