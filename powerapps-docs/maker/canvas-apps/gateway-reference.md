---
title: Lokales Daten Gateway | Microsoft-Dokumentation
description: Dieser Artikel stellt eine Übersicht über das lokale Daten Gateway für powerapps dar.
author: arthiriyer
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2019
ms.author: arthii
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 879fc0df86f05191941c6ff6b3b6403fe34fecea
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74676552"
---
# <a name="what-is-an-on-premises-data-gateway"></a>Was ist ein lokales Daten Gateway?

Das lokale Daten Gateway fungiert als Brücke, um eine schnelle und sichere Datenübertragung zwischen lokalen Daten (Daten, die nicht in der Cloud sind) und mehreren Microsoft Cloud Services bereitzustellen. Diese Clouddienste umfassen Power BI, powerapps, Energie Automatisierung, Azure Analysis Services und Azure Logic apps. Mithilfe eines Gateways können Organisationen Datenbanken und andere Datenquellen in Ihren lokalen Netzwerken aufbewahren und diese lokalen Daten sicher in Clouddiensten verwenden.

## <a name="how-the-gateway-works"></a>Funktionsweise des Gateways

![Übersicht über das Gateway](media/gateway-reference/on-premises-data-gateway.png)

Weitere Informationen zur Funktionsweise des Gateways finden Sie unter [Architektur des lokalen Daten Gateways](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="types-of-gateways"></a>Typen von Gateways

Es gibt zwei verschiedene Arten von Gateways, jeweils für ein anderes Szenario:

- Das **lokale Daten Gateway** ermöglicht mehreren Benutzern das Herstellen einer Verbindung mit mehreren lokalen Datenquellen. Sie können ein lokales Daten Gateway mit allen unterstützten Diensten mit einer einzelnen Gatewayinstallation verwenden. Dieses Gateway eignet sich gut für komplexe Szenarien, in denen mehrere Personen auf mehrere Datenquellen zugreifen.

- Das **lokale Daten Gateway (persönlicher Modus)** ermöglicht einem Benutzer das Herstellen einer Verbindung mit Quellen und kann nicht für andere Benutzer freigegeben werden. Ein lokales Daten Gateway (persönlicher Modus) kann nur mit Power BI verwendet werden. Dieses Gateway eignet sich gut für Szenarien, in denen Sie die einzige Person sind, die Berichte erstellt, und Sie müssen keine Datenquellen für andere Benutzer freigeben.

## <a name="use-a-gateway"></a>Verwenden eines Gateways

Es gibt vier Hauptschritte für die Verwendung eines Gateways.

1. [Laden Sie das Gateway herunter, und installieren Sie](/data-integration/gateway/service-gateway-install) es auf einem lokalen Computer.
2. [Konfigurieren](/data-integration/gateway/service-gateway-app) Sie das Gateway basierend auf Ihrer Firewall und anderen Netzwerk Anforderungen.
3. [Fügen Sie Gateway-Administratoren hinzu](/data-integration/gateway/service-gateway-manage) , die auch andere Netzwerk Anforderungen verwalten und verwalten können.
4. Behandeln von [Problemen](/data-integration/gateway/service-gateway-tshoot) mit dem Gateway bei Fehlern.

## <a name="next-steps"></a>Nächste Schritte

- [Installieren des lokalen Daten Gateways](/data-integration/gateway/service-gateway-install)