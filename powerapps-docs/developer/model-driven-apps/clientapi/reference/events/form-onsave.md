---
title: Form OnSave Ereignis (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="form-onsave-event-client-api-reference-in-model-driven-apps"></a>Form OnSave Ereignis (Client-API-Referenz) in modellgestützten Apps



Das `OnSave`-Ereignis tritt auf, wenn Folgendes zutrifft:
- Der Benutzer klickt auf die Schaltfläche **Speichern** in der unteren rechten Ecke des Formulars, selbst wenn keine geänderten Daten gespeichert werden müssen.
- Code führt die [formContext.data.entity.save](../formContext-data-entity/save.md)-Methode aus, selbst wenn keine geänderten Daten gespeichert werden müssen.
- Der Benutzer navigiert von dem Formular weg, und es befinden sich nicht gespeicherte Daten im Formular.
- Bei aktivierter automatischer Speicherung 30 Sekunden nach der Änderung der Daten, wenn sich im Formular nicht gespeicherte Daten befinden.
- Code führt die [formContext.data.save](../formContext-data/save.md)-Methode aus, und es befinden sich nicht gespeicherte Daten in dem Formular.
- Code führt die [formContext.data.refresh](../formContext-data/refresh.md)-Methode durch, wobei der Wert "True" als erster Parameter übergeben wird und sich nicht gespeicherte Daten in dem Formular befinden.

Um festzustellen auf welche Schaltfläche geklickt wurde, um das Speichern auszuführen, verwenden Sie die getSaveMode-Methode.

Sie können die Speicheraktion abbrechen, indem Sie die preventDefault-Methode im Ereignisargumentobjekt bereitstellen. Die preventDefault-Methode, die verfügbar ist, indem Sie die getEventArgs-Methode anwenden, die Teil des Ausführungskontexts ist. Der Ausführungskontext wird automatisch an den Formularereignishandler weitergegeben.

### <a name="related-topic"></a>Verwandtes Thema
[Raster OnSave-Ereignis](grid-onsave.md)  



