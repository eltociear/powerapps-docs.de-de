---
title: Systemanforderungen, Einschränkungen und Konfigurationswerte für Canvas-Apps | Microsoft-Dokumentation
description: Systemanforderungen, Einschränkungen und Konfigurationswerte für in PowerApps erstellte Canvas-Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/30/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1c8591790fe14d184f5d5e4ef5fc79ff0bfe0e2a
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177897"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>Systemanforderungen, Einschränkungen und Konfigurationswerte für Canvas-Apps
In diesem Artikel werden Anforderungen für Geräteplattformen und Webbrowser sowie Einschränkungen und Konfigurationswerte für PowerApps behandelt.

## <a name="supported-platforms-for-running-canvas-apps-using-the-powerapps-app"></a>Unterstützte Plattformen für das Ausführen von Canvas-Apps mithilfe der PowerApps-App

| **Mindestens erforderlich** | **Empfohlen** |
| --- | --- |
| iOS 12 or later |iOS 12 or later|
| Android 7 or later |Android 7 or later |
| Windows 8.1 oder höher (nur PC) |Windows 10 Fall Creators Update mit mindestens 8 GB RAM|

> [!NOTE]
> We currently don't support new features on Windows platform for PowerApps app. Features such as the Improved Common Data Service option and guest access are not available on this platform. We recommend using a web player on Windows to leverage the full set of capabilities. Updates to the PowerApps app for Windows platform will be announced in future.

## <a name="supported-browsers-for-running-canvas-apps"></a>Unterstützte Browser für das Ausführen von Canvas-Apps

| **Browser** | **Betriebssystem** |
| --- | --- |
| Google Chrome (aktuelle Version)<br>(empfohlen) |Windows 7 SP1, 8.1 und 10 <br>Android 5 oder höher <br>iOS 8 oder höher<br>macOS |
| Microsoft Edge (neueste Version)<br>(empfohlen) |Windows 10 |
| Microsoft Internet Explorer 11 (mit deaktivierter Kompatibilitätsansicht) |Windows 7 SP1, 8.1 und 10 |
| Mozilla Firefox (aktuelle Version) |Windows 7 SP1, 8.1 und 10 <br> Android 5 oder höher <br>iOS 8 oder höher <br>macOS |
| Apple Safari (aktuelle Version) |iOS 8 oder höher <br>macOS |

## <a name="supported-browsers-for-powerapps-studio"></a>Unterstützte Browser für PowerApps Studio

| **Browser** | **Betriebssystem** |
| --- | --- |
| Google Chrome (aktuelle Version)<br>(empfohlen) |Windows 7 SP1, 8.1 und 10 <br>macOS |
| Microsoft Edge (neueste Version)<br>(empfohlen) |Windows 10 |
| Microsoft Internet Explorer 11 (mit deaktivierter Kompatibilitätsansicht) |Windows 7 SP1, 8.1 und 10 |

## <a name="request-limits"></a>Anforderungsbegrenzungen
Diese Begrenzungen gelten für jede einzelne ausgehende Anforderung:

| Name | Maximale Anzahl |
| --- | --- |
| Timeout |180 Sekunden |
| Wiederholungsversuche |4 |

> [!NOTE]
> Der Wert für die Anzahl der Wiederholungsversuche kann variieren. Bei bestimmten Fehlerbedingungen ist ein wiederholter Versuch nicht erforderlich.

## <a name="ip-addresses"></a>IP-Adressen
Anforderungen von PowerApps verwenden IP-Adressen, die vom Bereich der [Umgebung](../../administrator/environments-overview.md) abhängig sind, in der sich die App befindet. Es werden keine für PowerApps-Szenarios verfügbaren vollqualifizierten Domänennamen veröffentlicht.

Aufrufe, die von einer API erfolgen, die durch eine App verbunden ist (z.B. die SQL-API oder die SharePoint-API), stammen von der IP-Adresse, die weiter unten in diesem Thema angegeben wird.

