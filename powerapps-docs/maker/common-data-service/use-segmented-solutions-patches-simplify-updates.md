---
title: 'Verwenden Sie segmentierte Lösungen und Patches, um Lösungsupdates mit PowerApps zu vereinfachen | MicrosoftDocs'
description: 'Hier erfahren Sie, wie Sie Workflowaufträge nutzen, um Ihre Lösungen zu aktualisieren'
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
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
---
# <a name="use-segmented-solutions-and-patches-to-export-selected-entity-assets"></a>Verwenden von segmentierten Lösungen und Patches zum Exportieren ausgewählter Entitätsressourcen

Um genauere Kontrolle darüber zu erlangen, welche Elemente in Patches und Lösungen verteilt werden, verwenden Sie Lösungssegmentierung. Mit der Lösungssegmentierung können Sie Lösungen mit ausgewählten Entitätsanlagen exportieren, beispielsweise Entitätsfelder, Formulare oder Ansichten, anstatt gesamte Entitäten mit allen Anlagen. Um die segmentierten Lösungen und Patches zu erstellen, können Sie die Lösungs-Benutzeroberfläche verwenden, ohne einen Code zu schreiben.  
  
 Neben mehr Kontrolle über dem, was in einer Lösung ist, werden Sie kontrollieren können, was in ein Patch hineinkommt. Sie können einen Patch für eine übergeordnete Lösung erstellen und ihn als ein Nebenupdate für die Basislösung exportieren. Wenn Sie eine Lösung klonen, führt das System ein Rollup für alle verknüpften Patches in die Basislösung aus, und es erstellt eine neue Version.  
  
 Wenn Sie mit Patches und geklonten Lösungen arbeiten, berücksichtigen Sie die folgenden Informationen:  
  
-   Ein Patch stellt ein inkrementelles Nebenupdate für die übergeordnete Lösung dar. Ein Patch kann Komponenten und Anlagen in der übergeordneten Lösung hinzufügen oder aktualisieren, wenn es auf dem Zielsystem installiert ist, es kann aber keine Komponenten oder Anlagen aus der übergeordneten Lösung löschen.  
  
-   Ein Patch kann nur eine übergeordnete Lösung haben, aber eine übergeordnete Lösung kann ein oder mehrere Patches haben.  
  
-   Ein Patch wird für eine nicht verwaltete Lösung erstellt. Sie können keinen Patch für eine verwaltete Lösung erstellen.  
  
-   Wenn Sie ein Patch auf ein Zielsystem exportieren, sollten sie es als verwaltetes Patch exportieren. Verwenden Sie keine unverwalteten Patches in Produktionsumgebungen.  
  
-   Die übergeordnete Lösung muss im Zielsystem vorhanden sein, um ein Patch zu installieren.  
  
-   Sie können ein Patch löschen oder aktualisieren.  
  
-   Wenn Sie eine übergeordnete Lösung löschen, werden auch alle untergeordneten Patches gelöscht. Das System gibt Ihnen eine Warnmeldung, dass Sie den Löschvorgang nicht rückgängig machen können. Das Löschen wird in einer einzigen Transaktion ausgeführt. Wenn eines der Patches oder die übergeordnete Lösung nicht gelöscht werden kann, wird für die gesamte Transaktion ein Rollback ausgeführt.  
  
-   Wenn Sie das erste Patch für übergeordnete Lösung erstellt haben, wird die Lösung gesperrt, und Sie können keine Änderungen in dieser Lösung vornehmen oder sie exportieren. Wenn Sie jedoch alle ihre untergeordneten Patches löschen, wird die übergeordnete Lösung entsperrt.  
  
-   Wenn Sie eine Basislösung klonen, wird für alle untergeordneten Patches ein Rollup in die Basislösung ausgeführt, und sie wird zu einer neuen Version. Sie können Komponenten und Anlagen in der geklonten Lösung hinzufügen, bearbeiten oder löschen.  
  
-   Eine geklonte Lösung stellt einen Ersatz der Basislösung dar, wenn sie im Zielsystem als verwaltete Lösung installiert wird. Normalerweise verwenden Sie eine geklonte Lösung, um ein Hauptupdate an die vorhergehende Lösung zu versenden.  
  
## <a name="understanding-version-numbers-for-cloned-solutions-and-patches"></a>Versionsnummern für geklonte Lösungen und Patches verstehen  
 Eine Lösungsversion hat das folgende Format: major.minor.build.revision. Ein Patch muss eine höhere Build- oder Revisionsnummer als die übergeordnete Lösung haben. Es kann keine höhere Haupt- oder Nebenversion haben. Beispielsweise bei einer Basislösungsversion 3.1.5.7 könnte ein Patch Version 3.1.5.8 oder Version 3.1.7.0 sein, aber nicht Version 3.2.0.0. Eine geklonte Lösung muss die Versionsnummer haben, die höher oder gleich der Versionsnummer der Basislösung ist. Beispielsweise bei einer Basislösungsversion 3.1.5.7 könnte eine geklonte Lösung Version 3.2.0.0 oder Version 3.1.5.7 sein. In der Benutzeroberfläche können Sie die Werte für die Haupt- und Nebenversion für eine geklonte Lösung festlegen sowie die Build- oder Revisionswerte für ein Patch.  
  
