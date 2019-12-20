---
title: Bearbeiten einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3c93c6696efc39e4f2354418ad1743fca3ebea95
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873043"
---
# <a name="edit-a-canvas-app-embedded-on-a-model-driven-form"></a>Bearbeiten einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist
In diesem Artikel wird erläutert, wie Sie eine Canvas-App bearbeiten, die in einem modellgesteuerten Formular eingebettet ist.

## <a name="edit-the-canvas-app-directly"></a>Canvas-App direkt bearbeiten
Sie können eine Canvas-App, die in einem modellgesteuerten Formular eingebettet ist, genau wie jede andere Canvas-App bearbeiten. Die Schritte zum Bearbeiten einer Canvas-App finden Sie unter: [Bearbeiten einer Canvas-App](../canvas-apps/edit-app.md)

## <a name="edit-the-canvas-app-via-the-host-model-driven-form"></a>Bearbeiten der Canvas-App über das modellgestützte Hostformular
Eine alternative Option ist es, die eingebettete Canvas-App über das modellgesteuerte Hostformular zu bearbeiten.

Stellen Sie sich vor, dass Sie eine Canvas-App bearbeiten möchten, die in einem Formular namens Firmenhauptformular für die Entität „Firmen” eingebettet ist. Gehen Sie dazu wie folgt vor: 

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.
2.  [Bearbeiten Sie das Formular](create-and-edit-forms.md) namens Firmenhauptformular für die Entität „Firma”. 
3.  Wählen Sie in der Befehlsleiste **In klassischen Modus wechseln**, um das Formular im klassischen Formular-Designer zu öffnen.
4.  Wählen Sie im klassischen Formular-Designer das Feld aus, das angepasst wird, um die eingebettete Canvas-App anzuzeigen.
5.  Wenn das Feld ausgewählt ist, wählen Sie auf der Registerkarte **Start** in der Gruppe **Bearbeiten** die Option **Eigenschaften ändern**.
6.  Wählen Sie im Dialogfeld **Feldeigenschaften** die **Steuerelemente**-Registerkarte aus.
7.  Wählen Sie im Dialogfeld **Feldeigenschaften** in der Liste der Steuerelemente die Option **Canvas-App**.
8.  Wählen Sie im Abschnitt unter der Liste mit den Steuerelementen die Option **Anpassen**, um die Canvas-App zu bearbeiten. Dadurch wird die Canvas-App zum Bearbeiten in Power Apps Studio in einer neuen Registerkarte geöffnet.
       > [!NOTE]
       > Wenn das Öffnen von Power Apps Studio aufgrund eines Popupblockers des Webbrowsers blockiert ist, müssen Sie die Website make.powerapps.com aktivieren oder den Popupblocker vorübergehend deaktivieren und dann erneut **Anpassen** auswählen.
9. Wenn Sie fertig mit Ihren Änderungen sind, wählen Sie die Registerkarte **Datei** und dann **Speichern** aus.
10. Um Ihre Änderungen für Endbenutzer verfügbar zu machen, wählen Sie **Veröffentlichen** und dann **Diese Version veröffentlichen**.

## <a name="see-also"></a>Siehe auch
[Einbetten einer Canvas-App in einem modellgesteuerten Formular](embed-canvas-app-in-form.md) <br />
[Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular](embedded-canvas-app-add-classic-designer.md) <br />
[Anpassen der Bildschirmgröße und Ausrichtung einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-customize-screen.md) <br />
[Führen Sie vordefinierte Aktionen aus einer eingebetteten Canvas-App auf dem Hostformular aus](embedded-canvas-app-actions.md) <br />
[Eigenschaften und Aktionen des ModelDrivenFormIntegration-Steuerelements](embedded-canvas-app-properties-actions.md) <br />
[Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md) <br />
[Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps](embedded-canvas-app-guidelines.md) <br />
[Migrieren von eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion als die neueste Version erstellt wurden](embedded-canvas-app-migrate-from-preview.md) <br />
