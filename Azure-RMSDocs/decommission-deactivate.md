---
title: Außer Betrieb nehmen und Deaktivieren von Azure RMS
description: Informationen und Anweisungen für den Fall, dass Sie den cloudbasierten Schutzdienst von Azure Information Protection nicht mehr verwenden möchten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 683434b4094ca694539613279d0fae74bdde7be1
ms.sourcegitcommit: a5f595f8a453f220756fdc11fd5d466c71d51963
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67520550"
---
# <a name="decommissioning-and-deactivating-protection-for-azure-information-protection"></a>Außerbetriebsetzen und Deaktivieren des Schutzes für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Sie steuern immer, ob Ihre Organisation Inhalt mithilfe des Azure Rights Management-Diensts von Azure Information Protection schützt. Wenn Sie entscheiden, dass dieser Datenschutzdienst nicht mehr verwendet werden soll, können Sie sich sicher sein, dass Ihnen die bisher geschützten Inhalte trotzdem weiter uneingeschränkt zur Verfügung stehen.

Wenn Sie keinen weiteren Zugriff auf zuvor geschützte Inhalte mehr benötigen, deaktivieren Sie den Dienst, und lassen Sie Ihr Abonnement für Azure Information Protection ablaufen. Dies ist zum Beispiel angebracht, nachdem Sie das Testen von Azure Information Protection abgeschlossen haben, und bevor Sie es in einer Produktionsumgebung bereitstellen.

Wenn Sie Azure Information Protection jedoch in der Produktion bereitgestellt haben und Dokumente sowie E-Mails geschützt haben, stellen Sie sicher, dass Sie über eine Kopie Ihres Azure Information Protection-Mandantenschlüssels verfügen, bevor Sie den Azure Rights Management-Dienst deaktivieren. Stellen Sie sicher, dass Sie eine Kopie Ihres Schlüssels besitzen, bevor Ihr Abonnement abläuft, um sicherzustellen, dass Sie den Zugriff auf Inhalt beibehalten, der durch Azure Rights Management geschützt wurde, nachdem der Dienst deaktiviert wird. Wenn Sie die BYOK-Lösung (Bring Your Own Key) verwendet haben, bei der Sie Ihren eigenen Schlüssel in einem HSM erstellen und verwalten, verfügen Sie bereits über Ihren Azure Information Protection-Mandantenschlüssel. Wenn der Schlüssel jedoch von Microsoft verwaltet wurde (Standardlösung), lesen Sie die Anweisungen zum Exportieren Ihres Mandantenschlüssels im Artikel [Vorgänge für Ihren Azure Information Protection-Mandantenschlüssel](operations-tenant-key.md).

> [!TIP]
> Selbst nachdem Ihr Abonnement abgelaufen ist, steht Ihnen Ihr Azure Information Protection-Mandant zur Nutzung der Inhalte für einen erweiterten Zeitraum zur Verfügung. Sie können den Mandantenschlüssel dann jedoch nicht mehr exportieren.

Wenn Sie über einen Azure Information Protection-Mandantenschlüssel verfügen, können Sie Rights Management lokal bereitstellen (AD RMS) und Ihren Mandantenschlüssel als vertrauenswürdige Veröffentlichungsdomäne (Trusted Publishing Domain, TPD) importieren. Ihnen stehen dann die folgenden Optionen für die Außerbetriebsetzung Ihrer Azure Information Protection-Bereitstellung zur Verfügung:

