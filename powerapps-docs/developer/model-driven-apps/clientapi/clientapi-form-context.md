---
title: Client API-Formularkontext in modellgestützten Apps| MicrosoftDocs
ms.date: 04/10/2019
ms.service: powerapps
ms.topic: conceptual
applies_to:
- Dynamics 365 (online)
ms.assetid: 0cf94e8d-801a-451f-98c3-130e912f963b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3e40c21bb1e26ebefca3ea8d71fb1d02dad1700b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748478"
---
# <a name="client-api-form-context"></a>Formularkontext der Client-API



Der Client-API-Formularkontext (**formContext**) bietet eine Referenz im Formular oder auf ein Element im Formular, wie z. B. ein Steuerelement für die Schnellansicht oder eine Zeile in einem bearbeitbaren Raster, für den der aktuelle Code ausgeführt wird.

Früher wurde das globale **Xrm.Page**-Objekt dazu verwendet, um ein Formular oder ein Element im Formular darzustellen. Mit der neuesten Version ist das **Xrm.Page**-Object [veraltet](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated), und Sie sollen nun die [getFormContext](reference/executioncontext/getFormContext.md)-Methode aus dem zur Ausführung übergebenen Kontextobjekt verwenden, um die Referenz ins entsprechende Formular oder ein Element im Formular zurückzugeben. 

