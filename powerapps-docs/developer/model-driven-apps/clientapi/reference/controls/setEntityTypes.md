---
title: setEntityTypes (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 93154168-1e9f-4849-b4bb-be8804f86f81
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setentitytypes-client-api-reference"></a>setEntityTypes (Client-API-Referenz)



Legt die Typen von Entitäten fest, die im Suchsteuerelement zulässig sind.

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suchsteuerelement

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).setEntityTypes([entityLogicalNames]);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|entityLogicalNames|Zeichenfolgenarray|Ja|Die logischen Namen der Entitäten angeben, die im Suchen-Steuerelement zulässig sind.|

### <a name="related-topics"></a>Verwandte Themen

[getEntityTypes](getEntityTypes.md)

 


