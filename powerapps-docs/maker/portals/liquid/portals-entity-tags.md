---
title: Verwenden von powerapps-Common Data Service Entitäts Tags für ein Portal | MicrosoftDocs
description: Erfahren Sie mehr über powerapps Common Data Service im Portal verfügbaren Entitäts Tags.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b6efc3e176602d366315b9b54b66593005051e55
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543264"
---
# <a name="powerapps-common-data-service-entity-tags"></a>Powerapps-Common Data Service Entitäts Tags

Powerapps-Entitätstag werden zum Laden und Anzeigen von powerapps-Daten oder zum Verwenden anderer powerapps-Portale-Framework-Dienste verwendet. Diese Tags sind powerapps-spezifische Erweiterungen der Liquid-Sprache.

## <a name="chart"></a>Fluss

Fügt einer Webseite ein powerapps-Diagramm hinzu. Das diagrammtag kann im Feld "Kopieren" auf einer Webseite oder im Quellfeld einer Webvorlage hinzugefügt werden. Schritte zum Hinzufügen eines powerapps-Diagramms zu einer Webseite finden Sie unter [Hinzufügen eines Diagramms zu einer Webseite im Portal](../configure/add-chart.md).

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>Metern

Es gibt zwei Parameter, die mit dem diagrammtag bereitgestellt werden können: Diagramm-ID und viewId.

**Diagramm-ID**

Die Visualisierungs-ID des Diagramms. Dies können Sie erreichen, indem Sie das Diagramm exportieren.

**viewId**

ID der Entität, wenn Sie im Ansichts-Editor geöffnet ist. 

## <a name="powerbi"></a>powerbi

Fügt die Power BI Dashboards und Berichte innerhalb von Seiten hinzu. Das-Tag kann im Feld " **Kopieren** " auf einer Webseite oder im **Quellfeld** einer Webvorlage hinzugefügt werden. Schritte zum Hinzufügen eines Power BI Berichts oder eines Dashboards zu einer Webseite im Portal finden [Sie unter Hinzufügen eines Power BI Berichts oder Dashboards zu einer Webseite im Portal](../admin/add-powerbi-report.md).

> [!NOTE]
> Damit das-Tag funktioniert, müssen Sie [Power BI Integration](../admin/set-up-power-bi-integration.md) über das powerapps-Portal Admin Center aktivieren. Wenn die Power BI Integration nicht aktiviert ist, werden Dashboard oder Bericht nicht angezeigt.

### <a name="parameters"></a>Metern

Das powerbi-Tag akzeptiert die folgenden Parameter:

**ADS**

Der Pfad des Power BI Berichts oder Dashboards. Wenn der Power BI Bericht oder das Dashboard sicher ist, müssen Sie den Authentifizierungstyp angeben.

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Der für den Power BI Bericht oder das Dashboard erforderliche Authentifizierungstyp. Gültige Werte für diesen Parameter sind:

- **Anonym**: Hiermit können Sie veröffentlichen in Web-Power BI-Berichte einbetten. Der Standard Authentifizierungstyp ist anonym.

- **Aad**: Hiermit können Sie sichere Power BI Berichte oder Dashboards freigeben, um Azure Active Directory authentifizierten Benutzern Power BI.

- **powerbiembedded**: ermöglicht Ihnen das Freigeben der sicheren Power BI-Berichte oder-Dashboards für externe Benutzer, die nicht über Power BI Lizenz oder Azure Active Directory-Authentifizierungs Einrichtung verfügen. Weitere Informationen zum Einrichten des Power BI Embedded Dienstanbieter finden Sie unter [aktivieren Power BI Embedded Dienstanbieter](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service). 

Stellen Sie beim Hinzufügen des Berichts oder Dashboards Secure Power BI sicher, dass es für Portal Azure Active Directory oder Power BI Embedded Dienste freigegeben ist. 

> [!NOTE]
> Bei den Werten für den `authentication_type`-Parameter wird die Groß-/Kleinschreibung

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

