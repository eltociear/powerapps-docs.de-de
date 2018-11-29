---
title: getBarcodeValue| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 0218b96c-2809-4f2d-9f9f-d8ee8f8e3b7b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getbarcodevalue-client-api-reference"></a>getBarcodeValue (Client-API-Referenz)



[!INCLUDE[./includes/getBarcodeValue-description.md](./includes/getBarcodeValue-description.md)]


## <a name="syntax"></a>Syntax

`Xrm.Device.getBarcodeValue().then(successCallback, errorCallback)`

## <a name="parameters"></a>Parameter

| Parametername        | Typ           | Erforderlich  |Beschreibung  |
| ------------- |-------------| -----|-----|
|successCallback |Funktion | Ja|Ein Funktion, die bei der Rückgabe des Barcodewerts als Zeichenfolge zurückgegeben wird.|
|errorCallback |Funktion | Ja|Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug. Ein Fehlerobjekt mit der **Message**-Eigenschaft (Zeichenfolge) wird übergeben, das die Fehlerdetails beschreibt.|
 

## <a name="return-value"></a>Rückgabewert
Bei Erfolg wird eine Zeichenfolge zurückgegeben, die den gescannten Barcodewert enthält.

## <a name="remarks"></a>Anmerkungen
Diese Methode wird nur für mobile Clients unterstützt.

## <a name="example"></a>Beispiel

```JavaScript
Xrm.Device.getBarcodeValue().then(
    function success(result) {
        Xrm.Navigation.openAlertDialog({ text: "Barcode value: " + result });
    },
    function (error) {
        Xrm.Navigation.openAlertDialog( {text: error.message} );
    }
);
``` 

### <a name="related-topics"></a>Verwandte Themen
[Xrm.Device](../xrm-device.md)

