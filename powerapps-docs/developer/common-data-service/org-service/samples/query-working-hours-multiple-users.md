---
title: 'Beispiel: Abfragen der Arbeitszeit von mehreren Benutzern (Common Data Service) | Microsoft Docs'
description: 'In diesem Beispiel wird gezeigt, wie die Arbeitszeit von mehrere Benutzern abgefragt wird'
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
# <a name="sample-query-the-working-hours-of-multiple-users"></a>Beispiel: Abfragen der Arbeitszeit von mehreren Benutzern

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-query-working-hours-multiple-users -->

Dieses Beispiel zeigt, wie Sie die Arbeitszeit von mehreren Benutzern mithilfe der Message [QueryMultipleSchedulesRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.querymultipleschedulesrequest?view=dynamics-general-ce-9) abrufen. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23) herunterladen.

Dieses Beispiel benötigt weitere Benutzer, die nicht in Ihrem System vorhanden sind. Erstellen Sie den erforderlichen Benutzer manuell **wie dargestellt** unten in **Office 365**, bevor Sie sich das Beispiel ausführen. Ersetzen Sie `yourorg` durch den `OrgName` Ihrer Organisation.

**Vorname**: Kevin<br/>
**Nachname**: Cook<br/>
**Sicherheitsrolle**: Vertriebsmanager<br/>
**Benutzername**: kcook@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Message `QueryMultipleScheduleRequest` soll in einem Szenario verwendet werden, in dem sie die Daten enthält, die erforderlich sind, um mehrere Ressourcen nach einem verfügbaren Zeitblock zu durchsuchen, der den angegebenen Parametern entspricht.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Ruft die Informationen des aktuellen Benutzers sowie des Benutzers ab, den Sie manuell in **Office 365** erstellt haben.

### <a name="demonstrate"></a>Demonstrieren

1. Die Message `QueryMultipleScheduleRequest` ruft die Arbeitszeit des aktuellen Benutzers und der Benutzer ab, die Sie manuell erstellt haben.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
