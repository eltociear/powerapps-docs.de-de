---
title: invokeProcessAction (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e71012ba-249d-4ae7-8891-f7d3ae16a20a
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="invokeprocessaction-client-api-reference"></a>invokeProcessAction (Client-API-Referenz)



[!INCLUDE[./includes/invokeProcessAction-description.md](./includes/invokeProcessAction-description.md)] 

Weitere Informationen über sämtliche Aktionen finden Sie unter [Aktionen nutzen](/flow/actions)

## <a name="syntax"></a>Syntax

`Xrm.Utility.invokeProcessAction(name,parameters).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|Name|String|Ja|Name der aufzurufenden Prozessaktion.|
|Parameter|Objekt|No|Ein Objekt, das die Eingabeparameter für die Aktion enthält. Sie definieren ein Objekt mit `key:value` Paaren von Elementen, wobei `key` vom Typ **Zeichenfolge** ist.|
|successCallback |Funktion |Ja |Ein Funktion, die beim Aufrufen der Aktion aufgerufen wird.  |
|errorCallback |Funktion |Ja |Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug.  |

## <a name="returns"></a>Gibt zurück

Bei Erfolg wird ein Internet-API-Ergebnis zusammen mit der Aktionsausgabe zurückgegeben.

### <a name="related-topics"></a>Verwandte Themen

[Aktionen nutzen](/flow/actions)

[Xrm.Utility](../xrm-utility.md)


