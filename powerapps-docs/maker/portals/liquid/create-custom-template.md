---
title: Erstellen einer benutzerdefinierten Seitenvorlage mithilfe von Liquid und einer Webseiten-Seitenvolage für ein Portal | MicrosoftDocs
description: Anweisungen, eine benutzerdefinierte Seitenvorlage mithilfe von flüssigen Operatoren zu erstellen.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757398"
---
# <a name="create-a-custom-page-template"></a>Eine benutzerdefinierte Seitenvorlage erstellen

In diesem Beispiel erstellen wir eine benutzerdefinierte Seitenvorlage mithilfe von Liquid und einer Seitenvorlage, die auf einer Webvorlage basiert. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Speichern Sie Quellinhalt mithilfe von Webvorlagen](store-content-web-templates.md). Unser Ziel ist es, eine einfache Vorlage mit zwei Spalten zu erstellen, die einen [Weblink](../configure/manage-web-links.md) verwenden, der auf der linken Seite angezeigt und auf die Seiteninhalte auf der rechten Seite verweist. 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>Schritt 1: Erstellen einer Webvorlage und Schreiben des Liquid-Vorlagencodes

Zunächst erstellen wir unsere Webvorlage und schreiben unseren Liquid-Vorlagencode. Wir können wohl einige allgemeine Elemente dieser Vorlage in zukünftigen Vorlagen wieder verwenden. Also erstellen wir eine allgemeine Grundvorlage, die wir dann mit unserer bestimmten Vorlage erweitern. Unser Grundvorlage liefert die Breadcrumb-Links und unsere Titel/Kopfseite und definiert auch unser einspaltiges Layout:

> [!div class=mx-imgBorder]
![Einspaltiges Layout der Webvorlage](../media/web-template-two-column-layout.png "Einspaltiges Layout der Webvorlage")

> [!TIP]
> Informieren Sie sich über Vorlagenvererbung mithilfe des Blocks und erweiterter Tags: [Vorlagentags](template-tags.md#extends)

### <a name="two-column-layout-web-template"></a>Zwei-Spalten-Layout (Webvorlage)

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

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>Schritt 2: Erstellen einer neuen Webvorlage, die die Basislayoutvorlage erweitert

Verwenden Sie die Navigations-Weblinks, die der aktuellen Seite für unsere Navigationslinks zugeordnet sind, um eine neue Webvorlage zu erstellen, die unsere Basis-Layoutvorlage erweitert.

> [!div class=mx-imgBorder]
![Webvorlagenlinks-Layout linke Navigation](../media/web-template-weblinks-left-navigation-layout.png "Webvorlagenlinks-Layout linke Navigation")  

> [!TIP]
> Machen Sie sich mit dem Laden von Web-Links mithilfe des Objekts [weblinks](liquid-objects.md#weblinks) vertraut.

### <a name="weblinks-left-navigation-web-template"></a>Weblinks linke Navigation (Webvorlage)

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

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>Schritt 3: Erstellen einer neue Seitenvorlage basierend auf der Webvorlage

In diesem Schritt erstellen wir eine neue Seitenvorlage, die auf einer Webvorlage basiert, die wir im vorherigen Schritt erstellt haben.

> [!div class=mx-imgBorder]
![Weblinks-Layout linke Navigation-Seitenvorlage](../media/page-template-weblinks-left-navigation-layout.png "Weblinks-Layout linke Navigation-Seitenvorlage")  

## <a name="step-4-create-a-web-page-to-display-content"></a>Schritt 4: Erstellen einer Webseite zum Anzeigen von Inhalt

Jetzt müssen wir nur noch eine Webvorlage erstellen, die unsere Seitenvorlage verwendet und eine dazugehörige Weblink-Gruppe hat und wir verfügen über das Ergebnis.

> [!div class=mx-imgBorder]
![Webseite mit linker Navigation](../media/web-page-left-navigation.png "Webseite mit linker Navigation")  

### <a name="see-also"></a>Siehe auch

[Erstellen einer benutzerdefinierte Seitenvorlage zum Rendern eines RSS-Feed](render-rss-custom-page-template.md)  
[Rendern der Entitätsliste, die der aktuellen Seite zugeordnet ist](render-entity-list-current-page.md)  
[Rendern einer Websitekopfzeile und primären Navigationsleiste](render-site-header-primary-navigation.md)  
[Rendern von bis zu drei Ebenen der Seitenhierarchie mithilfe der hybriden Navigation](hybrid-navigation-render-page-hierachy.md)  

