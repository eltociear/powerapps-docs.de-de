---
title: 'Beispiel: Senden von Massen-E-Mails und Überwachen der Ergebnisse (Common Data Service) | Microsoft-Dokumentation'
description: Diese Beispiele zeigen, wie Massen-E-Mails gesendet und Ergebnisse überwacht werden
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
ms.openlocfilehash: bc2fcd19815339fd822a5de7674b0e6f031b5532
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155590"
---
# <a name="sample-send-bulk-email-and-monitor-results"></a>Beispiel: Senden von Massen-E-Mails und Überwachen der Ergebnisse

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-send-bulk-email-monitor-results -->

Dieses Beispiel zeigt, wie mithilfe von <xref:Microsoft.Crm.Sdk.Messages.SendBulkMailRequest> Massen-E-Mails gesendet und die Ergebnisse durch Abrufen von Datensätzen aus der `AsyncOperation`-Entität überwacht werden. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/BulkEmail) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Message `SendBulkMailRequest` ist zur Verwendung in einem Szenario zum Senden von Massen-E-Mails bestimmt.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf die aktuelle Version der Organisation.
1. Die Methode `Contact` erstellt 2 Kontaktdatensätze für dieses Beispiel.

### <a name="demonstrate"></a>Demonstrieren

1. Fordert den als Absender zu verwendeten Systembenutzer an.
2. Legen Sie die Nachverfolgungs-ID für die E-Mail-Massen-Anforderung fest.
3. Erstellt einen Abfrageausdruck für den Massenvorgang, um die Kontakte in der E-Mail-Liste abzurufen.
4. Legen Sie die entsprechende ID fest und führen Sie die Massen-E-Mail-Anforderung aus.
5. Rufen Sie den Massen-E-Mail-async-Vorgang ab und überwachen Sie ihn durch Abruf.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
