---
title: Erstellen einer benutzerdefinierten Entität, die Komponenten Power Apps enthält | Microsoft-Dokumentation
description: Thema mit schrittweisen Anweisungen zum Erstellen und Konfigurieren einer Entität zur Verwendung mit einer Power Apps-App.
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: tutorial
ms.date: 01/23/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 864bc9c8cfad92bac661db0b12b47d880cc86edf
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883790"
---
# <a name="create-a-custom-entity-that-has-components-in-power-apps"></a>Erstellen Sie eine benutzerdefinierte Entität mit Komponenten in Power Apps

Mit Power Apps können Sie Ihre App genauer an die Branche, Benennungsstandards und besonderen Geschäftsprozesse Ihrer Organisation anpassen. Power Apps-App-Entwicklung umfasst das Hinzufügen von Standard "vordefinierten Entitäten" oder dem Erstellen benutzerdefinierter Entitäten. Eine Entität definiert die Informationen, die Sie in Form von Datensätzen nachverfolgen möchten, die normalerweise Eigenschaften wie Firmenname, Standort, Produkte, E-Mail und Telefon umfassen. 

In diesem Thema erstellen Sie eine Entität und fügen Schlüsselkomponenten wie Felder, Beziehungen, Ansichten und Formularen hinzu und bearbeiten sie. Informationen zu:

- Erstellen einer benutzerdefinierten Entität.
- Fügen Sie benutzerdefinierte Felder der Entität hinzu
- Eine Entitätsbeziehung hinzufügen
- Anpassen von Ansichten 
- Formular anpassen

Dieses Thema folgt der Firma Contoso, die ein Haustierpflegeunternehmen hat, das Hunde und Katzen betreut. Contoso erfordert eine App für Client- und Haustiernachverfolgung von Mitarbeitern, die mit einer Reihe unterschiedlicher Geräte verwendet werden kann.

