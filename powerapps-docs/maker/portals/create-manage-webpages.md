---
title: Erstellen und Verwalten von Webseiten | MicrosoftDocs
description: Anweisungen zum Erstellen und Verwalten von Webseiten in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 09/16/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-and-manage-webpages"></a>Erstellen und Verwalten von Webseiten

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Eine Website ist ein Dokument, das über eine eindeutige URL in einer Website identifiziert wird. Sie ist eines der Kernobjekte der Website und bildet durch übergeordnete und untergeordnete Beziehungen zu anderen Webseiten eine Hierarchie der Website.

> [!NOTE]
> Wenn Sie das Portal mithilfe des Portaldesigners anpassen, würden die Websitebenutzer eine Auswirkung auf die Leistung feststellen. Wir empfehlen daher, die Änderungen nicht während der Hauptnutzungszeiten auf einem Liveportal durchzuführen.

## <a name="create-webpage"></a>Erstellen einer Webseite

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Portaldesigner zu öffnen.  

2.  Wählen Sie in der Befehlsleiste die Option **Neue Seite** und dann die Seitenvorlage aus.

    > [!div class=mx-imgBorder]
    > ![Erstellen einer neuen Webseite](media/create-webpage.png "Erstellen einer neuen Webseite")

3.  Geben Sie im Eigenschaftenbereich auf der rechten Seite des Bildschirms die folgenden Informationen ein:

    - **Name**: Der Name der Seite. Dieser Wert wird auch als Titel der Seite verwendet.

    - **Teil-URL**: Das URL-Pfadsegment, das zur Erstellung der Portal-URL dieser Seite verwendet wird.

    - **Vorlage**: Die Seitenvorlage, die zum Rendern dieser Seite im Portal verwendet wird. Bei Bedarf kann eine andere Vorlage aus der Liste ausgewählt werden.

        > [!div class=mx-imgBorder]
        > ![Webseiteneigenschaften](media/webpage-props.png "Webseiteneigenschaften")

Die von Ihnen erstellten Webseiten werden hinzugefügt und ihre Hierarchie wird im Bereich **Seiten** angezeigt. Um den Bereich **Seiten** anzuzeigen, wählen Sie **Seiten** ![Seitensymbol](media/pages-icon.png "Seitensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.  

Gehen wir davon aus, Sie haben einige Webseiten für Ihr Portal erstellt. Die Seitenhierarchie sieht wie folgt aus:

> [!div class=mx-imgBorder]
> ![Bereich "Seiten"](media/pages-pane.png "Bereich \"Seiten\"")  

Das primäre Menü auf der Website wird automatisch anhand der Hierarchie der Webseiten erstellt. Dies wird als **Standardmenü** bezeichnet. Sie können auch ein benutzerdefiniertes Menü erstellen, das auf der Website angezeigt wird. Weitere Informationen: [Hinzufügen eines benutzerdefinierten Menüs](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![Websitenavigation](media/website-navigation.png "Websitenavigation")

Wenn Sie mit Dynamics 365-Portalen arbeiten und das Menü mit der Seitenhierarchie übereinstimmen soll, müssen Sie **Standard** aus der Liste **Navigationsmenü** auswählen.

> [!div class=mx-imgBorder]
> ![Standardnavigationsmenü](media/navigation-menu-default.png "Standardnavigationsmenü")

## <a name="manage-webpage"></a>Verwalten der Webseite

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Portaldesigner zu öffnen.  

2.  Wählen Sie **Seiten** ![Seitensymbol](media/pages-icon.png "Seitensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.  

3.  Bewegen Sie den Mauszeiger über die Seite, die Sie verwalten möchten, und wählen Sie die Schaltfläche mit den **Auslassungspunkten** (…) für die Webseite aus, die Sie verwalten möchten. Abwechselnd können Sie mit der rechten Maustaste auf die entsprechende Seite klicken, die Sie verwalten möchten.

4.  Wählen Sie im Kontextmenü die erforderlichen Aktion aus:

    - **Im Standardmenü ausblenden**: Blenden Sie die Seite aus, sodass sie über das Standardmenü nicht in der Siteübersicht angezeigt wird.

    - **Im Standardmenü anzeigen**: Sie können die Seite über das Standardmenü in der Siteübersicht anzeigen.

    - **Untergeordnete Seite hinzufügen**: Sie können der ausgewählten Seite eine untergeordneten Seite hinzufügen. Die untergeordnete Seite übernimmt die Seitenvorlage ihrer übergeordneten Seite.

    - **Als Homepage festlegen**: Sie können die Seite damit als Homepage festlegen. Die URL der neuen Homepage wird auf dem Stamm der Website festgelegt und die URL der alten Seite entsprechend aktualisiert.

    - **Nach oben**: Damit können Sie die Seite in der Hierarchie nach oben verschieben.

    - **Nach unten**: Damit können Sie die Seite in der Hierarchie nach unten verschieben.

        > [!NOTE]
        > Das Verschieben einer Seite nach oben oder unten wird bei Seiten auf derselben Ebene unterstützt.

    - **Unterseite hochstufen**: Verringern Sie den Einzug und legen Sie die untergeordnete Seite auf die Ebene der vorherigen Seite in der Hierarchie.

    - **Unterseite erstellen**: Erhöhen Sie den Einzug und machen Sie die Seite zu einer untergeordneten Seite der vorherigen Seite in der Hierarchie.

    - **Löschen**: Löschen Sie die Seite.

        > [!div class=mx-imgBorder]
        > ![Verwaltungsoptionen der Webseite](media/webpage-manage-options.png "Verwaltungsoptionen der Webseite")  





