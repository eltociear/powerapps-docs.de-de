---
title: Entwickeln von offlinefähigen Canvas-Apps | Microsoft-Dokumentation
description: Entwickeln Sie offlinefähige Canvas-Apps, damit Ihre Benutzer online und offline stets produktiv sein können.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/29/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6ec1a55713b3cce0a98c02058124b5b3d159b376
ms.sourcegitcommit: 129d004e3d33249b21e8f53e0217030b5c28b53f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78265565"
---
# <a name="develop-offline-capable-canvas-apps"></a>Entwickeln von offlinefähigen Canvas-Apps

Mobile Benutzer müssen häufig produktiv sein, auch wenn Sie über eingeschränkte oder keine Konnektivität verfügen. Wenn Sie eine Canvas-app erstellen, können Sie folgende Aufgaben ausführen:

- Öffnen Sie powerapps Mobile, und führen Sie apps Offline aus.
- Mithilfe des Signalobjekts [Connection](functions/signals.md#connection) bestimmen, ob eine App offline, online oder in einer getakteten Verbindung ist.
- Verwenden Sie Auflistungen, [und nutzen Sie](create-update-collection.md) die [ **LoadData** -Funktion und die **SaveData** -](functions/function-savedata-loaddata.md) Funktion für die grundlegende Datenspeicherung

Dieser Artikel enthält ein Beispiel für die Verwendung von Twitter-Daten.  Ein noch einfacheres Beispiel, das keine Verbindung erfordert, ist in der [Funktionsreferenz " **LoadData** " und " **SaveData** ](functions/function-savedata-loaddata.md)" enthalten.

## <a name="limitations"></a>Einschränkungen

**LoadData** und **SaveData** bilden einen einfachen Mechanismus zum Speichern kleiner Datenmengen auf einem lokalen Gerät. Mithilfe dieser Funktionen können Sie Ihrer app einfache Offline Funktionen hinzufügen.

Diese Funktionen sind durch die Menge des verfügbaren APP-Speichers beschränkt, da Sie für eine Auflistung im Arbeitsspeicher ausgeführt werden. Der verfügbare Arbeitsspeicher kann abhängig vom Gerät, dem Betriebssystem, dem von Power Apps Mobile verwendeten Arbeitsspeicher und der Komplexität der app in Bezug auf Bildschirme und Steuerelemente variieren. Wenn Sie mehr als ein paar Megabyte Daten speichern, testen Sie Ihre APP mit den erwarteten Szenarien auf den Geräten, auf denen Sie erwarten, dass Sie ausgeführt werden. In der Regel verfügen Sie über 30-70 Megabyte an verfügbarem Arbeitsspeicher.

Die Funktionen lösen auch Mergekonflikte nicht automatisch auf, wenn ein Gerät online geschaltet wird. Die Konfiguration, welche Daten gespeichert werden und wie die erneute Verbindung gehandhabt wird, ist beim Schreiben von Ausdrücken der Ersteller.

Weitere Informationen zu Offline Funktionen erhalten Sie, wenn Sie zu diesem Thema zurückkehren und den [Blog zu Power apps](https://powerapps.microsoft.com/blog/)abonnieren.

## <a name="overview"></a>Übersicht

Beim Entwerfen von Offline Szenarien sollten Sie zuerst berücksichtigen, wie Ihre apps mit Daten arbeiten. Apps in Power apps greifen in erster Linie auf Daten über eine Reihe von [Connectors](../canvas-apps/connections-list.md) zu, die die Plattform bereitstellt, z. b. SharePoint, Office 365 und Common Data Service. Darüber hinaus können Sie benutzerdefinierte Connectors erstellen, die Apps den Zugriff auf jeden Dienst ermöglichen, der einen RESTful-Endpunkt bereitstellt. Dabei kann es sich um eine Web-API oder um einen Dienst handeln, wie etwa Azure Functions. Alle diese Connectors verwenden HTTPS im Internet, was bedeutet, dass Ihre Benutzer online sein müssen, damit sie auf Daten und andere Funktionen zugreifen können, die von einem Dienst bereitgestellt werden.

![Powerapps-App mit Connectors](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>Verarbeitung von Offlinedaten

In powerapps können Sie Daten unabhängig von der Datenquelle auf konsistente Weise filtern, durchsuchen, sortieren, Aggregieren und bearbeiten. Quellen reichen von in-Memory-Auflistungen in der APP zu SharePoint-Listen bis hin zu SQL-Datenbanken und Common Data Service. Aufgrund dieser Konsistenz können Sie eine APP problemlos neu zuweisen, um eine andere Datenquelle zu verwenden. Noch wichtiger ist für Offline Szenarien, dass Sie lokale Sammlungen für die Datenverwaltung ohne Änderungen an der Logik einer App verwenden können. Tatsächlich stellen lokale Sammlungen den wichtigsten Mechanismus in der Verarbeitung von Offlinedaten dar.

## <a name="build-an-offline-app"></a>Erstellen einer Offline-App

Um den Fokus auf die Offline Aspekte der APP-Entwicklung zu behalten, veranschaulicht dieses Thema ein einfaches Szenario, das sich auf Twitter konzentriert. Sie erstellen eine APP, die es Ihnen ermöglicht, Twitter-Beiträge zu lesen und Tweets zu senden, während Sie offline sind. Wenn die App Zugang zu einer Onlineverbindung erhält, veröffentlicht sie die Tweets und lädt die lokalen Daten erneut.

Auf hoher Ebene führt die APP die folgenden Aufgaben aus:

- Wenn der Benutzer die APP öffnet:

  - Wenn das Gerät online ist, ruft die APP Daten über den Twitter-Connector ab und füllt eine Sammlung mit diesen Daten auf.
  - Wenn das Gerät offline ist, lädt die APP die Daten mithilfe der [**LoadData**](../canvas-apps/functions/function-savedata-loaddata.md) -Funktion aus einer lokalen Cachedatei.
  - Der Benutzer kann tweets übermitteln. Wenn die APP Online ist, werden die tweets direkt an Twitter gesendet, und der lokale Cache wird aktualisiert.

- Alle fünf Minuten, während die APP Online ist:

  - Die APP postet alle tweets im lokalen Cache.
  - Die APP aktualisiert den lokalen Cache und speichert Sie mithilfe der [**SaveData**](../canvas-apps/functions/function-savedata-loaddata.md) -Funktion.

### <a name="step-1-add-twitter-to-a-blank-phone-app"></a>Schritt 1: Hinzufügen von Twitter zu einer leeren Phone-App

1. Wählen Sie in powerapps Studio **Datei** > **neu**aus.
1. Wählen Sie auf der Kachel **Leere App** **Telefonlayout** aus.
1. Klicken Sie auf der Registerkarte **Ansicht** auf die Option **Datenquellen**.
1. Wählen Sie im Bereich **Daten** die Option **Datenquelle hinzufügen**aus.
1. Wählen Sie **neue Verbindung** > **Twitter** > **Erstellen**aus.
1. Geben Sie Ihre Anmelde Informationen ein, erstellen Sie die Verbindung, und schließen Sie dann den **Daten** Bereich.

### <a name="step-2-collect-existing-tweets"></a>Schritt 2: erfassen vorhandener tweets

1. Wählen Sie im Struktur **Ansichts** Bereich **App**aus, und legen Sie dann die zugehörige **OnStart** -Eigenschaft auf die folgende Formel fest:

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
    > ![Formel zum Laden von Tweets](./media/offline-apps/load-tweets.png)

1. Wählen Sie im Struktur **Ansichts** Bereich das Menü mit den Auslassungs Punkten für das **App** -Objekt aus, und klicken Sie dann auf **OnStart ausführen** , um die Formel auszuführen.

    > [!div class="mx-imgBorder"]
    > ![Run-Formel zum Laden von Tweets](./media/offline-apps/load-tweets-run.png)

    > [!NOTE]
    > Die Funktionen " **LoadData** " und " **SaveData** " zeigen möglicherweise einen Fehler in Power apps Studio an, da Sie von Browsern nicht unterstützt werden Sie werden jedoch normal durchgeführt, nachdem Sie diese APP auf einem Gerät bereitgestellt haben.

Diese Formel überprüft, ob das Gerät online ist:

- Wenn das Gerät online ist, lädt die Formel bis zu 10 tweets mit dem Suchbegriff "powerapps" in eine **localtweets** -Sammlung.
- Wenn das Gerät offline ist, lädt die Formel den lokalen Cache aus einer Datei mit dem Namen "localtweets", sofern diese verfügbar ist.

### <a name="step-3-show-tweets-in-a-gallery"></a>Schritt 3: Anzeigen von tweets in einem Katalog

1. **Wählen Sie** auf der Registerkarte **Einfügen** die Option Katalog aus, > **leere flexible Höhe**.

1. Legen Sie die **Items** -Eigenschaft des Katalog [ **-Steuer Elements**](controls/control-gallery.md) auf `LocalTweets`fest.

1. Fügen Sie in der Katalog Vorlage drei [**Label**](controls/control-text-box.md) -Steuerelemente hinzu, und legen Sie die **Text** -Eigenschaft jeder Bezeichnung auf einen der folgenden Werte fest:

    - `ThisItem.UserDetails.FullName & " (@" & ThisItem.UserDetails.UserName & ")"`
    - `Text(DateTimeValue(ThisItem.CreatedAtIso), DateTimeFormat.ShortDateTime)`
    - `ThisItem.TweetText`

1. Legen Sie den Text in der letzten Bezeichnung Fett fest, damit der Katalog dem folgenden Beispiel ähnelt.

    > [!div class="mx-imgBorder"]
    > ![Galerie mit Beispiel-tweets](./media/offline-apps/tweet-gallery.png)

### <a name="step-4-show-connection-status"></a>Schritt 4: Anzeigen des Verbindungsstatus

1. Fügen Sie im Katalog eine Bezeichnung ein, und legen Sie die **Farb** Eigenschaft auf **rot**fest.

1. Legen Sie die **Text** -Eigenschaft der neuesten Bezeichnung auf diese Formel fest:

    `If( Connection.Connected, "Connected", "Offline" )`

Diese Formel bestimmt, ob das Gerät online ist. Wenn dies der Fall ist, zeigt die Bezeichnung **verbunden**an. Andernfalls wird es **Offline**angezeigt.

### <a name="step-5-add-a-box-to-compose-tweets"></a>Schritt 5: Hinzufügen eines Felds zum Verfassen von Tweets

1. Fügen Sie unter der Bezeichnung Verbindungsstatus ein [**Text Eingabe**](controls/control-text-input.md) -Steuerelement ein, und benennen Sie es **newtweettextinput**um.

1. Legen Sie die **default** -Eigenschaft des Texteingabe Felds auf `""`fest.

    > [!div class="mx-imgBorder"]
    > ![Galerie über Statusinformationen und Texteingabefeld](./media/offline-apps/status-input.png)

### <a name="step-6-add-a-button-to-post-the-tweet"></a>Schritt 6: Hinzufügen einer Schaltfläche zum Posten des tweets

1. Fügen Sie im Textfeld Texteingabe ein **Schalt** Flächen-Steuerelement hinzu, und legen Sie dessen **Text** -Eigenschaft auf diesen Wert fest:

    `"Tweet"`

1. Legen **Sie die onselect** -Eigenschaft der Schaltfläche auf die folgende Formel fest:

    ```powerapps-dot
    If( Connection.Connected,
        Twitter.Tweet( "", {tweetText: NewTweetTextInput.Text} ),
        Collect( LocalTweetsToPost, {tweetText: NewTweetTextInput.Text} );
            SaveData( LocalTweetsToPost, "LocalTweetsToPost" )
    );
    Reset( NewTweetTextInput );
    ```  

1. Fügen Sie in der **OnStart** -Eigenschaft für die **App**am Ende der Formel eine Zeile hinzu:

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
    > ![Formel ausführen, um Tweets mit nicht kommentierter Zeile zu laden](./media/offline-apps/load-tweets-save.png)

Diese Formel bestimmt, ob das Gerät online ist:

- Wenn das Gerät online ist, sendet es sofort den Tweet.
- Wenn das Gerät offline ist, wird der Tweet in einer **localtweetstopost** -Sammlung erfasst und auf dem Gerät gespeichert.

Anschließend setzt die Formel den Text im Texteingabefeld zurück.

### <a name="step-7-check-for-new-tweets"></a>Schritt 7: Überprüfen auf neue tweets

1. Fügen Sie auf der rechten Seite der Schaltfläche ein **Timer** -Steuerelement hinzu.

    > [!div class="mx-imgBorder"]
    > ![endgültige apps](./media/offline-apps/final-app.png)

1. Legen Sie die **Duration** -Eigenschaft des Timers auf **300000**fest.

1. Legen Sie die **Autostart** -und **Repeat** -Eigenschaften des Timers auf " **true**" fest.

1. Legen Sie die **ontimerend** -Eigenschaft des Timers auf diese Formel fest:

    ```powerapps-dot
    If( Connection.Connected,
        ForAll( LocalTweetsToPost, Twitter.Tweet( "", {tweetText: tweetText} ) );
        Clear( LocalTweetsToPost );
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
        SaveData( LocalTweets, "LocalTweets" );
   )
    ```

Diese Formel bestimmt, ob das Gerät online ist. Wenn dies der Fall ist, werden alle Elemente in der **localtweetstopost** -Auflistung von der APP mit einem Tweet und dann die Auflistung gelöscht.

## <a name="test-the-app"></a>Testen der App

1. Öffnen Sie die APP auf einem mobilen Gerät, das mit dem Internet verbunden ist.

    Vorhandene tweets werden im Katalog angezeigt, und der Status zeigt **verbunden**an.

1. Trennen Sie die Verbindung zwischen dem Gerät und dem Internet, indem Sie den Flugzeug Modus des Geräts aktivieren und Wi-Fi deaktivieren.

    Die Status Bezeichnung zeigt, dass die APP **Offline**ist.

1. Wenn das Gerät offline ist, schreiben Sie einen Tweet, der **powerapps**enthält, und wählen Sie dann die Schaltfläche **Tweet** aus.

    Der Tweet wird lokal in der **localtweetstopost** -Auflistung gespeichert.

1. Stellen Sie erneut eine Verbindung zwischen dem Gerät und dem Internet her, indem Sie den Flugzeug Modus des Geräts deaktivieren und Wi-Fi aktivieren.

    Innerhalb von fünf Minuten sendet die APP den Tweet, der im Katalog angezeigt wird.

Wir hoffen, dass dieser Artikel Ihnen einen Überblick über die Funktionen von Power Apps zum Entwickeln von Offline-Apps bietet. Bitte geben Sie in unserem [Forum](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1) Feedback, und teilen Sie Ihre Beispiele für Offline-Apps im [Community-Blog von powerapps](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog).