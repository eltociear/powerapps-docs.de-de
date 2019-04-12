---
title: Webhooks zum Erstellen externer Handler für Serverereignisse verwenden (Common Data Service) | Microsoft Docs
description: 'Sie können Daten zu Ereignissen senden, die auf dem Server für eine Webanwendung mit Webhooks auftreten. Webhooks ist ein einfaches HTTP-Muster zur Verbindung von Web-APIs und -diensten mit einem Veröffentlichungs-/Abonnementmodell. Webhooks-Absender benachrichtigen Empfänger über Ereignisse, indem sie Anfragen mit einigen Informationen zu den Ereignissen an Empfängerendpunkte senden.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-webhooks-to-create-external-handlers-for-server-events"></a>Verwenden Sie Webhooks zum Erstellen externer Handler für Serverereignisse

Mit Common Data Service können Sie mithilfe von Webhooks Daten zu Ereignissen senden, die auf dem Server bei einer Webanwendung auftreten. Webhooks ist ein einfaches HTTP-Muster zur Verbindung von Web-APIs und -diensten mit einem Veröffentlichungs-/Abonnementmodell. Webhook-Absender benachrichtigen Empfänger über Ereignisse, indem sie Anfragen mit einigen Informationen zu den Ereignissen an Empfängerendpunkte senden.

Mit Webhooks können Entwickler und ISVs Daten aus dem Customer Engagement in Ihren eigenen benutzerdefinierten Code integrieren, der von externen Diensten gehostet wird. Mit dem Webhook-Modell können Sie Ihren Endpunkt sichern, indem Sie einen Authentifizierungsheader oder Abfrage-Zeichenfolgenparameterschlüssel verwenden. Dies ist einfacher als das SAS-Authentifizierungsmodell, das Sie derzeit möglicherweise für die Azure Service Bus-Integration verwenden.

Beim Entscheiden zwischen dem Webhook-Modell und der Azure Service Bus-Integration sollten Sie Folgendes berücksichtigen:

- Azure Service Bus eignet sich für die hochskalierte Verarbeitung und bietet einen vollständigen Abfragemechanismus, wenn Common Data Service viele Ereignisse weiterleitet.
- Webhooks können nur soweit skaliert werden, wie ihr gehosteter Webdienst Nachrichten verarbeiten kann.
- Webhooks unterstützen synchrone und asynchronen Schritte. Azure Service Bus lässt nur asynchrone Schritte zu.
- Webhooks senden POST-Anforderungen mit JSON-Nutzlast und können von allen Programmiersprachen oder Webanwendungen an jedem beliebigen Ort konsumiert werden.
- Webhooks und Azure Service Bus können von einem Plug-In oder einer benutzerdefinierten Workflowaktivität aufgerufen werden.


## <a name="get-started"></a>Erste Schritte

Die Anwendung von Webhooks gliedert sich in drei Teile:

- Erstellen oder Konfigurieren eines Services zum Konsumieren von Webhook-Anforderungen.
- Schritt zum Registrieren eines Webhooks im Common Data Service oder
- Aufrufen des Webhooks von einem Plug-In oder einer benutzerdefinierten Workflowaktivität. 

### <a name="start-by-registering-a-test-webhook"></a>Beginnen Sie mit dem Registrieren eines Test-Webhook

Um zu verstehen, wie ein Service zur Verwendung einer Webhookanforderung von Common Data Service erstellt und konfiguriert wird, ist es nützlich, sich mit den Grundlagen der Registrierung eines Webhook vertraut zu machen. Weitere Informationen: [Registrieren Sie einen Webhook](register-web-hook.md)

Wenn Sie ein Beispiel-Webhook registriert haben, können Sie eine Protokollierungsanforderungs-Website verwenden, um kontextbezogenen Daten zu überprüfen, die übergeben werden. Weitere Informationen: [Test-Webhook-Registrierung mit Anforderungsprotokollierungs-Website](test-webhook-registration.md)

