---
title: Entitätsformulare anpassen (modellgesteuerte Apps) | Microsoft Docs
description: Formulare bieten die Benutzeroberfläche (UI), mit der Benutzer Entitätsdatensätze erstellen, anzeigen oder bearbeiten. Verwenden Sie den Formular-Designer in der Anpassungstools, um Entitätsformulare zu erstellen und zu bearbeiten. Dieses Thema enthält die erforderlichen Informationen, um programmgesteuert Formulare zu erstellen oder zu bearbeiten.
keywords: ''
ms.date: 03/10/2020
ms.service: powerapps
ms.topic: article
ms.assetid: e6a25bbe-e484-cfe9-9ad9-20ac6f19336a
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b5ca535e329f20813662e9a218ed47da19d09a08
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275938"
---
# <a name="customize-entity-forms"></a>Anpassen von Entitätsformularen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/customize-entity-forms -->

Formulare bieten die Benutzeroberfläche (UI), mit der Benutzer Entitätsdatensätze erstellen, anzeigen oder bearbeiten. Verwenden Sie den Formular-Designer in der Anpassungstools, um Entitätsformulare zu erstellen und zu bearbeiten. Weitere Informationen: [Formulare erstellen und gestalten](../../maker/model-driven-apps/create-design-forms.md) zu Informationen über Aufgaben im Zusammenhang mit der Arbeit mit Formularen in der Anwendung.  

 Dieses Thema enthält die erforderlichen Informationen, um programmgesteuert Formulare zu erstellen oder zu bearbeiten.  

<a name="BKMK_AccessingFormDefinitions"></a>   

## <a name="access-form-definitions"></a>Zugriffsformulardefinitionen  
 Entitätsformulare werden in der `SystemForm`-Entität zusammen mit Dashboards und Visualisierungen gespeichert. Es gibt zwei Möglichkeiten, die Formulardefinitionen für eine Entität einzusehen:  

-   Schließen Sie die Entität in einer nicht verwalteten Lösung ein, und exportieren Sie die Lösung.  

-   Fragen Sie die `SystemForm`-Entität ab.  

<a name="BKMK_ViewingFormXml"></a>   

### <a name="view-formxml-from-an-exported-entity"></a>Anzeige von FormXML aus einer exportierten Entität  
 Nur Definitionen von Systementitätsformularen, die angepasst wurden, sind in einer exportierten verwalteten Lösung enthalten. Um die Definition eines Systementitätsformulars anzuzeigen, müssen Sie sie entweder irgendwie ändern oder ein neues Formular erstellen, indem Sie das vorhandene Formular unter einem neuen Namen speichern.  

 Nachdem Sie die Lösung exportiert haben, extrahieren Sie die Inhalte und zeigen Sie die customizations.xml-Datei an. Die Definition der Formulare finden Sie unter `ImportExportXml` > `Entities` > `Entity` > `FormXml`. Im Knoten `<FormXml>` finden Sie jeden Formulartyp in einem `<forms>`-Element gruppiert, wobei das Attribut `type` den Formulartyp angibt.  

<a name="BKMK_FormProperties"></a>   
## <a name="form-properties"></a>Formulareigenschaften  
 Die folgende Tabelle enthält zentrale `SystemForm`-Entitätsattribute und die entsprechenden Daten in den mit der Lösung exportierten XML-Elementen.  


