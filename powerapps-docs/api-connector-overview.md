---
title: "API-Connectorübersicht | Microsoft-Dokumentation"
description: "ISVs und Besitzer von SaaS-Diensten können Connectors erstellen und sie von Microsoft zertifizieren lassen."
services: 
suite: powerapps
documentationcenter: na
author: asavaritayal
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/06/2017
ms.author: astay
ms.openlocfilehash: 74bac3b0f5bad2b95ab9b6b312fc5209bf5da3a2
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2018
---
# <a name="api-connector-overview-powerapps"></a>API-Connectorübersicht (PowerApps)
Ein **API-Connector** ist ein OpenAPI-basierter (Swagger) Wrapper um eine REST-API, die dem zugrundeliegenden Dienst die Kommunikation mit [Microsoft Flow](https://flow.microsoft.com), [PowerApps](https://powerapps.microsoft.com) und [Logic Apps](https://docs.microsoft.com/azure/logic-apps/) ermöglicht. Er bietet Benutzern eine Möglichkeit, Verbindungen mit ihren Konten herzustellen und zum Erstellen von Apps und Workflows einen Satz von vordefinierten **Triggern** und **Aktionen** zu nutzen.

Als **unabhängiger Softwarehersteller (ISV)** oder **SaaS-Diensteigentümer** können Sie Connectors erstellen, die eine Vielzahl von Geschäfts- und Produktionsszenarien für Ihre Benutzer unterstützen. Ein Connector hilft Ihnen, über einen definierten Satz von Integrationen hinaus zu gehen und die Reichweite, Erkennbarkeit und Nutzung Ihres Dienstes zu steigern.

## <a name="requirements"></a>Anforderungen
Damit Sie einen Connector erstellen und einreichen können, muss Ihr Dienst die folgenden Anforderungen erfüllen:

* Geschäftsbenutzerszenario, das sich gut in Microsoft Flow, PowerApps und Logic Apps einfügt
* Öffentlich zugänglicher Dienst mit stabilen REST-APIs

## <a name="build-your-connector"></a>Erstellen des Connectors
Der erste Schritt beim Erstellen eines API-Connectors besteht im Erstellen eines benutzerdefinierten Connectors mit vollem Funktionsumfang. Ein benutzerdefinierter Connector funktioniert genau so wie ein API-Connector, seine Verfügbarkeit ist jedoch auf den Autor und bestimmte Benutzer im Mandanten des Autors eingeschränkt.

Die Erstellung eines Connectors umfasst mehrere Schritte:

![Schritte der API-Connectorerstellung](./media/api-connectors-overview/authoring-steps.png)

[Weitere Informationen](api-connector-dev.md) zum Entwickeln eines API-Connectors.

## <a name="submit-for-certification"></a>Einreichen zur Zertifizierung
Nachdem Sie einen Connector erstellt haben, reichen Sie ihn zur Zertifizierung ein. Microsoft überprüft den Connector vor der Veröffentlichung im Rahmen seines Drittanbieter-Zertifizierungsprogramms.

In diesem Prozess wird die Funktion des Connectors in Microsoft Flow und PowerApps geprüft und seine technische und inhaltliche Kompatibilität überprüft.

[Weitere Informationen](api-connector-submission.md) über den Prozess zum Einreichen des Connectors zur Zertifizierung und Veröffentlichung.

## <a name="get-support"></a>Support erhalten
Wenden Sie sich für Support bei Onboarding und Entwicklung per E-Mail an [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com). Dieses Konto wird aktiv überwacht und verwaltet. Entwickleranfragen und Vorfälle finden schnell ihren Weg zum passenden Team.

