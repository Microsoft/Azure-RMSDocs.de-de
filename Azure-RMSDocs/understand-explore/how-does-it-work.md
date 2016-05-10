---
# required metadata

title: Funktionsweise von Azure RMS | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ed6c964e-4701-4663-a816-7c48cbcaf619

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Funktionsweise von Azure RMS Hinter den Kulissen
Es ist wichtig, hinsichtlich der Funktionsweise von Azure RMS zu verstehen, dass der Rechteverwaltungsdienst (und Microsoft) Ihre Daten als Teil des Informationsschutzvorgangs weder sieht noch speichert. Informationen, die Sie schützen, werden niemals an Azure gesendet oder dort gespeichert – es sei denn, dass Sie diese explizit in Azure speichern oder einen anderen Cloud-Dienst verwenden, der sie in Azure speichert. Durch Azure RMS werden die Daten in einem Dokument einfach nicht lesbar für Personen, die keine autorisierten Benutzer und Dienste sind:

-   Die Daten werden auf der Anwendungsebene verschlüsselt und enthalten eine Richtlinie, die die autorisierte Verwendung für dieses Dokument definiert.

-   Wenn ein geschütztes Dokument von einem legitimen Benutzer verwendet oder von einem autorisierten Dienst verarbeitet wird, werden die Daten im Dokument entschlüsselt, und die Rechte, die in der Richtlinie definiert werden, werden durchgesetzt.

Die folgende Abbildung zeigt die Funktionsweise dieses Vorgangs als Übersicht. Ein Dokument, das die geheime Formel enthält, ist geschützt und wird dann von einem autorisierten Benutzer oder Dienst erfolgreich geöffnet. Das Dokument wird durch einen Inhaltsschlüssel (der grüne Schlüssel in der Abbildung) geschützt. Er ist für jedes Dokument eindeutig und wird im Dateiheader gespeichert. Dort ist er durch den Stammschlüssel Ihres RMS-Mandanten geschützt (der rote Schlüssel in der Abbildung). Ihr Mandantenschlüssel kann von Microsoft generiert und verwaltet werden, oder Sie generieren und verwalten Ihren eigenen Mandantenschlüssel.

Während des gesamten Schutzvorgangs (wenn Azure RMS Daten verschlüsselt und entschlüsselt, autorisiert und Einschränkungen durchsetzt) wird die geheime Formel niemals an Azure gesendet.

![](../media/AzRMS_SecretColaFormula_final.png)

