---
title: Verwenden von Liquid-Objekten für ein Portal | MicrosoftDocs
description: Erfahren Sie mehr über die verfügbaren Liquid-Objekte in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 05e3dfbeb2c3356821a0952ed14a1924e657c293
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976643"
---
# <a name="available-liquid-objects"></a>Verfügbare Liquid-Objekte

Liquid-Objekte enthalten Attribute, um dynamischen Inhalt auf der Seite auszugeben. Das Page-Objekt hat z. b. ein Attribut mit dem Namen "Title", das zum Ausgeben des Titels der aktuellen Seite verwendet werden kann.

Wenn Sie über den Namen auf ein Objekt Attribut zugreifen möchten, verwenden Sie einen Punkt. Um das Attribut eines Objekts in einer Vorlage zu erstellen, müssen Sie es in {{und}} einschließen.

```
{{ page.title }}
```
Auf die Attribute eines Objekts kann auch über einen Zeichen folgen Namen und \[\]zugegriffen werden. Dies ist hilfreich in Fällen, in denen das gewünschte Attribut dynamisch bestimmt wird, oder wenn der Attribut Name Zeichen, Leerzeichen, Sonderzeichen usw. enthält, die bei Verwendung des ungültig sind. Syntax.

```
{{ page[title] }}

{% assign attribute_name = Name with spaces %}

{{ object[attribute_name] }}
```

Die folgenden Objekte können in einer beliebigen Vorlage verwendet und überall dort verwendet werden.


