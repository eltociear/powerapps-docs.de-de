---
title: ShowError-Funktion | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die ShowError-Funktion in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/05/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5e18b64910bbc7efca8c460100163e1a0716a089
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992157"
---
# <a name="notify-function-in-powerapps"></a>Benachrichtigungsfunktion in PowerApps
Zeigt dem Benutzer eine Bannermeldung an.

## <a name="description"></a>Beschreibung
Über die **Benachrichtigungsfunktion** „Notify“ wird dem Benutzer im oberen Bereich des Bildschirms eine Bannermeldung über der zu diesem Zeitpunkt geöffneten Seite angezeigt.  

Abhängig vom Typ der Meldung werden eine passende Farbe und ein passendes Symbol angezeigt.   Der Typ wird vom zweiten Argument der Funktion angegeben:

| NotificationType-Argument | Beschreibung |
| --- | --- |
| **NotificationType.Error** | Zeigt eine Fehlermeldung an. |
| **NotificationType.Information** (Standard) | Zeigt eine Informationsmeldung an.  |
| **NotificationType.Success** | Zeigt eine Erfolgsmeldung an. |
| **NotificationType.Warning** | Zeigt eine Warnmeldung an. |

Die Meldungen werden beim Erstellen der App und beim Verwenden der App durch die Endbenutzer angezeigt.

**Notify** kann ausschließlich in [Verhaltensformeln eingesetzt werden](../working-with-formulas-in-depth.md).

**Notify** kann zusammen mit der [**IfError**](function-iferror.md)-Funktion verwendet werden. Dadurch können Fehler erkannt und mit einer benutzerdefinierten Fehlernachricht gemeldet werden.

PowerApps kann auch über einen anderen Mechanismus, der sich gänzlich von **Notify** unterscheidet, Pushbenachrichtigungen senden.  Weitere Informationen finden Sie unter [Senden einer Pushbenachrichtigung in PowerApps](../add-notifications.md).

**Notify** gibt immer *TRUE* zurück.

Nebenbei Diese Funktion hieß zuvor " **ShowError** ", als Sie nur Fehlermeldungen anzeigen konnte.

## <a name="syntax"></a>Syntax
**Notify**( *Message*, [ *NotificationType* ] )

* *Message* – Erforderlich.  Meldung, die dem Benutzer angezeigt wird.
* *NotificationType* – Optional.  In der obenstehenden Tabelle aufgelisteter Meldungstyp, der angezeigt werden soll.  Standardmäßig wird **NotificationType.Information** angezeigt.  

## <a name="examples"></a>Beispiele

### <a name="step-by-step"></a>Schritt für Schritt

1. Fügen Sie der Anzeige ein **Schaltflächen-Steuerelement** („Button“) hinzu.

2. Legen Sie die Eigenschaft **OnSelect** der **Schaltfläche** auf die folgende Formel fest:

    **Notify( "Hello, World" )**

3. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.  

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als Information angezeigt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem blauen Banner angezeigt wird.](media/function-showerror/hello-world.png)

4. Ändern Sie den Meldungstyp, damit ein Fehler angezeigt wird.  Fügen Sie ein zweites Argument zu der Formel hinzu:

    **Notify( "Hello, World", NotificationType.Error )**

5. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als ein Fehler angezeigt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem roten Banner angezeigt wird.](media/function-showerror/hello-world-error.png)

4. Ändern Sie den Meldungstyp, damit eine Warnung angezeigt wird.  Ändern Sie das zweite Argument in der Formel:

    **Notify( "Hello, World", NotificationType.Warning )**

5. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als Warnung angezeigt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem orangen Banner angezeigt wird.](media/function-showerror/hello-world-warning.png)

4. Ändern Sie den Meldungstyp, damit ein Erfolg angezeigt wird.  Ändern Sie das zweite Argument in der Formel:

    **Notify( "Hello, World", NotificationType.Success )**

5. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als Erfolg angezeigt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem grünen Banner angezeigt wird.](media/function-showerror/hello-world-success.png)
