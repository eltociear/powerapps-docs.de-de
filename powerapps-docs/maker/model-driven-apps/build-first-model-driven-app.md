---
title: Neuerstellen Ihrer ersten modellgesteuerten App mit PowerApps | Microsoft-Dokumentation
description: Informationen zur Erstellung einer einfachen modellgesteuerten App
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 04/18/2018
ms.author: matp
ms.openlocfilehash: 36e189c75ef4c53ac97805fae38094e25c2c4804
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39663945"
---
# <a name="build-your-first-model-driven-app-from-scratch"></a>Neuerstellen Ihrer ersten modellgesteuerten App
Das Design einer modellgesteuerten App ist ein auf Komponenten bezogener Ansatz zum Entwickeln von Apps. In diesem Thema erfahren Sie, wie Sie eine modellgesteuerte App mithilfe einer der Standardentitäten erstellen, die in Ihrer PowerApps-Umgebung zur Verfügung stehen.

> [!TIP]
> Informationen zum Erstellen von modellgesteuerten Apps finden Sie unter [Grundlegendes zu Komponenten von modellgesteuerten Apps](model-driven-app-components.md). 

## <a name="sign-in-to-powerapps"></a>Anmelden bei PowerApps
Melden Sie sich bei [PowerApps](https://web.powerapps.com/) an. Wenn Sie noch nicht über ein [!INCLUDE [powerapps](../../includes/powerapps.md)]-Konto verfügen, klicken Sie auf **Steigen Sie kostenlos ein**. 

## <a name="create-your-model-driven-app"></a>Erstellen der modellgesteuerten App

1.  Wählen Sie die gewünschte Umgebung aus, oder wechseln Sie ins [PowerApps Admin Center](https://admin.powerapps.com/), um eine neue zu erstellen.
2.  Klicken Sie im linken Navigationsbereich auf **Model-driven** (Modellgesteuert). 

    ![Modellgesteuert](media/build-first-model-driven-app/choose-design-mode.png)

  > [!IMPORTANT]
  > Wenn der Designmodus **Modellgesteuert** nicht verfügbar ist, müssen Sie ggf. eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).   

3. Klicken Sie im linken Bereich auf **Apps** und dann auf **App erstellen**.

4.  Geben Sie auf der Seite **Neue App erstellen** die folgenden Details ein, und klicken Sie dann auf **Done** (Fertig): 
  - **Name**: Geben Sie einen Namen für die App ein, z.B. *Myfirstapp*. 
  - **Description** (Beschreibung): Erläutern Sie in einer kurzen Beschreibung, was es mit der App auf sich hat oder welchen Zweck sie erfüllt, z.B. *Das ist meine erste App*.
Informationen zu zusätzlichen App-Eigenschaften finden Sie unter [Erstellen einer App](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app#create-an-app).
 
    ![Neue App erstellen](media/build-first-model-driven-app/create-new-app.png)

## <a name="add-components-to-your-app"></a>Hinzufügen von Komponenten zur App
Über den App-Designer können Sie Ihrer App Komponenten hinzufügen.
1.  Klicken Sie auf den Pfeil **Open the Site Map Designer** (Designer für die Siteübersicht öffnen), um den Designer für die Siteübersicht zu öffnen. 

    ![Neue Siteübersicht erstellen](media/build-first-model-driven-app/new-sitemap.png)

2.  Klicken Sie im Designer für die Siteübersicht auf **New Subarea** (Neuer Unterbereich) und im rechten Bereich auf die Registerkarte **Properties** (Eigenschaften), und wählen Sie dann die folgenden Eigenschaften aus.
  - **Type** (Typ): Die Entität
  - **Entity** (Entität): Das Konto

    ![Siteübersicht Komponenten hinzufügen](media/build-first-model-driven-app/sitemap.png)

3.  Klicken Sie auf **Save And Close** (Speichern und schließen).
4.  Klicken Sie auf dem Zeichenbereich des App-Designers auf **Forms** (Formulare), und wählen Sie rechts unter der Gruppe **Main Forms** (Hauptformulare) das Formular **Account** (Konto) aus.

    ![Hauptformular „Konto“](media/build-first-model-driven-app/main-form.png)

5.  Klicken Sie im Zeichenbereich des App-Designers auf **View** (Ansicht), und wählen Sie dann die Ansichten **Aktive Firmen**, **Alle Konten** und **Meine aktiven Firmen** aus.

    ![Kontoansichten](media/build-first-model-driven-app/views.png)

6. Klicken Sie im Zeichenbereich des App-Designers auf **Charts** (Diagramme), und wählen Sie dann das Diagramm **Firmen nach Branche** aus.
7. Klicken Sie auf der Symbolleiste des Ansicht-Designers auf **Speichern**.

    ![„Speichern“ auf der Symbolleiste des App-Designers](media/build-first-model-driven-app/app-designer-toolbar.png)
 
<!-- ##  Validate your app
This step checks for component dependencies that are required for the app to work, but haven't yet been added to the app. 

1. On the app designer canvas, select the component that indicates a dependency, such as the **Forms** component. Then, on the right-pane select the **Required** tab, expand **Entity Dependencies** and then select all required dependencies. 

    ![Add dependencies](media/build-first-model-driven-app/resolve-dependencies.png)

2. Select **Add Dependencies**.
3. On the app designer toolbar, select **Save**.  -->

## <a name="publish-your-app"></a>Veröffentlichen der App
Klicken Sie auf der Symbolleiste des Ansicht-Designers auf **Veröffentlichen**.

Anschließend können Sie die App ausführen oder für andere Personen freigeben.

![Entitäts-App mit einfachem Konto](media/build-first-model-driven-app/accounts-quickstart-app.png)

## <a name="next-steps"></a>Nächste Schritte
In diesem Thema haben Sie eine einfache modellgesteuerte App erstellt. 
- Weitere Informationen zum Ausführen Ihrer App finden Sie unter [Ausführen einer modellgesteuerten App auf einem mobilen Gerät](../../user/run-app-client-model-driven.md).
- Informationen zum Freigeben einer App finden Sie unter [Freigeben einer modellgesteuerten App](share-model-driven-app.md).
- Zum Einstieg finden Sie Informationen zum Erstellen von modellgesteuerten Apps unter [Grundlegendes zu Komponenten von modellgesteuerten Apps](model-driven-app-components.md).
