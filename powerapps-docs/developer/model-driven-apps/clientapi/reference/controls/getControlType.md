---
title: getControlType (Client-API-Referenz) in modellgestützten Apps für Dynamics 365| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcontroltype-client-api-reference"></a>getControlType (Client-API-Referenz)



Gibt einen Wert zurück, der Steuerelemente kategorisiert.

## <a name="control-types-supported"></a>Unterstützte Steuerelementtypen

Alle

## <a name="syntax"></a>Syntax

`getControl(arg).getControlType();`

**Rückgabewert**:

**Typ:**: Zeichenfolge

|Rückgabewert |Beschreibung|
|--|--|
|standard|Ein Standardsteuerelement|
|IFrame|Ein IFRAME-Steuerelement|
|kbsearch|Ein Suchsteuerelement für die Wissensdatenbank|
|Suche|Ein Suchsteuerelement|
|multiselectoptionset|Ein Mehrfachauswahl-Optionssatzsteuerelement|
|Hinweise|Ein Hinweis-Steuerelement|
|optionset|Ein Optionssatz-Steuerelement|
|quickform | Ein [Schnellansicht](../formContext-ui-quickForms.md)-Steuerelement|
|subgrid | Ein [Unterraster](../grids.md)-Steuerelement|
|timercontrol | Ein Zeitgeber-Steuerelement|
|timelinewall | Ein Zeitachsen--Steuerelement (für Unified Interface)|
|webresource | Ein Webressourcen-Steuerelement|
|customcontrol: \<*namespace*>.\<*name*> | Ein benutzerdefiniertes Dataset-Steuerelement für mobile Dynamics 365-Clients (Smartphones und Tablets).|
|customsubgrid:\<*namespace*>.\<*name*> | Ein benutzerdefiniertes Dataset-Steuerelement für mobile Dynamics 365-Clients (Smartphones und Tablets).|

### <a name="related-topics"></a>Verwandte Themen

[Steuerelemente](../controls.md)

[getControl](getcontrol.md)


