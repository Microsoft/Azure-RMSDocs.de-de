---
title: Die Standardrichtlinie für Azure Information Protection
description: Erfahren Sie, wie die Standardrichtlinie für Azure Information Protection konfiguriert wird. Wenn Sie die Standardrichtlinie ändern, können Sie mithilfe dieser Werte die Standardeinstellungen wiederherstellen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
ms.openlocfilehash: e8830047e57352d71810d43315ca033ec4ae91e5
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2018
ms.locfileid: "39371423"
---
# <a name="the-default-azure-information-protection-policy"></a>Die Azure Information Protection-Standardrichtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Anhand der folgenden Informationen erfahren Sie, wie die Standardrichtlinie für Azure Information Protection konfiguriert wird.

Wenn ein Administrator erstmals über das Azure-Portal eine Verbindung mit dem Azure Information Protection-Dienst herstellt, wird die Standardrichtlinie für diesen Mandanten erstellt. Gelegentlich nimmt Microsoft möglicherweise Änderungen an der Standardrichtlinie vor. Wenn Sie den Dienst aber bereits verwendet haben, bevor die Standardrichtlinie überarbeitet wurde, wird die frühere Version der Standardrichtlinie nicht aktualisiert, da Sie sie konfiguriert und für die Produktion bereitgestellt haben könnten.

Sie können auf die folgenden Werte verweisen, um die Richtlinie auf die Standardwerte zurückzusetzen, oder die Richtlinie auf die aktuellen Werte aktualisieren.

## <a name="current-default-policy"></a>Aktuelle Standardrichtlinie

Diese Version der Standardrichtlinie stammt vom 31. Juli 2017.

