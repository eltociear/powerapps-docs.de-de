---
title: Einschränkung der Registrierung von Plugins für Retrieve- und RetrieveMultiple-Nachrichten | MicrosoftDocs
description: Das Hinzufügen von synchroner Plugin-Logik zu den Nachrichtenereignissen Retrieve und RetrieveMultiple kann zu Verzögerungen führen.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4bd25cf31e21278d94450eadb0a38e32a4ae1292
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861851"
---
# <a name="limit-the-registration-of-plug-ins-for-retrieve-and-retrievemultiple-messages"></a>Einschränkung der Registrierung von Plugins für Retrieve- und RetrieveMultiple-Nachrichten

**Kategorie**: Leistung

**Wirkungspotential**: Mittel

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Das Hinzufügen von synchroner Plugin-Logik zu den Nachrichtenereignissen Retrieve und RetrieveMultiple kann zu folgenden Ergebnissen führen:

- Nicht reaktionsfähige, modellgetriebene Anwendungen
- Langsame Kundeninteraktionen
- Der Browser reagiert nicht mehr.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Bewerten Sie das Design von Lösungen, die Plug-Ins enthalten, die für die Nachrichten Retrieve und RetrieveMultiple registriert sind.  Im Allgemeinen wird empfohlen, Plug-Ins für diese Nachrichten nicht zu registrieren, da die Gefahr besteht, dass die Anfragen zur Rückgabe eines oder mehrerer Entitätsdatensätze von verschiedenen Einstiegspunkten verzögert werden.  Es kann jedoch für das Design Ihrer Anwendung angemessen sein. Ein Beispiel für eine gemeinsame Anwendung wäre die Einspeisung zusätzlicher Filterkriterien in eine bestimmte bestehende Abfrage. Dies ermöglicht es einer Lösung, das zu kompensieren, was in der Benutzeroberfläche für Views nicht möglich ist.  Der Ansichtsdesigner kann nur eine gewisse Komplexität unterstützen, und dann müssen andere Optionen verwendet werden, um die Ergebnisse oder die Abfrage zu erweitern.

Wenn es sich um eine geeignete Lösung handelt, befolgen Sie diese Tipps, um die Auswirkungen auf die Umwelt zu minimieren:

- Fügen Sie Bedingungen in den Plugin-Code ein, um schnell zu prüfen, ob die gewünschte Logik ausgeführt werden muss. Wenn dies nicht der Fall ist, kehren Sie schnell zurück und unterlassen Sie es, unnötige zusätzliche Schritte auszuführen, die die Rückgabe der Daten an den Anrufer verzögern.

- Vermeiden Sie es, lang laufende Aufgaben einzubeziehen, insbesondere solche, die nicht deterministisch sein können, wie z.B. der Aufruf von externen Serviceanrufen oder komplexe Abfragen an Dynamics 365.

- Beschränken oder vermeiden Sie die Abfrage zusätzlicher Daten aus Common Data Service

### <a name="virtual-entities"></a>Virtuelle Entitäten

Am häufigsten wird Retrieve and RetrieveMultiple innerhalb von Plugins aufgerufen, um Daten aus externen Quellen abzurufen. Die Daten aus den externen Quellen werden in Power Apps gerendert oder zum Bearbeiten/Ändern vorhandener Daten verwendet. Dynamics 365 (online), Version 9.0 stellt eine Funktion namens [Virtual Entities](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve) vor, die die Integration von Daten, die sich in externen Systemen befinden, ermöglicht, indem sie diese Daten nahtlos als Entitäten in Power Apps, ohne Replikation von Daten und oft ohne benutzerdefinierte Codierung, wiedergibt. Weitere Informationen zu den Funktionen, Einschränkungen und der Konfiguration finden Sie in der Dokumentation zu [Virtual Entities](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve).

### <a name="retrieve-caution"></a>Vorsicht bei Retrieve

Common Data Service löst mindestens zwei Abruf-Nachrichten für jedes Laden von Entitätsformularen aus.  Ein Abruf enthält begrenzte Attribute, die je nach Entität variieren können, und nachfolgende Aufrufe enthalten mehr Attribute.  Wenn Sie erwarten, dass während des Ladens eines Formulars eine einzelne Aktion ausgeführt wird, dann verlassen Sie sich nicht strikt auf den Auslöser einer Retrieve-Nachricht.

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Die `Retrieve` und `RetrieveMultiple` Meldungen sind zwei der am häufigsten verarbeiteten Meldungen. Die Meldung `Retrieve` wird beim Öffnen eines Entitätsformulars oder beim Zugriff auf eine Entität mit der Operation `Retrieve` in einem der Service-Endpunkte ausgelöst. `RetrieveMultiple` wird durch verschiedene Aktionen in den Anwendungs- und Service-Endpunkten ausgelöst, z.B. beim Füllen eines Rasters in der Benutzeroberfläche.  Das Hinzufügen von synchroner Plugin-Logik zu diesen Nachrichtenereignissen kann zu Verzögerungen führen.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Leistungsoptimierungen für Microsoft Dynamics CRM Online](https://mbs.microsoft.com/customersource/northamerica/CRM/learning/documentation/user-guides/PerformanceOptimizationsCRMOnlineSuccess)<br />
[Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten](/powerapps/maker/common-data-service/create-edit-virtual-entities)<br />
