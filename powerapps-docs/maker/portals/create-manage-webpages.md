---
title: Erstellen und Verwalten von Webseiten | Microsoft-Dokumentation
description: Anweisungen zum Erstellen und Verwalten von Webseiten im Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 26bb1186710bbf0bc3fd40765459638245f3b027
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542593"
---
# <a name="create-and-manage-webpages"></a>Erstellen und Verwalten von Webseiten

Eine Webseite ist ein Dokument, das durch eine eindeutige URL auf einer Website identifiziert wird. Es ist eines der Kern Objekte der Website und erstellt eine Hierarchie der Website über übergeordnete und untergeordnete Beziehungen zu anderen Webseiten.

> [!NOTE]
> Wenn Sie Ihr Portal mithilfe von powerapps Portale Studio anpassen, bemerken die Benutzer der Website eine Beeinträchtigung der Leistung. Es wird empfohlen, dass Sie die Änderungen in einem Live Portal außerhalb der Spitzenzeiten durchführen.

## <a name="create-webpage"></a>Webseite erstellen

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.  

2.  Wählen Sie in der Befehlsleiste **neue Seite** aus, und wählen Sie entweder eine Seite aus **Layouts** oder **fixierten Layouts**aus.

    > [!div class=mx-imgBorder]
    > ![neue Webseite erstellen](media/create-webpage.png "Neue Webseite erstellen")

    > [!NOTE]
    > - Das Erstellen einer Seite mithilfe von **Layouts** bietet Ihnen die Flexibilität, die gesamte Seite zu bearbeiten. **Festgelegte Layouts** enthalten die Seitenvorlagen, die im Rahmen der Portal Bereitstellung installiert werden, sowie die benutzerdefinierten Seitenvorlagen, die mithilfe der [Portal Verwaltungs-App](configure/configure-portal.md)erstellt wurden.
    > - Für die Seiten, die mithilfe der **Layouts** -Option erstellt werden sollen, wird eine neue Vorlage für die Vorlagen Seite " **Standardvorlage** " installiert.

3.  Geben Sie im Eigenschaften Bereich auf der rechten Seite des Bildschirms die folgenden Informationen ein:

    - **Name**: der Name der Seite. Dieser Wert wird auch als Titel der Seite verwendet.

    - **Partielle URL**: das URL-Pfad Segment, das verwendet wird, um die Portal-URL dieser Seite zu erstellen.

    - **Vorlage**: Seitenvorlage, die zum Rendering dieser Seite im Portal verwendet wird. Falls erforderlich, können Sie eine andere Vorlage in der Liste auswählen.

        > [!div class=mx-imgBorder]
        > ![Webseiten Eigenschaften](media/webpage-props.png "Webseiten Eigenschaften")

Die von Ihnen erstellten Webseiten werden hinzugefügt, und ihre Hierarchie wird im **Seiten** Bereich angezeigt. Um den **Seiten** Bereich anzuzeigen, wählen Sie im toolbelt auf der linken Seite des Bildschirms **Seiten** ![Seiten Symbol](media/pages-icon.png "Seiten Symbol") aus.  

Nehmen wir an, Sie haben einige Webseiten für Ihr Portal erstellt. Die Seiten Hierarchie sieht wie folgt aus:

> [!div class=mx-imgBorder]
> ![Seitenbereich](media/pages-pane.png "Seitenbereich")  

Das primäre Menü auf der Website wird automatisch basierend auf der Hierarchie der Webseiten erstellt. Sie wird als **Standard** Menü bezeichnet. Sie können auch ein benutzerdefiniertes Menü erstellen, das auf der Website angezeigt wird. Weitere Informationen: [Hinzufügen eines benutzerdefinierten Menüs](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![Website Navigation](media/website-navigation.png "Website Navigation")

Wenn Sie mit einem Portal arbeiten, das in einer Umgebung erstellt wurde, die Modell gesteuerte apps in Dynamics 365 enthält, und Sie möchten, dass das Menü mit der Seiten Hierarchie identisch ist, müssen Sie **Standard** in der **Navigationsmenü** Liste auswählen.

> [!div class=mx-imgBorder]
> ![Standard-Navigationsmenü](media/navigation-menu-default.png "Standard-Navigationsmenü")

## <a name="manage-webpage"></a>Webseite verwalten

1.  [Bearbeiten Sie das Portal](manage-existing-portals.md#edit) , um es in powerapps Portals Studio zu öffnen.  

2.  Wählen Sie im toolbelt auf der linken Seite des Bildschirms **Seiten** ![Seiten Symbol](media/pages-icon.png "Seiten Symbol") aus.  

3.  Zeigen Sie auf die Seite, die Sie verwalten möchten, und wählen Sie **die Schaltfläche** mit den Auslassungs Punkten (...) für die zu verwaltende Webseite aus. Abwechselnd. Sie können mit der rechten Maustaste auf die Seite klicken, die Sie verwalten möchten.

4.  Wählen Sie im Kontextmenü die erforderliche Aktion aus:

    - **Im Standardmenü ausblenden**: Blendet die Seite aus, die im Menü "Sitemap über Default" angezeigt wird.

    - **In Standardmenü anzeigen**: zeigt die Seite im Menü "Sitemap über Standard" an.

    - **Hinzufügen einer**untergeordneten Seite: Fügen Sie der ausgewählten Seite eine untergeordnete Seite hinzu. Die untergeordnete Seite erbt die Seitenvorlage der übergeordneten Seite.

    - **Als Startseite festlegen**: Legen Sie die Seite als Startseite fest. Die URL der neuen Startseite wird auf das Stammverzeichnis der Website festgelegt, und die URL der alten Seite wird entsprechend aktualisiert.

    - Nach **oben**: verschiebt die Seite in der Hierarchie nach oben.

    - **Nach unten**: verschiebt die Seite in der Hierarchie nach unten.

        > [!NOTE]
        > Das Verschieben einer Seite nach oben oder unten wird zwischen den Seiten auf derselben Ebene unterstützt.

    - **Unterseite**höher stufen: verringern Sie den Einzug, und legen Sie die untergeordnete Seite auf der Ebene der vorherigen Seite in der Hierarchie ab.

    - **Unterseite erstellen**: Vergrößern Sie den Einzug, und machen Sie die Seite zu einer untergeordneten Seite der vorherigen Seite in der Hierarchie.

    - **Löschen**: Löscht die Seite.

        > [!div class=mx-imgBorder]
        > ![Webseiten verwalten (Optionen)](media/webpage-manage-options.png "Webseiten verwalten (Optionen)")  




