---
title: Verwenden von Liquid-Objekten für ein Portal | MicrosoftDocs
description: Lesen Sie mehr zu den verfügbaren Liquid-Objekten in einem Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 4f741c8db2c0f73df8ee10c16793df78d4d58625
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108280"
---
# <a name="available-liquid-objects"></a>Verfügbare Liquid-Objekte

Liquid-Objekte enthalten Attribute für die Ausgabe von dynamischem Inhalten auf einer Seite. Beispielsweise hat das Seiten-Objekt ein Attribut namens Titel, mit dem der Titel der aktuellen Seite ausgegeben werden kann.

Um auf ein Objektattribut anhand des Namens zuzugreifen, verwenden Sie einen Punkt . Um ein Objektattribut in einer Vorlage zu rendern, setzen Sie es zwischen {{ und }}.

```
{{ page.title }}
```
Auf Attribute eines Objekts kann auch mithilfe eines Zeichenfolgennamens und mit \[\] zugegriffen werden. Dies ist hilfreich in Fällen, in denen das gewünschte Attribut dynamisch ermittelt wird, oder in denen der Attributname Zeichen, Leerzeichen, Sonderzeichen usw. enthält, die bei Verwendung der .-Syntax ungültig wären.

```
{{ page[title] }}

{% assign attribute_name = Name with spaces %}

{{ object[attribute_name] }}
```

Auf die folgenden Objekte kann an beliebiger Stelle, in einer beliebigen Vorlage zugegriffen werden.


