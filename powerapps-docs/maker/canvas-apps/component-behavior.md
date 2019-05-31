---
title: Verhaltensformeln für Komponenten | Microsoft-Dokumentation
description: Auslösen einer app, um eine oder mehrere Aufgaben auszuführen, wenn es sich bei eine komponentenbasierten-Aktion tritt auf, an.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 05/24/2019
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7275395a4c21afaebc60e9635461afc08f5e84a0
ms.sourcegitcommit: afe958805d8e1cfa4fdf02c7bceea947185f71f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66420312"
---
# <a name="behavior-formulas-for-components"></a>Verhaltensformeln für Komponenten

> [!IMPORTANT]
> Diese Funktion ist noch experimentell und standardmäßig deaktiviert. Weitere Informationen finden Sie unter [experimentell und Vorschaufunktionen](working-with-experimental.md).

Geben Sie eine oder mehrere [verhaltensformeln](working-with-formulas-in-depth.md) , die ausgeführt werden, wenn ein Ereignis wird, eine Änderung in Instanzen von Komponenten ausgelöst. Z. B. Festlegen einer Komponente **OnReset** Eigenschaftswerte in ein oder mehrere Formeln, die Initialisierung ausführen, Eingabe löschen und die kennwortzurücksetzung bei der **zurücksetzen** Funktion, die auf den Komponenteninstanzen ausgeführt wird.

## <a name="onreset"></a>OnReset ##

Wählen Sie eine Komponente ausgewählt ist, **OnReset** in der Dropdown-Liste von Eigenschaften (auf der rechten Seite der Bearbeitungsleiste), und geben Sie dann auf einer oder mehreren Formeln.

> [!div class="mx-imgBorder"]
> ![OnReset-Beispiel](./media/component-behavior/example-onreset.png)

So testen Sie **OnReset**, konfigurieren Sie ein Steuerelement zum Zurücksetzen der Komponente. Legen Sie z. B. die **OnSelect** -Eigenschaft einer Schaltfläche auf diese Formel: **Zurücksetzen**(*ComponentName*)

> [!div class="mx-imgBorder"]
> ![Schaltfläche "Zurücksetzen"](./media/component-behavior/reset-button.png)
