---
title: Code-Komponenten für modellgetriebene Anwendungen | Microsoft Docs
description: Erstellen von Codekomponenten für Canvas-Apps
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 02/24/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: 4380d99439b9103ea40800ea8a5a20e1e13768d8
ms.sourcegitcommit: 27cb5ad024d43f208ef6acfbea456a05df3edf8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "3082823"
---
# <a name="code-components-for-model-driven-apps"></a>Code-Komponenten für modellgesteuerte Anwendungen

Power Apps component framework gibt Entwicklern die Möglichkeit, die Visualisierungen in modellgesteuerten Anwendungen zu erweitern. Professionelle Entwickler können mit Hilfe von [Power Apps CLI](get-powerapps-cli.md) Codekomponenten in modellgesteuerten Anwendungen erstellen, debuggen, importieren und hinzufügen. Sie können Codekomponenten zu Feldern, Gittern und Untergittern in modellgesteuerten Anwendungen hinzufügen. 

> [!IMPORTANT]
> Das Power Apps component framework ist für modellgesteuerte Anwendungen standardmäßig aktiviert. Siehe [Komponenten für Canvas-Anwendungen](component-framework-for-canvas-apps.md), um zu erfahren, wie das Power Apps component framework für Canvas-Anwendungen aktiviert wird.

## <a name="implementing-code-components"></a>Implementieren von Codekomponenten

Bevor Sie mit der Erstellung von Code-Komponenten beginnen, stellen Sie sicher, dass Sie alle Voraussetzungen installiert haben, die für die Entwicklung von Komponenten mit dem Power Apps component framework erforderlich sind. 

Das Thema [Erstellen Ihrer ersten Codekomponente](implementing-controls-using-typescript.md) demonstriert den schrittweisen Prozess zur Erstellung von Codekomponenten.

## <a name="add-code-components-to-model-driven-apps"></a>Hinzufügen von Codekomponenten zu modellgesteuerten Anwendungen

Um Codekomponenten zu einem Feld oder einer Entität in modellgesteuerten Anwendungen hinzuzufügen, siehe [Codekomponenten zu modellgesteuerten Anwendungen hinzufügen](add-custom-controls-to-a-field-or-entity.md).

> [!div class="mx-imgBorder"] 
> ![Lineares Schieberegler-Steuerelement hinzufügen](../../maker/model-driven-apps/media/add-slider.PNG "Lineares Schieberegler-Steuerelement hinzufügen")

> [!div class="mx-imgBorder"]
> ![Dataset-Rasterkomponente](media/add-dataset-component.png "Dataset-Rasterkomponente")

## <a name="update-existing-code-components"></a>Aktualisieren vorhandener Codekomponenten

Immer wenn Sie die Codekomponenten aktualisieren und die Änderungen in der Laufzeit sehen möchten, müssen Sie das Versionsattribut in der Manifestdatei stoppen. Es wird empfohlen, die Version der Komponente immer zu stoppen, wenn Sie Änderungen vornehmen.

## <a name="see-also"></a>Siehe auch

[Power Apps component framework Übersicht](overview.md)<br/>
[Erstellen Sie Ihre erste Codekomponente](implementing-controls-using-typescript.md)
