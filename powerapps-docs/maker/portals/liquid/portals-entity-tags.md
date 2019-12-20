---
title: Verwenden von Power Apps Common Data Service Entity-Tags für ein Portal | MicrosoftDocs
description: Erfahren Sie mehr über die im Portal verfügbaren Power Apps Common Data Service Entity-Tags.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/28/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f252b0c9ef0ea90f6206863fe45a36702e4ce481
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884647"
---
# <a name="power-apps-common-data-service-entity-tags"></a>Power Apps Common Data Service Entity-Tags

Power Apps-Entitätstags werden verwendet, um Power Apps-Daten zu laden und anzuzeigen, oder um andere Power Apps-Portalframeworkdienste zu verwenden. Diese Tags sind Power Apps-spezifische Erweiterungen der Liquid-Sprache.

## <a name="chart"></a>Diagramm

Hinzufügen eines Power Apps-Diagramms zu einer Webseite Sie können das Diagramm im Feld Kopie auf einer Webseite oder im Feld Quelle auf einer Webvorlage hinzufügen. Schritte zum Hinzufügen eines Power Apps-Diagramms zu einer Webseite finden Sie unter [Diagramm zu einer Webseite in Portal](../configure/add-chart.md) hinzufügen.

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>Parameter

Es gibt zwei Parameter, die mit dem Diagrammtag bereitgestellt werden müssen: Diagramm-ID und viewid.

**Diagramm-ID**

Visualisierungs-ID des Diagramms. Sie können dieses abrufen, indem Sie das Diagramm exportieren.

**viewid**

ID der Entität, wenn sie im Ansichts-Editor geöffnet wird. 

## <a name="powerbi"></a>PowerBI

Fügt die Power BI-Dashboards und Berichte innerhalb von Seiten hinzu. Der Tag kann im Feld **Copy** auf einer Webseite oder im Feld **Source** auf einer Webvorlage hinzugefügt werden. Weitere Informationen zum Hinzufügen eines Power BI-Berichts oder Dashboards zu einer Webseite im Portal finden Sie unter [Hinzufügen eines Power BI-Berichts oder Dashboards zu einer Webseite im Portal](../admin/add-powerbi-report.md).

> [!NOTE]
> Damit das Tag funktioniert, müssen Sie die [Power BI-Integration aktivieren](../admin/set-up-power-bi-integration.md) über das Power Apps-Portal-Administratorcenter. Wenn die Power BI-Integration nicht aktiviert ist, wird das Dashboard oder der Bericht nicht angezeigt.

### <a name="parameters"></a>Parameter

Das powerbi-Tag akzeptiert die folgenden Parameter:

**path**

Pfad des Power BI-Berichts oder des Dashboards. Wenn der Power BI-Bericht oder Dashboard sicher ist, müssen Sie den Authentifizierungstyp angeben.

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Typ der Authentifizierung, die für den Power BI-Bericht oder Dashboard erforderlich ist. Gültige Werte für diesen Parameter sind:

