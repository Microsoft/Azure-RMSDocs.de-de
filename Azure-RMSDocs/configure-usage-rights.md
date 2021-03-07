---
title: Konfigurieren von Nutzungsrechten für Azure Information Protection (AIP)
description: Verstehen und identifizieren Sie die spezifischen Rechte, die beim Schützen von Dateien oder e-Mails mithilfe Rights Management Schutzes von Azure Information Protection verwendet werden.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/04/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.subservice: azurerms
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 13263b8d11829104bb0175b4ca91d023637dd1f5
ms.sourcegitcommit: 74b8d03d1ede3da12842b84546417e63897778bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2021
ms.locfileid: "102415278"
---
# <a name="configure-usage-rights-for-azure-information-protection"></a>Konfigurieren von Nutzungsrechten für Azure Information Protection

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
> 
> Aus Gründen der Vollständigkeit enthält der Artikel Werte aus dem klassischen Azure-Portal, das am 8. Januar 2018 außer Kraft gesetzt wurde.

In diesem Artikel werden Nutzungsrechte beschrieben, die Sie so konfigurieren können, dass Sie automatisch angewendet werden, wenn eine Bezeichnung oder eine Vorlage von Benutzern, Administratoren oder konfigurierten Diensten ausgewählt wird.

Wenn Sie Vertraulichkeits Bezeichnungen oder Schutz Vorlagen für die Verschlüsselung konfigurieren, werden die Nutzungsrechte ausgewählt. Sie können beispielsweise Rollen auswählen, die eine logische Gruppierung von Nutzungsrechten konfigurieren, oder die einzelnen Rechte separat konfigurieren. Alternativ können Benutzer die Nutzungsrechte selbst auswählen und anwenden.

> [!IMPORTANT]
> Verwenden Sie diesen Artikel, um zu *verstehen, wie* Nutzungsrechte von Anwendungen interpretiert werden können. 
>
> Anwendungen können sich bei der Implementierung von Nutzungsrechten unterscheiden, und wir empfehlen Ihnen, sich mit der Dokumentation Ihrer Anwendung zu informieren und ihre eigenen Tests durchzuführen, um das Anwendungsverhalten vor der Bereitstellung in der Produktion zu
> 

## <a name="usage-rights-and-descriptions"></a>Nutzungsrechte und Beschreibungen
In der folgenden Tabelle sind die Nutzungsrechte aufgelistet und beschrieben, die Rights Management unterstützt, und wie sie verwendet und interpretiert werden. Sie sind mit ihrem **allgemeinen Namen** aufgelistet, wie die Nutzungsrechte in der Regel angezeigt werden, bzw. über den auf sie verwiesen wird, als benutzerfreundlichere Version des Einzelwortwerts, der im Code verwendet wird (der **Richtliniencodierungswert**). 

In dieser Tabelle gilt Folgendes:

- Die **API-Konstante oder der API-Wert** ist der SDK-Name für einen msipc-API-Befehl, der verwendet wird, wenn Sie eine Anwendung schreiben, die ein Nutzungsrecht prüft, oder einer Richtlinie ein Nutzungsrecht hinzufügt.

- Die **Bezeichnung Admin Center** bezieht sich auf den Speicherort der Vertraulichkeits Bezeichnungen und kann entweder das Microsoft 365 Compliance Center, das Microsoft 365 Security Center oder das Microsoft 365 Security & Compliance Center sein.

    Wenn Sie über den klassischen Client verfügen, konfigurieren Sie Ihre Bezeichnungen und Bezeichnungs Richtlinien im Azure-Portal.


