---
title: 'Beispiel: Konvertieren von Abfragen zwischen FetchXML und QueryExpression (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie Abfragen zwischen FetchXML und QueryExpression konvertiert werden'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-convert-queries-between-fetchxml-and-queryexpression"></a>Beispiel: Konvertieren von Abfragen zwischen FetchXML und QueryExpression

Dieses Beispiel zeigt, wie Abfragen zwischen FetchXML und QueryExpression konvertiert werden. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Convertqueriesfetchqueryexpressions) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `QueryExpression` und `fetchExpression`-Nachrichten sind für die Verwendung in einem Szenario vorgesehen, das Abfragen in einer Hierarchie von Ausdrücken bzw. FetchXML enthält.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation. 
1. Die `CreateRequireRecords`-Methode erstellt ein Konto und zwei Kontaktdatensätze, die vom Beispiel verwendet werden.
1. Die `QueryExpression` erstellt einen Abfrageausdruck, den wir in FetchXML konvertieren.
1. Diese `DoFetchXmlToQueryExpressionConversion`-Klasse erstellt eine Fetch-Abfrage, die Sie in einen Abfrageausdruck konvertieren.
1. Zum `conversionRequest`-Methode konvertiert den generierte Abfrageausdruck in FetchXML und umgekehrt.
1. Verwenden Sie eine konvertierte Abfrage, um Mehrfachanfragen festzulegen. 

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
