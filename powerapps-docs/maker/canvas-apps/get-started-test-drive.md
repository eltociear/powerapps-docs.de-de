---
title: Erstellen einer Canvas-App aus einer Vorlage | Microsoft-Dokumentation
description: Hier finden Sie eine ausführliche Anleitung zum automatischen Erstellen einer Canvas-App auf Grundlage einer Power Apps-Vorlage.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/29/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d64b1ef3f6d885093fc9f89ecf31b785c07ea6bd
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918755"
---
# <a name="create-a-canvas-app-from-a-template-in-power-apps"></a>Erstellen einer Canvas-App aus einer Vorlage in Power Apps

Erstellen Sie eine Canvas-App automatisch aus einer Vorlage für ein bestimmtes Szenario, z.B. das Nachverfolgen von Budgets oder das Planen von Urlauben, und führen Sie die App dann aus, um deren Standardverhalten nachvollziehen zu können.

Sie benötigen ein Cloudspeicherkonto (z.B. Dropbox, OneDrive oder Google Drive), um die Beispieldaten von Vorlagen zu speichern und eine App aus einer Vorlage zu erstellen.

Wenn Sie keine Lizenz für Power Apps haben, können Sie sich [kostenlos registrieren](../signup-for-powerapps.md).

## <a name="create-an-app"></a>Erstellen einer App

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1. Klicken Sie im linken Navigationsbereich auf **Apps**. Klicken Sie auf das Dropdownmenü **Neue App**, und wählen Sie **Canvas** aus.

    ![Neue Canvas-App](./media/get-started-test-drive/new-canvas-app.png)

    Dadurch wird [Power Apps Studio](https://docs.microsoft.com/powerapps/powerapps-overview#power-apps-for-app-makerscreators) in einer neuen Registerkarte geöffnet.

1. Klicken Sie bei der Kachel **App-Vorlagen** auf **Smartphonelayout** oder auf **Tabletlayout**.

    ![Kachel „App aus Vorlage“](./media/get-started-test-drive/template-tile.png)

1. Wählen Sie eine Vorlage aus der Liste aus, und klicken Sie anschließend rechts unten auf **Verwenden**.

    ![Power Apps-Vorlage öffnen](./media/get-started-test-drive/open-template.png)

    Power Apps Studio wird in einer neuen Registerkarte geöffnet, und die App wird erstellt.

    > [!NOTE]
    > Wenn die Schaltfläche **Verwenden** deaktiviert ist, müssen Sie eine Datenquelle für die App auswählen. Klicken Sie dazu unten auf **Auswählen**.
    >
    > ![Datenquelle auswählen](./media/get-started-test-drive/choose-data-source.png)

## <a name="run-the-app"></a>Ausführen der App
Eine App aus einer Vorlage wird im Standardarbeitsbereich geöffnet, wo Sie den größten Teil Ihrer Zeit mit Anpassen verbringen. Testen Sie, wie die App im **Vorschaumodus** funktioniert, bevor Sie Änderungen an der App vornehmen.

1. Drücken Sie F5 (oder klicken oder tippen Sie auf den Pfeil nach rechts in der oberen rechten Ecke), um die App im **Vorschaumodus** zu öffnen.

    ![Schaltfläche zum Öffnen der Vorschau](./media/get-started-test-drive/open-preview.png)

    Die App wird mit Beispieldaten zur Veranschaulichung der Funktionalität der App aufgefüllt. Die App für die Kostenschätzung enthält z.B. Daten für das Erstellen von Beauftragungen und die Schätzung der Kosten für die Installation eines bestimmten Fußbodenprodukts in einem Raum einer bestimmten Größe.

4. Testen Sie das Standardverhalten der App, indem Sie Beispieldaten erstellen, aktualisieren und löschen. Überprüfen Sie dann, ob die Daten in Ihrem Cloudspeicherkonto Ihre Änderungen wiedergeben.

    Machen Sie beispielsweise eine Beauftragung, und erstellen Sie eine Kostenschätzung in der App für die Kostenschätzung.

5. Kehren Sie durch Drücken der ESC-TASTE oder durch Klicken oder Tippen auf das Symbol **X** in der oberen rechten Ecke zum Standardarbeitsbereich zurück.

## <a name="next-steps"></a>Nächste Schritte
1. Drücken Sie STRG+S, geben Sie Ihre App einen Namen, und klicken oder tippen Sie anschließend auf **Save** (Speichern), um Ihre App in der Cloud zu speichern.

1. Mit [Share your app](share-app.md) (App freigeben) stellen Sie Ihre App anderen Personen zur Verfügung.

> [!IMPORTANT]
> Stellen Sie vor dem Freigeben einer App sicher, dass die Personen, für die Sie die App freigeben, auf die Daten zugreifen können. Beispielsweise müssen Sie [eine Excel- oder andere Datei freigeben](share-app-data.md) über ein Cloudspeicherkonto durchführen.
