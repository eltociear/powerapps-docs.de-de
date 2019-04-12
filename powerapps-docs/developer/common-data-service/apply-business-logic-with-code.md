---
title: Geschäftslogik mit Code anwenden (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie, wie Entwickler Geschäftslogik in Common Data Service mit Code anwenden können.'
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: kvivek
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="apply-business-logic-using-code"></a>Geschäftslogik mit Code anwenden

Wenn immer möglich, sollten Sie zunächst überlegen, eine der mehreren deklarativen Prozessoptionen zur Definition oder Anwendung der Geschäftslogik anzuwenden. Weitere Informationen: [Anwenden von Geschäftslogik in Common Data Service](../../maker/common-data-service/cds-processes.md)

Wenn ein deklarativer Prozess eine Anforderung nicht erfüllt, haben Sie als Entwickler mehrere Möglichkeiten. In diesem Thema werden allgemeine Optionen zum Schreiben von Code vorgestellt.

## <a name="create-a-plug-in"></a>Plug-In erstellen

Sie können eine.NET-Assembly schreiben, um ein Plug-in für die Datentransaktion zu erstellen, um die Geschäftslogik auf den Server anzuwenden. Mit Common Data Service gibt es ein Framework, mit dem Sie bestimmte Ereignisse registrieren können, um innerhalb einer Klasse definierten Code in einer Assembly auszuführen. 

Weitere Infroamtionen: [Schreiben von Plug-Ins zur Erweiterung von Geschäftsprozessen](plug-ins.md)

## <a name="create-a-workflow-extension"></a>Erstellen einer Workflow-Erweiterung

Sie können eine.NET-Assembly schreiben, um neue Optionen innerhalb des Prozess-Designers bereitzustellen. Diese Methode bietet eine neue Option für Personen, die den Workflow-Designer verwenden, um eine Bedingung anzuwenden oder eine neue Aktion auszuführen. Eine Workflowerweiterung kann dann von Personen, die keine Entwickler sind, wiederverwendet werden, um die Logik in Ihrem Code anzuwenden.

Weitere Informationen: [Workflowerweiterungen](workflow/workflow-extensions.md)

### <a name="see-also"></a>Siehe auch

[Common Data Service-Entwicklerübersicht](overview.md)
