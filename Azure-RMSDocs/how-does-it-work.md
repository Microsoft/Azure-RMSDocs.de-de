---
title: Funktionsweise von Azure RMS – Azure Information Protection
description: Aufschlüsselung der Funktionsweise von Azure RMS, der verwendeten kryptografischen Steuerelemente sowie Schritt-für-Schritt-Diagramme zur Funktionsweise dieses Prozesses.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ed6c964e-4701-4663-a816-7c48cbcaf619
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 8adba522d85bec9d2d1062c510b10ae9b96368a3
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97381747"
---
# <a name="how-does-azure-rms-work-under-the-hood"></a>Funktionsweise von Azure RMS Hinter den Kulissen

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified Bezeichnung Client und Classic Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). *

Ein wichtiger Aspekt der Funktionsweise von Azure RMS ist, dass dieser Datenschutzdienst von Azure Information Protection Ihre Daten im Rahmen des Schutzprozesses weder sieht noch speichert. Informationen, die Sie schützen, werden niemals an Azure gesendet oder in Azure gespeichert, es sei denn, Sie speichern sie explizit in Azure oder verwenden einen anderen Clouddienst, der sie in Azure speichert. Azure RMS sorgt lediglich dafür, dass die Daten in einem Dokument nur für autorisierte Benutzer und Dienste lesbar sind:

- Die Daten werden auf der Anwendungsebene verschlüsselt und enthalten eine Richtlinie, die die autorisierte Verwendung für dieses Dokument definiert.

- Wenn ein geschütztes Dokument von einem legitimen Benutzer verwendet oder von einem autorisierten Dienst verarbeitet wird, werden die Daten im Dokument entschlüsselt und die Rechte, die in der Richtlinie definiert sind, werden durchgesetzt.

Die folgende Abbildung gibt einen Überblick über die Funktionsweise dieses Prozesses. Ein Dokument, das die geheime Formel enthält, ist geschützt und wird dann von einem autorisierten Benutzer oder Dienst erfolgreich geöffnet. Das Dokument wird durch einen Inhaltsschlüssel (der grüne Schlüssel in der Abbildung) geschützt. Er ist für jedes Dokument eindeutig und wird im Dateiheader gespeichert. Dort ist er durch den Stammschlüssel Ihres Azure Information Protection-Mandanten geschützt (der rote Schlüssel in der Abbildung). Ihr Mandantenschlüssel kann von Microsoft generiert und verwaltet werden, oder Sie können Ihren eigenen Mandantenschlüssel generieren und verwalten.

Während des gesamten Schutzprozesses, bei dem Azure RMS verschlüsselt und entschlüsselt, autorisiert und Einschränkungen durchsetzt, wird die geheime Formel niemals an Azure gesendet.

![Schutz einer Datei durch Azure RMS](./media/AzRMS_SecretColaFormula_final.png)

