---
title: Funktionen
description: Funktionen
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 11/4/2019
ms.openlocfilehash: cfc80ab9e4704c9efa5d3105f36c668bce26a6b9
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73591642"
---
# <a name="functions"></a>Funktionen

## <a name="mip_cc_auth_callback"></a>mip_cc_auth_callback

Rückruf Funktionsdefinition zum Abrufen des OAuth2-Tokens

**Parameters**

Parameter | Description
|---|---|
| Identität | Die e-Mail-Adresse, für die das Token abgerufen wird. |
| challenge | OAuth2 Challenge |
| context | Nicht transparenter Anwendungskontext, der an die MIP-API übermittelt wurde, die zu diesem Authentifizierungs Rückruf geführt hat. |
| zu "-Puffer" | Ausgeben Puffer, in den das Token kopiert wird. Wenn der Wert NULL ist, wird "actualbykensize" aufgefüllt, aber |
| "-pukenbuffersize" | Größe des Ausgabepuffers (in Bytes) |
| actualbykensize | Ausgeben Tatsächliche Größe (in Bytes) des Tokens |

**Return**: true, wenn das Token abgerufen wurde, andernfalls false

```c
MIP_CC_CALLBACK(mip_cc_auth_callback,
    bool,
    const mip_cc_identity*,
    const mip_cc_oauth2_challenge*,
    const void*,
    uint8_t*,
    const int64_t,
    int64_t*);
```

## <a name="mip_cc_consent_callback"></a>mip_cc_consent_callback

Definition der Rückruffunktion für Zustimmung vom Benutzer für den Zugriff auf einen externen Dienst Endpunkt

**Parameters**

Parameter | Description
|---|---|
| URL | Die URL, für die das SDK Benutzer Zustimmung erfordert |

**Rückgabe**: Antwort auf Benutzer Zustimmung

```c
MIP_CC_CALLBACK(mip_cc_consent_callback,
    mip_cc_consent,
    const char*);
```

## <a name="mip_cc_createdictionary"></a>MIP_CC_CreateDictionary

Erstellen eines Wörterbuchs mit Zeichen folgen Schlüsseln/-Werten

**Parameters**

Parameter | Description
|---|---|
| entries | Array von Schlüssel-Wert-Paaren |
| count | Anzahl von Schlüssel-Wert-Paaren |
| dictionary | Ausgeben Neu erstelltes Wörterbuch |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: ein mip_cc_dictionary muss durch Aufrufen von freigegeben werden MIP_CC_ReleaseDictionary 

```c
mip_cc_result MIP_CC_CreateDictionary(
    const mip_cc_kv_pair* entries,
    const int64_t count,
    mip_cc_dictionary* dictionary);
```

## <a name="mip_cc_dictionary_getentries"></a>MIP_CC_Dictionary_GetEntries

Schlüssel-Wert-Paare zum Verfassen eines Wörterbuchs erhalten

**Parameters**

Parameter | Description
|---|---|
| dictionary | Quell Wörterbuch |
| entries | Ausgeben Array von Schlüssel-Wert-Paaren, Arbeitsspeicher im Besitz mip_cc_dictionary Objekts |
| count | Ausgeben Anzahl von Schlüssel-Wert-Paaren |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: der Speicher für ' Entries ' liegt im Besitz des mip_cc_dictionary Objekts und sollte daher nicht unabhängig freigegeben werden. 

```c
mip_cc_result MIP_CC_Dictionary_GetEntries(
    const mip_cc_dictionary dictionary,
    mip_cc_kv_pair** entries,
    int64_t* count);
```

## <a name="mip_cc_releasedictionary"></a>MIP_CC_ReleaseDictionary

Freigeben von Ressourcen, die einem Wörterbuch zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| dictionary | Das zu veröffentlichende Wörterbuch. |

```c
void MIP_CC_ReleaseDictionary(mip_cc_dictionary dictionary);
```

## <a name="mip_cc_http_send_callback_fn"></a>mip_cc_http_send_callback_fn

Rückruf Funktionsdefinition zum Ausgeben einer HTTP-Anforderung

**Parameters**

Parameter | Description
|---|---|
| Anforderung | Die HTTP-Anforderung, die von der Anwendung ausgeführt werden soll. |
| context | Der gleiche nicht transparente Kontext wurde an den MIP-API-Befehl, der diese HTTP-Anforderung verursacht hat, |

```c
MIP_CC_CALLBACK(mip_cc_http_send_callback_fn,
    void,
    const mip_cc_http_request*,
    const void*);
```

## <a name="mip_cc_http_cancel_callback_fn"></a>mip_cc_http_cancel_callback_fn

Rückruf Funktionsdefinition für das Abbrechen einer HTTP-Anforderung

**Parameters**

Parameter | Description
|---|---|
| requestId | Die ID der HTTP-Anforderung, die abgebrochen werden soll. |

```c
MIP_CC_CALLBACK(mip_cc_http_cancel_callback_fn,
    void,
    const char*);
```

## <a name="mip_cc_createhttpdelegate"></a>MIP_CC_CreateHttpDelegate

Erstellt einen HTTP-Delegaten, der zum Überschreiben des HTTP-Standard Stapels verwendet werden kann.

**Parameters**

Parameter | Description
|---|---|
| SendCallback | Funktionszeiger für das Ausgeben von HTTP-Anforderungen |
| cancelcallback | Funktionszeiger zum Abbrechen von HTTP-Anforderungen |
| httpdelegat | Ausgeben Handle für http-Delegatobjekt |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_CreateHttpDelegate(
    const mip_cc_http_send_callback_fn sendCallback,
    const mip_cc_http_cancel_callback_fn cancelCallback,
    mip_cc_http_delegate* httpDelegate);
```

## <a name="mip_cc_notifyhttpdelegateresponse"></a>MIP_CC_NotifyHttpDelegateResponse

Benachrichtigt einen HTTP-Delegaten, dass eine HTTP-Antwort bereit ist.

**Parameters**

Parameter | Description
|---|---|
| httpdelegat | Handle für http-Delegatobjekt |
| requestId | ID der HTTP-Anforderung, die diesem Vorgang zugeordnet ist. |
| result | Erfolg/Fehlerstatus des Vorgangs |
| Antwort-Brücke | Die HTTP-Antwort, wenn der Vorgang erfolgreich war, andernfalls nullptr |

**Hinweis**: Diese Funktion muss von der Anwendung aufgerufen werden, wenn ein HTTP-Vorgang abgeschlossen wurde. Die ID der HTTP-Antwort muss mit der ID der HTTP-Anforderung identisch sein, damit MIP eine Antwort mit Ihrer Anforderung korrelieren kann. 

```c
void MIP_CC_NotifyHttpDelegateResponse(
    const mip_cc_http_delegate httpDelegate,
    const char* requestId,
    const mip_cc_http_result result,
    const mip_cc_http_response* response);
```

## <a name="mip_cc_releasehttpdelegate"></a>MIP_CC_ReleaseHttpDelegate

Freigabe Ressourcen, die einem http-delegathandle zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| httpdelegat | Zu veröffentlichende http-Delegat |

```c
void MIP_CC_ReleaseHttpDelegate(mip_cc_http_delegate httpDelegate);
```

## <a name="mip_cc_logger_init_callback_fn"></a>mip_cc_logger_init_callback_fn

Rückruf Funktionsdefinition für die Initialisierung der Protokollierung

**Parameters**

Parameter | Description
|---|---|
| storagepath | Dateipfad, in dem Protokolle gespeichert werden können |

```c
MIP_CC_CALLBACK(mip_cc_logger_init_callback_fn,
    void,
    const char*);
```

## <a name="mip_cc_logger_write_callback_fn"></a>mip_cc_logger_write_callback_fn

Rückruf Funktionsdefinition zum Schreiben einer Log-Anweisung

**Parameters**

Parameter | Description
|---|---|
| level | die Protokollebene für die Log-Anweisung. |
| message | die Meldung für die Log-Anweisung. |
| Funktion | der Funktionsname der Log-Anweisung. |
| Datei | der Dateiname, in dem die Log-Anweisung generiert wurde. |
| Zeile | die Zeilennummer, in der die Log-Anweisung generiert wurde. |

```c
MIP_CC_CALLBACK(mip_cc_logger_write_callback_fn,
    void,
    const mip_cc_log_level,
    const char*,
    const char*,
    const char*,
    const int32_t);
```

## <a name="mip_cc_createloggerdelegate"></a>MIP_CC_CreateLoggerDelegate

Erstellt einen Logger-Delegaten, der zum Überschreiben der Standard Protokollierung von MIP verwendet werden kann

**Parameters**

Parameter | Description
|---|---|
| initcallback | Funktionszeiger für die Initialisierung |
| flushcallback | Funktionszeiger für das Leeren von Protokollen |
| Rück Rückruf | Funktionszeiger zum Schreiben einer Log-Anweisung |
| loggerdelegat | Ausgeben Handle für Logger-Delegatobjekt |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_CreateLoggerDelegate(
    const mip_cc_logger_init_callback_fn initCallback,
    const mip_cc_logger_flush_callback_fn flushCallback,
    const mip_cc_logger_write_callback_fn writeCallback,
    mip_cc_logger_delegate* loggerDelegate);
```

## <a name="mip_cc_releaseloggerdelegate"></a>MIP_CC_ReleaseLoggerDelegate

Freigabe Ressourcen, die einem Protokollierungs delegathandle zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| loggerdelegat | zu veröffentlichende Protokollierungs Delegat |

```c
void MIP_CC_ReleaseLoggerDelegate(mip_cc_logger_delegate loggerDelegate);
```

## <a name="mip_cc_createmipcontext"></a>MIP_CC_CreateMipContext

Erstellen eines MIP-Kontexts zum Verwalten des Zustands, der für alle Profil Instanzen verwendet wird

**Parameters**

Parameter | Description
|---|---|
| applicationInfo | Informationen über die Anwendung, die das Schutz-SDK nutzt |
| path | Dateipfad, unter dem Protokollierung, Telemetrie und andere Schutz-Begleitelemente gespeichert werden |
| logLevel | Mindestprotokolliergrad für. miplog |
| isofflineonly | Netzwerk Vorgänge aktivieren/deaktivieren (nicht alle Aktionen, die offline unterstützt werden) |
| loggerdelegateoverride | Optionale Protokollierungs Überschreibungs Implementierung |
| telemetryoverride | Optionale Überschriebene telemetrieeinstellungen. Wenn der Wert NULL ist, werden die Standardeinstellungen verwendet. |
| mipcontext | Ausgeben Neu erstellte MIP-Kontext Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_CreateMipContext(
    const mip_cc_application_info* applicationInfo,
    const char* path,
    const mip_cc_log_level logLevel,
    const bool isOfflineOnly,
    const mip_cc_logger_delegate loggerDelegateOverride,
    const mip_cc_telemetry_configuration telemetryOverride,
    mip_cc_mip_context* mipContext);
```

## <a name="mip_cc_createmipcontextwithcustomfeaturesettings"></a>MIP_CC_CreateMipContextWithCustomFeatureSettings

Erstellen eines MIP-Kontexts zum Verwalten des Zustands, der für alle Profil Instanzen verwendet wird

**Parameters**

Parameter | Description
|---|---|
| applicationInfo | Informationen über die Anwendung, die das Schutz-SDK nutzt |
| path | Dateipfad, unter dem Protokollierung, Telemetrie und andere Schutz-Begleitelemente gespeichert werden |
| logLevel | Mindestprotokolliergrad für. miplog |
| isofflineonly | Netzwerk Vorgänge aktivieren/deaktivieren (nicht alle Aktionen, die offline unterstützt werden) |
| loggerdelegateoverride | Optionale Protokollierungs Überschreibungs Implementierung |
| telemetryoverride | Optionale Überschriebene telemetrieeinstellungen. Wenn der Wert NULL ist, werden die Standardeinstellungen verwendet. |
| featuresettings | Optionale Array von außer Kraft setzungen von benutzerdefinierten Funktionen |
| featuresettingssize | Größe von außer Kraft setzungen von benutzerdefinierten Features (in Anzahl von außer Kraft setzungen) |
| mipcontext | Ausgeben Neu erstellte MIP-Kontext Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_CreateMipContextWithCustomFeatureSettings(
    const mip_cc_application_info* applicationInfo,
    const char* path,
    const mip_cc_log_level logLevel,
    const bool isOfflineOnly,
    const mip_cc_logger_delegate loggerDelegateOverride,
    const mip_cc_telemetry_configuration telemetryOverride,
    const mip_cc_feature_override* featureSettings,
    const int64_t featureSettingsSize,
    mip_cc_mip_context* mipContext);
```

## <a name="mip_cc_releasemipcontext"></a>MIP_CC_ReleaseMipContext

Freigeben von Ressourcen, die einem MIP-Kontext zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| mipcontext | Zu veröffentlichende MIP-Kontext |

```c
void MIP_CC_ReleaseMipContext(mip_cc_mip_context mipContext);
```

## <a name="mip_cc_protectiondescriptor_getprotectiontype"></a>MIP_CC_ProtectionDescriptor_GetProtectionType

Ruft den Typ des Schutzes ab, unabhängig davon, ob er durch eine RMS-Vorlage definiert ist.

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| ProtectionType | Ausgeben Schutztyp |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetProtectionType(
    const mip_cc_protection_descriptor protectionDescriptor,
    mip_cc_protection_type* protectionType);
```

## <a name="mip_cc_protectiondescriptor_getownersize"></a>MIP_CC_ProtectionDescriptor_GetOwnerSize

Ruft die Größe des zum Speichern des Besitzers erforderlichen Puffers ab

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| Besitzer Größe | Ausgeben Größe des Puffers für den Besitzer (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetOwnerSize(
    const mip_cc_protection_descriptor protectionDescriptor,
    int64_t* ownerSize);
```

## <a name="mip_cc_protectiondescriptor_getowner"></a>MIP_CC_ProtectionDescriptor_GetOwner

Ruft den Schutz Besitzer ab

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| Besitzer Puffer | Ausgeben Puffer, in den der Besitzer kopiert wird. |
| Besitzer Puffergröße | Größe (in Anzahl der Zeichen) des Besitzer Puffers. |
| actualownersize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn "Besitzer Buffer" NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und "actualownersize" wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetOwner(
    const mip_cc_protection_descriptor protectionDescriptor,
    char* ownerBuffer,
    const int64_t ownerBufferSize,
    int64_t* actualOwnerSize);
```

## <a name="mip_cc_protectiondescriptor_getnamesize"></a>MIP_CC_ProtectionDescriptor_GetNameSize

Ruft die Größe des zum Speichern des Namens erforderlichen Puffers ab

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| namesize | Ausgeben Größe des zu haltenen Puffers (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetNameSize(
    const mip_cc_protection_descriptor protectionDescriptor,
    int64_t* nameSize);
```

## <a name="mip_cc_protectiondescriptor_getname"></a>MIP_CC_ProtectionDescriptor_GetName

Ruft den Schutz Namen ab

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| namebuffer | Ausgeben Puffer, in den der Name kopiert wird. |
| namebuffersize | Größe (in Anzahl der Zeichen) des namebuffer. |
| actualnamesize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn namebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualnamesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetName(
    const mip_cc_protection_descriptor protectionDescriptor,
    char* nameBuffer,
    const int64_t nameBufferSize,
    int64_t* actualNameSize);
```

## <a name="mip_cc_protectiondescriptor_getdescriptionsize"></a>MIP_CC_ProtectionDescriptor_GetDescriptionSize

Ruft die Größe des Puffers zum Speichern der Beschreibung ab.

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| deskriptionsize | Ausgeben Größe des Puffers zum Speichern der Beschreibung (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetDescriptionSize(
    const mip_cc_protection_descriptor protectionDescriptor,
    int64_t* descriptionSize);
```

