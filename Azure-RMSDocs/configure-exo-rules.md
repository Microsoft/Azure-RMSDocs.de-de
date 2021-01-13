---
title: Exchange Online-e-Mail-Fluss Regeln für Azure Information Protection Bezeichnungen
description: Anweisungen und Beispiele zum Konfigurieren von Exchange Online-Regeln für den Nachrichtenfluss für Azure Information Protection-Bezeichnungen
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 10/26/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ba4e4a4d-5280-4e97-8f5c-303907db1bf5
ROBOTS: NOINDEX
ms.reviewer: shakella
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 7c76e7e79acb0cd12bfcbe2d71a1fee3ce78b1ba
ms.sourcegitcommit: 78c7ab80be7c292ea4bc62954a4e29c449e97439
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98164282"
---
# <a name="configuring-exchange-online-mail-flow-rules-for-azure-information-protection-labels"></a>Konfigurieren von Exchange Online-Regeln für den Nachrichtenfluss für Azure Information Protection-Bezeichnungen

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified Label-Client finden Sie in der Microsoft 365-Dokumentation unter Informationen [zu Empfindlichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) und [DLP-Bezeichnungen](/microsoft-365/compliance/dlp-sensitivity-label-as-condition) . *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Verwenden Sie die folgenden Informationen, um die Regeln für den Nachrichtenfluss in Exchange Online für die Verwendung von Azure Information Protection-Bezeichnungen zu konfigurieren und zusätzlichen Schutz für bestimmte Szenarien anzuwenden. Beispiel:

- Die Standardbezeichnung **Allgemein** bietet keinen Schutz. Für E-Mails mit dieser Bezeichnung, die extern versendet werden, wenden Sie die zusätzliche Schutzaktion „Nicht weiterleiten“ an.

- Wenn eine Anlage mit der Bezeichnung " **Confidential \ Partner** " per e-Mail an Personen außerhalb der Organisation gesendet wird und die e-Mail nicht geschützt ist, wenden Sie die zusätzliche Schutz Aktion "nur verschlüsseln" an.

Regeln für den Nachrichtenfluss, die eine Aktion zum Schutz anwenden, werden ignoriert, wenn die E-Mail bereits geschützt ist. Beispielsweise kann eine e-Mail-Nachricht, die durch nicht weiterleiten geschützt wurde, von einer Exchange-e-Mail-Fluss Regel nicht geändert werden, um die Option nur verschlüsseln zu verwenden.  

