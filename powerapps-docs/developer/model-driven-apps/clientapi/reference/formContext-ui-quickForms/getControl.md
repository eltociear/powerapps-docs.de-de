---
title: getControl (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 57eb6b4b-90c1-4d56-b4b0-a7160af17f8f
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



[!INCLUDE[./includes/getControl-description.md](./includes/getControl-description.md)]

## <a name="syntax"></a>Syntax

`quickViewControl.getControl(arg);`

## <a name="parameter"></a>Parameter

**arg**: Optional. Sie können auf ein einzelnes Steuerelement in der zugehörigen Sammlung von Steuerelementen zugreifen, indem Sie das Argument entweder als Name oder zugehörigen Indexwert des Steuerelements an ein Steuerelement für die Schnellansicht übergeben. Beispiel: `quickViewControl.getControl("firstname")` oder `quickViewControl.getControl(0)`.


## <a name="return-value"></a>Rückgabewert

**Typ**: Objekt- oder Objektsammlung.

**Typ:** Objekt, wenn Sie die Methode mit Parameter verwenden, Objektsammlung, wenn Sie die Methode ohne Parameter verwenden.

## <a name="remarks"></a>Anmerkungen

Nachdem Sie ein zugehöriges Steuerelement in einem Steuerelement für die Schnellansicht abgerufen haben, können Sie eine der Methoden verwenden, die für ein Steuerelement in modellgesteuerten Apps im zugehörigen Steuerelement unterstützt werden, das die zugehörigen Steuerelementdaten nicht ändert. Dies liegt daran, dass zugehörige Steuerelemente in einem Steuerelement für die Schnellansicht schreibgeschützt sind. So können Sie beispielsweise Folgendes verwenden: 

`quickViewControl.getControl(0).getAttribute()` 

Weitere Informationen über die Methoden, die für ein Steuerelement unterstützt werden, finden Sie unter [Steuerelemente](../controls.md).

>[!IMPORTANT]
>Das [getAttribute](../controls/getAttribute.md) oder eine beliebige Datenmethode in einem zugehörigen Steuerelement funktionieren möglicherweise nicht mit dem Hauptformular [OnLoad](../events/form-onload.md), da das gebundene Schnellansichtsformular beim Laden des Hauptformulars möglicherweise nicht vollständig geladen wurde. Sie müssen die [isLoaded](isLoaded.md)-Methode für die Instanz des Steuerelements für die Schnellansicht verwenden, um zu ermitteln, ob das gebundene Schnellansichtsformular vollständig geladen wurde. 

>Die Art des Abrufens der zugehörigen Steuerelemente in einem Steuerelement für die Schnellansicht auf Formularen unterscheidet sich beim neuen Formularrenderingmodul von den Vorgängerformularen. Wenn Sie daher Vorgängerformulare verwenden und Code für zugehörige Steuerelemente in einem Steuerelement für die Schnellansicht haben, müssen Sie Ihren Code aktualisieren, wenn Sie sich entscheiden, das neue Formularrenderingmodul zu verwenden.

### <a name="related-topics"></a>Verwandte Themen

[formContext.ui.quickForms](../formContext-ui-quickForms.md)



