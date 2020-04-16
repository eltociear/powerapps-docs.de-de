---
title: Registrieren eines Webhooks (Common Data Service) | Microsoft-Dokumentation
description: In diesem Thema wird beschrieben, wie ein Webhook mithilfe des Plug-In-Registrierungstools registriert wird
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fcddd11548be64f80a1f2e7518431537c8343efb
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155338"
---
# <a name="register-a-webhook"></a>Registrieren eines Webhooks

Verwenden Sie das Plug-In-Registrierungstool, um einen Webhook zu registrieren. Das Plugin Registrations-Tool finden Sie unter [Tools von NuGet herunterladen](download-tools-nuget.md). 

Im Plug-In-Registrierungstool gibt es eine neue Option zum **Registrieren eines neuen Webhooks**, die ausgewählt werden kann.

![Zeigt die Menüoption zum Registrieren eines neuen Webhooks an. STRG+W ist die Tastenkombination.](media/register-new-web-hook.PNG)

Wenn Sie einen Webhook registrieren, müssen Sie drei Arten von Informationen zur Verfügung stellen:


|Element  |Beschreibung  |
|---------|---------|
|**Name**|Ein eindeutiger Name, der den Webhook beschreibt.|
|**Endpunkt-URL**|Die URL, an die Ausführungskontextinformationen gepostet werden.|
|**Authentifizierung**|Eine von drei Authentifizierungsoptionen. Für jeden Authentifizierungstyp müssen Sie die Schlüssel bereitstellen, durch die die Anforderung als legitim erkannt wird.|

## <a name="authentication-options"></a>Authentifizierungsoptionen

Die richtige zu verwendende Authentifizierungsoption zur Webhook-Registrierung und die Werte hängen davon ab, was der Endpunkt erwartet.  Der Besitzer des Endpunkts muss Ihnen mitteilen, was verwendet werden soll. Zum Verwenden von Webhooks mit Common Data Service muss der Endpunkt eine der drei nachfolgend beschriebenen Authentifizierungsoptionen zulassen:


|Typ  |Beschreibung  |
|---------|---------|
|**HttpHeader**|Enthält eine oder mehrere Schlüsselwertpaare im Header der HTTP-Anforderung.<br />Beispiel: <br />`Key1: Value1`<br />`Key2: Value2`|
|**WebhookKey**|Enthält einer Abfragezeichenfolge mithilfe `code` als den Schlüssel und einen Wert, der vom Endpunkt erforderlich ist. Wenn Sie den Internet-Hook mithilfe des Plug-In Registrierungstools nutzen, können Sie nur den Wert eingeben.<br />Beispiel: <br />`?code=00000000-0000-0000-0000-000000000001`|
|**HttpQueryString**|Enthält eine oder mehrere Schlüsselwertpaare als Zeichenfolgenparameter.<br />Beispiel: <br />`?Key1=Value1&Key2=Value2`|

