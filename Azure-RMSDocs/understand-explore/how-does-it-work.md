---
title: Funktionsweise von Azure RMS – Azure Information Protection
description: Detaillierte Übersicht über die Funktionsweise von Azure RMS, die verwendeten kryptografischen Steuerelemente sowie Schritt-für-Schritt-Diagramme zur Funktionsweise dieses Prozesses.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed6c964e-4701-4663-a816-7c48cbcaf619
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a261e356e167687190cc71eed4b2da715ab45697
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="how-does-azure-rms-work-under-the-hood"></a>Funktionsweise von Azure RMS Hinter den Kulissen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Ein wichtiger Punkt hinsichtlich der Funktionsweise von Azure RMS ist, dass dieser Datenschutzdienst von Azure Information Protection Ihre Daten im Rahmen des Schutzprozesses weder sieht noch speichert. Informationen, die Sie schützen, werden niemals an Azure gesendet oder dort gespeichert – es sei denn, Sie speichern die Daten explizit in Azure oder verwenden einen anderen Clouddienst, der sie in Azure speichert. Durch Azure RMS werden die Daten in einem Dokument einfach nicht lesbar für Personen, die keine autorisierten Benutzer und Dienste sind:

- Die Daten werden auf der Anwendungsebene verschlüsselt und enthalten eine Richtlinie, die die autorisierte Verwendung für dieses Dokument definiert.

- Wenn ein geschütztes Dokument von einem legitimen Benutzer verwendet oder von einem autorisierten Dienst verarbeitet wird, werden die Daten im Dokument entschlüsselt, und die Rechte, die in der Richtlinie definiert werden, werden durchgesetzt.

Die folgende Abbildung zeigt die Funktionsweise dieses Vorgangs als Übersicht. Ein Dokument, das die geheime Formel enthält, ist geschützt und wird dann von einem autorisierten Benutzer oder Dienst erfolgreich geöffnet. Das Dokument wird durch einen Inhaltsschlüssel (der grüne Schlüssel in der Abbildung) geschützt. Er ist für jedes Dokument eindeutig und wird im Dateiheader gespeichert. Dort ist er durch den Stammschlüssel Ihres Azure Information Protection-Mandanten geschützt (der rote Schlüssel in der Abbildung). Ihr Mandantenschlüssel kann von Microsoft generiert und verwaltet werden, oder Sie generieren und verwalten Ihren eigenen Mandantenschlüssel.

Während des gesamten Schutzvorgangs (wenn Azure RMS Daten verschlüsselt und entschlüsselt, autorisiert und Einschränkungen durchsetzt) wird die geheime Formel niemals an Azure gesendet.

![Schützen einer Datei mit Azure RMS (Funktionsweise)](../media/AzRMS_SecretColaFormula_final.png)