|   Objekt    |                                                                                                                                                                                          Beschreibung                                                                                                                                                                                           |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Kleinstunternehmen   |                                                                                                 Ermöglicht das Laden beliebiger powerapps-Entitäten nach ID. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Entitäten](#entities)                                                                                                 |
|     gerade     |                                          Ein Datums-/Uhrzeit-Objekt, das sich auf die aktuelle UTC-Zeit zum Zeitpunkt der Vorlagen Darstellung bezieht.<br>**Hinweis**: dieser Wert wird von der Portal-Web-App zwischengespeichert und nicht jedes Mal aktualisiert. Filter für [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Datum](liquid-filters.md#date-filters)                                          |
|    s     | Verweist auf die aktuelle Portal Anforderungsseite. Das Page-Objekt ermöglicht den Zugriff auf Elemente wie den Brotkrümel für die aktuelle Seite, den Titel oder die URL der aktuellen Seite sowie alle anderen Attribute oder zugehörigen Entitäten des zugrunde liegenden powerapps-Datensatzes. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Seite](#page) |
|   params    |                                                                                                                             Eine bequeme Verknüpfung für "Request. para". [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Anforderung](#request)                                                                                                                              |
|   Anforderung   |                                                                                                                        Enthält Informationen über die aktuelle HTTP-Anforderung. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Anforderung](#request)                                                                                                                        |
|  Einstellungen   |                                                                                                            Ermöglicht das Laden beliebiger [Website Einstellungen](../configure/configure-site-settings.md) nach Namen. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Einstellungen](#settings)                                                                                                            |
|   tex   |                                                                                                                               Ermöglicht den Zugriff auf die Portal Site Übersicht. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)]- [Sitemap](#sitemap)                                                                                                                                |
| sitemarkers |                                                                                                                        Ermöglicht das Laden beliebiger Site Marker nach Namen. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [sitemarkers](#sitemarkers)                                                                                                                        |
|  p   |                                                                                                         Ermöglicht das Laden beliebiger [Inhalts](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/customize-content-snippets) Ausschnitte anhand des Namens. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Ausschnitte](#snippets)                                                                                                         |
|    Bedienungs     |                             Bezieht sich auf den aktuellen Portalbenutzer, der den Zugriff auf alle Attribute des zugrunde liegenden powerapps-Kontaktdaten Satzes ermöglicht. Wenn kein Benutzer angemeldet ist, ist diese Variable [null](liquid-types.md#null). [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Benutzer](#user)                              |
|  Weblinks   |                                                                                                                        Ermöglicht das Laden beliebiger Weblinks, die anhand des Namens oder der ID festgelegt sind. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Weblinks](#weblinks)                                                                                                                        |
|   Website   |                                                      Bezieht sich auf den Daten Satz der Portal Website und ermöglicht den Zugriff auf alle Attribute des Datensatzes der powerapps-Website (ADX\_-Website) für das Portal. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)]- [Website](#website)                                                       |

## <a name="ads"></a>Teams


Bietet die Möglichkeit, auf eine Werbe-und Rendering zuzugreifen.

Das ADS-Objekt ermöglicht es Ihnen, eine bestimmte AD-oder Ad-Platzierung auszuwählen:

```
<div>

{% assign ad = ads[Ad Name] %}

<h4>{{ ad.title }}</h4>

<a href={{ ad.redirect_url }}>

<img src={{ ad.image.url }} alt={{ ad.image.alternate_text }} />

</a>

</div>
```

### <a name="ads-attributes"></a>ADS-Attribute

|Versehen   |Beschreibung   |
|---|---|
| Vermittlung        | Gibt das adplacement-Objekt zurück.    |
| \[Ad-Name oder-ID\] | Sie können mit den Eigenschaften "Name" oder "ID" auf eine beliebige Werbung zugreifen. <br> `{% assign ad = ads[Ad Name] %}`<br>`{% assign ad = ads["da8b8a92-2ee6-476f-8a21-782b047ff460"] %}`  |


### <a name="ad-placements-attributes"></a>AD-Platzierungs Attribute

|Versehen   |Beschreibung   |
|---|---|
| Name oder ID der \[Ad-Platzierung\] | Sie können mit den Eigenschaften "Name" oder "ID" auf jede beliebige adplacement zugreifen.<br>`{% assign placement = ads.placements[Placement Name or Id] %}`<br>`{% assign placement = ads.placements[2423d713-abb3-44c3-8a7d-c445e16fccad] %}`  |

### <a name="ad-placement-attributes"></a>AD-Platzierungs Attribute

Eine Ad-Platzierung ist ein Entitäts Objekt mit den gleichen Attributen, zusätzlich zu den unten aufgeführten Attributen.

|Versehen   |Beschreibung   |
|---|---|
| Teams            | Gibt die Auflistung der AD-Objekte zurück, die der Platzierung zugeordnet sind.  [Iterations Tags](iteration-tags.md) und [Array Filter](liquid-filters.md#array-filters) können mit dieser Auflistung verwendet werden.  |  
| Name           | Gibt das Namensfeld für die Ad-Platzierung zurück.                                                                |
| Platzierung\_URL | Die URL, die zum Abrufen der von einer Vorlage vollständig gerenderten Ad-Platzierung verwendet werden kann.                         |
| Random\_URL    | Die URL, die verwendet werden kann, um eine zufällige Werbung von der Platzierung abzurufen, die vollständig von einer Vorlage gerendert wird.           |

### <a name="ad-attributes"></a>AD-Attribute

> [!Note]
> Ein AD ist ein Entitäts Objekt, das zusätzlich zu den unten aufgeführten Attributen über dieselben Attribute verfügt.

|Versehen   |Beschreibung   |
|---|---|
| AD\_-URL |  Die URL, die verwendet werden kann, um den vollständig von einer Vorlage gerenderten AD abzurufen.   |
| Skopie| Gibt das Feld "Kopieren" für die Werbeanzeige zurück.|
| Klang| Gibt das Image-Objekt (sofern vorhanden) für das AD zurück.|
| Name| Gibt das Namensfeld für die AD-Auflistung zurück.|
| \_in\_Fenster "neues\_" öffnen | Gibt true zurück, wenn die durch Redirect\_URL angegebene URL in einem neuen Fenster geöffnet werden soll. |
| Umleiten\_URL| Die URL, an die der Benutzer weitergeleitet wird, indem er die Anzeige auswählt.|

### <a name="ad-image-attributes"></a>AD-Image Attribute

|Versehen   |Beschreibung   |
|---|---|
| alternativer\_Text | Gibt den Text zurück, der im alt-Attribut des Tags angezeigt werden soll. |
| height          | Gibt die Höhe des Bilds in Pixel zurück.                             |
| Urne             | Gibt die URL-Quelle für das Bild zurück.                                  |
| width           | Gibt die Breite des Bilds in Pixel zurück.                              |


## <a name="blogs"></a>gt

Bietet die Möglichkeit, auf Blogs und Blog Beiträge zuzugreifen und diese zu erstellen.

Das Blogs-Objekt ermöglicht Ihnen die Auswahl eines bestimmten Blogs oder Blogbeitrags.

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

### <a name="blogs-object"></a>Blogs-Objekt

Mit dem Blogs-Objekt können Sie auf einen bestimmten Blog im Portal zugreifen oder auf alle Blogbeiträge im Portal zugreifen (unabhängig vom Blog).

In der folgenden Tabelle werden die Attribute erläutert, die dem Blogs-Objekt zugeordnet sind.

|Versehen   |Beschreibung   |
|---|---|
| Beiträge               | Gibt ein Blogposts-Objekt zurück, das alle Blogbeiträge im Portal enthält.     |
| \[Blog Name oder ID\] | Sie können über die Eigenschaften Name oder ID auf einen beliebigen Blog zugreifen.                   

```
{% assign blog = blogs[Blog Name] %}                             

{% assign blog = blogs[da8b8a92-2ee6-476f-8a21-782b047ff460] %}  |
```

### <a name="blog-object"></a>Blog Objekt

Mit dem Blog-Objekt können Sie mit einem einzelnen Blog arbeiten, sodass Sie auf die Beiträge für diesen Blog zugreifen können.

In der folgenden Tabelle werden verschiedene Attribute erläutert, die dem Blog Objekt zugeordnet sind.

|Versehen   |Beschreibung   |
|---|---|
| Beiträge | Gibt ein Blogposts-Objekt zurück, das alle Blogbeiträge für den Blog enthält. |
| Name  | Der Name des Blogs.                                              |
| Tel | Der Titel des Blogs.                                             |
| Urne   | Die URL des Blogs.                                               |

### <a name="blogposts-object"></a>Blogposts-Objekt

Das Blogposts-Objekt ermöglicht den Zugriff auf eine Auflistung von Blog Post-Objekten. Sie können die Blogbeiträge anordnen und die Paginierung zusätzlich zur Verwendung von Liquid-Filtern erreichen:

{% Assign Blogposts = Blogs. Posts | Order\_by "ADX\_Name", "Besc" | paginate: 0,0 | alle%} Beachten Sie, dass Blogs. Posts. all auch eine gültige Methode ist, um alle Blogbeiträge Blogs. Posts zu erhalten. aus\_Index: 0 | Take: 2 ist ebenfalls möglich.

In der folgenden Tabelle werden verschiedene Attribute erläutert, die dem Blog Posts-Objekt zugeordnet sind.

|Versehen   |Beschreibung   |
|---|---|
| Allen | Gibt alle Blogbeitrag-Objekte in der Auflistung zurück. |

### <a name="blogpost-object"></a>Blogbeitrag-Objekt

Bezieht sich auf einen einzelnen Blogbeitrag.

In der folgenden Tabelle werden verschiedene Attribute erläutert, die dem Blogbeitrag-Objekt zugeordnet sind.

|Versehen   |Beschreibung   |
|---|---|
| Urne            | Die URL des Beitrags.                                                                |
| Inhaltliche        | Gibt das Inhaltsfeld für den Beitrag zurück.                                             |
| Inhaltliche        | Gibt das Inhaltsfeld für den Beitrag zurück.                                             |
| Schrift         | Gibt den authorf für den Post-Dienst zurück (bei dem es sich um ein Kontakt Entitäts Objekt handelt.          |
| Tel          | Der Titel des Beitrags.                                                              |
| Kommentar\_Anzahl | Gibt den ganzzahligen Wert der Anzahl der für einen gegebenen Beitrag vorhandenen Kommentare zurück. |
| Veröffentlichungs\_Datum  | Das Datum, an dem der Beitrag veröffentlicht wurde.                                           |

## <a name="entities"></a>Kleinstunternehmen

Ermöglicht das Laden beliebiger powerapps-Entitäten nach ID. Wenn die Entität vorhanden ist, wird ein Entitäts Objekt zurückgegeben. Wenn keine Entität mit der angegebenen ID gefunden wird, wird [null](liquid-types.md#null) zurückgegeben.  

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

### <a name="entity"></a>Organisation

Ein Entitäts Objekt ermöglicht den Zugriff auf die Attribute eines powerapps-Entitäts Datensatzes.


|             Versehen              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                 Id                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Die GUID-ID der Entität als Zeichenfolge. Beispiel: 936da01f -9abd-4d9d-80c7-02af85c822a8                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|           logischer\_Name            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   Der logische powerapps-Name der Entität.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|               Hinweise                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Lädt alle Notizen (Anmerkungen), die der Entität zugeordnet sind, von der ältesten zum aktuellen (aufheftungs-). Notizen werden als Notiz Objekte zurückgegeben.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|            Griff             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Lädt Ergebnisse von Entitäts Berechtigungs Assertionen für die Entität. Die Ergebnisse werden als Berechtigungs Objekt zurückgegeben.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                Urne                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Gibt den URL-Pfad des Inhalts Verwaltungssystems des powerapps-Portals für die Entität zurück. Wenn die Entität keine gültige URL in der aktuellen Website hat, gibt NULL zurück. Im Allgemeinen wird nur ein Wert für bestimmte Entitäts Typen zurückgegeben, die in das Portal-CMS integriert wurden, es sei denn, Sie haben den URL-Anbieter in Ihrer Anwendung angepasst.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| \[Attribut-oder Beziehungs Name\] | Sie können auf ein beliebiges Attribut der powerapps-Entität mit logischem Namen zugreifen. `{{ entity.createdon }}{% assign attribute_name = 'name' %}{{ entity[attribute_name] }}` <br>Die Werte der meisten Entitäts Attribute sind direkt den [Liquid-Typen](liquid-types.md)zugeordnet: zwei Options Felder werden booleschen Werten, Textfeldern zu Zeichen folgen, numerischen/Währungs Feldern zu zahlen, Datums-/Uhrzeitfelder und Datums Objekten zugeordnet. Einige Attributtypen werden jedoch als Objekte zurückgegeben:<ul><li>Suchfelder (Entitäts Verweis) werden als Entitäts Verweis Objekte zurückgegeben.</li><li>Options Satz-/picklist-Felder werden als Options Satz Wert-Objekte zurückgegeben.</li><li>Sie können auch alle zugehörigen Entitäten nach beziehungsschema Namen laden.</li>`{{ page.adx_webpage_entitylist.adx_name }}`in dem Fall, dass eine Beziehung reflexiv (d. h. selbstreferenziell) ist, wird ein reflexives Beziehungs Objekt zurückgegeben. (Andernfalls wäre das Ergebnis mehrdeutig.)`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**Hinweis**: das Laden einer großen Anzahl von verknüpften Entitäten oder das Zugreifen auf eine große Anzahl von Beziehungen in einer einzelnen Vorlage kann sich negativ auf die Leistung von Vorlagen Rendering auswirken. Vermeiden Sie das Laden von verknüpften Entitäten für jedes Element in einem Array innerhalb einer Schleife. Verwenden Sie nach Möglichkeit [powerapps Common Data Service-Entitäts Tags](portals-entity-tags.md) , um Auflistungen von Entitäten zu laden. |

### <a name="entity-reference"></a>Entitäts Verweis

Such Attributwerte werden als Entitäts Verweis Objekte mit den folgenden Attributen zurückgegeben.


|   Versehen   |                                                Beschreibung                                                |
|---------------|-----------------------------------------------------------------------------------------------------------|
|      Id       | Die GUID-ID der Entität, auf die verwiesen wird, als Zeichenfolge. <br> Beispiel: 936da01f -9abd-4d9d-80c7-02af85c822a8 |
| logischer\_Name |  Der logische powerapps-Name der Entität, auf die verwiesen wird.   |
|     Name      |                           Das primäre Namensattribut der Entität, auf die verwiesen wird.                            |

### <a name="note"></a>Note

Ein Hinweis ist ein Entitäts Objekt, das den Zugriff auf die Attribute und Beziehungen eines Anmerkung-Datensatzes ermöglicht. Zusätzlich zu allen Attributen eines Entitäts Objekts weist ein Hinweis die folgenden zusätzlichen Attribute auf.


|  Versehen   |                                                                                                                                                                                                                                  Beschreibung                                                                                                                                                                                                                                  |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| documentbody | Lädt das documentbody-Attribut des Notiz Satzes der Notiz Notiz als Base64-codierte Zeichenfolge. Da der Inhalt dieses Attributs möglicherweise groß ist, wird er nicht mit dem Rest der Note-Attribute geladen, sondern nur bei Bedarf geladen. <br> **Hinweis**: die Verwendung des documentbody-Attributs kann sich negativ auf die Leistung der Vorlagen Rendering auswirken und sollte mit Bedacht durchgeführt werden.<br>Verwenden Sie das URL-Attribut, um einen Link zur Hinweis Anlage anzugeben, sofern dies möglich ist. |
|     Urne      |                                                                                                                                   Gibt den URL-Pfad für den integrierten Anlage Handler der Portal Anmerkung zurück. Wenn der Benutzer über die Berechtigung verfügt und der Hinweis über eine angefügte Datei verfügt, wird durch eine Anforderung an diese URL die Anlage der Hinweis Datei heruntergeladen.                                                                                                                                    |

>[!Note]
> [Zusätzliche Filter](liquid-filters.md#additional-filters)                     

### <a name="option-set-value"></a>Options Satz Wert

Options Satz-/picklist-Attributwerte werden als Entitäts Verweis Objekte mit den folgenden Attributen zurückgegeben.

| Versehen | Beschreibung                                                     |
|-----------|-----------------------------------------------------------------|
| Bezeichnung     | Die lokalisierte Bezeichnung des Options Satz-/picklist-Attribut Werts. Beispielsweise "aktiv"|
| Value     | Der ganzzahlige Wert des Options Satz-/picklist-Attribut Werts. Beispiel: 0                                                           |

### <a name="entity-permissions"></a>Entitäts Berechtigungen

Das Entitäts Berechtigungs Objekt ermöglicht den Zugriff auf aggregierte Berechtigungs assertionsergebnisse für eine Entität.

| Versehen       | Beschreibung                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| kann\_angefügt werden     | Gibt true zurück, wenn der aktuelle Benutzer über die Berechtigung zum Anfügen von Datensätzen an die Beziehungen dieses Datensatzes verfügt. Gibt andernfalls false zurück.                                                                                              |
| \_kann\_angefügt werden an | Gibt "true" zurück, wenn der aktuelle Benutzer über die Berechtigung zum Anfügen dieses Datensatzes an eine Beziehung einer anderen Entität verfügt. Gibt andernfalls false zurück.                                                                                      |
| kann\_erstellt werden.     | Gibt "true" zurück, wenn der aktuelle Benutzer über die Berechtigung zum Erstellen neuer Datensätze dieses Entitäts Typs verfügt. Gibt andernfalls false zurück.                                                                                                      |
| kann\_gelöscht werden.     | Gibt true zurück, wenn der aktuelle Benutzer über die Berechtigung zum Löschen dieses Datensatzes verfügt. Gibt andernfalls false zurück.                                                                                                                          |
| Lese\_möglich       | Gibt true zurück, wenn der aktuelle Benutzer über die Berechtigung zum Lesen dieses Datensatzes verfügt. Gibt andernfalls false zurück.                                                                                                                            |
| kann\_schreiben      | Gibt true zurück, wenn der aktuelle Benutzer über die Berechtigung zum Aktualisieren dieses Datensatzes verfügt. Gibt andernfalls false zurück.                                                                                                                          |
| Regeln\_vorhanden    | Gibt true zurück, wenn die von diesem-Objekt dargestellten Berechtigungs Ergebnisse das Ergebnis von explizit definierten Berechtigungs Regeln sind. Gibt false zurück, wenn es sich um die Standard Ergebnisse handelt, wenn explizit definierte Berechtigungen fehlen. |

### <a name="reflexive-relationship"></a>Reflexive Beziehung

Versuche, reflexive (d. h. selbstreferenzielle) Beziehungen für Entitäten zu laden, werden als Objekte mit den folgenden Attributen zurückgegeben.

| Versehen     | Beschreibung                                                                                                   |
|---------------|---------------------------------------------------------------------------------------------------------------|
| ist\_reflexiv | Gibt true zurück. Kann verwendet werden, um zu testen, ob ein Objekt, das von einer Beziehung zurückgegeben wurde, ein reflexives Beziehungs Objekt ist. |
| verwiesen wird    | Gibt ein Array von Entitäten zurück, auf die verwiesen wird.                                           |
| verweisen   | Gibt eine verweisende Entität für die angegebene Beziehung zurück. Gibt NULL zurück, wenn keine verweisende Entität vorhanden ist. Wenn die Beziehung m:n (n:n) ist, wird ein Array von verweisenden Entitäten zurückgegeben.                          

## <a name="entitylist"></a>entityList

Das entityList-Objekt wird innerhalb der [powerapps Common Data Service-Entitäts Tags](portals-entity-tags.md)verwendet. Sie ermöglicht den Zugriff auf alle Attribute einer bestimmten Entitäts Liste.  

> [!Note]                                                       
> [Rendering der der aktuellen Seite zugeordneten Entitäts Liste](render-entity-list-current-page.md)

### <a name="attributes"></a>Attribute

> [!Note]
> [Kleinstunternehmen](#entities)

|               Versehen               |                                                                                                                            Beschreibung                                                                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Erstellen\_aktiviert            |                                                                                Gibt true zurück, wenn die Erstellung neuer Datensätze für die Entitäts Liste konfiguriert ist. Gibt andernfalls false zurück.                                                                                |
|              \_-URL erstellen              |                                                                                          Gibt den konfigurierten URL-Pfad für eine Erstellungs Verknüpfung/-Schaltfläche für die Entitäts Liste zurück.                                                                                          |
|            Detail\_aktiviert            |                                                                         Gibt true zurück, wenn eine Detailansicht für einzelne Datensätze für die Entitäts Liste konfiguriert ist. Gibt andernfalls false zurück.                                                                          |
|         Details\_ID\_Parameter         |               Gibt den Namen der Abfrage Zeichenfolgen-Parameter zurück, die für die Datensatz-ID beim Erstellen einer Datensatz-Detailansicht verwendet werden soll Weitere Informationen zur Verwendung von Liquid-Filtern zum Erstellen von URLs finden Sie unter [URL-Filter](liquid-filters.md#url-filters) . Beispiel: ID                |
|             Detail\_Bezeichnung             |                                                                                     Gibt die konfigurierte lokalisierte Bezeichnung für Verknüpfungen/Schaltflächen der Detailansicht für die Entitäts Liste zurück.                                                                                     |
|              Details\_URL              |                                                                                       Gibt den konfigurierten URL-Pfad für eine Detailansicht Links/Schaltflächen für die Entitäts Liste zurück.                                                                                        |
|           leere\_Liste\_Text           |                                                                                Gibt den konfigurierten lokalisierten Text zurück, der angezeigt wird, wenn die Entitäts Listenansicht keine Ergebnisse zurückgibt.                                                                                |
|      \_Entitäts\_Berechtigungen aktivieren      |                                                                               Gibt true zurück, wenn das Filtern von Entitäts Berechtigungen für diese Entitäts Liste aktiviert ist. Gibt andernfalls false zurück.                                                                               |
|         Entitäts\_logischer\_Name         |                                                 Gibt den logischen powerapps-Entitäts Namen für Datensätze zurück, die von dieser Entitäts Liste angezeigt werden sollen. Wenden Sie sich beispielsweise an                                                 |
|   \_Konto\_Attribut\_Name Filtern    |                                            Gibt den logischen Attributnamen für die Suche nach dem Konto zurück, das zum Filtern von Ergebnisdatensätzen nach dem übergeordneten Konto des aktuellen Portal Benutzers verwendet wird. Beispiel: AccountId                                            |
|         Filter\_\_Bezeichnung anwenden          |                                                            Gibt die konfigurierte lokalisierte Bezeichnung zurück, die für die Verknüpfung/Schaltfläche verwendet werden soll, die einen erweiterten Attribut Filter auf die Ergebnisse der Entitäts Liste anwendet.                                                            |
|          Filter\_Definition           |                      Gibt die JSON-Attribut Filter Definition für die Entitäts Liste zurück. Ausführliche Informationen zur Verwendung des Liquid-Filters für MetaFilter zum Verarbeiten dieser Definition finden Sie unter [Filter für Entitäts Listen](liquid-filters.md#entity-list-filters) .                       |
|            Filter\_aktiviert            |                                                                               Gibt true zurück, wenn die erweiterte Attribut Filterung für die Entitäts Liste aktiviert ist. Gibt andernfalls false zurück.                                                                               |
| Filter\_-Portal\_Benutzer\_Attribut\_Name |                                                 Gibt den logischen Attributnamen für die Suche an, die zum Filtern von Ergebnisdatensätzen nach dem Kontakt des aktuellen Portal Benutzers verwendet wird. Beispielsweise ContactID                                                  |
|   Filter\_Website\_Attribut\_Name    |                                              Gibt den logischen Attributnamen für die Suche an AdX\_-Website zurück, die zum Filtern von Ergebnisdatensätzen auf der aktuellen Portal Website verwendet wird. Beispiel: ADX\_WebsiteID                                              |
|            sprach\_Code             |                                               Gibt den Code der ganzzahligen powerapps-Sprache zurück, der verwendet wird, um alle lokalisierten Bezeichnungen für diese Entitäts Liste auszuwählen.                                                |
|              Seiten\_Größe               |                                                                                                   Gibt die konfigurierte Ergebnisseiten Größe für die Entitäts Liste zurück.                                                                                                    |
|          Name des primär\_Schlüssels\_           |                                                                                  Gibt den logischen Namen des Primärschlüssel Attributs für Datensätze zurück, die von dieser Entitäts Liste angezeigt werden sollen.                                                                                  |
|            Such\_aktiviert            |                                                                                         Gibt true zurück, wenn die Suche für diese Entitäts Liste aktiviert ist. Gibt andernfalls false zurück.                                                                                          |
|          \_Platzhalter suchen          |                                                                                        Gibt den konfigurierten lokalisierten Text für den Platzhalter für den Suchbereich der Entitäts Liste zurück                                                                                        |
|            \_QuickInfo suchen            |                                                                                             Gibt den konfigurierten lokalisierten Text für die QuickInfo der Entitäts Listen Suche zurück.                                                                                             |
|                 Ansichten                 |                                                                                           Gibt die verfügbaren Sichten für die Entitäts Liste als Objekte der Entitäts Listenansicht zurück.                                                                                           |
|      logischer Name des \[Attributs\]       | Sie können auf ein beliebiges Attribut des powerapps-Datensatzes der Entitäts Liste (ADX\_entityList) mithilfe des logischen namens zugreifen, und zwar auf dieselbe Weise wie ein [Entitäts](liquid-objects.md#entity) Objekt. Beispiel: {{entityList. ADX\_Name}} |

### <a name="entity-list-view-attributes"></a>Attribute der Entitäts Listenansicht

|          Versehen          |                                                                                     Beschreibung                                                                                     |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Spalten           |                                                         Gibt die Spalten der Sicht als Spalten Objekte der Entitäts Listenansicht zurück.                                                         |
|    Entitäts\_logischer\_Name    |               Gibt den logischen Namen der powerapps-Entität für die in der Sicht enthaltenen Datensätze zurück. Wenden Sie sich beispielsweise an                |
|             Id              |                                                                          Gibt die GUID-ID der Sicht zurück.                                                                           |
|       sprach\_Code        | Gibt den Code der ganzzahligen powerapps-Sprache zurück, der verwendet wird, um alle lokalisierten Bezeichnungen (Spaltenüberschriften usw.) für die Sicht auszuwählen. |
|            Name             |                                          Gibt den powerapps-anzeigen amen der Ansicht zurück.                                          |
| primärer\_Schlüssel\_logischer\_Name |        Gibt den logischen Namen des powerapps-Entitäts Primärschlüssels für die in der Sicht enthaltenen Datensätze zurück. Beispielsweise ContactID         |
|      \_Ausdruck sortieren       |                                               Gibt den Standard Sortier Ausdruck für die Ansicht zurück. Nennen Sie z. b. "ASC", "kreatedon".                                               |

### <a name="entity-list-view-column-attributes"></a>Spalten Attribute der Entitäts Listenansicht

|    Versehen     |                                                                                    Beschreibung                                                                                    |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Attribut\_Typs  | Gibt den powerapps-Attributtyp Namen für die Spalte als Zeichenfolge zurück. Beispiel: Lookup, picklist, String, Boolean, DateTime |
|  logischer\_Name   |                       Gibt den logischen Namen des powerapps-Attributs für die Spalte zurück. Beispiel: "".                       |
|       Name       |                      Gibt den lokalisierten powerapps-anzeigen Amen für die Spalte zurück. Beispielsweise erstellt am                       |
| \_aufsteigend sortieren  |                                      Gibt eine Sortier Ausdrucks Zeichenfolge zum Sortieren der Spalte in aufsteigender Reihenfolge zurück. Beispielsweise:                                       |
| \_absteigend sortieren |                                     Gibt eine Sortier Ausdrucks Zeichenfolge zum Sortieren der Spalte in absteigender Reihenfolge zurück. Beispiel: "kreatedon"                                      |
|  Sortierung\_deaktiviert  |                                                   Gibt true zurück, wenn die Sortierung für die Spalte deaktiviert ist. Gibt andernfalls false zurück.                                                    |
|  Sortierung\_aktiviert   |                                                    Gibt true zurück, wenn die Sortierung für die Spalte aktiviert ist. Gibt andernfalls false zurück.                                                    |
|      width       |                                                              Gibt die konfigurierte Breite für die Spalte in Pixel zurück.                                                              |

## <a name="entityview"></a>entityview

Das entityview-Objekt wird innerhalb des entityview-Tags verwendet und ermöglicht den Zugriff auf die Metadaten für die Sicht, zusätzlich zum Anzeigen von Ergebnisdatensätzen.

### <a name="attributes"></a>Attribute

|          Versehen          |                                                                               Beschreibung                                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Spalten           |                         Gibt die Spalten in der Sicht als [Entitäts Sicht-Spalten Objekte](liquid-objects.md#entity-list-view-column-attributes)zurück.                          |
| Berechtigung für Entitäts\_\_verweigert  | Gibt "true" zurück, wenn der Zugriff zum Anzeigen von Ergebnissen aufgrund unzureichender Entitäts Berechtigungen für den aktuellen Benutzer verweigert wurde. Gibt false zurück, wenn der Lesezugriff zum Anzeigen der Ergebnisse gewährt wurde. |
|    Entitäts\_logischer\_Name    |                   Der logische Name der powerapps-Entität der Ergebnisdaten Sätze der Sicht. Wenden Sie sich beispielsweise an                   |
|         erste\_Seite         |                 Die Seitenzahl der ersten Seite der Sicht Ergebnisse. Dies ist 1, es sei denn, es wurden keine Ergebnisse zurückgegeben. in diesem Fall ist der Wert NULL.                  |
|             Id              |                            Die GUID-ID der powerapps-Ansicht, die diese entityview definiert.                             |
|       sprach\_Code        |             Der Code der ganzzahligen powerapps-Sprache, mit dem lokalisierte Bezeichnungen für die aktuelle Ansicht geladen werden.              |
|         Letzte\_Seite          |                                 Die Seitenzahl der letzten Seite der Sicht Ergebnisse. Wenn keine Ergebnisse zurückgegeben wurden, ist dies NULL.                                  |
|            Benennen             |              Der Name der powerapps-Ansicht, die diese entityview definiert, z. b. aktive Kontakte.               |
|         nächste\_Seite          |                                Die Seitenzahl der nächsten Seite der Sicht Ergebnisse. Wenn keine nächste Seite mit Ergebnissen vorhanden ist, ist dies NULL.                                 |
|            s             |                                                           Die Seitenzahl der aktuellen Seite der Sicht Ergebnisse.                                                           |
|            Seiten            |                                          Gibt ein Array von Seitenzahlen zurück, das alle Seiten der Ergebnisse für die aktuelle Ansicht enthält.                                          |
|         Seiten\_Größe          |                                                      Die Anzahl der für die aktuelle Ansicht pro Seite zurückgegebenen Ergebnisse.                                                       |
|       vorherige\_Seite        |                              Die Seitenzahl der nächsten Seite der Sicht Ergebnisse. Wenn keine vorherige Seite mit Ergebnissen vorhanden ist, ist diese NULL.                               |
| primärer\_Schlüssel\_logischer\_Name |  Der logische powerapps-Name des Primary Key-Attributs der Ergebnis Entität für diese Sicht. Beispielsweise ContactID.   |
|           Best           |                                                   Die aktuelle Seite der Ergebnisdaten Sätze für die Sicht als Entitäts Objekte.                                                    |
|      \_Ausdruck sortieren       |                                             Der Standard Sortier Ausdruck für die Ansicht. Beispiel: nameasc, kreatedon Entsc.                                              |
|        Gesamt\_Seiten         |                                                              Die Gesamtanzahl der Ergebnisseiten für die Sicht.                                                              |
|       Gesamtanzahl\_Datensätze        |                                                       Die Gesamtanzahl der Ergebnisse für die Ansicht (auf allen Seiten).                                                       |

## <a name="events"></a>Fall

Bietet die Möglichkeit, auf Ereignisse zuzugreifen und Sie zu Rendering. Mit dem Events-Objekt können Sie ein bestimmtes Ereignis oder alle Ereignisse auswählen.

### <a name="events-object"></a>Events-Objekt

Das Ereignis Objekt ermöglicht Ihnen den Zugriff auf ein bestimmtes Ereignis im Portal oder auf das Zugreifen auf alle Ereignisse im Portal (unabhängig vom Ereignis).

Das Ereignis Objekt weist die folgenden Attribute auf:

|Versehen   |Beschreibung   |
|---|---|
|vorkommen |Gibt ein eventeventancessobject-Objekt zurück, das alle Ereignis vorkommen im Portal enthält. |
|[Ereignis Name oder ID] |Sie können auf jedes beliebige Ereignis über dessen Name oder ID-Eigenschaften zugreifen.<br>{% Assign Event = Ereignisse [&quot;Ereignis Name&quot;]%}<br>{% Assign Event = Ereignisse [&quot;da8b8a92-2ee6-476f-8a21-782b047ff460&quot;]%} |

### <a name="event-object"></a>Ereignis Objekt

Das Ereignis Objekt ermöglicht Ihnen das Arbeiten mit einem einzelnen Ereignis, sodass Sie auf die Zeitpläne und Vorkommen für dieses Ereignis zugreifen können.

Das Ereignis Objekt hat die folgenden Attribute:

|Versehen   |Beschreibung   |
|---|---|
| Alltag | Gibt ein eventocaccesscesobject-Objekt zurück, das alle Vorkommen für das Ereignis enthält. |
| Benennen       | Der Name des Ereignisses.                                                     |
| Urne        | Die URL des Ereignisses.                                                      |

### <a name="eventoccurences-object"></a>eventvorkommen-Objekt

Mit dem eventvorkommen-Objekt können Sie auf eine Auflistung von Ereignissen für Ereignis vorkommen zugreifen. Sie können die Ereignis vorkommen anordnen und einen Datumsbereich für die abzurufenden vorkommen angeben. Außerdem können Sie die Paginierung mithilfe von Liquid-Filtern erreichen.

```
{% assign occurances = event.occurrences.from[today].to[advance_date] %}
```

Beachten Sie, dass

```
{% assign occurances = event.occurrences.min[today].max[advance_date] %}
```

ist ebenfalls möglich.

Die folgenden Attribute sind dem eventvorkommen-Objekt zugeordnet.

|Versehen   |Beschreibung   |
|---|---|
| Allen | Gibt alle eventvorkommen-Objekte in der Auflistung zurück. |

### <a name="eventoccurence-object"></a>eventvorkommen-Objekt

Stellt das Vorkommen eines einzelnen Ereignisses dar. Die zugeordneten Attribute sind unten angegeben:

|Versehen   |Beschreibung   |
|---|---|
| Urne                 | Die URL des Auftretens.    |
| \_alle\_Tag\_Ereignis | Handelt es sich um ein alltägige Ereignis?     |
| Start\_Zeit         | Die Startzeit für das Ereignis. |
| Endzeit\_           | Die Endzeit für das Ereignis.   |


## <a name="forloop"></a>Schleife

Enthält Eigenschaften, die in einem [for](iteration-tags.md#for) -Schleifen Block nützlich sind.  

> [!Note]
> Schleife kann nur innerhalb eines [for](iteration-tags.md#for) -Tags verwendet werden.

**Ordnung**

```
{% for child in page.children %}

{% if forloop.first %}

This is the first child page!

{% else %}

This is child page number {{ forloop.index }}.

{% endif %}

{% endfor %}
```

**Ausgeben**

```
This is the first child page!

This is child page number 2.

This is child page number 3.
```

### <a name="attributes"></a>Attribute

|Versehen   |Beschreibung   |
|---|---|
| Erstes   | Gibt true zurück, wenn es sich um die erste Iterations Schleife handelt. Gibt false zurück, wenn es sich nicht um die erste Iterations Datei handelt.       |
| Sin   | Die Position des aktuellen Elements in der Auflistung, wobei das erste Element die Position 1 hat.                   |
| index0  | Die Position des aktuellen Elements in der Auflistung, wobei das erste Element die Position 0 hat.                   |
| Last    | Gibt true zurück, wenn es sich um die letzte Iterations Schleife handelt. Gibt false zurück, wenn es sich nicht um die letzte Iterations Vorgang handelt.         |
| Füll  | Gibt die Anzahl der Iterationen für die Schleife zurück ߝ die Anzahl der Elemente in der Auflistung, die durchlaufen wird. |
| rindex  | Anzahl der Elemente, die in der Schleife verbleiben (Längen Index), wobei 1 der Index des letzten Elements ist.              |
| rindex0 | Anzahl der Elemente, die in der Schleife verbleiben (Längen Index), wobei 0 der Index des letzten Elements ist.              |


## <a name="forums"></a>Fan

Bietet die Möglichkeit, auf Foren und Forenthreads zuzugreifen und diese zu Rendering. Beachten Sie, dass die Möglichkeit zur Verwendung von Liquid zum renderingforendaten in Beiträgen erweitert wird. um jedoch einen neuen Post-oder Thread zu erstellen, müssen Sie eine ASP.net Web Forms-Seitenvorlage mit der in integrierten Funktionalität (z. b. dem Standard Forums Thread und den Vorlagen-Post Page Vorlagen) verwenden.

Das Forums Objekt ermöglicht Ihnen die Auswahl eines Forums oder Forenthreads:

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

### <a name="forums-object"></a>Forums Objekt

Das Forums Objekt ermöglicht Ihnen den Zugriff auf ein bestimmtes Forum im Portal oder auf das Zugreifen auf alle Forenthreads im Portal (unabhängig vom Forum).

Das Forums Objekt ermöglicht Ihnen das Arbeiten mit einem einzelnen Forum, das Ihnen den Zugriff auf die Threads für dieses Forum ermöglicht.

Das Forumthreads-Objekt ermöglicht den Zugriff auf eine Auflistung von Forumthread-Objekten. Mithilfe von Liquid-filtern können Sie die Forenthreads sortieren und auch Paginierung erzielen.

```
{% assign threads = forum.threads | order_by adx_name, desc | paginate: 0,4 | all %}
```

Ein einzelner Forums Thread

Das forumposts-Objekt ermöglicht den Zugriff auf eine Auflistung von Forumpost-Objekten.

### <a name="attributes"></a>Attribute

|Versehen   |Beschreibung   |
|---|---|
| Threads              | Gibt ein Forumthreads-Objekt zurück, das alle Forumthread-Objekte im Portal enthält.             |
| Allen                  | Gibt alle Forums Objekte im Portal zurück. Beachten Sie, dass Website. Forums gleichwertig ist.    |
| Thread\_Anzahl        | Gibt den ganzzahligen Wert für die Anzahl der Threads zurück, die auf der gesamten Website vorhanden sind. |
| Anzahl nach\_          | Gibt den ganzzahligen Wert der Gesamtanzahl von Beiträgen im Portal zurück.                       |
| Name oder ID des \[Forums\] | Sie können mit den Eigenschaften "Name" oder "ID" auf jedes Forum zugreifen. <br>"{% Assign Forum = Foren [Forums Name]%}<br>{% Assign Forum = Foren [da8b8a92-2ee6-476f-8a21-782b047ff460]%} 

### <a name="forum-object"></a>Forums Objekt

### <a name="attributes"></a>Attribute

> [!Note]
> [Kleinstunternehmen](#entities)

|Versehen   |Beschreibung   |
|---|---|
| Threads       | Gibt ein Forumthreads-Objekt zurück, das alle Forenthreads für das Forum enthält.               |
| Name          | Der Name des Forums.                                                                  |
| Thread\_Anzahl | Gibt den ganzzahligen Wert für die Anzahl der Threads zurück, die im Forum vorhanden sind.      |
| Anzahl nach\_   | Gibt den ganzzahligen Wert der Anzahl von Beiträgen im gesamten Forum zurück. |

### <a name="forumthreads-object"></a>Forumthreads-Objekt

### <a name="attributes"></a>Attribute

|Versehen   |Beschreibung   |
|---|---|
| Allen | Gibt alle Forenthread-Objekte in der Auflistung zurück. |

### <a name="forumthread-object"></a>forumschlag Thread-Objekt

### <a name="attributes"></a>Attribute

> [!Note]
> [Kleinstunternehmen](#entities)

|Versehen   |Beschreibung   |
|---|---|
| Beiträge        | Gibt ein forumposts-Objekt zurück, das alle Forenbeiträge für den Thread enthält.            |
| Schrift       | Gibt den Autor für den Thread zurück (bei dem es sich einfach um ein Contact-Entitäts Objekt handelt).      |
| Letztes\_Beitrag | Gibt den letzten Beitrag im Thread zurück.                                            |
| erste\_Post  | Gibt den ersten Beitrag im Thread zurück.                                             |
| Anzahl nach\_  | Gibt den ganzzahligen Wert der Anzahl von Beiträgen im Thread zurück. |
| wird\_beantwortet | Wurde der Thread beantwortet oder nicht?                                                    |
| ist\_Kurznotiz   | Ist der Thread ein Kurznotiz Thread?                                                    |

### <a name="forumposts-object"></a>forumposts-Objekt

### <a name="attributes"></a>Attribute

|Versehen   |Beschreibung   |
|---|---|
| Allen | Gibt alle Forenthread-Objekte in der Auflistung zurück. |

Ein einzelner Forumsbeitrag

### <a name="attributes"></a>Attribute

> [!Note] 
> [Kleinstunternehmen](#entities)

|Versehen   |Beschreibung   |
|---|---|
| Schrift     | Gibt den Autor für den Beitrag zurück (bei dem es sich einfach um ein Contact-Entitäts Objekt handelt). |
| Inhaltliche    | Der Inhalt des Beitrags.                                                   |
| ist\_Antwort | Hat dies eine Antwort an den Thread gepostet?                                      |


## <a name="knowledge"></a>Kenntnissen

Bietet Zugriff auf powerapps-Entitäts Datensätze "knowledgearticle" und "Category" zum Rendering von Artikeln und Kategorien in einem Portal.

### <a name="attributes"></a>Attribute

|Versehen|Beschreibung|
|---|---|
|Gegenstände|Gibt ein Artikel Objekt zurück, das Artikel Objekte für die im Portal verfügbaren knowledgearticle-Entitäts Datensätze enthält.|
|Klassen|Gibt ein categories-Objekt mit kategorieobjekten für die kategorieentitäts Datensätze zurück, die im Portal|
|||

### <a name="articles-object"></a>Articles-Objekt

Das Artikel Objekt ermöglicht den Zugriff auf eine Sammlung von Artikel Objekten. Sie können die Artikel Sortieren und die Paginierung auch durch Verwendung von Liquid-Filtern erreichen.

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

|Versehen|Beschreibung|
|---|---|
|Beliebtheit |Gibt eine Auflistung von Artikel Objekten zurück, die die meisten Ansichten enthalten. `{% assign popular_articles = knowledge.articles.popular %}` |
|jüngste |Gibt eine Auflistung von Artikel Objekten zurück, die das Datum der letzten Änderung enthalten. `{% assign recent_articles = knowledge.articles.recent %}` |
|top |Gibt eine Auflistung von Artikel Objekten zurück, die die höchste Bewertung enthält. `{% assign top_articles = knowledge.articles.top  %}` |
| | |

### <a name="filters"></a>Filter

Die folgenden Filter können optionale Parameter für die Seitengröße und Sprache akzeptieren. Der erste Parameter ist die Anzahl der abzurufenden Datensätze. Die Standardseiten Größe ist 5. Der zweite Parameter ist der Code einer Sprache zum Abrufen von Artikeln für eine bestimmte Sprache. Filter können mit anderen [flüssigen Filtern](liquid-filters.md)kombiniert werden.

```
{% assign page_size = 5 %}
{% assign language_code = website.selected_language.code %}
{% assign recent_articles = knowledge.articles | recent: page_size, language_code %}
```

|Versehen|Beschreibung|
|---|---|
|Beliebtheit |Gibt eine Auflistung von Artikel Objekten zurück, die die meisten Ansichten enthalten. `{% assign popular_articles = knowledge.articles \| popular: 10, en-US %}` |
|jüngste |Gibt eine Auflistung von Artikel Objekten zurück, die das Datum der letzten Änderung enthalten. `{% assign recent_articles = knowledge.articles \| recent: 5 %}` |
|top |Gibt eine Auflistung von Artikel Objekten zurück, die die höchste Bewertung enthält. `{% assign top_articles = knowledge.articles \| top: 3, en-US %}` |
| | |

### <a name="categories-object"></a>Categories-Objekt

Das categories-Objekt ermöglicht den Zugriff auf eine Auflistung von kategorieobjekten. Sie können die Kategorien sortieren und die Paginierung auch durch Verwendung von Liquid-Filtern erreichen.

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

|Versehen|Beschreibung|
|---|---|
|jüngste |Gibt eine Auflistung von kategorieobjekten zurück, die das Datum der letzten Änderung enthalten. |
|top_level |Gibt eine Auflistung von kategorieobjekten zurück, die keine übergeordnete Kategorie haben. |
|||

### <a name="filters"></a>Filter

Die folgenden Filter können einen optionalen Parameter annehmen, der die Seitengröße angibt. Die Standardseiten Größe ist 5. Filter können mit anderen [flüssigen Filtern](liquid-filters.md)kombiniert werden.

```
{% assign page_size = 5 %}
{% assign recent_categories = knowledge.categories | recent: page_size %}
```

|Versehen|Beschreibung|
|---|---|
|jüngste |Gibt eine Auflistung von kategorieobjekten zurück, die das Datum der letzten Änderung enthalten. Sie können Parameter angeben `{% assign recent_categories = knowledge.categories \| recent: 10 %}` |
|top_level |Gibt eine Auflistung von kategorieobjekten zurück, die keine übergeordnete Kategorie haben. `{% assign root_categories = knowledge.categories \| top_level %}` |
|||

### <a name="article-object"></a>Artikel Objekt

Das Artikel Objekt ermöglicht Ihnen das Arbeiten mit einem einzelnen knowledgearticle, um Details zu diesem Artikel im Portal anzuzeigen.

### <a name="attributes"></a>Attribute

der Artikel ist ein [Entitäts](#entity) Objekt mit den gleichen Attributen, zusätzlich zu den unten aufgeführten Attributen.

|Versehen|Beschreibung|
|---|---|
|article_public_number| Der öffentliche Artikelnummer des Artikels.|
|comment_count| Der ganzzahlige Wert der Anzahl der Kommentare, die für einen bestimmten Artikel vorhanden sind.|
|Inhaltliche|Der Inhalt des Artikels.|
|current_user_can_comment|Gibt einen booleschen Wert zurück, der angibt, ob der aktuelle Benutzerkommentare zum Artikel hinzufügen kann.|
|is_rating_enabled|Gibt einen booleschen Wert zurück, der angibt, ob die Bewertung für einen Artikel aktiviert ist.|
|Keywords|Die Schlüsselwörter für den Artikel.|
|Benennen|Ein alternativer Alias für den Titel des Artikels.|
|Leistung|Der Dezimal Bewertungs Wert für den Artikel.|
|Tel|Der Titel des Artikels.|
|view_count|Der ganzzahlige Wert der Häufigkeit, mit der der Artikel angezeigt wurde.|
|||

### <a name="category-object"></a>Category-Objekt

Mit dem Kategorieobjekt können Sie mit einer einzelnen Kategorie arbeiten, um die Details im Portal anzuzeigen.

### <a name="attributes"></a>Attribute

Category ist neben den unten aufgeführten [Entitäts](#entity) Objekten mit allen Attributen identisch.

|Versehen|Beschreibung|
|---|---|
|CategoryNumber|Die Kategorienummer der Kategorie.|
|Benennen|Ein alternativer Alias für den Titel der Kategorie.|
|Tel|Der Titel der Kategorie.|
|||

## <a name="page"></a>s

Verweist auf die aktuelle Portal Anforderungsseite. Dieses Objekt kombiniert die Attribute der [Sitemap](#sitemap) und der aktuellen Anforderungs [Entitäten](#entities) (in der Regel eine Webseite).  

Das Page-Objekt ermöglicht den Zugriff auf Elemente wie den Brotkrümel für die aktuelle Seite, den Titel oder die URL der aktuellen Seite sowie alle anderen Attribute oder zugehörigen Entitäten des zugrunde liegenden powerapps-Datensatzes.

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

### <a name="page-attributes"></a>Seiten Attribute

> [!Note]  
> [Kleinstunternehmen](#entities)

|             Versehen              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Breadcrumbs             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Gibt die Breadcrumb-Site Übersichts Knoten Objekte für die Seite zurück, beginnend mit dem Stamm Knoten der Site Übersicht und endende bei übergeordnetem Element.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|              Kind              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Gibt die untergeordneten Site Map-Knoten Objekte der Seite zurück.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|               übergeordneten               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           Gibt den übergeordneten Site Übersichts Knoten der Seite zurück. Wenn die Seite die Startseite ist, wird das übergeordnete Element NULL sein.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|               Tel                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Der Titel der Seite.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                Urne                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Die URL der Seite.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| \[Attribut-oder Beziehungs Name\] | Sie können auf jedes Attribut des zugrunde liegenden powerapps-Datensatzes der Seite über den logischen Namen zugreifen.<br>`{{ page.createdon }}`<br>`{% assign attribute_name = 'name' %}`<br>`{{ page[attribute_name] }}`<br>Die Werte der meisten Entitäts Attribute sind direkt den [Liquid-Typen](liquid-types.md)zugeordnet: zwei Options Felder werden booleschen Werten, Textfeldern zu Zeichen folgen, numerischen/Währungs Feldern zu zahlen, Datums-/Uhrzeitfelder und Datums Objekten zugeordnet. Einige Attributtypen werden jedoch als Objekte zurückgegeben:<ul><li>Suchfelder (Entitäts Verweis) werden als [Entitäts Verweis Objekte](#entity-reference)zurückgegeben.</li><li>Options Satz-/picklist-Felder werden als [options Satz Wert-Objekte](#option-set-value)zurückgegeben.</li> Sie können auch alle zugehörigen Entitäten nach beziehungsschema Namen laden. <br> `{{ page.adx_webpage_entitylist.adx_name }}`<br>Wenn eine Beziehung reflexiv (d. h. selbstreferenziell) ist, wird ein [Entitäts](#entities) Objekt zurückgegeben. (Andernfalls wäre das Ergebnis mehrdeutig.)`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**Hinweis**: das Laden einer großen Anzahl von verknüpften Entitäten oder das Zugreifen auf eine große Anzahl von Beziehungen in einer einzelnen Vorlage kann sich negativ auf die Leistung von Vorlagen Rendering auswirken. Vermeiden Sie das Laden von verknüpften Entitäten für jedes Element in einem Array innerhalb einer Schleife. Verwenden Sie nach Möglichkeit die Verwendung der [powerapps Common Data Service-Entitäts Tags](portals-entity-tags.md) , um Auflistungen von Entitäten zu laden. |

## <a name="polls"></a>Pokal

Bietet die Möglichkeit, auf einen Abruf zuzugreifen und ihn zu erzeugen.

Mit dem "Umfragen"-Objekt können Sie eine bestimmte Abruf-oder Abruf Platzierung auswählen:

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

### <a name="polls-attributes"></a>Ruft Attribute ab.

|Versehen   |Beschreibung   |
|---|---|
| Vermittlung          | Gibt das pollplacement-Objekt zurück.                                      |
| \[Abrufen des Namens oder der ID\] | Sie können mit den Eigenschaften Name oder ID auf alle Abfragen zugreifen. `{% assign poll = polls[Poll Name] %}`<br>`{% assign poll = polls["41827a5c-33de-49b8-a0c7-439e6a02eb98"] %}`  |

### <a name="poll-placements-attributes"></a>Platzierungs Attribute abrufen

|Versehen   |Beschreibung   |
|---|---|
| der Name oder die ID der \[Abruf Platzierung\] | Sie können auf eine beliebige Abruf Platzierung mit ihren Namen-oder ID-Eigenschaften zugreifen.`{% assign placement = polls.placements[Placement Name or Id] %}`<br>`{% assign placement = polls.placements[7677c5d4-406e-4b6c-907c-916ac17dba0f] %} `|

### <a name="poll-placement-attributes"></a>Platzierungs Attribute abrufen

> [!Note] 
> [Kleinstunternehmen](#entities)                                       

|Versehen   |Beschreibung   |
|---|---|
| Name           | Gibt das Namensfeld für die Abruf Platzierung zurück.                            
| Platzierung\_URL | Die URL, die zum Abrufen der von einer Vorlage vollständig gerenderten Abruf Platzierung verwendet werden kann.                       |
| Pokal          | Gibt die Auflistung der der Platzierung zugeordneten Abruf Objekte zurück. [Iterations Tags](iteration-tags.md) und [Array Filter](liquid-filters.md#array-filters) können mit dieser Auflistung verwendet werden.  |  
| Random\_URL    | Die URL, die verwendet werden kann, um einen zufälligen Abruf von der Platzierung abzurufen, die vollständig von einer Vorlage gerendert wird.         |
| Senden\_URL    | Die URL, an die ein abgeschlossener Abruf übermittelt wird.                                                             |

### <a name="poll-attributes"></a>Abruf Attribute

> [!Note] 
> [Kleinstunternehmen](#entities)                                          

|Versehen   |Beschreibung   |
|---|---|
| hat\_Benutzer\_abgestimmt       | Gibt true zurück, wenn der aktuelle (angemeldete oder anonyme) Benutzer bereits in dieser Umfrage zugestimmt hat.         |
| Name                   | Gibt das Namensfeld für die Abfrage zurück.                                                              |
| Optionen                | Gibt die Auflistung von Abruf Options Objekten zurück, die der Abfrage zugeordnet sind. [Iterations Tags](iteration-tags.md) und- [Entitäten](#entities) können mit dieser Sammlung verwendet werden.  |  
| \_-URL abrufen              | Die URL, mit der der Abruf vollständig von einer Vorlage gerendert werden kann.                       |
| betreffenden               | Gibt das Fragefeld für die Abfrage zurück.                                                          |
| \_Schaltfläche\_Bezeichnung übermitteln  | Gibt eine Zeichenfolge zurück, die verwendet werden kann, um die Bezeichnung für das Senden einer Schaltfläche für den Abruf zu               |
| Senden\_URL            | Die URL, an die ein abgeschlossener Abruf übermittelt wird.                                                   |
| Benutzer\_\_Option ausgewählt | Gibt das vom Benutzer ausgewählte polloption-Objekt zurück (wenn Sie bereits gewählt haben).                  |
| Abgabe                  | Gibt die Anzahl der Stimmen zurück, die für die Abfrage in der Tabelle angezeigt wurden.                                |

### <a name="poll-option-attributes"></a>Abruf Options Attribute

>[!Note]
> [Kleinstunternehmen](#entities)                                         

|Versehen   |Beschreibung   |
|---|---|
| Te     | Gibt das Antwortfeld für die Abfrage zurück. |
| aler | Gibt den Prozentsatz der Stimmen in der Abfrage für die Option als Dezimalzahl zwischen 0 und 100 zurück. |
| Abgabe      | Gibt die Anzahl der Stimmen zurück, die für die Option in Tabellenform angezeigt wurden.                              |


## <a name="request"></a>Anforderung

Enthält Informationen über die aktuelle HTTP-Anforderung.

```
{% assign id = request.params['id'] %}

<a href={{ request.url | add_query: 'foo', 1 }}>Link</a>
```

> [!Note]
> Sie können URLs dynamisch in Liquid erstellen, indem Sie URL-Filter verwenden. 

### <a name="attributes"></a>Attribute

|Versehen   |Beschreibung   |
|---|---|
| params           | Benannte Parameterwerte für die aktuelle Anforderung. Parameter sind eine Kombination aus URL-Abfrage Zeichenfolgen-Parametern, Formular Bereitstellungs Parametern und Cookies.  |
| ADS             | Der Pfad der aktuellen Anforderungs-URL. <br> /profile|
| Pfad\_und\_Abfrage | Der Pfad und die Abfrage der aktuellen Anforderungs-URL.<br> /Profile/? foo = 1 & Leiste = etwas|
| query            | Der Abfrage Teil der aktuellen Anforderungs-URL. <br> ? foo = 1 & Leiste = etwas |
| Urne              | Die vollständige URL der aktuellen Anforderung.<br>  http://www.example.com/profile/?foo=1&bar=something  |


## <a name="searchindex"></a>SearchIndex

Das SearchIndex-Objekt wird innerhalb der [powerapps Common Data Service-Entitäts Tags](portals-entity-tags.md)verwendet und ermöglicht den Zugriff auf die Ergebnisse einer Abfrage.  

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

|Versehen   |Beschreibung   |
|---|---|
| ungefähre\_Gesamt\_Treffer | Gibt eine ungefähre Anzahl von Treffern zurück, die mit der Index Abfrage übereinstimmen. Beachten Sie, dass diese Zahl aufgrund der Art und Weise, wie der Suchindex in Bezug auf die Sicherheits Filterung und andere Entwurfs Faktoren funktioniert, nur eine Näherung darstellt und möglicherweise nicht genau mit der Gesamtzahl der Ergebnisse übereinstimmt, die dem aktuellen Benutzer in einigen Situationen zur Verfügung stehen.  |
| s                     | Gibt die Seitenzahl der aktuellen Abfrage zurück.                                                                                                                                                                                                           |
| Seiten\_Größe               | Gibt die maximale Seitengröße der aktuellen Abfrage zurück. Wenn die tatsächliche Anzahl der Ergebnisse für die aktuelle Seite zurückgegeben werden soll (da dies möglicherweise kleiner als die angegebene maximale Seitengröße ist), verwenden Sie "results. Size".                                                                                           |
| Folgen                  | Gibt die Abfrageergebnis Seite als Such Index Ergebnis-Objekte zurück.                                                                                                                                                                                          |

### <a name="search-index-results"></a>Such Index Ergebnisse

|   Versehen   |                                                                                                                                                Beschreibung                                                                                                                                                 |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Organisation     |                                                                                                                            Die zugrunde liegenden [Entitäten](#entities) für das Ergebnis.                                                                                                                            |
|   Bruch    | Ein relevantes kurzes Textfragment für das Ergebnis, wobei die mit der angegebenen Abfrage übereinstimmenden Begriffe mithilfe des &lt;EM&gt; HTML-Tags hervorgehoben werden. Beachten Sie, dass bestimmte Abfrage Typen keine markierten Fragmente unterstützen, wie z. b. fuzzyabfragen (~) und Platzhalter Abfragen (\*). Diese Eigenschaft ist in diesen Fällen NULL. |
|      Id       |                                                             Die powerapps-Entitäts-ID des zugrunde liegenden Datensatzes für das Ergebnis als Zeichenfolge. Beispiel: 936da01f -9abd-4d9d-80c7-02af85c822a8                                                              |
| logischer\_Name |                                                                           Der logische Name der powerapps-Entität des zugrunde liegenden Datensatzes für das Ergebnis. Beispiel: ADX\_Webseite                                                                           |
|    Zahl     |                                                            Die Anzahl der Ergebnisse auf allen Ergebnisseiten, beginnend bei 1. Beispielsweise ist der Wert für das erste Ergebnis der zweiten Seite der Ergebnisse mit der Seitengröße 10 11.                                                             |
|     Endergebnis     |                                                                                                 Das Lucene-Ergebnis des Ergebnisses, als Gleit Komma Wert. Die Ergebnisse werden nach diesem Wert geordnet zurückgegeben.                                                                                                 |
|     Tel     |                                                                                                                                          Der Titel des Ergebnisses.                                                                                                                                          |
|      Urne      |                                                            Die URL für das Ergebnis. Dies wird in der Regel&mdash;, aber nicht notwendigerweise&mdash;als absoluter Pfad für die aktuelle Anwendung, sondern nicht als vollständige URL. Beispiel:/Articles/Article1/                                                             |

## <a name="settings"></a>Einstellungen

Ermöglicht das Laden beliebiger [Website Einstellungen](../configure/configure-site-settings.md) nach Namen. Wenn keine Einstellung mit dem angegebenen Namen gefunden wird, wird [null](liquid-types.md#null) zurückgegeben.  

> [!Note]
> Einstellungen [werden als Zeichen](liquid-types.md#string)folgen zurückgegeben, Sie können jedoch [Typfilter](liquid-filters.md#type-filters) verwenden, um Sie in andere Typen zu konvertieren.

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
> [Rendering einer Website Kopfzeile und der primären Navigationsleiste](render-site-header-primary-navigation.md)


## <a name="sitemap"></a>tex

Ermöglicht den Zugriff auf die Portal Site Übersicht.

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

### <a name="site-map-attributes"></a>Site Übersichts Attribute

|Versehen   |Beschreibung   |
|---|---|
| Strömung | Gibt das Site Map-Knoten Objekt für die aktuelle Seite zurück.                    |
| Fasst    | Gibt das Site Map-Knoten Objekt für die Stamm Seite (Homepage) der Website zurück. |

### <a name="site-map-node-attributes"></a>Attribute des Site Übersichts Knotens

|Versehen   |Beschreibung   |
|-------|-------|
| Breadcrumbs           | Gibt die Breadcrumb-Site Übersichts Knoten-Objekte für den Knoten zurück, beginnend mit dem Stamm Knoten der Site Übersicht und endende bei übergeordnetem Element. |
| Kind              | Gibt die untergeordneten Site Map-Knoten Objekte des Knotens zurück.                                                                  |
| Beschreibung           | Der Beschreibungs-/Zusammenfassungs Inhalt für den Knoten. (Dieses Feld kann HTML enthalten.)                                          |
| Organisation                | Gibt die zugrunde liegenden [Entitäten](#entities) des Knotens zurück. Wenn der Knoten nicht über eine zugrunde liegende Entität verfügt, ist dieser Wert NULL.                                                         |
| ist\_Sitemap\_Vorgänger | Gibt true zurück, wenn der Sitemap-Knoten ein Vorgänger des aktuellen Knotens ist, andernfalls false.                                                                                                         |
| ist\_Sitemap\_aktuell  | Gibt true zurück, wenn der Sitemap-Knoten der aktuelle Knoten ist, andernfalls false.                                                                                                         |
| übergeordneten                | Gibt den übergeordneten Site Übersichts Knoten des Knotens zurück. Wenn der Knoten der Stamm Knoten ist, ist das übergeordnete Element NULL.                                                                     |
| Title                 | Der Titel des Knotens.                                                                                                |
| Urne                   | Die URL des Knotens.                                                                                                  |


## <a name="sitemarkers"></a>sitemarkers

Ermöglicht das Laden beliebiger Site Marker nach Namen. Wenn sitemarker vorhanden ist, wird ein sitemarker-Objekt zurückgegeben. Wenn kein sitemarker mit dem angegebenen Namen gefunden wird, wird [null](liquid-types.md#null) zurückgegeben.  

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
> [Rendering einer Website Kopfzeile und der primären Navigationsleiste](render-site-header-primary-navigation.md)  

### <a name="sitemarker-attributes"></a>Sitemarker-Attribute

|         Versehen          |                                                                                    Beschreibung                                                                                    |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Urne             |                                                                         Die URL des sitemarker-Ziels.                                                                         |
| logischer Name des \[Attributs\] | Sie können auf jedes Attribut des sitemarker-Ziels powerapps-Datensatzes mit logischem Namen zugreifen. Beispiel: {{sitemarker. ADX\_Name}} |

## <a name="snippets"></a>p

Ermöglicht das Laden beliebiger Inhalts Ausschnitte nach Namen. Wenn kein Code Ausschnitt mit dem angegebenen Namen gefunden wird, wird [null](liquid-types.md#null) zurückgegeben.  

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

Enthält Eigenschaften, die in einem Schleifen Block für [iterations Tags](iteration-tags.md) nützlich sind.  

> [!Note] 
> tablerowloop kann nur innerhalb eines [iterationtagtags](iteration-tags.md) verwendet werden.

### <a name="attributes"></a>Attribute

|Versehen   |Beschreibung   |
|---|---|
| Col        | Gibt den Index der aktuellen Zeile zurück, beginnend bei 1.                                                       |
| col0       | Gibt den Index der aktuellen Zeile zurück, beginnend bei 0.                                                       |
| zuerst\_Spalten | Gibt true zurück, wenn die aktuelle Spalte die erste Spalte in einer Zeile ist, andernfalls false.               |
| Letzte Spalten\_  | Gibt true zurück, wenn es sich bei der aktuellen Spalte um die letzte Spalte in einer Zeile handelt, andernfalls false.                |
| First      | Gibt true zurück, wenn es sich um die erste Iterations Schleife handelt. Gibt false zurück, wenn es sich nicht um die erste Iterations Datei handelt.       |
| Sin      | Die Position des aktuellen Elements in der Auflistung, wobei das erste Element die Position 1 hat.                   |
| index0     | Die Position des aktuellen Elements in der Auflistung, wobei das erste Element die Position 0 hat.                   |
| Last       | Gibt true zurück, wenn es sich um die letzte Iterations Schleife handelt. Gibt false zurück, wenn es sich nicht um die letzte Iterations Vorgang handelt.         |
| Füll     | Gibt die Anzahl der Iterationen für die Schleife zurück ߝ die Anzahl der Elemente in der Auflistung, die durchlaufen wird. |
| rindex     | Anzahl der Elemente, die in der Schleife verbleiben (Längen Index), wobei 1 der Index des letzten Elements ist.              |
| rindex0    | Anzahl der Elemente, die in der Schleife verbleiben (Längen Index), wobei 0 der Index des letzten Elements ist.              |



## <a name="user"></a>Bedienungs

Bezieht sich auf den aktuellen Portalbenutzer, der den Zugriff auf alle Attribute des zugrunde liegenden powerapps-Kontaktdaten Satzes ermöglicht. Wenn kein Benutzer angemeldet ist, ist diese Variable [null](liquid-types.md#null).  

der Benutzer ist ein [Entitäts](#entity) Objekt.  

```
{% if user %}

Hello, {{ user.fullname }}!

{% else %}

Hello, anonymous user!

{% endif %}
```

### <a name="attributes"></a>Attribute

Zusätzlich zu allen Attributen eines [Entitäts](#entity) Objekts verfügt der Benutzer über die folgenden Attribute.


|    Versehen     |                                                                                                                                                                                     Beschreibung                                                                                                                                                                                     |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Rollen       |                                                      Gibt die Rollen zurück, zu denen der Benutzer gehört, als [Array](liquid-types.md#array).<br>`{% if user.roles contains 'Administrators' %} User is an administrator. {% endif %}`<br>**Hinweis**: Sie können auch den `has_role` Filter verwenden, um die einzelnen Rollen Mitgliedschaften zu testen.                                                       |
| basic_badges_url | Gibt die Dienst-URL zum Abrufen der Ausweise eines Benutzers zurück.<br>Zum Rendering von Badge für einen Benutzer müssen Sie ein Tag mit den Attributen "Data-Badge" und "Data-URI" einschließen. So Rendering Sie die Kennzeichen des aktuellen Benutzers:<br>`<div data-badge data-uri='{{user.basic_badges_url }}'></div>`<br>So erstellen Sie die Ausweise eines Benutzers anhand der ID (Variable UserID)<br>\`< div Data-Badge Data-URI = ' {{User. basic_badges_url |
|                  |                                                                                                                                                                                                                                                                                                                                                                                     |

## <a name="weblinks"></a>Weblinks

Ermöglicht das Laden von Weblinks nach Name oder ID.  

Wenn die weblinkmenge vorhanden ist, wird ein [weblinkset-Objekt](#web-link-set-attributes) zurückgegeben. Wenn eine weblinkmenge mit dem angegebenen Namen oder der ID nicht gefunden wird, wird [null](liquid-types.md#null) zurückgegeben.


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
> [Eine Website Kopfzeile und eine primäre Navigationsleiste](render-site-header-primary-navigation.md) |  

### <a name="web-link-set-attributes"></a>Attribute für weblinksätze

> [!Note]
> Eine weblinkgruppe ist ein [Entitäts](#entity) Objekt mit den gleichen Attributen, zusätzlich zu den unten aufgeführten Attributen.                                         

|         Versehen          |                                                                                 Beschreibung                                                                                  |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Skopie            |                                                                      Die HTML-Kopie der weblinkgruppe.                                                                      |
|            Name            |                                                                        Der Name der weblinkgruppe.                                                                         |
|           Title            |                                                                        Der Titel der weblinkmenge.                                                                        |
|          Weblinks          |                                                       Das Array von Weblink-Objekten, die mit der weblinkmenge verknüpft sind.                                                        |
| logischer Name des \[Attributs\] | Sie können auf jedes Attribut des Weblink Satzes powerapps-Datensatz mit logischem Namen zugreifen. Beispiel: {{weblinkset. kreatedon}} |

### <a name="web-link-attributes"></a>Weblink Attribute

> [!Note]
> Ein Weblink ist ein [Entitäts](#entity) Objekt mit den gleichen Attributen, zusätzlich zu den unten aufgeführten Attributen.

|          Versehen          |                                                                              Beschreibung                                                                              |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Beschreibung         |                                                                 Die HTML-Beschreibung des Weblinks.                                                                 |
|    nur\_Bild anzeigen\_     |                              Ein boolesches Attribut, das angibt, ob der Weblink nur als Bild ohne Linktext angezeigt werden soll.                               |
| anzeigen\_Seite\_untergeordneten\_Links |            Boolesches Attribut, das angibt, ob der Weblink Links zu den untergeordneten [*Sitemap*](#sitemap) -Seiten der verknüpften Seite als untergeordnete Links anzeigen soll.             |
|            Bild            |                                     Das Weblink Bild-Objekt für diesen Link. Dieses Attribut ist NULL, wenn kein Bild vorhanden ist.                                      |
|        ist\_extern         |                 Ein boolesches Attribut, das angibt, ob die Ziel-URL des Weblinks eine externe Site ist (statt einer internen Portalseite).                  |
|    ist\_Sitemap\_Vorgänger    |                                Gibt true zurück, wenn die Weblink-URL auf einen Vorgänger des aktuellen Sitemap-Knotens verweist; andernfalls false.                                 |
|    ist\_Sitemap\_aktuell     |                                        Gibt true zurück, wenn die Weblink-URL auf den aktuellen Sitemap-Knoten verweist; andernfalls false.                                        |
|            Name             |                                                                    Der Name/Titel des Weblinks.                                                                    |
|          Nofollow           |                                         Boolesches Attribut, das angibt, ob der Weblink als rel = nofollow gekennzeichnet werden soll.                                         |
|    \_in\_Fenster "neues\_" öffnen    |                             Boolesches Attribut, das angibt, ob der Weblink bei ausgewählter Option in einem neuen Browserfenster bzw. einer neuen Registerkarte geöffnet werden soll.                             |
|           QuickInfo           |                                                                    QuickInfo-Text für den Weblink.                                                                     |
|             Urne             |                                                                       Die URL des Weblinks.                                                                        |
|          Weblinks           |                                                   Das Array von untergeordneten Weblink-Objekten, die mit dem Weblink verknüpft sind.                                                   |
| logischer Name des \[Attributs\]  | Sie können auf jedes Attribut des Weblink-powerapps-Datensatzes mit logischem Namen zugreifen. Beispiel: {{Weblink. kreatedon}} |

### <a name="web-link-image-attributes"></a>Weblink Bildattribute

| alternativer\_Text | Alternativer Text für das Bild.                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
| Höhe          | Eine ganze Zahl, die die angegebene Höhe des Bilds enthält. Wenn kein Height-Wert angegeben wurde, ist dieses Attribut NULL. |
| Urne             | Die URL des Bilds.                                                                                               |
| Breite           | Eine ganze Zahl, die die angegebene Breite des Bilds enthält. Wenn kein Breitenwert angegeben wurde, ist dieses Attribut NULL.   |


## <a name="website"></a>Website

Bezieht sich auf die Portal Website, die den Zugriff auf alle Attribute des Datensatzes der powerapps-Website (ADX\_-Website) für das Portal ermöglicht.  

> [!Note]
> Website ist ein [Entitäts](#entity) Objekt mit den gleichen Attributen.

**Ordnung**

```
{{ website.adx_name }} ({{ website.id }})
```

**Ausgeben**

```
Community Portal (936DA01F-9ABD-4d9d-80C7-02AF85C822A8)
```


### <a name="see-also"></a>Siehe auch

[Liquid-Typen](liquid-types.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md)  