> [!NOTE]
> Die Option **WebhookKey** ist für die Verwendung mit [Azure-Funktionen](https://azure.microsoft.com/services/functions/) hilfreich, da von der Authentifizierungsabfragezeichenfolge erwartet wird, dass sie einen Schlüsselnamen von `code` hat.

Alle Anforderungen an den konfigurierten Endpunkt sollten fehlschlagen, wenn die in der Anforderung übergebenen Authentifizierungsoptionen nicht übereinstimmen. Dies ist die Aufgabe des Endpunkts.

<a name="query-webhook-registrations"></a>

## <a name="query-webhook-registrations"></a>Webhookregistrierungen abfragen

Webhook-Registrierungen werden gespeichert in der [ServiceEndpoint-Entität](reference/entities/serviceendpoint.md) und haben einen [Vertrag](reference/entities/serviceendpoint.md#BKMK_Contract)-Wert von `8`.

Informationen zu registrierten Webhooks erhalten Sie durch Abfrage der **ServiceEndpoint**-Entität.

**Web-API:**

`GET [organization URI]/api/data/v9.0/serviceendpoints?$filter=contract eq 8&$select= serviceendpointid,name,authtype,url`

Mehr Informationen: [Datenabfrage über die Web API](webapi/query-data-web-api.md).

**FetchXml:**

```xml
<fetch>
  <entity name="serviceendpoint" >
    <attribute name="serviceendpointid" />
    <attribute name="name" />
    <attribute name="authtype" />
    <attribute name="url" />
    <filter>
      <condition attribute="contract" operator="eq" value="8" />
    </filter>
  </entity>
</fetch> 
```

Weitere Informationen: [Verwendung von FetchXML mit FetchExpression](org-service/entity-operations-query-data.md#use-fetchxml-with-fetchexpression)

Informationen zu den festgelegten Authentifizierungswerten sind in der [AuthValue](reference/entities/serviceendpoint.md#BKMK_AuthValue)-Eigenschaft gespeichert und können nicht abgerufen werden.

## <a name="register-a-step-for-a-webhook"></a>Registrieren eines Schritts für einen Webhook

Das Registrieren eines Schritts für einen Webhook gleicht dem Registrieren eines Schritts für ein Plug-In. Der Hauptunterschied ist, dass Sie keine Konfigurationsinformationen angeben können. 

Genau wie bei einem Plug-In geben Sie die Nachricht und bei Bedarf Informationen zu Entitäten an. Sie können auch angeben, wo in der Ereignis-Pipeline der Webhook ausgeführt werden soll. Zudem können Sie den Ausführungsmodus festlegen und angeben, ob **AsyncOperation** bei erfolgreicher Operation gelöscht werden sollen. 

![Plug-In-Registrierungs-Dialogfeld zum Registrieren eines neuen Webhook-Schritts](media/Plugin-registration-register-webhook-step.PNG)

Informationen zu **Schrittname** und **Beschreibung** werden basierend auf den ausgewählten Optionen automatisch gefüllt, Sie können die Daten jedoch ändern. Wenn Sie keine **Filterattribute** für eine Nachricht festlegen, die diese unterstützt, werden Sie zwecks optimalem Leistungsverfahren dazu aufgefordert.

### <a name="execution-mode-and-debugging-your-web-hook-registration"></a>Ausführungsmodus und Debuggen der Webhookregistrierung

Die Auswahl, die Sie bei der Webhookregistrierung treffen, wirkt sich auf die Erfahrung aus, die Sie beim Debuggen machen, wenn etwas nicht funktioniert.

#### <a name="asynchronous-mode"></a>Asynchroner Modus
Wenn Sie einen asynchronen Ausführungsmodus verwenden, wird ein asyncoperation-Auftrag erstellt, um Erfolg oder Misserfolg der Operation zu erfassen. Wenn Sie bei einem Erfolg die "asyncoperation" löschen, geben Sie Speicherplatz in Ihrer Datenbank frei. 

Alle Fehler, die auftreten, werden in Systemaufträgen aufgezeichnet. In der Webanwendung können Sie **Einstellungen > System > Systemaufträge** aufrufen, um den Status von Webhooks anzuzeigen. Es gibt einen **Statusgrund**-Wert vom Typ **Fehler**. Öffnen Sie die fehlerhafte Systemauftragsentität, um herauszufinden, warum der Auftrag fehlgeschlagen ist.

<a name="query-failed-asynchronous-jobs-for-a-given-step"></a>

#### <a name="query-failed-asynchronous-jobs-for-a-given-step"></a>Fehlgeschlagene asynchrone Aufträge für einen gegebenen Schritt abfragen

Wenn Sie die **sdkmessageprocessingstepid** einen gegebenen Schritts kennen, können Sie eine Fehlerabfrage an die [AsynchronousOperations-Entität](reference/entities/asyncoperation.md) stellen. Mit dem [OwningExtensionId](reference/entities/asyncoperation.md#BKMK_OwningExtensionId)-Wert können Sie die Ergebnisse nach einem bestimmten registrierten Schritt filtern. Die folgenden Beispiele nutzen *&lt;stepid&gt;* für die **sdkmessageprocessingstepid** des nächsten Schritts.

> [!TIP]
> Um die **sdkmessageprocessingstepid** eines bestimmten Schritts abzurufen, siehe [Abfragen von Schritten, die für ein Webhook registriert sind](#query-steps-registered-for-a-webhook) unten.

**Web-API:**

`GET [organization URI]/api/data/v9.0/asyncoperations?$orderby=completedon desc&$filter=statuscode eq 31 and _owningextensionid_value eq @stepid&$select=name,friendlymessage,errorcode,message,completedon?@stepid=<stepid>`

Mehr Informationen: [Datenabfrage über die Web API](webapi/query-data-web-api.md).

**FetchXml:**

```xml
<fetch>
  <entity name="asyncoperation" >
    <attribute name="name" />
        <attribute name="friendlymessage" />
    <attribute name="errorcode" />
    <attribute name="message" />
    <attribute name="completedon" />     
    <filter>
      <condition attribute="owningextensionid" operator="eq" value="<stepid>" />
    </filter>
    <order attribute="completedon" descending="true" />
  </entity>
</fetch>
```

Weitere Informationen: [Verwendung von FetchXML mit FetchExpression](org-service/entity-operations-query-data.md#use-fetchxml-with-fetchexpression)

#### <a name="synchronous-mode"></a>Synchroner Modus

[!INCLUDE [synchronous-webhook-error](includes/synchronous-webhook-error.md)]

> [!NOTE]
> Sie sollten den synchronen Modus verwenden, wenn es wichtig ist, dass die durch den Webhook ausgelöste Operation sofort ausgeführt wird, oder wenn Sie möchten, dass die gesamte Transaktion fehlschlägt, wenn die Webhook-Nutzlast nicht vom Service empfangen wird. Eine einfache Webhook-Schritt-Registrierung bietet begrenzte Optionen zur Fehlerbehandlung. Sie können aber auch Webhooks mit den Plug-In-Workflowaktivitäten aufrufen, wenn Sie mehr Kontrolle benötigen. Weitere Informationen: [Aufrufen des Webhooks von einem Plug-In oder einer benutzerdefinierten Workflowaktivität](use-webhooks.md#invoke-a-webhook-from-a-plugin-or-workflow-activity).

## <a name="query-steps-registered-for-a-webhook"></a>Abfragen von Schritten, die für ein Webhook registriert sind

Daten zu registrierten Webkooks befinden sich in der [SdkMessageProcessingStep-Entität](reference/entities/sdkmessageprocessingstep.md).

Sie können die Schritte abfragen, die für einen bestimmten Webhook registriert sind, wenn Sie die serviceendpointid für das Webhook kennen. Lesen Sie [Webhookregistrierungen abfragen](#query-webhook-registrations) für eine Abfrage, um die ID für einen registrierten Webhook zu erhalten.

**Web-API:**

Sie können diese Web-API-Abfrage verwenden, bei der *&lt;id&gt;* die [ServiceEndpointId](reference/entities/serviceendpoint.md#BKMK_ServiceEndpointId) des Webhooks darstellt:

```http
GET [organization URI]/api/data/v9.0/serviceendpoints(@id)/serviceendpoint_sdkmessageprocessingstep?$select=sdkmessageprocessingstepid,name,description,asyncautodelete,filteringattributes,mode,stage?@id=<id>
```

Weitere Informationen über den registrierten Schritt erhalten Sie, wenn Sie die Web-API-Abfrage nutzen, bei der die *&lt;stepid&gt;* die [SdkMessageProcessingStepId](reference/entities/sdkmessageprocessingstep.md#BKMK_SdkMessageProcessingStepId) für den Schritt ist:

```http
GET [organization URI]/api/data/v9.0/sdkmessageprocessingsteps(@id)?$select=name,description,filteringattributes,asyncautodelete,mode,stage&$expand=plugintypeid($select=friendlyname),eventhandler_serviceendpoint($select=name),sdkmessagefilterid($select=primaryobjecttypecode),sdkmessageid($select=name)?@id=<stepid>
```

**FetchXml:**

Sie können dieses FetchXML verwenden, um dieselben Informationen in einer Abfrage zu erhalten. Dabei ist *&lt;serviceendpointid&gt;* die ID des Webhooks:

```xml
<fetch>
  <entity name="sdkmessageprocessingstep" >
    <attribute name="name" />
    <attribute name="filteringattributes" />
    <attribute name="stage" />
    <attribute name="asyncautodeletename" />
    <attribute name="description" />
    <attribute name="mode" />
    <link-entity name="serviceendpoint" from="serviceendpointid" to="eventhandler" link-type="inner" alias="endpnt" >
      <attribute name="name" />
      <filter>
        <condition attribute="serviceendpointid" operator="eq" value="<serviceendpointid>" />
      </filter>
    </link-entity>
    <link-entity name="sdkmessagefilter" from="sdkmessagefilterid" to="sdkmessagefilterid" link-type="inner" alias="fltr" >
      <attribute name="primaryobjecttypecode" />
    </link-entity>
    <link-entity name="sdkmessage" from="sdkmessageid" to="sdkmessageid" link-type="inner" alias="msg" >
      <attribute name="name" />
    </link-entity>
  </entity>
</fetch>
```

## <a name="next-steps"></a>Nächste Schritte

[Testen der Webhook-Registrierung mit der Anforderungsprotokollierungs-Website](test-webhook-registration.md)<br />
[Verwenden Sie Webhooks zum Erstellen externer Handler für Serverereignisse](use-webhooks.md)