Sie sollten diese Adressen beispielsweise verwenden, wenn Sie eine Whitelist mit IP-Adressen für eine Azure SQL-Datenbank erstellen müssen.

> [!IMPORTANT]
>   Wenn Sie bereits über Konfigurationen verfügen, aktualisieren Sie diese so schnell wie möglich (vor dem 30. September 2018), sodass diese die in der folgenden Liste aufgeführten IP-Adressen für die Regionen umfassen, in denen Ihre PowerApps-Apps vorhanden sind, und diesen entsprechen.

| Region | Ausgehende IP |
| --- | --- |
| Asien | 13.75.36.64 - 13.75.36.79, 13.67.8.240 - 13.67.8.255, 52.175.23.169, 52.187.68.19 |
| Australien  | 13.70.72.192 - 13.70.72.207, 13.72.243.10, 13.77.50.240 - 13.77.50.255, 13.70.136.174 |
| Brazil | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| Kanada | 13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152|
| Europa | 13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 137.117.161.181|
| Indien  | 104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218 |
| Japan | 13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248 |
| Südamerika | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| United Kingdom | 51.140.148.0 - 51.140.148.15, 51.140.80.51, 51.140.211.0 - 51.140.211.15, 51.141.47.105 |
| USA | 13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49 |
| USA (Frühzeitiger Zugriff)  | 13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157 |

## <a name="required-services"></a>Erforderliche Dienste
In dieser Liste werden alle Dienste aufgeführt, mit denen PowerApps Studio kommuniziert; zudem wird ihr Verwendungszweck angegeben. Ihr Netzwerk darf diese Dienste **nicht** blockieren.

| Domäne(n) | Protokolle | Verwendung |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |Laufzeit der Connector/APIs |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph - For getting user info (e.g., profile photo) |
| gallery.azure.com |https |Beispiel- und Vorlagen-Apps |
| \*.azure-apim.net |https |API-Hubs: Verschiedene Unterdomänen für jedes Gebietsschema |
| \*.powerapps.com |https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| \*.azureedge.net |https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| \*.blob.core.windows.net |https | Blob Storage |
| \*.flow.microsoft.com | https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| *.dynamics.com | https | Common Data Service |
| vortex.data.microsoft.com |https |Telemetrie |
| localhost | https | PowerApps Mobile

> [!NOTE]
> Wenn Sie ein VPN verwenden, muss dieses so konfiguriert sein, dass „localhost“ vom Tunneling für PowerApps Mobile ausgeschlossen wird.

## <a name="size-limits"></a>Size limits

You can find information about size limits on text, hyperlinks, images, and media in [Data types](functions/data-types.md#text-hyperlink-image-and-media).

## <a name="powerapps-per-app-plan"></a>PowerApps per app plan

PowerApps per app plan allows individual users to run 2 applications on a single portal for a specific business scenario based on the full capabilities of PowerApps. This plan provides an easy way for users to get started with the platform before broader scale adoption.

After an admin allocates PowerApps per app plan to an environment, they're assigned to unlicensed users when an app in that environment is shared with them. You can see how an admin allocates per app plans [here](https://docs.microsoft.com/power-platform/admin/capacity-add-on).

Follow these steps to turn off the assigning per app plans for users when an app is shared with them:

- Choose the **App**.
- Select **Settings**.
- Change the **Auto assign per app passes** toggle under **Pass assignment**.

The **Auto assign per app passes** toggle appears in all app setting.

> [!NOTE]
> Disabling the per app plan is currently available for only canvas apps.  Model-driven apps and Portals will have this ability in the future.
>
> The ability to control per app plan assignment for an app is only available for apps that are in an environment that had Per app plans allocated in the [Power Platform Admin center](https://admin.powerplatform.microsoft.com).  

### <a name="app-settings"></a>App Settings

![Canvas app settings](./media/limits-and-config/app_settings.png "Canvas app settings")

### <a name="pass-assignment"></a>Pass assignment

![Canvas app settings pass assignment](./media/limits-and-config/app_settings_pass_assignment.png "Canvas app settings pass assignment")