Eine ausführliche Beschreibung der Funktionsweise finden Sie im Abschnitt [Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsaufnahme](#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) in diesem Artikel.

Technische Details zu den Algorithmen und Schlüssellängen, die Azure RMS verwendet, finden Sie im nächsten Abschnitt.

## <a name="cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths"></a>Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellängen
Auch wenn Sie die Funktionsweise dieser Technologie nicht in jedem Detail kennen, müssen Sie möglicherweise Fragen zu den verwendeten kryptografischen Steuerelementen beantworten. Beispielsweise müssen Sie möglicherweise bestätigen, dass der Sicherheitsschutz dem Branchenstandard entspricht.


|Kryptographische Steuerelemente|Verwendung in Azure RMS|
|-|-|
|Algorithmus: AES<br /><br />Schlüssellänge: 128 Bits und 256 Bits [[1]](#footnote-1)|Dokumentationsschutz|
|Algorithmus: RSA<br /><br />Schlüssellänge: 2.048 Bits [[2]](#footnote-2)|Schlüsselschutz|
|SHA-256|Zertifikatsignatur|

###### <a name="footnote-1"></a>Fußnote 1 

256 Bit werden vom Azure Information Protection-Client und der Rights Management-Freigabeanwendung für den generischen und den systemeigenen Schutz verwendet, wenn die Datei die Dateinamenerweiterung PPDF aufweist oder eine geschützte Text- oder Bilddatei (z. B. eine PTXT- oder PJPG-Datei) ist.

###### <a name="footnote-2"></a>Fußnote 2

2048 Bits ist die Länge des Schlüssels, wenn der Azure Rights Management-Dienst aktiviert ist. 1024 Bits werden für die folgenden optionalen Szenarien unterstützt:

- Während einer Migration vom lokalen Computer, wenn der AD RMS-Cluster im Kryptografiemodus 1 ausgeführt wird.

- Nach der Migration vom lokalen Computer, wenn der AD RMS-Cluster Exchange Online verwendet hat.

- Für archivierte Schlüssel, die vor der Migration lokal erstellt wurden, sodass Inhalte, die zuvor von AD RMS geschützt wurden, nach der Migration zum Azure Rights Management-Dienst weiterhin geöffnet werden können.

- Wenn Kunden ihren eigenen Schlüssel (BYOK) mithilfe von Azure Key Vault verwenden möchten. Azure Information Protection unterstützt Schlüssellängen von 1024 Bits und 2048 Bits. Für ein höheres Maß an Sicherheit wird eine Schlüssellänge von 2048 Bits empfohlen.

### <a name="how-the-azure-rms-cryptographic-keys-are-stored-and-secured"></a>So werden die kryptografischen Azure RMS-Schlüssel gespeichert und geschützt:

Für jedes Dokument oder jede E-Mail, das bzw. die von Azure RMS geschützt wird, erstellt Azure RMS einen einzelnen AES-Schlüssel (der „Inhaltsschlüssel“), und dieser Schlüssel wird in das Dokument eingebettet und bleibt weiterhin in allen Editionen des Dokuments erhalten. 

Der Inhaltsschlüssel wird mit dem RSA-Schlüssel der Organisation (der „Azure Information Protection-Mandantenschlüssel“) als Teil der Richtlinie im Dokument geschützt, und die Richtlinie wird auch vom Autor des Dokuments signiert. Dieser Mandantenschlüssel gilt für alle Dokumente und E-Mails, die vom Azure Rights Management-Dienst für die Organisation geschützt werden, und dieser Schlüssel kann von einem Azure Information Protection-Administrator nur geändert werden, wenn die Organisation einen Mandantenschlüssel verwendet, der kundenverwaltet ist (bezeichnet als „Bring-Your-Own-Key“ oder BYOK). 

Dieser Mandantenschlüssel wird in Microsofts Onlinediensten in einer umfassend kontrollierten Umgebung und unter enger Beobachtung geschützt. Wenn Sie einen vom Kunden verwalteten Mandantenschlüssel (BYOK) verwenden, wird diese Sicherheit erweitert, indem in jeder Azure-Region ein Array von hochleistungsfähigen Hardwaresicherheitsmodulen (HSMs) verwendet wird, ohne dass irgendeine Möglichkeit besteht, die Schlüssel zu extrahieren, zu exportieren oder freizugeben. Weitere Informationen zum Mandantenschlüssel und BYOK finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md).

Lizenzen und Zertifikate, die an ein Windows-Gerät gesendet werden, sind mit dem privaten Geräteschlüssel des Clients geschützt. Dieser Schlüssel wird erstellt, wenn ein Benutzer das erste Mal Azure RMS auf dem Gerät verwendet. Dieser private Schlüssel wird wiederum mit DPAPI auf dem Client geschützt, die diese geheimen Informationen unter Verwendung eines Schlüssels schützt, der aus dem Kennwort des Benutzers abgeleitet wurde. Auf mobilen Geräten werden die Schlüssel nur ein Mal verwendet, also müssen sie, weil sie nicht auf den Clients gespeichert werden, auf dem jeweiligen Gerät nicht geschützt werden. 


## <a name="walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption"></a>Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsaufnahme
Sehen Sie sich zum besseren Verständnis der Funktionsweise von Azure RMS einen typischen Ablauf an, nachdem der [Azure Rights Management-Dienst aktiviert wurde](../deploy-use/activate-service.md) und ein Benutzer den Rights Management-Dienst erstmals auf seinem Windows-Computer verwendet (ein Vorgang, der auch als **Initialisierung der Benutzerumgebung** oder Bootstrapping bezeichnet wird), **Inhalte geschützt werden** (ein Dokument oder eine E-Mail) und dann ein Inhalt **genutzt** (geöffnet und verwendet) wird, der durch eine andere Person geschützt wurde.

Nach der Initialisierung der Benutzerumgebung kann der Benutzer Dokumente schützen oder geschützte Dokumente auf diesem Computer nutzen.

> [!NOTE]
> Wenn dieser Benutzer zu einem anderen Windows-Computer wechselt oder ein anderer Benutzer den gleichen Windows-Computer verwendet, wird der Initialisierungsvorgang wiederholt.

### <a name="initializing-the-user-environment"></a>Initialisieren der Benutzerumgebung
Bevor ein Benutzer Inhalte schützen oder geschützte Inhalte auf einem Windows-Computer nutzen kann, muss die Benutzerumgebung auf dem Gerät vorbereitet werden. Dies ist ein einmaliger Vorgang. Er geschieht automatisch ohne Benutzereingriff, wenn ein Benutzer versucht, Inhalte zu schützen oder geschützte Inhalte zu nutzen:

![RMS-Client-Aktivierungsfluss – Schritt 1, Authentifizieren des Clients](../media/AzRMS.png)

**Das geschieht in Schritt 1**: Der RMS-Client auf dem Computer stellt zunächst eine Verbindung mit dem Azure Rights Management-Dienst her und authentifiziert den Benutzer mithilfe seines Azure Active Directory-Kontos.

Wenn das Konto des Benutzers einen Verbund mit Azure Active Directory aufweist, erfolgt diese Authentifizierung automatisch, und der Benutzer wird nicht zur Eingabe von Anmeldeinformationen aufgefordert.

![RMS-Clientaktivierung – Schritt 2, Zertifikate werden für den Client heruntergeladen](../media/AzRMS_useractivation2.png)

**Das geschieht in Schritt 2**: Nachdem der Benutzer authentifiziert wurde, wird die Verbindung automatisch an den Azure Information Protection-Mandanten der Organisation umgeleitet, der Zertifikate ausstellt, mit denen sich der Benutzer beim Azure Rights Management-Dienst authentifiziert, um geschützte Inhalte zu nutzen und Inhalte offline zu schützen.

Eine Kopie des Zertifikats des Benutzers wird in Azure gespeichert, damit die Zertifikate mithilfe der gleichen Schlüsseln erstellt werden, wenn der Benutzer ein anderes Gerät verwendet.

### <a name="content-protection"></a>Inhaltsschutz
Wenn ein Benutzer ein Dokument schützt, führt der RMS-Client die folgenden Aktionen für ein ungeschütztes Dokument aus:

![RMS-Dokumentenschutz – Schritt 1, das Dokument wird verschlüsselt](../media/AzRMS_documentprotection1.png)

**Das geschieht in Schritt 1**: Der RMS-Client erstellt einen zufälligen Schlüssel (den Inhaltsschlüssel) und verschlüsselt das Dokument mithilfe dieses Schlüssels mit dem symmetrischen Verschlüsselungsalgorithmus AES.

![RMS-Dokumentenschutz – Schritt 2, die Richtlinie wird erstellt](../media/AzRMS_documentprotection2.png)

**Das passiert in Schritt 2**: Der RMS-Client erstellt ein Zertifikat, das eine Richtlinie für das Dokument enthält, das die [Benutzerrechte](../deploy-use/configure-usage-rights.md) für Benutzer oder Gruppen einschließt sowie andere Einschränkungen, z.B. ein Ablaufdatum. Diese Einstellungen können in einer zuvor von einem Administrator konfigurierten Vorlage definiert oder zu dem Zeitpunkt angegeben werden, zu dem der Inhalt geschützt wird (Letzteres wird zuweilen auch als „Ad-hoc-Richtlinie“ bezeichnet).   

Das Azure AD-Attribut, das hauptsächlich verwendet wird, um die ausgewählten Benutzer und Gruppen zu identifizieren, ist das Attribut „Azure AD ProxyAddresses“, das alle E-Mail-Adressen für einen Benutzer oder eine Gruppe speichert. Wenn ein Benutzerkonto jedoch keine Werte im Attribut „Azure AD ProxyAddresses“ enthält, wird stattdessen der „UserPrincipalName“-Wert des Benutzers verwendet.

Der RMS-Client verwendet dann den Schlüssel der Organisation, der abgerufen wurde, als die Benutzerumgebung initialisiert wurde. Er verwendet diesen Schlüssel zum Verschlüsseln der Richtlinie und des symmetrischen Inhaltsschlüssels. Der RMS-Client signiert die Richtlinie außerdem mit dem Zertifikat des Benutzers, das abgerufen wurde, als die Benutzerumgebung initialisiert wurde.

![RMS-Dokumentenschutz – Schritt 3, die Richtlinie wird im Dokument eingebettet](../media/AzRMS_documentprotection3.png)

**Das geschieht in Schritt 3**: Schließlich bettet der RMS-Client die Richtlinie in eine Datei mit dem Text des zuvor verschlüsselten Dokuments ein. Zusammen ergibt dies ein geschütztes Dokument.

Dieses Dokument kann an einem beliebigen Ort gespeichert oder mithilfe einer beliebigen Methode freigegeben werden. Die Richtlinie verbleibt immer im verschlüsselten Dokument.

### <a name="content-consumption"></a>Inhaltsnutzung
Wenn ein Benutzer ein geschütztes Dokument nutzen möchte, fordert der RMS-Client im ersten Schritt Zugriff auf den Azure Rights Management-Dienst an:

![RMS-Dokumentennutzung – Schritt 1, der Benutzer wird authentifiziert und erhält die Liste der Rechte](../media/AzRMS_documentconsumption1.png)

**Das geschieht in Schritt 1**: Der authentifizierte Benutzer sendet die Dokumentrichtlinie und die Zertifikate des Benutzers an den Azure Rights Management-Dienst. Der Dienst entschlüsselt die Richtlinie und wertet sie aus und erstellt dann eine Liste der Rechte (sofern vorhanden), die der Benutzer für das Dokument besitzt. Um den Benutzer zu identifizieren, wird das Attribut „Azure AD ProxyAddresses“ für das Benutzerkonto und die Gruppen verwendet, in denen der Benutzer Mitglied ist. Aus Leistungsgründen wird die Gruppenmitgliedschaft [zwischengespeichert](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection). Wenn das Benutzerkonto über keine Werte für das Attribut „Azure AD ProxyAddresses“ verfügt, wird stattdessen der Wert im Attribut „Azure AD UserPrincipalName“ verwendet.

![RMS-Dokumentennutzung – Schritt 2, die Nutzungslizenz wird an den Client zurückgegeben](../media/AzRMS_documentconsumption2.png)

**Das geschieht in Schritt 2**: Der Dienst extrahiert dann den AES-Inhaltsschlüssel aus der entschlüsselten Richtlinie. Dieser Schlüssel wird dann mit öffentlichen RSA-Schlüssel des Benutzers verschlüsselt, der mit der Anforderung abgerufen wurde.

Der erneut verschlüsselte Inhaltsschlüssel wird dann in eine verschlüsselte Nutzungslizenz mit der Liste der Benutzerberechtigungen eingebettet, die dann an den RMS-Client zurückgegeben wird.

![RMS-Dokumentennutzung – Schritt 3: Das Dokument wird verschlüsselt und Rechte werden erzwungen](../media/AzRMS_documentconsumption3.png)

**Das geschieht in Schritt 3**: Schließlich verwendet der RMS-Client die verschlüsselte Nutzungslizenz und entschlüsselt diese mit dem privaten Schlüssel seines eigenen Benutzers. Auf diese Weise kann der RMS-Client den Text des Dokuments nach Bedarf entschlüsseln und auf dem Bildschirm darstellen.

Der Client entschlüsselt außerdem die Rechteliste und übergibt sie an die Anwendung, die diese Rechte in der Benutzeroberfläche der Anwendung durchsetzt.

> [!NOTE]
> Wenn Benutzer, die sich außerhalb Ihrer Organisation befinden, von Ihnen geschützten Inhalt nutzen, bleibt der Nutzungsfluss derselbe. Es ändert sich an diesem Szenario nur die Art und Weise, wie der Benutzer authentifiziert wird. Weitere Informationen finden Sie unter [Wenn ich ein geschütztes Dokument für eine Person außerhalb meiner Firma freigebe, wie wird dieser Benutzer authentifiziert?](../get-started/faqs-rms.md#when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated)


### <a name="variations"></a>Variationen
Die vorherigen exemplarischen Vorgehensweisen beschreiben die Standardszenarien. Es gibt jedoch einige Varianten:

-   **Mobile Geräte**: Wenn mobile Geräte Dateien mit dem Azure Rights Management-Dienst schützen oder nutzen, sind die Prozessabläufe wesentlich einfacher. Mobile Geräte durchlaufen nicht zuerst den Initialisierungsprozess, weil stattdessen jede Transaktion (zum Schützen oder Nutzen von Inhalten) unabhängig ist. Ebenso wie Windows-Computer stellen mobile Geräte eine Verbindung mit dem Azure Rights Management-Dienst her und authentifizieren sich. Zum Schützen von Inhalten übermitteln mobile Geräte eine Richtlinie, und der Azure Rights Management-Dienst sendet ihnen dann eine Veröffentlichungslizenz und einen symmetrischen Schlüssel zum Schützen des Dokuments. Zum Nutzen von Inhalten senden mobile Geräte die Dokumentrichtlinie an den Azure Rights Management-Dienst und fordern eine Nutzungslizenz an, um das Dokument zu nutzen, wenn sie eine Verbindung mit dem Azure Rights Management-Dienst herstellen und sich authentifizieren. Als Antwort sendet der Azure Rights Management-Dienst die erforderlichen Schlüssel und Einschränkungen an das mobile Gerät. Beide Prozesse verwenden TLS, um den Schlüsselaustausch und andere Kommunikation zu schützen.

-   **RMS-Connector**: Wenn der Azure Rights Management-Dienst mit dem RMS-Connector verwendet wird, bleiben die Prozessabläufe unverändert. Der einzige Unterschied besteht darin, dass der Connector als Relay zwischen den lokalen Diensten (z. B. Exchange Server und SharePoint Server) und dem Azure Rights Management-Dienst fungiert. Der Verbindungsdienst selbst führt keine Vorgänge aus, z. B. die Initialisierung der Benutzerumgebung oder Ver- und Entschlüsselung. Er leitet lediglich die Kommunikation weiter, die in der Regel an einen AD RMS-Server gehen würde, und verarbeitet die Übersetzung zwischen den Protokollen, die auf jeder Seite verwendet werden. In diesem Szenarien können Sie den Azure Rights Management-Dienst mit lokalen Diensten verwenden.

-   **Allgemeiner Schutz (PFILE)**: Wenn der Azure Rights Management-Dienst eine Datei allgemein schützt, ist der Datenfluss grundsätzlich mit der Ausnahme, dass der RMS-Client eine Richtlinie erstellt, die alle Rechte gewährt, identisch mit dem Inhaltsschutz. Wenn die Datei genutzt wird, wird sie entschlüsselt, bevor sie an die Zielanwendung übergeben wird. In diesem Szenario können Sie alle Dateien selbst dann schützen, wenn sie keine systemeigene Unterstützung für RMS besitzen.

-   **Geschützte PDF (PPDF)**: Wenn der Azure Rights Management-Dienst eine Office-Datei mit systemeigenem Schutz versieht, wird auch eine Kopie dieser Datei erstellt und auf die gleiche Weise geschützt. Der einzige Unterschied besteht darin, dass die Dateikopie im PPDF-Dateiformat vorliegt. Die RMS-Freigabeanwendung und der Azure Information Protection-Client-Viewer wissen, wie diese ausschließlich für die Anzeige geöffnet wird. In diesem Szenario können Sie geschützte Anlagen per E-Mail senden und dabei sicher sein, dass der Empfänger diese immer auf einem mobilen Gerät lesen kann – selbst dann, wenn das mobile Gerät nicht über eine App verfügt, die eine native Unterstützung für geschützte Office-Dateien bietet.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie weitere Informationen zum Azure Rights Management-Dienst benötigen, lesen Sie die weiteren Themen im Abschnitt **Verstehen und Kennenlernen**, z. B. [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md), um zu erfahren, wie Ihre vorhandenen Anwendungen zur Bereitstellung einer Datenschutzlösung in Azure Rights Management integriert werden können. 

Lesen Sie [Terminologie für Azure Information Protection](../get-started/terminology.md), um sich mit den Begriffen vertraut zu machen, auf die Sie möglicherweise stoßen werden, wenn Sie den Azure Rights Management-Dienst konfigurieren und verwenden. Außerdem sollten Sie unbedingt [Voraussetzungen für Azure Information Protection](../get-started/requirements-azure-rms.md) lesen, bevor Sie mit der Bereitstellung beginnen. Wenn Sie es ohne weitere Vorbereitung gleich selbst ausprobieren möchten, verwenden Sie das [Schnellstart-Lernprogramm für Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

Wenn Sie soweit sind, mit der Bereitstellung von Datenschutz für Ihre Organisation zu beginnen, finden Sie die Bereitstellungsschritte und Links zu praktischen Anweisungen in der [Roadmap für die Bereitstellung von Azure Information Protection](../plan-design/deployment-roadmap.md).

> [!TIP]
> Weitere Informationen und Hilfe finden Sie in den Ressourcen und Links in [Informationen und Support für Azure Information Protection](../get-started/information-support.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]