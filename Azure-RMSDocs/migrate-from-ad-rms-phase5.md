---
title: Migrieren von AD RMS-Azure Information Protection – Phase 5
description: Phase 5 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 10 bis 12 der Migration von AD RMS zu Azure Information Protection ab.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/11/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.subservice: migration
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin, has-adal-ref
ms.openlocfilehash: fd030502c6d6583e72be63fa424ff8186ebaadc7
ms.sourcegitcommit: af7ac2eeb8f103402c0036dd461c77911fbc9877
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2021
ms.locfileid: "98560304"
---
# <a name="migration-phase-5---post-migration-tasks"></a>Migrationsphase 5: Aufgaben nach der Migration

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Verwenden Sie die folgenden Informationen für Phase 5 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken die Schritte 10 bis 12 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.

## <a name="step-10-deprovision-ad-rms"></a>Schritt 10. Aufheben der Bereitstellung von AD RMS

Entfernen Sie den Dienstverbindungspunkt (Service Connection Point, SCP) aus Active Directory, um zu verhindern, dass Computer Ihre lokale Rights Management-Infrastruktur ermitteln. Dies ist für die vorhandenen Clients, die Sie migriert haben, optional, und zwar aufgrund der Umleitung, die Sie in der Registrierung konfiguriert haben (z. B. durch Ausführen des Migrationsskripts). Allerdings hindert das Entfernen des Dienstverbindungspunkts neue Clients und möglicherweise auf RMS bezogene Dienste und Tools am Auffinden des Dienstverbindungspunkts, wenn die Migration abgeschlossen ist. Hier sollten nur alle Computerverbindungen mit Azure Rights Management hergestellt werden.

Stellen Sie zum Entfernen des Dienstverbindungspunkts sicher, dass Sie als Unternehmensadministrator einer Domäne angemeldet sind, und gehen Sie dann folgendermaßen vor:

1. Klicken Sie in der Active Directory Rights Management Services-Konsole mit der rechten Maustaste auf den AD RMS-Cluster, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **SCP**.

3. Aktivieren Sie das Kontrollkästchen **SCP ändern**.

4. Wählen Sie **Aktuellen SCP entfernen** aus, und klicken Sie dann auf **OK**.

Überwachen Sie jetzt Ihre AD RMS-Server auf Aktivität. Beispielsweise durch Überprüfen der [Anforderungen im Systemintegritätsbericht](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee221012(v=ws.10)) und der [ServiceRequest-Tabelle](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd772686(v=ws.10)) oder durch [Überwachung des Benutzerzugriffs auf geschützte Inhalte](https://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx).

Wenn Sie bestätigt haben, dass RMS-Clients nicht mehr mit diesen Servern kommunizieren und Clients erfolgreich Azure Information Protection verwenden, können Sie die AD RMS-Serverrolle von diesen Servern entfernen. Wenn Sie dedizierte Server verwenden, bevorzugen Sie möglicherweise den Vorsichts Schritt zum ersten Herunterfahren der Server für einen bestimmten Zeitraum. So haben Sie Zeit, sicherzustellen, dass es keine gemeldeten Probleme gibt, die den Neustart dieser Server erfordern, um die Dienstkontinuität zu gewährleisten, während Sie untersuchen, weshalb Clients nicht Azure Information Protection verwenden.

Nachdem Sie die Bereitstellung Ihrer AD RMS Server durch yo aufgehoben haben, können Sie die Möglichkeit haben, Ihre Vorlage und Bezeichnungen zu überprüfen. Konvertieren Sie z. b. Vorlagen in Bezeichnungen, konsolidieren Sie Sie, damit Benutzer weniger auswählen können, oder konfigurieren Sie Sie neu. Dies wäre auch ein guter Zeitpunkt, Standardvorlagen zu veröffentlichen.

Verwenden Sie für Vertraulichkeits Bezeichnungen und den Unified Label-Client ihre Bezeichnung Admin Center, einschließlich der Microsoft 365 Security Center, Microsoft 365 Compliance Center oder des Microsoft 365 Security & Compliance Center. Weitere Informationen finden Sie in der Microsoft 365-Dokumentation.

Wenn Sie den klassischen Client verwenden, verwenden Sie den Azure-Portal. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](./configure-policy-templates.md).

>[!IMPORTANT]
> Am Ende dieser Migration kann der AD RMS Cluster nicht mit Azure Information Protection und der Option hold your own Key ([Hyok](configure-adrms-restrictions.md)) verwendet werden. 
>
> Wenn Sie den klassischen Client mit Hyok verwenden, muss der AD RMS Cluster, den Sie verwenden, aufgrund der nun vorhandenen Umleitungen über unterschiedliche Lizenzierungs-URLs für diejenigen in den Clustern verfügen, die Sie migriert haben.
>
### <a name="additional-configuration-for-computers-that-run-office-2010"></a>Zusätzliche Konfiguration für Computer, auf denen Office 2010 ausgeführt wird

