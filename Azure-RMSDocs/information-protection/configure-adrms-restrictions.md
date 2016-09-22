---
title: "HYOK-Einschränkungen | Azure Information Protection"
description: Identify the limitations, prerequisites, and recommendations if you select AD RMS protection with Azure Information Protection. This solution is sometimes referred to as "hold your own key" (HYOK).
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
translationtype: Human Translation
ms.sourcegitcommit: 6bbac611f9c8bba96fbbba69e8044e494134d792
ms.openlocfilehash: fe0f492b94cbcc437c722daae9c3c56820593566


---

# Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Wenn Sie Ihre vertraulichsten Dokumente und E-Mails schützen, tun Sie dies für gewöhnlich durch Anwenden des Azure Rights Management-Schutzes, um von folgenden Punkten zu profitieren:

- Es ist keine Serverinfrastruktur erforderlich, wodurch die Lösung schneller und kostengünstiger bereitzustellen und zu verwalten ist als eine lokale Lösung.

- Einfachere Freigabe für Partner und Benutzer aus anderen Organisationen durch die Verwendung cloudbasierter Authentifizierung.

- Enge Integration mit Office 365-Diensten, wie z.B. Suche, Web-Viewer, pivotierte Sichten, Antischadsoftware, eDiscovery und Delve.

- Dokumentenverfolgung, Sperrung und E-Mail-Benachrichtigung für vertrauliche Dokumente, die Sie freigegeben haben.

Azure RMS schützt die Dokumente und E-Mails Ihrer Organisation durch die Verwendung eines privaten Schlüssels für die Organisation, die von Microsoft (standardmäßig) oder von Ihnen (das „Bring-your-own-key“- oder BYOK-Szenario) verwaltet wird. Die Informationen, die Sie mit Azure RMS schützen, werden nie an die Cloud gesendet. Die geschützte Dokumente und E-Mails werden nicht in Azure gespeichert, es sei denn, Sie speichern sie explizit dort oder verwenden einen anderen Clouddienst, der sie in Azure speichert. Weitere Informationen zum Mandantenschlüsseloptionen finden Sie unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md). 

Allerdings müssen einige Kunden möglicherweise ausgewählte Dokumente und E-Mails mit einem Schlüssel schützen, der lokal gehostet wird. Dies kann aus gesetzlichen Gründen oder Kompatibilitätsgründen möglicherweise nicht erforderlich sein. 

Diese Konfiguration wird manchmal als „Hold Your Own Key“ (HYOK) bezeichnet und wird durch Azure Information Protection unterstützt, wenn Sie über eine funktionierende Active Directory Rights Management Services-Bereitstellung (AD RMS) mit den Anforderungen verfügen, die im nächsten Abschnitt beschrieben werden. 

In diesem HYOK-Szenario werden die Richtlinien und der private Schlüssel der Organisation, die diese Richtlinien schützt, lokal verwaltet und gehalten, während die Azure Information Protection-Richtlinie für die Bezeichnung und Klassifizierung in Azure verwaltet und gespeichert wird. So wie bei Azure RMS-Schutz werden Informationen, die Sie mit AD RMS schützen, nie an die Cloud gesendet.

> [!NOTE]
> Verwenden Sie diese Konfiguration nur, wenn Sie es müssen, und auch nur für die Dokumente und E-Mails, die dies erfordern. AD RMS-Schutz bietet nicht die aufgeführten Vorteile, die Sie erhalten, wenn Sie Azure RMS-Schutz verwenden, und der Zweck davon ist „Uneinsehbarkeit um jeden Preis“.

Benutzer erkennen nicht, wenn eine Bezeichnung AD RMS-Schutz und nicht Azure RMS-Schutz verwendet. Stellen Sie aufgrund der Einschränkungen, die mit AD RMS-Schutz einhergehen sicher, dass Sie klare Anweisungen für den Fall bieten, wenn Benutzer Bezeichnungen auswählen, die für den AD RMS-Schutz gelten.

## Anforderungen an HYOK

Überprüfen Sie, dass Ihre AD RMS-Bereitstellung die folgenden Anforderungen für die Bereitstellung des AD RMS-Schutzes für Azure Information Protection erfüllt.

