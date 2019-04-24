---
title: Übersicht über die SharePoint-Verbindung | Microsoft-Dokumentation
description: Für SharePoint finden Sie unter den verfügbaren Funktionen, Antworten und Beispiele.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/03/2019
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 65ce3b7736b55f3734d6da7d945965ed791a3ce4
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61549202"
---
# <a name="connect-to-sharepoint-from-a-canvas-app"></a>Verbinden Sie mit SharePoint aus einer Canvas-app

![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

Verbinden mit einer SharePoint-Website, um eine app aus einer benutzerdefinierten Liste automatisch zu generieren, oder erstellen Sie eine Verbindung aus, bevor Sie das Hinzufügen von Daten zu einer vorhandenen app oder eine app von Grund auf neu erstellen.

Je nachdem, wo Ihre Daten befinden können Sie eine oder beide der folgenden Ansätze ausführen:

- Zeigen Sie Daten aus einer benutzerdefinierten Liste in einer SharePoint Online-Website oder einem lokalen Standort.
- Anzeigen von Bildern und Wiedergabe von Video- oder audio-Dateien in einer Bibliothek (nur SharePoint-Online).

## <a name="generate-an-app"></a>Eine App generieren

Wenn Sie Daten in einer benutzerdefinierten Liste verwalten möchten, können PowerApps [eine app mit drei Bildschirmen automatisch für Sie generieren](../app-from-sharepoint.md). Benutzer können die Liste auf dem ersten Bildschirm durchsuchen, Details zum Anzeigen eines Elements im zweiten Bildschirm, und erstellen oder aktualisieren Elemente im dritten Bildschirm.

> [!NOTE]
> Wenn die SharePoint-Liste enthält eine **Wahl**, **Lookup**, oder **Person oder Gruppe** Spalte finden Sie unter [Anzeigen von Daten in einem Katalog](connection-sharepoint-online.md#show-list-columns-in-a-gallery) weiter unten in diesem Thema.

## <a name="create-a-connection"></a>Verbindung erstellen

1. [Melden Sie sich bei PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)Option **Daten** > **Verbindungen** im linken Navigationsbereich, und klicken Sie anschließend **neue Verbindung** in der Nähe der linke obere Ecke.

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie Daten aus > Verbindungen in der linken Navigationsleiste, und wählen Sie dann neue Verbindung in der Nähe der oberen linken Ecke.](./media/connection-sharepoint-online/new-connection.png)

1. Geben Sie in das Suchfeld in der Nähe der oberen rechten Ecke, oder fügen Sie **SharePoint**, und wählen Sie dann **SharePoint**.

    > [!div class="mx-imgBorder"]
    > ![Klicken Sie in das Suchfeld in der Nähe der oberen rechten Ecke Geben Sie oder fügen Sie die SharePoint, und wählen Sie dann auf SharePoint.](./media/connection-sharepoint-online/select-sharepoint.png)

1. Führen Sie einen der folgenden Schritte aus:

    - Wählen Sie zum Verbinden mit SharePoint Online **direkt verbinden (Clouddienste)** Option **erstellen**, und geben Sie Anmeldeinformationen (sofern es sich um eine Aufforderung zur Bestätigung).

        > [!div class="mx-imgBorder"]
        > ![Wählen Sie zum Verbinden mit SharePoint Online direkt verbinden (Clouddienste)](./media/connection-sharepoint-online/select-online.png)

        Die Verbindung wird hergestellt, und Sie können zum Hinzufügen eines zu einer vorhandenen app oder eine app von Grund auf neu erstellen.

    - Wählen Sie zum Verbinden mit einem lokalen Standort **Herstellen einer Verbindung mit einem lokalen datengateway**.

        > [!div class="mx-imgBorder"]
        > ![Wählen Sie zum Verbinden mit einem lokalen Standort ** Herstellen einer Verbindung mit lokalen Datengateways)](./media/connection-sharepoint-online/select-onprem.png)

        Geben Sie **Windows** als Authentifizierungstyp an, und geben Sie dann Ihre Anmeldeinformationen ein. (Wenn Ihre Anmeldeinformationen einen Domänennamen enthalten, geben Sie sie folgendermaßen an: *Domäne\Alias*.)

        > [!div class="mx-imgBorder"]
        > ![Geben Sie die Anmeldeinformationen](./media/connection-sharepoint-online/specify-creds.png)

        Klicken Sie unter **wählen Sie ein Gateway**, wählen Sie das Gateway, das Sie verwenden möchten, und wählen Sie dann **erstellen**.

        > [!NOTE]
        > Wenn Sie ein lokales datengateway installiert haben, nicht [installieren Sie eine](../gateway-reference.md), und wählen Sie dann auf das Symbol, um die Liste der Gateways zu aktualisieren.

        > [!div class="mx-imgBorder"]
        > ![Gateway auswählen](./media/connection-sharepoint-online/choose-gateway.png)

        Die Verbindung wird hergestellt, und Sie können zum Hinzufügen eines zu einer vorhandenen app oder eine app von Grund auf neu erstellen.

