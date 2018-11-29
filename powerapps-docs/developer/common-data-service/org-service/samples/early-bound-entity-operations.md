---
title: 'Beispiel: Erstellen und Aktualisieren von verknüpften Datensätzen (früher gebunden) (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel veranschaulicht die Erstellungs-, Abruf-, Aktualisierungs- und Löschungsvorgänge für ein Konto mithilfe der Klasse mit früher Bindung. '
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
# <a name="sample-early-bound-entity-operations"></a>Beispiel: Früh gebundene Entitätsvorgänge

<!-- sample-associate-records-early-bound.md 

sample-create-update-records-related-records-early-bound.md

show deep insert equivalent

sample-initialize-record-existing-record.md

https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/sample-create-retrieve-update-delete-records-early-bound

-->

Dieses Beispiel veranschaulicht die Erstellungs-, Abruf-, Aktualisierungs- und Löschungsvorgänge für ein Konto mithilfe der Klasse mit früher Bindung. Das Beispiel verwendet die folgenden allgemeinen Methoden:

- <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>  
  
-   <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*>  
  
-   <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>  
  
-   <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*>  

Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/EarlyBoundEntityOperations) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IOrganizationService`-Nachricht soll in einem Szenario verwendet werden, wo sie programmgesteuerten Zugriff auf die Metadaten und Daten einer Organisation bereitstellt.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft die aktuelle Version der Organisation.
1. Erstellt die Beispielfirmendatensätze, die für dieses Beispiel benötigt werden.

### <a name="demonstrate"></a>Demonstrieren

1. Instanziiert ein Kontoobjekt.
1. Ruft den Account mit den Attributen ab.
1. Ruft die Versionsnummer des Accounts ab.
1. Aktualisiert den Account mit dem Attribut des Codes postal1. 


### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.

