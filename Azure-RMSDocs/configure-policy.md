---
title: Konfigurieren der Azure Information Protection-Richtlinie – AIP
description: Zum Konfigurieren von Klassifizierung, Bezeichnung und Schutz für den Azure Information Protection klassischen Client müssen Sie die Azure Information Protection-Richtlinie konfigurieren.
author: batamig
ms.author: bagol
ms.date: 08/17/2020
manager: rkarlin
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ROBOTS: NOINDEX
ms.subservice: aiplabels
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 6112682c202d32632e5d3678c4f7b0434018a4fb
ms.sourcegitcommit: b32c16e41ba36167b5a3058b56a73183bdd4306d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/29/2020
ms.locfileid: "97806310"
---
# <a name="configuring-the-azure-information-protection-policy"></a>Konfigurieren der Azure Information Protection-Richtlinie

>***Gilt für** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified Label-Client finden Sie in der Microsoft 365-Dokumentation unter Informationen [zu Sensitivitäts Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) . *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Zum Konfigurieren von Klassifizierung, Bezeichnung und Schutz für den klassischen Client müssen Sie die Azure Information Protection Richtlinie konfigurieren. Diese Richtlinie wird dann auf Computer heruntergeladen, auf denen der Azure Information Protection-Client installiert ist.

Die Richtlinie enthält Bezeichnungen und Einstellungen:

- Durch Bezeichnungen erhalten Dokumente und E-Mails einen Klassifizierungswert: Diese Inhalte können optional durch Bezeichnungen geschützt werden. Der Azure Information Protection-Client zeigt diese Bezeichnungen für Ihre Benutzer in Office-Apps, und wenn Benutzer im Datei-Explorer mit der rechten Maustaste klicken, an. Diese Bezeichnungen können auch mithilfe von PowerShell und der Azure Information Protection-Überprüfung angewendet werden.

- Diese Einstellungen ändern das Standardverhalten des Azure Information Protection-Clients. Sie können beispielsweise eine Standardbezeichnung auswählen, die angibt, ob alle Dokumente und E-Mails über eine Bezeichnung verfügen müssen, und ob die Azure Information Protection-Leiste in Office-Apps angezeigt wird.

## <a name="subscription-support"></a>Abonnementsupport

Azure Information Protection unterstützt verschiedene Abonnementebenen:

- Azure Information Protection P2: Unterstützung für alle Klassifizierungs-, Bezeichnungs- und Schutzfunktionen

- Azure Information Protection P1: Unterstützung für die meisten Klassifizierungs-, Bezeichnungs- und Schutzfunktionen, jedoch keine automatische Klassifizierung oder HYOK

- Microsoft 365, die den Azure Rights Management-Dienst umfasst: Unterstützung für Schutz, aber keine Klassifizierung und Bezeichnung.

Optionen, die ein Azure Information Protection P2-Abonnement erfordern, werden im Portal identifiziert.

Wenn in Ihrer Organisation eine Kombination aus verschiedenen Abonnements vorhanden ist, liegt es in Ihrer Verantwortung, sicherzustellen, dass Benutzer keine Features verwenden, für die ihr Konto nicht lizenziert ist. Der Azure Information Protection-Client ist nicht für die Überprüfung und Erzwingung von Lizenzen zuständig. Wenn Sie Optionen konfigurieren, für die nicht alle Benutzer eine Lizenz besitzen, verwenden Sie bereichsbezogene Richtlinien oder eine Registrierungseinstellung, um sicherzustellen, dass Ihre Organisation die Lizenzbestimmungen einhält:

- **In Ihrer Organisation ist eine Kombination aus Azure Information Protection P1- und Azure Information Protection P2-Lizenzen vorhanden**: Erstellen und verwenden Sie mindestens eine [bereichsbezogene Richtlinie](configure-policy-scope.md) für Benutzer mit einer P2-Lizenz, wenn Sie Optionen konfigurieren, die eine Azure Information Protection P2-Lizenz erfordern. Stellen Sie sicher, dass Ihre globale Richtlinie keine Optionen umfasst, die eine Azure Information Protection P2-Lizenz erfordern.

