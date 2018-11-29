---
title: form Context.ui.quickForms (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
description: Erfahren Sie mehr über das Verwenden modellgestützten Apps mithilfe von Client-API.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a04043de-3497-433a-ae73-4101806dd931
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextuiquickforms-client-api-reference"></a>formContext.ui.quickForms (Client-API-Referenz)



Bietet Methoden für den Zugriff auf alle Steuerelemente für die Schnellansicht und die zugehörigen modellgestützten Apps-Formulare, wenn sie das neue Formularanpassungsmodul verwenden (auch als "Turbo-Formulare" bezeichnet). Ein Steuerelement für die Schnellansicht ist ein Schnellansichtsformular in modellgesteuerten Apps, mit dem Sie die Informationen über einen verknüpften Entitätsdatensatz im Hauptformular anzeigen können. Daten in der zugehörigen Steuerelementen in einem Steuerelement für die Schnellansicht können nicht bearbeitet werden.

Die **quickForms**-Sammlung bietet Zugriff allen Steuerelementen für die Schnellansicht in einem Formular und sichert die Standardverfahren der Sammlungen. Siehe [Sammlungen](collections.md) für Informationen zu den Sammlungsmethoden. 

Sie können ein Steuerelement für die Schnellansicht in der **quickForms**-Sammlung mithilfe der [get](collections/get.md)-Methode abrufen, indem der Indexwert (ganze Zahl) oder der Name (Zeichenfolge) für die Instanz des Steuerelements für die Schnellansicht als Argument angegeben wird.

`quickViewControl = formContext.ui.quickForms.get(arg)`


## <a name="quick-form-control-methods"></a>Schnellerfassungsformularsteuermethoden

|Name|Beschreibung|
|--|--|
|[getControl](formcontext-ui-quickForms/getControlType.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getControl-description.md](formcontext-ui-quickForms/includes/getControl-description.md)]|
|[getControlType](formcontext-ui-quickForms/getControlType.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getControlType-description.md](formcontext-ui-quickForms/includes/getControlType-description.md)]|
|[getDisabled](formcontext-ui-quickForms/getDisabled.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getDisabled-description.md](formcontext-ui-quickForms/includes/getDisabled-description.md)]|
|[getLabel](formcontext-ui-quickForms/getLabel.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getLabel-description.md](formcontext-ui-quickForms/includes/getLabel-description.md)]|
|[getName](formcontext-ui-quickForms/getName.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getName-description.md](formcontext-ui-quickForms/includes/getName-description.md)]|
|[getParent](formcontext-ui-quickForms/getParent.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getParent-description.md](formcontext-ui-quickForms/includes/getParent-description.md)]|
|[getVisible](formcontext-ui-quickForms/getVisible.md)|[!INCLUDE[formcontext-ui-quickForms/includes/getVisible-description.md](formcontext-ui-quickForms/includes/getVisible-description.md)]|
|[isLoaded](formcontext-ui-quickForms/isLoaded.md)|[!INCLUDE[formcontext-ui-quickForms/includes/isLoaded-description.md](formcontext-ui-quickForms/includes/isLoaded-description.md)]|
|[Aktualisieren](formcontext-ui-quickForms/refresh.md)|[!INCLUDE[formcontext-ui-quickForms/includes/refresh-description.md](formcontext-ui-quickForms/includes/refresh-description.md)]|
|[setDisabled](formcontext-ui-quickForms/setDisabled.md)|[!INCLUDE[formcontext-ui-quickForms/includes/setDisabled-description.md](formcontext-ui-quickForms/includes/setDisabled-description.md)]|
|[setFocus](formcontext-ui-quickForms/setFocus.md)|[!INCLUDE[formcontext-ui-quickForms/includes/setFocus-description.md](formcontext-ui-quickForms/includes/setFocus-description.md)]|
|[setLabel](formcontext-ui-quickForms/setLabel.md)|[!INCLUDE[formcontext-ui-quickForms/includes/setLabel-description.md](formcontext-ui-quickForms/includes/setLabel-description.md)]|
|[setVisible](formcontext-ui-quickForms/setVisible.md)|[!INCLUDE[formcontext-ui-quickForms/includes/setVisible-description.md](formcontext-ui-quickForms/includes/setVisible-description.md)]|


### <a name="related-topics"></a>Verwandte Themen

[formContext.ui](formContext-ui.md)