---
title: openAlertDialog (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8615a284-41b4-479c-81bd-577b3b7c79ad
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openalertdialog-client-api-reference"></a>openAlertDialog (Client-API-Referenz)



[!INCLUDE[./includes/openAlertDialog-description.md](./includes/openAlertDialog-description.md)]

## <a name="syntax"></a>Syntax

`Xrm.Navigation.openAlertDialog(alertStrings,alertOptions).then(closeCallback,errorCallback);`

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|alertStrings|Objekt|Ja|Die im Dialogfeld Warnung verwendeten Zeichenfolgen. Das Objekt hat die folgenden Attribute:<br/>- **confirmButtonLabel**: (Optional) Zeichenfolge. Die Bestätigensschaltflächenbeschriftung. Wenn Sie nicht die Beschriftung der Schaltfläche angeben, wird **OK** als Beschriftung der Schaltfläche verwendet.<br/>- **Text**: Zeichenfolge. Die im Dialogfeld anzuzeigende Nachricht.|
|alertOptions|Objekt|No|Die Höhen- und Breitenoptionen für Warnung-Dialogfeld. Das Objekt hat die folgenden Attribute:<br/>- **Höhe**: (Optional) Zahl. Höhe des Warnung-Dialogfelds in Pixeln.<br/>- **Breite**: (Optional) Zahl. Breite des Warnung-Dialogfelds in Pixeln.|
|successCallback|Funktion|No|Ein Feature zum Ausführen, wenn das Warnung-Dialogfeld durch Klicken auf die Bestätigen-Schaltfläche geschlossen oder abgebrochen wird, indem ESC gedrückt wird.|
|errorCallback|Funktion|No|Eine auszuführende Funktion, wenn der Vorgang fehlgeschlagen ist.|


## <a name="example"></a>Beispiel

Der folgende Warnung-Beispielcode zeigt ein Dialogfeld an. Wenn Sie im Dialogfeld Warnung auf die Schaltfläche **Ja** klicken oder das Dialogfeld Warnung durch Drücken von ESC abbrechen, wird die `close`-Funktion aufgerufen:

```JavaScript
var alertStrings = { confirmButtonLabel: "Yes", text: "This is an alert." };
var alertOptions = { height: 120, width: 260 };
Xrm.Navigation.openAlertDialog(alertStrings, alertOptions).then(
    function success(result) {
        console.log("Alert dialog closed");
    },
    function (error) {
        console.log(error.message);
    }
);
```

### <a name="related-topics"></a>Verwandte Themen

[Xrm.navigation](../xrm-navigation.md)

