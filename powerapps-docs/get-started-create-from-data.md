---
title: Generieren einer App aus Excel-Daten | Microsoft-Dokumentation
description: "Erstellen Sie eine Anwendung automatisch basierend auf einer Excel-Datei in der Cloud, passen Sie die App an und untersuchen Sie anschließend, wie sie funktioniert."
services: 
suite: powerapps
documentationcenter: na
author: karthik-1
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/16/2016
ms.author: sharik
ms.openlocfilehash: 1558dba59f4b755ded709329c099feb94b55fac6
ms.sourcegitcommit: e827813cd898ca9a1046b5952ea5e32ce2989a65
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="generate-an-app-from-excel-data"></a>Generieren einer App aus Excel-Daten
Erstellen Sie automatisch eine App basierend auf Daten in einer Excel-Datei, die Sie in ein Cloudspeicherkonto wie OneDrive hochladen. Nachdem Sie die App generiert haben, können Sie sie beliebig anpassen und anschließend ausführen, um sicherzustellen, dass sie Ihren Vorstellungen entspricht.

Generierte Apps verfügen standardmäßig über drei Bildschirme:

* **BrowseScreen1** zeigt eine Teilmenge eines oder mehrerer Felder, eine Suchleiste und eine Schaltfläche zum Sortieren an, mit deren Hilfe Benutzer einen bestimmten Datensatz leicht finden können.
* **DetailsScreen1** zeigt mehrere oder alle Felder für einen bestimmten Datensatz.
* **EditScreen1** enthält Elemente der Benutzeroberfläche, mit deren Hilfe Benutzer einen Datensatz erstellen oder aktualisieren und die Änderungen speichern können.

> [!NOTE]
> Sie können eine App auch aus einer [benutzerdefinierten SharePoint-Liste](app-from-sharepoint.md) generieren.

