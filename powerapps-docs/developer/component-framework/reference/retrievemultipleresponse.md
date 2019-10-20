---
title: Retrievemultipleresponse | Microsoft-Dokumentation
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
ms.assetid: 08ea66d3-b4af-44af-a3ae-cb2ebad043e8
ms.openlocfilehash: 0e5b2cad047bcf91b0c63e27c4a7ceb35c1ed538
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341309"
---
# <a name="retrievemultipleresponse"></a>"Retrievemultipleresponse"

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="properties"></a>Eigenschaften

### <a name="entities"></a>Kleinstunternehmen

Ein Array von JSON-Objekten, wobei jedes-Objekt den abgerufenen Entitäts Daten Satz mit Attributen und deren Werten darstellt.

**Typ**: `Entity[]`

### <a name="nextlink"></a>nextLink

Wenn die Anzahl der abgerufenen Datensätze größer ist als der Wert, der im `maxPageSize`-Parameter in der Anforderung angegeben ist, gibt dieses Attribut die URL zurück, um die nächste Gruppe von Datensätzen zurückzugeben.

**Typ**: `string`


### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)