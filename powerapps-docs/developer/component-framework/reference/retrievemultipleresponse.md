---
title: RetrieveMultipleResponse | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08ea66d3-b4af-44af-a3ae-cb2ebad043e8
---

# <a name="retrievemultipleresponse"></a>RetrieveMultipleResponse

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

## <a name="properties"></a>Eigenschaften

## <a name="entities"></a>Entitäten

Ein Array von JSON-Objekten, wobei jedes Objekt den abgerufenen Entitätsdatensatz darstellt, der die Attribute und Ihre Werte enthält.

**Typ**: `Entity[]`

## <a name="nextlink"></a>nextLink

Wenn die Anzahl von Datensätzen, die abgerufen werden, mehr als der Wert ist, der im 'maxPageSize'-Parameter in der Anforderung angegeben ist, gibt dieses Attribut die URL an, um die folgenden Datensatzgruppe zurückzugeben.

**Typ**: `string`


### <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)