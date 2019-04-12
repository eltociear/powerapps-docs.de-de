---
title: 'Beispiel: Freigeben von Datensätzen mithilfe von GrantAccess, ModifyAccess und RevokeAccess (Common Data Service) | Microsoft Docs'
description: 'Dieses Beispiel veranschaulicht, wie ein Datensatz mithilfe der GrantAccess-, ModifyAccess- und RevokeAcces-Message freigegeben wird.'
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
# <a name="sample-share-records-using-grantaccess-modifyaccess-and-revokeaccess-messages"></a>Beispiel: Datensätze mithilfe von GrantAccess, ModifyAccess und RevokeAccess Nachrichten teilen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-share-records-using-grantaccess-modifyaccess-revokeaccess-messages 

Change sample to make sure it works with Common Data Service
-->

Dieses Beispiel zeigt, wie ein Datensatz mit den nachfolgenden Meldungen geteilt wird:

[GrantAccessRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.grantaccessrequest?view=dynamics-general-ce-9)

[ModifyAccessRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.modifyaccessrequest?view=dynamics-general-ce-9)

[RevokeAccessRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.revokeaccessrequest?view=dynamics-general-ce-9)

Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/GrantModifyRevokeAccess) herunterladen.

Dieses Beispiel benötigt weitere Benutzer, die nicht in Ihrem System sind. Erstellen Sie die erforderlichen Benutzer manuell in **Office 365**, um das Beispiel ohne Fehler auszuführen. Für dieses Beispiel erstellen Sie 2 Benutzerprofile **wie unten dargestellt**. Ersetzen Sie `yourorg` durch den Namen Ihrer Organisation.

**Vorname**: Dan<br/>
**Nachname**: Wilson<br/>
**Sicherheitsrolle**: Stellvertretung<br/>
**Benutzername**: dwilson@yourorg.onmicrosoft.com<br/>

**Vorname**: Christen<br/>
**Nachname**: Anderson<br/>
**Sicherheitsrolle**: Stellvertretung<br/>
**Benutzername**: canderson@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Messages `GrantAccessRequest`, `ModifyAccessRequest`, `RevokeAccessRequest` sind für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthalten, die für das Gewähren, Ändern und Widerrufen des Zugriffs erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Erstellt einen eindeutigen Bezeichner für das Verhindern von Namenskonflikten.
3. Ruft den manuell in **Office 365** erstellten Benutzer für dieses Beispiel ab.
4. Ruft die Stammunternehmenseinheit für das Erstellen des Teams für das Beispiel ab.
5. `WhoAMIRequest` fordert die aktuellen Benutzerinformationen an.
6. Erstellt das Team und fügt die Benutzer zum Team hinzu. 
7. Erstellt einen Account-Datensatz und auch eine Aufgabe oder einen Brief, die bzw. der dem Account zugeordnet werden soll.

### <a name="demonstrate"></a>Demonstrieren

1. Ruft den Zugriff ab, über den der aufrufende Benutzer für den erstellten Account verfügt, und zeigt ihn an.
2. Ruft den Zugriff ab, über den der erste Benutzer für den erstellten Account verfügt, und zeigt ihn an. 
3. Die Methode `GrantAccessRequest` gewährt dem ersten Benutzer `read`-Zugriff auf den erstellten Account.
4. Die Methode `ModifyAccessRequest` gewährt dem ersten Benutzer `delete`-Zugriff auf den erstellten Account.
5. Die Methode `RevokeAccessRequest` gewährt dem ersten Benutzer `revoke`-Zugriff auf den erstellten Account.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
