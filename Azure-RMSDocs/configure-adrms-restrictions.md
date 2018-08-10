---
title: HYOK-Schutz für Azure Information Protection
description: Übersicht über den HYOK-Schutz (AD RMS) mit Azure Information Protection und die dazugehörigen Szenarios, Einschränkungen, Voraussetzungen und Empfehlungen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/01/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ms.openlocfilehash: 07ce6d2bc9a606692ccaffb42cfe6717092c72b6
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39490323"
---
# <a name="hold-your-own-key-hyok-protection-for-azure-information-protection"></a>HYOK-Schutz (Hold Your Own Key) für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Anhand der folgenden Informationen erfahren Sie, was der HYOK-Schutz für Azure Information Protection ist, und wie er sich vom cloudbasierten Standardschutz unterscheidet. Stellen Sie sicher, dass Sie verstehen, wann der HYOK-Schutz, die unterstützten Szenarios, die Einschränkungen und die Voraussetzungen geeignet sind, bevor Sie ihn verwenden. 

## <a name="cloud-based-protection-vs-hyok"></a>Cloudbasierter Schutz im Vergleich zum Schutz mit HYOK

Wenn Sie Ihre vertraulichsten Dokumente und E-Mails mit Azure Information Protection schützen, tun Sie dies für gewöhnlich durch Anwenden eines cloudbasierten Schlüssels der den Azure Rights Management-Schutz (Azure RMS) verwendet, um von folgenden Punkten zu profitieren:

- Es ist keine Serverinfrastruktur erforderlich, wodurch die Lösung schneller und kostengünstiger bereitzustellen und zu verwalten ist als eine lokale Lösung.

- Einfachere Freigabe für Partner und Benutzer aus anderen Organisationen durch die Verwendung cloudbasierter Authentifizierung.

- Enge Integration mit anderen Azure- und Office 365-Diensten, wie z.B. Suche, Web-Viewer, pivotierte Ansichten, Antischadsoftware, eDiscovery und Delve.

- Dokumentenverfolgung, Sperrung und E-Mail-Benachrichtigung für vertrauliche Dokumente, die Sie freigegeben haben.

Ein cloudbasierter Schlüssel schützt die Dokumente und E-Mails Ihrer Organisation durch die Verwendung eines privaten Schlüssels für die Organisation, die von Microsoft (standardmäßig) oder von Ihnen (das „Bring Your Own Key“- bzw. BYOK-Szenario) verwaltet wird. Weitere Informationen zu Mandantenschlüsseloptionen finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

Dokumente und E-Mails, die Sie schützen, können in der Cloud oder lokal gespeichert werden. Weitere Informationen über die Funktionsweise des Schutzvorgangs für diesen cloudbasierten Schlüssel finden Sie unter [Was ist Azure Rights Management?](what-is-azure-rms.md )

Office 365-Dienste und cloudbasierte Anwendungen für Ihren Mandanten können mit Azure Information Protection integriert werden, sodass wichtige Geschäftsfunktionen, z.B. die Suche, Indizierung, Archivierung und Anti-Malware-Dienste, weiterhin problemlos für Inhalte verwendet werden können, die von Azure Information Protection geschützt werden. Diese Möglichkeit, den verschlüsselten Inhalt dieser Szenarios lesen zu können, wird häufig als „Schlussfolgern über Daten“ (reasoning over data) bezeichnet. Beispielsweise kann Exchange Online dank dieser Funktion E-Mails für die Überprüfung auf Schadsoftware entschlüsseln und Regeln für die Verhinderung von Datenverlust (DLP) auf verschlüsselten E-Mails ausführen.

Allerdings müssen einige Organisationen Inhalte aufgrund von gesetzlichen Anforderungen möglicherweise mit einem Schlüssel verschlüsseln, der von der Cloud isoliert ist. Diese Isolierung bedeutet, dass der verschlüsselte Inhalt nur von lokalen Anwendungen und lokalen Diensten gelesen werden kann. Diese Option für die Schlüsselverwaltung wird von Azure Information Protection unterstützt und als „Hold Your Own Key“ bzw. „HYOK“ bezeichnet. Wenn Sie Azure Information Protection mit HYOK verwenden, verfügt Ihr Mandant über einen cloudbasierten und einen lokalen Schlüssel.

## <a name="hyok-guidance-and-best-practices"></a>HYOK-Leitfaden und Best Practices

