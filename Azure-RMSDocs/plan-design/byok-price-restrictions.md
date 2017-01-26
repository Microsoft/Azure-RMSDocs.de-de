---
title: "BYOK – Preise und Einschränkungen | Azure Information Protection"
description: "Lernen Sie die Einschränkungen bei Verwendung kundenverwalteter Schlüssel (bekannt als „Bring Your Own Key“, BYOK) mit Azure RMS kennen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/04/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 2e8a00d4c8d38387645d015d3f69a4d568fc9683


---

# <a name="byok-pricing-and-restrictions"></a>BYOK – Preise und Einschränkungen

>*Gilt für: Azure Information Protection, Office 365*


Organisationen mit einem Abonnement, das Azure Information Protection umfasst, können ihren Azure Information Protection-Mandanten so konfigurieren, dass ein vom Kunden verwalteter Schlüssel (Bring Your Own Key, BYOK) verwendet wird, dessen [Nutzung ohne Aufpreis protokolliert](../deploy-use/log-analyze-usage.md) werden kann. 

Der Schlüssel muss in Azure Key Vault gespeichert werden. Dies erfordert ein kostenpflichtiges bzw. Testabonnement von Azure. Außerdem müssen Sie zur Unterstützung von durch HSM geschützte Schlüssel den Diensttarif „Azure Key Vault Premium“ wählen. Bei Nutzung eines durch HSM geschützten Schlüssels in Azure Key Vault fällt eine monatliche Gebühr an. Weitere Informationen finden Sie auf der [Seite mit den Azure Key Vault-Preisen](https://azure.microsoft.com/en-us/pricing/details/key-vault/).

Wenn Sie Azure Key Vault für Ihren Azure Information Protection-Mandantenschlüssel einsetzen, empfiehlt es sich, einen dedizierten Schlüsseltresor für diesen Schlüssel mit einem dedizierten Abonnement zu verwenden, um sicherzustellen, dass er nur vom Azure Rights Management-Dienst verwendet wird. 

## <a name="benefits-of-using-azure-key-vault"></a>Vorteile der Verwendung von Azure Key Vault

Zusätzlich zur Verwendung der Azure Information Protection-Verwendungsprotokollierung können Sie für zusätzliche Sicherheit Querverweise zur [Azure Key Vault-Protokollierung](https://azure.microsoft.com/documentation/articles/key-vault-logging/) einrichten, um unabhängig zu überwachen, dass dieser Schlüssel nur vom Azure Rights Management-Dienst verwendet wird. Bei Bedarf können Sie den Zugriff auf den Schlüssel sofort widerrufen, indem Sie die Berechtigungen für den Schlüsseltresor entfernen.

Weitere Vorteile der Verwendung von Azure Key Vault für den Azure Information Protection-Mandantenschlüssel:

- Azure Key Vault ist eine zentralisierte Schlüsselverwaltungslösung, die eine konsistente Verwaltungslösung für viele cloudbasierte und sogar lokale Dienste bietet, die Verschlüsselung verwenden.

- Azure Key Vault unterstützt eine Reihe von integrierten Schnittstellen für die Schlüsselverwaltung, einschließlich PowerShell, CLI, REST-APIs und das Azure-Portal. Andere Dienste und Tools wurden in den Schlüsseltresor integriert, um Funktionen bereitzustellen, die für bestimmte Aufgaben, z. B. Überwachung, optimiert wurden. So können Sie beispielsweise die Schlüsselverwendungsprotokolle über Log Analytics aus der Operations Management Suite analysieren, festlegen, dass bei Erfüllung bestimmter Kriterien Benachrichtigungen gesendet werden, und so weiter.

- Azure Key Vault bietet Rollentrennung als anerkannte und bewährte Sicherheitsmethode. Azure Information Protection-Administratoren können sich auf die Verwaltung von Datenklassifizierung und -Datenschutz konzentrieren, und Azure Key Vault-Administratoren können sich auf die Verwaltung von Verschlüsselungsschlüsseln und speziellen Richtlinien konzentrieren, die möglicherweise aus Sicherheits- oder Compliancegründen erforderlich sind.

- In einigen Organisationen gibt es Einschränkungen für die Verwahrung ihres Hauptschlüssels. Azure Key Vault bietet ein hohes Maß an Kontrolle über den Speicherort des Hauptschlüssels, da der Dienst in viele Azure-Regionen verfügbar ist. Derzeit können Sie unter 28 Azure-Regionen wählen, und Sie dürfen davon ausgehen, dass diese Anzahl noch steigen wird. Weitere Informationen finden Sie auf der Seite „Produkte nach Region“ (https://azure.microsoft.com/regions/services/) auf der Azure-Website.

Zusätzlich zum Verwalten von Schlüsseln bietet Azure Key Vault Ihren Sicherheitsadministratoren die gleiche Verwaltungsumgebung zum Speichern von, Zugreifen auf und Verwalten von Zertifikaten und geheimen Schlüsseln (z. B. Kennwörtern) für andere Dienste und Anwendungen, die Verschlüsselung verwenden. 

Weitere Informationen zu Azure Key Vault finden Sie unter [Was ist Azure Key Vault?](https://azure.microsoft.com/documentation/articles/key-vault-whatis/). Im [Azure Key Vault-Teamblog](https://blogs.technet.microsoft.com/kv/) finden Sie aktuelle Informationen und erfahren, wie andere Dienste diese Technologie verwenden.


## <a name="restrictions-when-using-byok"></a>Einschränkungen bei Verwendung von BYOK

Wenn Benutzer sich über RMS for Individuals für ein kostenloses Konto registriert haben, können Sie BYOK oder die Verwendungsprotokollierung nicht nutzen, da in dieser Konfiguration kein Mandantenadministrator zum Konfigurieren dieser Features vorhanden ist.


> [!NOTE]
> Weitere Informationen zu RMS for Individuals finden Sie unter [RMS for Individuals und Azure Rights Management](../understand-explore/rms-for-individuals.md).

![BYOK unterstützt Exchange Online nicht.](../media/RMS_BYOK_noExchange.png)

BYOK und die Nutzungsprotokollierung arbeiten nahtlos mit jeder Anwendung zusammen, die den Azure Rights Management-Dienst (Azure RMS) von Azure Information Protection integriert. Dazu gehören Clouddienste wie SharePoint Online, lokale Server mit Exchange und SharePoint, für die Azure RMS unter Verwendung des RMS-Connectors eingesetzt wird, sowie Clientanwendungen wie Office 2016 und Office 2013. Sie erhalten Protokolle der Schlüsselnutzung unabhängig davon, welche Anwendung Anforderungen an Azure RMS stellt.

Es gibt eine Ausnahme: Derzeit ist **Azure RMS BYOK nicht mit Exchange Online kompatibel**. Wenn Sie Exchange Online verwenden möchten, empfehlen wir, dass Sie Azure RMS jetzt im Standard-Schlüsselverwaltungsmodus bereitstellen, in dem Microsoft Ihren Schlüssel generiert und verwaltet. Sie können später zu BYOK wechseln, beispielsweise wenn Exchange Online Azure RMS BYOK unterstützt. Wenn Sie jedoch nicht warten können, haben Sie jetzt die Möglichkeit, Azure RMS mit BYOK mit eingeschränkter RMS-Funktionalität für Exchange Online bereitzustellen (ungeschützte E-Mails und Anlagen bleiben dabei voll funktionsfähig):

-   Geschützte E-Mails oder Anlagen in Outlook Web Access können nicht angezeigt werden.

-   Geschützte E-Mails auf mobilen Geräten, die Exchange ActiveSync IRM verwenden, können nicht angezeigt werden.

-   Die Transport- (z. B. zum Scannen nach Schadsoftware) und Journalentschlüsselung sind nicht möglich, sodass geschützte E-Mails und Anlagen übersprungen werden.

-   Transportschutzregeln und die Verhinderung von Datenverlust (Data Loss Prevention, DLP), die IRM-Richtlinien erzwingen, sind nicht möglich, sodass der RMS-Schutz mit diesen Methoden nicht angewendet werden kann.

-   Serverbasierte Suche für geschützte E-Mails, sodass geschützte E-Mails übersprungen werden.

Bei der Verwendung von Azure RMS BYOK mit eingeschränkter RMS-Funktionalität für Exchange Online funktioniert RMS mit E-Mail-Clients in Outlook auf Windows- und Mac-Computern und mit anderen E-Mail-Clients, die Exchange ActiveSync IRM nicht verwenden.

Wenn Sie von AD RMS zu Azure RMS migrieren, haben Sie möglicherweise Ihren Schlüssel als vertrauenswürdige Veröffentlichungsdomäne (TPD) in Exchange Online importiert (in der Exchange-Terminologie auch als BYOK bezeichnet, was sich von Azure Key Vault BYOK unterscheidet). In diesem Szenario müssen Sie die vertrauenswürdige Veröffentlichungsdomäne aus Exchange Online entfernen, um in Konflikt stehende Vorlagen und Richtlinien zu vermeiden. Weitere Informationen finden Sie unter [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) in der Cmdlets-Bibliothek für Exchange Online.

In einigen Fällen stellt die Azure RMS BYOK-Ausnahme in der Praxis kein Problem für Exchange Online dar. Beispielsweise führen Organisationen, die BYOK und Protokollierung benötigen, ihre Datenanwendungen (Exchange, SharePoint, Office) lokal aus und verwenden Azure RMS für Funktionen, die bei lokalem AD RMS nicht einfach verfügbar sind (z. B. Zusammenarbeit mit anderen Unternehmen und Zugriff von mobilen Clients aus). Sowohl BYOK als auch die Protokollierung funktionieren gut in diesem Szenario und gestatten der Organisation die Übernahme der vollständigen Kontrolle über ihr Azure RMS-Abonnement.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie sich für die Verwaltung Ihres eigenen Schlüssels entschieden haben, helfen Ihnen die Informationen unter [Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md#implementing-your-azure-information-protection-tenant-key) weiter.

Wenn Sie sich für die Standardkonfiguration entschieden haben, bei der Ihr Mandantenschlüssel von Microsoft verwaltet wird, helfen Ihnen die Informationen im Abschnitt [Nächste Schritte](plan-implement-tenant-key.md#next-steps) des Artikels „Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels“ weiter.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


