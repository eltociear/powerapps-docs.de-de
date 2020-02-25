---
title: 'Beispiel: Workflow-Operationen (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel zeigt, wie eine Reihe von Workflow-Operationen wie Erstellen, Löschen, Aktivieren, Status setzen und mehr durchgeführt werden.
ms.custom: ''
ms.date: 1/14/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 051e08f11afaf9a291f28d8229311cf667e1db56
ms.sourcegitcommit: 1c4ab1859febccf79a835bd2f168e7e12a953a18
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "2957657"
---
# <a name="sample-workflow-operations"></a>Beispiel: Workflow-Operationen

Dieses Beispiel zeigt, wie eine Reihe von Workflow-Operationen wie Erstellen, Löschen, Aktivieren, Status setzen und mehr durchgeführt werden.

Laden Sie das Beispiel herunter: [Workflow](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Workflow)

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

Siehe [Wie man Beispiele ausführt ](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/README.md) für allgemeine Informationen über die Ausführung dieses Beispiels.

Beachten Sie, dass es fünf separate Beispiele, jedes in seiner eigenen C#-Datei, in der Lösung [Projekt](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Workflow/Workflow) gibt. Um jedes Beispiel auszuführen, legen Sie sie vor der Ausführung des Beispiels als Startobjekt in den Projekteigenschaften fest.

## <a name="what-this-sample-does"></a>Funktionsweise:

Die durch diese Beispiele veranschaulichten Operationen sind wie folgt:

- Erstellen Sie einen synchronen (Echtzeit) oder asynchronen Workflow
- Löschen eines Workflows
- Ausführen eines Workflows
- Aktivieren oder Deaktivieren eines Workflows
- Setzen oder Abrufen von Status und Zustand eines Workflows
- Erstellen Sie einen Workflow aus einer Vorlage

Sie können die erstellten Workflows unter **Einstellungen > Prozesse** (unter Prozesszentrum) anzeigen, wenn Sie Ihre Organisation mit einem Webbrowser betrachten.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

Jedes Beispiel erstellt alle erforderlichen Entitätsinstanzen, die der Demonstrationscode erfordert. Dies geschieht in der `CreateRequiredRecords()`-Methode.

### <a name="demonstrate"></a>Demonstrieren

Der Hauptdemonstrationscode für jedes Beispiel befindet sich im Bereich `Demonstrate` der `Main()`-Methode in jeder Klassendatei.

### <a name="clean-up"></a>Bereinigung

Bei der `DeleteRequiredRecords()`-Methode wird im Konsolenfenster eine Option zum Löschen aller durch das/die Beispiel(e) erstellten Datensätze angezeigt.

Die Löschung ist optional, falls Sie die von der/den Stichprobe(n) erzeugten Entitätsinstanzen (Datensätze) untersuchen wollen. Normalerweise würden Sie auf die Löschaufforderung im Konsolenfenster erst reagieren, nachdem Sie die neuen Organisationseinträge in Ihrem Browser angezeigt haben. Sie können die erstellten Datensätze jederzeit manuell löschen, nachdem das Programm beendet wurde, um das gleiche Ergebnis zu erzielen.
