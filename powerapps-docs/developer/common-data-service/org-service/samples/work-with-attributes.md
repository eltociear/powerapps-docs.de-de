---
title: 'Beispiel: Arbeiten mit Attributen (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel zeigt, wie man mit Attributen arbeitet
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 230746590755e6c467ed5846505b889c1fbefd75
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155486"
---
# <a name="work-with-attribute-metadata"></a>Verwenden von Attributmetadaten

Dieses Beispiel zeigt, wie Sie verschiedene Aktionen für Attribute ausführen. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkWithAttributes) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Dieses Beispiel zeigt, wie man verschiedene Arten von Attributen in Common Data Service erstellt.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `BooleanAttributeMetadata`-Methode erstellt ein Attribut vom Typ "Boolean".
2. Die `DateTimeAttributeMetadata`-Nachricht erzeugt ein Attribut vom Typ Datum/Uhrzeit.
3. Die `DecimalAttributeMetadata`-Nachricht erzeugt ein Attribut vom Typ Dezimal.
4. Die `IntegerAttributeMetadata`-Nachricht erzeugt ein Attribut vom Typ Integer.
5. Die `MemoAttributeMetadata`-Nachricht erzeugt ein Attribut vom Typ Memo.
6. Die `MoneyAttributeMetadata`-Nachricht erzeugt ein Attribut vom Typ Währung.
7. Die Meldung `PicklistAttributeMetadata` erzeugt ein Attribut vom Typ Picklist.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.