> [!IMPORTANT]
> *Veraltet* bedeutet, dass wir eine Funktion aus einer zukünftigen Version von modellgesteuerten Apps entfernen möchten; die Funktionen oder die Funktionalität wird weiterhin funktionieren und vollständig unterstützt, bis sie offiziell entfernt wird. Mindestens sechs Monate vor dem Entfernen wird eine öffentliche Ankündigung hier in der Dokumentation, im offiziellen Blog und an vielen anderen Orten ausgegeben.<br/><br/>Verwendung von **Xrm.Page** als statischen Zugang zum primären Formularkontext ist *weiterhin* unterstützt, um die vorhandene Abwärtskompatibilität mit Skripten beizubehalten und wird nicht entfernt, sobald weitere Client API-Methoden im Bereich der [Client API-Veraltung](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated) entfernt werden. Es wird empfohlen, das Sie das neue **formContext**-Objekt und nicht das **Xrm.Page**-Objekt in Ihrer  Codezielgruppenadressierung Version 9.0 oder höher verwenden, sofern möglich. Ein weiterer Vorteil der Verwendung des **formContext**-Objekts ist, dass es Ihnen ermöglicht, gemeinsame Ereignishandler zu erstellen, die entweder über ein Formular oder in einem bearbeitbaren Raster verwendet werden, je nachdem wo sie aufgerufen werden. Weitere Informationen: [getFormContext (Client-API-Referenz)](reference/executioncontext/getFormContext.md).<br><br>Das Ziel für **formContext** JavaScript-Funktionen für Menübandaktionen abzurufen, ist jedoch unterschiedlich vom Abrufen von Formularskripts. Weitere Informationen: [Formular- und Rasterkontext in Menübandaktionen](../pass-data-page-parameter-ribbon-actions.md#form-and-grid-context-in-ribbon-actions).

## <a name="using-the-formcontext-object-instead-of-the-xrmpage-object"></a>Verwendung des formContext-Objekts anstelle des Xrm.Page-Objekts 

Es ist einfach, den vorhandenen Code mit **Xrm.Page** zu konvertieren, um das neue **formContext**-Objekt zu verwenden. Betrachten Sie beispielsweise das folgende Skript, das das **Xrm.Page**-Objekt verwendet:

```JavaScript
function displayName()
{
    var firstName = Xrm.Page.getAttribute("firstname").getValue();
    var lastName = Xrm.Page.getAttribute("lastname").getValue();
    console.log(firstName + " " + lastName);
}
```

Hier finden Sie das aktualisierte Skript, das den zur Ausführung übergabenen Kontext verwendet, um das **formContext**-Objekt anstatt Verwendung des **Xrm.Page**-Objekts abzurufen:

```JavaScript
function displayName(executionContext)
{
    var formContext = executionContext.getFormContext(); // get formContext

    // use formContext instead of Xrm.Page  
    var firstName = formContext.getAttribute("firstname").getValue(); 
    var lastName = formContext.getAttribute("lastname").getValue();
    console.log(firstName + " " + lastName);
}
```

>[!IMPORTANT]
>Sie müssen daran denken, die Option **Ausführungskontext als ersten Parameter übergeben** im Dialogfeld **Handlereigenschaften** auszuwählen, während Sie die Ereignishandler für die Verwendung des Objekts **formContext** definieren. Weitere Informationen: [Client-API-Ausführungskontext](clientapi-execution-context.md)

## <a name="formcontext-object-model"></a>formContext-Objektmodell

Verwenden Sie die **Daten**- und **Benutzerschnittstelle**-Objekte unter dem **formContext**-Objekt, um Daten oder Benutzerschnittstellenelemente in modellgesteuerten Apps programmgesteuert zu bearbeiten.

![formContext-Objektmodell](../media/ClientAPI-formContextModel.png)

### <a name="data-object"></a>Datenobjekt

Bietet Zugriff auf die Entitätsdaten und Methoden der Datenverwaltung im Formular sowie im Geschäftsprozessflusssteuerelement. Enthält die folgenden Objekte:

| **Objekt**  | **Beschreibung**|
|-----------------|----------------|
|Entität|Bietet Methoden zum Abrufen von Informationen, die für den auf der Seite angezeigten Datensatz spezifisch sind, die Speichermethode und eine Sammlung aller im Formular enthaltenen Attribute.|
|Prozess|Bietet Methoden zum Abrufen der Eigenschaften eines Geschäftsprozessflusses.|

Es bietet auch eine **Attribute**-Sammlung für den Zugriff auf das non-entity-gebundenen Steuerelement. Weitere Informationen finden Sie im Abschnitt **Sammlungen im formContext-Objektmodell** in diesem Thema unten.

Weitere Informationen: [formContext.data](reference/formContext-data.md) 

### <a name="ui-object"></a>Benutzerschnittstellenobjekt

Bietet neben Sammlungen für verschiedene Unterkomponenten des Formulars oder Rasters die Methoden zum Abrufen von Informationen über die Benutzerschnittstelle. Enthält die folgenden Objekte:

| **Objekt**  | **Beschreibung**|
|-----------------|----------------|
|formSelector|Bietet eine Elementsammlung, die Funktionen zum Abfragen der Formulare, die für den aktuellen Benutzer verfügbar sind, bereitstellt. Verwenden Sie die Navigationsmethode, um das aktuelle Formular zu schließen und ein anderes zu öffnen.|
|Navigation|Enthält keine Methoden. Bietet Zugriff auf die Navigationselemente über die Elementsammlung. Weitere Informationen über Sammlungen finden Sie im folgenden Abschnitt.|
|Prozess|Stellt Methoden zum Interagieren mit den Geschäftsprozessflusssteuerung in einem Formular bereit.|

Weitere Informationen: [formContext.ui](reference/formContext-ui.md)

## <a name="collections-in-the-formcontext-object-model"></a>Sammlungen im formContext-Objektmodell

Die folgende Tabelle beschreibt die Sammlungen im **Xrm**-Objektmodell. Weitere Informationen über die für Sammlungen allgemein verfügbaren Methode finden Sie unter [Sammlungen (Client-API-Referenz)](reference/collections.md).

| **Sammlung**  | **Beschreibung**|
|-----------------|----------------|
| [Attribute](reference/attributes.md)  | Zwei Objekte enthalten einen Attributsammlung:<br/><br/>- **formContext.data.attributes**-Sammlung bietet den Zugriff auf nicht entitätsgebundene Attribute.<br/><br/>- **formContext.data.entity.attributes**-Sammlung bietet Zugriff auf jedes Entitätsattribut, das im Formular verfügbar ist. Nur die Attribute, die Feldern entsprechen, die im Formular hinzugefügt wurden, sind verfügbar.| 
| [Steuerelemente](reference/controls.md)  | Drei Objekte enthalten eine Sammlung von Steuerelementen:<br/><br/> - **formContext.ui.controls**: Bietet den Zugriff auf jedes Steuerelement, das im Formular vorhanden ist.<br/><br/>- **formContext.data.entity.attribute.controls**: Da ein Attribut über mehr als ein Steuerelement im Formular verfügen kann, bietet diese Sammlung den Zugriff auf jedes davon. Diese Sammlung enthält nur ein Element, es sei denn, dass mehrere Steuerelemente für das Attribut dem Formular hinzugefügt werden.<br/><br/>- **formContext.ui.tabs.sections.controls**: Diese Sammlung enthält nur die Steuerelemente, die im Bereich gefunden sind.|
|**formContext.data.process.**[stages](reference/formContext-data-process/process/getStages.md) und **formContext.data.process**.[steps](reference/formContext-data-process/stage/getSteps.md)| Stellt den Zugriff auf die Phasen- und Schrittsammlungen in einem Geschäftsprozessfluss bereit. Diese erlauben auch das Hinzufügen und Entfernen der Elementen der Sammlung.|
|**formContext.ui.formselector.**[items](reference/formContext-ui-formselector.md)|Wenn für eine Entität mehrere Formulare bereitgestellt werden, können Sie jedem Formular Sicherheitsrollen zuordnen. Wenn die Sicherheitsrollen, die einem Benutzer zugeordnet sind, es diesem ermöglichen, mehr als ein Formular anzuzeigen, bietet die **formContext.ui.formSelector.items**-Sammlung den Zugriff auf jede Formulardefinition, die diesem Benutzer verfügbar ist.|
|**formContext.ui.navigation.**[items](reference/formContext-ui-navigation.md)|Die **formContext.ui.navigation.items**-Sammlung bietet den Zugriff auf die Navigationselemente, die mithilfe des Navigationsbereichs des Formular-Editors definiert werden. Benutzer navigieren dazu mithilfe der Befehlsleiste.|
| **formContext.ui.**[quickForms](reference/formContext-ui-quickForms.md) | Stellt Methoden des Zugriffs auf sämtliche Steuerelemente für die Schnellansicht und deren zugehörigen Kontrollelemente für die Customer Enagagement-Formularen bereit.| **Xrm.Page.ui.tabs**-Sammlung bietet Zugriff auf jede dieser Registerkarten.|
| **formContext.ui.**[tabs](reference/formContext-ui-tabs.md) | Sie können jedes Formular organisieren, indem Sie eine oder mehrere Registerkarten verwenden. Diese Sammlung bietet Zugriff auf jede dieser Registerkarten.|
| **formContext.ui.tabs.**[sections](reference/formContext-ui-sections.md) | Sie können jede Registerkarte im Formular organisieren, indem Sie einen oder mehrere Abschnitte verwenden. Die **sections**-Sammlung der Registerkarten bietet Zugriff auf jeden dieser Abschnitte.|


  
### <a name="related-topics"></a>Verwandte Themen

[getFormContext-Methode](reference/executioncontext/getFormContext.md)<br/>
[getGlobalContext-Methode](reference/xrm-utility/getGlobalContext.md)<br/>
[Ausführungskontextmethoden](reference/execution-context.md) 

 

