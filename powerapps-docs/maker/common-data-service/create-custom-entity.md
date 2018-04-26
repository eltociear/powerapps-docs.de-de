---
title: Tutorial zum Erstellen einer benutzerdefinierten Entität mit Komponenten mit PowerApps | Microsoft-Dokumentation
description: Tutorial mit ausführlichen Anleitungen zum Erstellen und Konfigurieren einer Entität zur Verwendung mit einer PowerApps-App
documentationcenter: na
author: Mattp123
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 03/21/2018
ms.author: matp
ms.openlocfilehash: 685a275f496c631e6c784bde4e8b2b245507388f
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="tutorial-create-a-custom-entity-that-has-components-in-powerapps"></a>Tutorial: Erstellen benutzerdefinierter Entitäten mit Komponenten in PowerApps

Mit [!INCLUDE [powerapps](../../includes/powerapps.md)] können Sie Ihre App an die Branche, Terminologie und die Geschäftsprozesse Ihres Unternehmens anpassen. Die App-Entwicklung mit [!INCLUDE [powerapps](../../includes/powerapps.md)] umfasst das Hinzufügen von vordefinierten Standardentitäten oder das Erstellen von benutzerdefinierten Entitäten. Mit einer Entität werden die Informationen definiert, die Sie in Form von Datensätzen nachverfolgen möchten. Diese enthalten üblicherweise Eigenschaften wie den Firmennamen, den Standort, die Produkte, die E-Mail-Adresse und die Telefonnummer. 

In diesem Tutorial erstellen Sie eine Entität und fügen dann Hauptkomponenten wie Felder, Beziehungen, Ansichten und Formulare hinzu oder passen diese an. In diesem Tutorial lernen Sie Folgendes:

- Eine benutzerdefinierte Entität erstellen
- Hinzufügen von benutzerdefinierten Feldern zu Ihrer Entität
- Hinzufügen einer verknüpften Entität
- Anpassen einer Ansicht 
- Anpassen eines Formulars

> [!IMPORTANT]
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

In diesem Tutorial wird das Beispielunternehmen Contoso verwendet, das Haustierpflegedienstleistungen für Hunde und Katzen anbietet. Contoso benötigt eine App für die Verwaltung von Kunden und Haustieren, die von den Mitarbeitern auf verschiedenen Geräten verwendet werden kann.

## <a name="prerequisites"></a>Voraussetzungen

