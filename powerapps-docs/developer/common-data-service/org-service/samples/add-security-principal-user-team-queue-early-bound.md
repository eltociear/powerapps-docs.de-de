---
title: 'Beispiel: Hinzufügen eines Sicherheitsprinzipals (Benutzer oder Team) zu einer Warteschlange (Common Data Service) | Microsoft-Dokumentation'
description: Hinzufügen eines Sicherheitsprinzipals zu einer Warteschlange
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: c41dfe21ad8a706b5502b637e0a9a3c68317c6a0
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934438"
---
# <a name="sample-add-a-security-principal-user-or-team-to-a-queue"></a>Beispiel: Hinzufügen eines Sicherheitsprinzipals (Benutzer oder Team) zu einer Warteschlange 

Dieses Beispiel zeigt, wie einem Benutzer oder Team Zugriff auf eine Warteschlange gewährt wird. Die [AddPrincipalToQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.addprincipaltoqueuerequest?view=dynamics-general-ce-9) fügt den angegebenen Prinzipal der Liste der Warteschlangenmitglieder hinzu. Wenn der angegebene Sicherheitsprinzipal ein Team ist, wird jedes Teammitglied der Warteschlange hinzugefügt. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AddSecurityPrincipalToQueue) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `AddPrincipalToQueueRequest`-Nachricht ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die benötigt werden, um den angegebenen Prinzipal zur Liste der Warteschlangenmitglieder hinzuzufügen. Wenn der Prinzipal ein Team ist, fügen Sie jedes Teammitglied zur Warteschlange hinzu.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die `Queue`-Methode erstellt eine Warteschlangeninstanz und legt deren Eigenschaftswerte fest. Die zurückgegebenen GUIDs werden in einer Variablen gespeichert.
3. Die `QueryExpression` ruft die Standardunternehmenseinheit für die Erstellung eines Teams und der Rolle ab.
4. Erstellt ein neues Beispielsteam und eine neue -Rolle, die für das Beispiel benötigt werden.
5. Ruft `prvReadQueue` und `prvAppendToQueue` -Rechte ab.
6. Die `AddPrivilegeRoleRequest`-Methode fügt der Beispielrolle die `prvReadQueue` und `prvAppendToQueue`-Rechte hinzu.

### <a name="demonstrate"></a>Demonstrieren

Die `AddPrincipalToQueueRequest`-Methode fügt das Team der Warteschlange hinzu.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