Verwenden Sie den HYOK-Schutz nur für Dokumente und E-Mails, die einen Verschlüsselungsschlüssel erfordern, der von der Cloud isoliert ist. Der HYOK-Schutz bietet nicht die aufgeführten Vorteile, die Sie erhalten, wenn Sie cloudbasierten Schlüsselschutz verwenden und ist oft mit der „Uneinsehbarkeit von Daten“ verbunden. Dieser Ausdruck bedeutet, dass nur lokale Anwendungen und Dienste dazu in der Lage sind, HYOK-geschützte Daten zu öffnen. Cloudbasierte Dienste und Anwendungen können nicht auf HYOK-geschützte Daten zugreifen.

Auch für die Organisationen, die den HYOK-Schutz verwenden, ist es in der Regel für eine kleine Anzahl an zu schützenden Dokumenten geeignet. Als Richtlinie gilt: Verwenden Sie es nur für Dokumente, die die folgenden Kriterien erfüllen:

- Der Inhalt weist den höchsten Geheimhaltungsgrad in Ihrer Organisation auf („Streng geheim“), und der Zugriff ist auf einige wenige Personen beschränkt.

- Der Inhalt wird nicht außerhalb der Organisation freigegeben.

- Der Inhalt wird nur im internen Netzwerk genutzt.

Da der HYOK-Schutz eine Administratorkonfigurationsoption für eine Bezeichnung ist, bleiben die Workflows der Benutzer unverändert, unabhängig davon, ob der Schutz einen cloudbasierten Schlüssel oder HYOK verwendet.

[Bereichsbezogene Richtlinien](configure-policy-scope.md) sind eine gute Möglichkeit, um sicherzustellen, dass Bezeichnungen für den HYOK-Schutz konfiguriert sind, nur von Benutzern angezeigt werden können, die den HYOK-Schutz anwenden müssen. 

## <a name="supported-scenarios-for-hyok"></a>Unterstützte Szenarios für HYOK

Verwenden Sie Bezeichner von Azure Information Protection, um den HYOK-Schutz anzuwenden. 

In der folgenden Tabelle werden die unterstützten Szenarios für den Schutz von Inhalten mithilfe von Bezeichnern aufgelistet, die für HYOK konfiguriert sind und Inhalte öffnen (bzw. verarbeiten), die vom HYOK-Schutz geschützt werden.

|Plattform|Anwendung|Unterstützt|
|----------------------|----------|-----------|
|Windows|Azure Information Protection-Client mit Office 2016 und Office 2013 <br /><br />Word, Excel, PowerPoint|Schutz: Ja<br /><br />Verbrauch: Ja|
|Windows|Azure Information Protection-Client mit Office 2016 und Office 2013 <br /><br />Outlook|Schutz: Ja<br /><br />Verbrauch: Ja|
|Windows|Azure Information Protection-Client mit Datei-Explorer|Schutz: Ja <br /><br />Verbrauch: Ja|
|Windows|Azure Information Protection-Viewer|Schutz: Nicht verfügbar<br /><br />Verbrauch: Ja|
|Windows|Azure Information Protection-Client PowerShell-Cmdlets für die Bezeichnung|Schutz: Ja<br /><br />Verbrauch: Ja|
|Windows|Azure Information Protection-Überprüfung|Schutz: Ja<br /><br />Verbrauch: Ja|
|Windows|Rights Management-Freigabeanwendung|Schutz: Nein<br /><br />Verbrauch: Ja|
|MacOS|Office für Mac <br /><br /> Word, Excel, PowerPoint|Schutz: Nein<br /><br />Verbrauch: Ja|
|MacOS|Office für Mac<br /><br />Outlook|Schutz: Nein<br /><br />Verbrauch: Ja|
|MacOS|Rights Management-Freigabeanwendung|Schutz: Nein<br /><br />Verbrauch: Ja|
|iOS|Office Mobile <br /><br />Word, Excel, PowerPoint|Schutz: Nein<br /><br />Verbrauch: Ja|
|iOS|Office Mobile <br /><br />Outlook|Schutz: Nein<br /><br />Verbrauch: Nein|
|iOS|Azure Information Protection-Viewer|Schutz: Nicht verfügbar<br /><br />Verbrauch: Ja|
|Android|Office Mobile <br /><br />Word, Excel, PowerPoint|Schutz: Nein<br /><br />Verbrauch: Ja|
|Android|Office Mobile <br /><br />Outlook|Schutz: Nein<br /><br />Verbrauch: Nein|
|Android|Azure Information Protection-Viewer|Schutz: Nicht verfügbar<br /><br />Verbrauch: Ja|
|Web|Outlook im Web|Schutz: Nein<br /><br />Verbrauch: Nein|
|Web|Office Online<br /><br />Word, Excel, PowerPoint|Schutz: Nein<br /><br />Verbrauch: Nein|
|Universell|Universelle Office-Apps<br /><br />Word, Excel, PowerPoint|Schutz: Nein<br /><br />Verbrauch: Nein|


