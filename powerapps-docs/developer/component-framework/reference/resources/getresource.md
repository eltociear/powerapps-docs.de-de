---
title: GetResource | Microsoft-Dokumentation
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
ms.assetid: 5c04ba7c-acfe-4375-8dd8-6c537ded9352
ms.openlocfilehash: 919606c7b6669265a8bdd4f7b43080564e87a80f
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341401"
---
# <a name="getresource"></a>getResource

[!INCLUDE [getresource-description](includes/getresource-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.resources.getResource(id, success, failure)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|id|`String`|Ja|Der Ressourcen Zeichen folgen Bezeichner.|
|Erfolglos|`String`|Nein|Der Erfolgs Rückruf. Ressourcen Daten werden 64 im Base64-codierten Format zurückgegeben.|
|Fehler|`String`|Nein|Der Fehler Rückruf.|


### <a name="related-topics"></a>Verwandte Themen

[Resources](../resources.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)