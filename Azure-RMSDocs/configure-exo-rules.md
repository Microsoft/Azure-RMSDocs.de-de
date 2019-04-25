---
title: Konfigurieren von Exchange Online-Regeln für den Nachrichtenfluss für Azure Information Protection-Bezeichnungen
description: Anweisungen und Beispiele zum Konfigurieren von Exchange Online-Regeln für den Nachrichtenfluss für Azure Information Protection-Bezeichnungen
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ba4e4a4d-5280-4e97-8f5c-303907db1bf5
ms.reviewer: shakella
ms.suite: ems
ms.openlocfilehash: f96daf289d5fdde320b98482eaf921646023e480
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "62773717"
---
# <a name="configuring-exchange-online-mail-flow-rules-for-azure-information-protection-labels"></a>Konfigurieren von Exchange Online-Regeln für den Nachrichtenfluss für Azure Information Protection-Bezeichnungen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Verwenden Sie die folgenden Informationen, um die Regeln für den Nachrichtenfluss in Exchange Online für die Verwendung von Azure Information Protection-Bezeichnungen zu konfigurieren und zusätzlichen Schutz für bestimmte Szenarien anzuwenden. Zum Beispiel:

- Die Standardbezeichnung **Allgemein** bietet keinen Schutz. Für E-Mails mit dieser Bezeichnung, die extern versendet werden, wenden Sie die zusätzliche Schutzaktion „Nicht weiterleiten“ an.

- Wenn ein Anhang mit der Bezeichnung **Vertraulich\Partner** an Personen außerhalb des Unternehmens gesendet wird und die E-Mail nicht geschützt ist, wenden Sie die zusätzliche Schutzaktion „Nur verschlüsseln“ an.

Regeln für den Nachrichtenfluss, die eine Aktion zum Schutz anwenden, werden ignoriert, wenn die E-Mail bereits geschützt ist. Beispielsweise kann eine E-Mail-Nachricht, die durch „Nicht weiterleiten“ geschützt wurde, nicht durch eine Exchange-Regel für den Nachrichtenfluss auf die Option „Nur verschlüsseln“ geändert werden.  

