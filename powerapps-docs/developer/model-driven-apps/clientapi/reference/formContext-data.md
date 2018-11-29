---
title: formContext.data (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
description: Erfahren Sie mehr über das Verwenden modellgestützten Apps mithilfe von Client-API.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 32e8d1d0-4093-4588-a517-2930eec34dce
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextdata-client-api-reference"></a>formContext.data (Client-API-Referenz)



Stellt Eigenschaften und Methoden zum Verwenden von Daten im Formular bereit.

![formContext Datenobjektmodell](../../media/ClientAPI-formContext-data-Model.png)

## <a name="properties"></a>Eigenschaften

|Name|Beschreibung|
|--|--|
|Attribute|Sammlung von Nicht-Entitätsdaten im Formular. Elemente in dieser Sammlung sind vom gleichen Typ wie die Attributsammlung, aber sie sind keine Attribute der Formularentität. <br/>Weitere Informationen: [Sammlungen](collections.md).|
|Entität|Stellt Methoden zum Abrufen von Informationen bereit, die für den auf der Seite angezeigten Datensatz spezifisch sind, die Speichermethode und eine Sammlung aller im Formular enthaltenen Attribute. Attribute werden durch Felder beschränkt, die im Formular angezeigt werden. <br/>Weitere Informationen: [formContext.data.entity](formContext-data-entity.md)|
|Prozess|Stellt Objekte und Methoden zum Interagieren mit den Geschäftsprozessfluss-Daten in einem Formular bereit.<br/>Weitere Informationen: [formContext.data.process](formContext-data-process.md)|


## <a name="methods"></a>Methoden 

|Name|Beschreibung|
|--|--|
|[addOnLoad](formContext-data/addOnload.md)|[!INCLUDE[formContext-data/includes/addOnLoad-description.md](formContext-data/includes/addOnLoad-description.md)]|
|[getIsDirty](formContext-data/getIsDirty.md)|[!INCLUDE[formContext-data/includes/getIsDirty-description.md](formContext-data/includes/getIsDirty-description.md)]|
|[isValid](formContext-data/isValid.md)|[!INCLUDE[formContext-data/includes/isValid-description.md](formContext-data/includes/isValid-description.md)]|
|[Aktualisieren](formContext-data/refresh.md)|[!INCLUDE[formContext-data/includes/refresh-description.md](formContext-data/includes/refresh-description.md)]|
|[removeOnLoad](formContext-data/removeOnLoad.md)|[!INCLUDE[formContext-data/includes/removeOnLoad-description.md](formContext-data/includes/removeOnLoad-description.md)]|
|[save](formContext-data/save.md)|[!INCLUDE[formContext-data/includes/save-description.md](formContext-data/includes/save-description.md)]|


### <a name="related-topics"></a>Verwandte Themen

[formContext.data.entity](formContext-data-entity.md)

[formContext.data.process](formContext-data-process.md)




