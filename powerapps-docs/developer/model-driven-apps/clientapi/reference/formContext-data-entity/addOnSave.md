---
title: addOnSave (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1a66f93d-a47c-4316-91f1-dcf5d09f9d19
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonsave-client-api-reference"></a>addOnSave (Client-API-Referenz)



[!INCLUDE[./includes/addOnSave-description.md](./includes/addOnSave-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.entity.addOnSave(myFunction)`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die aufgerufen wird, wenn der Datensatz gespeichert wird.  Die Funktion wird unten auf der Ereignishandlerpipeline hinzugefügt. Der Ausführungskontext wird automatisch als der erste Parameter für die Funktion übergeben. Weitere Informationen finden Sie unter [Ausführungskontex](../../clientapi-execution-context.md).

### <a name="related-topics"></a>Verwandte Themen

[removeOnSave](removeOnSave.md)

[Formular OnSave-Ereignis](../events/form-onsave.md)