## <a name="mip_cc_protectiondescriptor_getdescription"></a>MIP_CC_ProtectionDescriptor_GetDescription

Ruft die Schutz Beschreibung ab

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| deskriptionbuffer | Ausgeben Puffer, in den die Beschreibung kopiert wird. |
| deskriptionbuffersize | Die Größe (in Anzahl der Zeichen) des deskriptionbuffer. |
| actualdescriptionsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn descriptionbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben und actualdescriptionsize auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetDescription(
    const mip_cc_protection_descriptor protectionDescriptor,
    char* descriptionBuffer,
    const int64_t descriptionBufferSize,
    int64_t* actualDescriptionSize);
```

## <a name="mip_cc_protectiondescriptor_gettemplateid"></a>MIP_CC_ProtectionDescriptor_GetTemplateId

Ruft Vorlagen-ID ab

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| TemplateID | Ausgeben Dem Schutz zugeordnete Vorlagen-ID |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetTemplateId(
    const mip_cc_protection_descriptor protectionDescriptor,
    mip_cc_guid* templateId);
```

## <a name="mip_cc_protectiondescriptor_getlabelid"></a>MIP_CC_ProtectionDescriptor_GetLabelId

Bezeichnungs-ID abrufen

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| LabelId | Ausgeben Dem Schutz zugeordnete Bezeichnungs-ID |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetLabelId(
    const mip_cc_protection_descriptor protectionDescriptor,
    mip_cc_guid* labelId);
```

## <a name="mip_cc_protectiondescriptor_getcontentid"></a>MIP_CC_ProtectionDescriptor_GetContentId

Ruft Inhalts-ID ab

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| contentId | Ausgeben Dem Schutz zugeordnete Inhalts-ID |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetContentId(
    const mip_cc_protection_descriptor protectionDescriptor,
    mip_cc_guid* contentId);
```

## <a name="mip_cc_protectiondescriptor_doescontentexpire"></a>MIP_CC_ProtectionDescriptor_DoesContentExpire

Ruft ab, ob der Inhalt eine Ablaufzeit aufweist oder nicht.

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| doescontentexpire | Ausgeben Ob Inhalt abläuft |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_DoesContentExpire(
    const mip_cc_protection_descriptor protectionDescriptor,
    bool* doesContentExpire);
```

## <a name="mip_cc_protectiondescriptor_getcontentvaliduntil"></a>MIP_CC_ProtectionDescriptor_GetContentValidUntil

Ruft die Ablaufzeit des Schutzes ab (in Sekunden seit der Epoche).

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| contentvaliduntil | Ausgeben Ablaufzeit des Inhalts (in Sekunden seit der Epoche) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetContentValidUntil(
    const mip_cc_protection_descriptor protectionDescriptor,
    int64_t* contentValidUntil);
```

## <a name="mip_cc_protectiondescriptor_doesallowofflineaccess"></a>MIP_CC_ProtectionDescriptor_DoesAllowOfflineAccess

Ruft ab, ob der Offline Zugriff zulässig ist.

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| doesallowofflineaccess | Ausgeben Gibt an, ob der Offline Zugriff zulässig ist. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_DoesAllowOfflineAccess(
    const mip_cc_protection_descriptor protectionDescriptor,
    bool* doesAllowOfflineAccess);
```

## <a name="mip_cc_protectiondescriptor_getreferrersize"></a>MIP_CC_ProtectionDescriptor_GetReferrerSize

Ruft die Größe des für die Speicher Verweise erforderlichen Puffers ab.

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| referenrersize | Ausgeben Größe des Puffers, der referenrer (in Anzahl von Zeichen) enthalten sein soll. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetReferrerSize(
    const mip_cc_protection_descriptor protectionDescriptor,
    int64_t* referrerSize);
```

## <a name="mip_cc_protectiondescriptor_getreferrer"></a>MIP_CC_ProtectionDescriptor_GetReferrer

Ruft Schutz Verweise ab.

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Dem geschützten Inhalt zugeordneter Deskriptor |
| Verweis Puffer | Ausgeben Puffer, in den der referenrer kopiert wird. |
| referenrerbuffersize | Die Größe (in Anzahl der Zeichen) des referrerpuffers. |
| actualreferrersize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn referrerbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualreferrersize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_ProtectionDescriptor_GetReferrer(
    const mip_cc_protection_descriptor protectionDescriptor,
    char* referrerBuffer,
    const int64_t referrerBufferSize,
    int64_t* actualReferrerSize);
```

## <a name="mip_cc_releaseprotectiondescriptor"></a>MIP_CC_ReleaseProtectionDescriptor

Freigeben von Ressourcen, die einer Schutz Beschreibung zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Schutz Deskriptor | Zu veröffentlichende Schutz Deskriptoren |

```c
void MIP_CC_ReleaseProtectionDescriptor(mip_cc_protection_descriptor protectionDescriptor);
```

## <a name="mip_cc_createstringlist"></a>MIP_CC_CreateStringList

Zeichen folgen Liste erstellen

**Parameters**

Parameter | Description
|---|---|
| Zeichenfolgen | Ein Array von Zeichenfolgen |
| count | Anzahl von Zeichen folgen |
| stringlist | Ausgeben Neu erstellte Zeichen folgen Liste |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: ein mip_cc_string_list muss durch Aufrufen von freigegeben werden MIP_CC_ReleaseStringList 

```c
mip_cc_result MIP_CC_CreateStringList(
    const char** strings,
    const int64_t count,
    mip_cc_string_list* stringList);
```

## <a name="mip_cc_stringlist_getstrings"></a>MIP_CC_StringList_GetStrings

Zeichen folgen, die eine Zeichen folgen Liste bilden, erhalten

**Parameters**

Parameter | Description
|---|---|
| stringlist | Quell Zeichen folgen Liste |
| Zeichenfolgen | Ausgeben Array von Zeichen folgen, Arbeitsspeicher im Besitz mip_cc_string_list Objekts |
| count | Ausgeben Anzahl von Zeichen folgen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: der Speicher für ' Strings ' liegt im Besitz des mip_cc_string_list Objekts und sollte daher nicht unabhängig freigegeben werden. 

```c
mip_cc_result MIP_CC_StringList_GetStrings(
    const mip_cc_string_list stringList,
    const char*** strings,
    int64_t* count);
```

## <a name="mip_cc_releasestringlist"></a>MIP_CC_ReleaseStringList

Freigeben von Ressourcen, die einer Zeichen folgen Liste zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| stringlist | Zu veröffentlichende Zeichen folgen Liste |

```c
void MIP_CC_ReleaseStringList(mip_cc_string_list stringList);
```

## <a name="mip_cc_dispatch_task_callback_fn"></a>mip_cc_dispatch_task_callback_fn

Rückruf Funktionsdefinition für das Senden einer asynchronen Aufgabe

**Parameters**

Parameter | Description
|---|---|
| taskId | Bezeichner für eindeutige Aufgabe |

```c
MIP_CC_CALLBACK(mip_cc_dispatch_task_callback_fn,
    void,
    const mip_cc_async_task*);
```

## <a name="mip_cc_cancel_task_callback_fn"></a>mip_cc_cancel_task_callback_fn

Rückruffunktion zum Abbrechen von Hintergrundaufgaben

**Parameters**

Parameter | Description
|---|---|
| taskId | Bezeichner für eindeutige Aufgabe |

**Return**: true, wenn die Aufgabe erfolgreich abgebrochen wurde, andernfalls false.

```c
MIP_CC_CALLBACK(mip_cc_cancel_task_callback_fn,
    bool,
    const char*);
```

## <a name="mip_cc_createtaskdispatcherdelegate"></a>MIP_CC_CreateTaskDispatcherDelegate

Erstellt einen Aufgaben Verteiler Delegaten, der zum Überschreiben der standardmäßigen asynchronen Task Verarbeitung von MIP verwendet werden kann.

**Parameters**

Parameter | Description
|---|---|
| dispatchtaskcallback | Funktionszeiger für die Verteilung asynchroner Aufgaben |
| canceltaskcallback | Funktionszeiger zum Abbrechen von Hintergrundaufgaben |
| cancelalltaskscallback | Funktionszeiger zum Abbrechen aller Hintergrundaufgaben |
| taskdispatcher | Ausgeben Handle für taskdispatcher-Delegatobjekt |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_CreateTaskDispatcherDelegate(
    const mip_cc_dispatch_task_callback_fn dispatchTaskCallback,
    const mip_cc_cancel_task_callback_fn cancelTaskCallback,
    const mip_cc_cancel_all_tasks_callback_fn cancelAllTasksCallback,
    mip_cc_task_dispatcher_delegate* taskDispatcher);
```

## <a name="mip_cc_executedispatchedtask"></a>MIP_CC_ExecuteDispatchedTask

Benachrichtigt einen taskdispatcher-Delegaten, dass eine Aufgabe jetzt für die Ausführung im aktuellen Thread geplant ist.

**Parameters**

Parameter | Description
|---|---|
| taskdispatcher | Handle für taskdispatcher-Delegatobjekt |
| taskId | ID des Async-Tasks, der diesem Vorgang zugeordnet ist. |

**Hinweis**: Diese Funktion muss von der Anwendung aufgerufen werden, wenn eine Aufgabe für die Ausführung geplant ist. Dies führt dazu, dass die Aufgabe sofort im aktuellen Thread ausgeführt wird. Die ID sollte mit der einer zuvor verteilten, nicht abgebrochenen Aufgabe identisch sein. 

```c
void MIP_CC_ExecuteDispatchedTask(const mip_cc_task_dispatcher_delegate taskDispatcher, const char* taskId);
```

## <a name="mip_cc_releasetaskdispatcherdelegate"></a>MIP_CC_ReleaseTaskDispatcherDelegate

Freigeben von Ressourcen, die einem Aufgaben Verteiler-delegathandle zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| taskdispatcher | Zu veröffentlichende taskdispatcher-Delegat |

```c
void MIP_CC_ReleaseTaskDispatcherDelegate(mip_cc_task_dispatcher_delegate taskDispatcher);
```

## <a name="mip_cc_telemetryconfiguration_sethostname"></a>MIP_CC_TelemetryConfiguration_SetHostName

Festlegen eines telemetriehostnamens, der interne telemetrieeinstellungen außer Kraft setzt

**Parameters**

Parameter | Description
|---|---|
| telemetryConfig | Telemetriekonfiguration |
| hostName | Hostname |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Diese Eigenschaft wird festgelegt, wenn eine Client Anwendung dieselbe Aria/1Ds-telemetriekomponente verwendet und die internen telemetrieeinstellungen (Caching, Protokollierung, Priorität usw.) anstelle der Standardeinstellungen von MIP verwendet werden sollen. 

```c
mip_cc_result MIP_CC_TelemetryConfiguration_SetHostName(
    const mip_cc_telemetry_configuration telemetryConfig,
    const char* hostName);
```

## <a name="mip_cc_telemetryconfiguration_setlibraryname"></a>MIP_CC_TelemetryConfiguration_SetLibraryName

Überschreiben einer freigegebenen telemetriebibliothek festlegen

**Parameters**

Parameter | Description
|---|---|
| telemetryConfig | Telemetriekonfiguration |
| libraryName | Name der dll, die die C-API des Aria/1Ds SDK implementiert |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Diese Eigenschaft wird festgelegt, wenn ein Client über eine vorhandene Telemetrie-dll verfügt, die die C-API des Aria/1Ds SDK implementiert, die anstelle von mip_ClientTelemetry. dll verwendet werden soll. 

```c
mip_cc_result MIP_CC_TelemetryConfiguration_SetLibraryName(
    const mip_cc_telemetry_configuration telemetryConfig,
    const char* libraryName);
```

## <a name="mip_cc_telemetryconfiguration_sethttpdelegate"></a>MIP_CC_TelemetryConfiguration_SetHttpDelegate

Standard-Telemetrie-HTTP-Stapel mit eigenem Client überschreiben

**Parameters**

Parameter | Description
|---|---|
| telemetryConfig | Telemetriekonfiguration |
| httpdelegat | Von der Client Anwendung implementierte HTTP-Rückruf Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn diese Eigenschaft nicht festgelegt ist, wird von der telemetriekomponente der Standard-HTTP-Stapel von MIP verwendet. 

```c
mip_cc_result MIP_CC_TelemetryConfiguration_SetHttpDelegate(
    const mip_cc_telemetry_configuration telemetryConfig,
    const mip_cc_http_delegate httpDelegate);
```

## <a name="mip_cc_telemetryconfiguration_setisnetworkdetectionenabled"></a>MIP_CC_TelemetryConfiguration_SetIsNetworkDetectionEnabled

Legt fest, ob für die telemetriekomponente ein Ping-Netzwerkstatus in einem Hintergrund Thread zulässig ist.

**Parameters**

Parameter | Description
|---|---|
| telemetryConfig | Telemetriekonfiguration |
| iscachingenabled | Gibt an, ob für die telemetriekomponente ein Ping-Netzwerkstatus in einem Hintergrund Thread zulässig ist. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: der Standardwert ist "true". 

```c
mip_cc_result MIP_CC_TelemetryConfiguration_SetIsNetworkDetectionEnabled(
    const mip_cc_telemetry_configuration telemetryConfig,
    const bool isNetworkDetectionEnabled);
```

## <a name="mip_cc_telemetryconfiguration_setislocalcachingenabled"></a>MIP_CC_TelemetryConfiguration_SetIsLocalCachingEnabled

Legt fest, ob die telemetriekomponente Caches auf den Datenträger schreiben darf.

**Parameters**

Parameter | Description
|---|---|
| telemetryConfig | Telemetriekonfiguration |
| iscachingenabled | Gibt an, ob die telemetriekomponente Caches auf den Datenträger schreiben darf. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: der Standardwert ist "true". 

```c
mip_cc_result MIP_CC_TelemetryConfiguration_SetIsLocalCachingEnabled(
    const mip_cc_telemetry_configuration telemetryConfig,
    const bool isCachingEnabled);
```

## <a name="mip_cc_telemetryconfiguration_setistraceloggingenabled"></a>MIP_CC_TelemetryConfiguration_SetIsTraceLoggingEnabled

Legt fest, ob die telemetriekomponente Protokolle auf den Datenträger schreiben darf.

**Parameters**

Parameter | Description
|---|---|
| telemetryConfig | Telemetriekonfiguration |
| istraceloggingenabled | Gibt an, ob die telemetriekomponente Protokolle auf den Datenträger schreiben darf. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: der Standardwert ist "true". 

```c
mip_cc_result MIP_CC_TelemetryConfiguration_SetIsTraceLoggingEnabled(
    const mip_cc_telemetry_configuration telemetryConfig,
    const bool isTraceLoggingEnabled);
```

## <a name="mip_cc_telemetryconfiguration_setistelemetryoptedout"></a>MIP_CC_TelemetryConfiguration_SetIsTelemetryOptedOut

Legt fest, ob eine Anwendung bzw. ein Benutzer die optionale Telemetrie deaktiviert hat.

**Parameters**

Parameter | Description
|---|---|
| telemetryConfig | Telemetriekonfiguration |
| istelemetryoptedout | Gibt an, ob eine Anwendung bzw. ein Benutzer die optionale Telemetrie deaktiviert hat. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: der Standardwert ist ' false '. 

```c
mip_cc_result MIP_CC_TelemetryConfiguration_SetIsTelemetryOptedOut(
    const mip_cc_telemetry_configuration telemetryConfig,
    const bool isTelemetryOptedOut);
```

## <a name="mip_cc_telemetryconfiguration_setcustomsettings"></a>MIP_CC_TelemetryConfiguration_SetCustomSettings

