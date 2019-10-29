---
title: Erstellen einer Canvas-app in einer Projekt Mappe | Microsoft-Dokumentation
description: Erstellen Sie in powerapps eine Canvas-app in einer Projekt Mappe, damit Sie die app in einer anderen Umgebung bereitstellen können.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/23/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c908e3d25530b52b103ef58989545e46b931e791
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "71987703"
---
# <a name="create-a-canvas-app-from-within-a-solution"></a>Erstellen einer Canvas-App aus einer Projekt Mappe

Erstellen Sie eine APP aus einer Projekt Mappe, wenn Sie z. b. die app in einer anderen Umgebung bereitstellen möchten. Lösungen können nicht nur apps, sondern auch angepasste Entitäten, Optionssätze und andere Komponenten enthalten. Sie können eine Umgebung auf unterschiedlichste Weise anpassen, indem Sie apps und andere Komponenten innerhalb einer Projekt Mappe erstellen, die Lösung exportieren und Sie dann in eine andere Umgebung importieren.

Weitere Informationen zu Lösungen finden Sie unter [Übersicht über Lösungen](../common-data-service/solutions-overview.md).

## <a name="prerequisite"></a>Voraussetzung

Wenn Sie die Schritte in diesem Thema ausführen möchten, müssen Sie zu einer Umgebung wechseln, in der eine Common Data Service-Datenbank enthalten ist.

## <a name="create-a-solution"></a>Erstellen einer Lösung

Sie können dieses Verfahren überspringen, wenn Sie bereits über eine Projekt Mappe verfügen, in der Sie eine APP erstellen möchten, oder für die Sie eine APP verknüpfen möchten.

