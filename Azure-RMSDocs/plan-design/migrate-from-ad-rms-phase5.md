---
title: Migrieren von AD RMS-Azure Information Protection – Phase 5
description: Phase 5 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 10 bis 12 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 227a7f1f0ac08ed67648f97a78a5ff89e9b4a586
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "30207511"
---
# <a name="migration-phase-5---post-migration-tasks"></a>Migrationsphase 5: Aufgaben nach der Migration

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Verwenden Sie die folgenden Informationen für Phase 5 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken die Schritte 10 bis 12 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.

## <a name="step-10-deprovision-ad-rms"></a>Schritt 10: Aufheben der Bereitstellung von AD RMS

Entfernen Sie den Dienstverbindungspunkt (Service Connection Point, SCP) aus Active Directory, um zu verhindern, dass Computer Ihre lokale Rights Management-Infrastruktur ermitteln. Dies ist für die vorhandenen Clients, die Sie migriert haben, optional, und zwar aufgrund der Umleitung, die Sie in der Registrierung konfiguriert haben (z. B. durch Ausführen des Migrationsskripts). Allerdings hindert das Entfernen des Dienstverbindungspunkts neue Clients und möglicherweise auf RMS bezogene Dienste und Tools am Auffinden des Dienstverbindungspunkts, wenn die Migration abgeschlossen ist. Hier sollten nur alle Computerverbindungen mit Azure Rights Management hergestellt werden. 

Stellen Sie zum Entfernen des Dienstverbindungspunkts sicher, dass Sie als Unternehmensadministrator einer Domäne angemeldet sind, und gehen Sie dann folgendermaßen vor:

1. Klicken Sie in der Active Directory Rights Management Services-Konsole mit der rechten Maustaste auf den AD RMS-Cluster, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **SCP** .

3. Aktivieren Sie das Kontrollkästchen **SCP ändern** .

4. Wählen Sie **Aktuellen SCP entfernen** aus, und klicken Sie dann auf **OK**.

Überwachen Sie jetzt Ihre AD RMS-Server auf Aktivität. Beispielsweise durch Überprüfen der [Anforderungen im Systemintegritätsbericht](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx) und der [ServiceRequest-Tabelle](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) oder durch [Überwachung des Benutzerzugriffs auf geschützte Inhalte](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). 

Wenn Sie bestätigt haben, dass RMS-Clients nicht mehr mit diesen Servern kommunizieren und Clients erfolgreich Azure Information Protection verwenden, können Sie die AD RMS-Serverrolle von diesen Servern entfernen. Wenn Sie dedizierte Server verwenden, kann es sinnvoll sein, zunächst die Server vorsichtshalber für einen gewissen Zeitraum abzuschalten. So haben Sie Zeit, sicherzustellen, dass es keine gemeldeten Probleme gibt, die den Neustart dieser Server erfordern, um die Dienstkontinuität zu gewährleisten, während Sie untersuchen, weshalb Clients nicht Azure Information Protection verwenden.

Nachdem Sie die Bereitstellung Ihrer AD RMS-Server aufgehoben haben, können Sie sich Ihre Vorlagen im Azure-Portal anschauen. Konvertieren Sie sie z.B. in Bezeichnungen, konsolidieren Sie sie, sodass Benutzer weniger Wahlmöglichkeiten haben, oder konfigurieren Sie sie neu. Außerdem wäre dies ein guter Zeitpunkt, um die Standardvorlagen zu veröffentlichen. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](../deploy-use/configure-policy-templates.md).

>[!IMPORTANT]
> Am Ende dieser Migration können Ihre AD RMS-Cluster nicht mit Azure Information Protection und der HYOK-Option (Hold Your Own Key) verwendet werden. Wenn Sie sich dazu entscheiden, HYOK für die Azure Information Protection-Bezeichnung aufgrund der nun festliegenden Umleitungen zu verwenden, muss der AD RMS-Cluster, den Sie verwenden, über unterschiedliche Lizenzierungs-URLs für die in den Clustern verfügen, die Sie migriert haben.

## <a name="step-11-complete-client-migration-tasks"></a>Schritt 11: Durchführen der Clientmigrationstasks

