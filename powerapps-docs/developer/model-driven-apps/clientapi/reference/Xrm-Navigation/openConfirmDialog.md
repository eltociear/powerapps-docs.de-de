---
title: openConfirmDialog (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9c82028d-cbc9-4d40-9987-6ce1ea01fde2
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openconfirmdialog-client-api-reference"></a>openConfirmDialog (Client-API-Referenz)



[!INCLUDE[./includes/openConfirmDialog-description.md](./includes/openConfirmDialog-description.md)]

## <a name="syntax"></a>Syntax

`Xrm.Navigation.openConfirmDialog(confirmStrings,confirmOptions).then(successCallback,errorCallback);`

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|confirmStrings|Objekt|Ja|Die im Dialogfeld Bestätigung verwendeten Zeichenfolgen. Das Objekt hat die folgenden Attribute:<br/>- **cancelButtonLabel**: (Optional) Zeichenfolge. Die Abbrechen-Schaltflächenbeschriftung. Wenn Sie nicht die Beschriftung der Abbrechen-Schaltfläche angeben, wird **Abbrechen** als Beschriftung der Schaltfläche verwendet.<br/>- **confirmButtonLabel**: (Optional) Zeichenfolge. Die Bestätigensschaltflächenbeschriftung. Wenn Sie nicht die Beschriftung der Bestätigen-Schaltfläche angeben, wird **OK** als Beschriftung der Schaltfläche verwendet.<br/>- **Untertitel**: (Optional) Zeichenfolge. Der Untertitel zum Anzeigen im Dialogfeld Bestätigen.<br/>- **Text**: Zeichenfolge. Die im Bestätigungsdialog anzuzeigende Nachricht.<br/>- **Titel**: (Optional) Zeichenfolge. Der im Bestätigungsdialog anzuzeigende Titel.|
|confirmOptions|Objekt|Nr.|Die Höhen- und Breitenoptionen für Bestätigen-Dialogfeld. Das Objekt hat die folgenden Attribute:<br/>- **Höhe**: (Optional) Zahl. Höhe des Bestätigung-Dialogfelds in Pixeln.<br/>- **Breite**: (Optional) Zahl. Breite des Bestätigung-Dialogfelds in Pixeln.|
|successCallback|Funktion|No|Ein Feature zum Ausführen, wenn das Bestätigungsdialogfeld geschlossen ist, indem das bestätigte, Löschen oder in der **X** rechten Ecke des Dialogfelds. Ein Objekt mit dem Attribut **Bestätigt** (boolesch) wird übergeben, das angibt, ob die Bestätigen-Schaltfläche angeklickt wurde, um das Dialogfeld zu schließen.|
|errorCallback|Funktion|No|Eine auszuführende Funktion, wenn der Vorgang fehlgeschlagen ist.|

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird ein Bestätigungsdialogfeld angezeigt. Entsprechende Nachricht wird in der Konsole protokolliert, je nachdem, ob Sie bestätigen oder cancel/**X** geklickt wurde, um das Dialogfeld zu schließen.

```JavaScript
var confirmStrings = { text:"This is a confirmation.", title:"Confirmation Dialog" };
var confirmOptions = { height: 200, width: 450 };
Xrm.Navigation.openConfirmDialog(confirmStrings, confirmOptions).then(
function (success) {    
    if (success.confirmed)
        console.log("Dialog closed using OK button.");
    else
        console.log("Dialog closed using Cancel button or X.");
});

```

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Navigation](../xrm-navigation.md)

