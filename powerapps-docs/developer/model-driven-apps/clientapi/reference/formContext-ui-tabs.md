---
title: form Context.ui.tabs (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
description: Erfahren Sie mehr über das Verwenden modellgestützten Apps mithilfe von Client-API.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1888a882-7dfc-41a8-9bb4-d693d6046666
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextuitabs-client-api-reference"></a>formContext.ui.tabs (Client-API-Referenz)



Eine Registerkarte ist eine Gruppe von Abschnitten auf einer Seite. Sie enthält Eigenschaften und Methoden, um den Zugriff auf Registerkarten und Abschnitte der Registerkarte durch die Abschnittssammlung zu bearbeiten.

Sie können ein Registerkartenobjekt (z. B. **tabObj**) abrufen, indem Sie folgenden Beispielcode verwenden:

```JavaScript
var tabObj = formContext.ui.tabs.get(arg);
```

## <a name="properties"></a>Eigenschaften

- **Abschnitte**: Die Abschnittssammlung bietet Zugriff auf die Abschnitte in der Registerkarte. Siehe [Sammlungen (Client-API-Referenz)](collections.md) für Informationen zu Methoden, um auf die Abschnitte in der Sammlung zugreifen. Siee [formContext.ui-Abschnitt](formContext-ui-sections.md) für Informationen zu den Eigenschaften und Mhethoden, die von den Abschnittsobjekten in dieser Sammlung verfügbar gemacht werden.

## <a name="methods"></a>Methoden

|Name | Beschreibung |
|--|--|
|[addTabStateChange](formcontext-ui-tabs/addTabStateChange.md)|[!INCLUDE[formcontext-ui-tabs/includes/addTabStateChange-description.md](formcontext-ui-tabs/includes/addTabStateChange-description.md)]|
|[getDisplayState](formcontext-ui-tabs/getDisplayState.md)|[!INCLUDE[formcontext-ui-tabs/includes/getDisplayState-description.md](formcontext-ui-tabs/includes/getDisplayState-description.md)]|
|[getLabel](formcontext-ui-tabs/getLabel.md)|[!INCLUDE[formcontext-ui-tabs/includes/getLabel-description.md](formcontext-ui-tabs/includes/getLabel-description.md)]|
|[getName](formcontext-ui-tabs/getName.md)|[!INCLUDE[formcontext-ui-tabs/includes/getName-description.md](formcontext-ui-tabs/includes/getName-description.md)]|
|[getParent](formcontext-ui-tabs/getParent.md)|[!INCLUDE[formcontext-ui-tabs/includes/getParent-description.md](formcontext-ui-tabs/includes/getParent-description.md)]|
|[getVisible](formcontext-ui-tabs/getVisible.md)|[!INCLUDE[formcontext-ui-tabs/includes/getVisible-description.md](formcontext-ui-tabs/includes/getVisible-description.md)]|
|[removeTabStateChange](formcontext-ui-tabs/removeTabStateChange.md)|[!INCLUDE[formcontext-ui-tabs/includes/removeTabStateChange-description.md](formcontext-ui-tabs/includes/removeTabStateChange-description.md)]|
|[setDisplayState](formcontext-ui-tabs/setDisplayState.md)|[!INCLUDE[formcontext-ui-tabs/includes/setDisplayState-description.md](formcontext-ui-tabs/includes/setDisplayState-description.md)]|
|[setFocus](formcontext-ui-tabs/setFocus.md)|[!INCLUDE[formcontext-ui-tabs/includes/setFocus-description.md](formcontext-ui-tabs/includes/setFocus-description.md)]|
|[setLabel](formcontext-ui-tabs/setLabel.md)|[!INCLUDE[formcontext-ui-tabs/includes/setLabel-description.md](formcontext-ui-tabs/includes/setLabel-description.md)]|
|[setVisible](formcontext-ui-tabs/setVisible.md)|[!INCLUDE[formcontext-ui-tabs/includes/setVisible-description.md](formcontext-ui-tabs/includes/setVisible-description.md)]|

### <a name="related-topics"></a>Verwandte Themen

[formcontext.ui.tabs](formcontext-ui-tabs.md)

[formContext](../clientapi-form-context.md)

