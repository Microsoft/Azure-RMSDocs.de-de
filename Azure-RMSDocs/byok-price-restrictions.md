---
title: BYOK – Preise und Einschränkungen – Azure Information Protection
description: Lernen Sie die Einschränkungen bei Verwendung kundenverwalteter Schlüssel (bekannt als „Bring Your Own Key“, BYOK) mit Azure Information Protection kennen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/18/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: c27e94caa2a03c31d99b4fbfd702d5e205b86971
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491073"
---
# <a name="byok-pricing-and-restrictions"></a>BYOK – Preise und Einschränkungen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Organisationen mit einem Abonnement, das Azure Information Protection umfasst, können ihren Azure Information Protection-Mandanten so konfigurieren, dass ein vom Kunden verwalteter Schlüssel (Bring Your Own Key, BYOK) verwendet und dessen [Nutzung protokolliert wird](./log-analyze-usage.md). 

Der Schlüssel muss in Azure Key Vault gespeichert werden. Hierfür ist ein Azure-Abonnement erforderlich. Sie müssen den Premiumtarif von Azure Key Vault verwenden, um einen HSM-geschützten Schlüssel nutzen zu können. Für die Verwendung eines Schlüssels in Azure Key Vault fällt eine monatliche Gebühr an. Weitere Informationen finden Sie auf der [Seite mit den Azure Key Vault-Preisen](https://azure.microsoft.com/pricing/details/key-vault/).

Wenn Sie Azure Key Vault für Ihren Azure Information Protection-Mandantenschlüssel einsetzen, empfiehlt es sich, einen dedizierten Schlüsseltresor für diesen Schlüssel zu verwenden, um sicherzustellen, dass er nur vom Azure Rights Management-Dienst verwendet wird. Diese Konfiguration gewährleistet, dass Aufrufe anderer Dienste nicht zu einer Überschreitung der Key Vault-[Dienstgrenzwerte](/azure/key-vault/key-vault-service-limits) führen, wodurch die Antwortzeiten des Azure Rights Management-Diensts gedrosselt werden könnten.  

Da jeder Dienst, der Azure Key Vault verwendet, in der Regel andere Anforderungen an die Schlüsselverwaltung aufweist, empfiehlt es sich darüber hinaus, ein separates Azure-Abonnement für diesen Schlüsseltresor zu verwenden, um fehlerhafte Konfigurationen zu verhindern. 

Wenn Sie jedoch ein Azure-Abonnement auch für andere Dienste verwenden möchten, die Azure Key Vault nutzen, stellen Sie sicher, dass eine gemeinsame Gruppe von Administratoren für das Abonnement zuständig ist. Mit dieser Vorsichtsmaßnahme können Sie dafür sorgen, dass Administratoren, die dieses Abonnement verwenden, alle Schlüssel genau kennen, auf die sie Zugriff haben, sodass die Wahrscheinlichkeit fehlerhaften Konfigurationen sinkt. Ein gemeinsames Azure-Abonnement bietet sich z.B. dann an, wenn es sich bei den Administratoren für Ihren Azure Information Protection-Mandantenschlüssel um die gleichen Personen handelt, die Office 365-Kundenschlüssel und Schlüssel für CRM Online verwalten. Wenn es sich bei den Administratoren für die Kundenschlüssel oder CRM Online-Schlüssel jedoch nicht um die gleichen Personen handelt, die Ihren Azure Information Protection-Mandantenschlüssel verwalten, empfiehlt sich die gemeinsame Nutzung des Azure-Abonnements für Azure Information Protection nicht.

## <a name="benefits-of-using-azure-key-vault"></a>Vorteile der Verwendung von Azure Key Vault

Zusätzlich zur Verwendung der Azure Information Protection-Verwendungsprotokollierung können Sie für zusätzliche Sicherheit Querverweise zur [Azure Key Vault-Protokollierung](https://azure.microsoft.com/documentation/articles/key-vault-logging/) einrichten, um unabhängig zu überwachen, dass dieser Schlüssel nur vom Azure Rights Management-Dienst verwendet wird. Bei Bedarf können Sie den Zugriff auf den Schlüssel sofort widerrufen, indem Sie die Berechtigungen für den Schlüsseltresor entfernen.

Weitere Vorteile der Verwendung von Azure Key Vault für den Azure Information Protection-Mandantenschlüssel:

- Azure Key Vault ist eine zentralisierte Schlüsselverwaltungslösung, die eine konsistente Verwaltungslösung für viele cloudbasierte und sogar lokale Dienste bietet, die Verschlüsselung verwenden.

- Azure Key Vault unterstützt eine Reihe von integrierten Schnittstellen für die Schlüsselverwaltung, einschließlich PowerShell, CLI, REST-APIs und das Azure-Portal. Andere Dienste und Tools wurden in den Schlüsseltresor integriert, um Funktionen bereitzustellen, die für bestimmte Aufgaben, z. B. Überwachung, optimiert wurden. So können Sie beispielsweise die Schlüsselverwendungsprotokolle über Log Analytics aus der Operations Management Suite analysieren, festlegen, dass bei Erfüllung bestimmter Kriterien Benachrichtigungen gesendet werden, und so weiter.

- Azure Key Vault bietet Rollentrennung als anerkannte und bewährte Sicherheitsmethode. Azure Information Protection-Administratoren können sich auf die Verwaltung von Datenklassifizierung und -Datenschutz konzentrieren, und Azure Key Vault-Administratoren können sich auf die Verwaltung von Verschlüsselungsschlüsseln und speziellen Richtlinien konzentrieren, die möglicherweise aus Sicherheits- oder Compliancegründen erforderlich sind.

- In einigen Organisationen gibt es Einschränkungen für die Verwahrung ihres Hauptschlüssels. Azure Key Vault bietet ein hohes Maß an Kontrolle über den Speicherort des Hauptschlüssels, da der Dienst in viele Azure-Regionen verfügbar ist. Derzeit können Sie aus 28 Azure-Regionen wählen, und diese Zahl wird aller Wahrscheinlichkeit nach noch steigen. Weitere Informationen finden Sie auf der Seite [Verfügbare Produkte nach Region] (https://azure.microsoft.com/regions/services/) auf der Azure-Website.

Zusätzlich zum Verwalten von Schlüsseln bietet Azure Key Vault Ihren Sicherheitsadministratoren die gleiche Verwaltungsumgebung zum Speichern von, Zugreifen auf und Verwalten von Zertifikaten und geheimen Schlüsseln (z. B. Kennwörtern) für andere Dienste und Anwendungen, die Verschlüsselung verwenden. 

Weitere Informationen zu Azure Key Vault finden Sie unter [Was ist Azure Key Vault?](/azure/key-vault/key-vault-whatis). Im [Azure Key Vault-Teamblog](https://cloudblogs.microsoft.com/kv/) finden Sie aktuelle Informationen und erfahren, wie andere Dienste diese Technologie verwenden.

## <a name="restrictions-when-using-byok"></a>Einschränkungen bei Verwendung von BYOK

BYOK und die Nutzungsprotokollierung arbeiten nahtlos mit jeder Anwendung zusammen, die den Azure Rights Management-Dienst von Azure Information Protection integriert. Dazu gehören Clouddienste wie SharePoint Online, lokale Server mit Exchange und SharePoint, für die der Azure Rights Management-Dienst unter Verwendung des RMS-Connectors eingesetzt wird, sowie Clientanwendungen wie Office 2016 und Office 2013. Sie erhalten Protokolle der Schlüsselnutzung unabhängig davon, welche Anwendung Anforderungen an den Azure Rights Management-Dienst sendet.

Wenn Sie bereits Exchange Online IRM aktiviert haben, indem Sie Ihre vertrauenswürdige Veröffentlichungsdomäne (TPD) aus Azure RMS importiert haben, führen Sie die Anweisungen unter [Set up new Office 365 Message Encryption capabilities built on top of Azure Information Protection (Einrichten von neuen, auf Azure Information Protection basierenden Funktionen in der Office 365-Nachrichtenverschlüsselung)](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) aus, um die neuen Funktionen in Exchange Online zu aktivieren, die die Verwendung von BYOK für Azure Information Protection unterstützen.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie sich für die Verwaltung Ihres eigenen Schlüssels entschieden haben, helfen Ihnen die Informationen unter [Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key) weiter.

Wenn Sie sich für die Standardkonfiguration entschieden haben, bei der Ihr Mandantenschlüssel von Microsoft verwaltet wird, helfen Ihnen die Informationen im Abschnitt [Nächste Schritte](plan-implement-tenant-key.md#next-steps) des Artikels „Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels“ weiter.

