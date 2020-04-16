---
title: Erstellen Sie Ihre erste modellgesteuerte App komplett neu mit Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine einfache modellgetriebene App erstellen
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 02/05/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4c404c8aab419fa4b0445a392d7440c2ab3f099b
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136142"
---
# <a name="build-your-first-model-driven-app-from-scratch"></a>Erstellen Sie Ihre erste Modell-angetriebene App neu
Modell-angetriebener App-Entwurf ist eine Komponenten-fokussierte Methode zur App-Entwicklung. In diesem Thema vereinfachen Sie, wie Sie eine modellgesteuerte App erstellen, indem Sie eine der Standardentitäten verwenden, die in Ihrer Power Apps-Umgebung verfügbar ist.

> [!TIP]
> Um alles über das Erstellen von Modell-angetriebene Apps zu erfahren, beginnen Sie hier: [Modell-angetriebene App-Komponenten verstehen](model-driven-app-components.md). 

## <a name="sign-in-to-power-apps"></a>Bei Power Apps anmelden
Melden Sie sich bei [Power Apps](https://make.powerapps.com/) an. Wenn Sie noch kein [!INCLUDE [powerapps](../../includes/powerapps.md)]-Konto haben, wählen Sie den Link **Kostenlos beginnen** aus. 

## <a name="create-your-model-driven-app"></a>Erstellen Sie Ihre modellgesteuerte Anwendung

1.    Wählen Sie die gewünschte Umgebung aus oder gehen Sie zu [Power Apps-Administratorcenter](https://admin.powerapps.com/), um eine neue zu erstellen.

2.  Wählen Sie auf der **Startseite** die Option **Modellgetriebene App aus dem Leerfeld**.

    > [!div class="mx-imgBorder"] 
    > <img src="media/build-first-model-driven-app/start-from-blank-model-driven.png" alt="Start from blank model" height="429" width="673">

3.  Wählen Sie **Erstellen** aus.

3.    Geben Sie auf der Seite **Eine neue App erstellen** die folgenden Details ein und wählen Sie dann **Fertig** aus: 
  - **Name**: Geben Sie einen Namen für die App ein, z. B. *Meine erste App*. 
  - **Eindeutiger Name**: Standardmäßig verwendet der eindeutige Name den Namen, den Sie im Feld **Name** ohne Leerzeichen angegeben haben und der durch das Verlegerpräfix und einen Unterstrich (_) eingeleitet wird. Zum Beispiel *crecf_Myfirstapp*. Weitere Informationen [Lösungsherausgeberpräfix ändern](../common-data-service/change-solution-publisher-prefix.md)
  - **Beschreibung**: Geben Sie eine kurze Beschreibung ein, um was es bei der App geht, wie *Dies ist meine erste App*.
Informationen zu den zusätzlichen App-Eigenschaften finden Sie unter [Eine App erstellen](create-edit-app.md#create-an-app)

  > [!div class="mx-imgBorder"] 
  > ![Erstellen einer neuen App](media/create-new-app.png "Eine neue App erstellen")

## <a name="add-components-to-your-app"></a>Fügen Sie der App zusätzliche Komponenten hinzu.
Im Anwendungs-Designer fügen Sie Komponenten der App hinzu.
1.    Wählen Sie die Bearbeitungsschaltfläche **Siteübersichts-Designer öffnen** aus, um den Siteübersichts-Designer zu öffnen.

      > [!div class="mx-imgBorder"] 
      > ![Erstellen von neuen Sitemaps](media/build-first-model-driven-app/new-sitemap.png "Siteübersichts-Designer")

2.    Klicken Sie im Siteübersichtsdesigner im rechten Bereich **Neuer Unterbereich** wählen Sie die **Eigenschaften**, und dann die folgenden Eigenschaften aus.
  - **Typ**. Entität
  - **Entität**: Firma

    > [!div class="mx-imgBorder"] 
    > ![So fügen Sie Komponenten der Siteübersicht hinzu](media/build-first-model-driven-app/sitemap.png "Neuer Unterbereich")

3.    Klicken Sie auf **Speichern und schließen**.
4.    Auf dem App-Designer Canvas wählen Sie **Formulare** und anschließend im rechten Bereich **Hauptformulare** und wählen in der Gruppe **Firma**.

      > [!div class="mx-imgBorder"] 
      > ![Kontohauptformular](media/build-first-model-driven-app/main-form.png "App-Formulare")

5.    Auf dem App-Designer-Canvas wählen Sie die Option **Ansichten** und dann **Aktive Firmen**, **Alle Firmen** und **Meine aktiven Firmen** Ansicht aus.<!-- All checkbox seems to be selected by default -->

      > [!div class="mx-imgBorder"] 
      > ![Anzeigen von Konten](media/build-first-model-driven-app/views.png "App-Ansichten")

6. Auf der App-Designer-Canvas wählen Sie die Option **Diagramme** und wählen dann das Diagramm aus **Firmen nach Branche**.
7. Wählen Sie auf der Symbolleiste des App-Designers **Speichern** aus.

      > [!div class="mx-imgBorder"] 
      > ![App-Designer Systemleiste speichern](media/build-first-model-driven-app/app-designer-toolbar.png "App speichern")
 
<!-- ##  Validate your app
This step checks for component dependencies that are required for the app to work, but haven't yet been added to the app. 

1. On the app designer canvas, select the component that indicates a dependency, such as the **Forms** component. Then, on the right-pane select the **Required** tab, expand **Entity Dependencies** and then select all required dependencies. 

    ![Add dependencies](media/build-first-model-driven-app/resolve-dependencies.png)

2. Select **Add Dependencies**.
3. On the app designer toolbar, select **Save**.  -->

## <a name="publish-your-app"></a>Veröffentlichen der App.
Wählen Sie auf der Symbolleiste des App-Designers **Veröffentlichen** aus.

Nachdem die App veröffentlicht wurde, ist Sie bereit, dass Sie sie ausführen oder teilen können.

  > [!div class="mx-imgBorder"] 
  > ![Einfache Firmaenentitäts-App](media/build-first-model-driven-app/accounts-quickstart-app.png "App ausführen")

## <a name="next-steps"></a>Nächste Schritte
In diesem Thema werden Modell-angetriebene einfache Apps erstellt. 
- Zur Anzeige der App beim Ausführen, gehen sie zu [Modell-angetriebene App auf einem mobilen Gerät ausführen](../../user/run-app-client-model-driven.md).
- Informationen zum teilen Ihrer App finden Sie unter [Eine Modell-angetriebenen App freigeben](share-model-driven-app.md).
- Um alles über das Erstellen von Modell-angetriebene Apps zu erfahren, beginnen Sie hier: [Modell-angetriebene App-Komponenten verstehen](model-driven-app-components.md).
