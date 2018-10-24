---
title: Erstellen von Geschäftsregeln und -empfehlungen für modellgesteuerte Apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
caps.latest.revision: 31
author: Mattp123
ms.author: matp
manager: kvivek
tags:
- PowerApps maker portal impact
ms.openlocfilehash: c1a132648a63845c42cde8a80636d0e87e10a328
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39685233"
---
# <a name="tutorial-create-business-rules-and-recommendations-to-apply-logic-in-a-model-driven-app-form"></a>Tutorial: Erstellen von Geschäftsregeln und -empfehlungen zur Anwendung einer Logik in einem modellgesteuerten App-Formular

In diesem Tutorial erfahren Sie, wie Geschäftsregeln und -empfehlungen erstellt werden, um eine Formularlogik anzuwenden, ohne JavaScript-Code schreiben oder Plug-Ins erstellen zu müssen.  Geschäftsregeln stellen eine einfache Schnittstelle bereit, um sich schnell ändernde und häufig verwendete Regeln zu implementieren und zu verwalten. Sie können auf Haupt- und Schnellerfassungsformulare angewendet und in PowerApps-Apps, Dynamics 365 Customer Engagement-Webanwendungen, Dynamics 365 für Tablets und Dynamics 365 für Outlook (Online- oder Offlinemodus) verwendet werden.  
  
 Indem Sie Bedingungen und Aktionen kombinieren, können Sie folgende Vorgänge mit Geschäftsregeln durchführen:  
  
-   Festlegen von Feldwerten  
  
-   Löschen von Feldwerten  
  
-   Festlegen von Anforderungsebenen für Felder  
  
-   Anzeigen oder Ausblenden von Feldern  
  
-   Aktivieren oder Deaktivieren von Feldern  
  
-   Überprüfen von Daten und Anzeigen von Fehlermeldungen  
  
-   Erstellen von Geschäftsempfehlungen, die auf Business Intelligence basieren  
  
## <a name="create-a-business-rule-or-business-recommendation"></a>Erstellen einer Geschäftsregel oder Geschäftsempfehlung
  
