---
title: Enumerationen
description: Enumerationen
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 4/16/2020
ms.openlocfilehash: e65dae9c6df3d65a8bccf6bb08d61ff49b21d7ee
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764171"
---
# <a name="enumerations"></a>Enumerationen

## <a name="mip_cc_cache_storage_type"></a>mip_cc_cache_storage_type

Speichertyp für Caches

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_CACHE_STORAGE_TYPE_IN_MEMORY = 0         | In-Memory-Speicher  |
|  MIP_CACHE_STORAGE_TYPE_ON_DISK = 1           | Speicher auf dem Datenträger  |
|  MIP_CACHE_STORAGE_TYPE_ON_DISK_ENCRYPTED = 2  | Speicher auf dem Datenträger mit Verschlüsselung (sofern von der Plattform unterstützt)  |


```c
typedef enum {
  MIP_CACHE_STORAGE_TYPE_IN_MEMORY = 0,        
  MIP_CACHE_STORAGE_TYPE_ON_DISK = 1,          
  MIP_CACHE_STORAGE_TYPE_ON_DISK_ENCRYPTED = 2 
} mip_cc_cache_storage_type;

```

## <a name="mip_cc_content_format"></a>mip_cc_content_format

Inhalts Format

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_CONTENT_FORMAT_DEFAULT = 0  | Standard Dateiformat  |
|  MIP_CONTENT_FORMAT_EMAIL = 1    | Email  |


```c
typedef enum {
  MIP_CONTENT_FORMAT_DEFAULT = 0, 
  MIP_CONTENT_FORMAT_EMAIL = 1,   
} mip_cc_content_format;

```

## <a name="mip_cc_label_assignment_method"></a>mip_cc_label_assignment_method

Beschreibt, wie eine neue Bezeichnung angewendet wird.

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_LABEL_ASSIGNMENT_METHOD_STANDARD = 0    | Standard Bezeichnungs Zuweisungen überschreiben keine vorherige privilegierte Zuweisung.  |
|  MIP_LABEL_ASSIGNMENT_METHOD_PRIVILEGED = 1  | Die Zuweisung privilegierter Bezeichnungen wird von zukünftigen Standard Zuweisungen nicht überschrieben.  |
|  MIP_LABEL_ASSIGNMENT_METHOD_AUTO = 2        | Reserviert. Darf nicht verwendet werden.  |


```c
typedef enum {
  MIP_LABEL_ASSIGNMENT_METHOD_STANDARD = 0,   
  MIP_LABEL_ASSIGNMENT_METHOD_PRIVILEGED = 1, 
  MIP_LABEL_ASSIGNMENT_METHOD_AUTO = 2,       
} mip_cc_label_assignment_method;

```

## <a name="mip_cc_content_mark_alignment"></a>mip_cc_content_mark_alignment

Ausrichtung für Inhalts Markierungen (Inhalts Kopfzeile oder Inhalts Fußzeile)

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_CONTENT_MARK_ALIGNMENT_LEFT = 0    | Die Inhalts Markierung wird linksbündig ausgerichtet.  |
|  MIP_CONTENT_MARK_ALIGNMENT_RIGHT = 1   | Die Inhalts Markierung wird rechtsbündig ausgerichtet.  |
|  MIP_CONTENT_MARK_ALIGNMENT_CENTER = 2  | Das Markieren von Inhalten wird zentriert.  |


```c
typedef enum {
  MIP_CONTENT_MARK_ALIGNMENT_LEFT = 0,   
  MIP_CONTENT_MARK_ALIGNMENT_RIGHT = 1,  
  MIP_CONTENT_MARK_ALIGNMENT_CENTER = 2, 
} mip_cc_content_mark_alignment;

```

## <a name="mip_cc_watermark_layout"></a>mip_cc_watermark_layout

Layout für Wasserzeichen

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_WATERMARK_LAYOUT_HORIZONTAL = 0  | Wasserzeichen Layout ist horizontal  |
|  MIP_WATERMARK_LAYOUT_DIAGONAL = 1    | Wasserzeichen Layout ist diagonal  |


