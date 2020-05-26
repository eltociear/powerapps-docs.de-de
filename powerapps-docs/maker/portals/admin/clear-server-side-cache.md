---
title: Löschen des serverseitigen Caches für ein Portal | Microsoft-Dokumentation
description: Anleitungen zum Erzwingen, dass das Portal seinen Cache sofort aktualisiert.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/23/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 614ee17fdbf9a5104c51ff918df8bf8c66fccd98
ms.sourcegitcommit: 504bf052f7fe276484fa8c9b1ea04b19ad63484f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2020
ms.locfileid: "3288286"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>Löschen des serverseitigen Caches für ein Portal

Als Portaladministrator können Sie den serverseitigen Cache für das gesamte Portal löschen, damit aktualisierte Daten von Common Data Service direkt im Portal angezeigt werden. Aktualisierungen von Common Data Service werden dem Portal im asynchronen Modus übermittelt, so dass es zu einer Verzögerung zwischen der Zeit, zu der die Daten in Common Data Service aktualisiert werden, und der Zeit, zu der die aktualisierten Daten im Portal erscheinen, kommen kann. Um diese Verzögerung zu eliminieren, beispielsweise, wenn sie Probleme mit der Portalkonfiguration verursacht, können Sie erzwingen, dass das Portal seinen Cache unmittelbar aktualisiert.

> [!NOTE]
> Das SLA für Cacheaktualisierung (Datenübertragung zwischen Common Data Service und Portal) ist 15 Minuten.

## <a name="steps-to-clear-portal-server-side-cache"></a>Schritte zum Löschen des serverseitigen Portal-Caches

> [!IMPORTANT]
> Das Löschen des serverseitigen Portal-Caches führt zu einer vorübergehenden Leistungsverschlechterung des Portals, während Daten von Common Data Service neu geladen werden.

So löschen Sie den serverseitigen Cache:

1. Melden Sie sich als Administrator am Portal an.

1. Navigieren Sie wie folgt zu der URL: `<portal_path>/_services/about`.

1. Wählen Sie **Cache löschen** aus.

Der serverseitige Cache wird gelöscht, und Daten werden von Common Data Service neu geladen. 

![Löschen des Portalcaches](media/clear-server-side-cache/clear-portal-cache.png)

## <a name="configuration-entity-caching-portals-with-capacity-based-licenses"></a>Caching-Portale für Konfigurationseinheiten mit kapazitätsbasierten Lizenzen

[Kapazitätsbasiert](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#portals) Portale haben mehr Optionen auf `<portal_path>/_services/about`:

![Portal-Cache löschen mit kapazitätsbasierter Lizenz](media/clear-server-side-cache/clear-config-capacity-license.png)

Um mehr über die Unterschiede zwischen Power Apps-Portalen und Portal-Add-ons zu erfahren, lesen Sie [Power Apps-Portal-FAQ](../faq.md#what-is-the-difference-between-power-apps-portals-dynamics-365-portals-and-add-on-portals).

Portal-Metadaten werden in Entitäten mit der Bezeichnung *Konfigurationseinheiten* gespeichert. Wenn Sie Konfigurationseinheiten mit *Einheitliche Benutzeroberfläche - Anwendung* ändern, müssen Sie **muss** wählen **Konfiguration löschen**, um den Konfigurationscache zu leeren, damit die Änderungen in Ihrem Portal berücksichtigt werden können.  

### <a name="list-of-configuration-entities-refreshed-when-you-clear-config"></a>Liste der Konfigurationseinheiten, die beim Löschen der Konfiguration aktualisiert werden

Das Löschen des serverseitigen Konfigurations-Caches für ein Portal umfasst das Aktualisieren der Daten aus den folgenden *Konfigurationseinheiten*:

| Konfigurationseinheiten:| | |
|-------------------------------------------|---------------------------|--------------------------------------|
| adx_contentaccesslevel                    | adx_redirect              | adx_webpage_tag                      |
| adx_contentsnippet                        | adx_setting               | adx_webpageaccesscontrolrule         |
| adx_entityform                            | adx_shortcut              | adx_webpageaccesscontrolrule_webrole |
| adx_entityformmetadata                    | adx_sitemarker            | adx_webpagehistory                   |
| adx_entitylist                            | adx_sitesetting           | adx_webpagelog                       |
| adx_entitypermission_webrole              | adx_webfile               | adx_webrole_systemuser               |
| adx_externalidentity                      | adx_webfilelog            | adx_website                          |
| adx_pagealert                             | adx_webform               | adx_website_list                     |
| adx_pagenotification                      | adx_webformmetadata       | adx_website_sponsor                  |
| adx_pagetag                               | adx_webformsession        | adx_websiteaccess                    |
| adx_pagetag_webpage                       | adx_webformstep           | adx_websiteaccess_webrole            |
| adx_pagetemplate                          | adx_weblink               | adx_websitebinding                   |
| adx_portallanguage                        | adx_weblinkset            | adx_websitelanguage                  |
| adx_publishingstate                       | adx_webnotificationentity | adx_webtemplate                      |
| adx_publishingstatetransitionrule         | adx_webnotificationurl    | adx_urlhistory                       |
| adx_publishingstatetransitionrule_webrole | adx_webpage               | adx_entitypermission                 |