- **Wenn Ihre Organisation über ein Abonnement für Azure Information Protection verfügt, einige Benutzer aber nur über eine Lizenz für Microsoft 365 verfügen, die den Azure Rights Management-Dienst umfasst**: für die Benutzer, die über keine Lizenz für Azure Information Protection verfügen, bearbeiten Sie die Registrierung auf ihren Computern, damit Sie die Azure Information Protection Richtlinie nicht herunterladen. Anweisungen dazu finden Sie im Administratorhandbuch für die folgende Anpassung: [Erzwingen des reinen Schutzmodus, wenn die Organisation über eine Kombination verschiedener Lizenzen verfügt](./rms-client/client-admin-guide-customizations.md#enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses).

Weitere Informationen zu Abonnements finden Sie unter [Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?](faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)

## <a name="signing-in-to-the-azure-portal"></a>Anmelden beim Azure-Portal

So melden Sie sich beim Azure-Portal an, um Azure Information Protection zu konfigurieren und zu verwalten:

- Verwenden Sie den folgenden Link: https://portal.azure.com

- Verwenden Sie ein Azure AD Konto mit einer der folgenden [Administrator Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
    - **Azure Information Protection-Administrator**
    
  - **Complianceadministrator**
    
  - **Compliancedatenadministrator**
    
  - **Sicherheitsadministrator**
    
    **Sicherheits Leser**  -  Nur [Azure Information Protection Analytics](reports-aip.md)
    
    **Globaler Reader**  -  Nur [Azure Information Protection Analytics](reports-aip.md)
    
  - **Globaler Administrator**
    
    > [!NOTE] 
    > Wenn sich Ihr Mandant auf der [Unified-Bezeichnung-Plattform](faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)befindet, wird die Azure Information Protection Administrator Rolle (ehemals "Information Protection Administrator") für die Azure-Portal nicht unterstützt. [Weitere Informationen](configure-policy-migrate-labels.md#administrative-roles-that-support-the-unified-labeling-platform)
    
    Microsoft-Konten können Azure Information Protection nicht verwalten.

## <a name="to-access-the-azure-information-protection-pane-for-the-first-time"></a>So greifen Sie zum ersten Mal auf den Azure Information Protection Bereich zu

1. Melden Sie sich beim Azure-Portal an.

2. Klicken Sie auf die Option **+ Ressource erstellen**, und geben Sie dann im Suchfeld für den Marketplace **Azure Information Protection** ein. 
    
3. Wählen Sie aus den Ergebnisliste **Azure Information Protection** aus. Klicken Sie im Bereich **Azure Information Protection** auf **Erstellen**.
    
    > [!TIP] 
    > Wählen Sie optional **An Dashboard anheften** aus, um eine **Azure Information Protection**-Kachel auf Ihrem Dashboard zu erstellen, damit Sie bei der nächsten Anmeldung beim Portal nicht erneut nach dem Dienst suchen müssen können.
    
    Klicken Sie erneut auf **Erstellen**.

4. Beachten Sie die Seite **Schnellstart**, die automatisch geöffnet wird, wenn Sie zum ersten Mal eine Verbindung mit dem Dienst herstellen. Durchsuchen Sie die empfohlenen Ressourcen, oder verwenden Sie andere Menüoptionen. Verwenden Sie das folgende Verfahren, um Bezeichnungen, die Benutzer auswählen können, zu konfigurieren.

Wenn Sie das nächste Mal auf den **Azure Information Protection** Bereich zugreifen, wird automatisch die Option **Labels** ausgewählt, damit Sie Bezeichnungen für alle Benutzer anzeigen und konfigurieren können. Sie können zur Seite **Schnellstart** zurückkehren, indem Sie Sie im Menü **Allgemein** auswählen.

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Informationen zum Konfigurieren der Azure Information Protection-Richtlinie

1. Stellen Sie sicher, dass Sie beim Azure-Portal angemeldet sind, indem Sie eine dieser administrativen Rollen verwenden: Azure Information Protection Administrator, Sicherheitsadministrator oder globale Verwaltung. Im [vorherigen Abschnitt](#signing-in-to-the-azure-portal) finden Sie weitere Informationen zu diesen Administratorrollen.

2. Navigieren Sie ggf. zum **Azure Information Protection** Bereich: Klicken Sie beispielsweise im hubmenü auf **alle Dienste** , und beginnen Sie mit der Eingabe **Information Protection** im Filter Feld. Wählen Sie aus den Ergebnissen **Azure Information Protection** aus. 
    
    Der Bereich **Azure Information Protection-Bezeichnungen** wird automatisch geöffnet, damit Sie die verfügbaren Bezeichnungen anzeigen und bearbeiten können. Die Bezeichnungen können allen Benutzern, ausgewählten Benutzern oder keinem Benutzer zur Verfügung gestellt werden, indem diese zu einer Richtlinie hinzugefügt oder daraus entfernt werden.

3. Wählen Sie aus den Menüoptionen die Option **Richtlinien** aus, um die Richtlinien anzuzeigen und zu bearbeiten. Wählen Sie die Richtlinie **Global** aus, um die Richtlinie anzuzeigen und zu bearbeiten, die von sämtlichen Benutzern abgerufen werden kann. Klicken Sie auf **Neue Richtlinie hinzufügen**, um eine benutzerdefinierte Richtlinie für ausgewählte Benutzer zu erstellen.
    

### <a name="making-changes-to-the-policy"></a>Vornehmen von Änderungen an der Richtlinie

Sie können eine beliebige Anzahl von Bezeichnungen erstellen. Wenn jedoch so viele Bezeichnungen vorhanden sind, dass Benutzer nur schwer die richtige auswählen können, sollten Sie bereichsbezogene Richtlinien erstellen, damit Benutzern nur relevante Bezeichnungen angezeigt werden. Die Höchstgrenze für Bezeichnungen, die Schutz anwenden, beträgt 500.

Wenn Sie Änderungen an einem Azure Information Protection Bereich vornehmen, klicken Sie auf **Speichern** , um die Änderungen zu speichern, oder auf **verwerfen** , um die zuletzt gespeicherten Einstellungen wiederherzustellen. Wenn Sie Änderungen in einer Richtlinie speichern oder Änderungen an Bezeichnungen vornehmen, die zu Richtlinien hinzugefügt werden, werden diese Änderungen automatisch veröffentlicht. Es gibt keine gesonderte Veröffentlichungsoption.

Beim Start einer unterstützten Office-Anwendung prüft der Azure Information Protection-Client, ob Änderungen vorgenommen wurden. Gegebenenfalls lädt der Client diese Änderungen dann als neueste Azure Information Protection-Richtlinie herunter. Folgende zusätzliche Trigger aktualisieren die Richtlinie im Client ebenfalls:

- Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen.

- Ausführen der [PowerShell-Cmdlets](./rms-client/client-admin-guide-powershell.md) zur Bezeichnung und zum Schutz (Get-AIPFileStatus, Set-AIPFileClassification und Set-AIPFileLabel).

- Alle 24 Stunden

- Für die [Azure Information Protection-Überprüfung](deploy-aip-scanner.md): Wenn der Dienst gestartet wird (wenn die Richtlinie älter als eine Stunde ist) und jede Stunde während des Vorgangs.


>[!NOTE]
>Wenn der Client die Richtlinie herunterlädt, sollten Sie mit einigen Minuten Wartezeit rechnen, bevor sie vollständig einsatzbereit ist. Die tatsächliche Zeit hängt von Faktoren wie der Größe und Komplexität der Richtlinienkonfiguration und der Netzwerkkonnektivität ab. Wenn die resultierende Aktion Ihrer Bezeichnungen nicht mit Ihren letzten Änderungen übereinstimmt, sollten Sie bis zu 15 Minuten warten und es dann erneut versuchen.

### <a name="configuring-your-organizations-policy"></a>Konfigurieren der Richtlinie Ihrer Organisation

Über die folgenden Links können Sie auf Informationen zum Konfigurieren der Azure Information Protection-Richtlinie zugreifen:

- [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md)

- [Konfigurieren der Richtlinieneinstellungen](configure-policy-settings.md)

- [Erstellen einer neuen Bezeichnung für Azure Information Protection](configure-policy-new-label.md)

- [Hinzufügen oder Entfernen einer Bezeichnung](configure-policy-add-remove-label.md)
 
- [Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection](configure-policy-delete-reorder.md)

- [Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection](configure-policy-change-label.md)

- [Konfigurieren einer Bezeichnung zum Schutz](configure-policy-protection.md)

- [Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information Protection](configure-policy-markings.md)

- [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)

- [Konfigurieren der Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md)

- [Informationen zum Konfigurieren und Verwalten von Vorlagen](configure-policy-templates.md)

- [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md)

- [Vorgehensweise beim Migrieren von Azure Information Protection Bezeichnungen zu Microsoft 365](configure-policy-migrate-labels.md)

## <a name="label-information-stored-in-emails-and-documents"></a>In E-Mails und Dokumenten gespeicherte Bezeichnungsinformationen

Wenn eine Bezeichnung auf ein Dokument oder eine E-Mail angewendet wird, wird die Bezeichnung hinter den Kulissen in den Metadaten gespeichert, so dass Anwendungen und Dienste die Bezeichnung lesen können:

- In e-Mails werden diese Informationen in der Datei "x-Header: **msip_labels: MSIP_Label_ \<GUID> _Enabled = true** " gespeichert. 

- Für Word-Dokumente (doc und DOCX), Excel-Kalkulations Tabellen (. xls und. xlsx), PowerPoint-Präsentationen (. ppt und. pptx) und PDF-Dokumente werden diese Metadaten in der folgenden benutzerdefinierten Eigenschaft gespeichert: **MSIP_Label_ \<GUID> _Enabled = true**

Bei e-Mails werden die Bezeichnungs Informationen gespeichert, wenn die e-Mail gesendet wird. Bei Dokumenten werden die Bezeichnungs Informationen gespeichert, wenn die Datei gespeichert wird. 

Um die GUID für eine Bezeichnung zu identifizieren, suchen Sie den Bezeichnungs-ID-Wert im Bereich **Bezeichnung** im Azure-Portal, wenn Sie die Azure Information Protection Richtlinie anzeigen oder konfigurieren. Bei Dateien, auf die Bezeichnungen angewendet wurden, können Sie auch das PowerShell-Cmdlet [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) ausführen, um die GUID (MainLabelId oder SubLabelId) zu identifizieren. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, geben Sie immer die GUID einer untergeordneten Bezeichnung an, nicht die der übergeordneten Bezeichnung.

## <a name="next-steps"></a>Nächste Schritte

Beispiele zum Anpassen der Azure Information Protection-Richtlinie und das resultierende Verhalten für Benutzer finden Sie in den folgenden Tutorials:

- [Bearbeiten der Azure Information Protection-Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md)

- [Konfigurieren von Azure Information Protection-Richtlinieneinstellungen, die nahtlos funktionieren](infoprotect-settings-tutorial.md)

Informationen zur Leistung Ihrer Richtlinie finden Sie unter [Zentrale Berichterstellung für Azure Information Protection](reports-aip.md).