Legt benutzerdefinierte telemetrieeinstellungen fest

**Parameters**

Parameter | Description
|---|---|
| telemetryConfig | Telemetriekonfiguration |
| Datei "CustomSettings | Benutzerdefinierte telemetrieeinstellungen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_TelemetryConfiguration_SetCustomSettings(
    const mip_cc_telemetry_configuration telemetryConfig,
    const mip_cc_dictionary customSettings);
```

## <a name="mip_cc_releasetelemetryconfiguration"></a>MIP_CC_ReleaseTelemetryConfiguration

Freigeben von Ressourcen, die mit einer Schutzprofil Einstellung verknüpft sind

**Parameters**

Parameter | Description
|---|---|
| Profile Settings | Zu veröffentlichende Schutzprofil Einstellungen |

```c
void MIP_CC_ReleaseTelemetryConfiguration(mip_cc_telemetry_configuration telemetryConfig);
```

## <a name="mip_cc_releaseprotectionengine"></a>MIP_CC_ReleaseProtectionEngine

Freigeben von Ressourcen, die einer Schutz-Engine zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Engine | Zu veröffentlichensendem Schutz Modul |

```c
void MIP_CC_ReleaseProtectionEngine(mip_cc_protection_engine engine);
```

## <a name="mip_cc_protectionengine_createprotectionhandlerforpublishing"></a>MIP_CC_ProtectionEngine_CreateProtectionHandlerForPublishing

Erstellt einen Schutz Handler zum Veröffentlichen von neuem Inhalt.

**Parameters**

Parameter | Description
|---|---|
| Engine | Engine, unter der ein Handler erstellt wird |
| Einstellungen | Einstellungen für den Schutz Handler |
| context | Client Kontext, der an httpdelegaten und authdelegat übergeben wird |
| Handler | Ausgeben Neu erstellte schutzhandlerinstanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionEngine_CreateProtectionHandlerForPublishing(
    const mip_cc_protection_engine engine,
    const mip_cc_protection_handler_publishing_settings settings,
    const void* context,
    mip_cc_protection_handler* handler);
```

## <a name="mip_cc_protectionengine_createprotectionhandlerforconsumption"></a>MIP_CC_ProtectionEngine_CreateProtectionHandlerForConsumption

Erstellt einen Schutz Handler für die Verwendung von vorhandenem Inhalt.

**Parameters**

Parameter | Description
|---|---|
| Engine | Engine, unter der ein Handler erstellt wird |
| Einstellungen | Einstellungen für den Schutz Handler |
| context | Client Kontext, der an httpdelegaten und authdelegat übergeben wird |
| Handler | Ausgeben Neu erstellte schutzhandlerinstanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionEngine_CreateProtectionHandlerForConsumption(
  const mip_cc_protection_engine engine,
  const mip_cc_protection_handler_consumption_settings settings,
  const void* context,
  mip_cc_protection_handler* handler);
```

## <a name="mip_cc_protectionengine_getengineidsize"></a>MIP_CC_ProtectionEngine_GetEngineIdSize

Ruft die Größe des für Engine-ID erforderlichen Puffers ab

**Parameters**

Parameter | Description
|---|---|
| Engine | Schutz-Engine |
| idsize | Ausgeben Größe des Puffers für die Engine-ID (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionEngine_GetEngineIdSize(
    const mip_cc_protection_engine engine,
    int64_t* idSize);
```

## <a name="mip_cc_protectionengine_getengineid"></a>MIP_CC_ProtectionEngine_GetEngineId

Ruft Engine-ID ab

**Parameters**

Parameter | Description
|---|---|
| Engine | Schutz-Engine |
| idbuffer | Ausgeben Puffer, in den die ID kopiert wird. |
| idbuffersize | Größe (in Anzahl der Zeichen) des idbuffer. |
| actualidsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn idbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualidsize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_ProtectionEngine_GetEngineId(
    const mip_cc_protection_engine engine,
    char* idBuffer,
    const int64_t idBufferSize,
    int64_t* actualIdSize);
```

## <a name="mip_cc_protectionengine_gettemplatessize"></a>MIP_CC_ProtectionEngine_GetTemplatesSize

Ruft die Anzahl von RMS-Vorlagen ab, die einer Schutz-Engine zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Engine | Schutz-Engine |
| context | Client Kontext, der an httpdelegaten und authdelegat übergeben wird |
| templatessize | Ausgeben Anzahl der Vorlagen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Diese API kann zu einem unabhängigen http-Vorgang führen. Verwenden Sie ggf. "MIP_CC_ProtectionEngine_GetTemplates" direkt mit einem vordefinierten Puffer, um unnötige zusätzliche http-Vorgänge zu vermeiden. 

```c
mip_cc_result MIP_CC_ProtectionEngine_GetTemplatesSize(
    const mip_cc_protection_engine engine,
    const void* context,
    int64_t* templatesSize);
```

## <a name="mip_cc_protectionengine_gettemplates"></a>MIP_CC_ProtectionEngine_GetTemplates

Sammlung von Vorlagen für Benutzer verfügbar machen

**Parameters**

Parameter | Description
|---|---|
| Engine | Schutz-Engine |
| context | Client Kontext, der an httpdelegaten und authdelegat übergeben wird |
| templatebuffer | Ausgeben Puffer, in den die Vorlagen kopiert werden. |
| templatebuffersize | Größe (in Anzahl der Elemente) des templatebuffer. |
| actualtemplatessize | Ausgeben Anzahl der in den Puffer geschriebenen Vorlagen-IDs |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn templatebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualtemplatesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_ProtectionEngine_GetTemplates(
    const mip_cc_protection_engine engine,
    const void* context,
    mip_cc_guid* templateBuffer,
    const int64_t templateBufferSize,
    int64_t* actualTemplatesSize);
```

## <a name="mip_cc_protectionengine_getrightsforlabelid"></a>MIP_CC_ProtectionEngine_GetRightsForLabelId

Liste der Rechte, die einem Benutzer für eine Bezeichnungs-ID erteilt werden

**Parameters**

Parameter | Description
|---|---|
| Engine | Schutz-Engine |
| context | Client Kontext, der an httpdelegaten und authdelegat übergeben wird |
| documentId | Dokument-ID, die dem Dokument zugewiesen ist |
| LabelId | Bezeichnungs-ID auf das Dokument angewendet |
| ownerEmail | Besitzer des Dokuments |
| Delta-e-Mail | E-Mail-Adresse des Benutzers, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert, leer, wenn keine |
| Rechte | Ausgeben Liste der Rechte, die einem Benutzer gewährt wurden, Arbeitsspeicher im Besitz des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die Rights-Variable muss vom Aufrufer durch Aufrufen von freigegeben werden MIP_CC_ReleaseStringList 

```c
mip_cc_result MIP_CC_ProtectionEngine_GetRightsForLabelId(
    const mip_cc_protection_engine engine,
    const void* context,
    const char* documentId,
    const char* labelId,
    const char* ownerEmail,
    const char* delegatedUserEmail,
    mip_cc_string_list* rights);
```

## <a name="mip_cc_protectionengine_getclientdatasize"></a>MIP_CC_ProtectionEngine_GetClientDataSize

Ruft die Größe der Client Daten ab, die einer Schutz-Engine zugeordnet sind.

**Parameters**

Parameter | Description
|---|---|
| Engine | Schutz-Engine |
| clientdatasize | Ausgeben Größe der Client Daten (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionEngine_GetClientDataSize(
    const mip_cc_protection_engine engine,
    int64_t* clientDataSize);
```

## <a name="mip_cc_protectionengine_getclientdata"></a>MIP_CC_ProtectionEngine_GetClientData

Client Daten erhalten, die einer Schutz-Engine zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Engine | Schutz-Engine |
| clientdatabuffer | Ausgeben Puffer, in den die Client Daten kopiert werden |
| clientdatabuffersize | Größe (in Anzahl von Zeichen) von clientdatabuffer. |
| actualclientdatasize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn clientdatabuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualclientdatasize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_ProtectionEngine_GetClientData(
    const mip_cc_protection_engine engine,
    char* clientDataBuffer,
    const int64_t clientDataBufferSize,
    int64_t* actualClientDataSize);
```

## <a name="mip_cc_createprotectionenginesettingswithidentity"></a>MIP_CC_CreateProtectionEngineSettingsWithIdentity

Erstellen Sie ein Einstellungs Objekt, das zum Erstellen einer neuen Schutz-Engine verwendet wird.

**Parameters**

Parameter | Description
|---|---|
| Identität | Identität, die Schutz-Engine zugeordnet wird |
| clientData | Anpassbare Client Daten, die neben der Engine gespeichert werden |
| Gebietsschema | Das Gebiets Schema, in dem Text Ergebnisse ausgegeben werden. |
| EngineSettings | Ausgeben Neu erstellte Einstellungs Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_CreateProtectionEngineSettingsWithIdentity(
    const mip_cc_identity* identity,
    const char* clientData,
    const char* locale,
    mip_cc_protection_engine_settings* engineSettings);
```

## <a name="mip_cc_protectionenginesettings_setclientdata"></a>MIP_CC_ProtectionEngineSettings_SetClientData

Legt die Client Daten fest, die mit dieser Engine verdeckt gespeichert werden und Sitzungs übergreifend beibehalten werden

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Engine-Einstellungen |
| clientData | Client Daten |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionEngineSettings_SetClientData(
    const mip_cc_protection_engine_settings engineSettings,
    const char* clientData);
```

## <a name="mip_cc_protectionenginesettings_setcustomsettings"></a>MIP_CC_ProtectionEngineSettings_SetCustomSettings

Konfiguriert benutzerdefinierte Einstellungen, die zum Gating und Testen von Features verwendet werden.

**Parameters**

Parameter | Description
|---|---|
| EngineSettings | Engine-Einstellungen |
| Datei "CustomSettings | Schlüssel-Wert-Paare von benutzerdefinierten Einstellungen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionEngineSettings_SetCustomSettings(
    const mip_cc_protection_engine_settings engineSettings,
    const mip_cc_dictionary customSettings);
```

## <a name="mip_cc_protectionenginesettings_setsessionid"></a>MIP_CC_ProtectionEngineSettings_SetSessionId

Legt die Sitzungs-ID fest, die zum Korrelieren von Protokollen und Telemetriedaten verwendet werden kann.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Engine-Einstellungen |
| sessionID | Sitzungs-ID, die die Lebensdauer einer Schutz-Engine darstellt |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionEngineSettings_SetSessionId(
    const mip_cc_protection_engine_settings engineSettings,
    const char* sessionId);
```

## <a name="mip_cc_protectionenginesettings_setcloudendpointbaseurl"></a>MIP_CC_ProtectionEngineSettings_SetCloudEndpointBaseUrl

Legt die Basis-URL für alle Service Requests fest.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Engine-Einstellungen |
| cloudendpointbaseurl | Basis-URL (z. b. "https://api.aadrm.com") |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionEngineSettings_SetCloudEndpointBaseUrl(
    const mip_cc_protection_engine_settings engineSettings,
    const char* cloudEndpointBaseUrl);
```

## <a name="mip_cc_releaseprotectionenginesettings"></a>MIP_CC_ReleaseProtectionEngineSettings

Freigeben von Ressourcen, die den Einstellungen der Schutz-Engine zugeordnet

**Parameters**

Parameter | Description
|---|---|
| EngineSettings | Zu veröffentlichende Schutz-Engine-Einstellungen |

```c
void MIP_CC_ReleaseProtectionEngineSettings(mip_cc_protection_engine_settings engineSettings);
```

## <a name="mip_cc_createprotectionhandlerpublishingsettings"></a>MIP_CC_CreateProtectionHandlerPublishingSettings

Erstellen Sie ein Einstellungs Objekt, das zum Erstellen eines Schutz Handlers zum Veröffentlichen neuer Inhalte verwendet wird.

**Parameters**

Parameter | Description
|---|---|
| descriptor | Details zum Schutz |
| Einstellungen | Ausgeben Neu erstellte Einstellungs Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_CreateProtectionHandlerPublishingSettings(
    const mip_cc_protection_descriptor descriptor,
    mip_cc_protection_handler_publishing_settings* settings);
```

## <a name="mip_cc_protectionhandlerpublishingsettings_setisdeprecatedalgorithmpreferred"></a>MIP_CC_ProtectionHandlerPublishingSettings_SetIsDeprecatedAlgorithmPreferred

Legt fest, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Einstellungen für den Schutz Handler |
| isdeprealisiedalgorithmpreferred | Gibt an, ob der als veraltet markierte Algorithmus bevorzugt wird. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandlerPublishingSettings_SetIsDeprecatedAlgorithmPreferred(
    const mip_cc_protection_handler_publishing_settings settings,
    const bool isDeprecatedAlgorithmPreferred);
```

## <a name="mip_cc_protectionhandlerpublishingsettings_setisauditedextractionallowed"></a>MIP_CC_ProtectionHandlerPublishingSettings_SetIsAuditedExtractionAllowed

Legt fest, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Einstellungen für den Schutz Handler |
| isauditedextractionallowed | Gibt an, ob nicht-MIP-fähige Anwendungen geschützte Inhalte öffnen dürfen. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandlerPublishingSettings_SetIsAuditedExtractionAllowed(
    const mip_cc_protection_handler_publishing_settings settings,
    const bool isAuditedExtractionAllowed);
```

## <a name="mip_cc_protectionhandlerpublishingsettings_setispublishingformatjson"></a>MIP_CC_ProtectionHandlerPublishingSettings_SetIsPublishingFormatJson

Legt fest, ob pl im JSON-Format vorliegt (Standardwert ist XML).

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Einstellungen für den Schutz Handler |
| ispublishingformatjson | Gibt an, ob sich die resultierende pl im JSON-Format befinden sollte. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandlerPublishingSettings_SetIsPublishingFormatJson(
    const mip_cc_protection_handler_publishing_settings settings,
    const bool isPublishingFormatJson);
```

## <a name="mip_cc_protectionhandlerpublishingsettings_setdelegateduseremail"></a>MIP_CC_ProtectionHandlerPublishingSettings_SetDelegatedUserEmail

Legt Delegierten Benutzer fest.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Einstellungen für den Schutz Handler |
| delegateduseremail | E-Mail-Adresse des delegierten Benutzers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert. 

```c
mip_cc_result MIP_CC_ProtectionHandlerPublishingSettings_SetDelegatedUserEmail(
    const mip_cc_protection_handler_publishing_settings settings,
    const char* delegatedUserEmail);
```

## <a name="mip_cc_createprotectionhandlerconsumptionsettings"></a>MIP_CC_CreateProtectionHandlerConsumptionSettings

Erstellen eines Einstellungs Objekts, das zum Erstellen eines Schutz Handlers zum Verarbeiten vorhandener Inhalte verwendet wird

**Parameters**

Parameter | Description
|---|---|
| publishinglicenabbuffer | Puffer mit unformatierten Veröffentlichungs Lizenz |
| publishinglicenabbuffersize | Größe des Veröffentlichungs Lizenz Puffers |
| isofflineonly | Gibt an, ob das Abrufen einer neuen Lizenz vom RMS-Server zulässig ist. |
| delegateduseremail | Optionale Benutzer im Auftrag, für den Schutz Vorgänge ausgeführt werden |
| Einstellungen | Ausgeben Neu erstellte Einstellungs Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_CreateProtectionHandlerConsumptionSettings(
    const uint8_t* publishingLicenseBuffer,
    const int64_t publishingLicenseBufferSize,
    mip_cc_protection_handler_consumption_settings* settings);
```

