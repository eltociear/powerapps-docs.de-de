---
title: Speichern und Veröffentlichen einer Canvas-App | Microsoft-Dokumentation
description: Schrittanleitungen für App-Autoren zum Speichern und Veröffentlichung von Canvas-Apps
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 09/14/2017
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7a64c7e0eeff1a48385ea251597a9e8d91c075f1
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675337"
---
# <a name="save-and-publish-a-canvas-app-in-powerapps"></a>Speichern und Veröffentlichen einer Canvas-App in PowerApps
Wenn Sie Änderungen an einer Canvas-App speichern, veröffentlichen Sie diese automatisch nur für sich selbst und andere Benutzer, die über Berechtigungen zum Bearbeiten der App verfügen. Wenn Sie die Änderungen abgeschlossen haben, müssen Sie sie explizit veröffentlichen, um sie allen Benutzern zur Verfügung zu stellen, für die die App freigegeben ist.

Informationen zum Freigeben einer App finden Sie unter [Freigeben einer App](share-app.md).

## <a name="save-changes-to-an-app"></a>Speichern von Änderungen an einer App
Klicken oder tippen Sie in powerapps Studio im Menü **Datei** (auf der linken Seite) auf **Speichern** , und führen Sie dann einen der folgenden Schritte aus:

* Wenn Sie die App zuvor noch nicht gespeichert haben, geben Sie einen Namen für sie ein, und klicken oder tippen Sie auf **Speichern**.

    ![Speichern der neuen App](./media/save-publish-app/save-as.png)
* Wenn die App schon gespeichert wurde, klicken oder tippen Sie auf **Speichern**.  

    ![Speichern der aktualisierten App](./media/save-publish-app/save-app.png)

Powerapps kann die APP auch in regelmäßigen Abständen alle 2 Minuten speichern. Wenn Sie die APP einmal gespeichert haben, speichert Power apps weiterhin regelmäßig eine Version der APP, ohne dass der Benutzer die Aktion zum Speichern drücken oder tippen muss. Autoren können im Menü **Datei** auf der Registerkarte **Konto** die Einstellung **Automatisch speichern** aktivieren oder deaktivieren.

![Einstellung „Automatisch speichern“](./media/save-publish-app/autosave.png)

## <a name="publish-an-app"></a>Veröffentlichen einer Anwendung
1. Klicken oder tippen Sie in powerapps Studio im Menü **Datei** (auf der linken Seite) auf **Speichern** , und klicken oder tippen Sie dann auf **Diese Version veröffentlichen**.

    ![Veröffentlichen einer App](./media/save-publish-app/publish-app.png)
2. Tippen oder klicken Sie im Dialogfeld **Veröffentlichen** auf **Diese Version veröffentlichen**, um die App für alle Benutzer zu veröffentlichen, für die die App freigegeben ist.

   ![Überprüfen der Veröffentlichung](./media/save-publish-app/publish-review.png)

   > [!NOTE]
   > Wenn Sie eine Canvas-App veröffentlichen, wird Ihre APP so aktualisiert, dass Sie auf der neuesten Version von powerapps ausgeführt wird – das bedeutet, dass Sie alle neuesten Features und Leistungs Upgrades, die wir seit der letzten Veröffentlichung hinzugefügt haben, nutzen werden. Wenn Sie seit mehreren Monaten kein Update veröffentlicht haben, werden Sie jetzt beim Veröffentlichen vermutlich eine deutliche Leistungsverbesserung bemerken.

## <a name="identify-the-live-version"></a>Bestimmen der Liveversion
Klicken oder tippen Sie auf [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) im Menü **Datei** (auf der linken Seite) auf **Apps**, dann auf das Symbol „Details“ einer App und schließlich auf die Registerkarte **Versionen**.

Die **Liveversion** wird für alle Benutzer veröffentlicht, für die die App freigegeben ist. Die neueste Version einer App ist nur für diejenigen verfügbar, die über Berechtigungen zum Bearbeiten der App verfügen.

![Veröffentlichen über das Portal](./media/save-publish-app/publish-portal.png)

Um die neueste Version zu veröffentlichen, klicken oder tippen Sie auf **Diese Version veröffentlichen** und dann im Dialogfeld **Veröffentlichen** auf **Diese Version veröffentlichen**.

## <a name="next-steps"></a>Nächste Schritte
* Suchen Sie die APP, und führen Sie Sie in einem [Browser](../../user/run-app-browser.md) oder auf einem [Telefon](../../user/run-app-client.md)aus.
* [Umbenennen einer App](set-name-tile.md) auf powerapps.com.
* [Wiederherstellen einer App](restore-an-app.md), wenn Sie mehrere Versionen einer App haben.
