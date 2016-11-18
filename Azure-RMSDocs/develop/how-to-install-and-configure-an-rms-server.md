---
title: 'Gewusst wie: Installieren, Konfigurieren und Testen mit einem RMS-Server | Azure RMS'
description: "Installieren und konfigurieren Sie den RMS-Server zum Testen der rechtlich geschützten Anwendung."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 32C7F387-CF7E-4CE0-AFC9-4C63FE1E134A
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 47f9cf725b864ee22afc7605702992b08cb686dc


---

# <a name="howto-install-configure-and-test-with-an-rms-server"></a>Exemplarische Vorgehensweise: Installieren, Konfigurieren und Testen mit einem RMS-Server

In diesem Thema werden die Schritte zum Herstellen einer Verbindung mit einem RMS-Server oder Azure RMS zum Testen der rechtlich geschützten Anwendung behandelt.
 
## <a name="instructions"></a>Anweisungen

### <a name="step-1-setup-your-rms-server"></a>Schritt 1: Einrichten des RMS-Servers

Die folgenden Schritte führen Sie durch die Einrichtung eines RMS-Servers und umfassen Folgendes:

-   Installieren des Servers
-   Registrieren des Servers

1.  **Installieren des Servers**

    AD RMS (Active Directory Rights Management Services) besteht aus separaten Client- und Serverkomponenten. Die Serverkomponente wird als Gruppe von Webdiensten implementiert, die zum Verwalten der RMS-Infrastruktur, Ausstellen von Lizenzen für Verbraucher und Herausgeber von Inhalten und zum Ausstellen von Zertifikaten für Computer und Benutzer verwendet werden kann.

    Ab Windows Server 2008 sind sowohl die Client- als auch die Serverkomponenten im Betriebssystem enthalten. Sie können die Serverkomponenten für frühere Betriebssysteme vom folgenden Speicherort herunterladen.

    -   [RMS Server v1.0 SP2](http://go.microsoft.com/fwlink/p/?linkid=73722)

    Um die Serverkomponente unter Windows Server 2008 zu konfigurieren, müssen Sie die AD RMS-Rolle installieren. Wenn Sie jedoch eine Anwendung für ein früheres Serverbetriebssystem bereitstellen, konfigurieren Sie die Registrierung nach der Installation von RMS Server v1.0 SP2, aber vor der Bereitstellung des RMS-Diensts.

2.  **Registrieren des Servers**

    Sie müssen einen RMS (Rights Management Services)-Server registrieren, um ihn in der Präproduktions- oder Produktionshierarchie zu identifizieren. Nach dem Registrierungsprozess bleibt ein lizenzgebendes Serverzertifikat auf dem Servercomputer. Dieses Zertifikat ist mit der vertrauenswürdigen Microsoft-Stammzertifizierungsstelle verkettet. Wie Sie den Server registrieren, hängt von der verwendeten RMS-Version ab.

    -   **Selbstregistrierung**

        Ab Windows Server 2008 können Sie einen RMS-Server in der entsprechenden Hierarchie registrieren, ohne die Informationen an Microsoft zu senden. Bei der Installation der RMS-Serverrolle werden auch ein Selbstregistrierungszertifikat und ein privater Schlüssel installiert. Diese werden zur automatischen Erstellung des lizenzgebenden Serverzertifikats verwendet. Mit Microsoft werden keine Informationen ausgetauscht.

    -   **Onlineregistrierung**

        Wenn Sie AD RMS 1.0 SP2 verwenden, können Sie den Server online registrieren. Die Registrierung findet während des Bereitstellungsvorgangs im Hintergrund statt; Sie müssen jedoch über eine Internetverbindung verfügen.

        **HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**1.0**\\**UddiProvider** = 0e3d9bb8-b765-4a68-a329-51548685fed3

3. **Testen mit einem RMS-Server**

    Konfigurieren Sie zum Testen mit einem RMS-Server die serverseitige Ermittlung oder die clientseitige Ermittlung, damit der Rights Management Service Client 2.1 den RMS-Server erkennen und die Kommunikation mit ihm aufbauen kann.

    > [!Note]
    > Beim Testen mit Azure RMS muss keine Ermittlung konfiguriert werden.

  - Bei der serverseitigen Ermittlung registriert der Administrator einen Dienstverbindungspunkt (SCP) für den RMS-Stammcluster bei Active Directory, und der Client fragt Active Directory ab, um den SCP zu ermitteln und eine Verbindung mit dem Server herzustellen.
  - Bei der clientseitigen Ermittlung konfigurieren Sie auf dem Computer, auf dem der RMS-Client 2.1 ausgeführt wird, RMS-Dienstermittlungseinstellungen in der Registrierung. Diese Einstellungen verweisen den RMS-Client 2.1 auf den zu verwendenden RMS-Server. Wenn sie vorhanden sind, wird keine serverseitige Ermittlung ausgeführt.

  Zum Konfigurieren der clientseitigen Ermittlung können Sie die folgenden Registrierungsschlüssel festlegen, dass sie auf den RMS-Server verweisen. Informationen zum Konfigurieren der dienstseitigen Ermittlung finden Sie in den [Anmerkungen zur Bereitstellung des RMS-Clients 2.0](https://technet.microsoft.com/library/jj159267(WS.10).aspx).

1. **EnterpriseCertification**

        HKEY_LOCAL_MACHINE
          SOFTWARE
            Microsoft
              MSIPC
                ServiceLocation
                  EnterpriseCertification

   **Value**: (Default): [**http|https**]://RMSClusterName/**_wmcs/Certification**

2. **EnterprisePublishing**

        HKEY_LOCAL_MACHINE
          SOFTWARE
            Microsoft
              MSIPC
                ServiceLocation
                  EnterprisePublishing
                  
   **Value**: (Default): [**http|https**]://RMSClusterName/**_wmcs/Licensing**

>[!NOTE] 
> Standardmäßig sind diese Schlüssel nicht in der Registrierung vorhanden, und sie müssen erstellt werden.

>[!IMPORTANT] 
> Wenn Sie eine 32-Bit-Anwendung unter einer 64-Bit-Version von Windows ausführen, müssen Sie diese Schlüssel im folgenden Schlüsselpfad festlegen:<p>
  ```    
  HKEY_LOCAL_MACHINE
    SOFTWARE
      Wow6432Node
        Microsoft
          MSIPC
            ```

 

 



<!--HONumber=Nov16_HO2-->


