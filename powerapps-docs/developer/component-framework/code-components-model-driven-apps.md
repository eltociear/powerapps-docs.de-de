---
title: Codekomponenten für modellgesteuerte Apps | Microsoft-Dokumentation
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
ms.openlocfilehash: 7011c11ef8beb9549e864f650fad891f9c3d61bc
ms.sourcegitcommit: 13d4042c7bd73580cc8c595e137de7e7fec22875
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "3170218"
---
# <a name="code-components-for-model-driven-apps"></a>Codekomponenten für modellgesteuerte Apps

Power Apps component framework gibt Entwicklern die Möglichkeit, die Visualisierungen in modellgesteuerten Apps zu erweitern. Dank [Power Apps CLI](get-powerapps-cli.md) wird es professionellen Entwicklern ermöglicht, Codekomponenten für modellgesteuerte Apps zu erstellen, zu debuggen, zu importieren und hinzuzufügen. Sie können Codekomponenten zu Feldern, Rastern und Unterrastern in modellgesteuerten Apps hinzufügen. 

> [!IMPORTANT]
> Das Power Apps component framework ist für modellgesteuerte Apps standardmäßig aktiviert. Siehe [Komponenten für Canvas-Anwendungen](component-framework-for-canvas-apps.md), um zu erfahren, wie das Power Apps component framework für Canvas-Anwendungen aktiviert wird.

## <a name="implementing-code-components"></a>Implementieren von Codekomponenten

Bevor Sie mit der Erstellung von Codekomponenten beginnen, stellen Sie sicher, dass Sie alle Voraussetzungen installiert haben, die für die Entwicklung von Komponenten mit dem Power Apps component framework erforderlich sind. 

Im Artikel [Erstellen der ersten Codekomponente](implementing-controls-using-typescript.md) wird der schrittweise Prozess zum Erstellen von Codekomponenten beschrieben.

## <a name="add-code-components-to-model-driven-apps"></a>Hinzufügen von Codekomponenten zu modellgesteuerten Apps

Um Codekomponenten zu einem Feld oder einer Entität in modellgesteuerten Apps hinzuzufügen, siehe [Hinzufügen von Codekomponenten zu modellgesteuerten Apps](add-custom-controls-to-a-field-or-entity.md).

> [!div class="mx-imgBorder"] 
> ![Lineares Schieberegler-Steuerelement hinzufügen](../../maker/model-driven-apps/media/add-slider.PNG "Lineares Schieberegler-Steuerelement hinzufügen")

> [!div class="mx-imgBorder"]
> ![Dataset-Rasterkomponente](media/add-dataset-component.png "Dataset-Rasterkomponente")

## <a name="update-existing-code-components"></a>Aktualisieren vorhandener Codekomponenten

Immer wenn Sie die Codekomponenten aktualisieren und die Änderungen in der Laufzeit sehen möchten, müssen Sie das Versionsattribut in der Manifestdatei stoppen. Es wird empfohlen, die Version der Komponente immer zu stoppen, wenn Sie Änderungen vornehmen.

## <a name="see-also"></a>Siehe auch

[Power Apps component framework Übersicht](overview.md)<br/>
[Erstellen Sie Ihre erste Codekomponente](implementing-controls-using-typescript.md)<br/>
[Erlernen des Power Apps component framework](https://docs.microsoft.com/learn/paths/use-power-apps-component-framework)
