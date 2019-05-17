---
title: EntityFormOptions | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 418871c0-59dc-4a7c-a8f9-9364a19f7662
---
# <a name="entityformoptions"></a>EntityFormOptions

## <a name="createfromentity-entityreference"></a>createFromEntity: EntityReference

Gibt einen Datensatz an, der Standardwerte basierend auf dem zugeordneten Attributwert bereitstellt. Das Suchobjekt hat folgende Eigenschaften: Entitätstyp, ID und Name.

## <a name="entity"></a>Entität

Eindeutige ID des Entitätsdatensatzes, für den das Formular angezeigt wird. 

**Typ**: `string`

## <a name="entityname"></a>entityName

Die ID des Entitätsdatensatzes, für den das Formular angezeigt wird. 

**Typ**: `string`

## <a name="formid"></a>formId

ID der anzuzeigenden Formularinstanz.

**Typ**: `string`

## <a name="height"></a>height

Die Höhe des zu öffnenden Formulars in Pixeln.

**Typ**: `number`

## <a name="openinnewwindow"></a>openInNewWindow

Ob das Formular in einem neuen Fenster angezeigt wird

**Typ**: `boolean`

## <a name="usequickcreateform"></a>useQuickCreateForm

Ob das Formular "Schnellerfassung" geöffnet wird Wird dieser Parameter nicht angegeben, wird false als Standardwert übergeben. 

**Typ**: `boolean`

## <a name="width"></a>width

Die Breite des zu öffnenden Formulars in Pixeln.

**Typ**: `boolean`

## <a name="windowposition"></a>windowPosition

Gibt die Fensterposition auf dem Bildschirm an.

**Typ**: `number`

Der windowPosition-Wert ist eine Nummer mit folgenden möglichen Werten:

|Value|Position|
|---|---|
|1|Zentriert|
|2|Seite|


### <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)