## <a name="additional-limitations-when-using-hyok"></a>Weitere Einschränkungen bei der Verwendung von HYOK

Darüber hinaus unterliegt die Verwendung des HYOK-Schutzes mit Azure Information Protection den folgenden Einschränkungen:

- Office 2010 und Office 2007 werden nicht unterstützt.

- Office 365-Dienste und andere Onlinedienste können HYOK-geschützte Dokumente und E-Mails nicht entschlüsseln, um den Inhalt zu überprüfen oder Aktionen auszuführen. Diese Einschränkung erstreckt sich über HYOK-geschützte Dokumente und E-Mails, die mit dem Rights Management-Connector geschützt werden. 
    
    Dieser Funktionsverlust bei HYOK-geschützten E-Mails schließt Malwarescanner, Lösungen für die Verhinderung von Datenverlust, E-Mail-Routing-Regeln, Journaling, eDiscovery, Archivierungslösungen und Exchange ActiveSync ein. Darüber hinaus werden Benutzer nicht verstehen, warum einige Geräte ihre HYOK-geschützten E-Mails nicht öffnen können, was zu Anrufen bei Ihrem Helpdesk führen kann. Aufgrund dieser vielen Einschränkungen wird der HYOK-Schutz für E-Mails nicht empfohlen.

## <a name="implementing-hyok"></a>Implementieren von HYOK

HYOK wird von Azure Information Protection unterstützt, wenn Sie über eine funktionierende Active Directory Rights Management Services-Bereitstellung (AD RMS) mit den Anforderungen verfügen, die im nächsten Abschnitt beschrieben werden. In diesem Szenario werden die Richtlinien zu den Nutzungsrechten und der private Schlüssel der Organisation, die diese Richtlinien schützt, lokal verwaltet und gehalten, während die Azure Information Protection-Richtlinie für die Bezeichnung und Klassifizierung in Azure verwaltet und gespeichert wird. 

Verwechseln Sie HYOK und Azure Information Protection nicht mit der Verwendung einer vollständigen AD RMS-Bereitstellung und Azure Information Protection bzw. einer Alternative zur Migration von AD RMS zu Azure Information Protection. HYOK wird nur durch das Anwenden von Bezeichnern unterstützt, bietet keine Featureparität mit AD RMS an und unterstützt nicht alle AD RMS-Bereitstellungskonfigurationen:

- Weitere Informationen über Szenarios, die von HYOK zum Schützen von Inhalten und Verarbeiten von geschütztem Inhalten unterstützt werden, finden Sie im Abschnitt [Unterstützte Szenarios für HYOK](#supported-scenarios-for-hyok).

- Anweisungen für die Migration aus AD RMS finden Sie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

- Weitere Informationen zu den Bereitstellungsanforderungen von AD RMS finden Sie im nächsten Abschnitt.

### <a name="requirements-for-ad-rms-to-support-hyok"></a>Anforderungen für die Unterstützung für HYOK von AD RMS

Eine AD RMS-Bereitstellung muss die folgenden Anforderungen erfüllen, um den HYOK-Schutz für Azure Information Protection-Bezeichner bereitzustellen.

- AD RMS-Konfiguration:
    
    - Mindestversion von Windows Server 2012 R2: erforderlich für Produktionsumgebungen. Für Tests oder zu Evaluierungszwecken können Sie jedoch eine Mindestversion von Windows Server 2008 R2 mit Service Pack 1 verwenden.
    
    - Eine der folgenden Topologien:
        
        - Eine einzelne Gesamtstruktur mit einem einzelnen AD RMS-Stammcluster. 
        
        - Mehrere Gesamtstrukturen mit unabhängigen AD RMS-Stammclustern sowie Benutzer haben keinen Zugriff auf den Inhalt, der durch die Benutzer in den anderen Gesamtstrukturen geschützt wird.
        
        - Mehrere Gesamtstrukturen, die jeweils AD RMS-Cluster beinhalten. Jeder AD RMS-Cluster gibt eine Lizenzierungs-URL frei, die auf den gleichen AD RMS-Cluster zeigt. Sie müssen auf diesem AD RMS-Cluster alle Zertifikate der vertrauenswürdigen Benutzerdomänen (Truster User Domain, TUD) von allen anderen AD RMS-Clustern importieren. Weitere Informationen zu dieser Topologie finden Sie unter [Trusted User Domain (Vertrauenswürdige Benutzerdomäne)](https://technet.microsoft.com/library/dd983944(v=ws.10\).aspx).
        
    Wenn Sie über mehrere AD RMS-Cluster in separaten Gesamtstrukturen verfügen, löschen Sie Bezeichnungen in der globalen Richtlinie, die HYOK-Schutz (AD RMS) anwenden, und konfigurieren Sie eine [bereichsbezogene Richtlinie](configure-policy-scope.md) für jeden Cluster. Weisen Sie anschließend Benutzer für jeden Cluster ihrer bereichsbezogenen Richtlinie zu. Stellen Sie dabei sicher, dass Sie keine Gruppen verwenden, die dazu führen würden, dass ein Benutzer mehr als einer bereichsbezogenen Richtlinie zugewiesen werden würde. Jeder Benutzer sollte letztendlich Bezeichnungen für nur einen AD RMS-Cluster besitzen. 
    
    - [Kryptografiemodus 2](https://technet.microsoft.com/library/hh867439.aspx): Sie können den Modus auf der Registerkarte **Allgemein** der AD RMS-Clustereigenschaften prüfen.
    
    - Jeder AD RMS-Server wird für die Zertifizierungs-URL konfiguriert. [Anweisungen](#configuring-ad-rms-servers-to-locate-the-certification-url) 
    
    - Ein Dienstverbindungspunkt ist nicht in Active Directory registriert: Ein Dienstverbindungspunkt wird nicht verwendet, wenn Sie den AD RMS-Schutz mit Azure Information Protection verwenden. 
    
        - Wenn Sie über einen registrierten Dienstverbindungspunkt für Ihre AD RMS-Bereitstellung verfügen, müssen Sie diesen entfernen, sodass die [Dienstermittlung](./rms-client/client-deployment-notes.md#rms-service-discovery) für den Azure Rights Management-Schutz erfolgreich ist. 
        
        - Bei der Installation eines neuen AD RMS-Clusters für HYOK überspringen Sie den Schritt zur Registrierung des Dienstverbindungspunkts bei der Konfiguration des ersten Knotens. Stellen Sie für jeden weiteren Knoten sicher, dass der Server für die Zertifizierungs-URL konfiguriert ist, bevor Sie die AD RMS-Rolle hinzufügen und dem vorhandenen Cluster beitreten.
    
    - Die AD RMS-Server sind so konfiguriert, dass sie SSL/TLS mit einem gültigen x.509-Zertifikat verwenden, welches von den Clients, die eine Verbindung herstellen, als vertrauenswürdig eingestuft wird: Dies ist erforderlich für Produktionsumgebungen, aber nicht für Tests oder zu Evaluierungszwecken.
    
    - Konfigurierte Rechtevorlagen.
    
    - Nicht für Exchange IRM konfiguriert
    
    - Für Mobilgeräte und Mac-Computer: [Active Directory Rights Management Services Mobile Device Extension (Active Directory Rights Management Services-Mobilgeräteerweiterung)](https://technet.microsoft.com/library/dn673574.aspx) ist installiert und konfiguriert.

- Die Verzeichnissynchronisierung ist zwischen Ihrem lokalen Active Directory und Azure Active Directory konfiguriert, und Benutzer, die den HYOK-Schutz verwenden, werden für einmaliges Anmelden konfiguriert.

- Wenn Sie Dokumente oder E-Mails, die mithilfe von HYOK geschützt wurden, mit anderen Personen außerhalb Ihrer Organisation teilen: AD RMS wird für explizit definierte Vertrauensstellungen in einer direkten Punkt-zu-Punkt-Beziehung mit den anderen Organisationen konfiguriert, indem entweder vertrauenswürdige Benutzerdomänen (trusted user domains, TUDs) oder Verbundvertrauensstellungen verwendet werden, die mit Active Directory-Verbunddiensten erstellt wurden.

- Benutzer haben eine Version von Office 2016 Professional Plus oder Office 2013 Professional Plus mit Service Pack 1, die auf Windows 7 Service Pack 1 oder höher ausgeführt wird. Beachten Sie, dass Office 2010 und Office 2007 für dieses Szenario nicht unterstützt werden.
    
    - Für Office 2016, auf Microsoft Installer (.msi) basierte Ausgabe: Sie haben [Update 4018295 für Microsoft Office 2016 vom 6. März 2018](https://support.microsoft.com/en-us/help/4018295/march-6-2018-update-for-office-2016-kb4018295) installiert.

> [!IMPORTANT]
> Zum Erfüllen der hohen Sicherheit des HYOK-Schutzes wird empfohlen, dass Ihre AD RMS-Server sich nicht in Ihrem Umkreisnetzwerk befinden und nur von verwalteten Geräten verwendet werden. 
> 
> Außerdem wird empfohlen, dass das AD RMS-Cluster ein Hardwaresicherheitsmodul (HSM) verwendet, sodass der private Schlüssel für Ihr lizenzgebendes Serverzertifikat (SLC) nicht offengelegt oder gestohlen wird, wenn die AD RMS-Bereitstellung jemals verletzt oder gefährdet werden sollte. 

Weitere Informationen zur Bereitstellung sowie Anweisungen für AD RMS finden Sie unter [Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx) in der Windows Server-Bibliothek. 


### <a name="configuring-ad-rms-servers-to-locate-the-certification-url"></a>Konfigurieren von AD RMS-Servern zum Finden der Zertifizierungs-URL

1. Erstellen Sie auf jedem AD RMS-Server im Cluster den folgenden Registrierungseintrag:

    `Computer\HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\GICURL = "<string>"`
    
    Geben Sie für den \<Zeichenfolgenwert> einen der folgenden Einträge an:
    
    - Für AD RMS-Cluster mit SSL/TLS:

            https://<cluster_name>/_wmcs/certification/certification.asmx
    
    - Für AD RMS-Cluster ohne SSL/TLS (nur für Testnetzwerke):
        
            http://<cluster_name>/_wmcs/certification/certification.asmx

2. Starten Sie IIS neu.

### <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Suchen von Informationen zum Angeben des AD RMS-Schutzes mit einer Azure Information Protection-Bezeichnung

Wenn Sie eine Bezeichnung für den **HYOK (AD RMS)**-Schutz konfigurieren, müssen Sie die Lizenzierungs-URL Ihres AD RMS-Clusters angeben. Zusätzlich müssen Sie entweder eine Vorlage angeben, die Sie für die Berechtigungen konfiguriert haben, die Benutzern erteilt werden, oder Sie lassen die Benutzer die Berechtigungen und Benutzer definieren. 

Sie können die Vorlagen-GUID und die Werte für die Lizenzierungs-URL über die Konsole von Active Directory Rights Management Services suchen:

- Suchen einer Vorlagen-GUID: Erweitern Sie den Cluster, und klicken Sie auf **Vorlagen für Benutzerrechterichtlinien**. Sie können aus der Information **Verteilte Vorlagen für Benutzerrechterichtlinien** dann die GUID der Vorlage kopieren, die Sie verwenden möchten. Zum Beispiel: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Suchen der Lizenzierungs-URL: Klicken Sie auf den Clusternamen. Kopieren Sie aus der Information **Clusterdetails** den Wert **Lizenzierung** minus der Zeichenfolge **/_wmcs/licensing**. Beispiel: https://rmscluster.contoso.com 
    
    Wenn Sie über einen Extranetlizenzierungswert sowie über einen Intranetlizenzierungswert verfügen und diese verschieden sind: Geben Sie den Extranetwert nur an, wenn Sie geschützte Dokumente oder E-Mails für Partner freigeben, mit denen Sie Punkt-zu-Punkt-Vertrauensstellungen definiert haben. Verwenden Sie andernfalls den Intranetwert, und stellen Sie sicher, dass alle Clientcomputer, die AD RMS-Schutz mit Azure Information Protection verwenden, eine Verbindung über eine Intranetverbindung herstellen (z.B. verwenden Remotecomputer eine VPN-Verbindung).


## <a name="next-steps"></a>Nächste Schritte

Informationen zum Konfigurieren einer Bezeichnung für den HYOK-Schutz finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md). 