1. [Melden](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Sie sich bei powerapps an, und wechseln Sie dann (falls erforderlich) in die entsprechende Umgebung:

    - Wenn Sie in einer Projekt Mappe eine APP erstellen möchten, wechseln Sie zu einer beliebigen Umgebung, die eine Common Data Service Datenbank enthält.
    - Wenn Sie eine vorhandene App mit einer Projekt Mappe verknüpfen möchten, wechseln Sie zu der Umgebung, in der die APP enthalten ist.

1. Wählen Sie in der linken Navigationsleiste **Lösungen**aus.

    > [!div class="mx-imgBorder"]
    > ![Lösungs Option in der linken Navigationsleiste](./media/add-app-solution/left-nav.png "Lösungs Option in der linken Navigationsleiste")

1. Wählen Sie im Banner unter der Titelleiste die Option **neue**Projekt Mappe aus.

    > [!div class="mx-imgBorder"]
    > ![New-Solution-Option im Banner](./media/add-app-solution/banner-new-solution.png "New-Solution-Option im Banner")

1. Geben Sie im angezeigten Fenster einen anzeigen Amen, einen Herausgeber und eine Version für die Projekt Mappe an.

    > [!div class="mx-imgBorder"]
    > ![Optionen für eine neue Projekt Mappe](./media/add-app-solution/configure-new-solution.png "Optionen für eine neue Projekt Mappe")

    Ein Name (ohne Leerzeichen) wird automatisch auf der Grundlage des von Ihnen angegebenen anzeigen Amens generiert, aber Sie können den generierten Namen bei Bedarf anpassen. Sie können den Standard Herausgeber für Ihre Umgebung und **1,0** für die Version angeben, wenn in diesen Bereichen keine speziellen Anforderungen vorliegen.

1. Wählen Sie in der Nähe der oberen linken Ecke **Speichern und schließen**aus.

    > [!div class="mx-imgBorder"]
    > ![Speichern einer neuen Projekt Mappe](./media/add-app-solution/save-new-solution.png "Speichern einer neuen Projekt Mappe")

## <a name="create-a-canvas-app-in-a-solution"></a>Erstellen einer Canvas-app in einer Projekt Mappe

Sie können eine leere Canvas-APP innerhalb einer Projekt Mappe erstellen. Sie können eine APP mit drei Bildschirmen nicht automatisch generieren oder eine Vorlage oder Beispiel-APP innerhalb einer Projekt Mappe anpassen.

1. [Melden](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Sie sich bei powerapps an.

1. Wechseln Sie ggf. in die Umgebung, in der die Lösung enthalten ist, in der Sie eine Canvas-app erstellen möchten.

1. Wählen Sie in der linken Navigationsleiste **Lösungen**aus.

    > [!div class="mx-imgBorder"]
    > ![Lösungs Option in der linken Navigationsleiste](./media/add-app-solution/left-nav.png "Lösungs Option in der linken Navigationsleiste")

1. Wählen Sie in der Liste der Lösungen die Lösung aus, in der Sie eine Canvas-app erstellen möchten.

1. Wählen Sie im Banner unter der Titelleiste die Option **neu** > **App** - > **Canvas-App**aus, und wählen Sie dann den Formular Faktor (Telefon oder Tablet) der APP aus, die Sie erstellen möchten.

    > [!div class="mx-imgBorder"]
    > ![Optionen zum Erstellen einer APP in einer Projekt Mappe](./media/add-app-solution/new-option.png "Optionen zum Erstellen einer APP in einer Projekt Mappe")

    PowerApps Studio wird mit einem leeren Zeichenbereich in einer anderen Browser Registerkarte geöffnet.

1. Erstellen Sie Ihre APP (oder nehmen Sie mindestens eine Änderung vor), und speichern Sie dann die Änderungen.

1. Wählen Sie auf der Registerkarte Browser, auf der Sie die Projekt Mappe ausgewählt haben, die Option **abgeschlossen** aus, um die Liste mit den Komponenten in der

    > [!div class="mx-imgBorder"]
    > ![Schaltfläche ""](./media/add-app-solution/done-button.png "Schaltfläche „Fertig“")

    Die neue APP wird in der Liste der Komponenten für diese Lösung angezeigt. Wenn Sie Änderungen an Ihrer APP speichern, werden Sie in der Version angezeigt, die sich in der Projekt Mappe befindet.

## <a name="link-an-existing-canvas-app-to-a-solution"></a>Eine vorhandene Canvas-App mit einer Projekt Mappe verknüpfen

Wenn Sie eine APP mit einer Projekt Mappe verknüpfen möchten, müssen sich beide in der gleichen Umgebung befinden, und die APP muss in einer Projekt Mappe erstellt worden sein.

1. [Melden](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Sie sich bei powerapps an.

1. Wechseln Sie ggf. in die Umgebung, in der die Projekt Mappe enthalten ist, mit der Sie eine APP verknüpfen möchten.

1. Wählen Sie in der linken Navigationsleiste **Lösungen**aus.

    > [!div class="mx-imgBorder"]
    > ![Lösungs Option in der linken Navigationsleiste](./media/add-app-solution/left-nav.png "Lösungs Option in der linken Navigationsleiste")

1. Wählen Sie in der Liste der Lösungen die Lösung aus, mit der Sie eine APP verknüpfen möchten.

1. Wählen Sie im Banner unter der Titelleiste vorhandene > **App** > Canvas- **App** **Hinzufügen** aus.

    > [!div class="mx-imgBorder"]
    > ![Banner Optionen zum Verknüpfen einer vorhandenen APP](./media/add-app-solution/add-existing.png "Banner Optionen zum Verknüpfen einer vorhandenen APP")

    Eine Liste von Canvas-apps, die in einer Projekt Mappe in dieser Umgebung erstellt wurden, wird angezeigt.

1. Wählen Sie in der Liste der apps die APP aus, die Sie mit der Projekt Mappe verknüpfen möchten, und klicken Sie dann auf **Hinzufügen**.

    > [!div class="mx-imgBorder"]
    > ![Schaltfläche Hinzufügen](./media/add-app-solution/add-button.png "Hinzufügen einer Schaltfläche")

## <a name="known-limitations"></a>Bekannte Einschränkungen

Informationen zu bekannten Einschränkungen finden Sie unter [Verwenden von Lösungen in powerapps](../common-data-service/use-solution-explorer.md#known-limitations). 

## <a name="next-steps"></a>Nächste Schritte

- Erstellen oder verknüpfen Sie weitere apps und [andere Komponenten](../common-data-service/use-solution-explorer.md), z. b. Entitäten, Flows und Dashboards, mit Ihrer Lösung.
- [Exportieren Sie Ihre Lösung](../common-data-service/import-update-export-solutions.md) , damit Sie Sie in einer anderen Umgebung, in appsource usw. bereitstellen können.
