---
title: openErrorDialog (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9749143d-c159-4833-aff9-d8bc2c3395f3
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openerrordialog-client-api-reference"></a>openErrorDialog (Client-API-Referenz)



[!INCLUDE[./includes/openErrorDialog-description.md](./includes/openErrorDialog-description.md)]

## <a name="syntax"></a>Syntax

`Xrm.Navigation.openErrorDialog(errorOptions).then(successCallback,errorCallback);`

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|errorOptions|Objekt|Ja|Ein Objekt, um die Optionen für das Dialogfeld Fehler anzugeben. Das Objekt hat die folgenden Attribute:<br/>- **Details**: (Optional) Zeichenfolge. Informationen zum Fehler. Wenn Sie dem angeben, ist die Schaltfläche **Protokolldatei herunterladen** in der Fehlermeldung ist verfügbar, indem Sie darauf klicken und eine Textdatei den Inhalt herunterladen, die in diesem Attribut angegeben ist.<br/>- **errorCode**: (Optional) Zahl. Der Fehlercode. Wenn Sie nur **errorCode** einstellen, wird die Meldung für den Fehlercode automatisch vom Server abgerufen und im Fehlerdialogfeld angezeigt. Wenn Sie einen ungültiger Wert **errorCode** angeben, wird eine Standardfehlermeldung angezeigt.<br/>- **Meldung**: (Optional) Zeichenfolge. Die im Fehler-Dialogfeld anzuzeigende Nachricht.<br/><br/>Sie müssen entweder das Attribut **errorCode** oder **Beitrag** festlegen. |
|successCallback|Funktion|No|Eine Funktion, die ausgeführt wird, wenn auf die Fehler-Dialog-Schaltfläche geklickt wird.|
|errorCallback|Funktion|No|Eine auszuführende Funktion, wenn der Vorgang fehlgeschlagen ist.|

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt ein falsches errorCode (1234) um einen Standardfehlerdialog anzuzeigen:

```JavaScript
Xrm.Navigation.openErrorDialog({ errorCode:1234 }).then(
    function (success) {
        console.log(success);        
    },
    function (error) {
        console.log(error);
    });
```

Hier sehen Sie ein Fehler-Dialogfeld mit der Standardnachricht:

![Fehler-Dialogfeld mit Standardnachricht](../../../media//clientapi_sampleerrordialog.png)

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Navigation](../xrm-navigation.md)

