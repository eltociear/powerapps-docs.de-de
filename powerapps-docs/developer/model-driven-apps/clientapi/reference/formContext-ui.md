---
title: formContext.ui (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
description: Erfahren Sie mehr über das Verwenden modellgestützten Apps mithilfe von Client-API.
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: f93e0e21-f911-4681-81b0-82ccf98ee28b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextui-client-api-reference"></a>formContext.ui (Client-API-Referenz)



Stellt Eigenschaften und Methoden zum Abrufen von Informationen zur Benutzeroberfläche (UI) sowie Sammlungen für verschiedene Unterkomponenten des Formulars bereit.

![formContext UI-Objektmodell](../../media/ClientAPI-formContext-ui-Model.png)

## <a name="properties"></a>Eigenschaften

|Name|Beschreibung|
|--|--|
|Steuerelemente|Sammlung aller Steuerelemente auf der Seite. Siehe [Sammlungen](collections.md) für Informationen zu den Sammlungen und [Steuerelemente](controls.md) für Informationen zu den Steuerobjekten in der Sammlung.|
|formSelector|Verwenden Sie die formSelector.getCurrentItem-Methode, über die Informationen zum gerade verwendeten Formular abzurufen. Verwenden Sie die formSelector.items-Sammlung zur Rückmeldung für alle Formulare, die für die Benutzer verfügbar sind. **formSelector** ist für Microsoft Dynamics 365 für Tablets nicht verfügbar.|
|Navigation|Eine Sammlung aller Navigationselemente auf der Seite. Siehe [Sammlungen](collections.md) für Informationen zu den Sammlungsmethoden und [formContext.ui.navigation-Element](formContext-ui-navigation.md) für Informationen zu den Elementen in der Sammlung. **navigation** ist für Microsoft Dynamics 365 für Tablets nicht verfügbar.|
|Prozess|Stellt Objekte und Methoden zum Interagieren mit den Geschäftsprozessflusssteuerung in einem Formular bereit.<br/>Weitere Informationen: [formContext.ui.process](formContext-ui-process.md)|
|quickForms|Eine Sammlung aller Steuerelemente für die Schnellansicht in einem Formular mithilfe des neuen Formularrenderingmoduls (auch als "Turbo-Formulare" bezeichnet).<br/>Weitere Informationen: [formContext.ui. quickForms](formContext-ui-quickforms.md)|
|Registerkarten|Eine Sammlung aller Registerkarten auf der Seite.<br/>Siehe [Sammlungen](collections.md) für Informationen zu den Sammlungsmethoden und [formContext.ui-Registerkarte](formContext-ui-tabs.md) für Informationen zu den Elementen in der Sammlung.|


## <a name="methods"></a>Methoden 

|Name|Beschreibung|
|--|--|
|[addOnLoad](formContext-ui/addOnload.md)|[!INCLUDE[formContext-ui/includes/addOnLoad-description.md](formContext-ui/includes/addOnLoad-description.md)]|
|[clearFormNotification](formContext-ui/clearFormNotification.md)|[!INCLUDE[formContext-ui/includes/clearFormNotification-description.md](formContext-ui/includes/clearFormNotification-description.md)]|
|[Schließen](formContext-ui/close.md)|[!INCLUDE[formContext-ui/includes/close-description.md](formContext-ui/includes/close-description.md)]|
|[getFormType](formContext-ui/getFormType.md)|[!INCLUDE[formContext-ui/includes/getFormType-description.md](formContext-ui/includes/getFormType-description.md)]|
|[getViewPortHeight](formContext-ui/getViewPortHeight.md)|[!INCLUDE[formContext-ui/includes/getViewPortHeight-description.md](formContext-ui/includes/getViewPortHeight-description.md)]|
|[getViewPortWidth](formContext-ui/getViewPortWidth.md)|[!INCLUDE[formContext-ui/includes/getViewPortWidth-description.md](formContext-ui/includes/getViewPortWidth-description.md)]|
|[refreshRibbon](formContext-ui/refreshRibbon.md)|[!INCLUDE[formContext-ui/includes/refreshRibbon-description.md](formContext-ui/includes/refreshRibbon-description.md)]|
|[removeOnLoad](formContext-ui/removeOnLoad.md)|[!INCLUDE[formContext-ui/includes/removeOnLoad-description.md](formContext-ui/includes/removeOnLoad-description.md)]|
|[setFormEntityName](formContext-ui/setFormEntityName.md)|[!INCLUDE[formContext-ui/includes/setFormEntityName-description.md](formContext-ui/includes/setFormEntityName-description.md)]|
|[setFormNotification](formContext-ui/setFormNotification.md)|[!INCLUDE[formContext-ui/includes/setFormNotification-description.md](formContext-ui/includes/setFormNotification-description.md)]|



### <a name="related-topics"></a>Verwandte Themen

[formContext](../clientapi-form-context.md)




