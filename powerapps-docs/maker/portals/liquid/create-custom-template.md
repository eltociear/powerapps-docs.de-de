---
title: Erstellen einer benutzerdefinierten Seitenvorlage mithilfe von Liquid und einer Vorlage für eine Webvorlagen Seite für ein Portal | MicrosoftDocs
description: Anweisungen zum Erstellen einer benutzerdefinierten Seitenvorlage mithilfe von Liquid-Operatoren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8fe2d6f6496c609a9811ddb4ca28c3df47d8e04d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542459"
---
# <a name="create-a-custom-page-template"></a>Erstellen einer benutzerdefinierten Seitenvorlage

In diesem Beispiel erstellen wir eine benutzerdefinierte Seitenvorlage mithilfe von Liquid und einer Seitenvorlage, die auf einer Webvorlage basiert. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Quell Inhalt mithilfe von Webvorlagen speichern](store-content-web-templates.md). Unser Ziel ist es, eine einfache zweispaltige Vorlage zu erstellen, die einen [Weblink](../configure/manage-web-links.md) als linksseitige Navigation mit dem Seiten Inhalt auf der rechten Seite verwendet. 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>Schritt 1: Erstellen einer Webvorlage und Schreiben des Liquid-Vorlagen Codes

Zuerst erstellen wir unsere Webvorlage und schreiben den Liquid-Vorlagen Code. Wir werden wahrscheinlich einige allgemeine Elemente dieser Vorlage in zukünftigen Vorlagen wieder verwenden. Daher erstellen wir eine gemeinsame Basisvorlage, die wir dann mit unserer spezifischen Vorlage erweitern. Unsere Basisvorlage stellt Breadcrumb-Links und den Seitentitel/-Header bereit und definiert das einspaltige Layout:

> [!div class=mx-imgBorder]
![Webvorlage ein Spalten Layout](../media/web-template-two-column-layout.png "Webvorlage ein Spalten Layout")

> [!TIP]
> Erfahren Sie mehr über die Vorlagen Vererbung mithilfe der Block-und Erweiterungs Tags: [Vorlagen Tags](template-tags.md#extends)

### <a name="two-column-layout-web-template"></a>Zweispaltige Layouts (Webvorlage)

```xml
<div class=container>
  <div class=page-heading>
    <ul class=breadcrumb>
      {% for crumb in page.breadcrumbs -%}
        <li>
          <a href={{ crumb.url }}>{{ crumb.title }}</a>
        </li>
      {% endfor -%}
      <li class=active>{{ page.title }}</li>
    </ul>
    <div class=page-header>
      <h1>{{ page.title }}</h1>
    </div>
  </div>
  <div class=row>
    <div class=col-sm-4 col-lg-3>
      {% block sidebar %}{% endblock %}
    </div>
    <div class=col-sm-8 col-lg-9>
      {% block content %}{% endblock %}
    </div>
  </div>
</div>
```

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>Schritt 2: Erstellen einer neuen Webvorlage, mit der unsere basislayoutvorlage erweitert wird

Verwenden Sie die Navigationslinks, die der aktuellen Seite zugeordnet sind, für unsere Navigationslinks, um eine neue Webvorlage zu erstellen, mit der unsere basislayoutvorlage erweitert wird.

> [!div class=mx-imgBorder]
![Web-Vorlagen Weblinks Links Navigations Layout](../media/web-template-weblinks-left-navigation-layout.png "Web-Vorlagen Weblinks Links Navigations Layout")  

> [!TIP]
> Machen Sie sich mit dem Laden von weblinksets mit dem [Weblinks](liquid-objects.md#weblinks) -Objekt vertraut.

### <a name="weblinks-left-navigation-web-template"></a>Links Navigation in Weblinks (Webvorlage)

```xml
{% extends 'Two Column Layout' %}

{% block sidebar %}
  {% assign weblinkset_id = page.adx_navigation.id %}
  {% if weblinkset_id %}
    {% assign nav = weblinks[page.adx_navigation.id] %}
    {% if nav %}
      <div class=list-group>
        {% for link in nav.weblinks %}
          <a class=list-group-item href={{ link.url }}>
            {{ link.name }}
          </a>
        {% endfor %}
      </div>
    {% endif %}
  {% endif %}
{% endblock %}

{% block content %}
  <div class=page-copy>
    {{ page.adx_copy }}
  </div>
{% endblock %}
```

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>Schritt 3: Erstellen einer neuen Seitenvorlage basierend auf der Webvorlage

In diesem Schritt erstellen wir eine neue Seitenvorlage, die auf der im vorherigen Schritt erstellten Webvorlage basiert.

> [!div class=mx-imgBorder]
![Seitenvorlage Weblinks Links Navigations Layout](../media/page-template-weblinks-left-navigation-layout.png "Seitenvorlage Weblinks Links Navigations Layout")  

## <a name="step-4-create-a-web-page-to-display-content"></a>Schritt 4: Erstellen einer Webseite zum Anzeigen von Inhalten

Nun müssen Sie nur noch eine Webseite erstellen, die unsere Seitenvorlage verwendet, und es ist ein verknüpften Weblink festgelegt, und wir haben unser Ergebnis.

> [!div class=mx-imgBorder]
![Webseite mit Links Navigation](../media/web-page-left-navigation.png "Webseite mit Links Navigation")  

### <a name="see-also"></a>Siehe auch

[Erstellen einer benutzerdefinierten Seitenvorlage zum Rendering eines RSS-Feeds](render-rss-custom-page-template.md)  
[Rendering der der aktuellen Seite zugeordneten Entitäts Liste](render-entity-list-current-page.md)  
[Rendering einer Website Kopfzeile und der primären Navigationsleiste](render-site-header-primary-navigation.md)  
[Rendering von bis zu drei Ebenen der Seiten Hierarchie mithilfe der Hybriden Navigation](hybrid-navigation-render-page-hierachy.md)  

