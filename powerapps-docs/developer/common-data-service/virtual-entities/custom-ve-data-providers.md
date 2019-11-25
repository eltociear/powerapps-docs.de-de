---
title: Benutzerdefinierte virtuelle Entitätsdatenanbieter (Common Data Service) | Microsoft Docs
description: Durch Verwenden von Common Data Service Data SDK haben .NET-Entwickler die Möglichkeit zum Erstellen benutzerdefinierter virtueller Entitätsdatenanbieter, um externe Datenquellentypen zu kennen, die nicht von einem vorhandenen Datenanbieter unterstützt werden.
ms.date: 09/05/2019
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: d329dade-16c5-46e9-8dec-4b8efb996d22
author: mayadumesh
ms.author: jdaly
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 50223ab21a885a43c6dcb91285545e67b43c144c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748368"
---
# <a name="custom-virtual-entity-data-providers"></a>Benutzerdefinierte virtuelle Entitätsdatenanbieter

Durch Verwenden von Common Data Service Data SDK haben .NET-Entwickler die Möglichkeit zum Erstellen benutzerdefinierter virtueller Entitätsdatenanbieter, um externe Datenquellentypen zu kennen, die nicht von einem vorhandenen Datenanbieter unterstützt werden. Jeder Datenanbieter besteht aus einem wiederverwendbaren Satz von Common Data Service-Plugins, die die unterstützten CRUD-Vorgänge implementieren. (Die ursprüngliche Version ist auf **Abrufen** und **RetrieveMultiple**-Lesevorgänge beschränkt.) Dieser Abschnitt enthält erläuternde Informationen zu Datenanbietern und Vorgehensweisen zum Entwickeln benutzerdefinierter Anbieter, einschließlich Beispielcode.

