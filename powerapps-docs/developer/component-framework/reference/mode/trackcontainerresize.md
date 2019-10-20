---
title: Trackcontainerresize | Microsoft-Dokumentation
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: c5f482c2-dde2-460b-89a7-39e0efcc5704
ms.openlocfilehash: 8f9bc1ef17bdcb762e992d9f77dcdcd7ba1e8c50
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342551"
---
# <a name="trackcontainerresize"></a>trackContainerResize

[!INCLUDE [trackcontainerresize-description](includes/trackcontainerresize-description.md)].

Wenn der übergeordnete Kontext, der die Komponente gehostet, eine Begrenzung der Höhe in Modell gesteuerten apps bereitstellt, wird das gleiche ordnungsgemäß auf die untergeordnete Komponente angewendet. In den meisten Szenarios schränkt der übergeordnete Kontext jedoch nicht die Höhe der Komponente ein und erhält daher den Wert "-1", um anzugeben, dass der Vorgang möglicherweise weiter zunimmt.

In Canvas-apps stellt der übergeordnete Kontext immer die Höhe und die Breite für die Komponente in der Art des Drag & Drop-Editors bereit.

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.mode.trackContainerResize(value)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|value|`Boolean`|Ja|`True` wenn die Steuerelemente die Containergröße nachverfolgen müssen, erhält die Komponente "zustandortbreite" oder "zukünftig".|


### <a name="related-topics"></a>Verwandte Themen

[Mode](../mode.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