Melden Sie sich bei [PowerApps](https://powerapps.microsoft.com/) an. Wenn Sie noch nicht über ein [!INCLUDE [powerapps](../../includes/powerapps.md)]-Konto verfügen, klicken Sie unter [powerapps.com](https://web.powerapps.com) auf **Steigen Sie kostenlos ein**.

## <a name="create-a-custom-entity"></a>Eine benutzerdefinierte Entität erstellen

1. Klicken Sie im linken Navigationsbereich unter **Common Data Service** auf **Entitäten** > **Neue Entität**.
    ![Neue Entität](media/create-custom-entity/create-new-entity.png)
2. Geben Sie im rechten Bereich folgende Werte ein, und klicken Sie dann auf **Weiter**.
  - **Anzeigename:** *Haustier* 
  - **Beschreibung:** *Benutzerdefinierte Entität zum Nachverfolgen von Haustierdienstleistungen*
3. Klicken Sie auf **Entität speichern**.

## <a name="add-and-customize-fields"></a>Hinzufügen und Anpassen von Feldern

1. Klicken Sie auf der Registerkarte **Felder** auf das Feld **Primärer Name**.
2. Nehmen Sie im rechten Bereich folgende Änderungen am Feld **Primärer Name** vor: 
  - Ändern Sie den **Anzeigenamen** von **Primärer Name** in *Name des Haustiers*.
  - Aktivieren Sie das Kontrollkästchen **Durchsuchbar**.

    ![Primäres Feld ändern](media/create-custom-entity/primary-field.png)
3. Wählen Sie **Fertig** aus.
4. Klicken Sie in der Symbolleiste des Entitäts-Designers auf das Feld **Hinzufügen**. Geben Sie im Bereich **Feldeingenschaften** folgende Werte und Optionen ein, oder wählen Sie diese aus.
  - **Anzeigename:** *Tierart*
  - **Datentyp:** *Optionssatz*
  - **Optionssatz:** *Neu*
5. Erstellen des Optionssatzes

  a. Klicken Sie auf **Neues Element hinzufügen**. 
  
  b. Ersetzen Sie **Neue Option** mit *Hund*. 
   
  c. Klicken Sie auf **Neues Element hinzufügen**. 
    
  d.  Ersetzen Sie **Neue Option** mit *Katze*. 
    
  e. Wählen Sie **Speichern**. 

  ![Neuer Optionssatz](media/create-custom-entity/optionset-add-items.png)

6. Aktivieren Sie das Kontrollkästchen **Durchsuchbar**, und klicken Sie dann auf **Fertig**.

7. Klicken Sie in der Symbolleiste des Entitäts-Designers auf **Feld hinzufügen**. Geben Sie im Bereich **Feldeigenschaften** folgende Werte ein, oder wählen Sie diese aus, und klicken Sie dann auf **Fertig**.
  - **Anzeigename:** *Rasse*
  - **Datentyp:** *Text*
  - **Durchsuchbar:** *Ja*

8. Klicken Sie in der Symbolleiste des Entitäts-Designers auf **Feld hinzufügen**. 

9. Geben Sie im Bereich **Feldeigenschaften** folgende Werte ein, oder wählen Sie diese aus, und klicken Sie dann auf **Fertig**. 
  - **Anzeigename:** *Termin*
  - **Datentyp:** *Datum und Uhrzeit*

10. Klicken Sie auf **Entität speichern**.

## <a name="add-a-relationship"></a>Hinzufügen einer Beziehung

1. Klicken Sie auf die Registerkarte **Beziehungen**, und klicken Sie in der Symbolleiste des Entitäts-Designers auf **Beziehung hinzufügen**. 
2. Wählen Sie aus der Liste **Verknüpfte Entität** im rechten Bereich **Konto** aus, und klicken Sie dann auf **Fertig**.
3. Klicken Sie auf **Entität speichern**.

Beachten Sie, dass beim Hinzufügen einer Beziehung ein Feld mit dem Datentyp **Lookup** (Suche) automatisch zur Liste der Felder auf der Registerkarte **Felder** hinzugefügt wird. ![Nachschlagefeld des Kontos](media/create-custom-entity/account-lookup-field.png)

## <a name="customize-a-view"></a>Anpassen einer Ansicht

1. Klicken Sie auf die Registerkarte **Ansichten**, und klicken Sie dann auf die Ansicht **Active Pets** (Aktive Haustiere).
2. Klicken Sie im Ansicht-Designer auf **Spalten hinzufügen**, wählen Sie folgende Spalten aus, und klicken Sie dann auf **OK**.
  - Konto
  - Termin 
  - Rasse 
  - Tierart
3. Klicken Sie auf die Spalte **Erstellt am** > **Entfernen**, und klicken Sie dann auf **OK**, um die Entfernung der Spalte zu bestätigen.
4. Wählen Sie die Spalte aus, die Sie verschieben möchten, und verwenden Sie die Pfeile nach links und nach rechts, bis Ihre Ansicht folgendermaßen aussieht.
    ![Ansicht „Aktive Haustiere“](media/create-custom-entity/active-pets-view.png)
5. Klicken Sie auf der Symbolleiste des Ansicht-Designers auf **Speichern und schließen**.  
6. Klicken Sie auf **Entität speichern**.

## <a name="model-driven-apps-only-customize-the-main-form"></a>Nur für modellgesteuerte Apps: Anpassen des Hauptformulars

Überspringen Sie diesen Schritt, wenn Sie die Entität „Haustier“ nur in einer Canvas-App verwenden möchten. 

1. Klicken Sie im linken Navigationsbereich von [!INCLUDE [powerapps](../../includes/powerapps.md)] auf **Modellgesteuert**.
2. Klicken Sie im linken Navigationsbereich auf **Erweitert**.
3. Klicken Sie im linken Navigationsbereich des Fensters „Projektmappe“ auf **Entitäten**, erweitern Sie **Haustier**, und klicken Sie dann auf **Formulare**.
4. Klicken Sie neben dem Formulartyp **Main** (Hauptformular) auf **Informationen**, um den Formular-Editor zu öffnen.
    ![Hauptformular bearbeiten](media/create-custom-entity/main-form-edit.png)
5. Ziehen Sie im Formular-Editor die Felder **Tierart**, **Rasse**, **Termin** und **Konto**, die sich im Bereich „Feld-Explorer“ befinden, zum Abschnitt „Allgemein“ der Formularcanvas, und legen Sie diese dort ab, bis das Formular folgendermaßen aussieht.
    ![Felder für Hauptformular auswählen](media/create-custom-entity/main-form-edit2.png) 
6. Klicken Sie auf **Speichern und schließen**.
7. Klicken Sie im Fenster „Projektmappe“ auf **Publish All Customizations** (Alle Anpassungen veröffentlichen).
    ![Alle Anpassungen veröffentlichen](media/create-custom-entity/publish-all-customizations.png)

## <a name="add-the-custom-entity-to-an-app"></a>Hinzufügen der benutzerdefinierten Entität zu einer App

Ihre Entität ist nun bereit, zum Erstellen einer Canvas-App oder einer modellgesteuerten App verwendet zu werden. 

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Sie eine Entität erstellen, die zum Erstellen einer nützlichen App verwendet werden kann. Weitere Informationen zum Erstellen einer Canvas-App finden Sie unter [Create an app from scratch (Neuerstellen einer App von Grund auf)](../canvas-apps/get-started-create-from-blank.md).
