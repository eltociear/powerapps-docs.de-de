---
title: captureAudio | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: fa39d18e-4b82-423a-84a0-e54450b7964e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="captureaudio-client-api-reference"></a>captureAudio (Client-API-Referenz)



[!INCLUDE[./includes/captureAudio-description.md](./includes/captureAudio-description.md)]


## <a name="syntax"></a>Syntax

`Xrm.Device.captureAudio().then(successCallback, errorCallback)`

## <a name="parameters"></a>Parameter

| Parametername        | Typ           | Erforderlich  |Beschreibung  |
| ------------- |-------------| -----|-----|
|successCallback |Funktion | Ja|Eine Funktion, die bei der Rückgabe des Audios aufgerufen wird. Ein base64-kodiertes Audioobjekt wird mit folgenden Attributen an die Funktion übergeben:<br/>- **fileContent**: Inhalt der Audiodatei. String <br/>- **fileName**: Name der Audiodatei. Zeichenfolge.<br/>- **fileSize**: Größe der Audiodatei in KB. Nummer.<br/>- **mimeType**: Audiodatei-MIME-Typ. Zeichenfolge.|
|errorCallback |Funktion | Ja|Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug. |
 

## <a name="return-value"></a>Rückgabewert
Bei Erfolg wird ein base64-kodiertes Audioobjekt mit den zuvor angegebenen Attributen zurückgegeben.

## <a name="remarks"></a>Anmerkungen
Diese Methode wird nur für mobile Clients unterstützt.

### <a name="related-topics"></a>Verwandte Themen
[Xrm.Device](../xrm-device.md)

