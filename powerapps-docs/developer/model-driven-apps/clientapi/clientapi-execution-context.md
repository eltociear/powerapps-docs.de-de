---
title: Client API-Ausführung in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: conceptual
applies_to:
- Dynamics 365 (online)
ms.assetid: 1fcbf0fd-4e47-4352-a555-9315f7e57331
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 34fdb04b4151c0325a2d593753e76386793bacb3
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115894"
---
# <a name="client-api-execution-context"></a>Client-API-Ausführungskontext



Der Ausführungskontext definiert den Ereigniskontext, an dem Ihr Code ausgeführt wird. Der Ausführungskontext wird, wenn ein Ereignis für ein Formular oder Raster, die Sie in Ihrem Ereignishandler verwenden können, um die verschiedenen Aufgaben wie Bestimmen von [formContext](clientapi-form-context.md) oder [gridContext](clientapi-grid-context.md) oder dasselbe Ereignis zu verwalten, auftritt, übergeben. 

Der Ausführungskontext wird in eine der folgenden Weisen übergeben:

- **Definieren von Ereignishandlern mithilfe der Benutzerschnittstelle**: Der Ausführungskontext ist ein *optionaler* Parameter, der an eine JavaScript-Bibliotheksfunktion über einen Ereignishandler übergeben werden kann. Verwenden Sie die Option **Ausführungskontext als ersten Parameter übergeben** im **Handlereigenschaften** im Dialogfeld, während den Namen einer Funktion bestimmt wird, um den Ereignisausführungskontext zu übergeben. Der Ausführungskontext ist der erste Parameter, der an eine Funktion übergeben wird.<br/><br/>
![Ausführungskontext übergeben](../media/ClientAPI-PassExecutionContext.png)<br/><br/>

- **Bestimmen der Eventhandler mithilfe des Codes**: Der Ausführungskontext wird automatisch als den ersten Parameter an Funktionen, die den Code verwenden, übergeben. Eine Liste von Methoden, die verwendet werden können, um die Ereignishandler im Code zu definieren, finden Sie unter [Funktionen der Ereignisse mithilfe des Codes hinzufügen oder entfernen](events-forms-grids.md#add-or-remove-event-handler-function-to-event-using-code). 

Das Ausführungskontextobjekt bietet mehrere Methoden zum weiteren Arbeiten im Kontext. Weitere Informationen: [Ausführungskontext (Client-API-Referenz)](reference/execution-context.md)


### <a name="related-topics"></a>Verwandte Themen

 [Formularkontext der Client-API](clientapi-form-context.md)<br>
 [Rasterkontext der Client-API](clientapi-grid-context.md)<br>
 [Formular- und Rasterkontext in Menübandaktionen](../pass-data-page-parameter-ribbon-actions.md#form-and-grid-context-in-ribbon-actions)