- AD RMS-Konfiguration:
    
    - Mindestversion von Windows Server 2012 R2: erforderlich für Produktionsumgebungen. Für Tests oder zu Evaluierungszwecken können Sie jedoch eine Mindestversion von Windows Server 2008 R2 mit Service Pack 1 verwenden.
    
    - Einzelner AD RMS-Stammcluster.
    
    - [Kryptografiemodus 2](https://technet.microsoft.com/library/hh867439.aspx): Sie können die Version des Kryptografiemodus des AD RMS-Clusters und dessen Gesamtzustand mithilfe des [RMS Analyzer-Tools](https://www.microsoft.com/en-us/download/details.aspx?id=46437) überprüfen.   
    
    - Die AD RMS-Server sind so konfiguriert, dass sie SSL/TLS mit einem gültigen x.509-Zertifikat verwenden, welches von den Clients, die eine Verbindung herstellen, als vertrauenswürdig eingestuft wird: Dies ist erforderlich für Produktionsumgebungen, aber nicht für Tests oder zu Evaluierungszwecken.
    
    - Konfigurierte Rechtevorlagen.

- Die Verzeichnissynchronisierung ist zwischen Ihrem lokalen Active Directory und Azure Active Directory konfiguriert, und Benutzer, die AD RMS-Schutz verwenden, werden für einmaliges Anmelden konfiguriert.

- Wenn Sie Dokumente oder E-Mails, die mithilfe von AD RMS geschützt wurden, mit anderen Personen außerhalb Ihrer Organisation teilen: AD RMS wird für explizit definierte Vertrauensstellungen in einer direkten Punkt-zu-Punkt-Beziehung mit den anderen Organisationen konfiguriert, indem entweder vertrauenswürdige Benutzerdomänen (trusted user domains; TUDs) oder Verbundvertrauensstellungen verwendet werden, die mit dem Active Directory-Verbunddienste (Active Directory Federation Services; AD FS) erstellt wurden.

- Benutzer verfügen über eine Office-Version, und zwar Office 2013 Pro Plus mit Service Pack 1 oder Office 2016 Pro Plus, die auf Windows 7 Service Pack 1 oder höher ausgeführt wird. Beachten Sie, dass Office 2010 und Office 2007 für dieses Szenario nicht unterstützt werden.

- Der [Azure Information Protection-Client](info-protect-client.md) weist die Version **1.0.233.0** oder höher auf.

> [!IMPORTANT]
> Wir empfehlen, dass sich Ihre AD RMS-Server nicht in Ihrem DMZ befinden und dass sie nur von ordnungsgemäß verwalteten Computern verwendet werden (z.B. keine mobilen Geräte oder Arbeitsgruppencomputer),um die hohe Sicherheit zu erfüllen, die dieses Szenario bietet. 
> 
> Außerdem wird empfohlen, dass das AD RMS-Cluster ein Hardwaresicherheitsmodul (HSM) verwendet, sodass der private Schlüssel für Ihr lizenzgebendes Serverzertifikat (SLC) nicht offengelegt oder gestohlen wird, wenn die AD RMS-Bereitstellung jemals verletzt oder gefährdet werden sollte. 

Weitere Informationen zur Bereitstellung sowie Anweisungen für AD RMS finden Sie unter [Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx) in der Windows Server-Bibliothek. 


## Suchen von Informationen zum Angeben des AD RMS-Schutzes mit einer Azure Information Protection-Bezeichnung

Wenn Sie eine Bezeichnung für den AD RMS-Schutz konfigurieren, müssen Sie die Vorlagen-GUID und Lizenzierungs-URL Ihres AD RMS-Clusters angeben. Sie können beide Werte in der Konsole von Active Directory Rights Management Services finden:

- Suchen der Vorlagen-GUID: Erweitern Sie den Cluster, und klicken Sie auf **Vorlagen für Benutzerrechterichtlinien**. Sie können aus der Information **Verteilte Vorlagen für Benutzerrechterichtlinien** dann die GUID der Vorlage kopieren, die Sie verwenden möchten. Zum Beispiel: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Suchen der Lizenzierungs-URL: Klicken Sie auf den Clusternamen. Kopieren Sie aus der Information **Clusterdetails** den Wert **Lizenzierung** minus der Zeichenfolge **/_wmcs/licensing**. Zum Beispiel: https://rmscluster.contoso.com 
    
    Wenn Sie über einen Extranetlizenzierungswert sowie über einen Intranetlizenzierungswert verfügen und diese verschieden sind: Geben Sie den Extranetwert nur an, wenn Sie geschützte Dokumente oder E-Mails für Partner freigeben, mit denen Sie Punkt-zu-Punkt-Vertrauensstellungen definiert haben. Verwenden Sie andernfalls den Intranetwert, und stellen Sie sicher, dass alle Clientcomputer, die AD RMS-Schutz mit Azure Information Protection verwenden, eine Verbindung über eine Intranetverbindung herstellen (z.B. verwenden Remotecomputer eine VPN-Verbindung).

## Nächste Schritte

Weitere Informationen zu dieser Previewfunktion finden Sie in der Blogbeitragsankündigung [Azure Information Protection with HYOK (Hold Your Own Key)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azure-information-protection-with-hyok-hold-your-own-key/) (in englischer Sprache).

Weitere Informationen zum Konfigurieren einer Bezeichnung für den AD RMS-Schutz finden Sie unter [Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden](configure-policy-protection.md). 



<!--HONumber=Sep16_HO1-->


