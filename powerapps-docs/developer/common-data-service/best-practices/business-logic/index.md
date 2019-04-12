---
title: 'Entwickler: Bewährte Methoden und Anleitungen zur Plug-in- und Workflow-Entwicklung für den Common Data Service | Microsoft Docs'
description: Bewährte Methoden und Anleitungen zur Plug-in- und Workflow-Entwicklung für Entwickler des Common Data Service in PowerApps.
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
---
# <a name="best-practices-and-guidance-regarding-plug-in-and-workflow-development-for-the-common-data-service"></a>Bewährte Methoden und Anleitungen zur Plug-in- und Workflow-Entwicklung für den Common Data Service

Diese Liste enthält alle Anleitungen und bewährte Methoden für die Plug-in- und Workflow-Entwicklung innerhalb des Common Data Service

|Bewährte Methode  |Beschreibung  |
|---------|---------|
|[Vermeiden Sie die Verwendung von Batch-Requesttypen in Plugins und Workflow-Aktivitäten.](avoid-batch-requests-plugin.md)     |Sie sollten die Nachrichtenanforderungsklassen ExecuteMultipleRequest oder ExecuteTransactionRequest nicht im Rahmen einer Plug-in- oder Workflow-Aktivität verwenden.         |
|[Entwicklung von IPlugin-Implementierungen als zustandslose Systeme](develop-iplugin-implementations-stateless.md)     |Mitglieder von Klassen, die IPlugin implementieren, sind potenziellen Thread-Sicherheitsproblemen ausgesetzt, die zu Dateninkonsistenz- oder Performanceproblemen führen können.         |
|[Keine Registrierung von Plug-in-Schritten duplizieren](do-not-duplicate-plugin-step-registration.md)     |Die Registrierung eines doppelten Plug-in-Schrittes bewirkt, dass das Plug-in bei derselben Nachricht/Ereignis mehrmals ausgelöst wird.         |
|[Einbeziehen von Filterattributen mit Plugin-Registrierung](include-filtering-attributes-plugin-registration.md)     |Wenn für einen Registrierungsschritt des Plugins keine Filterattribute festgelegt sind, wird das Plug-in jedes Mal ausgeführt, wenn eine Update-Meldung für dieses Ereignis auftritt.         |
|[Einschränkung der Registrierung von Plugins für Retrieve- und RetrieveMultiple-Nachrichten](limit-registration-plugins-retrieve-retrievemultiple.md)     |Das Hinzufügen von synchroner Plugin-Logik zu den Nachrichtenereignissen Retrieve und RetrieveMultiple kann zu Verzögerungen führen.         |
|[Optimierung der Entwicklung kundenspezifischer Assemblies](optimize-assembly-development.md)     |Erwägen Sie, separate Plug-Ins/Anpassungen von Arbeitsabläufen in einer einzigen benutzerdefinierten Assembly zusammenzuführen, um die Leistung und Wartbarkeit zu verbessern, und verschieben Sie Plug-Ins/Anpassungen von Arbeitsabläufen in mehrere benutzerdefinierte Assemblies, wenn sich eine Assembly-Größe in der Nähe der Größenbeschränkungen von SandboxAssemblies befindet.         |
|[KeepAlive auf falsch setzen, wenn Sie mit externen Hosts in einem Plug-in interagieren](set-keepalive-false-interacting-external-hosts-plugin.md)     |Die KeepAlive-Eigenschaft, die im HTTP-Request-Header auf true gesetzt oder nicht explizit als false definiert ist, kann zu längeren Ausführungszeiten von Plug-Ins führen.         |
|[InvalidPluginExecutionExceptionException in Plugins und Workflow-Aktivitäten verwenden](use-invalidpluginexecutionexception-plugin-workflow-activities.md)     |Verwenden Sie InvalidPluginExecutionExceptionException, wenn Sie im Rahmen einer Plug-in- oder Workflow-Aktivität Fehler melden.         |

# <a name="see-also"></a>Siehe auch
[Geschäftslogik mit Code anwenden](../../apply-business-logic-with-code.md)<br />
[Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen](../../plug-ins.md)<br />
[Workflowerweiterungen](../../workflow/workflow-extensions.md)<br />