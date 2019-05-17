---
title: openForm | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bea56947-d976-4974-9ac7-2d5f5c7b6732
---

# <a name="openform"></a>openForm

[!INCLUDE [openform-description](includes/openform-description.md)]

## <a name="syntax"></a>Syntax

`openForm(options, parameters)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Optionen|`EntityFormOptions`|Ja|EntityFormOptions hat die folgenden Attribute:<br/>- **createFromEntity**: [EntityReference](../entityreference.md). Gibt einen Datensatz an, der Standardwerte basierend auf zugeordneten Attributwerten bereitstellt. Das Suchobjekt hat folgende Zeichenfolgeneigenschaften: entityType, id und name. <br/>- **entityId**: `string`. Die ID des Entitätsdatensatzes, für den das Formular angezeigt wird.<br/>- **entityName**: `string`. Die ID des Entitätsdatensatzes, für den das Formular angezeigt wird.<br/>- **formId**: `string`. ID der anzuzeigenden Formularinstanz.<br/>- **height**: `number`. Die Höhe des zu öffnenden Formulars in Pixeln.<br/>- **openInNewWindow**: `boolean`. ob das Formular in einem neuen Fenster angezeigt wird.<br/>- **useQuickCreateForm**: `boolean`. ob das Formular "Schnellerfassung" geöffnet wird. Wird dieser Parameter nicht angegeben, wird `false` als Standardwert übergeben.<br/>- **width**: `number`. Die Breite des zu öffnenden Formulars in Pixeln.<br/>- **windowPosition**: `number`. Geben Sie einen der folgenden Werte für die Fensterposition des Formulars auf den Bildschirm an: `1:center` <br/> `2:side`|
|Parameter|`key`|Ja|Parameter des Entitätsformulars.|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise`

## <a name="remarks"></a>Anmerkungen

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) und [Datei](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)