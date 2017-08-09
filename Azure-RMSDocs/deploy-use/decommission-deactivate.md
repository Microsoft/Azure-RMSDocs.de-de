---
title: "Außer Betrieb nehmen und Deaktivieren von Azure RMS"
description: "Informationen und Anweisungen für den Fall, dass Sie diese Lösung für den Informationsschutz von Azure Information Protection nicht mehr verwenden möchten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 277630708fb1d88d59b418146d0e42615ebf495c
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2017
---
# <a name="decommissioning-and-deactivating-azure-rights-management"></a>Außerbetriebsetzen und Deaktivieren von Azure Rights Management

>*Gilt für: Azure Information Protection, Office 365*

Sie steuern immer, ob Ihre Organisation Inhalt mithilfe des Azure Rights Management-Diensts von Azure Information Protection schützt. Wenn Sie entscheiden, dass dieser Datenschutzdienst nicht mehr verwendet werden soll, können Sie sich sicher sein, dass Ihnen die bisher geschützten Inhalte trotzdem weiter uneingeschränkt zur Verfügung stehen.

Wenn Sie keinen weiteren Zugriff auf zuvor geschützte Inhalte mehr benötigen, deaktivieren Sie einfach den Dienst, und lassen Sie Ihr Abonnement für Azure Information Protection ablaufen. Dies ist zum Beispiel angebracht, nachdem Sie das Testen von Azure Information Protection abgeschlossen haben, und bevor Sie es in einer Produktionsumgebung bereitstellen.

Wenn Sie Azure Information Protection jedoch in der Produktion bereitgestellt haben und Dokumente sowie E-Mails geschützt haben, stellen Sie sicher, dass Sie über eine Kopie Ihres Azure Information Protection-Mandantenschlüssels verfügen, bevor Sie den Azure Rights Management-Dienst deaktivieren. Stellen Sie sicher, dass Sie eine Kopie Ihres Schlüssels besitzen, bevor Ihr Abonnement abläuft, um sicherzustellen, dass Sie den Zugriff auf Inhalt beibehalten, der durch Azure Rights Management geschützt wurde, nachdem der Dienst deaktiviert wird. Wenn Sie die BYOK-Lösung (Bring Your Own Key) verwendet haben, bei der Sie Ihren eigenen Schlüssel in einem HSM erstellen und verwalten, verfügen Sie bereits über Ihren Azure Information Protection-Mandantenschlüssel. Wenn der Schlüssel jedoch von Microsoft verwaltet wurde (Standardlösung), lesen Sie die Anweisungen zum Exportieren Ihres Mandantenschlüssels im Artikel [Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel](operations-tenant-key.md).

> [!TIP]
> Selbst nachdem Ihr Abonnement abgelaufen ist, steht Ihnen Ihr Azure Information Protection-Mandant zur Nutzung der Inhalte für einen erweiterten Zeitraum zur Verfügung. Sie können den Mandantenschlüssel dann jedoch nicht mehr exportieren.

Wenn Sie über einen Azure Information Protection-Mandantenschlüssel verfügen, können Sie Rights Management lokal bereitstellen (AD RMS) und Ihren Mandantenschlüssel als eine vertrauenswürdige Veröffentlichungsdomäne (Trusted Publishing Domain, TPD) importieren. Ihnen stehen dann die folgenden Optionen für die Außerbetriebsetzung Ihrer Azure Information Protection-Bereitstellung zur Verfügung:

