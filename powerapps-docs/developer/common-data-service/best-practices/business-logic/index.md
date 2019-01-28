---
title: 'Entwickler: Best Practices und Handlungsempfehlungen zur Entwicklung von Plug-Ins und Workflows für Common Data Service für Apps | Microsoft-Dokumentation'
description: Best Practices und Handlungsempfehlungen zur Entwicklung von Plug-Ins und Workflows für Entwickler von Common Data Service für Apps in PowerApps.
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
ms.openlocfilehash: 87e7337a4bf62a10647edfd9b6c17bce0a0903bf
ms.sourcegitcommit: 72c97378e96fb54e5d92ec087a59dd0fb1444f99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334015"
---
# <a name="best-practices-and-guidance-regarding-plug-in-and-workflow-development-for-the-common-data-service-for-apps"></a>Best Practices und Handlungsempfehlungen zur Entwicklung von Plug-Ins und Workflows für Common Data Service für Apps

In der folgenden Liste sind alle Best Practices und Handlungsempfehlungen zur Entwicklung von Plug-Ins und Workflows innerhalb von Common Data Service für Apps aufgeführt.

|Best Practice  |Beschreibung  |
|---------|---------|
|[Vermeiden von Batchanforderungstypen in Plug-Ins und Workflowaktivitäten](avoid-batch-requests-plugin.md)     |Verwenden Sie nicht die ExecuteMultipleRequest- oder ExecuteTransactionRequest-Meldungsanforderungsklassen im Kontext eines Plug-Ins oder einer Workflowaktivität.         |
|[Entwickeln von zustandslosen IPlugin-Implementierungen](develop-iplugin-implementations-stateless.md)     |Member von Klassen, die IPlugin implementieren, sind potenziellen Threadsicherheitsproblemen ausgesetzt, die zu Problemen mit der Datenkonsistenz oder Leistung führen können.         |
|[Kein Duplizieren der Plug-In-Schrittregistrierung](do-not-duplicate-plugin-step-registration.md)     |Eine Registrierung eines duplizierten Plug-in-Schritts bewirkt, dass das Plug-In bei der gleichen Meldung oder dem gleichen Ereignis mehrmals aktiv wird.         |
|[Einschließen von Filterattributen in die Plug-In-Registrierung](include-filtering-attributes-plugin-registration.md)     |Wenn Sie keine Filterattribute für einen Plug-in-Registrierungsschritt festlegen, wird das Plug-In jedes Mal ausgeführt, wenn eine Aktualisierungsmeldung für dieses Ereignis auftritt.         |
|[Beschränken der Registrierung von Plug-Ins für Retrieve- und RetrieveMultiple-Meldungen](limit-registration-plugins-retrieve-retrievemultiple.md)     |Wenn Sie den Retrieve- und RetrieveMultiple-Meldungsereignissen synchrone Plug-In-Logik hinzufügen, kann dies eine langsame Ausführung zur Folge haben.         |
|[Optimieren der Entwicklung benutzerdefinierter Assemblys](optimize-assembly-development.md)     |Zur Verbesserung der Leistung und Wartbarkeit empfiehlt es sich, unterschiedliche Plug-Ins oder benutzerdefinierte Workflowaktivitäten in einer einzelnen benutzerdefinierten Assembly zusammenzuführen. Wenn die Größe einer Assembly sich der maximalen Größe der Sandboxassembly annähert, sollten Sie Plug-Ins oder benutzerdefinierte Workflowaktivitäten in mehrere benutzerdefinierte Assemblys verschieben.         |
|[Festlegen von „KeepAlive“ auf FALSE bei der Interaktion mit externen Hosts in einem Plug-In](set-keepalive-false-interacting-external-hosts-plugin.md)     |Wenn für die „KeepAlive“-Eigenschaft der Wert TRUE im HTTP-Anforderungsheader festgelegt wird oder die Eigenschaft nicht expliziert auf FALSE festgelegt wird, kann dies dazu führen, dass sich die Ausführungszeit von Plug-Ins erhöht.         |
|[Verwenden von „InvalidPluginExecutionException“ in Plug-Ins und Workflowaktivitäten](use-invalidpluginexecutionexception-plugin-workflow-activities.md)     |Verwenden Sie „InvalidPluginExecutionException“ beim Auslösen von Fehlern im Kontext eines Plug-Ins oder einer Workflowaktivität.         |

# <a name="see-also"></a>Siehe auch
[Anwenden von Geschäftslogik mithilfe von Code](../../apply-business-logic-with-code.md)<br />
[Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen](../../plug-ins.md)<br />
[Workflowerweiterungen](../../workflow/workflow-extensions.md)<br />