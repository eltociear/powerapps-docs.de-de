---
title: GetGlobalContext-Funktion und ClientGlobalContext.js.aspx in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: conceptual
applies_to:
  - Dynamics 365 (online)
ms.assetid: b58e6173-e3cd-4a3b-b39a-334c295503ec
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getglobalcontext-function-and-clientglobalcontextjsaspx-client-api-reference"></a>GetGlobalContext function und ClientGlobalContext.js.aspx (clientseitige API-Referenz)



Verwenden Sie die Funktion **GetGlobalContext** bei der Programmierung mit [Webressourcen](../../web-resources.md), um zu globalen Kontextinformationen wie Informationen zum Kunden, der Organisation oder dem Benutzer für Ihre modellgestützte App-Instanz Zugriff zu erhalten. 

Um die **GetGlobalContext**-Funktion in der HTML-Webressource zu erhalten,schließen Sie einen Verweis auf **ClientGlobalContext.js.aspx** ein.

> [!NOTE]
> Durch Einschließen eines Verweises auf **ClientGlobalContext.js.aspx** macht das **Xrm**-Objekt nicht in HTML-Webressourcen verfügbar. Daher werden Skripts, die `Xrm.*`-Methoden enthalten in HTML-Webressourcen nicht unterstützt. `parent.Xrm.*` funktioniert, wenn die HTML-Webressource in einem Formularcontainer geladen wird. Für andere Orte, wie etwa das Laden einer HTML-Webressource als Bestandteil der Siteübersicht, funktioniert `parent.Xrm.*` allerdings nicht.

## <a name="getglobalcontext-function"></a>GetGlobalContext-Funktion

Die Funktion **GetGlobalContext** gibt das gleiche Kontextobjekt zurück wie die **Xrm.Utility.getGlobalContext**-Methode, die impliziert, dass das Kontextobjekt die gleichen Eigenschaften und Methoden hat wie für **Xrm.Utility.getGlobalContext** verfügbar. Weitere Informationen: Xrm.Utility.[getGlobalContext](Xrm-Utility/getGlobalContext.md)

## <a name="clientglobalcontextjsaspx"></a>ClientGlobalContext.js.aspx

Sie müssen einen Verweis auf der **ClientGlobalContext.js.aspx** Seite einschließen, die am Stamm des Webressourceverzeichnisses vorhanden ist, um **GetGlobalContext** zu verwenden.

- Wenn Sie keine Schrägstriche im HTML-Webressourcenamen verwenden, um eine Ordnerstruktur zu simulieren, können Sie das Skript auf der Seite mit diesem Skriptelements einschließen:  Beispiel:

    ```HTML
    <head>
      <title>HTML Web Resource</title>
      <script src="ClientGlobalContext.js.aspx" type="text/javascript" ></script>
      
    </head>
    ```
- Wenn Sie umgekehrte Schrägstriche nicht in den HTML-Webressourcenamen verwenden, um eine Verzeichnisstruktur zu simulieren, müssen Sie dies im Skriptelement wiedergeben. Das folgende Beispiel ist für eine HTML-Webressource namens **sdk_/Contoso.htm** und eine -Webressource, die **ssdk_/Scripts/ContosoScript.js** mit einer CSS-Webressource namens **sdk_/Styles/ContosoStyles.css**.

    ```HTML
    <head>
      <title>HTML Web Resource</title>
      <script src="../ClientGlobalContext.js.aspx" type="text/javascript" ></script>

      <script src="Scripts/ContosoScript.js" type="text/javascript"></script>
      <link href="Styles/ContosoStyles.css" rel="stylesheet" type="text/css" />
    </head>

    ```

> [!NOTE]
> Das Verwenden eines relativen Pfads einschließlich des WebResourcen-Stammverzeichnisses, beispielsweise  /WebResources/ClientGlobalContext.js.aspx, wird nicht empfohlen, da es dazu führen kann, dass die Seite eine Organisationskontext in einer Umgebung mit mehreren Iinstanzen verlieren kann.

Die **ClientGlobalContext.js.aspx**-Seite enthält mehrere globale Ereignishandler. Diese Ereignishandler brechen die Ereignisse [onselectstart](https://developer.mozilla.org/en-US/docs/Web/Events/selectstart), [contextmenu](https://developer.mozilla.org/en-US/docs/Web/Events/contextmenu) und [ondragstart](https://developer.mozilla.org/en-US/docs/Web/Events/dragstart) ab. 

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility.getGlobalContext](Xrm-Utility/getGlobalContext.md)

[Grundlegendes zum Client API-Objektmodell](../understand-clientapi-object-model.md) 

[Webressourcen für modellgesteuerte Apps](../../web-resources.md)