Sie können den Bericht auch nach einem oder mehreren Werten filtern. Die Syntax zum Filtern eines Berichts lautet wie folgt:

URL? Filter =**Table**/**Field** EQ '**value**'

Angenommen, Sie möchten den Bericht filtern, um Daten für einen Kontakt mit dem Namen "Bert Hair" anzuzeigen. Sie müssen die URL mit folgendem anfügen:

? Filter = Führungskräfte/Executive EQ ' Bert Hair '

Der gesamte Code lautet wie folgt:

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

Weitere Informationen zum Filtern eines Berichts: [Filtern eines Berichts mithilfe von Abfrage Zeichenfolgen-Parametern in der URL](https://docs.microsoft.com/power-bi/service-url-filters)

> [!NOTE]
> Der anonyme Bericht unterstützt das Filtern nicht. 

Sie können auch einen dynamischen Pfad erstellen, indem Sie die Variable `capture ` Liquid wie folgt verwenden:

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

Weitere Informationen zur Liquid-Variablen: [Variablen Tags](variable-tags.md)

**tileid**

Zeigt die angegebene Kachel des Dashboards an. Sie müssen die ID der Kachel angeben.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**Rollen**

Rollen, die dem Power BI Bericht zugewiesen sind. Dieser Parameter funktioniert nur, wenn der **authentication_type** -Parameter auf **powerbiembedded**festgelegt ist.

Wenn Sie in Power BI Rollen definiert und diesen Berichten zugewiesen haben, müssen Sie die entsprechenden Rollen im **powerbi** Liquid-Tag angeben. Mit Rollen können Sie die Daten filtern, die in einem Bericht angezeigt werden sollen. Sie können mehrere Rollen durch Kommas getrennt angeben. Weitere Informationen zum Definieren von Rollen in Power BI finden Sie unter [Sicherheit auf Zeilenebene (Row-Level Security, RLS) mit Power BI](https://docs.microsoft.com/power-bi/service-admin-rls).

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

Wenn Sie einem Power BI Bericht eine Rolle zugewiesen haben und den **Rollen** Parameter nicht im Liquid-Tag angegeben haben oder keine Rolle im Parameter angegeben haben, wird ein Fehler angezeigt.

> [!TIP]
> Wenn Sie die im Portal definierten Webrollen als Power BI Rollen verwenden möchten, können Sie eine Variable definieren und Ihr Webrollen zuweisen. Sie können dann die definierte Variable im Liquid-Tag verwenden.
>
> Nehmen wir an, Sie haben zwei Webrollen als Region_East und Region_West in Ihrem Portal definiert. Sie können Sie mit dem folgenden Code verknüpfen: `{% assign webroles = user.roles | join: ", " %}`
>
> Im obigen Code Ausschnitt ist `webroles` eine Variable, und die Region_East-und Region_West-Webrollen werden darin gespeichert.
>
> Verwenden Sie die `webroles` Variable wie folgt im Liquid-Tag:
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>bearbeitet

Rendert ein angegebenes powerapps-Portale-CMS-Objekt als bearbeitbar im Portal für Benutzer mit Inhalts Bearbeitungs Berechtigung für dieses Objekt. Bearbeitbare Objekte sind z. b. [Seiten](liquid-objects.md#page)-, Code [Ausschnitte](liquid-objects.md#snippets)und [Weblinks](liquid-objects.md#weblinks).  

```
{% editable page 'adx_copy' type: 'html', title: 'Page Copy', escape: false, liquid: true %}

{% editable snippets Header type: 'html' %}

<!--

An editable web link set required a specific DOM structure, with

certain classes on the containing element, as demonstrated here.

-->

{% assign primary_nav = weblinks[Primary Navigation] %}

{% if primary_nav %}

<div {% if primary_nav.editable %}class=xrm-entity xrm-editable-adx_weblinkset{% endif %}>

<ul>

<!-- Render weblinks... -->

</ul>

{% editable primary_nav %}

</div>

{% endif %}
```

### <a name="parameters"></a>Metern

Der erste für bearbeitet bereitgestellte Parameter ist das bearbeitbare Objekt. Dies kann z. b. eine weblinkmenge, Code Ausschnitte oder die aktuelle Seite sein. Der optionale zweite Parameter besteht darin, einen Attributnamen oder-Schlüssel in diesem Objekt anzugeben, der gerendert und bearbeitet werden soll. Dies kann z. b. der Name eines Entitäts Attributs oder ein Ausschnitt Name sein.

Nach diesen anfänglichen Parametern unterstützt das-Tag eine Reihe optionaler benannter Parameter.

**klassi**

Gibt einen Klassen Attribut Wert für das Stamm Element an, das von diesem Tag gerendert wird.

**vorgegebene**

Ein Standardwert, der gerendert werden soll, wenn das bearbeitbare Element keinen Wert besitzt.

**Weg**

Ein boolescher Wert, der angibt, ob ein von diesem Tag gerenderter Wert HTML-codiert wird. Der Standardwert ist false.

**flüssi**

Ein boolescher Wert, der angibt, ob ein beliebiger Liquid-Vorlagen Code, der in dem von diesem Tag dargestellten Textwert gefunden wird, verarbeitet wird. Dies ist standardmäßig der Fall.

**Tag**

Der Name der Container-HTML-Tags, die von diesem Tag gerendert werden. Dieses Tag wird DIV-Elemente standardmäßig Rendering. Im Allgemeinen wird empfohlen, zwischen div oder span als Wert für diesen Parameter auszuwählen.

**Tel**

Gibt eine Bezeichnung für dieses bearbeitbare Element innerhalb der Inhalts Bearbeitungs Schnittstelle an. Wenn kein Wert angegeben wird, wird automatisch eine benutzerfreundliche Bezeichnung generiert.

**Sorte**

Ein Zeichen folgen Wert, der den Typ der Bearbeitungs Schnittstelle angibt, der für bearbeitbare Textwerte angezeigt werden soll. Gültige Werte für diesen Parameter sind HTML oder Text. HTML ist die Standardeinstellung.

## <a name="entitylist"></a>entityList

Lädt eine angegebene Entitäts Liste anhand des Namens oder der ID. Auf die Eigenschaften der Entitäts Liste kann dann mithilfe eines [entityList-Objekts](liquid-objects.md#entitylist) zugegriffen werden, das im tagblock verfügbar ist. Um die tatsächlichen Ergebnisdaten Sätze der Entitäts Liste zu erzeugen, verwenden Sie das [entityview](#entityview) -Tag innerhalb des-Blocks.  

Wenn die Entitäts Liste erfolgreich geladen wird, wird der Inhalt innerhalb des Blocks gerendert. Wenn die Entitäts Liste nicht gefunden wird, wird der Block Inhalt nicht gerendert.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
Standardmäßig erhält das entityList-Objekt den Variablennamen "entityList". Optional kann ein anderer Variablenname angegeben werden.

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>Metern

Geben Sie **nur eine** ID, einen Namen oder einen Schlüssel an, um die zu ladende Entitäts Liste auszuwählen.

**Name**

Lädt eine Entitäts Liste nach [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier) -ID. die ID muss eine Zeichenfolge sein, die als GUID analysiert werden kann.  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

Im Allgemeinen werden literalguid-Zeichen folgen nicht verwendet. Stattdessen wird die ID mithilfe einer GUID-Eigenschaft einer anderen Variablen angegeben.

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**Benennen**

Lädt eine Entitäts Liste anhand des Namens.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**wichtigen**

Lädt eine Entitäts Liste nach ID **oder** Name. Wenn der angegebene Schlüsselwert als [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier)analysiert werden kann, wird die Entitäts Liste nach ID geladen. Andernfalls wird Sie nach dem Namen geladen.

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**sprach\_Code**

Ein ganzzahliger powerapps-Sprachcode zum Auswählen der zu ladenden lokalisierten Bezeichnungen für die Entitäts Liste. Wenn keine sprach\_Code bereitgestellt wird, wird die Standardsprache der powerapps-Verbindung der Portal Anwendung verwendet.

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>entityview

Lädt eine angegebene powerapps-Ansicht anhand des Namens oder der ID. Der Zugriff auf die Eigenschaften der Sicht ߝ Spalten Metadaten, paginierte Ergebnisdaten Sätze usw. kann dann mithilfe eines [entityview-Objekts](liquid-objects.md#entityview) erfolgen, das im tagblock verfügbar ist.  

Wenn die Ansicht erfolgreich geladen wird, wird der Inhalt innerhalb des Blocks gerendert. Wenn die Sicht nicht gefunden wird, wird der Block Inhalt nicht gerendert.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Standardmäßig erhält das entityview-Objekt den Variablennamen entityview. Optional kann ein anderer Variablenname angegeben werden.

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

Wenn entityview in einem entityList-Block geschachtelt ist, erbt es die Standardkonfiguration (Ergebnisseiten Größe, Filteroptionen usw.) aus der Entitäts Liste. Wenn entityview keine View ID-oder Name-Parameter bereitgestellt werden, wird die Standardansicht aus der einschließenden entityList geladen.

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>Metern

Geben Sie **entweder** ID **oder** logischer\_Name mit Name an, um die zu ladende powerapps-Ansicht auszuwählen. Wenn keines von beiden bereitgestellt wird und das entityview-Tag innerhalb eines entityList-Tags geschachtelt ist, wird die Standardansicht der einschließenden entityList geladen.

**Name**

die ID muss eine Zeichenfolge sein, die als GUID analysiert werden kann.

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

Im Allgemeinen werden literalguid-Zeichen folgen nicht verwendet. Stattdessen wird die ID mithilfe einer GUID-Eigenschaft einer anderen Variablen angegeben.

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**logischer\_Name**

Der logische Name der powerapps-Entität der zu ladenden Ansicht. Muss in Kombination mit Name verwendet werden.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**Benennen**

Der powerapps-Name der Ansicht, die geladen werden soll. Muss in Kombination mit logischem\_Name verwendet werden.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**Filter**

Gibt an, ob die Ansichts Ergebnisse nach Benutzer oder Konto gefiltert werden sollen. Muss den Zeichen folgen Wert "User" oder "Account" aufweisen.

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Ein häufiger Anwendungsfall besteht darin, diesen Parameter basierend auf einer [Anforderung](liquid-objects.md#request)festzulegen.  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**MetaFilter**

Gibt den metadatenfilterausdruck der Entitäts Liste an, nach dem die Sicht Ergebnisse gefiltert werden Dieser Parameter ist nur gültig, wenn "entityview" in Kombination mit "entityList" verwendet wird. In den meisten Fällen wird dieser Parameter auf der Grundlage einer [Anforderung](liquid-objects.md#request)festgelegt.  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**Reihenfolge**

Gibt einen Sortierungs Ausdruck zum Sortieren von Ansichts Ergebnissen an. Ein Sortierungs Ausdruck kann ein oder mehrere logische Namen von Entitäts Attributen enthalten, gefolgt von der Sortierreihenfolge "ASC" oder "Debug".

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Ein häufiger Anwendungsfall besteht darin, diesen Parameter basierend auf einer [Anforderung](liquid-objects.md#request)festzulegen.  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**s**

Gibt die zu ladende Ansichts Ergebnisseite an. Wenn dieser Parameter nicht angegeben wird, wird die erste Seite der Ergebnisse geladen.

Diesem Parameter muss entweder ein ganzzahliger Wert oder eine Zeichenfolge übergeben werden, die als Ganzzahl analysiert werden kann. Wenn für diesen Parameter ein Wert angegeben wird, der Wert jedoch NULL ist oder andernfalls nicht als ganze Zahl analysiert werden kann, wird die erste Seite der Ergebnisse geladen.

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Ein häufiger Anwendungsfall besteht darin, diesen Parameter basierend auf einer [Anforderung](liquid-objects.md#request)festzulegen.  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**Seiten\_Größe**

Gibt die Anzahl der zu ladenden Ergebnisse für die aktuelle Ergebnisseite an. Wenn für diesen Parameter kein Wert angegeben wird und entityview innerhalb eines [entityList](#entitylist) -Blocks verwendet wird, wird die Seitengröße der Entitäts Liste verwendet. Wenn nicht innerhalb eines entityList-Blocks, wird der Standardwert 10 verwendet.

Diesem Parameter muss entweder ein ganzzahliger Wert oder eine Zeichenfolge übergeben werden, die als Ganzzahl analysiert werden kann. Wenn für diesen Parameter ein Wert angegeben wird, der Wert jedoch NULL ist oder andernfalls nicht als Ganzzahl analysiert werden kann, wird die Standardseiten Größe verwendet.

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Ein häufiger Anwendungsfall besteht darin, diesen Parameter basierend auf einer [Anforderung](liquid-objects.md#request)festzulegen.  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**Such**

Gibt einen Such Ausdruck an, nach dem die Sicht Ergebnisse gefiltert werden sollen. Einfache Schlüsselwort Such Ausdrücke Filtern nach, ob Attribute mit dem-Schlüsselwort beginnen. Platzhalter \* können auch in den Ausdruck eingeschlossen werden.

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

Ein häufiger Anwendungsfall besteht darin, diesen Parameter auf Grundlage einer [Anforderung](liquid-objects.md#request)festzulegen, damit der Suchfilter basierend auf der Benutzereingabe festgelegt werden kann.  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**\_Entitäts\_Berechtigungen aktivieren**

Gibt an, ob das Filtern von Entitäts Berechtigungen auf Sicht Ergebnisse angewendet wird. Dieser Parameter ist standardmäßig auf false festgelegt. Wenn entityview innerhalb eines entityList-Blocks verwendet wird, wird der Wert dieses Parameters von der Konfiguration der Entitäts Liste geerbt.

Diesem Parameter muss entweder ein [boolescher](liquid-types.md#boolean) Wert oder eine Zeichenfolge übergeben werden, die als boolescher Wert (true, false) analysiert werden kann. Wenn für diesen Parameter ein Wert angegeben wird, der Wert jedoch NULL ist oder andernfalls nicht als boolescher Wert analysiert werden kann, wird der Standardwert false verwendet.  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**sprach\_Code**

Ein ganzzahliger powerapps-Sprachcode zum Auswählen der zu ladenden lokalisierten Bezeichnungen (Spaltenheader Bezeichnungen usw.). Wenn keine sprach\_Code bereitgestellt wird, wird die Standardsprache der powerapps-Verbindung der Portal Anwendung verwendet.

Wenn entityview innerhalb eines entityList-Blocks verwendet wird, erbt entityview seine Sprachcode Konfiguration von entityList.

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>SearchIndex

Führt eine Abfrage für den Portal Suchindex aus. Auf die übereinstimmenden Ergebnisse kann dann mithilfe eines [SearchIndex](liquid-objects.md#searchindex) zugegriffen werden, der im tagblock verfügbar ist.  

```
{% searchindex query: 'support', page: params.page, page_size: 10 %}

{% if searchindex.results.size > 0 %}

<p>Found about {{ searchindex.approximate_total_hits }} matches:</p>

<ul>

{% for result in searchindex.results %}

<li>

<h3><a href={{ result.url | escape }}>{{ result.title | escape }}</a></h3>

<p>{{ result.fragment }}</p>

</li>

{% endfor %}

</ul>

{% else %}

<p>Your query returned no results.</p>

{% endif %}

{% endsearchindex %}
```

Standardmäßig erhält das Suchindex-Objekt den Variablennamen SearchIndex. Optional kann ein anderer Variablenname angegeben werden.

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>Metern

Das SearchIndex-Tag akzeptiert die folgenden Parameter.

**Such**

Die Abfrage, die zum Abgleichen der Ergebnisse verwendet wird. Dieser Parameter soll den vom Benutzer angegebenen Teil der Index Abfrage akzeptieren (sofern vorhanden).

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

Ein häufiger Anwendungsfall besteht darin, diesen Parameter basierend auf einer [Anforderung](liquid-objects.md#request)festzulegen.  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

Dieser Parameter unterstützt [die Lucene-Abfrage Parser-Syntax](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

**Filter**

Eine zusätzliche Abfrage, mit der Ergebnisse abgeglichen werden. Dieser Parameter soll einen vom Entwickler angegebenen Filter für Ergebnisse akzeptieren, wenn gewünscht.

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

Dieser Parameter unterstützt [die Lucene-Abfrage Parser-Syntax](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).  

> [!Note]     
> Der Unterschied zwischen Filter und Abfrage besteht darin, dass die Abfrage für die Lucene-Abfrage parsersyntax von der Abfrage eher so bestimmt werden soll, wie diese Syntax analysiert wird ߝ da erwartet wird, dass die meisten Endbenutzer diese Syntax nicht kennen. Wenn also die Abfrage nach dieser Syntax fehlschlägt, wird die gesamte Abfrage mit Escapezeichen versehen und als Abfragetext übermittelt. Filter hingegen werden strikt analysiert und geben bei ungültiger Syntax einen Fehler zurück.

**logische\_Namen**

Die logischen Namen der powerapps-Entität, auf die die übereinstimmenden Ergebnisse eingeschränkt werden, als durch Trennzeichen getrennte Zeichenfolge. Wenn keine Angabe erfolgt, werden alle übereinstimmenden Entitäten zurückgegeben.

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**s**

Die Suchergebnisseite, die zurückgegeben werden soll. Wenn nicht angegeben, wird die erste Seite (1) zurückgegeben.

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

Ein häufiger Anwendungsfall besteht darin, diesen Parameter basierend auf einer [Anforderung](liquid-objects.md#request)festzulegen.  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**Seiten\_Größe**

Die Größe der Ergebnisseite, die zurückgegeben werden soll. Wenn keine Angabe erfolgt, wird eine Standardgröße von 10 verwendet.

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

Rendert eine von powerapps konfigurierte Entitäts Formulare vollständig nach Name oder ID.  

> [!Note]
> Das entityform-Tag ist nur für die Verwendung in Inhalt verfügbar, der in einer  <em>[Webvorlage](store-content-web-templates.md)–</em>basierten Seitenvorlage gerendert wird. Wenn Sie versuchen, das-Tag in einer Umschreib basierten Seitenvorlage zu verwenden, wird nichts angezeigt. Sie können nur ein einzelnes entityform-oder Webform-Tag pro Seite Rendering. entityform-oder Webform-Tags nach dem ersten werden nicht gerendert.       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>Metern

**Benennen**

Der Name des Entitäts Formulars, das Sie laden möchten.

`{% entityform name:My Entity Form %}`

### <a name="webform"></a>**Webform**

Rendert ein mit powerapps konfiguriertes Webformular vollständig nach Name oder ID. Das Webform-Tag ist nur für die Verwendung in Inhalt verfügbar, der in einer [Webvorlagen](store-content-web-templates.md) basierten Seitenvorlage gerendert wird. Wenn Sie versuchen, das-Tag in einer Umschreib basierten Seitenvorlage zu verwenden, wird nichts angezeigt. Sie können nur ein einzelnes entityform-oder Webform-Tag pro Seite Rendering. entityform-oder Webform-Tags nach dem ersten werden nicht gerendert.                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>Metern

**Benennen**

Der Name des Webformulars, das Sie laden möchten.

`{% webform name:My Web Form %}`

### <a name="see-also"></a>Siehe auch

[Ablauf Steuerungs Tags](control-flow-tags.md)<br>
[Iterations Tags](iteration-tags.md)<br>
[Variablen Tags](variable-tags.md)<br>
[Vorlagen Tags](template-tags.md)
