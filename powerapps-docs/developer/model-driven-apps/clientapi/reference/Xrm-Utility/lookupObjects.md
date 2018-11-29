---
title: lookupObjects (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
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
# <a name="lookupobjects-client-api-reference"></a>lookupObjects (Client-API-Referenz)



[!INCLUDE[./includes/lookupObjects-description.md](./includes/lookupObjects-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.Utility.lookupObjects(lookupOptions).then(successCallback, cancelCallback)`

## <a name="parameters"></a>Parameter

**lookupOptions**: Objekt. Definiert die Optionen für das Öffnen des Suchendialogfelds. Verfügt über die folgenden Eigenschaften:

|Eigenschaftsname |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|allowMultiSelect|Boolean|No|Gibt an, dass die Suche mehr als ein ausgewähltes Element erlaubt.|
|defaultEntityType|String|No|Der zu verwenden Standardentitätstyp.|
|defaultViewId|String|No|Die zu verwendende Standardansicht|
|entityTypes|Array|No|Die anzuzeigenden Entitätstypen.|
|showBarcodeScanner|Boolean|No|Gibt an, ob das Nachschlagesteuerelement den Barcodescanner in mobilen Clients anzeigen soll.|
|viewIds|Array|No|Die Ansichten die in der Ansichtsauswahl verfügbar sein sollen. Nur Systemansichten werden unterstützt.|
|successCallback |Funktion |Ja |Ein Funktion, die beim Aufrufen des Suchensteuerelements aufgerufen wird. Es wird ein Objekt mit den folgenden Eigenschaften übergeben:<br/>- **entityType**: Zeichenfolge. Entitätstyp des ausgewählten Datensatzes im Nachschlagesteuerelement.<br/>- **id**: Zeichenfolge. ID des ausgewählten Datensatzes im Nachschlagesteuerelement.<br/>- **name**: Zeichenfolge. Name des ausgewählten Datensatzes im Nachschlagesteuerelement.|
|errorCallback |Funktion |Ja |Ein Feature, um aufzurufen, wenn das Nachschlagesteuerelement oder der Vorgang fehlschlägt.  |


### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility](../xrm-utility.md)