## <a name="add-data-to-an-existing-app"></a>Hinzufügen von Daten zu einer vorhandenen app

1. In PowerApps Studio, öffnen Sie die app, die Sie aktualisieren möchten, wählen Sie die **Ansicht** Registerkarte, und wählen Sie dann **Datenquellen**.

    > [!div class="mx-imgBorder"]
    > ![Auf der Registerkarte "Ansicht", und wählen Sie dann die Datenquellen](./media/connection-sharepoint-online/view-data-sources.png)

1. In der **Daten** wählen Sie im Bereich **Datenquelle hinzufügen** > **SharePoint**.

1. Klicken Sie unter **Herstellen einer Verbindung mit einer SharePoint-Website**, wählen Sie einen Eintrag in der **zuletzt geöffnete Websites** Liste (oder geben oder fügen Sie die URL für die Website, die Sie verwenden möchten), und wählen Sie dann **Connect**.

    > [!div class="mx-imgBorder"]
    > ![Website auswählen](./media/connection-sharepoint-online/select-sp-site.png)

1. Klicken Sie unter **wählen Sie eine Liste**, wählen Sie das Kontrollkästchen für **Dokumente** oder eine oder mehrere Listen, die Sie verwenden möchten, und wählen Sie dann **Connect**:

    > [!div class="mx-imgBorder"]
    > ![Klicken Sie unter Wählen Sie eine Liste Wählen Sie das Kontrollkästchen für Dokumente oder eine oder mehrere Listen, die Sie verwenden möchten, und wählen Sie dann auf Verbinden](./media/connection-sharepoint-online/select-sp-tables.png)

    Nicht alle Typen von Listen werden standardmäßig angezeigt. PowerApps unterstützt benutzerdefinierte Liste, aber keine vorlagenbasierten Listen. Wenn der Name der Liste, die Sie verwenden möchten, angezeigt wird, scrollen Sie nach unten, und geben Sie den Namen der Liste in das Feld **Geben Sie benutzerdefinierte Tabellennamen**.

    > [!div class="mx-imgBorder"]
    > ![Geben Sie den Namen der Liste in das Feld Geben Sie einen Namen für die benutzerdefinierte Liste ein.](./media/connection-sharepoint-online/custom-list.png)

    Die Datenquelle oder Datenquellen werden Ihrer app hinzugefügt.

## <a name="build-your-own-app-from-scratch"></a>Ihre eigene app von Grund auf neu erstellen

Gelten die Konzepte in [erstellen Sie eine app von Grund auf Neu](../get-started-create-from-blank.md) in SharePoint anstelle von Excel.

## <a name="show-list-columns-in-a-gallery"></a>Anzeigen der von Listenspalten in einem Katalog

Wenn die benutzerdefinierte Liste alle Typen von Spalten enthält, zeigen Sie die Daten in eine **Katalog** Steuerelement mithilfe der Bearbeitungsleiste zum Festlegen der **Text** Eigenschaft einer oder mehreren **Bezeichnung** Steuerelemente in diesem Katalog:

- Für eine **Wahl** oder **Lookup** Spalte geben **ThisItem.** _ColumnName_**. Wert** Daten in dieser Spalte angezeigt.

    Geben Sie z.B. **ThisItem.Standort.Value** an, wenn Sie eine **Auswahl**-Spalte mit dem Namen **Standort** haben. Geben Sie **ThisItem.PostalCode.Value** für eine **Nachschlage**-Spalte namens **PostalCode** ein.