Eine ausführliche Beschreibung der Funktionsweise finden Sie im Abschnitt [Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsaufnahme](#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) in diesem Artikel.

Technische Details zu den Algorithmen und Schlüssellängen, die Azure RMS verwendet, finden Sie im nächsten Abschnitt.

## Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellängen
Auch wenn Sie selbst die Funktionsweise von RMS nicht kennen müssen, werden Sie ggf. zu den verwendeten kryptografischen Steuerelementen befragt, um sicherzustellen, dass ein Sicherheitsschutz nach Branchenstandard verwendet wird.


|Kryptographische Steuerelemente|Verwendung in Azure RMS|
|-|-|
|Algorithmus: AES<br /><br />Schlüssellänge: 128 Bits und 256 Bits [[1]](#footnote-1)|Dokumentationsschutz|
|Algorithmus: RSA<br /><br />Schlüssellänge: 2.048 Bits|Schlüsselschutz|
|SHA-256|Zertifikatsignatur|

###### Fußnote 1 

256 Bit werden von der Rights Management-Freigabeanwendung für den generischen und den systemeigenen Schutz verwendet, wenn die Datei die Dateinamenerweiterung PPDF aufweist oder eine geschützte Text- oder Bilddatei (z. B. eine PTXT- oder PJPG-Datei) ist.

So werden die kryptografischen Schlüssel gespeichert und geschützt:

- Für jedes Dokument oder jede E-Mail, das bzw. die von Azure RMS geschützt wird, erstellt Azure RMS einen einzelnen AES-Schlüssel (der „Inhaltsschlüssel“), und dieser Schlüssel wird in das Dokument eingebettet und bleibt weiterhin in allen Editionen des Dokuments erhalten. 

- Der Inhaltsschlüssel wird mit dem RSA-Schlüssel der Organisation (der „Azure RMS-Mandantenschlüssel“) als Teil der Richtlinie im Dokument geschützt, und die Richtlinie wird auch vom Autor des Dokuments signiert. Dieser Mandantenschlüssel gilt für alle Dokumente und E-Mails, die von Azure RMS für die Organisation geschützt werden, und dieser Schlüssel kann von einem Azure RMS-Administrator nur geändert werden, wenn die Organisation einen Mandantenschlüssel verwendet, der kundenverwaltet ist (bezeichnet als „Bring-Your-Own-Key“ oder BYOK). 

    Dieser Mandantenschlüssel wird in Microsofts Onlinediensten in einer umfassend kontrollierten Umgebung und unter enger Beobachtung geschützt. Wenn Sie einen kundenverwalteten Mandantenschlüssel (BYOK) verwenden, wird diese Sicherheit erweitert, indem in jeder Azure-Region ein Array von hochleistungsfähigen Hardwaresicherheitsmodulen (HSMs) verwendet wird, ohne dass irgendeine Möglichkeit besteht, die Schlüssel zu extrahieren, zu exportieren oder freizugeben. Weitere Informationen zum Mandantenschlüssel und zu BYOK finden Sie unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md).

- Lizenzen und Zertifikate, die an ein Windows-Gerät gesendet werden, sind mit dem privaten Geräteschlüssel des Clients geschützt. Dieser Schlüssel wird erstellt, wenn ein Benutzer das erste Mal Azure RMS auf dem Gerät verwendet. Dieser private Schlüssel wird wiederum mit der DPAPI auf dem Client geschützt, die diese geheimen Informationen unter Verwendung eines Schlüssels schützt, der aus dem Kennwort des Benutzers abgeleitet wurde. Auf mobilen Geräten werden die Schlüssel nur ein Mal verwendet, also müssen sie, weil sie nicht auf den Clients gespeichert werden, auf dem jeweiligen Gerät nicht geschützt werden. 



## Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsaufnahme
Sehen Sie sich zum besseren Verständnis der Funktionsweise von Azure RMS einen typischen Ablauf an, nachdem [Azure RMS aktiviert wurde](../deploy-use/activate-service.md) und ein Benutzer RMS erstmals auf seinem Windows-Computer verwendet (ein Vorgang, der auch als **Initialisierung der Benutzerumgebung** oder Bootstrapping bezeichnet wird), **Inhalte geschützt werden** (ein Dokument oder eine E-Mail) und dann ein Inhalt **genutzt** (geöffnet und verwendet) wird, der durch eine andere Person geschützt wurde.

Nach der Initialisierung der Benutzerumgebung kann der Benutzer Dokumente schützen oder geschützte Dokumente auf diesem Computer nutzen.

> [!NOTE]
> Wenn dieser Benutzer zu einem anderen Windows-Computer wechselt oder ein anderer Benutzer den gleichen Windows-Computer verwendet, wird der Initialisierungsvorgang wiederholt.

### Initialisieren der Benutzerumgebung
Bevor ein Benutzer Inhalte schützen oder geschützte Inhalte auf einem Windows-Computer nutzen kann, muss die Benutzerumgebung auf dem Gerät vorbereitet werden. Dies ist ein einmaliger Vorgang. Er geschieht automatisch ohne Benutzereingriff, wenn ein Benutzer versucht, Inhalte zu schützen oder geschützte Inhalte zu nutzen:

![](../media/AzRMS.png)

**Das geschieht in Schritt 1**: Der RMS-Client auf dem Computer stellt zunächst eine Verbindung mit Azure RMS her und authentifiziert den Benutzer mithilfe seines Azure Active Directory-Kontos.

Wenn das Konto des Benutzers einen Verbund mit Azure Active Directory aufweist, erfolgt diese Authentifizierung automatisch, und der Benutzer wird nicht zur Eingabe von Anmeldeinformationen aufgefordert.

![](../media/AzRMS_useractivation2.png)

**Das geschieht in Schritt 2**: Nachdem der Benutzer authentifiziert wurde, wird die Verbindung automatisch an den RMS-Mandanten der Organisation umgeleitet, der Zertifikate ausstellt, mit denen sich der Benutzer bei Azure RMS authentifiziert, um geschützte Inhalte zu nutzen und Inhalte offline zu schützen.

Eine Kopie des Zertifikats des Benutzers wird in Azure RMS gespeichert, damit die Zertifikate mithilfe der gleichen Schlüsseln erstellt werden, wenn der Benutzer ein anderes Gerät verwendet.

### Inhaltsschutz
Wenn ein Benutzer ein Dokument schützt, führt der RMS-Client die folgenden Aktionen für ein ungeschütztes Dokument aus:

![](../media/AzRMS_documentprotection1.png)

**Das geschieht in Schritt 1**: Der RMS-Client erstellt einen zufälligen Schlüssel (den Inhaltsschlüssel) und verschlüsselt das Dokument mithilfe dieses Schlüssels mit dem symmetrischen Verschlüsselungsalgorithmus AES.

![](../media/AzRMS_documentprotection2.png)

**Das geschieht in Schritt 2**: Der RMS-Client erstellt dann ein Zertifikat, das eine Richtlinie für das Dokument enthält. Diese basiert entweder auf einer Vorlage oder auf der Angabe bestimmter Rechte für das Dokument. Diese Richtlinie umfasst die Rechte für verschiedene Benutzer oder Gruppen und andere Einschränkungen, z. B. ein Ablaufdatum.

Der RMS-Client verwendet dann den Schlüssel der Organisation, der abgerufen wurde, als die Benutzerumgebung initialisiert wurde. Er verwendet diesen Schlüssel zum Verschlüsseln der Richtlinie und des symmetrischen Inhaltsschlüssels. Der RMS-Client signiert die Richtlinie außerdem mit dem Zertifikat des Benutzers, das abgerufen wurde, als die Benutzerumgebung initialisiert wurde.

![](../media/AzRMS_documentprotection3.png)

**Das geschieht in Schritt 3**: Schließlich bettet der RMS-Client die Richtlinie in eine Datei mit dem Text des zuvor verschlüsselten Dokuments ein. Zusammen ergibt dies ein geschütztes Dokument.

Dieses Dokument kann an einem beliebigen Ort gespeichert oder mithilfe einer beliebigen Methode freigegeben werden. Die Richtlinie verbleibt immer im verschlüsselten Dokument.

### Inhaltsnutzung
Wenn ein Benutzer ein geschütztes Dokument nutzen möchte, fordert der RMS-Client im ersten Schritt Zugriff auf den Azure RMS-Dienst an:

![](../media/AzRMS_documentconsumption1.png)

**Das geschieht in Schritt 1**: Der authentifizierte Benutzer sendet die Dokumentrichtlinie und die Zertifikate des Benutzers an Azure RMS. Der Dienst entschlüsselt die Richtlinie und wertet sie aus und erstellt dann eine Liste der Rechte (sofern vorhanden), die der Benutzer für das Dokument besitzt.

![](../media/AzRMS_documentconsumption2.png)

**Das geschieht in Schritt 2**: Der Dienst extrahiert dann den AES-Inhaltsschlüssel aus der entschlüsselten Richtlinie. Dieser Schlüssel wird dann mit öffentlichen RSA-Schlüssel des Benutzers verschlüsselt, der mit der Anforderung abgerufen wurde.

Der erneut verschlüsselte Inhaltsschlüssel wird dann in eine verschlüsselte Nutzungslizenz mit der Liste der Benutzerberechtigungen eingebettet, die dann an den RMS-Client zurückgegeben wird.

![](../media/AzRMS_documentconsumption3.png)

**Das geschieht in Schritt 3**: Schließlich verwendet der RMS-Client die verschlüsselte Nutzungslizenz und entschlüsselt diese mit dem privaten Schlüssel seines eigenen Benutzers. Auf diese Weise kann der RMS-Client den Text des Dokuments nach Bedarf entschlüsseln und auf dem Bildschirm darstellen.

Der Client entschlüsselt außerdem die Rechteliste und übergibt sie an die Anwendung, die diese Rechte in der Benutzeroberfläche der Anwendung durchsetzt.

### Variationen
Die vorherigen exemplarischen Vorgehensweisen beschreiben die Standardszenarien. Es gibt jedoch einige Varianten:

-   **Mobile Geräte**: Wenn mobile Geräte Dateien mit Azure RMS schützen oder nutzen, sind die Prozessabläufe wesentlich einfacher. Mobile Geräte durchlaufen nicht zuerst den Initialisierungsprozess, weil stattdessen jede Transaktion (zum Schützen oder Nutzen von Inhalten) unabhängig ist. Ebenso wie Windows-Computer stellen mobile Geräte eine Verbindung mit dem Azure RMS-Dienst her und authentifizieren sich. Zum Schützen von Inhalten übermitteln mobile Geräte eine Richtlinie, und Azure RMS sendet ihnen dann eine Veröffentlichungslizenz und einen symmetrischen Schlüssel zum Schützen des Dokuments. Zum Nutzen von Inhalten senden mobile Geräte die Dokumentrichtlinie an Azure RMS und fordern eine Nutzungslizenz an, um das Dokument zu nutzen, wenn sie eine Verbindung mit dem Azure RMS-Dienst herstellen und sich authentifizieren. Als Antwort sendet Azure RMS die erforderlichen Schlüssel und Einschränkungen an das mobile Gerät. Beide Prozesse verwenden TLS, um den Schlüsselaustausch und andere Kommunikation zu schützen.

-   **RMS-Connector**: Wenn Azure RMS mit dem RMS-Verbindungsdienst verwendet wird, bleiben die Prozessabläufe unverändert. Der einzige Unterschied besteht darin, dass der Verbindungsdienst als Relay zwischen den lokalen Diensten (z. B. Exchange Server und SharePoint Server) und Azure RMS fungiert. Der Verbindungsdienst selbst führt keine Vorgänge aus, z. B. die Initialisierung der Benutzerumgebung oder Ver- und Entschlüsselung. Er leitet lediglich die Kommunikation weiter, die in der Regel an einen AD RMS-Server gehen würde, und verarbeitet die Übersetzung zwischen den Protokollen, die auf jeder Seite verwendet werden. In diesem Szenario können Sie Azure RMS mit lokalen Diensten verwenden.

-   **Allgemeiner Schutz (PFILE)**: Wenn Azure RMS eine Datei allgemein schützt, ist der Datenfluss grundsätzlich mit der Ausnahme, dass der RMS-Client eine Richtlinie erstellt, die alle Rechte gewährt, identisch mit dem Inhaltsschutz. Wenn die Datei genutzt wird, wird sie entschlüsselt, bevor sie an die Zielanwendung übergeben wird. In diesem Szenario können Sie alle Dateien selbst dann schützen, wenn sie keine systemeigene Unterstützung für RMS besitzen.

-   **Geschützte PDF (PPDF)**: Wenn Azure RMS eine Office-Datei mit systemeigenen Schutz versieht, wird auch eine Kopie dieser Datei erstellt und auf die gleiche Weise geschützt. Der einzige Unterschied besteht darin, dass die Dateikopie im PPDF-Dateiformat vorliegt. Die RMS-Freigabeanwendung weiß, wie diese ausschließlich für die Anzeige geöffnet wird. In diesem Szenario können Sie geschützte Anlagen per E-Mail senden und dabei sicher sein, dass der Empfänger auf einem mobilen Gerät diese immer lesen kann – selbst dann, wenn das mobile Gerät nicht über eine App verfügt, die systemeigene Unterstützung für geschützte Office-Dateien bietet.

## Nächste Schritte

Wenn Sie weitere Informationen zu Azure RMS benötigen, lesen Sie die weiteren Themen im Abschnitt **Verstehen und Kennenlernen**, z. B. [So unterstützen Anwendungen Azure Rights Management](applications-support.md), um zu erfahren, wie Ihre vorhandenen Anwendungen zur Bereitstellung einer Datenschutzlösung in Azure RMS integriert werden können. 

Lesen Sie [Terminologie für Azure Rights Management](../get-started/terminology.md), um sich mit den Begriffen vertraut zu machen, auf die Sie möglicherweise stoßen werden, wenn Sie Azure RMS konfigurieren und verwenden. Außerdem sollten Sie unbedingt [Voraussetzungen für Azure Rights Management](../get-started/requirements-azure-rms.md) lesen, bevor Sie mit der Bereitstellung beginnen. Wenn Sie es ohne weitere Vorbereitung gleich selbst ausprobieren möchten, verwenden Sie das [Schnellstart-Lernprogramm für Azure Rights Management](../get-started/quick-start-tutorial.md).

Wenn Sie soweit sind, mit der Bereitstellung von Azure RMS für Ihre Organisation zu beginnen, sollten Sie die [Roadmap für die Bereitstellung von Azure Rights Management](../plan-design/deployment-roadmap.md) für die Bereitstellungsschritte und sowie für Links zu praktischen Anweisungen verwenden.

> [!TIP]
> Weitere Informationen und Hilfe finden Sie in den Ressourcen und Links in [Informationen und Support für Azure Rights Management](../get-started/information-support.md).


<!--HONumber=Apr16_HO3-->

