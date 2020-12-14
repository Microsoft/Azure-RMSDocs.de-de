---
title: Migrieren von AD RMS-Azure Information Protection – Phase 3
description: Phase 3 der Migration von AD RMS zu Azure Information Protection deckt den Schritt 7 der Migration von AD RMS zu Azure Information Protection ab.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/11/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.subservice: migration
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: d0c643ea787d8ef9a977930aee270af5023c89a7
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97381526"
---
# <a name="migration-phase-3---client-side-configuration"></a>Migrationsphase 3: Clientseitige Konfiguration

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Verwenden Sie die folgenden Informationen für Phase 3 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken den Schritt 7 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.

## <a name="step-7-reconfigure-windows-computers-to-use-azure-information-protection"></a>Schritt 7. Neukonfigurieren von Windows-Computern zur Verwendung von Azure Information Protection

Konfigurieren Sie Ihre Windows-Computer so neu, dass Sie Azure Information Protection mithilfe einer der folgenden Methoden verwenden:

- **DNS-Umleitung**. Einfachste und bevorzugte Methode, wenn Sie unterstützt wird. 

    Unterstützt für Windows-Computer, die Office 2016 oder spätere Click-to-Run-Desktop-Apps verwenden, einschließlich:

    - Microsoft 365-Apps
    - Office 2019
    - Office 2016 klicken zum Ausführen von Desktop-Apps

    Erfordert, dass Sie einen neuen SRV-Datensatz erstellen und eine NTFS-DENY-Berechtigung für Benutzer am Endpunkt für die AD RMS Veröffentlichung festlegen.

    Weitere Informationen finden Sie unter [Neukonfiguration des Clients mithilfe der DNS-Umleitung](#client-reconfiguration-by-using-dns-redirection).

- Bearbeitbare **Änderungen der Registrierung**. Relevant für alle unterstützten Umgebungen, einschließlich der folgenden:

    - Windows-Computer, die Office 2016 oder höher verwenden, klicken, um Desktop-Apps wie oben aufgeführt zu starten
    - Windows-Computer, die andere apps verwenden
    
    Nehmen Sie die erforderlichen Registrierungs Änderungen manuell vor, oder bearbeiten und stellen Sie herunterladbare Skripts bereit, um die Registrierung für Sie zu ändern.

    Weitere Informationen finden Sie unter [Neukonfiguration des Clients mithilfe von Registrierungs Änderungen](#client-reconfiguration-by-using-registry-edits).


> [!TIP]
> Wenn Sie über eine Mischung aus Office-Versionen verfügen, für die keine DNS-Umleitung verwendet werden kann, können Sie entweder eine Kombination aus DNS-Umleitung verwenden und die Registrierung bearbeiten oder die Registrierung als einzelne Methode für alle Windows-Computer bearbeiten.


## <a name="client-reconfiguration-by-using-dns-redirection"></a>Clientneukonfiguration mithilfe der DNS-Umleitung

Diese Methode eignet sich nur für Windows-Clients, die Microsoft 365-apps und Office 2016 (oder höher)-Click-to-Run-Desktop-Apps ausführen. 

1. Erstellen Sie einen DNS-SRV-Eintrag im folgenden Format:
    
    ```sh
    _rmsredir._http._tcp.<AD RMS cluster>. <TTL> IN SRV <priority> <weight> <port> <your tenant URL>.
    ```
    
    Geben Sie für den voll qualifizierten Namen *\<AD RMS cluster>* Ihres AD RMS Clusters an. Dies kann zum Beispiel **rmscluster.contoso.com** sein.
    
    Wenn Sie nur über einen AD RMS-Cluster in dieser Domäne verfügen, können Sie alternativ auch nur den Domänennamen des AD RMS-Clusters angeben. In unserem Beispiel ist dies **contoso.com**. Wenn Sie den Domänennamen in diesem Eintrag angeben, gilt die Umleitung für jeden AD RMS-Cluster in der Domäne.
    
    Die *\<port>* Zahl wird ignoriert.
    
    Geben Sie für Ihren Mandanten *\<your tenant URL\>* Ihre eigene [Azure Rights Management-Dienst-URL an](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).
    
    Wenn Sie die DNS-Serverrolle in Windows Server verwenden, können Sie sich beim Festlegen der SRV-Eintragseigenschaften in der DNS-Manager-Konsole an der folgenden Tabelle orientieren:
    
    |Feld|Wert|  
    |-----------|-----------|  
    |**Domäne**|_tcp.rmscluster.contoso.com|  
    |**Service**|_rmsredir|  
    |**Protokoll**|_http|  
    |**Priority**|0|  
    |**Weight**|0|  
    |**Portnummer**|80|  
    |**Host, der diesen Dienst anbietet**|5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com|  
    | | |

2. Legen Sie für Benutzer, die Microsoft 365 Apps oder Office 2016 (oder höher) ausführen, eine DENY-Berechtigung für den AD RMS Veröffentlichungs Endpunkt fest:

    a. Starten Sie die IIS-Manager-Konsole auf einem der AD RMS-Server im Cluster.

    b. Navigieren Sie zur **Standard Website** , und erweitern Sie **_wmcs**.

    c. Klicken Sie mit der rechten Maustaste auf **Lizenzierung** , und wählen Sie **zur Inhaltsansicht wechseln**

    d. Klicken Sie im Detailfenster mit der rechten Maustaste auf **License. asmx**-  >  **Eigenschaften**  >  **Bearbeiten** .

    e. Wählen Sie im Dialogfeld **Berechtigungen für Lizenz. asmx** entweder **Benutzer** aus, wenn Sie die Umleitung für alle Benutzer festlegen möchten, oder klicken Sie auf **Hinzufügen** , und geben Sie dann eine Gruppe an, die die Benutzer enthält, die Sie umleiten möchten.
    
    Auch wenn alle Ihre Benutzer eine Version von Office verwenden, die DNS-Umleitung unterstützt, kann es sinnvoll sein, zunächst nur einen Teil der Benutzer festzulegen und eine phasenweise Migration durchzuführen.
    
    f. Wählen Sie für die ausgewählte Gruppe **Verweigern** für die Berechtigungen **Lesen & Ausführen** und **Lesen** aus, und klicken Sie anschließend zweimal auf **OK**.

    g. Um zu überprüfen, ob die Konfiguration ordnungsgemäß funktioniert, versuchen Sie, eine Verbindung mit der Datei „licencing.asmx“ direkt über einen Browser herzustellen. Die folgende Fehlermeldung sollte angezeigt werden, die bewirkt, dass der Client, der Microsoft 365-Apps oder Office 2019 oder Office 2016 ausgeführt wird, nach dem SRV-Datensatz sucht:
    
    **Fehlermeldung 401.3: You do not have permissions to view this directory or page using the credentials you supplied (access denied due to Access Control Lists)** (Mit den bereitgestellten Anmeldeinformationen haben Sie keine Berechtigung zum Anzeigen dieses Verzeichnisses oder dieser Seite (Zugriff aufgrund von Zugriffssteuerungslisten verweigert)).


## <a name="client-reconfiguration-by-using-registry-edits"></a>Clientneukonfiguration mithilfe von Änderungen an der Registrierung

Diese Methode eignet sich für alle Windows-Clients und sollte verwendet werden, wenn Sie nicht Microsoft 365-Apps oder Office 2016 (oder höher) ausgeführt werden. Diese Methode verwendet zwei Migrationsskripts zur Neukonfiguration von AD RMS-Clients:

- Migrate-Client.cmd

- Migrate-User.cmd

Das Konfigurationsskript für den Client (Migrate-Client.cmd) konfiguriert die Einstellungen in der Registrierung auf Computerebene. Das bedeutet, dass es in einem Sicherheitskontext ausgeführt werden muss, in dem diese Änderungen vorgenommen werden können. Dies bezieht sich üblicherweise auf eine der folgenden Methoden:

- Verwenden Sie die Gruppenrichtlinien, um das Skript als Startskript für den Computer zu verwenden.

- Verwenden Sie die Softwareinstallation der Gruppenrichtlinien, um das Skript dem Computer zuzuweisen.

- Verwenden Sie eine Lösung für die Softwarebereitstellung, um das Skript für die Computer bereitzustellen. Verwenden Sie beispielsweise die [Pakete und Programme](/sccm/apps/deploy-use/packages-and-programs) von System Center Configuration Manager. Geben Sie in den Eigenschaften des Pakets und des Programms unter **Ausführungsmodus** an, dass das Skript auf dem Gerät mit Administratorberechtigungen ausgeführt wird. 

- Verwenden Sie ein Anmeldeskript, wenn der Benutzer über lokale Administratorrechte verfügt.

Das Konfigurationsskript für den Benutzer (Migrate-User.cmd) konfiguriert die Einstellungen auf Benutzerebene und bereinigt den Lizenzspeicher des Clients. Das bedeutet, dass dieses Skript im Kontext des tatsächlichen Benutzers ausgeführt werden muss. Zum Beispiel:

- Verwenden Sie ein Anmeldeskript.

- Verwenden Sie die Softwareinstallation der Gruppenrichtlinien, um das Skript für die Ausführung durch den Benutzer zu veröffentlichen.

- Verwenden Sie eine Lösung für die Softwarebereitstellung, um das Skript für die Benutzer bereitzustellen. Verwenden Sie beispielsweise die [Pakete und Programme](/sccm/apps/deploy-use/packages-and-programs) von System Center Configuration Manager. Geben Sie in den Eigenschaften des Pakets und des Programms unter **Ausführungsmodus** an, dass das Skript mit den Berechtigungen des Benutzers ausgeführt wird. 

- Fordern Sie den Benutzer zum Ausführen des Skripts auf, wenn dieser an seinem Benutzer angemeldet ist.

Beide Skripts enthalten eine Versionsnummer und werden nicht erneut ausgeführt, bis diese Versionsnummer geändert wird. Das bedeutet, dass Sie die Skripts belassen können, bis die Migration abgeschlossen ist. Wenn Sie jedoch Änderungen an dem Skript vornehmen, das von Benutzern und Computern erneut auf deren Windows-Computern ausgeführt werden soll, aktualisieren Sie die folgende Zeile in beiden Skripts auf einen höheren Wert:

```sh
SET Version=20170427
```

Das Konfigurationsskript für Benutzer wurde dafür entworfen, nach dem Konfigurationsskript für den Client ausgeführt zu werden und verwendet bei dieser Überprüfung die Versionsnummer. Es wird angehalten, wenn das Konfigurationsskript für den Client mit der gleichen Version nicht ausgeführt wurde. Durch diese Überprüfung wird sichergestellt, dass die beiden Skripts in der richtigen Reihenfolge ausgeführt werden. 

Wenn Sie nicht alle Ihre Windows-Clients gleichzeitig migrieren können, führen Sie die folgenden Prozeduren für Clientbatches aus. Fügen Sie jeden Benutzer, der über einen Windows-Computer verfügt, den Sie in Ihren Batch migrieren möchten, zur **AIPMigrated**-Gruppe hinzu, die Sie zuvor erstellt haben.

### <a name="modifying-the-scripts-for-registry-edits"></a>Modifizieren von Skripts für Registrierungsbearbeitungen

1. Kehren Sie zu den Migrationsskripts **Migrate-Client.cmd** und **Migrate-User.cmd** zurück, die Sie zuvor beim Herunterladen dieser Skripts in der [Vorbereitungsphase](migrate-from-ad-rms-phase1.md#step-2-prepare-for-client-migration) extrahiert haben.

2. Befolgen Sie die Anweisungen in **Migrate-Client. cmd** , um das Skript so zu ändern, dass es die URL des Azure-Rights Management Dienstanbieter Ihres Mandanten enthält, sowie die Servernamen für Ihre AD RMS Cluster-extranetlizenzierungs-URL und die URL für die Intranet Erhöhen Sie dann wie zuvor erläutert die Version des Skripts. Zum Nachverfolgen von Skript Versionen empfiehlt es sich, das heutige Datum im folgenden Format zu verwenden: YYYYMMDD
    
   > [!IMPORTANT]
   > Achten Sie auch hier wieder darauf, keine zusätzlichen Leerzeichen vor oder nach Ihren Adressen einzufügen.
   > 
   > Wenn Ihre AD RMS-Server zusätzlich SSL/TLS-Serverzertifikate verwenden, überprüfen Sie, ob die Werte der Lizenzierungs-URL die Portnummer **443** in der Zeichenfolge enthalten. Beispiel: https://rms.treyresearch.net:443/_wmcs/licensing. Diese Informationen können Sie in der Active Directory Rights Management Services-Konsole finden, wenn Sie auf den Clusternamen klicken und sich die **Clusterdetails** ansehen. Wenn Sie sehen, dass die URL die Portnummer 443 enthält, fügen Sie diesen Wert beim Ändern des Skripts hinzu. Beispiel: https://rms.treyresearch.net:<strong>443</strong>. 
    
   Wenn Sie Ihre Azure Rights Management Service-URL für *&lt; yourtenanturl &gt;* abrufen müssen, informieren Sie sich unter, [um Ihre Azure Rights Management Dienst-URL zu identifizieren](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3. Konfigurieren Sie Ihre Skriptbereitstellungsmethoden mithilfe der Anweisungen am Anfang dieses Schritts, um **Migrate-Client.cmd** und **Migrate-User.cmd** auf den Windows-Clientcomputern auszuführen, die von den Mitgliedern der Gruppe „AIPMigrated“ verwendet werden. 

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit [Phase 4: Unterstützung der Dienstekonfiguration](migrate-from-ad-rms-phase4.md) fort, um die Migration fortzusetzen.