## <a name="mip_cc_protectionhandlerconsumptionsettings_setisofflineonly"></a>MIP_CC_ProtectionHandlerConsumptionSettings_SetIsOfflineOnly

Legt fest, ob die Erstellung von Schutz Handlern Online-http-Vorgänge zulässt

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Einstellungen für den Schutz Handler |
| isofflineonly | True, wenn http-Vorgänge nicht zulässig sind, andernfalls false. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn diese Eigenschaft auf "true" festgelegt ist, wird die Erstellung des Schutz Handlers nur erfolgreich ausgeführt, wenn der Inhalt bereits zuvor entschlüsselt und seine nicht abgelaufene Lizenz zwischengespeichert wird. Wenn zwischen gespeicherter Inhalt nicht gefunden wird, wird ein MIP_RESULT_ERROR_NETWORK Ergebnis zurückgegeben. 

```c
mip_cc_result MIP_CC_ProtectionHandlerConsumptionSettings_SetIsOfflineOnly(
    const mip_cc_protection_handler_consumption_settings settings,
    const bool isOfflineOnly);
```

## <a name="mip_cc_protectionhandlerconsumptionsettings_setdelegateduseremail"></a>MIP_CC_ProtectionHandlerConsumptionSettings_SetDelegatedUserEmail

Legt Delegierten Benutzer fest.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Einstellungen für den Schutz Handler |
| delegateduseremail | E-Mail-Adresse des delegierten Benutzers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert. 

```c
mip_cc_result MIP_CC_ProtectionHandlerConsumptionSettings_SetDelegatedUserEmail(
    const mip_cc_protection_handler_consumption_settings settings,
    const char* delegatedUserEmail);
```

## <a name="mip_cc_protectionhandler_getserializedpublishinglicensesize"></a>MIP_CC_ProtectionHandler_GetSerializedPublishingLicenseSize

Ruft die Größe der Veröffentlichungs Lizenz ab (in Bytes).

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| publishinglicenabbuffersize | Ausgeben Größe der Veröffentlichungs Lizenz (in Bytes) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandler_GetSerializedPublishingLicenseSize(
    const mip_cc_protection_handler handler,
    int64_t* publishingLicenseBufferSize);
```

## <a name="mip_cc_protectionhandler_getserializedpublishinglicense"></a>MIP_CC_ProtectionHandler_GetSerializedPublishingLicense

Ruft die Veröffentlichungs Lizenz ab

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| publishinglicenabbuffer | Ausgeben Puffer, in den die Veröffentlichungs Lizenz geschrieben wird |
| publishinglicenabbuffersize | Größe des Veröffentlichungs Lizenz Puffers |
| actualpublishinglicen\size | Ausgeben Tatsächliche Größe der Veröffentlichungs Lizenz (in Bytes) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn publishinglicensebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualpublishinglicensesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_ProtectionHandler_GetSerializedPublishingLicense(
    const mip_cc_protection_handler handler,
    uint8_t* publishingLicenseBuffer,
    const int64_t publishingLicenseBufferSize,
    int64_t* actualPublishingLicenseSize);
```

## <a name="mip_cc_protectionhandler_getprotectiondescriptor"></a>MIP_CC_ProtectionHandler_GetProtectionDescriptor

Ruft den Schutz Deskriptor ab.

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| descriptor | Ausgeben Schutz Beschreibung |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandler_GetProtectionDescriptor(
    const mip_cc_protection_handler handler,
    mip_cc_protection_descriptor* descriptor);
```

## <a name="mip_cc_protectionhandler_getrights"></a>MIP_CC_ProtectionHandler_GetRights

Ruft eine Liste der dem Benutzer gewährten Rechte ab.

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| Rechte | Ausgeben Liste der Rechte, die einem Benutzer gewährt wurden, Arbeitsspeicher im Besitz des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die Rights-Variable muss vom Aufrufer durch Aufrufen von freigegeben werden MIP_CC_ReleaseStringList 

```c
mip_cc_result MIP_CC_ProtectionHandler_GetRights(
    const mip_cc_protection_handler handler,
    mip_cc_string_list* rights);
```

## <a name="mip_cc_protectionhandler_getprotectedcontentsize"></a>MIP_CC_ProtectionHandler_GetProtectedContentSize

Berechnet die Größe geschützter Inhalte, Factoring in Auffüll Zeichen usw.

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| unprotectedsize | Größe des ungeschützten/Klartext-Inhalts (in Bytes) |
| includesfinalblock | Beschreibt, ob der fragliche ungeschützte Inhalt den Endblock enthält oder nicht. |
| protectedsize | Ausgeben Größe geschützter Inhalte |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandler_GetProtectedContentSize(
    const mip_cc_protection_handler handler,
    const int64_t unprotectedSize,
    const bool includesFinalBlock,
    int64_t* protectedSize);
```

## <a name="mip_cc_protectionhandler_getblocksize"></a>MIP_CC_ProtectionHandler_GetBlockSize

Ruft die Blockgröße (in Bytes) für den Verschlüsselungs Modus ab, der von einem Schutz Handler verwendet wird.

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| BlockSize | Ausgeben Block Größe (in Bytes) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandler_GetBlockSize(
    const mip_cc_protection_handler handler,
    int64_t* blockSize);
```

## <a name="mip_cc_protectionhandler_getissuedusersize"></a>MIP_CC_ProtectionHandler_GetIssuedUserSize

Ruft die Größe des Puffers ab, der zum Speichern des Benutzers benötigt wird, dem Zugriff auf geschützte Inhalte gewährt wurde

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| issuedusersize | Ausgeben Größe des Puffers für den ausgestellten Benutzer (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandler_GetIssuedUserSize(
    const mip_cc_protection_handler handler,
    int64_t* issuedUserSize);
```

## <a name="mip_cc_protectionhandler_getissueduser"></a>MIP_CC_ProtectionHandler_GetIssuedUser

Ruft den Benutzer ab, dem Zugriff auf geschützte Inhalte gewährt wurde.

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| issueduserbuffer | Ausgeben Puffer, in den der ausgegebene Benutzer kopiert wird. |
| issueduserbuffersize | Die Größe (in Anzahl der Zeichen) des issueduserbuffer. |
| actualissuedusersize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn issueduserbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualissuedusersize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_ProtectionHandler_GetIssuedUser(
    const mip_cc_protection_handler handler,
    char* issuedUserBuffer,
    const int64_t issuedUserBufferSize,
    int64_t* actualIssuedUserSize);
```

## <a name="mip_cc_protectionhandler_getownersize"></a>MIP_CC_ProtectionHandler_GetOwnerSize

Ruft die Größe des Puffers ab, der zum Speichern des Besitzers geschützter Inhalte benötigt wird.

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| Besitzer Größe | Ausgeben Größe des Puffers für den ausgestellten Benutzer (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandler_GetOwnerSize(
    const mip_cc_protection_handler handler,
    int64_t* ownerSize);
```

## <a name="mip_cc_protectionhandler_getowner"></a>MIP_CC_ProtectionHandler_GetOwner

Ruft den Besitzer geschützter Inhalte ab.

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| Besitzer Puffer | Ausgeben Puffer, in den der ausgegebene Benutzer kopiert wird. |
| Besitzer Puffergröße | Größe (in Anzahl der Zeichen) des Besitzer Puffers. |
| actualownersize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn "Besitzer Buffer" NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und "actualownersize" wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_ProtectionHandler_GetOwner(
    const mip_cc_protection_handler handler,
    char* ownerBuffer,
    const int64_t ownerBufferSize,
    int64_t* actualOwnerSize);
```

## <a name="mip_cc_protectionhandler_getcontentid"></a>MIP_CC_ProtectionHandler_GetContentId

Ruft den Inhalt des geschützten Inhalts ab.

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| contentId | Ausgeben Inhalts-ID |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandler_GetContentId(
    const mip_cc_protection_handler handler,
    mip_cc_guid* contentId);
```

## <a name="mip_cc_protectionhandler_doesusedeprecatedalgorithm"></a>MIP_CC_ProtectionHandler_DoesUseDeprecatedAlgorithm

Ruft ab, ob der Schutz Handler den veralteten Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität verwendet.

**Parameters**

Parameter | Description
|---|---|
| Handler | Handler, der geschützte Inhalte darstellt |
| doesusedeprealisiedalgorithmus | Ausgeben Gibt an, ob der Schutz Handler einen veralteten Kryptografiealgorithmus verwendet. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandler_DoesUseDeprecatedAlgorithm(
    const mip_cc_protection_handler handler,
    bool* doesUseDeprecatedAlgorithm);
```

## <a name="mip_cc_protectionhandler_decryptbuffer"></a>MIP_CC_ProtectionHandler_DecryptBuffer

Entschlüsseln eines Puffers

**Parameters**

Parameter | Description
|---|---|
| offsetfromstart | Relative Position von Input Buffer vom Anfang des verschlüsselten Inhalts |
| inputBuffer | Puffer verschlüsselter Inhalte, die entschlüsselt werden |
| Input bufferSize | Größe (in Bytes) des Eingabe Puffers |
| OUTPUTBUFFER | Ausgeben Puffer, in den der entschlüsselte Inhalt kopiert wird |
| outputbuffersize | Größe des Ausgabepuffers (in Bytes) |
| sowie | Wenn der Eingabepuffer die endgültigen verschlüsselten Bytes enthält oder nicht. |
| actualdecryptedsize | Ausgeben Tatsächliche Größe von verschlüsseltem Inhalt (in Bytes) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionHandler_DecryptBuffer(
    const mip_cc_protection_handler handler,
    const int64_t offsetFromStart,
    const uint8_t* inputBuffer,
    const int64_t inputBufferSize,
    uint8_t* outputBuffer,
    const int64_t outputBufferSize,
    const bool isFinal,
    int64_t *actualDecryptedSize);
```

## <a name="mip_cc_releaseprotectionhandlerpublishingsettings"></a>MIP_CC_ReleaseProtectionHandlerPublishingSettings

Freigeben von Ressourcen, die den Einstellungen eines Schutz Handlers zugeordnet

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Zu veröffentlichende schutzhandlereinstellungen |

```c
void MIP_CC_ReleaseProtectionHandlerPublishingSettings(mip_cc_protection_handler_publishing_settings settings);
```

## <a name="mip_cc_releaseprotectionhandlerconsumptionsettings"></a>MIP_CC_ReleaseProtectionHandlerConsumptionSettings

Freigeben von Ressourcen, die den Einstellungen eines Schutz Handlers zugeordnet

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Zu veröffentlichende schutzhandlereinstellungen |

```c
void MIP_CC_ReleaseProtectionHandlerConsumptionSettings(mip_cc_protection_handler_consumption_settings settings);
```

## <a name="mip_cc_releaseprotectionhandler"></a>MIP_CC_ReleaseProtectionHandler

Freigeben von Ressourcen, die einem Schutz Handler zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Handler | Der zu veröffentlichende Schutz Handler. |

```c
void MIP_CC_ReleaseProtectionHandler(mip_cc_protection_handler handler);
```

## <a name="mip_cc_loadprotectionprofile"></a>MIP_CC_LoadProtectionProfile

Profil laden

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen |
| Profils | Ausgeben Neu erstellte Schutzprofil Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_LoadProtectionProfile(
    const mip_cc_protection_profile_settings settings,
    mip_cc_protection_profile* profile);
```

## <a name="mip_cc_releaseprotectionprofile"></a>MIP_CC_ReleaseProtectionProfile

Freigeben von Ressourcen, die einem Schutzprofil zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Profils | Zu veröffentlichende Schutzprofil |

```c
void MIP_CC_ReleaseProtectionProfile(mip_cc_protection_profile profile);
```

## <a name="mip_cc_protectionprofilesettings_setsessionid"></a>MIP_CC_ProtectionProfileSettings_SetSessionId

Legt die Sitzungs-ID fest, die zum Korrelieren von Protokollen und Telemetriedaten verwendet werden kann.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen |
| sessionID | Die Sitzungs-ID, die die Lebensdauer eines Schutz Profils darstellt. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionProfileSettings_SetSessionId(
    const mip_cc_protection_profile_settings settings,
    const char* sessionId);
```

## <a name="mip_cc_protectionprofilesettings_setcancachelicenses"></a>MIP_CC_ProtectionProfileSettings_SetCanCacheLicenses

Hiermit wird konfiguriert, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen |
| Abbrechen | Gibt an, ob die Engine beim Öffnen von geschütztem Inhalt eine Lizenz zwischenspeichern soll. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionProfileSettings_SetCanCacheLicenses(
    const mip_cc_protection_profile_settings settings,
    const bool canCacheLicenses);
```

## <a name="mip_cc_protectionprofilesettings_sethttpdelegate"></a>MIP_CC_ProtectionProfileSettings_SetHttpDelegate

Standard-HTTP-Stapel mit eigenem Client überschreiben

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen, denen der http-Delegat zugewiesen wird |
| httpdelegat | Von der Client Anwendung implementierte HTTP-Rückruf Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionProfileSettings_SetHttpDelegate(
    const mip_cc_protection_profile_settings settings,
    const mip_cc_http_delegate httpDelegate);
```

## <a name="mip_cc_protectionprofilesettings_settaskdispatcherdelegate"></a>MIP_CC_ProtectionProfileSettings_SetTaskDispatcherDelegate

Standardmäßiger asynchroner Aufgaben Verteiler mit eigenem Client überschreiben

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen, denen der Aufgaben Verteiler Delegat zugewiesen wird |
| taskdispatcherdelegat | Von der Client Anwendung implementierte Rückruf Instanz des Task Dispatchers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionProfileSettings_SetTaskDispatcherDelegate(
    const mip_cc_protection_profile_settings settings,
    const mip_cc_task_dispatcher_delegate taskDispatcherDelegate);
```

## <a name="mip_cc_protectionprofilesettings_setcustomsettings"></a>MIP_CC_ProtectionProfileSettings_SetCustomSettings

Konfiguriert benutzerdefinierte Einstellungen, die zum Gating und Testen von Features verwendet werden.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen |
| Datei "CustomSettings | Schlüssel-Wert-Paare von benutzerdefinierten Einstellungen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectionProfileSettings_SetCustomSettings(
    const mip_cc_protection_profile_settings settings,
    const mip_cc_dictionary customSettings);
```

## <a name="mip_cc_releaseprotectionprofilesettings"></a>MIP_CC_ReleaseProtectionProfileSettings

Freigeben von Ressourcen, die mit einer Schutzprofil Einstellung verknüpft sind

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Zu veröffentlichende Schutzprofil Einstellungen |

```c
void MIP_CC_ReleaseProtectionProfileSettings(mip_cc_protection_profile_settings profilsettingseSettings);
```

## <a name="mip_cc_action_gettype"></a>MIP_CC_Action_GetType

Ruft den Typ der Aktion ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Action |
| Action Type | Ausgeben Aktionstyp |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Action_GetType(
    const mip_cc_action action,
    mip_cc_action_type* actionType);
```

## <a name="mip_cc_action_getid"></a>MIP_CC_Action_GetId

Ruft die ID einer Aktion ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Action |
| id | Ausgeben Eindeutige Aktions-ID |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Action_GetId(
    const mip_cc_action action,
    mip_cc_guid* id);
```

## <a name="mip_cc_actionresult_getactions"></a>MIP_CC_ActionResult_GetActions

Aktionen zum Erstellen eines Aktions Ergebnisses

**Parameters**

Parameter | Description
|---|---|
| actionResult | Ergebnis der Quell Aktion |
| Aktionen | Ausgeben Array von Aktionen, Arbeitsspeicher im Besitz mip_cc_action_result Objekts |
| count | Ausgeben Anzahl von Schlüssel-Wert-Paaren |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: der Arbeitsspeicher für "Actions" liegt im Besitz des mip_cc_action_result Objekts und sollte daher nicht unabhängig freigegeben werden. 

