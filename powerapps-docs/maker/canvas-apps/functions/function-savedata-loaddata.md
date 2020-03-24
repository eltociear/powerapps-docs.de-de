---
title: Funktionen „SaveData“ und „LoadData“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax für die Funktionen "SaveData" und "LoadData" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c90f0be8d1f8f62afd3fdec1701b98b434f74387
ms.sourcegitcommit: 1b29cd1fa1492037ef04188dd857a911edeb4985
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80122825"
---
# <a name="savedata-and-loaddata-functions-in-power-apps"></a>Funktionen "SaveData" und "LoadData" in powerapps
Speichert und lädt eine [Sammlung](../working-with-data-sources.md#collections) von einem lokalen Gerät.

## <a name="description"></a>Beschreibung
Die Funktion **SaveData** speichert eine Sammlung für die spätere Verwendung unter einem Namen.  

Die **LoadData** -Funktion lädt eine Auflistung anhand des Namens, der zuvor mit **SaveData**gespeichert wurde, erneut. Sie können diese Funktion nicht dazu verwenden, eine Sammlung aus einer anderen Quelle zu laden.  

Verwenden Sie diese Funktionen, um die APP-Startleistung zu verbessern:

- Zwischenspeichern von Daten in der **[app. OnStart](../controls/control-screen.md#additional-properties)** -Formel bei einer ersten Testlauf.
- Der lokale Cache wird bei den nächsten Ausführungen erneut geladen.

Sie können diese Funktionen auch verwenden, um Ihrer APP [einfache Offline Funktionen](../offline-apps.md) hinzuzufügen.

Sie können diese Funktionen nicht in einem Browser verwenden, wenn:

- Erstellen der app in powerapps Studio.
- Ausführen der APP im Web Player. 

Um Ihre APP zu testen, führen Sie Sie in powerapps Mobile auf einem iPhone-oder Android-Gerät aus.

Diese Funktionen werden durch die Menge an verfügbarem App-Arbeitsspeicher begrenzt, wenn Sie für eine Auflistung im Arbeitsspeicher ausgeführt werden. Der verfügbare Arbeitsspeicher kann abhängig von folgenden Faktoren variieren: 

- Das Gerät und das Betriebssystem.
- Der Arbeitsspeicher, den der Power apps-Player verwendet.
- Komplexität der APP mit Bildschirmen und Steuerelementen. 

Testen Sie Ihre APP mit erwarteten Szenarien auf dem Typ der Geräte, die bei der Speicherung großer Daten von der APP erwartet werden. Erwarten Sie in der Regel zwischen 30 MB und 70 MB verfügbarem Arbeitsspeicher.

Diese Funktionen hängen davon ab, dass die Sammlung implizit mit **[Collect](function-clear-collect-clearcollect.md)** oder **[clearcollect](function-clear-collect-clearcollect.md)** definiert wird. Sie müssen **Collect** oder **clearcollect** nicht aufrufen, um Daten in die Auflistung zu laden, um Sie zu definieren. Bei der Verwendung von **LoadData** nach einem vorherigen **SaveData**-Wert ist dies häufig der Fall.  Alles, was erforderlich ist, besteht darin, dass diese Funktionen in einer Formel vorhanden sind, um die Struktur der Auflistung implizit zu definieren.  Weitere Informationen finden Sie unter [Erstellen und Entfernen von Variablen](../working-with-variables.md#create-and-remove-variables).

Die geladenen Daten werden an die Auflistung angefügt. Verwenden Sie die **[Clear](function-clear-collect-clearcollect.md)** -Funktion vor dem Aufrufen von **LoadData** , wenn Sie mit einer leeren Auflistung beginnen möchten.

Die integrierten App-Sandbox-Funktionen des Geräts werden zum isolieren gespeicherter Daten von anderen apps verwendet. 

Das Gerät kann auch die Daten verschlüsseln. oder Sie können ein Verwaltungs Tool für mobile Geräte wie [Microsoft InTune](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune)verwenden.

## <a name="syntax"></a>Syntax
**SaveData**( *Sammlung*, *Name* )<br>**LoadData**( *Sammlung*, *Name* [, *NichtVorhandeneDateiIgnorieren* ])

* *Sammlung*: Erforderlich.  Die zu speichernde oder zu ladende Sammlung.
* *Name*: Erforderlich.  Der Name des Speichers. Der Name muss identisch sein, um denselben Datensatz zu speichern und zu laden. Der Namespace wird nicht für andere Apps oder Benutzer freigegeben.
* *NichtVorhandeneDateiIgnorieren*: optional. Ein boolescher Wert, der angibt, was geschehen soll, wenn die Datei nicht bereits vorhanden ist.  Verwenden Sie *false* (Standard), um einen Fehler zurückzugeben, und *true* , um den Fehler zu unterdrücken.   

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **SaveData (LocalCache, "myCache")** | Speichern Sie die **LocalCache** -Auflistung auf dem Gerät des Benutzers unter dem Namen "myCache", damit **LoadData** später abgerufen werden kann. | Die Daten werden auf dem lokalen Gerät gespeichert. |
| **LoadData (LocalCache, "myCache")** | Lädt die **LocalCache** -Auflistung aus dem Gerät des Benutzers unter dem Namen "myCache", der zuvor mit einem Auflistungs Befehl von **SaveData**gespeichert wurde.  | Die Daten werden vom lokalen Gerät geladen. |   

### <a name="simple-offline-example"></a>Einfaches Beispiel für Offline

Im folgenden einfachen Beispiel werden die Namen und Bilder täglicher Elemente im Offline Modus erfasst und gespeichert.  Sie speichert die Informationen zur späteren Verwendung im lokalen Speicher des Geräts. Dadurch kann die app geschlossen oder das Gerät neu gestartet werden, ohne dass Daten verloren gehen.  

Sie müssen über ein Gerät verfügen, um dieses Beispiel zu bearbeiten, da es die **LoadData** -und **SaveData** -Funktionen verwendet, die in einem Webbrowser nicht funktionieren.

1. Erstellen Sie eine leere Canvas-App mit einem Tablet-Layout.  Weitere Informationen finden Sie unter [Erstellen einer App aus einer Vorlage](../get-started-test-drive.md) und auswählen des **Tablet-Layouts** unter **leere App**.  

1. Fügen Sie ein [**Text Eingabe**](../controls/control-text-input.md) -Steuerelement und ein [**Kamera**](../controls/control-camera.md) Steuerelement hinzu, und ordnen Sie Sie wie gezeigt an:
    > [!div class="mx-imgBorder"]  
    > ![ein einem leeren Bildschirm hinzugefügtes Texteingabe-und Kamera Steuerelement](media/function-savedata-loaddata/simple-text-camera.png)

1. Hinzufügen eines [**Schalt**](../controls/control-button.md) Flächen-Steuer Elements

2. Doppelklicken Sie auf das Schaltflächen-Steuerelement, um den Text der Schaltfläche zum **Hinzufügen eines Elements** zu ändern (oder die **Text** -Eigenschaft

3. Legen **Sie die onselect** -Eigenschaft des Schaltflächen-Steuer Elements auf diese Formel fest, mit der der Auflistung ein Element hinzugefügt wird:
    ```powerapps-dot
    Collect( MyItems, { Item: TextInput1.Text, Picture: Camera1.Photo } )
    ```
    > [!div class="mx-imgBorder"] 
    > ![ein Schaltflächen-Steuerelement hinzu, das mit dem Text "Add Item" und der onselect-Eigenschaft hinzugefügt wurde](media/function-savedata-loaddata/simple-additem.png)

1. Fügen Sie eine weitere **Schaltfläche** hinzu.

2. Doppelklicken Sie auf das Schaltflächen-Steuerelement, um den Schaltflächen Text zum **Speichern von Daten** (oder Ändern der **Text** -Eigenschaft) zu ändern

3. Legen **Sie die onselect** -Eigenschaft des Schaltflächen-Steuer Elements auf diese Formel fest, um die Sammlung auf dem lokalen Gerät zu speichern:
    ```powerapps-dot
    SaveData( MyItems, "LocalSavedItems" )
    ```
    > [!div class="mx-imgBorder"] 
    > ![ein Button-Steuerelement hinzugefügt, das mit dem Text "Daten speichern" und der onselect-Eigenschaft festgelegt wurde](media/function-savedata-loaddata/simple-savedata.png)

    Es ist verlockend, die Schaltfläche zu testen, da Sie nichts beeinträchtigt. Beim Erstellen eines Webbrowsers wird jedoch nur ein Fehler angezeigt. Speichern Sie zuerst die APP, und öffnen Sie Sie auf einem Gerät, bevor Sie die nächsten Schritte ausführen, um diese Formel zu testen:

1. Fügen Sie ein drittes **Button** -Steuerelement hinzu.

2. Doppelklicken Sie auf das Schaltflächen-Steuerelement, um den Schaltflächen Text zum **Laden von Daten** zu ändern (oder ändern Sie die **Text** -Eigenschaft

3. Legen **Sie die onselect** -Eigenschaft des Schaltflächen-Steuer Elements auf diese Formel fest, um die Sammlung vom lokalen Gerät zu laden:
    ```powerapps-dot
    LoadData( MyItems, "LocalSavedItems" )
    ``` 
    > [!div class="mx-imgBorder"] 
    > ![ein Button-Steuerelement hinzugefügt, das mit dem Text "Load Data" und der onselect-Eigenschaft festgelegt wurde](media/function-savedata-loaddata/simple-loaddata.png)

1. Fügen Sie ein Katalog-Steuerelement mit einem vertikalen Layout hinzu, [**das einen Bild**](../controls/control-gallery.md) -und Textbereich umfasst: 
    > [!div class="mx-imgBorder"] 
    > ![Galerie Auswahl "vertikal" mit Bild-und Textbereichen ausgewählt](media/function-savedata-loaddata/simple-gallery-add.png)

1. Wenn Sie dazu aufgefordert werden, wählen Sie die Sammlung **MyItems** als Datenquelle für diesen Katalog aus.  Dadurch wird die **Items** -Eigenschaft des Katalog **-Steuer Elements** festgelegt: 
    > [!div class="mx-imgBorder"] 
    > ![Katalogauswahl der Datenquelle](media/function-savedata-loaddata/simple-gallery-collection.png) das Image-Steuerelement in der Katalog Vorlage die **Image** -Eigenschaft auf **thisitem.** Image und die Label-Steuerelemente standardmäßig Ihre **Text** Eigenschaften auf **thisitem. Item**festlegen.  Überprüfen Sie diese Formeln, wenn Sie nach dem Hinzufügen von Elementen in den folgenden Schritten nichts im Katalog sehen. 

1. Positionieren Sie das Steuerelement auf der rechten Seite der anderen Steuerelemente: 
    > [!div class="mx-imgBorder"] 
    > ![Galerie auf der rechten Seite des Bildschirms neu positioniert](media/function-savedata-loaddata/simple-gallery-placed.png)

1. Speichern Sie Ihre APP.  Wenn es das erste Mal ist, dass es gespeichert wurde, ist es nicht erforderlich, es zu veröffentlichen. Wenn dies nicht der erste Zeitpunkt ist, veröffentlichen Sie die APP nach dem Speichern.

1. Öffnen Sie die APP auf einem Gerät, z. b. einem Telefon oder Tablet.  **SaveData** und **LoadData** können nicht in Studio oder in einem Webbrowser verwendet werden.  Aktualisieren der APP-Liste wenn Sie Ihre APP nicht sofort sehen können, kann es einige Sekunden dauern, bis die APP auf Ihrem Gerät angezeigt wird.  Sie können sich auch bei Ihrem Konto abmelden und wieder anmelden.
    > [!div class="mx-imgBorder"] 
    > ![App ohne hinzugefügte Elemente](media/function-savedata-loaddata/simple-mobile.png) nachdem Ihre APP heruntergeladen wurde, können Sie die Verbindung mit dem Netzwerk trennen und die APP offline ausführen.

1. Geben Sie den Namen ein, und sehen Sie sich ein Element an.

2. Wählen Sie die Schaltfläche **Element hinzufügen** aus.  Wiederholen Sie das Hinzufügen von Elementen mehrmals, um die Sammlung zu laden.
    > [!div class="mx-imgBorder"] 
    > ![APP wird ausgeführt, die drei hinzugefügte Elemente](media/function-savedata-loaddata/simple-mobile-with3.png) 

1. Wählen Sie die Schaltfläche **Daten speichern** aus.  Dadurch werden die Daten in Ihrer Sammlung auf dem lokalen Gerät gespeichert.

1. Schließen Sie die app.  Die Sammlung im Arbeitsspeicher geht verloren, einschließlich aller Elementnamen und Bilder, aber Sie befinden sich weiterhin im Speicher des Geräts.

1. Starten Sie die APP erneut.  Die Sammlung im Arbeitsspeicher wird im Katalog erneut als leer angezeigt.
    > [!div class="mx-imgBorder"] 
    > ![APP wird erneut ausgeführt, und es werden keine Elemente hinzugefügt](media/function-savedata-loaddata/simple-mobile.png) 

1. Wählen Sie die Schaltfläche **Daten laden** aus.  Die Sammlung wird von den gespeicherten Daten auf Ihrem Gerät erneut ausgefüllt, und ihre Elemente werden wieder im Katalog angezeigt.  Die Auflistung war leer, bevor diese Schaltfläche die **LoadData** -Funktion aufruft. vor dem Laden der Daten aus dem Speicher war es nicht erforderlich, **Collect** oder **clearcollect** aufzurufen.
    > [!div class="mx-imgBorder"] 
    > ![APP, die mit drei Elementen ausgeführt wird, nachdem Sie die LoadData-Funktion aufgerufen haben](media/function-savedata-loaddata/simple-mobile-load1.png) 

1. Klicken Sie erneut auf die Schaltfläche **Daten laden** .  Die gespeicherten Daten werden an das Ende der Auflistung angehängt, und im Katalog wird eine Schiebe Leiste angezeigt.  Wenn Sie anstelle von anfügen ersetzen möchten, verwenden Sie zuerst die **Clear** -Funktion, um die Auflistung zu löschen, bevor Sie die **LoadData** -Funktion aufrufen.
    > [!div class="mx-imgBorder"] 
    > ![APP, die mit sechs Elementen ausgeführt wird, nachdem die LoadData-Funktion zweimal aufgerufen wurde](media/function-savedata-loaddata/simple-mobile-load2.png) 
 
### <a name="more-advanced-offline-example"></a>Beispiel für erweiterte Offline Schaltung

Ein ausführliches Beispiel finden Sie im Artikel über [einfache Offline Funktionen](../offline-apps.md).







