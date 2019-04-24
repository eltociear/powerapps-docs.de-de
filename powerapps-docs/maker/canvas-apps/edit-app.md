---
title: Bearbeiten einer Canvas-App | Microsoft-Dokumentation
description: Hier finden Sie Schrittanleitungen zum Bearbeiten von Canvas-Apps und Szenarien mit gesperrten Sitzungen in PowerApps.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/19/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 03a6f9939f5de5e4eb3f4abd941a725ce24b46fb
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61550208"
---
# <a name="edit-a-canvas-app-in-powerapps"></a>Bearbeiten einer Canvas-App in PowerApps
Sie können alle Canvas-Apps bearbeiten, die Sie erstellt haben, deren Besitzer Sie sind oder für die Sie die Berechtigung **Kann bearbeiten** haben. Sie können eine App in PowerApps Studio bearbeiten. Wenn Sie versuchen, eine App zu bearbeiten, die an anderer Stelle zur Bearbeitung geöffnet ist, gibt eine Meldung Aufschluss darüber, ob Sie oder ein anderer Benutzer sie bereits geöffnet hat.

## <a name="verify-your-permissions"></a>Überprüfen Ihrer Berechtigungen
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, und klicken oder tippen Sie im Menü **Datei** auf der linken Seite auf **Apps**.
   
    ![Option „Apps“ im Menü „Datei“](./media/edit-app/file-apps.png)

2. Klicken oder tippen Sie in der App-Kategorieauswahl auf **Apps, die ich bearbeiten kann**.

    Sie können alle Apps in der angezeigten Liste bearbeiten. Sie können auch nach einer App suchen, indem Sie in das Suchfeld rechts oben ein oder mehrere Zeichen eingeben.

    > [!NOTE]
    > Wenn die App, die Sie bearbeiten möchten, immer noch nicht angezeigt wird, überprüfen Sie rechts oben, ob Sie die richtige Umgebung ausgewählt haben.
   
    ![Liste der Umgebungen](./media/edit-app/environment-list.png)

1. Klicken oder tippen Sie für die App, die Sie bearbeiten möchten, auf die Auslassungspunkte (...), und klicken oder tippen Sie anschließend auf **Bearbeiten**.

## <a name="collaborate-on-an-app"></a>Zusammenarbeiten an einer App
Jeder Benutzer mit der Berechtigung **Bearbeiten** für eine App kann diese bearbeiten. Doch die App kann immer nur von einem Benutzer gleichzeitig bearbeitet werden. Wenn Sie versuchen, eine App zu bearbeiten, die bereits von einem anderen Benutzer bearbeitet wird, wird diese Meldung angezeigt. Sie können erst fortfahren, nachdem der andere Benutzer die App geschlossen hat (oder ein Timeout der Sitzung des Benutzers eintritt).

![](./media/edit-app/applock-otheruser.png)

Darüber hinaus wird diese Meldung angezeigt, wenn Sie eine App zur Bearbeitung öffnen und versuchen, sie auf einem anderen Gerät oder in einem anderen Browserfenster zu öffnen. Sie können die vorherige Sitzung überschreiben, aber Sie verlieren möglicherweise alle Änderungen, die Sie nicht gespeichert haben.

![](./media/edit-app/applock-selfuser.png)

## <a name="next-steps"></a>Nächste Schritte
Erfahren Sie mehr dazu, wie Sie einen [Bildschirm](add-screen-context-variables.md), ein [Steuerelement](add-configure-controls.md) oder eine [Datenverbindung](add-data-connection.md) hinzufügen.