Für Clients für mobile Geräte und Mac-Computer: Entfernen Sie die DNS-SRV-Einträge, die Sie bei der Bereitstellung der [AD RMS-Erweiterung für mobile Geräte](http://technet.microsoft.com/library/dn673574.aspx) erstellt haben.

Wenn die DNS-Änderungen weitergegeben wurden, ermitteln und verwenden diese Clients den Azure Rights Management-Dienst automatisch. Mac-Computer, die Office Mac ausführen, speichern jedoch die Informationen von AD RMS zwischen. Für diese Computer kann der Vorgang bis zu 30 Tage dauern. 

Suchen Sie im Schlüsselbund nach „adal“, und löschen Sie alle ADAL-Einträge, um Mac-Computer zum sofortigen Ausführen des Ermittlungsprozesses zu zwingen. Führen Sie dann folgende Befehle auf diesen Computern aus:

````

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

        Connect-Aadrmservice

2. Führen Sie den folgenden Befehl aus, und geben Sie **Y** zur Bestätigung ein:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False
    
    Beachten Sie, dass dieser Befehl alle Lizenzerzwingungen für den Schutzdienst Azure Rights Management entfernt, sodass alle Computer Dokumente und E-Mails schützen können.

3. Bestätigen Sie, dass Onboarding-Steuerelemente nicht länger festgelegt sind:

        Get-AadrmOnboardingControlPolicy

    In der Ausgabe sollte **Lizenz** nun **FALSE** sein, und es wird keine GUID für die **SecurityGroupOjbectId** angezeigt.

Wenn Sie Office 2010 verwenden, und Sie den Task **Verwaltung der AD RMS-Vorlagen für Benutzerrechterichtlinien (Automatisiert)** in der Windows-Taskplanerbibliothek aktiviert haben, deaktivieren Sie diesen Task, da er nicht vom Azure Information Protection-Client verwendet wird. Dieser Task wird in der Regel mit der Gruppenrichtlinie aktiviert und unterstützt eine AD RMS-Bereitstellung. Sie finden den Task an folgendem Speicherort: **Microsoft** > **Windows** > **Active Directory Rights Management Services-Client**

## <a name="step-12-rekey-your-azure-information-protection-tenant-key"></a>Schritt 12: Neuerstellen Ihres Azure Information Protection-Mandantenschlüssels

Dieser Schritt wird nach dem Abschluss der Migration empfohlen, wenn Ihre AD RMS-Bereitstellung den RMS-Kryptografiemodus 1 verwendet hat. Das Neuerstellen des Schlüssels führt zu Schutz, der den RMS-Kryptografiemodus 2 verwendet. 

Auch wenn Ihre AD RMS-Bereitstellung den Kryptografiemodus 2 verwendet hat, wird dieser Schritt empfohlen, da ein neuer Schlüssel dabei hilft, Ihren Mandanten vor potenziellen Sicherheitsverletzungen Ihres AD RMS-Schlüssels zu schützen.

Wenn Sie für Ihren Azure Information Protection-Mandantenschlüssel einen neuen Schlüssel erstellen (oder neu vergeben), wird der aktuell aktive Schlüssel archiviert, und Azure Information Protection verwendet ab diesem Zeitpunkt einen anderen Schlüssel, den Sie angeben. Bei diesem anderen Schlüssel kann es sich um einen neuen Schlüssel handeln, den Sie in Azure Key Vault erstellen, oder um den Standardschlüssel, der automatisch für Ihren Mandanten erstellt wurde.

Der Übergang von einem Schlüssel zum anderen geschieht nicht sofort, sondern über einige Wochen hinweg. Da dies nicht sofort erfolgt, sollten Sie nicht warten, bis Sie eine Verletzung Ihres ursprünglichen Schlüssels vermuten, sondern diesen Schritt ausführen, sobald die Migration abgeschlossen ist.

So erstellen Sie Ihren Azure Information Protection-Mandantenschlüssel neu:

- **Wenn Ihr Mandantenschlüssel von Microsoft verwaltet wird**: Führen Sie das PowerShell-Cmdlet [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) aus, und geben Sie die Schlüsselkennung für den Schlüssel an, der automatisch für Ihren Mandanten erstellt wurde. Sie können den anzugebenden Wert identifizieren, indem Sie das Cmdlet [Get-AadrmKeys](/powershell/module/aadrm/get-aadrmkeys) ausführen. Der Schlüssel, der automatisch für Ihren Mandanten erstellt wurde, hat das am weitesten zurückliegende Erstellungsdatum, damit Sie ihn mithilfe des folgenden Befehls identifizieren können:
    
        (Get-AadrmKeys) | Sort-Object CreationTime | Select-Object -First 1

- **Wenn Ihr Mandantenschlüssel von Ihnen verwaltet wird (BYOK)**: Wiederholen Sie in Azure Key Vault den Schlüsselerstellungsvorgang für Ihren Azure Information Protection-Mandanten, und führen Sie dann das Cmdlet [Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey) erneut aus, um den URI für diesen neuen Schlüssel anzugeben. 

Weitere Informationen zum Verwalten des Azure Information Protection-Mandantenschlüssels finden Sie unter [Vorgänge für Ihren Azure Information Protection-Mandantenschlüssel](../deploy-use/operations-tenant-key.md).


## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die Migration nun abgeschlossen haben, können Sie sich die [Roadmap für die Bereitstellung](deployment-roadmap.md) ansehen, um die ggf. erforderlichen weiteren Bereitstellungsaufgaben zu ermitteln.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
