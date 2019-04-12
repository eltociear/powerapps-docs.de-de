---
title: Abrufen spezifischer Spalten für eine Entität über Query-APIs | MicrosoftDocs
description: 'Abfragen, die zum Abrufen von Daten übermittelt werden, sollten bestimmte Spalten in der ColumnSet-Instanz enthalten, die der Abfrage zugeordnet ist, und nicht alle Spalten.'
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
--- 
# <a name="do-not-retrieve-entity-all-columns-via-query-apis"></a>Rufen Sie nicht alle Spalten der Entität über Query-APIs ab

**Kategorie**: Leistung

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Das Abrufen aller Spalten kann zu Folgendem führen:

- Performance-Probleme durch die Menge der abgerufenen Daten
- Unbeabsichtigte Ausführung von Plugins und Prozessen

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Für eine optimale Leistung sollten Sie bei der Abfrage von Daten des Common Data Service nur die von Ihrer Anwendung benötigte Mindestmenge an Daten auswählen. 

### <a name="columnset-parameter"></a>ColumnSet-Parameter

Wenn Sie die <xref:Microsoft.Xrm.Sdk.IOrganizationService> verwenden.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> Methode setzt den Parameter `columnSet` auf eine Instanz <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> mit angegebenen Spalten.  Wenn Sie <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> verwenden, setzen Sie die Eigenschaft <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.ColumnSet> mit den erforderlichen Attributen.

Im Folgenden finden Sie einige Beispiele:

- [ColumnSet(param string[] columns)](/dotnet/api/microsoft.xrm.sdk.query.columnset.-ctor#Microsoft_Xrm_Sdk_Query_ColumnSet__ctor_System_String___) Konstruktorüberladung für <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>.

    ```csharp
        var query = new QueryExpression("account")
        {
            ColumnSet = new ColumnSet("name", "address1_city")
        };

        var results = service.RetrieveMultiple(query);
    ```

- [ColumnSet(param string[] columns)](/dotnet/api/microsoft.xrm.sdk.query.columnset.-ctor#Microsoft_Xrm_Sdk_Query_ColumnSet__ctor_System_String___) Konstruktorüberladung für <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest>.

    ```csharp
        var entity = service.Retrieve("account", Guid.NewGuid(), new ColumnSet("name", "address1_city"));
    ```

- <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.<xref:Microsoft.Xrm.Sdk.Query.ColumnSet.AddColumn(System.String)> Methodenaufruf.

    ```csharp
        var query = new QueryExpression("account");
        query.ColumnSet.AddColumn("name");
        query.ColumnSet.AddColumn("address1_city");

        var results = service.RetrieveMultiple(query);
    ```

- <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.<xref:Microsoft.Xrm.Sdk.Query.ColumnSet.AddColumns(System.String[])> Methodenaufruf.

    ```csharp
        var query = new QueryExpression("account");
        query.ColumnSet.AddColumns("name", "address1_city");

        var results = service.RetrieveMultiple(query);
    ```

Die folgenden Klassen enthalten eine <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> Instanz:

- <xref:Microsoft.Crm.Sdk.Messages.ConvertQuoteToSalesOrderRequest>
- <xref:Microsoft.Crm.Sdk.Messages.GenerateInvoiceFromOpportunityRequest>
- <xref:Microsoft.Crm.Sdk.Messages.GenerateQuoteFromOpportunityRequest>
- <xref:Microsoft.Crm.Sdk.Messages.GenerateSalesOrderFromOpportunityRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveAllChildUsersSystemUserRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveBusinessHierarchyBusinessUnitRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveMembersTeamRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveSubsidiaryTeamsBusinessUnitRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveSubsidiaryUsersBusinessUnitRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveTeamsSystemUserRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveUnpublishedRequest>
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveUserSettingsSystemUserRequest>
- <xref:Microsoft.Crm.Sdk.Messages.ReviseQuoteRequest>
- <xref:Microsoft.Crm.Sdk.Messages.SearchByBodyKbArticleRequest>
- <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*>
- <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

Abfragen, die eine definierte <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> beinhalten, bei denen die Eigenschaft <xref:Microsoft.Xrm.Sdk.Query.ColumnSet.AllColumns> `true` ist, weisen die Plattform an, einen SQL-Befehl zum ["SELECT *"](https://technet.microsoft.com/library/ms189287.aspx) für alle physischen Daten, die im Abfrageplan enthalten sind, auszugeben.  Dieses Szenario sollte nach Möglichkeit vermieden werden.

> [!WARNING]
> Diese Szenarien sollten vermieden werden.

- <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.<xref:Microsoft.Xrm.Sdk.Query.ColumnSet.AllColumns> Aufruf der Setter-Methode.

    ```csharp
        var columns = new ColumnSet();
        columns.AllColumns = true;

        var query = new QueryExpression("account");
        query.ColumnSet = columns;

        var results = service.RetrieveMultiple(query);
    ```

- [ColumnSet(bool allColumns)](/dotnet/api/microsoft.xrm.sdk.query.columnset.-ctor#Microsoft_Xrm_Sdk_Query_ColumnSet__ctor_System_Boolean_) Konstruktorüberladung.

    ```csharp
        var query = new QueryExpression("account")
        {
            ColumnSet = new ColumnSet(true)
        };

        var results = service.RetrieveMultiple(query);
    ```

- [ColumnSet(bool allColumns)](/dotnet/api/microsoft.xrm.sdk.query.columnset.-ctor#Microsoft_Xrm_Sdk_Query_ColumnSet__ctor_System_Boolean_) Konstruktorüberladung für <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest>.

    ```csharp
        var entity = service.Retrieve("account", Guid.Parse("bec45132-392a-4617-b935-a64ef04738e4"), new ColumnSet(true));
    ```

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Abfragen, die zum Abrufen von Daten aus Dynamics 365 gesendet werden, sollten nicht alle Spalten markieren.  Vielmehr sollten in der der Abfrage zugeordneten Instanz <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> spezifische Einzelspalten angegeben werden. Das Abrufen aller Spalten einer Entität kann sich negativ auf die Performance auswirken. Darüber hinaus können Sie unbeabsichtigt Plug-in-Registrierungsereignisse auslösen, indem Sie Spalten abrufen, mit denen Sie nicht arbeiten, und ein Update durchführen.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

<xref href="Microsoft.Xrm.Sdk.Query.ColumnSet?text=ColumnSet Class" /><br />
[Verwendung der ColumnSet-Klasse](../../org-service/use-the-columnset-class.md)<br />
[Erstellen von Abfragen mit QueryExpression](../../org-service/build-queries-with-queryexpression.md)<br />