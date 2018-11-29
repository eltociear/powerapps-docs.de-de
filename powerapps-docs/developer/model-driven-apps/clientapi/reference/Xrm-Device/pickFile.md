---
title: pickFile| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c777a0b8-2b07-458b-8a4f-8938f7a2e696
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="pickfile-client-api-reference"></a>pickFile (Client-API-Referenz)



[!INCLUDE[./includes/pickFile-description.md](./includes/pickFile-description.md)]


## <a name="syntax"></a>Syntax

`Xrm.Device.pickFile(pickFileOptions).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parameter

| Parametername        | Typ           | Erforderlich  |Beschreibung  |
| ------------- |-------------| -----|-----|
|pickFileOptions |Objekt | No|Ein Objekt mit folgenden Attributen:<br/>- **akzeptieren**: Auszuwählende Bilddateitypen. Gültige Werte lauten "Audio ", "Video " oder "Bild". Zeichenfolge.<br/>- **allowMultipleFiles**: Gibt an, ob das Aktivieren von mehreren Dateien möglich ist. Boolescher Wert<br/>- **maximumAllowedFileSize**: Maximal zulässige Größe der Datei(en), die ausgewählt werden können. Nummer.|
|successCallback |Funktion | Ja|Ein Feature zum Aufrufen, wenn die ausgewählten Dateien zurückgegeben werden. Ein Objektarray mit *jedem* Objekt, das die folgenden Attribute aufweist, wird zur Funktion übergeben:<br/>- **fileContent**: Inhalt der Datei. String <br/>- **fileName**: Name der Datei. Zeichenfolge.<br/>- **fileSize**: Dateigröße in KB. Nummer.<br/>- **mimeType**: Datei-MIME-Typ. Zeichenfolge.|
|errorCallback |Funktion | Ja|Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug. |
 

## <a name="return-value"></a>Rückgabewert
Bei Erfolg wird ein Versprechenmit Objektarray zurückgegeben, das zuvor für die **successCallback**-Funktion angegeben wurde.

### <a name="related-topics"></a>Verwandte Themen
[Xrm.Device](../xrm-device.md)

