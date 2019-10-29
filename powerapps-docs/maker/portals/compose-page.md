---
title: Erstellen von Webseiten | Microsoft-Dokumentation
description: Anweisungen zum Verfassen von Webseiten im Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cec2b106ba35f73a34128e9e89233c18d2d70dd1
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975700"
---
# <a name="compose-a-page"></a>Zusammenstellen einer Seite

Nach dem Hinzufügen der erforderlichen Webseiten und der Verwaltung Ihrer Hierarchie in der Sitemap können Sie verschiedene Komponenten hinzufügen. Mit dem WYSIWYG-Editor können Sie die erforderlichen Komponenten auf der Canvas problemlos hinzufügen und bearbeiten. Sie können die folgenden Komponenten auf der Canvas hinzufügen und bearbeiten:

- Abschnitte
    - Ein Spalten Abschnitt
    - Abschnitt mit zwei Spalten
    - Abschnitt mit drei Spalten
- Portal Komponenten
    - Text
    - Bild
    - IFrame
    - Formular
    - List
    - Breadcrumb

> [!NOTE]
> Wenn Sie Ihr Portal mithilfe von powerapps Portale Studio anpassen, bemerken die Benutzer der Website eine Beeinträchtigung der Leistung. Es wird empfohlen, dass Sie die Änderungen in einem Live Portal außerhalb der Spitzenzeiten durchführen. 

## <a name="use-the-wysiwyg-editor"></a>Verwenden des WYSIWYG-editors

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.  

2.  Wählen Sie die Seite aus, der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein Editier bares Element im Zeichenbereich aus.

    > [!NOTE]
    > Die bearbeitbaren Elemente werden durch eine Grenze abgegrenzt.

4.  Wählen Sie im toolbelt auf der linken Seite des Bildschirms **Komponenten** Komponenten ![Symbol](media/components-icon.png "Komponenten") aus.  

5.  Wählen Sie die Komponente aus, die hinzugefügt werden soll.

    > [!div class=mx-imgBorder]
    > ![Komponentenbereich](media/components-pane.png "Komponenten") Bereich  

    Die ausgewählte Komponente wird der Canvas im bearbeitbaren Element hinzugefügt.

6.  Um eine Komponente zu löschen, wählen Sie die Komponente im Zeichenbereich aus, und wählen Sie dann in der Befehlsleiste am oberen Rand der Seite die Option **Löschen** aus.

    > [!div class=mx-imgBorder]
    > Komponente zum(media/delete-component.png "Löschen") der ![Komponente löschen]  

## <a name="add-sections"></a>Abschnitte hinzufügen

In den Abschnitten können Sie eine Struktur für die Seite definieren und Portal Komponenten entsprechend anordnen. Wenn Sie der Seite Abschnitte hinzufügen, können Sie in den Abschnitten nach Bedarf Portal Komponenten hinzufügen.

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.

2.  Wählen Sie die Seite aus, für die Sie einen Abschnitt hinzufügen möchten.

3.  Wählen Sie ein Editier bares Element im Zeichenbereich aus.

4.  Wählen Sie im toolbelt auf der linken Seite des Bildschirms **Komponenten** Komponenten ![Symbol](media/components-icon.png "Komponenten") aus.

5.  Wählen Sie unter **Abschnitts Layout**den Typ aus, der eingefügt werden soll.

