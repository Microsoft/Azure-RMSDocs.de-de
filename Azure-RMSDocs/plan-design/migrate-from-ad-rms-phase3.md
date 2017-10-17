---
title: "Migrieren von AD RMS-Azure Information Protection – Phase 3"
description: Phase 3 der Migration von AD RMS zu Azure Information Protection deckt den Schritt 7 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/11/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5de30d095e1c279babb8f8be74a5a9b9d54db204
ms.sourcegitcommit: 45c23b3b353ad0e438292cb1cd8d1b13061620e1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2017
---
# <a name="migration-phase-3---client-side-configuration"></a>Migrationsphase 3: Clientseitige Konfiguration

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Verwenden Sie die folgenden Informationen für Phase 3 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken den Schritt 7 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.

## <a name="step-7-reconfigure-windows-computers-to-use-azure-information-protection"></a>Schritt 7: Neukonfigurieren von Windows-Computern zur Verwendung von Azure Information Protection

Verwenden Sie für Windows-Computer zwei Migrationsskripts zur erneuten Konfiguration von AD RMS-Clients:

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

### <a name="windows-client-reconfiguration-by-using-registry-edits"></a>Neukonfiguration der Windows-Clients mithilfe von Änderungen der Registrierung

1. Kehren Sie zu den Migrationsskripts **Migrate-Client.cmd** und **Migrate-User.cmd** zurück, die Sie zuvor beim Herunterladen dieser Skripts in der [Vorbereitungsphase](migrate-from-ad-rms-phase1.md#step-2-prepare-for-client-migration) extrahiert haben.

2.  Befolgen Sie die Anweisungen in **Migrate-Client.cmd**, um das Skript so zu bearbeiten, dass es die Azure Rights Management-Dienst-URL Ihres Mandanten sowie die Servernamen Ihrer Extranet- und Intranetlizenzierungs-URLs des AD RMS-Clusters enthält. Erhöhen Sie dann wie zuvor erläutert die Version des Skripts. Zum Nachverfolgen der Skriptversionen wird empfohlen, das heutige Datum in folgendem Format zu verwenden: YYYYMMDD.

    > [!IMPORTANT]
    > Achten Sie auch hier wieder darauf, keine zusätzlichen Leerzeichen vor oder nach Ihren Adressen einzufügen.
    > 
    > Wenn Ihre AD RMS-Server zusätzlich SSL/TLS-Serverzertifikate verwenden, überprüfen Sie, ob die Werte der Lizenzierungs-URL die Portnummer **443** in der Zeichenfolge enthalten. Zum Beispiel: https:// rms.treyresearch.net:443/_wmcs/licensing. Diese Informationen finden Sie in der Active Directory Rights Management Services-Konsole wenn Sie auf den Clusternamen klicken und sich die Information **Cluster Details** (Clusterdetails) ansehen. Wenn Sie sehen, dass die URL die Portnummer 443 enthält, fügen Sie diesen Wert beim Ändern des Skripts hinzu. Zum Beispiel: https://rms.treyresearch.net**:443**. 

    Wenn Sie Ihre Azure Rights Management-Dienst-URL für *&lt;IhreMandantenURL&gt;* abrufen müssen, erhalten Sie die nötigen Informationen darüber unter [To identify your Azure Rights Management service URL (So identifizieren Sie Ihre Azure Rights Management-Dienst-URL)](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3. Konfigurieren Sie Ihre Skriptbereitstellungsmethoden mithilfe der Anweisungen am Anfang dieses Schritts, um **Migrate-Client.cmd** und **Migrate-User.cmd** auf den Windows-Clientcomputern auszuführen, die von den Mitgliedern der Gruppe „AIPMigrated“ verwendet werden. 

## <a name="next-steps"></a>Nächste Schritte
Fahren Sie mit [Phase 4: Unterstützung der Dienstekonfiguration](migrate-from-ad-rms-phase3.md) fort, um die Migration fortzusetzen.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]