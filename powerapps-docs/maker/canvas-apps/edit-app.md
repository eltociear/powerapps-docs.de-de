---
title: Bearbeiten einer App | Microsoft-Dokumentation
description: Detaillierte Anleitungen zum Bearbeiten von Apps und zu Szenarien mit gesperrten Sitzungen
author: karthik-1
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/19/2017
ms.author: sharik
ms.openlocfilehash: b1e9f514973313a1028aa3b1958bf8e01ff2c167
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2018
ms.locfileid: "39023779"
---
# <a name="edit-an-app-in-powerapps"></a>Bearbeiten einer App in PowerApps
Sie können alle Apps bearbeiten, die Sie erstellt haben, deren Besitzer Sie sind oder für die Sie die Berechtigung **Bearbeiten** haben. Sie können eine App in PowerApps Studio bearbeiten. Wenn Sie versuchen, eine App zu bearbeiten, die an anderer Stelle zur Bearbeitung geöffnet ist, gibt eine Meldung Aufschluss darüber, ob Sie oder ein anderer Benutzer sie bereits geöffnet hat.

## <a name="verify-your-permissions"></a>Überprüfen Ihrer Berechtigungen
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com) an, und klicken oder tippen Sie im Menü **Datei** auf der linken Seite auf **Apps**.
   
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