|Wenn dies auf Sie zutrifft, ...|… Vorgehensweise|
|----------------------------|--------------|
|Sie möchten, dass alle Benutzer weiterhin Rights Management verwenden, wobei Sie jedoch eine lokale Lösung statt Azure Information Protection verwenden möchten.    →|Verwenden Sie das Cmdlet [Set-AadrmMigrationUrl](/powershell/module/aadrm/Set-AadrmMigrationUrl), um vorhandene Benutzer zu Ihrer lokalen Bereitstellung zu leiten, wenn diese Benutzer Inhalte verwenden möchten, die nach dieser Änderung geschützt wurden. Benutzer verwenden automatisch die AD RMS-Installation, um die geschützten Inhalt zu nutzen.<br /><br />Leiten Sie Ihre Clients zur lokalen Bereitstellung um, damit Benutzer Inhalt nutzen können, der vor dieser Änderung geschützt wurde, indem sie den Registrierungsschlüssel **LicensingRedirection** für Office 2016 oder Office 2013 verwenden. Anweisungen finden Sie im [Abschnitt zur Dienstermittlung](../rms-client/client-deployment-notes.md) in den Notizen zur RMS-Clientbereitstellung sowie im **LicenseServerRedirection**-Registrierungsschlüssel für Office 2010, so wie in den [Einstellungen für die Office-Registrierung](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.|
|Sie möchten die Rights Management-Technologie überhaupt nicht mehr verwenden    →|Gewähren Sie einem vorgesehenen Administrator [Administratorberechtigungen](../deploy-use/configure-super-users.md) , und stellen Sie dieser Person das [RMS Protection Tool](http://www.microsoft.com/en-us/download/details.aspx?id=47256)zur Verfügung.<br /><br />Dieser Administrator kann dann das Tool verwenden, um eine Massenentschlüsselung der Dateien in Ordnern durchführen, die vom Azure Rights Management-Dienst geschützt wurden. Dateien werden auf die ungeschützte Einstellung zurückgesetzt und können deshalb ohne Rights Management-Technologie wie Azure Information Protection oder AD RMS gelesen werden. Da dieses Tool kann mit dem Azure Rights Management-Dienst von Azure Information Protection und AD RMS verwendet werden kann,haben Sie also die Möglichkeit, die Dateien vor dem oder nach dem Deaktivieren des Azure Rights Management-Diensts zu entschlüsseln.|
|Sie können nicht alle Dateien identifizieren, die durch den Azure Rights Management-Dienst von Azure Information Protection geschützt wurden. Oder Sie möchten, dass alle Benutzer geschützte Dateien, die ausgelassen wurden, automatisch lesen können →|Stellen Sie eine Registrierungseinstellung auf allen Clientcomputern bereit, indem Sie den **LicensingRedirection**-Registrierungsschlüssel für Office 2016 und Office 2013 verwenden, wie im [Abschnitt zur Diensterkennung](../rms-client/client-deployment-notes.md) in den Bereitstellungsanmerkungen für den RMS-Client beschrieben, sowie den **LicenseServerRedirection**-Registrierungsschlüssel für Office 2010 verwenden, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.<br /><br />Stellen Sie außerdem eine weitere Registrierungseinstellung bereit, um zu verhindern, dass Benutzer neue Dateien schützen. Legen Sie dazu **DisableCreation** auf **1** fest, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.|
|Sie möchten einen kontrollierten, manuellen Wiederherstellungsdienst für Dateien verwenden, die übergangen wurden    →|Gewähren Sie designierten Benutzern in einer Datenwiederherstellungsgruppe [Administratorberechtigungen](../deploy-use/configure-super-users.md) , und stellen Sie diesen Benutzern das [RMS Protection Tool](http://www.microsoft.com/en-us/download/details.aspx?id=47256) zur Verfügung, sodass sie den Schutz von Dateien aufheben können, wenn sie von Standardbenutzern dazu aufgefordert werden.<br /><br />Stellen Sie auf allen Computern die Registrierungseinstellung bereit, um zu verhindern, dass Benutzer neue Dateien schützen. Legen Sie dazu **DisableCreation** auf **1** fest, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.|
Weitere Informationen zu den Vorgehensweisen in dieser Tabelle finden Sie in den folgenden Ressourcen:

-   Informationen zu AD RMS und Bereitstellungsreferenzen finden Sie unter [Active Directory-Rechteverwaltungsdienste (Übersicht)](https://technet.microsoft.com/library/hh831364.aspx).

-   Anweisungen zum Importieren Ihres Azure Information Protection-Mandantenschlüssels als eine TPD-Datei finden Sie unter [Hinzufügen einer vertrauenswürdigen Veröffentlichungsdomäne](https://technet.microsoft.com/library/cc771460.aspx).

-   Informationen zum Installieren des Windows PowerShell-Moduls für Azure Information Protection zum Festlegen der Migrations-URL finden Sie unter [Installieren von Windows PowerShell für Azure Rights Management](install-powershell.md).

Wenn Sie soweit sind, dass Sie den Azure Rights Management-Dienst für Ihre Organisation deaktivieren können, gehen Sie gemäß den folgenden Anweisungen vor.

## <a name="deactivating-rights-management"></a>Deaktivieren von Rights Management
Verwenden Sie eine der folgenden Methoden, um [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu deaktivieren.

> [!TIP]
> Sie können auch das Windows PowerShell-Cmdlet [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm)zum Deaktivieren von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]verwenden.

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>So deaktivieren Sie Rights Management über das Office 365 Admin Center

1. Wechseln Sie zur [Rights Management-Seite](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) für Office 365-Administratoren.
    
    Wenn Sie aufgefordert werden, sich anzumelden, verwenden Sie das Konto eines globalen Administrators für Office 365.    

2. Klicken Sie auf der Seite **Rights Management** auf **Deaktivieren**.

3.  Wenn die Aufforderung **Möchten Sie Rights Management deaktivieren?** angezeigt wird, klicken Sie auf **Deaktivieren**.

Es sollte jetzt die Meldung **Rights Management ist nicht aktiviert** sowie die Option zum Aktivieren angezeigt werden.

#### <a name="to-deactivate-rights-management-from-the-azure-classic-portal"></a>So deaktivieren Sie Rights Management über das klassische Azure-Portal

1.  Melden Sie sich beim [klassischen Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=275081) an.

2.  Klicken Sie im linken Bereich auf **ACTIVE DIRECTORY**.

3.  Klicken Sie auf der Seite **Active Directory** auf **RIGHTS MANAGEMENT**.

4.  Stellen Sie sicher, dass Ihr Mandantenname ausgewählt ist, klicken Sie auf **DEAKTIVIEREN**, und bestätigen Sie Ihre Aktion.

Als **RIGHTS MANAGEMENT-STATUS** sollte jetzt **Inaktiv** angezeigt werden, und statt der Option **DEAKTIVIEREN** wird die Option **AKTIVIEREN**angezeigt.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>So deaktivieren Sie Rights Management über das Azure-Portal

Diese Methode befindet sich derzeit in der Vorschauphase.

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, melden Sie sich als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Auf dem ersten **Azure Information Protection**-Blatt wählen Sie **Einstellungen für RMS (Vorschau)** aus. 

3.  Wählen Sie auf dem Blatt **Azure Information Protection – Einstellungen für RMS (Vorschau)** die Option **Deaktivieren** aus. Klicken Sie zum Bestätigen Ihrer Auswahl auf **Ja**.

Die Informationsleiste zeigt daraufhin **Deactivation finished successfully** (Deaktivierung erfolgreich ausgeführt) an, und **Deaktivieren** wird nun durch **Aktivieren** ersetzt. 


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


