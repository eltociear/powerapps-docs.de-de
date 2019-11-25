---
title: Entfernen von nicht unterstütztem Code, der Reflektion in benutzerdefinierten Workflowaktivitäten verwendet | MicrosoftDocs
description: Sie müssen den Codeausschnitt, der in diesem Thema beschrieben wird, entfernen, wenn Sie ihn in benutzerdefinierten Workflowaktivitäten finden
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
ms.date: 08/15/2019
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e1cfd0c9c0ac9b2a5ce5f71f1035a7d6c2f84be2
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748243"
---
# <a name="remove-unsupported-code-that-uses-reflection-in-custom-workflow-activities"></a>Entfernen von nicht unterstütztem Code, der Reflektion in benutzerdefinierten Workflowaktivitäten verwendet

**Kategorie**: Zuverlässigkeit

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Bei Workflowaktivitäten, die nicht unterstützten Code enthalten, der Reflektion verwendet, wird es in den kommenden Monaten zu Problemen kommen, sofern dieser nicht entfernt wurde.

Workflowerweiterungen können den Fehler `Could not load file or assembly 'Microsoft.Crm.Workflow, Version=` nicht auslösen. Die Versionsnummer kann sich unterscheiden, lautet aber normalerweise `6.0.0.0`.


<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Code in benutzerdefinierten Workflowaktivitäten sollte nicht hinzugefügt und daher proaktiv gesucht und entfernt werden. Beispiel:

```
var type = Type.GetType("Microsoft.Crm.Workflow.SynchronousRuntime.WorkflowContext, Microsoft.Crm.Workflow, Version=6.0.0.0");
type.GetProperty("ProxyTypesAssembly").SetValue(serviceFactory, typeof(YourServiceContext).Assembly, null); 
```

Wenn Sie Code wie diesen finden, der Reflektion in einer benutzerdefinierten Workflowaktivität verwendet, sollten Sie ihn entfernen, rekompilieren und die Assembly, die ihn enthält, aktualisieren.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

Dieser Code dient derzeit keinem Zweck. Er wurde anscheinend vor etwa 7 Jahren von Entwicklern zur Umgehung von Problemen mit starken Typen (mit früher Bindung) hinzugefügt. 

Ausschnitte mit diesem Code können in vielen Forenbeiträgen gefunden werden, die nicht mit dem Problem verknüpft sind. Dies wird als Lösung in diesem Beitrag zum Stapelüberlauf beschrieben: [So aktivieren Sie Proxytypen für einen Dienst, auf den über IWorkflowContext in CRM 2011 zugegriffen wird](https://stackoverflow.com/questions/9230117/how-to-enableproxytypes-on-a-service-accessed-from-the-iworkflowcontext-in-crm-2/45948206)

Das zugrundeliegende Problem beim Unterstützen von starken Typen wurde behoben, aber dieser Code ist in der Codebasis für benutzerdefinierte Workflowaktivitäten geblieben. Dieser Code wurde nie unterstützt, aber er hat keine Probleme verursacht. In den kommenden Monaten wird er bei benutzerdefinierten Workflows, die ihn enthalten, Probleme verursachen.


<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Derzeit ist die Reflektion nicht zulässig. Dieser Code verweist auf eine interne Assembly, die in eine Whitelist aufgenommen wurde, so dass der interne Code darüber nachdenken kann. Daher löst er derzeit keinen Fehler aus. Wenn aber allgemeine Einschränkungen in der Zukunft aufgehoben werden, kann er Probleme bei Workflowaktivitäten verursachen.

Um umfassendere Funktionen in benutzerdefinierten Workflowaktivitäten bieten zu können, ohne Probleme bei der Geschäftslogik der Benutzer zu verursachen, müssen alle ihre Codebasis überprüfen und Verweise wie diesen entfernen.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Workflowerweiterungen](../../workflow/workflow-extensions.md)
