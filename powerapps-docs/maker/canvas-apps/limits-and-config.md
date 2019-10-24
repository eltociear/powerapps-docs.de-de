---
title: Systemanforderungen, Einschränkungen und Konfigurationswerte für Canvas-Apps | Microsoft-Dokumentation
description: Systemanforderungen, Einschränkungen und Konfigurationswerte für in PowerApps erstellte Canvas-Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0ce5218143a8283690cdaf7c1d9be2b1da3d629e
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72393142"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>Systemanforderungen, Einschränkungen und Konfigurationswerte für Canvas-Apps
In diesem Artikel werden Anforderungen für Geräteplattformen und Webbrowser sowie Einschränkungen und Konfigurationswerte für PowerApps behandelt.

## <a name="supported-platforms-for-running-canvas-apps-using-the-powerapps-app"></a>Unterstützte Plattformen für das Ausführen von Canvas-Apps mithilfe der PowerApps-App

| **Mindestens erforderlich** | **Empfohlen** |
| --- | --- |
| iOS 9.3 oder höher |iOS 10 oder höher mit mindestens 2 GB RAM |
| Android 5 oder höher |Android 7 oder höher mit mindestens 4 GB RAM |
| Windows 8.1 oder höher (nur PC) |Windows 10 Fall Creators Update mit mindestens 8 GB RAM|

> [!NOTE]
> Wir unterstützen derzeit keine neuen Features auf der Windows-Plattform für die powerapps-app. Features wie die verbesserte Common Data Service Option und der Gast Zugriff sind auf dieser Plattform nicht verfügbar. Wir empfehlen die Verwendung eines webplayers unter Windows, um den vollständigen Satz von Funktionen zu nutzen. In Zukunft werden Updates der powerapps-App für Windows-Plattform angekündigt.

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
| Brazilien | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| Kanada | 13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152|
| Europa | 13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 137.117.161.181|
| Indien  | 104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218 |
| Japan | 13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248 |
| Südamerika | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| Vereinigtes Königreich | 51.140.148.0 - 51.140.148.15, 51.140.80.51, 51.140.211.0 - 51.140.211.15, 51.141.47.105 |
| USA | 13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49 |
| USA (Frühzeitiger Zugriff)  | 13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157 |

## <a name="required-services"></a>Erforderliche Dienste
In dieser Liste werden alle Dienste aufgeführt, mit denen PowerApps Studio kommuniziert; zudem wird ihr Verwendungszweck angegeben. Ihr Netzwerk darf diese Dienste **nicht** blockieren.

| Domäne(n) | Protokolle | Verwendung |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |Laufzeit der Connector/APIs |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph: zum erhalten von Benutzerinformationen (z. b. Profilfoto) |
| gallery.azure.com |https |Beispiel- und Vorlagen-Apps |
| \*. Azure-APIM.net |https |API-Hubs: Verschiedene Unterdomänen für jedes Gebietsschema |
| \*. powerapps.com |https | Create.powerapps.com, make.powerapps.com, Content.powerapps.com und Web.powerapps.com |
| \*. azureedge.net |https | Create.powerapps.com, make.powerapps.com, Content.powerapps.com und Web.powerapps.com |
| \*. BLOB.Core.Windows.net |https | Blob Storage |
| \*. Flow.Microsoft.com | https | Create.powerapps.com, make.powerapps.com, Content.powerapps.com und Web.powerapps.com |
| vortex.data.microsoft.com |https |Telemetrie |
| localhost | https | PowerApps Mobile

> [!NOTE]
> Wenn Sie ein VPN verwenden, muss dieses so konfiguriert sein, dass „localhost“ vom Tunneling für PowerApps Mobile ausgeschlossen wird.

## <a name="size-limits"></a>Größen Limits

Informationen zu Größenbeschränkungen für Text, Hyperlinks, Bilder und Medien finden Sie unter [Datentypen](functions/data-types.md#text-hyperlink-image-and-media).

## <a name="powerapps-per-app-plan"></a>Powerapps pro App-Plan

Mit powerapps pro App-Plan können einzelne Benutzer 2 Anwendungen in einem einzelnen Portal für ein bestimmtes Geschäftsszenario ausführen, das auf den vollständigen Funktionen von powerapps basiert. Dieser Plan bietet Benutzern eine einfache Möglichkeit, mit der Plattform zu beginnen, bevor Sie eine breitere Akzeptanz erzielen.

Nachdem ein Administrator einer Umgebung powerapps pro App-Plan zugewiesen hat, werden Sie standardmäßig Benutzern zugewiesen, wenn die APP für Sie freigegeben wird.

Führen Sie die folgenden Schritte aus, um die Zuweisung von App-Plänen für Benutzer zu deaktivieren, wenn eine APP für Sie freigegeben wird:

- Wählen Sie die **App**aus.
- Wählen Sie **Einstellungen**aus.
- Ändern Sie die UMSCHALT Fläche **automatische Zuweisung pro App** wird unter **Pass Zuweisung**geändert.

Die UMSCHALT Fläche **automatisch zuweisen pro App** wird in der app-Einstellung angezeigt.

> [!NOTE]
> Die Deaktivierung des pro-App-Plans ist zurzeit nur für Canvas-apps verfügbar.  Modell gesteuerte apps und Portale können diese Möglichkeit in Zukunft haben.

### <a name="app-settings"></a>App-Einstellungen

![Canvas-App-Einstellungen](./media/limits-and-config/app_settings.png "Canvas-App-Einstellungen")

### <a name="pass-assignment"></a>Pass Zuweisung

![Pass Zuweisung der Canvas-App-Einstellungen](./media/limits-and-config/app_settings_pass_assignment.png "Pass Zuweisung der Canvas-App-Einstellungen")
