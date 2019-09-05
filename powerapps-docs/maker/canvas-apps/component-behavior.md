---
title: Verhaltens Formeln für Komponenten | Microsoft-Dokumentation
description: Löst eine APP aus, um eine oder mehrere Tasks auszuführen, wenn eine komponentenbasierte Aktion auftritt.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 05/24/2019
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c8ec4edd835f12fb6fccf04ba0fb27f1e755cac0
ms.sourcegitcommit: ea3ab5926541c60a9e7c17f52f937c9812d48c71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2019
ms.locfileid: "70310063"
---
# <a name="behavior-formulas-for-components"></a>Verhaltens Formeln für Komponenten

> [!IMPORTANT]
> Diese Funktion ist in der Standardeinstellung immer noch experimentell und deaktiviert. Weitere Informationen finden Sie unter [experimentelle Features und Vorschau Features](working-with-experimental.md).

Geben Sie mindestens eine [Verhaltens Formel](working-with-formulas-in-depth.md) an, die ausgeführt wird, wenn ein Ereignis eine Änderung in Komponenten Instanzen auslöst. Legen Sie z. b. die **onreset** -Eigenschaft einer Komponente auf eine oder mehrere Formeln fest, die die Initialisierung durchführen, die Eingabe löschen und Werte zurücksetzen, wenn die **Reset** -Funktion auf den Komponenten Instanzen ausgeführt wird.

## <a name="onreset"></a>OnReset

Wenn eine Komponente ausgewählt ist, wählen Sie in der Dropdown Liste mit den Eigenschaften (auf der rechten Seite der Bearbeitungs Leiste) die Option **onreset** aus, und geben Sie dann eine oder mehrere Formeln ein.

> [!div class="mx-imgBorder"]
> ![Onreset-Beispiel](./media/component-behavior/example-onreset.png)

Zum Testen von **onreset**konfigurieren Sie ein-Steuerelement, um die Komponente zurückzusetzen. Legen Sie z. b. die **onselect** -Eigenschaft einer Schaltfläche auf diese Formel fest: **Zurücksetzen** (*Componentname*)

> [!div class="mx-imgBorder"]
> ![Schaltfläche Zurücksetzen](./media/component-behavior/reset-button.png)
