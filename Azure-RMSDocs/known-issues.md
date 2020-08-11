---
title: Bekannte Probleme-Azure Information Protection
description: Suchen Sie nach bekannten Problemen und Einschränkungen für Azure Information Protection, und Durchsuchen Sie Sie.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/10/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 7c55faf0138e007ed1a8877ebb60cf01551c4dd3
ms.sourcegitcommit: e6b594b8d15f81884b0999f5c0009386aef02cc3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2020
ms.locfileid: "88073736"
---
# <a name="known-issues---azure-information-protection"></a>Bekannte Probleme-Azure Information Protection

Verwenden Sie die Listen und Tabellen unten, um Details zu bekannten Problemen und Einschränkungen im Zusammenhang mit Azure Information Protection Funktionen zu finden.

> [!NOTE]
> Dieser Artikel bezieht sich auf bekannte Probleme sowohl bei den klassischen als auch bei der vereinheitlichten Bezeichnung von Clients. Wenn Sie nicht sicher sind, was der Unterschied zwischen diesen Clients ist, Siehe [FAQs](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients).

<!--removed from this page
## HYOK known issues

HYOK has the following known issues:

- [Supported Microsoft Office versions](#supported-microsoft-office-versions)
- [Email recommendations for Office 365 and other online services](#email-recommendations-for-office-365-and-other-online-services)

### Supported Microsoft Office versions

HYOK for the Azure Information Protection classic client does not support versions of Office earlier than Office 2013.

### Email recommendations for Office 365 and other online services

We recommend that you do not use HYOK protection for emails in Office 365 and other online services.

Office 365 and other online services are not be able to decrypt HYOK-protected documents and emails. This limitation includes HYOK-protected documents and emails that have been protected with the Rights Management connector, and prevents these services from inspecting the content and taking action on them.

This loss of functionality for HYOK-protected email includes malware scanners, data loss prevention (DLP) solutions, mail routing rules, journaling, eDiscovery, archiving solutions, and Exchange ActiveSync.

Additionally, users may not understand why some devices cannot open their HYOK-protected emails, resulting in more calls to your help desk.
-->

## <a name="client-support-for-container-files-such-as-zip-files"></a>Client Unterstützung für Container Dateien, z. b. zip-Dateien

Containerdateien sind Dateien, die andere Dateien enthalten. Ein typisches Beispiel sind ZIP-Dateien, die komprimierte Dateien enthalten. Weitere Beispiele sind RAR-, .7z- und MSG-Dateien sowie PDF-Dokumente, die Anlagen enthalten.

Sie können diese Containerdateien klassifizieren und schützen, jedoch werden die Klassifizierung und der Schutz nicht auf jede Datei im Container angewendet.

Bei einer Containerdatei, die klassifizierte und geschützte Dateien enthält, müssen Sie zuerst die Dateien extrahieren, um die Einstellungen für die Klassifizierung oder den Schutz zu ändern. Es ist jedoch auch möglich, den Schutz für alle Dateien in unterstützten Containerdateien mit dem Cmdlet [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) zu entfernen.

Mit dem Azure Information Protection-Viewer können keine Anlagen in einem geschützten PDF-Dokument geöffnet werden. In diesem Szenario sind die Anlagen bei geöffnetem Dokument im Viewer nicht sichtbar.

Weitere Informationen finden Sie unter [Administrator Handbuch: vom Azure Information Protection-Client unterstützte Dateitypen](rms-client/client-admin-guide-file-types.md).

## <a name="powershell-support-for-the-azure-information-protection-client"></a>PowerShell-Unterstützung für den Azure Information Protection-Client

Die aktuelle Version des PowerShell-Moduls **azureinformationprotection** , das mit dem Azure Information Protection-Client installiert wird, weist die folgenden bekannten Probleme auf:

- **Persönliche Outlook-Ordner (* PST *-Dateien) * *. Der systemeigene Schutz von *PST* -Dateien wird mit dem **azureinformationprotection** -Modul nicht unterstützt.

- Von **Outlook geschützte e-Mail-Nachrichten *(rpmsg* -Dateien)**. Das Aufheben des Schutzes von durch Outlook geschützten e-Mail-Nachrichten wird nur vom **azureinformationprotection** -Modul unterstützt, wenn Sie sich in einem persönlichen Outlook-Ordner *(PST* -Datei)

    Das Aufheben von e-Mail-Nachrichten außerhalb einer *PST* -Datei wird nicht unterstützt.

Weitere Informationen finden Sie unter [Administrator Handbuch: Verwenden von PowerShell mit dem Azure Information Protection-Client](rms-client/client-admin-guide-powershell.md).

<!-- removed from this page
## Protection-only mode known issues

The following known issues apply for [Protection-only mode for the Azure Information Protection client](rms-client/client-protection-only-mode.md):

- In Office apps, the Azure Information Protection bar is not shown. When you click **Protect** > **Show Bar**, this menu option is unavailable.

- When you use the **Classify and protect - Azure Information Protection** dialog box with the File Explorer, labels for classification are not shown. Instead, you have an option select a Rights Management (RMS) template.
-->

## <a name="aip-known-issues-in-office-applications"></a>In Office-Anwendungen bekannte AIP-Probleme

|Funktion  |Bekannte Probleme  |
|---------|---------|
|**Mehrere Versionen von Office**    | Die Azure Information Protection Clients, einschließlich der klassischen und einheitlichen Bezeichnung, unterstützen nicht mehrere Office-Versionen auf demselben Computer oder das Wechseln von Benutzerkonten in Office.       |
|**Mehrere anzeigen** |Wenn Sie mehrere anzeigen verwenden und eine Office-Anwendung geöffnet ist: </br></br>-Bei Ihren Office-Apps können Leistungsprobleme auftreten.</br>-Die Azure Information Protection Leiste kann in der Mitte des Office-Bildschirms auf einem oder beiden anzeigen angezeigt werden. </br></br>Um eine konsistente Leistung sicherzustellen und die Leiste am richtigen Speicherort verbleibt, öffnen Sie das Dialogfeld Optionen für Ihre Office-Anwendung, und wählen Sie unter **Allgemein** die **Option** **für Kompatibilität optimieren** anstelle von **optimieren aus, um das beste Aussehen** zu erzielen.    |
|**Unterstützung von "unm" in Office 2016**| Die [drmencryptproperty](https://docs.microsoft.com/deployoffice/security/protect-sensitive-messages-and-documents-by-using-irm-in-office#office-2016-irm-registry-key-options) -Registrierungs Einstellung, die die metadatenverschlüsselung in Office 2016 steuert, wird für Azure Information Protection Bezeichnungen nicht unterstützt.|
|**Inhalts Markierungen in Word**    | Azure Information Protection Inhalts [Markierungen](configure-policy-markings.md) werden möglicherweise in den Microsoft Word-Fußzeilen ausgeblendet, wenn der Fußzeile auch eine Tabelle enthält. Weitere Informationen finden Sie unter [Wenn visuelle Kennzeichnungen angewendet werden](configure-policy-markings.md#when-visual-markings-are-applied). |
|**An e-Mails angefügte Dateien** |Aufgrund einer Einschränkung in den jüngsten Windows-Updates, wenn [Microsoft Outlook durch Azure Rights Management geschützt ist](office-apps-services-support.md), können Dateien, die an e-Mails angefügt sind, nach dem Öffnen der Datei gesperrt werden. |
|**Nachrichten Zusammenführung**    |  Das Feature für die Office-e- [Mail](https://support.office.com/article/use-mail-merge-for-bulk-email-letters-labels-and-envelopes-f488ed5b-b849-4c11-9cff-932c49474705) -Zusammenführung wird von keiner Azure Information Protection Funktion unterstützt       |
| | |

<!-- removing b/c this is relevant for classic only. for UL, labels are configured in m365. so this is basically irrelevant for us.
## Known issues in labeling

Depending on your policy rule size limit, configuring more than 200 users or user groups for each label may cause unexpected errors. 
-->

## <a name="known-issues-in-policies"></a>Bekannte Probleme in Richtlinien

Das Veröffentlichen von Richtlinien kann bis zu 24 Stunden dauern.

## <a name="known-issues-in-the-aip-client"></a>Bekannte Probleme im AIP-Client

- **Maximale Dateigröße. Dateien** mit mehr als 2 GB werden für den Schutz unterstützt, aber nicht für die Entschlüsselung.

- **AIP-Viewer.** Der AIP-Viewer zeigt Bilder im Hochformat an, und einige große, quer Ansichts Bilder können scheinbar gestreckt werden.

    Beispielsweise wird ein ursprüngliches Bild unten auf der linken Seite mit einer gestreckten Hochformat Version im AIP-Viewer auf der rechten Seite angezeigt. 
    
    :::image type="content" source="media/client-viewer-stretched-images.PNG" alt-text="Bild im Client-Viewer gestreckten":::
    
    Weitere Informationen finden Sie unter

    - [**Klassischer Client**: Anzeigen geschützter Dateien mit dem Azure Information Protection Viewer](rms-client/client-view-use-files.md)
    - [**Einheitlicher**Bezeichnungs Client: geschützte Dateien mit dem Azure Information Protection Viewer anzeigen](rms-client/clientv2-view-use-files.md)


## <a name="more-information"></a>Weitere Informationen

Die folgenden zusätzlichen Artikel können hilfreich sein, um Fragen zu bekannten Problemen in Azure Information Protection zu beantworten:

- [Häufig gestellte Fragen zu Azure Information Protection](faqs.md)
- [Häufig gestellte Fragen zum Schutz von Daten in Azure Information Protection](faqs-rms.md)
- [Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen in Azure Information Protection](faqs-infoprotect.md)
- [Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android](rms-client/mobile-app-faq.md)