1. Öffnen Sie den [Projektmappen-Explorer](advanced-navigation.md#solution-explorer).  
  
2.  Öffnen Sie die Entität, für die Sie die Geschäftsregel erstellen möchten (z.B. die Entität **Account**), und doppelklicken Sie dann auf **Geschäftsregeln**.  
  
 ![Erstellen einer Geschäftsregel in der Standardlösung](media/create-business-rule-the-default-solution.png "Erstellen einer Geschäftsregel in der Standardlösung")  
  
3.  Wählen Sie **Neu** aus.  
  
     Das Fenster des Geschäftsregel-Designers wird mit einer einzelnen Bedingung geöffnet, die bereits für Sie erstellt wurde. Jede Regel beginnt mit einer Bedingung. Die Geschäftsregel führt auf Grundlage dieser Bedingung eine oder mehrere Aktionen durch.  
  
 ![Fenster zum Entwerfen einer Geschäftsregel](media/business-rules-design-window.png "Fenster zum Entwerfen einer Geschäftsregel")  
  
   > [!TIP]
> Wenn Sie eine vorhandene Geschäftsregel ändern möchten, müssen Sie diese zuvor deaktivieren.

4.  Fügen Sie im Feld „Beschreibung“ in der oberen linken Ecke des Fensters nach Belieben eine Beschreibung hinzu.  
  
5.  Legen Sie den Bereich folgendermaßen fest:  
  
    |||  
    |-|-|  
    |**Ausgewähltes Element**|**Festgelegter Bereich**|  
    |**Entität**|Alle Formulare und Server|  
    |**Alle Formulare**|Alle Formulare|  
    |Bestimmte Formulare (z.B. das **Account**-Formular)|Nur dieses Formular|  
  
6. **Hinzufügen von Bedingungen:** So fügen Sie Ihrer Geschäftsregel weitere Bedingungen hinzu:  
  
    1.  Ziehen Sie die Komponente **Bedingung** von der Registerkarte **Komponenten** zu einem Pluszeichen im Designer.  
  
        ![Eine Bedingung zu einer Geschäftsregel hinzufügen](media/add-condition-business-rule.png "Add a condition in a business rule")  
  
    2.  Klicken Sie zum Festlegen von Eigenschaften für die Bedingung auf die Komponente **Bedingung** im Fenster des Designers, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften** fest, die sich auf der rechten Seite des Bildschirms befindet. Während Sie die Eigenschaften festlegen, wird im unteren Bereich der Registerkarte **Eigenschaften** ein Ausdruck erstellt.  
  
    3.  Klicken Sie zum Hinzufügen einer zusätzlichen Klausel (eine AND- oder OR-Klausel) zur Bedingung auf in der Registerkarte **Eigenschaften** auf **Neu**, um eine neue Regel zu erstellen. Legen Sie anschließend die Eigenschaften für diese Regel fest. Im Feld **Regellogik** können Sie angeben, ob die neue Regel als AND- oder OR-Klausel hinzugefügt werden soll.  
  
        ![Eine neue Regel zu einer Bedingung hinzufügen](media/add-new-rule-condition.png "Add a new rule to a condition")  
  
    4.  Wenn Sie mit dem Festlegen der Eigenschaften für die Bedingung fertig sind, klicken Sie auf **Übernehmen**.  
  
7. **Hinzufügen von Aktionen:** So fügen Sie eine Aktion hinzu:  
  
    1.  Ziehen Sie eine der Aktionskomponenten von der Registerkarte **Komponenten** zu einem Pluszeichen neben der Komponente **Bedingung**. Ziehen Sie die Aktion zu einem Pluszeichen neben einem Häkchen, wenn Sie möchten, dass die Geschäftsregel angewendet wird, wenn die Bedingung erfüllt ist. Ziehen Sie sie zu einem Pluszeichen neben einem X-Symbol, wenn Sie möchten, dass die Geschäftsregel angewendet wird, wenn die Bedingung nicht erfüllt ist.  
  
        ![Eine Aktion zu einer Geschäftsregel ziehen](media/drag-an-action-business-rule.png "Drag an action to a business rule")  
  
    2.  Klicken Sie zum Festlegen von Eigenschaften für die Aktion auf die Komponente **Aktion** im Fenster des Designers, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften** fest.  
  
    3.  Wenn Sie mit dem Festlegen der Eigenschaften fertig sind, klicken Sie auf **Übernehmen**.  
  
8. **Fügen Sie eine Geschäftsempfehlung hinzu.** So fügen Sie eine Geschäftsempfehlung hinzu:  
  
    1.  Ziehen Sie die Komponente **Empfehlung** von der Registerkarte **Komponenten** zu einem Pluszeichen neben einer **Bedingung**-Komponente. Ziehen Sie die Komponente **Empfehlung** zu einem Pluszeichen neben einem Häkchen, wenn Sie möchten, dass die Geschäftsregel angewendet wird, wenn die Bedingung erfüllt ist. Ziehen Sie sie zu einem Pluszeichen neben einem X-Symbol, wenn Sie möchten, dass die Geschäftsregel angewendet wird, wenn die Bedingung nicht erfüllt ist.  
  
    2.  Klicken Sie zum Festlegen von Eigenschaften für die Empfehlung auf die Komponente **Empfehlung** im Fenster des Designers, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften** fest.  
  
    3.  Wenn Sie weitere Aktionen zur Empfehlung hinzufügen möchten, ziehen Sie diese aus der Registerkarte **Komponenten**, und legen Sie dann Eigenschaften für jede Aktion in der Registerkarte **Eigenschaften** fest.  
  
        > [!NOTE]
        >  Beim Erstellen einer Empfehlung wird automatisch eine Aktion hinzugefügt. Klicken Sie in der Komponente **Empfehlung** auf **Details**, um alle Aktionen in einer Empfehlung anzuzeigen.  
  
    4.  Wenn Sie mit dem Festlegen der Eigenschaften fertig sind, klicken Sie auf **Übernehmen**.  
  
9. Klicken Sie in der Aktionsleiste auf **Überprüfen**, um eine Geschäftsregel zu überprüfen.  
  
10. Klicken Sie in der Aktionsleiste auf **Speichern**, um eine Geschäftsregel zu speichern.  
  
11. Wenn Sie eine Geschäftsregel aktivieren möchten, wählen Sie diese im Fenster des Projektmappen-Explorers aus, und klicken Sie dann auf **Aktivieren**. Sie können keine Geschäftsregel über das Fenster des Designers aktivieren.  
  
> [!TIP]
>  Hier sind einige Tipps, die Sie beachten sollten, wenn Sie an Geschäftsregeln im Fenster des Designers arbeiten:  
>   
> - Klicken Sie in der Aktionsleiste auf **Momentaufnahme**, um eine Momentaufnahme aller Elemente im Fenster „Geschäftsregel“ zu erstellen. Dies ist beispielsweise nützlich, wenn Sie Kommentare zur Geschäftsregel von einem Teammitglied freigeben und abrufen möchten.  
> - Verwenden Sie die Minikarte, um schnell zu verschiedenen Teilen des Prozesses zu navigieren. Dies ist nützlich, wenn der Prozess kompliziert ist und über den Bildschirmbereich hinausgeht.  
> - Während Sie Bedingungen, Aktionen und Geschäftsempfehlungen zu Ihrer Geschäftsregel hinzufügen, wird der Code für die Geschäftsregel erstellt und im unteren Bereich des Designer-Fensters angezeigt. Dieser Code ist schreibgeschützt.  
  
<a name="BKMK_LocalizingErrorMessages"></a>   
## <a name="localize-error-messages-used-in-business-rules"></a>Lokalisieren von Fehlermeldungen, die in Geschäftsregeln verwendet werden  
 Wenn in Ihrer Organisation mehr als eine Sprache verwendet wird, sollten Sie alle festgelegten Fehlermeldungen lokalisieren. Jedes Mal, wenn Sie eine Meldung festlegen, wird eine Bezeichnung vom System generiert. Wenn Sie die Übersetzungen Ihrer Organisation exportieren, können Sie lokalisierte Versionen zu Ihren Meldungen hinzufügen und diese Bezeichnungen dann zurück in das System importieren. Dadurch können die Personen, die andere Sprachen als die Standardsprache verwenden, die übersetzten Meldungen anzeigen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Create custom business logic through processes (Erstellen einer benutzerdefinierten Geschäftslogik durch Prozesse)](guide-staff-through-common-tasks-processes.md)   
 [Erstellen eines Geschäftsprozessflusses](/flow/create-business-process-flow)   

