---
title: Byok-Details-Azure Information Protection
description: Informieren Sie sich über die Details und Einschränkungen, wenn Sie von Kunden verwaltete Schlüssel (die als "Bring your own Key" bezeichnet werden, oder Byok) mit Azure Information Protection.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 04/28/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.subservice: kms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: dd07fe942f9f715dea6d6dc17d5c5d00e2da0d65
ms.sourcegitcommit: 8499602fba94fbfa28d7682da2027eeed6583c61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2020
ms.locfileid: "83746342"
---
# <a name="bring-your-own-key-byok-details-for-azure-information-protection"></a>Byok-Details (Bring your own Key) für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Organisationen mit einem Abonnement, das Azure Information Protection umfasst, können Ihren Azure Information Protection Mandanten so konfigurieren, dass er einen vom Kunden verwalteten Schlüssel verwendet und [seine Verwendung protokolliert](log-analyze-usage.md). Die vom Kunden verwaltete Schlüssel Konfiguration wird häufig als "Bring your own Key" oder Byok bezeichnet.

Dieser vom Kunden verwaltete Schlüssel muss in Azure Key Vault gespeichert werden, für die ein Azure-Abonnement erforderlich ist. Sie müssen den Premiumtarif von Azure Key Vault verwenden, um einen HSM-geschützten Schlüssel nutzen zu können. Für die Verwendung eines Schlüssels in Azure Key Vault fällt eine monatliche Gebühr an. Weitere Informationen finden Sie auf der [Seite Azure Key Vault Preise](https://azure.microsoft.com/pricing/details/key-vault/).

Wenn Sie Azure Key Vault für Ihren Azure Information Protection-Mandantenschlüssel einsetzen, empfiehlt es sich, einen dedizierten Schlüsseltresor für diesen Schlüssel zu verwenden, um sicherzustellen, dass er nur vom Azure Rights Management-Dienst verwendet wird. Diese Konfiguration gewährleistet, dass Aufrufe anderer Dienste nicht zu einer Überschreitung der Key Vault-[Dienstgrenzwerte](/azure/key-vault/key-vault-service-limits) führen, wodurch die Antwortzeiten des Azure Rights Management-Diensts gedrosselt werden könnten.  

Da jeder Dienst, der Azure Key Vault verwendet, in der Regel andere Anforderungen an die Schlüsselverwaltung aufweist, empfiehlt es sich darüber hinaus, ein separates Azure-Abonnement für diesen Schlüsseltresor zu verwenden, um fehlerhafte Konfigurationen zu verhindern. 

Wenn Sie jedoch ein Azure-Abonnement auch für andere Dienste verwenden möchten, die Azure Key Vault nutzen, stellen Sie sicher, dass eine gemeinsame Gruppe von Administratoren für das Abonnement zuständig ist. Mit dieser Vorsichtsmaßnahme können Sie dafür sorgen, dass Administratoren, die dieses Abonnement verwenden, alle Schlüssel genau kennen, auf die sie Zugriff haben, sodass die Wahrscheinlichkeit fehlerhaften Konfigurationen sinkt. 

Ein gemeinsames Azure-Abonnement bietet sich z.B. dann an, wenn es sich bei den Administratoren für Ihren Azure Information Protection-Mandantenschlüssel um die gleichen Personen handelt, die Office 365-Kundenschlüssel und Schlüssel für CRM Online verwalten. 

Wenn die Administratoren, die die Schlüssel für Customer Key oder CRM Online verwalten, nicht dieselben Personen sind, die ihren Azure Information Protection Mandanten Schlüssel verwalten, wird empfohlen, dass Sie Ihr Azure-Abonnement nicht für Azure Information Protection freigeben.

## <a name="benefits-of-using-azure-key-vault"></a>Vorteile der Verwendung von Azure Key Vault

Um die Sicherheit zu erhöhen, können Sie mit [Azure Key Vault Protokollierung](/azure/key-vault/key-vault-logging)einen Querverweis auf die Azure Information Protection Verwendungs Protokollierung durchsuchen. Die Key Vault Protokolle stellen eine Methode bereit, mit der Sie unabhängig überwachen können, dass nur der Azure Rights Management-Dienst Ihren Schlüssel verwendet. Bei Bedarf können Sie den Zugriff auf den Schlüssel sofort widerrufen, indem Sie die Berechtigungen für den Schlüsseltresor entfernen.

Weitere Vorteile der Verwendung von Azure Key Vault für Ihren Azure Information Protection Mandanten Schlüssel:

- Azure Key Vault ist eine zentralisierte Schlüsselverwaltungslösung, die eine konsistente Verwaltungslösung für viele cloudbasierte und sogar lokale Dienste bietet, die Verschlüsselung verwenden.

- Azure Key Vault unterstützt eine Reihe von integrierten Schnittstellen für die Schlüsselverwaltung, einschließlich PowerShell, CLI, REST-APIs und das Azure-Portal. Andere Dienste und Tools wurden in den Schlüsseltresor integriert, um Funktionen bereitzustellen, die für bestimmte Aufgaben, z. B. Überwachung, optimiert wurden. So können Sie beispielsweise die Schlüsselverwendungsprotokolle über Log Analytics aus der Operations Management Suite analysieren, festlegen, dass bei Erfüllung bestimmter Kriterien Benachrichtigungen gesendet werden, und so weiter.

- Azure Key Vault bietet Rollentrennung als anerkannte und bewährte Sicherheitsmethode. Azure Information Protection-Administratoren können sich auf die Verwaltung von Datenklassifizierung und -Datenschutz konzentrieren, und Azure Key Vault-Administratoren können sich auf die Verwaltung von Verschlüsselungsschlüsseln und speziellen Richtlinien konzentrieren, die möglicherweise aus Sicherheits- oder Compliancegründen erforderlich sind.

- In einigen Organisationen gibt es Einschränkungen für die Verwahrung ihres Hauptschlüssels. Azure Key Vault bietet ein hohes Maß an Kontrolle über den Speicherort des Hauptschlüssels, da der Dienst in viele Azure-Regionen verfügbar ist. Sie können aus einer Reihe von Azure-Regionen auswählen, und Sie können davon ausgehen, dass sich diese Anzahl erhöht. Weitere Informationen finden Sie auf der Seite [Verfügbare Produkte nach Region](https://azure.microsoft.com/regions/services/) auf der Azure-Website.

Zusätzlich zum Verwalten von Schlüsseln bietet Azure Key Vault Ihren Sicherheitsadministratoren die gleiche Verwaltungsumgebung zum Speichern von, Zugreifen auf und Verwalten von Zertifikaten und geheimen Schlüsseln (z. B. Kennwörtern) für andere Dienste und Anwendungen, die Verschlüsselung verwenden. 

Weitere Informationen zu Azure Key Vault finden Sie unter [Was ist Azure Key Vault?](/azure/key-vault/key-vault-whatis). Im [Azure Key Vault-Teamblog](https://blogs.technet.microsoft.com/kv/) finden Sie aktuelle Informationen und erfahren, wie andere Dienste diese Technologie verwenden.

## <a name="byok-support-for-services-and-clients"></a>Byok-Unterstützung für Dienste und Clients

Byok und die [Verwendungs Protokollierung](log-analyze-usage.md) arbeiten nahtlos mit jeder Anwendung zusammen, die in den Azure-Rights Management-Dienst integriert ist, der von Azure Information Protection zum Schutz von Daten verwendet wird. Dies schließt Clouddienste wie Microsoft SharePoint, lokale Server, die Exchange und SharePoint ausführen, die den Azure Rights Management Service mithilfe des RMS-Verbindungs Diensts verwenden, sowie Client Anwendungen wie Office 2019, Office 2016 und Office 2013 ein. 

Sie erhalten Schlüssel Verwendungs Protokolle, jede Anwendung, die Anforderungen an den Azure Rights Management-Dienst sendet.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie sich für die Verwaltung Ihres eigenen Schlüssels entschieden haben, helfen Ihnen die Informationen unter [Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key) weiter.

Wenn Sie sich für die Standardkonfiguration entschieden haben, bei der Ihr Mandantenschlüssel von Microsoft verwaltet wird, helfen Ihnen die Informationen im Abschnitt [Nächste Schritte](plan-implement-tenant-key.md#next-steps) des Artikels „Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels“ weiter.

