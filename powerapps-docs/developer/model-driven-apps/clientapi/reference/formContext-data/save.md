---
title: save (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 03e970ee-7ed3-4df2-9670-222d76a479fd
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="save-client-api-reference"></a>Speichern (Client-API-Referenz)



[!INCLUDE[./includes/save-description.md](./includes/save-description.md)]

Sie können auch ein Objekt festlegen, um zu steuern, wie ein Termin, Serientermin oder Serviceaktivitätsdatensätze verarbeitet werden.

## <a name="syntax"></a>Syntax

`formContext.data.save(saveOptions).then(successCallback, errorCallback);`

## <a name="parameters"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|saveOptions|Objekt|No|Ein Objekt zum Festlegen von Optionen zum Speichern des Datensatzes. Das -Objekt hat die folgenden Attribute:<br/><br/>- **saveMode**: (Optional) Zahl. Geben Sie einen Wert an, der angibt, wie das Speichern-Ereignis initiiert wurde. Eine Liste der unterstützten Werte, siehe den Rückgabewert der [getSaveMode](../save-event-arguments/getsavemode.md)-Methode. Beachten Sie, dass der **saveMode** nicht wirklich die entsprechenden Aktivitäten ausführt; es ist einfach, Informationen zu den **OnSave**-Ereignishandlern zu dem Grund für den Speichervorgang bereitzustellen.<br/><br/>- **useSchedulingEngine**: (Optional) boolesch. Geben Sie an, ob die Schaltfläche **Buchen** oder **Erneut planen** Nachrichten und nicht die Meldungen **Erstellen** oder **Aktualisieren** verwendeten soll. Diese Option gilt nur, wenn sie mit einem Termin, Serientermin oder Serviceaktivitätsdatensätzen verwendet wird.|
|successCallback|Funktion|No|Eine Funktion zum Aufrufen, wenn der Vorgang erfolgreich war.|
|errorCallback|Funktion|Nein|Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug. Es wird ein Objekt mit den folgenden Eigenschaften übergeben:<br/><br/>- **errorCode**: Zahl. Der Fehlercode.<br/><br/>- **Nachricht**: Zeichenfolge. Eine loklisierte Fehlermeldung.|


### <a name="related-topics"></a>Verwandte Themen

[formContext.data.entity.save](../formContext-data-entity/save.md)

[formContext](../../clientapi-form-context.md)