Eine ausführliche Beschreibung der Funktionsweise finden Sie im Abschnitt [Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsnutzung](#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) in diesem Artikel.

Technische Details zu den Algorithmen und Schlüssellängen, die Azure RMS verwendet, finden Sie im nächsten Abschnitt.

## <a name="cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths"></a>Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellängen
Auch wenn Sie die Funktionsweise dieser Technologie nicht im Detail kennen müssen, werden Ihnen möglicherweise Fragen zu den verwendeten kryptografischen Steuerelementen gestellt. Beispielsweise müssen Sie ggf. bestätigen, dass der Sicherheitsschutz dem Branchenstandard entspricht.


|Kryptografische Steuerelemente|Verwendung in Azure RMS|
|-|-|
|Algorithmus: AES<br /><br />Schlüssellänge: 128 Bits und 256 Bits [[1]](#footnote-1)|Inhaltsschutz|
|Algorithmus: RSA<br /><br />Schlüssellänge: 2048 Bits [[2]](#footnote-2)|Schlüsselschutz|
|SHA-256|Zertifikatsignierung|
| | |

###### <a name="footnote-1"></a>Fußnote 1 

256 Bits werden vom Azure Information Protection-Client in den folgenden Szenarios verwendet:

- Allgemeiner Schutz (.pfile).

- Nativer Schutz für PDF-Dokumente, wenn das Dokument mit dem ISO-Standard für PDF-Verschlüsselung geschützt wurde, oder das daraus resultierende geschützte Dokument eine .ppdf-Dateinamenserweiterung hat.

- Nativer Schutz für Text- oder Bilddateien (z B. .ptxt oder .pjpg).

###### <a name="footnote-2"></a>Fußnote 2

2048 Bits ist die Länge des Schlüssels, wenn der Azure Rights Management-Dienst aktiviert ist. 1024 Bits werden für die folgenden optionalen Szenarien unterstützt:

- Während einer Migration vom lokalen Computer, wenn der AD RMS-Cluster im Kryptografiemodus 1 ausgeführt wird.

- Für archivierte Schlüssel, die vor der Migration lokal erstellt wurden, sodass Inhalte, die zuvor von AD RMS geschützt wurden, nach der Migration weiterhin vom Azure Rights Management-Dienst geöffnet werden können.

### <a name="how-the-azure-rms-cryptographic-keys-are-stored-and-secured"></a>Speichern und Schützen kryptografischer Azure RMS-Schlüssel

Für jedes Dokument oder jede E-Mail, das bzw. die von Azure RMS geschützt wird, erstellt Azure RMS einen einzelnen AES-Schlüssel (den „Inhaltsschlüssel“), und dieser Schlüssel wird in das Dokument eingebettet und bleibt bei allen Editionen des Dokuments erhalten. 

Der Inhaltsschlüssel wird mit dem RSA-Schlüssel der Organisation (dem „Azure Information Protection-Mandantenschlüssel“) als Teil der Richtlinie im Dokument geschützt, und die Richtlinie wird auch vom Autor des Dokuments signiert. Dieser Mandantenschlüssel gilt für alle Dokumente und E-Mails, die vom Azure Rights Management-Dienst für die Organisation geschützt werden, und dieser Schlüssel kann von einem Azure Information Protection-Administrator nur geändert werden, wenn die Organisation einen Mandantenschlüssel verwendet, der kundenverwaltet ist (als „Bring-Your-Own-Key“ oder BYOK bezeichnet). 

Dieser Mandantenschlüssel wird in den Onlinediensten von Microsoft, in einer umfassend kontrollierten Umgebung und unter enger Beobachtung geschützt. Wenn Sie einen vom Kunden verwalteten Mandantenschlüssel (BYOK) verwenden, wird diese Sicherheit erweitert, indem in jeder Azure-Region ein Array von hochleistungsfähigen Hardwaresicherheitsmodulen (HSMs) verwendet wird, ohne dass irgendeine Möglichkeit besteht, die Schlüssel zu extrahieren, zu exportieren oder freizugeben. Weitere Informationen zum Mandantenschlüssel und BYOK finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

Lizenzen und Zertifikate, die an ein Windows-Gerät gesendet werden, sind mit dem privaten Geräteschlüssel des Clients geschützt. Dieser Schlüssel wird erstellt, wenn ein Benutzer das erste Mal Azure RMS auf dem Gerät verwendet. Dieser private Schlüssel wird wiederum mit DPAPI auf dem Client geschützt, die diese geheimen Informationen unter Verwendung eines Schlüssels schützt, der aus dem Kennwort des Benutzers abgeleitet wurde. Auf mobilen Geräten werden die Schlüssel nur ein Mal verwendet, also müssen sie, weil sie nicht auf den Clients gespeichert werden, auf dem jeweiligen Gerät nicht geschützt werden. 


## <a name="walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption"></a>Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsnutzung

Sehen Sie sich zum besseren Verständnis der Funktionsweise von Azure RMS einen typischen Ablauf an, nachdem der [Azure Rights Management-Dienst aktiviert wurde](activate-service.md) und ein Benutzer den Rights Management-Dienst erstmals auf seinem Windows-Computer verwendet (ein Vorgang, der auch als **Initialisierung der Benutzerumgebung** oder Bootstrapping bezeichnet wird), **Inhalte geschützt werden** (ein Dokument oder eine E-Mail) und dann ein Inhalt **genutzt** (geöffnet und verwendet) wird, der durch eine andere Person geschützt wurde.

Nach der Initialisierung der Benutzerumgebung kann der Benutzer Dokumente schützen oder geschützte Dokumente auf diesem Computer nutzen.

> [!NOTE]
> Wenn dieser Benutzer zu einem anderen Windows-Computer wechselt oder ein anderer Benutzer den gleichen Windows-Computer verwendet, wird der Initialisierungsvorgang wiederholt.

### <a name="initializing-the-user-environment"></a>Initialisieren der Benutzerumgebung
Bevor ein Benutzer Inhalte schützen oder geschützte Inhalte auf einem Windows-Computer nutzen kann, muss die Benutzerumgebung auf dem Gerät vorbereitet werden. Dies ist ein einmaliger Vorgang. Er geschieht automatisch ohne Benutzereingriff, wenn ein Benutzer versucht, Inhalte zu schützen oder geschützte Inhalte zu nutzen:

![RMS-Clientaktivierung – Schritt 1: Authentifizierung des Clients](./media/AzRMS.png)

**Ablauf in Schritt 1**: Der RMS-Client auf dem Computer stellt zunächst eine Verbindung mit dem Azure Rights Management-Dienst her und authentifiziert den Benutzer mithilfe seines Azure Active Directory-Kontos.

Wenn das Konto des Benutzers einen Verbund mit Azure Active Directory aufweist, erfolgt diese Authentifizierung automatisch, und der Benutzer wird nicht zur Eingabe von Anmeldeinformationen aufgefordert.

![RMS-Clientaktivierung – Schritt 2: Zertifikate werden auf den Client heruntergeladen](./media/AzRMS_useractivation2.png)

**Ablauf in Schritt 2**: Nachdem der Benutzer authentifiziert wurde, wird die Verbindung automatisch an den Azure Information Protection-Mandanten der Organisation umgeleitet, der Zertifikate ausstellt, mit denen sich der Benutzer beim Azure Rights Management-Dienst authentifiziert, um geschützte Inhalte zu nutzen und Inhalte offline zu schützen.

Eines dieser Zertifikate ist das Rechtekontozertifikat (Rights Account Certificate, RAC). Dieses Zertifikat authentifiziert den Benutzer bei Azure Active Directory und ist 31 Tage gültig. Das Zertifikat wird automatisch vom RMS-Client erneuert, vorausgesetzt das Benutzerkonto befindet sich noch in Azure Active Directory und das Konto ist aktiviert. Dieses Zertifikat kann nicht von einem Administrator konfiguriert werden. 

Eine Kopie dieses Zertifikats wird in Azure gespeichert. Falls der Benutzer also ein anderes Gerät verwendet, werden die Zertifikate mithilfe derselben Schlüssel erstellt.

### <a name="content-protection"></a>Inhaltsschutz
Wenn ein Benutzer ein Dokument schützt, führt der RMS-Client die folgenden Aktionen für ein ungeschütztes Dokument aus:

![RMS-Dokumentschutz – Schritt 1: Dokument wird verschlüsselt](./media/AzRMS_documentprotection1.png)

**Ablauf in Schritt 1**: Der RMS-Client erstellt einen zufälligen Schlüssel (den Inhaltsschlüssel) und verschlüsselt das Dokument mithilfe dieses Schlüssels mit dem symmetrischen Verschlüsselungsalgorithmus AES.

![RMS-Dokumentschutz – Schritt 2: Richtlinie wird erstellt](./media/AzRMS_documentprotection2.png)

**Ablauf in Schritt 2**: Der RMS-Client erstellt dann ein Zertifikat, das eine Richtlinie für das Dokument enthält, das die [Benutzerrechte](configure-usage-rights.md) für Benutzer oder Gruppen einschließt sowie andere Einschränkungen, z. B. ein Ablaufdatum. Diese Einstellungen können in einer zuvor von einem Administrator konfigurierten Vorlage definiert oder zu dem Zeitpunkt angegeben werden, zu dem der Inhalt geschützt wird (Letzteres wird zuweilen auch als „Ad-hoc-Richtlinie“ bezeichnet).   

Das Azure AD-Attribut, das hauptsächlich verwendet wird, um die ausgewählten Benutzer und Gruppen zu identifizieren, ist das Attribut „Azure AD ProxyAddresses“, das alle E-Mail-Adressen für einen Benutzer oder eine Gruppe speichert. Wenn ein Benutzerkonto jedoch keine Werte im Attribut „Azure AD ProxyAddresses“ enthält, wird stattdessen der „UserPrincipalName“-Wert des Benutzers verwendet.

Der RMS-Client verwendet dann den Schlüssel der Organisation, der beim Initialisieren der Benutzerumgebung abgerufen wurde, zum Verschlüsseln der Richtlinie und des symmetrischen Inhaltsschlüssels. Der RMS-Client signiert die Richtlinie außerdem mit dem Zertifikat des Benutzers, das beim Initialisieren der Benutzerumgebung abgerufen wurde.

![RMS-Dokumentschutz – Schritt 3: Richtlinie wird in das Dokument eingebettet](./media/AzRMS_documentprotection3.png)

Das **geschieht in Schritt 3**: schließlich bettet der RMS-Client die Richtlinie in eine Datei mit dem Text des zuvor verschlüsselten Dokuments ein, die zusammen ein geschütztes Dokument umfasst.

Dieses Dokument kann an einem beliebigen Ort gespeichert oder mithilfe einer beliebigen Methode freigegeben werden. Die Richtlinie verbleibt immer im verschlüsselten Dokument.

### <a name="content-consumption"></a>Inhaltsnutzung
Wenn ein Benutzer ein geschütztes Dokument nutzen möchte, fordert der RMS-Client im ersten Schritt Zugriff auf den Azure Rights Management-Dienst an:

![RMS-Dokumentnutzung – Schritt 1: Benutzer wird authentifiziert und erhält die Rechteliste](./media/AzRMS_documentconsumption1.png)

**Ablauf in Schritt 1**: Der authentifizierte Benutzer sendet die Dokumentrichtlinie und die Zertifikate des Benutzers an den Azure Rights Management-Dienst. Der Dienst entschlüsselt die Richtlinie und wertet sie aus und erstellt dann eine Liste der Rechte (sofern vorhanden), die der Benutzer für das Dokument besitzt. Um den Benutzer zu identifizieren, wird das Attribut „Azure AD ProxyAddresses“ für das Benutzerkonto und die Gruppen verwendet, in denen der Benutzer Mitglied ist. Aus Leistungsgründen wird die Gruppenmitgliedschaft [zwischengespeichert](prepare.md#group-membership-caching-by-azure-information-protection). Wenn das Benutzerkonto über keine Werte für das Attribut „Azure AD ProxyAddresses“ verfügt, wird stattdessen der Wert im Attribut „Azure AD UserPrincipalName“ verwendet.

![RMS-Dokumentnutzung – Schritt 2: Nutzungslizenz wird an den Client zurückgegeben](./media/AzRMS_documentconsumption2.png)

**Ablauf in Schritt 2**: Der Dienst extrahiert dann den AES-Inhaltsschlüssel aus der entschlüsselten Richtlinie. Dieser Schlüssel wird dann mit dem öffentlichen RSA-Schlüssel des Benutzers verschlüsselt, der mit der Anforderung abgerufen wurde.

Der erneut verschlüsselte Inhaltsschlüssel wird dann in eine verschlüsselte Nutzungslizenz mit der Liste der Benutzerrechte eingebettet, die dann an den RMS-Client zurückgegeben wird.

![RMS-Dokumentnutzung – Schritt 3: Dokument wird entschlüsselt und Rechte werden durchgesetzt](./media/AzRMS_documentconsumption3.png)

**Ablauf in Schritt 3**: Schließlich verwendet der RMS-Client die verschlüsselte Nutzungslizenz und entschlüsselt diese mit dem privaten Schlüssel seines eigenen Benutzers. Auf diese Weise kann der RMS-Client den Text des Dokuments nach Bedarf entschlüsseln und auf dem Bildschirm darstellen.

Der Client entschlüsselt außerdem die Rechteliste und übergibt sie an die Anwendung, die diese Rechte in der Benutzeroberfläche der Anwendung durchsetzt.

> [!NOTE]
> Wenn Benutzer, die sich außerhalb Ihrer Organisation befinden, von Ihnen geschützten Inhalt nutzen, bleibt der Nutzungsfluss derselbe. Es ändert sich in diesem Szenario nur die Art und Weise, wie der Benutzer authentifiziert wird. Weitere Informationen finden Sie unter [Wenn ich ein geschütztes Dokument mit jemandem außerhalb meines Unternehmens teile, wie wird dieser Benutzer authentifiziert?](./faqs-rms.md#when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated)


### <a name="variations"></a>Abweichungen
Die vorherigen exemplarischen Vorgehensweisen beschreiben die Standardszenarien. Es gibt jedoch einige Variationen:

- **E-Mail-Schutz**: Wenn E-Mail-Nachrichten mit Exchange Online und Office 365-Nachrichtenverschlüsselung mit neuen Funktionen geschützt werden, kann bei der Authentifizierung für die Nutzung auch ein Verbund bei einem Social Identity-Anbieter oder ein Einmalpasscode verwendet werden. Dann sind die Prozessabläufe sehr ähnlich, außer dass die Inhaltsnutzung dienstseitig in einer Webbrowsersitzung über eine vorübergehend zwischengespeicherte Kopie der ausgehenden E-Mail erfolgt.

- **Mobile Geräte**: Wenn mobile Geräte Dateien mit dem Azure Rights Management-Dienst schützen oder nutzen, sind die Prozessabläufe wesentlich einfacher. Mobile Geräte durchlaufen nicht zuerst den Initialisierungsprozess, da stattdessen jede Transaktion (zum Schützen oder Nutzen von Inhalten) unabhängig ist. Ebenso wie Windows-Computer stellen mobile Geräte eine Verbindung mit dem Azure Rights Management-Dienst her und authentifizieren sich. Zum Schützen von Inhalten übermitteln mobile Geräte eine Richtlinie, und der Azure Rights Management-Dienst sendet ihnen eine Veröffentlichungslizenz und einen symmetrischen Schlüssel zum Schützen des Dokuments. Zum Nutzen von Inhalten senden mobile Geräte die Dokumentrichtlinie an den Azure Rights Management-Dienst und fordern eine Nutzungslizenz an, um das Dokument zu nutzen, wenn sie eine Verbindung mit dem Azure Rights Management-Dienst herstellen und sich authentifizieren. Als Antwort sendet der Azure Rights Management-Dienst die erforderlichen Schlüssel und Einschränkungen an das mobile Gerät. Beide Prozesse verwenden TLS, um den Schlüsselaustausch und andere Kommunikation zu schützen.

- **RMS-Connector**: Wenn der Azure Rights Management-Dienst mit dem RMS-Connector verwendet wird, bleiben die Prozessabläufe unverändert. Der einzige Unterschied besteht darin, dass der Connector als Relay zwischen den lokalen Diensten (z. B. Exchange Server und SharePoint Server) und dem Azure Rights Management-Dienst fungiert. Der Connector selbst führt keine Vorgänge aus, z. B. die Initialisierung der Benutzerumgebung oder Ver- und Entschlüsselung. Er leitet lediglich die Kommunikation weiter, die normalerweise an einen AD RMS-Server gehen würde, und verarbeitet die Übersetzung zwischen den Protokollen, die auf beiden Seiten verwendet werden. In diesem Szenario können Sie den Azure Rights Management-Dienst mit lokalen Diensten verwenden.

- **Generischer Schutz (PFILE)**: Wenn der Azure Rights Management-Dienst eine Datei generisch schützt, ist der Ablauf beim Inhaltsschutz grundsätzlich identisch, jedoch mit der Ausnahme, dass der RMS-Client eine Richtlinie erstellt, die alle Rechte gewährt. Bei Nutzung der Datei wird sie entschlüsselt, bevor sie an die Zielanwendung übergeben wird. In diesem Szenario können Sie alle Dateien selbst dann schützen, wenn sie keine systemeigene Unterstützung für RMS besitzen.

- **Microsoft-Konten:** Azure Information Protection kann E-Mail-Adressen für die Nutzung autorisieren, wenn sie mit einem Microsoft-Konto authentifiziert werden. Es können jedoch nicht alle Anwendungen geschützten Inhalt öffnen, wenn ein Microsoft-Konto für die Authentifizierung verwendet wird. [Weitere Informationen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents).

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie weitere Informationen zum Azure Rights Management-Dienst benötigen, lesen Sie die anderen Artikel im Abschnitt **Verstehen und Kennenlernen**, z. B. [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md), um zu erfahren, wie Ihre vorhandenen Anwendungen zur Bereitstellung einer Datenschutzlösung in Azure Rights Management integriert werden können. 

Lesen Sie [Terminologie für Azure Information Protection](./terminology.md), um sich mit den Begriffen vertraut zu machen, auf die Sie möglicherweise stoßen werden, wenn Sie den Azure Rights Management-Dienst konfigurieren und verwenden. Außerdem sollten Sie unbedingt [Anforderungen an Azure Information Protection](requirements.md) lesen, bevor Sie mit der Bereitstellung beginnen. Wenn Sie es selbst ausprobieren möchten, verwenden Sie den Schnellstart und die Tutorials:

- [Schnellstart: Bereitstellen des Clients für einheitliche Bezeichnungen](quickstart-deploy-client.md)
- [Tutorial: Installieren des Azure Information Protection-Scanners (AIP) für einheitliche Bezeichnungen](tutorial-install-scanner.md)
- [Tutorial: Erkennen vertraulicher Inhalte mit dem Azure Information Protection-Scanner (AIP)](tutorial-scan-networks-and-content.md)
- [Tutorial: Verhindern übermäßiger Freigaben in Outlook mit Azure Information Protection (AIP)](tutorial-preventing-oversharing.md)

Wenn Sie bereit sind, mit der Bereitstellung von Datenschutz für Ihre Organisation zu beginnen, verwenden Sie die [AIP-Bereitstellungs Roadmap für Klassifizierung, Bezeichnung und Schutz](deployment-roadmap-classify-label-protect.md) für Ihre Bereitstellungs Schritte und Links zu Anleitungen.

> [!TIP]
> Weitere Informationen und Hilfe finden Sie in den Ressourcen und Links unter [Informationen und Support für Azure Information Protection](information-support.md).
