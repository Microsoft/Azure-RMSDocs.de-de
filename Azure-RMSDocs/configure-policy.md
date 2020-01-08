---
title: Konfigurieren der Azure Information Protection-Richtlinie – AIP
description: Zum Konfigurieren von Klassifizierung, Bezeichnung und Schutz für den Azure Information Protection-Client (klassisch) müssen Sie die Azure Information Protection-Richtlinie konfigurieren.
author: mlottner
ms.author: mlottner
ms.date: 1/06/2020
manager: rkarlin
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.subservice: aiplabels
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: a43059d0df56673955ebdfb2dd2890e0dba20c10
ms.sourcegitcommit: d0012de76c9156dd9239f7ba09c044a4b42ffc71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "75675328"
---
# <a name="configuring-the-azure-information-protection-policy"></a>Konfigurieren der Azure Information Protection-Richtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

> [!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection Client (klassisch)** und die Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021**eingestellt. Dieser Zeitrahmen ermöglicht es allen aktuellen Azure Information Protection Kunden, mithilfe der Microsoft Information Protection Unified-Beschriftungs Plattform zu unserer vereinheitlichten Bezeichnungs Lösung zu wechseln. Weitere Informationen finden Sie in der offiziellen [veralteten Notiz](https://aka.ms/aipclassicsunset).

> [!NOTE]
> Die Azure Information Protection-Richtlinie gilt für den Azure Information Protection Client (klassisch) und nicht für den Azure Information Protection Unified-Bezeichnungs Client. Wenn Sie nicht sicher sind, was der Unterschied zwischen diesen Clients ist, sehen Sie sich diese [FAQ](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client) an.
> 
> Informationen zum Konfigurieren von Vertraulichkeits Bezeichnungen und Richtlinien Einstellungen für den Unified Label-Client finden Sie unter [Overview of Sensitivität Labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) in der Office-Dokumentation.

Zum Konfigurieren von Klassifizierung, Bezeichnung und Schutz für den klassischen Client müssen Sie die Azure Information Protection Richtlinie konfigurieren. Diese Richtlinie wird dann auf Computer heruntergeladen, auf denen der [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) installiert ist.

Die Richtlinie enthält Bezeichnungen und Einstellungen:

- Durch Bezeichnungen erhalten Dokumente und E-Mails einen Klassifizierungswert: Diese Inhalte können optional durch Bezeichnungen geschützt werden. Der Azure Information Protection-Client zeigt diese Bezeichnungen für Ihre Benutzer in Office-Apps, und wenn Benutzer im Datei-Explorer mit der rechten Maustaste klicken, an. Diese Bezeichnungen können auch mithilfe von PowerShell und der Azure Information Protection-Überprüfung angewendet werden.

- Diese Einstellungen ändern das Standardverhalten des Azure Information Protection-Clients. Sie können beispielsweise eine Standardbezeichnung auswählen, die angibt, ob alle Dokumente und E-Mails über eine Bezeichnung verfügen müssen, und ob die Azure Information Protection-Leiste in Office-Apps angezeigt wird.

## <a name="subscription-support"></a>Abonnementsupport

Azure Information Protection unterstützt verschiedene Abonnementebenen:

- Azure Information Protection P2: Unterstützung für alle Klassifizierungs-, Bezeichnungs- und Schutzfunktionen

- Azure Information Protection P1: Unterstützung für die meisten Klassifizierungs-, Bezeichnungs- und Schutzfunktionen, jedoch keine automatische Klassifizierung oder HYOK

- Office 365, einschließlich des Azure Rights Management-Diensts: Unterstützung für Schutzfunktionen, jedoch keine Klassifizierung und Bezeichnung

Optionen, die ein Azure Information Protection P2-Abonnement erfordern, werden im Portal identifiziert.

Wenn in Ihrer Organisation eine Kombination aus verschiedenen Abonnements vorhanden ist, liegt es in Ihrer Verantwortung, sicherzustellen, dass Benutzer keine Features verwenden, für die ihr Konto nicht lizenziert ist. Der Azure Information Protection-Client ist nicht für die Überprüfung und Erzwingung von Lizenzen zuständig. Wenn Sie Optionen konfigurieren, für die nicht alle Benutzer eine Lizenz besitzen, verwenden Sie bereichsbezogene Richtlinien oder eine Registrierungseinstellung, um sicherzustellen, dass Ihre Organisation die Lizenzbestimmungen einhält:

- **In Ihrer Organisation ist eine Kombination aus Azure Information Protection P1- und Azure Information Protection P2-Lizenzen vorhanden**: Erstellen und verwenden Sie mindestens eine [bereichsbezogene Richtlinie](configure-policy-scope.md) für Benutzer mit einer P2-Lizenz, wenn Sie Optionen konfigurieren, die eine Azure Information Protection P2-Lizenz erfordern. Stellen Sie sicher, dass Ihre globale Richtlinie keine Optionen umfasst, die eine Azure Information Protection P2-Lizenz erfordern.

- **In Ihrer Organisation ist ein Abonnement für Azure Information Protection vorhanden, einige Benutzer verfügen aber nur über eine Lizenz für Office 365, die den Azure Rights Management-Dienst umfasst**: Bearbeiten Sie die Registrierung auf den Computern derjenigen Benutzer, die keine Lizenz für Azure Information Protection besitzen, damit diese Benutzer die Azure Information Protection-Richtlinie nicht herunterladen können. Anweisungen dazu finden Sie im Administratorhandbuch für die folgende Anpassung: [Erzwingen des reinen Schutzmodus, wenn die Organisation über eine Kombination verschiedener Lizenzen verfügt](./rms-client/client-admin-guide-customizations.md#enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses).

Weitere Informationen zu Abonnements finden Sie unter [Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?](faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)

## <a name="signing-in-to-the-azure-portal"></a>Anmelden beim Azure-Portal

So melden Sie sich beim Azure-Portal an, um Azure Information Protection zu konfigurieren und zu verwalten:

- Verwenden Sie den folgenden Link: https://portal.azure.com

- Verwenden Sie ein Azure AD Konto mit einer der folgenden [Administrator Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
    - **Azure Information Protection-Administrator**
    
  - **Complianceadministrator**
    
  - **Kompatibilitäts Daten Administrator**
    
  - **Sicherheitsadministrator**
    
    **Sicherheits Leser** - nur [Azure Information Protection Analytics](reports-aip.md)
    
    Nur **globale Reader** - - [Azure Information Protection Analytics](reports-aip.md)
    
  - **Globaler Administrator**
    
    > [!NOTE] 
    > Wenn sich Ihr Mandant auf der [Unified-Bezeichnung-Plattform](faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)befindet, wird die Azure Information Protection Administrator Rolle (ehemals "Information Protection Administrator") für die Azure-Portal nicht unterstützt. [Weitere Informationen](configure-policy-migrate-labels.md#administrative-roles-that-support-the-unified-labeling-platform)
    
    Microsoft-Konten können Azure Information Protection nicht verwalten.

## <a name="to-access-the-azure-information-protection-pane-for-the-first-time"></a>So greifen Sie zum ersten Mal auf den Azure Information Protection Bereich zu

1. Melden Sie sich im Azure-Portal an.

2. Klicken Sie auf die Option **+ Ressource erstellen**, und geben Sie dann im Suchfeld für den Marketplace **Azure Information Protection** ein. 
    
3. Wählen Sie aus den Ergebnisliste **Azure Information Protection** aus. Klicken Sie im Bereich **Azure Information Protection** auf **Erstellen**.
    
    > [!TIP] 
    > Wählen Sie optional **An Dashboard anheften** aus, um eine **Azure Information Protection**-Kachel auf Ihrem Dashboard zu erstellen, damit Sie bei der nächsten Anmeldung beim Portal nicht erneut nach dem Dienst suchen müssen können.
    
    Klicken Sie erneut auf **Erstellen**.

4. Beachten Sie die Seite **Schnellstart**, die automatisch geöffnet wird, wenn Sie zum ersten Mal eine Verbindung mit dem Dienst herstellen. Durchsuchen Sie die empfohlenen Ressourcen, oder verwenden Sie andere Menüoptionen. Verwenden Sie das folgende Verfahren, um Bezeichnungen, die Benutzer auswählen können, zu konfigurieren.

Wenn Sie das nächste Mal auf den **Azure Information Protection** Bereich zugreifen, wird automatisch die Option **Labels** ausgewählt, damit Sie Bezeichnungen für alle Benutzer anzeigen und konfigurieren können. Über das Menü **Allgemein** können Sie zur **Schnellstart**-Seite zurückkehren.

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

- Alle 24 Stunden.

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

- [Migrieren von Azure Information Protection-Bezeichnungen zu Office 365](configure-policy-migrate-labels.md)

## <a name="label-information-stored-in-emails-and-documents"></a>In E-Mails und Dokumenten gespeicherte Bezeichnungsinformationen

Wenn eine Bezeichnung auf ein Dokument oder eine E-Mail angewendet wird, wird die Bezeichnung hinter den Kulissen in den Metadaten gespeichert, so dass Anwendungen und Dienste die Bezeichnung lesen können:

- In e-Mails werden diese Informationen in der Datei "x-Header: **msip_labels: MSIP_Label_\<GUID > _Enabled = true** " gespeichert. 

- Für Word-Dokumente (. doc und. docx), Excel-Kalkulations Tabellen (XLS und. xlsx), PowerPoint-Präsentationen (PPT und PPTX) und PDF-Dokumente werden diese Metadaten in der folgenden benutzerdefinierten Eigenschaft gespeichert: **MSIP_Label_\<GUID > _Enabled = true**

Bei e-Mails werden die Bezeichnungs Informationen gespeichert, wenn die e-Mail gesendet wird. Bei Dokumenten werden die Bezeichnungs Informationen gespeichert, wenn die Datei gespeichert wird. 

Um die GUID für eine Bezeichnung zu identifizieren, suchen Sie den Bezeichnungs-ID-Wert im Bereich **Bezeichnung** im Azure-Portal, wenn Sie die Azure Information Protection Richtlinie anzeigen oder konfigurieren. Bei Dateien, auf die Bezeichnungen angewendet wurden, können Sie auch das PowerShell-Cmdlet [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) ausführen, um die GUID (MainLabelId oder SubLabelId) zu identifizieren. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, geben Sie immer die GUID einer untergeordneten Bezeichnung an, nicht die der übergeordneten Bezeichnung.

## <a name="next-steps"></a>Nächste Schritte

Beispiele zum Anpassen der Azure Information Protection-Richtlinie und das resultierende Verhalten für Benutzer finden Sie in den folgenden Tutorials:

- [Bearbeiten der Azure Information Protection-Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md)

- [Tutorial: Konfigurieren von Azure Information Protection-Richtlinieneinstellungen, die nahtlos funktionieren](infoprotect-settings-tutorial.md)

Informationen zur Leistung Ihrer Richtlinie finden Sie unter [Zentrale Berichterstellung für Azure Information Protection](reports-aip.md).

