---
title: ' Ereignisframework (Common Data Service für Apps) | Microsoft Docs'
description: 'Beschreibt das Ereignisframework und Informationsentwickler sollten wissen, wenn sie damit arbeiten.'
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
# <a name="event-framework"></a>Ereignisframework

<!-- Re-write from
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/introduction-event-framework
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/event-execution-pipeline

See notes at https://microsoft-my.sharepoint.com/:w:/p/jdaly/EfmTW7DQXNREuqj1s7tBtIIB4VZmvasZ1Nsbl4F5zlD1ZQ?e=FNlBmr 


Make sure to call out the changes due to the legacy update messages. That information was moved.

See 
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/perform-specialized-operations-using-update#impact-of-this-change-on-plug-ins

https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/perform-specialized-operations-using-update#impact-of-this-change-on-workflows


-->

Die Funktion, die Angabe des Common Data Service für Apps für zu erweitern hängt vom Erkennen ab, wann Ereignisse im Server auftreten. *Ereignisframework* bietet die Möglichkeit, benutzerdefinierte Codes zu erfassen, die in Antworten für bestimmte Ereignisse ausgeführt werden. 

Alle Funktionen, das standardmäßige Verhalten der Plattform zu erweitern hängt vom Ereignisframework ab. Wenn Sie einen Workflow so konfigurieren, dass er auf Ereignisse mithilfe des Workflowdesigners reagiert ohne einen Code zu verfassen, wird dieses Ereignis vom Ereignisframework bereitgestellt. 

Als Entwickler können Sie *Steckbares Plug-In-Registrierungstool* verwenden, die Plug-Ins, Azure, Entitätsdatenanbieter und Integrationen virtuelle Internet-Hooks so konfigurieren, dass sie auf Ereignisse reagieren, die vom Ereignisframework bereitgestellt werden. Wenn Ereignisse ausgeführt werden und den Erwerb einer Erweiterung registriert ist, darauf zu reagieren, werden kontextbezogene Informationen über die Daten, auf die in den Vorgang mit einbezogen werden, zur Erweiterung übergeben. Je nachdem, wie die Registrierung für das Ereignis konfiguriert ist, kann die Erweiterung die Daten weitergeben, automatisierten Prozessse zur sofortigen Anwendung auslösen oder efinieren, dass eine Aktion einer Warteschlange hinzugefügt wird, die später ausgeführt wird.

Damit das Ereignisframework für die benutzerdefinierten Erweiterungen profitieren, müssen Sie verstehen:

 - Folgende Ereignisse sind verfügbar:
 - Wie das Ereignis verarbeitet wird
 - Welcher Art von Daten für die Erweiterung zur Verfügung stehen, wenn das Ereignis eintritt
 - Zeit- und Ressourcenbeschränkungen
 - Gesamtleistung überwachen

## <a name="available-events"></a>Folgende Ereignisse sind verfügbar

Wie beschrieben unter [Verwenden von Messages mit Organisationsservice](org-service/use-messages.md), Datenenvorgänge in den CDS für App-Plattform basieren Sie auf Messages und jede Message hat einen Namen. Es gibt `Create``Retrieve``RetrieveMultiple``Update``Delete``Associate`, und `Disassociate` Nachrichten, die die Vorgänge der grundlegenden Daten enthalten, die mit Entitäten geschehen. Darüber hinaus spezialisierte Messages für komplexere Transformationsvorgänge. Benutzerdefinierte Aktionen fügen neue Messages hinzu.

Wenn Sie Plug-In-Registrierungstool verwenden, um eine Erweiterung für eine bestimmte E-Mail-Nachricht zuzuordnen, registrieren Sie sie als *Schritt* Der Screenshot unten ist der Dialog **Registrieren neuer Schritt** verwendet, wenn er ein Plug-In  registriert.

![Dialog zum Registrieren eines neuen Schrittes](media/register-new-step-plug-in.png)

Ein Schritt enthält die Informationen, auf welche Message die Erweiterung reagieren sollen und einige weitere Konfigurations-Auswahlen. Geben Sie im Feld **Message** die Message der Erweiterung ein, au die reagiert wird

Im Allgemeinen können Sie wie, eine Meldung für die meisten **Anforderungs*klassen in oder <xref:Microsoft.Crm.Sdk.Messages> in den Namespaces<xref:Microsoft.Xrm.Sdk.Messages> benötigen, aber Sie erhalten außerdem Beiträge für alle benutzerdefinierten Aktionen, die in der Organisation erstellt wurden. Vorgänge mit Einbezug von Entitätsmetadaten sind nicht verfügbar.

Daten über organisationsübergreifende Messages werden in [SDK-Message](reference/entities/sdkmessage.md) und im [SdkMessageFilter](reference/entities/sdkmessagefilter.md) gespeichert. Das Plug-In-Registrierungstool filtert diese Informationen, um nur gültige Nachrichten anzuzeigen.

> [!CAUTION]
> Die `Execute` Nachricht ist verfügbar, aber Sie sollten Erweiterungen in der Regel nicht registrieren, da diese von jedem Vorgang erstellt werden.

> [!NOTE]
> In bestimmten Fällen können Plug-Ins und Workflows, die für das Update-Ereignis registriert sind, zweimal aufgerufen werden. Weitere Informationen: [Verhalten spezieller Vorgänge mithilfe Update](special-update-operation-behavior.md)

## <a name="event-execution-pipeline"></a>Ereignisausführungspipeline

