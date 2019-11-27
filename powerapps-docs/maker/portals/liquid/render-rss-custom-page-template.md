---
title: Darstellen eines RSS-Feeds mit einer benutzerdefinierten Seitenvorlage für ein Portal | MicrosoftDocs
description: Anweisungen, eine benutzerdefinierte Seitenvorlage zu erstellen und anschließend zu verwenden, um einen RSS-Feed zu rendern.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757178"
---
# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>Erstellen einer benutzerdefinierte Seitenvorlage zum Rendern eines RSS-Feed
In diesem Beispiel erstellen wir eine benutzerdefinierte Seitenvorlage, um einen [RSS-Feed](https://en.wikipedia.org/wiki/RSS) neuer Artikel mithilfe von Liquid und einer Webvorlage-Seitenvorlage zu rendern. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Quellinhalt mithilfe von Webvorlagen speichern](store-content-web-templates.md)  

## <a name="step-1-create-a-new-powerapps-view"></a>Schritt 1: Erstellen einer neuen PowerApps-Ansicht

Zunächst erstellen wir eine neue PowerApps-Ansicht die wir verwenden, um die Daten für unseren Feed zu laden. In diesem Beispiel erstellen wir eine Ansicht auf Webseiten und verwenden diese Entität, um unsere Artikel zu speichern. Es können diese Ansicht verwenden, um den Filter und der Sortierung der Ergebnisse zu konfigurieren als Spalten und schließen welche Entitätsattribute ein, die wir in unserer Vorlage zur flüssigen soll.

![Bearbeiten einer Seitenvorlage](../media/edit-page-template.png "Bearbeiten einer Seitenvorlage")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>Schritt 2: Erstellen einer Webvorlage für einen RSS-Feed

In diesem Schritt erstellen wir eine Webvorlage für unseren RSS-Feed. Diese Vorlage wird auf eine bestimmte Webseite in unserer Website angewendet, somit verwenden wir den Titel und die Zusammenfassung dieser Seite als Titel und Beschreibung des Feeds. Wir verwenden den Tag „entityview”, um unsere neu erstellte Ansicht „Neue Artikell” zu laden. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [PowerApps common data service Entitäts-Tags](portals-entity-tags.md). Beachten Sie, dass wir auch das Feld **MIME-Typ** der Webvorlage auf „application/rss+xml” festgelegt haben. Dadurch wird angegeben, welche Leistungen dem Warteinhaltstyp sein könnte, wenn wir unsere Vorlage gerendert wird.  

![Eine Webvorlage für einen RSS-Feed konfigurieren](../media/web-template-rss-feed.png "Eine Webvorlage für einen RSS-Feed konfigurieren")  

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

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>Schritt 3: Erstellen einer Seitenvorlage für die Zuweisung einer RSS-Feedvorlage

Erstellen wir nun eine neue Seitenvorlage, die es uns gestattet, unsere RSS-Feed-Vorlage jeder beliebigen Webseite in unserer Website zuzuweisen. Beachten Sie, dass wird **Kopf- und Fußzeile der Website verwenden** deaktiviert haben. Wir möchten das Rendern der gesamten Seiten für unseren Feed übernehmen.

![Eine Seitenvorlage für einen RSS-Feed konfigurieren](../media/page-template-rss-feed.png "Eine Seitenvorlage für einen RSS-Feed konfigurieren")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>Schritt 4: Erstellen einer Webseite zum Hosten eines RSS-Feeds

Jetzt bleibt nur noch, eine neue Webseite mit der RSS-Feed-Vorlage zu erstellen, um unseren Feed zu hosten. Wenn wir diese neue Webseite anfordern, erhalten wir unseren RSS-Feed XML:

![Beispiel eines RSS-Feed](../media/rss-feed-example.png "Beispiel eines RSS-Feed")  

In diesem Beispiel gesehen haben wir, wie wir Flüssigkeit, Internet-Vorlagen, PowerApps-Ansichten Funktionen zur Inhaltsverwaltung in Portalen kombinieren können, um einen angepassten RSS-Feed zu erstellen. Die Kombination dieser Funktionen wird jeder Portal-Anwendung leistungsstarke Anpassungsmöglichkeiten hinzu.

### <a name="see-also"></a>Siehe auch

[Erstellen einer benutzerdefinierten Seitenvorlage mithilfe von Liquid und einer Webseiten-Seitenvorlage](create-custom-template.md)  
[Rendern der Entitätsliste, die der aktuellen Seite zugeordnet ist](render-entity-list-current-page.md)  
[Rendern einer Websitekopfzeile und primären Navigationsleiste](render-site-header-primary-navigation.md)  
[Rendern von bis zu drei Ebenen der Seitenhierarchie mithilfe der hybriden Navigation](hybrid-navigation-render-page-hierachy.md)  

