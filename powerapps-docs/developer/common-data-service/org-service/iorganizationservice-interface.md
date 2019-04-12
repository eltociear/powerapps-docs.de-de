---
title: IOrganizationService-Schnittstelle (Common Data Service) | Microsoft Docs
description: 'Informationen zu allgemeinen Methoden, die verfügbar gemacht werden, um Datenvorgänge mit Common Data Service für Apps auszuführen.'
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
# <a name="iorganizationservice-interface"></a>IOrganizationService-Schnittstelle

Die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Schnittstelle stellt einen Satz von Methoden bereit, die verwendet werden, um die häufigsten Vorgänge für System- und benutzerdefinierte Entitäten und die Metadaten für die Organisation auszuführen.

## <a name="client-applications"></a>Client-Anwendung

Diese Schnittstelle ist in einigen Klassen implementiert, die Sie in Ihrem Code verwenden können, wenn Sie Client-Anwendungen erstellen.

|Klasse|Beschreibung|
|--|--|
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy>|Dies ist die erste Klasse auf niedriger Ebene, die von WCF und dem SOAP-Endpunkt verwendet wird |
|<xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient>|Diese Klasse auf niedriger Ebene wurde erstellt, um die OAuth-Authentifizierung zum SOAP-Endpunkt zu aktivieren|
|<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>|Dies ist die Klasse, die Sie verwenden sollen, wenn Sie .NET-Client-Anwendungen erstellen. |

> [!NOTE]
> Sie finden ältere Code und Beispiele mithilfe des  <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> niedriger Ebene oder<xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient> der Klassen, aber es empfiehlt sich die<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> für neue .NET-Client-Anwendungen zu nutzen

## <a name="plug-ins"></a>Plug-Ins

Wenn Sie zu Plug-ins schreiben, wird auch ein Objekt von der <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>.<xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})> zurückgegeben welche die <xref:Microsoft.Xrm.Sdk.IOrganizationService> Schnittstelle implementier, die aber kein Type der Klassen oben ist.

## <a name="iorganizationservice-methods"></a>IOrganizationService-Methoden

Jede der Klassen, die die Benutzeroberfläche <xref:Microsoft.Xrm.Sdk.IOrganizationService> implementieren, wird möglicherweise zusätzliche Eigenschaften und Methoden haben, aber die <xref:Microsoft.Xrm.Sdk.IOrganizationService> Schnittstelle hat nur 8 Möglichkeiten.


|Methode  |Beschreibung  |
|---------|---------|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Associate*>|Zwei Entitäten mit einer Entitätsbeziehung verknüpfen|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>|Erstellt einen Entitätsdatensatz.|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*>|Löscht einen Entitätsdatensatz|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Disassociate*>|Entfernt die Verknüpfung zwischen zwei Entitäten mit einer Entitätsbeziehung|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>|Anwenden eines Vorgangs, der als Message definiert wird, indem eine Instanz einer  <xref:Microsoft.Xrm.Sdk.OrganizationRequest> oder Klasse davon abgeleitet wird.|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*>|Eine Instanz  von einem Entitätsdatensatz abzurufen.|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*>|Rufen Sie eine Sammlung von Entitätsdatensätze ab, die mit den Kriterien übereinstimmen, die in einer Abfrage angegeben werden.|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>|Ändern den Attributwert eines Entitätsdatensatzes.|

> [!NOTE]
> Der Organisationsservice macht nur die `Execute` Methode verfügbar. Die anderen Methoden in der <xref:Microsoft.Xrm.Sdk.IOrganizationService> Schnittstelle sind einfach  Verpackungen rund um die `Execute` Methode. Diese anderen Methoden werden für doe Benutzerfreundlichkeit bereitgestellt. Sie können alle Vorgänge mithilfe der Methode `Execute` ausführen. Weitere Informationen: [Verwenden von Meldungen mit dem Organisationsservice](use-messages.md)

## <a name="see-also"></a>Siehe auch

[Verwenden von Messages mithilfe des Organisationsservices](use-messages.md)<br />
[Erstellen einer Client-Anwendung](create-client-app.md)<br />
[Schreiben eines Plug-Ins](../write-plug-in.md)<br />
[Entitäts-Vorgänge mithilfe des Organisationsservice](entity-operations.md)