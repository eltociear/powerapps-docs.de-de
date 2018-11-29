---
title: Erstellen Sie Ihre erste Modell-angetriebene App von Beginn weg mit PowerApps | Microsoft Docs
description: 'Erfahren Sie, wie Sie eine einfache modellgetriebene App erstellen'
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 10/15/2018
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="build-your-first-model-driven-app-from-scratch"></a>Erstellen Sie Ihre erste Modell-angetriebene App neu
Modell-angetriebener App-Entwurf ist eine Komponenten-fokussierte Methode zur App-Entwicklung. In diesem Thema vereinfachen Sie, wie Sie eine Modell-angetriebene App erstellen, indem Sie eine der Standard-Informationsstrukturen verwenden, die in der PowerApps-Umgebung verfügbar ist.

> [!TIP]
> Um alles über das Erstellen von Modell-angetriebene Apps zu erfahren, beginnen Sie hier: [Modell-angetriebene App-Komponenten verstehen](model-driven-app-components.md). 

## <a name="sign-in-to-powerapps"></a>Bei PowerApps anmelden
Melden Sie sich bei [PowerApps](https://web.powerapps.com/) an. Wenn Sie noch kein [!INCLUDE [powerapps](../../includes/powerapps.md)] Konto haben, wählen Sie den Link **Kostenlos beginnen** aus. 

## <a name="create-your-model-driven-app"></a>Erstellen Sie Ihre modellgesteuerte Anwendung

1.  Wählen Sie die gewünschte Umgebung aus oder gehen Sie zu [PowerApps-Administratorcenter](https://admin.powerapps.com/), um eine neue zu erstellen.

  > [!IMPORTANT]
  > "Wenn der **Modell-angetriebe** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).   

2. Klicken Sie auf der **Start**-Seite die Option **Ohne Vorlage erstellen** für eine modellgesteuerte App aus.
![Start-from-blank_model](media/build-first-model-driven-app/start-from-blank-model-driven.png)

3.  Klicken Sie auf der Seite **Eine neue App erstellen "** und geben Sie die folgenden Details ein und wählen dann **Fertig** aus: 
  - **Name**: Geben Sie einen Namen für die App ein, wie *Myfirstapp*. 
  - **Beschreibung**: Geben Sie eine kurze Beschreibung ein, um was es bei der App geht, wie *Dies ist meine erste App*.
Informationen zu den zusätzlichen App-Eigenschaften finden Sie unter [Eine App erstellen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app#create-an-app)
 
    ![Neue App erstellen](media/build-first-model-driven-app/create-new-app.png)

## <a name="add-components-to-your-app"></a>Fügen Sie der App zusätzliche Komponenten hinzu.
Im Anwendungs-Designer fügen Sie Komponenten der App hinzu.
1.  Wählen Sie den Pfeil **Siteübersichts-Designer öffnen**, um den Siteübersichtsdesigner zu öffnen. 

    ![Erstellen von neuen Sitemaps](media/build-first-model-driven-app/new-sitemap.png)

2.  Klicken Sie im Siteübersichtsdesigner im rechten Bereich **Neuer Unterbereich** wählen Sie die **Eigenschaften**, und dann die folgenden Eigenschaften aus.
  - **Typ**. Entität
  - **Entität**: Firma

    ![So fügen Sie Komponenten der Siteübersicht hinzu](media/build-first-model-driven-app/sitemap.png)

3.  Klicken Sie auf **Speichern und schließen**.
4.  Auf dem App-Designer Canvas wählen Sie **Formulare** und anschließend im rechten Bereich **Hauptformulare** und wählen in der Gruppe **Firma**.

    ![Kontohauptformular](media/build-first-model-driven-app/main-form.png)

5.  Auf dem App-Designer-Canvas wählen Sie die Option **Ansichten** und dann **Aktive Firmen**, **Alle Firmen** und **Meine aktiven Firmen** Ansicht aus.

    ![Anzeigen von Konten](media/build-first-model-driven-app/views.png)

6. Auf der App-Designer-Canvas wählen Sie die Option **Diagramme** und wählen dann das Diagramm aus **Firmen nach Branche**.
7. Wählen Sie auf der Symbolleiste des App-Designers **Speichern** aus.

    ![App-Designer Systemleiste speichern](media/build-first-model-driven-app/app-designer-toolbar.png)
 
<!-- ##  Validate your app
This step checks for component dependencies that are required for the app to work, but haven't yet been added to the app. 

1. On the app designer canvas, select the component that indicates a dependency, such as the **Forms** component. Then, on the right-pane select the **Required** tab, expand **Entity Dependencies** and then select all required dependencies. 

    ![Add dependencies](media/build-first-model-driven-app/resolve-dependencies.png)

2. Select **Add Dependencies**.
3. On the app designer toolbar, select **Save**.  -->

## <a name="publish-your-app"></a>Veröffentlichen der App.
Wählen Sie auf der Symbolleiste des App-Designers **Veröffentlichen** aus.

Nachdem die App veröffentlicht wurde, ist Sie bereit, dass Sie sie ausführen oder teilen können.

![Einfache Firmaenentitäts-App](media/build-first-model-driven-app/accounts-quickstart-app.png)

## <a name="next-steps"></a>Nächste Schritte
In diesem Thema werden Modell-angetriebene einfache Apps erstellt. 
- Zur Anzeige der App beim Ausführen, gehen sie zu [Modell-angetriebene App auf einem mobilen Gerät ausführen](../../user/run-app-client-model-driven.md).
- Informationen zum teilen Ihrer App finden Sie unter [Eine Modell-angetriebenen App freigeben](share-model-driven-app.md).
- Um alles über das Erstellen von Modell-angetriebene Apps zu erfahren, beginnen Sie hier: [Modell-angetriebene App-Komponenten verstehen](model-driven-app-components.md).
