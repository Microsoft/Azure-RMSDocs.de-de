---
title: "Migration von AD RMS zu Azure Rights Management – Phase 4 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: 21fac7d684f2d544ab97f5ca6eb7faaaca3e9d26


---

# Migrationsphase 4: Aufgaben nach der Migration

*Gilt für: Active Directory Rights Management Services, Azure Rights Management*


Verwenden Sie die folgenden Informationen für Phase 4 der Migration von AD RMS zu Azure Rights Management (Azure RMS). Diese Verfahren beziehen sich auf die Schritte 8 bis 9 der [Migration von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md).


## Schritt 8: Außerbetriebsetzung von AD RMS

Optional: Entfernen Sie den Dienstverbindungspunkt (Service Connection Point, SCP) aus Active Directory, um zu verhindern, dass Computer Ihre lokale Rights Management-Infrastruktur ermitteln. Dies ist aufgrund der Umleitung, die Sie in der Registrierung konfiguriert haben (z. B. durch Ausführen des Migrationsskripts), optional. Um den Service Connection Point zu entfernen, verwenden Sie das AD-SCP-Register-Tool aus dem [Rights Management Services-Verwaltungstoolkit](http://www.microsoft.com/download/details.aspx?id=1479).

Überwachen Sie die Aktivität Ihrer AD RMS-Server, z.B. durch Überprüfen der [Anforderungen im Systemintegritätsbericht](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx) und der [ServiceRequest-Tabelle](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) oder durch [Überwachung des Benutzerzugriffs auf geschützte Inhalte](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Wenn Sie bestätigt haben, dass RMS-Clients nicht mehr mit diesen Servern kommunizieren und Clients erfolgreich Azure RMS verwenden, können Sie die AD RMS-Serverrolle von diesen Servern entfernen. Wenn Sie dedizierte Server verwenden, können Sie auch als Vorsichtsmaßnahme zuerst die Server für einen gewissen Zeitraum herunterfahren, um zu gewährleisten, dass keine Probleme gemeldet werden, die möglicherweise einen Neustart dieser Server erfordern. Damit wird Dienstkontinuität sichergestellt, während Sie untersuchen, warum Clients Azure RMS nicht verwenden.

Nach der Außerbetriebsetzung Ihrer AD RMS-Server haben Sie die Gelegenheit, Ihre Vorlagen im klassischen Azure-Portal zu überprüfen und zu konsolidieren, sodass sich Benutzer unter weniger Vorlagen entscheiden müssen. Sie können die Vorlagen zu diesem Zeitpunkt auch neu konfigurieren oder sogar neue Vorlagen hinzufügen. Außerdem wäre dies ein guter Zeitpunkt, um die Standardvorlagen zu veröffentlichen. Weitere Informationen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](../deploy-use/configure-custom-templates.md).

## Schritt 9: Ändern des Azure RMS-Mandantenschlüssels
Dieser Schritt ist nur anwendbar, wenn Ihre ausgewählte Mandantenschlüsseltopologie von Microsoft anstatt von Kunden (BYOK mit Azure Key Vault) verwaltet wird.

Dieser Schritt ist optional, wird jedoch empfohlen, wenn Ihr Azure RMS-Mandantenschlüssel von Microsoft verwaltet wird und von AD RMS migriert wurde. In diesem Szenario schützt das Erstellen neuer Schlüssel Ihren Azure RMS-Mandantenschlüssel vor potenziellen Sicherheitslücken des AD RMS-Schlüssels.

Wenn Sie Ihren Azure RMS-Mandantenschlüssel ändern (oder "neu vergeben"), wird ein neuer Schlüssel erstellt und der ursprüngliche Schlüssel archiviert. Da der Wechsel von einem Schlüssel zu einem anderen jedoch nicht sofort erfolgt, sondern sich über einige Wochen zieht, sollten Sie nicht warten, bis Sie eine Verletzung Ihres ursprünglichen Schlüssels vermuten, sondern Ihren Azure RMS-Mandantenschlüssel ändern, sobald die Migration abgeschlossen ist.

Um Ihren von Microsoft verwalteten Azure RMS-Mandantenschlüssel neu zu erstellen: Wenden Sie sich an den [Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support) und erstellen Sie eine **Azure Rights Management-Supportanfrage, um die Neuerstellung Ihres Azure RMS-Schlüssels nach der Migration von AD RMS anzufordern**. Sie müssen nachweisen, dass Sie der Administrator Ihres Azure RMS-Mandanten sind; beachten Sie, dass die Bestätigung für diesen Prozess mehrere Tage dauert. Dabei fallen die Standardgebühren für Support an; das Ändern Ihres Mandantenschlüssels ist keine kostenfreie Supportleistung.


## Nächste Schritte

Weitere Informationen zum Verwalten des RMS-Mandantenschlüssels finden Sie unter [Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel](../deploy-use/operations-tenant-key.md).

Nachdem Sie die Migration nun abgeschlossen haben, können Sie sich die [Roadmap für die Bereitstellung](deployment-roadmap.md) ansehen, um die ggf. erforderlichen weiteren Bereitstellungsaufgaben zu ermitteln.




<!--HONumber=Aug16_HO3-->


