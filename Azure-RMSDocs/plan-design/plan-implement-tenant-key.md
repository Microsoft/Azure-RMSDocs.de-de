---
title: "Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/30/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f01d57759ab80b4946c07a627269550c80114131
ms.openlocfilehash: aa482dace1086222f63e9165e3089051b5de3e8c


---

# Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels

*Gilt für: Azure Rights Management, Office 365*

Verwenden Sie die Informationen in diesem Artikel, um Ihren Rights Management (RMS)-Mandantenschlüssel für Azure RMS zu planen und zu verwalten. Angenommen, Sie möchten die Standardeinstellung ändern, dass Microsoft Ihren Mandantenschlüssel verwaltet, und Ihren eigenen Mandantenschlüssel verwalten, um bestimmte Vorschriften in Ihrer Organisation einzuhalten.  Das Verwalten Ihres eigenen Mandantenschlüssels wird auch als "Bring Your Own Key" (kurz BYOK) bezeichnet.

> [!NOTE]
> Der RMS-Mandantenschlüssel ist auch als SLC-Schlüssel (Server Licensor Certificate, lizenzgebendes Serverzertifikat) bekannt. Azure RMS pflegt für jede Organisation, die Azure RMS abonniert, mindestens einen Schlüssel. Immer, wenn ein Schlüssel für RMS in einer Organisation verwendet wird (z. B. Benutzerschlüssel, Computerschlüssel, Dokumentationsverschlüsselungsschlüssel), wird dieser kryptografisch mit Ihrem RMS-Mandantenschlüssel verkettet.

**Kurz zusammengefasst:** Verwenden Sie die folgende Tabelle als eine kurze Einführung in die empfohlene Mandantenschlüsseltopologie. Weitere Informationen finden Sie in der Zusatzdokumentation.

Wenn Sie Azure RMS mit einem Mandantenschlüssel bereitstellen, der von Microsoft verwaltet wird, können Sie später zu BYOK wechseln. Sie können allerdings derzeit noch nicht Ihren Azure RMS-Mandantenschlüssel von BYOK in die Verwaltung durch Microsoft ändern.

|Geschäftliche Anforderung|Empfohlene Mandantenschlüsseltopologie|
|------------------------|-----------------------------------|
|Schnelles Bereitstellen von Azure RMS ohne spezielle Hardware|Von Microsoft verwaltet|
|Volle IRM-Funktionalität in Exchange Online mit Azure RMS|Von Microsoft verwaltet|
|Schlüssel werden von Ihnen erstellt und in einem Hardwaresicherheitsmodul (HSM) geschützt|BYOK<br /><br />Derzeit führt diese Konfiguration zu eingeschränkter IRM-Funktionalität in Exchange Online. Weitere Informationen finden Sie unter [BYOK – Preise und Einschränkungen](byok-price-restrictions.md).|

## Wählen Sie Ihre Mandantenschlüsseltopologie aus: Verwaltet von Microsoft (Standard) oder verwaltet von Ihnen (BYOK)
Entscheiden Sie, welche Mandantenschlüsseltopologie für Ihre Organisation am besten geeignet ist. Standardmäßig generiert Azure RMS Ihren Mandantenschlüssel und verwaltet die meisten Aspekte des Lebenszyklus des Mandantenschlüssels. Dies ist die einfachste Möglichkeit mit dem geringsten Verwaltungsaufwand. In den meisten Fällen müssen Sie noch nicht einmal wissen, dass Sie einen Mandantenschlüssel besitzen. Sie registrieren sich einfach für Azure RMS, und der restliche Schlüsselverwaltungsprozess wird von Microsoft erledigt.

Alternativ können Sie, falls gewünscht, die vollständige Kontrolle über Ihren Mandantenschlüssel übernehmen, was das Erstellen Ihres Mandantenschlüssels und die Aufbewahrung der Masterkopie bei Ihnen vor Ort umfasst. Dieses Szenario wird häufig als „Bring Your Own Key“ (BYOK) bezeichnet. Bei dieser Option geschieht Folgendes:

1.  Sie generieren Ihren Mandantenschlüssel lokal, entsprechend Ihrer IT-Richtlinien.

2.  Sie übertragen den Mandantenschlüssel sicher von einem Hardwaresicherheitsmodul (HSM), das sich in Ihrem Besitz befindet, auf HSMs, die Microsoft gehören und von Microsoft verwaltet werden. Während dieses Prozesses verlässt Ihr Mandantenschlüssel nie die Hardwareschutzgrenzen.