|Wenn dies auf Sie zutrifft, ...|… gehen Sie wie folgt vor:|
|----------------------------|--------------|
|Sie möchten, dass alle Benutzer weiterhin Rights Management verwenden, wobei sie jedoch eine lokale Lösung statt Azure Information Protection verwenden sollen →|Leiten Sie Ihre Clients zur lokalen Bereitstellung mithilfe der **LicensingRedirection** Registrierungsschlüssel für Office 2016 oder Office 2013. Anweisungen finden Sie in der [Abschnitt zur diensterkennung](./rms-client/client-deployment-notes.md) in den Anmerkungen zur Bereitstellung des RMS-Client. Verwenden Sie für Office 2010 ist die **LicenseServerRedirection** -Registrierungsschlüssel für Office 2010 verwenden, wie in beschrieben [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Sie möchten die Rights Management-Technologie überhaupt nicht mehr verwenden    →|Gewähren Sie einem designierten Administrator [Administratorberechtigungen](configure-super-users.md), und installieren Sie den [Azure Information Protection-Client](./rms-client/client-admin-guide-install.md) für diesen Benutzer.<br /><br />Dieser Administrator können Sie dann das PowerShell-Modul von diesem Client massenentschlüsselung der Dateien in Ordnern durchführen, die von Azure Information Protection geschützt wurden. Dateien werden auf die ungeschützte Einstellung zurückgesetzt und können deshalb ohne Rights Management-Technologie wie Azure Information Protection oder AD RMS gelesen werden. Da dieses PowerShell-Moduls mit Azure Information Protection und AD RMS verwendet werden kann, müssen Sie die Möglichkeit, entschlüsseln Sie die Dateien vor oder nach dem Deaktivieren von des schutzdiensts von Azure Information Protection oder eine Kombination aus.|
|Sie sind nicht in der Lage, alle Dateien ermitteln, die von Azure Information Protection geschützt wurden. Oder Sie möchten, dass alle Benutzer geschützte Dateien, die ausgelassen wurden, automatisch lesen können →|Stellen Sie eine registrierungseinstellung auf allen Clientcomputern bereit, indem Sie mit der **LicensingRedirection** -Registrierungsschlüssel für Office 2016 und Office 2013 verwenden, wie in beschrieben die [Abschnitt zur diensterkennung](./rms-client/client-deployment-notes.md) in der RMS-Client Hinweise zur Bereitstellung. Verwenden Sie für Office 2010 ist die **LicenseServerRedirection** Registrierungsschlüssel unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).<br /><br />Stellen Sie außerdem eine weitere Registrierungseinstellung bereit, um zu verhindern, dass Benutzer neue Dateien schützen. Legen Sie dazu **DisableCreation** auf **1** fest, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.|
|Sie möchten einen kontrollierten, manuellen Wiederherstellungsdienst für Dateien verwenden, die übergangen wurden    →|Gewähren Sie designierten Benutzern in einer Datenwiederherstellungsgruppe [Administratorberechtigungen](configure-super-users.md), und installieren Sie den [Azure Information Protection-Client](./rms-client/client-admin-guide-install.md) für diese Benutzer, sodass diese den Dateischutz aufheben können, wenn diese Aktion von Standardbenutzern angefordert wird.<br /><br />Stellen Sie auf allen Computern die Registrierungseinstellung bereit, um zu verhindern, dass Benutzer neue Dateien schützen. Legen Sie dazu **DisableCreation** auf **1** fest, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.|

Weitere Informationen zu den Vorgehensweisen in dieser Tabelle finden Sie in den folgenden Ressourcen:

- Informationen zu AD RMS und Bereitstellungsreferenzen finden Sie unter [Active Directory-Rechteverwaltungsdienste (Übersicht)](https://technet.microsoft.com/library/hh831364.aspx).

- Anweisungen zum Importieren Ihres Azure Information Protection-Mandantenschlüssels als eine TPD-Datei finden Sie unter [Hinzufügen einer vertrauenswürdigen Veröffentlichungsdomäne](https://technet.microsoft.com/library/cc771460.aspx).

- Informationen zum Verwenden von PowerShell mit dem Azure Information Protection-Client finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).

Wenn Sie so deaktivieren Sie den Schutzdienst von Azure Information Protection bereit sind, gehen Sie folgendermaßen vor.

## <a name="deactivating-rights-management"></a>Deaktivieren von Rights Management
Verwenden Sie eines der folgenden Verfahren, um den Schutzdienst Azure Rights Management zu deaktivieren.

> [!TIP]
> Sie können auch das PowerShell-Cmdlet [Disable-AipService](/powershell/module/aipservice/disable-aipservice)zum Deaktivieren von Rights Management.

#### <a name="to-deactivate-rights-management-from-the-microsoft-365-admin-center"></a>So deaktivieren Sie Rights Management über das Microsoft 365 Admin Center

1. Wechseln Sie zur [Rights Management-Seite](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) für Office 365-Administratoren.
    
    Wenn Sie aufgefordert werden, sich anzumelden, verwenden Sie das Konto eines globalen Administrators für Office 365.

2. Klicken Sie auf der Seite **Rights Management** auf **Deaktivieren**.

3.  Wenn die Aufforderung **Möchten Sie Rights Management deaktivieren?** angezeigt wird, klicken Sie auf **Deaktivieren**.

Es sollte jetzt die Meldung **Rights Management ist nicht aktiviert** sowie die Option zum Aktivieren angezeigt werden.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>So deaktivieren Sie Rights Management über das Azure-Portal

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.

    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wählen Sie auf dem ersten **Azure Information Protection**-Blatt **Protection activation** (Schutzaktivierung) aus. 

3.  Wählen Sie auf dem Blatt **„Protection activation“ (Schutzaktivierung) von Azure Information Protection** **Deaktivieren** aus. Klicken Sie zum Bestätigen Ihrer Auswahl auf **Ja**.

Die Informationsleiste zeigt daraufhin **Deactivation finished successfully** (Deaktivierung erfolgreich ausgeführt) an, und **Deaktivieren** wird nun durch **Aktivieren** ersetzt. 
