---
title: " Zuweisen eines Diagramms zu einem anderen Benutzer (Common Data Service) | Microsoft-Dokumentation"
description: 'Dieses Beispiel zeigt, wie eine Visualisierung im Besitz eines Benutzers einem anderen Benutzer zugewiesen wird '
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: 7274ff6800dc86c5e566f64dbd5fe1b72182327d
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155966"
---
# <a name="assign-a-chart-to-another-user"></a>Zuweisen eines Diagramms zu einem anderen Benutzer

Dieses Beispiel zeigt, wie eine Visualisierung im Besitz eines Benutzers mithilfe der [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9)-Meldung einem anderen Benutzer zugewiesen wird. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssignChartToAnotherUser) herunterladen.

Dieses Beispiel benötigt einen weiteren Benutzer, der nicht in Ihrem System vorhanden sind. Erstellen Sie die erforderlichen Benutzer manuell in **Office 365**, um das Beispiel ohne Fehler auszuführen. Erstellen Sie für dieses Beispiel ein Benutzerprofil **wie** unten gezeigt. 

**Vorname**: Kevin<br/>
**Nachname**: Cook<br/>
**Sicherheitsrolle**: Vertriebsmanager<br/>
**Benutzername**: kcook@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9)-Meldung soll in einem Szenario verwendet werden, in dem sie die Daten enthält, die erforderlich sind, um den angegebenen Datensatz einem neuen Besitzer(Benutzer oder Team) zuzuweisen, indem das OwnerId-Attribut des Datensatzes geändert wird.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die Methode `CreateRequiredRecords` erstellt ein Beispielkonto und einige Verkaufschancen-Datensätze für die Visualisierung.
3. Die `newUserOwnedVisualization`-Methode erstellt die Instanz der Visualisierungsentität.

### <a name="demonstrate"></a>Demonstrieren

Die Methode `AssignRequest` weist die Visualisierung oder das Diagramm dem neu erstellten Benutzer zu.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.