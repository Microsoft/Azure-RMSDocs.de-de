---
title: 'Bekannte Probleme: Azure Information Protection'
description: Suchen Sie nach bekannten Problemen und Einschränkungen für Azure Information Protection, und Durchsuchen Sie Sie.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 12/29/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 1ee51978452a4f420478f2938020578166f49335
ms.sourcegitcommit: b32c16e41ba36167b5a3058b56a73183bdd4306d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/29/2020
ms.locfileid: "97805987"
---
# <a name="known-issues---azure-information-protection"></a>Bekannte Probleme: Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Verwenden Sie die Listen und Tabellen unten, um Details zu bekannten Problemen und Einschränkungen im Zusammenhang mit Azure Information Protection Funktionen zu finden.

## <a name="client-support-for-container-files-such-as-zip-files"></a>Client Unterstützung für Container Dateien, z. b. zip-Dateien

Containerdateien sind Dateien, die andere Dateien enthalten. Ein typisches Beispiel sind ZIP-Dateien, die komprimierte Dateien enthalten. Weitere Beispiele sind RAR-, .7z- und MSG-Dateien sowie PDF-Dokumente, die Anlagen enthalten.

Sie können diese Containerdateien klassifizieren und schützen, jedoch werden die Klassifizierung und der Schutz nicht auf jede Datei im Container angewendet.

Bei einer Containerdatei, die klassifizierte und geschützte Dateien enthält, müssen Sie zuerst die Dateien extrahieren, um die Einstellungen für die Klassifizierung oder den Schutz zu ändern. Es ist jedoch auch möglich, den Schutz für alle Dateien in unterstützten Containerdateien mit dem Cmdlet [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) zu entfernen.

Mit dem Azure Information Protection-Viewer können keine Anlagen in einem geschützten PDF-Dokument geöffnet werden. In diesem Szenario sind die Anlagen bei geöffnetem Dokument im Viewer nicht sichtbar.

Weitere Informationen finden Sie unter [Administrator Handbuch: vom Azure Information Protection-Client unterstützte Dateitypen](rms-client/client-admin-guide-file-types.md).

## <a name="known-issues-for-aip-and-exploit-protection"></a>Bekannte Probleme bei AIP und Exploit Protection

Der Azure Information Protection-Client wird auf Computern mit .NET 2 oder 3 nicht unterstützt, auf denen der [Exploit-Schutz](/windows/security/threat-protection/microsoft-defender-atp/enable-exploit-protection) aktiviert ist, und bewirkt, dass Office-Apps unerwartet Verhalten.

