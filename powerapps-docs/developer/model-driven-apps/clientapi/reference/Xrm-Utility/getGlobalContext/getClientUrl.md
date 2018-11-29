---
title: getClientUrl (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getclienturl-client-api-reference"></a>getClientUrl (Client-API-Referenz)



Gibt die Basis-URL zurück, die verwendet wurde, um auf die Anwendung zuzugreifen.

## <a name="syntax"></a>Syntax

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getClientUrl();
``` 

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Die Werte, die zurückgegebenen Werte ähneln denen, die in der folgenden Tabelle aufgeführt sind.

|Value |Client |
|---|---|
|https://[org].crm.dynamics.com|Modellgestützte Apps (online)|
|http(s)://[server]/[org]|Modell-angetriebene Apps (lokal)|
|http://localhost:2525|Modell-angetriebene Apps für Outlook mit Offlinezugriff im Offlinemodus|

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)





