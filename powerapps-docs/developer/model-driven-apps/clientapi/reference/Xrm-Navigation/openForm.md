---
title: openForm (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 03/10/2019
ms.service: powerapps
ms.topic: reference
ms.assetid: 0206c43b-b1fc-490d-a867-1d75331885a8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openform-client-api-reference"></a>openForm (Client-API-Referenz)

[!INCLUDE[./includes/openForm-description.md](./includes/openForm-description.md)]

## <a name="syntax"></a>Syntax

`Xrm.Navigation.openForm(entityFormOptions,formParameters).then(successCallback,errorCallback);`

## <a name="parameters"></a>Parameter


<table style="width:100%">
  <tr>
    <th>Name</th>
    <th>Typ</th> 
    <th>Erforderlich</th>
    <th>Beschreibung</th>
  </tr>
  <tr>
    <td>entityFormOptions</td>
    <td>Objekt</td> 
    <td>Ja</td>
    <td>Entitätsformularoptionen für das Öffnen des Formulars. Das Objekt hat die folgenden Attribute:<ul>
<li><b>cmdbar</b>: (Optional) Boolesch. Gibt an, ob die Befehlsleiste angezeigt werden soll. Wird dieser Wert nicht angegeben, wird standardmäßig die Befehlsleiste angezeigt.</li>
<li><b>createFromEntity</b>:( Optionale) Suche. Gibt einen Datensatz an, der Standardwerte basierend auf zugeordneten Attributwerten bereitstellt. Das Suchobjekt hat folgende Zeichenfolgeneigenschaften: <code>entityType</code>, <code>id</code>und <code>name</code> (optional).</li>
<li><b>entityId</b>: (Optional) Zeichenfolge. Die ID des Entitätsdatensatzes, für den das Formular angezeigt wird.</li>
<li><b>entityName</b>: (Optional) Zeichenfolge. Die ID des Entitätsdatensatzes, für den das Formular angezeigt wird.</li>
<li><b>formId</b>: (Optional) Zeichenfolge. ID der anzuzeigenden Formularinstanz.</li>
<li><b>Höhe</b>: (Optional) Zahl. Die Höhe des zu öffnenden Formulars in Pixeln.</li>
<li><b>navBar</b>: (Optional) Zeichenfolge. Steuert, ob die Navigationsleiste angezeigt wird und ob Anwendungsnavigation über die in der Siteübersicht definierten Bereiche und Unterbereiche verfügbar ist. Gültige Werte sind: "an", "aus" und" Entität".<ul><li><code>on</code>: Die Navigationsleiste wird angezeigt. Dies ist das Standardverhalten, wenn der Parameter <b>navbar</b> nicht verwendet wird.</li>
<li><code>off</code>: Die Navigationsleiste wird nicht angezeigt. Benutzer können andere Benutzeroberflächenelemente oder die Schaltflächen Zurück und Weiter für die Navigation verwenden.</li><li><code>entity</code>: In einem Entitätsformular sind nur die Navigationsoptionen für verknüpfte Entitäten verfügbar. Nach der Navigation zu einer verknüpften Entität wird die Schaltfläche Zurück in der Navigationsleiste angezeigt, mit der Sie zum ursprünglichen Datensatz zurückkehren können.</li></ul></li>
<li><b>openInNewWindow</b>: (Optional) Boolesch. Gibt an, ob das Formular in einem neuen Fenster angezeigt wird.</li>
<li><b>windowPosition</b>: (Optional) Zahl. Geben Sie einen der folgenden Werte für die Fensterposition des Formulars auf den Bildschirm an:<ul><li><code>1:center</code></li><li><code>2:side</code></li></ul>
<li><b>processId</b>: (Optional) Zeichenfolge. ID des im Formular anzuzeigenden Geschäftsprozesses.</li>
<li><b>processInstanceId</b>: (Optional) Zeichenfolge. ID der im Formular anzuzeigenden Geschäftsprozessinstanz.</li>
<li><b>Beziehung</b>: (Optiona) Objekt. Definieren eines Beziehungsobjekts, um die zugehörigen Datensätze im Formular anzuzeigen. Das Objekt hat die folgenden Attribute.
<table style="width:100%">
  <tr>
    <th>Name</th>
    <th>Typ</th> 
    <th>Beschreibung</th>
<tr>
<td>attributeName</td>
<td>String</td>
<td>Der Name des für die Beziehung verwendeten Attributs.</td>
</tr>
<tr>
<td>Name</td>
<td>String</td>
<td>Der Name der Beziehung.</td>
</tr>
<tr>
<td>navigationPropertyName</td>
<td>String</td>
<td>Name der Navigationseigenschaft für die Beziehung.</td>
</tr>
<tr>
<td>relationshipType</td>
<td>Zahl</td>
<td>Beziehungstyp. Geben Sie einen der folgenden Werte an:
<ul><li><code>0:OneToMany</code></li><li><code>1:ManyToMany</code></li></ul></td>
</tr>
<tr>
<td>roleType</td>
<td>Zahl</td>
<td>Beziehungsrollentyp. Geben Sie einen der folgenden Werte an:
<ul><li><code>1:Referencing</code></li><li><code>2:AssociationEntity</code></li></ul></td>
</tr>
</table>
</li>
<li><b>selectedStageId</b>: (Optional) Zeichenfolge. ID der ausgewählten Phase in der Geschäftsprozessinstanz.</li>
<li><b>useQuickCreateForm</b>: (Optional) Boolesch. Gibt an, ob das Formular "Schnellerfassung" geöffnet wird. Wird dieser Parameter nicht angegeben, wird <b>false</b> als Standardwert übergeben.</li>
<li><b>Breite</b>: (Optional) Zahl. Die Breite des zu öffnenden Formulars in Pixeln.</li>
</ul>
</tr>
<tr>
<td>formParameters</td>
<td>Objekt</td>
<td>No</td>
<td>Ein Wörterbuchobjekt, das dem Formular zusätzliche Parameter übergibt. Ungültige Parameter führen zu einem Fehler.<br/><br/>Informationen zum Übergeben von Parametern an ein Formular finden Sie unter <a href="https://docs.microsoft.com/powerapps/developer/model-driven-apps/set-field-values-using-parameters-passed-form
">Festlegen von Feldwerten mithilfe von Parametern, die an ein Formular übergeben werden</a> und <a href="https://docs.microsoft.com/powerapps/developer/model-driven-apps/configure-form-accept-custom-querystring-parameters">Ein Formular konfigurieren, um benutzerdefinierte Abfragezeichenfolgenparameter zu akzeptieren</a></td>
</tr>
<tr>
<td>successCallback</td>
<td>Funktion</td>
<td>Nein</td>
<td>Ein Feature, das ausgeführt wird, wenn der Datensatz im Schnellerfassungsformular gespeichert wird.

Dieser Funktion wird ein Objekt als Parameter übergeben. Das Ziel ist ein <b>savedEntityReference</b>-Array mit den folgenden Eigenschaften, um den erstellten oder angezeigten Datensatz zu identifizieren:
<ul>
<li><b>entityType</b>:  Der logische Name der Entität.</li>
<li><b>id</b>: Eine Zeichenfolgendarstellung eines GUID-Werts für den Datensatz.</li>
<li><b>name</b>: der primäre Attributwert des erstellten oder angezeigten Datensatzes.</li></ul>

<b>Hinweis</b>:
  <ul>
    <li>Die <b>successCallback</b>-Funktion wird nicht ausgeführt, wenn Sie ein Formular für einen vorhandenen oder einen neuen Datensatz öffnen.</li>
    <li>Die Funktion <b>successCallback</b> wird nur ausgeführt, wenn Sie eine Aufzeichnung in einem Formular für Schnellerfassung speichern, das mit der <strong>openForm</strong>-Methode geöffnet wurde.</li>    
  </ul>
</td>
</tr>
<tr>
<td>errorCallback</td>
<td>Funktion</td>
<td>Nein</td>
<td>Eine auszuführende Funktion, wenn der Vorgang fehlgeschlagen ist.<br>

<b>HINWEIS</b>: In [Einheitliche Schnittstelle](/dynamics365/customer-engagement/admin/about-unified-interface) wird die <b>errorCallback</b>-Funktion nur ausgeführt, wenn Sie das Schnellerfassungsformular öffnen.</td>
</tr>
</table>

## <a name="remarks"></a>Anmerkungen

Sie sollten diese Methode zum Öffnen der Entität oder Schnellerfassungsformulare verwenden anstelle der veralteten[Xrm.Utility.openEntityForm](https://msdn.microsoft.com/library/jj602956.aspx#openEntityForm) [Xrm.Utility.openQuickCreate](https://msdn.microsoft.com/library/jj602956.aspx#openQuickCreate)-Methoden.
 

## <a name="examples"></a>Beispiele

### <a name="example-1-open-an-entity-form-for-existing-record"></a>Beispiel 1: Öffnen Sie ein Entitätsformular für vorhandenen Datensatz

Der folgende Beispielcode öffnet ein Kontaktformular, um einen vorhandenen Kontakt anzuzeigen:

```JavaScript
var entityFormOptions = {};
entityFormOptions["entityName"] = "contact";
entityFormOptions["entityId"] = "8DA6E5B9-88DF-E311-B8E5-6C3BE5A8B200"

// Open the form.
Xrm.Navigation.openForm(entityFormOptions).then(
    function (success) {
        console.log(success);
    },
    function (error) {
        console.log(error);
    });
```

### <a name="example-2-open-an-entity-form-for-new-record"></a>Beispiel 2: Öffnen Sie ein Entitätsformular für neuen Datensatz

Der folgende Beispielcode öffnet ein Formular mit einigen voraufgefüllten Werte, um einen neuen Datensatz zu erstellen:

```JavaScript
var entityFormOptions = {};
entityFormOptions["entityName"] = "contact";

// Set default values for the Contact form
var formParameters = {};
formParameters["firstname"] = "Sample";
formParameters["lastname"] = "Contact";
formParameters["fullname"] = "Sample Contact";
formParameters["emailaddress1"] = "contact@adventure-works.com";
formParameters["jobtitle"] = "Sr. Marketing Manager";
formParameters["donotemail"] = "1";
formParameters["description"] = "Default values for this record were set programmatically.";

// Open the form.
Xrm.Navigation.openForm(entityFormOptions, formParameters).then(
    function (success) {
        console.log(success);
    },
    function (error) {
        console.log(error);
    });
```

### <a name="example-3-open-a-quick-create-form"></a>Beispiel 3: Öffnen Sie das Schnellerfassungsformular

Der folgende Beispielcode öffnet ein Formular mit einigen voraufgefüllten Werte, um einen neuen Datensatz zu erstellen:

```JavaScript
var entityFormOptions = {};
entityFormOptions["entityName"] = "contact";
entityFormOptions["useQuickCreateForm"] = true;

// Set default values for the Contact form
var formParameters = {};
formParameters["firstname"] = "Sample";
formParameters["lastname"] = "Contact";
formParameters["fullname"] = "Sample Contact";
formParameters["emailaddress1"] = "contact@adventure-works.com";
formParameters["jobtitle"] = "Sr. Marketing Manager";
formParameters["donotemail"] = "1";
formParameters["description"] = "Default values for this record were set programmatically.";

// Open the form.
Xrm.Navigation.openForm(entityFormOptions, formParameters).then(
    function (success) {
        console.log(success);
    },
    function (error) {
        console.log(error);
    });
```

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Navigation](../xrm-navigation.md)




