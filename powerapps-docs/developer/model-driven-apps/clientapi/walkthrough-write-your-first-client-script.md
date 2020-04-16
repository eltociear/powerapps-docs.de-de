---
title: 'Tutorial: Schreiben des ersten Clientskripts in modellgesteuerten Apps | MicrosoftDocs'
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: conceptual
applies_to: Dynamics 365 (online)
ms.assetid: 73dfc13c-a18c-42fc-b511-a37896c2f893
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8eb4dc2079cb274289395c975b4af143bc1ebb1d
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115922"
---
# <a name="walkthrough-write-your-first-client-script"></a>Exemplarische Vorgehensweise: Schreiben des ersten Clientskripts

Bereit für das Schreiben des ersten Clientskripts, um Dinge in Aktion zu sehen. Fangen wir an, wir halten es einfach.

## <a name="objective"></a>Ziel

Nach Durchführung dieser exemplarischen Vorgehensweise wissen Sie, wie Sie Ihren JavaScript-Code in modellgesteuerten Apps verwenden können. Dazu zählen folgende Schritte auf oberster Ebene:

- Schreiben Sie einen JavaScript-Code für einen Geschäftsfall
- Laden Sie Ihren JavaScript-Code als Webressource in modellgesteuerte Apps hoch
- Ordnen Sie die JavaScript-Funktionen in der Webressource verschiedenen clientseitigen Ereignissen in modellgesteuerten Apps zu.

Wir lenken Ihre Aufmerksamkeit auf wichtige Fakten und verweisen gegebenenfalls auf tatsächliche Methoden.

## <a name="step-1-write-your-custom-javascript-code"></a>Schritt : Schreiben des benutzerdefinierten JavaScript-Codes

Der erste Schritt besteht darin, das betriebswirtschaftliche Problem zu ermitteln, dem Sie sich mit dem Clientskript widmen wollen. Nach dem Identifizieren müssen Sie einen JavaScript-Code schreiben, der die angepasste Geschäftslogik enthält, die sich dem Geschäftsproblem widmet. 

