---
title: Erstellen einer Geschäftsregel in Common Data Service (CDS) für Apps | Microsoft-Dokumentation
description: Schrittanleitungen zum Erstellen einer Geschäftsregel in Common Data Service (CDS) für Apps.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: 13e00081ce01b44feeea6fc1d6fff9556c020298
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34168272"
---
# <a name="create-a-business-rule"></a>Erstellen einer Geschäftsregel

Sie können Geschäftsregeln und -empfehlungen erstellen, um Logiken und Validierungen anzuwenden, ohne Code zu schreiben oder Plug-Ins zu erstellen.  Geschäftsregeln stellen eine einfache Schnittstelle bereit, um sich schnell ändernde und häufig verwendete Regeln zu implementieren und zu verwalten. 
  
Indem Sie Bedingungen und Aktionen kombinieren, können Sie folgende Vorgänge mit Geschäftsregeln durchführen:  
  
* Festlegen von Feldwerten  
* Löschen von Feldwerten  
* Festlegen von Anforderungsebenen für Felder  
* Anzeigen oder Ausblenden von Feldern  
* Aktivieren oder Deaktivieren von Feldern  
* Überprüfen von Daten und Anzeigen von Fehlermeldungen  
* Erstellen von Geschäftsempfehlungen, die auf Business Intelligence basieren  
  
## <a name="differences-between-canvas-and-model-driven-apps"></a>Unterschiede zwischen Canvas-Apps und modellgesteuerten Apps

Modellgesteuerte Apps können alle Aktionen verwenden, die für Geschäftsregeln verfügbar sind. Derzeit sind jedoch nicht alle Aktionen für Geschäftsregeln in Canvas-Apps verfügbar. Folgende Aktionen sind in Canvas-Apps **nicht** verfügbar:

* Anzeigen oder Ausblenden von Feldern  
* Aktivieren oder Deaktivieren von Feldern  
* Erstellen von Geschäftsempfehlungen, die auf Business Intelligence basieren  

## <a name="prerequisites"></a>Voraussetzungen
Sie müssen in eine [Umgebung](../canvas-apps/working-with-environments.md) wechseln, in der Sie Entitäten erstellen und bearbeiten können, um diesem Artikel zu folgen.

## <a name="create-a-business-rule"></a>Erstellen einer Geschäftsregel
  
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com) an, und klicken oder tippen Sie am linken Rand auf den Pfeil nach unten für **Daten**.

2. Klicken oder tippen Sie in der angezeigten Liste auf **Entitäten**.
  
3. Öffnen Sie die Entität, für die Sie die Geschäftsregel erstellen möchten (z.B. die Entität **Account**), und klicken Sie dann auf die Registerkarte **Geschäftsregeln**.  

4. Klicken Sie auf **Neu**.  
  
    Das Fenster des Geschäftsregel-Designers wird mit einer einzelnen Bedingung geöffnet, die bereits für Sie erstellt wurde. Jede Regel beginnt mit einer Bedingung. Die Geschäftsregel führt auf Grundlage dieser Bedingung eine oder mehrere Aktionen durch.  

    > [!TIP]
    > Wenn Sie eine vorhandene Geschäftsregel ändern möchten, müssen Sie diese zuvor deaktivieren.  
  
5. Fügen Sie im Feld „Beschreibung“ in der oberen linken Ecke des Fensters nach Belieben eine Beschreibung hinzu.
  
6. Legen Sie den Bereich folgendermaßen fest:  
  
    |||  
    |-|-|  
    |**Ausgewähltes Element**|**Festgelegter Bereich**|  
    |**Entität**|Modellgesteuerte Formulare und Server|  
    |**Alle Formulare**|Modellgesteuerte Formulare|  
    |Bestimmte Formulare (z.B. das **Account**-Formular)|Nur dieses modellgesteuerte Formular|  

    > [!TIP]
    > Wenn Sie eine Canvas-App erstellen, müssen Sie „Entität“ als Bereich verwenden.
  
7. **Hinzufügen von Bedingungen:** So fügen Sie Ihrer Geschäftsregel weitere Bedingungen hinzu:  
  
    1. Ziehen Sie die Komponente **Bedingung** von der Registerkarte **Komponenten** zu einem Pluszeichen im Designer.  
  
        ![Eine Bedingung zu einer Geschäftsregel hinzufügen](./media/data-platform-cds-create-business-rule/add-condition-business-rule.png "Add a condition in a business rule")  
  
    2. Klicken Sie zum Festlegen von Eigenschaften für die Bedingung auf die Komponente **Bedingung** im Fenster des Designers, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften** fest, die sich auf der rechten Seite des Bildschirms befindet. Während Sie die Eigenschaften festlegen, erstellt Common Data Service einen Ausdruck im unteren Bereich der Registerkarte **Eigenschaften**.  
  
    3. Klicken Sie zum Hinzufügen einer zusätzlichen Klausel (eine AND- oder OR-Klausel) zur Bedingung auf in der Registerkarte **Eigenschaften** auf **Neu**, um eine neue Regel zu erstellen. Legen Sie anschließend die Eigenschaften für diese Regel fest. Im Feld **Regellogik** können Sie angeben, ob die neue Regel als AND- oder OR-Klausel hinzugefügt werden soll.  
  
        ![Eine neue Regel zu einer Bedingung hinzufügen](./media/data-platform-cds-create-business-rule/add-new-rule-condition.png "Add a new rule to a condition")  
  
    4. Wenn Sie mit dem Festlegen der Eigenschaften für die Bedingung fertig sind, klicken Sie auf **Übernehmen**.  
  
