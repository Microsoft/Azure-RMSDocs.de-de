---
title: "HYOK-Einschränkungen für Azure Information Protection"
description: "Identifizieren Sie die Einschränkungen, Voraussetzungen und Empfehlungen, wenn Sie HYOK (AD RMS)-Schutz mit Azure Information Protection auswählen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ms.openlocfilehash: d7788b909da4219ae80475bac4bd26b2a2ec8da9
ms.sourcegitcommit: 9b229852c59441f9387bab1d5f28a3c5d9017696
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2017
---
# <a name="hold-your-own-key-hyok-requirements-and-restrictions-for-ad-rms-protection"></a>Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz

>*Gilt für: Azure Information Protection*

Wenn Sie Ihre vertraulichsten Dokumente und E-Mails schützen, tun Sie dies für gewöhnlich durch Anwenden des Azure Rights Management-Schutzes (Azure RMS), um von folgenden Punkten zu profitieren:

- Es ist keine Serverinfrastruktur erforderlich, wodurch die Lösung schneller und kostengünstiger bereitzustellen und zu verwalten ist als eine lokale Lösung.

- Einfachere Freigabe für Partner und Benutzer aus anderen Organisationen durch die Verwendung cloudbasierter Authentifizierung.

- Enge Integration mit Office 365-Diensten, wie z.B. Suche, Web-Viewer, pivotierte Sichten, Antischadsoftware, eDiscovery und Delve.

- Dokumentenverfolgung, Sperrung und E-Mail-Benachrichtigung für vertrauliche Dokumente, die Sie freigegeben haben.

Azure RMS schützt die Dokumente und E-Mails Ihrer Organisation durch die Verwendung eines privaten Schlüssels für die Organisation, die von Microsoft (standardmäßig) oder von Ihnen (das „Bring-your-own-key“- oder BYOK-Szenario) verwaltet wird. Die Informationen, die Sie mit Azure RMS schützen, werden nie an die Cloud gesendet. Die geschützte Dokumente und E-Mails werden nicht in Azure gespeichert, es sei denn, Sie speichern sie explizit dort oder verwenden einen anderen Clouddienst, der sie in Azure speichert. Weitere Informationen zu Mandantenschlüsseloptionen finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md). 

Allerdings müssen einige Organisationen möglicherweise eine kleine Teilmenge von Dokumenten und E-Mails mit einem Schlüssel schützen, der lokal gehostet wird. Dies kann aus gesetzlichen Gründen oder Kompatibilitätsgründen möglicherweise nicht erforderlich sein.  

Diese Konfiguration wird manchmal als „Hold Your Own Key“ (HYOK) bezeichnet und wird durch Azure Information Protection unterstützt, wenn Sie über eine funktionierende Active Directory Rights Management Services-Bereitstellung (AD RMS) mit den Anforderungen verfügen, die im nächsten Abschnitt beschrieben werden.

In diesem HYOK-Szenario werden die Richtlinien und der private Schlüssel der Organisation, die diese Richtlinien schützt, lokal verwaltet und gehalten, während die Azure Information Protection-Richtlinie für die Bezeichnung und Klassifizierung in Azure verwaltet und gespeichert wird. So wie bei Azure RMS-Schutz werden Informationen, die Sie mit AD RMS schützen, nie an die Cloud gesendet.

> [!NOTE]
> Verwenden Sie diese Konfiguration nur, wenn Sie es müssen, und auch nur für die Dokumente und E-Mails, die dies erfordern. AD RMS-Schutz bietet nicht die aufgeführten Vorteile, die Sie erhalten, wenn Sie Azure RMS-Schutz verwenden, und der Zweck davon ist „Uneinsehbarkeit um jeden Preis“.
>
> Sogar für Organisationen, die diese Konfiguration verwenden, eignet sie sich in der Regel nur für weniger als 10 % des gesamten Inhalts, der geschützt werden muss. Als Leitfaden gilt: Verwenden Sie es nur für Dokumente oder E-Mails, die alle folgenden Kriterien erfüllen:
> 
> **Der Inhalt weist den höchsten Geheimhaltungsgrad in Ihrer Organisation auf („Streng geheim“), und der Zugriff ist auf einige wenige Personen beschränkt.**
> 
> **Der Inhalt wird niemals außerhalb der Organisation freigegeben.**
> 
> **Der Inhalt wird nur im internen Netzwerk genutzt.**
> 
> **Auf den Inhalt muss nicht von Mac-Computern oder Mobilgeräten aus zugegriffen werden.**

