---
title: Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen – AIP
description: Haben Sie Fragen, die sich speziell auf Klassifizierungen und Bezeichnungen bei Azure Information Protection beziehen? Vielleicht finden Sie hier eine Antwort.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/07/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 22d655bc69fc5db7b4bad27eb09a826a1fde34b9
ms.sourcegitcommit: 8a45d209273d748ee0f2a96c97893288c0b7efa5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102446880"
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen in Azure Information Protection

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Weitere Informationen finden Sie auch in den häufig gestellten Fragen [zum klassischen Client](faqs-classic.md). *

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Haben Sie Fragen zu Azure Information Protection, die sich speziell auf Klassifizierungen und Bezeichnungen beziehen?  Vielleicht finden Sie hier eine Antwort. 

## <a name="which-client-do-i-install-for-testing-new-functionality"></a>Welchen Client installiere ich zum Testen neuer Funktionen?

Es wird empfohlen, den **Azure Information Protection Unified Bezeichnung-Client** zu installieren. Der Unified Label-Client lädt Bezeichnungen und Richtlinien Einstellungen von einem der folgenden admin Centers herunter: 

- Office 365 Security & Compliance Center
- Microsoft 365 Security Center
- Microsoft 365 Compliance Center.

Dieser Client ist nun allgemein verfügbar und verfügt möglicherweise über eine Vorschauversion, um zusätzliche Funktionen für eine zukünftige Version zu testen.

Wenn Sie weiterhin Bezeichnungen in der Azure-Portal konfiguriert haben, die Sie noch nicht [zum vereinheitlichten Bezeichnungs Speicher migriert](configure-policy-migrate-labels.md)haben, verwenden Sie stattdessen den **klassischen Azure Information Protection-Client** .

Weitere Informationen, einschließlich einer Funktions-und Funktionalitäts Vergleichstabelle, finden [Sie unter Auswählen der Windows-beschriftungslösung](rms-client/use-client.md#choose-your-windows-labeling-solution).

> [!TIP]
> Der Azure Information Protection-Client wird nur unter Windows unterstützt. 
>
> Verwenden Sie zum klassifizieren und schützen von Dokumenten und e-Mails auf Ios, Android, macOS und im Web [Office-Apps, die die integrierte Bezeichnung unterstützen](/microsoft-365/compliance/sensitivity-labels-office-apps#support-for-sensitivity-label-capabilities-in-apps). 
> 

## <a name="where-can-i-find-information-about-using-sensitivity-labels-for-office-apps"></a>Wo finde ich Informationen zur Verwendung von Vertraulichkeits Bezeichnungen für Office-Apps?

Weitere Informationen finden Sie in den folgenden Dokumentations Ressourcen:

- [Informationen zu Empfindlichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) 

- [Verwenden von Vertraulichkeitsbezeichnungen in Office-Apps](/microsoft-365/compliance/sensitivity-labels-office-apps)

- [Aktivieren von Vertraulichkeitsbezeichnungen für Office-Dateien in SharePoint und OneDrive](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files)

- [Anwenden von Vertraulichkeits Bezeichnungen auf Ihre Dokumente und e-Mails innerhalb von Office](https://support.office.com/article/Apply-sensitivity-labels-to-your-documents-and-email-within-Office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9#ID0EBFAAA=Office_365)

Weitere Informationen zu anderen Szenarien, die Vertraulichkeits Bezeichnungen unterstützen, finden Sie unter [häufige Szenarien für Vertraulichkeits Bezeichnungen](/microsoft-365/compliance/get-started-with-sensitivity-labels#common-scenarios-for-sensitivity-labels).

## <a name="how-do-i-prevent-somebody-from-removing-or-changing-a-label"></a>Wie hindere ich jemanden daran, eine Bezeichnung zu entfernen oder zu ändern?

Um Benutzer daran zu hindern, eine Bezeichnung zu entfernen oder zu ändern, muss der Inhalt bereits geschützt sein. Die Schutzberechtigungen erteilen dem Benutzer nicht das [Nutzungsrecht](configure-usage-rights.md) „Exportieren“ oder „Vollzugriff“. 

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Wenn eine E-Mail eine Bezeichnung umfasst, erhalten Anlagen dann automatisch dieselbe Bezeichnung?

Nein. Wenn Sie einer E-Mail-Nachricht mit Anlagen eine Bezeichnung zuweisen, erben die Anlagen nicht dieselbe Bezeichnung. Die Anhänge erhalten keine Bezeichnung, oder es wird eine separate Bezeichnung angewendet. Wenn aber mit der Bezeichnung für die E-Mail ein Schutz konfiguriert wird, wird dieser Schutz auch auf die Office-Anlagen angewendet.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Wie können DLP-Lösungen und andere Anwendungen in Azure Information Protection integriert werden?

Da Azure Information Protection persistente Metadaten für die Klassifizierung verwendet, die eine Klartextbezeichnung enthalten, können diese Informationen von DLP-Lösungen und anderen Anwendungen gelesen werden. 

Beispiele für die Verwendung dieser Metadaten mit Exchange Online-Nachrichtenflussregeln finden Sie unter [Konfigurieren von Exchange Online-Nachrichtenflussregeln für Azure Information Protection-Bezeichnungen](configure-exo-rules.md).