In solchen Fällen empfiehlt es sich, die .NET-Version zu aktualisieren. Weitere Informationen finden Sie unter [Microsoft .NET Framework-Anforderungen](rms-client/reqs-ul-client.md#microsoft-net-framework-requirements).

Wenn Sie die .NET-Version 2 oder 3 beibehalten müssen, stellen Sie sicher, dass Sie den Exploit-Schutz vor der Installation von AIP deaktivieren. 

Führen Sie Folgendes aus, um den Exploit-Schutz über PowerShell zu deaktivieren:

```PowerShell
Set-ProcessMitigation -Name "OUTLOOK.EXE" -Disable EnableExportAddressFilterPlus, EnableExportAddressFilter, EnableImportAddressFilter
```

## <a name="powershell-support-for-the-azure-information-protection-client"></a>PowerShell-Unterstützung für den Azure Information Protection-Client

Die aktuelle Version des PowerShell-Moduls **azureinformationprotection** , das mit dem Azure Information Protection-Client installiert wird, weist die folgenden bekannten Probleme auf:

- **Persönliche Outlook-Ordner (* PST *-Dateien) * *. Der systemeigene Schutz von *PST* -Dateien wird mit dem **azureinformationprotection** -Modul nicht unterstützt.

- Von **Outlook geschützte e-Mail-Nachrichten *(rpmsg* -Dateien)**. Das Aufheben des Schutzes von durch Outlook geschützten e-Mail-Nachrichten wird nur vom **azureinformationprotection** -Modul unterstützt, wenn Sie sich in einem persönlichen Outlook-Ordner *(PST* -Datei)

    Das Aufheben von e-Mail-Nachrichten außerhalb einer *PST* -Datei wird nicht unterstützt.

Weitere Informationen finden Sie unter [Administrator Handbuch: Verwenden von PowerShell mit dem Azure Information Protection-Client](rms-client/client-admin-guide-powershell.md).

## <a name="aip-known-issues-in-office-applications"></a>In Office-Anwendungen bekannte AIP-Probleme

|Funktion  |Bekannte Probleme  |
|---------|---------|
|**Mehrere Versionen von Office**    | Die Azure Information Protection-Clients (sowohl der klassische als auch der Client für einheitliche Bezeichnungen) unterstützen nicht mehrere Office-Versionen auf ein und demselben Computer. Auch der Wechsel von Benutzerkonten in Office wird nicht unterstützt.       |
|**Mehrere anzeigen** |Wenn Sie mehrere anzeigen verwenden und eine Office-Anwendung geöffnet ist: <br><br>-Bei Ihren Office-Apps können Leistungsprobleme auftreten.<br>-Die Azure Information Protection Leiste kann in der Mitte des Office-Bildschirms auf einem oder beiden anzeigen angezeigt werden. <br><br>Um eine konsistente Leistung sicherzustellen und die Leiste am richtigen Speicherort verbleibt, öffnen Sie das Dialogfeld Optionen für Ihre Office-Anwendung, und wählen Sie unter **Allgemein** die **Option** **für Kompatibilität optimieren** anstelle von **optimieren aus, um das beste Aussehen** zu erzielen.    |
|**Unterstützung von "unm" in Office 2016**| Die [drmencryptproperty](/deployoffice/security/protect-sensitive-messages-and-documents-by-using-irm-in-office#office-2016-irm-registry-key-options) -Registrierungs Einstellung, die die metadatenverschlüsselung in Office 2016 steuert, wird für Azure Information Protection Bezeichnungen nicht unterstützt.|
|**Inhalts Markierungen in Word**    | AIP- [Inhalts Markierungen](configure-policy-markings.md) in den Kopf-oder Fußzeilen von Microsoft Word können Offset oder fehlerhaft sein oder vollständig ausgeblendet werden, wenn dieselbe Kopfzeile oder Fußzeile auch eine Tabelle enthält.<br><br>Weitere Informationen finden Sie unter [Wenn visuelle Kennzeichnungen angewendet werden](configure-policy-markings.md#when-visual-markings-are-applied). |
|**An e-Mails angefügte Dateien** |Aufgrund einer Einschränkung in den jüngsten Windows-Updates, wenn [Microsoft Outlook durch Azure Rights Management geschützt ist](office-apps-services-support.md), können Dateien, die an e-Mails angefügt sind, nach dem Öffnen der Datei gesperrt werden. |
|**Nachrichten Zusammenführung**    |  Das Office-Feature [Seriendruck](https://support.office.com/article/use-mail-merge-for-bulk-email-letters-labels-and-envelopes-f488ed5b-b849-4c11-9cff-932c49474705) wird mit keinem Azure Information Protection-Feature unterstützt.       |
| **S/MIME-e-Mails** | Das Öffnen von S/MIME-e-Mails im Lesebereich von Outlook kann zu Leistungsproblemen führen. <br><br>Um Leistungsprobleme bei S/MIME-e-Mails zu vermeiden, aktivieren Sie die erweiterte [**outlookskipsmimeonleseringpaneenable**](rms-client/clientv2-admin-guide-customizations.md#prevent-outlook-performance-issues-with-smime-emails) -Eigenschaft. <br><br>**Hinweis**: durch Aktivieren dieser Eigenschaft wird verhindert, dass die AIP-Leiste oder die e-Mail-Klassifizierung im Lesebereich von Outlook angezeigt wird. |
|**Option zum Senden an den Datei-Explorer** |Wenn Sie im Datei-Explorer mit der rechten Maustaste auf eine Datei klicken und **an > e-Mail-Empfänger senden** auswählen, wird die AIP-Symbolleiste möglicherweise nicht in der Outlook-Nachricht angezeigt, die mit der angefügten Datei geöffnet wird. <br><br>Wenn dies der Fall ist und Sie die AIP-Symbolleisten Optionen verwenden müssen, starten Sie Ihre e-Mail in Outlook, und navigieren Sie dann zu der Datei, die Sie senden möchten, und fügen Sie Sie an.|
| | |

## <a name="known-issues-in-policies"></a>Bekannte Probleme in Richtlinien

Das Veröffentlichen von Richtlinien kann bis zu 24 Stunden dauern.

## <a name="maximum-file-sizes"></a>Maximale Dateigröße

Dateien mit mehr als 2 GB werden für den Schutz unterstützt, aber nicht für die Entschlüsselung.

## <a name="known-issues-for-the-aip-viewer"></a>Bekannte Probleme für den AIP-Viewer

Der AIP-Viewer zeigt Bilder im Hochformat an, und einige große, quer Ansichts Bilder können scheinbar gestreckt werden.

Beispielsweise wird ein ursprüngliches Bild unten auf der linken Seite mit einer gestreckten Hochformat Version im AIP-Viewer auf der rechten Seite angezeigt. 
    
:::image type="content" source="media/client-viewer-stretched-images.PNG" alt-text="Bild im Client-Viewer gestreckten":::
    
Weitere Informationen finden Sie unter

- [**Klassischer Client**: Anzeigen geschützter Dateien mit dem Azure Information Protection Viewer](rms-client/client-view-use-files.md)
- [**Einheitlicher** Bezeichnungs Client: geschützte Dateien mit dem Azure Information Protection Viewer anzeigen](rms-client/clientv2-view-use-files.md)

## <a name="known-issues-for-track-and-revoke-features-public-preview"></a>Bekannte Probleme beim Nachverfolgen und widerrufen von Features (öffentliche Vorschau)

Das Nachverfolgen und widerrufen des Dokument Zugriffs mithilfe des Unified-bezeichungsclients hat die folgenden bekannten Probleme:

- [Mehrere Anlagen in einer geschützten e-Mail](#multiple-attachments-in-a-protected-email)
- [Dokumente, die über SharePoint aufgerufen werden](#documents-accessed-via-sharepoint)

Weitere Informationen finden Sie unter [Administrator Handbuch: nachverfolgen und widerrufen des Dokument Zugriffs mit Azure Information Protection](rms-client/track-and-revoke-admin.md) und [Benutzerhandbuch: widerrufen des Zugriffs auf Dokumente mit Azure Information Protection](rms-client/revoke-access-user.md).

#### <a name="multiple-attachments-in-a-protected-email"></a>Mehrere Anlagen in einer geschützten e-Mail

Wenn Sie mehrere Dokumente an eine e-Mail anfügen und dann die e-Mail schützen und senden, erhält jede der Anlagen denselben Wert für "contentid". 

Dieser contentid-Wert wird nur mit der ersten geöffneten Datei zurückgegeben. Beim Suchen nach den anderen Anlagen wird nicht der für die Erfassung von Überwachungsdaten erforderliche contentid-Wert zurückgegeben.      

Außerdem wird durch das Aufheben des Zugriffs für eine der Anhänge der Zugriff für die anderen Anlagen in derselben geschützten e-Mail aufgehoben.

#### <a name="documents-accessed-via-sharepoint"></a>Dokumente, die über SharePoint aufgerufen werden
    
- Geschützte Dokumente, die in SharePoint hochgeladen werden, verlieren ihren **contentid** -Wert, und der Zugriff kann nicht nachverfolgt oder widerrufen werden.

- Wenn ein Benutzer die Datei von SharePoint herunterlädt und von Ihrem lokalen Computer aus darauf zugreift, wird eine neue **contentid** auf das Dokument angewendet, wenn Sie Sie lokal öffnen. 
    
    Die Verwendung des ursprünglichen **contentid** -Werts zum Nachverfolgen von Daten umfasst keinen Zugriff auf die heruntergeladene Datei des Benutzers. Außerdem wird durch das Aufheben des Zugriffs auf Grundlage des ursprünglichen **contentid** -Werts der Zugriff für die heruntergeladenen Dateien nicht widerrufen.

    In solchen Fällen können Administratoren die heruntergeladenen Dateien mithilfe von PowerShell ausfindig machen, um die neuen **contentid** -Werte zum Nachverfolgen oder widerrufen des Zugriffs zu finden.

### <a name="knowns-issues-for-the-aip-client-and-onedrive"></a>Probleme mit dem AIP-Client und onedrive

Wenn Sie Dokumente, die in onedrive gespeichert sind und eine Vertraulichkeits Bezeichnung angewendet haben, und ein Administrator die Bezeichnung in der Beschriftungs Richtlinie so ändert, dass Schutz hinzugefügt wird, wird der neu angewendete Schutz nicht automatisch auf das bezeichnete Dokument angewendet. 

In solchen Fällen müssen Sie das Dokument manuell neu bezeichnen, um den Schutz nach Bedarf anzuwenden.
## <a name="aip-for-windows-and-office-versions-in-extended-support"></a>AIP für Windows und Office-Versionen in erweiterter Unterstützung

- Die [**Erweiterte Unterstützung von Windows 7 endete am 14. Januar 2020**](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet). 

    Wir empfehlen Ihnen dringend, ein Upgrade auf eine neuere Version von Windows 10 durchzuführen. 

    Wenn Sie jedoch über erweiterte Sicherheits Updates (ESU) und einen Supportvertrag verfügen, steht die AIP-Unterstützung zur Verfügung, um Ihre Windows 7-Systeme weiterhin sicher zu halten.

    Weitere Informationen erhalten Sie von Ihrem Support Kontakt.

- [**Der erweiterte Support von Office 2010 endete am 13. Oktober 2020**](https://support.microsoft.com/lifecycle/search?alpha=office%202010). 

    Diese Unterstützung wird nicht verlängert, und ESU wird nicht für Office 2010 angeboten. 

    Wir empfehlen Ihnen dringend, ein Upgrade auf eine neuere Version von Office 365 durchzuführen. 
    
    Weitere Informationen erhalten Sie von Ihrem Support Kontakt.

## <a name="aip-based-conditional-access-policies"></a>Richtlinien für den AIP-basierten bedingten Zugriff

Externe Benutzer, die durch [Richtlinien für den bedingten Zugriff](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) geschützte Inhalte empfangen, müssen ein Gastbenutzer Konto (Azure AD) für die B2B-Zusammenarbeit (Business-to-Business) Azure Active Directory, um den Inhalt anzuzeigen.

Obwohl Sie externe Benutzer zum Aktivieren eines Gastbenutzer Kontos einladen können, sodass Sie sich authentifizieren und die Anforderungen für den bedingten Zugriff erfüllen können, kann es schwierig sein, sicherzustellen, dass dies für alle externen Benutzer erforderlich ist.

Es wird empfohlen, Richtlinien für den AIP-basierten bedingten Zugriff nur für Ihre internen Benutzer zu aktivieren.

**Richtlinien für den bedingten Zugriff für AIP nur für interne Benutzer aktivieren**:

1.  Navigieren Sie im Azure-Portal zum Blatt für den **bedingten Zugriff** , und wählen Sie die Richtlinie für bedingten Zugriff aus, die Sie ändern möchten. 
2.  Wählen Sie unter **Zuweisungen** die Option **Benutzer und Gruppen** aus, und wählen Sie dann **alle Benutzer** aus. Stellen Sie sicher, dass die Option **alle Gäste und externe Benutzer** *nicht* ausgewählt ist.
3.  Speichern Sie die Änderungen. 
 
Sie können die Zertifizierungsstelle in Azure Information Protection auch vollständig deaktivieren, wenn die Funktionalität für Ihre Organisation nicht erforderlich ist, um dieses potenzielle Problem zu vermeiden. 

Weitere Informationen finden Sie in der [Dokumentation zu bedingtem Zugriff](/azure/active-directory/conditional-access/concept-conditional-access-users-groups).

## <a name="more-information"></a>Weitere Informationen

Die folgenden zusätzlichen Artikel können hilfreich sein, um Fragen zu bekannten Problemen in Azure Information Protection zu beantworten:

- [Häufig gestellte Fragen zu Azure Information Protection](faqs.md)
- [Häufig gestellte Fragen zum Schutz von Daten in Azure Information Protection](faqs-rms.md)
- [Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen in Azure Information Protection](faqs-infoprotect.md)
- [Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android](rms-client/mobile-app-faq.md)