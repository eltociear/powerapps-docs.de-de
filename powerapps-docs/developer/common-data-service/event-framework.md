---
title: ' Ereignisframework (Common Data Service) | Microsoft Docs'
description: 'Beschreibt das Ereignisframework und Informationsentwickler sollten wissen, wenn sie damit arbeiten.'
ms.custom: ''
ms.date: 06/18/2019
ms.reviewer: ''
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
---
# <a name="event-framework"></a>Ereignisframework

Die Funktion zur Erweiterung des Standardverhaltens von Common Data Service hängt davon ab, dass erkannt wird, wann Ereignisse im Server auftreten. *Ereignisframework* bietet die Möglichkeit, benutzerdefinierte Codes zu erfassen, die in Antworten für bestimmte Ereignisse ausgeführt werden. 

Alle Funktionen, das standardmäßige Verhalten der Plattform zu erweitern hängt vom Ereignisframework ab. Wenn Sie einen Workflow so konfigurieren, dass er auf Ereignisse mithilfe des Workflowdesigners reagiert ohne einen Code zu verfassen, wird dieses Ereignis vom Ereignisframework bereitgestellt. 

Als Entwickler können Sie *Steckbares Plug-In-Registrierungstool* verwenden, die Plug-Ins, Azure, Entitätsdatenanbieter und Integrationen virtuelle Internet-Hooks so konfigurieren, dass sie auf Ereignisse reagieren, die vom Ereignisframework bereitgestellt werden. Wenn Ereignisse ausgeführt werden und den Erwerb einer Erweiterung registriert ist, darauf zu reagieren, werden kontextbezogene Informationen über die Daten, auf die in den Vorgang mit einbezogen werden, zur Erweiterung übergeben. Je nachdem, wie die Registrierung für das Ereignis konfiguriert ist, kann die Erweiterung die Daten weitergeben, automatisierten Prozessse zur sofortigen Anwendung auslösen oder efinieren, dass eine Aktion einer Warteschlange hinzugefügt wird, die später ausgeführt wird.

Damit das Ereignisframework für die benutzerdefinierten Erweiterungen profitieren, müssen Sie verstehen:

 - Folgende Ereignisse sind verfügbar:
 - Wie das Ereignis verarbeitet wird
 - Welcher Art von Daten für die Erweiterung zur Verfügung stehen, wenn das Ereignis eintritt
 - Zeit- und Ressourcenbeschränkungen
 - Gesamtleistung überwachen

## <a name="available-events"></a>Folgende Ereignisse sind verfügbar

Wie beschrieben unter [Verwenden von Messages mit Organisationsservice](org-service/use-messages.md), Datenenvorgänge in der Common Data Service-Plattform basieren Sie auf Messages und jede Message hat einen Namen. Es gibt `Create``Retrieve``RetrieveMultiple``Update``Delete``Associate`, und `Disassociate` Nachrichten, die die Vorgänge der grundlegenden Daten enthalten, die mit Entitäten geschehen. Darüber hinaus spezialisierte Messages für komplexere Transformationsvorgänge. Benutzerdefinierte Aktionen fügen neue Messages hinzu.

Wenn Sie Plug-In-Registrierungstool verwenden, um eine Erweiterung für eine bestimmte E-Mail-Nachricht zuzuordnen, registrieren Sie sie als *Schritt* Der Screenshot unten ist der Dialog **Registrieren neuer Schritt** verwendet, wenn er ein Plug-In  registriert.

![Dialog zum Registrieren eines neuen Schrittes](media/register-new-step-plug-in.png)

Ein Schritt enthält die Informationen, auf welche Message die Erweiterung reagieren sollen und einige weitere Konfigurations-Auswahlen. Geben Sie im Feld **Message** die Message der Erweiterung ein, au die reagiert wird

Im Allgemeinen können Sie wie, eine Meldung für die meisten **Anforderungs*klassen in oder <xref:Microsoft.Crm.Sdk.Messages> in den Namespaces<xref:Microsoft.Xrm.Sdk.Messages> benötigen, aber Sie erhalten außerdem Beiträge für alle benutzerdefinierten Aktionen, die in der Organisation erstellt wurden. Vorgänge mit Einbezug von Entitätsmetadaten sind nicht verfügbar.

Daten über organisationsübergreifende Messages werden in [SDK-Message](reference/entities/sdkmessage.md) und im [SdkMessageFilter](reference/entities/sdkmessagefilter.md) gespeichert. Das Plug-In-Registrierungstool filtert diese Informationen, um nur gültige Nachrichten anzuzeigen.

Um zu überprüfen, ob eine Message- und Entitätskombination die Ausführung von Plug-Ins mithilfe einer Datenbankabfrage unterstützt, können Sie die folgende Web-API-Abfrage verwenden:

```
{{webapiurl}}sdkmessages?$select=name
&$filter=isprivate eq false 
and (name ne 'SetStateDynamicEntity' 
and name ne 'RemoveRelated' 
and name ne 'SetRelated' and 
name ne 'Execute') 
and sdkmessageid_sdkmessagefilter/any(s:s/iscustomprocessingstepallowed eq true 
and s/isvisible eq true)
&$expand=sdkmessageid_sdkmessagefilter($select=primaryobjecttypecode;
$filter=iscustomprocessingstepallowed eq true and isvisible eq true)
&$orderby=name
```

