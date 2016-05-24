---
# required metadata

title: Installieren und Konfigurieren des Servers | Azure RMS
description: Installieren und konfigurieren Sie den RMS-Server zum Testen der rechtlich geschützten Anwendung.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 32C7F387-CF7E-4CE0-AFC9-4C63FE1E134A
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Installieren und Konfigurieren des Servers

In diesem Thema werden die Schritte zum Installieren und Konfigurieren des RMS-Servers zum Testen der rechtlich geschützten Anwendung behandelt.

**Wichtig** Wenn Sie Ihre Anwendung zum Testen in der 1-Box-RMS ISV-Umgebung ausführen werden, müssen Sie keinen RMS-Server nicht installieren, weil in der 1-Box-Umgebung bereits ein RMS-Server installiert und konfiguriert ist.
Weitere Informationen zur 1-Box-RMS ISV-Umgebung finden Sie unter [Einrichten der Testumgebung](how-to-set-up-your-test-environment.md).

 

## Anweisungen

### Schritt 1: Einrichten des RMS-Servers

Die folgenden Schritte führen Sie durch die Einrichtung eines RMS-Servers und umfassen Folgendes:

-   Konfigurieren der Registrierung
-   Installieren des Servers
-   Registrieren des Servers

1.  **Konfigurieren der Registrierung**

    Um anzugeben, dass Sie die Zertifikatshierarchie der Präproduktionsumgebung verwenden, legen Sie die folgenden Registrierungswerte fest.

    **Hinweis** Wenn Sie Windows Server 2008 R2 oder Windows Server 2008 verwenden, legen Sie die Registrierungswerte vor der Installation des AD RMS-Diensts fest.

    Wenn Sie AD RMS unter Windows Server 2008 R2 verwenden, müssen Sie den folgenden **REG\_DWORD**-Wert festlegen. Ändern Sie diesen Wert in 0 (Null), um zur Produktionshierarchie zu wechseln.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**Hierarchy** = 0x00000001

    Wenn Sie AD RMS in Windows Server 2008 R2 verwenden und bereits ein anderer AD RMS-Dienst in Active Directory als Präproduktionsdienst bereitgestellt worden ist, fügen Sie den folgenden leeren Zeichenfolgenwert der Registrierung hinzu.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**GICURL** = ""

    Wenn Sie AD RMS unter Windows Server 2008 verwenden, müssen Sie den folgenden **REG\_DWORD**-Wert festlegen. Ändern Sie diesen Wert in 0 (Null), um zur Produktionshierarchie zu wechseln.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**2.0**\\**Hierarchy** = 0x00000001

    Wenn Sie AD RMS in Windows Server 2008 verwenden und bereits ein anderer AD RMS-Dienst in Active Directory als Präproduktionsdienst bereitgestellt worden ist, fügen Sie den folgenden leeren Zeichenfolgenwert der Registrierung hinzu.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**2.0**\\**GICURL** = ""

2.  **Installieren des Servers**

    AD RMS (Active Directory Rights Management Services) besteht aus separaten Client- und Serverkomponenten. Die Serverkomponente wird als Gruppe von Webdiensten implementiert, die zum Verwalten der RMS-Infrastruktur, Ausstellen von Lizenzen für Verbraucher und Herausgeber von Inhalten und zum Ausstellen von Zertifikaten für Computer und Benutzer verwendet werden kann.

    Ab Windows Server 2008 sind sowohl die Client- als auch die Serverkomponenten im Betriebssystem enthalten. Sie können die Serverkomponenten für frühere Betriebssysteme vom folgenden Speicherort herunterladen.

    -   [RMS Server v1.0 SP2](http://go.microsoft.com/fwlink/p/?linkid=73722)

    Um die Serverkomponente unter Windows Server 2008 zu konfigurieren, müssen Sie die AD RMS-Rolle installieren. Bevor Sie dies tun, müssen Sie jedoch die Registrierung konfigurieren, um anzugeben, dass Sie die Zertifikathierarchie der Präproduktionsumgebung statt der Produktionshierarchie verwenden möchten. Wenn Sie jedoch eine Anwendung für ein früheres Serverbetriebssystem bereitstellen, konfigurieren Sie die Registrierung nach der Installation der RMS-Server v1. 0 SP2, aber vor der Bereitstellung des RMS-Diensts.

    Weitere Informationen finden Sie im vorigen Schritt, Schritt 1, „Konfigurieren der Registrierung“.

3.  **Registrieren des Servers**

    Sie müssen einen RMS (Rights Management Services)-Server registrieren, um ihn in der Präproduktions- oder Produktionshierarchie zu identifizieren. Nach dem Registrierungsprozess bleibt ein lizenzgebendes Serverzertifikat auf dem Servercomputer. Dieses Zertifikat ist mit der vertrauenswürdigen Microsoft-Stammzertifizierungsstelle verkettet. Wie Sie den Server registrieren, hängt von der verwendeten RMS-Version ab.

    -   **Selbstregistrierung**

        Ab Windows Server 2008 können Sie einen RMS-Server in der entsprechenden Hierarchie registrieren, ohne die Informationen an Microsoft zu senden. Bei der Installation der RMS-Serverrolle werden auch ein Selbstregistrierungszertifikat und ein privater Schlüssel installiert. Diese werden zur automatischen Erstellung des lizenzgebenden Serverzertifikats verwendet. Mit Microsoft werden keine Informationen ausgetauscht.

    -   **Onlineregistrierung**Wenn Sie AD RMS 1.0 SP2 verwenden, können Sie den Server online registrieren. Die Registrierung erfolgt im Hintergrund während des Bereitstellungsprozesses, jedoch benötigen Sie eine Internetverbindung, und Sie müssen den entsprechenden Registrierungswert zur Bezeichnung der Hierarchie angeben, in welcher der Server registriert wird. Zur Registrierung in der Präproduktionshierarchie fügen Sie den folgenden **REG\_SZ**-Wert hinzu, und stellen Sie den Server bereit. Zur Registrierung in der Produktionshierarchie löschen Sie diesen Wert, und stellen Sie den Server bereit.

        Weitere Informationen finden Sie im vorigen Schritt, Schritt 1, „Konfigurieren der Registrierung“.

        **HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**1.0**\\**UddiProvider** = 0e3d9bb8-b765-4a68-a329-51548685fed3

## Verwandte Themen

* [Vorgehensweise](how-to-use-msipc.md)
 

 





<!--HONumber=Apr16_HO4-->


