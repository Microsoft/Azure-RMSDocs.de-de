---
title: "Migrieren von AD RMS zu Azure Information Protection – Phase 4 | Azure Information Protection"
description: Phase 4 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 8 bis 9 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 9c78ac81a90d46ab8d56cd205474fdf85f486c3d


---

# <a name="migration-phase-4---post-migration-tasks"></a>Migrationsphase 4: Aufgaben nach der Migration

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Verwenden Sie die folgenden Informationen für Phase 4 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken die Schritte 8 bis 9 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.


## <a name="step-8-decommission-ad-rms"></a>Schritt 8: Außerbetriebsetzung von AD RMS

Entfernen Sie den Dienstverbindungspunkt (Service Connection Point, SCP) aus Active Directory, um zu verhindern, dass Computer Ihre lokale Rights Management-Infrastruktur ermitteln. Dies ist für die vorhandenen Clients, die Sie migriert haben, optional, und zwar aufgrund der Umleitung, die Sie in der Registrierung konfiguriert haben (z. B. durch Ausführen des Migrationsskripts). Allerdings hindert das Entfernen des Dienstverbindungspunkts neue Clients und möglicherweise auf RMS bezogene Dienste und Tools am Auffinden des Dienstverbindungspunkts, wenn die Migration abgeschlossen ist und alle Verbindungen mit dem Azure Rights Management-Dienst hergestellt werden sollten. Um den Service Connection Point zu entfernen, verwenden Sie das AD-SCP-Register-Tool aus dem [Rights Management Services-Verwaltungstoolkit](http://www.microsoft.com/download/details.aspx?id=1479).

Überwachen Sie die Aktivität Ihrer AD RMS-Server, z.B. durch Überprüfen der [Anforderungen im Systemintegritätsbericht](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx) und der [ServiceRequest-Tabelle](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) oder durch [Überwachung des Benutzerzugriffs auf geschützte Inhalte](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Wenn Sie bestätigt haben, dass RMS-Clients nicht mehr mit diesen Servern kommunizieren und Clients erfolgreich Azure Information Protection verwenden, können Sie die AD RMS-Serverrolle von diesen Servern entfernen. Wenn Sie dedizierte Server verwenden, können Sie auch als Vorsichtsmaßnahme zuerst die Server für einen gewissen Zeitraum herunterfahren, um sicherzustellen, dass keine Probleme gemeldet werden, die möglicherweise einen Neustart dieser Server erfordern. Damit wird Dienstkontinuität gewährleistet, während Sie untersuchen, warum Clients nicht Azure Information Protection verwenden.

Nach der Außerbetriebsetzung Ihrer AD RMS-Server haben Sie die Gelegenheit, Ihre Vorlagen im klassischen Azure-Portal zu überprüfen und zu konsolidieren, sodass sich Benutzer unter weniger Vorlagen entscheiden müssen. Sie können die Vorlagen zu diesem Zeitpunkt auch neu konfigurieren oder sogar neue Vorlagen hinzufügen. Außerdem wäre dies ein guter Zeitpunkt, um die Standardvorlagen zu veröffentlichen. Weitere Informationen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md).

## <a name="step-9-re-key-your-azure-information-protection-tenant-key"></a>Schritt 9: Erneuern Ihres Azure Information Protection-Mandantenschlüssels
Dieser Schritt ist nur anwendbar, wenn Ihre ausgewählte Mandantenschlüsseltopologie von Microsoft anstatt von Kunden (BYOK mit Azure Key Vault) verwaltet wird.

Dieser Schritt ist optional, wird jedoch empfohlen, wenn Ihr Azure Information Protection-Mandantenschlüssel von Microsoft verwaltet wird und von AD RMS migriert wurde. In diesem Szenario schützt das Erneuern der Schlüssel Ihren Azure Information Protection-Mandantenschlüssel vor potenziellen Sicherheitslücken des AD RMS-Schlüssels.

Wenn Sie Ihren Azure Information Protection-Mandantenschlüssel erneuern (oder „neu vergeben“), wird ein neuer Schlüssel erstellt, und der ursprüngliche Schlüssel wird archiviert. Da der Wechsel von einem Schlüssel zu einem anderen jedoch nicht sofort erfolgt, sondern sich über einige Wochen zieht, sollten Sie nicht warten, bis Sie eine Verletzung Ihres ursprünglichen Schlüssels vermuten, sondern Ihren Azure Information Protection-Mandantenschlüssel ändern, sobald die Migration abgeschlossen ist.

Um Ihren von Microsoft verwalteten Azure Information Protection-Mandantenschlüssel neu zu erstellen, wenden Sie sich an den [Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support), und erstellen Sie eine **Azure Information Protection-Supportanfrage für die Neuerstellung Ihres Azure Information Protection-Schlüssels nach der Migration von AD RMS**. Sie müssen nachweisen, dass Sie der Administrator Ihres Azure Information Protection-Mandanten sind. Beachten Sie jedoch, dass die Bestätigung für diesen Prozess mehrere Tage dauert. Dabei fallen die Standardgebühren für Support an. Die Neuvergabe Ihres Mandantenschlüssels ist keine kostenfreie Supportleistung.


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Verwalten des Azure Information Protection-Mandantenschlüssels finden Sie unter [Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel](../deploy-use/operations-tenant-key.md).

Nachdem Sie die Migration nun abgeschlossen haben, können Sie sich die [Roadmap für die Bereitstellung](deployment-roadmap.md) ansehen, um die ggf. erforderlichen weiteren Bereitstellungsaufgaben zu ermitteln.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


