---
title: Implementierung aller Arten von Abfragen bei der Ergebnisfilterung mit PreOperation RetrieveMultiple | MicrosoftDocs
description: 'Für beste Leistung und konsistente Ergebnisse für alle Anwendungen müssen Sie die Filterung für alle Arten von Abfragen implementieren, die mit Plugins verwendet werden können, die für die Phase PreOperation von RetrieveMultiple registriert sind.'
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/23/2019
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="implement-all-types-of-queries-when-filtering-results-using-preoperation-retrievemultiple"></a>Implementierung aller Arten von Abfragen bei der Ergebnisfilterung mit PreOperation RetrieveMultiple

**Kategorie**: Entwurf, Leistung, Sicherheit, Unterstützbarkeit

**Wirkungspotential**: Mittel

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

RetrieveMultiple-Aufrufe aus verschiedenen Anwendungen zeigen unterschiedliche Ergebnisse an.

- Zum Beispiel: Dieselben Ansichten in Legacy-Anwendungen zeigen unterschiedliche Ergebnisse in neuen Anwendungen.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

> [!NOTE]
> Die `Retrieve` und `RetrieveMultiple` Nachrichten sind in der Regel die am häufigsten verwendeten Nachrichten. Plug-Ins für diese Nachrichten können die Systemleistung erheblich beeinträchtigen. Generell sollten Sie die Verwendung von Plugins für diese Nachrichten vermeiden, wenn die Anforderungen auf andere Weise erreicht werden können. Mehr Informationen: [Beschränken Sie die Registrierung von Plugins für Retrieve and RetrieveMultiple Nachrichten](limit-registration-plugins-retrieve-retrievemultiple.md).

Plugins, die in der `RetrieveMultiple`-Meldung registriert sind, sind typischerweise dazu gedacht, die Ergebnisse von Abfragen nach einer Entität zu filtern. Es gibt zwei Strategien, dies mit einem Plug-in zu tun, das entweder auf der Stufe `PostOperation` oder `PreOperation` registriert ist.

### <a name="postoperation-filtering"></a>PostOperation-Filterung

Werten Sie in der Phase `PostOperation` die in der Eigenschaft <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters> `BusinessEntityCollection` <xref:Microsoft.Xrm.Sdk.EntityCollection.Entities> zurückgegebenen Datensätze aus und entfernen Sie Entitäten, die nicht zurückgegeben werden sollen.

Dieser Ansatz ändert möglicherweise die erwartete Anzahl der Datensätze, die auf jeder Seite der Ergebnisse zurückgegeben werden, und kann zu inkonsistenten Erfahrungen führen, wenn die Daten in einer Anwendung angezeigt werden.

### <a name="preoperation-filtering"></a>PreOperation-Filterung

Werten Sie im Schritt `PreOperation` die Eigenschaft <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest.Query> aus und passen Sie die Abfrage an, um zu filtern, was vor der Ausführung zurückgegeben wird.

Bei der Verwendung dieses Ansatzes müssen Sie vor allem für die verschiedenen möglichen Arten von Abfragen die entsprechende Filterung implementieren: <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> und <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>. Wenn Sie nur eine dieser Optionen implementieren, werden Ihre Änderungen nicht von verschiedenen Anwendungen übernommen, die die andere Art von Abfrage verwenden.

Obwohl die Nachrichten `QueryExpressionToFetchXml` und `FetchXmlToQueryExpression` die Möglichkeit bieten, einen Abfragetyp in einen anderen umzuwandeln, empfehlen wir Ihnen, diese Nachrichten in diesem Zusammenhang nicht zu verwenden, da sie die Performance beeinträchtigen, wenn Sie zusätzliche Aufrufe in `RetrieveMultiple` aufnehmen. Implementieren Sie vielmehr Ihre Filterung mit der entsprechenden Logik in beiden. 

Es gibt eine dritte Art von Abfrage, die auch mit `RetrieveMultiple` verwendet werden kann: <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>. Diese Art von Abfrage sieht keine komplexe Filterung vor und es ist nicht möglich, komplexere Filterlogik in ein Plug-in einzubinden. Glücklicherweise wird diese Art der Abfrage nicht häufig verwendet. Abhängig von der Empfindlichkeit der von Ihnen hinzugefügten Filterung können Sie Anfragen dieses Typs ablehnen, indem Sie eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> auslösen.

## <a name="example"></a>Beispiel

Siehe [Muster: Ändern Sie die Abfrage in der Phase PreOperation](../../org-service/samples/modify-query-preoperation-stage.md) für ein Beispiel für die von uns empfohlene Strategie.

## <a name="problematic-patterns"></a>Problematische Muster

Wenn ein Plug-in geschrieben wird, um die Datensätze zu ändern, die in einer bestimmten Anwendung zurückgegeben werden, die nur eine Art von Abfrage verwendet, entweder <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> oder <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>, sind die Ergebnisse in anderen Anwendungen möglicherweise nicht konsistent oder wenn die Anwendung die Art der verwendeten Abfrage ändert. Plug-Ins sollten geschrieben werden, um unabhängig von der Anwendung das gleiche Ergebnis zu liefern.

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Bei Verwendung der Web API werden GET-Requests auf eine Collection in <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> konvertiert, es sei denn, die Abfrage verwendet FetchXml wie unter [Abrufen und Ausführen vordefinierter Abfragen](../../webapi/retrieve-and-execute-predefined-queries.md) beschrieben. In diesem Fall verwenden die Abfragen <xref:Microsoft.Xrm.Sdk.Query.FetchExpression>.

Der bestehende Webclient für modellgetriebene Anwendungen wird durch eine einheitliche Benutzeroberfläche ersetzt. Die einheitliche Benutzeroberfläche verwendet die in den Eigenschaften [SavedQuery.FetchXml](../../reference/entities/savedquery.md#BKMK_FetchXml) oder [UserQuery.FetchXml](../../reference/entities/userquery.md#BKMK_FetchXml) definierte FetchXml. Um die Leistung zu verbessern, konvertiert das einheitliche Benutzeroberfläche die FetchXml-Daten nicht in eine <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>, bevor diese Abfragen wie der alte Webclient ausgeführt werden. Daher werden Abfragen, die im Plugin-Code für den älteren Web-Client, der <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> verwendet hat, geändert wurden, nicht die gleichen Änderungen anwenden, da die Abfrage zur Unterstützung von Views mit <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> übergeben wird, es sei denn, der Plugin-Code wird geschrieben, um dieselbe Logik auf <xref:Microsoft.Xrm.Sdk.Query.FetchExpression>-Abfragen anzuwenden. 

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Beispiel: Ändern Sie die Abfrage in der Vorbereitungsphase](../../org-service/samples/modify-query-preoperation-stage.md)<br />
[Daten abfragen mithilfe des Organisation-Service](../../org-service/entity-operations-query-data.md)<br />
[Verwenden von FetchXML zum Erstellen einerAbfrage](../../use-fetchxml-construct-query.md)<br />
[Erstellen von Abfragen mit QueryExpression](../../org-service/build-queries-with-queryexpression.md)<br />
[Einschränkung der Registrierung von Plugins für Retrieve- und RetrieveMultiple-Nachrichten](limit-registration-plugins-retrieve-retrievemultiple.md)<br />
[Community für die einheitliche Benutzeroberfläche](https://community.dynamics.com/365/unified-interface/)