## <a name="prerequisites"></a>Voraussetzungen
* [Registrieren](signup-for-powerapps.md) Sie sich für PowerApps, und führen Sie anschließend einen dieser Schritte aus:
  * Installieren Sie [PowerApps Studio für Windows](http://aka.ms/powerappsinstall) auf einem Computer mit Windows 8, Windows 8.1 oder Windows 10.
  * Öffnen Sie [PowerApps Studio für das Web](create-app-browser.md) (Vorschau) in einem Browser.
* Melden Sie sich bei PowerApps mit denselben Anmeldeinformationen an, die Sie bei der Registrierung verwendet haben.
* Um dieses Tutorial nachzuvollziehen, laden Sie diese [Excel-Datei](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) herunter.
  
    > [!IMPORTANT]
> Sie können eine eigene Excel-Datei verwenden, wenn die Daten als Tabelle formatiert sind. Weitere Informationen finden Sie unter [Erstellen oder Löschen einer Excel-Tabelle](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664).
* Laden Sie die Excel-Datei in OneDrive oder ein anderes [Cloudspeicherkonto](connections/cloud-storage-blob-connections.md) hoch.

## <a name="create-an-app"></a>Erstellen einer App
1. Klicken oder tippen Sie in PowerApps Studio im Menü **Datei** auf **Neu** (nahe dem linken Rand).
   
    ![Option „New“ im Menü „File“](./media/get-started-create-from-data/file-new.png)
2. Befolgen Sie einen der folgenden Schritte:
   
   * Wenn Ihr Cloudspeicherkonto unter **Von Ihren Daten ausgehen** angezeigt wird, klicken oder tippen Sie auf **Smartphonelayout**.
     
     ![Option zum Erstellen einer App aus Daten](./media/get-started-create-from-data/create-from-data.png)
   * Wenn Ihr Cloudspeicherkonto unter **Von Ihren Daten ausgehen** nicht angezeigt wird, klicken Sie auf den Pfeil am Ende der Zeile mit den Kacheln. Wenn Ihr Konto in der Liste der Verbindungen angezeigt wird, klicken oder tippen Sie darauf.
   * Wenn Ihr Cloudspeicherkonto weder unter **Von Ihren Daten ausgehen** noch in der Liste der Verbindungen angezeigt wird, klicken oder tippen Sie auf **Neue Verbindung** und dann auf den Eintrag für Ihr Konto. Klicken oder tippen Sie auf **Verbinden**, und befolgen Sie die Anweisungen zum Konfigurieren der Verbindung.
     
     ![Mit OneDrive verbinden](./media/get-started-create-from-data/connect-onedrive.png)
3. Navigieren Sie unter **Choose an Excel file** zu **FlooringEstimates.xlsx**, und klicken oder tippen Sie darauf.
   
    ![FlooringEstimates Excel-Datei](./media/get-started-create-from-data/choose-spreadsheet.png)  
4. Klicken oder tippen Sie unter **Choose a table (Tabelle auswählen)** auf **FlooringEstimates**.  
   
    ![FlooringEstimates-Tabelle auswählen](./media/get-started-create-from-data/choose-table.png)
5. Klicken oder tippen Sie auf **Connect**, um die App zu generieren.
6. Wenn Sie aufgefordert werden, die Einführung anzuschauen, klicken oder tippen Sie auf **Next** (Weiter), um sich mit wichtigen Bereichen der PowerApps-Benutzeroberfläche vertraut zu machen (oder klicken bzw. tippen Sie auf **Skip** (Überspringen)).
   
    ![Mit „Next“ (Weiter) zur Tour](./media/get-started-create-from-data/quick-tour.png)
   
    > [!NOTE]
> Sie können sich die Einführung jederzeit später anschauen. Klicken oder tippen Sie hierzu auf das Fragezeichen-Symbol in der Nähe der oberen rechten Ecke, und klicken oder tippen Sie anschließend auf **Take the intro tour**.

## <a name="change-the-gallery-layout"></a>Ändern des Kataloglayouts
Wenn eine App erstellt wird, verfügt sie über ein Standardlayout auf Basis Ihrer Daten, aber Sie können dieses Kataloglayout nach Belieben anpassen.

1. Klicken oder tippen Sie auf der linken Navigationsleiste rechts unten auf ein Symbol, um zur Miniaturansicht zu wechseln.
   
    ![Umschalten der Ansichten](./media/get-started-create-from-data/toggle-view.png)
2. Klicken oder tippen Sie auf der linken Navigationsleiste auf die obere Miniaturansicht, um sicherzustellen, dass der Bildschirm zum Durchsuchen (**BrowseScreen1**) ausgewählt ist.
3. Klicken oder tippen Sie an eine beliebige Stelle im Katalog, beispielsweise auf das erste Bild.
   
    ![Bild auswählen](./media/get-started-create-from-data/select-image.png)
4. Öffnen Sie im Bereich auf der rechten Seite die Liste **Layout**, und klicken oder tippen Sie dann auf das Layout, das ein Bild, einen Titel und einen Untertitel enthält.
   
    ![Auswählen des Layouts](./media/get-started-create-from-data/select-layout.png)
   
    Das Layout der App ändert sich gemäß Ihren Änderungen.
   
    ![BrowseScreen1 mit neuem Layout](./media/get-started-create-from-data/browse-layout.png)

## <a name="change-the-data-that-appears"></a>Ändern der angezeigten Daten
1. Klicken oder tippen Sie unter **Elemente suchen (Search items)** auf **Teppich (Carpet)**, um das Steuerelement **Bezeichnung (Label)** auszuwählen.
   
   Die zugeordnete Liste wird im rechten Bereich hervorgehoben.
   
   ![Erste Bezeichnung auswählen](./media/get-started-create-from-data/select-gallery-textbox.png)
2. Öffnen Sie im rechten Bereich die markierte Liste, und klicken oder tippen Sie dann auf **Name**.
   
    ![Erste Bezeichnung festlegen](./media/get-started-create-from-data/set-gallery-textbox.png)
3. Öffnen Sie die Liste unten, und klicken oder tippen Sie auf **Category** (Kategorie).
   
    ![Kategorie festlegen](./media/get-started-create-from-data/set-category.png)
   
    **BrowseScreen1** zeigt jetzt für jeden Datensatz einen Namen und eine Kategorie an.
   
    ![BrowseScreen1 mit neuem Inhalt](./media/get-started-create-from-data/browse-content.png)
   
    > [!NOTE]
> Standardmäßig können Sie per Mausrad bzw. auf einem Touchscreen durch Wischen nach oben oder unten durch die Liste (auch „Katalog“ genannt) scrollen. Um entweder ein Trackpad oder eine Maus ohne Rad zu verwenden, wählen Sie den Katalog aus, klicken oder tippen Sie in der Eigenschaftenliste auf **Scrollleiste anzeigen**, und ersetzen Sie dann in der Bearbeitungsleiste **FALSE** durch **TRUE**.

## <a name="change-the-order-of-fields-in-a-form"></a>Ändern der Reihenfolge von Formularfeldern
1. Klicken oder tippen Sie in der linken Navigationsleiste auf die mittlere Miniaturansicht, um den Detailbildschirm (**DetailsScreen1**) zu öffnen.
   
    ![Miniaturansicht DetailScreen 1](./media/get-started-create-from-data/detail-screen-thumbnail.png)
2. Klicken oder tippen Sie auf das Bild, um die für das Anpassen des Formulars verfügbaren Optionen anzuzeigen.
   
    ![Auswählen einer Karte](./media/get-started-create-from-data/select-card.png)
3. Ziehen Sie im rechten Bereich das Feld **Name** in der Liste an die oberste Stelle.
   
    ![Karte verschieben](./media/get-started-create-from-data/move-card.png)
   
    Der Bildschirm wird den Änderungen entsprechend aktualisiert.
   
    ![Name am oberen Bildschirmrand](./media/get-started-create-from-data/name-first.png)

## <a name="change-a-control"></a>Ein Steuerelement ändern
1. Klicken oder tippen Sie in der linken Navigationsleiste auf die untere Miniaturansicht, um den Bearbeitungsbildschirm (**EditScreen1**) zu öffnen.
   
    ![Miniaturansicht EditScreen1](./media/get-started-create-from-data/edit-screen-thumbnail.png)
2. Klicken oder tippen Sie auf **Overview** (Übersicht).
   
    Mit diesem Schritt wird die Übersichtskarte ausgewählt. Jede Karte enthält Text zur Beschreibung des Zwecks der Karte. Sie können auch die Steuerelemente auf einer Karte anpassen. Weitere Informationen finden Sie unter [Karten-Steuerelement in PowerApps](controls/control-card.md).
   
    ![Übersichtkarte auswählen](./media/get-started-create-from-data/select-overview.png)
3. Klicken oder tippen Sie im rechten Bereich auf den Pfeil nach unten für die Karte, scrollen Sie nach unten, und klicken oder tippen Sie dann auf **Mehrzeiligen Text bearbeiten**.
   
    Mit diesem Schritt wird eine Übersicht jedes Produkts in einem Steuerelement angezeigt, das groß genug ist, um den Text darzustellen.
   
    ![Karte ändern](./media/get-started-create-from-data/card-selector.png)

## <a name="run-the-app"></a>Ausführen der App
Während Sie die App anpassen, können Sie Ihre Änderungen testen, indem Sie die App im Vorschaumodus ausführen.

1. Klicken oder tippen Sie in der linken Navigationsleiste auf die obere Miniaturansicht, um den Bildschirm zum Durchsuchen (**BrowseScreen1**) zu öffnen.
2. Öffnen Sie den Vorschaumodus durch Drücken von F5 oder durch Klicken bzw. Tippen auf die Schaltfläche **Play** (Wiedergabe) in der Nähe der oberen rechten Ecke.
   
    ![„Preview“-Symbol](./media/get-started-create-from-data/open-preview.png)
3. Klicken oder tippen Sie im **BrowseScreen1** auf den Pfeil rechts neben einem Datensatz, um ihn im Detailbildschirm (**DetailsScreen1**) anzuzeigen.
   
    ![Einen Pfeil in BrowseScreen1 wählen](./media/get-started-create-from-data/select-record.png)
4. Klicken oder tippen Sie im **DetailsScreen1** auf das Stiftsymbol rechts oben in der Ecke, um den Datensatz im Bearbeitungsbildschirm (**EditScreen1**) anzuzeigen.
   
    ![Datensatz bearbeiten](./media/get-started-create-from-data/edit-record.png)
5. Ändern Sie im **EditScreen1** die Informationen in mindestens einem Feld, und klicken oder tippen Sie auf das Häkchen in der oberen rechten Ecke, um Ihre Änderungen zu speichern.
   
    ![Änderungen auf EditScreen1 speichern](./media/get-started-create-from-data/save-record.png)
6. Schließen Sie den Vorschaumodus, indem Sie die ESC-Taste drücken (oder indem Sie auf das Symbol zum Schließen unter der Titelleiste klicken oder tippen).
   
    ![Schließen des Vorschaumodus](./media/get-started-create-from-data/close-preview.png)

### <a name="known-limitations"></a>Bekannte Einschränkungen
Weitere Informationen zum Freigeben von Excel-Daten in Ihrer Organisation erhalten Sie in diesen [Ausführungen zu Einschränkungen](connections/cloud-storage-blob-connections.md#sharing-excel-tables).

## <a name="next-steps"></a>Nächste Schritte
* Drücken Sie STRG+S, um Ihre App zu speichern, sodass sie auf anderen Geräten ausgeführt werden kann.
* Da Sie jetzt wissen, wie eine App aus Daten generiert wird, können Sie als Nächstes [eine App von Grund auf neu erstellen](get-started-create-from-blank.md).
* Sie können die [App freigeben](share-app.md), damit sie von anderen Personen ausgeführt werden kann.

