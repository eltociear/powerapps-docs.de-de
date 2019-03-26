---
title: Optimierung der Entwicklung kundenspezifischer Assemblies | MicrosoftDocs
description: 'Erwägen Sie, separate Plug-Ins/Anpassungen von Arbeitsabläufen in einer einzigen benutzerdefinierten Assembly zusammenzuführen, um die Leistung und Wartbarkeit zu verbessern, und verschieben Sie Plug-Ins/Anpassungen von Arbeitsabläufen in mehrere benutzerdefinierte Assemblies, wenn sich eine Assembly-Größe in der Nähe der Größenbeschränkungen von SandboxAssemblies befindet.'
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
# <a name="optimize-assembly-development"></a>Optimieren der Assemblyentwicklung

**Kategorie**: Leistung, Wartungsfreundlichkeit, Design

**Wirkungspotential**: Niedrig

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Bei der Entwicklung von kundenspezifischen Baugruppen gibt es einige Überlegungen zu berücksichtigen:

1. Mehrere verschiedene kundenspezifische Assemblies
    - Erhöhte Komplexität der Wartbarkeit
    - Potenzielle Erhöhung der Länge der Plug-in-Ausführung

2. Die Größenbeschränkung für Sandbox-Assemblies beträgt 16 MB im Common Data Service for Apps.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

> [!NOTE]
> Weitere Hinweise zur Klärung spezifischer Details bei der Optimierung der Assembliesentwicklung, wie z. B. die Zusammenführung einzelner Plug-Ins zu einer einzigen kundenspezifischen Assembly und Vorschläge zur Minimierung der Assembly-Größe, werden derzeit erarbeitet.

### <a name="consolidate-plug-ins-or-custom-workflow-activities-into-a-single-assembly"></a>Konsolidieren Sie Plug-Ins oder benutzerdefinierte Workflow-Aktivitäten in einer einzigen Assembly.

Plug-Ins und benutzerdefinierte Workflow-Aktivitäten, die für eine Common Data Service for Apps-Lösung entwickelt wurden, sollten zusammen mit anderen in einem einzigen Visual Studio-Projekt existieren. Erwägen Sie, separate Plug-Ins/Anpassungen von Arbeitsabläufen zu einem einzigen Visual Studio-Projekt/Assembly zusammenzuführen, es sei denn, die Plug-Ins fallen unter die folgenden Ausnahmen:

1. Eine Plug-in- und benutzerdefinierte Workflow-Aktivität muss selektiv in einer Umgebung eingesetzt werden, nicht aber in anderen.

2. Die Größe der physischen Assembly liegt nahe oder größer als 16 MB für einen Common Data Service for Apps Instanz.


### <a name="move-plug-inscustom-workflow-activities-into-multiple-assemblies"></a>Plug-Ins/Benutzerdefinierte Workflow-Aktivitäten in mehrere Assemblies verschieben

PowerApps und Dynamics 365 (online) haben eine Assembly-Größenbeschränkung von 16 MB, die nicht geändert werden kann. Wenn Ihre Assembly-Größe sich 16 MB nähert, ziehen Sie in Betracht, Plug-in- und benutzerdefinierte Workflow-Aktivitäten in mehrere Assemblys zu verschieben.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

### <a name="multiple-assemblies"></a>Mehrere Assemblys
Bei mehreren Assemblies gibt es eine Reihe von Bereichen, die betroffen sein können:

1. Leistung - jede Assembly hat einen Lebenszyklus, der von Common Data Service for Apps verwaltet wird.  Dazu gehören das Laden, Zwischenspeichern und Entladen der Assemblies.  Wenn mehr als eine Assembly vorhanden ist, wird mehr Arbeit auf dem Server geleistet, indem eine Assembly geladen und zwischengespeichert wird, was sich auf die gesamte Ausführungsdauer von Plugins und benutzerdefinierten Workflow-Aktivitäten auswirken kann.

2. Wartbarkeit - mehr als ein Visual Studio-Projekt mit mehr als einer Plug-in- und benutzerdefinierten Workflow-Aktivität führt zu einem komplexeren Application Lifecycle Management (ALM). Es erhöht das Risiko und die Zeitspanne, wenn das entsprechende Projekt für ein bestimmtes Plug-in/eine bestimmte Workflow-Aktivität aktualisiert bzw. gepatcht wird, wenn die Plug-ins/die benutzerdefinierten Workflow-Aktivitäten in einer Lösung zusammengefasst werden und wenn Plug-ins/die benutzerdefinierten Workflow-Aktivitäten innerhalb einer Bereitstellung verwaltet werden.

### <a name="assembly-larger-than-16-mb"></a>Assembly größer als 16 MB
Sie können keine benutzerdefinierte Assembly innerhalb des Common Data Service for Apps registrieren, die größer als 16 MB ist.

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Häufig erstellen Entwickler für jede Plug-in- und benutzerdefinierte Workflow-Aktivität ein neues Visual Studio-Projekt.  Dies wiederum führt dazu, dass für jede Plug-in-/kundenspezifische Workflow-Aktivität eine separate Assembly generiert wird.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Ereignisframework](../../event-framework.md)<br />
[Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen](../../plug-ins.md)<br />
