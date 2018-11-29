---
title: setDefaultView (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8c918cd4-d0ce-45e5-91a3-1addf11258c7
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setdefaultview-client-api-reference"></a>setDefaultView (Client-API-Referenz)



Legt die Standardansicht für das Suchsteuerelementdialogfeld fest.

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suche

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).setDefaultView(viewId);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|viewId|String|Ja|Die ID der Ansicht, die als Standardansicht festgelegt wird.|

## <a name="example"></a>Beispiel

Diese **setDefaultViewSample**-Funktion legt das **account**-Formular für die Suche nach dem primären Kontakt zu der Ansicht **Meine aktiven Kontakte** fest.

```JavaScript
function setDefaultViewSample(executionContext) {
    var formContext = executionContext.getFormContext();
    formContext.getControl("primarycontactid").setDefaultView("{00000000-0000-0000-00AA-000010001003}");
}
```

### <a name="related-topics"></a>Verwandte Themen

[getDefaultView](getDefaultView.md) 


