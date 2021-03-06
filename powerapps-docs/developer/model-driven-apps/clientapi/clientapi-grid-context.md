---
title: Client API-Rasterkontext in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: conceptual
applies_to:
- Dynamics 365 (online)
ms.assetid: f884d7d4-31e6-4080-acd9-493e81e6b278
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d7e842fdfca982bbe552d95a2b4ada1ff499aa76
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115886"
---
# <a name="client-api-grid-context"></a>Rasterkontext der Client-API

Raster präsentieren Daten in einem tabellarischen Format. Raster können das gesamte Formular einschließen oder eines der Elemente in einem Formular sein; die letzteren werden als **Unterraster** bezeichnet.

Das Client-API-Rasterkontextobjekt bietet eine Referenz auf das Unterraster im Formular, für das der aktuelle Code ausgeführt wird. 

> [!NOTE]
> Das Abrufen des Kontexts eines Rasters (über das gesamte Formular) wird nur in Menübandbefehlen unterstützt. Weitere Informationen: [Formular- und Rasterkontext in Menübandaktionen](/powerapps/developer/model-driven-apps/pass-data-page-parameter-ribbon-actions#form-and-grid-context-in-ribbon-actions)

Verwenden Sie das [formContext](clientapi-form-context.md)-Objekt, um eine Instanz des Formulars zu erhalten, in dem Code ausgeführt wird, und die anschließend Unterrastersteuerelement im Formular anzuzeigen. Zum Beispiel, wenn Sie den Namen eines Unterrastersteuerelements kennen (beispielweise **Kontakte**-Unterraster im Standardfirmenformular), können Sie mithilfe des folgenden Code darauf zugreifen:

```JavaScript
function doSomething(executionContext) {
   var formContext = executionContext.getFormContext(); // get the form Context
   var gridContext = formContext.getControl("Contacts"); // get the grid context

   // Perform operations on the subgrid
}
```

## <a name="related-topics"></a>Verwandte Themen

[Formularkontext der Client-API](clientapi-form-context.md)<br/>
[Client-API-Ausführungskontext](clientapi-execution-context.md)<br/>
[Grundlegendes zum Client API-Objektmodell](understand-clientapi-object-model.md)<br/>
[Raster und Unterraster](reference/grids.md)

