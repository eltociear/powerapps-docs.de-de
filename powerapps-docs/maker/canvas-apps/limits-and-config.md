---
title: Systemanforderungen, Einschränkungen und Konfigurationswerte | Microsoft-Dokumentation
description: Systemanforderungen, Einschränkungen und Konfigurationswerte für PowerApps
services: ''
suite: PowerApps
documentationcenter: na
author: skjerland
manager: kfile
editor: ''
tags: ''
ms.service: PowerApps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/07/2018
ms.author: sharik
ms.openlocfilehash: 84115ea98ec5d7d0fd60d36fc0cd3cc9196980ff
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="system-requirements-limits-and-configuration-values"></a>Systemanforderungen, Einschränkungen und Konfigurationswerte
In diesem Artikel werden Anforderungen für Geräteplattformen und Webbrowser sowie Einschränkungen und Konfigurationswerte für PowerApps behandelt.

## <a name="supported-platforms-for-running-apps-using-the-powerapps-app"></a>Unterstützte Plattformen für das Ausführen von Apps mithilfe der PowerApps-App
| **Mindestens erforderlich** | **Empfohlen** |
| --- | --- |
| iOS 9.3 oder höher |iOS 10 oder höher mit mindestens 2 GB RAM |
| Android 5 oder höher |Android 7 oder höher mit mindestens 4 GB RAM |
| Windows 8.1 oder höher (nur PC) |Windows 10 Fall Creators Update mit mindestens 8 GB RAM|

## <a name="supported-browsers-for-running-apps"></a>Unterstützte Browser für das Ausführen von Apps
| **Browser** | **Betriebssystem** |
| --- | --- |
| Google Chrome (aktuelle Version)<br>(empfohlen) |Windows 7 SP1, 8.1 und 10 <br>Android 5 oder höher <br>iOS 8 oder höher<br>macOS |
| Microsoft Edge (neueste Version)<br>(empfohlen) |Windows 10 |
| Microsoft Internet Explorer 11 (mit deaktivierter Kompatibilitätsansicht) |Windows 7 SP1, 8.1 und 10 |
| Mozilla Firefox (aktuelle Version) |Windows 7 SP1, 8.1 und 10 <br> Android 5 oder höher <br>iOS 8 oder höher <br>macOS |
| Apple Safari (aktuelle Version) |iOS 8 oder höher <br>macOS |

## <a name="supported-browsers-for-powerapps-studio-for-web"></a>Unterstützte Browser für PowerApps Studio für Web
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

| Region | Ausgehende IP |
| --- | --- |
| Asien |52.163.91.227, 52.163.89.40, 52.163.89.65, 52.163.95.29, 13.75.89.9, 13.75.91.198, 13.75.92.202, 13.75.92.124 |
| Australien |13.77.7.172, 13.70.191.49, 13.70.189.7, 13.70.187.251, 13.70.82.210, 13.73.203.158, 13.73.207.42, 13.73.205.35 |
| Kanada |52.233.30.222, 52.233.30.148, 52.233.30.199, 52.233.29.254, 52.232.130.205, 52.229.126.118, 52.229.126.28, 52.229.123.56 |
| Europa |52.166.241.149, 52.166.244.232, 52.166.245.173, 52.166.243.169, 40.69.45.126, 40.69.45.11, 40.69.45.93, 40.69.42.254 |
| Indien |52.172.54.172, 52.172.55.107, 52.172.55.84, 52.172.51.70, 52.172.158.185, 52.172.159.100, 52.172.158.2, 52.172.155.245 |
| Japan |104.214.137.186, 104.214.139.29, 104.214.140.23, 104.214.138.174, 13.78.85.193, 13.78.84.73, 13.78.85.200, 13.78.86.229 |
| USA |104.43.232.28, 104.43.232.242, 104.43.235.249, 104.43.234.211, 52.160.93.247, 52.160.91.66, 52.160.92.131, 52.160.95.100, 40.117.101.91, 40.117.98.246, 40.117.101.120, 40.117.100.191 |
| USA (Frühzeitiger Zugriff) |52.161.26.191, 52.161.27.42, 52.161.29.40, 52.161.26.33, 13.66.213.240, 13.66.214.51, 13.66.210.166, 13.66.213.29 |

## <a name="required-services"></a>Erforderliche Dienste
In dieser Liste werden alle Dienste aufgeführt, mit denen PowerApps Studio kommuniziert; zudem wird ihr Verwendungszweck angegeben. Ihr Netzwerk darf diese Dienste **nicht** blockieren.

| Domäne(n) | Protokolle | Verwendung |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |Laufzeit der Connector/APIs |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph: Zum Abrufen von Benutzerinformationen (z.B. Profilfotos) |
| gallery.azure.com |https |Beispiel- und Vorlagen-Apps |
| *.azure-apim.net |https |API-Hubs: Verschiedene Unterdomänen für jedes Gebietsschema |
| *.powerapps.com |https |WebAuth + Portal |
| *.azureedge.net |https |WebAuth |
| *.blob.core.windows.net |https |Blob Storage |
| vortex.data.microsoft.com |https |Telemetrie |
