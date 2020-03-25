---
title: Erstellen von Webseiten | Microsoft Docs
description: Anweisungen zum Erstellen von Webseiten im Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/10/2020
ms.author: tapanm
ms.reviewer: tapanm
ms.openlocfilehash: ec982dded0d67719effc0c2b0b4faecc19e656b8
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108295"
---
# <a name="compose-a-page"></a>Erstellen einer Seite

Wenn Sie die erforderlichen Webseiten hinzugefügt und ihre Hierarchie in der Siteübersicht verwaltet haben, können Sie verschiedene Komponenten hinzufügen. Mit dem WYSIWYG-Editor können Sie die erforderlichen Komponenten ganz leicht auf dem Canvas hinzuzufügen und bearbeiten. Die folgenden Komponenten können Sie auf dem Canvas hinzufügen und bearbeiten:

- Abschnitte
    - Einspaltiger Abschnitt
    - Zweispaltiger Abschnitt
    - Dreispaltiger Abschnitt
- Portalkomponenten
    - Text
    - Bild
    - IFrame
    - Formular
    - Liste
    - Breadcrumb

> [!NOTE]
> Wenn Sie Ihr Portal mithilfe des Power Apps-Portalstudios anpassen, würden die Websitebenutzer eine Auswirkung auf die Leistung feststellen. Wir empfehlen daher, die Änderungen nicht während der Hauptnutzungszeiten auf einem Liveportal durchzuführen. 

## <a name="use-the-wysiwyg-editor"></a>Verwenden des WYSIWYG-Editors

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.  

2.  Wählen Sie die Seite aus, auf der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein bearbeitbares Element auf dem Canvas aus.

    > [!NOTE]
    > Die bearbeitbaren Elemente werden durch eine Grenze voneinander abgetrennt.