Benutzer erkennen nicht, wenn eine Bezeichnung AD RMS-Schutz und nicht Azure RMS-Schutz verwendet. Stellen Sie aufgrund der Einschränkungen, die mit AD RMS-Schutz einhergehen sicher, dass Sie klare Anweisungen über die Ausnahmen für den Fall bieten, wenn Benutzer Bezeichnungen auswählen, die für den AD RMS-Schutz gelten. 

[Bereichsbezogene Richtlinien](configure-policy-scope.md) sind eine gute Möglichkeit, um sicherzustellen, dass Bezeichnungen, die für den AD RMS-Schutz konfiguriert sind, nur von Benutzern angezeigt werden können, die AD RMS-Schutz anwenden müssen. 

## <a name="additional-limitations-when-using-hyok"></a>Weitere Einschränkungen bei der Verwendung von HYOK

Bei Verwendung von AD RMS-Schutz in Verbindung mit Azure Information Protection werden die aufgeführten Vorteile des Azure RMS-Schutzes nicht unterstützt. Zudem sind damit folgende Einschränkungen verbunden:

- Office 2010 und Office 2007 werden nicht unterstützt.

- Weisen Sie die Benutzer an, in Outlook nicht **Nicht weiterleiten** auszuwählen, oder stellen Sie einen entsprechenden Leitfaden bereit. 

    Obwohl Sie einen Bezeichner für **Nicht weiterleiten** konfigurieren können, um HYOK oder den Azure Rights Management-Dienst zu verwenden, können Benutzer „Nicht weiterleiten“ auch selbst auswählen. Sie können diese Option auswählen, indem Sie die Schaltfläche **Nicht weiterleiten** auf der Registerkarte **Nachricht** des Office-Menübands oder die Outlook-Menüoptionen verwenden. Die Menüoptionen **Nicht weiterleiten** befinden sich in **Datei** > **Berechtigungen**. Die Schaltfläche **Berechtigungen** befindet sich in der Registerkarte **Optionen** des Menübands. 
    
    Der Azure Information Protection-Client verwendet immer Azure RMS, wenn ein Benutzer auf die Schaltfläche **Nicht weiterleiten** in Outlook klickt. Wenn Sie dieses Verhalten unterbinden möchten, können Sie diese Schaltfläche ausblenden, indem Sie die [Richtlinieneinstellung](../deploy-use/configure-policy-settings.md) **Add the Do Not Forward button to the Outlook ribbon** (Die Schaltfläche „Nicht weiterleiten“ dem Outlook-Menüband hinzufügen) auf **Aus** festlegen. 
    
    Wenn Benutzer auf **Nicht weiterleiten** über eine Outlook-Menüoption klicken, können sie Azure RMS oder AD RMS wählen, wissen aber möglicherweise nicht, welche Option für ihre E-Mail-Nachrichten ausgewählt ist. Wenn AD RMS verwendet wird, obwohl Azure RMS verwendet werden sollte, können externe Personen diese E-Mail-Nachrichten nicht öffnen.

- Wenn Sie benutzerdefinierte Berechtigungen für Word, Excel, PowerPoint und den Datei-Explorer konfigurieren: Im Datei-Explorer wird der Schutz immer mithilfe von Azure RMS statt mit HYOK (AD RMS) angewendet. Diese Beschränkung gilt nicht für die aktuelle Vorschauversion des Clients.

- Wenn Benutzer in Outlook eine Bezeichnung auswählen, die AD RMS-Schutz anwendet, und dann vor dem Senden der E-Mail-Adresse ihre Meinung ändern und eine Bezeichnung auswählen, die Azure RMS-Schutz anwendet, kann die neu ausgewählte Bezeichnung nicht angewendet werden. Es wird die folgende Fehlermeldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Sie sind nicht berechtigt, diese Aktion auszuführen.**
    
    Die einzige Problemumgehung besteht darin, die E-Mail-Nachricht zu schließen und von vorne zu beginnen. Die gleiche Einschränkung gilt, wenn Benutzer zunächst eine Bezeichnung auswählen, die Azure RMS-Schutz anwendet, und die Bezeichnung dann in eine Bezeichnung ändern, die AD RMS-Schutz anwendet.

