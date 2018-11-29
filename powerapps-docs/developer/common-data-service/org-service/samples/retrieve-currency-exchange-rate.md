---
title: 'Beispiel: Abrufen von Wechselkursen (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel veranschaulicht, wie Sie eine neue Währung erstellen und den Wechselkurs abrufen und anzeigen.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-retrieve-currency-exchange-rate"></a>Beispiel: Abrufen von Wechselkursen

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-retrieve-currency-exchange-rate -->

Dieses Beispiel zeigt, wie Sie eine neue Währung erstellt und wie der Wechselkurs in Bezug zur Basiswährung der Organisation abgerufen und angezeigt werden kann. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveCurrencyExchangeRate) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Message `RetrieveExchangeRateRequest` ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die für das Abrufen des Wechselkurses erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation. 
2. Die Methode `TransactionCurrency` erstellt eine neue Währung für das Beispiel.

### <a name="demonstrate"></a>Demonstrieren

1. Die Message `RetrieveExchangeRateRequest` ruft den Wechselkurs für die Basiswährung der Organisation ab.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Beispieldaten zu löschen, die unter [Einrichten](#setup) erstellt wurden.
    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