## <a name="create-a-segmented-solution-with-the-entity-assets-you-want"></a>Erstellen einer segmentierten Lösung mit den Entitätsanlagen, die Sie möchten  
 Um eine segmentierte Lösung zu erstellen, starten Sie mit dem Erstellen einer nicht verwalteten Lösung und fügen Sie die vorhandenen Ressourcen hinzu Sie können mehrere Systementitäten oder benutzerdefinierte Entitäten für jede Entität hinzufügen, die Anlagen auswählen, die Sie der Lösung hinzufügen möchten. Das Assistenten-ähnliche Setup führt Sie Schritt für Schritt durch den Prozess des Hinzufügens neuer Entitätsanlagen.  
  
1. Gehen Sie zu **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Lösungen**.   
  
2.  Wählen Sie **Neu** und erstellen Sie eine Lösung. Geben Sie die Informationen in den erforderlichen Feldern ein. Klicken Sie auf **Speichern und schließen**.  
  
3.  Öffnen Sie die Lösung, die Sie gerade erstellt haben. Wählen Sie in der Dropdown-Liste **Vorhandene hinzufügen** die Option **Entität** aus.  
  
4.  Wählen Sie im Dialogfeld **Lösungskomponenten auswählen** eine oder mehrere Entitäten aus, die Sie der Lösung hinzufügen möchten. Wählen Sie **OK** aus.  
  
5.  Der Assistent wird geöffnet. Folgen Sie den Anweisungen des Assistenten, um Anlagen für jede ausgewählte Entität der Lösung hinzuzufügen.  
  
6.  Wählen Sie **Veröffentlichen** aus, damit die Änderungen wirksam werden.  
  
 Folgende Abbildungen stellen ein Beispiel der Erstellung einer segmentierten Lösung bereit, indem Entitätsanlagen von den Entitäten `Account`, `Case` sowie `Contact` ausgewählt werden.  
  
 Beginnen Sie mit der Auswahl der Komponente **Entität**.  
  
 ![Fügen Sie vorhandene Ressourcen hinzu.](media/solution-segmentation-add-existing-resources-admin.png "Fügen Sie vorhandene Ressourcen hinzu.")  
  
 Wählen Sie dann die Lösungskomponenten aus.  
  
 ![Wählen Sie die Lösungskomponente aus.](media/solution-segmentation-select-components-admin.png "Wählen Sie die Lösungskomponente aus.")  
  
 Folgen Sie dem Assistenten. Wählen Sie in Schritt 1 in alphabetischer Reihenfolge die Anlagen für die erste Entität, der `Account`-Entität, wie hier gezeigt, aus.  
  
 ![Starten Sie den Assistenten.](media/solution-segmentation-wizard-starts-admin.png "Starten Sie den Assistenten.")  
  
 Öffnen Sie die Registerkarte **Felder** und wählen Sie das Feld **Firmennummer** aus.  
  
 ![Wählen Sie die Entitätsanlagen der Firma aus.](media/solution-segmentation-select-account-assets-admin.png "Wählen Sie die Entitätsanlagen der Firma aus.")  
  
 Fügen Sie in Schritt 2 für die Entität **Anfrage** alle Anlagen hinzu.  
  
 ![Wählen Sie die Entitätsanlagen des Falls aus.](media/solution-segmentation-select-case-assets-admin.png "Wählen Sie die Entitätsanlagen des Falls aus.")  
  
 Fügen Sie im Schritt 3 das Feld **Jahrestag** für die Entität **Kontakt** hinzu.  
  
 ![Wählen Sie die Entitätsanlagen des Kontakts aus.](media/solution-segmentation-select-contact-assets-admin.png "Wählen Sie die Entitätsanlagen des Kontakts aus.")  
  
 Daher enthält die segmentierte Lösung, die erstellt wird, drei Entitäten, nämlich `Account`, `Case` und `Contact`. Jede Entität enthält ausschließlich Anlagen, die ausgewählt waren.  
  
 ![Lösungen mit Entitäten.](media/solution-segmentation-solution-entities-admin.png "Lösungen mit Entitäten.")  
  
