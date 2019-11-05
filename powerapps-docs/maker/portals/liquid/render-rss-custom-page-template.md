---
title: Rendering eines RSS-Feeds mithilfe einer benutzerdefinierten Seitenvorlage für ein Portal | MicrosoftDocs
description: Anweisungen zum Erstellen einer benutzerdefinierten Seitenvorlage und zum Rendering eines RSS-Feeds.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 240af2f54e153490794358dc1598b72a16fe1c38
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543317"
---
# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>Erstellen einer benutzerdefinierten Seitenvorlage zum Rendering eines RSS-Feeds
In diesem Beispiel erstellen wir eine benutzerdefinierte Seitenvorlage zum Rendering eines [RSS-Feeds](https://en.wikipedia.org/wiki/RSS) von Newsartikeln mithilfe von Liquid und einer Vorlage für eine Webvorlagen Seite. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Speichern von Quell Inhalten mithilfe von Webvorlagen](store-content-web-templates.md)  

## <a name="step-1-create-a-new-powerapps-view"></a>Schritt 1: Erstellen einer neuen powerapps-Ansicht

Zuerst erstellen wir eine neue powerapps-Ansicht, mit der wir die Daten für den Feed laden. In diesem Beispiel werden wir eine Ansicht auf Webseiten machen und diese Entität zum Speichern unserer Artikel verwenden. Mithilfe dieser Ansicht können Sie das Sortieren und Filtern von Ergebnissen konfigurieren und die Entitäts Attribute, die wir in unserer Liquid-Vorlage zur Verfügung stellen möchten, als Spalten einschließen.

![Bearbeiten einer Seitenvorlage](../media/edit-page-template.png "Bearbeiten einer Seitenvorlage")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>Schritt 2: Erstellen einer Webvorlage für den RSS-Feed

In diesem Schritt erstellen wir eine Webvorlage für unseren RSS-Feed. Diese Vorlage wird auf eine bestimmte Webseite auf unserer Website angewendet. Daher verwenden wir den Titel und die Zusammenfassung dieser Seite als Titel und Beschreibung des Feeds. Wir verwenden das entityview-Tag, um die neu erstellte News-Artikel Ansicht zu laden. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [powerapps Common Data Service-Entitäts Tags](portals-entity-tags.md). Beachten Sie, dass auch das Feld **MIME Type** der Webvorlage auf Application/RSS + XML festgelegt wird. Dies gibt an, wie der Antwort Inhaltstyp sein kann, wenn unsere Vorlage gerendert wird.  

![Konfigurieren einer Webvorlage für einen RSS-Feed](../media/web-template-rss-feed.png "Konfigurieren einer Webvorlage für einen RSS-Feed")  

### <a name="rss-feed-web-template"></a>RSS-Feed (Webvorlage)

```xml
<?xml version=1.0 encoding=UTF-8 ?>
<rss version=2.0>
  <channel>
    <title>{{ page.title | xml_escape }}</title>
    <description>{{ page.description | strip_html | xml_escape }}</description>
    <link>{{ request.url | xml_escape }}</link>
    {% entityview logical_name:'adx_webpage', name:'News Articles', page_size:20 -%}
      {% for item in entityview.records %}
        <item>
          <title>{{ item.adx_name | xml_escape }}</title>
          <description>{{ item.adx_copy | escape }}</description>
          <link>{{ request.url | base | xml_escape }}{{ item.url | xml_escape }}</link>
          <guid>{{ item.id | xml_escape }}</guid>
          <pubDate>{{ item.createdon | date_to_rfc822 }}</pubDate>
        </item>
      {% endfor -%}
    {% endentityview %}
  </channel>
</rss>
```

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>Schritt 3: Erstellen einer Seitenvorlage zum Zuweisen einer RSS-Feed-Vorlage

Nun erstellen wir eine neue Seitenvorlage, mit der wir unsere RSS-Feed-Vorlage einer beliebigen Webseite auf unserer Website zuweisen können. Beachten Sie, dass wir die Auswahl der **Website Kopfzeile und-Fußzeile**deaktivieren, da wir das Rendering der gesamten Seiten Antwort für den Feed übernehmen möchten.

![Konfigurieren einer Seitenvorlage für einen RSS-Feed](../media/page-template-rss-feed.png "Konfigurieren einer Seitenvorlage für einen RSS-Feed")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>Schritt 4: Erstellen einer Webseite zum Hosten eines RSS-Feeds

Nun müssen Sie nur noch eine neue Webseite mit der RSS-Feed-Vorlage erstellen, um den Feed zu hosten. Wenn wir diese neue Webseite anfordern, erhalten wir unsere RSS-Feed-XML-Datei:

![Beispiel eines RSS-Feeds](../media/rss-feed-example.png "Beispiel eines RSS-Feeds")  

In diesem Beispiel haben wir gesehen, wie Sie Liquid-, Webvorlagen-, powerapps-Ansichten und Portale Content Management-Funktionen kombinieren können, um einen benutzerdefinierten RSS-Feed zu erstellen. Durch die Kombination dieser Features können Sie jeder Portal Anwendung leistungsstarke Anpassungsfunktionen hinzufügen.

### <a name="see-also"></a>Siehe auch

[Erstellen einer benutzerdefinierten Seitenvorlage mithilfe von Liquid und einer Vorlage für eine Webvorlagen Seite](create-custom-template.md)  
[Rendering der der aktuellen Seite zugeordneten Entitäts Liste](render-entity-list-current-page.md)  
[Rendering einer Website Kopfzeile und der primären Navigationsleiste](render-site-header-primary-navigation.md)  
[Rendering von bis zu drei Ebenen der Seiten Hierarchie mithilfe der Hybriden Navigation](hybrid-navigation-render-page-hierachy.md)  

