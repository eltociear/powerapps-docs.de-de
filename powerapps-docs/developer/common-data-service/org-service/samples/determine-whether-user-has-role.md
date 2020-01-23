---
title: " Ermitteln Sie, ob ein Benutzer eine Rolle hat (Common Data Service) | Microsoft-Dokumentation"
description: Dieses Beispiel zeigt, wie Sie bestimmen, ob ein Benutzer eine spezielle Rolle hat.
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: ''
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
ms.openlocfilehash: 77474ebc6f46800a3b1c28bea0a0dd1e1fb89c7e
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2914454"
---
# <a name="determine-whether-a-user-has-a-role"></a>Bestimmen, ob ein Benutzer über eine Rolle verfügt

Dieses Beispiel zeigt, wie Sie bestimmen, ob einem Benutzer in Common Data Service eine spezielle Rolle zugewiesen wurde. Dies erfolgt über eine Abfrage mit der Methode [IOrganizationService.RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9).  Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DetermineWhetherUserHasRole) herunterladen.

Dieses Beispiel benötigt einen weiteren Benutzer, der nicht in Ihrem System vorhanden sind. Erstellen Sie die erforderlichen Benutzer manuell in **Office 365**, um das Beispiel ohne Fehler auszuführen. Erstellen Sie für dieses Beispiel ein Benutzerprofil **wie** unten gezeigt. 

**Vorname**: Dan<br/>
Kontakt: **Nachname**<br/>
**Sicherheitsrolle** : Sicherheitsrolle Nein<br/>
**Benutzername**: dpark@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht [IOrganizationService.RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9) ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie eine Sammlung von Datensätzen abruft.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die Methode `CreateRequiredRecords` erstellt einen Benutzer, dem keine Sicherheitsrolle zugewiesen ist, wie oben gezeigt.

### <a name="demonstrate"></a>Demonstrieren

1. Die `retrieve`-Methode ruft einen Benutzer von Common Data Service ab.
2. Die Nachricht `query` wird verwendet, um eine Rolle herauszufinden.

### <a name="clean-up"></a>Bereinigung

Dieses Beispiel erstellt keine Datensätze. Keine Bereinigung erforderlich
