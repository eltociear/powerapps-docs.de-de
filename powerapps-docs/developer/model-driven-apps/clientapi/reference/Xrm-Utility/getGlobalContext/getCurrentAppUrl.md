---
title: getCurrentAppUrl (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
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
# <a name="getcurrentappurl-client-api-reference"></a>getCurrentAppUrl (Client-API-Referenz)



Gibt die URL der aktuellen Geschäfts-API in modellgetriebenen Apps zurück.

## <a name="syntax"></a>Syntax

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getCurrentAppUrl();
``` 

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: URL der aktuellen Unternehmens-App. Mögliche Rückgabewerte:

|Value |Client |
|---|---|
|https://[org].crm.dynamics.com/main.aspx?appid=[GUID]|Modellgestützte Apps (online)|
|https://[server]/[org]/main.aspx?appid=[GUID]|Modell-angetriebene Apps (lokal)|

### <a name="related-topics"></a>Verwandte Themen

[Erstellen, Verwalten und Veröffentlichen von modellgesteuerten Apps mithilfe von Code](../../../../create-manage-model-driven-apps-using-code.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md) 



