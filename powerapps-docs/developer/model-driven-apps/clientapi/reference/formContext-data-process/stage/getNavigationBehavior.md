---
title: getNavigationBehavior (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 649fe7b0-016d-409f-ba3c-b14e0f1953e0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getnavigationbehavior-client-api-reference"></a>getNavigationBehavior (Client-API-Referenz)



[!INCLUDE[./includes/getNavigationBehavior-description.md](./includes/getNavigationBehavior-description.md)]

> [!NOTE]
> Diese Methode wird nur für [Einheitliche Oberfläche](/dynamics365/get-started/whats-new/customer-engagement/new-in-version-9#unified-interface-framework-for-new-apps) unterstützt. 

## <a name="syntax"></a>Syntax

```
stageObj.getNavigationBehavior().allowCreateNew = function () {
    return true|false;
}
```

## <a name="returns"></a>Gibt zurück

**Typ:**: Objekt. 

**Beschreibung**: Ein Objekt mit der `allowCreateNew`-Eigenschaft, die definiert, ob die Schaltfläche **Erstellen** in einer Phase verfügbar ist, damit Benutzer einer Instanz von entityB im Formular Entität A in einem entitätsübergreifenden Geschäftsprozessfluss-Navigationsszenario erstellen können. 

Beispielsweise ist hier die Schaltfläche **Erstellen** in der **Entwickeln** Phasen des **AccountToContactProcess** Beispielgeschäftsprozessflusses, der Sie einen Kontaktdatensatz im Firmenformular erstellen lässt.

![](../../../../media/clientapi_getNavigationBehavior.png)

Die `allowCreateNew`-Eigenschaft gibt **nicht definiert** für Geschäftsprozessflussdatensätze zurück, die keine entitätsübergreifende Navigation bereitstellen.

## <a name="example"></a>Beispiel

Der folgende Beispielcode zeigt, wie Sie die Schaltfläche **Erstellen** für eine aktive Phase eines Geschäftsprozessflusses abhängig vom Namen ein- oder ausblenden können.

```JavaScript
function sampleFunction(executionContext) {
    var formContext = executionContext.getFormContext();
    formContext.data.process.getActiveStage.getNavigationBehavior().allowCreateNew = function () {
        if (formContext.data.process.getName() === 'Test Process') {
            return false; // Create button is not available
        }
        else {
            return true; // Create button is available
        }
    }
}
```

### <a name="related-topics"></a>Verwandte Themen
 
[formContext.data.process](../../formContext-data-process.md)

