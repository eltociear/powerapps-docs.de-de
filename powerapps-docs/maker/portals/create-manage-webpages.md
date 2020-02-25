---
title: Erstellen und Verwalten von Webseiten | MicrosoftDocs
description: Anweisungen zum Erstellen und Verwalten von Webseiten in einem Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 542622e814c2d650cbf3d6a4d3354bb363174e12
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980699"
---
# <a name="create-and-manage-webpages"></a>Erstellen und Verwalten von Webseiten

Eine Website ist ein Dokument, das über eine eindeutige URL in einer Website identifiziert wird. Sie ist eines der Kernobjekte der Website und bildet durch übergeordnete und untergeordnete Beziehungen zu anderen Webseiten eine Hierarchie der Website.

> [!NOTE]
> Wenn Sie Ihr Portal mithilfe des Power Apps-Portalstudios anpassen, würden die Websitebenutzer eine Auswirkung auf die Leistung feststellen. Wir empfehlen daher, die Änderungen nicht während der Hauptnutzungszeiten auf einem Liveportal durchzuführen.

## <a name="create-webpage"></a>Erstellen einer Webseite

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.  

2.  In der Befehlsleiste wählen Sie **Neue Seite** und entweder eine Seite aus **Layouts** oder **Feste Layouts** aus.

    > [!div class=mx-imgBorder]
    > ![Neue Webseite erstellen](media/create-webpage.png "Neue Webseite erstellen")

    > [!NOTE]
    > - Das Erstellen einer Seite mit **Layouts** gibt Ihnen die Flexibilität, die gesamte Seite zu bearbeiten. **Feste Layouts** enthält die Seitenvorlagen, die im Rahmen der Portalbereitstellung und benutzerdefinierten Seiten der Vorlagen mithilfe der [Portalverwaltungs-App](configure/configure-portal.md) installiert werden.
    > - Für die Seiten, die mithilfe der Option **Layouts** erstellt werden, ist eine neue **Standardstudiovorlage**-Seitenvorlage installiert.

3.  Geben Sie im Eigenschaftenbereich auf der rechten Seite des Bildschirms die folgenden Informationen ein:

    - **Name**: Der Name der Seite. Dieser Wert wird auch als Titel der Seite verwendet.

    - **Teil-URL**: Das URL-Pfadsegment, das zur Erstellung der Portal-URL dieser Seite verwendet wird.

    - **Vorlage**: Die Seitenvorlage, die zum Rendern dieser Seite im Portal verwendet wird. Bei Bedarf kann eine andere Vorlage aus der Liste ausgewählt werden.

        > [!div class=mx-imgBorder]
        > ![Webseiteneigenschaften](media/webpage-props.png "Webseiteneigenschaften")

Die von Ihnen erstellten Webseiten werden hinzugefügt und ihre Hierarchie wird im Bereich **Seiten** angezeigt. Um den Bereich **Seiten** anzuzeigen, wählen Sie **Seiten** ![Seitensymbol](media/pages-icon.png "Seitensymbol") aus dem Funktionsangebot auf der linken Seite des Bildschirms aus.  

Gehen wir davon aus, Sie haben einige Webseiten für Ihr Portal erstellt. Die Seitenhierarchie sieht wie folgt aus:

> [!div class=mx-imgBorder]
> ![Seitenbereich](media/pages-pane.png "Seitenbereich")  

Das primäre Menü auf der Website wird automatisch anhand der Hierarchie der Webseiten erstellt. Dies wird als **Standardmenü** bezeichnet. Sie können auch ein benutzerdefiniertes Menü erstellen, das auf der Website angezeigt wird. Weitere Informationen: [Hinzufügen eines benutzerdefinierten Menüs](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![Website-Navigation](media/website-navigation.png "Website-Navigation")

Wenn Sie mit einem Portal arbeiten, das in einer Umgebung, die modelgesteuerte Apps in Dynamics 365 enthält, erstellt wurde und das Menü mit der Seitenhierarchie übereinstimmen soll, müssen Sie **Standard** aus der Liste **Navigationsmenü** auswählen.

> [!div class=mx-imgBorder]
> ![Standard-Navigationsmenü](media/navigation-menu-default.png "Standard-Navigationsmenü")

## <a name="manage-webpage"></a>Verwalten der Webseite

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit), um es im Power Apps-Portalstudio zu öffnen.  

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
        > ![Webseite verwalten Optionen](media/webpage-manage-options.png "Webseite verwalten Optionen")  





