---
title: "Häufig gestellte Fragen (FAQs) zu API-Connectors | Microsoft-Dokumentation"
description: "Finden Sie Antworten zu Fragen über Anforderungen, Trigger und weitere Bereiche."
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
ms.openlocfilehash: b945f2775e26327557255a75f18e87a638a9fe66
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2018
---
# <a name="api-connector-faq-powerapps"></a>Häufig gestellte Fragen (FAQs) zu API-Connectors (PowerApps)
## <a name="requirements"></a>Anforderungen
**F:** Wenn ich kein ISV bin, kann ich trotzdem einen Connector erstellen?

**A:** Um einen Connector allgemein zu veröffentlichen, verlangen wir, dass Sie entweder den zugrundeliegenden Dienst besitzen oder explizite Rechte zur Nutzung der API nachweisen.

**F:** Kann ich einen Connector ohne REST-APIs erstellen?

**A:** Nein. Um einen API-Connector zu erstellen, müssen Sie stabile HTTP-REST-APIs für Ihren Dienst unterstützen.

**F:** Welche Authentifizierungstypen werden unterstützt?

**A:** Wir unterstützen die folgenden Authentifizierungsstandards:

* OAuth2.0 (einschließlich Azure Active Directory)
* API-Schlüssel
* Standardauthentifizierung

## <a name="triggers"></a>Trigger
**F:** Kann ich Trigger ohne Webhooks erstellen? 

**A:** API-Connectors für Microsoft Flow und Logic Apps gestatten nur die Erstellung von Webhook-basierten Triggern. Wenn bei Ihnen Bedarf an anderen Implementierungsformen besteht, wenden Sie sich mit weiteren Details über Ihre API an [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com).

## <a name="miscellaneous"></a>Sonstiges
**F:** Meine APIs verwenden einen dynamischen Host. Wie implementiere ich das in der OpenAPI?

**A:** Die API-Connectorfunktion unterstützt keine dynamischen Hosts. Verwenden Sie für Entwicklungs- und Testzwecke einen statischen Host. Wenden Sie sich im Rahmen der Einreichung wegen der dynamischen Implementierung an Ihren Microsoft-Kontakt.

**F:** Wird Postman Collection V2 unterstützt?

**A:** Nein, Postman V2 wird aktuell nicht unterstützt.

**F:** Wird OpenAPI 3.0 unterstützt?

**A:** Nein, OpenAPI 2.0 stellt aktuell die einzige unterstützte Version dar.