8. **Hinzufügen von Aktionen:** So fügen Sie eine Aktion hinzu:  
  
    1. Ziehen Sie eine der Aktionskomponenten von der Registerkarte **Komponenten** zu einem Pluszeichen neben der Komponente **Bedingung**. Ziehen Sie die Aktion zu einem Pluszeichen neben einem Häkchen, wenn Sie möchten, dass die Geschäftsregel angewendet wird, wenn die Bedingung erfüllt ist. Ziehen Sie sie zu einem Pluszeichen neben einem X-Symbol, wenn Sie möchten, dass die Geschäftsregel angewendet wird, wenn die Bedingung nicht erfüllt ist.
  
        ![Eine Aktion zu einer Geschäftsregel ziehen](./media/data-platform-cds-create-business-rule/drag-an-action-business-rule.png "Drag an action to a business rule")  
  
    2. Klicken Sie zum Festlegen von Eigenschaften für die Aktion auf die Komponente **Aktion** im Fenster des Designers, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften** fest.  
  
    3. Wenn Sie mit dem Festlegen der Eigenschaften fertig sind, klicken Sie auf **Übernehmen**.  
  
9. **Hinzufügen einer Geschäftsempfehlung (nur für modellgesteuerte Apps):** So fügen Sie eine Geschäftsempfehlung hinzu:  
  
    1. Ziehen Sie die Komponente **Empfehlung** von der Registerkarte **Komponenten** zu einem Pluszeichen neben einer **Bedingung**-Komponente. Ziehen Sie die Komponente **Empfehlung** zu einem Pluszeichen neben einem Häkchen, wenn Sie möchten, dass die Geschäftsregel angewendet wird, wenn die Bedingung erfüllt ist. Ziehen Sie sie zu einem Pluszeichen neben einem X-Symbol, wenn Sie möchten, dass die Geschäftsregel angewendet wird, wenn die Bedingung nicht erfüllt ist.  
  
    2. Klicken Sie zum Festlegen von Eigenschaften für die Empfehlung auf die Komponente **Empfehlung** im Fenster des Designers, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften** fest.  
  
    3. Wenn Sie weitere Aktionen zur Empfehlung hinzufügen möchten, ziehen Sie diese aus der Registerkarte **Komponenten**, und legen Sie dann Eigenschaften für jede Aktion in der Registerkarte **Eigenschaften** fest.  
  
        > [!NOTE]
        >  Wenn Sie eine Empfehlung erstellen, fügt Common Data Service standardmäßig eine einzelne Aktion hinzu. Klicken Sie in der Komponente **Empfehlung** auf **Details**, um alle Aktionen in einer Empfehlung anzuzeigen.  
  
    4. Wenn Sie mit dem Festlegen der Eigenschaften fertig sind, klicken Sie auf **Übernehmen**.  
  
10. Klicken Sie in der Aktionsleiste auf **Überprüfen**, um eine Geschäftsregel zu überprüfen.  
  
11. Klicken Sie in der Aktionsleiste auf **Speichern**, um eine Geschäftsregel zu speichern.  
12. Wenn Sie eine Geschäftsregel aktivieren möchten, wählen Sie diese im Fenster des Projektmappen-Explorers aus, und klicken Sie dann auf **Aktivieren**. Sie können keine Geschäftsregel über das Fenster des Designers aktivieren.  
  
    > [!TIP]
    >  Hier sind einige Tipps, die Sie beachten sollten, wenn Sie an Geschäftsregeln im Fenster des Designers arbeiten:  
    >   
    > - Klicken Sie in der Aktionsleiste auf **Momentaufnahme**, um eine Momentaufnahme aller Elemente im Fenster „Geschäftsregel“ zu erstellen. Dies ist beispielsweise nützlich, wenn Sie Kommentare zur Geschäftsregel von einem Teammitglied freigeben und abrufen möchten.  
    > - Verwenden Sie die Minikarte, um schnell zu verschiedenen Teilen des Prozesses zu navigieren. Dies ist nützlich, wenn der Prozess kompliziert ist und über den Bildschirmbereich hinausgeht.  
    > - Während Sie Bedingungen, Aktionen und Geschäftsempfehlungen zu Ihrer Geschäftsregel hinzufügen, erstellt Common Data Service den Code für die Geschäftsregel im unteren Bereich des Designer-Fensters. Dieser Code ist schreibgeschützt.  
  
## <a name="localize-error-messages-used-in-business-rules"></a>Lokalisieren von Fehlermeldungen, die in Geschäftsregeln verwendet werden  
 Wenn in Ihrer Organisation mehr als eine Sprache verwendet wird, sollten Sie alle festgelegten Fehlermeldungen lokalisieren. Jedes Mal, wenn Sie eine Meldung festlegen, wird eine Bezeichnung vom System generiert. Wenn Sie die Übersetzungen Ihrer Organisation exportieren, können Sie lokalisierte Versionen zu Ihren Meldungen hinzufügen und diese Bezeichnungen dann zurück in Common Data Service importieren. Dadurch können die Personen, die andere Sprachen als die Standardsprache verwenden, die übersetzten Meldungen anzeigen.  
  