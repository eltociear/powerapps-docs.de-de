---
title: Erstellen eines Kartenformulars mit PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie Sie Kartenformulare in PowerApps erstellen und verwenden'
keywords: ''
ms.date: 03/05/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Mattp123
ms.assetid: be93b9d7-f1c2-4ee7-8d7c-0f5c34dfa5f7
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-a-card-form"></a>Erstellen eines Kartenformulars
Kartenformulare werden in Ansichten für Apps der einheitlichen Oberfläche verwendet. Kartenformulare sind so konzipiert, dass sie Informationen kompakt anzeigen, sodass sie für Mobilgeräte geeignet sind. Beispielsweise definiert das Standardkartenformular für die Ansicht "Meine aktiven Firmen" die Informationen, die für jeden Firmendatensatz angezeigt werden. 

> [!div class="mx-imgBorder"] 
> ![](media/account-cardform-for-myactiveaccounts-view.png "Firmenkartenformular für die Ansicht \"Meine aktiven Firmen\"")

Obwohl Kartenformulare auf die gleiche Weise wie andere Formulartypen erstellt und bearbeitet werden können, werden Kartenformulare den Apps anders hinzugefügt. Statt ein Formular als App-Komponente hinzuzufügen, werden benutzerdefinierte Kartenformulare den Ansichten mit dem Steuerelement **Schreibgeschütztes Raster** hinzugefügt. 

## <a name="create-a-card-form"></a>Erstellen eines Kartenformulars
1. Um ein Kartenformular zu erstellen, melden Sie sich in [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an. 
2. Erweitern Sie **Daten**, wählen Sie **Entitäten** und dann die gewünschte Entität aus und wählen Sie die dann die Registerkarte **Formulare** aus.
3. Wählen Sie auf der Symbolleiste **Formular hinzufügen** aus und klicken Sie auf **Kartenformular**. Sie können auch einen vorhandenen **Formulartyp** öffnen, bei dem es sich um ein Formular **Karte** handelt, um es zu bearbeiten.
4. Fügen Sie die gewünschten Felder hinzu. Wir empfehlen Ihnen, die Anzahl der Felder zu beschränken, damit das Formular auf kleinen Bildschirmen gut angezeigt wird. 
5. Wählen Sie **Speichern** und dann **Veröffentlichen** aus. 

## <a name="add-a-card-form-to-a-view"></a>Hinzufügen eines Kartenformulars zu einer Ansicht 
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.
2. Erweitern Sie **Daten**, wählen Sie gewünschten Entitäten und dann die Registerkarte **Ansichten** aus.
3. Wählen Sie die gewünschten Ansicht aus, wählen Sie auf der Symbolleiste **In klassischen Modus wechseln** aus.
4. Wählen Sie **Benutzerdefinierte Steuerelemente** im Bereich **Allgemeine Aufgaben** aus.
5. Wählen Sie **Steuerelement hinzufügen** und in der Liste der Steuerelemente **Schreibgeschütztes Raster** und dann **Hinzufügen** aus.

   > [!NOTE]
   > Es gibt zwei Steuerelemente für schreibgeschützte Raster. Das standardmäßige schreibgeschützte Rastersteuerelement mit dem Namen **Schreibgeschütztes Raster (Standard)** unterstützt keine benutzerdefinierten Formulare. 

6. Auf der Eigenschaftenseite **Schreibgeschütztes Raster** konfigurieren Sie die folgenden Eigenschaften und wählen dann **OK** aus. 
   - **Kartenformular**. Wählen Sie das Stiftssymbol ![Bearbeiten der Steuerelementeigenschaften](media/ccf-pencil-icon.png) und dann das Kartenformular aus, das Sie in der Ansicht anzeigen möchten. Standardmäßig ist die primäre Entität, die der Ansicht zugeordnet ist, bereits ausgewählt, das können Sie jedoch ändern. 
   - **Dynamisches Umbruchsverhalten** Wenn Sie ändern möchten, ob das Kartenformular bei Größenänderung angezeigt wird, wählen Sie das Stiftssymbol ![Bearbeiten der Steuerelementeigenschaften](media/ccf-pencil-icon.png) aus. Weitere Informationen: [Zulassen, dass das Raster in die Liste in zurückfließt](specify-properties-for-unified-interface-apps.md#allow-grid-to-reflow-into-list)  
   - Wählen Sie die Client-Typen **Web**, **Telefon** oder **Tablet** aus, wo das Steuerelement **Schreibgeschütztes Raster** angezeigt werden soll.

     ![Schreibgeschütztes Raster für Kartenformular](media/read-only-grid-for-cardform.png)

7. Klicken Sie auf **OK**, um die Eigenschaftenseite **Benutzerdefinierte Steuerelemente** zu schließen. 
8. Wählen Sie auf der Symbolleiste des klassischen Ansicht-Designers **Speichern und beenden** aus. 

## <a name="see-also"></a>Siehe auch
[Verwenden Sie benutzerdefinierte Steuerelemente für modellgesteuerte App-Datenvisualisierungen](use-custom-controls-data-visualizations.md)