## <a name="requirements-for-hyok"></a>Anforderungen an HYOK

Überprüfen Sie, dass Ihre AD RMS-Bereitstellung die folgenden Anforderungen für die Bereitstellung des AD RMS-Schutzes für Azure Information Protection erfüllt.

- AD RMS-Konfiguration:
    
    - Mindestversion von Windows Server 2012 R2: erforderlich für Produktionsumgebungen. Für Tests oder zu Evaluierungszwecken können Sie jedoch eine Mindestversion von Windows Server 2008 R2 mit Service Pack 1 verwenden.
    
    - Eine der folgenden Topologien:
        
        - Eine einzelne Gesamtstruktur mit einem einzelnen AD RMS-Stammcluster. 
        
        - Mehrere Gesamtstrukturen mit unabhängigen AD RMS-Stammclustern sowie Benutzer haben keinen Zugriff auf den Inhalt, der durch die Benutzer in den anderen Gesamtstrukturen geschützt wird.
        
        - Mehrere Gesamtstrukturen, die jeweils AD RMS-Cluster beinhalten. Jeder AD RMS-Cluster gibt eine Lizenzierungs-URL frei, die auf den gleichen AD RMS-Cluster zeigt. Sie müssen auf diesem AD RMS-Cluster alle Zertifikate der vertrauenswürdigen Benutzerdomänen (Truster User Domain, TUD) von allen anderen AD RMS-Clustern importieren. Weitere Informationen zu dieser Topologie finden Sie unter [Trusted User Domain (Vertrauenswürdige Benutzerdomäne)](https://technet.microsoft.com/library/dd983944(v=ws.10\).aspx).
        
    Wenn Sie über mehrere AD RMS-Cluster in separaten Gesamtstrukturen verfügen, löschen Sie Bezeichnungen in der globalen Richtlinie, die HYOK-Schutz (AD RMS) anwenden, und konfigurieren Sie eine [bereichsbezogene Richtlinie](configure-policy-scope.md) für jeden Cluster. Weisen Sie anschließend Benutzer für jeden Cluster ihrer bereichsbezogenen Richtlinie zu. Stellen Sie dabei sicher, dass Sie keine Gruppen verwenden, die dazu führen würden, dass ein Benutzer mehr als einer bereichsbezogenen Richtlinie zugewiesen werden würde. Jeder Benutzer sollte letztendlich Bezeichnungen für nur einen AD RMS-Cluster besitzen. 
    
    - [Kryptografiemodus 2](https://technet.microsoft.com/library/hh867439.aspx): Sie können den Modus auf der Registerkarte **Allgemein** der AD RMS-Clustereigenschaften prüfen.
    
    - Ein Dienstverbindungspunkt ist nicht in Active Directory registriert: Ein Dienstverbindungspunkt wird nicht verwendet, wenn Sie den AD RMS-Schutz mit Azure Information Protection verwenden. Wenn Sie über einen registrierten Dienstverbindungspunkt für Ihre AD RMS-Bereitstellung verfügen, müssen Sie diesen entfernen, sodass die [Dienstermittlung](../rms-client/client-deployment-notes.md#rms-service-discovery) für den Azure Rights Management-Schutz erfolgreich ist.
    
    - Die AD RMS-Server sind so konfiguriert, dass sie SSL/TLS mit einem gültigen x.509-Zertifikat verwenden, welches von den Clients, die eine Verbindung herstellen, als vertrauenswürdig eingestuft wird: Dies ist erforderlich für Produktionsumgebungen, aber nicht für Tests oder zu Evaluierungszwecken.
    
    - Konfigurierte Rechtevorlagen.

- Die Verzeichnissynchronisierung ist zwischen Ihrem lokalen Active Directory und Azure Active Directory konfiguriert, und Benutzer, die AD RMS-Schutz verwenden, werden für einmaliges Anmelden konfiguriert.

- Wenn Sie Dokumente oder E-Mails, die mithilfe von AD RMS geschützt wurden, mit anderen Personen außerhalb Ihrer Organisation teilen: AD RMS wird für explizit definierte Vertrauensstellungen in einer direkten Punkt-zu-Punkt-Beziehung mit den anderen Organisationen konfiguriert, indem entweder vertrauenswürdige Benutzerdomänen (trusted user domains, TUDs) oder Verbundvertrauensstellungen verwendet werden, die mit Active Directory-Verbunddienste erstellt wurden.

- Benutzer verfügen über eine Office-Version, und zwar Office 2013 Pro Plus mit Service Pack 1 oder Office 2016 Pro Plus, die auf Windows 7 Service Pack 1 oder höher ausgeführt wird. Beachten Sie, dass Office 2010 und Office 2007 für dieses Szenario nicht unterstützt werden.

> [!IMPORTANT]
> Wir empfehlen, dass sich Ihre AD RMS-Server nicht in Ihrem DMZ befinden und dass sie nur von ordnungsgemäß verwalteten Computern verwendet werden (z.B. keine mobilen Geräte oder Arbeitsgruppencomputer),um die hohe Sicherheit zu erfüllen, die dieses Szenario bietet. 
> 
> Außerdem wird empfohlen, dass das AD RMS-Cluster ein Hardwaresicherheitsmodul (HSM) verwendet, sodass der private Schlüssel für Ihr lizenzgebendes Serverzertifikat (SLC) nicht offengelegt oder gestohlen wird, wenn die AD RMS-Bereitstellung jemals verletzt oder gefährdet werden sollte. 

Weitere Informationen zur Bereitstellung sowie Anweisungen für AD RMS finden Sie unter [Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx) in der Windows Server-Bibliothek. 


## <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Suchen von Informationen zum Angeben des AD RMS-Schutzes mit einer Azure Information Protection-Bezeichnung

Wenn Sie eine Bezeichnung für den **HYOK (AD RMS)**-Schutz konfigurieren, müssen Sie die Lizenzierungs-URL Ihres AD RMS-Clusters angeben. Zusätzlich müssen Sie entweder eine Vorlage angeben, die Sie für die Berechtigungen konfiguriert haben, die Benutzern erteilt werden, oder Sie lassen die Benutzer die Berechtigungen und Benutzer definieren. 

Sie können die Vorlagen-GUID und die Werte für die Lizenzierungs-URL über die Konsole von Active Directory Rights Management Services suchen:

- Suchen einer Vorlagen-GUID: Erweitern Sie den Cluster, und klicken Sie auf **Vorlagen für Benutzerrechterichtlinien**. Sie können aus der Information **Verteilte Vorlagen für Benutzerrechterichtlinien** dann die GUID der Vorlage kopieren, die Sie verwenden möchten. Zum Beispiel: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Suchen der Lizenzierungs-URL: Klicken Sie auf den Clusternamen. Kopieren Sie aus der Information **Clusterdetails** den Wert **Lizenzierung** minus der Zeichenfolge **/_wmcs/licensing**. Zum Beispiel: https://rmscluster.contoso.com 
    
    Wenn Sie über einen Extranetlizenzierungswert sowie über einen Intranetlizenzierungswert verfügen und diese verschieden sind: Geben Sie den Extranetwert nur an, wenn Sie geschützte Dokumente oder E-Mails für Partner freigeben, mit denen Sie Punkt-zu-Punkt-Vertrauensstellungen definiert haben. Verwenden Sie andernfalls den Intranetwert, und stellen Sie sicher, dass alle Clientcomputer, die AD RMS-Schutz mit Azure Information Protection verwenden, eine Verbindung über eine Intranetverbindung herstellen (z.B. verwenden Remotecomputer eine VPN-Verbindung).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Feature sowie Hinweise dazu, wann Sie es verwenden sollten, finden Sie in der Blogbeitragsankündigung [Azure Information Protection with HYOK (Hold Your Own Key)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azure-information-protection-with-hyok-hold-your-own-key/) (in englischer Sprache).

Weitere Informationen zum Konfigurieren einer Bezeichnung für den AD RMS-Schutz finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](../deploy-use/configure-policy-protection.md). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]