---
title: form Context.ui.sections (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
description: Erfahren Sie mehr über das Verwenden modellgestützten Apps mithilfe von Client-API.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e362dfb2-cb64-49f5-b3d4-d77e813325ca
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextuisections-client-api-reference"></a>formContext.ui.sections (Client-API-Referenz)



Ein Abschnitt enthält Methoden zum Verwalten seiner Darstellung und zum Zugreifen auf die Registerkarte, die den Abschnitt umfasst.

Sie können ein Abschnittsobjekt (z. B. **sectionObj**) abrufen, indem Sie folgenden Beispielcode verwenden:

```JavaScript
var tabObj = formContext.ui.tabs.get(arg);
var sectionObj = tabObj.sections.get(arg);
```

## <a name="properties"></a>Eigenschaften

- **Controls**: Die Abschnittssteuerelementsammlung bietet Zugriff auf die Steuerelemente in einem Abschnitt. Siehe [Sammlungen (Client-API-Referenz)](collections.md) für Informationen zu den Methoden, die durch Sammlungen verfügbar sind. Siehe [Steuerelemente (Client-API-Referenz)](controls.md) für Informationen zu den Eigenschaften und Methoden, die von den Objekten in dieser Sammlung verfügbar gemacht werden.


## <a name="methods"></a>Methoden

|Name | Beschreibung |
|--|--|
|[getLabel](formcontext-ui-sections/getLabel.md)|[!INCLUDE[formcontext-ui-sections/includes/getLabel-description.md](formcontext-ui-sections/includes/getLabel-description.md)]|
|[getName](formcontext-ui-sections/getName.md)|[!INCLUDE[formcontext-ui-sections/includes/getName-description.md](formcontext-ui-sections/includes/getName-description.md)]|
|[getParent](formcontext-ui-sections/getParent.md)|[!INCLUDE[formcontext-ui-sections/includes/getParent-description.md](formcontext-ui-sections/includes/getParent-description.md)]|
|[getVisible](formcontext-ui-sections/getVisible.md)|[!INCLUDE[formcontext-ui-sections/includes/getVisible-description.md](formcontext-ui-sections/includes/getVisible-description.md)]|
|[setLabel](formcontext-ui-sections/setLabel.md)|[!INCLUDE[formcontext-ui-sections/includes/setLabel-description.md](formcontext-ui-sections/includes/setLabel-description.md)]|
|[setVisible](formcontext-ui-sections/setVisible.md)|[!INCLUDE[formcontext-ui-sections/includes/setVisible-description.md](formcontext-ui-sections/includes/setVisible-description.md)]|

### <a name="related-topics"></a>Verwandte Themen

[formcontext.ui.tabs](formcontext-ui-tabs.md)

[formContext](../clientapi-form-context.md)