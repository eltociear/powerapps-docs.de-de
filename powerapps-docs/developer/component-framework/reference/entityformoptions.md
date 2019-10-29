---
title: Entityformoptions | Microsoft-Dokumentation
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
ms.assetid: 418871c0-59dc-4a7c-a8f9-9364a19f7662
ms.openlocfilehash: 0ed2d2b13fa084fe1521e90304b7e3ead4ccac27
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025469"
---
# <a name="entityformoptions"></a>Entityformoptions

Bietet Zugriff auf alle Informationen zu den Entitäts Formularen.

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="properties"></a>Eigenschaften

### <a name="createfromentity"></a>"kreatefromentity"

Legt einen Datensatz fest, der Standardwerte basierend auf dem zugeordneten Attribut Wert bereitstellt. Das Nachschlage Objekt verfügt über die folgenden Eigenschaften: Entitätstyp, ID und Name.

**Typ**: [EntityReference](entityreference.md)

### <a name="entityid"></a>entityId

Eindeutige ID des Entitäts Datensatzes, für den das Formular angezeigt werden soll. 

**Typ**: `string`

### <a name="entityname"></a>entityName

Logischer Name der Entität, für die das Formular angezeigt werden soll. 

**Typ**: `string`

### <a name="formid"></a>formid

Die ID der anzuzeigenden Formular Instanz.

**Typ**: `string`

### <a name="height"></a>height

Höhe des Formular Fensters, das in Pixel angezeigt werden soll.

**Typ**: `number`

### <a name="openinnewwindow"></a>OpenInNewWindow

Gibt an, ob das Formular in einem neuen Fenster angezeigt werden soll.

**Typ**: `boolean`

### <a name="usequickcreateform"></a>usequickkreateform

Ob ein schneller Erstellungs Formular geöffnet werden soll. Wenn Sie diesen Wert nicht angeben, wird standardmäßig false übermittelt. 

**Typ**: `boolean`

### <a name="width"></a>width

Breite des Formular Fensters, das in Pixel angezeigt werden soll.

**Typ**: `boolean`

### <a name="windowposition"></a>windowPosition

Gibt die Fensterposition auf dem Bildschirm an.

**Typ**: `number`

Der windowposition-Wert ist eine Zahl mit den folgenden möglichen Werten.

|Value|Position|
|---|---|
|1|Tagesstätte|
|2|Seite|


## <a name="example"></a>Beispiel

```TypeScript
private onRowClick(event: Event): void {
    let rowRecordId = (event.currentTarget as HTMLTableRowElement).getAttribute(
      RowRecordId
    );
    if (rowRecordId) {
      let entityreference = this.contextObj.parameters.simpleTableGrid.records[
        rowRecordId
      ].getNamedreference();
      let entityFormOptions = {
        entityName: entityreference.entityType!,
        entityId: entityreference.id
      };
      this.contextObj.navigation.openForm(entityFormOptions);
    }
  }
```

### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)