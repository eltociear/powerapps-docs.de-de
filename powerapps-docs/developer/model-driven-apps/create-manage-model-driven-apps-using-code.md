---
title: Erstellen, Verwalten und Veröffentlichen von modellgesteuerten Apps mithilfe von Code | Microsoft Docs
description: Erfahren Sie, wie Sie modellgesteuerte Apps mit Code in Power Apps erstellen, verwalten und veröffentlichen.
keywords: ''
ms.date: 03/04/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 4261c476-2eff-10e3-a334-d02e0cbbb9d5
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 80c604cf7595d64a946fab9faf186339d732eb5e
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115662"
---
# <a name="create-manage-and-publish-model-driven-apps-using-code"></a>Erstellen, Verwalten und Veröffentlichen von modellgesteuerten Apps mithilfe von Code

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/create-manage-custom-business-apps-using-code -->

Zusätzlich zur Erstellung einer modellgesteuerten App mit dem Power Apps App Designer können Sie modellgesteuerte Apps programmgesteuert erstellen und verwalten. 

> [!IMPORTANT]
> Sie müssen keinen Code schreiben, um modellgesteuerte Apps zu erstellen, wenn es nicht nötig ist! Der App-Designer bietet eine viel einfachere und intuitivere Funktionalität zum Erstellen von modellgesteuerten Apps, ohne dass Code geschrieben werden muss, indem er eine kachelbasierte Informationsstruktur und eine vereinfachte Benutzeroberfläche bereitstellt. Sehen Sie hier: [Gestalten Sie modellgesteuerte Apps mit dem App-Designer](../../maker/model-driven-apps/design-custom-business-apps-using-app-designer.md)  
  
Das Erstellen einer modellgesteuerten App umfasst die folgenden Schritte:
1. Erstellen einer [AppModule-Entität](../common-data-service/reference/entities/appmodule.md)-Instanz, um die App und ihre Eigenschaften zu definieren.
2. Hinzufügen oder Entfernen von Komponenten zur App, wie Entität, Siteübersicht und andere Komponenten für die benutzerdefinierte App mit <xref:Microsoft.Dynamics.CRM.AddAppComponents> und <xref:Microsoft.Dynamics.CRM.RemoveAppComponents>-Aktionen.
3. Überprüfen Sie die App auf alle fehlenden erforderlichen Komponenten mithilfe der Funktion <xref:Microsoft.Dynamics.CRM.ValidateApp>.
4. Veröffentlichen der App.
5. Ordnen Sie die entsprechenden Sicherheitsrollen der modellgesteuerten App zu, um den Zugriff für Benutzer zu ermöglichen.


## <a name="create-your-model-driven-app-and-define-its-properties"></a>Erstellen Sie die modellgesteuerte App und definieren Sie deren Eigenschaften

Sie müssen über die Sicherheitsrolle „Systemadministrator“ oder „Systemanpasser“ bzw. entsprechende Berechtigungen verfügen, um eine App zu erstellen. 

Sie müssen mindestens die folgenden Eigenschaften angeben, um eine App zu erstellen:
- **Name**: Eindeutig für die App
- **uniquename**: Dies kann anders als Name der App sein und darf nur englische Zeichen und nur Zahlen enthalten. Bei Erstellung dieser App wird automatisch der Name mit dem Lösungsherausgeberpräfix verwendet (beispielsweise 'new_'). 
- **webresourceid**: ID der Webressource, die als Bildsymbol für die App festgelegt werden soll. Das System bietet eine Standardwebressource (ID: 953b9fac-1e5e-e611-80d6-00155ded156f), die Sie als Symbol für die App verwenden können.

Die folgende Internet-API-Anforderung erstellt einen App-Typ einheitliche Schnittstelle:

```http
POST [Organization URI]/api/data/v9.0/appmodules HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
    "name": "SDKTestApp",
    "uniquename":"SDKTestApp",
    "webresourceid":"953b9fac-1e5e-e611-80d6-00155ded156f"    
}
```

