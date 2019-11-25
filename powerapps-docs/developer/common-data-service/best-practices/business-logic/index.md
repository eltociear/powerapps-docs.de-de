---
title: 'Entwickler: Bewährte Methoden und Anleitungen zur Plug-In- und Workflow-Entwicklung für den Common Data Service | Microsoft Docs'
description: Best Practices und Anleitungen zur Plug-in- und Workflow-Entwicklung für Entwickler der Common Data Service in PowerApps.
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
ms.date: 9/23/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a3915f554ef650df33f53921c4fba8135ea1baf5
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748247"
---
# <a name="best-practices-and-guidance-regarding-plug-in-and-workflow-development-for-the-common-data-service"></a>Bewährte Methoden und Anleitungen zur Plug-In- und Workflow-Entwicklung für den Common Data Service

Diese Liste enthält alle Anleitungen und bewährte Methoden für die Plug-In- und Workflow-Entwicklung innerhalb des Common Data Service.

|Bewährte Methode  |Beschreibung  |
|---------|---------|
|[Vermeiden Sie die Verwendung von Batch-Requesttypen in Plugins und Workflow-Aktivitäten.](avoid-batch-requests-plugin.md)     |Sie sollten die Nachrichtenanforderungsklassen ExecuteMultipleRequest oder ExecuteTransactionRequest nicht im Rahmen einer Plug-in- oder Workflow-Aktivität verwenden.         |
|[Entwicklung von IPlugin-Implementierungen als zustandslose Systeme](develop-iplugin-implementations-stateless.md)     |Mitglieder von Klassen, die IPlugin implementieren, sind potenziellen Thread-Sicherheitsproblemen ausgesetzt, die zu Dateninkonsistenz- oder Performanceproblemen führen können.         |
|[Keine Registrierung von Plug-in-Schritten duplizieren](do-not-duplicate-plugin-step-registration.md)     |Die Registrierung eines doppelten Plug-in-Schrittes bewirkt, dass das Plug-in bei derselben Nachricht/Ereignis mehrmals ausgelöst wird.         |
|[Verwenden Sie keine parallele Ausführung in Plug-Ins und Workflow-Aktivitäten](do-not-use-parallel-execution-in-plug-ins.md)|Multithreading oder paralleles Threading in Plug-Ins oder benutzerdefinierten Workflowaktivitäten wird nicht unterstützt.|
|[Implementieren Sie alle Arten von Abfragen bei der Filterung von Ergebnissen mit PreOperation RetrieveMultiple](implement-all-types-of-queries-when-filtering-preoperation-retrievemultiple.md)|Für beste Leistung und konsistente Ergebnisse für alle Anwendungen müssen Sie die Filterung für alle Arten von Abfragen implementieren, die mit Plugins verwendet werden können, die für die Phase PreOperation von RetrieveMultiple registriert sind.|
|[Einbeziehen von Filterattributen mit Plugin-Registrierung](include-filtering-attributes-plugin-registration.md)     |Wenn für einen Registrierungsschritt des Plugins keine Filterattribute festgelegt sind, wird das Plug-in jedes Mal ausgeführt, wenn eine Update-Meldung für dieses Ereignis auftritt.         |
|[Einschränkung der Registrierung von Plugins für Retrieve- und RetrieveMultiple-Nachrichten](limit-registration-plugins-retrieve-retrievemultiple.md)     |Das Hinzufügen von synchroner Plugin-Logik zu den Nachrichtenereignissen Retrieve und RetrieveMultiple kann zu Verzögerungen führen.         |
|[Optimierung der Entwicklung kundenspezifischer Assemblies](optimize-assembly-development.md)     |Erwägen Sie, separate Plug-Ins/Anpassungen von Arbeitsabläufen in einer einzigen benutzerdefinierten Assembly zusammenzuführen, um die Leistung und Wartbarkeit zu verbessern, und verschieben Sie Plug-Ins/Anpassungen von Arbeitsabläufen in mehrere benutzerdefinierte Assemblies, wenn sich eine Assembly-Größe in der Nähe der Größenbeschränkungen von SandboxAssemblies befindet.         |
|[Entfernen von nicht unterstütztem Code, der Reflektion in benutzerdefinierten Workflowaktivitäten verwendet](remove-unsupported-code-using-reflection-workflow-activities.md)|Bei Workflowaktivitäten, die nicht unterstützten Code enthalten, der Reflektion verwendet, wird es in den kommenden Monaten zu Problemen kommen, sofern dieser nicht entfernt wurde.|
|[KeepAlive auf falsch setzen, wenn Sie mit externen Hosts in einem Plug-in interagieren](set-keepalive-false-interacting-external-hosts-plugin.md)     |Die KeepAlive-Eigenschaft, die im HTTP-Request-Header auf true gesetzt oder nicht explizit als false definiert ist, kann zu längeren Ausführungszeiten von Plug-Ins führen.         |
|[Timeout einstellen bei externen Anrufen in einem Plugin](set-timeout-for-external-calls-from-plug-ins.md)     |Begrenzen Sie den Zeitraum, in dem externe Anrufe eine Antwort innerhalb von Plugins erwarten.|   
|[InvalidPluginExecutionExceptionException in Plugins und Workflow-Aktivitäten verwenden](use-invalidpluginexecutionexception-plugin-workflow-activities.md)     |Verwenden Sie InvalidPluginExecutionExceptionException, wenn Sie im Rahmen einer Plug-in- oder Workflow-Aktivität Fehler melden.         |

### <a name="see-also"></a>Siehe auch

[Geschäftslogik mit Code anwenden](../../apply-business-logic-with-code.md)<br />
[Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen](../../plug-ins.md)<br />
[Workflowerweiterungen](../../workflow/workflow-extensions.md)<br />