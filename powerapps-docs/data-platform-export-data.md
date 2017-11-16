---
title: Importieren oder Exportieren von Daten | Microsoft-Dokumentation
description: "Importieren oder exportieren Sie eine Entität."
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: 880881b31362d38ed0d44126245dd96d2a74150f
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="import-or-export-data-from-the-common-data-service"></a>Importieren oder Exportieren von Daten aus Common Data Service
Sie können Daten auf zwei Weisen in oder aus Common Data Service verschieben:

* Wenn Sie einen einmaligen Massenimport oder -export von Daten vornehmen möchten, können Sie Microsoft Excel für mehrere Entitäten verwenden.
* Wenn Sie einen fortlaufenden Import oder Export von Daten für eine einzelne Entität zu einem anderen Dienst wie z.B. Dynamics 365 oder Salesforce oder sogar in eine Excel-Datei vornehmen möchten. können Sie [Microsoft Flow](https://flow.microsoft.com) verwenden, um diesen fortlaufenden Import oder Export einzurichten.

## <a name="import-or-export-data-once"></a>Einmaliges Importieren oder Exportieren von Daten
### <a name="import-data-from-excel"></a>Importieren von Daten aus Excel
1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com) den Bereich **Common Data Service**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entities** (Entitäten).
2. Klicken oder tippen Sie neben **Neue Entität** auf die Schaltfläche mit den drei Punkten, und klicken oder tippen Sie anschließend auf **Daten importieren**.
3. Wählen Sie die Entität aus, in die Sie Daten importieren möchten, und klicken oder tippen Sie anschließend auf **Weiter**.
4. Klicken oder tippen Sie auf **Suchen**. Wählen Sie die Datei aus, aus der Sie Daten importieren möchten.
5. Wenn der **Zuordnungsstatus** nicht **Übereinstimmung** lautet und kein grünes Häkchen angezeigt wird, müssen Sie die Zuordnung zwischen den Entitätsfeldern und den Spalten in der Excel-Datei angeben. Um die Spalten zuzuordnen:
   1. klicken oder tippen Sie auf **Zuordnung anzeigen**,
   2. wählen Sie für jedes Entitätsfeld die entsprechende Spalte in der Excel-Datei aus,
   3. klicken oder tippen Sie auf **Änderungen speichern**,
6. klicken Sie auf **Importieren**.

### <a name="export-data-to-excel"></a>Exportieren von Daten nach Excel
Sie können Daten einmalig von einer Standardentität oder einer benutzerdefinierten Entität exportieren, und Sie können Daten von mehr als einer Entität gleichzeitig exportieren. Wenn Sie Daten aus mehr als einer Entität exportieren, wird jede Entität in eine eigene Microsoft Excel-Datei exportiert.

1. Klicken oder tippen Sie auf [powerapps.com](https://web.powerapps.com) im linken Navigationsbereich auf **Entitäten**.
2. Klicken oder tippen Sie neben **Neue Entität** auf die Schaltfläche mit den drei Punkten, und klicken oder tippen Sie anschließend auf **Daten exportieren**.
3. Wählen Sie die Entitäten aus, aus der Sie Daten exportieren möchten, und klicken oder tippen Sie anschließend auf **Nach Excel exportieren**.
4. Wenn **Der Export wurde abgeschlossen** angezeigt wird, klicken oder tippen Sie auf **Exportierte Daten herunterladen**, um die Daten herunterzuladen.

## <a name="use-microsoft-flow-to-set-up-ongoing-import-or-export"></a>Verwenden von Microsoft Flow zum Einrichten eines fortlaufenden Imports oder Exports
Sie können fortlaufende Importe oder Exporte für eine einzelne Standardentität oder benutzerdefinierte Entität gleichzeitig einrichten. Sie können eine Verbindung mit u.a. den folgenden Speicherorten herstellen:

* Dynamics 365
* Salesforce
* Microsoft Excel-Dateien, die in einem beliebigen Clouddateianbieter gespeichert sind
* Einer Microsoft SQL-Datenbank, sowohl in der Cloud als auch lokal
* Einem benutzerdefinierten Connector, den Sie definieren, um eine Verbindung mit Ihren eigenen Systemen herzustellen

Wenn Sie heute Microsoft Flow zum Importieren oder Exportieren von Daten verwenden, handelt es sich dabei nicht um einen vollständigen Synchronisationsdienst. Wenn ein Objekt zu einem Dienst hinzugefügt wird, wird es in das andere System importiert. Allerdings bedeutet dies auch, dass ein Objekt, das von einem System gelöscht wird, nicht auch vom anderen System gelöscht wird.

Wie der Import eingerichtet werden muss, hängt davon ab, ob bereits eine Vorlage für das Objekt, das Sie importieren möchten, vorhanden ist. Wenn eine Vorlage vorhanden ist, können Sie sie so einrichten, dass sie Daten von einem in ein anderes System kopiert. Weitere Informationen finden Sie unter [Erstellen eines Flows, der den Microsoft Common Data Service verwendet](https://flow.microsoft.com/documentation/common-data-model-intro/). Wenn aber keine solche Vorlage vorhanden ist, müssen Sie einen Flow erstellen, der die Datenbank verwenden kann. Weitere Informationen finden Sie unter [Erstellen eines Flows in Microsoft Flow](https://flow.microsoft.com/documentation/get-started-logic-flow/).

