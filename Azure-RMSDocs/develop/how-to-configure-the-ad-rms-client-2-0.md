---
# required metadata

title: Konfigurieren des Clients | Azure RMS
description: Anleitung zum Konfigurieren des Active Directory Rights Management Services-Clients 2.1.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 74C342BF-0F79-486D-AED7-C53230DE5FA7
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurieren des Clients

Dieses Thema enthält eine Anleitung zum Konfigurieren des Active Directory Rights Management Services-Clients 2.1.

**Wichtig** Wenn Sie Ihre Anwendung zum Testen in der 1-Box-RMS ISV-Umgebung ausführen werden, müssen Sie den AD RMS-Client 2.1 nicht konfigurieren. Weitere Informationen finden Sie unter [Testen Ihrer rechtlich geschützten Anwendung](running-your-first-application.md).

 

### Voraussetzungen

-   Sie müssen den AD RMS-Client 2.1 auf dem Computer installieren, auf dem Sie die Anwendung testen.

    -   Wenn Sie Ihre Anwendung auf Ihrem Entwicklungscomputer testen, dann sollte das Rights Management Services SDK 2.1 bereits installiert sein. Der AD RMS-Client 2.1 wurde zu diesem Zeitpunkt im Hintergrund installiert.

        Informationen zum Installieren des RMS SDK 2.1 finden Sie unter [Installieren des SDKs](create-your-first-rights-aware-application.md).

    -   Wenn Sie Ihre Anwendung auf einem anderem Computer als Ihrem Entwicklungscomputer testen, installieren Sie den AD RMS-Client 2.1 von der [AD RMS-Client 2.1-Downloadseite](http://www.microsoft.com/en-us/download/details.aspx?id=38396) auf diesem Computer.
        **Hinweis** Wenn die Anwendung den Server-API-Modus (**IPC\_API\_MODE\_SERVER**) verwendet, ist kein Anwendungsmanifest erforderlich. Sie können Ihre Anwendung mit einem RMS-Produktionsserver testen. Beim Wechsel zur Produktionsumgebung müssen Sie keine Produktionslizenz beziehen. Weitere Informationen zu Servermodusanwendungen finden Sie unter [Anwendungstypen](application-types.md).

         

-   Sie müssen einen RMS-Server installiert und für die Arbeit in der Präproduktionsumgebung konfiguriert haben. Weitere Informationen finden Sie unter [Installieren und Konfigurieren des Servers](how-to-install-and-configure-an-rms-server.md).

Anweisungen

### Schritt 1: Einrichten des RMS-Clients 2.1 für die Zertifikatshierarchie in der Präproduktionsumgebung

Die folgenden Schritte beschreiben, wie Sie die Developer-Laufzeit installieren, den Client für die Verwendung der ISV-Zertifikathierarchie (der Präproduktionsumgebung) konfigurieren und die Dienstermittlung auf dem Client einrichten.

1.  Kopieren Sie die Developer-Laufzeit „Ipcsecproc\_isv.dll“ aus dem Ordner „%MSIPCSDKDIR%\\bin\\x86“ (für 32-Bit-Versionen von Windows) bzw. „%MSIPCSDKDIR\\bin\\x64“ (für 64-Bit-Versionen von Windows) in den Ordner „C:\\Programme\\Active Directory Rights Management Services Client 2.1“.

    **Wichtig** Wenn Sie eine 32-Bit-Anwendung unter einer 64-Bit-Version von Windows ausführen, müssen Sie „Ipcsecproc\_isv.dll“ von „%MSIPCSDKDIR%\\bin\\x86“ in den Ordner „C:\\Programme(x86)\\Active Directory Rights Management Services Client 2.1“ kopieren.

     

2.  Konfigurieren Sie den AD RMS-Client 2.1, sodass er die ISV-Zertifikathierarchie (Präproduktion) verwendet, indem Sie den **Hierarchy**-Registrierungsschlüsselwert auf 1 festlegen.

    ```
    HKEY_LOCAL_MACHINE
       SOFTWARE
          Microsoft
             MSIPC
                Hierarchy DWORD = 00000001
                Data type
                DWORD
    ```

    **Hinweis** Wenn der **Hierarchy**-Wert in der Registrierung fehlt, hat dies die gleiche Bedeutung wie die Festlegung des Werts auf 0 (Null), das heißt, dass RMS SDK 2.1 im Produktionsmodus ausgeführt wird. Weitere Informationen zu Schlüsseln und Zertifikatketten finden Sie unter [Grundlegendes zu Zertifikatketten](understanding-certificate-chains.md).

    **Wichtig**  
    Wenn Sie eine 32-Bit-Anwendung unter einer 64-Bit-Version von Windows ausführen, müssen Sie den **Hierarchy**-Wert im folgenden Registrierungsschlüsselpfad festlegen:

    ```
    HKEY_LOCAL_MACHINE
        SOFTWARE
           Wow6432Node
              Microsoft
                MSIPC
    ```
     

3.  Konfigurieren Sie die serverseitige Ermittlung oder die clientseitige Ermittlung, damit der AD RMS-Client 2.1 den RMS-Server in der Präproduktionsumgebung erkennen und die Kommunikation mit ihm aufbauen kann.

    -   Bei der serverseitigen Ermittlung registriert der Administrator einen Dienstverbindungspunkt (SCP) für das RMS-Stammcluster der Präproduktionsumgebung bei Active Directory und der Client fragt Active Directory ab, um den SCP zu ermitteln und eine Verbindung mit dem Server herzustellen.
    -   Bei der clientseitigen Ermittlung konfigurieren Sie auf dem Computer, auf dem der AD RMS-Client 2.1 ausgeführt wird, RMS-Dienstermittlungseinstellungen in der Registrierung. Diese Einstellungen verweisen den AD RMS-Client 2.1 auf den zu verwendenden RMS-Server. Wenn sie vorhanden sind, wird keine serverseitige Ermittlung ausgeführt.

    Zum Konfigurieren der clientseitigen Ermittlung können Sie die folgenden Registrierungsschlüssel auf dem RMS-Server in der Präproduktionsumgebung festlegen. Informationen zum Konfigurieren der Ermittlung aufseiten des Dienstes finden Sie unter [Hinweise zur Bereitstellung des RMS-Clients 2.0](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx).

|Key|Wert|
|---|-----|
|`HKEY_LOCAL_MACHINE\`<br>`SOFTWARE\`<br>`Microsoft\`<br>`MSIPC\`<br>`ServiceLocation\`<br>`EnterpriseCertification`|(Default):<br><br> [**http**&#124;**https**]**://** *RMSClusterName* **/_wmcs/Certification**|
|`HKEY_LOCAL_MACHINE\`<br>`SOFTWARE\`<br>`Microsoft\`<br>`MSIPC\`<br>`ServiceLocation\`<br>`EnterprisePublishing`|(Default):<br><br> [**http**&#124;**https**]**://** *RMSClusterName* **/_wmcs/Licensing**|


**Hinweis** Standardmäßig sind diese Schlüssel nicht in der Registrierung vorhanden, sie müssen erstellt werden.
     
**Wichtig**  
    Wenn Sie eine 32-Bit-Anwendung unter einer 64-Bit-Version von Windows ausführen, müssen Sie diese Schlüssel im folgenden Schlüsselpfad festlegen:


    HKEY_LOCAL_MACHINE
        SOFTWARE
           Wow6432Node
              Microsoft
                MSIPC
    

### Hinweise

Die Anleitung in diesem Thema ist nicht vollständig. Detaillierte Informationen zum Konfigurieren des AD RMS Clients 2.1 finden Sie unter [Hinweise zur Bereitstellung des RMS-Clients 2.0](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx).

## Verwandte Themen


* [Vorgehensweise](how-to-use-msipc.md)
* [Hinweise zur Bereitstellung des RMS-Clients 2.0](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx)
* [Installieren des SDKs](create-your-first-rights-aware-application.md)
* [Installieren und Konfigurieren des Servers](how-to-install-and-configure-an-rms-server.md)
* [Testen Ihrer rechtlich geschützten Anwendungen](running-your-first-application.md)
* [Grundlegendes zu Zertifikatketten](understanding-certificate-chains.md)
 

 


<!--HONumber=Apr16_HO4-->