6.  Geben Sie im Eigenschaften Bereich auf der rechten Seite des Bildschirms die folgenden Informationen ein, oder wählen Sie Sie aus:

    - **Min height**: Geben Sie die Mindesthöhe des Abschnitts ein. Wenn Sie eine Komponente hinzufügen, die mehr Platz als die angegebene Höhe einnimmt, wird der Abschnitt erweitert, um die Komponente aufzunehmen. Standardmäßig beträgt die Mindesthöhe 100 px. Sie können auch die Höhe in Punkte (PT) und in Prozent (%) eingeben.

        > [!div class=mx-imgBorder]
        > ![Ausrichtung in der Abschnitts](media/section-props-height.png "Ausrichtung im Abschnitt")  

    - **Ausrichtung**: Wählen Sie aus, ob die Komponente im Abschnitt Links, zentriert oder rechtsbündig ausgerichtet werden muss.

        > [!div class=mx-imgBorder]
        > ![Ausrichtung in der Abschnitts](media/section-props-align.png "Ausrichtung im Abschnitt")  

    - **Background**: Wählen Sie diese Option aus, wenn die Farbe oder ein Bild als Abschnitts Hintergrund aussehen soll.

        - **Fill**: Wählen Sie eine Farbe für den Hintergrund aus.

            > [!div class=mx-imgBorder]
            > ![Füllfarbe in der](media/section-props-fill.png "Füllfarbe des Abschnitts im Abschnitt")  

        - **Image**: Wählen Sie ein Bild aus der Liste aus. Wenn Sie ein neues Bild hochladen möchten, wählen Sie **Bild hochladen**aus.

            > [!div class=mx-imgBorder]
            > ![Fügen Sie das Bild im]Abschnitt(media/section-props-image.png "Hinzufügen eines Bilds im Abschnitt") hinzu.  

7.  Fügen Sie im Abschnitt die erforderliche Portal Komponente hinzu.


## <a name="add-portal-components"></a>Hinzufügen von Portal Komponenten

Sie können die folgenden Komponenten auf einer Webseite hinzufügen:

- [Text](#add-text-box)
- [Bild](#add-image)
- [IFrame](#add-iframe)
- [Formular](#add-form)
- [List](#add-list)
- [Breadcrumb](#add-breadcrumb)


### <a name="add-text-box"></a>Hinzufügen des Textfelds

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.  

2.  Wählen Sie die Seite aus, der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein Editier bares Element im Zeichenbereich aus.

4.  Wählen Sie im toolbelt auf der linken Seite des Bildschirms **Komponenten** Komponenten ![Symbol](media/components-icon.png "Komponenten") aus.  

5.  Wählen Sie unter " **Portal Komponenten**" die Option **Text**aus.

6.  Geben Sie den erforderlichen Text in das Textfeld ein.

7.  Um den Text zu formatieren, wählen Sie den Text aus, um die Formatierungsoptionen anzuzeigen. Ändern Sie den Schrift Grad und den Stil nach Bedarf.

    > [!div class=mx-imgBorder]
    > Text ![Komponenten](media/text-component.png "Text-Komponente")  

8. Wählen Sie im Bereich Eigenschaften auf der rechten Seite des Bildschirms die folgenden Informationen aus:

    - **Ausrichtung**: Wählen Sie aus, ob der Text Links, zentriert oder rechtsbündig ausgerichtet werden muss.

    - **Schriftart Farbe**: Wählen Sie eine Farbe für den Text aus.

        > [!div class=mx-imgBorder]
        > ![Textausrichtung und]-Farbe auswählen wählen Sie(media/text-props.png "Textausrichtung und-Farbe") aus  
 

### <a name="add-image"></a>Bild hinzufügen

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.  

2.  Wählen Sie die Seite aus, der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein Editier bares Element im Zeichenbereich aus.

4.  Wählen Sie im toolbelt auf der linken Seite des Bildschirms **Komponenten** Komponenten ![Symbol](media/components-icon.png "Komponenten") aus.  

5.  Wählen Sie unter " **Portal Komponenten**" die Option **Bild**aus. Der Bild Platzhalter wird der Canvas hinzugefügt.

6.  Geben Sie im Eigenschaften Bereich auf der rechten Seite des Bildschirms die folgenden Informationen ein:

    - **Image**: Wählen Sie diese Option aus, wenn Sie ein vorhandenes Bild auswählen oder ein neues hochladen möchten. Wenn Sie ein zuvor hochgeladenes Image auswählen möchten, wählen Sie ein Bild aus der Liste **Image auswählen** aus. Wählen Sie zum Hochladen eines neuen Bilds **Bild hochladen**aus. Alle hochgeladenen Bilder sind in der Bildbibliothek enthalten, die in der Liste **Image auswählen** erneut ausgewählt werden kann.

        > [!div class=mx-imgBorder]
        > Bild(media/image-props.png "Eigenschaften der") ![Bildeigenschaften]  

        > [!NOTE]
        > - Sie können nur die Bilder des Typs PNG, SVG, JPG und JPEG mit der maximalen Größe von 5 MB hochladen.
        > - Ein Bild mit dem gleichen Namen kann nicht hochgeladen werden. Sie müssen den Namen des Images ändern, um es erneut hochladen zu können.

    - **Externe URL**: Wählen Sie diese Option aus, wenn Sie ein Bild aus einer externen URL hochladen möchten. Geben Sie die URL in das Feld **externe URL** ein. Nur gesicherte Verknüpfungen werden akzeptiert, d. –. https://ist obligatorisch. Wenn Sie Bilder in Ihrem Content Delivery Network gespeichert haben, können Sie den Link in diesem Feld angeben.

        > [!div class=mx-imgBorder]
        > externe(media/image-ext-url.png "URL für") ![Bild externe URL]  

    -   **Formatierungsoptionen**

        - **Width**: Geben Sie die Breite des Bilds ein.

        - **Height**: Geben Sie die Höhe des Bilds ein.

    > [!NOTE]
    > Sie können auch das Bild auf der Canvas auswählen und die Zieh Punkte ziehen, um die Größe zu ändern.

### <a name="add-iframe"></a>Iframe hinzufügen

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.  

2.  Wählen Sie die Seite aus, der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein Editier bares Element im Zeichenbereich aus.

4.  Wählen Sie im toolbelt auf der linken Seite des Bildschirms **Komponenten** Komponenten ![Symbol](media/components-icon.png "Komponenten") aus.  

5.  Wählen Sie unter **Portal Komponenten**die Option **iframe**aus. Der iframe-Platzhalter wird der Canvas hinzugefügt.

6.  Geben Sie im Eigenschaften Bereich auf der rechten Seite des Bildschirms die folgenden Informationen ein:

    - **Width**: gibt die Breite des iframes an.

    - **Height**: gibt die Höhe des iframes an.

    - **Link**: Geben Sie die URL der Website ein, die im iframe angezeigt werden soll. Nur gesicherte Verknüpfungen werden akzeptiert, d. –. https://ist obligatorisch. Standardmäßig ist <https://www.bing.com> als Wert verfügbar.

        > [!div class=mx-imgBorder]
        > iframe- ![Eigenschaften]((media/iframe-props.png "iframe") -Eigenschaften)  

    > [!NOTE]
    > Sie können auch den IFRAME auf der Canvas auswählen und die Zieh Punkte ziehen, um die Größe zu ändern.

### <a name="add-form"></a>Formular hinzufügen

Das Formular ist eine datengesteuerte Konfiguration, mit der Sie ein Formular zum Sammeln von Daten im Portal hinzufügen, ohne dass ein Entwickler das Formular im Portal verwenden muss. [Formulare werden in Common Data Service erstellt](https://docs.microsoft.com/powerapps/maker/model-driven-apps/form-designer-overview) , und Sie können Sie in Webseiten im Portal oder in Verbindung mit Listen verwenden, um umfassende Webanwendungen zu erstellen.  

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.  

2.  Wählen Sie die Seite aus, der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein Editier bares Element im Zeichenbereich aus.

4.  Wählen Sie im toolbelt auf der linken Seite des Bildschirms **Komponenten** Komponenten ![Symbol](media/components-icon.png "Komponenten") aus.  

5.  Wählen Sie unter " **Portal Komponenten**" die Option **Formular**aus.

6.  Wählen Sie im Bereich Eigenschaften auf der rechten Seite des Bildschirms eine der folgenden Optionen aus:

    - **Neu erstellen**: Erstellen Sie ein neues Formular.
    - **Vorhandene verwenden**: Verwenden Sie ein vorhandenes Formular.

7. Geben Sie Informationen ein, oder treffen Sie eine Auswahl für Folgendes:

    - **Name**: der Name des Formulars.

    - **Entity**: der Name der Entität, von der das Formular geladen wird.

    - **Formularlayout**: der Name des Formulars in der Ziel Entität in Common Data Service, das gerendert werden soll.

    - **Modus**: Wählen Sie eine der folgenden Optionen aus:

        - **Insert**: gibt an, dass das Formular beim Einreichen einen neuen Datensatz einfügen soll.

        - **Edit**: gibt an, dass das Formular einen vorhandenen Datensatz bearbeiten soll.

        - **Read Only**: gibt an, dass im Formular das nicht bearbeitbare Formular eines vorhandenen Datensatzes angezeigt werden soll.

        > [!NOTE]
        > Die Standardoption für **den Modus "** **Bearbeiten** " und "schreibgeschützt" wird als Parameter Name der Abfrage Zeichenfolge festgelegt. Um diese Werte zu ändern, müssen Sie die Portal Verwaltungs-APP öffnen und die Formular Eigenschaften aktualisieren.

    - **Bei Erfolg**: Wählen Sie eine der folgenden Optionen aus:

        - **Erfolgsmeldung anzeigen**: erfordert eine Meldung, die dem Benutzer bei erfolgreicher Übermittlung des Formulars angezeigt wird. Sie können bei **Erfolg auch Formular ausblenden** auswählen, um das Formular nach erfolgreicher Übermittlung auszublenden.

        - **An Webseite umleiten**: leitet den Benutzer an die ausgewählte Webseite im Portal um. Sie müssen eine Webseite aus der Liste **an Webseite umleiten** auswählen.

        - **An URL umleiten**: leitet den Benutzer zur angegebenen URL um. Sie müssen eine URL in das Feld **Umleitung an URL** eingeben.

    - **CAPTCHA für anonyme Benutzer anzeigen**: zeigt CAPTCHA für anonyme Benutzer an.

    - **CAPTCHA für authentifizierte Benutzer anzeigen**: zeigt CAPTCHA für authentifizierte Benutzer an.

    - **Entitäts Berechtigungen aktivieren**: Entitäts Berechtigungen, die für das Formular berücksichtigt werden sollen. Standardmäßig ist diese Option nicht ausgewählt. Wenn diese Option ausgewählt ist, sind explizite Berechtigungen für jeden Benutzer erforderlich, um auf das Formular zuzugreifen. Weitere Informationen: [Entitäts Berechtigung](https://docs.microsoft.com/dynamics365/customer-engagement/portals/assign-entity-permissions)

        > [!div class=mx-imgBorder]
        > Formular ![Eigenschaften (](media/form-props.png "Formular Eigenschaften)")

### <a name="add-list"></a>Liste hinzufügen

Die Liste ist eine datengesteuerte Konfiguration, mit der Sie eine Webseite hinzufügen, die eine Liste von Datensätzen Renderer, ohne dass ein Entwickler das Raster im Portal anzeigen muss. Listen verwenden [Common Data Service Ansichten](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-and-edit-views) zum Anzeigen von Datensätzen im Portal.  

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.  

2.  Wählen Sie die Seite aus, der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein Editier bares Element im Zeichenbereich aus.

4.  Wählen Sie im toolbelt auf der linken Seite des Bildschirms **Komponenten** Komponenten ![Symbol](media/components-icon.png "Komponenten") aus.  

5.  Wählen Sie unter " **Portal Komponenten**" die Option **Liste**aus.

6.  Wählen Sie im Bereich Eigenschaften auf der rechten Seite des Bildschirms eine der folgenden Optionen aus:

    - **Neu erstellen**: Erstellen Sie eine neue Liste.
    - **Vorhandene verwenden**: vorhandene Liste verwenden.

7.  Geben Sie Informationen ein, oder treffen Sie eine Auswahl für Folgendes:

    - **Name**: Name der Liste.

    - **Entity**: der Name der Entität, von der die Sichten geladen werden.

    - **Sichten**: die Liste der Sichten der Ziel Entität, die gerendert werden soll. Sie können mehrere Ansichten auswählen, um Datensätze in der Liste anzuzeigen. Die erste ausgewählte Ansicht ist die Standardansicht.

    - **Neuen Datensatz erstellen**: ermöglicht es einem Benutzer, einen Datensatz zu erstellen. Wählen Sie eine Webseite aus, die ein Formular zum Erstellen eines neuen Datensatzes enthält.

    - **Details anzeigen**: ermöglicht Benutzern das Anzeigen von Details. Wählen Sie eine Webseite aus, die ein Formular zum Anzeigen von Details enthält.

    - **Datensatz bearbeiten**: ermöglicht es einem Benutzer, einen Datensatz zu bearbeiten. Wählen Sie eine Webseite aus, die ein Formular zum Bearbeiten des Datensatzes enthält.

    - **Datensatz löschen**: ermöglicht einem Benutzer das Löschen eines Datensatzes.

    - **Leere Listen Meldung**: die Meldung, die angezeigt werden soll, wenn keine Datensätze angezeigt werden sollen.

    - **Anzahl der Datensätze pro Seite**: ein ganzzahliger Wert, der die Anzahl der Datensätze angibt, die auf einer Seite angezeigt werden sollen.

    - **Suche in Entitäts Liste aktivieren**: ermöglicht einem Benutzer das Durchsuchen von Datensätzen in der Liste.

    - **Entitäts Berechtigungen aktivieren**: Entitäts Berechtigungen, die für die Liste berücksichtigt werden sollen. Standardmäßig ist diese Option nicht ausgewählt. Wenn diese Option ausgewählt ist, sind explizite Berechtigungen für jeden Benutzer erforderlich, um auf das Formular zuzugreifen. Weitere Informationen: [Entitäts Berechtigung](https://docs.microsoft.com/dynamics365/customer-engagement/portals/assign-entity-permissions)  

    > [!div class=mx-imgBorder]
    > Eigenschaften der ![Listen Eigenschaften](media/list-props.png "Liste")

### <a name="add-breadcrumb"></a>Breadcrumb hinzufügen

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.  

2.  Wählen Sie die Seite aus, der Sie die Komponente hinzufügen möchten.

3.  Wählen Sie ein Editier bares Element im Zeichenbereich aus.

4.  Wählen Sie im toolbelt auf der linken Seite des Bildschirms **Komponenten** Komponenten ![Symbol](media/components-icon.png "Komponenten") aus.  

5.  Wählen Sie unter " **Portal Komponenten**" **Breadcrumb**aus.

## <a name="add-a-custom-menu"></a>Hinzufügen eines benutzerdefinierten Menüs

Standardmäßig wird das Menü auf der Website basierend auf der Hierarchie der Webseiten automatisch erstellt. Sie wird als **Standard** Menü bezeichnet. Zum Erstellen eines benutzerdefinierten Menüs müssen Sie den Weblink erstellen, der in der Portal Verwaltungs-App festgelegt ist. Weitere Informationen finden Sie unter [Verwalten von Weblinks](https://docs.microsoft.com/dynamics365/customer-engagement/portals/manage-web-links) .

Nachdem Sie den weblinksatz erstellt haben:

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.

2.  Wählen Sie die Header Komponente aus. 

3.  Wählen Sie in den Eigenschaften auf der rechten Seite des Bildschirms den Namen des weblinksets in der Liste **Navigationsmenü** aus.

    > [!div class=mx-imgBorder]
    > Navigations(media/navigation-menu.png "Menü für") ![Navigationsmenü]

## <a name="use-code-editor"></a>Verwenden des Code-Editors

Um die Quelle einer Komponente im Zeichenbereich anzuzeigen, wählen Sie die Komponente aus, und wählen Sie dann das Symbol Quell Code-Editor aus, **&lt;/&gt;** in der Fußzeile aus.

> [!div class=mx-imgBorder]
> Symbol für Code- ![Editor]-Symbol(media/code-editor-icon.png "Code-Editor")  

Der Quellcode wird im Bereich Code- **Editor** unten auf dem Bildschirm angezeigt. Die Änderungen, die Sie zuvor vorgenommen haben, werden im Quellcode aktualisiert. Aktualisieren Sie den Quellcode, und wählen Sie **Speichern**aus, um Änderungen vorzunehmen. Die Änderungen werden im Zeichenbereich widergespiegelt.

> [!div class=mx-imgBorder]
> Code(media/code-editor.png "-Editor für") ![Code]-Editor 

> [!NOTE]
> Sie können auch Liquid-Tags im Quellcode-Editor für die erweiterte Konfiguration hinzufügen. Weitere Informationen finden Sie [unter Arbeiten mit Liquid-Vorlagen](https://docs.microsoft.com/dynamics365/customer-engagement/portals/custom-templates-dynamic-content) .


