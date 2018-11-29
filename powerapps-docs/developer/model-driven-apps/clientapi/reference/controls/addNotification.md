---
title: addNotification (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addnotification-client-api-reference"></a>addNotification (Client-API-Referenz)



Zeigt eine Fehler- oder Empfehlungs- Benachrichtigung für ein Steuerelement an und Sie können Aktionen angeben, die basierend auf der Benachrichtung ausgeführt werden sollen. Wenn Sie einen Fehlertyp für eine Benachrichtigung angeben, wird ein rotes „X“-Symbol neben dem Steuerelement angezeigt. Wenn Sie einen Empfehlungstyp für eine Benachrichtigung angeben, wird ein „i“-Symbol neben dem Steuerelement angezeigt. Auf mobilen Dynamics 365-Clients wird die Benachrichtung angezeigt, wenn Sie auf die Schaltfläche tippen, und Sie können die konfigurierten Aktionen ausführen, indem Sie auf die Schaltfläche **Übernehmen** klicken oder die Meldung schließen. 

## <a name="control-types-supported"></a>Unterstützte Steuerelementtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).addNotification(notification);`

## <a name="parameters"></a>Parameter

<table style="width:100%">
<tr>
<th>Name</th>
<th>Typ</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>Benachrichtigung</td>
<td>Objekt</td>
<td>Ja</td>
<td>Die Benachrichtigung zum Hinzufügen. Das Objekt hat die folgenden Attribute:
<ul>
<li><b>actions</b>: (Optional) Objektarray. Eine Sammlung von Objekten mit den folgenden Attributen:
<ul>
<li><b>message</b>: (Optional) Zeichenfolge. Der Benachrichtigungstext, der dem Benutzer angezeigt wird. Beschränken Sie Ihre Nachricht auf 100 Zeichen für eine optimale Benutzerfreundlichkeit.</li>
<li><b>actions</b>: (Optional) Funktionenarray. Die entsprechenden Aktionen für die Nachricht.</li>
</ul>
<li><b>messages</b>: Zeichenfolgenarray. Die Meldung, die die Benachrichtigung anzeigt. In der aktuellen Version wird nur die erste Nachricht, die in diesem Array angegeben wird, angezeigt. Eine angegebene Zeichenfolge wird als fetter Text in der Benachrichtung angezeigt und wird in der Regel für Titel oder Betreff verwendet. Sie sollten Ihre Mitteilung auf 50 Zeichen beschränken, um eine optimale Benutzerfreundlichkeit zu gewährleisten.</li>
<li><b>notificationLevel</b>: Zeichenfolge. Definiert den Typ der Benachrichtigung. Gültige Werte sind ERROR oder RECOMMENDATION.</li>
<li><b>uniqueId</b>: Zeichenfolge. Die zum Löschen dieser Nachricht zu verwendende ID, wenn die <b>clearNotification</b>-Methode angewendet wird.</li>
</ul></td>
</tr>

</table>

## <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch.

**Beschreibung**: Gibt an, ob die Methode erfolgreich war.


## <a name="remarks"></a>Anmerkungen

Die **addNotification**-Methode zeigt eine Benachrichtigung mit den Nachrichten, die Sie angegeben haben, an und zwei Standardschaltflächen: **Übernehmen** und **Schließen**. Wenn Sie auf **Übernehmen** klicken, wird die Aktion ausgeführt, die von Ihnen definiert wurde; klicken Sie auf **Verwerfen** wird die Benachrichtigung geschlossen. 

## <a name="example"></a>Beispiel

Der folgende Beispielcode zeigt eine Benachrichtigung im Feld **Firmenname** des Firmenformulars an, um das **Tickersymbol** festzulegen, wenn das Feld **Firmenname** „Microsoft” enthält und das Tickersymbol bereits auf „MSFT” nicht festgelegt ist. Wenn Sie auf **Übernehmen** in der Benachrichtigung klicken, wird das **Tickersymbol**-Feld auf „MSFT” festgelegt.

```JavaScript
function addTickerSymbolRecommendation(executionContext) {
    var formContext = executionContext.getFormContext();
    var myControl = formContext.getControl('name');
    var accountName = formContext.data.entity.attributes.get('name');
    var tickerSymbol = formContext.data.entity.attributes.get('tickersymbol');

    if (accountName.getValue() == 'Microsoft' && tickerSymbol.getValue() != 'MSFT') {
        var actionCollection = {
            message: 'Set the Ticker Symbol to MSFT?',
            actions: null
        };

        actionCollection.actions = [function () {
            tickerSymbol.setValue('MSFT');
            myControl.clearNotification('my_unique_id');
        }];

        myControl.addNotification({
            messages: ['Set Ticker Symbol'],
            notificationLevel: 'RECOMMENDATION',
            uniqueId: 'my_unique_id',
            actions: [actionCollection]
        });
    }
    else
        console.log("Notification not set");
}
```

### <a name="related-topics"></a>Verwandte Themen

[clearNotification](clearNotification.md)

[setNotification](setNotification.md)



