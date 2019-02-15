---
title: Migrieren von AD RMS-Azure Information Protection – Phase 3
description: Phase 3 der Migration von AD RMS zu Azure Information Protection deckt den Schritt 7 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 01/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: bdd5d17bc947b25f312baa498da057b409dcd07e
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56256973"
---
# <a name="migration-phase-3---client-side-configuration"></a>Migrationsphase 3: Clientseitige Konfiguration

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Verwenden Sie die folgenden Informationen für Phase 3 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken den Schritt 7 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.

## <a name="step-7-reconfigure-windows-computers-to-use-azure-information-protection"></a>Schritt 7: Neukonfigurieren von Windows-Computern zur Verwendung von Azure Information Protection

Für Windows-Computer, die Office 365-Apps, Office 2019- oder Office 2016-Klick-und-Los-Desktop-Apps verwenden:

- Sie können diese Clients mit der DNS-Umleitung so neu konfigurieren, dass sie Azure Information Protection verwenden. Dies ist die bevorzugte Methode der Clientmigration, da sie die unkomplizierteste ist. Diese Methode ist allerdings auf Klick-und-Los-Desktopanwendungen von Office 2016 und höher für Windows-Computer beschränkt.
    
    Für diese Methode müssen Sie einen neuen SRV-Eintrag erstellen und für Benutzer auf dem AD RMS-Veröffentlichungsendpunkt eine NTFS-DENY-Berechtigung festlegen.

- Für Windows-Computer, die keine Office 2016- oder Office 2019-Klick-und-Los-Desktop-Apps verwenden:
    
    Sie können die DNS-Umleitung nicht verwenden und müssen stattdessen Änderungen an der Registrierung vornehmen. Wenn Sie eine Mischung aus Office-Versionen verwenden, die nur zum Teil mit DNS-Umleitung umgehen können, können Sie diese einzelne Methode für alle Windows-Computer oder eine Kombination aus der DNS-Umleitung und dem Ändern der Registrierung verwenden. 
    
    Änderungen der Registrierung werden Ihnen erleichtert, da Sie Skripts, die zum Download zur Verfügung stehen, bearbeiten und bereitstellen können. 

Weitere Informationen zum Neukonfigurieren der Windows-Clients finden Sie in den folgenden Abschnitten.

## <a name="client-reconfiguration-by-using-dns-redirection"></a>Clientneukonfiguration mithilfe der DNS-Umleitung

Diese Methode eignet sich nur für Windows-Clients, auf denen Klick-und-Los-Desktop-Apps von Office 365 und Office 2016 (oder höher) ausgeführt werden. 

1. Erstellen Sie einen DNS-SRV-Eintrag im folgenden Format:
    
    `_rmsredir._http._tcp.<AD RMS cluster>. <TTL> IN SRV <priority> <weight> <port> <your tenant URL>.`
    
    Geben Sie für *\<AD RMS cluster>* den FQDN Ihres AD RMS-Clusters an. Dies kann zum Beispiel **rmscluster.contoso.com** sein.
    
    Wenn Sie nur über einen AD RMS-Cluster in dieser Domäne verfügen, können Sie alternativ auch nur den Domänennamen des AD RMS-Clusters angeben. In unserem Beispiel ist dies **contoso.com**. Wenn Sie den Domänennamen in diesem Eintrag angeben, gilt die Umleitung für jeden AD RMS-Cluster in der Domäne.
    
    Die *\<port>*-Nummer wird ignoriert.
    
    Ersetzen Sie Ihre eigene [Azure Rights Management-Dienst-URL für Ihren Mandanten](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url) durch die *\<URL Ihres Mandanten\>*.
    
    Wenn Sie die DNS-Serverrolle in Windows Server verwenden, können Sie sich beim Festlegen der SRV-Eintragseigenschaften in der DNS-Manager-Konsole an der folgenden Tabelle orientieren:
    
    |Feld|Wert|  
    |-----------|-----------|  
    |**Domäne**|_tcp.rmscluster.contoso.com|  
    |**Dienst**|_rmsredir|  
    |**Protokoll**|_http|  
    |**Priorität**|0|  
    |**Gewichtung**|0|  
    |**Portnummer**|80|  
    |**Host, der diesen Dienst anbietet**|5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com|  