- Für eine **Person oder Gruppe** Spalte geben **ThisItem.** _ColumnName_**. "DisplayName"** um den Anzeigenamen des Benutzers oder der Gruppe anzuzeigen.

    Geben Sie z.B. **ThisItem.Manager.DisplayName** an, um die Anzeigenamen aus einer **Person oder Gruppe**-Spalte mit dem Namen **Manager** anzuzeigen.

    Sie können auch andere Informationen zu Benutzern anzeigen, z.B. E-Mail-Adressen oder Positionsbeschreibungen. Um eine vollständige Liste der Optionen anzuzeigen, geben **ThisItem.** _ColumnName_**.** (einschließlich des nachgestellten Punkts).

    > [!NOTE]
    > Für eine **CreatedBy** Spalte geben **ThisItem.Author.DisplayName** die Anzeigenamen von Benutzern angezeigt, die Elemente in der Liste erstellt haben. Für eine **ModifiedBy**-Spalte geben Sie **ThisItem.Editor.DisplayName** ein, um die Anzeigenamen von Benutzern anzuzeigen, die die Elemente in der Liste geändert haben.

- Für eine **verwaltete Metadaten** Spalte geben **ThisItem.** _ColumnName_**. Bezeichnung** Daten in dieser Spalte angezeigt.

    Geben Sie z.B. **ThisItem.Sprachen.Label** ein, wenn Sie mit einer **Verwaltete Metadaten**-Spalte mit dem Namen **Sprachen** arbeiten.

## <a name="show-data-from-a-library"></a>Anzeigen von Daten aus einer Bibliothek

Wenn Sie mehrere Bilder in einer SharePoint-Bibliothek verfügen, können Sie Hinzufügen einer **Dropdown** Steuern für Ihre app, sodass Benutzer, welches Bild angeben können angezeigt. Sie können auch gelten dieselben Prinzipien für andere Steuerelemente, z. B. **Katalog** Steuerelemente und andere Arten von Daten, z. B. Videos.

