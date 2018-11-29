---
title: reflow (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 6833e4ea-70fc-4ee0-8aab-68cc55e21444
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="reflow-client-api-reference"></a>reflow (Client-API-Referenz)



[!INCLUDE[./includes/reflow-description.md](./includes/reflow-description.md)]

## <a name="syntax"></a>Syntax

`formContext.ui.process.reflow(updateUI, parentStage, nextStage);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|updateUI|Boolean|Ja|Geben Sie **true** an, um die Benutzeroberfläche des Prozesssteuerelements zu aktualisieren; andernfalls **false**.|
|parentStage|String|Ja|Geben Sie die ID der übergeordneten Phase im GUID-Format an.|
|nextStage|String|Ja|Geben Sie die ID der nächsten Phase im GUID-Format an.|

### <a name="related-topics"></a>Verwandte Themen

[formContext.ui.process](../formContext-ui-process.md)



