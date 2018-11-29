---
title: getControlType (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 72d6c761-bcc7-4de6-b73f-5f2833297825
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



[!INCLUDE[./includes/getControlType-description.md](./includes/getControlType-description.md)]

## <a name="syntax"></a>Syntax

`quickViewControl.getControlType();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge.

**Beschreibung**: Für ein Steuerelement für die Schnellansicht gibt die Methode "quickform" zurück. 

Für ein zugehöriges Steuerelement in einem Steuerelement für die Schnellansicht gibt die Methode die tatsächliche Kategorie des Steuerelements zurück. Weitere Informationen über andere mögliche Rückgabewerte finden Sie unter [getControlType](../controls/getControlType.md)..

### <a name="related-topics"></a>Verwandte Themen

[formContext.ui.quickForms](../formContext-ui-quickForms.md)