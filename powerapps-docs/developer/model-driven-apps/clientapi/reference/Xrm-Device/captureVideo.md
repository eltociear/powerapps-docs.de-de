---
title: captureVideo | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9580d05a-a91f-4126-b94b-4d1068da35fa
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="capturevideo-client-api-reference"></a>captureVideo (Client-API-Referenz)



[!INCLUDE[./includes/captureVideo-description.md](./includes/captureVideo-description.md)]


## <a name="syntax"></a>Syntax

`Xrm.Device.captureVideo().then(successCallback, errorCallback)`

## <a name="parameters"></a>Parameter

| Parametername        | Typ           | Erforderlich  |Beschreibung  |
| ------------- |-------------| -----|-----|
|successCallback |Funktion | Ja|Eine Funktion, die bei der Rückgabe des Videos aufgerufen wird. Ein base64-kodiertes Videoobjekt wird mit folgenden Attributen an die Funktion übergeben:<br/>- **fileContent**: Inhalt der Videodatei. String <br/>- **fileName**: Name der Videodatei. Zeichenfolge.<br/>- **fileSize**: Größe der Videodatei in KB. Nummer.<br/>- **mimeType**: Videodatei-MIME-Typ. Zeichenfolge.|
|errorCallback |Funktion | Ja|Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug. |
 

## <a name="return-value"></a>Rückgabewert
Bei Erfolg wird ein base64-kodiertes Videoobjekt mit den zuvor angegebenen Attributen zurückgegeben.

## <a name="remarks"></a>Anmerkungen
Diese Methode wird nur für mobile Clients unterstützt.

### <a name="related-topics"></a>Verwandte Themen
[Xrm.Device](../xrm-device.md)

