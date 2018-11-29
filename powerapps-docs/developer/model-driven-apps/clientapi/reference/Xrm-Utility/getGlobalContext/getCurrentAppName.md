---
title: getCurrentAppName (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a8f83718-41a4-4958-a5ac-9b28cc2f8dba
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcurrentappname-client-api-reference"></a>getCurrentAppName (Client-API-Referenz)



Gibt den Namen der aktuellen Geschäfts-API in modellgetriebenen Apps zurück.

## <a name="syntax"></a>Syntax

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getCurrentAppName().then(successCallback, errorCallback);
``` 

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|successCallback |Funktion |Ja |Ein Funktion, die bei der Rückgabe des Namens der Geschäfts-App aufgerufen wird.  |
|errorCallback |Funktion |Ja |Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug.  |

## <a name="return-value"></a>Rückgabewert

Wenn die Methode im Rahmen einer Unternehmens-App aufgerufen wird, gibt sie den Namen der Unternehmens-App zurück. Andernfalls schlägt sie mit eine Fehlermeldung fehl.

### <a name="related-topics"></a>Verwandte Themen

[Erstellen, Verwalten und Veröffentlichen von modellgesteuerten Apps mithilfe von Code](../../../../create-manage-model-driven-apps-using-code.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)