Modellgesteuerte Apps bieten keinen JavaScript-Editor. Sie können also ein externes Autorenwerkzeug verwenden, das Funktionen zur Verfügung stellt, die das Bearbeiten von JavaScript-Dateien gezielt unterstützen, wie z.B. [Notepad++](https://notepad-plus-plus.org/), [Visual Studio Code](https://code.visualstudio.com/docs/languages/javascript), oder [Microsoft Visual Studio](https://docs.microsoft.com/scripting/javascript/).

Sie können den gesamten Beispiel-Code dieser exemplarischen Vorgehensweise später einsehen.

Sehen Sie sich den Code detailliert an:
 
### <a name="detailed-code-explanation"></a>Ausführliche Codeerklärung

- **Namespace definieren**: Das Schreiben des Codes beginnt mit der Definition eines Namespaces in Ihrem benutzerdefinierten Skript. Sie sollten immer JavaScript-Bibliotheken mit Namespaces erstellen, damit Ihre Funktionen nicht von Funktionen in einer anderen Bibliothek überschrieben werden.

    ```JavaScript
    var Sdk = window.Sdk || {};
    ``` 
    In diesem Fall können alle in dieser Bibliothek definierten Funktionen als `Sdk.[functionName]` verwendet werden.

- **Globale Variablen definieren**: Der folgende Abschnitt definiert einige globale Variablen, die im Skript verwendet werden. Beachten Sie, dass Sie den Formularkontext nicht durchlaufen müssen, um den Benutzernamen zu erhalten. Die Kontextinformationen sind nun global über die **Xrm.Utility.**[getGlobalContext](reference/xrm-utility/getGlobalContext.md)-Methode verfügbar.

    ```JavaScript
    // Define some global variables
    var myUniqueId = "_myUniqueId"; // Define an ID for the notification
    var currentUserName = Xrm.Utility.getGlobalContext().userSettings.userName; // get current user name
    var message = currentUserName + ": Your JavaScript code in action!";
    ```
- **Code, um OnLoad-Ereignisses ausführen**: Dieser Abschnitt beinhaltet den Code, der ausgeführt wird, wenn das Firmenformular geladen wird. Beispielsweise, wenn Sie einen neuen Firmendatensatz erstellen oder einen vorhandenen Firmendatensatz öffnen.

    Der Code verwendet das `executionContext`-Objekt, um das `formContext`-Objekt zu erhalten. Wenn wir später unseren Code mit einem Formularereignis verknüpfen, müssen wir daran denken, die Option auszuwählen, um den [Ausführungskontext](clientapi-execution-context.md) an diese Funktion zu übergeben. Als Nächstes zeigen wir mit der [setFormNotification](reference/formContext-ui/setFormNotification.md)-Methode eine Benachrichtigung auf Formularebene an. Dann verwenden wird die **setTimeOut**-Methode um die Ausführung der [clearFormNotification](reference/formContext-ui/clearFormNotification.md)-Methode zu verzögern, um die Benachrichtigung nach 5 Sekunden zu löschen.

    ```JavaScript
    // Code to run in the form OnLoad event
    this.formOnLoad = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // display the form level notification as an INFO
        formContext.ui.setFormNotification(message, "INFO", myUniqueId);
        
        // Wait for 5 seconds before clearing the notification
        window.setTimeout(function () { formContext.ui.clearFormNotification(myUniqueId); }, 5000);        
    }
    ```
- **Code zur Ausführung auf dem OnChange-Ereignis**: Der Code in diesem Abschnitt wird dem Feld **Kontoname** im Kontenformular zugeordnet, so dass er **nur** dann ausgeführt wird, wenn Sie den Wert des Kontonamens ändern.

    Der Code führt unter Berücksichtigung der Groß-/Kleinschreibung eine Suche nach "Contoso" im Firmennamen durch, und legt, sofern vorhanden, automatisch Werte für einige Felder im Firmenformular fest.

    ```JavaScript
    // Code to run in the attribute OnChange event 
    this.attributeOnChange = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // Automatically set some field values if the account name contains "Contoso"
        var accountName = formContext.getAttribute("name").getValue();
        if (accountName.toLowerCase().search("contoso") != -1) {
            formContext.getAttribute("websiteurl").setValue("https://www.contoso.com");
            formContext.getAttribute("telephone1").setValue("425-555-0100");
            formContext.getAttribute("description").setValue("Website URL, Phone and Description set using custom script.");
        }
    }
    ```

- **Code, um das OnSave-Ereignis auszuführen**: Der Code in diesem Abschnitt zeigt ein Benachrichtigungs-Dialogfeld über die [openAlertDialog](reference/xrm-navigation/openalertdialog.md)-Methode an. Dieses Dialogfeld enthält eine Meldung mit einer **OK**-Schaltfläche. Es kann durch Klicken auf **OK** geschlossen werden.

    Beachten Sie, dass bei dieser Funktion nicht der Ausführungskontext übergeben wird, da es nicht erforderlich ist, um **Xrm.Utility.***-Methoden auszuführen. 

    ```JavaScript
    // Code to run in the form OnSave event 
    this.formOnSave = function () {
        // Display an alert dialog
        Xrm.Navigation.openAlertDialog({ text: "Record saved." });
    }
    ```

## <a name="step-2-add-your-javascript-code-in-a-script-web-resource"></a>Schritt 2: Hinzufügen des JavaScript-Codes zu einer Skriptwebressource

Nachdem Ihr Code jetzt fertig ist, können Sie diesen Ereignissen in modellgesteuerten Apps zuordnen. Sie verwenden [Skriptwebressourcen](../script-jscript-web-resources.md) in modellgesteuerten Apps, um das Skript in Ihre Instanz für modellgesteuerte Apps hochzuladen und anschließend mit Ereignissen zu verknüpfen.

1. Navigieren Sie im Browser zu Ihrer Instanz für modellgesteuerte Apps, und wechseln Sie zu **Einstellungen** > **Anpassungen**.
2. Klicken Sie im Bereich Anpassung auf **Anpassen des Systems**.
3. Klicken Sie im Projektmappen-Explorer auf **Komponenten**, und wählen Sie **Webressourcen** aus.  
4. Wählen Sie **Neu**, um eine Webressource zu erstellen.
5. Geben Sie im Dialogfeld für die Webressource **Name** und **Anzeigename** ein. Beispiel: "mySampleScript.js "und "Beispiel: Exemplarische Vorgehensweise"-Skript. 
6. Wählen Sie **Script (JScript)** aus der Dropdownliste **Typ** aus. Sie können entweder eine Datei hochladen, die den JavaScript-Code enthält, indem Sie **Datei auswählen** oder indem Sie **Text-Editor** auswählen und anschließend den JavaScript-Code in den Editor einfügen.
    ![Erstellen einer Webressource](../media/clientapi_walkThrough-img1.png)
1. Wählen Sie **Speichern** aus, um die Webressource zu erstellen, die Ihren JavaScript-Code enthält.
2. Wählen Sie **Veröffentlichen**, um die Webressource zu veröffentlichen.

## <a name="step-3-associate-script-web-resource-to-a-form"></a>Schritt 3: Zuordnen der Skriptwebressource zu einem Formular

Ordnen Sie die Webressource, die Ihren JavaScript-Code enthält, Formularen für modellgesteuerte Apps zu, um Funktionen in Ihrem Code Ereignissen zuzuordnen. Da der JavaScript-Code in dieser Vorgehensweise auf den Firmendatensatz ausgerichtet ist, ordnen wir die Webressource dem Firmenformular zu.

1. Navigieren Sie zu Ihrer Instanz für modellgesteuerte Apps im Browser, und wechseln Sie zu **Vertrieb** > **Firmen** oder **Dienst** > **Firmen**.
2. Öffnen Sie einen Firmendatensatz, und wählen Sie zum Öffnen des Formular-Editors **Formular** aus.

    ![Öffnen des Formulareditors](../media/clientapi_walkThrough-img2.png)
1. Wählen Sie im Formular-Editor **Formulareigenschaften** aus.
2. Klicken Sie im Dialogfeld **Formulareigenschaften** auf der Registerkarte **Ereignisse** auf **Hinzufügen**, um der Webressource zu suchen und hinzuzufügen.

    ![Hinzufügen](../media/clientapi_walkThrough-img3.png)
1. In folgenden Dialogfeld suchen Sie nach dem Webressourcennamen, wählen diesen aus, und klicken auf **Hinzufügen**, um ihn als JavaScript-Bibliothek für das Firmenformular hinzufügen.

    ![Suchdatensatz](../media/clientapi_walkThrough-img4.png)

Dadurch steht die Webressource zur Verfügung, die unter dem Abschnitt **Ereignishandler** im Dialog **Formulareigenschaften** ausgewählt werden kann. Denken Sie daran, dass wir drei Funktionen in unserem JavaScript-Code haben, die mit entsprechenden Ereignissen im Formular verknüpft sind.

1. Wählen Sie im Abschnitt **Ereignishandler** **Formular** als das Steuerelement aus und **OnLoad** als **Ereignis**; klicken Sie auf **Hinzufügen**, um einen Ereignishandler für das OnLoad-Ereignis hinzuzufügen.

   ![Formular OnLoad](../media/clientapi_walkThrough-img5.png)
1. Im Dialogfeld **Handlereigenschaften**:   

    - Wählen Sie den Namen der Webressource in der Dropdownliste **Bibliothek** aus, und geben Sie **Sdk.formOnLoad** in das Feld **Funktion** ein. Der Funktionsname lautet [Namespace].[Funktion] vom JavaScript-Code.
    - Klicken Sie auf **Ausführungskontext als ersten Parameter übergeben**, um den Ausführungskontext als Parameter an diese Funktion zu übergeben. Wenn Sie die Funktionsdefinition im Code überprüfen, übergeben wir ein **executionContext**-Objekt an unsere Funktionsdefinition. Durch Auswahl der Option erfolgt eine Verknüpfung.
    
      ![Formular OnLoad](../media/clientapi_walkThrough-img6.png)

1. Klicken Sie auf **OK**, um zum Dialogfeld **Formulareigenschaften** zurückzukehren.
2. Wählen Sie diesmal im Abschnitt **Ereignishandler** **OnSave** als **Ereignis** aus, und klicken Sie auf **Hinzufügen**, um den Ereignishandler für das OnSave-Ereignis hinzuzufügen.

    ![OnSave-Formular](../media/clientapi_walkThrough-img7.png)

1. Wählen Sie im Dialogfeld **Handlereigenschaften** den Namen der Webressource in der Dropdownliste **Bibliothek** aus, und geben Sie **Sdk.formOnSave** im Feld **Funktion** an. Wir übergeben diesmal nicht den Ausführungskontext an die Funktion, da dies für den **Sdk.formOnSave**-Funktionscode nicht erforderlich ist.

    ![OnSave-Formular](../media/clientapi_walkThrough-img8.png)

1. Klicken Sie auf **OK**, um zum Dialogfeld **Formulareigenschaften** zurückzukehren.
2. Wählen Sie im Abschnitt **Ereignishandler** **Firmenname** als das Steuerelement aus und **OnChange** als Ereignis; klicken Sie auf **Hinzufügen**, um einen Ereignishandler für das OnChange-Ereignis hinzuzufügen.

    ![OnSave-Formular](../media/clientapi_walkThrough-img9.png)

1. Im Dialogfeld **Handlereigenschaften**:   

    - Wählen Sie den Namen der Webressource in der Dropdownliste **Bibliothek** aus, und geben Sie **Sdk.attributeOnChange** in das Feld **Funktion** ein.
    - Klicken Sie auf **Ausführungskontext als ersten Parameter übergeben**, um den Ausführungskontext als Parameter an diese Funktion zu übergeben. Wenn Sie die Funktionsdefinition im Code überprüfen, übergeben wir ein **executionContext**-Objekt an unsere Funktionsdefinition. Durch Auswahl der Option erfolgt eine Verknüpfung.
    
      ![OnChange-Attribut](../media/clientapi_walkThrough-img10.png) 
1. Klicken Sie auf **OK**, um zum Dialogfeld **Formulareigenschaften** zurückzukehren.
2. Klicken Sie auf **OK** im Dialogfenster **Formulareigenschaften**, um zum Formular-Editor zurückzukehren.
3. Klicken Sie auf **Save**, um die Änderungen im Formular zu speichern.
4. Klicken Sie auf **Veröffentlichen**, um die Formular-Änderungen zu veröffentlichen.

Das war es! Sie haben die Schritte abgeschlossen, die erforderlich waren, um das Firmenformular so zu konfigurieren, dass die angepasste Geschäftslogik aus Ihrem JavaScript-Code verwendet wird.

## <a name="test-your-javascript-code"></a>Testen des JavaScript-Codes

Es wird empfohlen, dass Sie Ihren Browser aktualisieren, damit die Änderungen in Instanz für modellgesteuerte Apps wirksam werden. So testen Sie die benutzerdefinierte Geschäftslogik, die Sie in dieser exemplarischen Vorgehensweise konfiguriert haben:

1. Melden Sie sich bei Ihrer Instanz für modellgesteuerte Apps an.
2. Navigieren Sie zu **Firmen**, und versuchen Sie , eine neue Firma zu erstellen. In diesem Fall öffnen wir eine vorhandene Firma, um das Firmenformular zu laden. Sie sehen eine Benachrichtigung mit Ihrem Benutzernamen, die in 5 Sekunden automatisch verschwindet.

      ![Benachrichtigung auf Formularebene](../media/clientapi_walkThrough-img11.png)

1. Bearbeiten Sie den Firmennamen, um "Contoso" als Namen hinzuzufügen, und wechseln Sie über die Tabulatortaste zum nächsten Feld. Dadurch wird das OnChange-Ereignis ausgelöst und die Felder **Telefon**, **Website** und **Beschreibung** mit dem im Code angegebenen Wert automatisch aktualisiert.

      ![Automatisch festgelegte Werte](../media/clientapi_walkThrough-img12.png)

1. Klicken Sie abschließend auf **Speichern**. Dadurch wird das OnSave-Ereignis ausgelöst und ein Benachrichtigungs-Dialogfeld anzeigt, das eine Benachrichtigung enthält, die Sie im Code konfiguriert haben. Klicken Sie auf **OK**, um die Benachrichtigung zu schließen.

      ![Dialog für Benachrichtigung](../media/clientapi_walkThrough-img13.png)

## <a name="complete-sample-code-used-in-the-walkthrough"></a>Vollständiger Beispielcode dieser exemplarischen Vorgehensweise

```JavaScript
// A namespace defined for the sample code
// As a best practice, you should always define 
// a unique namespace for your libraries
var Sdk = window.Sdk || {};
(function () {
    // Define some global variables
    var myUniqueId = "_myUniqueId"; // Define an ID for the notification
    var currentUserName = Xrm.Utility.getGlobalContext().userSettings.userName; // get current user name
    var message = currentUserName + ": Your JavaScript code in action!";

    // Code to run in the form OnLoad event
    this.formOnLoad = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // display the form level notification as an INFO
        formContext.ui.setFormNotification(message, "INFO", myUniqueId);

        // Wait for 5 seconds before clearing the notification
        window.setTimeout(function () { formContext.ui.clearFormNotification(myUniqueId); }, 5000);
    }

    // Code to run in the attribute OnChange event 
    this.attributeOnChange = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // Automatically set some field values if the account name contains "Contoso"
        var accountName = formContext.getAttribute("name").getValue();
        if (accountName.toLowerCase().search("contoso") != -1) {
            formContext.getAttribute("websiteurl").setValue("https://www.contoso.com");
            formContext.getAttribute("telephone1").setValue("425-555-0100");
            formContext.getAttribute("description").setValue("Website URL, Phone and Description set using custom script.");
        }
    }

    // Code to run in the form OnSave event 
    this.formOnSave = function () {
        // Display an alert dialog
        Xrm.Navigation.openAlertDialog({ text: "Record saved." });
    }
}).call(Sdk);
```
