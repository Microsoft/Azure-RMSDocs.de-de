---
title: Die Azure Information Protection-Standardrichtlinie | Azure Rights Management
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/21/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 977cbf2f45cab75aaca9c2a16dd1564c2af2fe4a


---

# Die Azure Information Protection-Standardrichtlinie

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Anhand der folgenden Informationen erfahren Sie, wie die Standardrichtlinie für Azure Information Protection konfiguriert wird. Wenn Sie die Standardrichtlinie ändern, können Sie mithilfe dieser Werte die Standardeinstellungen wiederherstellen.

## Information Protection-Leiste

Titel: **Sensitivity** (Vertraulichkeit)

QuickInfo: **Information Sensitivity consists of four distinct levels (Public, Internal, Confidential, Secret), allowing the user to identify the risk of exposing the information to unauthorized users inside or outside the business.** (Für die Vertraulichkeit von Informationen sind vier Einstellungen verfügbar („Öffentlich“, „Intern“, „Vertraulich“ und „Geheim“). Anhand dieser Einstellungen erkennt der Benutzer, mit welchem Risiko die Offenlegung der Informationen gegenüber nicht autorisierten Benutzern innerhalb oder außerhalb des Unternehmens einhergeht.)


## Bezeichnungen

Es sind fünf Standardbezeichnungen verfügbar, für die die folgenden Einstellungen festgelegt werden können:

### **Personal (Persönlich)**

QuickInfo: **For personal use only. This data will not be monitored by the organization. Personal information must not include any business-related data.** (Nur zur privaten Verwendung. Diese Daten werden nicht von der Organisation überwacht. Persönliche Informationen dürfen keine geschäftlichen Daten enthalten.)

Farbe: Hellgrün

Visuelle Kennzeichnung: Keine

Bedingungen: Keine

Schutz: Nein

----


### **Public (Öffentlich)**

QuickInfo: **This information is internal and can be used by everyone inside or outside the business.** (Diese internen Informationen können von beliebigen Benutzern innerhalb oder außerhalb des Unternehmens verwendet werden.)

Farbe: Grün

Visuelle Kennzeichnung: Keine

Bedingungen: Keine

Schutz: Nein

----

### **Internal (Intern)**

QuickInfo: **This information includes a wide spectrum of internal business data that can be used by all employees and can be shared with authorized customers and business partners. Examples for internal information are company policies and most internal communications.** (Diese Informationen umfassen diverse interne Geschäftsdaten, die von allen Mitarbeitern verwendet und für autorisierte Kunden und Geschäftspartner freigegeben werden können. Beispiele für interne Informationen sind Unternehmensrichtlinien und der Großteil der internen Kommunikation.)

Farbe: Blau

Visuelle Kennzeichnung: Fußzeile (Dokument und E-Mail)

Bedingungen: Keine

Schutz: Nein

----

### **Confidential (Vertraulich)**

QuickInfo: **This data includes sensitive business information. Exposing this data to unauthorized users may cause damage to the organization. Examples for Confidential information are employee information, individual customer projects or contracts, and sales account data.** (Diese Daten umfassen sensible Geschäftsinformationen. Eine Offenlegung dieser Daten gegenüber nicht autorisierten Benutzern kann einen Schaden für die Organisation zur Folge haben. Beispiele für vertrauliche Informationen sind Mitarbeiterdaten, individuelle Kundenprojekte oder -verträge sowie Daten zu Verkaufskonten.)

Farbe: Orange

Visuelle Kennzeichnung: Fußzeile (Dokument und E-Mail)

Bedingungen: Keine

Schutz: Nein

----

### **Geheim**

QuickInfo: **This data includes highly sensitive information for the business that must be protected. Exposing Secret data to unauthorized users may cause serious damage to the organization. Examples for Secret information are personal identification information, customer records, source code, and pre-announced financial reports.** (Diese Daten umfassen äußerst sensible Informationen des Unternehmens, die geschützt werden müssen. Eine Offenlegung von geheimen Daten gegenüber nicht autorisierten Benutzern kann einen erheblichen Schaden für die Organisation zur Folge haben. Beispiele für geheime Informationen sind PINs, Kundendatensätze, Quellcode und unveröffentlichte Finanzberichte.)

Farbe: Rot

Visuelle Kennzeichnung: Fußzeile (Dokument und E-Mail)

Bedingungen: Keine

Schutz: Nein

----


## Untergeordnete Bezeichnungen

Es sind zwei untergeordnete Standardbezeichnungen verfügbar, für die die folgenden Einstellungen festgelegt werden können:

### Secret > **All Company** („Geheim“ > „Gesamtes Unternehmen“)

QuickInfo: **This data includes sensitive business information - permitted for all company employees.** (Diese Daten umfassen sensible Geschäftsinformationen, die für alle Mitarbeiter des Unternehmens zulässig sind.)

Visuelle Kennzeichnung: Keine

Bedingungen: Keine

Schutz: Nein

----

### Secret > **My Group** („Geheim“ > „Meine Gruppe“)

QuickInfo: **This data includes sensitive business information - permitted for employee groups only.** (Diese Daten umfassen sensible Geschäftsinformationen, die nur für bestimmte Mitarbeitergruppen zulässig sind.)

Visuelle Kennzeichnung: Keine

Bedingungen: Keine

Schutz: Nein

## Globale Einstellungen

**All documents and emails must have a label (applied automatically or by users)** (Alle Dokumente und E-Mails müssen über eine Bezeichnung verfügen [automatisch oder von Benutzern angewendet]): Aus

**Select the default label** (Standardbezeichnung auswählen): Keine

**Users must provide justification when lowering the sensitivity level (for example, from Confidential to Public)** (Benutzer müssen bei der Herabsenkung der Vertraulichkeitsstufe eine Begründung angeben [z. B. beim Ändern von „Vertraulich“ in „Öffentlich“]): Aus

## Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organization-s-policy). 



<!--HONumber=Jul16_HO5-->


