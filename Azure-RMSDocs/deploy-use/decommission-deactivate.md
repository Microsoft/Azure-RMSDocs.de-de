---
title: "Außerbetriebsetzen und Deaktivieren des Azure Rights Management-Diensts | Azure Information Protection"
description: "Informationen und Anweisungen für den Fall, dass Sie diese Lösung für den Informationsschutz von Azure Information Protection nicht mehr verwenden möchten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 865913eae3e0956c18d2caef4e68ab1dc07d74de


---

# <a name="decommissioning-and-deactivating-azure-rights-management"></a>Außerbetriebsetzen und Deaktivieren von Azure Rights Management

>*Gilt für: Azure Information Protection, Office 365*

Sie können jederzeit steuern, ob Ihre Organisation Inhalte dem Azure Rights Management-Dienst von Azure Information Protection schützt. Wenn Sie entscheiden, dass diesen Dienst zum Schutz von Daten nicht mehr verwendet werden soll, können Sie sich sicher sein, dass Ihnen die zuvor geschützten Inhalte weiterhin uneingeschränkt zur Verfügung stehen. Wenn Sie keinen weiteren Zugriff auf zuvor geschützte Inhalte mehr benötigen, deaktivieren Sie einfach den Dienst, und lassen Sie Ihr Abonnement für Azure Information Protection ablaufen. Dies ist zum Beispiel angebracht, nachdem Sie das Testen von Azure Information Protection abgeschlossen haben, und bevor Sie es in einer Produktionsumgebung bereitstellen.

Wenn Sie Azure Information Protection jedoch in einer Produktionsumgebung bereitgestellt haben, müssen Sie sicherstellen, dass Sie über eine Kopie Ihres Azure Information Protection-Mandantenschlüssels verfügen, bevor Sie den Azure Rights Management-Dienst deaktivieren. Erledigen Sie dies unbedingt vor Ablauf des Abonnements, weil dadurch sichergestellt ist, dass Sie nach dem Deaktivieren des Diensts weiterhin Zugriff auf Inhalte haben, die von Azure Rights Management geschützt wurden. Wenn Sie die BYOK-Lösung (Bring Your Own Key) verwendet haben, bei der Sie Ihren eigenen Schlüssel in einem HSM erstellen und verwalten, verfügen Sie bereits über Ihren Azure Information Protection-Mandantenschlüssel. Wenn der Schlüssel jedoch von Microsoft verwaltet wurde (Standardlösung), lesen Sie die Anweisungen zum Exportieren Ihres Mandantenschlüssels im Artikel [Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel](operations-tenant-key.md).

> [!TIP]
> Selbst nachdem Ihr Abonnement abgelaufen ist, steht Ihnen Ihr Azure Information Protection-Mandant zur Nutzung der Inhalte für einen erweiterten Zeitraum zur Verfügung. Sie können den Mandantenschlüssel dann jedoch nicht mehr exportieren.

Wenn Sie über einen Azure Information Protection-Mandantenschlüssel verfügen, können Sie Rights Management lokal bereitstellen (AD RMS) und Ihren Mandantenschlüssel als eine vertrauenswürdige Veröffentlichungsdomäne (Trusted Publishing Domain, TPD) importieren. Ihnen stehen dann die folgenden Optionen für die Außerbetriebsetzung Ihrer Azure Information Protection-Bereitstellung zur Verfügung:

|Wenn dies auf Sie zutrifft, ...|… Vorgehensweise|
|----------------------------|--------------|
|Sie möchten, dass alle Benutzer weiterhin Rights Management verwenden, wobei Sie jedoch eine lokale Lösung statt Azure Information Protection verwenden möchten.    →|Verwenden Sie das Cmdlet [Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx), um vorhandene Benutzer zu Ihrer lokalen Bereitstellung zu leiten, wenn diese Benutzer Inhalte verwenden möchten, die nach dieser Änderung geschützt wurden. Benutzer verwenden automatisch die AD RMS-Installation, um die geschützten Inhalt zu nutzen.<br /><br />Damit Benutzer Inhalte verwenden können, die vor dieser Änderung geschützt wurden, leiten Sie die Clients auf die lokale Bereitstellung um, indem Sie den **LicensingRedirection**-Registrierungsschlüssel für Office 2016 oder Office 2013 verwenden, wie im [Abschnitt zur Diensterkennung](../rms-client/client-deployment-notes.md) in den Bereitstellungsanmerkungen für den RMS-Client beschrieben, sowie den **LicenseServerRedirection**-Registrierungsschlüssel für Office 2010 verwenden, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.|
|Sie möchten die Rights Management-Technologie überhaupt nicht mehr verwenden    →|Gewähren Sie einem vorgesehenen Administrator [Administratorberechtigungen](../deploy-use/configure-super-users.md) , und stellen Sie dieser Person das [RMS Protection Tool](http://www.microsoft.com/en-us/download/details.aspx?id=47256)zur Verfügung.<br /><br />Dieser Administrator kann dann mit dem Tool eine Massenentschlüsselung der Dateien in Ordnern durchführen, die durch den Azure Rights Management-Dienst geschützt wurden, sodass die Dateien wieder ungeschützt sind und daher ohne eine Rights Management-Technologie wie Azure Information Protection oder AD RMS gelesen werden können. Dieses Tool kann mit dem Azure Rights Management-Dienst von Azure Information Protection und AD RMS verwendet werden. Sie haben also die Möglichkeit, die Dateien vor dem oder nach dem Deaktivieren des Azure Rights Management-Diensts zu entschlüsseln.|
|Sie können nicht alle Dateien ermitteln, die durch den Azure Rights Management-Dienst von Azure Information Protection geschützt wurden, oder Sie möchten, dass alle Benutzer automatisch jede geschützte Datei lesen können, die verpasst wurde    →|Stellen Sie eine Registrierungseinstellung auf allen Clientcomputern bereit, indem Sie den **LicensingRedirection**-Registrierungsschlüssel für Office 2016 und Office 2013 verwenden, wie im [Abschnitt zur Diensterkennung](../rms-client/client-deployment-notes.md) in den Bereitstellungsanmerkungen für den RMS-Client beschrieben, sowie den **LicenseServerRedirection**-Registrierungsschlüssel für Office 2010 verwenden, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.<br /><br />Stellen Sie außerdem eine weitere Registrierungseinstellung bereit, um zu verhindern, dass Benutzer neue Dateien schützen. Legen Sie dazu **DisableCreation** auf **1** fest, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.|
|Sie möchten einen kontrollierten, manuellen Wiederherstellungsdienst für Dateien verwenden, die übergangen wurden    →|Gewähren Sie designierten Benutzern in einer Datenwiederherstellungsgruppe [Administratorberechtigungen](../deploy-use/configure-super-users.md) , und stellen Sie diesen Benutzern das [RMS Protection Tool](http://www.microsoft.com/en-us/download/details.aspx?id=47256) zur Verfügung, sodass sie den Schutz von Dateien aufheben können, wenn sie von Standardbenutzern dazu aufgefordert werden.<br /><br />Stellen Sie auf allen Computern die Registrierungseinstellung bereit, um zu verhindern, dass Benutzer neue Dateien schützen. Legen Sie dazu **DisableCreation** auf **1** fest, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.|
Weitere Informationen zu den Vorgehensweisen in dieser Tabelle finden Sie in den folgenden Ressourcen:

-   Informationen zu AD RMS und Bereitstellungsreferenzen finden Sie unter [Active Directory-Rechteverwaltungsdienste (Übersicht)](https://technet.microsoft.com/library/hh831364.aspx).

-   Anweisungen zum Importieren Ihres Azure Information Protection-Mandantenschlüssels als eine TPD-Datei finden Sie unter [Hinzufügen einer vertrauenswürdigen Veröffentlichungsdomäne](https://technet.microsoft.com/library/cc771460.aspx).

-   Informationen zum Installieren des Windows PowerShell-Moduls für Azure Information Protection zum Festlegen der Migrations-URL finden Sie unter [Installieren von Windows PowerShell für Azure Rights Management](install-powershell.md).

Wenn Sie soweit sind, dass Sie den Azure Rights Management-Dienst für Ihre Organisation deaktivieren können, gehen Sie gemäß den folgenden Anweisungen vor.

## <a name="deactivating-rights-management"></a>Deaktivieren von Rights Management
Verwenden Sie eine der folgenden Methoden, um [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu deaktivieren.

> [!TIP]
> Sie können auch das Windows PowerShell-Cmdlet [Disable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx)zum Deaktivieren von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]verwenden.

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>So deaktivieren Sie Rights Management über das Office 365 Admin Center

1.  [Melden Sie sich bei Office 365 mit einem Geschäfts- oder Schulkonto an](https://portal.office.com/) , das als ein Administratorkonto für Ihre Office 365-Bereitstellung fungiert.

2.  Wenn das Office 365 Admin Center nicht automatisch angezeigt wird, wählen Sie in der linken oberen Ecke das Symbol für das App-Startprogramm aus, und wählen Sie dann **Administrator** aus. Die Kachel **Administrator** wird nur für Office 365-Administratoren angezeigt.

    > [!TIP]
    > Hilfe zum Admin Center finden Sie in [Informationen zum Office 365 Admin Center - Hilfe für Administratoren](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  Klicken Sie im linken Bereich auf **DIENSTEINSTELLUNGEN**.

4.  Klicken Sie auf **Rights Management**.

5.  Klicken Sie auf der Seite **RIGHTS MANAGEMENT** auf **Verwalten**.

6.  Klicken Sie auf der Seite **Rights Management** auf **Deaktivieren**.

7.  Wenn die Aufforderung **Möchten Sie Rights Management deaktivieren?**angezeigt wird, klicken Sie auf **Deaktivieren**.

Es sollte jetzt die Meldung **Rights Management ist nicht aktiviert** sowie die Option zum Aktivieren angezeigt werden.

#### <a name="to-deactivate-rights-management-from-the-azure-classic-portal"></a>So deaktivieren Sie Rights Management über das klassische Azure-Portal

1.  Melden Sie sich beim [klassischen Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=275081) an.

2.  Klicken Sie im linken Bereich auf **ACTIVE DIRECTORY**.

3.  Klicken Sie auf der Seite **Active Directory** auf **RIGHTS MANAGEMENT**.

4.  Wählen Sie das für [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]zu verwaltende Verzeichnis aus, klicken Sie auf **DEAKTIVIEREN**, und bestätigen Sie den Vorgang.

Als **RIGHTS MANAGEMENT-STATUS** sollte jetzt **Inaktiv** angezeigt werden, und statt der Option **DEAKTIVIEREN** wird die Option **AKTIVIEREN**angezeigt.






<!--HONumber=Nov16_HO2-->


