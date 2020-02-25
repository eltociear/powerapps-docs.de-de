---
title: Verwenden Sie segmentierte Lösungen mit Power Apps | Microsoft Docs
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
ms.openlocfilehash: d13eafa6858a6eec86de2db08504575c7fab9acd
ms.sourcegitcommit: 60a721432b3fa2abd14ccb3bd16a6b34e13ada85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2020
ms.locfileid: "3026367"
---
# <a name="use-segmented-solutions"></a>Segmentierte Lösungen verwenden 

Um genauere Kontrolle darüber zu erlangen, welche Elemente in Patches und Lösungen verteilt werden, verwenden Sie Lösungssegmentierung. Abhängig von der Komplexität Ihrer Anwendung kann die Segmentierung der Lösung so einfach sein wie alles in einer einzigen Lösung zur Segmentierung nach Komponententyp, z. B. Entitäten in einer Lösung, Canvas-Anwendungen in einer anderen und Plugins in einer dritten. Um die segmentierten Lösungen zu erstellen, können Sie den Lösungsbereich in Power Apps verwenden, ohne Code zu schreiben.  

Es gibt drei Hauptmöglichkeiten zur Segmentierung von Lösungen: 
- Segmentieren Sie Lösungen während der Erstellung Ihrer Anwendung. Dazu fügen Sie spezifische Komponenten hinzu, um zu steuern, was in die Lösung einfließt. Mehr Informationen: [Eine segmentierte Lösung mit Entitätsvermögen erstellen](#create-a-segmented-solution-with-entity-assets)
- Erstellen Sie segmentierte Lösungen, um kleinere Aktualisierungen einer Lösung zu erstellen und zu veröffentlichen. Dazu klonen Sie einen Patch. Weitere Informationen: [Lösungsflicken erstellen](#create-a-solution-patch)
- Erstellen Sie segmentierte Lösungen, um größere Updates einer Lösung zu erstellen und zu veröffentlichen. Dazu klonen Sie die Lösung. Mehr Informationen: [Klonen einer Lösung](#clone-a-solution)

## <a name="when-to-plan-for-segmentation"></a>Wann ist die Segmentierung zu planen? 
Ähnlich wie bei der Planung, wie Sie die Daten modellieren, die in Ihre Anwendung eingehen, sollte die Planung für die Segmentierung in Betracht gezogen werden, bevor Sie Ihre Lösung verteilen. Die Segmentierung von Lösungen aus einer einzelnen Lösung in mehrere Lösungen einen Monat oder zwei Jahre nach der Erstellung der ersten Anwendung kann komplex sein und kann Probleme verursachen.  

## <a name="solutions-as-patches"></a>Lösungen als Patches
Mit der Lösungssegmentierung können Sie Lösungs-Patches mit ausgewählten Entitäts-Assets wie Entitätsfeldern, Formularen und Ansichten exportieren, anstatt ganze Entitäten mit allen Assets. 

Sie haben nicht nur mehr Kontrolle über den Inhalt einer Lösung, sondern können auch kontrollieren, was in den Patch einfließt. Sie können einen Patch für eine übergeordnete Lösung erstellen und ihn als ein Nebenupdate für die Basislösung exportieren. Wenn Sie eine Lösung klonen, führt das System ein Rollup für alle verknüpften Patches in die Basislösung aus, und es erstellt eine neue Version.  
  
 Wenn Sie mit Patches und geklonten Lösungen arbeiten, berücksichtigen Sie die folgenden Informationen:  
  
-   Ein Patch stellt ein inkrementelles Nebenupdate für die übergeordnete Lösung dar. Ein Patch kann Komponenten und Anlagen in der übergeordneten Lösung hinzufügen oder aktualisieren, wenn es auf dem Zielsystem installiert ist, es kann aber keine Komponenten oder Anlagen aus der übergeordneten Lösung löschen.  
  
-   Ein Patch kann nur eine übergeordnete Lösung haben, aber eine übergeordnete Lösung kann ein oder mehrere Patches haben.  
  
-   Für eine nicht verwaltete Lösung wird ein Patch erstellt. Sie können keinen Patch für eine verwaltete Lösung erstellen.  
  
-   Wenn Sie ein Patch auf ein Zielsystem exportieren, sollten sie es als verwaltetes Patch exportieren. Verwenden Sie keine unverwalteten Patches in Produktionsumgebungen.  
  
-   Die übergeordnete Lösung muss im Zielsystem vorhanden sein, um ein Patch zu installieren.  
  
-   Sie können ein Patch löschen oder aktualisieren.  
  
-   Wenn Sie eine übergeordnete Lösung löschen, werden auch alle untergeordneten Patches gelöscht. Das System gibt Ihnen eine Warnmeldung, dass Sie den Löschvorgang nicht rückgängig machen können. Das Löschen wird in einer einzigen Transaktion ausgeführt. Wenn eines der Patches oder die übergeordnete Lösung nicht gelöscht werden kann, wird für die gesamte Transaktion ein Rollback ausgeführt.  
  
-   Wenn Sie das erste Patch für übergeordnete Lösung erstellt haben, wird die Lösung gesperrt, und Sie können keine Änderungen in dieser Lösung vornehmen oder sie exportieren. Wenn Sie jedoch alle ihre untergeordneten Patches löschen, wird die übergeordnete Lösung entsperrt.  
  
-   Wenn Sie eine Basislösung klonen, wird für alle untergeordneten Patches ein Rollup in die Basislösung ausgeführt, und sie wird zu einer neuen Version. Sie können Komponenten und Anlagen in der geklonten Lösung hinzufügen, bearbeiten oder löschen.  
  
-   Eine geklonte Lösung stellt einen Ersatz der Basislösung dar, wenn sie im Zielsystem als verwaltete Lösung installiert wird. Normalerweise verwenden Sie eine geklonte Lösung, um ein Hauptupdate an die vorhergehende Lösung zu versenden.  
  
### <a name="understanding-version-numbers-for-cloned-solutions-and-patches"></a>Versionsnummern für geklonte Lösungen und Patches verstehen  
 Eine Lösungsversion hat das folgende Format: major.minor.build.revision. Ein Patch muss eine höhere Build- oder Revisionsnummer als die übergeordnete Lösung haben. Es kann keine höhere Haupt- oder Nebenversion haben. Beispielsweise bei einer Basislösungsversion 3.1.5.7 könnte ein Patch Version 3.1.5.8 oder Version 3.1.7.0 sein, aber nicht Version 3.2.0.0. Eine geklonte Lösung muss die Versionsnummer haben, die höher oder gleich der Versionsnummer der Basislösung ist. Beispielsweise bei einer Basislösungsversion 3.1.5.7 könnte eine geklonte Lösung Version 3.2.0.0 oder Version 3.1.5.7 sein. In der Benutzeroberfläche können Sie die Werte für die Haupt- und Nebenversion für eine geklonte Lösung festlegen sowie die Build- oder Revisionswerte für ein Patch.  
  
## <a name="create-a-segmented-solution-with-entity-assets"></a>Erstellen Sie eine segmentierte Lösung mit Entitäts-Assets 
 Um eine segmentierte Lösung zu erstellen, starten Sie mit dem Erstellen einer nicht verwalteten Lösung und fügen Sie die vorhandenen Ressourcen hinzu Sie können mehrere Systementitäten oder benutzerdefinierte Entitäten für jede Entität hinzufügen, die Anlagen auswählen, die Sie der Lösung hinzufügen möchten. Die assistentenähnliche Einrichtung führt Sie Schritt für Schritt durch den Prozess des Hinzufügens von Entitäts-Assets.  
  
1. Gehen Sie zum Portal Power Apps und wählen Sie dann **Lösungen**.  
  
2.  Wählen Sie **Neue Lösung** und erstellen Sie eine Lösung. Geben Sie die Informationen in den erforderlichen Feldern ein. Wählen Sie **Erstellen** aus.  
  
3.  Öffnen Sie die von Ihnen erstellte Lösung. Wählen Sie in der Befehlsleiste **Vorhandenes hinzufügen** und wählen Sie dann **Entität**.  
  
4.  Wählen Sie im Bereich **Existierende Entitäten hinzufügen** eine oder mehrere Entitäten aus, die Sie der Lösung hinzufügen möchten, z. B. eine Standard-Entität wie Kontakt und eine benutzerdefinierte Entität. Wählen Sie **Weiter**.  
    > [!div class="mx-imgBorder"] 
    > ![Vorhandene Entitäten hinzufügen ](media/add-existing-entities1.png)

5.  Im Bereich **Entitäten auswählen** können Sie aus den einzubeziehenden Assets wählen. 
    - **Alle Komponenten einbeziehen**. Diese Option umfasst alle Komponenten *und* die mit der Entität verbundenen Metadaten. Es kann andere Entitäten oder Entitätskomponenten wie z. B. Geschäftsprozessflows, Berichte, Verbindungen und Warteschlangen enthalten. 
    - **Einschließen der Metadaten der Entität**. Diese Option umfasst *nur* die mit der Entität verbundenen Metadaten. Zu den Metadaten gehören die Attribute der Entitäten, wie z. B. Auditierung, Dublettenerkennung oder Änderungsverfolgung. 
    - **Komponenten auswählen**. Mit dieser Option können Sie jede Komponente, die mit der Entität verknüpft ist, wie Felder, Beziehungen, Geschäftsregeln, Ansichten, Formulare und Diagramme, einzeln auswählen. 
      > [!div class="mx-imgBorder"] 
      > ![Entitätskomponenten auswählen](media/add-existing-entities2.png)
  
6.  Wählen Sie **Hinzufügen** aus.  

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
  
## <a name="create-a-solution-patch"></a>Einen Lösungspatch erstellen  
 Ein Patch enthält Änderungen an der übergeordneten Lösung, wie beispielsweise das Hinzufügen oder Bearbeiten von Komponenten und Anlagen. Sie müssen die Komponenten des übergeordneten Elements nicht einfügen, es sei denn, Sie planen, Sie zu bearbeiten.  
  
### <a name="create-a-patch-for-an-unmanaged-solution"></a>Ein Patch für eine nicht verwaltete Lösung erstellen  
  
1. Gehen Sie zum Portal Power Apps und wählen Sie dann **Lösungen**.   
  
2. Wählen Sie in der Lösungsliste eine nicht verwaltete Lösung aus, für die Sie einen Patch erstellen möchten. Wählen Sie in der Befehlsleiste **Klonen** und wählen Sie dann **Klonen Sie einen Patch**. Das rechte Fenster, das sich öffnet, enthält den Namen der Basislösung und die Patch-Versionsnummer. Wählen Sie **Speichern** aus.  
   > [!div class="mx-imgBorder"] 
   > <img src="media/clone-a-patch.png" alt="Clone a patch" height="735" width="408">
 
3. Suchen Sie in der Lösungsliste den neu erstellten Patch und öffnen Sie ihn. Beachten Sie, dass der eindeutige Name der Lösung mit _Patch_*Hex-Nummer* angehängt wurde. Fügen Sie wie bei der Basislösung die gewünschten Komponenten und Assets hinzu.  
  
#### <a name="create-a-patch-using-solution-explorer"></a>Erstellen Sie einen Patch mit dem Lösungsexplorer
 Folgende Abbildungen stellen ein Beispiel zum Erstellen eines Patches für eine vorhandene Lösung bereit. Beginnen Sie durch Klicken auf **Ein Patch klonen** (in der komprimierten Ansicht wird das Symbol **Ein Patch klonen** als zwei kleine Quadrate, wie unten gezeigt, abgebildet).  
  
 > [!div class="mx-imgBorder"] 
 > ![Klonen Sie ein Patch-Symbol.](media/solution-segmentation-click-patch-icon-admin.png "Klonen Sie ein Patch-Symbol.")  
  
 Im Dialogfeld **Zu patchender Klon** sehen Sie, dass die Versionsnummer für den Patch auf der Versionsnummer der übergeordneten Lösung basiert, aber die Buildnummer wird um eins erhöht. Jeder darauffolgende Patch hat eine höhere Build- oder Revisionsnummer als der vorhergehende Patch.  
  
 ![Verwenden Sie das „Zu patchender Klon“-Dialogfeld.](media/solution-segmentation-clone-patch-dialog-admin.png "Verwenden Sie das „Zu patchender Klon“-Dialogfeld.")  
  
 Der folgende Screenshot zeigt die Basislösung **SegmentedSolutionExample**, Version **1.0.1.0**, und den Patch **SegmentedSolutionExample_Patch**, Version **1.0.2.0**.  
  
 > [!div class="mx-imgBorder"] 
 > ![Ein Raster mit Lösungen und Patches.](media/solution-segmentation-solution-patch-grid-admin.png "Ein Raster mit Lösungen und Patches.")  
  
 Im Patch haben wir eine neue benutzerdefinierte Entität namens `Book` hinzugefügt und alle Assets der Entität `Book` in den Patch aufgenommen.  
  
 ![Fügen Sie die benutzerdefinierte Entität im Patch hinzu.](media/solution-segmentation-add-book-patch-admin.png "Fügen Sie die benutzerdefinierte Entität im Patch hinzu.")  
  
## <a name="clone-a-solution"></a>Eine Lösung klonen  
 Wenn Sie eine nicht verwaltete Lösung klonen, werden die ursprüngliche Lösung und alle Patches, die sich auf die Lösung beziehen, in eine neu erstellte Version der ursprünglichen Lösung hochgerollt. Nach dem Klonen enthält die neue Lösungsversion die ursprünglichen Entitäten sowie alle Komponenten oder Entitäten, die in einem Patch hinzugefügt wurden. 

![Eine Lösung klonen](media/cloned-solution.png)

> [!IMPORTANT]
> Durch das Klonen einer Lösung werden die ursprüngliche Lösung und die zugehörigen Patches entfernt. 
  
1. Gehen Sie zum Portal Power Apps und wählen Sie dann **Lösungen**.   
  
2.  Wählen Sie in der Lösungsliste eine nicht verwaltete Lösung aus, um einen Klon zu erstellen. Wählen Sie in der Befehlsleiste **Klonen** und wählen Sie dann **Lösung klonen**. Im rechten Fensterbereich werden der Name der Basislösung und die neue Versionsnummer angezeigt. Wählen Sie **Speichern** aus.  
  
  
### <a name="next-steps"></a>Nächste Schritte  
 [Überblick über Lösungen](solutions-overview.md)


