---
title: Getentitymetadata | Microsoft-Dokumentation
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
ms.assetid: 6a334af7-ca5b-449c-b90f-0901824654d2
ms.openlocfilehash: 89dc2e9d567b8ff38c41df2074d2a85d6bcaf467
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340964"
---
# <a name="getentitymetadata"></a>getEntityMetadata

[!INCLUDE [getentitymetadata-description](includes/getentitymetadata-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.utils.getEntityMetadata(entityName, attributes)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|entityName|`String`|Ja|Der logische Name der Entität.|
|Legt|`String[]`|Nein|Die Attribute, für die Metadaten zu erhalten sind.|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise<EntityMetadata>`


### <a name="related-topics"></a>Verwandte Themen

[Utility](../utility.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)