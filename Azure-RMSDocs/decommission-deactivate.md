---
title: Außer Betrieb nehmen und Deaktivieren von Azure RMS
description: Informationen und Anweisungen für den Fall, dass Sie den cloudbasierten Schutzdienst von Azure Information Protection nicht mehr verwenden möchten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 09/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 4af20afcbf89ce25bc758299e42e794b3ee6b908
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73559699"
---
# <a name="decommissioning-and-deactivating-protection-for-azure-information-protection"></a>Außerbetriebsetzen und Deaktivieren des Schutzes für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Sie steuern immer, ob Ihre Organisation Inhalt mithilfe des Azure Rights Management-Diensts von Azure Information Protection schützt. Wenn Sie entscheiden, dass dieser Datenschutzdienst nicht mehr verwendet werden soll, können Sie sich sicher sein, dass Ihnen die bisher geschützten Inhalte trotzdem weiter uneingeschränkt zur Verfügung stehen.

Wenn Sie keinen weiteren Zugriff auf zuvor geschützte Inhalte mehr benötigen, deaktivieren Sie den Dienst, und lassen Sie Ihr Abonnement für Azure Information Protection ablaufen. Dies ist zum Beispiel angebracht, nachdem Sie das Testen von Azure Information Protection abgeschlossen haben, und bevor Sie es in einer Produktionsumgebung bereitstellen.

Wenn Sie jedoch Azure Information Protection in Produktions-und geschützten Dokumenten und e-Mails bereitgestellt haben, stellen Sie sicher, dass Sie über eine Kopie Ihres Azure Information Protection Mandanten Schlüssels und eine geeignete vertrauenswürdige Veröffentlichungs Domäne (TPD) verfügen, bevor Sie Azure deaktivieren. Rights Management-Dienst. Stellen Sie sicher, dass Sie über eine Kopie Ihres Schlüssels und der TPD verfügen, bevor Ihr Abonnement abläuft, um sicherzustellen, dass Sie den Zugriff auf Inhalte, die von Azure Rights Management geschützt wurden, nach dem Deaktivieren des Dienstanbieter erhalten. 

Wenn Sie die BYOK-Lösung (Bring Your Own Key) verwendet haben, bei der Sie Ihren eigenen Schlüssel in einem HSM erstellen und verwalten, verfügen Sie bereits über Ihren Azure Information Protection-Mandantenschlüssel. Außerdem verfügen Sie über eine passende TPD, wenn Sie die Anweisungen befolgt haben, die sich [auf einen zukünftigen cloudausgang vorbereiten](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/How-to-prepare-an-Azure-Information-Protection-Cloud-Exit-plan/ba-p/382631). Wenn Ihr Mandanten Schlüssel jedoch von Microsoft verwaltet wurde (Standardeinstellung), lesen Sie die Anweisungen zum Exportieren Ihres Mandanten Schlüssels im Artikel [Vorgänge für Ihren Azure Information Protection Mandanten Schlüssel](operations-tenant-key.md) .

> [!TIP]
> Selbst nachdem Ihr Abonnement abgelaufen ist, steht Ihnen Ihr Azure Information Protection-Mandant zur Nutzung der Inhalte für einen erweiterten Zeitraum zur Verfügung. Sie können den Mandantenschlüssel dann jedoch nicht mehr exportieren.

Wenn Sie über Ihren Azure Information Protection Mandanten Schlüssel und die TPD verfügen, können Sie Rights Management lokal bereitstellen (AD RMS) und ihren Mandanten Schlüssel als eine vertrauenswürdige Veröffentlichungs Domäne (Trusted Publishing Domain, TPD) importieren. Ihnen stehen dann die folgenden Optionen für die Außerbetriebsetzung Ihrer Azure Information Protection-Bereitstellung zur Verfügung:

|Wenn dies auf Sie zutrifft, ...|… Vorgehensweise|
|----------------------------|--------------|
|Sie möchten, dass alle Benutzer weiterhin Rights Management verwenden, wobei sie jedoch eine lokale Lösung statt Azure Information Protection verwenden sollen →|Leiten Sie Ihre Clients mit dem Registrierungsschlüssel **licensingredirection** für Office 2016 oder Office 2013 an die lokale Bereitstellung um. Anweisungen hierzu finden Sie im [Abschnitt Dienst](./rms-client/client-deployment-notes.md) Ermittlung der Hinweise zur Bereitstellung des RMS-Clients. Verwenden Sie für Office 2010 den Registrierungsschlüssel **licenseserverredirect** für Office 2010, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx)beschrieben.|
|Sie möchten die Rights Management-Technologie überhaupt nicht mehr verwenden    →|Gewähren Sie einem designierten Administrator [Administratorberechtigungen](configure-super-users.md), und installieren Sie den [Azure Information Protection-Client](./rms-client/client-admin-guide-install.md) für diesen Benutzer.<br /><br />Dieser Administrator kann dann das PowerShell-Modul dieses Clients verwenden, um Dateien in Ordnern, die durch Azure Information Protection geschützt wurden, Massen entschlüsselt. Dateien werden auf die ungeschützte Einstellung zurückgesetzt und können deshalb ohne Rights Management-Technologie wie Azure Information Protection oder AD RMS gelesen werden. Da dieses PowerShell-Modul sowohl mit Azure Information Protection als auch mit AD RMS verwendet werden kann, haben Sie die Möglichkeit, Dateien vor oder nach dem Deaktivieren des Schutz Dienstanbieter von Azure Information Protection oder einer Kombination zu entschlüsseln.|
|Sie sind nicht in der Lage, alle Dateien zu identifizieren, die durch Azure Information Protection geschützt wurden. Oder Sie möchten, dass alle Benutzer geschützte Dateien, die ausgelassen wurden, automatisch lesen können →|Stellen Sie eine Registrierungs Einstellung auf allen Client Computern bereit, indem Sie den Registrierungsschlüssel **licensingredirection** für Office 2016 und Office 2013 verwenden, wie im [Abschnitt Dienst](./rms-client/client-deployment-notes.md) Ermittlung der Hinweise zur Bereitstellung des RMS-Clients beschrieben. Verwenden Sie für Office 2010 den Registrierungsschlüssel **licenseserverredirect** , wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx)beschrieben.<br /><br />Stellen Sie außerdem eine weitere Registrierungseinstellung bereit, um zu verhindern, dass Benutzer neue Dateien schützen. Legen Sie dazu **DisableCreation** auf **1** fest, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.|
|Sie möchten einen kontrollierten, manuellen Wiederherstellungsdienst für Dateien verwenden, die übergangen wurden    →|Gewähren Sie designierten Benutzern in einer Datenwiederherstellungsgruppe [Administratorberechtigungen](configure-super-users.md), und installieren Sie den [Azure Information Protection-Client](./rms-client/client-admin-guide-install.md) für diese Benutzer, sodass diese den Dateischutz aufheben können, wenn diese Aktion von Standardbenutzern angefordert wird.<br /><br />Stellen Sie auf allen Computern die Registrierungseinstellung bereit, um zu verhindern, dass Benutzer neue Dateien schützen. Legen Sie dazu **DisableCreation** auf **1** fest, wie unter [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) beschrieben.|

Weitere Informationen zu den Vorgehensweisen in dieser Tabelle finden Sie in den folgenden Ressourcen:

- Informationen zu AD RMS und Bereitstellungsreferenzen finden Sie unter [Active Directory-Rechteverwaltungsdienste (Übersicht)](https://technet.microsoft.com/library/hh831364.aspx).

- Anweisungen zum Importieren Ihres Azure Information Protection-Mandantenschlüssels als eine TPD-Datei finden Sie unter [Hinzufügen einer vertrauenswürdigen Veröffentlichungsdomäne](https://technet.microsoft.com/library/cc771460.aspx).

- Informationen zum Verwenden von PowerShell mit dem Azure Information Protection-Client finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).

Wenn Sie bereit sind, den Schutzdienst von Azure Information Protection zu deaktivieren, befolgen Sie die folgenden Anweisungen.

## <a name="deactivating-rights-management"></a>Deaktivieren von Rights Management
Verwenden Sie eines der folgenden Verfahren, um den Schutzdienst (Azure-Rights Management zu deaktivieren.

> [!TIP]
> Sie können auch das PowerShell-Cmdlet " [Deaktivieren-aipservice](/powershell/module/aipservice/disable-aipservice)" verwenden, um Rights Management zu deaktivieren.

#### <a name="to-deactivate-rights-management-from-the-microsoft-365-admin-center"></a>So deaktivieren Sie Rights Management über das Microsoft 365 Admin Center

1. Wechseln Sie zur [Rights Management-Seite](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) für Office 365-Administratoren.
    
    Wenn Sie aufgefordert werden, sich anzumelden, verwenden Sie das Konto eines globalen Administrators für Office 365.

2. Klicken Sie auf der Seite **Rights Management** auf **Deaktivieren**.

3.  Wenn die Aufforderung **Möchten Sie Rights Management deaktivieren?** angezeigt wird, klicken Sie auf **Deaktivieren**.

Es sollte jetzt die Meldung **Rights Management ist nicht aktiviert** sowie die Option zum Aktivieren angezeigt werden.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>So deaktivieren Sie Rights Management über das Azure-Portal

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie dann zum Bereich **Azure Information Protection** .

    Beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumente: beginnen Sie mit der Eingabe von **Informationen** , und wählen Sie **Azure Information Protection**aus.

2. Wählen Sie im Bereich erste **Azure Information Protection** die Option **Schutz Aktivierung**aus. 

3.  Wählen Sie im Bereich **Azure Information Protection-Schutz Aktivierung** die Option **Deaktivieren**aus. Klicken Sie zum Bestätigen Ihrer Auswahl auf **Ja**.

Die Informationsleiste zeigt daraufhin **Deactivation finished successfully** (Deaktivierung erfolgreich ausgeführt) an, und **Deaktivieren** wird nun durch **Aktivieren** ersetzt. 