> [!TIP]
> Sie können diese Daten mithilfe dieser Abfrage und der in diesem Blogbeitrag aufgeführten Anleitung in ein Excel-Arbeitsblatt exportieren: [Finden von Messages und Entitäten, die für Plug-Ins mithilfe von Common Data Service qualifiziert sind](https://powerapps.microsoft.com/en-us/blog/find-messages-and-entities-eligible-for-plug-ins-using-the-common-data-service/)


Sie können diese Informationen auch mithilfe des folgenden FetchXML abrufen. Der [FetchXML-Generator](http://fxb.xrmtoolbox.com) ist ein hilfreiches Tool, um diese Art von Abfrage auszuführen.

```xml
<fetch>
  <entity name='sdkmessage' >
    <attribute name='name' />
    <link-entity name='sdkmessagefilter' alias='filter' to='sdkmessageid' from='sdkmessageid' link-type='inner' >
      <filter type='and' >
        <condition attribute='iscustomprocessingstepallowed' operator='eq' value='1' />
        <condition attribute='isvisible' operator='eq' value='1' />
      </filter>
      <attribute name='primaryobjecttypecode' />
    </link-entity>
    <filter>
      <condition attribute='isprivate' operator='eq' value='0' />
      <condition attribute='name' operator='not-in' >
        <value>SetStateDynamicEntity</value>
        <value>RemoveRelated</value>
        <value>SetRelated</value>
          <value>Execute</value>
      </condition>
    </filter>
    <order attribute='name' />
  </entity>
</fetch>
```

> [!CAUTION]
> Die `Execute`-Message ist verfügbar, aber Sie sollten Erweiterungen nicht registrieren, da diese von jedem Vorgang erstellt werden.

> [!NOTE]
> In bestimmten Fällen können Plug-Ins und Workflows, die für das Update-Ereignis registriert sind, zweimal aufgerufen werden. Weitere Informationen: [Verhalten spezieller Vorgänge mithilfe Update](special-update-operation-behavior.md)

## <a name="event-execution-pipeline"></a>Ereignisausführungspipeline

Wenn Sie einen Schritt mit dem Plug-In Registrierungstools registrieren, müssen Sie **Ereignis-Pipeline-Phase der Ausführung** auswählen.  Jede Nachricht wird in eine Reihe von 4 Phasen verarbeitet, wie in der folgenden Tabelle beschrieben:

|Name|Beschreibung|
|--|--|
|**PreValidation**|[!INCLUDE [cc-prevalidation-description](../../includes/cc-prevalidation-description.md)]|
|**PreOperation**|[!INCLUDE [cc-preoperation-description](../../includes/cc-preoperation-description.md)]|
|**MainOperation**|Nur zur internen Verwendung.|
|**PostOperation**|[!INCLUDE [cc-postoperation-description](../../includes/cc-postoperation-description.md)]|

Die Phasen, die Sie aktivieren können, hängt von der Erweiterung ab. Sie müssen nicht die gesamte Geschäftslogik innerhalb eines Einzelschritts anwenden. Sie können mehrere Schritte gelten für die Logik zu, dass eines Prozesses können, um den Vorgang fortzusetzen Phase kann in der **PreValidation** sein und die Logik, um Änderungen an den Nachrichteneigenschaften ausführen kann in der **PostOperation** auftreten.

> [!IMPORTANT]
> Eine Ausnahme, die vom Code an Sie ausgegeben wurde, kann die gesamte Transaktion zurückrollen. Sie sollten achtgeben, um sicherzustellen, dass alle möglichen Ausnahmefälle vom Code behandelt werden. Wenn Sie den Vorgang abbrechen möchten, sollten Sie dies in der **PreValidations**-Phase  erkennen und ein<xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> integrieren, das eine entsprechende Message enthält, die nur beschreibt, weshalb der Vorgang storniert wurde.

Mehrere Erweiterungen können für dieselbe Phase derselben Message registriert werden. Innerhalb der Schrittregistrierung bestimmt die **Ausführungsreihenfolge** die Reihenfolge, in dem mehrere Erweiterungen für eine bestimmte Phase verarbeitet werden sollen.

Informationen über registrierte Schritte sind in [SdkMessageProcessingStep-Entität](reference/entities/sdkmessageprocessingstep.md) gespeichert.

## <a name="event-context"></a>Ereigniskontext

Wenn Ihre Erweiterung ein Plug-In ist, empfängt Sie ein Parameter, der die <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> Benutzeroberfläche implementiert. Dieser Klasse bietet einige Informationen über die <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.Stage> für die das Plug-In registriert ist, sowie Informationen über den <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.ParentContext>, der Informationen über jeglichen Vorgang innerhalb eines anderen Plug-In bereitstellt, das den aktuellen Vorgang ausgelöst hat.

Wenn die Erweiterung ein Internet-Hook oder ein Azure Servicebusendpunkt ist, stehen die Daten, die zum registrierten Endpunkt im Formular <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> veröffentlicht werden, in dem Formular, <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> und <xref:Microsoft.Xrm.Sdk.IExecutionContext>, das beide implementiert

Weitere Informationen zum Ausführungskontext finden Sie unter [Verstehen des Ausführungskontexts](understand-the-data-context.md).