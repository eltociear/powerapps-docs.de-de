---
title: 'Beispiel: Konvertieren Sie Faxe in Abfragen (Common Data Service) | Microsoft Docs'
description: 'Beispiel, das zeigt, wie man einen Fax in eine Aufgabe umwandelt. '
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
# <a name="sample-convert-a-fax-to-a-task"></a>Beispiel: Konvertieren eines Faxes für eine Aufgabe

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-convert-fax-task -->


Beispiel, das zeigt, wie man einen **Fax** in eine **Aufgabe** umwandelt. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ConvertFaxToTask) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Funktionsweise:

Die `CreateRequiredRecords`-Methode erzeugt das für die Beispieldaten erforderliche Beispiel. Die `retrievedFax`-Methode ruft das Fax ab. Die `DeleteRequiredRecords`-Methode bietet die Möglichkeit, alle Daten zu löschen, die das Beispiel erstellt hat.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `WhoAmIRequest`-Methode ruft die aktuellen Benutzerdetails ab.
1. Die `ActivityParty`-Methode erstellt die Aktivitätspartei für das Senden und Empfangen von Faxen.
1. Die `Fax`-Methode erstellt das für das Beispiel erforderliche Fax.


### <a name="demonstrate"></a>Demonstrieren

1. Ruft alle Fax-IDs ab, die im [Setup](#setup) erstellt wurden.
2. Erstellt eine Aufgabe und überprüft, ob die Aufgabe erstellt wurde. 

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an.
2. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.
