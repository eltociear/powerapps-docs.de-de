---
title: setFormNotification (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 48749e32-8490-4c8f-917c-3f1f8b9c028b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setformnotification-client-api-reference"></a>setFormNotification (Client-API-Referenz)



[!INCLUDE[./includes/setFormNotification-description.md](./includes/setFormNotification-description.md)]

Sie können eine beliebige Anzahl von Benachrichtigungen anzeigen, und sie werden angezeigt, bis sie mithilfe von [clearFormNotification](clearFormNotification.md) entfernt werden. Die Höhe des Infobereichs ist beschränkt, daher wird jede neue Nachricht oben hinzugefügt. Benutzer können einen Bildlauf nach unten durchführen, um ältere Nachrichten anzuzeigen, die noch nicht entfernt wurden.

## <a name="syntax"></a>Syntax

`formContext.ui.setFormNotification(message, level, uniqueId);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|Meldung|String|Ja|Der Text der Nachricht.|
|Ebene|String|Ja|Die Ebene der Meldung, die definiert, wie die Meldung angezeigt wird. Geben Sie einen der folgenden Werte an:<br>`ERROR` : Benachrichtigung verwendet das Systemfehlersymbol.<br/>`WARNING` : Benachrichtigung verwendet das Warnsymbol.<br/>`INFO` : Benachrichtigung verwendet das Infosymbol.|
|uniqueId|String|Ja|Ein eindeutiger Bezeichner für die Nachricht, der später mit [clearFormNotification](clearFormNotification.md) verwendet werden kann zu, um die Benachrichtigung zu entfernen.|

## <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch

**Bezeichnung**: true, wenn die Methode erfolgreich ist, ansonsten false. 


### <a name="related-topics"></a>Verwandte Themen

[clearFormNotification](clearFormNotification.md)

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