Der **OData-EntityId**-Antwortheader enthält die URI der erstellten App.

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/appmodules(dd621d4a-d898-e711-80e7-00155db763be)
```  

## <a name="add-or-remove-components-from-your-model-driven-app"></a>Hinzufügen oder Entfernen von Komponenten der modellgesteuerten App

Sie können Komponenten in einer App hinzufügen oder entfernen, wie Siteübersicht, Entität, Dashboard, Geschäftsprozessflüsse, Ansichten und Formulare, die in die modellgesteuerte App eingeschlossen werden sollen. Ausführliche Informationen zu Komponenten, die einer modellgesteuerten App hinzugefügt werden können, finden Sie unter [Hinzufügen oder Bearbeiten von App-Komponenten im App-Designer](../../maker/model-driven-apps/add-edit-app-components.md).

Verwenden Sie die <xref:Microsoft.Dynamics.CRM.AddAppComponents>-Aktion oder die <xref:Microsoft.Crm.Sdk.Messages.AddAppComponentsRequest>-Meldung, um Komponenten der modellgesteuerten App hinzuzufügen. Für die Aktion müssen Sie Folgendes angeben:
- **AppId**: ID der App, der Sie Komponenten hinzufügen möchten
- **Komponenten** Eine Sammlung von Komponenten, die hinzugefügt werden sollen. Sie müssen die ID sowie den Entitätstyp der Komponente angeben, die Sie hinzufügen möchten. Eine Liste der Entitätstypen in Common Data Service-Web-API finden Sie unter <xref:Microsoft.Dynamics.CRM.EntityTypeIndex>.

Die folgende Internet-API-Anforderung fügt der App eine Ansicht (savedquery) und ein Formular (systemform) hinzu:

```http
POST [Organization URI]/api/data/v9.0/AddAppComponents HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
    "AppId":"dd621d4a-d898-e711-80e7-00155db763be",
    "Components":[
        {
            "savedqueryid":"00000000-0000-0000-00aa-000000666000",
            "@odata.type":"Microsoft.Dynamics.CRM.savedquery"
        },
        {
            "formid":"c9e7ec2d-efca-4e4c-b3e3-f63c4bba5e4b",
            "@odata.type":"Microsoft.Dynamics.CRM.systemform"
        }
    ]
}
```

Um eine Komponente einer App zu entfernen, können Sie die Aktion <xref:Microsoft.Dynamics.CRM.RemoveAppComponents> oder die <xref:Microsoft.Crm.Sdk.Messages.RemoveAppComponentsRequest>-Nachricht verwenden. Diese Aktion verwendet denselben Satz von Parametern wie die Aktion **AddAppComponents**.

Die folgende Internet-API-Anforderung entfernt eine Ansicht (savedquery) von der App: 

```http
POST [Organization URI]/api/data/v9.0/RemoveAppComponents HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
    "AppId":"dd621d4a-d898-e711-80e7-00155db763be",
    "Components":[
        {
            "savedqueryid":"00000000-0000-0000-00aa-000000666000",
            "@odata.type":"Microsoft.Dynamics.CRM.savedquery"
        }
    ]
}
```

## <a name="validate-your-model-driven-app"></a>Validieren Sie Ihre modellgesteuerte Anwendung

Das Validieren einer App umfasst das Überprüfen der Abhängigkeiten für die Komponenten, die Sie in der modellgesteuerten App hinzugefügt haben, um sicherzustellen, dass die App adäquat funktioniert. Dies ist das Gleiche wie **Überprüfen** im App-Designer. Weitere Informationen: [Überprüfen der App](../../maker/model-driven-apps/validate-app.md)

Verwenden Sie die <xref:Microsoft.Dynamics.CRM.ValidateApp>-Funktionen oder die <xref:Microsoft.Crm.Sdk.Messages.ValidateAppRequest>-Meldung, um die App zu überprüfen. Die folgende Web-API-Anforderung zeigt, wie die modellgesteuerte App mit der ID: dd621d4a-d898-e711-80e7-00155db763be überprüft wird:

`GET [Organization URI]/api/data/v9.0/ValidateApp(AppModuleId=dd621d4a-d898-e711-80e7-00155db763be)`

Wenn es keine Überprüfungsfehler gibt, ist die Antwort wie folgt:

```http
HTTP/1.1 200 OK
OData-Version: 4.0

