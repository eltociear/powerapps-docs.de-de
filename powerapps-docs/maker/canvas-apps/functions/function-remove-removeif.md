---
title: Funktionen „Remove“ und „RemoveIf“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen "Remove" und "removeif" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/02/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bddce14842d111757859b836c0137b35111805d1
ms.sourcegitcommit: 49b69129262a9b530e69508e84c3822b742066df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759851"
ms.PowerAppsDecimalTransform: true
---
# <a name="remove-and-removeif-functions-in-power-apps"></a>Funktionen "Remove" und "removeif" in powerapps
Entfernt [Datensätze](../working-with-tables.md#records) aus einer [Datenquelle](../working-with-data-sources.md).

## <a name="description"></a>Beschreibung
### <a name="remove-function"></a>Remove-Funktion
Verwenden Sie die **Remove**-Funktion, um einen bestimmten Datensatz oder bestimmte Datensätze aus einer Datenquelle zu entfernen.  

Für [Sammlungen](../working-with-data-sources.md#collections) muss der gesamte Datensatz übereinstimmen. Sie können das **All**-Argument verwenden, um alle Kopien eines Datensatzes zu entfernen; andernfalls wird nur eine Kopie des Datensatzes entfernt.

### <a name="removeif-function"></a>RemoveIf-Funktion
Verwenden Sie die **RemoveIf**-Funktion,um einen Datensatz oder Datensätze auf Grundlage einer Bedingung oder eine Reihe von Bedingungen zu entfernen. Jede Bedingung kann jede beliebige Formel sein, die **TRUE** oder **FALSE** ergibt, und die auf [Spalten](../working-with-tables.md#columns) der Datenquelle anhand des Namens verweisen kann. Jede Bedingung wird einzeln für jeden Datensatz ausgewertet, und der Eintrag wird entfernt, wenn alle Bedingungen als **TRUE** ausgewertet werden.

**Remove** und **RemoveIf** geben die geänderten Datenquelle als eine [Tabelle](../working-with-tables.md) zurück. Beide Funktionen können nur in [Verhaltensformeln](../working-with-formulas-in-depth.md) geändert werden.

Sie können auch die **[Clear](function-clear-collect-clearcollect.md)** Funktion verwenden, um alle Datensätze in einer Datenquelle zu entfernen.

### <a name="delegation"></a>Delegierung
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Syntax
**Remove**( *DataSource*; *Record1* [; *Record2*; ... ] [; **All** ] )

* *DataSource*: erforderlich. Die Datenquelle mit den Datensatz bzw. Datensätze, die Sie entfernen möchten.
* *Datensatz/Datensätze*: erforderlich. Der Datensatz oder die Datensätze, die entfernt werden sollen.
* **All**: Optional. In einer Sammlung wird möglicherweise der gleiche Datensatz mehr als einmal angezeigt.  Sie können das **All**-Argument hinzufügen, um alle Kopien des Datensatzes zu entfernen.

**Remove**( *DataSource*; *Table* [; **All** ] )

* *DataSource*: erforderlich. Die Datenquelle, die die Datensätze enthält, die Sie entfernen möchten.
* *Tabelle*: erforderlich. Eine Tabelle von zu entfernenden Datensätzen
* **All**: Optional. In einer Sammlung wird möglicherweise der gleiche Datensatz mehr als einmal angezeigt.  Sie können das **All**-Argument hinzufügen, um alle Kopien des Datensatzes zu entfernen.

**RemoveIf**( *DataSource*; *Condition* [; ... ] )

* *DataSource*: erforderlich. Die Datenquelle mit den Datensatz bzw. Datensätze, die Sie entfernen möchten.
* *Bedingung(en)* : Erforderlich. Eine Formel, die **TRUE** für die zu ersetzenden Datensätze ergibt.  Sie können auch die Spaltennamen aus *DataSource* in der Formel verwenden.  Wenn Sie mehrere *Bedingungen* angeben, müssen alle für Datensätze oder zu entfernende Datensätze zu **TRUE** ausgewertet werden.

## <a name="examples---single-formulas"></a>Beispiele: einzelne Formeln

In diesen Beispielen entfernen Sie einen Datensatz oder Datensätze aus einer Datenquelle mit dem Namen **IceCream** (Eiscreme), die mit den Daten in dieser Tabelle beginnt:

![](media/function-remove-removeif/icecream.png)

#### <a name="create-a-collection-with-sample-records"></a>Erstellen einer Sammlung mit Beispiel Datensätzen

So erstellen Sie eine Sammlung mit diesen Daten:

1. Ein [**Schalt**](../controls/control-button.md) Flächen-Steuerelement einfügen.
1. Legen **Sie die onselect** -Eigenschaft des Schaltflächen Steuer Elements auf die folgende Formel fest:

    ```powerapps-comma
    ClearCollect( IceCream;
                  { ID: 1; Flavor: "Chocolate";  Quantity: 100 };
                  { ID: 2; Flavor: "Vanilla";    Quantity: 200 };
                  { ID: 3; Flavor: "Strawberry"; Quantity: 300 }
    )
    ```
1. Wählen Sie die Schaltfläche, [während Sie die Alt-Taste gedrückt halten](../keyboard-shortcuts.md#alternate-behavior):


#### <a name="remove-sample-records-from-collection-using-a-formula"></a>Entfernen von Beispiel Datensätzen aus einer Sammlung mithilfe einer Formel

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Remove(&nbsp;IceCream;<br>First(&nbsp;Filter(&nbsp;IceCream;&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) )** |Entfernt den Datensatz **Chocolate** (Schokolade) aus der Datenquelle |<style>IMG {max-width: None}</style> ![](media/function-remove-removeif/icecream-no-chocolate.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **Remove(&nbsp;IceCream;<br>First(&nbsp;Filter(&nbsp;IceCream;&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) First(&nbsp;Filter(&nbsp;IceCream;&nbsp;Flavor="Strawberry"&nbsp;)&nbsp;) )** |Entfernt zwei Datensätze aus der Datenquelle. |![](media/function-remove-removeif/icecream-only-vanilla.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **RemoveIf(&nbsp;IceCream; Quantity&nbsp;>&nbsp;150 )** |Entfernt die Datensätze mit einer **Quantity** (Menge) größer als **150**. |![](media/function-remove-removeif/icecream-only-chocolate.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **RemoveIf(&nbsp;IceCream; Quantity&nbsp;>&nbsp;150; Left(&nbsp;Flavor;&nbsp;1&nbsp;) = "S" )** |Entfernt die Datensätze mit einer **Quantity** (Menge) größer als 150 und einem **Flavor** (Geschmack), der mit **S** beginnt |![](media/function-remove-removeif/icecream-no-strawberry.png)<br><br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |
| **RemoveIf(&nbsp;IceCream; true )** |Entfernt alle Einträge aus der Datenquelle |![](media/function-remove-removeif/icecream-empty.png)<br><br>Die Datenquelle **IceCream** (Eiscreme) wurde geändert. |

## <a name="examples---remove-button-outside-a-gallery"></a>Beispiele: Entfernen der Schaltfläche außerhalb eines Katalogs

In diesem Beispiel verwenden Sie ein Katalog- [ **Gallery** Steuer](../controls/control-gallery.md) Element, um die Datensätze in einer Tabelle aufzulisten. Und verwenden Sie dann die **Remove** -Funktion, um ein Element selektiv zu entfernen.  

### <a name="prepare-for-sample-data"></a>Vorbereiten von Beispiel Daten

In diesem Beispiel wird die **Contacts** -Entität in Common Data Service mit den *Beispiel-apps und-Daten*verwendet. Sie können *Beispiel-apps und-Daten* bereitstellen, wenn Sie [eine Umgebung erstellen](https://docs.microsoft.com/power-platform/admin/create-environment#create-an-environment-with-a-database). Sie können stattdessen auch eine beliebige andere Datenquelle verwenden.

### <a name="remove-button-outside-a-gallery"></a>Schaltfläche "entfernen" außerhalb eines Katalogs

In diesem Beispiel entfernen Sie ein Element mithilfe einer *Schaltfläche* außerhalb des Katalogs.

1. Erstellen Sie eine [neue leere Canvas-App](../data-platform-create-app-scratch.md) mit einem Telefon Layout.

    ![Eine leere Canvas-APP, die das Telefon Layout verwendet](media/function-remove-removeif/gallery-new.png)

1. Wählen Sie den **Einfügevorgang** im linken Bereich aus.

1. Wählen Sie **vertikaler**Katalog aus. <br>
    Ein Katalog-Steuerelement **wird dem Bild** Schirm hinzugefügt.

    ![Verwenden des einfügetoolbereichs zum Hinzufügen eines vertikalen Katalog-Steuer Elements](media/function-remove-removeif/gallery-add.png)

1. Sie werden aufgefordert, eine Datenquelle auszuwählen, in der Sie eine Datenquelle aus den verfügbaren Datenquellen auswählen können. <br>
    Wählen Sie beispielsweise die **Contacts** -Entität aus, um *Beispiel Daten*zu verwenden:  

    ![Auswählen der Entität "Kontakte", die im Katalog angezeigt werden soll](media/function-remove-removeif/gallery-datasource.png)

    Der Katalog zeigt Elemente aus dieser Entität an: 

    ![Der Katalog wurde mit der Entität "Contacts"](media/function-remove-removeif/gallery-data.png)

1. Ein [**Schalt**](../controls/control-button.md) Flächen-Steuerelement aus dem linken Bereich einfügen:
    
    ![Verwenden des einfügetoolbereichs zum Hinzufügen eines Button-Steuer Elements](media/function-remove-removeif/gallery-addbutton.png)

1. Verschieben Sie die hinzugefügte Schaltfläche unterhalb der Galerie Elemente:

    ![Schaltfläche Verschieben](media/function-remove-removeif/move-button-down.png)

1. Aktualisieren der Schaltflächen Text-Eigenschaft zum *Entfernen des Datensatzes* Sie können auch den gewünschten Text verwenden:

    ![Schaltfläche Umbenennen](media/function-remove-removeif/button-text.png)

1. Legen **Sie die onselect** -Eigenschaft für dieses Schaltflächen-Steuerelement auf die folgende Formel fest:

    ```powerapps-comma
    Remove( Contacts; Gallery1.Selected )
    ```

    ![Festlegen der onselect-Eigenschaft des Schaltflächen-Steuer Elements](media/function-remove-removeif/gallery-button-onselect.png)

    Das Katalog-Steuerelement macht den aktuell ausgewählten Datensatz mithilfe der **ausgewählten** Eigenschaft verfügbar. Funktion **Entfernen** verweist auf diesen ausgewählten Datensatz, um ihn zu entfernen.

1. Verwenden Sie oben rechts die Schaltfläche "wieder *Gabe* ", oder drücken Sie *F5* auf der Tastatur, um die APP anzuzeigen:

    ![Vorschau der APP](media/function-remove-removeif/preview-app.png)

1. Wählen Sie einen zu entfernenden Datensatz aus, z. b. den *Nancy*-Datensatz in diesem Beispiel:

    ![Datensatz auswählen](media/function-remove-removeif/select-nancy-record.png)

1. Wählen Sie **Datensatz entfernen**aus:

    ![Galerie mit Kontakten, jetzt ohne den Nancy-Datensatz, der entfernt wurde](media/function-remove-removeif/gallery-activatebutton.png)

    Wenn Sie auf die Schaltfläche klicken, wird der ausgewählte Datensatz (in diesem Beispiel der Nancy-Datensatz) entfernt.

1. Schließen Sie die APP-Vorschau.

    > [!TIP]
    > Sie können auch alternatives Verhalten mit [*ALT-Taste*](../keyboard-shortcuts.md#alternate-behavior) verwenden, anstatt die APP-Vorschau mit der *Wiedergabe* Schaltfläche oder *F5*zu verwenden.

## <a name="examples---trash-can-icon-inside-a-gallery"></a>Beispiele: Papierkorb Symbol innerhalb eines Katalogs

In diesem Beispiel entfernen Sie ein Element, indem Sie ein *Symbol* in der Galerie verwenden.

### <a name="create-a-collection-with-sample-data"></a>Erstellen einer Sammlung mit Beispiel Daten

Wenn Sie bereits [Beispiel Daten vorbereitet](#prepare-for-sample-data)haben, überspringen Sie diesen Schritt, und wechseln Sie in einem Katalog zum [Papierkorb Symbol](#trash-can-icon-inside-a-gallery).

1. Fügen Sie dem Bildschirm ein [**Button**](../controls/control-button.md) -Steuerelement hinzu.
1. Legen Sie die **OnSelect**-Eigenschaft auf die folgende Formel fest:

    ```powerapps-comma
    ClearCollect( SampleContacts; 
          { 'Full Name': "Yvonne McKay (sample)";      'Primary Email': "someone_a@example.com" };
          { 'Full Name': "Susanna Stubberod (sample)"; 'Primary Email': "someone_b@example.com" };
          { 'Full Name': "Nancy Anderson (sample)";    'Primary Email': "someone_c@example.com" };
          { 'Full Name': "Maria Campbell (sample)";    'Primary Email': "someone_d@example.com" };
          { 'Full Name': "Robert Lyon (sample)";       'Primary Email': "someone_e@example.com" };
          { 'Full Name': "Paul Cannon (sample)";       'Primary Email': "someone_f@example.com" };
          { 'Full Name': "Rene Valdes (sample)";       'Primary Email': "someone_g@example.com" } 
    )
    ```
1. Wählen Sie die Schaltfläche, [während Sie die Alt-Taste gedrückt halten](../keyboard-shortcuts.md#alternate-behavior).

Die Beispiel Sammlung wird erstellt, die Sie im folgenden Beispiel verwenden können.

### <a name="trash-can-icon-inside-a-gallery"></a>Papierkorb Symbol innerhalb eines Katalogs

1. Erstellen Sie eine [neue leere Canvas-App](../data-platform-create-app-scratch.md) mit einem Telefon Layout.

    ![Eine leere Canvas-APP, die das Telefon Layout verwendet](media/function-remove-removeif/gallery-new.png)

1. Wählen Sie den **Einfügevorgang** im linken Bereich aus.

1. Wählen Sie **vertikaler**Katalog aus. <br>
    Ein Katalog-Steuerelement **wird dem Bild** Schirm hinzugefügt.

    ![Verwenden des einfügetoolbereichs zum Hinzufügen eines vertikalen Katalog-Steuer Elements](media/function-remove-removeif/gallery-add.png)

1. Sie werden aufgefordert, eine Datenquelle auszuwählen, in der Sie eine Datenquelle aus den verfügbaren Datenquellen auswählen können. <br>
    Wählen Sie beispielsweise die **Contacts** -Entität aus, um *Beispiel Daten*zu verwenden:  

    ![Auswählen der Entität "Kontakte", die im Katalog angezeigt werden soll](media/function-remove-removeif/gallery-datasource.png)

    Wenn Sie eine [Sammlung](#create-a-collection-with-sample-data)erstellt haben, wählen Sie stattdessen Ihre Sammlung aus:

    ![Sammlung von Beispiel Kontakten](media/function-remove-removeif/sample-contacts.png)

1. Wählen Sie ein Steuerelement im oberen Bereich des Katalogs aus. <br>
    
    Stellen Sie sicher, dass Sie diesen Schritt ausführen, bevor Sie mit dem nächsten Schritt fortfahren, um sicherzustellen, dass der nächste Schritt das Element in der Galerie Vorlage und nicht außerhalb des Katalogs
    
    ![Auswählen des obersten Datensatzes in einem Katalog](media/function-remove-removeif/gallery-select-template.png)

1. Wählen Sie im linken Bereich **Symbol hinzufügen** aus. <br>
    
    ![Verwenden des einfügetoolbereichs zum Hinzufügen eines Symbol Steuer Elements](media/function-remove-removeif/gallery-addicon.png)

    > [!NOTE]
    > **Symbol "hinzufügen** " fügt ein **+** Symbol auf der linken Seite des Katalogs ein, das für jedes Element im Katalog repliziert wird. 

1. Verschieben Sie das Symbol im oberen Element auf die Rechte Seite des Bildschirms.

    ![Symbol "Verschieben"](media/function-remove-removeif/move-icon.png)

1. Wählen Sie die **Symbol** Eigenschaft für Symbol aus, und legen Sie Sie auf die folgende Formel fest, um das Symbolbild als Papierkorb Symbol zu aktualisieren:

    ```powerapps-comma 
    Icon.Trash
    ```
    
    > [!NOTE]
    > Das **Symbol.** das Präfix wird nur angezeigt, wenn Sie die Formel aktiv bearbeiten.

    ![Ändern des Symbols in das Papierkorb Symbol](media/function-remove-removeif/gallery-icontrash.png)

1. Legen Sie die **OnSelect**-Eigenschaft auf die folgende Formel fest:

    ```powerapps-comma
    Remove( [@Contacts]; ThisItem )
    ```

    > [!NOTE]
    > Sie müssen den [globalen mehrdeutigkeits Operator](operators.md#disambiguation-operator) **[@** ... **]** in diesem Beispiel mit Beispiel Daten, die die *Contacts* -Entität verwenden, um Konflikte mit einer *1: n-* Beziehung zu vermeiden. Wenn Sie Datenquellen wie z. b. eine SharePoint-Liste oder eine SQL Server Tabelle verwenden, ist die Verwendung des *globalen disambgulations-Operators* nicht erforderlich.

    ![Onselect für Papierkorb (Symbol)](media/function-remove-removeif/gallery-onselect.png)

1. Verwenden Sie oben rechts die *Schaltfläche* wiedergeben, oder drücken Sie *F5* , um die app in der Vorschau anzuzeigen.

1. Wählen Sie das Papierkorb Symbol neben einem Datensatz aus, z. b. " *Maria*":

    ![Katalog mit einem der entfernten Kontakte](media/function-remove-removeif/gallery-activateicon.png)

    Der Datensatz wird gelöscht:

    ![Datensatz gelöscht](media/function-remove-removeif/deleted-record.png)

1. Schließen Sie die APP-Vorschau.
