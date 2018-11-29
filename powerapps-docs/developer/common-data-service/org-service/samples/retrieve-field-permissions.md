---
title: 'Beispiel: Abrufen von Feldberechtigungen (Common Data Service for Apps) | Microsoft Docs'
description: 'In diesem Beispiel wird gezeigt, wie gesicherte Felder für einen Benutzer abgerufen werden'
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
# <a name="sample-retrieve-field-permissions"></a>Beispiel: Abrufen von Feldberechtigungen

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-retrieve-field-permissions -->

Dieses Beispiel zeigt das Abrufen von gesicherten Feldern für einen Benutzer gemäß den Schritten, die unter [Feldsicherheitsentitäten](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/field-security-entities) erläutert werden. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveFieldPermission) herunterladen.

Dieses Beispiel benötigt weitere Benutzer, die nicht in Ihrem System sind. Erstellen Sie die erforderlichen Benutzer manuell in **Office 365**, um das Beispiel ohne Fehler auszuführen. Erstellen Sie für dieses Beispiel ein Benutzerprofil **wie** unten gezeigt. Ersetzen Sie `yourorg` durch den Namen Ihrer Organisation.

**Vorname**: Samantha <br/>
**Nachname**: Smith<br/>
**Sicherheitsrolle**: Marketing Manager<br/>
**Benutzername**: ssmith@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `FieldPermission`-Klasse ist in einem Szenario zu verwenden, in dem sie die Daten enthält, durch die die möglichen Feldberechtigungstypen definiert werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Ruft die Benutzerinformationen ab, die Sie manuell in **Office 365** erstellt haben.
1. Die Methode `QueryExpression` ruft die Sicherheitsrolle ab, die erforderlich ist, um den Benutzer zuzuweisen.
1. Die Methode `Team` instanziiert einen Teamentitätsdatensatz und legt seine Eigenschaftswerte fest.

### <a name="demonstrate"></a>Demonstrieren

1. Die Methode `FieldSecurityProfile` erstellt ein Feldsicherheitsprofil.
1. Die Methode `AssociateRequest` fügt Team und Benutzer zum Profil hinzu.
1. Die Methode `CreateEntityRequest` erstellt eine neue benutzerdefinierte Aktivitätsentität für das Beispiel.
1. Die Methode `RolePrivilege` fügt Berechtigungen für die neue benutzerdefinierte Entität hinzu.
1. Die Methode `AddPrivilegeRoleRequest` erstellt die Methode `RolePrivilege` und führt sie aus.
1. Die Methode `FieldPermission` erstellt ein Feldberechtigungsobjekt für die Identität.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
