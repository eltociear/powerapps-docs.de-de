---
title: Erstellen einer segmentierten Lösungen mit Power Apps | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Workflowaufträge nutzen, um Ihre Lösungen zu aktualisieren
ms.custom: ''
ms.date: 02/04/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 5c05f683-e1bd-4885-be23-b6973128773f
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 50e9e467727ab637d46dbc82ad0a313b5fe817db
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341565"
---
# <a name="create-segmented-solutions"></a>Segmentierte Lösungen erstellen 
Verwenden Sie die Lösungssegmentierung, damit Sie nur Entitätskomponenten einbeziehen, die beim Verteilen von Lösungsaktualisierungen aktualisiert werden. Mit der Lösungssegmentierung können Sie Lösungen mit ausgewählten Entitätsanlagen exportieren, beispielsweise Entitätsfelder, Formulare oder Ansichten, anstatt gesamte Entitäten mit allen Anlagen. Um eine segmentierte Lösung zu erstellen, können Sie die **Lösungen** im Beeich Power Apps verwenden. Weitere Informationen: [Verwenden von segmentierten Lösungen](/power-platform/alm/segmented-solutions-alm)

## <a name="create-a-segmented-solution-with-entity-assets"></a>Erstellen Sie eine segmentierte Lösung mit Entitäts-Assets 
 Um eine segmentierte Lösung zu erstellen, starten Sie mit dem Erstellen einer nicht verwalteten Lösung und fügen Sie die aktualisierte Komponenten hinzu. Die assistentenähnliche Einrichtung führt Sie Schritt für Schritt durch den Prozess des Hinzufügens von Entitäts-Assets. 

Stellen Sie sich beispielsweise vor, Sie haben eine neue benutzerdefinierte Entität erstellt, die in keiner anderen Umgebung mit dem Namen vorhanden ist *Benutzerdefinierte Entität* und die auch ein neues Feld mit dem Namen *topten* für die Konteneinheit hinzufügte. Führen Sie die folgenden Schritte aus, um eine segmentierte Lösung zu erstellen. 
  
1. Gehen Sie zum Portal Power Apps und wählen Sie dann **Lösungen**.  
  
2.  Wählen Sie **Neue Lösung** und erstellen Sie eine Lösung. Geben Sie die Informationen in den erforderlichen Feldern ein. Wählen Sie **Erstellen** aus.  
  
3.  Öffnen Sie die von Ihnen erstellte Lösung. Wählen Sie in der Befehlsleiste **Vorhandenes hinzufügen** und wählen Sie dann **Entität**.  
  
4.  Im Bereich **Bestehende Entitäten hinzufügen** wählen Sie eine oder mehrere Entitäten aus, die Sie der Lösung hinzufügen möchten. Wählen Sie zum Beispiel **Konto** und **Benutzerdefinierte Entität**. Wählen Sie **Weiter**.  

5.  Im Bereich **Entitäten auswählen** können Sie aus den einzubeziehenden Assets wählen: 
    - **Alle Komponenten einbeziehen**. Diese Option umfasst alle Komponenten *und* die mit der Entität verbundenen Metadaten. Es kann andere Entitäten oder Entitätskomponenten wie z. B. Geschäftsprozessflows, Berichte, Verbindungen und Warteschlangen enthalten. 
    - **Einschließen der Metadaten der Entität**. Diese Option umfasst *nur* die mit der Entität verbundenen Metadaten. Zu den Metadaten gehören die Attribute der Entitäten, wie z. B. Auditierung, Dublettenerkennung oder Änderungsverfolgung. 
    - **Komponenten auswählen**. Mit dieser Option können Sie jede Komponente, die mit der Entität verknüpft ist, wie Felder, Beziehungen, Geschäftsregeln, Ansichten, Formulare und Diagramme, einzeln auswählen. 
    - Keine Komponenten einbinden. 

      Für dieses Beispiel, weil *Benutzerdefinierte Entität* nie in die Zielumgebung importiert wurde neben der **Benutzerdefinierten Entität**, wählen Sie **Schließen Sie alle Komponenten ein**. Unter **Konto**, wählen Sie **Komponenten auswählen**.  
      > [!div class="mx-imgBorder"] 
      > ![Vorhandene Entitäten hinzufügen ](media/add-existing-entities1.png)
  
6.  Da nur das *topten* benutzerdefinierte Feld neu für die Kontoentität ist, wählen Sie **Top Ten** und dann **Hinzufügen** aus.  
     > [!div class="mx-imgBorder"] 
     > ![Entitätskomponenten auswählen](media/add-existing-entities2.png)

7. Wählen sie **hinzufügen**, um die Komponenten der Lösung hinzuzufügen. 

### <a name="create-a-segmented-solution-using-solution-explorer"></a>Erstellen Sie eine segmentierte Lösung mit dem Lösungsexplorer  
Folgende Abbildungen stellen ein Beispiel der Erstellung einer segmentierten Lösung bereit, indem Entitätsanlagen von den Entitäten `Account`, `Case` sowie `Contact` ausgewählt werden.  

> [!NOTE]
> Die Fallentität ist bei einigen Dynamics 365-Anwendungen, wie z. B. beim Dynamics 365 Customer Service, enthalten. 
  
Beginnen Sie mit dem Öffnen einer nicht verwalteten Lösung, die Sie erstellt haben. Wählen Sie die Komponente **Entität**.  

 > [!div class="mx-imgBorder"] 
 > ![Fügen Sie vorhandene Ressourcen hinzu.](media/solution-segmentation-add-existing-resources-admin.png "Fügen Sie vorhandene Ressourcen hinzu.")  
  
 Wählen Sie dann die Lösungskomponenten aus.  
  
 ![Wählen Sie die Lösungskomponenten aus.](media/solution-segmentation-select-components-admin.png "Wählen Sie die Lösungskomponenten aus.")  
  
 Folgen Sie dem Assistenten. Wählen Sie in Schritt 1 in alphabetischer Reihenfolge die Anlagen für die erste Entität, der `Account`-Entität, wie hier gezeigt, aus.  
  
 ![Starten Sie den Assistenten.](media/solution-segmentation-wizard-starts-admin.png "Starten Sie den Assistenten.")  
  
 Öffnen Sie die Registerkarte **Felder** und wählen Sie das Feld **Firmennummer** aus.  
  
 ![Wählen Sie die Entitätsanlagen der Firma aus.](media/solution-segmentation-select-account-assets-admin.png "Wählen Sie die Entitätsanlagen der Firma aus.")  
  
 Fügen Sie in Schritt 2 für die Entität **Anfrage** alle Anlagen hinzu.  
  
 ![Wählen Sie die Entitätsanlagen des Falls aus.](media/solution-segmentation-select-case-assets-admin.png "Wählen Sie die Entitätsanlagen des Falls aus.")  
  
 Fügen Sie im Schritt 3 das Feld **Jahrestag** für die Entität **Kontakt** hinzu.  
  
 ![Wählen Sie die Entitätsanlagen des Kontakts aus.](media/solution-segmentation-select-contact-assets-admin.png "Wählen Sie die Entitätsanlagen des Kontakts aus.")  
  
 Daher enthält die segmentierte Lösung, die erstellt wird, drei Entitäten, nämlich `Account`, `Case` und `Contact`. Jede Entität enthält ausschließlich Anlagen, die ausgewählt waren.  
  
 > [!div class="mx-imgBorder"] 
 > ![Lösung mit Entitäten.](media/solution-segmentation-solution-entities-admin.png "Lösung mit Entitäten.")  
  
  
### <a name="see-also"></a>Siehe auch  
 [Überblick über Lösungen](solutions-overview.md)


