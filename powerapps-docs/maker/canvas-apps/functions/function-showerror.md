---
title: Notify-Funktion | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktion "Benachrichtigen" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/28/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9a4facf4689ed09e7628411f1c55739f8980336f
ms.sourcegitcommit: 129d004e3d33249b21e8f53e0217030b5c28b53f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78265535"
ms.PowerAppsDecimalTransform: true
---
# <a name="notify-function-in-power-apps"></a>Funktion "Benachrichtigen" in powerapps
Zeigt dem Benutzer eine Bannermeldung an.

## <a name="description"></a>Beschreibung
Über die **Benachrichtigungsfunktion** wird dem Benutzer im oberen Bereich des Bildschirms eine Bannermeldung über der zu diesem Zeitpunkt geöffneten Seite angezeigt.  Die Benachrichtigung bleibt erhalten, bis Sie vom Benutzer geschlossen wird, Sie durch eine andere Benachrichtigung ersetzt wird oder das Timeout abläuft, das standardmäßig 10 Sekunden beträgt.

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

Powerapps kann auch Pushbenachrichtigungen mit einem völlig anderen Mechanismus als **Benachrichtigung**senden.  Weitere Informationen finden [Sie unter Senden einer Benachrichtigung in powerapps](../add-notifications.md).

**Notify** gibt immer *TRUE* zurück.

Hinweis: Diese Funktion hatte in der Vergangenheit den Namen **ShowError**, wenn nur Fehlermeldungen angezeigt werden konnten.

## <a name="syntax"></a>Syntax
**Benachrichtigen**( *Meldung* [; *NOTIFICATIONTYPE* [; *Timeout* ]])

* *Message* – Erforderlich.  Meldung, die dem Benutzer angezeigt wird.
* *NotificationType* – Optional.  In der obenstehenden Tabelle aufgelisteter Meldungstyp, der angezeigt werden soll.  Standardmäßig wird **NotificationType.Information** angezeigt.  
* *Timeout* – optional.  Anzahl der Millisekunden, die gewartet werden soll, bevor die Benachrichtigung automatisch verworfen wird.  Der Standardwert ist 10 Sekunden (oder 10.000 Millisekunden).  Die Benachrichtigung wird unbegrenzt mit einem *Timeout* von 0 angezeigt.

## <a name="examples"></a>Beispiele

### <a name="step-by-step"></a>Schritt für Schritt

1. Fügen Sie der Anzeige ein **Schaltflächen-Steuerelement** („Button“) hinzu.

2. Legen **Sie die onselect** -Eigenschaft der **Schaltfläche** auf die folgende Formel fest:

    ```powerapps-comma
    Notify( "Hello, World" )
    ```

3. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.  

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als Information angezeigt.  Sie wird automatisch in 10 Sekunden geschlossen (Standard Timeout), wenn der Benutzer Sie nicht schließt oder die Schaltfläche erneut drückt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem blauen Banner angezeigt wird.](media/function-showerror/hello-world.png)

4. Ändern Sie den Meldungstyp, damit ein Fehler angezeigt wird.  Fügen Sie ein zweites Argument zu der Formel hinzu:

    ```powerapps-comma
    Notify( "Hello, World"; NotificationType.Error )
    ```

5. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als ein Fehler angezeigt.  Sie wird automatisch in 10 Sekunden geschlossen (Standard Timeout), wenn der Benutzer Sie nicht schließt oder die Schaltfläche erneut drückt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem roten Banner angezeigt wird.](media/function-showerror/hello-world-error.png)

4. Ändern Sie den Meldungstyp, damit eine Warnung angezeigt wird.  Ändern Sie das zweite Argument in der Formel:

    ```powerapps-comma
    Notify( "Hello, World"; NotificationType.Warning; 4000 )
    ```

5. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als Warnung angezeigt.  Sie wird automatisch in 4 Sekunden (4.000 Millisekunden) geschlossen, wenn der Benutzer Sie nicht schließt oder die Schaltfläche erneut drückt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem orangen Banner angezeigt wird.](media/function-showerror/hello-world-warning.png)

4. Ändern Sie den Meldungstyp, damit ein Erfolg angezeigt wird.  Ändern Sie das zweite Argument in der Formel:

    ```powerapps-comma
    Notify( "Hello, World"; NotificationType.Success; 0 )
    ```

5. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.

    Bei jedem Klick auf die Schaltfläche wird dem Benutzer die Meldung **Hello, World** als Erfolg angezeigt.  Bei einem Timeout von **0** wird die Benachrichtigung nur vom Benutzer oder durch erneutes Drücken der Schaltfläche verworfen.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch Button.OnSelect wird Notify aufgerufen, wodurch die Meldung „Hello, World“ dem Benutzer auf einem grünen Banner angezeigt wird.](media/function-showerror/hello-world-success.png)