|   Objekt    |                                                                                                                                                                                          Beschreibung                                                                                                                                                                                           |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Entitäten   |                                                                                                 Ermöglicht das Laden einer beliebigen Power Apps-Entität nach ID. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [entities](#entities)                                                                                                 |
|     now     |                                          Ein Datums-/Uhrzeitobjekt, das auf die aktuelle UTC-Zeit verweist, zum Zeitpunkt des Renderns der Vorlage.<br>**Hinweis**: Dieser Wert wird in der Portal-Web-App zwischengespeichert und nicht jedes Mal aktualisiert. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Datumsfilter](liquid-filters.md#date-filters)                                          |
|    Seite     | Verweist auf die aktuelle Portalanforderungsseite. Das Objekt page bietet Zugriff auf Dinge wie die Breadcrumbs für die aktuelle Seite, den Titel oder die URL der aktuellen Seite und alle anderen Attribute oder verbundenen Entität des zugrunde liegenden Power Apps-Datensatzes. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Seite](#page) |
|   Parameter    |                                                                                                                             Eine bequeme Verknüpfung für request.params. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Anforderung](#request)                                                                                                                              |
|   Anfrage   |                                                                                                                        Enthält Informationen zum aktuellen HTTP-Request. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Anforderung](#request)                                                                                                                        |
|  Einstellungen   |                                                                                                            Ermöglicht das Laden einer beliebigen [Website-Einstellung](../configure/configure-site-settings.md) nach Namen. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Einstellungen](#settings)                                                                                                            |
|   Siteübersicht   |                                                                                                                               Ermöglicht Zugriff auf die Portalsiteübersicht. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Sitemap](#sitemap)                                                                                                                                |
| Websitemarkierungen |                                                                                                                        Ermöglicht das Laden einer beliebigen Websitemarkierung nach Namen. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Sitemarkers](#sitemarkers)                                                                                                                        |
|  Ausschnitte   |                                                                                                         Ermöglicht das Laden von [Inhaltsausschnitten](../configure/customize-content-snippets.md) nach Namen. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Ausschnitte](#snippets)                                                                                                         |
|    Benutzer     |                             Verweist auf den aktuellen Portalbenutzer und ermöglicht Zugriff auf alle Attribute des zugrunde liegenden Power Apps-Kontaktdatensatzes. Wenn kein Benutzer angemeldet ist, ist diese Variable [Null](liquid-types.md#null). [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Benutzer](#user)                              |
|  Weblinks   |                                                                                                                        Ermöglicht das Laden eines beliebigen Weblinksatzes nach Namen oder ID. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Weblinks](#weblinks)                                                                                                                        |
|   Website   |                                                      Verweist auf den Portal-Websitedatensaz und ermöglicht Zugriff auf alle Attribute des Power Apps Website-(adx\_website)-Datensatzes für das Portal. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Website](#website)                                                       |

## <a name="ads"></a>Anzeigen


Bietet die Möglichkeit, auf eine Anzeige zuzugreifen und sie zu rendern.

Das Objekt das ermöglicht die Auswahl einer bestimmten Anzeige oder Anzeigenplatzierung:

```
<div>

{% assign ad = ads[Ad Name] %}

<h4>{{ ad.title }}</h4>

<a href={{ ad.redirect_url }}>

<img src={{ ad.image.url }} alt={{ ad.image.alternate_text }} />

</a>

</div>
```

### <a name="ads-attributes"></a>Anzeigenattribute

|Attribut   |Beschreibung   |
|---|---|
| placements        | Gibt das adplacements-Objekt zurück.    |
| \[Anzeigenname oder -ID\] | Sie können auf jede beliebige Anzeige über ihre Namens- oder ID-Eigenschaften zugreifen. <br> `{% assign ad = ads[Ad Name] %}`<br>`{% assign ad = ads["da8b8a92-2ee6-476f-8a21-782b047ff460"] %}`  |


### <a name="ad-placements-attributes"></a>Attribute von Anzeigenplatzierungen

|Attribut   |Beschreibung   |
|---|---|
| \[Anzeigenplatzierungsname oder -ID\] | Sie können auf jede beliebige Anzeigenplatzierung über ihre Namens- oder ID-Eigenschaften zugreifen.<br>`{% assign placement = ads.placements[Placement Name or Id] %}`<br>`{% assign placement = ads.placements[2423d713-abb3-44c3-8a7d-c445e16fccad] %}`  |

### <a name="ad-placement-attributes"></a>Attribute von Anzeigenplatzierungen

Eine ad placement ist ein Entitätsobjekt mit allen gleichen Attributen, zusätzlich zu den unten aufgeführten.

|Attribut   |Beschreibung   |
|---|---|
| Anzeigen            | Gibt die Sammlung von Anzeigenobjekten zurück, die mit der Platzierung verbunden sind.  [Iterationtags](iteration-tags.md) und [Arrayfilter](liquid-filters.md#array-filters) werden möglicherweise mit dieser Sammlung verwendet.  |  
| Name           | Gibt das Feld "Name" für die Anzeigenplatzierung zurück.                                                                |
| placement\_url | Die URL, mit der die Anzeigenplatzierung abgerufen werden kann, die vollständig über eine Vorlage gerendert wird.                         |
| random\_url    | Die URL, mit der eine willkürliche Anzeige aus der Platzierung abgerufen werden kann, die vollständig über eine Vorlage gerendert wird.           |

### <a name="ad-attributes"></a>Anzeigenattribute

> [!Note]
> Ein ad ist ein Entitätsobjekt mit allen gleichen Attributen, zusätzlich zu den unten aufgeführten.

|Attribut   |Beschreibung   |
|---|---|
| ad\_url |  Die URL, mit der die Anzeig abgerufen werden kann, die vollständig über eine Vorlage gerendert wird.   |
| Kopieren| Gibt das Feld "Kopie" für die Anzeige zurück.|
| image| Gibt das Bildobjekt für die Anzeige zurück (sofern vorhanden).|
| Name| Gibt das Feld "Name" für die Anzeige zurück.|
| open\_in\_new\_window | Gibt "true" zurück, wenn die URL, die von redirect\_url angegeben ist, in einem neuen Fenster geöffnet werden soll. |
| redirect\_url| Die URL, an die der Benutzer verwiesen wird auf, indem er auf die Anzeige klickt.|

### <a name="ad-image-attributes"></a>Anzeigenbildattribute

|Attribut   |Beschreibung   |
|---|---|
| alternate\_text | Gibt den Text zurück der im alt-Attribut des Tags angezeigt werden soll. |
| height          | Gibt die Höhe für das Bild in Pixeln zurück                             |
| URL             | Gibt die URL-Quelle für das Bild zurück.                                  |
| width           | Gibt die Breite für das Bild in Pixeln zurück                              |


## <a name="blogs"></a>Blogs

Stellt die Möglichkeit zur Verfügung, Blogs und Blog-Beiträge aufzurufen und zu rendern.

Das Objekt blogs ermöglicht die Auswahl eines bestimmten Blogs oder Blog-Beitrags.

```
{% assign posts = blogs.posts | paginate: 0,4 %}

<div class=content-panel panel panel-default>

<div class=panel-heading>

{% assign sitemarker = sitemarkers[Blog Home] %}

{% assign snippet = snippets[Home Blog Activity Heading] %}

<a class=pull-right href={{sitemarker.url}}> All Blogs </a>

<h4>

<a class=feed-icon fa fa-rss-square href={{ blogs.feedpath }} />

{{ snippet.adx_value }}

</h4>

</div>

<ul class=list-group>

{% for post in posts.all %}

<li class=list-group-item >

<a class=user-avatar href={{ post.author_url }}>

<img src={{ post.user_image_url }} />

</a>

<h4 class=list-group-item-heading>

<a href={{ post.app_relative_path }}>{{ post.title }}</a>

</h4>

<div class=content-metadata>

<abbr class=timeago>{{ post.publish_date }}</abbr>

&ndash;

<a href={{ post.author_url }}> {{ post.author_name }} </a>

&ndash;

<a href={{ post.application_path }}#comments>

<span class=fa fa-comment aria-hidden=true></span> {{ post.comment_count }}

</a>

</div>

</li>

{% endfor %}

</ul>

</div>
```

### <a name="blogs-object"></a>blogs-Objekt

Das Blogs-Objekt ermöglicht Ihnen den Zugriff auf spezielle Blogs im Portal oder auf alle Blog-Aritkel im Portal (unabhängig vom Blog).

In der folgenden Tabelle werden die Attribute zum blogs-Objekt beschrieben.

|Attribut   |Beschreibung   |
|---|---|
| Beiträge               | Gibt ein blogposts-Objekt zurück, das alle Blog-Beiträge im Portal enthält.     |
| \[Blogname oder -ID\] | Sie können auf jeden Blog über dessen Namens- oder ID-Eigenschaften zugreifen.                   

```
{% assign blog = blogs[Blog Name] %}                             

{% assign blog = blogs[da8b8a92-2ee6-476f-8a21-782b047ff460] %}  |
```

### <a name="blog-object"></a>blog-Objekt

Das Blog-Objekt ermöglicht Ihnen die Arbeit mit einem einzelnen Blog, wobei Sie auf die Beiträge für dieses Blog zugreifen können.

In der folgenden Tabelle werden die Attribute zum Blog-Objekt beschrieben.

|Attribut   |Beschreibung   |
|---|---|
| posts | Gibt ein blogposts-Objekt zurück, das alle Blog-Beiträge enthält. |
| Name  | Der Name des Blogs.                                              |
| title | Der Titel des Blogs                                             |
| URL   | Die URL des Blogs.                                               |

### <a name="blogposts-object"></a>blogposts-Objekt

Das Blogposts-Objekt ermöglicht Ihnen, auf eine Sammlung von blogpost-Objekten zuzugreifen. Sie können auch die Blog-Beiträge sortieren und eine Paginierung mithilfe von Liquid-Filtern umsetzen:

{% assign blogposts = blogs.posts | order\_by “adx\_name”, “desc” | paginate: 0,4 | all %} Hinweis: blogs.post ist euch eine Möglichkeit, um all Blogbeiträge abzurufen blogs.posts from\_index: 0 | take: 2 ist auch möglich

In der folgenden Tabelle werden die Attribute zum blogposts-Objekt beschrieben.

|Attribut   |Beschreibung   |
|---|---|
| Alle | Gibt alle blogposts-Objekte in der Sammlung zurück. |

### <a name="blogpost-object"></a>blogpost-Objekt

Verweist auf einen einzelnen Blog-Beitrag.

In der folgenden Tabelle werden die Attribute zum blogpost-Objekt beschrieben.

|Attribut   |Beschreibung   |
|---|---|
| URL            | Die URL des Beitrags.                                                                |
| content        | Gibt das Feld "Content" für den Beitrag zurück.                                             |
| content        | Gibt das Feld "Content" für den Beitrag zurück.                                             |
| author         | Gibt den Autor für den Beitrag zurück (ein Kontakt-Entität-Objekt).          |
| title          | Der Titel des Beitrags.                                                              |
| comment\_count | Gibt als ganzzahligen Wert die Anzahl an Kommentaren für den Beitrag zurück. |
| publish\_date  | Das Datum, an dem der Beitrag veröffentlicht wurde.                                           |

## <a name="entities"></a>Entitäten

Ermöglicht das Laden einer beliebigen Power Apps-Entität nach ID. Wenn die Entität vorhanden ist, wird ein Entitätsobjekt zurückgegeben. Wird eine Entität mit der angegebenen ID nicht gefunden, wird [Null](liquid-types.md#null)  zurückgegeben.  

```
{% assign account = entities.account['936DA01F-9ABD-4d9d-80C7-02AF85C822A8'] %}

{% if account %}

{{ account.name }} ({{ account.statecode.label }})

{% endif %}

{% assign entity_logical_name = 'contact' %}

{% assign contact = entities[entity_logical_name][request.params.contactid] %}

{% if contact %}

{{ contact.fullname }} ({{ contact.parentcustomerid.name }})

{% endif %}
```

### <a name="entity"></a>Entity

Ein Entitätsobjekt bietet Zugriff auf die Attribute eines Power Apps-Entitätsdatensatzes.


|             Attribut              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                 Kennung                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Die GUID-ID einer Entität als Zeichenfolge. Beispielsweise 936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|           logical\_name            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   Der Power Apps logische Name der Entität.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|               Notizen                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Lädt alle Notizen (Anmerkungen), die der Entität zugeordnet sind von der ältesten zur neuesten (createdon). Notizen werden als Notizenobjekte zurückgegeben.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|            Berechtigungen             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Lädt Entitätsberechtigungsassertions-Ergebnisse für die Entität. Ergebnisse werden als Berechtigungsobjekt zurückgegeben.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                URL                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Gibt den URL-Pfad des Content Management Systems des Power Apps-Portals für die Entität zurück. Wenn die Entität in der aktuellen Website keine gültige URL hat, wird Null zurückgegeben. Im Allgemeinen wird nur einen Wert für bestimmte Entitätstypen zurückgegeben, die in das Portal-CMS integriert wurden, solange Sie den URL-Anbieter in Ihrer Anwendung angepasst haben.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| \[Attribut- oder Beziehungsname\] | Sie können auf ein beliebiges Attribut der Power Apps-Entität nach logischem Namen zugreifen. `{{ entity.createdon }}{% assign attribute_name = 'name' %}{{ entity[attribute_name] }}` <br>Die Werte der meisten Entitätsattribute werden direkt zu [Liquid-Typen](liquid-types.md) zugeordnet: Felder mit zwei Optionsmöglichkeiten werden booleschen Werten zugeordnet, Textfelder werden Zeichenfolgen zugeordnet, nummerische Felder/Währungsfelder werden Zahlen zugeordnet und Datum/Uhrzeit-Felder werden Datum-Objekten zugeordnet. Einige Attributtypen werden jedoch als Objekte zurückgegeben:<ul><li>Suchfelder (Entitätsreferenz) werden als Entitätsreferenzobjekte zurückgegeben.</li><li>Optionssatz-/Auswahllistenfelder werden als Optionssatzwertobjekte zurückgegeben.</li><li>Sie können beliebigen verknüpfte Entitäten über den Beziehungsschemanamen laden.</li>`{{ page.adx_webpage_entitylist.adx_name }}`Wenn eine Beziehung reflexiv ist (d.h. auf sich selbst verweist), wird ein Reflexivbeziehungsobjekt zurückgegeben. (Andernfalls wäre das Ergebnis mehrdeutig.)`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**Hinweis**: Das Laden großer Mengen von verknüpfte Entitäten oder der Zugriff auf viele Beziehungen in einer einzigen Vorlage können negative Auswirkungen auf die Renderleistung der Vorlage haben. Vermeiden Sie das Laden verknüpfte Entitäten für jeden Artikel in einem Array innerhalb einer Schleife. Wenn möglich, verwenden Sie [Power Apps common data service Entitäts-Tags](portals-entity-tags.md), um Sammlungen von Entitäten zu laden. |

### <a name="entity-reference"></a>Entitätsreferenz

Suchattributwerte werden mit den folgenden Attribute als Entitätsreferenzobjekte zurückgegeben.


|   Attribut   |                                                Beschreibung                                                |
|---------------|-----------------------------------------------------------------------------------------------------------|
|      Kennung       | Die GUID-ID einer Referenzentität als Zeichenfolge. <br> Beispielsweise 936DA01F-9ABD-4d9d-80C7-02AF85C822A8 |
| logical\_name |  Der logische Power Apps-Name der referenzierten Entität.   |
|     Name      |                           Das Attribut "Primärer Name" der referenzierten Entität.                            |

### <a name="note"></a>Notiz

Eine Notiz ist ein Entitätsobjekt, das Zugriff auf die Attribute und Beziehungen eines Anmerkungs-Datensatzes bereitstellt. Neben allen Attributen eines Entitätsobjektes hat es die folgende zusätzlichen Attribute.


|  Attribut   |                                                                                                                                                                                                                                  Beschreibung                                                                                                                                                                                                                                  |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| documentbody | Lädt das documentbody Attribut des Notiz-Anmerkung-Datensatzes als Base-64-codierte Zeichenfolge. Da der Inhalt dieses Attributs möglicherweise umfangreich sein kann, wird er nicht mit dem Rest der Notizenattribute geladen, sondern nur bei Bedarf. <br> **Hinweis**: Die Nutzung des documentbody-Attributs kann negative Auswirkungen auf die Renderleistung der Vorlage haben und sollte mit Vorsicht ausgeführt werden.<br>Verwenden Sie stattdessen das URL-Attribut, um wenn möglich eine Verknüpfung zu einer Notizenanlage bereitzustellen. |
|     URL      |                                                                                                                                   Gibt den URL-Pfad für den integrierten Portal-Notizanhang-Handler zurück. Wenn der Benutzer über die Berechtigung verfügt, und die Notiz einen Dateianhang hat, lädt die Anforderung dieser URL den Notizendateianhang herunter.                                                                                                                                    |

>[!Note]
> [Zusätzliche Filter](liquid-filters.md#additional-filters)                     

### <a name="option-set-value"></a>Optionssatzwert

Optionssatz-/Auswahllisten-Attributwerte werden mit den folgenden Attribute als Entitätsreferenzobjekte zurückgegeben.

| Attribut | Beschreibung                                                     |
|-----------|-----------------------------------------------------------------|
| Bezeichnung     | Die lokalisierte Beschriftung des Optionssatz-/Auswahllistenattributwerts. Beispiele, Aktiv|
| Wert     | Der Integer-Wert des Optionssatz-/Auswahllistenattributwerts. Zum Beispiel 0                                                           |

### <a name="entity-permissions"></a>Entitätsberechtigungen

Das Entitätsberechtigungsobjekt bietet Zugriff auf zusammengefasste Berechtigungsassertionsergebnisse für eine Entität.

| Attribut       | Beschreibung                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| can\_append     | Gibt „True“ zurück, wenn der aktuelle Benutzer die Berechtigung zum Anfügen von Datensätzen an Beziehungen dieses Datensatzes hat. Andernfalls wird „False“ ausgegeben.                                                                                              |
| can\_append\_to | Gibt „True“ zurück, wenn der aktuelle Benutzer die Berechtigung zum Anfügen dieses Datensatzes an eine Beziehung einer anderen Entität hat. Andernfalls wird „False“ ausgegeben.                                                                                      |
| can\_create     | Gibt „True“ zurück, wenn der aktuelle Benutzer die Berechtigung zum Erstellen neuer Datensätze dieses Entitätstyps hat. Andernfalls wird „False“ ausgegeben.                                                                                                      |
| can\_delete     | Gibt „True“ zurück, wenn der aktuelle Benutzer die Berechtigung zum Löschen dieses Datensatzes hat. Andernfalls wird „False“ ausgegeben.                                                                                                                          |
| can\_read       | Gibt „True“ zurück, wenn der aktuelle Benutzer die Berechtigung zum Lesen dieses Datensatzes hat. Andernfalls wird „False“ ausgegeben.                                                                                                                            |
| can\_write      | Gibt „True“ zurück, wenn der aktuelle Benutzer die Berechtigung zum Aktualisieren dieses Datensatzes hat. Andernfalls wird „False“ ausgegeben.                                                                                                                          |
| rules\_exist    | Gibt „True“ zurück, wenn die Berechtigungsergebnisse dieses Objekts auf explizit definierten Berechtigungsregeln basieren. Gibt „False“ zurück, wenn die Standardergebnisse nicht auf explizit definierten Berechtigungen basieren. |

### <a name="reflexive-relationship"></a>Reflexive Beziehung

Der Versuch reflexive (d.h. auf sich selbst verweisend) Beziehungen oder Entitäten zu laden gibt Objekte mit den folgenden Attributen zurück.

| Attribut     | Beschreibung                                                                                                   |
|---------------|---------------------------------------------------------------------------------------------------------------|
| is\_reflexive | Gibt „True“ zurück. Kann verwendet werden, um zu testen, ob ein Objekt, das über eine Beziehungen zurückgegeben wird, ist Reflexivbeziehungsobjekt ist. |
| referenced    | Gibt ein Array referenzierter Entitäten für die jeweilige Beziehung zurück.                                           |
| referencing   | Gibt eine referenzierende Entität für die jeweilige Beziehung zurück. Gibt Null zurück, wenn keine verweisende Entität vorhanden ist. Bei einer n: n-Beziehung wird ein Array aus referenzierenden Entitäten zurückgegeben.                          

## <a name="entitylist"></a>entitylist

Das entitylist-Objekt wird innerhalb der [Power Apps Common Data Service Entity Tags](portals-entity-tags.md) verwendet. Es bietet Zugriff auf alle Attribute einer bestimmten Liste mit Entitäten.  

> [!Note]                                                       
> [Rendern der Entitätsliste, die der aktuellen Seite zugeordnet ist](render-entity-list-current-page.md)

### <a name="attributes"></a>Attribute

> [!Note]
> [Entitäten](#entities)

|               Attribut               |                                                                                                                            Beschreibung                                                                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            create\_enabled            |                                                                                Gibt „True“ zurück, wenn das Erstellen neuer Datensätze für die Liste mit Entitäten konfiguriert ist. Andernfalls wird „False“ ausgegeben.                                                                                |
|              create\_url              |                                                                                          Gibt den konfigurierten URL-Pfad für einen Erstellungslink/-schaltfläche für die Liste mit Entitäten zurück.                                                                                          |
|            detail\_enabled            |                                                                         Gibt „True“ zurück, wenn eine Detailansicht für einzelne Datensätze für die Liste mit Entitäten konfiguriert ist. Andernfalls wird „False“ ausgegeben.                                                                          |
|         detail\_id\_parameter         |               Gibt den Abfragezeichenfolgen-Parameternamen zurück, der für die Datensatz-ID verwendet werden soll, wenn eine Datensatzdetailansichts-URL erstellt wird. Siehe [URL-Filter](liquid-filters.md#url-filters) für Details zur Verwendung von Liquid-Filtern zur URL-Erstellung. Beispiel: id                |
|             detail\_label             |                                                                                     Gibt die konfigurierte lokalisierte Beschriftung für Detailansichtslinks/-schaltflächen für die Liste mit Entitäten zurück.                                                                                     |
|              detail\_url              |                                                                                       Gibt den konfigurierten URL-Pfad für Detailansichtslinks/-schaltflächen für die Liste mit Entitäten zurück.                                                                                        |
|           empty\_list\_text           |                                                                                Gibt den konfigurierten lokalisierten Text zurück, der angezeigt werden soll, wenn die Entitätslistenansicht keine Ergebnisse zurückgibt.                                                                                |
|      enable\_entity\_permissions      |                                                                               Gibt „True“ zurück, wenn die Entitätsberechtigungsfilterung für diese Liste mit Entitäten aktiviert ist. Andernfalls wird „False“ ausgegeben.                                                                               |
|         entity\_logical\_name         |                                                 Gibt den logischen Power Apps-Entitätsnamen für Datensätze zurück, die von dieser Liste mit Entitäten angezeigt werden sollen. Beispiel: contact                                                 |
|   filter\_account\_attribute\_name    |                                            Gibt den logischen Attributsnamen für die Suche in Firmen zum Filtern von Ergebnisdatensätzen nach der übergeordneten Firma des aktuellen Portal-Benutzers zurück. Zum Beispiel: accountid                                            |
|         filter\_apply\_label          |                                                            Gibt die konfigurierte lokalisierte Beschriftung zurück, die für den Link/die Schaltfläche verwendet werden soll, der/die einen erweiterten Attributfilter für die Entitätslistenergebnisse anwendet.                                                            |
|          filter\_definition           |                      Gibt die JSON-Attributfilterdefinition für die Liste mit Entitäten zurück. Siehe [Entitäts-Listenfilter](liquid-filters.md#entity-list-filters) für Details zum Verwenden des metafilters-Liquid-Filters zur Verarbeitung dieser Definition.                       |
|            filter\_enabled            |                                                                               Gibt „True“ zurück, wenn die erweiterte Attributfilterung für die Liste mit Entitäten aktiviert ist. Andernfalls wird „False“ ausgegeben.                                                                               |
| filter\_portal\_user\_attribute\_name |                                                 Gibt den logischen Attributsnamen für die Suche an Kontakten zum Filtern von Ergebnisdatensätzen nach dem Kontakt des aktuellen Portal-Benutzers zurück. Beispiel: contactid                                                  |
|   filter\_website\_attribute\_name    |                                              Gibt den logischen Attributsnamen für die Suche an adx\_website zum Filtern von Ergebnisdatensätzen nach der Website des aktuellen Portals zurück. Beispiel: adx\_websiteid                                              |
|            language\_code             |                                               Gibt den ganzzahligen Power Apps-CRM-Sprachcode zurück, der verwendet wird, um alle lokalisierten Bezeichnungen für diese Liste mit Entitäten auszuwählen.                                                |
|              page\_size               |                                                                                                   Gibt die Größe der konfigurierten Ergebnisseite für die Liste mit Entitäten zurück.                                                                                                    |
|          primary\_key\_name           |                                                                                  Gibt den logischen Primärschlüsselattributnamen für Datensätze zurück, die von dieser Liste mit Entitäten angezeigt werden sollen.                                                                                  |
|            search\_enabled            |                                                                                         Gibt „True“ zurück, wenn die Suche für diese Liste mit Entitäten aktiviert ist. Andernfalls wird „False“ ausgegeben.                                                                                          |
|          search\_placeholder          |                                                                                        Gibt den konfigurierten lokalisierten Text für den Entitätslisten-Suchfeldplatzhalter zurück.                                                                                        |
|            search\_tooltip            |                                                                                             Gibt den konfigurierten lokalisierten Text für die Entitätslistensuch-QuickInfo zurück.                                                                                             |
|                 Ansichten                 |                                                                                           Gibt die verfügbaren Ansichten für die Entitätsliste als Entitätslisten-Ansichtsobjekte zurück.                                                                                           |
|      \[Logischer Attributname\]       | Sie können ein beliebiges Attribut der Entitätsliste (adx\_Entitätsliste)Power Apps-Datensatzes der Liste nach logischem Namen aufrufen, genau wie bei [Entitäts](liquid-objects.md#entity) objekten. Beispielsweise {{ entitylist.adx\_name }} |

### <a name="entity-list-view-attributes"></a>Entitätslisten-Ansichtsattribute

|          Attribut          |                                                                                     Beschreibung                                                                                     |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           columns           |                                                         Gibt die Spalten der Ansicht als Entitätslisten-Ansichtsspaltenobjekte zurück.                                                         |
|    entity\_logical\_name    |               Gibt den logischen Power Apps-Entitätsnamen für die Datensätze zurück, die in der Ansicht enthalten sind. Beispiel: contact                |
|             Kennung              |                                                                          Gibt die GUID-ID der Ansicht zurück.                                                                           |
|       language\_code        | Gibt den ganzzahligen Power Apps-Sprachcode zurück, der verwendet wird, um alle lokalisierten Bezeichnungen (Spaltenüberschriften usw.) für die Ansicht auszuwählen. |
|            Name             |                                          Gibt den Power Apps-Anzeigenamen der Ansicht zurück.                                          |
| primary\_key\_logical\_name |        Gibt den logischen Power Apps-Entitäts-Primärschlüsselnamen für die Datensätze zurück, die in der Ansicht enthalten sind. Beispiel: contactid         |
|      sort\_expression       |                                               Gibt den Standardsortierausdruck für die Ansicht zurück. Beispielsweise nameASC, createdon DESC                                               |

### <a name="entity-list-view-column-attributes"></a>Entitätslisten-Ansichtsspaltenattribute

|    Attribut     |                                                                                    Beschreibung                                                                                    |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| attribute\_type  | Gibt den Power Apps-Attributtypnamen als Zeichenfolge für die Spalte zurück. Beispielsweise Lookup, Picklist, String, Boolean, DateTime |
|  logical\_name   |                       Gibt den logischen Power Apps-Attributnamen für die Spalte zurück. Beispielsweise createdon                       |
|       Name       |                      Gibt den lokalisierten Power Apps-Anzeigenamen für die Spalte zurück. Beispielsweise Created On                       |
| sort\_ascending  |                                      Gibt eine Sortierausdruckszeichenfolge für die Sortierung der Spalte in aufsteigender Reihenfolge zurück. Beispielsweise createdon ASC                                       |
| sort\_descending |                                     Gibt eine Sortierausdruckszeichenfolge für die Sortierung der Spalte in absteigender Reihenfolge zurück. Beispielsweise createdon DESC                                      |
|  sort\_disabled  |                                                   Gibt „True“ zurück, wenn die Sortierung für die Spalte deaktiviert ist. Andernfalls wird „False“ ausgegeben.                                                    |
|  sort\_enabled   |                                                    Gibt „True“ zurück, wenn die Sortierung für die Spalte aktiviert ist. Andernfalls wird „False“ ausgegeben.                                                    |
|      width       |                                                              Gibt die konfigurierte Breite für die Spalte in Pixeln zurück.                                                              |

## <a name="entityview"></a>entityview

Das entityview-Objekt wird innerhalb des entityview-Tags verwendet und bietet Zugriff auf die Metadaten für die Ansicht sowie die Anzeigeergebnisdatensätze.

### <a name="attributes"></a>Attribute

|          Attribut          |                                                                               Beschreibung                                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           columns           |                         Gibt die Spalten in der Ansicht als [entitylist-Ansichtsspaltenobjekte](liquid-objects.md#entity-list-view-column-attributes) zurück.                          |
| entity\_permission\_denied  | Gibt „True“ zurück, wenn der Zugriff auf die Ansichtsergebnisse aufgrund unzureichender Entitäts-Berechtigungen für den aktuellen Benutzer verweigert wurde. Gibt „False“ zurück, wenn der Lesezugriff auf Ansichtsergebnisse erteilt wurde. |
|    entity\_logical\_name    |                   Der logische Name der Power Apps-Entität der Ansichtsergebnisdatensätze. Beispiel: contact                   |
|         first\_page         |                 Die Seitenzahl der ersten Seite der Ansichtsergebnisse. Das ist 1, es sei denn, es wurden keine Ergebnisse zurückgegeben. In diesem Fall ist es Null.                  |
|             Kennung              |                            Die GUID-ID der Power Apps-Ansicht, die diese entityview definiert.                             |
|       language\_code        |             Der Sprachcode für Ganzzahlen von Power Apps, der verwendet wird, um lokalisierte Bezeichnungen für die aktuelle Ansicht zu laden.              |
|         last\_page          |                                 Die Seitenzahl der letzten Seite der Ansichtsergebnisse. Wenn keine Ergebnisse zurückgegeben wurden, ist dies Null.                                  |
|            Name             |              Der Name der Power Apps-Ansicht, die diese entityview definiert, beispielsweise Active Contacts               |
|         next\_page          |                                Die Seitenzahl der nächsten Seite der Ansichtsergebnisse. Ist keine nächste Seite mit Ergebnissen vorhanden, ist dies Null.                                 |
|            Seite             |                                                           Die Seitenzahl der aktuellen Seite der Ansichtsergebnisse.                                                           |
|            pages            |                                          Gibt ein Array von Seitenzahlen zurück, die alle Ergebnisseiten der aktuellen Ansicht enthalten.                                          |
|         page\_size          |                                                      Die Anzahl an Ergebnissen, die pro Seite für die aktuelle Ansicht zurückgegeben werden.                                                       |
|       previous\_page        |                              Die Seitenzahl der nächsten Seite der Ansichtsergebnisse. Ist keine vorherige Seite mit Ergebnissen vorhanden, ist dies Null.                               |
| primary\_key\_logical\_name |  Der logische Power Apps-Name des Primärschlüsselattributs der Ergebnisentität für diese Ansicht. Beispiel: contactid   |
|           Datensätze           |                                                   Die aktuelle Seite der Ergebnisdatensätze für die Ansicht als Entitätsobjekte.                                                    |
|      sort\_expression       |                                             Der Standardsortierausdruck für die Ansicht. Beispielsweise nameASC, createdon DESC.                                              |
|        total\_pages         |                                                              Die Gesamtanzahl an Ergebnisseiten für die Ansicht.                                                              |
|       total\_records        |                                                       Die Gesamtanzahl an Ergebnissen für die Ansicht (über alle Seiten).                                                       |

## <a name="events"></a>ereignisse

Bietet die Möglichkeit, auf Ereignisse zuzugreifen und sie zu rendern. Das events-Objekt ermöglicht die Auswahl eines bestimmten Ereignisses oder alle Ereignisse.

### <a name="events-object"></a>events-Objekt

Das events-Objekt ermöglicht Ihnen den Zugriff auf spezielle Ereignisse im Portal oder auf alle Ereignisse im Portal (unabhängig vom Ereignis).

Das events-Objekt hat die folgenden Attribute:

|Attribut   |Beschreibung   |
|---|---|
|occurences |Gibt ein eventoccurancess-Objekt zurück, das alle Ereignisse im Portal enthält. |
|[Ereignisname oder -ID] |Sie können auf jedes Ereignis über dessen Namens- oder ID-Eigenschaften zugreifen.<br>{% assign event = events[&quot;Ereignisname&quot;] %}<br>{% assign event = events[&quot;da8b8a92-2ee6-476f-8a21-782b047ff460&quot;] %} |

### <a name="event-object"></a>event-Objekt

Das event-Objekt ermöglicht Ihnen die Arbeit an einem einzelnen Ereignis, wobei Sie auf die Zeitpläne und Vorkommen für dieses Ereignis zugreifen können.

Das event-Objekt hat die folgenden Attribute:

|Attribut   |Beschreibung   |
|---|---|
| Vorkommen | Gibt ein eventoccurrences-Objekt zurück, das alle Vorkommen für das Ereignis enthält. |
| Name       | Der Name des Ereignisses.                                                     |
| URL        | Die URL des Ereignisses.                                                      |

### <a name="eventoccurences-object"></a>eventoccurences-Objekt

Das eventoccurrences -Objekt ermöglicht Ihnen, auf eine Sammlung von Ereignis-Instanz-Objekten zuzugreifen. Sie können die Ereignisvorkommen sortieren und einen Datumsbereich angeben, sodass eine Paginierung erreicht wird und Liquid-Filtern verwendet werden können,

```
{% assign occurances = event.occurrences.from[today].to[advance_date] %}
```

beachten Sie, dass

```
{% assign occurances = event.occurrences.min[today].max[advance_date] %}
```

auch möglich ist.

Nachfolgende Attribute sind dem eventoccurrences-Objekt zugeordnet

|Attribut   |Beschreibung   |
|---|---|
| Alle | Gibt alle eventoccurance-Objekte in der Sammlung zurück. |

### <a name="eventoccurence-object"></a>eventoccurence-Objekt

Stellt ein einzelnes Ereignisvorkommen dar. Die zugeordnete Attribute:

|Attribut   |Beschreibung   |
|---|---|
| URL                 | Die URL des Vorkommens.    |
| is\_all\_day\_event | Betriff das Ereignis einen ganzen Arbeitstag?     |
| start\_time         | Die Startzeit für das Ereignis. |
| end\_time           | Die Endzeit für das Ereignis.   |


## <a name="forloop"></a>forloop

Enthält Eigenschaften, die mit einem [für](iteration-tags.md#for)  Loop-Block nützlich sind.  

> [!Note]
> forloop kann nur innerhalb einer [für ](iteration-tags.md#for)-Tags verwendet werden.

**Code**

```
{% for child in page.children %}

{% if forloop.first %}

This is the first child page!

{% else %}

This is child page number {{ forloop.index }}.

{% endif %}

{% endfor %}
```

**Ausgabe**

```
This is the first child page!

This is child page number 2.

This is child page number 3.
```

### <a name="attributes"></a>Attribute

|Attribut   |Beschreibung   |
|---|---|
| erste   | Gibt „True“ zurück, wenn es sich um den ersten Schleifendurchlauf handelt. Gibt „False“ zurück, wenn es sich nicht um den ersten Schleifendurchlauf handelt.       |
| index   | Die Position des aktuellen Elements in der Sammlung (das ersten Element hat die Position 1).                   |
| index0  | Die Position des aktuellen Elements in der Sammlung (das ersten Element hat die Position 0).                   |
| Letzter    | Gibt „True“ zurück, wenn es sich um den letzten Schleifendurchlauf handelt. Gibt „False“ zurück, wenn es sich nicht um den letzten Schleifendurchlauf handelt.         |
| length  | Gibt die Anzahl der Durchlaufe der Schleife zurück ߝ Die Anzahl der Elemente in der Sammlung, die durchlaufen werden. |
| rindex  | Anzahl der Elemente, die noch in der Schleife verbleiben (Länge - Index), wobei 1 der Index des letzten Elements ist.              |
| rindex0 | Anzahl der Elemente, die noch in der Schleife verbleiben (Länge - Index), wobei 0 der Index des letzten Elements ist.              |


## <a name="forums"></a>forums

Stellt die Möglichkeit zur Verfügung, Foren und Forenthreads aufzurufen und zu rendern. Beachten Sie, dass die Möglichkeit, Liquid zu verwenden, um Forumsdaten zu rendern, sich auf Beiträge erstreckt. Um aber eine neue Thread-Nachricht zu erstellen, müssen Sie eine ASP.NET-Internetformular-Seitenvorlage mit besagter integrierter Funktion verwenden (z. B. standardmäßige Forenthread- und Forenbeitrags-Seitenvorlagen).

Das forums-Objekt ermöglicht Ihnen, ein Forum oder Forenthreads auszuwählen:

```
<div class=content-panel panel panel-default>

<div class=panel-heading>

<h4>

<span class=fa fa-comments aria-hidden=true></span>

{{ snippets[Home Forum Activity Heading] | default: Forum Activity | h }}

</h4>

</div>

{% for forum in website.forums %}

<ul class=list-group>

<li class=list-group-item>

<div class=row>

<div class=col-sm-6>

<h4 class=list-group-item-heading><a href="{{ forum.url | h }}"> {{ forum.name | h }}</a></h4>

<div class=list-group-item-text content-metadata>{{ forum.adx_description | h }}</div>

</div>

<div class=col-sm-3 content-metadata>{{ forum.thread_count }} threads</div>

<div class=col-sm-3 content-metadata>{{ forum.post_count }} posts</div>

</div>

</li>

</ul>

{% endfor %}

</div>
```

### <a name="forums-object"></a>forums-Objekt

Das forums-Objekt ermöglicht Ihnen den Zugriff auf spezielle Foren im Portal oder auf alle Forenthreads im Portal (unabhängig vom Forum).

Das forum-Objekt ermöglicht Ihnen die Arbeit an einem einzelnen Forum, wobei Sie auf die Threads für dieses Forum zugreifen können.

Das forumthreads-Objekt ermöglicht Ihnen, auf eine Sammlung von forumthread-Objekten zuzugreifen. Sie können auch die Forenthreads sortieren und eine Paginierung erzielen mithilfe von Liquid-Filtern.

```
{% assign threads = forum.threads | order_by adx_name, desc | paginate: 0,4 | all %}
```

Ein einzelner Forenthread

Das forumposts-Objekt ermöglicht Ihnen, auf eine Sammlung von forumposts-Objekten zuzugreifen.

### <a name="attributes"></a>Attribute

|Attribut   |Beschreibung   |
|---|---|
| threads              | Gibt ein forumthreads-Objekt zurück, das alle forumthreads-Objekte im Portal enthält.             |
| Alle                  | Gibt alle forum-Objekte im Portal zurück. Beachten Sie, dass website.forums auch eine Entsprechung ist.    |
| thread\_count        | Gibt den ganzzahligen Wert der Anzahl an Threads der gesamten Website zurück. |
| post\_count          | Gibt den ganzzahligen Wert der Gesamtanzahl der Beiträge im Portal zurück.                       |
| \[Forumname oder -ID\] | Sie können auf jedes Forum über dessen Namens- oder ID-Eigenschaften zugreifen. <br>`{% assign forum = forums[Forumname] %}<br>{% assign forum = forums[da8b8a92-2ee6-476f-8a21-782b047ff460] %} 

### <a name="forum-object"></a>forum-Objekt

### <a name="attributes"></a>Attribute

> [!Note]
> [Entitäten](#entities)

|Attribut   |Beschreibung   |
|---|---|
| threads       | Gibt ein forumthreads-Objekt zurück, das alle Forenthreads für das Forum enthält.               |
| Name          | Der Name des Forums.                                                                  |
| thread\_count | Gibt den ganzzahligen Wert der Anzahl an Threads im Forum zurück.      |
| post\_count   | Gibt den ganzzahligen Wert der Anzahl an Beiträgen im gesamten Forum zurück. |

### <a name="forumthreads-object"></a>forumthreads-Objekt

### <a name="attributes"></a>Attribute

|Attribut   |Beschreibung   |
|---|---|
| Alle | Gibt alle forumthread-Objekte in der Sammlung zurück. |

### <a name="forumthread-object"></a>forumthread-Objekt

### <a name="attributes"></a>Attribute

> [!Note]
> [Entitäten](#entities)

|Attribut   |Beschreibung   |
|---|---|
| posts        | Gibt ein forumposts-Objekt zurück, das alle Forenbeiträge für den Thread enthält.            |
| author       | Gibt den Autor für den Thread zurück (ein Kontakt-Entität-Objekt).      |
| latest\_post | Gibt den aktuellen Beitrag im Thread zurück.                                            |
| first\_post  | Gibt den ersten Beitrag im Thread zurück.                                             |
| post\_count  | Gibt den ganzzahligen Wert der Anzahl an Beiträgen im Thread zurück. |
| is\_answered | Wurde der Thread beantwortet oder nicht?                                                    |
| is\_sticky   | Ist der Thread ein angehefteter Thread?                                                    |

### <a name="forumposts-object"></a>forumposts-Objekt

### <a name="attributes"></a>Attribute

|Attribut   |Beschreibung   |
|---|---|
| Alle | Gibt alle forumthread-Objekte in der Sammlung zurück. |

Ein einzelner Forenbeitrag

### <a name="attributes"></a>Attribute

> [!Note] 
> [Entitäten](#entities)

|Attribut   |Beschreibung   |
|---|---|
| author     | Gibt den Autor für den Beitrag zurück (ein einfaches Kontakt-Entität-Objekt). |
| content    | Der Textinhalt des Beitrags.                                                   |
| is\_answer | Ist dieser Beitrag eine Antwort zum Thread?                                      |


## <a name="knowledge"></a>knowledge

Bietet Zugriff auf Power Apps knowledgearticle und Kategorieentitätsdatensätze, um Artikel und Kategorien in einem Portal zu rendern.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---|---|
|Artikel|Gibt ein Artikelobjekt zurück, das Artikelobjekte für die knowledgearticle-Entitätsdatensätze enthält, die im Portal verfügbar sind.|
|categories|Gibt ein Kategorieobjekt zurück, das Kategorieobjekte für die Kategorieentitätsdatensätze enthält, die im Portal verfügbar sind.|
|||

### <a name="articles-object"></a>articles-Objekt

Mit dem Objekt articles können Sie auf eine Sammlung von article-Objekten zugreifen. Sie können die Artikel sortieren und paginieren sowie Liquid-Filter verwenden.

```
{% assign count = count | default: 3 %}
{% assign languagecode = website.selected_language.code %}
{% assign popular_articles = knowledge.articles | popular: count,languagecode  %}
{% if popular_articles %}
    <div class=list-group>
    {% for article in popular_articles %}
      <div class=list-group-item clearfix>
        <a class=title href={{ article.url | escape }}>{{ article.title | escape }}</a>
        <p class=description>{{ article.description | escape }}</p>
      </div>
    {% endfor %}
    </div>
{% endif %}
```

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---|---|
|popular |Gibt eine Sammlung von Artikelobjekten zurück, die die meisten Aufrufe enthalten. `{% assign popular_articles = knowledge.articles.popular %}` |
|recent |Gibt eine Sammlung von Artikelobjekten zurück, die das Datum der letzten Änderung enthalten. `{% assign recent_articles = knowledge.articles.recent %}` |
|Oben |Gibt eine Sammlung von Artikelobjekten zurück, die die höchsten Bewertungen enthalten. `{% assign top_articles = knowledge.articles.top  %}` |
| | |

### <a name="filters"></a>Filter

Die folgenden Filter können optionale Parameter für Seitengröße und Sprache akzeptieren. Der erste Parameter ist die Zahl der Datensätze, die abgerufen werden sollen. Die Standardseitengröße ist 5. Der zweite Parameter ist der Code einer Sprache, um Artikel für eine bestimmte Sprache abzurufen. Die Filter können mit anderen [Liquid-Filtern](liquid-filters.md) kombiniert werden.

```
{% assign page_size = 5 %}
{% assign language_code = website.selected_language.code %}
{% assign recent_articles = knowledge.articles | recent: page_size, language_code %}
```

|Attribut|Beschreibung|
|---|---|
|popular |Gibt eine Sammlung von Artikelobjekten zurück, die die meisten Aufrufe enthalten. `{% assign popular_articles = knowledge.articles \| popular: 10, en-US %}` |
|recent |Gibt eine Sammlung von Artikelobjekten zurück, die das Datum der letzten Änderung enthalten. `{% assign recent_articles = knowledge.articles \| recent: 5 %}` |
|Oben |Gibt eine Sammlung von Artikelobjekten zurück, die die höchsten Bewertungen enthalten. `{% assign top_articles = knowledge.articles \| top: 3, en-US %}` |
| | |

### <a name="categories-object"></a>categories-Objekt

Das categories-Objekt ermöglicht Ihnen, auf eine Sammlung von Kategorieobjekten zuzugreifen. Sie können die Kategorien sortieren und paginieren sowie Liquid-Filter verwenden.

```
{% assign category_url = sitemarkers['Category'].url %}
  {% assign count = count | default: 0 %}  
  {% assign categories = knowledge.categories | top_level: count %}
  {% if categories %}
    <div class=list-group unstyled>
    {% for category in categories %}
      <a href={{ category_url | add_query: 'id', category.categorynumber }} class=list-group-item>
        {{ category.title }}
      </a>
    {% endfor %}
    </div>
  {% endif %}
```

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---|---|
|recent |Gibt eine Sammlung von Kategorieobjekten zurück, die das Datum der letzten Änderung enthalten. |
|top_level |Gibt eine Sammlung von Kategorieobjekten zurück, die keine übergeordnete Kategorie besitzen. |
|||

### <a name="filters"></a>Filter

Die folgenden Filter können einen optionalen Parameter für die Seitengröße akzeptieren. Die Standardseitengröße ist 5. Die Filter können mit anderen [Liquid-Filtern](liquid-filters.md) kombiniert werden.

```
{% assign page_size = 5 %}
{% assign recent_categories = knowledge.categories | recent: page_size %}
```

|Attribut|Beschreibung|
|---|---|
|recent |Gibt eine Sammlung von Kategorieobjekten zurück, die das Datum der letzten Änderung enthalten. Sie können Parameter `{% assign recent_categories = knowledge.categories \| recent: 10 %}` angeben |
|top_level |Gibt eine Sammlung von Kategorieobjekten zurück, die keine übergeordnete Kategorie besitzen. `{% assign root_categories = knowledge.categories \| top_level %}` |
|||

### <a name="article-object"></a>article-Objekt

Mit dem Artikelobjekt können Sie mit einem einzelnen knowledgearticle arbeiten, um Details dieses Artikels im Portal anzuzeigen.

### <a name="attributes"></a>Attribute

article ist ein [entity](#entity)-Objekt mit den gleichen Attributen zusätzlich zu den unten aufgelisteten.

|Attribut|Beschreibung|
|---|---|
|article_public_number| Die öffentliche Artikelnummer des Artikels.|
|comment_count| Der ganzzahlige Wert für die Anzahl der Kommentare für einen bestimmten Artikel.|
|content|Der Inhalt des Artikels.|
|current_user_can_comment|Gibt einen booleschen Wert zurück, der angibt, ob der aktuelle Benutzer dem Artikel Kommentare hinzufügen kann.|
|is_rating_enabled|Gibt einen booleschen Wert zurück, der angibt, ob für einen Artikel Bewertungen aktiviert sind.|
|keywords|Die Schlüsselwörter für den Artikel.|
|Name|Ein alternativer Alias für den Titel des Artikels.|
|rating|Der Dezimalbewertungswert für den Artikel.|
|title|Der Titel des Artikels.|
|view_count|Der ganzzahlige Wert für die Häufigkeit, mit der der Artikel angezeigt wurde.|
|||

### <a name="category-object"></a>category-Objekt

Mit dem Kategorieobjekt können Sie mit einer einzelnen category arbeiten, um Details im Portal anzuzeigen.

### <a name="attributes"></a>Attribute

category ist ein [entity](#entity)-Objekt mit den gleichen Attributen zusätzlich zu den unten aufgelisteten.

|Attribut|Beschreibung|
|---|---|
|categorynumber|Die Kategorienummer der Kategorie.|
|Name|Ein alternativer Alias für den Titel der Kategorie.|
|title|Der Titel der Kategorie.|
|||

## <a name="page"></a>Seite

Verweist auf die aktuelle Portalanforderungsseite. Dieses Objekt kombiniert die Attribute der [Siteübersicht](#sitemap) und der aktuellen Anfrage [Entitäten](#entities) (in der Regel eine Webseite).  

Das Objekt page bietet Zugriff auf Dinge wie die Breadcrumbs für die aktuelle Seite, den Titel oder die URL der aktuellen Seite und alle anderen Attribute oder verbundenen Entität des zugrunde liegenden Power Apps-Datensatzes.

```
<ul class=breadcrumb>

{% for crumb in page.breadcrumbs %}

<li><a href={{ crumb.url | escape }}>{{ crumb.title | escape }}</a></li>

{% endfor %}

<li class=active>{{ page.title | escape }}</li>

</ul>

<div class=page-header>

<h1>{{ page.title | escape }}</h1>

</div>

<div class=page-copy>

{{ page.adx_copy }}

</div>

<div class=list-group>

{% for child in page.children %}

<a class=list-group-item href={{ child.url | escape }}>

{{ child.title | escape }}

</a>

{% endfor %}

</div>

<!-- Page {{ page.id }} was last modified on {{ page.modifiedon }}. -->
```

### <a name="page-attributes"></a>Seitenattribute

> [!Note]  
> [Entitäten](#entities)

|             Attribut              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            breadcrumbs             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Gibt die Breadcrumb-Siteübersichtsknotenobjekte für die Seite zurück, beginnend ab dem Knotenpunkt für die Siteübersicht und endent bei übergeordnet                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|              children              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Gibt die untergeordneten Siteübersichtsknotenobjekte der Seite zurück                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|               parent               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           Gibt den übergeordneten Siteübersichtsknoten der Seite zurück. Wenn die Seite die Homepage ist, ist das übergeordnete Element Null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|               title                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Der Titel der Seite.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                URL                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Die URL der Seite.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| \[Attribut- oder Beziehungsname\] | Sie können auf ein beliebiges Attribut des der Seite zugrundeliegenden Power Apps-Datensatzes nach logischem Namen zugreifen.<br>`{{ page.createdon }}`<br>`{% assign attribute_name = 'name' %}`<br>`{{ page[attribute_name] }}`<br>Die Werte der meisten Entitätsattribute werden direkt zu [Liquid-Typen](liquid-types.md) zugeordnet: Felder mit zwei Optionsmöglichkeiten werden booleschen Werten zugeordnet, Textfelder werden Zeichenfolgen zugeordnet, nummerische Felder/Währungsfelder werden Zahlen zugeordnet und Datum/Uhrzeit-Felder werden Datum-Objekten zugeordnet. Einige Attributtypen werden jedoch als Objekte zurückgegeben:<ul><li>Suchfelder (Entitätsreferenz) werden als [Entitätsreferenzobjekte](#entity-reference) zurückgegeben.</li><li>Optionssatz-/Auswahllistenfelder werden als [Optionssatzwertobjekte ](#option-set-value)zurückgegeben.</li> Sie können beliebigen verknüpfte Entitäten über den Beziehungsschemanamen laden. <br> `{{ page.adx_webpage_entitylist.adx_name }}`<br>Wenn eine Beziehung reflexiv ist (z. B. auf sich selbst verweist), wird ein [Entitäten-Objekt ](#entities)zurückgegeben. (Andernfalls wäre das Ergebnis mehrdeutig.)`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**Hinweis**: Das Laden großer Mengen von verknüpfte Entitäten oder der Zugriff auf viele Beziehungen in einer einzigen Vorlage können negative Auswirkungen auf die Renderleistung der Vorlage haben. Vermeiden Sie das Laden verknüpfte Entitäten für jeden Artikel in einem Array innerhalb einer Schleife. Wenn möglich, bevorzugen Sie die Verwendung der [Power Apps Common Data Service Entity Tags](portals-entity-tags.md), um Sammlungen von Entitäten zu laden. |

## <a name="polls"></a>Umfragen

Bietet die Möglichkeit, auf eine Umfrage zuzugreifen und sie zu rendern.

Das polls-Objekt ermöglicht die Auswahl einer bestimmten Umfrage oder Umfragenplatzierung:

```
<div>

{% assign poll = polls[Poll Name] %}

<h4>{{ poll.question }}</h4>

{% for option in poll.options %}

<div>

<input type=radio name={{ poll.name }} id={{ option.id }} />

<label for={{ option.id }}>{{ option.answer }}</label>

</div>

{% endfor %}

<button type=button>{{ poll.submit_button_label }}</button>

</div>
```

### <a name="polls-attributes"></a>Umfrageattribute

|Attribut   |Beschreibung   |
|---|---|
| placements          | Gibt das Umfrageplatzierungs-Objekt zurück.                                      |
| \[Umfragenname oder -ID\] | Sie können auf jede beliebige Umfrage über ihre Namens- oder ID-Eigenschaften zugreifen. `{% assign poll = polls[Poll Name] %}`<br>`{% assign poll = polls["41827a5c-33de-49b8-a0c7-439e6a02eb98"] %}`  |

### <a name="poll-placements-attributes"></a>Attribute von Umfragenplatzierungen

|Attribut   |Beschreibung   |
|---|---|
| \[Umfragenplatzierungsname oder -ID\] | Sie können auf jede beliebige Umfragenplatzierung über ihre Namens- oder ID-Eigenschaften zugreifen.`{% assign placement = polls.placements[Placement Name or Id] %}`<br>`{% assign placement = polls.placements[7677c5d4-406e-4b6c-907c-916ac17dba0f] %} `|

### <a name="poll-placement-attributes"></a>Attribute von Umfragenplatzierungen

> [!Note] 
> [entities](#entities)                                       

|Attribut   |Beschreibung   |
|---|---|
| Name           | Gibt das Feld "Name" für die Umfragenplatzierung zurück.                            
| placement\_url | Die URL, mit der die Umfragenplatzierung abgerufen werden kann, die vollständig über eine Vorlage gerendert wird.                       |
| Umfragen          | Gibt die Sammlung von Umfrageobjekten zurück, die mit der Platzierung verbunden sind. [Iterationtags](iteration-tags.md) und [Arrayfilter](liquid-filters.md#array-filters) werden möglicherweise mit dieser Sammlung verwendet.  |  
| random\_url    | Die URL, mit der eine willkürliche Umfrage aus der Platzierung abgerufen werden kann, die vollständig über eine Vorlage gerendert wird.         |
| submit\_url    | Die URL, an die eine abgeschlossene Umfrage gesendet wird.                                                             |

### <a name="poll-attributes"></a>Umfrageattribute

> [!Note] 
> [Entitäten](#entities)                                          

|Attribut   |Beschreibung   |
|---|---|
| has\_user\_voted       | Gibt "True" zurück, wenn der aktuelle Benutzer (angemeldet oder anonym) bereits an dieser Umfrage teilgenommen hat.         |
| Name                   | Gibt das Feld "Name" für die Umfrage zurück.                                                              |
| Optionen                | Gibt die Sammlung von Umfrageoptionsobjekten zurück, die mit der Umfrage verbunden sind. [Iterationstags](iteration-tags.md) und [Entitäten](#entities) können mit dieser Sammlung verwendet werden.  |  
| poll\_url              | Die URL, mit der die Umfrage abgerufen werden kann, die vollständig über eine Vorlage gerendert wird.                       |
| -Frage               | Gibt das Feld "Frage" für die Umfrage zurück.                                                          |
| submit\_button\_label  | Gibt eine Zeichenfolge an, die verwendet werden kann, um die Schaltflächen-Beschriftung für die Übermittlung zu überschreiben.               |
| submit\_url            | Die URL, an die eine abgeschlossene Umfrage gesendet wird.                                                   |
| user\_selected\_option | Gibt das Objekt Umfrageoption zurück, das vom Benutzer ausgewählt wurde (falls er bereits gewählt hat.)                  |
| votes                  | Gibt die Anzahl der getätigten Stimmen zurück, die für die Umfrage tabelliert wurden.                                |

### <a name="poll-option-attributes"></a>Umfrageoptionsattribute

>[!Note]
> [Entitäten](#entities)                                         

|Attribut   |Beschreibung   |
|---|---|
| answer     | Gibt das Feld "Antwort" für die Umfrage zurück. |
| percentage | Gibt den Prozentsatz der Stimmen in der Umfrage für die entsprechende Option als Dezimalstelle zwischen 0 und 100 zurück. |
| votes      | Gibt die Anzahl der getätigten Stimmen zurück, die für die Umfrage tabelliert wurden.                              |


## <a name="request"></a>Anfrage

Enthält Informationen zum aktuellen HTTP-Request.

```
{% assign id = request.params['id'] %}

<a href={{ request.url | add_query: 'foo', 1 }}>Link</a>
```

> [!Note]
> Sie können URLs in Liquid mithilfe von URL-Filtern dynamisch erstellen. 

### <a name="attributes"></a>Attribute

|Attribut   |Beschreibung   |
|---|---|
| params           | Benannte Parameterwerte für die aktuelle Anforderung. params ist eine Kombination aus URL-Abfragezeichenfolgenparametern, Formular-Post-Parametern und Cookies.  |
| Pfad             | Der Pfad der aktuellen Anforderungs-URL. <br> /profile/|
| path\_and\_query | Der Pfad und die Abfrage der aktuellen Anforderungs-URL.<br> /profile/?foo=1&bar=something|
| query            | Der Abfragepfad der aktuellen Anforderungs-URL. <br> ?foo=1&bar=something |
| URL              | Der vollständige Pfad der aktuellen Anforderungs-URL.<br>  https://www.example.com/profile/?foo=1&bar=something  |


## <a name="searchindex"></a>searchindex

Das Suchindex-Objekt wird innerhalb der [Power Apps Common Data Service Entity Tags](portals-entity-tags.md) verwendet und ermöglicht den Zugriff auf die Ergebnisse einer Abfrage.  

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

### <a name="attributes"></a>Attribute

|Attribut   |Beschreibung   |
|---|---|
| approximate\_total\_hits | Gibt eine ungefähre Gesamtanzahl der Treffer zurück, welche mit der Indexabfrage übereinstimmen. Aufgrund der Funktionsweise des Suchindex im Hinblick auf die Sicherheitsfilterung und andere Entwurfsfaktoren ist diese Zahl eine Schätzung und entspricht möglicherweise nicht der genauen Anzahl der Ergebnisse, die dem aktuellen Benutzer in einigen Situationen zur Verfügung stehen.  |
| Seite                     | Gibt die Seitenzahl der aktuellen Abfrage zurück.                                                                                                                                                                                                           |
| page\_size               | Gibt die maximale Seitengröße der aktuellen Abfrage zurück. Wenn Sie die tatsächliche Anzahl der für die aktuelle Seite zurückgegebenen Ergebnisse möchten (denn dies ist möglicherweise weniger als die angegebene maximale Seitengröße), müssen Sie results.size verwenden.                                                                                           |
| Ergebnisse                  | Gibt die Abfrageergebnisseite als Suchenindex-Ergebnisobjekte zurück.                                                                                                                                                                                          |

### <a name="search-index-results"></a>Suchindexergebnisse

|   Attribut   |                                                                                                                                                Beschreibung                                                                                                                                                 |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Entität     |                                                                                                                            Die zugrunde liegenden [Entitäten](#entities) für das Ergebnis.                                                                                                                            |
|   fragment    | Ein relevantes kurzes Textfragment für das Ergebnis mit Begriffen, die der angegebenen Abfrage entsprechen und mit dem &lt;em&gt;-HTML-Tag markiert sind. Beachten Sie, dass bestimmte Typen von Abfragen keine markierten Fragmente unterstützen, beispielsweise Fuzzyabfragen (~) und Platzhalterabfragen (\*). Diese Eigenschaft ist in diesen Fällen null. |
|      Kennung       |                                                             Die Power Apps-Entitäts-ID des zugrunde liegenden Datensatzes für das Ergebnis als Zeichenfolge. Beispielsweise 936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                              |
| logical\_name |                                                                           Der logische Name der Power Apps-Entität des zugrunde liegenden Datensatzes für das Ergebnis. Beispiel: adx\_webpage                                                                           |
|    Anzahl     |                                                            Die Nummer des Ergebnisse auf allen Ergebnisseiten, beginnend bei 1. Für das erste Ergebnis der zweiten Ergebnisseite bei einer Seitengröße von 10 wäre dieser Wert 11.                                                             |
|     score     |                                                                                                 Die Lucene-Punktzahl des Ergebnisses als Gleitkommawert. Ergebnisse werden nach diesem Wert geordnet zurückgegeben.                                                                                                 |
|     title     |                                                                                                                                          Der Titel des Ergebnisses.                                                                                                                                          |
|      URL      |                                                            Die URL für das Ergebnis. Dies ist eigentlich&mdash;aber nicht notwendigerweise&mdash;eher ein absoluter Pfad für die aktuelle Anwendung, statt eine vollständige URL. Beispiel: /articles/article1/                                                             |

## <a name="settings"></a>Einstellungen

Ermöglicht das Laden einer beliebigen [Website-Einstellung](../configure/configure-site-settings.md) nach Namen. Wird eine Einstellung mit dem angegebenen Namen gefunden, wird [Null](liquid-types.md#null) zurückgegeben.  

> [!Note]
> Einstellungen werden als [Zeichenfolgen](liquid-types.md#string) zurückgegeben, aber Sie können [Type-Filter](liquid-filters.md#type-filters) verwenden, um sie in andere Typen zu konvertieren.

```
{{ settings[My Setting] }}

{% assign search_enabled = settings[Search/Enabled] | boolean %}

{% if search_enabled %}

Search is enabled.

{% endif %}

{% assign pagesize = settings['page size'] | integer | default: 10 %}

{% if pagesize > 10 %}

Page size is greater than 10.

{% endif %}
```

> [!Note]
> [Rendern einer Websitekopfzeile und primären Navigationsleiste](render-site-header-primary-navigation.md)


## <a name="sitemap"></a>Siteübersicht

Ermöglicht Zugriff auf die Portalsiteübersicht.

```
<h1>{{ sitemap.root.title }}</h1>

<ul class=breadcrumb>

{% for crumb in sitemap.current.breadcrumbs %}

<li><a href={{ crumb.title }}>{{ crumb.title }}</a></li>

{% endfor %}

<li class=active>{{ sitemap.current.title }}</li>

</ul>

{% for child in sitemap.current.children %}

<a href={{ child.url }}>{{ child.title }}</a>

{% endfor %}

It's also possible to load a site map node by URL path:

{% assign node = sitemap[/content/page1/] %}

{% if node %}

{% for child in node.children %}

<a href={{ child.url }}>{{ child.title }}</a>

{% endfor %}

{% endif %}
```

### <a name="site-map-attributes"></a>Siteübersichtsattribute

|Attribut   |Beschreibung   |
|---|---|
| Aktuell | Gibt das Siteübersichtsknotenobjekt für die aktuelle Seite zurück.                    |
| Stamm    | Gibt das Siteübersichtsknotenobjekt für die Startseite der Website zurück. |

### <a name="site-map-node-attributes"></a>Siteübersichtsknotenattribute

|Attribut   |Beschreibung   |
|-------|-------|
| Breadcrumbs           | Gibt die Breadcrumb-Siteübersichtsknotenobjekte für den Knoten zurück, beginnend ab dem Knotenpunkt für die Siteübersicht und endend bei dem übergeordneten. |
| Kinder              | Gibt die Siteübersichtsknotenobjekte des untergeordneten Knotens zurück.                                                                  |
| Beschreibung           | Die Beschreibung/der Inhalt des Knotens. (Dieses Feld enthält möglicherweise HTML.)                                          |
| Entität                | Gibt die zugrunde liegenden [Entitäten](#entities) des Knotens zurück. Wenn der Konten keine zugrunde liegende Entität aufweist, ist dieser Wert Null.                                                         |
| is\_sitemap\_ancestor | Gibt „True“ zurück, wenn der Siteübersichtsknoten ein Vorgänger des aktuellen Knoten ist, andernfalls „False“.                                                                                                         |
| is\_sitemap\_current  | Gibt „True“ zurück, wenn der Siteübersichtsknoten der aktuelle Knoten ist, andernfalls „False“.                                                                                                         |
| Übergeordnetes Element                | Gibt das übergeordneten Siteübersichtsknoten des Knotens zurück. Wenn der Konten der Stammknoten ist, ist das übergeordnete Element Null.                                                                     |
| Position                 | Der Titel des Knotens.                                                                                                |
| URL                   | Die URL des Knotens.                                                                                                  |


## <a name="sitemarkers"></a>Websitemarkierungen

Ermöglicht das Laden einer beliebigen Websitemarkierung nach Namen. Wenn die Websitemarkierung vorhanden ist, wird ein Websitemarkierungsobjekt zurückgegeben. Wird eine Einstellung mit dem angegebenen Namen gefunden, wird [Null](liquid-types.md#null) zurückgegeben.  

```
{{ sitemarkers[Login].url }}

{% assign my_sitemarker = sitemarkers[My Site Marker] %}

{% if my_sitemarker %}

<a href={{ my_sitemarker.url }}>{{ my_sitemarker.adx_name }}</a>

{% else %}

Site marker My Site Marker does not exist.

{% endif %}
```

> [!Note]
> [Rendern einer Websitekopfzeile und primären Navigationsleiste](render-site-header-primary-navigation.md)  

### <a name="sitemarker-attributes"></a>Websitemarkierungsattribute

|         Attribut          |                                                                                    Beschreibung                                                                                    |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            URL             |                                                                         Die URL des Websitemarkierungsziels.                                                                         |
| \[Logischer Attributname\] | Sie können auf ein beliebiges Attribut des Power Apps-Datensatzes des Websitemarkierungsziels nach logischem Namen zugreifen. Beispielsweise {{ sitemarker.adx\_name }} |

## <a name="snippets"></a>Ausschnitte

Ermöglicht das Laden von Inhaltsausschnitten nach Namen. Wird kein Ausschnitt mit dem angegebenen Namen gefunden, wird [Null](liquid-types.md#null) zurückgegeben.  

```
{{ snippets[Header] }}

{% assign footer = snippets[Footer] %}

{% if footer %}

{{ footer }}

{% else %}

No footer snippet was found.

{% endif %}
```


## <a name="tablerowloop"></a>tablerowloop

Enthält Eigenschaften, die in einem [Iterationstags](iteration-tags.md)-Loop-Block nützlich sind.  

> [!Note] 
> tablerowloop kann nur innerhalb eines [Iterationstag-Tags](iteration-tags.md) Tag verwendet werden.

### <a name="attributes"></a>Attribute

|Attribut   |Beschreibung   |
|---|---|
| Col        | Gibt den Index der aktuellen Zeile wieder, beginnend bei 1.                                                       |
| col0       | Gibt den Index der aktuellen Zeile wieder, beginnend bei 0.                                                       |
| col\_first | Gibt „True“ wieder, wenn die aktuelle Spalte die erste Spalte in einer Zeile ist und gibt „False“ wieder, wenn nicht.               |
| col\_last  | Gibt „True“ wieder, wenn die aktuelle Spalte die letzte Spalte in einer Zeile ist und gibt „False“ wieder, wenn nicht.                |
| Erster      | Gibt „True“ zurück, wenn es sich um den ersten Schleifendurchlauf handelt. Gibt „False“ zurück, wenn es sich nicht um den ersten Schleifendurchlauf handelt.       |
| Index      | Die Position des aktuellen Elements in der Sammlung (das ersten Element hat die Position 1).                   |
| index0     | Die Position des aktuellen Elements in der Sammlung (das ersten Element hat die Position 0).                   |
| Letzter       | Gibt „True“ zurück, wenn es sich um den letzten Schleifendurchlauf handelt. Gibt „False“ zurück, wenn es sich nicht um den letzten Schleifendurchlauf handelt.         |
| Länge     | Gibt die Anzahl der Durchlaufe der Schleife zurück ߝ Die Anzahl der Elemente in der Sammlung, die durchlaufen werden. |
| Rindex     | Anzahl der Elemente, die noch in der Schleife verbleiben (Länge - Index), wobei 1 der Index des letzten Elements ist.              |
| rindex0    | Anzahl der Elemente, die noch in der Schleife verbleiben (Länge - Index), wobei 0 der Index des letzten Elements ist.              |



## <a name="user"></a>Benutzer

Verweist auf den aktuellen Portalbenutzer und ermöglicht Zugriff auf alle Attribute des zugrunde liegenden Power Apps-Kontaktdatensatzes. Wenn kein Benutzer angemeldet ist, ist diese Variable [Null](liquid-types.md#null).  

Benutzer ist ein [Entität](#entity)-Objekt.  

```
{% if user %}

Hello, {{ user.fullname }}!

{% else %}

Hello, anonymous user!

{% endif %}
```

### <a name="attributes"></a>Attribute

Neben der Verfügbarkeit aller Attribute von[ Entitäten](#entity) Objekt, hat der Benutzer folgende Attribute.


|    Attribut     |                                                                                                                                                                                     Beschreibung                                                                                                                                                                                     |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Rollen       |                                                      Gibt die Rollen, denen der Benutzer angehört, als [" Array "](liquid-types.md#array) wieder.<br>`{% if user.roles contains 'Administrators' %} User is an administrator. {% endif %}`<br>**Hinweis**: Sie können den `has_role` Filter auch nutzen, um einzelne Rollen Mitgliedschaften zu testen.                                                       |
| basic_badges_url | Gibt die Service-URL zurück, um die Ausweise eines Benutzers abzurufen.<br>Um Ausweise für Benutzer zu rendern, müssen Sie ein Tag für die Attribute "Datenausweis" und" Daten-URI" enthalten. Wenn Sie die Ausweise des Benutzers rendern:<br>`<div data-badge data-uri='{{user.basic_badges_url }}'></div>`<br>Wenn Sie die Ausweise eines Benutzers nach ID rendern (variable Benutzer-ID):<br>\`<div data-badge data-uri='{{user.basic_badges_url |
|                  |                                                                                                                                                                                                                                                                                                                                                                                     |

## <a name="weblinks"></a>Weblinks

Ermöglicht das Laden eines beliebigen Weblinks nach Namen oder ID.  

Wenn der Weblinksatz vorhanden ist, wird ein [Weblinksatz-Objekt](#web-link-set-attributes) zurückgegeben. Wird kein Weblinksatz mit dem angegebenen Namen oder der ID gefunden, wird [Null](liquid-types.md#null) zurückgegeben.


```
<!-- Load web link set by ID -->

{{ weblinks[page.adx_navigation.id].name }}

<!-- Load web link set by name -->

{% assign nav = weblinks[Primary Navigation] %}

{% if nav %}

<h1>{{ nav.title | escape }}</h1>

<ul>

{% for link in nav.weblinks %}

<li>

<a href={{ link.url | escape }} title={{ link.tooltip | escape }}>

{% if link.image %}

<img src={{ link.image.url | escape }} alt={{ link.image.alternate_text | escape }} />

{% endif %}

{{ link.name | escape }}

</a>

</li>

{% endfor %}

</ul>

{% endif %}
```

> [!Note]
> [Rendern einer Websitekopfzeile und der primäre Navigationsleiste](render-site-header-primary-navigation.md) |  

### <a name="web-link-set-attributes"></a>Weblinksatz-Attribute

> [!Note]
> Ein Weblink-Set ist ein [Entitäts](#entity)-Objekt mit den gleichen Attributen zusätzlich zu den unten aufgelisteten.                                         

|         Attribut          |                                                                                 Beschreibung                                                                                  |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Kopieren            |                                                                      Der HTML-Text des Weblinksatzes.                                                                      |
|            Name            |                                                                        Der Name des Weblinksatzes.                                                                         |
|           Position            |                                                                        Der Titel des Weblinksatzes.                                                                        |
|          Weblinks          |                                                       Das Array der Weblinkobjekte, die dem Weblinksatz zugeordnet sind.                                                        |
| \[Logischer Attributname\] | Sie können auf ein beliebiges Attribut des Power Apps-Datensatzes des Weblinksatzes nach logischem Namen zugreifen. Beispielsweise {{ weblinkset.createdon }} |

### <a name="web-link-attributes"></a>Weblinkattribute

> [!Note]
> Ein Weblink-Set ist ein [Entitäts](#entity)-Objekt mit den gleichen Attributen zusätzlich zu den unten aufgelisteten.

|          Attribut          |                                                                              Beschreibung                                                                              |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Beschreibung         |                                                                 Die HTML-Beschreibung des Weblinks.                                                                 |
|    display\_image\_only     |                              Das boolesche Attribut gibt an, ob der Weblink lediglich als Bild und ohne Linktext angezeigt werden soll.                               |
| display\_page\_child\_links |            Das boolesche Attribut gibt an, ob der Weblink Links zu untergeordneten [*Siteübersicht*](#sitemap)-Seiten der verlinkten Seite als Sublinks anzeigen soll.             |
|            Bild            |                                     Das Weblink-Bildobjekt für diesen Link. Dieses Attribut ist null, falls kein Bild vorhanden ist.                                      |
|        is\_external         |                 Das boolesche Attribut gibt an, ob die Ziel-URL des Weblinks auf eine externe Website verweist(und nicht zu einer internen Portalseite).                  |
|    is\_sitemap\_ancestor    |                                Gibt „True“ zurück, wenn die URL des Weblinks auf einen Vorgänger des aktuellen Siteübersichtsknoten verweist, andernfalls „False“.                                 |
|    is\_sitemap\_current     |                                        Gibt „True“ zurück, wenn die URL des Weblinks auf den aktuellen Siteübersichtsknoten verweist, andernfalls „False“.                                        |
|            Name             |                                                                    Der Name/Titel des Weblinks.                                                                    |
|          Nofollow           |                                         Das boolesche Attribut gibt an, ob der Weblink als rel="nofollow"gekennzeichnet werden soll.                                         |
|    open\_in\_new\_window    |                             Das boolesche Attributgibt an, ob der Weblink in einem neuen Browserfenster/in einer neuen Registerkarte geöffnet werden soll, sobald er angeklickt wird.                             |
|           QuickInfo           |                                                                    QuickInfo-Text für den Weblink.                                                                     |
|             URL             |                                                                       Die URL des Weblinks.                                                                        |
|          Weblinks           |                                                   Das Array der untergeordneten Weblinkobjekte, die dem Weblink zugeordnet sind.                                                   |
| \[Logischer Attributname\]  | Sie können auf ein beliebiges Attribut des Power Apps-Datensatzes des Weblinks nach logischem Namen zugreifen. Beispielsweise {{ weblink.createdon }} |

### <a name="web-link-image-attributes"></a>Weblink-Bildattribute

| alternate\_text | Alternativer Text für das Bild.                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
| Höhe          | Ganze Zahl, die die angegebene Höhe des Bildes enthält. Wenn kein Wert für die Höhe bereitgestellt wurde, ist dieses Attribut null. |
| URL             | Geben Sie die URL des Bildes ein.                                                                                               |
| Breite           | Ganze Zahl, die die angegebene Breite des Bildes enthält. Wenn kein Wert für die Breite bereitgestellt wurde, ist dieses Attribut null.   |


## <a name="website"></a>Website

Verweist auf die Portal-Website und ermöglicht Zugriff auf alle Attribute des Power Apps-Websitedatensatz (adx\_website) für das Portal.  

> [!Note]
> Website ist ein [Entität](#entity)-Objekt, mit all den gleichen Attributen.

**Code**

```
{{ website.adx_name }} ({{ website.id }})
```

**Ausgabe**

```
Community Portal (936DA01F-9ABD-4d9d-80C7-02AF85C822A8)
```


### <a name="see-also"></a>Siehe auch

[Liquid-Typen](liquid-types.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md)  
