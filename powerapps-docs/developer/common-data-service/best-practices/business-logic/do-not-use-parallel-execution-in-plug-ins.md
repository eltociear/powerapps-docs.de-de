---
title: Verwenden Sie keine parallele Ausführung in Plug-Ins und Workflow-Aktivitäten | MicrosoftDocs
description: Multithreading oder paralleles Threading in Plug-Ins oder benutzerdefinierten Workflowaktivitäten wird nicht unterstützt.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/14/2019
ms.author: pehecke
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="do-not-use-parallel-execution-within-plug-ins-and-workflow-activities"></a>Verwenden Sie keine parallele Ausführung in Plug-Ins und Workflow-Aktivitäten

**Kategorie**: Entwurf, Leistung, Sicherheit, Unterstützbarkeit

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Multithreading oder parallele Aufrufe in Plug-Ins oder benutzerdefinierten Workflowaktivitäten können diese Verbindungen beschädigen.  Beispielsweise kann die Ausführung von parallelen Threads Ausnahmen protokollieren, beispielsweise:

`Generic SQL error.`
`The transaction active in this session has been committed or aborted by another session.`

Außerdem können nicht threadsichere Objekte wie Elemente im [System.Collections-Namespace](/dotnet/api/system.collections) durch parallele Threads beschädigt werden.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Der Sandboxdienst wurde konzipiert, um Aufrufe in einer bestimmten Reihenfolge als Bestandteil der Transaktion auszuführen.  Die Entwicklung von Plug-Ins oder benutzerdefinierten Workflowaktivitäten für parallele oder Multithread-Aufrufe wird nicht unterstützt.  Berücksichtigen Sie bei der Entwicklung von Plug-Ins und benutzerdefinierten Workflowaktivitäten, dass Aufrufe sequenziell ausgeführt werden und möglicherweise ein Rollback ausgeführt werden muss.

> [!NOTE]
> Das Verwenden der parallelen Ausführung über ein Clientprogramm ist eine unterstützte Methode, um die Leistung nach Bedarf zu optimieren. Diese Anleitung ist speziell für Code, der erstellt wird, um in einem Plug-In oder einer benutzerdefinierten Workflowaktivität ausgeführt zu werden.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

Plug-Ins und benutzerdefinierte Workflowaktivitäten werden in einer einzelnen Transaktion ausgeführt und mehreren Threads, die von parallelen Ausführen eingeführt werden, können die Transaktion beschädigten. Nachfolgend sehen Sie Beispiele von Mustern und Methoden, die nicht in Plug-Ins und benutzerdefinierten Workflowaktivitäten verwendet werden sollten:

- Verwendung von [aufgabenbasierten asynchronen Mustern (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)
- Verwendung einer [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)
- Verwendung von [verwaltetem Threading](/dotnet/standard/threading/index)


<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Die Verwendung und Aktualisierung von freigegebenen Pipelinekontextobjekten kann dazu führen, dass diese Objekte unerwartete Ergebnisse enthalten oder beschädigt werden. Die Auswirkung davon kann ein Fehler im Plug-In oder einer benutzerdefinierten Workflowaktivität sein. 

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Parallelverarbeitung, Parallelität und asynchrone Programmierung in .NET](/dotnet/standard/parallel-processing-and-concurrency)<br />