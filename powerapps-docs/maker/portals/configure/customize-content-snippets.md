---
title: Anpassen von Inhalten mithilfe von Inhalts Ausschnitten in einem Portal | MicrosoftDocs
description: Erfahren Sie, wie Sie Inhalte mithilfe von Inhalts Ausschnitten anpassen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 362bbe27850e8e72d7af4b2fb32b42796334d579
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552817"
---
# <a name="customize-content-by-using-content-snippets"></a>Anpassen von Inhalten mithilfe von Inhalts Ausschnitten

Inhalts Ausschnitte sind kleine Blöcke von bearbeitbarem Inhalt, die von einem Entwickler in einer Seitenvorlage platziert werden können, sodass anpassbare Inhalte einen Teil des Layouts einer Seite problemlos auffüllen können. Code Ausschnitt Steuerelemente, die für das Rendern des Inhalts von Ausschnitten im Webportal verantwortlich sind, werden von Entwicklern in einer Seitenvorlage platziert.

## <a name="edit-snippets"></a>Ausschnitte bearbeiten

Ausschnitte können entweder über die Portal Verwaltungs-APP bearbeitet werden. Die Hauptstärke des Code Ausschnitts ist die Tatsache, dass Sie einen Teil des Inhalts (außer der Haupt Kopie der Seite) abstrahieren und separat bearbeiten können, sodass im Grunde alle statischen Inhalte auf Ihrer Website vollständig Inhalts verwaltet und bearbeitbar sind.

1. Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2.  Wechseln Sie zu **Portale** > **Inhalts Ausschnitte**.

3.  Um einen neuen Code Ausschnitt zu erstellen, wählen Sie **neu**aus.

4.  Um einen vorhandenen Ausschnitt zu bearbeiten, wählen Sie einen vorhandenen **Inhalts Ausschnitt** im Raster aus.

Geben Sie Werte für die folgenden Felder ein:

| Name    | Beschreibung                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| Name    | Der Name kann von einem Entwickler verwendet werden, um den Ausschnitt Wert in einer Seitenvorlage im Code des Portals zu platzieren. |
| Website | Die Website, die dem Ausschnitt zugeordnet ist.                                                              |
| Value   | Der Inhalt des Code Ausschnitts, der im Portal angezeigt werden soll. Dies kann nur-Text-oder HTML-Markup enthalten.         |



