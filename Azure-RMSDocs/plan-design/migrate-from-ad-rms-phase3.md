---
title: "Migrieren von AD RMS-Azure Information Protection – Phase 3"
description: Phase 3 der Migration von AD RMS zu Azure Information Protection deckt den Schritt 7 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 27dc3de51c72d0142ac3dbdbd97c02c0241e902d
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
# <a name="migration-phase-3---client-side-configuration"></a>Migrationsphase 3: Clientseitige Konfiguration

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Verwenden Sie die folgenden Informationen für Phase 3 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken den Schritt 7 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.

Wenn Sie nicht alle Clients gleichzeitig migrieren können, führen Sie diese Prozeduren für Clientbatches aus. Fügen Sie jeden Benutzer, der über einen Windows-Computer verfügt, den Sie in Ihren Batch migrieren möchten, zur **AIPMigrated**-Gruppe hinzu, die Sie zuvor erstellt haben.

## <a name="step-7-reconfigure-clients-to-use-azure-information-protection"></a>Schritt 7: Neukonfigurieren von Clients zur Verwendung von Azure Information Protection

Dieser Schritt verwendet Migrationsskripts zur Neukonfiguration von AD RMS-Clients. Diese Skripts setzen die Konfiguration auf Windows-Computern zurück, um den Azure RMS-Dienst anstelle von AD RMS zu verwenden. 

**CleanUpRMS.cmd**:

- Löscht den Inhalt aller Ordner und Registrierungsschlüssel, die vom AD RMS-Client verwendet werden, um die Konfiguration zu speichern. Diese Informationen umfassen den Speicherort des AD RMS-Clusters des Clients.

**MigrateClient.cmd**:

- Konfiguriert den Client zum Initialisieren der Benutzerumgebung (Bootstrap) für den Azure Rights Management-Dienst.

-  Konfiguriert den Client so, dass er eine Verbindung mit Ihrem Azure Rights Management-Dienst herstellt, um Nutzungslizenzen für den Inhalt zu erhalten, der durch Ihren AD RMS-Cluster geschützt ist. 


### <a name="client-reconfiguration-by-using-registry-edits"></a>Clientneukonfiguration mithilfe von Änderungen an der Registrierung

1. Kehren Sie zu den Migrationsskripts **CleanUpRMS.cmd** und **MigrateClient.cmd** zurück, die Sie zuvor extrahiert haben.

2.  Befolgen Sie die Anweisungen in **MigrateClient.cmd**, um das Skript so zu bearbeiten, dass es die Azure Rights Management-Dienst-URL Ihres Mandanten enthält und auch die Servernamen Ihrer Extranet- und Intranetlizenzierungs-URLs des AD RMS-Clusters.

    > [!IMPORTANT]
    > Achten Sie auch hier wieder darauf, keine zusätzlichen Leerzeichen vor oder nach Ihren Adressen einzufügen.
    > 
    > Wenn Ihre AD RMS-Server zusätzlich SSL/TLS-Serverzertifikate verwenden, überprüfen Sie, ob die Werte der Lizenzierungs-URL die Portnummer **443** in der Zeichenfolge enthalten. Zum Beispiel: https:// rms.treyresearch.net:443/_wmcs/licensing. Diese Informationen finden Sie in der Active Directory Rights Management Services-Konsole wenn Sie auf den Clusternamen klicken und sich die Information **Cluster Details** (Clusterdetails) ansehen. Wenn Sie sehen, dass die URL die Portnummer 443 enthält, fügen Sie diesen Wert beim Ändern des Skripts hinzu. Zum Beispiel: https://rms.treyresearch.net**:443**. 

    Wenn Sie Ihre Azure Rights Management-Dienst-URL für *&lt;IhreMandantenURL&gt;* abrufen müssen, erhalten Sie die nötigen Informationen darüber unter [To identify your Azure Rights Management service URL (So identifizieren Sie Ihre Azure Rights Management-Dienst-URL)](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3.  Führen Sie **CleanUpRMS.cmd** und dann **MigrateClient.cmd** auf den Clientcomputern aus, die von den Mitgliedern der **AIPMigrated**-Gruppe verwendet werden. Erstellen Sie z.B. ein Gruppenrichtlinienobjekt, das diese Skripts ausführt, und weisen Sie es dieser Benutzergruppe zu.


## <a name="next-steps"></a>Nächste Schritte
Fahren Sie mit [Phase 4: Unterstützung der Dienstekonfiguration](migrate-from-ad-rms-phase3.md) fort, um die Migration fortzusetzen.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]