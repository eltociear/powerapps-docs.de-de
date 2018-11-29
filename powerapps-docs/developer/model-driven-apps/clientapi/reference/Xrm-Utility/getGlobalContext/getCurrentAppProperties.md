---
title: getCurrentAppProperties (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5f8d91ff-ba0d-4e90-a79a-18e32d09baa3
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcurrentappproperties-client-api-reference"></a>getCurrentAppProperties (Client-API-Referenz)



Gibt der Eigenschaft der aktuellen Geschäfts-API in modellgetriebenen Apps zurück.

## <a name="syntax"></a>Syntax

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getCurrentAppProperties().then(successCallback, errorCallback);
``` 

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|successCallback |Funktion |Ja |Ein Funktion, die bei der Rückgabe der Eigenschaftsinformationen der Geschäfts-App aufgerufen wird. Ein Objekt mit folgenden Attributen (App-Eigenschaften) wird an die Funktion übergeben:<br/>- **appId**<br/>- **displayName**<br/>- **uniqueName**<br/>- **url**<br/>- **webResourceId**<br/>- **webResourceName**<br/>- **welcomePageId**<br/>- **welcomePageName**|
|errorCallback |Funktion |Ja |Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug.  |

## <a name="return-value"></a>Rückgabewert

Wenn die Methode im Rahmen einer Unternehmens-App aufgerufen wird, gibt sie die Eigenschaften der Unternehmens-App zurück. Andernfalls schlägt sie mit eine Fehlermeldung fehl.

### <a name="related-topics"></a>Verwandte Themen

[Erstellen, Verwalten und Veröffentlichen von modellgesteuerten Apps mithilfe von Code](../../../../create-manage-model-driven-apps-using-code.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md) 