Wenn Sie einen Schritt mit dem Plug-In Registrierungstools registrieren, müssen Sie **Ereignis-Pipeline-Phase der Ausführung** auswählen.  Jede Nachricht wird in eine Reihe von 4 Phasen verarbeitet, wie in der folgenden Tabelle beschrieben:

|Name|Beschreibung|
|--|--|
|**PreValidation**<br />Phase: 10|[!INCLUDE [cc-prevalidation-description](../../includes/cc-prevalidation-description.md)]|
|**PreOperation**<br />Phase: 20|[!INCLUDE [cc-preoperation-description](../../includes/cc-preoperation-description.md)]|
|**MainOperation**<br />Phase: 30|Nur zur internen Verwendung.|
|**PostOperation**<br />Phase: 40|[!INCLUDE [cc-postoperation-description](../../includes/cc-postoperation-description.md)]|

Die Phasen, die Sie aktivieren können, hängt von der Erweiterung ab. Sie müssen nicht die gesamte Geschäftslogik innerhalb eines Einzelschritts anwenden. Sie können mehrere Schritte gelten für die Logik zu, dass eines Prozesses können, um den Vorgang fortzusetzen Phase kann in der **PreValidation** sein und die Logik, um Änderungen an den Nachrichteneigenschaften ausführen kann in der **PostOperation** auftreten.

> [!IMPORTANT]
> Eine Ausnahme, die vom Code an Sie ausgegeben wurde, kann die gesamte Transaktion zurückrollen. Sie sollten achtgeben, um sicherzustellen, dass alle möglichen Ausnahmefälle vom Code behandelt werden. Wenn Sie den Vorgang abbrechen möchten, sollten Sie dies in der **PreValidations**-Phase  erkennen und ein<xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> integrieren, das eine entsprechende Message enthält, die nur beschreibt, weshalb der Vorgang storniert wurde.

Mehrere Erweiterungen können für dieselbe Phase derselben Message registriert werden. Innerhalb der Schrittregistrierung bestimmt die **Ausführungsreihenfolge** die Reihenfolge, in dem mehrere Erweiterungen für eine bestimmte Phase verarbeitet werden sollen.

Informationen über registrierte Schritte sind in [SdkMessageProcessingStep-Entität](reference/entities/sdkmessageprocessingstep.md) gespeichert.

## <a name="event-context"></a>Ereigniskontext

Wenn Ihre Erweiterung ein Plug-In ist, empfängt Sie ein Parameter, der die <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> Benutzeroberfläche implementiert. Dieser Klasse bietet einige Informationen über die <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.Stage> für die das Plug-In registriert ist, sowie Informationen über den <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.ParentContext>, der Informationen über jeglichen Vorgang innerhalb eines anderen Plug-In bereitstellt, das den aktuellen Vorgang ausgelöst hat.

Wenn die Erweiterung ein Internet-Hook oder ein Azure Servicebusendpunkt ist, stehen die Daten, die zum registrierten Endpunkt im Formular <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> veröffentlicht werden, in dem Formular, <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> und <xref:Microsoft.Xrm.Sdk.IExecutionContext>, das beide implementiert

### <a name="information-about-the-operation"></a>Informationen über einen Vorgang

Die Eigenschaften der <xref:Microsoft.Xrm.Sdk.IExecutionContext> Benutzeroberfläche sind die meisten Informationen über den Vorgang, der angezeigt wird.

Zwei der Schlüsseleigenschaften zum Ereignis werden im <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> und <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters> in den Eigenschaften gefunden. Diese <xref:Microsoft.Xrm.Sdk.ParameterCollection>-Werte enthalten die Daten des Vorgangs.

Alle Eigenschaften von <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> sind schreibgeschützt, aber die Erweiterung werden die Inhalte von Eigenschaften ändern, die diese haben.

In den **PreValidation** Phasen und der Eigenschaft **PreOperation** enthält <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> die Parameter für die<xref:Microsoft.Xrm.Sdk.OrganizationRequest>-Klasse.

In der **PostOperations-Phase** enthält das  <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters>die  die<xref:Microsoft.Xrm.Sdk.OrganizationResponse>-Klasse, die durch den Vorgang zurückgegeben wird.

### <a name="shared-variables"></a>Freigegebene Variablen

Die <xref:Microsoft.Xrm.Sdk.IExecutionContext.SharedVariables>-Eigenschaft lässt das Einschließen von Daten zu, die von einem Plug-In an einen Schritt übergeben werden können, der später in der Ausführungspipeline auftritt. Da dies ein <xref:Microsoft.Xrm.Sdk.ParameterCollection>-Wert ist, können Plug-Ins Eigenschaften hinzufügen, lesen oder ändern, um Daten für nachfolgende Schritten freizugeben.

### <a name="entity-images"></a>Entitätsbilder

Wenn Sie einen Schritt für ein Plug-In registrieren, das eine Entität vom Datenmigrations-Assistenten als einen der Parameter enthält, haben Sie die Möglichkeit anzugeben, ob eine Kopie der Entitätsdaten als *Momentaufnahme* oder Bild mit der <xref:Microsoft.Xrm.Sdk.IExecutionContext.PreEntityImages> und/oder <xref:Microsoft.Xrm.Sdk.IExecutionContext.PostEntityImages> Eigenschaft ist.

Diese Daten stellen einen Vergleichspunkt für Entitätsdaten zur Verfügung, während sie durch die Ereignispipeline durchfließt. Mithilfe dieser Bilder kann eine bessere Leistung bereitgestellt werden, anstelle Code in einen Plug-In einzubeziehen, um eine Entität abzurufen, oder um nur die Attributwerte zu vergleichen.