3.  Wenn Sie Ihren Mandantenschlüssel an Microsoft übertragen, bleibt er durch Thales HSMs geschützt. Microsoft arbeitet mit Thales zusammen, um sicherzustellen, dass Ihr Mandantenschlüssel nicht aus den HSMs von Microsoft extrahiert werden kann.

Obgleich dies optional ist, möchten Sie wahrscheinlich auch die beinahe in Echtzeit erstellten Nutzungsprotokolle von Azure RMS verwenden, um genau verfolgen zu können, wie und wann Ihr Mandantenschlüssel verwendet wird.

> [!NOTE]
> Als zusätzliche Schutzmaßnahme verwendet Azure RMS getrennte Security Worlds für seine Rechenzentren in Nordamerika, EMEA (Europa, Naher Osten und Afrika) und Asien. Wenn Sie Ihren eigenen Mandantenschlüssel verwalten, ist dieser an die Security World der Region gebunden, in der Ihr RMS-Mandant registriert ist. Ein Mandantenschlüssel eines europäischen Kunden kann beispielsweise nicht in Rechenzentren in Nordamerika oder Asien verwendet werden.

## Der Lebenszyklus des Mandantenschlüssels
Wenn Sie sich entschließen, dass Microsoft Ihren Mandantenschlüssel verwalten soll, wickelt Microsoft die meisten aller Vorgänge des Schlüssellebenszyklus ab. Wenn Sie sich jedoch entschließen, Ihren Mandantenschlüssel selbst zu verwalten, sind Sie für zahlreiche der Vorgänge des Schlüssellebenszyklus sowie einige zusätzliche Verfahren verantwortlich.

Die folgenden Diagramme zeigen und vergleichen diese zwei Optionen. Das erste Diagramm zeigt, wie niedrig der Verwaltungsaufwand in der Standardkonfiguration ist, wenn Microsoft den Mandantenschlüssel verwaltet.

![Lebenszyklus des Azure RMS-Mandantenschlüssels – verwaltet von Microsoft, Standardeinstellung](../media/RMS_BYOK_cloud.png)

Das zweite Diagramm zeigt die zusätzlichen Schritte, die erforderlich sind, wenn Sie Ihren eigenen Mandantenschlüssel verwalten.

![Lebenszyklus des Azure RMS-Mandantenschlüssels – verwaltet von Ihnen, BYOK](../media/RMS_BYOK_onprem.png)

