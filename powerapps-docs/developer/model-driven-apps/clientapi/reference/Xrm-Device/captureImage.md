---
title: captureImage | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1b24e8b2-20af-4e75-8c00-1aa393c07aef
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="captureimage-client-api-reference"></a>captureImage (Client-API-Referenz)



[!INCLUDE[./includes/captureImage-description.md](./includes/captureImage-description.md)]


## <a name="syntax"></a>Syntax

`Xrm.Device.captureImage(imageOptions).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parameter

| Parametername        | Typ           | Erforderlich  |Beschreibung  |
| ------------- |-------------| -----|-----|
|imageOptions |Objekt | No|Ein Objekt mit folgenden Attributen:<br/>- **allowEdit**: Bestimmt, ob das Bild vor dem Speichern zu bearbeiten ist. Boolescher Wert<br/>- **height**: Höhe des Bilds zum Erfassen. Nummer.<br/>- **preferFrontCamera**: Bestimmt, ob das Bild mit der Frontkamera des Geräts aufzunehmen ist. Boolescher Wert<br/>- **quality**: Qualität der Bilddatei in Prozent. Nummer.<br/>- **width**: Breite des Bilds zum Erfassen. Anzahl.|
|successCallback |Funktion | Ja|Eine Funktion, die bei der Rückgabe des Bilds aufgerufen wird. Ein base64-kodiertes Bildobjekt wird mit folgenden Attributen an die Funktion übergeben:<br/>- **fileContent**: Inhalt der Bilddatei. String <br/>- **fileName**: Name der Bilddatei. Zeichenfolge.<br/>- **fileSize**: Größe der Bilddatei in KB. Nummer.<br/>- **mimeType**: Bilddatei-MIME-Typ. Zeichenfolge.|
|errorCallback |Funktion | Ja|Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug. |
 

## <a name="return-value"></a>Rückgabewert
Bei Erfolg wird ein base64-kodiertes Bildobjekt mit den zuvor angegebenen Attributen zurückgegeben.

## <a name="remarks"></a>Anmerkungen
Diese Methode wird nur für mobile Clients unterstützt.

### <a name="related-topics"></a>Verwandte Themen
[Xrm.Device](../xrm-device.md)

