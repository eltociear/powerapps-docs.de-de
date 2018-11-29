---
title: getEnabledProcesses (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 52f79803-2ce0-4ca7-8200-aec544545d62
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getenabledprocesses-client-api-reference"></a>getEnabledProcesses (Client-API-Referenz)



[!INCLUDE[./includes/getEnabledProcesses-description.md](./includes/getEnabledProcesses-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.getEnabledProcesses(callbackFunction(enabledProcesses));`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|callbackFunction|Funktion|Ja|Die Rückruffunktion muss einen Parameter akzeptieren, der ein Objekt mit Wörterbucheigenschaften enthält, in denen der Name der Eigenschaft die ID des Geschäftsprozessflusses ist und der Wert der Eigenschaft der Name des Geschäftsprozessflusses ist.<br/><br/>Die aktivierten Prozesse werden in Übereinstimmung mit den Rechten des Benutzers gefiltert. Die Liste der aktivierten Prozesse ist die gleiche, die ein Benutzer in der Ui sehen kann, wenn er den Prozess manuell ändern möchte.|

## <a name="example"></a>Beispiel

Die Funktion **Sdk.formOnLoad** im Beispiel verwendet die **formContext.data.process.getEnabledProcesses**-Methode, um Informationen zu Geschäftsprozessflüssen, die für die Entität aktiviert sind, asynchron abzurufen. Die Funktion übergibt eine anonyme Funktion als ersten Parameter. Diese Funktion wird asynchron ausgeführt, wenn die Daten zurückgegeben werden und die Daten als Parameter an die anonyme Funktion übergeben werden.

Die Informationen zum aktivierten Geschäftsprozessfluss werden als Wörterbuchobjekt bereitgestellt, in dem die ID des Vorgangs der Name der Eigenschaft und der Name des Geschäftsprozessflusses der Wert der Eigenschaft ist. Der Beispielcode verarbeitet diese Informationen und legt die Werte in einem globalen **Sdk.enabledProcesses**-Array festgelegt, auf das später durch Logik zugegriffen wird, die später ausgeführt wird. Im Beispiel wird auch ein Loop durch die Werte durchgeführt, die im **Sdk.enabledProcesses**-Array verwendet werden, und verwendet die **Sdk.writeToConsole**-Funktion, um Informationen zu Geschäftsprozessflüssen auf die Konsole zu schreiben.

>[!NOTE]
>Die Funktion **Sdk.formOnLoad** in der Beispiel-JavaScript-Bibliothek muss als **OnLoad**-Ereignishandler für ein Formular festgelegt werden, und das Kontrollkästchen **Ausführungskontext als ersten Parameter übergeben** muss im Dialogfeld **Handlereigenschaften** ausgewählt werden.<br/>Dieses Beispiel verdeutlicht auch die Nutzung von einigen der Methoden in der **formContext.data.process** API. Es stellt nicht dar, wie diese API verwendet wird, um eine Geschäftsanforderung zu erfüllen; es soll nur zeigen, wie auf die Schlüsseleigenschaftenwerte im Code zugegriffen werden kann.

```JavaScript
//A namespace defined for SDK sample code
//You should define a unique namespace for your libraries
var Sdk = window.Sdk || {};
(function () {
    //A global variable to store information about enabled business processes after they are retrieved asynchronously
    this.enabledProcesses = [];

    // A function to log messages while debugging only
    this.writeToConsole = function (message) {
        if (typeof console != 'undefined')
        { console.log(message); }
    };

    // Code to run in the OnLoad event 
    this.formOnLoad = function (executionContext) {
        // Retrieve the formContext
        var formContext = executionContext.getFormContext();

        // Retrieve Enabled processes
        formContext.data.process.getEnabledProcesses(function (processes) {
            //Move processes to the global Sdk.enabledProcesses array;
            for (var processId in processes) {
                Sdk.enabledProcesses.push({ id: processId, name: processes[processId] })
            }
            Sdk.writeToConsole("Enabled business processes flows retrieved and added to Sdk.enabledProcesses array.");

            //Write the values of the Sdk.enabledProcesses array to the console
            if (Sdk.enabledProcesses.length < 0) {
                Sdk.writeToConsole("There are no enabled business process flows for this entity.");
            }
            else {
                Sdk.writeToConsole("These are the enabled business process flows for this entity:");
                for (var i = 0; i < Sdk.enabledProcesses.length; i++) {
                    var enabledProcess = Sdk.enabledProcesses[i];
                    Sdk.writeToConsole("id: " + enabledProcess.id + " name: " + enabledProcess.name)
                }
            }

            //Any code that depends on the Sdk.enabledProcesses array needs to be initiated here

        });
    };

}).call(Sdk);
```

Wenn Sie dieses Beispiel mit offenen Browserentwicklertools ausführen, ist Folgendes ein Beispiel der Ausgabe, die auf die Konsole für eine Entität mit mehreren aktivierten Geschäftsprozessflüssen geschrieben wird.

```
Enabled business processes flows retrieved and added to Sdk.enabledProcesses array.
These are the enabled business process flows for this entity:
id: 7994be68-899e-4a40-8d18-f5c3b6940188 name: Sample Lead Process
id: 919e14d1-6489-4852-abd0-a63a6ecaac5d name: Lead to Opportunity Sales Process
```

### <a name="related-topics"></a>Verwandte Themen

[setActiveProcessInstance](setActiveProcessInstance.md)

[formContext.data.process](../formContext-data-process.md)
 


