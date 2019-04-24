---
title: Erstellen Sie eine Canvas-app in einer Projektmappe | Microsoft-Dokumentation
description: Erstellen Sie eine Canvas-app in einer Projektmappe in PowerApps, damit Sie die app in einer anderen Umgebung bereitstellen können
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/23/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dcb6a9c69e602b739d58afde2242d18b60e6f477
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61540436"
---
# <a name="create-a-canvas-app-from-within-a-solution"></a>Erstellen einer Canvas-app aus in einer Projektmappe

Erstellen Sie eine app in einer Lösung, wenn Sie z. B. die app zu einer anderen Umgebung bereitgestellt werden sollen. Projektmappen können nicht nur apps aber auch benutzerdefinierte Entitäten, Optionssätze und andere Komponenten enthalten. Sie können eine Umgebung in einer Vielzahl von Möglichkeiten schnell durch Erstellen von apps und andere Komponenten in einer Lösung, die Projektmappe exportieren und dann importieren, wird in eine andere Umgebung anpassen.

Lösungen basieren auf derselben Plattform wie Dynamics 365 for Customer Engagement. Weitere Informationen finden Sie unter [Übersicht über Lösungen](../common-data-service/solutions-overview.md).

## <a name="prerequisite"></a>Voraussetzung

Um die Schritte in diesem Thema folgen zu können, müssen Sie in einer Umgebung wechseln, die eine Common Data Service-Datenbank enthält.

## <a name="create-a-solution"></a>Erstellen einer Lösung

Sie können dieses Verfahren überspringen, wenn Sie bereits eine Lösung haben, in dem Sie eine app erstellen möchten, oder auf dem Sie eine app verknüpfen möchten.

1. [Melden Sie sich bei](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) powerapps an, und klicken Sie dann (falls erforderlich) wechseln Sie zu der entsprechenden Umgebung:

    - Wenn Sie eine app in eine Lösung erstellen möchten, wechseln Sie in einer beliebigen Umgebung, die eine Common Data Service-Datenbank enthält.
    - Wenn Sie eine vorhandene app zu einer Projektmappe verknüpfen möchten, wechseln Sie zur Umgebung, die diese app enthält.

1. Wählen Sie in der linken Navigationsleiste auf **Lösungen**.

    > [!div class="mx-imgBorder"]
    > ![Lösungen in der linken Navigationsleiste option](./media/add-app-solution/left-nav.png "Option \"Lösungen\" in der linken Navigationsleiste")

1. Wählen Sie in dem Banner unter der Titelleiste **neue Projektmappe**.

    > [!div class="mx-imgBorder"]
    > ![New-Lösung-Option im Banner](./media/add-app-solution/banner-new-solution.png "New-Lösung-Option im Banner")

1. Geben Sie im Fenster, das angezeigt wird, einen Anzeigenamen, einen Verleger und eine Version für Ihre Lösung an.

    > [!div class="mx-imgBorder"]
    > ![Optionen für eine neue Projektmappe](./media/add-app-solution/configure-new-solution.png "Optionen für eine neue Projektmappe")

    Ein Namen (ohne Leerzeichen) generiert werden automatisch basierend auf den Anzeigenamen, den Sie angeben, aber Sie können den generierten Namen anpassen, wenn Sie möchten. Sie können den Standard-Verleger angeben, für Ihre Umgebung und **1.0** für die Version, wenn Sie den spezifische Anforderungen in diesen Bereichen haben.

1. Wählen Sie in der Nähe der oberen linken Ecke **speichern und schließen Sie**.

    > [!div class="mx-imgBorder"]
    > ![Speichern Sie eine neue Projektmappe](./media/add-app-solution/save-new-solution.png "speichern eine neue Projektmappe")

## <a name="create-a-canvas-app-in-a-solution"></a>Erstellen Sie eine Canvas-app in einer Projektmappe

Sie können eine leere Canvas-app aus in einer Projektmappe erstellen. Sie können nicht automatisch generieren einer app mit drei Bildschirmen oder Anpassen eine Vorlage oder die Beispiel-app aus in einer Projektmappe.

1. [Melden Sie sich bei](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) in PowerApps.

1. Falls erforderlich, wechseln Sie zur Umgebung, die die Projektmappe enthält, in dem Sie eine Canvas-app erstellen möchten.

