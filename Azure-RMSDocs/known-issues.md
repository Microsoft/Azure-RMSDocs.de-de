---
title: 'Bekannte Probleme: Azure Information Protection'
description: Suchen Sie nach bekannten Problemen und Einschränkungen für Azure Information Protection, und Durchsuchen Sie Sie.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/16/2021
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 220b1e7ffec1f1bd4332058c9320241106de2e1d
ms.sourcegitcommit: 99f1a1ab40eea7802e6c4f98724958409ee779ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2021
ms.locfileid: "103558154"
---
# <a name="known-issues---azure-information-protection"></a>Bekannte Probleme: Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Verwenden Sie die Listen und Tabellen unten, um Details zu bekannten Problemen und Einschränkungen im Zusammenhang mit Azure Information Protection Funktionen zu finden.

## <a name="third-party-digital-signing-apps"></a>Drittanbieter-Apps für die digitale Signierung

Mit Azure Information Protection können Dateien, die digital signiert sind, nicht geschützt oder entschlüsselt werden.

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
|**Mehrere Versionen von Office <br> <br> mehrere Office-Konten**    | Die Azure Information Protection Clients, einschließlich der klassischen und einheitlichen Bezeichnung, unterstützen Folgendes nicht:  <br><br>-Mehrere Versionen von Office auf demselben Computer <br>-Mehrere Office-Konten oder Benutzerkonten in Office wechseln <br>-Freigegebene Postfächer     |
|**Mehrere anzeigen** |Wenn Sie mehrere anzeigen verwenden und eine Office-Anwendung geöffnet ist: <br><br>-Bei Ihren Office-Apps können Leistungsprobleme auftreten.<br>-Die Azure Information Protection Leiste kann in der Mitte des Office-Bildschirms auf einem oder beiden anzeigen angezeigt werden. <br><br>Um eine konsistente Leistung sicherzustellen und die Leiste am richtigen Speicherort verbleibt, öffnen Sie das Dialogfeld Optionen für Ihre Office-Anwendung, und wählen Sie unter **Allgemein** die **Option** **für Kompatibilität optimieren** anstelle von **optimieren aus, um das beste Aussehen** zu erzielen.    |
|**Unterstützung von "unm" in Office 2016**| Die [drmencryptproperty](/deployoffice/security/protect-sensitive-messages-and-documents-by-using-irm-in-office#office-2016-irm-registry-key-options) -Registrierungs Einstellung, die die metadatenverschlüsselung in Office 2016 steuert, wird für Azure Information Protection Bezeichnungen nicht unterstützt.|
|**Zugriff auf das Outlook-Objektmodell** | -Die " [prompyomaddressbookaccess](/outlook/troubleshoot/security/information-about-email-security-settings#configure-a-prompt-when-a-program-accesses-an-address-book-by-using-the-outlook-object-model) "-Registrierungs Einstellung, die die Eingabe Aufforderungen steuert, die beim Zugriff auf Adressbücher über das Outlook-Objektmodell angezeigt werden, wird mit Azure Information Protection Bezeichnungen nicht unterstützt. <br><br>-Die [promptomaddressinformationaccess](/outlook/troubleshoot/security/information-about-email-security-settings#configure-a-prompt-when-a-program-reads-address-information-by-using-the-outlook-object-model) -Registrierungs Einstellung, die die Eingabe Aufforderungen steuert, die angezeigt werden, wenn ein Programm Adressinformationen liest, wird für Azure Information Protection Bezeichnungen nicht unterstützt.|
|**Inhalts Markierungen in Word**    | AIP- [Inhalts Markierungen](configure-policy-markings.md) in den Kopf-oder Fußzeilen von Microsoft Word können Offset oder fehlerhaft sein oder vollständig ausgeblendet werden, wenn dieselbe Kopfzeile oder Fußzeile auch eine Tabelle enthält.<br><br>Weitere Informationen finden Sie unter [Wenn visuelle Kennzeichnungen angewendet werden](configure-policy-markings.md#when-visual-markings-are-applied). |
|**An e-Mails angefügte Dateien** |Aufgrund einer Einschränkung in den jüngsten Windows-Updates, wenn [Microsoft Outlook durch Azure Rights Management geschützt ist](office-apps-services-support.md), können Dateien, die an e-Mails angefügt sind, nach dem Öffnen der Datei gesperrt werden. |
|**Nachrichten Zusammenführung**    |  Das Office-Feature [Seriendruck](https://support.office.com/article/use-mail-merge-for-bulk-email-letters-labels-and-envelopes-f488ed5b-b849-4c11-9cff-932c49474705) wird mit keinem Azure Information Protection-Feature unterstützt.       |
| **S/MIME-e-Mails** | Das Öffnen von S/MIME-e-Mails im Lesebereich von Outlook kann zu Leistungsproblemen führen. <br><br>Um Leistungsprobleme bei S/MIME-e-Mails zu vermeiden, aktivieren Sie die erweiterte [**outlookskipsmimeonleseringpaneenable**](rms-client/clientv2-admin-guide-customizations.md#prevent-outlook-performance-issues-with-smime-emails) -Eigenschaft. <br><br>**Hinweis**: durch Aktivieren dieser Eigenschaft wird verhindert, dass die AIP-Leiste oder die e-Mail-Klassifizierung im Lesebereich von Outlook angezeigt wird. |
|**Option zum Senden an den Datei-Explorer** |Wenn Sie im Datei-Explorer mit der rechten Maustaste auf eine Datei klicken und **an > e-Mail-Empfänger senden** auswählen, wird die AIP-Symbolleiste möglicherweise nicht in der Outlook-Nachricht angezeigt, die mit der angefügten Datei geöffnet wird. <br><br>Wenn dies der Fall ist und Sie die AIP-Symbolleisten Optionen verwenden müssen, starten Sie Ihre e-Mail in Outlook, und navigieren Sie dann zu der Datei, die Sie senden möchten, und fügen Sie Sie an.|
|**Zusammenstellung** |Die Unterstützung von Co-Authoring wird durch eine [dedizierte Installation](rms-client/unifiedlabelingclient-version-release-history.md#version-210460-for-co-authoring-public-preview) des Azure Information Protection Clients bereitgestellt und ist zurzeit als öffentliche Vorschauversion verfügbar. <br><br>Weitere Informationen finden Sie unter [bekannte Probleme bei der gemeinsamen Dokument Erstellung (Public Preview)](#known-issues-for-co-authoring-public-preview). |
| | |

### <a name="known-issues-for-co-authoring-public-preview"></a>Bekannte Probleme bei der gemeinsamen Erstellung (Public Preview)

- [Nur in Testumgebungen verwenden](#use-in-testing-environments-only)
- [Unterstützte Versionen für die gemeinsamen Erstellung und Vertraulichkeits Bezeichnungen](#supported-versions-for-co-authoring-and-sensitivity-labels)
- [Richtlinien Updates](#policy-updates)
- [AIP-Analyse-und-Überwachungs Protokolle](#aip-analytics-and-audit-logs)
- [Bezeichnungen mit benutzerdefinierten Berechtigungen](#labels-with-user-defined-permissions)
- [Nicht unterstützte Funktionen für die gemeinsamen Erstellung](#unsupported-features-for-co-authoring)

> [!IMPORTANT]
> Die gemeinsamen Erstellung und die Vertraulichkeits Bezeichnungen können nur einigen Benutzern bereitgestellt werden, da neue Bezeichnungen für Benutzer mit einer älteren Version des Office-Clients nicht sichtbar sind.
> 
Weitere Informationen zur Unterstützung von Co-Authoring, einschließlich Einschränkungen und bekannte Probleme bei der öffentlichen Vorschau, finden Sie in der [Microsoft 365-Dokumentation](/microsoft-365/compliance/sensitivity-labels-coauthoring).

#### <a name="use-in-testing-environments-only"></a>Nur in Testumgebungen verwenden

Um Konflikte zwischen den gekennzeichneten Dateien zu vermeiden, kann die gemeinsamen Erstellung während des öffentlichen Vorschau Zeitraums nicht deaktiviert werden.

Aus diesem Grund wird empfohlen, dass Sie die gemeinsamen Erstellung für Ihr System derzeit nur in Testumgebungen aktivieren.

#### <a name="supported-versions-for-co-authoring-and-sensitivity-labels"></a>Unterstützte Versionen für die gemeinsamen Erstellung und Vertraulichkeits Bezeichnungen

Alle apps, Dienste und Vorgangs Tools in Ihrem Mandanten müssen die gemeinsamen Dokument Erstellung unterstützen.

Bevor Sie beginnen, stellen Sie sicher, dass Ihr System den in den [Microsoft 365 Voraussetzungen für die gemeinsamen Erstellung](/microsoft-365/compliance/sensitivity-labels-coauthoring#prerequisites)aufgeführten Versions Anforderungen entspricht.

> [!NOTE]
> Vertraulichkeits Bezeichnungen können zwar auf Dateien in Office 97-2003-Formaten (z  **. b. doc**, **. ppt** und **. xls**) angewendet werden, aber die gemeinsamen Erstellung für diese Dateitypen wird nicht unterstützt. Wenn eine Bezeichnung auf eine neu erstellte Datei oder eine Datei im erweiterten Dateiformat (z **. b. docx**, **PPTX** und **xlsx**) angewendet wird, wird beim Speichern der Datei im Office 97-2003-Format die Bezeichnung entfernt.
> 

#### <a name="policy-updates"></a>Richtlinien Updates

Wenn die Beschriftungs Richtlinie aktualisiert wurde, während eine Office-Anwendung mit Azure Information Protection geöffnet wurde, werden alle neuen Bezeichnungen angezeigt, aber die Anwendung führt zu einem Fehler. 

Wenn dies der Fall ist, schließen Sie die Office-Anwendung, und öffnen Sie Sie erneut, damit Sie Ihre Bezeichnungen anwenden können

#### <a name="aip-analytics-and-audit-logs"></a>AIP-Analyse-und-Überwachungs Protokolle

Wenn die gemeinsamen Erstellung aktiviert ist, sendet der Azure Information Protection Client keine Überwachungs [Protokolle](audit-logs.md).

#### <a name="labels-with-user-defined-permissions"></a>Bezeichnungen mit benutzerdefinierten Berechtigungen

In Microsoft Word, Excel und PowerPoint sind Bezeichnungen mit benutzerdefinierten Berechtigungen weiterhin verfügbar und können auf Dokumente angewendet werden, werden aber nicht für Funktionen zur gemeinsamen Dokument Erstellung unterstützt. 

Dies bedeutet, dass Sie das Anwenden einer Bezeichnung mit benutzerdefinierten Berechtigungen daran hindern, das Dokument gleichzeitig mit anderen zu bearbeiten.

#### <a name="unsupported-features-for-co-authoring"></a>Nicht unterstützte Funktionen für die gemeinsamen Erstellung

Die folgenden Funktionen werden beim Arbeiten mit der gemeinsamen Erstellung und den Vertraulichkeits Bezeichnungen nicht unterstützt:

- **DKE-Vorlagen und benutzerdefinierte DKE-Eigenschaften**. Weitere Informationen finden Sie unter [Double Key Encryption (DKE)](plan-implement-tenant-key.md#double-key-encryption-dke).

- **Entfernen externer Inhalts Markierungen in-apps**. Weitere Informationen finden Sie unter [Die Clientseite von Azure Information Protection](rms-client/use-client.md).

- Die folgenden erweiterten Einstellungen:

    - **custompropertiesbylabel**. Weitere Informationen finden Sie unter [Anwenden einer benutzerdefinierten Eigenschaft, wenn eine Bezeichnung angewendet wird](rms-client/clientv2-admin-guide-customizations.md#apply-a-custom-property-when-a-label-is-applied).

    - **labelbycustomproperties** und **enablelabelbysharepointproperties**. Weitere Informationen finden Sie unter [Migrieren von Bezeichnungen aus sicheren Inseln und anderen](rms-client/clientv2-admin-guide-customizations.md#migrate-labels-from-secure-islands-and-other-labeling-solutions)Bezeichnungs Lösungen.

## <a name="known-issues-in-policies"></a>Bekannte Probleme in Richtlinien

Das Veröffentlichen von Richtlinien kann bis zu 24 Stunden dauern.

## <a name="maximum-file-sizes"></a>Maximale Dateigröße

Dateien mit mehr als 2 GB werden für den Schutz unterstützt, aber nicht für die Entschlüsselung.

## <a name="known-issues-for-the-aip-viewer"></a>Bekannte Probleme für den AIP-Viewer

- [Quer Ansichten](#landscape-views-in-the-aip-viewer)
- [Externe Benutzer](#external-users-and-the-aip-viewer)

Weitere Informationen finden Sie unter [ **Unified Bezeichnung Client**: Anzeigen geschützter Dateien mit dem Azure Information Protection Viewer](rms-client/clientv2-view-use-files.md).
### <a name="landscape-views-in-the-aip-viewer"></a>Quer Ansichten im AIP-Viewer

Der AIP-Viewer zeigt Bilder im Hochformat an, und einige große, quer Ansichts Bilder können scheinbar gestreckt werden.

Beispielsweise wird ein ursprüngliches Bild unten auf der linken Seite mit einer gestreckten Hochformat Version im AIP-Viewer auf der rechten Seite angezeigt. 

:::image type="content" source="media/client-viewer-stretched-images.PNG" alt-text="Bild im Client-Viewer gestreckten":::

### <a name="external-users-and-the-aip-viewer"></a>Externe Benutzer und der AIP-Viewer 

Wenn ein externer Benutzer bereits über ein Gastkonto in Azure AD verfügt, zeigt der AIP-Viewer möglicherweise einen Fehler an, wenn der Benutzer ein geschütztes Dokument öffnet, und teilt ihm mit, dass er sich nicht mit einem persönlichen Konto anmelden kann.

Wenn ein solcher Fehler auftritt, muss der Benutzer [Adobe Acrobat DC mit der MIP-Erweiterung](https://helpx.adobe.com/il_en/acrobat/kb/mip-plugin-download.html) installieren, um das geschützte Dokument zu öffnen.

Wenn Sie das geschützte Dokument nach der Installation von Adobe Acrobat DC mit der MIP-Erweiterung öffnen, wird dem Benutzer möglicherweise weiterhin ein Fehler angezeigt, der anzeigt, dass das ausgewählte Benutzerkonto nicht im Mandanten vorhanden ist, und Sie werden aufgefordert, ein Konto auszuwählen. 

Dies ist ein erwarteter Fehler. Wählen Sie im Eingabe Aufforderungs Fenster **zurück** aus, um das geschützte Dokument zu öffnen.

## <a name="known-issues-for-track-and-revoke-features-public-preview"></a>Bekannte Probleme beim Nachverfolgen und widerrufen von Features (öffentliche Vorschau)

Das Nachverfolgen und widerrufen des Dokument Zugriffs mithilfe des Unified-bezeichungsclients hat die folgenden bekannten Probleme:

- [Kenn Wort geschützte Dokumente](#password-protected-documents)
- [Mehrere Anlagen in einer geschützten e-Mail](#multiple-attachments-in-a-protected-email)
- [Dokumente, die über SharePoint oder onedrive aufgerufen werden](#documents-accessed-via-sharepoint-or-onedrive)

Weitere Informationen finden Sie im [Administrator Handbuch](rms-client/track-and-revoke-admin.md) und in den [Benutzerhandbuch](rms-client/revoke-access-user.md) -Prozeduren.

#### <a name="password-protected-documents"></a>Kenn Wort geschützte Dokumente

Kenn Wort geschützte Dokumente werden von den Funktionen zum Nachverfolgen und widerrufen nicht unterstützt.
#### <a name="multiple-attachments-in-a-protected-email"></a>Mehrere Anlagen in einer geschützten e-Mail

Wenn Sie mehrere Dokumente an eine e-Mail anfügen und dann die e-Mail schützen und senden, erhält jede der Anlagen denselben Wert für "contentid".

Dieser contentid-Wert wird nur mit der ersten geöffneten Datei zurückgegeben. Beim Suchen nach den anderen Anlagen wird nicht der für die Erfassung von Überwachungsdaten erforderliche contentid-Wert zurückgegeben.

Außerdem wird durch das Aufheben des Zugriffs für eine der Anhänge der Zugriff für die anderen Anlagen in derselben geschützten e-Mail aufgehoben.

#### <a name="documents-accessed-via-sharepoint-or-onedrive"></a>Dokumente, die über SharePoint oder onedrive aufgerufen werden

- Geschützte Dokumente, die in SharePoint oder onedrive hochgeladen werden, verlieren ihren **contentid** -Wert, und der Zugriff kann nicht nachverfolgt oder widerrufen werden.

- Wenn ein Benutzer die Datei von SharePoint oder onedrive herunterlädt und von Ihrem lokalen Computer aus darauf zugreift, wird eine neue **contentid** auf das Dokument angewendet, wenn Sie Sie lokal öffnen.

    Die Verwendung des ursprünglichen **contentid** -Werts zum Nachverfolgen von Daten umfasst keinen Zugriff auf die heruntergeladene Datei des Benutzers. Außerdem wird durch das Aufheben des Zugriffs auf Grundlage des ursprünglichen **contentid** -Werts der Zugriff für die heruntergeladenen Dateien nicht widerrufen.

    In solchen Fällen können Administratoren die heruntergeladenen Dateien mithilfe von PowerShell ausfindig machen, um die neuen **contentid** -Werte zum Nachverfolgen oder widerrufen des Zugriffs zu finden.

### <a name="known-issues-for-the-aip-client-and-onedrive"></a>Bekannte Probleme beim AIP-Client und onedrive

Wenn Sie Dokumente, die in onedrive gespeichert sind und eine Vertraulichkeits Bezeichnung angewendet haben, und ein Administrator die Bezeichnung in der Beschriftungs Richtlinie so ändert, dass Schutz hinzugefügt wird, wird der neu angewendete Schutz nicht automatisch auf das bezeichnete Dokument angewendet. 

In solchen Fällen müssen Sie das Dokument manuell neu bezeichnen, um den Schutz nach Bedarf anzuwenden.
## <a name="aip-and-legacy-windows-and-office-versions"></a>AIP und ältere Windows-und Office-Versionen

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