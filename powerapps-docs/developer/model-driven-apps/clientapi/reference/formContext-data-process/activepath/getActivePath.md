---
title: getActivePath (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4916df68-b2d4-4a0b-b341-eb9f7032bc20
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getactivepath-client-api-reference"></a>getActivePath (Client-API-Referenz)



[!INCLUDE[./includes/getActivePath-description.md](./includes/getActivePath-description.md)]

Der aktive Pfad stellt die Phasen dar, die aktuell in der Prozesssteuerung anhand der Verzweigungsregeln und den aktuellen Daten im Datensatz gerendert werden.

## <a name="syntax"></a>Syntax

`var stageCollection = formContext.data.process.getActivePath();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Sammlung. 

**Beschreibung**: Eine Sammlung aller abgeschlossenen Phasen, die derzeit aktive Phase und der vorausgesagte Satz der zukünftigen Phasen anhand der erfüllten Bedingungen in der Verzweigungsregel. Dies ist kann eine Teilmenge der Phasen sein, die mit **formContext.data.process**.[getActiveProcess](../activeprocess/getActiveProcess.md) zurückgegeben werden, da es nur die Phasen enthält, die einen gültigen Übergang von der aktuellen Phase darstellt, basierend auf der Verzweigung, die im Prozess aufgetreten ist.

## <a name="example"></a>Beispiel

Die Sdk.formOnLoad-Funktion verwendet die **formContext.data.process.getActivePath**-Methode, um eine Sammlung von Phasen zu erhalten. Dann verwendet der Beispielcode die [forEach](../../collections/forEach.md)-Methode der Sammlung, um jede Phase als Schleife zu durchlaufen. Der Code schreibt anschließend die Schlüsseleigenschaftender der Phase mit der **Sdk.writeToConsole**-Funktion, die in dieser Bibliothek definiert wird. Der Code kann dann auf eine Sammlung von Schritten für jede Phase mithilfe der [getSteps](../stage/getSteps.md)-Methode zugreifen. Zuletzt verwendet das Beispiel die [forEach](../../collections/forEach.md)-Methode der Schrittsammlung, um auf die einzelnen Schritte zuzugreifen und Schlüsseleigenschaften des Schritts auf die Konsole zu schreiben.

>[!NOTE]
>Die Funktion **Sdk.formOnLoad** in der Beispiel-JavaScript-Bibliothek muss als **OnLoad**-Ereignishandler für ein Formular festgelegt werden, und das Kontrollkästchen **Ausführungskontext als ersten Parameter übergeben** muss im Dialogfeld **Handlereigenschaften** ausgewählt werden.<br/>Dieses Beispiel verdeutlicht auch die Nutzung von einigen der Methoden in der **formContext.data.process** API. Es stellt nicht dar, wie diese API verwendet wird, um eine Geschäftsanforderung zu erfüllen; es soll nur zeigen, wie auf die Schlüsseleigenschaftenwerte im Code zugegriffen werden kann.

```JavaScript
// A namespace defined for SDK sample code
// You should define a unique namespace for your libraries
var Sdk = window.Sdk || {};
(function () {

    // A function to log messages while debugging only
    this.writeToConsole = function (message) {
        if (typeof console != 'undefined')
        { console.log(message); }
    };

    // Code to run in the OnLoad event 
    this.formOnLoad = function (executionContext) {
        // Retrieve the formContext
        var formContext = executionContext.getFormContext();

        // Enumerate the stages and steps in the active path
        var activePathCollection = formContext.data.process.getActivePath();
        activePathCollection.forEach(function (stage, n) {
            Sdk.writeToConsole("Stage Index: " + n);
            Sdk.writeToConsole("Entity: " + stage.getEntityName());
            Sdk.writeToConsole("StageId: " + stage.getId());
            Sdk.writeToConsole("Status: " + stage.getStatus());
            var stageSteps = stage.getSteps();
            stageSteps.forEach(function (step, i) {
                Sdk.writeToConsole("    Step Name: " + step.getName());
                Sdk.writeToConsole("    Step Attribute: " + step.getAttribute());
                Sdk.writeToConsole("    Step Required: " + step.isRequired());
                Sdk.writeToConsole("    ---------------------------------------")
            })
            Sdk.writeToConsole("---------------------------------------")
        });
    };
}).call(Sdk);
```

Wenn das Beispiel im Browsern ausgeführt wird, können Sie die Entwicklertools des Browsers verwenden, um den Text anzuzeigen, der auf die Konsole geschrieben wird. Angenommen, dieses Beispiel wird im Verkaufschancen-Entitätsformular mit dem Verkaufschancen-Vertriebsprozess ausgeführt, wird Folgendes auf die Konsole geschrieben:

```
Stage Index: 0
Entity: opportunity
StageId: 6b9ce798-221a-4260-90b2-2a95ed51a5bc
Status: active
    Step Name: Identify Contact
    Step Attribute: parentcontactid
    Step Required: false
    ---------------------------------------
    Step Name: Identify Account
    Step Attribute: parentaccountid
    Step Required: false
    ---------------------------------------
    Step Name: Purchase Timeframe
    Step Attribute: purchasetimeframe
    Step Required: false
    ---------------------------------------
    Step Name: Estimated Budget
    Step Attribute: budgetamount
    Step Required: false
    ---------------------------------------
    Step Name: Purchase Process
    Step Attribute: purchaseprocess
    Step Required: false
    ---------------------------------------
    Step Name: Identify Decision Maker
    Step Attribute: decisionmaker
    Step Required: false
    ---------------------------------------
    Step Name: Capture Summary
    Step Attribute: description
    Step Required: false
    ---------------------------------------
---------------------------------------
Stage Index: 1
Entity: opportunity
StageId: 650e06b4-789b-46c1-822b-0da76bedb1ed
Status: inactive
    Step Name: Customer Need
    Step Attribute: customerneed
    Step Required: false
    ---------------------------------------
    Step Name: Proposed Solution
    Step Attribute: proposedsolution
    Step Required: false
    ---------------------------------------
    Step Name: Identify Stakeholders
    Step Attribute: identifycustomercontacts
    Step Required: false
    ---------------------------------------
    Step Name: Identify Competitors
    Step Attribute: identifycompetitors
    Step Required: false
    ---------------------------------------
---------------------------------------
Stage Index: 2
Entity: opportunity
StageId: d3ca8878-8d7b-47b9-852d-fcd838790cfd
Status: inactive
    Step Name: Identify Sales Team
    Step Attribute: identifypursuitteam
    Step Required: false
    ---------------------------------------
    Step Name: Develop Proposal
    Step Attribute: developproposal
    Step Required: false
    ---------------------------------------
    Step Name: Complete Internal Review
    Step Attribute: completeinternalreview
    Step Required: false
    ---------------------------------------
    Step Name: Present Proposal
    Step Attribute: presentproposal
    Step Required: false
    ---------------------------------------
---------------------------------------
Stage Index: 3
Entity: opportunity
StageId: bb7e830a-61bd-441b-b1fd-6bb104ffa027
Status: inactive
    Step Name: Complete Final Proposal
    Step Attribute: completefinalproposal
    Step Required: false
    ---------------------------------------
    Step Name: Present Final Proposal
    Step Attribute: presentfinalproposal
    Step Required: false
    ---------------------------------------
    Step Name: Confirm Decision Date
    Step Attribute: finaldecisiondate
    Step Required: false
    ---------------------------------------
    Step Name: Send Thank You
    Step Attribute: sendthankyounote
    Step Required: false
    ---------------------------------------
    Step Name: File De-brief
    Step Attribute: filedebrief
    Step Required: false
    ---------------------------------------
---------------------------------------
```

### <a name="related-topics"></a>Verwandte Themen

[formContext.data.process](../../formContext-data-process.md)
 