2. Legen Sie auf dem AD RMS-Veröffentlichungsendpunkt für Benutzer, die Office 365-Apps oder Office 2016 (oder höher) ausführen, eine Ablehnungsberechtigung fest:

    ein. Starten Sie die IIS-Manager-Konsole auf einem der AD RMS-Server im Cluster.

    b. Navigieren Sie zur **Standardwebsite** > **_wmcs** > **licensing** > **licensing.asmx**

    c. Klicken Sie mit der rechten Maustaste auf **licensing.asmx** > **Eigenschaften** > **Bearbeiten**

    d. Im Dialogfeld **Berechtigungen für licensing.asmx** wählen Sie entweder **Benutzer**, wenn Sie die Umleitung für alle Benutzer festlegen möchten, oder Sie klicken auf **Hinzufügen**, und geben dann eine Gruppe mit den Benutzern an, die Sie umleiten möchten.
    
    Auch wenn alle Ihre Benutzer eine Version von Office verwenden, die DNS-Umleitung unterstützt, kann es sinnvoll sein, zunächst nur einen Teil der Benutzer festzulegen und eine phasenweise Migration durchzuführen.
    
    e. Wählen Sie für die ausgewählte Gruppe **Verweigern** für die Berechtigungen **Lesen & Ausführen** und **Lesen** aus, und klicken Sie anschließend zweimal auf **OK**.

    f. Um zu überprüfen, ob die Konfiguration ordnungsgemäß funktioniert, versuchen Sie, eine Verbindung mit der Datei „licencing.asmx“ direkt über einen Browser herzustellen. Sie sollten die folgende Fehlermeldung erhalten, wodurch der Client, der Office 365-Apps, Office 2019 oder Office 2016 ausführt, nach dem SRV-Eintrag sucht:
    
    **Fehlermeldung 401.3: You do not have permissions to view this directory or page using the credentials you supplied (access denied due to Access Control Lists)** (Mit den bereitgestellten Anmeldeinformationen haben Sie keine Berechtigung zum Anzeigen dieses Verzeichnisses oder dieser Seite (Zugriff aufgrund von Zugriffssteuerungslisten verweigert)).


## <a name="client-reconfiguration-by-using-registry-edits"></a>Clientneukonfiguration mithilfe von Änderungen an der Registrierung

Diese Methode eignet sich für alle Windows-Clients und sollte verwendet werden, wenn diese keine Office 365-Apps, Office 2019 oder Office 2016, sondern stattdessen eine frühere Version von Office ausführen. Diese Methode verwendet zwei Migrationsskripts zur Neukonfiguration von AD RMS-Clients:

- Migrate-Client.cmd

- Migrate-User.cmd

Das Konfigurationsskript für den Client (Migrate-Client.cmd) konfiguriert die Einstellungen in der Registrierung auf Computerebene. Das bedeutet, dass es in einem Sicherheitskontext ausgeführt werden muss, in dem diese Änderungen vorgenommen werden können. Dies bezieht sich üblicherweise auf eine der folgenden Methoden:

- Verwenden Sie die Gruppenrichtlinien, um das Skript als Startskript für den Computer zu verwenden.

- Verwenden Sie die Softwareinstallation der Gruppenrichtlinien, um das Skript dem Computer zuzuweisen.

- Verwenden Sie eine Lösung für die Softwarebereitstellung, um das Skript für die Computer bereitzustellen. Verwenden Sie beispielsweise die [Pakete und Programme](/sccm/apps/deploy-use/packages-and-programs) von System Center Configuration Manager. Geben Sie in den Eigenschaften des Pakets und des Programms unter **Ausführungsmodus** an, dass das Skript auf dem Gerät mit Administratorberechtigungen ausgeführt wird. 

- Verwenden Sie ein Anmeldeskript, wenn der Benutzer über lokale Administratorrechte verfügt.

Das Konfigurationsskript für den Benutzer (Migrate-User.cmd) konfiguriert die Einstellungen auf Benutzerebene und bereinigt den Lizenzspeicher des Clients. Das bedeutet, dass dieses Skript im Kontext des tatsächlichen Benutzers ausgeführt werden muss. Beispiel:

- Verwenden Sie ein Anmeldeskript.

- Verwenden Sie die Softwareinstallation der Gruppenrichtlinien, um das Skript für die Ausführung durch den Benutzer zu veröffentlichen.

- Verwenden Sie eine Lösung für die Softwarebereitstellung, um das Skript für die Benutzer bereitzustellen. Verwenden Sie beispielsweise die [Pakete und Programme](/sccm/apps/deploy-use/packages-and-programs) von System Center Configuration Manager. Geben Sie in den Eigenschaften des Pakets und des Programms unter **Ausführungsmodus** an, dass das Skript mit den Berechtigungen des Benutzers ausgeführt wird. 

