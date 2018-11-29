---
title: getName (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
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
# <a name="getname-client-api-reference"></a>getName (Client-API-Referenz)



Gibt den Namen zurück, der dem Steuerelement zugewiesen ist.

>[!NOTE]
>Der Name, der einem Steuerelement zugewiesen wird, wird nicht bestimmt, bis das Formular geladen ist. Änderungen am Formular ändern ggf. den Namen, der einem angegebenen Steuerelement zugewiesen ist. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).getName();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Der Name des Steuerelements.

### <a name="related-topics"></a>Verwandte Themen

[Steuerelemente](../controls.md)

