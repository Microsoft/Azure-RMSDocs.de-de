---
title: Unterstützen von Benutzern beim Schützen von Dateien mithilfe von Azure RMS – AIP
description: Informationen, anhand derer Sie Unterstützung für Benutzer, Administratoren und Ihren Helpdesk bieten können, nachdem Sie den Azure Rights Management-Dienst von Azure Information Protection bereitgestellt und konfiguriert haben.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/04/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 0954f3caa116ee100ed819f71f5be04f36392bd9
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97382172"
---
# <a name="helping-users-to-protect-files-by-using-the-azure-rights-management-service"></a>Unterstützen von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Nachdem Sie Azure Information Protection für Ihre Organisation bereitgestellt und konfiguriert haben, können Sie Ihren Benutzern und Administratoren sowie Ihrem Helpdesk Hilfe und Anleitung bieten:

-   **Endbenutzer Informationen**
    
    Informieren Sie Benutzer darüber, wie und wann sie Dokumente und E-Mails, die sensible Informationen enthalten, schützen können. Stellen Sie diese Informationen wann immer möglich für ihre vorhandenen Workflows bereit, sodass sie die zusätzlichen Schritte in einen bereits vertrauten Prozess implementieren können, anstatt neue Prozesse einzuführen. Stellen Sie sicher, dass sie die Vorteile (und Risiken) kennenlernen, die für Ihr Geschäft spezifisch sind, und bieten Sie Ihnen Anleitung, wann Dateien und E-Mails geschützt werden sollten. 

    Wenn Sie über den klassischen AIP-Client verfügen und [Vorlagen](configure-policy-templates.md)konfiguriert haben, geben Sie Anweisungen dazu an, welche auszuwählen sind, wenn der Vorlagen Name und die Beschreibung nicht ausreichen, um die richtige auszuwählen.
    
    > [!TIP]
    > Beispielvideos für Endbenutzer:
    > -   [Microsoft Azure Information Protection](https://youtu.be/ToShAUdlrPo?list=PL8nfc9haGeb6qSm1kLU8n3Zqg398764h5)
    > -   [Azure RMS-Dokumentenverfolgung und -widerruf](https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Administrator Informationen**
    
    Einige Anwendungen wenden automatisch Informationsschutz an, indem sie Richtlinien und Einstellungen verwenden, die von Administratoren konfiguriert werden. Für diese Anwendungen müssen Sie möglicherweise Anleitungen für andere Administratoren bereitstellen, die diese Anwendungen und Dienste verwalten. 
    
    Weitere Informationen finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md) und [Konfigurieren von Anwendungen für den Azure Rights Management-Dienst](configure-applications.md).
    
-   **Helpdesk-Informationen**
    
    Wenn Benutzer über den Azure Information Protection-Client verfügen, können sie von Helpdesk-Betreibern darum gebeten werden, die Option **Hilfe und Feedback** zum Übermitteln von Informationen zu verwenden. Dabei kann es sich um Informationen dazu handeln, ob die Edition von Office den Schutz nicht unterstützen kann, sowie zum derzeit angemeldeten Benutzerkonto. Sie können diese Option auch dazu verwenden, Protokolldateien zu sammeln und den Client zurückzusetzen. Weitere Informationen finden Sie im Administratorhandbuch: [Installationsüberprüfungen und Problembehandlung](./rms-client/clientv2-admin-guide.md#installation-checks-and-troubleshooting).
    
    Wenn legitime Anforderungen vorhanden sind, die über uneingeschränkten Zugriff auf geschützte Dokumente verfügen, stellen Sie sicher, dass der Helpdesk über Prozesse verfügt, um diesen Zugriff mithilfe der Azure Information Protection Administrator [Funktion](configure-super-users.md)anzufordern. Diese Anforderungen können beispielsweise von der Rechtsabteilung oder einem Vorgesetzten stammen, nachdem ein Mitarbeiter die Organisation verlassen hat.
    
    Darüber hinaus finden Sie einige der möglicherweise auftretenden Probleme in den folgenden Kategorien:
    
    - **Anmelde Hilfe**
        
        Benutzer werden möglicherweise zur Eingabe von Anmeldeinformationen aufgefordert, wenn mit dem Azure Rights Management-Dienst ein Benutzer authentifiziert werden muss und dazu keine zwischengespeicherten Anmeldeinformationen verwendet werden können. Die erforderlichen Anmeldeinformationen gelten üblicherweise für das Geschäfts-, Schul- oder Unikonto des Benutzers, das Ihrem Office 365- oder Azure Active Directory-Mandanten zugeordnet ist. Obwohl Azure Rights Management AD-Konten authentifizieren kann, können einige Anwendungen auch geschützte Inhalte öffnen, wenn ein Microsoft-Konto für die Authentifizierung verwendet wird. [Weitere Informationen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents) 
        
        Stellen Sie Benutzern und Ihrem Helpdesk Anweisungen bereit, welches Konto zu verwenden ist, wenn Benutzer nach Anmeldeinformationen gefragt werden, wenn sie über Anwendungen verfügen, die den Azure Rights Management-Dienst verwenden.
        
    - **Probleme beim schützen oder nutzen von Inhalten**
        
        Stellen Sie sicher, dass den Benutzern entsprechende Anweisungen für die verwendeten Anwendungen vorliegen und dass sie Anwendungen und Geräte verwenden, die vom Azure Rights Management-Dienst unterstützt werden. Weitere Informationen zu unterstützten Anwendungen und Geräten finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).
        
        Unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md) erfahren Sie, wie Sie prüfen können, ob ein bestimmter Benutzer oder eine bestimmte Gruppe von Azure Active Directory dafür autorisiert werden kann, geschützte Inhalte zu schützen oder zu nutzen.
        
        Wenn die Rechte, die Benutzer haben, nicht wie erwartet sind, überprüfen Sie in der [Tabelle mit den Nutzungsrechten](configure-usage-rights.md#usage-rights-and-descriptions) die Beschreibung und etwaige anwendungsspezifische Implementierungen der Rechte.

        **Nur klassischer Client**: Wenn Benutzer melden, dass Sie geschützte Inhalte zwar öffnen können, jedoch nicht über die erforderlichen Berechtigungen verfügen, besteht das Problem möglicherweise darin, dass sich der Benutzer nicht in der richtigen Gruppe befindet, die für eine Rights Management Vorlage konfiguriert ist. Oder das Problem ist, dass es erforderlich ist, dass die [Vorlage für den Benutzer oder die Gruppe neu konfiguriert wird](configure-policy-templates.md). 
        
        
Verwenden Sie folgende Abschnitte für anwendungsspezifische Informationen, um Benutzern beim Schützen von Dokumenten und E-Mails zu helfen.

## <a name="using-information-protection-with-the-azure-information-protection-client"></a>Verwenden des Informationsschutzes mit dem Azure Information Protection-Client

Wenn Benutzer Office 2010 verwenden, ist der Azure Information Protection-Client erforderlich, um geschützte Dokumente und E-Mails zu schützen und zu nutzen. Der Azure Information Protection-Client wird jedoch auch für alle Computer und mobilen Geräte empfohlen, die diesen Dienst unterstützen.

Der Azure Information Protection-Client erleichtert Benutzern nicht nur, Dokumente und E-Mails zu schützen, sondern auch das Nachverfolgen der Dokumente, die sie geschützt haben. Nachverfolgte Dokumente können auch widerrufen werden, wenn die zuvor autorisierten Benutzer keinen Zugriff mehr darauf haben sollen.

Anweisungen zur Verwendung dieses Clients für Windows-Computer finden Sie im [Azure Information Protection-Client – Benutzerhandbuch](./rms-client/clientv2-user-guide.md).


## <a name="using-information-protection-with-office-365-office-2019-office-2016-or-office-2013"></a>Verwenden von Informationsschutz mit Office 365, Office 2019, Office 2016 oder Office 2013

Wenn Sie den Azure Rights Management-Dienst verwenden und den Azure Information Protection-Client nicht installiert haben, wird die Azure Information Protection-Leiste nicht in den Office-Desktopanwendungen der Benutzer angezeigt. Außerdem wird die **Vertraulichkeits** Schaltfläche auf dem Menüband nicht angezeigt, oder Sie können im Datei **-Explorer klassifizieren und schützen** . Mithilfe dieser Ergänzungen können Dokumente und E-Mails einfacher geschützt werden. Diese Benutzer müssen ähnliche Anleitungen wie die nachfolgenden befolgen.

> [!TIP]
> Um anwendungsspezifische Hilfe und Anleitungen zur Verwendung von Informationsschutz mit diesen Anwendungen zu finden, suchen Sie nach **IRM** und dem Anwendungsnamen und der Version.

#### <a name="to-protect-a-document-in-word-from-office-365-proplus"></a>Schützen eines Dokuments in Word von Office 365 ProPlus

1.  Erstellen Sie in Microsoft Word ein Dokument.

2.  Über das Menü **Datei** : **Info**  >  **Schutz Dokument**  >   **Einschränken des Zugriffs**.

3. Wählen Sie dann eine Vorlage aus, um schnell die entsprechenden Nutzungsrechte anzuwenden, oder klicken Sie auf **Zugriff beschränken**, und wählen Sie die Nutzungsrechte selbst aus.

    > [!NOTE]
    > Wenn Sie Rights Management nicht zuvor auf dem Computer verwendet haben, wird über die Option **Zugriff beschränken** eine Verbindung mit dem Azure Rights Management-Dienst hergestellt, und Sie werden zur Angabe von Anmeldeinformationen aufgefordert, um den Office IRM-Client zu konfigurieren. Sie können dann eine Vorlage oder Nutzungsrechte auswählen.

3.  Speichern Sie das Dokument.

Wenn das Dokument von anderen geöffnet wird, werden sie zuerst authentifiziert. Wenn Sie nicht autorisiert sind, um das Dokument zu öffnen, wird es nicht geöffnet. Wenn Sie zum Öffnen des Dokuments autorisiert sind, wird es mit den eingeschränkten [Nutzungsrechten](configure-usage-rights.md) geöffnet, die für diesen Benutzer angegeben wurden. 

Beispielsweise gestattet ein Nutzungsrecht „Nur anzeigen“ dem Benutzer nicht das Bearbeiten oder Speichern des Dokuments, auch nicht, wenn es vorher an einen anderen Speicherort kopiert wird. 

Die Nutzungsrechte werden am oberen Rand des Dokuments in einem Einschränkungsbanner angezeigt. In dem Banner können die Berechtigungen angezeigt werden, die auf das Dokument angewendet werden, oder es kann ein Link zu deren Anzeige vorhanden sein.

#### <a name="to-protect-an-email-message-using-outlook-from-office-365-proplus-connecting-to-exchange-online"></a>Schützen einer E-Mail-Nachricht mit Outlook von Office 365 ProPlus mit Verbindung zu Exchange Online

1.  Erstellen Sie in Outlook eine E-Mail, die an einen Empfänger in Ihrer Organisation adressiert ist.

2.  Auf der Registerkarte **Optionen** : **Berechtigung** > wählen Sie eine Option aus. Beispiel: **nicht weiterleiten** oder **\<Company Name> -vertraulich** oder **\<Company Name> -vertrauliche Ansicht**.

3.  Senden Sie die Nachricht.

Ähnlich wie beim Anzeigen eines geschützten Dokuments werden die Empfänger beim Öffnen der geschützten E-Mail zunächst authentifiziert. Wenn Sie zum Anzeigen der e-Mail-Nachricht autorisiert sind, wird Sie mit den eingeschränkten [Nutzungsrechten](configure-usage-rights.md) geöffnet, die für diesen Benutzer angegeben wurden. 

Wenn die E-Mail-Nachricht beispielsweise mit der Option **Nicht weiterleiten** geschützt ist, steht die Schaltfläche „Weiterleiten“ nicht auf dem Menüband zur Verfügung.

#### <a name="to-protect-an-email-message-using-outlook-on-the-web"></a>So schützen Sie eine E-Mail-Nachricht mithilfe von Outlook im Web

1. Erstellen Sie in Outlook im Web eine E-Mail-Nachricht, die an einen Empfänger in Ihrer Organisation adressiert ist.

2. Wählen Sie **Schützen** aus. Die Option **Nicht weiterleiten** ist automatisch aktiviert, sofern die Standardeinstellung nicht von einem Administrator geändert wurde. Wenn Sie die Standardeinstellung ändern möchten, klicken Sie auf **Berechtigungen ändern** , und wählen Sie dann eine Option aus der Dropdown-Dropdown Beispiel: **verschlüsseln** oder **\<Company Name> -vertraulich**.

3. Senden Sie die Nachricht.

Ähnlich wie beim Anzeigen eines geschützten Dokuments werden die Empfänger beim Öffnen der E-Mail zunächst authentifiziert. Wenn Sie zum Anzeigen der e-Mail-Nachricht autorisiert sind, wird Sie mit den eingeschränkten [Nutzungsrechten](configure-usage-rights.md) geöffnet, die für diesen Benutzer angegeben wurden. 

Beispielsweise ist bei der Standardoption **Nicht weiterleiten** die Option **Weiterleiten** im Nachrichtenfenster nicht verfügbar.
