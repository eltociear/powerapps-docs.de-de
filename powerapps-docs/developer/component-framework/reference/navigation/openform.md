---
title: OpenForm | Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bea56947-d976-4974-9ac7-2d5f5c7b6732
ms.openlocfilehash: d0754030de4880f0ad693105e96b47d785f1561b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342367"
---
# <a name="openform"></a>openForm

[!INCLUDE [openform-description](includes/openform-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.navigation.openForm(options, parameters)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Optionen|`EntityFormOptions`|Ja|Formular Optionen für Entitäten zum Öffnen des Formulars. Die entityformoptions verfügt über die folgenden Attribute:<br/>-  "**kreatefromentity**: `Lookup`. Legt einen Datensatz fest, der Standardwerte basierend auf zugeordneten Attributwerten bereitstellt. Das Nachschlage Objekt verfügt über die folgenden Zeichen folgen Eigenschaften: `entityType`, `id` und `name`. <br/>- **EntityID**: `String`. ID des Entitäts Datensatzes, für den das Formular angezeigt werden soll.<br/>- **EntityName**: `String`. Logischer Name der Entität, für die das Formular angezeigt werden soll.<br/>- **formId**: `String`. Die ID der anzuzeigenden Formular Instanz.<br/>- **Höhe**: `Number`. Höhe des Formular Fensters, das in Pixel angezeigt werden soll.<br/>- **OpenInNewWindow**: `boolean`. Gibt an, ob das Formular in einem neuen Fenster angezeigt werden soll.<br/>- **usequickkreateform**: `Boolean`. Ob ein schneller Erstellungs Formular geöffnet werden soll. Wenn Sie diesen Wert nicht angeben, wird standardmäßig `false` übermittelt.<br/>- **Breite**: `Number`. Breite des Formular Fensters, das in Pixel angezeigt werden soll.<br/>- **windowposition**: `Number`. Geben Sie einen der folgenden Werte für die Fensterposition des Formulars auf dem Bildschirm an: `1:center` <br/> `2:side`|
|Metern|`Object`|Nein|Ein Dictionary-Objekt, das zusätzliche Parameter an das Formular übergibt. Ungültige Parameter verursachen einen Fehler. Weitere Informationen [finden Sie unter Feld Werte mit Parametern, die an ein Formular weitergegeben](https://docs.microsoft.com/en-us/powerapps/developer/model-driven-apps/set-field-values-using-parameters-passed-form) wurden, und [Konfigurieren eines Formulars zum akzeptieren benutzerdefinierter Abfrage Zeichen](https://docs.microsoft.com/en-us/powerapps/developer/component-framework/sample-controls/navigation-api-control)|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise<OpenFormSuccessResponse>`

## <a name="remarks"></a>Rede

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)

### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)