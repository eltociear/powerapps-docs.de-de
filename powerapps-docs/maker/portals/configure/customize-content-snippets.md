---
title: Anpassen von Inhalt mithilfe von Inhaltsausschnitten in einem Portal | MicrosoftDocs
description: Informationen zum Anpassen von Inhalt mit Inhaltsausschnitten.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: ef85ea6f62f6b0f90a7463a11c4bf4566eee251a
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977160"
---
# <a name="customize-content-by-using-content-snippets"></a>Anpassen von Inhalt mit Inhaltsausschnitten

Inhaltsausschnitte sind kleine Segmente bearbeitbaren Inhalts, die von einem Entwickler in einer Seitenvorlage platziert werden können, sodass anpassbarer Inhalt Teile eines Seitenlayouts leicht auffüllen können. Ausschnittssteuerelemente, die für das Rendern der Inhaltsausschnitte im webbasierten Portal zuständig sind, werden in .aspx-Seiten von Entwicklern platziert.

## <a name="edit-snippets"></a>Bearbeiten Sie Ausschnitte

Ausschnitte können durch die Portalverwaltungs-App bearbeitet werden. Der Hauptvorteil des Ausschnitts ist die Tatsache, dass Sie etwas Inhalt entnehmen können (mit Ausnahme der Hauptkopie der Seite) und ihn separat bearbeiten können. So ist im Wesentlichen sämtlicher statischer Inhalt Ihrer Website vollständig inhaltsverwaltet und bearbeitbar.

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2.  Gehen Sie zu **Portale** > **Inhaltsausschnitte**.

3.  Klicken Sie auf **Neu**, um einen neuen Ausschnitt zu erstellen.

4.  So bearbeiten Sie einen vorhandenen Ausschnitt: Wählen Sie einen vorhandenen **Inhaltsausschnitt** im Raster.

Geben Sie Werte in die folgenden Felder ein:

| Name    | Beschreibung                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| Name    | Der Name kann von einem Entwickler verwendet werden, um den Ausschnittswert in einer Seitenvorlage innerhalb des Portalcodes zu platzieren. |
| Website | Die Website, die dem Ausschnitt zugeordnet ist.                                                              |
| Wert   | Der Inhalt des im Portal angezeigten Ausschnitts. Dies kann normalen Text oder HTML-Markup enthalten.         |