- Fordern Sie den Benutzer zum Ausführen des Skripts auf, wenn dieser an seinem Benutzer angemeldet ist.

Beide Skripts enthalten eine Versionsnummer und werden nicht erneut ausgeführt, bis diese Versionsnummer geändert wird. Das bedeutet, dass Sie die Skripts belassen können, bis die Migration abgeschlossen ist. Wenn Sie jedoch Änderungen an dem Skript vornehmen, das von Benutzern und Computern erneut auf deren Windows-Computern ausgeführt werden soll, aktualisieren Sie die folgende Zeile in beiden Skripts auf einen höheren Wert:

    SET Version=20170427

Das Konfigurationsskript für Benutzer wurde dafür entworfen, nach dem Konfigurationsskript für den Client ausgeführt zu werden und verwendet bei dieser Überprüfung die Versionsnummer. Es wird angehalten, wenn das Konfigurationsskript für den Client mit der gleichen Version nicht ausgeführt wurde. Durch diese Überprüfung wird sichergestellt, dass die beiden Skripts in der richtigen Reihenfolge ausgeführt werden. 

Wenn Sie nicht alle Ihre Windows-Clients gleichzeitig migrieren können, führen Sie die folgenden Prozeduren für Clientbatches aus. Fügen Sie jeden Benutzer, der über einen Windows-Computer verfügt, den Sie in Ihren Batch migrieren möchten, zur **AIPMigrated**-Gruppe hinzu, die Sie zuvor erstellt haben.

### <a name="modifying-the-scripts-for-registry-edits"></a>Modifizieren von Skripts für Registrierungsbearbeitungen

1. Kehren Sie zu den Migrationsskripts **Migrate-Client.cmd** und **Migrate-User.cmd** zurück, die Sie zuvor beim Herunterladen dieser Skripts in der [Vorbereitungsphase](migrate-from-ad-rms-phase1.md#step-2-prepare-for-client-migration) extrahiert haben.

2. Befolgen Sie die Anweisungen in **Migrate-Client.cmd**, um das Skript so zu bearbeiten, dass es die Azure Rights Management-Dienst-URL Ihres Mandanten sowie die Servernamen Ihrer Extranet- und Intranetlizenzierungs-URLs des AD RMS-Clusters enthält. Erhöhen Sie dann wie zuvor erläutert die Version des Skripts. Zum Nachverfolgen der Skriptversionen wird empfohlen, das heutige Datum in folgendem Format zu verwenden: YYYYMMDD
    
   > [!IMPORTANT]
   > Achten Sie auch hier wieder darauf, keine zusätzlichen Leerzeichen vor oder nach Ihren Adressen einzufügen.
   > 
   > Wenn Ihre AD RMS-Server zusätzlich SSL/TLS-Serverzertifikate verwenden, überprüfen Sie, ob die Werte der Lizenzierungs-URL die Portnummer **443** in der Zeichenfolge enthalten. Beispiel: https://rms.treyresearch.net:443/_wmcs/licensing. Diese Informationen können Sie in der Active Directory Rights Management Services-Konsole finden, wenn Sie auf den Clusternamen klicken und sich die **Clusterdetails** ansehen. Wenn Sie sehen, dass die URL die Portnummer 443 enthält, fügen Sie diesen Wert beim Ändern des Skripts hinzu. Beispiel: https://rms.treyresearch.net:<strong>443</strong>. 
    
   Wenn Sie Ihre Azure Rights Management-Dienst-URL für *&lt;IhreMandantenURL&gt;* abrufen müssen, erhalten Sie die nötigen Informationen darüber unter [To identify your Azure Rights Management service URL (So identifizieren Sie Ihre Azure Rights Management-Dienst-URL)](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3. Konfigurieren Sie Ihre Skriptbereitstellungsmethoden mithilfe der Anweisungen am Anfang dieses Schritts, um **Migrate-Client.cmd** und **Migrate-User.cmd** auf den Windows-Clientcomputern auszuführen, die von den Mitgliedern der Gruppe „AIPMigrated“ verwendet werden. 

## <a name="next-steps"></a>Nächste Schritte
Fahren Sie mit [Phase 4: Unterstützung der Dienstekonfiguration](migrate-from-ad-rms-phase4.md) fort, um die Migration fortzusetzen.