```c
mip_cc_result MIP_CC_ActionResult_GetActions(
    const mip_cc_action_result actionResult,
    mip_cc_action** actions,
    int64_t* count);
```

## <a name="mip_cc_releaseactionresult"></a>MIP_CC_ReleaseActionResult

Freigeben von Ressourcen, die einem Aktions Ergebnis zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| actionResult | Aktions Ergebnis, das freigegeben werden soll |

```c
void MIP_CC_ReleaseActionResult(mip_cc_action_result actionResult);
```

## <a name="mip_cc_addcontentfooteraction_getuielementnamesize"></a>MIP_CC_AddContentFooterAction_GetUIElementNameSize

Ruft die Größe des Puffers ab, der zum Speichern des Benutzeroberflächen-Element namens für die Aktion "Content Footer" erforderlich ist

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| namesize | Ausgeben Größe des Puffers für den Namen des Benutzeroberflächen Elements (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetUIElementNameSize(
    const mip_cc_action action,
    int64_t* nameSize);
```

## <a name="mip_cc_addcontentfooteraction_getuielementname"></a>MIP_CC_AddContentFooterAction_GetUIElementName

Ruft den Benutzeroberflächen Elementnamen der Aktion "Content Footer hinzufügen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| namebuffer | Ausgeben Puffer, in den der Benutzeroberflächen Elementname kopiert wird. |
| namebuffersize | Größe (in Anzahl der Zeichen) des namebuffer. |
| actualnamesize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn namebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualnamesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetUIElementName(
    const mip_cc_action action,
    char* nameBuffer,
    const int64_t nameBufferSize,
    int64_t* actualNameSize);
```

## <a name="mip_cc_addcontentfooteraction_gettextsize"></a>MIP_CC_AddContentFooterAction_GetTextSize

Ruft die Größe des Puffers ab, der zum Speichern des Aktions Texts "Content Footer hinzufügen" erforderlich ist.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| namesize | Ausgeben Größe des Puffers zum Speichern von Text (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetTextSize(
    const mip_cc_action action,
    int64_t* textSize);
```

## <a name="mip_cc_addcontentfooteraction_gettext"></a>MIP_CC_AddContentFooterAction_GetText

Ruft den Text der Aktion "Content Footer hinzufügen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| TextBuffer | Ausgeben Puffer, in den der Text kopiert wird. |
| textbuffersize | Größe (in Anzahl der Zeichen) des textBuffer. |
| actualtextsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn TextBuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben und actualtextsize auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetText(
    const mip_cc_action action,
    char* textBuffer,
    const int64_t textBufferSize,
    int64_t* actualTextSize);
```

## <a name="mip_cc_addcontentfooteraction_getfontnamesize"></a>MIP_CC_AddContentFooterAction_GetFontNameSize

Ruft die Größe des Puffers ab, der zum Speichern des Schriftart namens der Aktion "Content Footer" hinzugefügt wird.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| namesize | Ausgeben Größe des Puffers für den Schriftart Namen (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetFontNameSize(
    const mip_cc_action action,
    int64_t* nameSize);
```

## <a name="mip_cc_addcontentfooteraction_getfontname"></a>MIP_CC_AddContentFooterAction_GetFontName

Ruft den Schriftart Namen der Aktion "Content Footer hinzufügen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| namebuffer | Ausgeben Puffer, in den der Schriftart Name kopiert wird. |
| namebuffersize | Größe (in Anzahl der Zeichen) des namebuffer. |
| actualnamesize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn namebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualnamesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetFontName(
    const mip_cc_action action,
    char* nameBuffer,
    const int64_t nameBufferSize,
    int64_t* actualNameSize);
```

## <a name="mip_cc_addcontentfooteraction_getfontsize"></a>MIP_CC_AddContentFooterAction_GetFontSize

Ruft den Schrift Grad der ganzen Zahl ab

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| FontSize | Ausgeben Schrift Grad |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetFontSize(
    const mip_cc_action action,
    int32_t* fontSize);
```

## <a name="mip_cc_addcontentfooteraction_getfontcolorsize"></a>MIP_CC_AddContentFooterAction_GetFontColorSize

Ruft die Größe des Puffers ab, der zum Speichern der Schriftfarbe der Aktion "Content Footer" hinzugefügt wird.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| colorsize | Ausgeben Größe des Puffers zum Speichern der Schriftart Farbe (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetFontColorSize(
    const mip_cc_action action,
    int64_t* colorSize);
```

## <a name="mip_cc_addcontentfooteraction_getfontcolor"></a>MIP_CC_AddContentFooterAction_GetFontColor

Ruft die Schriftfarbe für die Aktion "Inhalts Fußzeile hinzufügen" (z. b. "#000000") ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| colorbuffer | Ausgeben Puffer, in den die Schriftart Farbe kopiert wird. |
| colorbuffersize | Die Größe (in Anzahl der Zeichen) des colorbuffer. |
| actualcolorsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn colorbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualcolorsize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetFontColor(
    const mip_cc_action action,
    char* colorBuffer,
    const int64_t colorBufferSize,
    int64_t* actualColorSize);
```

## <a name="mip_cc_addcontentfooteraction_getalignment"></a>MIP_CC_AddContentFooterAction_GetAlignment

Ruft die Ausrichtung ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| Ausrichtung | Ausgeben Richt |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetAlignment(
    const mip_cc_action action,
    mip_cc_content_mark_alignment* alignment);
```

## <a name="mip_cc_addcontentfooteraction_getmargin"></a>MIP_CC_AddContentFooterAction_GetMargin

Ruft die Rand Größe ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content Footer hinzufügen" |
| marginsize | Ausgeben Rand Größe (in mm) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentFooterAction_GetMargin(
    const mip_cc_action action,
    int32_t* marginSize);
```

## <a name="mip_cc_addcontentheaderaction_getuielementnamesize"></a>MIP_CC_AddContentHeaderAction_GetUIElementNameSize

Ruft die Größe des Puffers ab, der zum Speichern des Benutzeroberflächen Element namens für die Aktion "Content Header hinzufügen"

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| namesize | Ausgeben Größe des Puffers für den Namen des Benutzeroberflächen Elements (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetUIElementNameSize(
    const mip_cc_action action,
    int64_t* nameSize);
```

## <a name="mip_cc_addcontentheaderaction_getuielementname"></a>MIP_CC_AddContentHeaderAction_GetUIElementName

Ruft den Benutzeroberflächen Elementnamen für die Aktion "Content Header hinzufügen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| namebuffer | Ausgeben Puffer, in den der Benutzeroberflächen Elementname kopiert wird. |
| namebuffersize | Größe (in Anzahl der Zeichen) des namebuffer. |
| actualnamesize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn namebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualnamesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetUIElementName(
    const mip_cc_action action,
    char* nameBuffer,
    const int64_t nameBufferSize,
    int64_t* actualNameSize);
```

## <a name="mip_cc_addcontentheaderaction_gettextsize"></a>MIP_CC_AddContentHeaderAction_GetTextSize

Ruft die Größe des Puffers ab, der zum Speichern eines Aktions Texts für "Inhalts Header hinzufügen" erforderlich ist

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| namesize | Ausgeben Größe des Puffers zum Speichern von Text (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetTextSize(
    const mip_cc_action action,
    int64_t* textSize);
```

## <a name="mip_cc_addcontentheaderaction_gettext"></a>MIP_CC_AddContentHeaderAction_GetText

Ruft den Text der Aktion "Content Header hinzufügen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| TextBuffer | Ausgeben Puffer, in den der Text kopiert wird. |
| textbuffersize | Größe (in Anzahl der Zeichen) des textBuffer. |
| actualtextsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn TextBuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben und actualtextsize auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetText(
    const mip_cc_action action,
    char* textBuffer,
    const int64_t textBufferSize,
    int64_t* actualTextSize);
```

## <a name="mip_cc_addcontentheaderaction_getfontnamesize"></a>MIP_CC_AddContentHeaderAction_GetFontNameSize

Ruft die Größe des Puffers ab, der zum Speichern des Schriftart namens der Aktion "Inhalts Header hinzufügen" erforderlich ist

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| namesize | Ausgeben Größe des Puffers für den Schriftart Namen (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetFontNameSize(
    const mip_cc_action action,
    int64_t* nameSize);
```

## <a name="mip_cc_addcontentheaderaction_getfontname"></a>MIP_CC_AddContentHeaderAction_GetFontName

Ruft den Schriftart Namen der Aktion "Content-Header hinzufügen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| namebuffer | Ausgeben Puffer, in den der Schriftart Name kopiert wird. |
| namebuffersize | Größe (in Anzahl der Zeichen) des namebuffer. |
| actualnamesize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn namebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualnamesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetFontName(
    const mip_cc_action action,
    char* nameBuffer,
    const int64_t nameBufferSize,
    int64_t* actualNameSize);
```

## <a name="mip_cc_addcontentheaderaction_getfontsize"></a>MIP_CC_AddContentHeaderAction_GetFontSize

Ruft den Schrift Grad der ganzen Zahl ab

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| FontSize | Ausgeben Schrift Grad |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetFontSize(
    const mip_cc_action action,
    int32_t* fontSize);
```

## <a name="mip_cc_addcontentheaderaction_getfontcolorsize"></a>MIP_CC_AddContentHeaderAction_GetFontColorSize

Ruft die Größe des Puffers ab, der zum Speichern der Schriftfarbe der Aktion "Inhalts Header hinzufügen" erforderlich ist

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| colorsize | Ausgeben Größe des Puffers zum Speichern der Schriftart Farbe (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetFontColorSize(
    const mip_cc_action action,
    int64_t* colorSize);
```

## <a name="mip_cc_addcontentheaderaction_getfontcolor"></a>MIP_CC_AddContentHeaderAction_GetFontColor

Ruft die Schriftfarbe für die Aktion "Content-Header hinzufügen" (z. b. "#000000") ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| colorbuffer | Ausgeben Puffer, in den die Schriftart Farbe kopiert wird. |
| colorbuffersize | Die Größe (in Anzahl der Zeichen) des colorbuffer. |
| actualcolorsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn colorbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualcolorsize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetFontColor(
    const mip_cc_action action,
    char* colorBuffer,
    const int64_t colorBufferSize,
    int64_t* actualColorSize);
```

## <a name="mip_cc_addcontentheaderaction_getalignment"></a>MIP_CC_AddContentHeaderAction_GetAlignment

Ruft die Ausrichtung ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| Ausrichtung | Ausgeben Richt |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetAlignment(
    const mip_cc_action action,
    mip_cc_content_mark_alignment* alignment);
```

## <a name="mip_cc_addcontentheaderaction_getmargin"></a>MIP_CC_AddContentHeaderAction_GetMargin

Ruft die Rand Größe ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Content-Header hinzufügen" |
| marginsize | Ausgeben Rand Größe (in mm) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddContentHeaderAction_GetMargin(
    const mip_cc_action action,
    int32_t* marginSize);
```

## <a name="mip_cc_addwatermarkaction_getuielementnamesize"></a>MIP_CC_AddWatermarkAction_GetUIElementNameSize

Ruft die Größe des Puffers ab, der zum Speichern des Benutzeroberflächen Element namens der Aktion "Wasserzeichen hinzufügen" erforderlich

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen hinzufügen" |
| namesize | Ausgeben Größe des Puffers für den Namen des Benutzeroberflächen Elements (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddWatermarkAction_GetUIElementNameSize(
    const mip_cc_action action,
    int64_t* nameSize);
```

## <a name="mip_cc_addwatermarkaction_getuielementname"></a>MIP_CC_AddWatermarkAction_GetUIElementName

Ruft den Benutzeroberflächen Elementnamen der Aktion "Wasserzeichen hinzufügen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen hinzufügen" |
| namebuffer | Ausgeben Puffer, in den der Benutzeroberflächen Elementname kopiert wird. |
| namebuffersize | Größe (in Anzahl der Zeichen) des namebuffer. |
| actualnamesize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn namebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualnamesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddWatermarkAction_GetUIElementName(
    const mip_cc_action action,
    char* nameBuffer,
    const int64_t nameBufferSize,
    int64_t* actualNameSize);
```

## <a name="mip_cc_addwatermarkaction_getlayout"></a>MIP_CC_AddWatermarkAction_GetLayout

Ruft das Wasserzeichen Layout ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen hinzufügen" |
| layout | Ausgeben Wasserzeichen Layout |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddWatermarkAction_GetLayout(
    const mip_cc_action action,
    mip_cc_watermark_layout* layout);
```

## <a name="mip_cc_addwatermarkaction_gettextsize"></a>MIP_CC_AddWatermarkAction_GetTextSize

Ruft die Größe des Puffers ab, der zum Speichern des Texts der Aktion "Wasserzeichen hinzufügen" erforderlich ist

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen hinzufügen" |
| namesize | Ausgeben Größe des Puffers zum Speichern von Text (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddWatermarkAction_GetTextSize(
    const mip_cc_action action,
    int64_t* textSize);
```

## <a name="mip_cc_addwatermarkaction_gettext"></a>MIP_CC_AddWatermarkAction_GetText

Ruft den Text der Aktion "Wasserzeichen hinzufügen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen hinzufügen" |
| TextBuffer | Ausgeben Puffer, in den der Text kopiert wird. |
| textbuffersize | Größe (in Anzahl der Zeichen) des textBuffer. |
| actualtextsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn TextBuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben und actualtextsize auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddWatermarkAction_GetText(
    const mip_cc_action action,
    char* textBuffer,
    const int64_t textBufferSize,
    int64_t* actualTextSize);
```

## <a name="mip_cc_addwatermarkaction_getfontnamesize"></a>MIP_CC_AddWatermarkAction_GetFontNameSize

Ruft die Größe des Puffers ab, der zum Speichern des Schriftart namens "Wasserzeichen hinzufügen" erforderlich ist.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen hinzufügen" |
| namesize | Ausgeben Größe des Puffers für den Schriftart Namen (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddWatermarkAction_GetFontNameSize(
    const mip_cc_action action,
    int64_t* nameSize);
```

## <a name="mip_cc_addwatermarkaction_getfontname"></a>MIP_CC_AddWatermarkAction_GetFontName

Ruft den Schriftart Namen der Aktion "Wasserzeichen hinzufügen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen hinzufügen" |
| namebuffer | Ausgeben Puffer, in den der Schriftart Name kopiert wird. |
| namebuffersize | Größe (in Anzahl der Zeichen) des namebuffer. |
| actualnamesize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn namebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualnamesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddWatermarkAction_GetFontName(
    const mip_cc_action action,
    char* nameBuffer,
    const int64_t nameBufferSize,
    int64_t* actualNameSize);
```

## <a name="mip_cc_addwatermarkaction_getfontsize"></a>MIP_CC_AddWatermarkAction_GetFontSize

Ruft den Schrift Grad der ganzen Zahl ab

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen hinzufügen" |
| FontSize | Ausgeben Schrift Grad |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddWatermarkAction_GetFontSize(
    const mip_cc_action action,
    int32_t* fontSize);
```

## <a name="mip_cc_addwatermarkaction_getfontcolorsize"></a>MIP_CC_AddWatermarkAction_GetFontColorSize

Ruft die Größe des Puffers ab, der zum Speichern der Schriftart Farbe für "Wasserzeichen hinzufügen" erforderlich ist.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen hinzufügen" |
| colorsize | Ausgeben Größe des Puffers zum Speichern der Schriftart Farbe (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_AddWatermarkAction_GetFontColorSize(
    const mip_cc_action action,
    int64_t* colorSize);
```

## <a name="mip_cc_addwatermarkaction_getfontcolor"></a>MIP_CC_AddWatermarkAction_GetFontColor

Ruft die Schriftfarbe der Aktion "Wasserzeichen hinzufügen" (z. b. "#000000") ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen hinzufügen" |
| colorbuffer | Ausgeben Puffer, in den die Schriftart Farbe kopiert wird. |
| colorbuffersize | Die Größe (in Anzahl der Zeichen) des colorbuffer. |
| actualcolorsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn colorbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualcolorsize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_AddWatermarkAction_GetFontColor(
    const mip_cc_action action,
    char* colorBuffer,
    const int64_t colorBufferSize,
    int64_t* actualColorSize);
```

## <a name="mip_cc_releasecontentlabel"></a>MIP_CC_ReleaseContentLabel

Freigeben von Ressourcen, die einer Inhalts Bezeichnung zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| contentLabel | Zu veröffentlichende Bezeichnung |

```c
void MIP_CC_ReleaseContentLabel(mip_cc_content_label contentLabel);
```

## <a name="mip_cc_contentlabel_getcreationtime"></a>MIP_CC_ContentLabel_GetCreationTime

Ruft die Zeit ab, zu der Bezeichnung angewendet wurde

**Parameters**

Parameter | Description
|---|---|
| contentLabel | Label |
| creationTime | Ausgeben Uhrzeit, zu der die Bezeichnung auf das Dokument angewendet wurde (in Sekunden seit der Epoche) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ContentLabel_GetCreationTime(
    const mip_cc_content_label contentLabel,
    int64_t* creationTime);
```

## <a name="mip_cc_contentlabel_getassignmentmethod"></a>MIP_CC_ContentLabel_GetAssignmentMethod

Ruft die Bezeichnung für die Bezeichnung ab

**Parameters**

Parameter | Description
|---|---|
| contentLabel | Label |
| zutragmethode | Ausgeben Zuweisungs Methode (z. b. "Standard" oder "privilegiert") |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ContentLabel_GetAssignmentMethod(
    const mip_cc_content_label contentLabel,
    mip_cc_label_assignment_method* assignmentMethod);
```

## <a name="mip_cc_contentlabel_getextendedproperties"></a>MIP_CC_ContentLabel_GetExtendedProperties

Ruft erweiterte Eigenschaften ab.

**Parameters**

Parameter | Description
|---|---|
| contentLabel | Label |
| Eigenschaften | Ausgeben Wörterbuch erweiterter Eigenschaften, Arbeitsspeicher im Besitz des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die "Properties"-Variable muss vom Aufrufer freigegeben werden, indem aufgerufen wird MIP_CC_ReleaseDictionary 

```c
mip_cc_result MIP_CC_ContentLabel_GetExtendedProperties(
    const mip_cc_content_label contentLabel,
    mip_cc_dictionary* properties);
```

## <a name="mip_cc_contentlabel_isprotectionappliedfromlabel"></a>MIP_CC_ContentLabel_IsProtectionAppliedFromLabel

Ruft ab, ob ein Schutz durch eine Bezeichnung angewendet wurde.

**Parameters**

Parameter | Description
|---|---|
| contentLabel | Label |
| isprotectionappliedbylabel | Ausgeben , Wenn das Dokument geschützt ist und der Schutz explizit durch diese Bezeichnung angewendet wurde. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ContentLabel_IsProtectionAppliedFromLabel(
    const mip_cc_content_label contentLabel,
    bool* isProtectionAppliedByLabel);
```

## <a name="mip_cc_contentlabel_getlabel"></a>MIP_CC_ContentLabel_GetLabel

Ruft generische Bezeichnungs Eigenschaften aus einer Instanz der Inhalts Bezeichnung ab.

**Parameters**

Parameter | Description
|---|---|
| contentLabel | Label |
| label | Ausgeben Generische Bezeichnung, Arbeitsspeicher im Besitz des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die "Label"-Variable muss vom Aufrufer durch Aufrufen von freigegeben werden MIP_CC_ReleaseLabel 

```c
mip_cc_result MIP_CC_ContentLabel_GetLabel(
    const mip_cc_content_label contentLabel,
    mip_cc_label* label);
```

## <a name="mip_cc_customaction_getnamesize"></a>MIP_CC_CustomAction_GetNameSize

Ruft die Größe des Puffers ab, der zum Speichern des Namens einer benutzerdefinierten Aktion erforderlich ist.

**Parameters**

Parameter | Description
|---|---|
| Aktion | benutzerdefinierte Aktion |
| namesize | Ausgeben Größe des zu haltenen Puffers (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_CustomAction_GetNameSize(
    const mip_cc_action action,
    int64_t* nameSize);
```

## <a name="mip_cc_customaction_getname"></a>MIP_CC_CustomAction_GetName

Ruft den Namen der benutzerdefinierten Aktion ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | benutzerdefinierte Aktion |
| namebuffer | Ausgeben Puffer, in den der Name kopiert wird. |
| namebuffersize | Größe (in Anzahl der Zeichen) des namebuffer. |
| actualnamesize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn namebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualnamesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_CustomAction_GetName(
    const mip_cc_action action,
    char* nameBuffer,
    const int64_t nameBufferSize,
    int64_t* actualNameSize);
```

## <a name="mip_cc_customaction_getproperties"></a>MIP_CC_CustomAction_GetProperties

Ruft die Eigenschaften der benutzerdefinierten Aktion ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | benutzerdefinierte Aktion |
| Eigenschaften | Ausgeben Wörterbuch mit Eigenschaften, Speicher im Besitz des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die "Properties"-Variable muss vom Aufrufer freigegeben werden, indem aufgerufen wird MIP_CC_ReleaseDictionary 

```c
mip_cc_result MIP_CC_CustomAction_GetProperties(
    const mip_cc_action action,
    mip_cc_dictionary* properties);
```

## <a name="mip_cc_metadata_callback"></a>mip_cc_metadata_callback

Rückruf Funktionsdefinition zum Abrufen von Dokument Metatdaten, gefiltert nach Name/Präfix

**Parameters**

Parameter | Description
|---|---|
| -Namen | Array von metadatenschlüsselnamen, die im Ergebnis enthalten sein sollen |
| namessize | Anzahl von Werten im Array "Names" |
| nameprefixes | Array von Metadaten-Schlüsselnamen Präfixen, die im Ergebnis enthalten sein sollen |
| nameprefixessize | Anzahl von Werten im Array "namesprefixes" |
| context | Der Anwendungskontext wurde vom API-Rückruf an den Rückruf übermittelt. |
| Metadaten | Ausgeben Wörterbuch mit metadatenschlüsseln/-Werten, die von der Client Anwendung erstellt wurden. Dieses Wörterbuch wird von MIP freigegeben. |

```c
MIP_CC_CALLBACK(mip_cc_metadata_callback,
    void,
    const char**,
    const int64_t,
    const char**,
    const int64_t,
    const void*,
    mip_cc_dictionary*);
```

## <a name="mip_cc_releaselabel"></a>MIP_CC_ReleaseLabel

Freigeben von Ressourcen, die einer Bezeichnung zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| label | Zu veröffentlichende Bezeichnung |

```c
void MIP_CC_ReleaseLabel(mip_cc_label label);
```

## <a name="mip_cc_label_getid"></a>MIP_CC_Label_GetId

Bezeichnungs-ID abrufen

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| LabelId | Ausgeben Bezeichnungs-ID |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Label_GetId(
    const mip_cc_label label,
    mip_cc_guid* labelId);
```

## <a name="mip_cc_label_getnamesize"></a>MIP_CC_Label_GetNameSize

Ruft die Größe des zum Speichern des Namens erforderlichen Puffers ab

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| namesize | Ausgeben Größe des zu haltenen Puffers (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Label_GetNameSize(
    const mip_cc_label label,
    int64_t* nameSize);
```

## <a name="mip_cc_label_getname"></a>MIP_CC_Label_GetName

Ruft den Bezeichnung

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| namebuffer | Ausgeben Puffer, in den der Name kopiert wird. |
| namebuffersize | Größe (in Anzahl der Zeichen) des namebuffer. |
| actualnamesize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn namebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualnamesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_Label_GetName(
    const mip_cc_label label,
    char* nameBuffer,
    const int64_t nameBufferSize,
    int64_t* actualNameSize);
```

## <a name="mip_cc_label_getdescriptionsize"></a>MIP_CC_Label_GetDescriptionSize

Ruft die Größe des Puffers zum Speichern der Beschreibung ab.

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| deskriptionsize | Ausgeben Größe des Puffers zum Speichern der Beschreibung (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Label_GetDescriptionSize(
    const mip_cc_label label,
    int64_t* descriptionSize);
```

## <a name="mip_cc_label_getdescription"></a>MIP_CC_Label_GetDescription

Beschreibung der Bezeichnung wird abgerufen

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| deskriptionbuffer | Ausgeben Puffer, in den die Beschreibung kopiert wird. |
| deskriptionbuffersize | Die Größe (in Anzahl der Zeichen) des deskriptionbuffer. |
| actualdescriptionsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn descriptionbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben und actualdescriptionsize auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_Label_GetDescription(
    const mip_cc_label label,
    char* descriptionBuffer,
    const int64_t descriptionBufferSize,
    int64_t* actualDescriptionSize);
```

## <a name="mip_cc_label_getcolorsize"></a>MIP_CC_Label_GetColorSize

Ruft die Größe des Puffers zum Speichern der Farbe ab.

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| colorsize | Ausgeben Größe des Puffers für die Farbe (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Label_GetColorSize(
    const mip_cc_label label,
    int64_t* colorSize);
```

## <a name="mip_cc_label_getcolor"></a>MIP_CC_Label_GetColor

Ruft die Bezeichnung ab.

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| colorbuffer | Ausgeben Puffer, in den die Farbe kopiert wird (in #RRGGBB Format). |
| colorbuffersize | Die Größe (in Anzahl der Zeichen) des colorbuffer. |
| actualcolorsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn colorbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualcolorsize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_Label_GetColor(
    const mip_cc_label label,
    char* colorBuffer,
    const int64_t colorBufferSize,
    int64_t* actualColorSize);
```

## <a name="mip_cc_label_getsensitivity"></a>MIP_CC_Label_GetSensitivity

Ruft die Vertraulichkeits Stufe der Bezeichnung ab. Ein höherer Wert bedeutet mehr sensitiv.

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| sensitivity | Ausgeben Empfindlichkeitsstufe |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Label_GetSensitivity(
    const mip_cc_label label,
    int32_t* sensitivity);
```

## <a name="mip_cc_label_gettooltipsize"></a>MIP_CC_Label_GetTooltipSize

Ruft die Größe des Puffers zum Speichern der QuickInfo ab

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| ToolTipSize | Ausgeben Größe des Puffers zum Speichern der QuickInfo (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Label_GetTooltipSize(
    const mip_cc_label label,
    int64_t* tooltipSize);
```

## <a name="mip_cc_label_gettooltip"></a>MIP_CC_Label_GetTooltip

QuickInfo für Bezeichnung abrufen

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| tooltipbuffer | Ausgeben Puffer, in den die QuickInfo kopiert wird. |
| tooltipbuffersize | Größe (in Anzahl der Zeichen) des tooltipbuffer. |
| actualtooltipsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn tooltipbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben und actualtooltipsize auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_Label_GetTooltip(
    const mip_cc_label label,
    char* tooltipBuffer,
    const int64_t tooltipBufferSize,
    int64_t* actualTooltipSize);
```

## <a name="mip_cc_label_getautotooltipsize"></a>MIP_CC_Label_GetAutoTooltipSize

Ruft die Größe des Puffers zum Speichern der QuickInfo für die automatische Klassifizierung ab

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| ToolTipSize | Ausgeben Größe des Puffers zum Speichern der QuickInfo (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Label_GetAutoTooltipSize(
    const mip_cc_label label,
    int64_t* tooltipSize);
```

## <a name="mip_cc_label_getautotooltip"></a>MIP_CC_Label_GetAutoTooltip

Ruft die Bezeichnung für die automatische Klassifizierung der Bezeichnung ab

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| tooltipbuffer | Ausgeben Puffer, in den die QuickInfo kopiert wird. |
| tooltipbuffersize | Größe (in Anzahl der Zeichen) des tooltipbuffer. |
| actualtooltipsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn tooltipbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben und actualtooltipsize auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_Label_GetAutoTooltip(
    const mip_cc_label label,
    char* tooltipBuffer,
    const int64_t tooltipBufferSize,
    int64_t* actualTooltipSize);
```

## <a name="mip_cc_label_isactive"></a>MIP_CC_Label_IsActive

Ruft ab, ob eine Bezeichnung aktiv ist.

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| IsActive | Ausgeben Gibt an, ob eine Bezeichnung als aktiv betrachtet wird. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Es können nur aktive Bezeichnungen angewendet werden. Inactivte-Bezeichnungen können nicht angewendet werden und werden nur zu Anzeige Zwecken verwendet. 

```c
mip_cc_result MIP_CC_Label_IsActive(
    const mip_cc_label label,
    bool* isActive);
```

## <a name="mip_cc_label_getparent"></a>MIP_CC_Label_GetParent

Ruft die übergeordnete Bezeichnung ab, sofern vorhanden.

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| parent (parent) | Ausgeben Übergeordnete Bezeichnung, falls vorhanden, andernfalls NULL |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Label_GetParent(
    const mip_cc_label label,
    mip_cc_label* parent);
```

## <a name="mip_cc_label_getchildrensize"></a>MIP_CC_Label_GetChildrenSize

Ruft die Anzahl der untergeordneten Bezeichnungen ab.

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| Kindergröße | Ausgeben Anzahl der untergeordneten Elemente |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_Label_GetChildrenSize(
    const mip_cc_label label,
    int64_t* childrenSize);
```

## <a name="mip_cc_label_getchildren"></a>MIP_CC_Label_GetChildren

Ruft die untergeordneten Bezeichnungen ab.

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| Children-Buffer | Ausgeben Puffer, in den die untergeordneten Bezeichnungen kopiert werden. Untergeordnete Bezeichnungen |
| Children-bufferSize | Größe (in Anzahl der Bezeichnungen) des Children-Buffer. |
| actualchildren ensize | Ausgeben Anzahl der in den Puffer geschriebenen untergeordneten Bezeichnungen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn "Kinder Puffer" NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und "actualchildren ensize" wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_Label_GetChildren(
    const mip_cc_label label,
    mip_cc_label* childrenBuffer,
    const int64_t childrenBufferSize,
    int64_t* actualChildrenSize);
```

## <a name="mip_cc_label_getcustomsettings"></a>MIP_CC_Label_GetCustomSettings

Ruft Richtlinien definierte benutzerdefinierte Einstellungen einer Bezeichnung ab.

**Parameters**

Parameter | Description
|---|---|
| label | Label |
| Einstellungen | Ausgeben Wörterbuch mit Einstellungen im Besitz des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die "Settings"-Variable muss vom Aufrufer freigegeben werden, indem aufgerufen wird MIP_CC_ReleaseDictionary 

```c
mip_cc_result MIP_CC_Label_GetCustomSettings(
    const mip_cc_label label,
    mip_cc_dictionary* settings);
```

## <a name="mip_cc_metadataaction_getmetadatatoremove"></a>MIP_CC_MetadataAction_GetMetadataToRemove

Ruft die zu entfern aus den Metadaten der metadatenaktion ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Metadata" |
| metadataNames | Ausgeben Schlüsselnamen der zu entfernenden Metadaten, Speicher im Besitz des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die Variable "metadataNames" muss vom Aufrufer freigegeben werden, indem aufgerufen wird, MIP_CC_ReleaseStringList @note Entfernen von Metadaten vor dem Hinzufügen von Metadaten erfolgen soll. 

```c
mip_cc_result MIP_CC_MetadataAction_GetMetadataToRemove(
    const mip_cc_action action,
    mip_cc_string_list* metadataNames);
```

## <a name="mip_cc_metadataaction_getmetadatatoadd"></a>MIP_CC_MetadataAction_GetMetadataToAdd

Ruft die hinzu zufügenden Metadaten der metadatenaktion ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Metadata" |
| Metadaten | Ausgeben Schlüssel-Wert-Paare von Metadaten, die hinzugefügt werden sollen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die Variablen "Metadata" muss vom Aufrufer freigegeben werden, indem aufgerufen wird, MIP_CC_ReleaseDictionary @note Entfernen von Metadaten vor dem Hinzufügen von Metadaten erfolgen soll. 

```c
mip_cc_result MIP_CC_MetadataAction_GetMetadataToAdd(
    const mip_cc_action action,
    mip_cc_dictionary* metadata);
```

## <a name="mip_cc_releasepolicyengine"></a>MIP_CC_ReleasePolicyEngine

Freigeben von Ressourcen, die einer Richtlinie-Engine zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Engine | Zu veröffentlichendem Richtlinien Modul |

```c
void MIP_CC_ReleasePolicyEngine(mip_cc_policy_engine engine);
```

## <a name="mip_cc_policyengine_getengineidsize"></a>MIP_CC_PolicyEngine_GetEngineIdSize

Ruft die Größe des für Engine-ID erforderlichen Puffers ab

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| idsize | Ausgeben Größe des Puffers für die Engine-ID (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetEngineIdSize(
    const mip_cc_policy_engine engine,
    int64_t* idSize);
```

## <a name="mip_cc_policyengine_getengineid"></a>MIP_CC_PolicyEngine_GetEngineId

Ruft Engine-ID ab

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| idbuffer | Ausgeben Puffer, in den die ID kopiert wird. |
| idbuffersize | Größe (in Anzahl der Zeichen) des idbuffer. |
| actualidsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn idbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualidsize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_PolicyEngine_GetEngineId(
    const mip_cc_policy_engine engine,
    char* idBuffer,
    const int64_t idBufferSize,
    int64_t* actualIdSize);
```

## <a name="mip_cc_policyengine_getmoreinfourlsize"></a>MIP_CC_PolicyEngine_GetMoreInfoUrlSize

Ruft die Größe der der Richtlinien-Engine zugeordneten Client Daten ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| moreinfourlsize | Ausgeben Größe der Client Daten (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetMoreInfoUrlSize(
    const mip_cc_policy_engine engine,
    int64_t* moreInfoUrlSize);
```

## <a name="mip_cc_policyengine_getmoreinfourl"></a>MIP_CC_PolicyEngine_GetMoreInfoUrl

Client Daten mit einer Richtlinien-Engine

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| morumfourlbuffer | Ausgeben Puffer, in den die Client Daten kopiert werden |
| moreinfourlbuffersize | Größe (in Anzahl von Zeichen) von moreinfourlbuffer. |
| actualmoreinfourlsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn moreinfourlbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualmoreinfourlsize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_PolicyEngine_GetMoreInfoUrl(
    const mip_cc_policy_engine engine,
    char* moreInfoUrlBuffer,
    const int64_t moreInfoUrlBufferSize,
    int64_t* actualMoreInfoUrlSize);
```

## <a name="mip_cc_policyengine_islabelingrequired"></a>MIP_CC_PolicyEngine_IsLabelingRequired

Ruft ab, ob die Richtlinie festlegt, dass ein Dokument mit einer Bezeichnung versehen werden muss.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| islabelingrequired | Ausgeben Ob die Richtlinie festlegt, dass ein Dokument mit einer Bezeichnung versehen werden muss |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_IsLabelingRequired(
    const mip_cc_policy_engine engine,
    bool* isLabelingRequired);
```

## <a name="mip_cc_policyengine_getpolicyfileidsize"></a>MIP_CC_PolicyEngine_GetPolicyFileIdSize

Ruft die Größe der der Richtlinien-Engine zugeordneten Client Daten ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| policymeleidsize | Ausgeben Größe der Client Daten (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetPolicyFileIdSize(
    const mip_cc_policy_engine engine,
    int64_t* policyFileIdSize);
```

## <a name="mip_cc_policyengine_getpolicyfileid"></a>MIP_CC_PolicyEngine_GetPolicyFileId

Client Daten mit einer Richtlinien-Engine

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| policyfleidbuffer | Ausgeben Puffer, in den die Client Daten kopiert werden |
| policyfleidbuffersize | Größe (in Anzahl von Zeichen) von policyfleidbuffer. |
| actualpolicyfleidsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn policyfleidbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualpolicyfleidsize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_PolicyEngine_GetPolicyFileId(
    const mip_cc_policy_engine engine,
    char* policyFileIdBuffer,
    const int64_t policyFileIdBufferSize,
    int64_t* actualPolicyFileIdSize);
```

## <a name="mip_cc_policyengine_getsensitivityfileidsize"></a>MIP_CC_PolicyEngine_GetSensitivityFileIdSize

Ruft die Größe der der Richtlinien-Engine zugeordneten Client Daten ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| sensitivityfleidsize | Ausgeben Größe der Client Daten (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetSensitivityFileIdSize(
    const mip_cc_policy_engine engine,
    int64_t* sensitivityFileIdSize);
```

## <a name="mip_cc_policyengine_getsensitivityfileid"></a>MIP_CC_PolicyEngine_GetSensitivityFileId

Client Daten mit einer Richtlinien-Engine

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| sensitivityfleid-Puffer | Ausgeben Puffer, in den die Client Daten kopiert werden |
| sensitivityfleidbuffersize | Größe (in Anzahl von Zeichen) von sensitivityfleidbuffer. |
| actualsensitivityfleidsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn sensitivityfleid buffer null oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualsensitivityfleidsize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_PolicyEngine_GetSensitivityFileId(
    const mip_cc_policy_engine engine,
    char* sensitivityFileIdBuffer,
    const int64_t sensitivityFileIdBufferSize,
    int64_t* actualSensitivityFileIdSize);
```

## <a name="mip_cc_policyengine_hasclassificationrules"></a>MIP_CC_PolicyEngine_HasClassificationRules

Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| hasclassificationrules | Ausgeben Gibt an, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_HasClassificationRules(
    const mip_cc_policy_engine engine,
    bool* hasClassificationRules);
```

## <a name="mip_cc_policyengine_getlastpolicyfetchtime"></a>MIP_CC_PolicyEngine_GetLastPolicyFetchTime

Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| lastpolicyfetchtime | Ausgeben Uhrzeit, zu der die Richtlinie zuletzt abgerufen wurde (in Sekunden seit der Epoche) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetLastPolicyFetchTime(
    const mip_cc_policy_engine engine,
    int64_t* lastPolicyFetchTime);
```

## <a name="mip_cc_policyengine_getsensitivitylabelssize"></a>MIP_CC_PolicyEngine_GetSensitivityLabelsSize

Ruft die Anzahl der der Richtlinien-Engine zugeordneten Vertraulichkeits Bezeichnungen ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| labelssize | Ausgeben Anzahl von Bezeichnungen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetSensitivityLabelsSize(
    const mip_cc_policy_engine engine,
    int64_t* labelsSize);
```

## <a name="mip_cc_policyengine_getsensitivitylabels"></a>MIP_CC_PolicyEngine_GetSensitivityLabels

Ruft die der Richtlinien-Engine zugeordneten Vertraulichkeits Bezeichnungen ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| labelbuffer | Ausgeben Puffer, in den die Bezeichnungen kopiert werden. Bezeichnungen befinden sich im Besitz des Clients |
| LabelBufferSize | Größe (in Anzahl der Bezeichnungen) des labelbuffer. |
| actuallabelssize | Ausgeben Anzahl der Bezeichnungen, die in den Puffer geschrieben werden |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn labelbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actuallabelssize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_PolicyEngine_GetSensitivityLabels(
    const mip_cc_policy_engine engine,
    mip_cc_label* labelBuffer,
    const int64_t labelBufferSize,
    int64_t* actualLabelsSize);
```

## <a name="mip_cc_policyengine_getlabelbyid"></a>MIP_CC_PolicyEngine_GetLabelById

Ruft die Vertraulichkeits Bezeichnung nach ID ab

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| LabelId | Bezeichnungs-ID |
| label | Ausgeben Vertraulichkeits Bezeichnung. Dieser Wert befindet sich im Besitz des Aufrufers und muss mit MIP_CC_ReleaseLabel freigegeben werden. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetLabelById(
    const mip_cc_policy_engine engine,
    const char* labelId,
    mip_cc_label* label);
```

## <a name="mip_cc_policyengine_getsensitivitytypessize"></a>MIP_CC_PolicyEngine_GetSensitivityTypesSize

Ruft die Anzahl der Empfindlichkeits Typen ab, die der Richtlinien-Engine zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| sensitivitytypessize | Ausgeben Anzahl der Empfindlichkeits Typen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetSensitivityTypesSize(
    const mip_cc_policy_engine engine,
    int64_t* sensitivityTypesSize);
```

## <a name="mip_cc_policyengine_getsensitivitytypes"></a>MIP_CC_PolicyEngine_GetSensitivityTypes

Ruft die der Richtlinien-Engine zugeordneten Empfindlichkeits Typen ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| sensitivitytypebuffer | Ausgeben Puffer, in den die Empfindlichkeits Typen kopiert werden. Sensitivität |
| sensitivitytypebuffersize | Größe (in Anzahl der Empfindlichkeits Typen) von sensitivitytypebuffer. |
| actualsensitivitytypessize | Ausgeben Anzahl der in den Puffer geschriebenen Vertraulichkeits Typen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn sensitivitytypebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualsensitivitytypessize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_PolicyEngine_GetSensitivityTypes(
    const mip_cc_policy_engine engine,
    mip_cc_sensitivity_type* sensitivityTypeBuffer,
    const int64_t sensitivityTypeBufferSize,
    int64_t* actualSensitivityTypesSize);
```

## <a name="mip_cc_policyengine_createpolicyhandler"></a>MIP_CC_PolicyEngine_CreatePolicyHandler

Erstellen eines Richtlinien Handlers zum Ausführen von Richtlinien bezogenen Funktionen

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| isauditdiscoveryaktivierte | Gibt an, ob die Überwachungs Ermittlung aktiviert ist. |
| Handler | Ausgeben Neu erstellte richtlinienhandlerinstanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_CreatePolicyHandler(
    const mip_cc_policy_engine engine,
    const bool isAuditDiscoveryEnabled,
    mip_cc_policy_handler* handler);
```

## <a name="mip_cc_policyengine_sendapplicationauditevent"></a>MIP_CC_PolicyEngine_SendApplicationAuditEvent

Protokolliert ein anwendungsspezifisches Ereignis in der Überwachungs Pipeline.

**Parameters**

Parameter | Description
|---|---|
| level | Ereignis Ebene: info/Fehler/Warnung |
| eventType | Eine Beschreibung des Ereignis Typs. |
| eventData | Die Daten, die dem Ereignis zugeordnet sind. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_SendApplicationAuditEvent(
    const mip_cc_policy_engine engine,
    const char* level,
    const char* eventType,
    const char* eventData);
```

## <a name="mip_cc_policyengine_getpolicydataxmlsize"></a>MIP_CC_PolicyEngine_GetPolicyDataXmlSize

Ruft die Größe der Richtlinien Daten-XML ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| xmlsize | Ausgeben Größe von Richtlinien Daten-XML (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetPolicyDataXmlSize(
    const mip_cc_policy_engine engine,
    int64_t* xmlSize);
```

## <a name="mip_cc_policyengine_getpolicydataxml"></a>MIP_CC_PolicyEngine_GetPolicyDataXml

Ruft Richtlinien Daten-XML ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| xmlbuffer | Ausgeben Der Puffer, in den das XML kopiert wird. |
| xmlbuffersize | Größe (in Anzahl der Zeichen) des xmlbuffer. |
| actualxmlsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn xmlbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben und actualxmlsize auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_PolicyEngine_GetPolicyDataXml(
    const mip_cc_policy_engine engine,
    char* xmlBuffer,
    const int64_t xmlBufferSize,
    int64_t* actualXmlSize);
```

## <a name="mip_cc_policyengine_getsensitivitytypesdataxmlsize"></a>MIP_CC_PolicyEngine_GetSensitivityTypesDataXmlSize

Ruft die Größe der Vertraulichkeits Typen Daten-XML ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| xmlsize | Ausgeben Größe von Richtlinien Daten-XML (als Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetSensitivityTypesDataXmlSize(
    const mip_cc_policy_engine engine,
    int64_t* xmlSize);
```

## <a name="mip_cc_policyengine_getsensitivitytypesdataxml"></a>MIP_CC_PolicyEngine_GetSensitivityTypesDataXml

Ruft Daten der Vertraulichkeits Typen ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| xmlbuffer | Ausgeben Der Puffer, in den das XML kopiert wird. |
| xmlbuffersize | Größe (in Anzahl der Zeichen) des xmlbuffer. |
| actualxmlsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn xmlbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben und actualxmlsize auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_PolicyEngine_GetSensitivityTypesDataXml(
    const mip_cc_policy_engine engine,
    char* xmlBuffer,
    const int64_t xmlBufferSize,
    int64_t* actualXmlSize);
```

## <a name="mip_cc_policyengine_getclientdatasize"></a>MIP_CC_PolicyEngine_GetClientDataSize

Ruft die Größe der der Richtlinien-Engine zugeordneten Client Daten ab.

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| clientdatasize | Ausgeben Größe der Client Daten (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngine_GetClientDataSize(
    const mip_cc_policy_engine engine,
    int64_t* clientDataSize);
```

## <a name="mip_cc_policyengine_getclientdata"></a>MIP_CC_PolicyEngine_GetClientData

Client Daten mit einer Richtlinien-Engine

**Parameters**

Parameter | Description
|---|---|
| Engine | Richtlinien-Engine |
| clientdatabuffer | Ausgeben Puffer, in den die Client Daten kopiert werden |
| clientdatabuffersize | Größe (in Anzahl von Zeichen) von clientdatabuffer. |
| actualclientdatasize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn clientdatabuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualclientdatasize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_PolicyEngine_GetClientData(
    const mip_cc_policy_engine engine,
    char* clientDataBuffer,
    const int64_t clientDataBufferSize,
    int64_t* actualClientDataSize);
```

## <a name="mip_cc_createpolicyenginesettingswithidentity"></a>MIP_CC_CreatePolicyEngineSettingsWithIdentity

Erstellen eines Einstellungs Objekts, das zum Erstellen einer neuen Richtlinien-Engine verwendet wird

**Parameters**

Parameter | Description
|---|---|
| Identität | Identität, die policyengine zugeordnet wird |
| clientData | Anpassbare Client Daten, die neben der Engine gespeichert werden |
| Gebietsschema | Das Gebiets Schema, in dem Text Ergebnisse ausgegeben werden. |
| loadsensitivitytypes | Gibt an, ob Daten der Vertraulichkeits Typen (für die Klassifizierung) ebenfalls geladen werden sollen. |
| Einstellungen | Ausgeben Neu erstellte Einstellungs Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: "loadsensitivitytypes" sollte nur "true" sein, wenn die Anwendung später MIP_CC_PolicyEngine_GetSensitivityTypes aufruft. Andernfalls sollte Sie false sein, um einen unnötigen http-Vorgang zu vermeiden. 

```c
mip_cc_result MIP_CC_CreatePolicyEngineSettingsWithIdentity(
    const mip_cc_identity* identity,
    const char* clientData,
    const char* locale,
    bool loadSensitivityTypes,
    mip_cc_policy_engine_settings* settings);
```

## <a name="mip_cc_policyenginesettings_setclientdata"></a>MIP_CC_PolicyEngineSettings_SetClientData

Legt die Client Daten fest, die mit dieser Engine verdeckt gespeichert werden und Sitzungs übergreifend beibehalten werden

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Engine-Einstellungen |
| clientData | Client Daten |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngineSettings_SetClientData(
    const mip_cc_policy_engine_settings settings,
    const char* clientData);
```

## <a name="mip_cc_policyenginesettings_setcustomsettings"></a>MIP_CC_PolicyEngineSettings_SetCustomSettings

Konfiguriert benutzerdefinierte Einstellungen, die zum Gating und Testen von Features verwendet werden.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Engine-Einstellungen |
| Datei "CustomSettings | Schlüssel-Wert-Paare von benutzerdefinierten Einstellungen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngineSettings_SetCustomSettings(
    const mip_cc_policy_engine_settings settings,
    const mip_cc_dictionary customSettings);
```

## <a name="mip_cc_policyenginesettings_setsessionid"></a>MIP_CC_PolicyEngineSettings_SetSessionId

Legt die Sitzungs-ID fest, die zum Korrelieren von Protokollen und Telemetriedaten verwendet werden kann.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Engine-Einstellungen |
| sessionID | Sitzungs-ID, die die Lebensdauer einer Richtlinie-Engine darstellt |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngineSettings_SetSessionId(
    const mip_cc_policy_engine_settings settings,
    const char* sessionId);
```

## <a name="mip_cc_policyenginesettings_setcloudendpointbaseurl"></a>MIP_CC_PolicyEngineSettings_SetCloudEndpointBaseUrl

Legt die Basis-URL für alle Service Requests fest.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Engine-Einstellungen |
| cloudendpointbaseurl | Basis-URL (z. b. "https://api.aadrm.com") |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyEngineSettings_SetCloudEndpointBaseUrl(
    const mip_cc_policy_engine_settings settings,
    const char* cloudEndpointBaseUrl);
```

## <a name="mip_cc_policyenginesettings_setdelegateduseremail"></a>MIP_CC_PolicyEngineSettings_SetDelegatedUserEmail

Legt Delegierten Benutzer fest.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Engine-Einstellungen |
| delegateduseremail | E-Mail-Adresse des delegierten Benutzers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert. 

```c
mip_cc_result MIP_CC_PolicyEngineSettings_SetDelegatedUserEmail(
    const mip_cc_policy_engine_settings settings,
    const char* delegatedUserEmail);
```

## <a name="mip_cc_releasepolicyenginesettings"></a>MIP_CC_ReleasePolicyEngineSettings

Freigeben von Ressourcen, die einem Richtlinien Modul-Einstellungen zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Richtlinien Moduleinstellungen, die freigegeben werden sollen |

```c
void MIP_CC_ReleasePolicyEngineSettings(mip_cc_policy_engine_settings settings);
```

## <a name="mip_cc_releasepolicyhandler"></a>MIP_CC_ReleasePolicyHandler

Freigeben von Ressourcen, die einem Richtlinien Handler zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Handler | Richtlinien Handler für Freigabe |

```c
void MIP_CC_ReleasePolicyHandler(mip_cc_policy_handler handler);
```

## <a name="mip_cc_policyhandler_getsensitivitylabel"></a>MIP_CC_PolicyHandler_GetSensitivityLabel

Ruft die aktuelle Bezeichnung eines Dokuments ab.

**Parameters**

Parameter | Description
|---|---|
| Handler | Richtlinien Handler |
| DocumentState | Dokument Status |
| context | Anwendungskontext, der an alle Rückrufe weitergeleitet wird |
| contentLabel | Bezeichnung, die zurzeit auf ein Dokument angewendet wird |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyHandler_GetSensitivityLabel(
    const mip_cc_policy_handler handler,
    const mip_cc_document_state* documentState,
    const void* context,
    mip_cc_content_label* contentLabel);
```

## <a name="mip_cc_policyhandler_computeactions"></a>MIP_CC_PolicyHandler_ComputeActions

Führt Richtlinien Regeln basierend auf dem angegebenen Status aus und bestimmt die entsprechenden Aktionen.

**Parameters**

Parameter | Description
|---|---|
| Handler | Richtlinien Handler |
| DocumentState | Dokument Status |
| ApplicationState | Anwendungs Aktions Status |
| context | Anwendungskontext, der an alle Rückrufe weitergeleitet wird |
| actionResult | Ausgeben Aktionen, die von der Anwendung ausgeführt werden sollen, Arbeitsspeicher im Besitz des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die "aktionresult"-Variable muss vom Aufrufer freigegeben werden, indem aufgerufen wird MIP_CC_ReleaseActionResult 

```c
mip_cc_result MIP_CC_PolicyHandler_ComputeActions(
    const mip_cc_policy_handler handler,
    const mip_cc_document_state* documentState,
    const mip_cc_application_action_state* applicationState,
    const void* context,
    mip_cc_action_result* actionResult);
```

## <a name="mip_cc_policyhandler_notifycommittedactions"></a>MIP_CC_PolicyHandler_NotifyCommittedActions

Wird von der Anwendung nach dem Anwenden berechneter Aktionen und dem Commit der Daten auf den Datenträger aufgerufen

**Parameters**

Parameter | Description
|---|---|
| Handler | Richtlinien Handler |
| DocumentState | Dokument Status |
| ApplicationState | Anwendungs Aktions Status |
| context | Anwendungskontext, der an alle Rückrufe weitergeleitet wird |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: zum Übertragen von Überwachungsdaten für die komplette Bezeichnung ist ein Aufrufe dieser Funktion erforderlich. 

```c
mip_cc_result MIP_CC_PolicyHandler_NotifyCommittedActions(
    const mip_cc_policy_handler handler,
    const mip_cc_document_state* documentState,
    const mip_cc_application_action_state* applicationState,
    const void* context);
```

## <a name="mip_cc_loadpolicyprofile"></a>MIP_CC_LoadPolicyProfile

Profil laden

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen |
| Profils | Ausgeben Neu erstellte Richtlinien Profil Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_LoadPolicyProfile(
    const mip_cc_policy_profile_settings settings,
    mip_cc_policy_profile* profile);
```

## <a name="mip_cc_releasepolicyprofile"></a>MIP_CC_ReleasePolicyProfile

Freigeben von Ressourcen, die einem Richtlinien Profil zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| Profils | Richtlinien Profil, das freigegeben werden soll |

```c
void MIP_CC_ReleasePolicyProfile(mip_cc_policy_profile profile);
```

## <a name="mip_cc_policyprofilesettings_setsessionid"></a>MIP_CC_PolicyProfileSettings_SetSessionId

Legt die Sitzungs-ID fest, die zum Korrelieren von Protokollen und Telemetriedaten verwendet werden kann.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen |
| sessionID | Die Sitzungs-ID, die die Lebensdauer eines Richtlinien Profils darstellt. |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyProfileSettings_SetSessionId(
    const mip_cc_policy_profile_settings settings,
    const char* sessionId);
```

## <a name="mip_cc_policyprofilesettings_sethttpdelegate"></a>MIP_CC_PolicyProfileSettings_SetHttpDelegate

Standard-HTTP-Stapel mit eigenem Client überschreiben

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen, denen der http-Delegat zugewiesen wird |
| httpdelegat | Von der Client Anwendung implementierte HTTP-Rückruf Instanz |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyProfileSettings_SetHttpDelegate(
    const mip_cc_policy_profile_settings settings,
    const mip_cc_http_delegate httpDelegate);
```

## <a name="mip_cc_policyprofilesettings_settaskdispatcherdelegate"></a>MIP_CC_PolicyProfileSettings_SetTaskDispatcherDelegate

Standardmäßiger asynchroner Aufgaben Verteiler mit eigenem Client überschreiben

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen, denen der Aufgaben Verteiler Delegat zugewiesen wird |
| taskdispatcherdelegat | Von der Client Anwendung implementierte Rückruf Instanz des Task Dispatchers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyProfileSettings_SetTaskDispatcherDelegate(
    const mip_cc_policy_profile_settings settings,
    const mip_cc_task_dispatcher_delegate taskDispatcherDelegate);
```

## <a name="mip_cc_policyprofilesettings_setcustomsettings"></a>MIP_CC_PolicyProfileSettings_SetCustomSettings

Konfiguriert benutzerdefinierte Einstellungen, die zum Gating und Testen von Features verwendet werden.

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Profileinstellungen |
| Datei "CustomSettings | Schlüssel-Wert-Paare von benutzerdefinierten Einstellungen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_PolicyProfileSettings_SetCustomSettings(
    const mip_cc_policy_profile_settings settings,
    const mip_cc_dictionary customSettings);
```

## <a name="mip_cc_releasepolicyprofilesettings"></a>MIP_CC_ReleasePolicyProfileSettings

Freigeben von Ressourcen, die mit Richtlinien Profileinstellungen verknüpft sind

**Parameters**

Parameter | Description
|---|---|
| Einstellungen | Richtlinien Profileinstellungen, die freigegeben werden sollen |

```c
void MIP_CC_ReleasePolicyProfileSettings(mip_cc_policy_profile_settings profilsettingseSettings);
```

## <a name="mip_cc_protectbytemplateaction_gettemplateid"></a>MIP_CC_ProtectByTemplateAction_GetTemplateId

Ruft die Vorlagen-ID "Schutz nach Vorlage" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "nach Vorlage schützen" |
| TemplateID | Ausgeben ID der Vorlage, die Schutzmaßnahmen definiert |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_ProtectByTemplateAction_GetTemplateId(
    const mip_cc_action action,
    mip_cc_guid* templateId);
```

## <a name="mip_cc_removecontentfooteraction_getuielementnames"></a>MIP_CC_RemoveContentFooterAction_GetUIElementNames

Ruft die zu entfern Endes UI-Elementnamen der Aktion "Inhalts Fußzeile entfernen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Inhalts Fußzeile entfernen" |
| -Namen | Ausgeben Namen der zu entfernenden Benutzeroberflächen Elemente, Arbeitsspeicher des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die "Names"-Variable muss vom Aufrufer durch Aufrufen von freigegeben werden MIP_CC_ReleaseStringList 

```c
mip_cc_result MIP_CC_RemoveContentFooterAction_GetUIElementNames(
    const mip_cc_action action,
    mip_cc_string_list* names);
```

## <a name="mip_cc_removecontentheaderaction_getuielementnames"></a>MIP_CC_RemoveContentHeaderAction_GetUIElementNames

Ruft die zu entfern Endes UI-Elementnamen der Aktion "Inhalts Header entfernen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Inhalts Header entfernen" |
| -Namen | Ausgeben Namen der zu entfernenden Benutzeroberflächen Elemente, Arbeitsspeicher des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die "Names"-Variable muss vom Aufrufer durch Aufrufen von freigegeben werden MIP_CC_ReleaseStringList 

```c
mip_cc_result MIP_CC_RemoveContentHeaderAction_GetUIElementNames(
    const mip_cc_action action,
    mip_cc_string_list* names);
```

## <a name="mip_cc_removewatermarkaction_getuielementnames"></a>MIP_CC_RemoveWatermarkAction_GetUIElementNames

Ruft die zu entfern Endes UI-Elementnamen der Aktion "Wasserzeichen entfernen" ab.

**Parameters**

Parameter | Description
|---|---|
| Aktion | Aktion "Wasserzeichen entfernen" |
| -Namen | Ausgeben Namen der zu entfernenden Benutzeroberflächen Elemente, Arbeitsspeicher des Aufrufers |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: die "Names"-Variable muss vom Aufrufer durch Aufrufen von freigegeben werden MIP_CC_ReleaseStringList 

```c
mip_cc_result MIP_CC_RemoveWatermarkAction_GetUIElementNames(
    const mip_cc_action action,
    mip_cc_string_list* names);
```

## <a name="mip_cc_releasesensitivitytype"></a>MIP_CC_ReleaseSensitivityType

Freigeben von Ressourcen, die einem Vertraulichkeits Typ zugeordnet sind

**Parameters**

Parameter | Description
|---|---|
| sensitivitytype | Zu veröffentlichende Vertraulichkeits Typen |

```c
void MIP_CC_ReleaseSensitivityType(mip_cc_sensitivity_type sensitivityType);
```

## <a name="mip_cc_sensitivitytype_getrulepackageidsize"></a>MIP_CC_SensitivityType_GetRulePackageIdSize

Ruft die Größe des Puffers ab, der zum Speichern der Regelpaket-ID eines Vertraulichkeits Typs

**Parameters**

Parameter | Description
|---|---|
| sensitivitytype | Sensitivitäts-Typ |
| idsize | Ausgeben Größe des Puffers zum Speichern der Regelpaket-ID (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_SensitivityType_GetRulePackageIdSize(
    const mip_cc_sensitivity_type sensitivityType,
    int64_t* idSize);
```

## <a name="mip_cc_sensitivitytype_getrulepackageid"></a>MIP_CC_SensitivityType_GetRulePackageId

Ruft die Regelpaket-ID eines Vertraulichkeits Typs ab.

**Parameters**

Parameter | Description
|---|---|
| sensitivitytype | Sensitivitäts-Typ |
| idbuffer | Ausgeben Puffer, in den die ID kopiert wird. |
| idbuffersize | Größe (in Anzahl der Zeichen) des idbuffer. |
| actualidsize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn idbuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualidsize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_SensitivityType_GetRulePackageId(
    const mip_cc_sensitivity_type sensitivityType,
    char* idBuffer,
    const int64_t idBufferSize,
    int64_t* actualIdSize);
```

## <a name="mip_cc_sensitivitytype_getrulepackagesize"></a>MIP_CC_SensitivityType_GetRulePackageSize

Ruft die Größe des Puffers ab, der zum Speichern des Regel Pakets für sensible Typen erforderlich ist

**Parameters**

Parameter | Description
|---|---|
| sensitivitytype | Sensitivitäts-Typ |
| rulepackagesize | Ausgeben Größe des Puffers zum Speichern des Regel Pakets (in Anzahl von Zeichen) |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

```c
mip_cc_result MIP_CC_SensitivityType_GetRulePackageSize(
    const mip_cc_sensitivity_type sensitivityType,
    int64_t* rulePackageSize);
```

## <a name="mip_cc_sensitivitytype_getrulepackage"></a>MIP_CC_SensitivityType_GetRulePackage

Ruft das Regelpaket eines Vertraulichkeits Typs ab.

**Parameters**

Parameter | Description
|---|---|
| sensitivitytype | Sensitivitäts-Typ |
| rulepackagebuffer | Ausgeben Puffer, in den das Regelpaket kopiert wird. |
| rulepackagebuffersize | Größe (in Anzahl der Zeichen) des rulepackagebuffer. |
| actualrulepackagesize | Ausgeben Anzahl der in den Puffer geschriebenen Zeichen |

**Return**: Ergebniscode, der einen Erfolg oder Fehler angibt

**Hinweis**: Wenn rulepackagebuffer NULL oder unzureichend ist, wird MIP_RESULT_ERROR_INSUFFICIENT_BUFFER zurückgegeben, und actualrulepackagesize wird auf die mindestens erforderliche Puffergröße festgelegt. 

```c
mip_cc_result MIP_CC_SensitivityType_GetRulePackage(
    const mip_cc_sensitivity_type sensitivityType,
    char* rulePackageBuffer,
    const int64_t rulePackageBufferSize,
    int64_t* actualRulePackageSize);
```