Sie können diese Beispiele erweitern und auch ändern. Fügen Sie beispielsweise weitere Bedingungen hinzu. Weitere Informationen zur Konfiguration von Regeln für den Nachrichtenfluss finden Sie in der Dokumentation zu Exchange Online unter [Mail flow rules (transport rules) in Exchange Online (Regeln für den Nachrichtenfluss (Transportregeln) in Exchange Online)](https://technet.microsoft.com/library/jj919238(v=exchg.150).aspx).

Weitere Informationen zur Konfiguration von Regeln für den Nachrichtenfluss zum Verschlüsseln von E-Mail-Nachrichten finden Sie in der Office-Dokumentation unter [Definieren von Nachrichtenflussregeln zum Verschlüsseln von E-Mail-Nachrichten in Office 365](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8). 

## <a name="prerequisite-know-your-label-guid"></a>Voraussetzung: Die GUID der Bezeichnung muss bekannt sein

Da eine Azure Information Protection-Bezeichnung in den Metadaten gespeichert ist, können die Nachrichtenflussregeln in Exchange Online diese Informationen für Nachrichten und Office-Dokumentanlagen lesen. Die E-Mail-Flussregeln unterstützen keine Untersuchung der Metadaten für PDF-Dokumente.

Bevor Sie Nachrichtenflussregeln konfigurieren, um Nachrichten und Dokumente mit Bezeichnungen zu identifizieren, stellen Sie sicher, dass Sie die GUID der Azure Information Protection-Bezeichnung kennen, die Sie verwenden möchten. 

Weitere Informationen über die von einer Bezeichnung gespeicherten Metadaten und das Verfahren zum Identifizieren von Bezeichnungs-GUIDs finden Sie unter [In E-Mails und Dokumenten gespeicherte Bezeichnungsinformationen](configure-policy.md#label-information-stored-in-emails-and-documents).

## <a name="example-configurations"></a>Beispielkonfigurationen

Erstellen Sie für die folgenden Beispiele eine neue Nachrichtenflussregel, indem Sie folgende Schritte ausführen:

1. Melden Sie sich in einem Webbrowser bei Office 365 mit einem Geschäfts-, Schul- oder Unikonto an, dem globale Administratorberechtigungen zugewiesen wurden. 

2. Wählen Sie die **Admin**-Kachel aus.

3. Wählen Sie im Microsoft 365 Admin Center **Admin Center** > **Exchange** aus.

4. Im Exchange Admin Center: **Nachrichtenfluss** > **Regeln** > **+** > **Neue Regel erstellen**. 

> [!TIP]
> Wenn Sie bei der Konfiguration Ihrer Regeln Probleme mit der Benutzeroberfläche haben, versuchen Sie es mit einem anderen Browser, z.B. Internet Explorer.

In den Beispielen gibt es eine einzige Bedingung, die den Schutz anwendet, wenn eine E-Mail außerhalb des Unternehmens versendet wird. Weitere Informationen zu anderen Bedingungen, die Sie auswählen können, finden Sie unter [Mail flow rule conditions and exceptions (predicates) in Exchange Online (Bedingungen und Ausnahmen (Prädikate) zu Nachrichtenflussregeln in Exchange Online)](https://technet.microsoft.com/library/jj919235(v=exchg.150).aspx).


### <a name="example-1-rule-that-applies-the-do-not-forward-option-to-emails-that-are-labeled-general-when-they-are-sent-outside-the-organization"></a>Beispiel 1: Regel, die die Option „Nicht weiterleiten“ auf E-Mails mit der Bezeichnung **Allgemein** anwendet, wenn diese an Empfänger außerhalb der Organisation versendet werden

In diesem Beispiel weist die Bezeichnung **Allgemein** die GUID 0e421e6d-ea17-4fdb-8f01-93a3e71333b8 auf. Ersetzen Sie Ihre eigene Bezeichnungs- oder Unterbezeichnungs-GUID, die Sie mit dieser Regel verwenden möchten. 

In der Azure Information Protection-Richtlinie wurde diese Bezeichnung als Standardbezeichnung konfiguriert, um E-Mails als **Allgemein** zu klassifizieren, wobei die Bezeichnung keinen Schutz anwendet. 

1. Geben Sie unter **Name** einen Namen für die Regel ein, z.B. `Apply Do Not Forward for General emails sent externally`.
 
2. Für **Diese Regel anwenden, wenn...**: Wählen Sie **Der Empfänger befindet sich** und **Außerhalb der Organisation** aus, und wählen Sie dann **OK** aus.

3. Wählen Sie **Weitere Optionen** und dann **Bedingung hinzufügen** aus.
 
4. Für **und**: Wählen Sie einen **Nachrichtenheader** aus, und wählen Sie dann **enthält eines dieser Wörter** aus:
     
    a. Wählen Sie **Text eingeben** aus, und geben Sie `msip_labels` ein.
     
    b. Wählen Sie **Wörter eingeben** aus, und geben Sie `MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;` ein.
    
    c. Wählen Sie **+** und dann **OK** aus.

5. Für **Folgende Aktion ausführen**: Wählen Sie **Nachrichtensicherheit ändern** > **Office 365-Nachrichtenverschlüsselung und -Rechteschutz anwenden** > **Nicht weiterleiten** aus, und wählen Sie dann **OK** aus.
    
    Ihre Regelkonfiguration sollte nun ungefähr wie folgt aussehen:  ![Exchange Online e-Mail-Flussregel, die für eine Azure Information Protection-Bezeichnung - Beispiel 1 konfiguriert](./media/aip-exo-rule-ex1.png)

7. Wählen Sie **Speichern** aus. 

Weitere Informationen zur „Nicht weiterleiten“-Option finden Sie unter [Option „Nicht weiterleiten“ für E-Mails](configure-usage-rights.md#do-not-forward-option-for-emails).

### <a name="example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization"></a>Beispiel 2: Regel, die die Option „Nur verschlüsseln“ auf E-Mails anwendet, wenn sie Anlagen mit der Bezeichnung **Vertraulich \ Partner** haben und an Empfänger außerhalb der Organisation versendet werden

In diesem Beispiel weist die Bezeichnung **Confidential \ Partners** die GUID 0e421e6d-ea17-4fdb-8f01-93a3e71333b8 auf. Ersetzen Sie Ihre eigene Bezeichnungs- oder Unterbezeichnungs-GUID, die Sie mit dieser Regel verwenden möchten. 

Diese Bezeichnung wird zum Klassifizieren und Schützen von Dokumenten bei der Zusammenarbeit mit Partnern verwendet.   

1. Geben Sie unter **Name** einen Namen für die Regel ein, z.B. `Apply Encrypt to emails sent externally if protected attachments`.
 
2. Für **Diese Regel anwenden, wenn...**: Wählen Sie **Der Empfänger befindet sich** und **Außerhalb der Organisation** aus, und wählen Sie dann **OK** aus.

3. Wählen Sie **Weitere Optionen** und dann **Bedingung hinzufügen** aus.
 
4. Für **und**: Wählen Sie **Beliebige Anlage** aus, und wählen Sie dann **verfügt über Eigenschaften, die eines dieser Wörter enthalten** aus:
     
    a. Wählen Sie **+** > **Benutzerdefinierte Anlageeigenschaft festlegen** aus.
  
    b. Geben Sie für **Eigenschaft** `MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled` ein.
    
    c. Geben Sie für **Wert** `True` ein.
    
    d. Wählen Sie **Speichern** und dann **OK** aus.

5. Für **Folgende Aktion ausführen**: Wählen Sie **Nachrichtensicherheit ändern** > **Office 365-Nachrichtenverschlüsselung und -Rechteschutz anwenden** > **Verschlüsseln** aus, und wählen Sie dann **OK** aus.
    
    Ihre Regelkonfiguration sollte nun ungefähr wie folgt aussehen:  ![Exchange Online e-Mail-Flussregel, die für eine Azure Information Protection-Bezeichnung - Beispiel 2 konfiguriert](./media/aip-exo-rule-ex2.png)

6. Wählen Sie **Speichern** aus. 

Weitere Informationen zur Verschlüsselungsoption finden Sie unter [Option „Encrypt Only“ (Nur verschlüsseln) für E-Mails](configure-usage-rights.md#encrypt-only-option-for-emails).


## <a name="next-steps"></a>Nächste Schritte

Informationen zum Erstellen und Konfigurieren der Bezeichnungen für die Verwendung mit Exchange Online-Nachrichtenflussregeln finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

Darüber hinaus sollten Sie die Verwendung der folgenden [Richtlinieneinstellung](configure-policy-settings.md) von Azure Information Protection in Erwägung ziehen, um E-Mail-Nachrichten zu klassifizieren, die Anlagen enthalten: **Wenden Sie für E-Mails mit Anlagen eine Bezeichnung an, die der höchsten Klassifizierung dieser Anlagen entspricht**.


