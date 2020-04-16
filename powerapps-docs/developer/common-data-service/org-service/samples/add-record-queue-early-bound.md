---
title: 'Beispiel: Hinzufügen eines Datensatzes zu einer Warteschlange (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie einem einer Warteschlange ein Datensatz zugefügt wird.
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
ms.openlocfilehash: 6c3ecaa99c557b771a285b0bff2f14c2863a7950
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155978"
---
# <a name="sample-add-a-record-to-a-queue"></a>Beispiel: Einen Datensatz zur Abfrage hinzufügen

Dieses Beispiel zeigt, wie einem einer Warteschlange ein Datensatz zugefügt wird. Es erstellt Zielwarteschlangen und Quellwarteschlangen. Es fügt der Quellwarteschlange eine Schreiben-Aktivität hinzu und verschiebt sie dann in die Zielwarteschlange. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RecordToQueue) herunterladen.

Dieses Beispiel benötigt weitere Benutzer, die nicht in Ihrem System sind. Erstellen Sie die Benutzer manuell in **Office 365**, um das Beispiel ohne Fehler auszuführen. Erstellen Sie für dieses Beispiel ein Benutzerprofil **wie** unten gezeigt. 

**Vorname**: Kevin<br/>
**Nachname**: Cook<br/>
**Sicherheitsrolle**: Vertriebsmanager<br/>
**Benutzername**: kcook@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht `AddToQueueRequest` ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die benötigt werden, um einen Entitätsdatensatz von einer Quellwarteschlange in eine Zielwarteschlange zu verschieben.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Zum `Queue` Methode erstellt Quell- und Zielwarteschlangen und speichert die zurückgegebenen GUIDs in einer Variablen.
3. Erstellt eine Briefentität.
4. Die `AddToQueueRequest`-Methode fügt einen Entitätsdatensatz einer Warteschlange hinzu, in diesem Beispiel , ordnet sie den Brief der ersten Warteschlange zu.
5. Ruft den manuell in **Office 365** erstellten Benutzer zum Zuweisen der Queue-Elemente zur Warteschlange des Benutzers ab.

### <a name="demonstrate"></a>Demonstrieren

1. Die `RetrieveUserQueueRequest` Nachricht ruft die bekannten privaten Warteschlangen für den Benutzer ab.
2. Die `AddToQueueRequest` Nachricht fügt den Datensatz von einer Quellwarteschlange einer Zielwarteschlange hinzu.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