> [!NOTE]
> Alternativ zum Erstellen eines benutzerdefinierten Datenquellenanbieters, sollten Sie erwägen, die Datenquelle an einen vorhandenen Datenanbieter anzupassen. Wenn Sie z. B. eine Schnittstelle von ODatas v4 zur externen Datenquelle erstellen, dann können Sie auf sie mit dem angegebenen Standard-Datenanbieter ODatas v4 direkt zugreifen. Die Funktion zum Hinzufügen dieser REST-Schnittstelle variiert nach der zugrunde liegenden Datendiensttechnologie, beispielsweise [WCF Data Services 4.5](https://docs.microsoft.com/dotnet/framework/data/wcf/). OData hat breiten Branchesupport, mit einer breiten Palette von dedizierten von Tools und kompatiblen Technologien.


## <a name="prerequisites"></a>Voraussetzungen

Benutzerdefinierte Datenanbieter erfordern erhebliche Entwicklungsressourcen, um sie zu erstellen und zu warten. Sie benötigen mindestens grundlegende Kenntnisse der folgenden Bereiche:

- Das externe Datenquellenschema und die zugeordneten Datenzugriffstechniken.  Dies Domänenwissen ist spezifisch für den externem Datenquellentyp.
- Common Data Service Metadatenschema: Mehr Informationen: [Arbeiten Sie mit Metadaten unter Verwendung von Code](../metadata-services.md).
- Common Data Service Event-Framework: Mehr Informationen: [Event Framework](../event-framework.md). 
- Common Data Service Plug-in-Architektur und Entwicklung: Mehr Informationen: [Verwenden Sie Plug-Ins, um Geschäftsprozesse zu erweitern](../plug-ins.md).

Die `Microsoft.Xrm.Sdk.Data.dll`-Assembly wird als NuGet-Paket bereitgestellt: [Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/)

## <a name="categories-of-providers"></a>Kategorien von Anbietern

Es gibt zwei allgemeine Kategorien von Datenanbietern, die Sie mit den virtuellen Entitätsdaten SDK-Assemblys erstellen können: generisch oder gezielt. Die folgende Tabelle beschreibt nur diese beiden Ansätze und ordnet sie dem Datenanbieterentwicklungsmodell zu, das für diesen Ansatz bestgeeignet ist.

|**Kategorie**|**Entwickler-Modell**|**Beschreibung**|
|------------|-------------|---------------|
|Generisch|"Bare Metal"-Anbieter|Diese können FetchXML-Abfrageausdrücke Anbieter der zugeordneten Anforderung für externe Datenquelle flexibel übersetzen, und geben die resultierenden Entitätsinstanzen zurückgegeben. Solch ein Anbieter kann für alle Instanzen des Datenquellentyps wiederverwendet werden. Diese Methode ist am allgemeinsten, jedoch kompliziert zu entwickeln.  Wenn das Schema der Datenquelle geändert wird, müssen die betroffenen virtuellen Entitäten nur neu zugeordnet werden.|
|Ausgerichtet|LINQ-Anbieter für bekanntes Schema|Ein solcher Anbieter übersetzt nur knapp Abfragen an den zugeordneten LINQ-Anruf an eine vertraute, vorhandene Datenquelleninstanz. Die Datenquelle sollte ein LINQ-Anbieter sein, wie in diesem Thema beschrieben [Aktivieren einer Datenquelle für LINQ-Abfragen](/dotnet/csharp/programming-guide/concepts/linq/enabling-a-data-source-for-linq-querying1). Diese Methode ist auf eine bestimmte Datenquelleninstanz eingeschränkt, es ist aber wesentlich weniger Codierung erforderlich. Wenn das Schema der Datenquelle geändert wird, muss der Datenanbieter aktualisiert und neu erstellt werden.|

Der Standard-Odata v4-Datenanbieter und der Cosmos DB-Datenanbieter sind Beispiele für generische Anbieter.

## <a name="steps-to-use-a-custom-data-provider"></a>Schritte, um einen benutzerdefinierten Datenanbieter zu verwenden

Es gibt verschiedene Schritte, die erforderlich sind, um eine virtuelle Entitätsdatenanbieterlösung zu erstellen, die in die Common Data Service-Anwendungen importiert werden können:

1. Entwickeln des benutzerdefinierten Datenanbieter-Pug-Ins in DLL (oder ein Satz von DLLs).
2. Registrieren des benutzerdefinierten Datenanbieters in Ihrem Common Data Service-Dienst unter Verwendung des Plug-In-Registrierungstools (PRT).
3. Erstellen einer Datenanbieterlösung.
4. Anpassen der Datenquellenentität, um einen Typ oder besondere Instanz widerzuspiegeln.
5. Exportieren Sie die benutzerdefinierte Datenanbieterlösung.


### <a name="plug-in-development"></a>Plug-In-Entwicklung

Da virtuelle Entitäten in dieser Version schreibgeschützt sind, schreiben Sie den Datenanbieter in Form eines Plug-Ins, das auf **Abrufen** und **RetrieveMultiple**-Ereignissen registriert ist. Jedes jeweilige Ereignis enthält Informationen im Ausführungskontext, die die Art von Daten beschreiben, die zurückzugeben sind. 

|**Ereignis**|**Ausführungskontext**|
|---------|---------------------|
|**Abrufen**|Beschreibt, welche Entität abzurufen sind sowie die Attribute alle verknüpften Entitäten, die einzuschließen sind.|
|**RetrieveMultiple**|Enthält ein <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>-Objekt, das die Abfrage definiert. Das Framework enthält eine **QueryExpressionVisitor**-Klasse, die dazu konzipiert ist, um verschiedene Teile der Abfrageausdruckstruktur zu überprüfen.|

Für beide Ereignisse müssen Sie:

1. Konvertieren Sie die entsprechenden Informationen im Ausführungskontext in eine Abfrage, die für Ihre externe Datenquelle funktioniert.
2. Abrufen von Daten aus dem externen System.
3. Für **Abrufen** konvertieren Sie Daten in eine <xref:Microsoft.Xrm.Sdk.Entity>; andernfalls, für **RetrieveMultiple**, konvertieren Sie sie in eine <xref:Microsoft.Xrm.Sdk.EntityCollection>. Das Ergebnis wird mithilfe der Common Data Service-Plattform dem Benutzer zurückgegeben, der die Abfrage ausführt. 

Die Klassen im <xref:Microsoft.Xrm.Sdk.Data>-Namespace bieten ein Framework, das Ihnen hilft, die Common Data Service-Abfrageinformationen aus dem Ausführungskontext in eine Abfrage im für Ihre externe Datenquelle geeigneten Format abzubilden. Dieses Framework hilft Ihnen, die Daten zu konvertieren, die zu den entsprechenden <xref:Microsoft.Xrm.Sdk.Entity>- oder <xref:Microsoft.Xrm.Sdk.EntityCollection>-Typen zurückgegeben werden, die von der Common Data Service-Plattform erwartet werden. 

#### <a name="data-provider-exceptions"></a>Datenanbieterausnahmen

Wenn aus irgendeinem Grund Ihr Code nicht das erwartete Ergebnis erzielen kann, müssen Sie den entsprechenden Fehler auslösen. Der <xref:Microsoft.Xrm.Sdk.Data.Exceptions>-Namespace enthält die folgenden Ausnahmeklassen, die von dem <xref:Microsoft.Xrm.Sdk.SdkExceptionBase> abgeleitet sind, das Sie für diesen Zweck verwenden können:  

|**Ausnahme-Klasse**|**Beschreibung**|
|---------------|-----------|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.AuthenticationException>|Ein Fehler ist bei der Sicherheitsauthentifizierung für den externem auf Datenquellenservice aufgetreten, z. B. HTTP-Status 401 wird von externe Datenservice erhalten. Tritt in der Regel auf, weil der aktuelle Benutzer nicht die erforderlichen Rechte hat, oder die zugeordneten Informationen in **EntityDataSource** sind falsch.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.EndpointException>|Die Endpunktkonfiguration in der Datenquellenentität ist ungültig oder der Endpunkt ist nicht vorhanden.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.GenericDataAccessException>|Ein allgemeiner Datenzugriffsfehler ist aufgetreten, wird verwendet, wenn der Fehler nicht einer bestimmteren Ausnahme zugeordnet ist.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.InvalidMetadataException>| |
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.InvalidQueryException>|Die angegebene Abfrage ist ungültig; beispielsweise eine ungültige die Klauselkombination oder ein nicht unterstützter Vergleichsoperator.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.ObjectNotFoundException>|Der angegebene Datensatz in der externen Datenquelle ist nicht vorhanden.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.TimeoutException>|Der externe Vorgang wurde nicht in der angegeben Zeit abgeschlossen; z. B. das Ergebnis eines HTTP-Status 408 des externen Datenservices.|


### <a name="plug-in-registration"></a>Plug-In-Registrierung

Im Gegensatz zu gewöhnlichen Plug-Ins verwenden Sie nur das Plugin Registration Tool (PRT), um die Assembly und Plug-Ins für jedes Ereignis zu registrieren. Sie registrieren nicht bestimmte Schritte. Ihr Plug-In wird ausgeführt in der Phase 30, der Hauptkerntransaktionsphase für den Vorgang, die nicht für gewöhnliche Plugin-Schritte verfügbar ist. Anstatt Schritte zu registrieren, konfigurieren Sie Ihren Datenanbieter mit den folgenden Entitäten. 


|**Entität**|**Beschreibung**|
|-----|-----|
|[EntityDataProvider](../reference/entities/entitydataprovider.md)|Definiert die Plug-Ins, die für jedes Ereignis verwendet werden und den logischen Namen der Datenquelle.|
|[EntityDataSource](../reference/entities/entitydatasource.md)|Stellt den Entitätskontext und alle Verbindungsinformationen zur Verfügung, die für externe die Datenquelle erforderlich sind, einschließlich aller geheimen Informationen, die nötig sind, um sich zu authentifizieren.|

Wenn die Metadaten für Ihre virtuelle Entität konfiguriert werden, werden die Plug-Ins mithilfe des PRT registriert und die richtigen Konfigurationsdaten in **EntityDataProvider** und **EntityDataSource** festgelegt sind, beginnt die virtuelle Entität, auf Anforderungen zu reagieren.

### <a name="debugging-plug-ins"></a>Debuggen von Plug-Ins

Ein benutzerdefinierter Anbieter virtueller Entitäten ist eine Art von Plug-in. Verwenden Sie die Informationen in diesen Themen, um Plugins für benutzerdefinierte Anbieter virtueller Entitäten zu debuggen: [Debug Plug-ins](../debug-plug-in.md) und [Tutorial: Debuggen eines Plugins](../tutorial-debug-plug-in.md).


### <a name="see-also"></a>Siehe auch

[Erste Schritte mit virtuellen Entitäten](get-started-ve.md)<br />
[API-Rücksichten auf virtuelle Entitäten](api-considerations-ve.md)<br />
[Beispiel: Generisches virtuelles Entitätsdatenanbieter-Plug-In](sample-generic-ve-plugin.md)

 