1. Wenn Sie nicht bereits geschehen, [erstellen Sie eine Verbindung](#create-a-connection), und klicken Sie dann [Hinzufügen von Daten zu einer vorhandenen app](#add-data-to-an-existing-app).

1. Hinzufügen einer **Dropdown** steuern, und nennen Sie sie **ImageList**.

1. Legen Sie die **Elemente** Eigenschaft **ImageList** zu **Dokumente**.

1. Auf der **Eigenschaften** Registerkarte im rechten Bereich, und Öffnen der **Wert** aus, und wählen Sie dann **Namen**.

    Die Dateinamen der Bilder in der Bibliothek angezeigt, **ImageList**.

    > [!div class="mx-imgBorder"]
    > ![Liste der images](./media/connection-sharepoint-online/dropdown-items.png)

1. Hinzufügen einer **Image** steuern, und legen dessen **Image** Eigenschaft auf den folgenden Ausdruck:

    `ImageList.Selected.'Link to item'`

1. Drücken Sie F5, und wählen Sie dann auf einen anderen Wert im **ImageList**.

    Das Bild, das Sie angegeben haben, wird angezeigt.

    > [!div class="mx-imgBorder"]
    > ![Beispielbild](./media/connection-sharepoint-online/golden-honey.png)

Sie können [eine Beispiel-app herunterladen](https://pwrappssamples.blob.core.windows.net/samples/spdoclib_blogapp.msapp) veranschaulicht, dass einen komplexeren Ansatz zum Anzeigen von Daten aus einer SharePoint-Bibliothek.

1. Nachdem Sie die app heruntergeladen haben, öffnen Sie [PowerApps Studio](https://us.create.powerapps.com/studio/#)Option **öffnen** im linken Navigationsbereich, und klicken Sie anschließend **Durchsuchen**.
1. In der **öffnen** Dialogfeld Suchen und öffnen Sie die Datei, die Sie heruntergeladen haben, und klicken Sie dann eine SharePoint-Bibliothek als Datenquelle hinzufügen, durch die ersten beiden Schritte in diesem Thema.

> [!NOTE]
> Standardmäßig zeigt diese app [Delegierung Warnungen](../delegation-overview.md), aber Sie können diese ignorieren, wenn Ihre Bibliothek mit weniger als 500 Elemente enthält.

In dieser app einem Bildschirm zeigt die Liste in der unteren linken Ecke alle Dateien in der Bibliothek.

- Sie können für eine Datei suchen, indem eingeben oder Einfügen eines oder mehrere Zeichen in das Suchfeld im oberen Bereich.
- Wenn Ihre Bibliothek Ordner enthält, können Sie die Liste der Dateien filtern, wählen Sie ein Symbol "Filter" in der Liste der Ordner direkt unter der Titelleiste.

Wenn Sie die Datei, die Sie möchten gefunden, wählen Sie ihn auf diesen in der **Video**, **Image**, oder **Audio** -Steuerelement entlang der rechten Seite.

> [!div class="mx-imgBorder"]
> ![Beispielbild](./media/connection-sharepoint-online/library-app.png)

## <a name="known-issues"></a>Bekannte Probleme

### <a name="lists"></a>Listen

PowerApps erhalten Spaltennamen, die Leerzeichen enthalten, aber die Leerzeichen werden durch den hexadezimalen Escapecode ersetzt **"\_X0020\_"**. **"Name der Spalte"** in SharePoint wird beispielsweise in PowerApps bei Anzeige im Datenlayout oder Verwendung in einer Formel als **"Name_x0020_der_x0020_Spalte"** angezeigt.

Nicht alle Typen von Spalten werden unterstützt, und nicht alle Spaltentypen unterstützen alle Typen von Karten.

| Spaltentyp | Support | Standardkarten |
| --- | --- | --- |
| Eine Textzeile |Ja |Text anzeigen |
| Mehrere Textzeilen |Ja |Text anzeigen |
| Auswahl |Ja |Suche anzeigen<br>Suche bearbeiten<br>Mehrfachauswahl anzeigen<br>Mehrfachauswahl bearbeiten |
| Number |Ja |Prozentsatz anzeigen<br>Bewertung anzeigen<br>Text anzeigen |
| Währung |Ja |Prozentsatz anzeigen<br>Bewertung anzeigen<br>Text anzeigen |
| Datum und Uhrzeit |Ja |Text anzeigen |
| Nachschlagen |Ja |Suche anzeigen<br>Suche bearbeiten<br>Mehrfachauswahl anzeigen<br>Mehrfachauswahl bearbeiten |
| Boolesch (Ja/Nein) |Ja |Text anzeigen<br>Ansicht umschalten |
| Person oder Gruppe |Ja |Suche anzeigen<br>Suche bearbeiten<br>Mehrfachauswahl anzeigen<br>Mehrfachauswahl bearbeiten |
| Hyperlink |Ja |URL anzeigen<br>Text anzeigen |
| Bild |Ja (schreibgeschützt) |Bild anzeigen<br>Text anzeigen |
| Anlage |Ja (schreibgeschützt) |Anlagen anzeigen|
| Berechnet |Ja (schreibgeschützt) | |
| Ergebnis der Aufgabe |Nein | |
| Externe Daten |Nein | |
| Verwaltete Metadaten |Ja (schreibgeschützt) | |
| Bewertung |Nein | |

### <a name="libraries"></a>Bibliotheken

- Sie können keine Dateien von PowerApps in einer Bibliothek hochladen.
- PDF-Dateien aus einer Bibliothek kann nicht in einem PDF-Viewer-Steuerelement angezeigt werden.
- PowerApps Mobile unterstützt nicht die **herunterladen** Funktion.
- Wenn Ihre Benutzer die app in PowerApps Mobile oder Windows 10-app ausgeführt werden, verwenden Sie die **starten** Funktion, um die Bibliotheksinhalte in einem Katalog anzeigen.

## <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie, wie Sie [Daten aus einer Datenquelle anzeigen](../add-gallery.md).
- Erfahren Sie, wie Sie [Details anzeigen und Datensätze erstellen oder aktualisieren](../add-form.md).
- Hier erhalten Sie Informationen zu anderen Arten von [Datenquellen](../connections-list.md), mit denen Sie eine Verbindung herstellen können.
