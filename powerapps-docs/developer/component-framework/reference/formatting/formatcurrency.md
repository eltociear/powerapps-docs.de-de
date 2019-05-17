---
title: FormatCurrency | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87e433e6-573f-414f-b49d-1213f2bd8cf4
---

# <a name="formatcurrency"></a>formatCurrency

[!INCLUDE [formatcurrency-description](includes/formatcurrency-description.md)]

## <a name="syntax"></a>Syntax

`formatCurrency(value, precision, symbol)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Wert|`number`|Ja| Ein zu formatierender Wert.|
|Genauigkeit|`number`|Ja| Die Anzahl der Stellen nach dem Dezimalpunkt.|
|Symbol|`string`|Ja| Das Währungssymbol/der Code, der mit dem Währungswert hinzugefügt werden soll.|

## <a name="return-value"></a>Rückgabewert

Typ: `string`


### <a name="related-topics"></a>Verwandte Themen

[Formatierung](../formatting.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)