Sie können diese Beispiele erweitern und auch ändern. Fügen Sie beispielsweise weitere Bedingungen hinzu. Weitere Informationen zur Konfiguration von Regeln für den Nachrichtenfluss finden Sie in der Dokumentation zu Exchange Online unter [Mail flow rules (transport rules) in Exchange Online (Regeln für den Nachrichtenfluss (Transportregeln) in Exchange Online)](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

Weitere Informationen zum Konfigurieren von e-Mail-Fluss Regeln zum Verschlüsseln von e-Mail-Nachrichten finden Sie unter [Definieren von e-Mail-Fluss Regeln zum Verschlüsseln von e-Mails in Microsoft 365](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8) aus der 

## <a name="prerequisite-know-your-label-guid"></a>Voraussetzung: Ihre Bezeichnungs-GUID kennen

Da eine Azure Information Protection-Bezeichnung in den Metadaten gespeichert ist, können die Nachrichtenflussregeln in Exchange Online diese Informationen für Nachrichten und Office-Dokumentanlagen lesen. Die E-Mail-Flussregeln unterstützen keine Untersuchung der Metadaten für PDF-Dokumente.

Bevor Sie Nachrichtenflussregeln konfigurieren, um Nachrichten und Dokumente mit Bezeichnungen zu identifizieren, stellen Sie sicher, dass Sie die GUID der Azure Information Protection-Bezeichnung kennen, die Sie verwenden möchten. 

Weitere Informationen über die von einer Bezeichnung gespeicherten Metadaten und das Verfahren zum Identifizieren von Bezeichnungs-GUIDs finden Sie unter [In E-Mails und Dokumenten gespeicherte Bezeichnungsinformationen](configure-policy.md#label-information-stored-in-emails-and-documents).

## <a name="example-configurations"></a>Beispielkonfigurationen

Erstellen Sie für die folgenden Beispiele eine neue Nachrichtenflussregel, indem Sie folgende Schritte ausführen:

1. Melden Sie sich in einem Webbrowser mit einem Geschäfts-, Schul-oder unikonto an, dem globale Administrator Berechtigungen erteilt wurden, und melden Sie sich bei Microsoft 365 an. 

2. Wählen Sie die Kachel **Admin** aus.

3. Wählen Sie im Microsoft 365 Admin Center **Admin Centers**  >  **Exchange** aus.

4. Im Exchange Admin Center: **Nachrichtenfluss**  >  **Regeln**  >  **+**  >  **Erstellen Sie eine neue Regel**. 

> [!TIP]
> Wenn Sie bei der Konfiguration Ihrer Regeln Probleme mit der Benutzeroberfläche haben, versuchen Sie es mit einem anderen Browser, z.B. Internet Explorer.

In den Beispielen gibt es eine einzige Bedingung, die den Schutz anwendet, wenn eine E-Mail außerhalb des Unternehmens versendet wird. Weitere Informationen zu anderen Bedingungen, die Sie auswählen können, finden Sie unter [Mail flow rule conditions and exceptions (predicates) in Exchange Online (Bedingungen und Ausnahmen (Prädikate) zu Nachrichtenflussregeln in Exchange Online)](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions).


### <a name="example-1-rule-that-applies-the-do-not-forward-option-to-emails-that-are-labeled-general-when-they-are-sent-outside-the-organization"></a>Beispiel 1: Regel, die die Option „Nicht weiterleiten“ auf E-Mails mit der Bezeichnung **Allgemein** anwendet, wenn sie außerhalb der Organisation versendet werden.

In diesem Beispiel weist die Bezeichnung **Allgemein** die GUID 0e421e6d-ea17-4fdb-8f01-93a3e71333b8 auf. Ersetzen Sie Ihre eigene Bezeichnungs- oder Unterbezeichnungs-GUID, die Sie mit dieser Regel verwenden möchten. 

In der Azure Information Protection-Richtlinie wurde diese Bezeichnung als Standardbezeichnung konfiguriert, um E-Mails als **Allgemein** zu klassifizieren, wobei die Bezeichnung keinen Schutz anwendet. 

1. Geben Sie unter **Name** einen Namen für die Regel ein, z.B. `Apply Do Not Forward for General emails sent externally`.
 
2. Für **Diese Regel anwenden, wenn**: Wählen Sie **Der Empfänger befindet sich** und **Außerhalb der Organisation** aus, und wählen Sie dann **OK** aus.

3. Wählen Sie **Weitere Optionen** und dann **Bedingung hinzufügen** aus.
 
4. Für **und**: Wählen Sie **einen Nachrichtenheader**, und wählen Sie dann **enthält eines dieser Wörter** aus:
     
    a. Wählen Sie **Text eingeben** aus, und geben Sie `msip_labels` ein.
     
    b. Wählen Sie **Wörter eingeben** aus, und geben Sie `MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True` ein.
    
    c. Wählen Sie aus **+** , und klicken Sie dann auf **OK**.

5. Für **Folgende Aktion ausführen**: Wählen Sie **Nachrichtensicherheit ändern** > **Office 365-Nachrichtenverschlüsselung und -Rechteschutz anwenden** > **Nicht weiterleiten**, und wählen Sie dann **OK** aus.
    
    Die Regel Konfiguration sollte nun in etwa wie folgt aussehen:  ![ Exchange Online-e-Mail-Fluss Regel konfiguriert für eine Azure Information Protection Bezeichnung-Beispiel 1](./media/aip-exo-rule-ex1.png)

7. Wählen Sie **Speichern** aus. 

Weitere Informationen zur „Nicht weiterleiten“-Option finden Sie unter [Option „Nicht weiterleiten“ für E-Mails](configure-usage-rights.md#do-not-forward-option-for-emails).

### <a name="example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization"></a>Beispiel 2: Regel, die die Option "nur verschlüsseln" auf e-Mails anwendet, wenn Sie über Anlagen mit der Bezeichnung " **vertraulich \ Partner** " verfügen und diese e-Mails außerhalb der Organisation gesendet werden

In diesem Beispiel weist die Bezeichnung **Confidential \ Partners** die GUID 0e421e6d-ea17-4fdb-8f01-93a3e71333b8 auf. Ersetzen Sie Ihre eigene Bezeichnungs- oder Unterbezeichnungs-GUID, die Sie mit dieser Regel verwenden möchten. 

Diese Bezeichnung wird zum Klassifizieren und Schützen von Dokumenten bei der Zusammenarbeit mit Partnern verwendet.   

1. Geben Sie unter **Name** einen Namen für die Regel ein, z.B. `Apply Encrypt to emails sent externally if protected attachments`.
 
2. Für **Diese Regel anwenden, wenn**: Wählen Sie **Der Empfänger befindet sich** und **Außerhalb der Organisation** aus, und wählen Sie dann **OK** aus.

3. Wählen Sie **Weitere Optionen** und dann **Bedingung hinzufügen** aus.
 
4. Für **und**: Wählen Sie **Beliebige Anlage** aus, und wählen Sie dann **verfügt über Eigenschaften, die eines dieser Wörter enthalten**:
     
    a. Wählen Sie **+**  >  **benutzerdefinierte Anlage Eigenschaft angeben** aus.
  
    b. Geben Sie für **Eigenschaft**`MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled` ein.
    
    c. Geben Sie für **Wert**`True` ein.
    
    d. Wählen Sie **Speichern** und dann **OK** aus.

5. Für **Folgende Aktion ausführen**: Wählen Sie **Nachrichtensicherheit ändern** > **Office 365-Nachrichtenverschlüsselung und -Rechteschutz anwenden** > **Verschlüsseln**, und wählen Sie dann **OK** aus.
    
    Die Regel Konfiguration sollte nun in etwa wie folgt aussehen:  ![ Exchange Online-e-Mail-Fluss Regel ist für eine Azure Information Protection Bezeichnung konfiguriert-Beispiel 2](./media/aip-exo-rule-ex2.png)

6. Wählen Sie **Speichern** aus. 

Weitere Informationen zur Option Verschlüsseln finden Sie unter [nur verschlüsseln für e-Mails](configure-usage-rights.md#encrypt-only-option-for-emails).


## <a name="next-steps"></a>Nächste Schritte

Informationen zum Erstellen und Konfigurieren der Bezeichnungen für die Verwendung mit Exchange Online-Nachrichtenflussregeln finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

Um die Klassifizierung von E-Mail-Nachrichten, die Anlagen enthalten, zu erleichtern, sollten Sie außerdem die folgende [Richtlinieneinstellung](configure-policy-settings.md) in Azure Information Protection verwenden: **Auf E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Klassifizierung dieser Anlagen entspricht.**