## <a name="prerequisites"></a>Voraussetzungen

Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an. Wenn Sie noch kein Power Apps-Konto haben, wählen Sie den Link **Kostenlos beginnen** aus [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="create-a-custom-entity"></a>Erstellen einer benutzerdefinierten Entität.

1. Klicken Sie im linken Navigationsbereich auf **Daten** erweitern und wählen Sie **Entitäten** und wählen Sie dann im Hauptbereich **Neue Entität** aus.
    > [!div class="mx-imgBorder"] 
    > ![Neue Entität](media/create-custom-entity/create-new-entity.png)
2. Geben Sie im rechten Bereich die folgenden Werte ein und wählen Sie **weiter**.
  - **Anzeigename**: *Haustier* 
  - **Beschreibung**: *Benutzerdefinierte Entität, um Haustierdienstleistungen nachzuverfolgen*
3. **Entität speichern** auswählen.

## <a name="add-and-customize-fields"></a>Hinzufügen und Anpassen von Feldern
 
1. In der Liste der Entitäten wählen Sie die Entität **Haustier** aus, die im vorherigen Abschnitt erstellt wurde.
2. Auf der Registerkarte **Felder** Klicken Sie auf das Feld **Haustier**.
3. Nehmen Sie im rechten Bereich die folgenden Änderungen am Feld **Anzeigename** vor: 
  - Ändern Sie **Anzeigename** in **Haustier** *Kosename*
  - Wählen Sie **Suchen**.  
  
    > [!div class="mx-imgBorder"] 
    > ![Primäre Feldeinstellungen ändern](media/create-custom-entity/primary-field.png)
3. **Fertig** auswählen
4. Klicken Sie auf der Registerkarte **Felder** auf der Entitätsdesignersymbolleiste und wählen Sie die Option aus **Feld hinzufügen** Klicken Sie auf den Bereich **Feldeigenschaften** und geben Sie ein oder wählen Sie die folgenden Werte und Optionen.
  - **Anzeigename**. *Spezies*
  - **Datentyp**. *Optionssatz*
  - **Optionssatz**. *Neuer Optionssatz*
5. Einen Optionssatz erstellen

  a. Wählen Sie **Neue Einheit hinzufügen**. 
  
  b. Ersetzen Sie **Neue Option** mit *Hund*. 
   
  c. Wählen Sie **Neue Einheit hinzufügen**. 
    
  d.  Ersetzen Sie **Neue Option** mit *Katze*. 
    
  e. Wählen Sie **Speichern** aus. 

  > [!div class="mx-imgBorder"] 
  > ![Neuer Optionssatz](media/create-custom-entity/optionset-add-items.png)

6. Wählen Sie **Durchsuchbar** und dann **Fertig** aus.

7. Klicken Sie auf der Entitätsdesignersymbolleiste und wählen Sie die Option **Feld hinzufügen**. Klicken Sie auf den Bereich **Feldeigenschaften** und geben Sie ein oder wählen Sie **Fertig**.
  - **Anzeigename**. *Zucht*
  - **Datentyp**. *Text*
  - **Durchsuchbar**. *Ja*

8. Klicken Sie auf der Entitätsdesignersymbolleiste und wählen Sie die Option **Feld hinzufügen**. 

9. Klicken Sie auf den Bereich **Feldeigenschaften** und geben Sie ein oder wählen Sie **Fertig**. 
  - **Anzeigename**. *Termindatum*
  - **Datentyp**. *Datum und Uhrzeit*

10. **Entität speichern** auswählen.

## <a name="add-a-relationship"></a>Eine Beziehung hinzufügen

1. Wählen Sie die Registerkarte **Beziehungen**, klicken Sie auf der Entitätsdesignersymbolleiste auf **Beziehung hinzufügen** und wählen Sie dann aus **viele-zu-einer**. 
2. Wählen Sie im rechten Bereich in der Liste **Verknüpft** die Option **Firma** aus.
3. **Fertig** auswählen
4. **Entität speichern** auswählen.

  Beachten Sie, dass, wenn Sie eine n: 1-Beziehung hinzufügen, ein Feld **Firma** den Datentyp automatisch **Suche** in der Liste der Felder auf der Registerkarte hinzugefügt wird. **Felder**
  > [!div class="mx-imgBorder"]
  > ![Suchfeld für die Kontensuche](media/create-custom-entity/account-lookup-field.png)

## <a name="customize-a-view"></a>Anpassen von Ansichten

1. Wählen Sie die Registerkarte **Ansichten**, und wählen Sie dann **Aktive Haustiere** aus der Ansicht aus. Wenn Sie die Ansicht **Aktive Haustiere** nicht sehen, wählen Sie **Filter entfernen** aus.
2. Klicken Sie im Ansicht-Designer und wählen Sie **Spalten hinzufügen** aus, wählen Sie die folgenden Spalten aus, und wählen Sie dann **OK** aus.
  - Firma
  - Termindatum 
  - Zucht 
  - Spezies
3. Wählen Sie die Spalte **Erstellt am**, wählen Sie **Entfernen** aus, und wählen Sie dann **OK**, um das Spaltenentfernen zu bestätigen.
4. Um die Spalten zu positionieren, wählen Sie die Spalte aus, die < - und - > Pfeilschaltflächen und verschieben Sie diese, bis die Ansicht wie folgt erscheint.
    > [!div class="mx-imgBorder"] 
    > ![Aktive Haustieransicht](media/create-custom-entity/active-pets-view.png)
5. Wählen Sie auf der Symbolleiste des App-Designers **Speichern und beenden** aus.  

## <a name="model-driven-apps-only-customize-the-main-form"></a>Nur Modell-angetriebene Apps: Anpassen des Hauptformulars

Überspringen Sie diesen Schritt, wenn Sie nur die Haustierentität in einer Canvas-App verwenden möchten. 

1. Klicken Sie im linken Navigationsbereich auf **Daten** erweitern und wählen Sie **Entitäten** und wählen Sie dann im Hauptbereich **Haustier** aus.
2. Wählen Sie die Registerkarte **Formulare**, und wählen Sie dann **Informationen** neben dem Formulartyp **Hauptformular** aus, um den Formular-Editor zu öffnen.
    > [!div class="mx-imgBorder"] 
    > ![Hauptformular bearbeiten](media/create-custom-entity/main-form-edit.png)
3. Im Formulareditor Ziehen Sie die Felder **Spezies**, **Zucht**, **Termindatum** und **Firma** im Explorer-Bereich in den Abschnitt Allgemein im Formularcanvas bis das Formular wie dieses aussieht.
    > [!div class="mx-imgBorder"] 
    > ![Wählen Sie die Felder vom Hauptformular](media/create-custom-entity/main-form-edit2.png) 
4. Wählen Sie **Speichern** aus.
5. Wählen Sie **Veröffentlichen** aus.
6. Klicken Sie auf **Speichern und schließen**, um den Formular-Editor zu schließen.

## <a name="add-the-custom-entity-to-an-app"></a>Fügen Sie die benutzerdefinierte Entität einer App hinzu

Ihre Entität ist nun bereit, um entweder eine Canvas oder Modell-angetriebene App zu erstellen. 

## <a name="next-steps"></a>Nächste Schritte

In diesem Thema erfuhren Sie, wie Sie eine Entität erstellen, die verwendet werden kann, um eine nützliche App zu erstellen. 
- Sie können erfahren, wie eine Modell-angetriebene App erstellt wird[Erstellen Sie Ihre erste Modell-angetriebene App](../model-driven-apps/build-first-model-driven-app.md).
- Hier erfahren Sie, wie Sie eine Canvas-App erstellen, vgl. [Erstellen Sie eine App neu](../canvas-apps/get-started-create-from-blank.md).