Diese Standardrichtlinie wird bei Aktivierung des Azure Rights Management-Diensts erstellt. Dies gilt für neue Mandanten ab Februar 2018. Weitere Informationen finden Sie in der Blogbeitragsankündigung [Improvements to the protection stack in Azure Information Protection](https://cloudblogs.microsoft.com/enterprisemobility/2018/03/08/improvements-to-the-protection-stack-in-azure-information-protection) (Verbesserungen am Schutzstapel in Azure Information Protection).

Diese Standardrichtlinie wird auch erstellt, wenn Sie [den Dienst manuell aktiviert haben](activate-service.md), bevor die Richtlinie erstellt wurde. 

Wenn der Dienst nicht aktiviert wurde, konfiguriert die Standardrichtlinie den Schutz nicht für die folgenden Unterbezeichnungen:

- **Vertraulich\Alle Mitarbeiter**

- **Vertraulich\Nur Empfänger**

- **Streng vertraulich\Alle Mitarbeiter** 

- **Streng Vertraulich\Nur Empfänger** 

Wenn diese Unterbezeichnungen nicht automatisch für den Schutz konfiguriert werden, bleibt die Standardrichtlinie die gleiche wie die [vorherige Standardrichtlinie](#default-policy-before-july-31-2017).

Wenn Schutz auf die Unterbezeichnung **Alle Mitarbeiter** angewendet wird, wird der Schutz mithilfe der Standardvorlagen konfiguriert, die automatisch im Azure-Portal in Bezeichnungen konvertiert werden. Weitere Informationen zu diesen Vorlagen finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](configure-policy-templates.md).

Ab dem 30. August 2017 enthält diese Version der Standardrichtlinie mehrsprachige Versionen der Bezeichnungsnamen und -beschreibungen. 

#### <a name="more-information-about-the-recipients-only-sublabel"></a>Weitere Informationen zu der Unterbezeichnung „Nur Empfänger“

Benutzer sehen diese Bezeichnung nur in Outlook. Diese Bezeichnung wird in Word, Excel, PowerPoint oder vom Datei-Explorer nicht angezeigt. 

Wenn Benutzer diese Bezeichnung auswählen, wird die Outlook-Version „Nicht weiterleiten“ automatisch für die E-Mail angewendet. Die Empfänger, die die Benutzer angeben, können die E-Mail nicht weiterleiten und können die Inhalte kopieren oder drucken oder Anhänge speichern.


### <a name="labels"></a>Bezeichnungen

|Label|QuickInfo|Einstellung|
|-------------------------------|---------------------------|-----------------|
|Personal (Persönlich)|Keine Geschäftsdaten, nur zur persönlichen Verwendung.|**Aktiviert**: Ein <br /><br />**Farbe**: Hellgrün<br /><br />**Visuelle Kennzeichnung**: Aus <br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Public (Öffentlich)|Geschäftsdaten, die zur öffentlichen Nutzung speziell vorbereitet und genehmigt werden.|**Aktiviert**: Ein <br /><br />**Farbe**: Grün<br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Allgemein|Geschäftsdaten, die nicht zur öffentlichen Nutzung vorgesehen sind. Sie können jedoch nach Bedarf für externe Partner freigegeben werden. Beispiele sind u.a. ein unternehmensinternes Telefonverzeichnis, Organigramme, interne Standards und die meiste interne Kommunikation.|**Aktiviert**: Ein <br /><br />**Farbe**: Blau <br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Confidential (Vertraulich)|Sensible Geschäftsdaten, die dem Unternehmen schaden können, wenn sie an Unbefugte weitergegeben werden. Beispiele hierfür sind Verträge, Sicherheitsberichte, Prognosen und Vertriebsdaten.|**Aktiviert**: Ein <br /><br />**Farbe**: Orange<br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Streng vertraulich|Sehr sensible Geschäftsdaten, die dem Unternehmen schaden, wenn sie an Unbefugte weitergegeben werden. Beispiele hierfür sind Mitarbeiter- und Kundeninformationen, Kennwörter, Quellcode und vorangekündigte Finanzberichte.|**Aktiviert**: Ein <br /><br />**Farbe**: Rot<br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|


### <a name="sublabels"></a>Unterbezeichnungen

|Label|QuickInfo|Einstellung|
|-------------------------------|---------------------------|-----------------|
|Vertraulich\Alle Mitarbeiter|Vertrauliche Daten, die Schutz erfordern, der allen Mitarbeitern volle Berechtigungen gewährt. Besitzer der Daten können Inhalte nachverfolgen und widerrufen.|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />Als vertraulich eingestuft<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Azure (Cloud-Schlüssel) [[1]](#footnote-1)|
|Vertraulich\Jeder (nicht geschützt)|Daten, die keinen Schutz erfordern. Verwenden Sie diese Option mit Vorsicht und mit einer entsprechenden geschäftlichen Begründung.|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />Als vertraulich eingestuft <br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Vertraulich\Nur Empfänger|Vertrauliche Daten ,die den Schutz benötigen und die nur von Empfängern angezeigt werden können.|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Fußzeile (E-Mail)<br /><br />Als vertraulich eingestuft <br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Festlegen von benutzerdefinierten Berechtigungen (Vorschau) bzw. Anwenden von „Nicht weiterleiten“ in Outlook|
|Streng vertraulich\Alle Mitarbeiter|Streng vertrauliche Daten, deren Inhalte von allen Mitarbeitern angezeigt, bearbeitet und beantwortet werden dürfen. Besitzer der Daten können Inhalte nachverfolgen und widerrufen.|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />Als streng vertraulich eingestuft<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Azure (Cloud-Schlüssel) [[2]](#footnote-2)|
|Streng vertraulich\Jeder (nicht geschützt)|Daten, die keinen Schutz erfordern. Verwenden Sie diese Option mit Vorsicht und mit einer entsprechenden geschäftlichen Begründung.|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />Als streng vertraulich eingestuft<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Streng Vertraulich\Nur Empfänger|Streng vertrauliche Daten,die den Schutz benötigen und die nur von Empfängern angezeigt werden können.|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Fußzeile (E-Mail)<br /><br />Als streng vertraulich eingestuft <br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Festlegen von benutzerdefinierten Berechtigungen (Vorschau) bzw. Anwenden von „Nicht weiterleiten“ in Outlook|

###### <a name="footnote-1"></a>Fußnote 1
Die Berechtigungen für den Schutz stimmen mit denen in der [Standardvorlage](configure-policy-templates.md#default-templates) (**Vertraulich \ Alle Mitarbeiter**) überein.

###### <a name="footnote-2"></a>Fußnote 2 
Die Berechtigungen für den Schutz stimmen mit denen in der [Standardvorlage](configure-policy-templates.md#default-templates) (**Streng vertraulich \ Alle Mitarbeiter**) überein.


### <a name="information-protection-bar"></a>Information Protection-Leiste

|Einstellung|Wert|
|-------------------------------|---------------------------|
|Titel|Vertraulichkeit|
|QuickInfo|Die aktuelle Bezeichnung für diesen Inhalt. Mit dieser Einstellung wird das Risiko für das Unternehmen angegeben, wenn dieser Inhalt für nicht autorisierte Personen innerhalb oder außerhalb der Organisation freigegeben wird.|


### <a name="settings"></a>Einstellung

|Einstellung|Wert|
|-------------------------------|---------------------------|
|All documents and emails must have a label (applied automatically or by users) (Alle Dokumente und E-Mails müssen über eine Bezeichnung verfügen (automatisch oder von Benutzern angewendet).)|Aus|
|Select the default label (Standardbezeichnung auswählen)|Keine|
|Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten.|Aus|
|Wenden Sie für E-Mail-Nachrichten mit Anlagen eine Bezeichnung an, die der höchsten Einstufung dieser Anlagen entspricht|Aus|
|Geben Sie eine benutzerdefinierte URL für die „Weitere Infos“-Webseite des Azure Information Protection-Clients an|Leer|


## <a name="default-policy-before-july-31-2017"></a>Standardrichtlinie vor dem 31. Juli 2017

Beachten Sie, dass Beschreibungen in dieser Richtlinie auf Daten verweisen, die Schutz erfordern, sowie auf Nachverfolgung und Widerruf von Daten. Die Richtlinie konfiguriert diesen Schutz nicht für diese Bezeichnungen, sodass Sie zur Erfüllung dieser Beschreibung zusätzliche Schritte ausführen müssen. Konfigurieren Sie z.B. die Bezeichnung, um den Schutz anzuwenden, oder verwenden Sie eine Lösung zur Verhinderung von Datenverlust (Data Loss Prevention, DLP). Bevor Sie ein Dokument mithilfe der Website zur Dokumentkontrolle verfolgen und widerrufen können, muss das Dokument von dem Dienst Azure Rights Management geschützt und von der Person nachverfolgt werden, die das Dokument geschützt hat. 


### <a name="labels"></a>Bezeichnungen

|Label|QuickInfo|Einstellung|
|-------------------------------|---------------------------|-----------------|
|Personal (Persönlich)|Keine Geschäftsdaten, nur zur persönlichen Verwendung.|**Aktiviert**: Ein <br /><br />**Farbe**: Hellgrün<br /><br />**Visuelle Kennzeichnung**: Aus <br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Public (Öffentlich)|Geschäftsdaten, die zur öffentlichen Nutzung speziell vorbereitet und genehmigt werden.|**Aktiviert**: Ein <br /><br />**Farbe**: Grün<br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Allgemein|Geschäftsdaten, die nicht zur öffentlichen Nutzung vorgesehen sind. Sie können jedoch nach Bedarf für externe Partner freigegeben werden. Beispiele sind u.a. ein unternehmensinternes Telefonverzeichnis, Organigramme, interne Standards und die meiste interne Kommunikation.|**Aktiviert**: Ein <br /><br />**Farbe**: Blau <br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Confidential (Vertraulich)|Sensible Geschäftsdaten, die dem Unternehmen schaden können, wenn sie an Unbefugte weitergegeben werden. Beispiele hierfür sind Verträge, Sicherheitsberichte, Prognosen und Vertriebsdaten.|**Aktiviert**: Ein <br /><br />**Farbe**: Orange<br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Streng vertraulich|Sehr sensible Geschäftsdaten, die dem Unternehmen schaden, wenn sie an Unbefugte weitergegeben werden. Beispiele hierfür sind Mitarbeiter- und Kundeninformationen, Kennwörter, Quellcode und vorangekündigte Finanzberichte.|**Aktiviert**: Ein <br /><br />**Farbe**: Rot<br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|


### <a name="sublabels"></a>Unterbezeichnungen

|Label|QuickInfo|Einstellung|
|-------------------------------|---------------------------|-----------------|
|Vertraulich\Alle Mitarbeiter|Vertrauliche Daten, die Schutz erfordern, der allen Mitarbeitern volle Berechtigungen gewährt. Besitzer der Daten können Inhalte nachverfolgen und widerrufen.|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />Als vertraulich eingestuft<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Vertraulich\Jeder (nicht geschützt)|Daten, die keinen Schutz erfordern. Verwenden Sie diese Option mit Vorsicht und mit einer entsprechenden geschäftlichen Begründung.|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />Als vertraulich eingestuft <br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Streng vertraulich\Alle Mitarbeiter|Streng vertrauliche Daten, deren Inhalte von allen Mitarbeitern angezeigt, bearbeitet und beantwortet werden dürfen. Besitzer der Daten können Inhalte nachverfolgen und widerrufen.|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />Als streng vertraulich eingestuft<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Streng vertraulich\Jeder (nicht geschützt)|Daten, die keinen Schutz erfordern. Verwenden Sie diese Option mit Vorsicht und mit einer entsprechenden geschäftlichen Begründung.|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />Als streng vertraulich eingestuft<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|

### <a name="information-protection-bar"></a>Information Protection-Leiste

|Einstellung|Wert|
|-------------------------------|---------------------------|
|Titel|Vertraulichkeit|
|QuickInfo|Die aktuelle Bezeichnung für diesen Inhalt. Mit dieser Einstellung wird das Risiko für das Unternehmen angegeben, wenn dieser Inhalt für nicht autorisierte Personen innerhalb oder außerhalb der Organisation freigegeben wird.|


### <a name="settings"></a>Einstellung

|Einstellung|Wert|
|-------------------------------|---------------------------|
|All documents and emails must have a label (applied automatically or by users) (Alle Dokumente und E-Mails müssen über eine Bezeichnung verfügen (automatisch oder von Benutzern angewendet).)|Aus|
|Select the default label (Standardbezeichnung auswählen)|Keine|
|Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten.|Aus|
|Wenden Sie für E-Mail-Nachrichten mit Anlagen eine Bezeichnung an, die der höchsten Einstufung dieser Anlagen entspricht|Aus|
|Geben Sie eine benutzerdefinierte URL für die „Weitere Infos“-Webseite des Azure Information Protection-Clients an|Leer|

## <a name="default-policy-before-march-21-2017"></a>Standardrichtlinie vor dem 21. März 2017

### <a name="labels"></a>Bezeichnungen

|Label|QuickInfo|Einstellung|
|-------------------------------|---------------------------|-----------------|
|Personal (Persönlich)|Nur zur privaten Verwendung. This data will not be monitored by the organization. Personal information must not include any business-related data (Persönliche Informationen dürfen keine geschäftlichen Daten enthalten).|**Aktiviert**: Ein <br /><br />**Farbe**: Hellgrün<br /><br />**Visuelle Kennzeichnung**: Aus <br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Public (Öffentlich)|Diese internen Informationen können von beliebigen Benutzern innerhalb oder außerhalb des Unternehmens verwendet werden.|**Aktiviert**: Ein <br /><br />**Farbe**: Grün<br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Internal (Intern)|Diese Informationen umfassen ein breites Spektrum interner Geschäftsdaten, die von allen Mitarbeitern verwendet und die für autorisierte Kunden und Geschäftspartner freigegeben werden können. Beispiele für interne Informationen sind Unternehmensrichtlinien und der Großteil der internen Kommunikation.|**Aktiviert**: Ein <br /><br />**Farbe**: Blau <br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail): <br /><br />Vertraulichkeit: Intern<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Confidential (Vertraulich)|This data includes sensitive business information. (Diese Daten umfassen sensible Geschäftsinformationen.) Exposing this data to unauthorized users may cause damage to the organization. Examples for Confidential information are employee information, individual customer projects or contracts, and sales account data. (Beispiele für vertrauliche Informationen sind Mitarbeiterdaten, individuelle Kundenprojekte oder -verträge sowie Daten zu Verkaufskonten.)|**Aktiviert**: Ein <br /><br />**Farbe**: Orange<br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail):<br /><br /> Vertraulichkeit: Vertraulich<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Geheim|This data includes highly sensitive information for the business that must be protected. (Diese Daten umfassen äußerst sensible Informationen des Unternehmens, die geschützt werden müssen.) Exposing Secret data to unauthorized users may cause serious damage to the organization. Examples for Secret information are personal identification information, customer records, source code, and pre-announced financial reports. (Beispiele für geheime Informationen sind PINs, Kundendatensätze, Quellcode und unveröffentlichte Finanzberichte.)|**Aktiviert**: Ein <br /><br />**Farbe**: Rot<br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail):<br /><br /> Vertraulichkeit: Geheim<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|


### <a name="sublabels"></a>Unterbezeichnungen

|Label|QuickInfo|Einstellung|
|-------------------------------|---------------------------|-----------------|
|Secret > All Company (Geheim > Gesamtes Unternehmen)|This data includes sensitive business information - permitted for all company employees. (Diese Daten umfassen sensible Geschäftsinformationen, die für alle Mitarbeiter des Unternehmens zulässig sind.)|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Secret \ My Group (Geheim > Meine Gruppe)|This data includes sensitive business information - permitted for employee groups only (Diese Daten umfassen sensible Geschäftsinformationen, die nur für bestimmte Mitarbeitergruppen zulässig sind.)|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|

### <a name="information-protection-bar"></a>Information Protection-Leiste

|Einstellung|Wert|
|-------------------------------|---------------------------|
|Titel|Vertraulichkeit|
|QuickInfo|Information Sensitivity consists of four distinct levels (Public, Internal, Confidential, Secret), allowing the user to identify the risk of exposing the information to unauthorized users inside or outside the business. (Für die Vertraulichkeit von Informationen sind vier Einstellungen verfügbar („Öffentlich“, „Intern“, „Vertraulich“ und „Geheim“). Anhand dieser Einstellungen erkennt der Benutzer, mit welchem Risiko die Offenlegung der Informationen gegenüber nicht autorisierten Benutzern innerhalb oder außerhalb des Unternehmens einhergeht.)|


### <a name="settings"></a>Einstellung

|Einstellung|Wert|
|-------------------------------|---------------------------|
|All documents and emails must have a label (applied automatically or by users) (Alle Dokumente und E-Mails müssen über eine Bezeichnung verfügen (automatisch oder von Benutzern angewendet).)|Aus|
|Select the default label (Standardbezeichnung auswählen)|Keine|
|Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten.|Aus|
|Geben Sie eine benutzerdefinierte URL für die „Weitere Infos“-Webseite des Azure Information Protection-Clients an|Leer|


## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy). 
