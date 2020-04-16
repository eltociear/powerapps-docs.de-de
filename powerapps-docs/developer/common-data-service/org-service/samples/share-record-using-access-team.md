---
title: 'Beispiel: Freigeben eines Datensatzes mithilfe eines Zugriffsteams (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Zugriff auf einen Datensatz mithilfe eines Zugriffsteams gewährt wird.
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
ms.openlocfilehash: 2132c1a101da0402644ae00c70297c1607ffb99b
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155562"
---
# <a name="sample-share-a-record-using-an-access-team"></a>Beispiel: Freigeben eines Datensatzes mithilfe eines Zugriffsteams

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-share-record-using-access-team -->

Dieses Beispiel zeigt, wie Zugriff auf einen Datensatz mithilfe eines Zugriffsteams gewährt wird. Alle Mitglieder des Teams erhalten denselben Zugriff auf den Datensatz, der dem Team gewährt wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ShareRecordUsingAccessTeam) herunterladen.

Dieses Beispiel benötigt weitere Benutzer, die nicht in Ihrem System sind. Legen Sie die erforderlichen Benutzer manuell in **Office 365** an, um das Beispiel fehlerfrei auszuführen. Erstellen Sie für dieses Beispiel ein Benutzerprofil **wie** unten gezeigt. Ersetzen Sie `yourorg` durch den Namen Ihrer Organisation.

**Vorname**: Nancy<br/>
**Nachname**: Anderson<br/>
**Sicherheitsrolle**: Vertriebsmitarbeiter<br/>
**Benutzername**: nanderson@yourorg.onmicrosoft.com<br/>

**Vorname**: David<br/>
**Nachname**: Bristol<br/>
**Sicherheitsrolle**: Vertriebsmitarbeiter<br/>
**Benutzername**: dbristol@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Messages `AddMembersTeamRequest`, `GrantAccessRequest`, `RemoveMembersTeamRequest` sind für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthalten, die für das Hinzufügen, Gewähren und Entfernen von Mitgliedern erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Erstellt einen Test-Account-Datensatz für das Beispiel.

### <a name="demonstrate"></a>Demonstrieren

1. Ruft die Vertriebsmitarbeiter ab, die manuell in **Office 365** erstellt werden, die dem Team hinzugefügt werden.
1. `WhoAMIRequest` ruft die ID des aktuellen Benutzers und der Unternehmenseinheit ab.
1. Erstellt ein Beispielzugriffsteam. `AddMembersTeamRequest` fügt zwei Vertriebspersonen zum Zugriffsteam hinzu.
1. `GrantAccessRequest` gewährt dem Team Lese-/Schreibzugriff auf den in Setup (#setup) erstellten Account.
1. `RetrieveAndDisplayEntityAccess` ruft Entitäts-Zugriffsinformationen ab und zeigt sie an.
1. `RetrieveAndDisplayPrincipalAccess` ruft Prinzipal-Zugriffsinformationen ab und zeigt sie an.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