> [!TIP]
> Durch Abschließen der Schritte zum Registrieren eines Test-Webhook und der Überprüfung kontextbezogener Daten, die übergeben werden, können die übrigen Informationen in diesem Thema leichter verstanden werden. Führen Sie diese Schritte aus und kehren Sie zu diesem Thema zurück.

<a name="create-or-configure"></a>

## <a name="create-or-configure-a-service-to-consume-webhook-requests"></a>Erstellen oder Konfigurieren eines Services zum Konsumieren von Webhook-Anforderungen.

Webhooks sind ein einfaches Muster, das mit einer Vielzahl von Technologien angewendet werden kann. Es gibt keine erforderlichen Frameworks, Plattformen oder Programmiersprachen, die Sie verwenden müssen. Nutzen Sie Ihr Wissen und Ihre Fähigkeiten, um die entsprechende Lösung bereitzustellen. 

[Azure-Funktionen](https://azure.microsoft.com/services/functions/) stellen eine ausgezeichnete Methode dar, um eine Lösung mit Webhooks zur Verfügung zu stellen, sind aber keine Notwendigkeit. Dieser Abschnitt enthält keine Anweisungen für eine bestimmte Lösung, stattdessen werden die Daten beschrieben, die an Ihren Service übergeben werden, damit dem Service ein Wert hinzugefügt werden kann.

Wie in [Test-Webhook-Registrierung mit einer Anforderungsprotokollierungs-Website](test-webhook-registration.md) beschrieben, können Sie einen Test-Webhook-Schritt registrieren und die Anforderungsprotokollierungs-Website nutzen, um die bestimmten Arten von Daten zu erfassen, die von Ihrer Anwendung verarbeitet werden können. 

### <a name="data-passed-to-the-service"></a>An einen Service übergebene Daten

Es gibt drei Datentypen in der Anforderung: Abfragezeichenfolge, Header-Daten und Anforderungstext.

#### <a name="query-string"></a>Abfragezeichenfolge

Die einzige Art von Daten, die als Abfragezeichenfolge übergeben werden, sind möglicherweise die Authentifizierungswerte, die übergeben werden, wenn der Webhook für die Nutzung der Optionen **WebhookKey** oder **HttpQueryString** konfiguriert ist, wie in [Authentifizierungsoptionen](register-web-hook.md#authentication-options) beschrieben. 

#### <a name="header-data"></a>Header-Daten

Wenn Sie die Authentifizierungsoption **HttpHeader** auswählen, müssen Sie die Schlüssel-Wert-Paare verwenden, die für den Service erforderlich sind.

Andere Daten, die möglicherweise an Ihren Service übergeben wurden, finden Sie in der untenstehenden Tabelle:


|Key|Wertbeschreibung|
|---------|---------|
|`x-request-id`|Ein eindeutiger Bezeichner für die Anforderung|
|`x-ms-dynamics-organization`|Der Name des Mandanten, der die Anforderung sendet|
|`x-ms-dynamics-entity-name`|Der logische Name der Entität, die in den Ausführungskontextdaten übergeben wird.|
|`x-ms-dynamics-request-name`|Der Name des Ereignisses, für das der Webhook-Schritt registriert wurde.|
|`x-ms-correlation-request-id`|Eindeutiger Bezeichner für die Nachverfolgung eines beliebigen Erweiterungstyps. Diese Eigenschaft wird von der Plattform zur Vorbeugung von Endlosschleifen verwendet. In den meisten Fällen kann diese Eigenschaft ignoriert werden. Dieser Wert wird möglicherweise verwendet, wenn Sie sich an den technischen Support wenden, da er zum Abfragen von Telementrie verwendet werden kann,um herauszufinden, was während der gesamten Operation passiert ist.
|`x-ms-dynamics-msg-size-exceeded`|Wird nur gesendet, wenn die Größe der HTTP-Nutzlast 256 KB übersteigt.|


#### <a name="request-body"></a>Anforderungstext

Der Text enthält die Zeichenfolge, die den JSON-Wert einer Instanz der <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext>-Klasse darstellt. Hierbei handelt es sich um dieselben Daten, die für Azure Service Bus-Integrationen übergeben werden. 

Der Service, den Sie erstellen, muss diese Daten analysieren, um für Ihren Service die relevanten Informationen zu extrahieren, um dessen Funktion bereitzustellen. Die Art, wie Sie das Analysieren dieser Daten festlegen, hängt von Ihren Einstellungen und der verwendeten Technologie ab.

Im Folgenden finden Sie ein Beispiel serialisierter JSON-Daten, die für einen Schritt übergeben werden, der mit den folgenden Eigenschaften übergeben wird.


|Eigenschaft|Beschreibung|
|---------|---------|
|**Meldung**|Update|
|**Primäre Entität**|Kontakt|
|**Sekundäre Entität**|keine|
|**Filterattribute**|firstname,lastname|
|**Im Kontext des Benutzers ausführen**|Aufrufender Benutzer|
|**Ausführungsreihenfolge**|1|
|**Ereignis-Pipeline-Phase der Ausführung**|PostOperation|
|**Ausführungsmodus**|Asynchron|

```json
{
    "BusinessUnitId": "e2b9dd85-e89e-e711-8122-000d3aa2331c",
    "CorrelationId": "b374239d-4233-41a9-8b17-a86cb4f737b5",
    "Depth": 1,
    "InitiatingUserId": "75c2dd85-e89e-e711-8122-000d3aa2331c",
    "InputParameters": [{
        "key": "Target",
        "value": {
            "__type": "Entity:http:\/\/schemas.microsoft.com\/xrm\/2011\/Contracts",
            "Attributes": [{
                "key": "firstname",
                "value": "James"
            }, {
                "key": "contactid",
                "value": "6d81597f-0f9f-e711-8122-000d3aa2331c"
            }, {
                "key": "fullname",
                "value": "James Glynn (sample)"
            }, {
                "key": "yomifullname",
                "value": "James Glynn (sample)"
            }, {
                "key": "modifiedon",
                "value": "\/Date(1506384247000)\/"
            }, {
                "key": "modifiedby",
                "value": {
                    "__type": "EntityReference:http:\/\/schemas.microsoft.com\/xrm\/2011\/Contracts",
                    "Id": "75c2dd85-e89e-e711-8122-000d3aa2331c",
                    "KeyAttributes": [],
                    "LogicalName": "systemuser",
                    "Name": null,
                    "RowVersion": null
                }
            }, {
                "key": "modifiedonbehalfby",
                "value": null
            }],
            "EntityState": null,
            "FormattedValues": [],
            "Id": "6d81597f-0f9f-e711-8122-000d3aa2331c",
            "KeyAttributes": [],
            "LogicalName": "contact",
            "RelatedEntities": [],
            "RowVersion": null
        }
    }],
    "IsExecutingOffline": false,
    "IsInTransaction": false,
    "IsOfflinePlayback": false,
    "IsolationMode": 1,
    "MessageName": "Update",
    "Mode": 1,
    "OperationCreatedOn": "\/Date(1506409448000-0700)\/",
    "OperationId": "4af10637-4ea2-e711-8122-000d3aa2331c",
    "OrganizationId": "4ef5b371-e89e-e711-8122-000d3aa2331c",
    "OrganizationName": "OrgName",
    "OutputParameters": [],
    "OwningExtension": {
        "Id": "75417616-4ea2-e711-8122-000d3aa2331c",
        "KeyAttributes": [],
        "LogicalName": "sdkmessageprocessingstep",
        "Name": null,
        "RowVersion": null
    },
    "ParentContext": {
        "BusinessUnitId": "e2b9dd85-e89e-e711-8122-000d3aa2331c",
        "CorrelationId": "b374239d-4233-41a9-8b17-a86cb4f737b5",
        "Depth": 1,
        "InitiatingUserId": "75c2dd85-e89e-e711-8122-000d3aa2331c",
        "InputParameters": [{
            "key": "Target",
            "value": {
                "__type": "Entity:http:\/\/schemas.microsoft.com\/xrm\/2011\/Contracts",
                "Attributes": [{
                    "key": "firstname",
                    "value": "James"
                }, {
                    "key": "contactid",
                    "value": "6d81597f-0f9f-e711-8122-000d3aa2331c"
                }],
                "EntityState": null,
                "FormattedValues": [],
                "Id": "6d81597f-0f9f-e711-8122-000d3aa2331c",
                "KeyAttributes": [],
                "LogicalName": "contact",
                "RelatedEntities": [],
                "RowVersion": null
            }
        }, {
            "key": "SuppressDuplicateDetection",
            "value": false
        }],
        "IsExecutingOffline": false,
        "IsInTransaction": false,
        "IsOfflinePlayback": false,
        "IsolationMode": 1,
        "MessageName": "Update",
        "Mode": 1,
        "OperationCreatedOn": "\/Date(1506409448000-0700)\/",
        "OperationId": "4af10637-4ea2-e711-8122-000d3aa2331c",
        "OrganizationId": "4ef5b371-e89e-e711-8122-000d3aa2331c",
        "OrganizationName": "OneFarm",
        "OutputParameters": [],
        "OwningExtension": {
            "Id": "75417616-4ea2-e711-8122-000d3aa2331c",
            "KeyAttributes": [],
            "LogicalName": "sdkmessageprocessingstep",
            "Name": null,
            "RowVersion": null
        },
        "ParentContext": null,
        "PostEntityImages": [],
        "PreEntityImages": [],
        "PrimaryEntityId": "6d81597f-0f9f-e711-8122-000d3aa2331c",
        "PrimaryEntityName": "contact",
        "RequestId": null,
        "SecondaryEntityName": "none",
        "SharedVariables": [{
            "key": "ChangedEntityTypes",
            "value": [{
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "feedback",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "contract",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "salesorder",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "connection",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "socialactivity",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "postfollow",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "incident",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "invoice",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "entitlement",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "lead",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "opportunity",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "quote",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "socialprofile",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "contact",
                "value": "Update"
            }]
        }],
        "Stage": 30,
        "UserId": "75c2dd85-e89e-e711-8122-000d3aa2331c"
    },
    "PostEntityImages": [{
        "key": "AsynchronousStepPrimaryName",
        "value": {
            "Attributes": [{
                "key": "fullname",
                "value": "James Glynn (sample)"
            }, {
                "key": "contactid",
                "value": "6d81597f-0f9f-e711-8122-000d3aa2331c"
            }],
            "EntityState": null,
            "FormattedValues": [],
            "Id": "6d81597f-0f9f-e711-8122-000d3aa2331c",
            "KeyAttributes": [],
            "LogicalName": "contact",
            "RelatedEntities": [],
            "RowVersion": null
        }
    }],
    "PreEntityImages": [],
    "PrimaryEntityId": "6d81597f-0f9f-e711-8122-000d3aa2331c",
    "PrimaryEntityName": "contact",
    "RequestId": null,
    "SecondaryEntityName": "none",
    "SharedVariables": [],
    "Stage": 40,
    "UserId": "75c2dd85-e89e-e711-8122-000d3aa2331c"
}
```
> [!IMPORTANT]
> Wenn die Größe der gesamten HTTP-Nutzlast 256 KB übersteigt, wird der `x-ms-dynamics-msg-size-exceeded`-Header mit eingeschlossen und die folgenden <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext>-Eigenschaften werden entfernt:
> 
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.ParentContext>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.InputParameters>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.PreEntityImages>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.PostEntityImages>
> 
>Einige Operationen enthalten diese Eigenschaften nicht.

## <a name="invoke-a-webhook-from-a-plugin-or-workflow-activity"></a>Aufrufen eines Webhooks von einem Plug-In oder einer benutzerdefinierten Workflowaktivität

Da ein Webhook eine Art Dienstendpunkt ist, können Sie diesen ebenso aufrufen, ohne dass die Registrierung eines Schritts mit einem Plug-In oder einer Workflowaktivität erforderlich ist, wie dies auch bei einem Azure Service Bus-Endpunkt der Fall ist.  Sie müssen die [ServiceEndpointId](reference/entities/serviceendpoint.md#BKMK_ServiceEndpointId) für die <xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService>-Schnittstelle bereitstellen. Sehen Sie die folgenden Azure Service Bus-Beispiele, um weitere Informationen zu erhalten: 
- [Beispiel: Benutzerdefiniertes Azure-fähiges Plug-In](org-service/samples/azure-aware-custom-plugin.md)
- [Beispiel: Azure-fähige benutzerdefinierte Workflowaktivität](org-service/samples/azure-aware-custom-workflow-activity.md)


## <a name="troubleshoot-web-hook-registrations"></a>Problembehandlung bei Webhook-Registrierungen

Webhooks sind verhältnismäßig einfach. Der Service sendet die Anforderung und wertet die Antwort aus. Das System kann keine Daten analysieren, die mit dem Text der Antwort zurückgegeben werden, es wird nur ein Blick auf den Reaktionswert `StatusCode` geworfen

Das Timeout beträgt 60 Sekunden. Im Allgemeinen kommt es zu einem Misserfolg, wenn keine Antwort vor dem Timeout zurückgegeben wird oder wenn der Reaktionswert `StatusCode` nicht innerhalb des Bereiches `2xx` ist, und so einen Erfolg anzeigt. Dies gilt nicht, wenn der zurückgegebene Fehler in folgender Tabelle enthalten ist:

|`StatusCode`|Beschreibung|
|-|-|
|`502`|Ungültiges Gateway|
|`503`|Dienst ist nicht verfügbar|
|`504`|Gateway-Timeout|

Diese Fehler weisen auf ein Netzwerkproblem hin, das möglicherweise mit einem anderen Versuch aufgelöst werden kann. Der Webhook-Service macht nur dann einen oder mehrere Versuche, wenn diese Fehlercodes zurückgegeben werden.

### <a name="asynchronous-webhooks"></a>Asynchrone Webhooks

Wenn Ihr Webhook registriert ist, um asynchron ausgeführt zu werden, können Sie den Systemauftrag überprüfen, um Details zum Fehler zu erhalten. Weitere Informationen: [Bei der Abfrage kam es zu Fehlern bei asynchronen Aufträgen für einen bestimmten Schritt](register-web-hook.md#query-failed-asynchronous-jobs-for-a-given-step)

### <a name="synchronous-webhooks"></a>Synchrone Webhooks

[!INCLUDE [synchronous-webhook-error](includes/synchronous-webhook-error.md)]

## <a name="next-steps"></a>Nächste Schritte
[Registrieren eines Webhooks](register-web-hook.md)<br />
[Testen der Webhook-Registrierung mit der Anforderungsprotokollierungs-Website](test-webhook-registration.md)

### <a name="see-also"></a>Siehe auch

[Schreiben eines Plug-Ins](write-plug-in.md)<br />
[Registrieren eines Plug-Ins](register-plug-in.md)<br />
[Asynchroner Dienst in Common Data Service](asynchronous-service.md)<br />
[Beispiel: Benutzerdefiniertes Azure-fähiges Plug-In](/org-service/samples/azure-aware-custom-plugin.md)<br />
[Beispiel: Azure-fähige benutzerdefinierte Workflowaktivität](org-service/samples/azure-aware-custom-workflow-activity.md)<br />
[Azure-Funktionen](https://azure.microsoft.com/services/functions/)<br />
[ServiceEndPoint-Entität](reference/entities/serviceendpoint.md)<br />
[SdkMessageProcessingStep Entity](reference/entities/sdkmessageprocessingstep.md)<br />
[AsynchronousOperations-Entität](reference/entities/asyncoperation.md)<br />
<xref:Microsoft.Xrm.Sdk.RemoteExecutionContext><br />
<xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService><br />