> [!IMPORTANT]
> Der erweiterte Support von Office 2010 endete am 13. Oktober 2020. Weitere Informationen finden Sie unter [AIP und ältere Windows-und Office-Versionen](known-issues.md#aip-and-legacy-windows-and-office-versions).
> 

Wenn migrierte Clients Office 2010 ausführen, kann es bei Benutzern zu Verzögerungen beim Öffnen geschützter Inhalte kommen, wenn die Bereitstellung der AD RMS Server aufgehoben wird. Oder Benutzer sehen möglicherweise Nachrichten, dass Sie nicht über Anmelde Informationen zum Öffnen geschützter Inhalte verfügen. Um diese Probleme zu beheben, erstellen Sie eine Netzwerk Umleitung für diese Computer, die den AD RMS URL-FQDN an die lokale IP-Adresse des Computers (127.0.0.1) umleitet. Hierzu können Sie die lokale Hosts-Datei auf jedem Computer oder mithilfe von DNS konfigurieren.

- **Umleitung über lokale Hostdatei**: Fügen Sie die folgende Zeile in der Datei "local Hosts" ein, und ersetzen Sie dabei `<AD RMS URL FQDN>` durch den Wert für den AD RMS Cluster ohne Präfixe oder Webseiten:

    ```sh
    127.0.0.1 <AD RMS URL FQDN>
    ```

- **Umleitung über DNS**: Erstellen Sie einen neuen Host (a)-Datensatz für den AD RMS URL-voll qualifizierten Namen, der die IP-Adresse 127.0.0.1 aufweist.

## <a name="step-11-complete-client-migration-tasks"></a>Schritt 11 Durchführen der Clientmigrationstasks

Für Clients für mobile Geräte und Mac-Computer: Entfernen Sie die DNS-SRV-Einträge, die Sie bei der Bereitstellung der [AD RMS-Erweiterung für mobile Geräte](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574(v=ws.11)) erstellt haben.

Wenn diese DNS-Änderungen weitergegeben wurden, ermitteln und verwenden diese Clients automatisch den Azure Rights Management-Dienst. Mac-Computer, die Office Mac ausführen, speichern jedoch die Informationen von AD RMS zwischen. Für diese Computer kann der Vorgang bis zu 30 Tage dauern.

Suchen Sie im Schlüsselbund nach „adal“, und löschen Sie alle ADAL-Einträge, um Mac-Computer zum sofortigen Ausführen des Ermittlungsprozesses zu zwingen. Führen Sie dann folgende Befehle auf diesen Computern aus:

````sh

rm -r ~/Library/Cache/MSRightsManagement

rm -r ~/Library/Caches/com.microsoft.RMS-XPCService

rm -r ~/Library/Caches/Microsoft\ Rights\ Management\ Services

rm -r ~/Library/Containers/com.microsoft.RMS-XPCService

rm -r ~/Library/Containers/com.microsoft.RMSTestApp

rm ~/Library/Group\ Containers/UBF8T346G9.Office/DRM.plist

killall cfprefsd

````

Wenn alle vorhandenen Windows-Computer zu Azure Information Protection migriert wurden, gibt es keinen Grund, weiterhin Onboarding-Steuerelemente zu verwenden und die **AIPMigrated**-Gruppe beizubehalten, die Sie für den Migrationsprozess erstellt haben.

Entfernen Sie zuerst die Onboarding-Steuerelemente, dann können Sie die Gruppe **AIPMigrated** und alle Methoden für die Softwarebereitstellung entfernen, die Sie zur Bereitstellung der Migrationsskripts erstellt haben.

So entfernen Sie die Onboarding-Steuerelemente:

1. Stellen Sie in einer PowerShell-Sitzung eine Verbindung mit dem Azure Rights Management-Dienst her, und geben Sie Ihre globalen Administratoranmeldeinformationen an, wenn Sie dazu aufgefordert werden:

    ```PowerShell
    Connect-AipService

2. Run the following command, and enter **Y** to confirm:

    ```PowerShell
    Set-AipServiceOnboardingControlPolicy -UseRmsUserLicense $False
    ```

    Beachten Sie, dass dieser Befehl alle Lizenzerzwingungen für den Schutzdienst Azure Rights Management entfernt, sodass alle Computer Dokumente und E-Mails schützen können.

3. Bestätigen Sie, dass Onboarding-Steuerelemente nicht länger festgelegt sind:

    ```PowerShell    
    Get-AipServiceOnboardingControlPolicy
    ```

    In der Ausgabe sollte **Lizenz** nun **FALSE** sein, und es wird keine GUID für die **SecurityGroupOjbectId** angezeigt.

Wenn Sie Office 2010 verwenden, und Sie den Task **Verwaltung der AD RMS-Vorlagen für Benutzerrechterichtlinien (Automatisiert)** in der Windows-Taskplanerbibliothek aktiviert haben, deaktivieren Sie diesen Task, da er nicht vom Azure Information Protection-Client verwendet wird. 

Dieser Task wird in der Regel mit der Gruppenrichtlinie aktiviert und unterstützt eine AD RMS-Bereitstellung. Sie finden diese Aufgabe unter folgendem Speicherort: **Microsoft**  >  **Windows**  >  **Active Directory Rights Management Services Client**. 

> [!IMPORTANT]
> Der erweiterte Support von Office 2010 endete am 13. Oktober 2020. Weitere Informationen finden Sie unter [AIP und ältere Windows-und Office-Versionen](known-issues.md#aip-and-legacy-windows-and-office-versions).

## <a name="step-12-rekey-your-azure-information-protection-tenant-key"></a>Schritt 12 Neuerstellen Ihres Azure Information Protection-Mandantenschlüssels

Dieser Schritt ist nach Abschluss der Migration erforderlich, wenn Ihre AD RMS Bereitstellung den RMS-Kryptografiemodus 1 verwendet hat, da dieser Modus einen 1024-Bit-Schlüssel und SHA-1 verwendet. Diese Konfiguration wird als unzureichender Schutzgrad angesehen. Microsoft unterstützt nicht die Verwendung niedrigerer Schlüssellängen wie z. b. 1024-Bit-RSA-Schlüssel und die damit verbundene Verwendung von Protokollen, die unzureichende Schutz Ebenen bieten, z. b. SHA-1.

Die erneute Schlüssel Erstellung führt zu Schutz, der den RMS-Kryptografiemodus 2 verwendet. Dies führt zu einem 2048-Bit-Schlüssel und SHA-256.

Auch wenn Ihre AD RMS-Bereitstellung den Kryptografiemodus 2 verwendet hat, wird dieser Schritt empfohlen, da ein neuer Schlüssel dabei hilft, Ihren Mandanten vor potenziellen Sicherheitsverletzungen Ihres AD RMS-Schlüssels zu schützen.

Wenn Sie für Ihren Azure Information Protection-Mandantenschlüssel einen neuen Schlüssel erstellen (oder neu vergeben), wird der aktuell aktive Schlüssel archiviert, und Azure Information Protection verwendet ab diesem Zeitpunkt einen anderen Schlüssel, den Sie angeben. Bei diesem anderen Schlüssel kann es sich um einen neuen Schlüssel handeln, den Sie in Azure Key Vault erstellen, oder um den Standardschlüssel, der automatisch für Ihren Mandanten erstellt wurde.

Der Wechsel von einem Schlüssel zu einem anderen geschieht nicht sofort, sondern über einige Wochen. Da dies nicht sofort erfolgt, sollten Sie nicht warten, bis Sie eine Verletzung Ihres ursprünglichen Schlüssels vermuten, sondern diesen Schritt ausführen, sobald die Migration abgeschlossen ist.

So erstellen Sie Ihren Azure Information Protection-Mandantenschlüssel neu:

- **Wenn Ihr Mandanten Schlüssel von Microsoft verwaltet wird**: führen Sie das PowerShell-Cmdlet [Set-aipservicekeyproperties](/powershell/module/aipservice/set-aipservicekeyproperties) aus, und geben Sie den Schlüssel Bezeichner für den Schlüssel an, der automatisch für Ihren Mandanten erstellt wurde. Sie können den Wert angeben, der angegeben werden soll, indem Sie das Cmdlet [Get-aipservicekeys](/powershell/module/aipservice/get-aipservicekeys) ausführen. Der Schlüssel, der automatisch für Ihren Mandanten erstellt wurde, hat das am weitesten zurückliegende Erstellungsdatum, damit Sie ihn mithilfe des folgenden Befehls identifizieren können:

        
    ```PowerShell
    (Get-AipServiceKeys) | Sort-Object CreationTime | Select-Object -First 1
    ```

- **Wenn Ihr Mandanten Schlüssel von Ihnen verwaltet wird (Byok)**: Wiederholen Sie in Azure Key Vault den Schlüssel Erstellungs Vorgang für Ihren Azure Information Protection-Mandanten, und führen Sie dann das Cmdlet " [use-aipservicekeyvaultkey](/powershell/module/aipservice/use-aipservicekeyvaultkey) " erneut aus, um den URI für diesen neuen Schlüssel anzugeben.

Weitere Informationen zum Verwalten des Azure Information Protection-Mandantenschlüssels finden Sie unter [Vorgänge für Ihren Azure Information Protection-Mandantenschlüssel](./operations-tenant-key.md).


## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die Migration abgeschlossen haben, lesen Sie die [Dokumentation zur AIP-Bereitstellung für Klassifizierung, Bezeichnung und Schutz](deployment-roadmap-classify-label-protect.md) , um alle anderen Bereitstellungs Aufgaben zu identifizieren, die Sie möglicherweise ausführen müssen.
