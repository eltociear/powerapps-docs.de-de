---
title: openWebResource (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 798dc921-1e80-42bc-b8ca-2056728bcba4
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openwebresource-client-api-reference"></a>openWebResource (Client-API-Referenz)



[!INCLUDE[./includes/openWebResource-description.md](./includes/openWebResource-description.md)]

## <a name="syntax"></a>Syntax

`Xrm.Navigation.openWebResource(webResourceName,windowOptions,data)`

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|webResourceName|String|Ja|Name der zu öffnenden HTML-Webressource.|
|windowOptions|Objekt|No|Fensteroptionen zum Öffnen der Webressource. Das Objekt hat die folgenden Attribute:<br/>- **Höhe**: (Optional) Zahl. Höhe des zu öffnenden Fensters in Pixeln.<br/>- **openInNewWindow**: Boolescher Wert. Gibt an, ob die Webressource in einem neuen Fenster geöffnet wird.<br/>- **Breite**: (Optional) Zahl. Breite des zu öffnenden Fensters in Pixeln.|
|-Daten|String|No|Daten, die in den Datenparameter übergeben werden.|

## <a name="remarks"></a>Anmerkungen

Sie müssen diese Methode verwenden, um Webressourcen anstelle der veralteten [Xrm.Utility.openWebResource](https://msdn.microsoft.com/library/jj602956.aspx#BKMK_OpenWebResource)-Methode anzuzeigen.

Eine HTML-Webressource kann die Parameterwerte akzeptieren, die in [Durchlaufparameter an HTML-Webressourcen übergeben](../../../webpage-html-web-resources.md#BKMK_PassingParametersToWebResources) beschrieben werden. Diese Funktion dient nur zum Übergeben des optionalen Datenparameters. Um Werte für weitere gültige Parameter zu übergeben, müssen Sie sie an den `webResourceName`-Parameter anfügen.

> [!NOTE]
> Das **Xrm**-Objekt ist in HTML-Webressourcen nicht verfügbar. Daher werden Skripts, die `Xrm.*`-Methoden enthalten in HTML-Webressourcen nicht unterstützt. `parent.Xrm.*` funktioniert, wenn die HTML-Webressource in einem Formularcontainer geladen wird. Für andere Orte, wie etwa das Laden einer HTML-Webressource als Bestandteil der Siteübersicht, funktioniert `parent.Xrm.*` allerdings nicht. Weitere Informationen: [GetGlobalContext Funktion und ClientGlobalContext.js.aspx](../GetGlobalContext-ClientGlobalContext.js.aspx.md)



## <a name="examples"></a>Beispiele

- Öffnen einer HTML-Webressource namens "new_webResource.htm":
   
   `Xrm.Navigation.openWebResource("new_webResource.htm");`

- Öffnen Sie eine HTML-Webressource, indem Sie die windowOptions einstellen:

  ```
  var windowOptions = { openInNewWindow: true, height: 400, width: 400 }
  Xrm.Navigation.openWebResource("new_webResource.htm",windowOptions);
  ```

- Öffnen einer HTML-Webressource und ein einzelnes Element von Daten für den `data`-Parameter

  `Xrm.Navigation.openWebResource("new_webResource.htm",null,"dataItemValue");`

 ### <a name="related-topics"></a>Verwandte Themen

[Xrm.Navigation](../xrm-navigation.md)