## <a name="create-a-solution-patch"></a>Einen Lösungspatch erstellen  
 Ein Patch enthält Änderungen an der übergeordneten Lösung, wie beispielsweise das Hinzufügen oder Bearbeiten von Komponenten und Anlagen. Sie müssen die Komponenten des übergeordneten Elements nicht einfügen, es sei denn, Sie planen, Sie zu bearbeiten.  
  
 #### <a name="create-a-patch-for-an-unmanaged-solution"></a>Ein Patch für eine nicht verwaltete Lösung erstellen  
  
1. Gehen Sie zu **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Lösungen**.   
  
2.  Wählen Sie in der Liste eine nicht verwaltete Lösung aus, für die Sie einen Patch erstellen möchten. Wählen Sie **Patch klonen**. Das Dialogfeld, das geöffnet wird, enthält den Namen der Basislösung und die Patchversionsnummer. Wählen Sie **Speichern** aus.  
  
3.  Im Raster suchen und öffnen Sie das neu erstellte Patch. Genau wie mit der Basislösung folgen Sie dem Assistenten, um die Komponenten und Anlagen, die Sie möchten, hinzuzufügen.  
  
4.  Wählen Sie **Veröffentlichen** aus, damit die Änderungen wirksam werden.  
  
 Folgende Abbildungen stellen ein Beispiel zum Erstellen eines Patches für eine vorhandene Lösung bereit. Beginnen Sie durch Klicken auf **Ein Patch klonen** (in der komprimierten Ansicht wird das Symbol **Ein Patch klonen** als zwei kleine Quadrate, wie unten gezeigt, abgebildet).  
  
 ![Klonen Sie ein Patch-Symbol.](media/solution-segmentation-click-patch-icon-admin.png "Klonen Sie ein Patch-Symbol.")  
  
 Im Dialogfeld **Zu patchender Klon** sehen Sie, dass die Versionsnummer für den Patch auf der Versionsnummer der übergeordneten Lösung basiert, aber die Buildnummer wird um eins erhöht. Jeder darauffolgende Patch hat eine höhere Build- oder Revisionsnummer als der vorhergehende Patch.  
  
 ![Verwenden Sie das "Zu patchender Klon"-Dialogfeld.](media/solution-segmentation-clone-patch-dialog-admin.png "Verwenden Sie das \"Zu patchender Klon\"-Dialogfeld.")  
  
 Im folgenden Screenshot wird die Basislösung **SegmentedSolutionExample**, Version **1.0.1.0** und der Patch **SegmentedSolutionExample_Patch**, Version **1.0.2.0**, angezeigt.  
  
 ![Ein Raster mit Lösungen und Patches.](media/solution-segmentation-solution-patch-grid-admin.png "Ein Raster mit Lösungen und Patches.")  
  
 Im Patch, haben wir eine neue benutzerdefinierte Entität mit dem Namen `Book` hinzugefügt und wir haben alle Anlagen der Entität `Book` im Patch eingefügt.  
  
 ![Fügen Sie die benutzerdefinierte Entität im Patch hinzu.](media/solution-segmentation-add-book-patch-admin.png "Fügen Sie die benutzerdefinierte Entität im Patch hinzu.")  
  
## <a name="clone-a-solution"></a>Eine Lösung klonen  
 Wenn Sie eine nicht verwaltete Lösung klonen, wird für alle Patches, die mit dieser Lösung verknüpft sind, ein Rollup in die neu erstellte Version der ursprünglichen Version ausgeführt.  
  
1. Gehen Sie zu **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Lösungen**.   
  
2.  Wählen Sie in der Liste eine nicht verwaltete Lösung aus, die Sie klonen möchten. Wählen Sie die **Lösung klonen** aus: Das Dialogfeld, das geöffnet wird, enthält den Namen der Basislösung und die neue Versionsnummer. Wählen Sie **Speichern** aus.  
  
3.  Wählen Sie **Veröffentlichen** aus, damit die Änderungen wirksam werden.  
  
 Beim Fortfahren mit diesem Beispiel sehen Sie das Dialogfeld **In Lösung klonen**, das die neue Lösungsversionsnummer anzeigt.  
  
 ![Verwenden Sie das Dialogfeld "In Lösung klonen".](media/solution-segmentation-clone-solution-dialog-admin.png "Verwenden Sie das Dialogfeld \"In Lösung klonen\".")  
  
 Nach dem Klonen enthält die neue Lösungsversion drei ursprüngliche Entitäten (`Account`, `Case` und `Contact`) und die benutzerdefinierte Entität mit der Bezeichnung `Book`, die dem Patch hinzugefügt wurde. Jede Entität enthält ausschließlich Anlagen, die im Beispiel hinzugefügt wurden.  
  
 ![Eine geklonte Lösung mit Patch-Rollup.](media/solution-segmentation-solution-rolled-up-patch-admin.png "Eine geklonte Lösung mit Patch-Rollup.")  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Lösungsübersicht](solutions-overview.md) [Erstellen von Patches zur Vereinfachung von Lösungsupdates]