|  SystemForm-Eigenschaft  |                 FormXML-Element                 |                                                                                                              Beschreibung                                                                                                              |
|-----------------------|-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   `AncestorFormId`    |                  `<ancestor>`                   |                      Eindeutiger Bezeichner des übergeordneten Formulars. Dieser wird festgelegt, wenn Sie ein neues Formular erstellen, indem Sie ein Formular mit **Speichern unter** fürein bestehendes Formular oder mit <xref:Microsoft.Crm.Sdk.Messages.CopySystemFormRequest> erstellen.                      |
|    `CanBeDeleted`     |                `<CanBeDeleted>`                 |                                    Informationen, mit denen angegeben wird, ob die Komponente gelöscht werden kann. Diese verwaltete Eigenschaft wird erst angewendet, wenn das Formular erstellt wurde, indem eine verwaltete Lösung importiert wird.                                    |
|     `Description`     |                `<Descriptions>`                 | `Description` ist eine Zeichenfolge und `<Descriptions>` enthält alle Bezeichnungen der lokalisierten Beschreibung des Formulars.<br /><br /> Die lokalisierten Etiketten können mithilfe von <xref:Microsoft.Crm.Sdk.Messages.RetrieveLocLabelsRequest> abgerufen werden. |
| `FormActivationState` |             `<FormActivationState>`             |                                  Legt den Status des Formulars fest.<br /><br /> Nur Formulare vom Typ "main" können deaktiviert werden.<br /><br /> Gültige Werte:<br /><br /> -   0 : Inaktiv<br />-   1 : Aktiv                                  |
|       `FormId`        |                   `<formid>`                    |                                                                                                     Eindeutiger Bezeichner des Formulars                                                                                                     |
|  `FormPresentation`   |              `<FormPresentation>`               |                                     Gibt an, ob sich dieses Formular im aktualisierten UI-Layout in Common Data Service befindet.                                      |
|       `FormXml`       |                    `<form>`                     |                                                                                                XML-Darstellung des Formularlayouts.                                                                                                 |
|  `IntroducedVersion`  |              `<IntroducedVersion>`              |                                                                                          Version der Lösung, in der das Formular hinzugefügt wurde.                                                                                          |
|     `IsAIRMerged`     |                       Nicht zutreffend                       |                                           Gibt an, ob dieses Formular mit dem aktualisierten UI-Layout in Common Data Service zusammengeführt wurde.                                           |
|   `IsCustomizable`    |               `<IsCustomizable>`                |                            Informationen, mit denen angegeben wird, ob die Komponente angepasst werden kann.<br /><br /> Diese verwaltete Eigenschaft wird nur angewendet, wenn das Formular durch Importieren einer verwalteten Lösung erstellt wurde.                            |
|      `IsDefault`      |                       Nicht zutreffend                       |                                                                          Informationen, die angeben, ob es sich bei Formular oder Dashboard um den Systemstandard handelt.                                                                          |
|        `Name`         |               `<LocalizedNames>`                |       `Name` ist eine Zeichenfolge und `<LocalizedNames>` enthält alle Bezeichnungen des lokalisierten Namens des Formulars.<br /><br /> Die lokalisierten Etiketten können mithilfe von <xref:Microsoft.Crm.Sdk.Messages.RetrieveLocLabelsRequest> abgerufen werden.       |
|   `ObjectTypeCode`    | Das Formular stammt von dem `Entity`-Element. |                                                                                        Der `ObjectTypeCode`-Wert ist der logische Name der Entität.                                                                                         |
|        `Type`         |       `<forms>` Element `type` Attribute        |                                                       Gültige Werte für Formulare sind:<br /><br /> -   2: `main`<br />-   5: `mobile`<br />-   6: `quick`<br />-   7: `quickCreate`                                                        |

<a name="BKMK_CreateAndEditForms"></a>   

## <a name="create-and-edit-forms"></a>Erstellen und Bearbeiten von Formularen  

 Sie können neue Formulare für eine Entität nur erstellen, wenn <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>. <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanCreateForms> dies zulässt.  

 Sie können neue Formulare entweder mit einer <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> oder mit <xref:Microsoft.Crm.Sdk.Messages.CopySystemFormRequest> erstellen. Wenn Sie <xref:Microsoft.Crm.Sdk.Messages.CopySystemFormRequest> oder **Speichern unter** im Formulareditor verwenden, findet keine Vererbung zwischen den Formularen statt. Änderungen am Basisformular werden daher nicht automatisch auf alle daraus erstellten Formulare angewendet.  

 Das Ändern der Formulardefinitionen aus einer exportierten verwalteten Lösung und der anschließende erneute Import der Lösung ist das unterstützte Verfahren für die Bearbeitung von Entitätsformularen. Beik manuellen Bearbeiten von Formularen wird nachdrücklich empfohlen, einen XML-Editor zu verwenden, der die Schemaevaluierung ermöglicht. Weitere Informationen: [Bearbeiten der Anpassungs-XML-Datei mit Schemaüberprüfung](edit-customizations-xml-file-schema-validation.md).  

## <a name="open-main-form-in-a-dialog-using-client-api"></a>Öffnen des Hauptformulars in einem Dialogfeld mithilfe der Client-API

Um das Hauptformular in einem Dialogfeld mithilfe der Client-API zu öffnen, müssen Sie den Aufruf mithilfe der [Xrm.Navigation.navigateTo](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/navigateto) Methode aufrufen. Mit [der Xrm.Navigation.navigateTo](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/navigateto) API-Methode können Sie das Dialogfeld mit mehreren Optionen öffnen, einschließlich Größe und Position.