- **Anonym**: Ermöglicht Ihnen einzubetten und zu Web-Power BI-Berichten zu veröffentlichen. Der Standardauthentifizierungstyp ist "Anonym". Wenn Sie den Authentifizierungstyp "Anonym" verwenden, müssen Sie die Power BI-Berichts-URL abrufen, wie beschrieben unter: [Veröffentlichen im Internet über Power BI](https://docs.microsoft.com/power-bi/service-publish-to-web)

- **AAD**: Ermöglicht Ihnen, sichere Power BI-Berichte oder Dashboards für authentifizierte Power BI Azure Active Directory-Benutzer freizugeben.

- **powerbiembedded**: Ermöglicht Ihnen, sichere Power BI-Berichte oder Dashboards externen Benutzern freizugeben, die keine Power BI-Lizenz oder authentifiziertes Azure Active Directory-Setup haben. Informationen zum Power BI Embedded-Dienstsetup finden Sie unter [Aktivieren von Power BI Embedded-Dienst](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service). 

Wenn Sie den/das sichere(n) Power BI-Bericht oder -Dashboard hinzufügen, stellen Sie sicher, dass er bzw. es mit Azure Active Directory- oder Power BI Embedded-Services im Portal geteilt ist. 

> [!NOTE]
> Bei Werten für den `authentication_type`-Parameter wird die Groß-/Kleinschreibung nicht beachtet.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

Sie können den Bericht für eine oder mehrere Werte auch filtern. Die Syntax, um einen Bericht zu filtern ist:

URL?filter=**Tabelle**/**Feld** eq '**Wert**'

Wenn Sie beispielsweise den Bericht filtern möchten, sehen Sie die Daten für den Kontakt Bert Hair. Die müssen die URL mit den folgenden Schritte ausführen:

?filter=Executives/Executive eq 'Bert Hair'

Der vollständige Code ist:

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

Weitere Informationen zum Filtern von Berichten: [Filtern eines Berichts mithilfe der Abfragezeichenfolgenparameter in der URL](https://docs.microsoft.com/power-bi/service-url-filters)

> [!NOTE]
> Die Filterung Anonymer Bericht wird nicht unterstützt. 

Sie können auch einen Pfad erstellen, indem Sie die `capture `-Variable verwenden:

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

Weitere Informationen zu flüssigen Variablen [Variable Tags](variable-tags.md)

**tileid**

Zeigt die angegebene Kachel des Dashboards an. Sie müssen die ID der Kachel angeben.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**Rollen**

Dem Power BI-Bericht zugewiesene Rollen. Dieser Parameter funktioniert nur, wenn der Parameter **authentication_type** auf **powerbiembedded** festgelegt ist.

Wenn Sie Rollen in Power BI definiert haben und sie Berichten zugewiesen haben, müssen Sie die entsprechenden Rollen im Liquid-Tag **powerbi** angeben. Rollen ermöglichen es Ihnen, die Daten zu filtern, die in einem Bericht angezeigt werden sollen. Sie können mehreren Rollen angeben, die durch ein Komma voneinander getrennt sind. Weitere Informationen zum Definieren von Rollen in Power BI finden Sie unter [Sicherheit auf Zeilenebene (RLS) mit Power BI](https://docs.microsoft.com/power-bi/service-admin-rls).

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

Wenn Sie einem Power BI-Bericht keine Rolle zugewiesen haben und den Parameter **Rollen** nicht im Liquid-Tag angegeben haben oder keine Rolle im Parameter angegeben haben, wird ein Fehler angezeigt.

> [!TIP]
> Wenn Sie die Webrollen verwenden möchten, die in Ihrem Portal als Power BI-Rollen definiert sind, können Sie eine Variable definieren und ihr Webrollen zuweisen. Sie können dann die definierte Variable im Liquid-Tag verwenden.
>
> Nehmen wir einmal an, Sie haben zwei Webrollen als Region_Ost und Region_West in Ihrem Portal definiert. Sie können diese mithilfe des Codes verknüpfen: `{% assign webroles = user.roles | join: ", " %}`
>
> Im obigen Codeausschnitt ist `webroles` eine Variable ist und die Webrollen Region_Ost und Region_West werden darin gespeichert.
>
> Verwenden Sie die Variable `webroles` folgendermaßen im Liquid-Tag:
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>editable

Rendert ein bestimmtes Power Apps-Portal-CMS-Objekt als im Portal editierbar für Benutzer mit Berechtigung zur Inhaltsbearbeitung für dieses Objekt. Bearbeitbare Objekte umfassen [Seite](liquid-objects.md#page), [Ausschnitte](liquid-objects.md#snippets) und [Weblinks](liquid-objects.md#weblinks).  

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

### <a name="parameters"></a>Parameter

Der erste Parameter für „editable” ist das bearbeitbare Objekt. Beispielsweise kann dies ein Weblinksatz, Ausschnitte oder die aktuelle Seite sein. Der zweite optionale Parameter ist zur Angabe eines Attributnamens oder Schlüssels innerhalb dieses Objekts, das gerendert und bearbeitet werden soll. Dies kann z. B. der Name eines Entitätsattributs oder ein Ausschnittsname sein.

Nach diesen ersten Parametern unterstützt der Tag einige optionale benannte Parameter.

**class**

Gibt einen „class”-Attributwert für ein Stammelement an, das von diesem Tag gerendert wird.

**default**

Ein Standardwert, der gerendert werden soll für den Fall, dass das bearbeitbare Element keinen Wert enthält.

**escape**

Ein Boolescher Wert, der angibt, ob ein Wert, der von diesem Tag gerendert wird, HTML-codiert ist. Dies ist standardmäßig „false”.

**liquid**

Ein Boolescher Wert, der angibt, ob ein Liquid-Vorlagencode, der im Textwert gefunden und von diesem Tag gerendert wird, verarbeitet wird. Dies ist standardmäßig „true”.

**tag**

Der Name der Container-HTML-Tags, die von diese Tag gerendert werden. Dieses Tag rendert standardmäßig „div”-Elemente. Es wird allgemein empfohlen, dass Sie zwischen „div” oder „span” als Wert für diesen Parameter auswählen.

**title**

Gibt eine Beschriftung für dieses bearbeitbare Element innerhalb der Inhaltsbearbeitungsschnittstelle an. Wenn "Keine" angegeben ist, wird automatisch eine Anzeigebeschriftung generiert.

**type**

Ein Zeichenfolgenwert, der den Typ der darzustellenden Bearbeitungsschnittstelle für bearbeitbare Textwerte angibt. Gültige Werte für diesen Parameter sind „html” oder „text”. „html” ist der Standard.

## <a name="entitylist"></a>entitylist

Lädt eine bestimmte Liste mit Entitäten, nach Name oder ID. Auf die Eigenschaften der Entitätsliste kann dann mithilfe einer [entitylist](liquid-objects.md#entitylist) zugegriffen werden, die innerhalb des Tagblocks verfügbar ist. Zum Rendern der tatsächlichen Ergebnisdatensätze der Entitätsliste verwenden Sie den Tag [entityview](#entityview) im Block.  

Wenn die Liste mit Entitäten erfolgreich geladen wird, wird der Inhalt im Block gerendert. Wenn die Liste mit Entitäten nicht gefunden wird, wird der Inhalt im Block nicht gerendert.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
Standardmäßig erhält das „entitylist”-Objekt den Variablennamen „entitylist”. Optional kann ein anderer Variablenname angegeben werden.

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>Parameter

Geben Sie **nur eins** von „id”, „name” oder „key” an, um die zu ladende Entitätsliste auszuwählen.

**id**

Lädt eine Entitätsliste nach [GUID-ID](https://en.wikipedia.org/wiki/Globally_unique_identifier). „id” muss eine Zeichenfolge sein, die als GUID analysiert werden kann.  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

Im Allgemeinen werden literale GUID-Zeichenfolgen nicht verwendet. Stattdessen wird „id” mit einer GUID-Eigenschaft einer anderen Variable angegeben.

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**name**

Lädt eine Entitätsliste nach Namen.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**key**

Lädt eine Entitätsliste nach ID **oder** Namen. Wenn der bereitgestellte Schlüsselwert als eine [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier) analysiert werden kann, wird die Entitätsliste von der ID geladen. Andernfalls wird sie nach Namen geladen.

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**language\_code**

Ein ganzzahliger Power Apps-Sprachcode, um die lokalisierten Bezeichnungen der Entitätsliste, die geladen werden sollen, auszuwählen. Ohne Angabe von language\_code wird die Standardsprache der Power Apps-Verbindung der Portal-Anwendung verwendet.

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>entityview

Lädt eine bestimmte Power Apps-Ansicht, nach Name oder ID. Auf die Eigenschaften der Ansicht ߝ Ansichtsspaltenmetadaten, paginierte Ergebnisdatensätze, usw. kann dann mithilfe einer [entityview](liquid-objects.md#entityview) zugegriffen werden, die im Tag-Block verfügbar sein wird.  

Wenn die Ansicht erfolgreich geladen wird, wird der Inhalt im Block gerendert. Wenn die Ansicht nicht gefunden wird, wird der Inhalt im Block nicht gerendert.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Standardmäßig erhält das „entityview”-Objekt den Variablennamen „entityview”. Optional kann ein anderer Variablenname angegeben werden.

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

Wenn „entityview” innerhalb eines „entitylist”-Blocks geschachtelt ist, erbt es seine Standardkonfiguration (Ergebnisseitengröße, Filteroptionen, usw.) von der Entitätsliste. Werden keine „id”- oder „name”-Parameter der „entityview” bereitgestellt, wird die Standardansicht aus der einschließenden „entitylist” geladen.

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>Parameter

Stellen Sie **entweder** „id” **oder** „logical\_name” mit dem Namen zum Auswählen der Power Apps-Ansicht bereit, die geladen werden soll. Wenn keine der Optionen bereitgestellt wurde und das entityview-Tag in einem entitylist-Tag geschachtelt ist, wird die Standardansicht der einschließenden entitylist geladen.

**id**

„id” muss eine Zeichenfolge sein, die als GUID analysiert werden kann.

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

Im Allgemeinen werden literale GUID-Zeichenfolgen nicht verwendet. Stattdessen wird „id” mit einer GUID-Eigenschaft einer anderen Variable angegeben.

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**logical\_name**

Der logische Name der Power Apps-Entität der zu ladenden Ansicht. Muss in Verbindung mit „name” verwendet werden.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**name**

Der Power Apps-Name der zu ladenden Ansicht. Muss in Verbindung mit „logical\_name” verwendet werden.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**filter**

Gibt an, ob die Ansichtsergebnisse nach Benutzer oder Firma gefiltert werden. Muss den Zeichenfolgenwert "Benutzer" oder "Firma" enthalten.

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Ein allgemeiner Anwendungsfall ist das Festlegen dieses Parameters anhand einer [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**metafilter**

Gibt den Entitätslisten-Metadatenfilterausdruck an, nach dem die Ansichtsergebnisse gefiltert werden sollen. Dieser Parameter ist nur gültig, wenn „entityview” in Verbindung mit „entitylist” verwendet wird. In den meisten Fällen wird dieser Parameter anhand einer [request](liquid-objects.md#request) festgelegt.  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**order**

Gibt einen Sortierausdruck für die Sortierung von Ansichtsergebnissen an. Ein Sortierausdruck kann mindestens einen logischen Namen des Entitätsattributs enthalten, gefolgt von der Sortierreihenfolge ASC oder DESC.

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Ein allgemeiner Anwendungsfall ist das Festlegen dieses Parameters anhand einer [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page**

Gibt die zu ladende Ansichtsergebnisseite an. Wird dieser Parameter nicht angegeben, wird die erste Seite der Ergebnisse geladen.

Diesem Parameter muss entweder ein ganzzahliger Wert übergeben werden oder eine Zeichenfolge, die als Ganzzahl analysiert werden kann. Wenn ein Wert für diesen Parameter bereitgestellt wird, der Wert aber Null ist oder anderweitig nicht als Ganzzahl analysiert werden kann, wird die erste Seite der Ergebnisse geladen.

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Ein allgemeiner Anwendungsfall ist das Festlegen dieses Parameters anhand einer [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page\_size**

Gibt die Anzahl der Ergebnisse an, die für die aktuelle Ergebnisseite zu laden ist. Wenn kein Wert für diesen Parameter bereitgestellt wird und „entityview” in einem [entitylist](#entitylist)-Block verwendet wird, wird die Entitätslisten-Seitengröße verwendet. Wird diese nicht in einem „entitylist”-Block verwendet, wird als Standardwert 10 verwendet.

Diesem Parameter muss entweder ein ganzzahliger Wert übergeben werden oder eine Zeichenfolge, die als Ganzzahl analysiert werden kann. Wenn ein Wert für diesen Parameter bereitgestellt wird, der Wert aber Null ist oder anderweitig nicht als Ganzzahl analysiert werden kann, wird die Standardseitengröße verwendet.

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Ein allgemeiner Anwendungsfall ist das Festlegen dieses Parameters anhand einer [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**search**

Gibt einen Suchausdruck an, nach dem die Ansichtsergebnisse gefiltert werden. Einfache Stichwortsuchausdrücke filtern, ob Attribute mit dem Schlüsselwort beginnen. Platzhalter \* können auch im Ausdruck eingeschlossen werden.

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

Ein allgemeiner Anwendungsfall ist das Festlegen dieses Parameters anhand einer [request](liquid-objects.md#request), sodass der Suchfilter anhand der Benutzereingabe festgelegt werden kann.  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**enable\_entity\_permissions**

Gibt an, ob die Entitätsberechtigungsfilterung für Ansichtsergebnisse angewendet wird. Dieser Parameter ist standardmäßig auf „false” festgelegt. Wird „entityview” in einem „entitylist”-Block verwendet, wird der Wert dieses Parameters von der Entitätslistenkonfiguration geerbt.

Diesem Parameter muss entweder ein [boolean](liquid-types.md#boolean) Wert übergeben werden oder eine Zeichenfolge, die als boolescher Wert ("true", "false") analysiert werden kann. Wenn ein Wert für diesen Parameter bereitgestellt wird, der Wert aber Null ist oder anderweitig nicht als boolescher Wert analysiert werden kann, wird „false” als Standard verwendet.  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**language\_code**

Ein ganzzahliger Power Apps-Sprachcode, um die zu ladenden lokalisierten Bezeichnungen der Entitätsansicht (Spaltenüberschriftsbezeichnungen, usw.) auszuwählen. Ohne Angabe von language\_code wird die Standardsprache der Power Apps-Verbindung der Portal-Anwendung verwendet.

Wenn „entityview” innerhalb eines „entitylist”-Blocks verwendet wird, erbt „entityview” die Sprachcodekonfiguration von „entitylist”.

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>searchindex

Führt eine Abfrage für den Portalsuchindex aus. Auf die passenden Ergebnisse kann dann mithilfe eines [searchindex](liquid-objects.md#searchindex) zugegriffen werden, der innerhalb des Tag-Blocks verfügbar ist.  

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

Standardmäßig erhält das Suchindex-Objekt den Variablennamen „searchindex”. Optional kann ein anderer Variablenname angegeben werden.

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>Parameter

Das „searchindex”-Tag akzeptiert die folgenden Parameter.

**query**

Die Abfrage für Ergebnisübereinstimmungen. Dieser Parameter soll den vom Benutzer angegebenen Teil der Indexabfrage (sofern zutreffend) annehmen.

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

Ein allgemeiner Anwendungsfall ist das Festlegen dieses Parameters anhand einer [request](liquid-objects.md#request).  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

Dieser Parameter unterstützt die [Lucene-Abfrageanalysesyntax](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

**filter**

Eine zusätzliche Abfrage für Ergebnisübereinstimmungen. Dieser Parameter soll einen vom Entwickler angegebenen Filter für Ergebnisse annehmen (bei Bedarf).

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

Dieser Parameter unterstützt die [Lucene-Abfrageanalysesyntax](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).  

> [!Note]     
> Der Unterschied zwischen „filter” und „query” ist, dass, während beide die Lucene-Abfrageanalysesyntax akzeptieren, „query” mehr Spielraum für die Analyse dieser Syntax gewährt ߝ, da erwartet wird, dass sich die meisten Endbenutzer sich dieser Syntax nicht bewusst sind. Wenn also die Analyse von „query” gemäß dieser Syntax fehlschlägt, wird die gesamte Abfrage umgangen und als Abfragetext übermittelt. „filter” wird dagegen strikt analysiert und im Falle einer ungültigen Syntax einen Fehler zurückgeben.

**logical\_names**

Die logischen Namen der Power Apps-Entität, auf die die passenden Ergebnisse beschränkt werden, als durch Trennzeichen getrennte Zeichenfolge. Wenn sie nicht angegeben werden, werden alle entsprechenden Entitäten zurückgegeben.

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**page**

Die Suchergebnisseite, die zurückgegeben werden soll. Wenn sie nicht angegeben wird, wird die erste Seite (1) zurückgegeben.

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

Ein allgemeiner Anwendungsfall ist das Festlegen dieses Parameters anhand einer [request](liquid-objects.md#request).  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**page\_size**

Die Größe der Ergebnisseite, die zurückgegeben werden soll. Wenn sie nicht angegeben wird, wird die Standardgröße 10 verwendet.

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

Vollständiges Rendern einer Power Apps-konfigurierten Entitätsform, nach Name oder ID.  

> [!Note]
> Das „entityform”-Tag ist nur für die Verwendung in Inhalten verfügbar, die in einer <em>[web template](store-content-web-templates.md)–</em>basierten Seitenvorlage gerendert werden. Wenn Sie versuchen, das Tag in einer Rewrite-basierten Seitenvorlage zu verwenden, wird kein Render-Vorgang ausgeführt. Sie können nur ein einziges „entityform”- oder „webform”-Tag pro Seite rendern. „entityform”- oder „webform”-Tags nach dem ersten werden nicht gerendert.       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>Parameter

**name**

Der Name des zu ladenden Entitätsformulars.

`{% entityform name:My Entity Form %}`

## <a name="webform"></a>webform

Rendert vollständig ein Power Apps-konfiguriertes Webformular, nach Name oder ID. Das „webform”-Tag ist nur für die Verwendung in Inhalten verfügbar, die in einer [web template](store-content-web-templates.md)–basierten Seitenvorlage gerendert werden. Wenn Sie versuchen, das Tag in einer Rewrite-basierten Seitenvorlage zu verwenden, wird kein Render-Vorgang ausgeführt. Sie können nur ein einziges „entityform”- oder „webform”-Tag pro Seite rendern. „entityform”- oder „webform”-Tags nach dem ersten werden nicht gerendert.                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>Parameter

**name**

Der Name des zu ladenden Webformulars.

`{% webform name:My Web Form %}`


### <a name="see-also"></a>Siehe auch

[Ablaufsteuerungstags](control-flow-tags.md)<br>
[Iterationstags](iteration-tags.md)<br>
[Variable Tags](variable-tags.md)<br>
[Vorlagentags](template-tags.md)
