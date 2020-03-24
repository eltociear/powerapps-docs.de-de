---
title: Datenabfrage mithilfe von LINQ (Common Data Service)| Microsoft Docs
description: Dieses Beispiel zeigt, wie Datensätze einem Team zugewiesen werden.
ms.custom: ''
ms.date: 02/05/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: phecke
ms.author: pehecke
manager: KumarVivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 20b68c32ccdf7a716b3bc021e7869e22f25f8526
ms.sourcegitcommit: d572c38a411e8588203d0909bc34c844ee508330
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "3029263"
---
# <a name="sample-query-data-using-linq"></a>Beispiel: Datenabfrage mithilfe von LINQ

Diese Beispiele zeigen, wie Geschäftsdaten mithilfe von [Sprachintegrierten Abfrage (LINQ) abgefragt werden](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries). Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueriesUsingLINQ) herunterladen. 

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

Weitere Informationen unter [Wie man Beispiele lässt](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/README.md) zum Ausführen dieses Beispiels. Die Lösung enthält mehrere Projekte. Jedes Projekt zeigt einige Aspekte von LINQ-Abfragen.

## <a name="what-this-sample-does"></a>Funktionsweise:

Lesen Sie die Kommentare jedes Beispiels, um herauszufinden, was jedes Beispiel tut. Es gibt Beispiele, die:
* Erstellen einer einfachen LINQ-Abfrage
* Erstellen Sie eine LINQ-Abfrage mithilfe der späten Entitätsbindung
* Mehrere Datensätze abrufen mit Bedingungsoperatoren
* Komplexe Abfragen – eine große Auswahl an LINQ-Beispielen

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

Erstellt alle Entitätsinstanzen, die von der `Demonstrate` Region von jeder `Main`() Methode erforderlich sind.

### <a name="demonstrate"></a>Demonstrieren

Code in der `Demonstrate` Region der `Main`() Methode führt eine oder mehrere LINQ-Abfragen aus.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die bei der [Einrichtung](#setup) erstellt wurden.

Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.