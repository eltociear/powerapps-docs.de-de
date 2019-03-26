---
title: lookupObjects (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 01/24/2019
ms.service: powerapps
ms.topic: reference
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="lookupobjects-client-api-reference"></a>lookupObjects (Client-API-Referenz)



[!INCLUDE[./includes/lookupObjects-description.md](./includes/lookupObjects-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.Utility.lookupObjects(lookupOptions).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parameter

**lookupOptions**: Objekt. Definiert die Optionen für das Öffnen des Suchendialogfelds. Verfügt über die folgenden Eigenschaften:

|Eigenschaftsname |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|allowMultiSelect|Boolean|No|Gibt an, dass die Suche mehr als ein ausgewähltes Element erlaubt.|
|defaultEntityType|String|No|Der zu verwenden Standardentitätstyp.|
|defaultViewId|String|Nein|Die zu verwendende Standardansicht|
|disableMru|Boolean|Nein|Legt fest, ob das zuletzt verwendete Element (MRU) angezeigt werden soll.<br />Nur für Einheitliche Oberfläche verfügbar.|
|entityTypes|Array|Nein|Die anzuzeigenden Entitätstypen.|
|Filter|Array von Objekten|Nein|Wird verwendet, um die Ergebnisse zu filtern. Jedes Objekt im Array enthält die folgenden Attribute:<br /><ul><li>**filterXml**: Zeichenfolge. Das anzuwendende FetchXML-Filterelement.</li><li>**entityLogicalName**: Zeichenkette. Der Entitätstyp, auf den dieser Filter angewendet werden soll.</li></ul>|
|showBarcodeScanner|Boolean|Nein|Gibt an, ob das Nachschlagesteuerelement den Barcodescanner in mobilen Clients anzeigen soll.|
|viewIds|Array|No|Die Ansichten die in der Ansichtsauswahl verfügbar sein sollen. Nur Systemansichten werden unterstützt.|
|successCallback |Funktion |Ja |Ein Funktion, die beim Aufrufen des Suchensteuerelements aufgerufen wird. Es wird ein Array von Objekten mit den folgenden Eigenschaften übergeben:<br/><ul><li>**entityType**: Zeichenfolge. Entitätstyp des ausgewählten Datensatzes im Nachschlagesteuerelement.</li><li>**id**: Zeichenfolge. ID des ausgewählten Datensatzes im Nachschlagesteuerelement.</li><li>**name**: Zeichenfolge. Name des ausgewählten Datensatzes im Nachschlagesteuerelement.</li>|
|errorCallback |Funktion |Ja |Ein Feature, um aufzurufen, wenn das Nachschlagesteuerelement oder der Vorgang fehlschlägt.  |


### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility](../xrm-utility.md)
