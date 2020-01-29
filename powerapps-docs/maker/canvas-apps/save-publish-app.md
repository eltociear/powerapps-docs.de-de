---
title: Speichern und Veröffentlichen einer Canvas-App | Microsoft-Dokumentation
description: Schrittanleitungen für App-Autoren zum Speichern und Veröffentlichung von Canvas-Apps
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/23/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 740107af85e59baf44c6cfbe89eb62a42daa08a2
ms.sourcegitcommit: b250e63e881d9bd10c0b3dea36c7f12e8a9c6ac2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2020
ms.locfileid: "76750690"
---
# <a name="save-and-publish-a-canvas-app-in-power-apps"></a>Speichern und Veröffentlichen einer Canvas-App in Power Apps
Wenn Sie Änderungen an einer Canvas-App speichern, veröffentlichen Sie diese automatisch nur für sich selbst und andere Benutzer, die über Berechtigungen zum Bearbeiten der App verfügen. Wenn Sie die Änderungen abgeschlossen haben, müssen Sie sie explizit veröffentlichen, um sie allen Benutzern zur Verfügung zu stellen, für die die App freigegeben ist.

Informationen zum Freigeben einer App finden Sie unter [Freigeben einer App](share-app.md).

## <a name="save-changes-to-an-app"></a>Speichern von Änderungen an einer App
Klicken Sie in Power Apps Studio im Menü **Datei** (auf der linken Seite) auf **Speichern**, und führen Sie dann einen der folgenden Schritte aus:

* Wenn Sie die App zuvor noch nicht gespeichert haben, geben Sie einen Namen für sie ein, und klicken Sie auf **Speichern**.

    ![Speichern der neuen App](./media/save-publish-app/save-as.png)
* Wenn die App schon gespeichert wurde, klicken Sie auf **Speichern**. Sie können auch versionsspezifische Hinweise oder Kommentare hinterlassen.  

    ![Speichern der aktualisierten App](./media/save-publish-app/save-app.png)

Die App kann auch automatisch alle 2 Minuten von Power Apps gespeichert werden. Wenn Sie die App einmal gespeichert haben, speichert Power Apps anschließend regelmäßig eine Version der App, ohne dass der Benutzer auf „Speichern“ klicken oder tippen muss. Autoren können im Menü **Datei** auf der Registerkarte **Konto** die Einstellung **Automatisch speichern** aktivieren oder deaktivieren.

![Einstellung „Automatisch speichern“](./media/save-publish-app/autosave.png)

## <a name="publish-an-app"></a>Veröffentlichen einer App
1. Klicken Sie in Power Apps Studio im Menü **Datei** (auf der linken Seite) auf **Speichern**, und führen Sie dann **Veröffentlichen** aus.

    ![App veröffentlichen](./media/save-publish-app/publish-app.png)
2. Klicken Sie im Dialogfeld **Veröffentlichen** auf **Diese Version veröffentlichen**, um die App für alle Benutzer zu veröffentlichen, für die die App freigegeben ist.

   ![Überprüfen der Veröffentlichung](./media/save-publish-app/publish-review.png)

   > [!NOTE]
   > Wenn Sie eine Canvas-App veröffentlichen, wird für Ihre App ein Upgrade auf die aktuelle Power Apps-Version durchgeführt, sodass Sie von den aktuellen Features und Leistungsverbesserungen profitieren können, die hinzugefügt wurden, seitdem Sie das letzte Mal eine Veröffentlichung vorgenommen haben. Wenn Sie seit mehreren Monaten kein Update veröffentlicht haben, werden Sie jetzt beim Veröffentlichen vermutlich eine deutliche Leistungsverbesserung bemerken.

## <a name="identify-the-live-version"></a>Bestimmen der Liveversion
Klicken Sie unter [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) im Menü **Datei** (auf der linken Seite) auf **Apps**, klicken Sie auf das Symbol „Details“ für eine App, und wählen Sie schließlich die Registerkarte **Versionen** aus.

Die **Liveversion** wird für alle Benutzer veröffentlicht, für die die App freigegeben ist. Die neueste Version einer App ist nur für diejenigen verfügbar, die über Berechtigungen zum Bearbeiten der App verfügen.

![Veröffentlichen über das Portal](./media/save-publish-app/publish-portal.png)

Um die neueste Version zu veröffentlichen, markieren Sie die Version, und klicken Sie auf die Auslassungspunkte (...). Wählen Sie anschließend im Dropdownmenü **Diese Version veröffentlichen** aus.

## <a name="next-steps"></a>Nächste Schritte
* Suchen Sie die App, und führen Sie sie in einem [Browser](../../user/run-app-browser.md) oder auf einem [Telefon](../../user/run-app-client.md) aus.
* [Umbenennen einer App](set-name-tile.md) auf powerapps.com.
* [Wiederherstellen einer App](restore-an-app.md), wenn Sie mehrere Versionen einer App haben.