```c
typedef enum {
  MIP_WATERMARK_LAYOUT_HORIZONTAL = 0, 
  MIP_WATERMARK_LAYOUT_DIAGONAL = 1,   
} mip_cc_watermark_layout;

```

## <a name="mip_cc_consent"></a>mip_cc_consent

Antwort eines Benutzers, wenn die Zustimmung zum Herstellen einer Verbindung mit einem unbekannten Dienst Endpunkt angefordert wird

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_CONSENT_ACCEPT_ALWAYS = 0  | Zustimmung und Erinnerung an diese Entscheidung  |
|  MIP_CONSENT_ACCEPT = 1         | Einmalige Zustimmung  |
|  MIP_CONSENT_REJECT = 2          | Keine Zustimmung  |


```c
typedef enum {
  MIP_CONSENT_ACCEPT_ALWAYS = 0, 
  MIP_CONSENT_ACCEPT = 1,        
  MIP_CONSENT_REJECT = 2         
} mip_cc_consent;

```

## <a name="mip_cc_flighting_feature"></a>mip_cc_flighting_feature

Definiert neue Features anhand des Namens.

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_FLIGHTING_FEATURE_SERVICE_DISCOVERY = 0          | Verlassen Sie sich auf separaten http-Aufrufe, um RMS-Dienst Endpunkte zu bestimmen (Standardwert false) |
|  MIP_FLIGHTING_FEATURE_AUTH_INFO_CACHE = 1            | Cache OAuth2 Anforderungen pro Domäne/Mandant, um unnötige 401-Antworten zu verringern. Deaktivieren für Apps/Dienste, die ihre eigene HTTP-Authentifizierung verwalten (Standardwert: true)  |
|  MIP_FLIGHTING_FEATURE_LINUX_ENCRYPTED_CACHE = 2      | Verschlüsseltes Zwischenspeichern für Linux-Plattformen aktivieren (Standardwert false)  |
|  MIP_FLIGHTING_FEATURE_SINGLE_DOMAIN_NAME = 3         | Aktivieren Sie einen einzelnen Firmennamen für die DNS-Suche (z. b.https://corprights)  |
|  MIP_FLIGHTING_FEATURE_POLICY_AUTH = 4                | Aktivieren Sie die automatische HTTP-Authentifizierung für an den Richtlinien Dienst gesendete Anforderungen. Deaktivieren für Apps/Dienste, die ihre eigene HTTP-Authentifizierung verwalten (Standardwert: true)  |
|  MIP_FLIGHTING_FEATURE_URL_REDIRECT_CACHE = 5         | Cache-URL-Umleitungen zum Reduzieren der Anzahl von http-Vorgängen  |
|  MIP_FLIGHTING_FEATURE_PRE_LICENSE = 6                | Aktivieren der Pre License API-Überprüfung  |
|  MIP_FLIGHTING_FEATURE_DOUBLE_KEY_PROTECTION = 7      | Aktivieren der doppelten Schlüsselschutz Funktion zur Verwendung eines Kunden Schlüssels für die Verschlüsselung mit  |
|  MIP_FLIGHTING_FEATURE_VARIABLE_POLICY_TTL = 8        | Variablen Richtlinien Gültigkeitsdauer im Speicher aktivieren  |
|  MIP_FLIGHTING_FEATURE_VARIABLE_TEXT_MARKING = 9      | Variablen Textmarkierung aktivieren  |
|  MIP_FLIGHTING_FEATURE_OPTIMIZE_PDF_MEMORY = 10       | Aktivieren von PDF-Speicher Ersteller in schützen und Aufheben des Schutzes von PDF-Dateien  |
|  MIP_FLIGHTING_FEATURE_REMOVE_DELETED_LABEL_MD = 11   | Entfernen der Metadaten für die Lösch Bezeichnung aktivieren  |
|  MIP_FLIGHTING_FEATURE_ENFORCE_TLS12 = 12             | Erzwingen von TLS 1,2 für nicht-ADRMS-HTTPS-Verbindungen  |


```c
typedef enum {
  MIP_FLIGHTING_FEATURE_SERVICE_DISCOVERY = 0,         
  MIP_FLIGHTING_FEATURE_AUTH_INFO_CACHE = 1,           
  MIP_FLIGHTING_FEATURE_LINUX_ENCRYPTED_CACHE = 2,     
  MIP_FLIGHTING_FEATURE_SINGLE_DOMAIN_NAME = 3,        
  MIP_FLIGHTING_FEATURE_POLICY_AUTH = 4,               
  MIP_FLIGHTING_FEATURE_URL_REDIRECT_CACHE = 5,        
  MIP_FLIGHTING_FEATURE_PRE_LICENSE = 6,               
  MIP_FLIGHTING_FEATURE_DOUBLE_KEY_PROTECTION = 7,     
  MIP_FLIGHTING_FEATURE_VARIABLE_POLICY_TTL = 8,       
  MIP_FLIGHTING_FEATURE_VARIABLE_TEXT_MARKING = 9,     
  MIP_FLIGHTING_FEATURE_OPTIMIZE_PDF_MEMORY = 10,      
  MIP_FLIGHTING_FEATURE_REMOVE_DELETED_LABEL_MD = 11,  
  MIP_FLIGHTING_FEATURE_ENFORCE_TLS12 = 12,            
} mip_cc_flighting_feature;

```

## <a name="mip_cc_http_request_type"></a>mip_cc_http_request_type

HTTP-Anforderungstyp

| Feld | BESCHREIBUNG |
|---|---|
|  HTTP_REQUEST_TYPE_GET = 0   | HTTP-GET  |
|  HTTP_REQUEST_TYPE_POST = 1  | HTTP Post  |


```c
typedef enum {
  HTTP_REQUEST_TYPE_GET = 0,  
  HTTP_REQUEST_TYPE_POST = 1, 
} mip_cc_http_request_type;

```

## <a name="mip_cc_http_result"></a>mip_cc_http_result

Erfolg/Fehlerstatus des http-Vorgangs

| Feld | BESCHREIBUNG |
|---|---|
|  HTTP_RESULT_OK = 0       | Der http-Vorgang wurde erfolgreich abgeschlossen.  |
|  HTTP_RESULT_FAILURE = 1  | Fehler beim http-Vorgang (z. b. Timeout, Netzwerkfehler usw.).  |


```c
typedef enum {
  HTTP_RESULT_OK = 0,      
  HTTP_RESULT_FAILURE = 1, 
} mip_cc_http_result;

```

## <a name="mip_cc_log_level"></a>mip_cc_log_level

Protokolliergrad

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_LOG_LEVEL_TRACE = 0   | Trace  |
|  MIP_LOG_LEVEL_INFO        | Info  |
|  MIP_LOG_LEVEL_WARNING     | Warnung  |
|  MIP_LOG_LEVEL_ERROR       | Fehler  |


```c
typedef enum {
  MIP_LOG_LEVEL_TRACE = 0,  
  MIP_LOG_LEVEL_INFO,       
  MIP_LOG_LEVEL_WARNING,    
  MIP_LOG_LEVEL_ERROR,      
} mip_cc_log_level;

```

## <a name="mip_cc_protection_type"></a>mip_cc_protection_type

Eine Beschreibung, ob der Schutz durch eine Vorlage oder Ad-hoc definiert wird

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_PROTECTION_TYPE_TEMPLATE_BASED = 0  | Basierend auf einer RMS-Vorlage  |
|  MIP_PROTECTION_TYPE_CUSTOM = 1          | Benutzerdefinierter, Ad-hoc-Schutz  |


```c
typedef enum {
  MIP_PROTECTION_TYPE_TEMPLATE_BASED = 0, 
  MIP_PROTECTION_TYPE_CUSTOM = 1,         
} mip_cc_protection_type;

```

## <a name="mip_cc_result"></a>mip_cc_result

Ergebnis der API-Erfolg/-Fehler

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_RESULT_ERROR_UNKNOWN = 1                     | Unbekannter Fehler.  |
|  MIP_RESULT_ERROR_INSUFFICIENT_BUFFER = 2         | Der von der Anwendung bereitgestellte Puffer ist zu klein.  |
|  MIP_RESULT_ERROR_BAD_INPUT = 3                   | Anwendung hat ungültige Eingabe überschritten  |
|  MIP_RESULT_ERROR_FILE_IO_ERROR = 4               | Allgemeiner Datei-e/a-Fehler  |
|  MIP_RESULT_ERROR_NETWORK = 5                     | Allgemeiner Netzwerkfehler (z. b. nicht erreichbarer Dienst)  |
|  MIP_RESULT_ERROR_INTERNAL = 6                    | Unerwarteter interner Fehler.  |
|  MIP_RESULT_ERROR_JUSTIFICATION_REQUIRED = 7      | Eine Legitimierung ist erforderlich, um die Aktion für die Datei abzuschließen.  |
|  MIP_RESULT_ERROR_NOT_SUPPORTED_OPERATION = 8     | Die opettung wird nicht unterstützt.  |
|  MIP_RESULT_ERROR_PRIVILEGED_REQUIRED = 9         | Die privilegierte Bezeichnung kann bei der Standardmethode nicht überschrieben werden  |
|  MIP_RESULT_ERROR_ACCESS_DENIED = 10              | Der Benutzer hat keine Zugriffsrechte für den Dienst.  |
|  MIP_RESULT_ERROR_CONSENT_DENIED = 11             | Einem Vorgang, der Zustimmung des Benutzers erforderte, wurde keine Zustimmung erteilt.  |
|  MIP_RESULT_ERROR_NO_PERMISSIONS = 12             | Der Benutzer konnte keinen Zugriff auf den Inhalt erhalten (z. b. keine Berechtigungen, widerrufen von Inhalt).  |
|  MIP_RESULT_ERROR_NO_AUTH_TOKEN = 13              | Der Benutzer konnte aufgrund eines leeren Authentifizierungs Tokens keinen Zugriff auf den Inhalt erhalten.  |
|  MIP_RESULT_ERROR_SERVICE_DISABLED = 14           | Der Benutzer konnte aufgrund deaktiviertem Dienst keinen Zugriff auf den Inhalt erhalten.  |
|  MIP_RESULT_ERROR_PROXY_AUTH = 15                 | Fehler bei der Proxy Authentifizierung  |
|  MIP_RESULT_ERROR_NO_POLICY = 16                  | Es ist keine Richtlinie für den Benutzer/Mandanten konfiguriert.  |
|  MIP_RESULT_ERROR_OPERATION_CANCELLED = 17        | Vorgang abgebrochen.  |
|  MIP_RESULT_ERROR_ADHOC_PROTECTION_REQUIRED = 18  | Der Ad-hoc-Schutz sollte festgelegt werden, um die Aktion für die Datei abzuschließen.  |
|  MIP_RESULT_ERROR_DEPRECATED_API = 19             | Aufrufer hat eine veraltete API aufgerufen  |
|  MIP_RESULT_ERROR_TEMPLATE_NOT_FOUND = 20         | Die Vorlagen-ID wurde nicht erkannt.  |
|  MIP_RESULT_ERROR_LABEL_NOT_FOUND = 21            | Bezeichnungs-ID wurde nicht erkannt.  |
|  MIP_RESULT_ERROR_LABEL_DISABLED = 22             | Die Bezeichnung ist deaktiviert oder inaktiv.  |


```c
typedef enum {
  MIP_RESULT_SUCCESS = 0,

  // MIP C API errors
  MIP_RESULT_ERROR_UNKNOWN = 1,                    
  MIP_RESULT_ERROR_INSUFFICIENT_BUFFER = 2,        

  // MIP C++ exceptions
  MIP_RESULT_ERROR_BAD_INPUT = 3,                  
  MIP_RESULT_ERROR_FILE_IO_ERROR = 4,              
  MIP_RESULT_ERROR_NETWORK = 5,                    
  MIP_RESULT_ERROR_INTERNAL = 6,                   
  MIP_RESULT_ERROR_JUSTIFICATION_REQUIRED = 7,     
  MIP_RESULT_ERROR_NOT_SUPPORTED_OPERATION = 8,    
  MIP_RESULT_ERROR_PRIVILEGED_REQUIRED = 9,        
  MIP_RESULT_ERROR_ACCESS_DENIED = 10,             
  MIP_RESULT_ERROR_CONSENT_DENIED = 11,            
  MIP_RESULT_ERROR_NO_PERMISSIONS = 12,            
  MIP_RESULT_ERROR_NO_AUTH_TOKEN = 13,             
  MIP_RESULT_ERROR_SERVICE_DISABLED = 14,          
  MIP_RESULT_ERROR_PROXY_AUTH = 15,                
  MIP_RESULT_ERROR_NO_POLICY = 16,                 
  MIP_RESULT_ERROR_OPERATION_CANCELLED = 17,       
  MIP_RESULT_ERROR_ADHOC_PROTECTION_REQUIRED = 18, 
  MIP_RESULT_ERROR_DEPRECATED_API = 19,            
  MIP_RESULT_ERROR_TEMPLATE_NOT_FOUND = 20,        
  MIP_RESULT_ERROR_LABEL_NOT_FOUND = 21,           
  MIP_RESULT_ERROR_LABEL_DISABLED = 22,            
} mip_cc_result;

```

## <a name="mip_cc_pre_license_format"></a>mip_cc_pre_license_format

Definiert das Prälizenzierungs Format.

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_PRE_LICENSE_FORMAT_XML = 0   | Von msipc verwendetes XML/SOAP-Legacy Format  |
|  MIP_PRE_LICENSE_FORMAT_JSON = 1  | Vom MIP SDK und RMS SDK verwendetes JSON/Rest-Format  |


```c
typedef enum {
  MIP_PRE_LICENSE_FORMAT_XML = 0,  
  MIP_PRE_LICENSE_FORMAT_JSON = 1, 
} mip_cc_pre_license_format;

```

## <a name="mip_cc_action_type"></a>mip_cc_action_type

Aktionstyp-Bitmaske

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_ACTION_TYPE_ADD_CONTENT_FOOTER = 1 << 0      | Fügt eine Fußzeile mit Inhalt zum Aktionstyp für das Dokument hinzu. |
|  MIP_ACTION_TYPE_ADD_CONTENT_HEADER = 1 << 1      | Fügt einen Header mit Inhalt zum Aktionstyp für das Dokument hinzu. |
|  MIP_ACTION_TYPE_ADD_WATERMARK = 1 << 2           | Fügt ein Wasserzeichen zum Aktionstyp für das gesamte Dokument hinzu. |
|  MIP_ACTION_TYPE_CUSTOM = 1 << 3                  | Ein benutzerdefinierter Aktionstyp |
|  MIP_ACTION_TYPE_JUSTIFY = 1 << 4                 | Ein Aktionstyp für die Legitimierung |
|  MIP_ACTION_TYPE_METADATA = 1 << 5                | Ein Aktionstyp zum Ändern von Metadaten |
|  MIP_ACTION_TYPE_PROTECT_ADHOC = 1 << 6           | Ein Aktionstyp zum Schutz anhand von benutzerdefinierten Richtlinien |
|  MIP_ACTION_TYPE_PROTECT_BY_TEMPLATE = 1 << 7     | Ein Aktionstyp zum Schutz anhand von Vorlagen |
|  MIP_ACTION_TYPE_PROTECT_DO_NOT_FORWARD = 1 << 8  | Ein Aktionstyp zum Schutz durch Verhinderung einer Weiterleitung |
|  MIP_ACTION_TYPE_REMOVE_CONTENT_FOOTER = 1 << 9   | Ein Aktionstyp, der Fußzeilen mit Inhalt entfernt |
|  MIP_ACTION_TYPE_REMOVE_CONTENT_HEADER = 1 << 10  | Ein Aktionstyp, der Header mit Inhalt entfernt |
|  MIP_ACTION_TYPE_REMOVE_PROTECTION = 1 << 11      | Ein Aktionstyp, der einen Schutz entfernt |
|  MIP_ACTION_TYPE_REMOVE_WATERMARK = 1 << 12       | Ein Aktionstyp, der Wasserzeichen entfernt |
|  MIP_ACTION_TYPE_APPLY_LABEL = 1 << 13            | Ein Aktionstyp, der eine Bezeichnung anwendet |
|  MIP_ACTION_TYPE_RECOMMEND_LABEL = 1 << 14        | Ein Aktionstyp, der eine Bezeichnung empfiehlt |


```c
typedef enum {
  MIP_ACTION_TYPE_ADD_CONTENT_FOOTER = 1 << 0,     
  MIP_ACTION_TYPE_ADD_CONTENT_HEADER = 1 << 1,     
  MIP_ACTION_TYPE_ADD_WATERMARK = 1 << 2,          
  MIP_ACTION_TYPE_CUSTOM = 1 << 3,                 
  MIP_ACTION_TYPE_JUSTIFY = 1 << 4,                
  MIP_ACTION_TYPE_METADATA = 1 << 5,               
  MIP_ACTION_TYPE_PROTECT_ADHOC = 1 << 6,          
  MIP_ACTION_TYPE_PROTECT_BY_TEMPLATE = 1 << 7,    
  MIP_ACTION_TYPE_PROTECT_DO_NOT_FORWARD = 1 << 8, 
  MIP_ACTION_TYPE_REMOVE_CONTENT_FOOTER = 1 << 9,  
  MIP_ACTION_TYPE_REMOVE_CONTENT_HEADER = 1 << 10, 
  MIP_ACTION_TYPE_REMOVE_PROTECTION = 1 << 11,     
  MIP_ACTION_TYPE_REMOVE_WATERMARK = 1 << 12,      
  MIP_ACTION_TYPE_APPLY_LABEL = 1 << 13,           
  MIP_ACTION_TYPE_RECOMMEND_LABEL = 1 << 14,       
} mip_cc_action_type;

```

## <a name="mip_cc_label_action_state"></a>mip_cc_label_action_state

Beschreibt, was die Anwendung in Bezug auf die aktuelle Bezeichnung tun soll.

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_LABEL_ACTION_STATE_NO_CHANGE = 0  | Die aktuelle Bezeichnung sollte nicht geändert werden.  |
|  MIP_LABEL_ACTION_STATE_REMOVE = 1     | Die aktuelle Bezeichnung sollte entfernt werden.  |
|  MIP_LABEL_ACTION_STATE_UPDATE = 2     | Die aktuelle Bezeichnung sollte geändert werden.  |


```c
typedef enum {
  MIP_LABEL_ACTION_STATE_NO_CHANGE = 0, 
  MIP_LABEL_ACTION_STATE_REMOVE = 1,    
  MIP_LABEL_ACTION_STATE_UPDATE = 2,    
} mip_cc_label_action_state;

```

## <a name="mip_cc_label_action_type"></a>mip_cc_label_action_type

Bezeichnungs bezogene Aktionen, die eine Anwendung versteht und unterstützt

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_LABEL_ACTION_TYPE_ADD_CONTENT_FOOTER = 1 << 0      | Fügt eine Fußzeile mit Inhalt zum Aktionstyp für das Dokument hinzu.  |
|  MIP_LABEL_ACTION_TYPE_ADD_CONTENT_HEADER = 1 << 1      | Fügt einen Header mit Inhalt zum Aktionstyp für das Dokument hinzu.  |
|  MIP_LABEL_ACTION_TYPE_ADD_WATERMARK = 1 << 2           | Fügt ein Wasserzeichen zum Aktionstyp für das gesamte Dokument hinzu.  |
|  MIP_LABEL_ACTION_TYPE_CUSTOM = 1 << 3                  | Ein benutzerdefinierter Aktionstyp  |
|  MIP_LABEL_ACTION_TYPE_JUSTIFY = 1 << 4                 | Ein Aktionstyp für die Legitimierung  |
|  MIP_LABEL_ACTION_TYPE_METADATA = 1 << 5                | Ein Aktionstyp zum Ändern von Metadaten  |
|  MIP_LABEL_ACTION_TYPE_PROTECT_ADHOC = 1 << 6           | Ein Aktionstyp zum Schutz anhand von benutzerdefinierten Richtlinien  |
|  MIP_LABEL_ACTION_TYPE_PROTECT_BY_TEMPLATE = 1 << 7     | Ein Aktionstyp zum Schutz anhand von Vorlagen  |
|  MIP_LABEL_ACTION_TYPE_PROTECT_DO_NOT_FORWARD = 1 << 8  | Ein Aktionstyp zum Schutz durch Verhinderung einer Weiterleitung  |
|  MIP_LABEL_ACTION_TYPE_REMOVE_CONTENT_FOOTER = 1 << 9   | Ein Aktionstyp, der Fußzeilen mit Inhalt entfernt  |
|  MIP_LABEL_ACTION_TYPE_REMOVE_CONTENT_HEADER = 1 << 10  | Ein Aktionstyp, der Header mit Inhalt entfernt  |
|  MIP_LABEL_ACTION_TYPE_REMOVE_PROTECTION = 1 << 11      | Ein Aktionstyp, der einen Schutz entfernt  |
|  MIP_LABEL_ACTION_TYPE_REMOVE_WATERMARK = 1 << 12       | Ein Aktionstyp, der Wasserzeichen entfernt  |
|  MIP_LABEL_ACTION_TYPE_APPLY_LABEL = 1 << 13            | Ein Aktionstyp, der eine Bezeichnung anwendet  |
|  MIP_LABEL_ACTION_TYPE_RECOMMEND_LABEL = 1 << 14        | Ein Aktionstyp, der eine Bezeichnung empfiehlt  |


```c
typedef enum {
  MIP_LABEL_ACTION_TYPE_ADD_CONTENT_FOOTER = 1 << 0,     
  MIP_LABEL_ACTION_TYPE_ADD_CONTENT_HEADER = 1 << 1,     
  MIP_LABEL_ACTION_TYPE_ADD_WATERMARK = 1 << 2,          
  MIP_LABEL_ACTION_TYPE_CUSTOM = 1 << 3,                 
  MIP_LABEL_ACTION_TYPE_JUSTIFY = 1 << 4,                
  MIP_LABEL_ACTION_TYPE_METADATA = 1 << 5,               
  MIP_LABEL_ACTION_TYPE_PROTECT_ADHOC = 1 << 6,          
  MIP_LABEL_ACTION_TYPE_PROTECT_BY_TEMPLATE = 1 << 7,    
  MIP_LABEL_ACTION_TYPE_PROTECT_DO_NOT_FORWARD = 1 << 8, 
  MIP_LABEL_ACTION_TYPE_REMOVE_CONTENT_FOOTER = 1 << 9,  
  MIP_LABEL_ACTION_TYPE_REMOVE_CONTENT_HEADER = 1 << 10, 
  MIP_LABEL_ACTION_TYPE_REMOVE_PROTECTION = 1 << 11,     
  MIP_LABEL_ACTION_TYPE_REMOVE_WATERMARK = 1 << 12,      
  MIP_LABEL_ACTION_TYPE_APPLY_LABEL = 1 << 13,           
  MIP_LABEL_ACTION_TYPE_RECOMMEND_LABEL = 1 << 14,       
} mip_cc_label_action_type;

```

## <a name="mip_cc_data_state"></a>mip_cc_data_state

Definiert den Zustand der Daten, während eine Anwendung darauf reagiert.

| Feld | BESCHREIBUNG |
|---|---|
|  MIP_DATA_STATE_REST = 0    | Inaktive Daten, die physisch in Datenbanken/Dateien/Lager speichern gespeichert  |
|  MIP_DATA_STATE_MOTION = 1  | Daten, die ein Netzwerk durchlaufen oder sich vorübergehend im zu lesenden oder zu aktualisierenden Computerspeicher befinden  |
|  MIP_DATA_STATE_USE = 2     | Aktive Daten unter konstanter Änderung werden physisch in Datenbanken/Dateien/Lagerhäusern gespeichert usw.  |


```c
typedef enum {
  MIP_DATA_STATE_REST = 0,   
  MIP_DATA_STATE_MOTION = 1, 
  MIP_DATA_STATE_USE = 2,    
} mip_cc_data_state;

```