1. Wählen Sie in der linken Navigationsleiste auf **Lösungen**.

    > [!div class="mx-imgBorder"]
    > ![Lösungen in der linken Navigationsleiste option](./media/add-app-solution/left-nav.png "Option \"Lösungen\" in der linken Navigationsleiste")

1. Wählen Sie in der Liste der Lösungen die Projektmappe, in der Sie eine Canvas-app erstellen möchten.

1. Wählen Sie in dem Banner unter der Titelleiste **neu** > **App** > **Canvas-app**, und wählen Sie dann auf den Formfaktor der app (Smartphone oder Tablet), Sie möchten erstellen.

    > [!div class="mx-imgBorder"]
    > ![Optionen zum Erstellen einer app in einer Projektmappe](./media/add-app-solution/new-option.png "Optionen zum Erstellen einer app in einer Projektmappe")

    PowerApps Studio wird mit einem leeren Zeichenbereich, in einer anderen Browserregisterkarte geöffnet.

1. Erstellen Sie Ihre app (oder mindestens eine Änderung vornehmen), und klicken Sie dann Ihre Änderungen zu speichern.

1. Wählen Sie auf der Browserregisterkarte, in dem Sie Ihre Lösung ausgewählt **Fertig** um die Liste der Komponenten in der Projektmappe zu aktualisieren.

    > [!div class="mx-imgBorder"]
    > ![Schaltfläche "Fertig"](./media/add-app-solution/done-button.png "Schaltfläche \"Fertig\"")

    Ihre neue app wird in der Liste der Komponenten für die betreffende Projektmappe angezeigt. Wenn Sie die Änderungen an Ihrer app speichern, werden sie in der Version wirksam werden, die in der Projektmappe ist.

## <a name="link-an-existing-canvas-app-to-a-solution"></a>Verknüpfen Sie eine vorhandene Canvas-app zu einer Projektmappe

Wenn Sie eine app zu einer Projektmappe verknüpfen möchten, beide müssen in der gleichen Umgebung sein, und die app muss erstellt wurden in einer Projektmappe.

1. [Melden Sie sich bei](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) in PowerApps.

1. Falls erforderlich, wechseln Sie zur Umgebung, die die Projektmappe enthält, zu dem Sie eine app zu verknüpfen möchten.

1. Wählen Sie in der linken Navigationsleiste auf **Lösungen**.

    > [!div class="mx-imgBorder"]
    > ![Lösungen in der linken Navigationsleiste option](./media/add-app-solution/left-nav.png "Option \"Lösungen\" in der linken Navigationsleiste")

1. Wählen Sie in der Liste der Lösungen die Lösung, die Sie eine app zu verknüpfen möchten.

1. Wählen Sie in dem Banner unter der Titelleiste **vorhandene hinzufügen** > **App** > **Canvas-app**.

    > [!div class="mx-imgBorder"]
    > ![Banner-Optionen, um eine vorhandene app verknüpfen](./media/add-app-solution/add-existing.png "Banner-Optionen, um eine vorhandene app zu verknüpfen.")

    Eine Liste von Canvas-apps, die innerhalb einer Lösung in dieser Umgebung erstellt wurden, wird angezeigt.

1. Wählen Sie in der Liste der apps, die app, die Sie verwenden möchten, Verknüpfen mit der Lösung, und wählen Sie dann **hinzufügen**.

    > [!div class="mx-imgBorder"]
    > ![Schaltfläche "hinzufügen"](./media/add-app-solution/add-button.png "Schaltfläche \"hinzufügen\"")

## <a name="known-limitations"></a>Bekannte Einschränkungen

Weitere Informationen zu bekannten Einschränkungen finden Sie unter [Verwenden von Lösungen in PowerApps](../common-data-service/use-solution-explorer.md#known-limitations). 

## <a name="next-steps"></a>Nächste Schritte

- Erstellen oder verknüpfen Sie weitere apps und [andere Komponenten](../common-data-service/use-solution-explorer.md), z. B. Entitäten, Flows und Dashboards, um Ihre Lösung.
- [Exportieren Sie Ihre Lösung](../common-data-service/import-update-export-solutions.md) , damit Sie können in eine andere Umgebung, in AppSource, bereitstellen und so weiter.
