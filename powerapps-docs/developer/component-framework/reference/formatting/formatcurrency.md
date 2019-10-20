---
title: FormatCurrency | Microsoft-Dokumentation
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
ms.assetid: 87e433e6-573f-414f-b49d-1213f2bd8cf4
ms.openlocfilehash: 6089e88ce5814ca24c8310435726bff07cc97894
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343241"
---
# <a name="formatcurrency"></a>formatCurrency

[!INCLUDE [formatcurrency-description](includes/formatcurrency-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="syntax"></a>Syntax

`context.formatting.formatCurrency(value, precision, symbol)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|value|`number`|ja| Ein Wert, der formatiert werden soll.|
|präziser|`number`|ja| Die Anzahl der Ziffern nach dem Dezimaltrennzeichen.|
|Tick|`string`|ja| Das Währungssymbol/der Code, der mit dem Währungswert hinzugefügt werden soll.|

## <a name="return-value"></a>Rückgabewert

Typ: `string`


### <a name="related-topics"></a>Verwandte Themen

[Formatierung](../formatting.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)