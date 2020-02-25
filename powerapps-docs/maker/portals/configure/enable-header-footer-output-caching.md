---
title: Aktivieren des Zwischenspeicherns von Kopf- undFußzeilenausgaben in einem Portal | MicrosoftDocs
description: Anweisungen zum Aktivieren des Zwischenspeicherns von Kopfzeilen- und Fußzeilenausgaben in einem Portal für vorhandene Benutzer.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e7a112c722e284f9060696d0fac5a3389b47b0d3
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977091"
---
# <a name="enable-header-and-footer-output-caching-on-a-portal"></a>Aktivieren des Zwischenspeicherns von Kopfzeilen- undFußzeilenausgaben in einem Portal

Um das Verarbeiten der Leistung von Kopf- und Fußzeilenwebvorlagen in einem Portal zu verbessern, aktivieren Sie das Zwischenspeichern von Kopf- und Fußzeilenausgaben. Kopf- und Fußzeilenwebvorlagen werden jedes Mal, wenn eine Seite geladen wird, analysiert und gerendert. Das Zwischenspeichern von Kopf- und Fußzeilenausgaben reduziert die Seitenverarbeitungszeit deutlich.

Für einen neuen Benutzer ist Ausgabecaching standardmäßig aktiviert. Die folgenden Websiteeinstellungen sind standardmäßig verfügbar und auf true festgelegt, um diese Funktionalität zu unterstützen:
- Header/OutputCache/Enabled: Legen Sie den Wert auf true fest, um das Zwischenspeichern von Kopfzeilenausgaben zu aktivieren.
- Footer/OutputCache/Enabled: Legen Sie den Wert auf true fest, um das Zwischenspeichern von Fußzeilenausgaben zu aktivieren.

ür Benutzer, der auf eine neuere Portalversion aktualisiert hat, ist das Zwischenspeichern von Ausgaben standardmäßig deaktiviert – die Kopf- und Fußzeilenwebvorlagen werden jedes Mal, wenn eine Seite geladen wird, analysiert und gerendert. Um das Zwischenspeichern von Ausgaben zu aktivieren, müssen Sie die Webvorlagen für Kopfzeile, Fußzeile und Sprach-Dropdownmenü aktualisieren und die erforderlichen Websiteeinstellungen erstellen.

> [!Note]
> Wenn Sie das Zwischenspeichern von Ausgaben nur durch Erstellen von Websiteeinstellungen aktivieren, werden Kopf- und Fußzeilen nicht korrekt gerendert und es werden Fehlermeldungen angezeigt.

### <a name="enable-header-and-footer-output-caching-for-an-existing-user"></a>Aktivieren des Zwischenspeicherns von Kopf- und Fußzeilenausgaben für vorhandene Benutzer

**Schritt 1: Aktualisieren der Kopfzeilenwebvorlage**

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).
2. Gehen Sie zu **Portale** > **Webvorlagen**.
3. Öffnen Sie die Kopfzeilenwebvorlage.
4. Führen Sie im Feld **Quelle** Folgendes aus:
    - Suchen Sie den folgenden Code und aktualisieren Sie ihn:
    
        **Vorhandener Code**

        ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/Account/Login/LogOff?returnUrl={{ request.raw_url_encode | escape }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/SignIn?returnUrl={{ request.raw_url_encode }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
        
        **Aktualisierter Code**

         ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_out_url_substitution }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_in_url_substitution }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
    - Suchen Sie den folgenden Code und aktualisieren Sie ihn:

        **Vorhandener Code**
        ```
        {% assign current_page = page.adx_partialurl %}
        {% assign sr_page = sitemarkers[Search].url | remove: '/' %}
        {% assign forum_page = sitemarkers[Forums].url | remove: '/' %}
        {% if current_page == sr_page or current_page == forum_page %}
          <section class=page_section section-landing-{{ current_page }} color-inverse>
            <div class=container>
              <div class=row >
                <div class=col-md-12 text-center>
                  {% if current_page == sr_page %}
                    <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                    {% include 'Search' %}
                  {% endif %}
                </div>
              </div>
            </div>
          </section>
        {% endif %}
        ```

        **Aktualisierter Code**

        ```
        {% substitution %}
          {% assign current_page = page.id %}
          {% assign sr_page = sitemarkers[Search].id %}
          {% assign forum_page = sitemarkers[Forums].id %}
          {% if current_page == sr_page or current_page == forum_page %}
            {% assign section_class = section-landing-search %}
            {% if current_page == forum_page %}
              {% assign section_class = section-landing-forums %}
            {% endif %}
           <section class=page_section section-landing-{{ current_page }} {{ section_class | h }} color-inverse>
              <div class=container>
                <div class=row >
                  <div class=col-md-12 text-center>
                    {% if current_page == sr_page %}
                      <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                      {% include 'Search' %}
                    {% endif %}
                  </div>
                </div>
              </div>
            </section>
          {% endif %}
        {% endsubstitution %}
        ```

5. Speichern Sie die Webvorlage.

**Schritt 2: Aktualisieren der Fußzeilenwebvorlage**

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).
2. Gehen Sie zu **Portale** > **Webvorlagen**.
3. Öffnen Sie die Fußzeilenwebvorlage.
4. Suchen Sie im Feld **Quelle** den folgenden Code und aktualisieren Sie ihn:
    
    **Vorhandener Code**
    
    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %} hidden-print>
    ```

    **Aktualisierter Code**

    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% substitution %}{% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %}{% endsubstitution %} hidden-print>
    ```

5. Speichern Sie die Webvorlage.

**Schritt 3: Aktualisieren der Webvorlage für das Sprach-Dropdownmenü**

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).
2. Gehen Sie zu **Portale** > **Webvorlagen**.
3. Öffnen Sie die Webvorlage für das Sprach-Dropdownmenü.
4. Suchen Sie im Feld **Quelle** den folgenden Code und aktualisieren Sie ihn:
    
    **Vorhandener Code**

    ```
    <a href=/{{ language.url }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

    **Aktualisierter Code**

    ```
    <a href=/{{ language.url_substitution }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

5. Speichern Sie die Webvorlage.

**Schritt 4: Erstellen von Websiteeinstellungen**

Erstellen Sie die folgenden Websiteeinstellungen:

|Name|Wert|
|----|-----|
|Header/OutputCache/Enabled|Wahr|
|Footer/OutputCache/Enabled|Wahr|
|||