{
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.ValidateAppResponse",
    "AppValidationResponse": {
        "ValidationSuccess": true,
        "ValidationIssueList": []
    }
}
```

Falls es Überprüfungsprobleme in der App gibt, werden in der Antwort Fehler/Warnungen in der **ValidationIssueList** angezeigt:

```http
HTTP/1.1 200 OK
OData-Version: 4.0

{
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.ValidateAppResponse",
    "AppValidationResponse": {
        "ValidationSuccess": false,
        "ValidationIssueList": [
            {
                "ErrorType": "Error",
                "Message": "App does not contain Site Map",
                "DisplayName": null,
                "ComponentId": "00000000-0000-0000-0000-000000000000",
                "ComponentType": 0,
                "ComponentSubType": 0,
                "ParentEntityId": "00000000-0000-0000-0000-000000000000",
                "ParentEntityName": null,
                "CRMErrorCode": -2147155684,
                "RequiredComponents": []
            },
            {
                "ErrorType": "Warning",
                "Message": "Account doesn’t reference a form or view. App users will see all forms and views.",
                "DisplayName": null,
                "ComponentId": "00000000-0000-0000-0000-000000000000",
                "ComponentType": 0,
                "ComponentSubType": 0,
                "ParentEntityId": "00000000-0000-0000-0000-000000000000",
                "ParentEntityName": null,
                "CRMErrorCode": -2147155691,
                "RequiredComponents": []
            }
        ]
    }
}
```

## <a name="publish-your-model-driven-app"></a>Veröffentlichen Ihrer modellgesteuerten Anwendung

Nachdem Sie erforderlichen Komponenten zu Ihrer modellgesteuerten App hinzugefügt bzw. sie überprüft haben, müssen Sie diese veröffentlichen, um sie Benutzern zur Verfügung zu stellen.

Mithilfe der <xref:Microsoft.Dynamics.CRM.PublishXml>-Aktion, oder der <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest>-Mitteilung veröffentlichen Sie die modellgesteuerte App. Die folgende Anforderung zeigt, wie die modellgesteuerte App mit der ID: dd621d4a-d898-e711-80e7-00155db763be veröffentlicht wird:

```http
POST [Organization URI]/api/data/v9.0/PublishXml HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{  
  "ParameterXml":"<importexportxml><appmodules><appmodule>dd621d4a-d898-e711-80e7-00155db763be</appmodule></appmodules></importexportxml>"
}
```

## <a name="manage-access-to-model-driven-app-using-security-roles"></a>Verwalten des Zugriffs auf modellgetriebene Anwendungen mithilfe von Sicherheitsrollen

Um Benutzern Zugriff auf Ihre Apps bereitzustellen, damit diese darauf aus ihrem Bereich **Einstellungen** > **Meine Apps** oder der Dynamics 365-Startseite zugreifen können, können Sie den modellgesteuerten Apps Sicherheitsrollen hinzufügen. Benutzer, die den zugeordneten Sicherheitsrollen zugewiesen sind, können Ihre modellgesteuerten Apps in Common Data Service anzeigen und verwenden. 

Verwenden Sie die **appmoduleroles_association**-Navigationseigenschaft der [AppModule-Entität](../common-data-service/reference/entities/appmodule.md)-Entität, um eine modellgesteuerte App zu einer Sicherheitsrolle zuzuordnen. Die folgende Anforderung veranschaulicht, wie Sie eine modellgesteuerte App einer Sicherheitsrolle zuordnen:

```http
POST [Organization URI]/api/data/v9.0/appmodules(dd621d4a-d898-e711-80e7-00155db763be)appmoduleroles_association/$ref HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{  
  "@odata.id":"[Organization URI]/api/data/v9.0/roles(<roleId>)"
}
```

Um die Zuordnung einer Sicherheitsrolle aus einer modellgesteuerte App zu entfernen, verwenden Sie die DELETE-Anforderung mit derselben Navigationseigenschaft. Beispiel:

```
DELETE  [Organization URI]/api/data/v9.0/appmodules(dd621d4a-d898-e711-80e7-00155db763be)/appmoduleroles_association/$ref?$id=[Organization URI]/api/data/v9.0/roles(<roleId)
```

## <a name="manage-your-model-driven-apps-and-its-components"></a>Verwalten Ihrer modellgesteuerten Apps und deren Komponenten

Dieser Abschnitt bietet Informationen zum Abrufen der Apps, Aktualisieren von App-Eigenschaften, das Abrufen von Apps-Komponenten und zum Löschvorgang von Apps.

### <a name="retrieve-published-apps"></a>Veröffentlichte Apps abrufen
Um veröffentlichte Apps abzurufen, können Sie die folgenden Anforderungen verwenden:

`GET [Organization URI]/api/data/v9.0/appmodules?$select=name,clienttype`

### <a name="retrieve-unpublished-apps"></a>Unveröffentlichte Apps abrufen
Zum Abrufen unveröffentlichter Apps verwenden Sie die <xref:Microsoft.Dynamics.CRM.RetrieveUnpublishedMultiple>-Funktion. Beispiel:

`GET [Organization URI]/api/data/v9.0/appmodules/Microsoft.Dynamics.CRM.RetrieveUnpublishedMultiple()?$select=name,clienttype`

### <a name="retrieve-components-in-a-published-model-driven-app"></a>Abrufen von Komponenten in einer veröffentlichten modellgesteuerten App
Um App-Komponenten für eine modellgesteuerte App abzurufen, verwenden Sie die <xref:Microsoft.Dynamics.CRM.RetrieveAppComponents>-Funktion oder die <xref:Microsoft.Crm.Sdk.Messages.RetrieveAppComponentsRequest>-Message. Beispiel:

`GET [Organization URI]/api/data/v9.0/RetrieveAppComponents(AppModuleId=dd621d4a-d898-e711-80e7-00155db763be)`

### <a name="retrieve-security-roles-associated-with-published-model-driven-app"></a>Rufen Sie Sicherheitsrollen ab, die einer veröffentlichten modellgesteuerten App zugeordnet sind

Um die Sicherheitsrollen abzurufen, die der modellgesteuerten App zugeordnet sind, können die `$expand` Systemabfrageoption mit der **appmoduleroles_association**-Navigationseigenschaft verwenden. Beispielsweise ist hier die Anforderung, alle Sicherheitsrollen anzuzeigen, die der modellgesteuerten App mit der ID: dd621d4a-d898-e711-80e7-00155db763be zugeordnet sind:

`GET [Organization URI]/api/data/v9.0/appmodules(dd621d4a-d898-e711-80e7-00155db763be)?$expand=appmoduleroles_association&$select=name,appmoduleroles_association`

### <a name="delete-model-driven-apps"></a>Löschen von modellgesteuerten Apps

Verwenden Sie die DELETE-Anforderung, um eine modellgesteuerte App zu löschen. Beispiel:

`DELETE [Organization URI]/api/data/v9.0/appmodules(dd621d4a-d898-e711-80e7-00155db763be)`

## <a name="client-api-support-for-model-driven-apps"></a>Client-API-Unterstützung für modellgesteuerte Apps

Sie können die folgenden Client-APIs verwenden, um mit modellgesteuerten Apps zu arbeiten:

- [getCurrentAppName](clientapi/reference/xrm-utility/getglobalcontext/getcurrentappname.md)
- [getCurrentAppProperties](clientapi/reference/xrm-utility/getglobalcontext/getCurrentAppProperties.md)
- [getCurrentAppUrl](clientapi/reference/xrm-utility/getglobalcontext/getCurrentAppUrl.md) 
  
### <a name="see-also"></a>Siehe auch  
[Gestalten Sie modellgesteuerte Apps mit dem App Designer](../../maker/model-driven-apps/design-custom-business-apps-using-app-designer.md)
 
