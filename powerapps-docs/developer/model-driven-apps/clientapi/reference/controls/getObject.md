---
title: getIObjecct (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: ad68d177-3715-468e-b4af-8cf9b3c77799
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getobject-client-api-reference"></a>getObject (Client-API-Referenz)



Gibt das Objekt im Formular zurück, das ein IFrame oder eine Webressource darstellt. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

IFrame, Webressource

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).getObject();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Objekt.

**Beschreibung**: Objekt hängt ab vom Typ des Steuerelements:
- Ein IFRAME gibt das [IFrame](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)-Element vom Dokumentobjektmodell (DOM) zurück.
- Eine Silverlight-Webressource gibt das [Objekt](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object)-Element vom DOM zurück, das das eingebettete Silverlight-Plug-In darstellt.



