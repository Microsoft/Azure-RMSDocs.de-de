---
title: "Die Standardrichtlinie für Azure Information Protection"
description: "Erfahren Sie, wie die Standardrichtlinie für Azure Information Protection konfiguriert wird. Wenn Sie die Standardrichtlinie ändern, können Sie mithilfe dieser Werte die Standardeinstellungen wiederherstellen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
ms.openlocfilehash: 3a2c5af41023021893f0eb751321e798ea523e8c
ms.sourcegitcommit: d5ce1bce5e63b3e510033ff9d4d246dd3511ed7c
translationtype: HT
---
# <a name="the-default-azure-information-protection-policy"></a>Die Azure Information Protection-Standardrichtlinie

>*Gilt für: Azure Information Protection*

Anhand der folgenden Informationen erfahren Sie, wie die Standardrichtlinie für Azure Information Protection konfiguriert wird. Wenn Sie die Standardrichtlinie ändern, können Sie mithilfe dieser Werte die Standardeinstellungen wiederherstellen.


## <a name="information-protection-bar"></a>Information Protection-Leiste

|Einstellung|Wert|
|-------------------------------|---------------------------|
|Titel|Vertraulichkeit|
|QuickInfo|Information Sensitivity consists of four distinct levels (Public, Internal, Confidential, Secret), allowing the user to identify the risk of exposing the information to unauthorized users inside or outside the business. (Für die Vertraulichkeit von Informationen sind vier Einstellungen verfügbar („Öffentlich“, „Intern“, „Vertraulich“ und „Geheim“). Anhand dieser Einstellungen erkennt der Benutzer, mit welchem Risiko die Offenlegung der Informationen gegenüber nicht autorisierten Benutzern innerhalb oder außerhalb des Unternehmens einhergeht.)|

## <a name="labels"></a>Bezeichnungen

|Label|QuickInfo|Einstellungen|
|-------------------------------|---------------------------|-----------------|
|Personal (Persönlich)|Nur zur privaten Verwendung. This data will not be monitored by the organization. Personal information must not include any business-related data (Persönliche Informationen dürfen keine geschäftlichen Daten enthalten).|**Aktiviert**: Ein <br /><br />**Farbe**: Hellgrün<br /><br />**Visuelle Kennzeichnung**: Aus <br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Public (Öffentlich)|Diese internen Informationen können von beliebigen Benutzern innerhalb oder außerhalb des Unternehmens verwendet werden.|**Aktiviert**: Ein <br /><br />**Farbe**: Grün<br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Internal (Intern)|Diese Informationen umfassen ein breites Spektrum interner Geschäftsdaten, die von allen Mitarbeitern verwendet und die für autorisierte Kunden und Geschäftspartner freigegeben werden können. Beispiele für interne Informationen sind Unternehmensrichtlinien und der Großteil der internen Kommunikation.|**Aktiviert**: Ein <br /><br />**Farbe**: Blau <br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Confidential (Vertraulich)|This data includes sensitive business information. (Diese Daten umfassen sensible Geschäftsinformationen.) Exposing this data to unauthorized users may cause damage to the organization. Examples for Confidential information are employee information, individual customer projects or contracts, and sales account data. (Beispiele für vertrauliche Informationen sind Mitarbeiterdaten, individuelle Kundenprojekte oder -verträge sowie Daten zu Verkaufskonten.)|**Aktiviert**: Ein <br /><br />**Farbe**: Orange<br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Geheim|This data includes highly sensitive information for the business that must be protected. (Diese Daten umfassen äußerst sensible Informationen des Unternehmens, die geschützt werden müssen.) Exposing Secret data to unauthorized users may cause serious damage to the organization. Examples for Secret information are personal identification information, customer records, source code, and pre-announced financial reports. (Beispiele für geheime Informationen sind PINs, Kundendatensätze, Quellcode und unveröffentlichte Finanzberichte.)|**Aktiviert**: Ein <br /><br />**Farbe**: Rot<br /><br />**Visuelle Kennzeichnung**: Fußzeile (Dokument und E-Mail)<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|

## <a name="sub-labels"></a>Untergeordnete Bezeichnungen

|Label|QuickInfo|Einstellungen|
|-------------------------------|---------------------------|-----------------|
|Secret > All Company (Geheim > Gesamtes Unternehmen)|This data includes sensitive business information - permitted for all company employees. (Diese Daten umfassen sensible Geschäftsinformationen, die für alle Mitarbeiter des Unternehmens zulässig sind.)|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|
|Secret \ My Group (Geheim > Meine Gruppe)|This data includes sensitive business information - permitted for employee groups only (Diese Daten umfassen sensible Geschäftsinformationen, die nur für bestimmte Mitarbeitergruppen zulässig sind.)|**Aktiviert**: Ein <br /><br />**Visuelle Kennzeichnung**: Aus<br /><br />**Bedingungen**: Keine<br /><br />**Schutz**: Keiner|

## <a name="global-settings"></a>Globale Einstellungen

|Einstellung|Wert|
|-------------------------------|---------------------------|
|All documents and emails must have a label (applied automatically or by users) (Alle Dokumente und E-Mails müssen über eine Bezeichnung verfügen (automatisch oder von Benutzern angewendet).)|Aus|
|Select the default label (Standardbezeichnung auswählen)|Keine|
|Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten.|Aus|


## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]