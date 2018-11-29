---
title: 'Beispiel: Abrufen von Zeitzoneninformationen (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie Zeitzoneninformationen abgerufen werden.'
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
# <a name="sample-retrieve-time-zone-information"></a>Beispiel: Abrufen von Zeitzoneninformationen

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-retrieve-time-zone-information -->

Dieses Beispiel zeigt, wie Zeitzoneninformationen abgerufen werden. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveTimeZone) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Methode `RetrieveAllTimeZonesForLocale` soll in einem Szenario verwendet werden, in dem die aktuelle Gebietsschema-ID verwendet wird, um alle Zonen abzurufen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die Methode `RetrieveCurrentUSerSettings` ruft den aktuellen Zeitzonencode und die aktuelle Gebietsschema-ID von Benutzern ab.
2. Die Methode `RetrieveAllTimeZonesForLocale` verwendet die aktuelle Gebietsschema-ID und ruft alle Zeitzonen ab.
3. Die Methode `GetTimeZoneCodeByLocaleAndName` ruft die Zeitzone nach Namen und die Gebietsschema-ID ab.
4. Die Methode `RetrieveTimeZoneById` ruft die Zeitzone nach ID ab.
5. Die Methode `RetrieveTimeZonesLessThan50` ruft Zeitzonen weniger als 50 ab.
6. Die Methode `RetrieveLocalTimeFromUTCTime` ruft die lokale Uhrzeit über die UTC-Zeit ab.
7. Die Methode `RetrieveUTCTimeFromLocalTime` ruft die UTC-Zeit über die lokale Uhrzeit ab.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