|Nutzungsrecht|BESCHREIBUNG|Implementierung|
|-------------------------------|---------------------------|-----------------|
|Allgemeiner Name: **Inhalt bearbeiten, Bearbeiten** <br /><br />Richtliniencodierung: **DOCEDIT**|Ermöglicht es dem Benutzer, den Inhalt innerhalb der Anwendung zu ändern, neu anzuordnen, zu formatieren oder zu sortieren. Gewährt nicht das Recht, die bearbeitete Kopie zu speichern.<br /><br />In Word ist dieses Recht nur bei Office 365 ProPlus mit einer Mindestversion von [1807](/officeupdates/monthly-channel-2018#version-1807-july-25) ausreichend, um **Änderungen nachverfolgen** zu aktivieren oder zu deaktivieren oder alle Features zum Nachverfolgen von Änderungen zu verwenden. Ist dies nicht der Fall, ist das Recht **Vollzugriff** erforderlich, um alle Optionen der Änderungsnachverfolgung zu verwenden. |Benutzerdefinierte Office-Rechte: als Teil der Optionen **Änderung** und **Vollzugriff**. <br /><br />Name im klassischen Azure-Portal: **Inhalt bearbeiten**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **Inhalt bearbeiten, bearbeiten (docedit)**<br /><br />Name in AD RMS-Vorlagen: **Bearbeiten** <br /><br />API-Konstante oder -Wert: nicht zutreffend.|
|Allgemeiner Name: **Speichern** <br /><br />Richtliniencodierung: **EDIT**|Ermöglicht es dem Benutzer, das Dokument am aktuellen Speicherort zu speichern.<br /><br />In Office-Anwendungen ermöglicht dieses Recht dem Benutzer, das Dokument zu ändern und unter einem neuen Namen zu speichern, wenn das ausgewählte Dateiformat nativ Unterstützung für den Rights Management-Schutz bietet. Die Dateiformatbeschränkung stellt dabei sicher, dass der ursprüngliche Schutz nicht aus der Datei entfernt werden kann.|Benutzerdefinierte Office-Rechte: als Teil der Optionen **Änderung** und **Vollzugriff**. <br /><br />Name im klassischen Azure-Portal: **Datei speichern**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **speichern (Bearbeiten)**<br /><br />Name in AD RMS-Vorlagen: **Speichern** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_WRITE L"EDIT"`|
|Allgemeiner Name: **Kommentar** <br /><br />Richtliniencodierung: **COMMENT**|Ermöglicht der Option, dem Inhalt Anmerkungen oder Kommentare hinzuzufügen.<br /><br />Dieses Recht ist im SDK verfügbar, als Ad-hoc-Richtlinie in AzureInformationProtection und dem RMS-Schutz-Modul für Windows PowerShell verfügbar und wurde in einigen Anwendungen von Softwareherstellern implementiert. Sie wird jedoch nicht häufig verwendet und wird von Office-Anwendungen nicht unterstützt.|Benutzerdefinierte Office-Rechte: nicht implementiert. <br /><br />Name im klassischen Azure-Portal: nicht implementiert.<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: nicht implementiert.<br /><br />Name in AD RMS-Vorlagen: nicht implementiert. <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_COMMENT L"COMMENT`|
|Allgemeiner Name: **Speichern unter, Exportieren** <br /><br />Richtliniencodierung: **EXPORT**|Aktiviert die Option zum Speichern des Inhalts unter einem anderen Dateinamen (Speichern unter). <br /><br />Für den Azure Information Protection-Client kann die Datei ohne Schutz gespeichert und auch mit neuen Einstellungen und Berechtigungen erneut geschützt werden. Diese zulässigen Aktionen bedeuten, dass ein Benutzer, der über dieses Recht verfügt, eine Azure Information Protection-Bezeichnung aus einem geschützten Dokument oder einer geschützten E-Mail ändern oder entfernen kann. <br /><br />Durch dieses Recht hat der Benutzer auch die Möglichkeit, andere Exportoptionen in Anwendungen auszuführen, beispielsweise **An OneNote senden**.|Benutzerdefinierte Office-Rechte: als Teil der Option **Vollzugriff** <br /><br />Name im klassischen Azure-Portal: **Inhalt exportieren (Speichern unter)** <br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **Speichern unter, exportieren (Export)**<br /><br />Name in AD RMS-Vorlagen: **Exportieren (Speichern unter)** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Allgemeiner Name: **Weiterleiten** <br /><br />Richtliniencodierung: **FORWARD**|Aktiviert die Option zum Weiterleiten einer E-Mail-Nachricht und zum Hinzufügen von Empfängern in den Zeilen **An** und **Cc**. Dieses Recht wird nicht auf Dokumente angewendet, sondern nur auf E-Mail-Nachrichten.<br /><br />Erlaubt der Weiterleitung nicht, als Teil des Weiterleitungsvorgangs anderen Benutzern Berechtigungen zu gewähren. <br /><br />Wenn Sie diese Berechtigung gewähren, gewähren Sie auch die Berechtigung **Inhalt bearbeiten, Bearbeiten** (allgemeiner Name) sowie **Speichern** (allgemeiner Name), um sicherzustellen, dass die geschützte E-Mail nicht als Anhang versendet wird. Legen Sie diese Berechtigungen außerdem fest, wenn Sie eine E-Mail an eine andere Organisation versenden, die den Outlook-Client oder Outlook Web App verwendet. Oder für Benutzer in Ihrer Organisation, die von der Verwendung Rights Management Schutzes ausgenommen sind, da Sie [Onboarding](/powershell/module/aipservice/set-aipserviceonboardingcontrolpolicy)-Steuerelemente implementiert haben.|Benutzerdefinierte Office-Rechte: Bei Verwendung der Standardrichtlinie **Nicht weiterleiten** verweigert.<br /><br />Name im klassischen Azure-Portal: **Weiterleiten**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **Forward (vorwärts)**<br /><br />Name in AD RMS-Vorlagen: **Weiterleiten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Allgemeiner Name: **Vollzugriff** <br /><br />Richtliniencodierung: **OWNER**|Gewährt alle Berechtigungen für das Dokument, und alle verfügbaren Aktionen können ausgeführt werden.<br /><br />Bietet die Möglichkeit zum Entfernen des Schutzes und erneuten Schützen eines Dokuments. <br /><br />Beachten Sie, dass dieses Nutzungsrecht nicht mit dem des [Rights Management-Besitzers](#rights-management-issuer-and-rights-management-owner) identisch ist.|Benutzerdefinierte Office-Rechte: wie die benutzerdefinierte Option **Vollzugriff**.<br /><br />Name im klassischen Azure-Portal: **Vollzugriff**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **Full Control (owner)**<br /><br />Name in AD RMS-Vorlagen: **Vollzugriff** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_ALL L"OWNER"`|
|Allgemeiner Name: **Drucken** <br /><br />Richtliniencodierung: **PRINT**|Aktiviert die Optionen zum Drucken des Inhalts.|Benutzerdefinierte Office-Rechte: wie die Option **Inhalt drucken** in benutzerdefinierten Berechtigungen. Keine Pro-Empfänger-Einstellung.<br /><br />Name im klassischen Azure-Portal: **Drucken**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **Print (Print)**<br /><br />Name in AD RMS-Vorlagen: **Drucken** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_PRINT L"PRINT"`|
|Allgemeiner Name: **Antworten** <br /><br />Richtliniencodierung: **REPLY**|Aktiviert die **Antworten**-Option in einem E-Mail-Client, ohne Änderungen in der **An**- oder **Cc**-Zeile zuzulassen.<br /><br />Wenn Sie diese Berechtigung gewähren, gewähren Sie auch die Berechtigung **Inhalt bearbeiten, Bearbeiten** (allgemeiner Name) sowie **Speichern** (allgemeiner Name), um sicherzustellen, dass die geschützte E-Mail nicht als Anhang versendet wird. Legen Sie diese Berechtigungen außerdem fest, wenn Sie eine E-Mail an eine andere Organisation versenden, die den Outlook-Client oder Outlook Web App verwendet. Oder für Benutzer in Ihrer Organisation, die von der Verwendung Rights Management Schutzes ausgenommen sind, da Sie [Onboarding](/powershell/module/aipservice/set-aipserviceonboardingcontrolpolicy)-Steuerelemente implementiert haben.|Benutzerdefinierte Office-Rechte: nicht zutreffend.<br /><br />Name im klassischen Azure-Portal: **Antworten**<br /><br />Name im klassischen Azure-Portal: **Antworten (REPLY)**<br /><br />Name in AD RMS-Vorlagen: **Antworten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_REPLY`|
|Allgemeiner Name: **Allen Antworten** <br /><br />Richtliniencodierung: **REPLYALL**|Aktiviert die Option **Allen antworten** in einem E-Mail-Client, ermöglicht es dem Benutzer jedoch nicht, der Zeile **An** oder **Cc** Empfänger hinzuzufügen.<br /><br />Wenn Sie diese Berechtigung gewähren, gewähren Sie auch die Berechtigung **Inhalt bearbeiten, Bearbeiten** (allgemeiner Name) sowie **Speichern** (allgemeiner Name), um sicherzustellen, dass die geschützte E-Mail nicht als Anhang versendet wird. Legen Sie diese Berechtigungen außerdem fest, wenn Sie eine E-Mail an eine andere Organisation versenden, die den Outlook-Client oder Outlook Web App verwendet. Oder für Benutzer in Ihrer Organisation, die von der Verwendung Rights Management Schutzes ausgenommen sind, da Sie [Onboarding](/powershell/module/aipservice/set-aipserviceonboardingcontrolpolicy)-Steuerelemente implementiert haben.|Benutzerdefinierte Office-Rechte: nicht zutreffend.<br /><br />Name im klassischen Azure-Portal: **Allen antworten**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **allen Antworten (allen Antworten)**<br /><br />Name in AD RMS-Vorlagen: **Allen antworten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Allgemeiner Name: **Anzeigen, Öffnen, Lesen** <br /><br />Richtliniencodierung: **VIEW**|Ermöglicht dem Benutzer, das Dokument zu öffnen und den Inhalt zu sehen.<br /><br /> In Excel reicht dieses Recht nicht aus, um Daten zu sortieren, sodass folgendes Recht erforderlich ist: **Inhalt bearbeiten, Bearbeiten**. Zum Filtern von Daten in Excel, benötigen Sie die folgenden Rechte: **Inhalt bearbeiten, Bearbeiten** und **Kopieren**.|Benutzerdefinierte Office-Rechte: wie die benutzerdefinierte Richtlinie **Lesen**, Option **Anzeigen**.<br /><br />Name im klassischen Azure-Portal: **Anzeigen**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **anzeigen, öffnen, lesen (Ansicht)**<br /><br />Name in den AD RMS-Vorlagen: **Lesen** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_READ L"VIEW"`|
|Allgemeiner Name: **Kopieren** <br /><br />Richtliniencodierung: **EXTRACT**|Aktiviert Optionen zum Kopieren von Daten (einschließlich Screenshots) aus dem Dokument in dasselbe oder ein anderes Dokument.<br /><br />In einigen Anwendungen wird auch das Speichern des gesamten Dokuments in ungeschützter Form ermöglicht.<br /><br />In Skype for Business und ähnlichen Anwendungen mit Bildschirmfreigabe muss der Referent über dieses Recht verfügen, um ein geschütztes Dokument erfolgreich präsentieren zu können. Wenn der Referent nicht über dieses Recht verfügt, können die Teilnehmer das Dokument nicht sehen, und stattdessen wird ein schwarzer Bildschirm angezeigt.|Benutzerdefinierte Office-Rechte: wie die benutzerdefinierte Richtlinienoption **Benutzern mit Lesezugriff das Kopieren des Inhalts erlauben**.<br /><br />Name im klassischen Azure-Portal: **Inhalt kopieren und extrahieren**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **Copy (Extract)**<br /><br />Name in AD RMS-Vorlagen: **Extrahieren** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Allgemeiner Name: **Rechte anzeigen** <br /><br />Richtliniencodierung: **VIEWRIGHTSDATA**|Ermöglicht dem Benutzer, die Richtlinie anzuzeigen, die auf das Dokument angewendet wird. <br /><br /> Wird von Office-Apps oder Azure Information Protection-Clients nicht unterstützt.|Benutzerdefinierte Office-Rechte: nicht implementiert.<br /><br />Name im klassischen Azure-Portal: **Zugewiesene Rechte anzeigen**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **Rechte anzeigen (vieschreightdata)**.<br /><br />Name in AD RMS-Vorlagen: **Rechte anzeigen** <br /><br />API-Konstante oder -Wert: `IPC_READ_RIGHTS L"VIEWRIGHTSDATA"`|
|Allgemeiner Name: **Rechte ändern** <br /><br />Richtliniencodierung: **EDITRIGHTSDATA**|Ermöglicht dem Benutzer, die Richtlinie zu ändern, die auf das Dokument angewendet wird. Beinhaltet, das Entfernen des Schutzes einzubeziehen. <br /><br /> Wird von Office-Apps oder Azure Information Protection-Clients nicht unterstützt.|Benutzerdefinierte Office-Rechte: nicht implementiert.<br /><br />Name im klassischen Azure-Portal: **Rechte ändern**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **Rechte bearbeiten (ediyghzdata)**.<br /><br />Name in AD RMS-Vorlagen: **Rechte bearbeiten** <br /><br />API-Konstante oder -Wert: `PC_WRITE_RIGHTS L"EDITRIGHTSDATA"`|
|Allgemeiner Name: **Makros zulassen** <br /><br />Richtliniencodierung: **OBJMODEL**|Aktiviert die Option zum Ausführen von Makros oder anderem programmgesteuertem oder Remotezugriff auf den Inhalt in einem Dokument.|Benutzerdefinierte Office-Rechte: wie die benutzerdefinierte Richtlinienoption **Programmgesteuerten Zugriff zulassen**. Keine Pro-Empfänger-Einstellung.<br /><br />Name im klassischen Azure-Portal: **Makros zulassen**<br /><br />Name in der Bezeichnung Admin Center und Azure-Portal: **Makros zulassen (objmodel)**<br /><br />Name in AD RMS-Vorlagen: **Makros zulassen** <br /><br />API-Konstante oder -Wert: nicht implementiert.|
| | | |

## <a name="rights-included-in-permissions-levels"></a>In Berechtigungsstufen enthaltene Rechte

Einige Anwendungen gruppieren Nutzungsrechte in Berechtigungsstufen, um die Auswahl von Nutzungsrechten zu vereinfachen, die in der Regel zusammen verwendet werden. Diese Berechtigungsstufen unterstützen das Abstrahieren eines Komplexitätsniveaus vor den Benutzern, damit sie rollenbasierte Optionen auswählen können.  Beispiele: **Prüfer** und **Mitautor**. Obwohl diese Optionen Benutzern häufig eine Zusammenfassung der Rechte anzeigen, enthalten sie möglicherweise nicht jede Berechtigung, die in der vorherigen Tabelle aufgelistet wird.

In der folgenden Tabelle finden Sie eine Liste dieser Berechtigungsstufen und eine vollständige Liste der Nutzungsrechte, die sie enthalten. Die Nutzungsrechte sind nach ihren [allgemeinen Namen](#usage-rights-and-descriptions) aufgelistet.

|Berechtigungsstufe|Anwendungen|Enthaltene Nutzungsrechte|
|---------------------|----------------|---------------------------------|
|**Viewer**|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Rechte anzeigen; Antworten [[1]](#footnote-1); Allen Antworten [[1]](#footnote-1); Makros zulassen [[2]](#footnote-2)<br /><br />Hinweis: Verwenden Sie für E-Mails „Prüfer“ statt dieser Berechtigungsstufe, um sicherzustellen, dass eine E-Mail-Antwort als E-Mail-Nachricht und nicht als Anlage empfangen wird. „Prüfer“ ist auch erforderlich, wenn Sie eine E-Mail an eine andere Organisation senden, die den Outlook-Client oder die Outlook-Web-App verwendet. Es ist ebenfalls für Benutzer in Ihrer Organisation erforderlich, die von der Verwendung des Azure Rights Management-Diensts ausgenommen sind, weil Sie [Onboardingsteuerelemente](/powershell/module/aipservice/set-aipserviceonboardingcontrolpolicy) implementiert haben.|
|**Prüfer**|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Rechte anzeigen; Antworten: Allen antworten [[3]](#footnote-3); Weiterleiten [[3]](#footnote-3); Makros zulassen [[2]](#footnote-2)|
|**Mitautor**|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Kopieren; Rechte anzeigen; Makros zulassen; Speichern unter, Exportieren [[4]](#footnote-4); Drucken; Antworten [[3]](#footnote-3); Allen antworten [[3]](#footnote-3); Weiterleiten [[3]](#footnote-3)|
|**Mitbesitzer**|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Kopieren; Rechte anzeigen; Rechte ändern; Makros zulassen; Speichern unter, Exportieren; Drucken; Antworten [[3]](#footnote-3); Allen antworten [[3]](#footnote-3); Weiterleiten [[3]](#footnote-3); Vollzugriff|
| | | |

###### <a name="footnote-1"></a>Fußnote 1

Nicht in der Bezeichnung Admin Center oder Azure-Portal enthalten.

###### <a name="footnote-2"></a>Fußnote 2

Für den Azure Information Protection-Client für Windows ist dieses Recht für die Information Protection Leiste in Office-Apps erforderlich.

###### <a name="footnote-3"></a>Fußnote 3
Gilt nicht für den Azure Information Protection-Client für Windows.

###### <a name="footnote-4"></a>Fußnote 4
Nicht in der Bezeichnung Admin Center, der Azure-Portal oder dem Azure Information Protection Client für Windows enthalten.

## <a name="do-not-forward-option-for-emails"></a>„Nicht weiterleiten“-Option für E-Mails

Exchange-Clients und -Dienste (z.B. der Outlook-Client, Outlook im Web, Exchange-Regeln zum E-Mail-Fluss und DLP-Aktionen für Exchange) haben eine zusätzliche Option zur Verwaltung von Informationsrechten für E-Mails: **Nicht weiterleiten**. 

Obwohl diese Option für Benutzer (und Exchange-Administratoren) so angezeigt wird, als sei sie eine Rights Management-Standardvorlage, die sie auswählen können, ist **Nicht weiterleiten** keine Vorlage. Aus diesem Grund wird sie nicht im Azure-Portal angezeigt, wenn Sie Vorlagen für Azure RMS aufrufen und verwalten. Stattdessen stellt die Option **Nicht weiterleiten** eine Reihe von Berechtigungen dar, die von Benutzern dynamisch auf ihre E-Mail-Empfänger angewendet werden.

Wenn die Option **Nicht weiterleiten** auf eine E-Mail angewendet wird, wird sie verschlüsselt, und Empfänger müssen authentifiziert werden. So können die Empfänger keine E-Mails weiterleiten, drucken oder Teile aus diesen kopieren. Im Outlook-Client ist beispielsweise die Schaltfläche „Weiterleiten“ nicht verfügbar, die Menüoptionen **Speichern unter** und **Drucken** sind nicht verfügbar, und Sie können keine Empfänger in den Feldern **An**, **Cc** und **Bcc** hinzufügen oder ändern.

An eine E-Mail angehängte, ungeschützte [Office-Dokumente](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) unterliegen automatisch denselben Einschränkungen. Für diese Dokumente gelten folgende Nutzungsrechte: **Inhalt bearbeiten, Bearbeiten**; **Speichern**; **Anzeigen, Öffnen, Lesen** und **Makros zulassen**. Wenn für einen Anhang andere Nutzungsrechte gelten sollen oder es sich um ein Office-Dokument handelt, das diesen geerbten Schutz nicht unterstützt, schützen Sie die Datei, bevor Sie sie an eine E-Mail anhängen. So können Sie die nötigen Nutzungsrechte zuweisen. 

### <a name="difference-between-do-not-forward-and-not-granting-the-forward-usage-right"></a>Unterschied zwischen der Option „Nicht weiterleiten“ und dem Nichtgewähren des Nutzungsrechts „Weiterleiten“

Es besteht ein wichtiger Unterschied zwischen dem Anwenden der Option **Nicht weiterleiten** und dem Anwenden einer Vorlage, die das Nutzungsrecht **Weiterleiten** für eine E-Mail nicht gewährt: Bei der Option **Nicht weiterleiten** wird eine dynamische Liste autorisierter Benutzer verwendet, der die vom Benutzer ausgewählten Empfänger der ursprünglichen E-Mail zugrunde liegen. Für die Berechtigungen in der Vorlage gilt hingegen eine statische Liste autorisierter Benutzer, die zuvor vom Administrator festgelegt wurde. Wo liegt der Unterschied? Ein Beispiel sollte das Verständnis vereinfachen: 

Ein Benutzer möchte per E-Mail einige Informationen an bestimmte Personen in der Marketingabteilung senden, die sonst niemand erfahren soll. Sollte er die E-Mail-Nachricht mit einer Vorlage schützen, die die Rechte (Anzeigen, Antworten und Speichern) auf die Marketingabteilung beschränkt?  Oder sollte er die **Nicht weiterleiten**-Option wählen? Beides würde dazu führen, dass die Empfänger die E-Mail nicht weiterleiten können. 

- Wenn er die Vorlage anwendet, können die Empfänger die Informationen noch für andere in der Marketingabteilung freigeben. Ein Empfänger könnte die E-Mail z.B. im Explorer ziehen und auf einem freigegebenen Speicherort oder einem USB-Laufwerk ablegen. Nun können alle Mitarbeiter der Marketingabteilung, die Zugriff auf diesen Speicherort haben (sowie der Besitzer der E-Mail), die Informationen in der E-Mail anzeigen.
 
- Wenn er die **Nicht weiterleiten**-Option angewendet hat, können die Empfänger die Informationen nicht für andere in der Marketingabteilung freigeben, indem sie die E-Mail an einen anderen Speicherort verschieben. In diesem Szenario können nur die ursprünglichen Empfänger (und der E-Mail-Besitzer) die Informationen in der E-Mail anzeigen.

> [!NOTE] 
> Verwenden Sie **Nicht weiterleiten**, wenn es wichtig ist, dass nur die vom Absender ausgewählten Empfänger die Informationen in der E-Mail einsehen. Verwenden Sie eine Vorlage für E-Mails, um die Rechte auf eine Gruppe von Personen zu beschränken, die der Administrator unabhängig von der Empfängerauswahl des Absenders im Voraus festlegt.

## <a name="encrypt-only-option-for-emails"></a>Option "nur verschlüsseln" für e-Mails

Wenn Exchange Online die neuen Funktionen für die Nachrichten Verschlüsselung in Office 365 verwendet, wird eine neue Option zum **verschlüsseln** von e-Mails zur Verfügung gestellt, mit der die Daten ohne zusätzliche Einschränkungen verschlüsselt werden.

Diese Option ist für Mandanten verfügbar, die Exchange Online verwenden und wie folgt ausgewählt werden können:

- **In Outlook im Web**
- **Als weitere Rechte Schutz Option** für eine Nachrichtenfluss Regel
- **Als Office 365 DLP-Aktion**
- In **Outlook** für die Versionen, die in der [Tabelle der unterstützten Versionen für Microsoft 365-apps nach Aktualisierungs Kanal](/officeupdates/update-history-microsoft365-apps-by-date)aufgeführt sind, wenn Sie über [Microsoft 365 apps verfügen, die Azure RMS unterstützen](requirements-applications.md#windows-computers-for-information-rights-management-irm). 

Weitere Informationen zur Option nur verschlüsseln finden Sie in der folgenden Blogbeitrag-Ankündigung des Office-Teams: [Verschlüsseln der Verschlüsselung nur bei der Office 365-Nachrichten Verschlüsselung](https://aka.ms/omefeb2018).

Wenn diese Option aktiviert ist, wird die E-Mail verschlüsselt, und Empfänger müssen authentifiziert werden. Anschließend verfügen die Empfänger über alle Nutzungsrechte außer **Speichern unter, Exportieren** und **Vollzugriff**. Durch diese Kombination von Nutzungsrechten gilt für Empfänger als einzige Einschränkung, dass sie den Schutz nicht entfernen können. Sie können eine E-Mail aber kopieren, ausdrucken und weiterleiten. 

Ebenso übernehmen ungeschützte [Office-Dokumente](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM), die an die E-Mail angehängt sind, standardmäßig die gleichen Berechtigungen. Diese Dokumente sind automatisch geschützt, und sie können von den Empfängern nach dem Herunterladen aus Office-Anwendungen gespeichert, bearbeitet, kopiert und ausgedruckt werden. Wenn ein Empfänger ein Dokument speichert, hat er die Möglichkeit, ihm einen neuen Namen zu geben und sogar ein anderes Format zu verwenden. Zur Auswahl stehen jedoch nur Dateiformate, die den Schutz unterstützten. So ist sichergestellt, dass dieser nicht durch Speichern umgangen wird. Wenn für einen Anhang andere Nutzungsrechte gelten sollen oder es sich um ein Office-Dokument handelt, das diesen geerbten Schutz nicht unterstützt, schützen Sie die Datei, bevor Sie sie an eine E-Mail anhängen. So können Sie die nötigen Nutzungsrechte zuweisen.

Alternativ können Sie diese Vererbung des Schutzes von Dokumenten ändern, indem Sie `Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true` für [Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) angeben. Verwenden Sie diese Konfiguration, wenn Sie den ursprünglichen Schutz für das Dokument nach der Authentifizierung des Benutzers nicht beibehalten müssen. Wenn Empfänger die E-Mail-Nachricht öffnen, wird das Dokument nicht geschützt.

Wenn der ursprüngliche Schutz eines angefügten Dokuments beibehalten werden soll, finden Sie weitere Informationen unter [Sicheres Zusammenarbeiten an Dokumenten mithilfe von Azure Information Protection](secure-collaboration-documents.md).

> [!NOTE]
> Wenn Sie Verweise auf **DecryptAttachmentFromPortal** sehen, beachten Sie, dass dieser Parameter inzwischen für [Set-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/set-irmconfiguration) als veraltet gilt. Sollten Sie den Parameter nicht zuvor festgelegt haben, ist er daher nicht verfügbar.
> 
## <a name="automatically-encrypt-pdf-documents-with-exchange-online"></a>Automatisches Verschlüsseln von PDF-Dokumenten mit Exchange Online

Wenn Exchange Online die neuen Funktionen für die Nachrichten Verschlüsselung von Office 365 verwendet, können Sie ungeschützte PDF-Dokumente automatisch verschlüsseln, wenn Sie an eine verschlüsselte e-Mail angefügt werden. Das Dokument erbt dieselben Berechtigungen wie die der e-Mail-Nachricht. Um diese Konfiguration zu aktivieren, legen Sie **enablepdfencryption $true** mit [Set-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/set-irmconfiguration)fest.

Empfänger, die noch nicht über einen installierten Reader verfügen, der den ISO-Standard für die PDF-Verschlüsselung unterstützt, können einen der in [PDF-Lesern aufgeführten Leser installieren, die Microsoft Information Protection unterstützen](./rms-client/protected-pdf-readers.md). Alternativ können Empfänger das geschützte PDF-Dokument im OMS-Portal lesen.

## <a name="rights-management-issuer-and-rights-management-owner"></a>Rights Management-Aussteller und Rights Management-Besitzer

Wenn ein Dokument oder eine E-Mail mithilfe des Azure Rights Management-Diensts geschützt ist, wird das Konto, das diesen Inhalt schützt, automatisch der Rights Management-Aussteller dieses Inhalts. Dieses Konto wird als **issuer**-Feld in den [Verwendungsprotokollen](log-analyze-usage.md#how-to-interpret-your-usage-logs) protokolliert. 

Dem Rights Management-Aussteller wird immer das Nutzungsrecht „Vollzugriff“ für das Dokument oder die E-Mail gewährt, und darüber hinaus:

- Wenn die Schutzeinstellungen ein Ablaufdatum umfassen, kann der Rights Management-Aussteller das Dokument oder die E-Mail nach diesem Datum immer noch öffnen und bearbeiten.

- Der Rights Management-Aussteller kann stets offline auf das Dokument oder die E-Mail zugreifen.

- Der Rights Management-Aussteller kann ein Dokument immer noch öffnen, nachdem es widerrufen wurde. 

Standardmäßig ist dieses Konto auch der **Rights Management-Besitzer** dieses Inhalts, was der Fall ist, wenn ein Benutzer, der das Dokument oder die E-Mail erstellt hat, den Schutz initiiert. Aber es gibt einige Szenarien, in denen ein Administrator oder Dienst Inhalte im Auftrag von Benutzern schützen kann. Beispiel:

- Ein Administrator schützt viele Dateien auf einer Dateifreigabe auf einmal: Das Administratorkonto in Azure AD schützt die Dokumente für die Benutzer.

- Der Rights Management-Connector schützt Office-Dokumente in einem Windows Server-Ordner: Das Dienstprinzipalkonto in Azure AD, das für den RMS-Connector erstellt wird, schützt die Dokumente für die Benutzer.

In diesen Szenarien kann der Rights Management-Aussteller den Rights Management-Besitzer mithilfe der Azure Information Protection-SDKs oder von PowerShell einem anderen Konto zuweisen. Wenn Sie z.B. das [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile)-PowerShell-Cmdlet mit dem Azure Information Protection-Client verwenden, können Sie den **OwnerEmail**-Parameter angeben, um den Rights Management-Besitzer einem anderen Konto zuzuweisen. 

Wenn der Rights Management-Aussteller im Auftrag von Benutzern schützt, stellt das Zuweisen des Rights Management-Besitzers sicher, dass der ursprüngliche Dokument- oder E-Mail-Besitzer das gleiche Maß an Kontrolle über seinen geschützten Inhalt hat, als hätte er den Schutz selbst initiiert. 

Beispielsweise kann der Benutzer, der das Dokument erstellt hat, es drucken, obwohl es jetzt mit einer Vorlage geschützt ist, die das Nutzungsrecht „Drucken“ nicht enthält. Derselbe Benutzer kann stets unabhängig von der Einstellung für Offlinezugriff oder Ablaufdatum, die in dieser Vorlage konfiguriert sein könnten, auf sein Dokument zugreifen. Da der Rights Management-Besitzer über das Nutzungsrecht „Vollzugriff“ verfügt, kann dieser Benutzer darüber hinaus sein Dokument auch erneut schützen, um weiteren Benutzern Zugriff zu gewähren (an diesem Punkt wird der Benutzer dann sowohl zum Rights Management-Aussteller als auch Rights Management-Besitzer), und dieser Benutzer kann sogar den Schutz entfernen. Allerdings kann nur der Rights Management-Aussteller ein Dokument nachverfolgen und widerrufen.

Der Rights Management-Besitzer für ein Dokument oder eine E-Mail wird im Feld **owner-email** der [Verwendungsprotokolle](log-analyze-usage.md#how-to-interpret-your-usage-logs) protokolliert.

> [!NOTE]
> Der Besitzer der Rights Management ist unabhängig vom Besitzer des Windows-Dateisystems. Sie sind häufig identisch, können jedoch unterschiedlich sein, auch wenn Sie nicht die SDKs oder PowerShell verwenden.
> 
## <a name="rights-management-use-license"></a>Rights Management-Nutzungslizenz

Wenn ein Benutzer ein Dokument oder eine E-Mail öffnet, das/die von Azure Rights Management geschützt wurde, erhält der Benutzer eine Rights Management-Nutzungslizenz für diesen Inhalt. Diese Nutzungslizenz ist ein Zertifikat, das die Nutzungsrechte für das Dokument oder die E-Mail-Nachricht und den Verschlüsselungsschlüssel enthält, der zum Verschlüsseln des Inhalts verwendet wurde. Die Lizenz enthält auch ein ggf. festgelegtes Ablaufdatum und die Gültigkeitsdauer der Nutzungslizenz.

Ein Benutzer muss zum Öffnen des Inhalts zusätzlich zu einer gültigen Nutzungslizenz über ein Rechtekontozertifikat (RAC) verfügen. Dieses Zertifikat wird erteilt, wenn die [Benutzerumgebung](how-does-it-work.md#initializing-the-user-environment) initialisiert wird, und es wird anschließend alle 31 Tage erneuert.

Für die Dauer der Nutzungslizenz wird der Benutzer für den Inhalt nicht erneut authentifiziert oder autorisiert. Dadurch kann der Benutzer das geschützte Dokument oder die e-Mail weiterhin ohne Internetverbindung öffnen. Wenn die Gültigkeitsdauer der Nutzungslizenz abläuft, muss der Benutzer beim nächsten Zugriff auf das geschützte Dokument oder die geschützte E-Mail erneut authentifiziert und autorisiert werden. 

Wenn Dokumente und E-Mail-Nachrichten mithilfe einer Bezeichnung oder Vorlage geschützt werden, die die Schutzeinstellungen definiert, können Sie diese Einstellungen in Ihrer Bezeichnung oder Vorlage ändern, ohne den Inhalt erneut schützen zu müssen. Wenn der Benutzer bereits auf den Inhalt zugegriffen hat, werden die Änderungen wirksam, wenn seine Nutzungslizenz abgelaufen ist. Wenn Benutzer jedoch benutzerdefinierte Berechtigungen (auch bekannt als Ad-hoc-Rechterichtlinie) anwenden, und diese Berechtigungen geändert werden müssen, nachdem das Dokument oder die E-Mail geschützt worden ist, muss dieser Inhalt erneut mit den neuen Berechtigungen geschützt werden. Benutzerdefinierte Berechtigungen für eine E-Mail-Nachricht werden mit der Option „Nicht weiterleiten“ implementiert.

Der Standardwert für die Gültigkeitsdauer der Nutzungslizenz für einen Mandanten beträgt 30 Tage. Sie können diesen Wert mithilfe des PowerShell-Cmdlets [Set-aipservicemaxuselicensevaliditytime](/powershell/module/aipservice/set-aipservicemaxuselicensevaliditytime)konfigurieren. Sie können mithilfe einer Bezeichnung oder Vorlage eine restriktivere Einstellung dafür konfigurieren, wann Schutz angewendet wird:

- Wenn Sie eine Bezeichnung oder Vorlage im Azure-Portal konfigurieren, wird der Wert für die Gültigkeitsdauer der Nutzungslizenz von der **Einstellung „Offlinezugriff zulassen“** übernommen. 
    
    Weitere Informationen und Anleitungen zum Konfigurieren dieser Einstellung im Azure-Portal finden Sie in der Tabelle [Informationen zu Schutzeinstellungen](configure-policy-protection.md#information-about-the-protection-settings) der Anleitung zum Konfigurieren einer Bezeichnung für Azure Rights Management.

- Wenn Sie eine Vorlage mithilfe von PowerShell konfigurieren, verwendet die Gültigkeitsdauer der Nutzungslizenz ihren Wert aus dem *licensevalidityduration* -Parameter in den Cmdlets " [Set-aipservicetemplateproperty](/powershell/module/aipservice/set-aipservicetemplateproperty) " und " [Add-aipservicetemplate](/powershell/module/aipservice/add-aipservicetemplate) ".
    
    Weitere Informationen und Anleitungen zum Konfigurieren dieser Einstellung mithilfe von PowerShell finden Sie in der Hilfe zu dem jeweiligen Cmdlet.

## <a name="rights-included-in-the-default-templates"></a>In den Standardvorlagen enthaltene Rechte

**Relevant für**: nur AIP Classic Client

Die folgende Tabelle enthält die Nutzungsrechte, die enthalten sind, wenn die Standardvorlagen erstellt werden. Die Nutzungsrechte sind nach ihren [allgemeinen Namen](#usage-rights-and-descriptions) aufgelistet.

Diese Standardvorlagen werden beim Erwerb Ihres Abonnements erstellt, und die Namen und Nutzungsrechte können im Azure-Portal und mit [PowerShell](/powershell/module/aipservice/set-aipservicetemplateproperty) [geändert](configure-policy-templates.md) werden. 

|Anzeigename der Vorlage|Nutzungsrechte vom 6. Oktober 2017 bis zum aktuellen Datum|Nutzungsrechte vor dem 6. Oktober 2017|
|----------------|--------------------|----------|
|**\<*organization name> -Nur vertrauliche Ansicht*** <br /><br />oder<br /><br /> **_Streng vertraulich \ alle Mitarbeiter_**|Anzeigen, Öffnen, Lesen; Kopieren; Rechte anzeigen; Makros zulassen; Drucken; Weiterleiten; Antworten; Allen antworten; Speichern; Inhalt bearbeiten, Bearbeiten|Anzeigen, Öffnen, Lesen|
|**\<*organization name>-Vertraulich*** <br /><br />oder <br /><br />**_Vertraulich \ alle Mitarbeiter_**|Anzeigen, Öffnen, Lesen; Speichern unter; Kopieren; Rechte anzeigen; Rechte ändern; Makros zulassen; Drucken; Weiterleiten; Antworten; Allen antworten; Speichern; Inhalt bearbeiten, Bearbeiten; Vollzugriff|Anzeigen, Öffnen, Lesen; Speichern unter; Inhalt bearbeiten, Bearbeiten; Rechte anzeigen; Makros zulassen; Weiterleiten; Antworten; Allen antworten|
| | | |

## <a name="see-also"></a>Weitere Informationen

- [Einschränken des Zugriffs auf Inhalte mithilfe von Vertraulichkeits Bezeichnungen zum Anwenden der Verschlüsselung](/microsoft-365/compliance/encryption-sensitivity-labels)
- [Configuring super users for Azure Information Protection and discovery services or data recovery](configure-super-users.md) (Konfigurieren von Administratoren für Azure Information Protection und Ermittlungsdienste oder Wiederherstellung von Daten)
