---
title: " Zuordnen von Sicherheitsrollen zu einem Benutzer (Common Data Service) | Microsoft Docs"
description: 'Dieses Beispiel zeigt, wie eine Sicherheitsrolle einem Benutzer zugewiesen wird. '
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
ms.openlocfilehash: e01d2fd39caa6405a7340634c48f25f1c533843b
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155940"
---
# <a name="sample-associate-security-role-to-a-user"></a>Beispiel: Zuordnen einer Sicherheitsrolle zu einem Benutzer

Dieses Beispiel zeigt, wie einem Team mithilfe der Meldung [IOrganizationService.Associate](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice?view=dynamics-general-ce-9) eine Sicherheitsrolle zugewiesen wird. 

Dieses Beispiel benötigt einen weiteren Benutzer, der nicht in Ihrem System vorhanden sind. Erstellen Sie die erforderlichen Benutzer manuell in **Office 365**, um das Beispiel ohne Fehler auszuführen. Erstellen Sie für dieses Beispiel ein Benutzerprofil **wie** unten gezeigt. 

**Vorname**: Dan<br/>
Kontakt: **Nachname**<br/>
**Sicherheitsrolle**: Benutzer ohne zugewiesene Rollen<br/>
**Benutzername**: dpark@yourorg.onmicrosoft.com<br/>

Sie können das Beispiel [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssociateSecurityRoleToUser) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die [IOrganizationService.Associate](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice?view=dynamics-general-ce-9) Methoden soll in einem Szenario verwendet werden, das Daten enthält, die programmgesteuerten Zugriff auf die Metadaten und Daten einer Organisation bereitstellen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die `CreateRequiredRecords`-Methode erstellt die erforderlichen Datensätze für das Beispiel.

### <a name="demonstrate"></a>Demonstrieren

1. Die `QueryExpression` Methode ruft eine Rolle von Common Data Service ab.
2. Die `Associate` Nachricht weist die Rolle einem Benutzer zu.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
