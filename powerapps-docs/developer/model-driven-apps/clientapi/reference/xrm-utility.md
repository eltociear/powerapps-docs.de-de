---
title: Xrm.Utility (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c044f7b8-7803-45fb-b99c-df01800c3b2a
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="xrmutility-client-api-reference"></a>Xrm.Utility (Client-API-Referenz)



Stellt einen Container für nützliche Methoden bereit.

## <a name="methods"></a>Methoden 

|Methode | Beschreibung | 
| ------------- |-------------| 
|[closeProgressIndicator](xrm-utility/closeProgressIndicator.md) |[!INCLUDE[./xrm-utility/includes/closeProgressIndicator-description.md](./xrm-utility/includes/closeProgressIndicator-description.md)]|
|[getAllowedStatusTransitions](xrm-utility/getAllowedStatusTransitions.md) |[!INCLUDE[./xrm-utility/includes/getAllowedStatusTransitions-description.md](./xrm-utility/includes/getAllowedStatusTransitions-description.md)]|
|[getEntityMetadata](xrm-utility/getEntityMetadata.md) |[!INCLUDE[./xrm-utility/includes/getEntityMetadata-description.md](./xrm-utility/includes/getEntityMetadata-description.md)]|
|[getGlobalContext](xrm-utility/getGlobalContext.md) |[!INCLUDE[./xrm-utility/includes/getGlobalContext-description.md](./xrm-utility/includes/getGlobalContext-description.md)]|
|[getLearningPathAttributeName](xrm-utility/getLearningPathAttributeName.md) |[!INCLUDE[./xrm-utility/includes/getLearningPathAttributeName-description.md](./xrm-utility/includes/getLearningPathAttributeName-description.md)]|
|[getResourceString](xrm-utility/getResourceString.md) |[!INCLUDE[./xrm-utility/includes/getResourceString-description.md](./xrm-utility/includes/getResourceString-description.md)]|
|[invokeProcessAction](xrm-utility/invokeProcessAction.md) |[!INCLUDE[./xrm-utility/includes/invokeProcessAction-description.md](./xrm-utility/includes/invokeProcessAction-description.md)]|
|[lookupObjects](xrm-utility/lookupObjects.md) |[!INCLUDE[./xrm-utility/includes/lookupObjects-description.md](./xrm-utility/includes/lookupObjects-description.md)]|
|[refreshParentGrid](xrm-utility/refreshParentGrid.md) |[!INCLUDE[./xrm-utility/includes/refreshParentGrid-description.md](./xrm-utility/includes/refreshParentGrid-description.md)]|
|[showProgressIndicator](xrm-utility/showProgressIndicator.md) |[!INCLUDE[./xrm-utility/includes/showProgressIndicator-description.md](./xrm-utility/includes/showProgressIndicator-description.md)]|

## <a name="deprecated-methods"></a>Veraltete Methoden

Die folgende Tabelle enthält die neuen Methoden, die Sie anstelle der veralteten Methoden im **Xrm.Utility**-Namespace verwenden sollten. Diese Methoden sind seit v9.0 veraltet.

|Veraltete Methode | Neue zu verwendende Methode | 
| ------------- |-------------|
|[alertDialog](https://msdn.microsoft.com/library/jj602956.aspx#BKMK_alertDialog)|Xrm.Navigation.[openAlertDialog](Xrm-Navigation/openAlertDialog.md)|
|[confirmDialog](https://msdn.microsoft.com/library/jj602956.aspx#BKMK_confirmDialog)|Xrm.Navigation.[openConfirmDialog](Xrm-Navigation/openConfirmDialog.md)|
|[getBarcodeValue](https://msdn.microsoft.com/library/jj602956.aspx#BKMK_getBarcodeValue)|Xrm.Device.[getBarcodeValue](Xrm-Device/getBarcodeValue.md)|
|[getCurrentPosition](https://msdn.microsoft.com/library/jj602956.aspx#BKMK_getCurrentPosition)|Xrm.Device.[getCurrentPosition](Xrm-Device/getCurrentPosition.md)|
|[openEntityForm](https://msdn.microsoft.com/library/jj602956.aspx#BKMK_OpenEntityForm)|Xrm.Navigation.[openForm](Xrm-Navigation/openForm.md)|
|[openQuickCreate](https://msdn.microsoft.com/library/jj602956.aspx#BKMK_openQuickCreate)|Xrm.Navigation.[openForm](Xrm-Navigation/openForm.md)|
|[openWebResource](https://msdn.microsoft.com/library/jj602956.aspx#BKMK_OpenWebResource)|Xrm.Navigation.[openWebResource](Xrm-Navigation/openWebResource.md)|


### <a name="related-topics"></a>Verwandte Themen

[Client-API-Ausführungskontext](../clientapi-execution-context.md)

[Client-API-Xrm-Objekt](../clientapi-xrm.md)

[Client-API-Referenz](../reference.md)

[Veraltete Client-APIs](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated)

