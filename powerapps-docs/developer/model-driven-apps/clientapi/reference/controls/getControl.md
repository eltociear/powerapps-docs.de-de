---
title: getControl (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 34715e1f-35c0-4b7f-971e-e0a6518f0722
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcontrol-client-api-reference"></a>getControl (Client-API-Referenz)



Ruft ein Steuerelement im Formular auf. 

## <a name="syntax"></a>Syntax

`formContext.getControl(arg);`

Die **formContext.getControl (arg)**-Verknüpfungsmethode, um auf **formContext.ui.controls.get** zuzugreifen.

## <a name="parameter"></a>Parameter

**arg**: Optional. Sie können auf ein Steuerelement in einem Formular zugreifen, indem Sie das Argument entweder als **Name** oder **Indexwert** des Steuerelements in einem Formular übergeben. Beispiel: `formContext.getControl("firstname")` oder `formContext.getControl(0)`.


## <a name="return-value"></a>Rückgabewert

**Typ**: Objekt- oder Objektsammlung.

**Typ:** Objekt, wenn Sie die Methode mit Parameter verwenden, Objektsammlung, wenn Sie die Methode ohne Parameter verwenden.



### <a name="related-topics"></a>Verwandte Themen

[formContext](../../clientapi-form-Context.md)