Wenn Sie sich entschließen, Ihren Mandantenschlüssel von Microsoft verwalten zu lassen, müssen Sie nichts weiter unternehmen, damit der Schlüssel generiert wird. Sie können direkt unter [Nächste Schritte](plan-implement-tenant-key.md#next-steps) fortfahren.

Wenn Sie sich entschließen, Ihren Mandantenschlüssel selbst zu verwalten, finden Sie in den folgenden Abschnitten weitere Informationen hierzu, die Sie lesen sollten.

## Implementieren Ihres Azure Rights Management-Mandantenschlüssels

Verwenden Sie die Informationen und Verfahren in diesem Abschnitt, wenn Sie sich entschieden haben, Ihren Mandantenschlüssel selber zu generieren und zu verwalten – das BYOK-Szenario (Bring Your Own Key):


> [!IMPORTANT]
> Wenn Sie bereits begonnen haben, [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu verwenden (der Dienst ist aktiviert), und Benutzer haben, die Office 2010 ausführen, [wenden Sie sich an den Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support), bevor Sie diese Prozeduren ausführen. Abhängig von Ihrem Szenario und den Voraussetzungen können Sie immer noch BYOK verwenden, allerdings mit einigen Einschränkungen bzw. zusätzlichen Schritten.
> 
> Wenden Sie sich auch an den [Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support), wenn Ihre Organisation über bestimmte Richtlinien für den Umgang mit Schlüsseln verfügt.

### Voraussetzungen für BYOK
In der folgenden Tabelle finden Sie eine Liste der Voraussetzungen für „Bring Your Own Key“ (BYOK).

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Ein Abonnement, das Azure RMS unterstützt.|Weitere Informationen zu den verfügbaren Abonnements finden Sie unter [Cloud-Abonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md).|
|Sie verwenden nicht RMS for Individuals oder Exchange Online. Oder, falls Sie doch Exchange Online verwenden, verstehen und akzeptieren Sie die Einschränkungen, die bei der Verwendung von BYOK mit dieser Konfiguration einhergehen.|Weitere Informationen zu diesen und anderen Einschränkungen für BYOK finden Sie unter [BYOK – Preise und Einschränkungen](byok-price-restrictions.md) .<br /><br />**Wichtig**: Derzeit ist BYOK nicht mit Exchange Online kompatibel.|
|Thales HSM, Smartcards und unterstützende Software.<br /><br />**Hinweis**: Wenn Sie von AD RMS zu Azure RMS mit der Softwareschlüssel-zu-Hardwareschlüssel-Migration migrieren, müssen die Thales-Treiber mindestens in der Version 11.62 vorliegen.|Sie benötigen Zugriff auf ein Thales Hardwaresicherheitsmodul sowie grundlegende Kenntnisse zum Betrieb von Thales HSMs. Eine Liste der kompatiblen Modelle bzw. Informationen zum Kauf eines HSM, wenn Sie noch keins besitzen, finden Sie unter [Thales Hardwaresicherheitsmodul](http://www.thales-esecurity.com/msrms/buy) .|
|Wenn Sie Ihren Mandantenschlüssel über das Internet übertragen statt physisch in Redmond (USA) abgeben möchten: Es bestehen drei Anforderungen:<br /><br />1: Eine offline arbeitende x64-Arbeitsstation mit einem Windows-Betriebssystem der Mindestversion Windows 7 und Thales nShield-Software der Mindestversion 11.62.<br /><br />Wenn diese Arbeitsstation Windows 7 ausführt, müssen Sie [Microsoft .NET Framework 4.5 installieren](http://go.microsoft.com/fwlink/?LinkId=225702).<br /><br />2: Eine Arbeitsstation, die mit dem Internet verbunden ist und über ein Windows-Betriebssystem der Mindestversion Windows 7 verfügt.<br /><br />3: Ein USB-Laufwerk oder anderes mobiles Speichergerät mit mindestens 16 MB freiem Speicherplatz.|Diese Voraussetzungen sind nicht erforderlich, wenn Sie nach Redmond reisen und Ihren Mandantenschlüssel persönlich überbringen.<br /><br />Aus Sicherheitsgründen empfehlen wir, dass die erste Arbeitsstation nicht mit einem Netzwerk verbunden ist. Dies ist jedoch nicht programmtechnisch erforderlich.<br /><br />Hinweis: In den folgenden Anleitungen wird diese erste Arbeitsstation als **nicht verbundene Arbeitsstation** bezeichnet.<br /><br />Wenn Ihr Mandantenschlüssel für ein Produktionsnetzwerk bestimmt ist, empfehlen wir zusätzlich, dass Sie eine zweite getrennte Arbeitsstation verwenden, um das Toolset herunterzuladen und den Mandantenschlüssel hochzuladen. Zu Testzwecken können Sie aber dieselbe Arbeitsstation wie die erste verwenden.<br /><br />Hinweis: In den folgenden Anleitungen wird diese zweite Arbeitsstation als **Arbeitsstation mit Internetverbindung** bezeichnet.|

Die Verfahren zum Generieren und Verwenden Ihres eigenen Mandantenschlüssels hängen davon ab, ob Sie dies über das Internet oder persönlich vornehmen möchten:

-   **Über das Internet:** Dies erfordert einige zusätzliche Konfigurationsschritte wie das Herunterladen und Verwenden eines Toolsets und von Windows PowerShell-Cmdlets. Sie müssen sich jedoch nicht physisch in einer Einrichtung von Microsoft aufhalten, um Ihren Mandantenschlüssel zu übertragen. Die Sicherheit wird mithilfe der folgenden Methoden aufrechterhalten:

    -   Sie generieren den Mandantenschlüssel auf einer Offlinearbeitsstation, was die Angriffsfläche verringert.

    -   Der Mandantenschlüssel wird mit einem Schlüsselaustauschschlüssel (Key Exchange Key, KEK) verschlüsselt und bleibt verschlüsselt, bis er auf die Azure RMS-HSMs übertragen wurde. Nur die verschlüsselte Version Ihres Mandantenschlüssels verlässt die ursprüngliche Arbeitsstation.

    -   Ein Toolset legt Eigenschaften Ihres Mandantenschlüssels fest, die den Mandantenschlüssel an die Azure RMS Security World binden. Somit können ausschließlich die Azure RMS-HSMs, nachdem sie Ihren Mandantenschlüssel empfangen und entschlüsselt haben, diesen verwenden. Ihr Mandantenschlüssel kann nicht exportiert werden. Diese Bindung wird von den Thales HSMs erzwungen.

    -   Der Schlüsselaustauschschlüssel, mit dem Ihr Mandantenschlüssel verschlüsselt wird, wird in den Azure RMS-HSMs generiert und kann nicht exportiert werden. Die HSMs erzwingen, dass keine unverschlüsselte Version des Schlüsselaustauschschlüssels außerhalb der HSMs vorhanden sein kann. Zusätzlich enthält das Toolset eine Beglaubigung von Thales, dass der Schlüsselaustauschschlüssel nicht exportiert werden kann und in einem von Thales hergestellten Original-HSM generiert wurde.

    -   Das Toolset enthält eine Beglaubigung von Thales, dass die Azure RMS Security World ebenfalls auf einem von Thales hergestellten Original-HSM generiert wurde. Dies weist Ihnen gegenüber nach, dass Microsoft Originalhardware verwendet.

    -   Microsoft verwendet in jeder geografisch getrennten Region getrennte Schlüsselaustauschschlüssel sowie getrennte Security Worlds, was sicherstellt, dass Ihr Mandantenschlüssel nur in Rechenzentren in der Region verwendet werden kann, in der Sie ihn verschlüsselt haben. Beispielsweise kann ein Mandantenschlüssel eines europäischen Kunden nicht in Rechenzentren in Nordamerika oder Asien verwendet werden.

    > [!NOTE]
    > Ihr Mandantenschlüssel kann nicht vertrauenswürdige Computer und Netzwerke sicher passieren, weil er verschlüsselt und mit Berechtigungen auf Zugriffssteuerungsebene gesichert ist, wodurch er nur in Ihren HSMs und in den HSMs für Azure RMS von Microsoft verwendet werden kann. Sie können die im Toolset bereitgestellten Skripts verwenden, um die Sicherheitsmaßnahmen zu überprüfen, und Sie können weitere Informationen von Thales zur Funktionsweise lesen: [Hardwareschlüsselverwaltung in der RMS-Cloud](https://www.thales-esecurity.com/knowledge-base/white-papers/hardware-key-management-in-the-rms-cloud).

-   **Persönlich:** Dies erfordert, dass Sie sich an den [Microsoft Support wenden](../get-started/information-support.md#to-contact-microsoft-support), um einen Termin für die Übergabe eines Azure RMS-Mandantenschlüssels zu vereinbaren. Sie müssen zu einer Microsoft-Niederlassung in Redmond, Washington, USA, reisen, um Ihren Mandantenschlüssel in die Azure RMS Security World zu übertragen.

Wählen Sie für Anweisungen zur Vorgehensweise, ob Sie den generierten Mandantenschlüssel über das Internet übertragen oder persönlich übergeben: 

- [Über das Internet](generate-tenant-key-internet.md)
- [Persönlich](generate-tenant-key-in-person.md)


## Nächste Schritte

Nachdem Sie Ihren Mandantenschlüssel geplant und gegebenenfalls generiert haben, führen Sie folgende Schritte aus:

1.  Beginnen Sie mit der Verwendung Ihres Mandantenschlüssels:

    -   Wenn noch nicht geschehen, müssen Sie jetzt Rights Management aktivieren, damit Ihre Organisation mit der Verwendung von RMS beginnen kann. Benutzer beginnen sofort mit der Verwendung Ihres Mandantenschlüssels (verwaltet von Microsoft oder von Ihnen).

        Weitere Informationen zur Aktivierung finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

    -   Wenn Sie Rights Management bereits aktiviert hatten und sich dann zur Verwaltung des eigenen Mandantenschlüssels entschlossen haben, erfolgt ein gestaffelter Übergang der Benutzer vom alten zum neuen Mandantenschlüssel, wobei dieser gestaffelte Übergang ein paar Wochen bis zum vollständigen Abschluss in Anspruch nehmen kann. Auf Dokumente und Dateien, die mit dem alten Mandantenschlüssel geschützt wurden, können autorisierte Benutzer weiterhin zugreifen.

2.  Erwägen Sie die Aktivierung der Nutzungsprotokollierung, durch die jede von RMS durchgeführte Transaktion protokolliert wird.

    Wenn Sie sich zur Verwaltung des eigenen Mandantenschlüssels entschlossen haben, enthält die Protokollierung Informationen über die Nutzung Ihres Mandantenschlüssels. Dies wird im folgenden Ausschnitt einer in Excel angezeigten Protokolldatei dargestellt, in der die Anforderungstypen **KMSPDecrypt** und **KMSPSignDigest** anzeigen, dass der Mandantenschlüssel verwendet wird.

    ![Protokolldatei in Excel, in der der Mandantenschlüssel verwendet wird.](../media/RMS_Logging.png)

    Weitere Informationen zur Nutzungsprotokollierung finden Sie unter [Protokollieren und Analysieren der Nutzung von Azure Rights Management](../deploy-use/log-analyze-usage.md).

3.  Pflegen Sie Ihren Mandantenschlüssel.

    Weitere Informationen finden Sie unter [Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel](../deploy-use/operations-tenant-key.md).




<!--HONumber=Jul16_HO3-->


