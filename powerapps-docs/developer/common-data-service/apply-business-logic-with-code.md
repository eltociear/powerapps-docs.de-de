---
title: Anwenden von Geschäftslogik mit Code | Microsoft-Dokumentation
description: Erfahren Sie, wie Entwickler Code verwenden können, um Geschäftslogik in Common Data Service für Apps anzuwenden.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/26/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9abcbf25d2376e28f83988ceb3797d3891ca53bc
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42843335"
---
# <a name="apply-business-logic-with-code"></a>Anwenden von Geschäftslogik mit Code

Wenn möglich sollten Sie zuerst eine der verschiedenen Prozessoptionen anwenden, wenn eine Anforderung das Definieren von Geschäftslogik umfasst. Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Geschäftslogik durch Prozesse](/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes).

Wenn ein deklarativer Prozess einer Anforderung nicht entspricht, haben Sie als Entwickler verschiedene Möglichkeiten. In diesem Artikel werden häufig zum Schreiben von Code verwendete Optionen erläutert.

## <a name="create-a-workflow-extension"></a>Erstellen einer Workflowerweiterung

Sie können eine .NET-Assembly schreiben, um innerhalb des Prozessdesigners neue Optionen zur Verfügung zu stellen. Diese Methode stellt eine neue Option zum Anwenden oder Durchführen einer neuen Aktion für die Benutzer des Workflow-Designers dar. Workflowerweiterungen können anschließend von Benutzern, bei denen es sich nicht um Entwickler handelt, erneut verwendet werden, um die Logik in ihrem Code anzuwenden.

Weitere Informationen finden Sie unter [Benutzerdefinierte Workflowaktivitäten (Workflowassemblys)](/dynamics365/customer-engagement/developer/custom-workflow-activities-workflow-assemblies).

## <a name="create-a-plug-in"></a>Erstellen eines Plug-Ins

Sie können eine .NET-Assembly schreiben, die als Plug-In für den Datentransaktionsflow dient, um auf dem Server Geschäftslogik anzuwenden. Common Data Service für Apps stellt ein Framework dar, mit dem Sie bestimmte Ereignisse registrieren können, um Code auszuführen, der innerhalb einer Klasse in einer Assembly definiert ist. Diese Klasse erbt eine bestimmte Schnittstelle, die eine [Execute-Methode](/dotnet/api/microsoft.xrm.sdk.iplugin.execute) verfügbar macht. Wenn das registrierte Ereignis auftritt, wird die `Execute`-Methode für die Klasse ausgelöst und Kontextdaten zu dem Ereignis weitergegeben.

Sie können mit dem *Tool zur Plug-In-Registrierung* Ihre Assemblys registrieren.

Innerhalb der `Execute`-Methode können Sie das Objektmodell verwenden, das in den SDK-Assemblys definiert ist, um die Kontextdaten zu dem Ereignis auszuwerten und angemessene Maßnahmen zu ergreifen. Dann können Sie Folgendes tun:
- Sie können bestimmen, ob der Vorgang abgebrochen werden soll, indem Sie einen Fehler auslösen.
- Sie können Änderungen an Kontextdaten vornehmen, die an die Execute-Methode weitergegeben werden.
- Sie können zusätzlich Vorgänge durchführen, um mithilfe des Organisationsdiensts Prozesse zu automatisieren.

### <a name="synchronous-and-asynchronous-plug-ins"></a>Synchrone und asynchrone Plug-Ins
Plug-Ins können so registriert werden, dass sie synchron innerhalb der Transaktion ausgeführt werden oder dass sie verzögert bereitgestellt und an eine Warteschlange gesendet werden, die die Logik zu einem Zeitpunkt anwendet, zu der der Server davon weniger beeinträchtigt wird. Aus diesem Grund werden asynchrone Plug-Ins bevorzugt.

Wenn Sie das Plug-In so registrieren, dass es synchron zu einem Ereignis ausgeführt wird, können Sie auswählen, wann der Code ausgeführt werden soll. Es gibt drei Phasen:

|Veranstaltung  |Beschreibung  |
|---------|---------|
|Vorabüberprüfung|Wird durchgeführt, bevor die Datenbanktransaktion gestartet wird. Dies ist eine gute Möglichkeit, Geschäftslogik anzuwenden, um zu bestimmen, ob der Vorgang abgebrochen werden sollte, bevor die Transaktion gestartet wird, um so Leistungseinbußen zu verhindern, die entstehen können, wenn ein Rollback ausgeführt wird.|
|Vorgelagerter Vorgang|Wird durchgeführt, nachdem die Datenbanktransaktion gestartet wurde. Wenn Sie in dieser Phase einen Vorgang abbrechen, muss ein Rollback für die Transaktion ausgeführt werden.|
|Nachgelagerter Vorgang|Wird innerhalb der Datenbanktransaktion durchgeführt, nachdem der wichtigste Datenvorgang abgeschlossen wurde. Umfasst jegliche Änderungen, die möglicherweise bei früheren Ereignissen angewendet wurden. Bei Abbruch des Vorgangs muss jedoch mit noch stärkeren Leistungseinbußen gerechnet werden.|

> [!NOTE]
> Synchrone Plug-Ins können nur eine beschränkte Anzahl von Systemressourcen verwenden. Wenn ein Plug-In Grenzwerte überschreitet oder nicht mehr antwortet, wird eine Ausnahme ausgelöst, durch die der Vorgang abgebrochen wird.

Weitere Informationen finden Sie unter [Schreiben von Plug-Ins, um Geschäftsprozesse zu erweitern](/dynamics365/customer-engagement/developer/write-plugin-extend-business-processes).

### <a name="see-also"></a>Siehe auch

[Common Data Service for Apps Developer Overview (Übersicht für Entwickler: Common Data Service für Apps)](overview.md)
