---
title: Formatdecimal | Microsoft-Dokumentation
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
ms.assetid: 05c1c54d-14b5-4dad-9cd8-eec07e750c00
ms.openlocfilehash: 02f31ce76df0300fae517bbf4699c6d559b04591
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343494"
---
# <a name="formatdecimal"></a>formatDecimal

[!INCLUDE [formatdecimal-description](includes/formatdecimal-description.md)]

## <a name="syntax"></a>Syntax

`context.formatting.formatDecimal(value, precision);`

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|value|`number`|Ja|Das zu formatierende Datum.|
|präziser|`number`|Ja|Die Anzahl der Ziffern nach dem Dezimaltrennzeichen.|

## <a name="return-value"></a>Rückgabewert

Typ: `string`


### <a name="related-topics"></a>Verwandte Themen

[Formatierung](../formatting.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)