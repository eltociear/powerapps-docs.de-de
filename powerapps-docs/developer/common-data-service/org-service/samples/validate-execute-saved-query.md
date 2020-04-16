---
title: 'Beispiel: Überprüfen und Ausführen einer gespeicherten Abfrage (Common Data Service) | Microsoft-Dokumentation'
description: In diesem Beispiel wird gezeigt, wie eine gespeicherte Abfrage überprüft und ausgeführt wird
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
ms.openlocfilehash: ba1bd8e9cef6cbfc30e6289a20c6d79114d156f9
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155506"
---
# <a name="sample-validate-and-execute-a-saved-query"></a>Beispiel: Überprüfen und ausführen einer gespeicherten Abfrage

<!-- Needs supporting conceptual topic 
https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-validate-execute-saved-query
-->
Dieses Beispiel zeigt die Verwendung der Nachricht [IOrganizationService.ValidateSavedQueryRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.validatesavedqueryrequest?view=dynamics-general-ce-9), zum Überprüfen einer FetchXML-Abfrage und dann die Verwendung der Nachricht [IOrganizationService.ExecuteByIdSavedQueryRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.executebyidsavedqueryrequest?view=dynamics-general-ce-9), um die Abfrage auszuführen. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ValidateandExecuteSavedQuery) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Funktionsweise:

Die `ValidateSavedQueryRequest`-Klasse ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie die Daten enthält, die zur Überprüfung einer gespeicherten Abfrage benötigt werden (Ansicht). 

Die `ExecuteByIdSavedQueryRequest`-Klasse ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie die Daten enthält, die zur Ausführung einer gespeicherten Abfrage benötigt werden (Ansicht), die die angegebene ID hat.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `Account`-Methode erstellt 3 Firmendatensätze.
1. Die `SavedQuery`-Methode erstellt eine „Gespeichert”-Abfrage.
1. Die `UserQuery`-Methode erstellt eine „Benutzer”-Abfrage.


### <a name="demonstrate"></a>Demonstrieren
1. Die `ValidateSavedQueryRequest`-Methode erstellt die Überprüfungsanforderung.
1. Die `ExecuteByIdSavedQueryRequest`-Methode führt die gespeicherte Abfrage aus.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.
