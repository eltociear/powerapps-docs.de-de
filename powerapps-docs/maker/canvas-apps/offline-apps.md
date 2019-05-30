---
title: Entwickeln von offlinefähigen Canvas-Apps | Microsoft-Dokumentation
description: Entwickeln Sie offlinefähige Canvas-Apps, damit Ihre Benutzer online und offline stets produktiv sein können.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/31/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8004a39e83ea3615ce8a77637a9f5c0271b67781
ms.sourcegitcommit: 157ab15738e2d0d1bf9097bbb7b9e3d9c29a4015
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66265731"
---
# <a name="develop-offline-capable-canvas-apps"></a>Entwickeln von offlinefähigen Canvas-Apps

Mobile Benutzer häufig zum produktiven arbeiten benötigen sogar wenn sie nur eine eingeschränkte oder keine Verbindung. Wenn Sie eine Canvas-app erstellen, können Sie diese Aufgaben ausführen:

- PowerApps Mobile öffnen und Ausführen von Offline-apps.
- Mithilfe des Signalobjekts [Connection](../canvas-apps/functions/signals.md#connection) bestimmen, ob eine App offline, online oder in einer getakteten Verbindung ist.
- Verwenden von [Sammlungen](../canvas-apps/create-update-collection.md) und Nutzung von Funktionen wie [LoadData und SaveData](../canvas-apps/functions/function-savedata-loaddata.md), um offline grundlegende Datenspeicherung zur Verfügung zu machen.

## <a name="limitations"></a>Einschränkungen

**LoadData** und **SaveData** kombinieren, um einen einfachen Mechanismus zum Speichern von kleine Mengen von Daten auf einem lokalen Gerät zu erstellen. Mithilfe dieser Funktionen können Sie einfache Offlinefunktionen zu Ihrer app hinzufügen.

Diese Funktionen werden durch die Größe des verfügbaren app-Speichers begrenzt, da sie in einer in-Memory-Sammlung ausgeführt werden. Verfügbare Arbeitsspeicher kann variieren, je nach Gerät, das Betriebssystem, den Arbeitsspeicher, den PowerApps Mobile verwendet und die Komplexität der app im Hinblick auf Bildschirme und Steuerelemente. Wenn Sie länger als einige Megabyte an Daten speichern, testen Sie Ihre app mit erwarteten Szenarien auf den Geräten, die auf denen Sie es erwarten. Sie müssen in der Regel 30 bis 70 MB des verfügbaren Arbeitsspeichers.

Die Funktionen auflösen nicht auch automatisch Mergekonflikte, wenn ein Gerät online geschaltet wird. Konfiguration auf welche Daten gespeichert werden und das Durchführen von erneuten Herstellen einer Verbindung verwendet wird, obliegt der Ersteller beim Schreiben von Ausdrücken.

Für Updates auf Offlinefunktionen, kehren Sie zu diesem Thema zurück, und Abonnieren der [PowerApps-Blog](https://powerapps.microsoft.com/blog/).

## <a name="overview"></a>Übersicht

Wenn Sie offline-Szenarien entwerfen, sollten Sie zunächst, wie Ihre apps mit Daten arbeiten. Apps in PowerApps greifen auf Daten hauptsächlich durch eine Reihe von [Connectors](../canvas-apps/connections-list.md) , die die Plattform bereitstellt, z. B. SharePoint, Office 365 und Common Data Service. Darüber hinaus können Sie benutzerdefinierte Connectors erstellen, die Apps den Zugriff auf jeden Dienst ermöglichen, der einen RESTful-Endpunkt bereitstellt. Dabei kann es sich um eine Web-API oder um einen Dienst handeln, wie etwa Azure Functions. Alle diese Connectors verwenden HTTPS im Internet, was bedeutet, dass Ihre Benutzer online sein müssen, damit sie auf Daten und andere Funktionen zugreifen können, die von einem Dienst bereitgestellt werden.

![PowerApps-App mit Connectors](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>Verarbeitung von Offlinedaten

In PowerApps können Sie filtern, suchen, sortieren, aggregieren, und Bearbeiten von Daten auf konsistente Weise unabhängig von der Datenquelle. Quellen reichen von Auflistungen im Arbeitsspeicher in der app in SharePoint-Listen, SQL-Datenbanken und Common Data Service. Aufgrund dieser Konsistenz können Sie eine app, um eine andere Datenquelle verwenden problemlos neu zuweisen. Für Offlineszenarien, können Sie noch wichtiger: lokale Sammlungen für die datenverwaltung mit fast ohne Änderungen an der Logik einer app verwenden. Tatsächlich stellen lokale Sammlungen den wichtigsten Mechanismus in der Verarbeitung von Offlinedaten dar.

## <a name="build-an-offline-app"></a>Erstellen Sie eine offline-app

Um den Fokus bei den offlineaspekten der app-Entwicklung zu halten, wird in diesem Thema veranschaulicht, ein einfaches Szenarios, die sich auf Twitter konzentriert. Sie erstellen eine app, mit der Sie Twitter-Beiträge lesen und Tweets Absenden, während Sie offline. Wenn die App Zugang zu einer Onlineverbindung erhält, veröffentlicht sie die Tweets und lädt die lokalen Daten erneut.

Auf einer hohen Ebene führt die app folgende Aufgaben aus:

- Wenn der Benutzer die app öffnet:

  - Wenn das Gerät online ist, wird die app Ruft Daten über den Twitter-Connector ab und füllt eine Auflistung mit den Daten.
  - Wenn das Gerät offline ist, lädt die app die Daten aus einer lokalen Cachedatei mithilfe der [ **LoadData** ](../canvas-apps/functions/function-savedata-loaddata.md) Funktion.
  - Der Benutzer kann die Tweets übermitteln. Wenn die app online ist, die Tweets direkt in Twitter gepostet, und der lokalen Cache wird aktualisiert.

- Alle fünf Minuten, während die app online ist:

  - Die app sendet alle Tweets im lokalen Cache.
  - Die app wird der lokalen Cache aktualisiert und speichert sie mithilfe der [ **SaveData** ](../canvas-apps/functions/function-savedata-loaddata.md) Funktion.

### <a name="step-1-add-twitter-to-a-blank-phone-app"></a>Schritt 1: Hinzufügen von Twitter in eine leere Smartphone-app

1. Wählen Sie in PowerApps Studio, **Datei** > **neu**.
1. Wählen Sie auf der Kachel **Leere App** **Telefonlayout** aus.
1. Klicken Sie auf der Registerkarte **Ansicht** auf **Datenquellen**.
1. In der **Daten** wählen Sie im Bereich **Datenquelle hinzufügen**.
1. Wählen Sie **neue Verbindung** > **Twitter** > **erstellen**.
1. Geben Sie Ihre Anmeldeinformationen ein, erstellen Sie die Verbindung, und schließen Sie die **Daten** Bereich.

### <a name="step-2-collect-existing-tweets"></a>Schritt 2: Erfassen der vorhandenen tweets

1. In der **Strukturansicht** wählen Sie im Bereich **App**, und legen Sie dann die **OnStart** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    If( Connection.Connected,
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
            Set( statusText, "Online data" ),
        LoadData( LocalTweets, "LocalTweets", true );
            Set( statusText, "Local data" )
    );
    SaveData( LocalTweets, "LocalTweets" );
    ```

    > [!div class="mx-imgBorder"]
    > ![Formel zum Laden von tweets](./media/offline-apps/load-tweets.png)

1. In der **Strukturansicht** Bereich Wählen Sie die Auslassungszeichen für die **App** Objekt aus, und wählen Sie dann **OnStart ausführen** diese Formel ausgeführt.

    > [!div class="mx-imgBorder"]
    > ![Führen Sie die Formel zum Laden von tweets](./media/offline-apps/load-tweets-run.png)

    > [!NOTE]
    > Die **LoadData** und **SaveData** Funktionen möglicherweise ein Fehler in PowerApps Studio angezeigt, da der Browser diese nicht unterstützen. Allerdings werden sie normalerweise ausführen, nachdem Sie diese app auf einem Gerät bereitstellen.

Diese Formel wird überprüft, ob das Gerät online ist:

- Wenn das Gerät online ist, lädt die Formel bis zu 10 Tweets mit dem Suchbegriff "PowerApps" in einem **LocalTweets** Auflistung.
- Wenn das Gerät offline ist, lädt die Formel im lokalen Cache aus einer Datei namens "LocalTweets", sofern diese verfügbar ist.

### <a name="step-3-show-tweets-in-a-gallery"></a>Schritt 3: Anzeigen von Tweets in einem Katalog

1. Auf der **einfügen** Registerkarte **Katalog** > **leer flexible Höhe**.

1. Legen Sie die **Elemente** Eigenschaft der [ **Katalog** ](controls/control-gallery.md) die Steuerung an `LocalTweets`.

1. Fügen Sie in der Katalogvorlage drei [ **Bezeichnung** ](controls/control-text-box.md) Steuerelemente, und legen die **Text** -Eigenschaft jeder Bezeichnung auf einen der folgenden Werte:

    - `ThisItem.UserDetails.FullName & " (@" & ThisItem.UserDetails.UserName & ")"`
    - `Text(DateTimeValue(ThisItem.CreatedAtIso), DateTimeFormat.ShortDateTime)`
    - `ThisItem.TweetText`

1. Der Text fett in die letzte Bezeichnung so, dass der Katalog in diesem Beispiel ähnelt.

    > [!div class="mx-imgBorder"]
    > ![Katalog mit Beispiel-tweets](./media/offline-apps/tweet-gallery.png)

### <a name="step-4-show-connection-status"></a>Schritt 4: Verbindungsstatus angezeigt

1. Klicken Sie unter den Katalog, fügen Sie eine Bezeichnung, und legen Sie seine **Farbe** Eigenschaft **Red**.

1. Legen Sie die neuesten Bezeichnung **Text** -Eigenschaft auf diese Formel:

    `If( Connection.Connected, "Connected", "Offline" )`

Diese Formel wird bestimmt, ob das Gerät online ist. Wenn es sich handelt, die Bezeichnung zeigt **verbunden**ist, andernfalls zeigt **Offline**.

### <a name="step-5-add-a-box-to-compose-tweets"></a>Schritt 5: Fügen Sie ein Feld, um die compose-tweets

1. Fügen Sie unter der Bezeichnung Verbindungsstatus einer [ **Texteingabe** ](controls/control-text-input.md) steuern, und benennen Sie sie **NewTweetTextInput**.

1. Legen Sie das Texteingabe-Feld des **Standard** Eigenschaft `""`.

    > [!div class="mx-imgBorder"]
    > ![Katalog über Statusinformationen und Texteingabe-Feld](./media/offline-apps/status-input.png)

### <a name="step-6-add-a-button-to-post-the-tweet"></a>Schritt 6: Fügen Sie eine Schaltfläche zum Veröffentlichen des TWEETS

1. Unter dem Feld Texteingabe Hinzufügen einer **Schaltfläche** steuern, und legen dessen **Text** -Eigenschaft auf diesen Wert:

    `"Tweet"`

1. Legen Sie die **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    If( Connection.Connected,
        Twitter.Tweet( "", {tweetText: NewTweetTextInput.Text} ),
        Collect( LocalTweetsToPost, {tweetText: NewTweetTextInput.Text} );
            SaveData( LocalTweetsToPost, "LocalTweetsToPost" )
    );
    Reset( NewTweetTextInput );
    ```  

1. In der **OnStart** -Eigenschaft für die **App**, fügen Sie am Ende der Formel eine Zeile hinzu:

    ```powerapps-dot
    If( Connection.Connected,
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 100} ) );
            Set( statusText, "Online data" ),
        LoadData( LocalTweets, "LocalTweets", true );
            Set( statusText, "Local data" )
    );
    SaveData( LocalTweets, "LocalTweets" );
    LoadData( LocalTweetsToPost, "LocalTweetsToPost", true );  // added line
    ```

    > [!div class="mx-imgBorder"]
    > ![Führen Sie die Formel zum Laden von Tweets mit auskommentierungen aufgehoben wurden](./media/offline-apps/load-tweets-save.png)

Diese Formel wird bestimmt, ob das Gerät online ist:

- Wenn das Gerät online ist, sendet er sofort den Tweet.
- Wenn das Gerät offline ist, erfasst es den Tweet in einer **LocalTweetsToPost** Auflistung und speichert sie auf dem Gerät.

Klicken Sie dann setzt die Formel den Text in das Texteingabe-Feld zurück.

### <a name="step-7-check-for-new-tweets"></a>Schritt 7: Überprüfung auf neue tweets

1. Fügen Sie auf der rechten Seite der Schaltfläche eine **Timer** Steuerelement.

    > [!div class="mx-imgBorder"]
    > ![Letzte apps](./media/offline-apps/final-app.png)

1. Festlegen des Timers **Dauer** Eigenschaft **300000**.

1. Festlegen des Timers **AutoStart** und **wiederholen** Eigenschaften **"true"**.

1. Festlegen des Timers **OnTimerEnd** auf diese Formel:

    ```powerapps-dot
    If( Connection.Connected,
        ForAll( LocalTweetsToPost, Twitter.Tweet( "", {tweetText: tweetText} ) );
        Clear( LocalTweetsToPost );
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
        SaveData( LocalTweets, "LocalTweets" );
   )
    ```

Diese Formel wird bestimmt, ob das Gerät online ist. Wenn es sich handelt, die app von tweets alle Elemente in der **LocalTweetsToPost** Auflistung und löscht dann die Auflistung.

## <a name="test-the-app"></a>Testen der App

1. Öffnen Sie die app auf einem mobilen Gerät, das mit dem Internet verbunden ist.

    Vorhandene Tweets, die im Katalog angezeigt werden, und zeigt der Status **verbunden**.

1. Durch Aktivieren des Geräts flugzeugmodus, und deaktivieren wi-Fi, trennen Sie das Gerät über das Internet.

    Die statusbezeichnung zeigt an, dass die app **Offline**.

1. Während das Gerät offline ist, Schreiben Sie einen Tweet, der enthält **PowerApps**, und wählen Sie dann die **Tweet** Schaltfläche.

    TWEETS befindet sich lokal in der **LocalTweetsToPost** Auflistung.

1. Schließen Sie das Gerät mit dem Internet durch das Deaktivieren des Geräts flugzeugmodus, und aktivieren wi-Fi wieder.

    Innerhalb von fünf Minuten sendet die app den Tweet, der im Katalog angezeigt wird.

Wir hoffen, dass dieser Artikel Ihnen eine Vorstellung von den Möglichkeiten gegeben hat, die PowerApps für das Erstellen von Offline-Apps bietet. Wie immer freuen wir uns über Ihr Feedback in unserem [Forum](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1) und über Ihre Beispiele für Offline-Apps im [PowerApps Community-Blog](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog).