---
title: Systemanforderungen, Einschränkungen und Konfigurationswerte für Canvas-Apps | Microsoft-Dokumentation
description: System Anforderungen, Einschränkungen und Konfigurationswerte für Canvas-apps, die in powerapps erstellt wurden
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/19/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7e434de24af417b5871c762d1aecd64cc41c5c72
ms.sourcegitcommit: 1b29cd1fa1492037ef04188dd857a911edeb4985
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80122761"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>Systemanforderungen, Einschränkungen und Konfigurationswerte für Canvas-Apps
Dieses Thema enthält die Anforderungen an Geräteplattform und Webbrowser sowie Grenzwerte und Konfigurationswerte für Canvas-apps.

## <a name="supported-platforms-for-running-canvas-apps-using-the-power-apps-mobile-app"></a>Unterstützte Plattformen für das Ausführen von Canvas-Apps mithilfe von powerapps Mobile App

| **Mindestens erforderlich** | **Empfohlen** |
| --- | --- |
| IOS 12 oder höher |IOS 12 oder höher|
| Android 7 oder höher |Android 7 oder höher |
| Windows 8.1 oder höher (nur PC) |Windows 10 Fall Creators Update mit mindestens 8 GB RAM|

> [!NOTE]
> Wir unterstützen derzeit keine neuen Features auf der Windows-Plattform für [Power Apps Mobile App](/powerapps/user/run-app-client). Features wie die verbesserte Common Data Service Option und der Gast Zugriff sind auf dieser Plattform nicht verfügbar. Wir empfehlen die Verwendung eines webplayers unter Windows, um den vollständigen Satz von Funktionen zu nutzen. In Zukunft werden Updates für die Power Apps-Mobile App für Windows-Plattform angekündigt.

## <a name="supported-browsers-for-running-canvas-apps"></a>Unterstützte Browser für das Ausführen von Canvas-Apps

| **Browser** | **Betriebssystem** |
| --- | --- |
| Google Chrome (aktuelle Version)<br>(empfohlen) |Windows 7 SP1, 8.1 und 10 <br>Android 5 oder höher <br>iOS 8 oder höher<br>macOS |
| Microsoft Edge (neueste Version)<br>(empfohlen) |Windows 10 |
| Microsoft Internet Explorer 11 (mit deaktivierter Kompatibilitätsansicht) |Windows 7 SP1, 8.1 und 10 |
| Mozilla Firefox (aktuelle Version) |Windows 7 SP1, 8.1 und 10 <br> Android 5 oder höher <br>iOS 8 oder höher <br>macOS |
| Apple Safari (aktuelle Version) |iOS 8 oder höher <br>macOS |

## <a name="supported-browsers-for-power-apps-studio"></a>Unterstützte Browser für Power apps Studio

| **Browser** | **Betriebssystem** |
| --- | --- |
| Google Chrome (aktuelle Version)<br>(empfohlen) |Windows 7 SP1, 8.1 und 10 <br>macOS |
| Microsoft Edge (neueste Version)<br>(empfohlen) |Windows 10 |
| Microsoft Internet Explorer 11 (mit deaktivierter Kompatibilitätsansicht) |Windows 7 SP1, 8.1 und 10 |

## <a name="request-limits"></a>Anforderungsgrenzwerte
Diese Begrenzungen gelten für jede einzelne ausgehende Anforderung:

| Name | Grenze |
| --- | --- |
| Timeout |180 Sekunden |
| Wiederholungsversuche |4 |

> [!NOTE]
> Der Wert für die Anzahl der Wiederholungsversuche kann variieren. Bei bestimmten Fehlerbedingungen ist ein wiederholter Versuch nicht erforderlich.

## <a name="ip-addresses"></a>IP-Adressen
Bei Anforderungen von Power apps werden IP-Adressen verwendet, die von der Region der [Umgebung](../../administrator/environments-overview.md) abhängen, in der sich die APP befindet. Für powerapps-Szenarios sind keine voll qualifizierten Domänen Namen veröffentlicht.

Aufrufe, die von einer API erfolgen, die durch eine App verbunden ist (z.B. die SQL-API oder die SharePoint-API), stammen von der IP-Adresse, die weiter unten in diesem Thema angegeben wird.

Sie sollten diese Adressen beispielsweise verwenden, wenn Sie eine Whitelist mit IP-Adressen für eine Azure SQL-Datenbank erstellen müssen.

> [!IMPORTANT]
>   Wenn Sie über vorhandene Konfigurationen verfügen, aktualisieren Sie Sie so bald wie möglich vor dem 30. September 2018, sodass Sie die IP-Adressen in dieser Liste für die Regionen enthalten, in denen Ihre powerapps-apps vorhanden sind.

| Region | Ausgehende IP-Adresse |
| --- | --- |
| Asien | 13.75.36.64-13.75.36.79, 13.67.8.240-13.67.8.255, 52.175.23.169, 52.187.68.19, 127.0.0.1 |
| Australien  | 13.70.72.192-13.70.72.207, 13.72.243.10, 13.77.50.240-13.77.50.255, 13.70.136.174, 127.0.0.1 |
| Brasilien | 191.233.203.192-191.233.203.207, 104.214.19.48-104.214.19.63, 13.65.86.57, 104.41.59.51, 127.0.0.1 |
| Kanada | 13.71.170.208-13.71.170.223, 13.71.170.224-13.71.170.239, 52.237.24.126, 40.69.106.240-40.69.106.255, 52.242.35.152, 127.0.0.1|
| Europa | 13.69.227.208-13.69.227.223, 52.178.150.68, 13.69.64.208-13.69.64.223, 52.174.88.118, 137.117.161.181, 127.0.0.1|
| Indien  | 104.211.81.192-104.211.81.207, 52.172.211.12, 40.78.194.240-40.78.194.255, 13.71.125.22, 104.211.146.224-104.211.146.239, 104.211.189.218, 127.0.0.1 |
| Japan | 13.78.108.0-13.78.108.15, 13.71.153.19, 40.74.100.224-40.74.100.239, 104.215.61.248, 127.0.0.1 |
| Südamerika | 191.233.203.192-191.233.203.207, 104.214.19.48-104.214.19.63, 13.65.86.57, 104.41.59.51, 127.0.0.1 |
| Großbritannien | 51.140.148.0-51.140.148.15, 51.140.80.51, 51.140.211.0-51.140.211.15, 51.141.47.105, 127.0.0.1 |
| USA | 13.89.171.80-13.89.171.95, 52.173.245.164, 40.71.11.80-40.71.11.95, 40.71.249.205, 40.70.146.208-40.70.146.223, 52.232.188.154, 52.162.107.160-52.162.107.175, 52.162.242.161, 40.112.243.160-40.112.243.175, 104.42.122.49, 127.0.0.1 |
| USA (Early Access)  | 13.71.195.32-13.71.195.47, 52.161.102.22, 13.66.140.128-13.66.140.143, 52.183.78.157, 127.0.0.1 |

## <a name="required-services"></a>Erforderliche Dienste
In dieser Liste werden alle Dienste identifiziert, mit denen Power apps Studio kommuniziert, sowie deren Verwendungen. Ihr Netzwerk darf diese Dienste **nicht** blockieren.

| Domäne(n) | Protokolle | Verwendung |
| --- | --- | --- |
| api.bap.microsoft.com<br/>api.businessappdiscovery.microsoft.com | https | Verwaltung von Umgebungs Berechtigungen|
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |Laufzeit der Connector/APIs |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph: zum erhalten von Benutzerinformationen (z. b. Profilfoto) |
| gallery.azure.com |https |Beispiel- und Vorlagen-Apps |
| \*. Azure-APIM.net |https |API-Hubs: Verschiedene Unterdomänen für jedes Gebietsschema |
| \*. powerapps.com |https | Create.powerapps.com, make.powerapps.com, Content.powerapps.com und Make.powerapps.com |
| \*. azureedge.net |https | Create.powerapps.com, make.powerapps.com, Content.powerapps.com und Make.powerapps.com |
| \*. BLOB.Core.Windows.net |https | Blobspeicher |
| \*. Flow.Microsoft.com | https | Create.powerapps.com, make.powerapps.com, Content.powerapps.com und Make.powerapps.com |
| \*. Dynamics.com | https | Common Data Service |
| vortex.data.microsoft.com |https |Telemetrie |
| Localhost | https | Powerapps Mobile|


> [!NOTE]
> Wenn Sie ein VPN verwenden, muss es so konfiguriert werden, dass localhost von Tunneln für Power Apps Mobile ausgeschlossen wird.

## <a name="size-limits"></a>Größen Limits

Informationen zu Größenbeschränkungen für Text, Hyperlinks, Bilder und Medien finden Sie unter [Datentypen](functions/data-types.md#text-hyperlink-image-and-media).

## <a name="power-apps-per-app-plan"></a>Powerapps pro App-Plan

Die Informationen sind jetzt im Abschnitt zu [powerapps pro App-Plan](/power-platform/admin/signup-for-powerapps-admin#power-apps-per-app-plan) im Administrator Handbuch für Power Platform verfügbar.