4.  Wählen Sie **Komponenten** ![Komponentensymbol](media/components-icon.png "Komponentensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.  

5.  Wählen Sie die hinzuzufügende Komponente aus.

    > [!div class=mx-imgBorder]
    > ![Bereich Komponenten](media/components-pane.png "Bereich Komponenten")  

    Die ausgewählte Komponente wird innerhalb des bearbeitbaren Elements dem Canvas hinzugefügt.

6.  Zum Löschen einer Komponente wählen Sie die Komponente auf dem Canvas aus. Dann wählen Sie **Löschen** in der Befehlsleiste oben auf der Seite aus.

    > [!div class=mx-imgBorder]
    > ![Löschen einer Komponente](media/delete-component.png "Löschen einer Komponente")  

## <a name="add-sections"></a>Abschnitte hinzufügen

Mit Abschnitten können Sie eine Struktur für die Seite definieren und Portalkomponenten entsprechend anordnen. Nachdem Sie Abschnitte zur Seite hinzugefügt haben, können Sie Portalkomponenten in den Abschnitten gemäß der Anforderung hinzufügen.

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.

2.  Wählen Sie die Seite aus, für die ein Abschnitt hinzugefügt werden soll.

3.  Wählen Sie ein bearbeitbares Element auf dem Canvas aus.

4.  Wählen Sie **Komponenten** ![Komponentensymbol](media/components-icon.png "Komponentensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.

5.  Wählen Sie unter **Abschnittslayout** den Abschnittstyp aus, der eingefügt werden soll.

6.  Geben Sie im Eigenschaftenbereich auf der rechten Seite des Bildschirms die folgenden Informationen ein oder wählen Sie sie aus:

    - **Mindesthöhe**: Geben Sie die Mindesthöhe des Abschnitts ein. Wenn Sie eine Komponente hinzufügen, die mehr Raum als die angegebene Höhe benötigt, wird der Abschnitt erweitert, damit die Komponente genügend Platz hat. Standardmäßig beträgt die Mindesthöhe 100 px. Sie können die Höhe auch in Punkten (pt) und in Prozent (%) angeben.

        > [!div class=mx-imgBorder]
        > ![Ausrichtung im Abschnitt](media/section-props-height.png "Ausrichtung im Abschnitt")  

    - **Ausrichtung**: Wählen Sie aus, ob die Komponente im Abschnitt links, mittig oder rechts ausgerichtet sein muss.

        > [!div class=mx-imgBorder]
        > ![Ausrichtung im Abschnitt](media/section-props-align.png "Ausrichtung im Abschnitt")  

    - **Hintergrund**: Wählen Sie aus, ob Sie eine Farbe oder ein Bild als Abschnittshintergrund haben möchten.

        - **Ausfüllen**: Wählen Sie eine Farbe für den Hintergrund aus.

            > [!div class=mx-imgBorder]
            > ![Füllfarbe im Abschnitt](media/section-props-fill.png "Füllfarbe im Abschnitt")  

        - **Bild**: Wählen Sie ein Bild aus der Liste aus. Wenn Sie ein neues Bild hochladen möchten, wählen Sie **Bild hochladen** aus.

            > [!div class=mx-imgBorder]
            > ![Bild hinzufügen in Abschnitt](media/section-props-image.png "Bild hinzufügen in Abschnitt")  

7.  Fügen Sie die erforderliche Portalkomponente im Abschnitt hinzu.


## <a name="add-portal-components"></a>Hinzufügen von Portalkomponenten

Sie können die folgenden Komponenten auf einer Webseite hinzufügen.

- [Text](#add-text-box)
- [Bild](#add-image)
- [IFrame](#add-iframe)
- [Formular](#add-form)
- [Liste](#add-list)
- [Breadcrumb](#add-breadcrumb)


### <a name="add-text-box"></a>Hinzufügen eines Textfelds

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.  

2.  Wählen Sie die Seite aus, auf der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein bearbeitbares Element auf dem Canvas aus.

4.  Wählen Sie **Komponenten** ![Komponentensymbol](media/components-icon.png "Komponentensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.  

5.  Wählen Sie unter **Portalkomponenten** die Option **Text**.

6.  Geben Sie den erforderlichen Text in das Textfeld ein.

7.  Wenn Sie den Text formatieren möchten, wählen Sie den Text aus, um die Formatoptionen anzuzeigen. Ändern Sie Schriftgröße und -stil nach Bedarf.

    > [!div class=mx-imgBorder]
    > ![Text-Komponente](media/text-component.png "Text-Komponente")  

8. Wählen Sie im Eigenschaftenbereich auf der rechten Seite des Bildschirms die folgenden Informationen aus:

    - **Ausrichtung**: Wählen Sie aus, ob der Text links, mittig oder rechts ausgerichtet sein muss.

    - **Schriftfarbe**: Wählen Sie eine Farbe für den Text aus.

        > [!div class=mx-imgBorder]
        > ![Textausrichtung und Farbe auswählen](media/text-props.png "Textausrichtung und Farbe auswählen")  
 

### <a name="add-image"></a>Hinzufügen eines Bilds

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.  

2.  Wählen Sie die Seite aus, auf der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein bearbeitbares Element auf dem Canvas aus.

4.  Wählen Sie **Komponenten** ![Komponentensymbol](media/components-icon.png "Komponentensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.  

5.  Wählen Sie unter **Portalkomponenten** die Option **Bild**. Der Bildplatzhalter wird dem Canvas hinzugefügt.

6.  Geben Sie im Eigenschaftenbereich auf der rechten Seite des Bildschirms die folgenden Informationen ein:

    - **Bild**: Wählen Sie diese Option aus, wenn Sie ein vorhandenes Bild auswählen oder ein neues Bild hochladen möchten. Wenn Sie ein zuvor hochgeladenes Bild auswählen möchten, wählen Sie das Bild aus der Liste **Bild auswählen** aus. Um ein neues Bild hochzuladen, wählen Sie **Bild hochladen** aus. Alle hochgeladenen Bilder sind in der Bildbibliothek enthalten, die über die Liste **Bild auswählen** erneut ausgewählt werden kann.

        > [!div class=mx-imgBorder]
        > ![Bildeigenschaften](media/image-props.png "Bildeigenschaften")  

        > [!NOTE]
        > - Sie können nur Bilder des Typs PNG, SVG, JPG und JPEG mit einer maximalen Größe von 5 MB hochladen.
        > - Hochgeladene Bilder müssen einen einzigartigen Namen besitzen. Sie müssen den Namen des Bilds ändern, um es wieder hochzuladen.

    - **Externe URL**: Wählen Sie diese Option aus, wenn Sie ein Bild von einer externen URL hochladen möchten. Geben Sie die URL im Feld **Externe URL** ein. Nur gesicherte Links werden akzeptiert – d. h. https:// ist erforderlich. Wenn Sie Bilder in Ihrem Content Delivery Network gespeichert haben, können Sie den Link in diesem Feld angeben.

        > [!div class=mx-imgBorder]
        > ![Bild externe URL](media/image-ext-url.png "Bild externe URL")  

    -   **Formatierungsoptionen**

        - **Breite**: Geben Sie die Breite des Bilds ein.

        - **Höhe**: Geben Sie die Höhe des Bilds ein.

    > [!NOTE]
    > Sie können auch das Bild auf der Canvas auswählen und die Ziehpunkte ziehen, um seine Größe zu ändern.

### <a name="add-iframe"></a>Hinzufügen eines IFrames

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.  

2.  Wählen Sie die Seite aus, auf der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein bearbeitbares Element auf dem Canvas aus.

4.  Wählen Sie **Komponenten** ![Komponentensymbol](media/components-icon.png "Komponentensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.  

5.  Wählen Sie unter **Portalkomponenten** die Option **IFrame**. Der IFrame-Platzhalter wird dem Canvas hinzugefügt.

6.  Geben Sie im Eigenschaftenbereich auf der rechten Seite des Bildschirms die folgenden Informationen ein:

    - **Breite**: Geben Sie die Breite des IFrames ein.

    - **Höhe**: Geben Sie die Höhe des IFrames ein.

        > [!NOTE]
        > Sie können auch den IFrame auf der Canvas auswählen und die Ziehpunkte ziehen, um seine Größe zu ändern.

    - **Link**: Geben Sie die URL der Website ein, die im IFrame angezeigt werden soll. Nur gesicherte Links werden akzeptiert – d. h. https:// ist erforderlich. Standardmäßig ist <https://www.bing.com> als Wert verfügbar.
    
        > [!div class=mx-imgBorder]
        > ![IFrame-Eigenschaften](media/iframe-props.png "iFrame-Eigenschaften")  

> [!NOTE]
> Sie können auch [Power Virtual Agent](https://docs.microsoft.com/power-virtual-agents/fundamentals-what-is-power-virtual-agents) Bot dem IFrame in ähnlicher Weise mit Schritten wie beschrieben in [Bot einer Website hinzufügen](https://docs.microsoft.com/power-virtual-agents/publication-connect-bot-to-web-channels#custom-website) hinzufügen.

### <a name="add-form"></a>Hinzufügen eines Formulars

Ein Formular ist eine datengestützte Konfiguration, mit der Sie ein Formular hinzuzufügen können, um Daten in einem Portal zu sammeln, ohne dass ein Entwickler hierfür das Formular auf der Portaloberfläche darstellen muß. [Formulare werden in Common Data Service erstellt](https://docs.microsoft.com/powerapps/maker/model-driven-apps/form-designer-overview) und Sie können sie für Webseiten im Portal oder zusammen mit Listen verwenden, um vollständige Webanwendungen zu erstellen.  

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.  

2.  Wählen Sie die Seite aus, auf der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein bearbeitbares Element auf dem Canvas aus.

4.  Wählen Sie **Komponenten** ![Komponentensymbol](media/components-icon.png "Komponentensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.  

5.  Wählen Sie unter **Portalkomponenten** die Option **Formular**.

6.  Wählen Sie im Eigenschaftenbereich auf der rechten Seite des Bildschirms eine der folgenden Optionen aus:

    - **Neu erstellen**: Erstellen Sie ein neues Formular.
    - **Vorhandene verwenden**: Verwenden Sie ein vorhandenes Formular.

7. Geben Sie Informationen ein oder treffen Sie eine Auswahl für folgende Optionen:

    - **Name**: Der Name des Formulars.

    - **Entität**: Der Name der Entität, aus der das Formular geladen wird.

    - **Formularlayout**: Der Name des Formulars in der Zielentität in Common Data Service, die gerendert wird.

    - **Modus**: Wählen Sie eine der folgenden Optionen aus:

        - **Einfügen**: Gibt an, dass das Formular nach der Übermittlung einen neuen Datensatz einfügen soll.

        - **Bearbeiten**: Gibt an, dass das Formular einen vorhandenen Datensatz bearbeiten soll.

        - **Schreibgeschützt**: Gibt an, dass das Formular ein nicht bearbeitbares Formular eines vorhandenen Datensatzes anzeigen soll.

        > [!NOTE]
        > Die Standardoption für die Modi **Bearbeiten** und **Schreibgeschützt** ist als Name für Abfragezeichenfolgeparameter festgelegt und wird in der URL als ID weitergegeben. Wenn Sie diese Werte ändern möchten, müssen Sie die Portalverwaltungs-App öffnen und die Formulareigenschaften aktualisieren.

    - **Bei Erfolg**: Wählen Sie eine der folgenden Optionen aus:

        - **Erfolgsmeldung anzeigen**: Erfordert, dass bei erfolgreicher Übermittlung des Formulars eine Meldung für den Benutzer angezeigt wird. Sie können auch **Formular bei Erfolg ausblenden** auswählen, um das Formular nach erfolgreicher Übermittlung auszublenden.

        - **Umleiten zu Webseite**: Dabei wird der Benutzer auf die ausgewählte Webseite im Portal weitergeleitet. Sie müssen eine Webseite aus der Liste **Umleiten zu Webseite** auswählen.

        - **Umleitung zu URL**: Dabei wird der Benutzer zur angegebenen URL umgeleitet. Sie müssen eine URL in das Feld **Umleitung zu URL** eingeben.

    - **Captcha für anonyme Benutzer anzeigen**: Zeigt anonymen Benutzern ein Captcha an.

    - **Captcha für authentifizierte Benutzer anzeigen**: Zeigt authentifizierten Benutzern ein Captcha an.

    - **Entitätsberechtigungen aktivieren**: Entitätsberechtigungen, die für das Formular berücksichtigt werden sollen. Dies ist standardmäßig nicht ausgewählt. Wenn diese Option ausgewählt ist, sind explizite Berechtigungen für jeden Benutzer erforderlich, der auf das Formular zugreifen möchte. Weitere Informationen: [Entitätsberechtigung](configure/assign-entity-permissions.md)

        > [!div class=mx-imgBorder]
        > ![Formulareigenschaften](media/form-props.png "Formulareigenschaften")

### <a name="add-list"></a>Hinzufügen einer Liste

Eine Liste ist eine datengestützte Konfiguration, die Ihnen die Möglichkeit gibt, eine Webseite hinzuzufügen, die eine Liste von Einträgen rendert, ohne dass ein Entwickler das Raster im Portal bearbeiten muss. Bei Listen werden [Common Data Service-Ansichten](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-and-edit-views) verwendet, um Datensätze im Portal anzuzeigen.  

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.  

2.  Wählen Sie die Seite aus, auf der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein bearbeitbares Element auf dem Canvas aus.

4.  Wählen Sie **Komponenten** ![Komponentensymbol](media/components-icon.png "Komponentensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.  

5.  Wählen Sie unter **Portalkomponenten** die Option **Liste**.

6.  Wählen Sie im Eigenschaftenbereich auf der rechten Seite des Bildschirms eine der folgenden Optionen aus:

    - **Neu erstellen**: Erstellen Sie eine neue Liste.
    - **Vorhandene verwenden**: Verwenden Sie eine vorhandene Liste.

7.  Geben Sie Informationen ein oder treffen Sie eine Auswahl für folgende Optionen:

    - **Name**: Der Name der Liste.

    - **Entität**: Der Name der Entität, aus der die Ansichten geladen werden.

    - **Ansichten**: Die Liste der Ansichten der Zielentität, die gerendert werden soll. Sie können mehrere Ansichten auswählen, um Datensätze in der Liste anzuzeigen. Das zuerst ausgewählte Ansicht wird zur Standardansicht.

    - **Neuen Datensatz erstellen**: Damit können Benutzer einen neuen Datensatz erstellen. Wählen Sie eine Webseite aus, die ein Formular enthält, um einen neuen Datensatz zu erstellen.

    - **Details anzeigen**: Damit können Benutzer sich Details ansehen. Wählen Sie eine Webseite aus, die ein Formular enthält, um Details anzuzeigen.

    - **Datensatz bearbeiten**: Damit können Benutzer einen Datensatz bearbeiten. Wählen Sie eine Webseite aus, die ein Formular enthält, um den Datensatz zu bearbeiten.

    - **Datensatz löschen**: Damit können Benutzer einen Datensatz löschen.

    - **Leere Listenmeldung**: Meldung, die angezeigt wird, wenn keine Datensätze vorhanden sind, die angezeigt werden können.

    - **Anzahl der Datensätze pro Seite**: Ein ganzzahliger Wert, um die Anzahl der Datensätze anzugeben, die auf einer Seite angezeigt werden.

    - **Suche in der Entitätsliste aktivieren**: Damit können Benutzer in der Liste nach Datensätzen suchen.

    - **Entitätsberechtigungen aktivieren**: Entitätsberechtigungen, die für die Liste berücksichtigt werden sollen. Dies ist standardmäßig nicht ausgewählt. Wenn diese Option ausgewählt ist, sind explizite Berechtigungen für jeden Benutzer erforderlich, der auf das Formular zugreifen möchte. Weitere Informationen: [Entitätsberechtigung](configure/assign-entity-permissions.md)  

    > [!div class=mx-imgBorder]
    > ![Eigenschaften auflisten](media/list-props.png "Eigenschaften auflisten")

### <a name="add-breadcrumb"></a>Hinzufügen eines Breadcrumbs

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.  

2.  Wählen Sie die Seite aus, auf der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein bearbeitbares Element auf dem Canvas aus.

4.  Wählen Sie **Komponenten** ![Komponentensymbol](media/components-icon.png "Komponentensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.  

5.  Wählen Sie unter **Portalkomponenten** die Option **Breadcrumb**.

## <a name="add-a-custom-menu"></a>Hinzufügen eines benutzerdefinierten Menüs

Standardmäßig wird das Menü auf der Website automatisch anhand der Hierarchie der Webseiten erstellt. Dies wird als **Standardmenü** bezeichnet. Wenn Sie ein benutzerdefiniertes Menü erstellen möchten, müssen Sie den Weblinksatz in der Portalverwaltungs-App erstellen. Weitere Informationen: [Verwalten von Weblinks](configure/manage-web-links.md)

Nachdem Sie den Weblinksatz erstellt haben:

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.

2.  Wählen Sie die Header-Komponente aus. 

3.  Wählen Sie in den Eigenschaften auf der rechten Seite des Bildschirms den Weblinksatz aus der Liste **Navigationsmenü** aus.

    > [!div class=mx-imgBorder]
    > ![Navigationsmenü](media/navigation-menu.png "Navigationsmenü")

## <a name="use-code-editor"></a>Verwenden des Code-Editors

Um die Quelle einer Komponente aus dem Canvas anzuzeigen, wählen Sie die Komponente und dann das Symbol für den Quellcode-Editor **&lt;/&gt;** in der Fußzeile aus.

> [!div class=mx-imgBorder]
> ![Code-Editor-Symbol](media/code-editor-icon.png "Code-Editor-Symbol")  

Der Quellcode wird im Bereich **Code-Editor** am unteren Bildschirmrand angezeigt. Die Änderungen, die Sie zuvor vorgenommen haben, werden im Quellcode aktualisiert. Wenn Sie Änderungen vornehmen möchten, aktualisieren Sie den Quellcode und wählen Sie **Speichern** aus. Die Änderungen werden im Canvas berücksichtigt.

> [!div class=mx-imgBorder]
> ![Code-Editor](media/code-editor.png "Code-Editor") 

> [!NOTE]
> Sie können im Quellcode-Editor Liquid-Tags für die erweiterte Konfiguration hinzufügen. Weitere Informationen: [Arbeiten mit Liquid-Vorlagen](liquid/liquid-overview.md)


