---
title: refreshRibbon (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: dbd43d7b-c9b0-4ca5-943d-dd813d3bb049
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="refreshribbon-client-api-reference"></a>refreshRibbon (Client-API-Referenz)



[!INCLUDE[./includes/refreshRibbon-description.md](./includes/refreshRibbon-description.md)]

## <a name="syntax"></a>Syntax

`formContext.ui.refreshRibbon(refreshAll);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|refreshAll|Boolean|No|Gibt an, ob alle Menübandbefehlleisten auf der aktuellen Seite aktualisiert werden. Wenn Sie nur **false** angeben, wird nur die Menübandbefehlleiste auf Seitenebene aktualisiert. Wird dieser Parameter nicht angegeben, wird **false** als Standardwert übergeben.|

## <a name="remarks"></a>Anmerkungen

 Diese Funktion wird normalerweise verwendet, wenn ein Menüband `<EnableRule>` (RibbonDiffXml) von einem Wert im Formular abhängt. Nachdem der Code sich ändert, der von einer Regel verwendet wird, verwenden Sie diese Methode, um das Menüband zu zwingen, die Daten im Formular neu zu bewerten, damit die Regel angewendet werden kann.

### <a name="related-topics"></a>Verwandte Themen

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