> [!IMPORTANT]
> - Das geöffnete Hauptformular in einem Dialogfeld mit der Client-API befindet sich noch in der Vorschau.
> - Vorschaufunktionen sind nicht für den produktiven Einsatz gedacht und haben möglicherweise eingeschränkte Funktionalität. Diese Funktionen stehen vor der offiziellen Version zur Verfügung, damit Kunden früher Zugriff darauf erhalten und Feedback geben können.

> [!NOTE]
> [Die Xrm.Navigation.openForm](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/openform) Methode wird nicht unterstützt, um ein Hauptformular als Dialog zu öffnen.

## <a name="examples"></a>Beispiele

### <a name="open-a-new-record"></a>Einen neuen Datensatz öffnen

In diesem Beispiel öffnet das Dialogfeld ein neues Kontoformular zum Erstellen eines neuen Datensatzes. Das Dialogfeld wird in der Mitte angezeigt, indem bis zu 50 % des verfügbaren Fensters als Modal auf dem Formular verwendet werden, das aufgerufen oder aufgerufen wurde.

```JavaScript
var pageInput = {
    pageType: "entityrecord",
    entityName: "account",
    formType: 2,
};
var navigationOptions = {
    target: 2,
    width: {value: 50, unit:"%"},
    position: 1
};
Xrm.Navigation.navigateTo(pageInput, navigationOptions);
```
> [!div class="mx-imgBorder"]
> ![Einen neuen Datensatz öffnen](media/open-new-record-mfd.png "Einen neuen Datensatz öffnen")

### <a name="open-an-existing-record"></a>Vorhandenen Datensatz öffnen

In diesem Beispiel öffnet das Dialogfeld einen vorhandenen Firmendatensatz mit dem Kontoentitäts-ID-Wert über dem Kontaktformular. Ersetzen Sie die Entitäts-ID durch einen beliebigen Datensatz-ID-Wert, den Sie im Dialogfeld öffnen möchten.

```JavaScript
var pageInput = {
    pageType: "entityrecord",
    entityName: "account",
    formType: 2,
    entityId: "5a57f2c3-5672-ea11-a812-000d3a339706" //replace with actual ID
};
var navigationOptions = {
    target: 2,
    width: {value: 80, unit:"%"},
    position: 1
};
Xrm.Navigation.navigateTo(pageInput, navigationOptions);
```
> [!div class="mx-imgBorder"]
> ![Vorhandenen Datensatz öffnen](media/open-existing-record-mfd.png "Vorhandenen Datensatz öffnen")

### <a name="open-a-new-record-on-the-side-pane"></a>Öffnen eines neuen Datensatzes im Seitenbereich

In diesem Beispiel öffnet das Dialogfeld einen neuen Datensatz in der rechten Ecke des Fensters. Dies kann durch die Verwendung der Pixeloptionen erreicht werden.

```JavaScript
var pageInput = {
    pageType: "entityrecord",
    entityName: "account",
    formType: 2,
};
var navigationOptions = {
    target: 2,
    width: {value: 500, unit:"px"},
    position: 2
};
Xrm.Navigation.navigateTo(pageInput, navigationOptions);
```
> [!div class="mx-imgBorder"]
> ![Öffnen eines bestehenden Datensatzes im Seitenbereich](media/open-record-side-pane-mfd.png "Öffnen eines bestehenden Datensatzes im Seitenbereich")

### <a name="open-main-form-in-a-dialog-with-callback-method"></a>Hauptformular in einem Dialog mit Rückrufmethode öffnen

Dieses Beispiel zeigt, wie ein Hauptformulardialog mit einer Rückrufmethode aufgerufen wird, nachdem ein Datensatz gespeichert und das Dialogfeld geschlossen wurde.

```Javascript
var pageInput = {
    pageType: "entityrecord",
    entityName: "account",
    formType: 2
};
var navigationOptions = {
    target: 2,
    width: {value: 80, unit:"%"},
    position: 2  
};
Xrm.Navigation.navigateTo(pageInput, navigationOptions).then(
    function success(result) {
            console.log("Record created with ID: " + result.savedEntityReference[0].id + 
            " Name: " + result.savedEntityReference[0].name)
            // Handle dialog closed
    },
    function error() {
            // Handle errors
    }
);
```

### <a name="see-also"></a>Siehe auch  

 [Erstellen und Gesalten von Formularen](../../maker/model-driven-apps/create-design-forms.md)   
 [SystemForm-Entität](../common-data-service/reference/entities/systemform.md)  
 [Formular-XML-Schema](form-xml-schema.md)<br/>
 [Xrm.Navigation.navigateTo](https://docs.microsoft.com/powerapps/developer/model-driven-apps/clientapi/reference/xrm-navigation/navigateto)
