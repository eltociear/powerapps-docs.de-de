---
title: getCurrentPosition| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 062a52d8-170c-4e98-b48a-ac99ec759f83
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcurrentposition-client-api-reference"></a>getCurrentPosition (Client-API-Referenz)



[!INCLUDE[./includes/getCurrentPosition-description.md](./includes/getCurrentPosition-description.md)]


## <a name="syntax"></a>Syntax

`Xrm.Device.getCurrentPosition().then(successCallback, errorCallback)`

## <a name="parameters"></a>Parameter

| Parametername        | Typ           | Erforderlich  |Beschreibung  |
| ------------- |-------------| -----|-----|
|successCallback |Funktion | Ja|Ein Funktion, die bei der Rückgabe der aktuellen Geostandortinformationen aufgerufen wird. Ein Geolokalisierungsobjekt mit folgenden Attributen wird an die Funktion übergeben:<br/>- **coords**: Enthält einen Satz geografischer Koordinaten mit entsprechender Genauigkeit sowie einen Satz anderer optionaler Attribute wie die Höhe und Geschwindigkeit. <br/>- **timestamp**: Stellt die Uhrzeit dar, zu der das Objekt erhalten wurde und ist ein DOMTimeStamp.|
|errorCallback |Funktion | Ja|Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug. Es wird ein Objekt mit den folgenden Eigenschaften übergeben: <br/>- **code**: Der Fehlercode. Nummer. <br/>- **message**: Lokalisierte Meldung, welche die Fehlerdetails beschreibt. Zeichenfolge.<br/><br/>Wenn der die Lokalisierungseinstellung des Benutzers nicht auf dem Mobilgerät aktiviert ist, zeigt die Fehlermeldung dies an. Falls Sie eine frühere Version des modellgesteuerten Apps mobilen Clients verwenden, oder wenn die Geolokalisierungsfunktion nicht auf mobilen Geräten verfügbar ist, wird Null an den Fehler-Callback übergeben.|
 

## <a name="return-value"></a>Rückgabewert
Bei Erfolg wird ein Geolocation-Objekt mit den Attributen zurückgegeben, die zuvor in der **successCallback**-Funktion angegeben wurden.

## <a name="remarks"></a>Anmerkungen
Damit die **getCurrentPosition**-Methode funktioniert, muss Geolokalisierungsfunktion auf dem Mobilgerät aktiviert sein und der modellgesteuerte Apps mobile Client muss die Berechtigungen besitzen, auf den Gerätespeicherort zuzugreifen (standardmäßig nicht aktiviert).

Diese Methode wird nur für mobile Clients unterstützt.

## <a name="example"></a>Beispiel

```JavaScript
Xrm.Device.getCurrentPosition().then(
    function success(location) {
        Xrm.Navigation.openAlertDialog({
            text: "Latitude: " + location.coords.latitude +
            ", Longitude: " + location.coords.longitude
        });
    },
    function (error) {
        Xrm.Navigation.openAlertDialog({ text: error.message });
    }
);
```

### <a name="related-topics"></a>Verwandte Themen
[Xrm.Device](../xrm-device.md)

