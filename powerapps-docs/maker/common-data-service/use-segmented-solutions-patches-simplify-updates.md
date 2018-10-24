---
title: Verwenden von segmentiert Lösungen und Patches zur Vereinfachung von Lösungsupdates mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Ihre Lösungen mit der Lösungssegmentierung aktualisieren.
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
ms.openlocfilehash: 274e2914d65b6bcb644821c044adb3b0246a75fc
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39685609"
---
# <a name="use-segmented-solutions-and-patches-to-export-selected-entity-assets"></a>Verwenden segmentierter Lösungen und Patches zum Exportieren von Entitätsobjekten

Um eine bessere Kontrolle darüber zu erhalten, was Sie in Lösungen und Lösungspatches verteilen, verwenden Sie die Lösungssegmentierung. Mit der Lösungssegmentierung können Sie Lösungen mit ausgewählten Entitätsobjekten, wie beispielsweise Entitätsfelder, Formulare und Ansichten, exportieren, anstatt ganze Entitäten mit allen Objekten. Um segmentierte Lösungen und Patches zu erstellen, können Sie die Benutzeroberfläche der Lösung verwenden, ohne Code zu schreiben.  
  
 Sie haben nicht nur mehr Kontrolle über das, was in einer Lösung enthalten ist, sondern können auch steuern, was in einen Patch einfließt. Sie können einen Patch für eine übergeordnete Lösung erstellen und ihn als kleines Update für die Basislösung exportieren. Wenn Sie eine Lösung klonen, führt das System alle zugehörigen Patches in die Basislösung aus und erstellt eine neue Version.  
  
 Wenn Sie mit Patches und geklonten Lösungen arbeiten, beachten Sie die folgenden Informationen:  
  
-   Ein Patch stellt ein inkrementelles kleines Update der übergeordneten Lösung dar. Ein Patch kann Komponenten und Objekte in der übergeordneten Lösung hinzufügen oder aktualisieren, wenn er auf dem Zielsystem installiert ist, aber er kann keine Komponenten oder Vermögenswerte aus der übergeordneten Lösung löschen.  
  
-   Ein Patch kann nur eine übergeordnete Lösung haben, aber eine übergeordnete Lösung kann einen oder mehrere Patches haben.  
  
-   Ein Patch wird für eine nicht verwaltete Lösung erstellt. Sie können keinen Patch für eine verwaltete Lösung erstellen.  
  
-   Wenn Sie einen Patch in ein Zielsystem exportieren, sollten Sie ihn als verwalteten Patch exportieren. Verwenden Sie keine nicht verwalteten Patches in Produktionsumgebungen.  
  
-   Die übergeordnete Lösung muss auf dem Zielsystem vorhanden sein, um einen Patch zu installieren.  
  
-   Sie können einen Patch nicht löschen oder aktualisieren.  
  
-   Wenn Sie eine übergeordnete Lösung löschen, werden alle untergeordneten Patches ebenfalls gelöscht. Das System zeigt eine Warnmeldung an, dass Sie den Löschvorgang nicht rückgängig machen können. Der Löschvorgang wird in einer einzelnen Transaktion ausgeführt. Wenn einer der Patches oder die übergeordnete Lösung nicht gelöscht werden kann, wird die gesamte Transaktion zurückgesetzt.  
  
-   Nachdem Sie den ersten Patch für eine übergeordnete Lösung erstellt haben, wird die Lösung gesperrt, und Sie können keine Änderungen an dieser Lösung vornehmen oder sie exportieren. Wenn Sie jedoch alle untergeordneten Patches löschen, wird die übergeordnete Lösung entsperrt.  
  
-   Wenn Sie eine Basislösung klonen, werden alle untergeordneten Patches in die Basislösung ausgeführt und es wird eine neue Version erstellt. Sie können das Komponenten und Objekte in der geklonten Lösung hinzufügen, bearbeiten oder löschen.  
  
-   Eine geklonte Lösung stellt einen Ersatz für die Basislösung dar, wenn sie als verwaltete Lösung auf dem Zielsystem installiert ist. In der Regel verwenden Sie eine geklonte Lösung, um ein größeres Update für die vorhergehende Lösung bereitzustellen.  
  
## <a name="understanding-version-numbers-for-cloned-solutions-and-patches"></a>Grundlegendes zu Versionsnummern für die geklonte Lösungen und Patches  
 Eine Lösungsversion hat das folgende Format: „Hauptversion.Nebenversion.Build.Revision“. Ein Patch muss eine höhere Build- oder Revisionsnummer haben als die übergeordnete Lösung. Es darf keine höhere Haupt- oder Nebenversion geben. So könnte beispielsweise für eine Basislösung der Version 3.1.5.7 ein Patch eine Version 3.1.5.8 oder eine Version 3.1.7.0 sein, aber nicht die Version 3.2.0.0.0. Die Versionsnummer einer geklonten Lösung muss größer oder gleich der Versionsnummer der Basislösung sein. So könnte beispielsweise für eine Basislösung der Version 3.1.5.7 ein Patch eine Version 3.2.0.0 oder eine Version 3.1.5.7 sein, aber nicht die Version 3.2.0.0.0. In der Benutzeroberfläche können Sie nur die Haupt- und Nebenversionswerte für eine geklonte Lösung und die Build- oder Revisionswerte für einen Patch festlegen.  
  
## <a name="create-a-segmented-solution-with-the-entity-assets-you-want"></a>Erstellen einer segmentierten Lösung mit den gewünschten Entitäten  
 Um eine segmentierte Lösung zu erstellen, beginnen Sie mit der Erstellung einer nicht verwalteten Lösung und dem Hinzufügen der vorhandenen Ressourcen. Sie können mehrere System- oder benutzerdefinierte Entitäten hinzufügen und für jede Entität die Objekte auswählen, die Sie in die Lösung aufnehmen möchten. Das assistentenähnliche Setup führt Sie Schritt für Schritt durch den Prozess des Hinzufügens von Entitätsobjekten.  
  
1. Wechseln Sie zu **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Lösungen**.   
  
2.  Wählen Sie **Neu** aus, und erstellen Sie eine Lösung. Geben Sie die Informationen in die erforderlichen Felder ein. Wählen Sie **Speichern und Schließen** aus.  
  
3.  Öffnen Sie die gerade erstellte Lösung. Wählen Sie in der Dropdownliste **Vorhandene hinzufügen** die Option **Entität**.  
  
4.  Wählen Sie im Dialogfeld **Lösungskomponenten auswählen** eine oder mehrere Entitäten aus, die Sie der Lösung hinzufügen möchten. Wählen Sie **OK** aus.  
  
5.  Der Assistenten wird geöffnet. Folgen Sie den Anweisungen des Assistenten, um Objekte für jede ausgewählte Entität zur Lösung hinzuzufügen.  
  
6.  Wählen Sie **Veröffentlichen**, für die Änderungen zu übernehmen.  
  
 Die folgenden Abbildungen zeigen ein Beispiel für die Erstellung einer segmentierten Lösung durch Auswahl von Entitätsobjekten aus den Entitäten `Account`, `Case` und `Contact`.  
  
 Wählen Sie zunächst die Komponente **Entität**.  
  
 ![Vorhandene Ressourcen hinzufügen.](media/solution-segmentation-add-existing-resources-admin.png "Vorhandene Ressourcen hinzufügen.")  
  
 Wählen Sie dann die Komponenten der Lösung.  
  
 ![Komponenten der Lösung auswählen.](media/solution-segmentation-select-components-admin.png "Komponenten der Lösung auswählen.")  
  
 Folgen Sie den Anweisungen des Assistenten. Wählen Sie in Schritt 1, beginnend in alphabetischer Reihenfolge, die Objekte für die erste Entität, die Entität `Account`, wie hier gezeigt.  
  
 ![Assistenten starten. ](media/solution-segmentation-wizard-starts-admin.png "Assistenten starten.")  
  
 Öffnen Sie die Registerkarte **Felder**, und wählen Sie das Feld **Kontonummer**.  
  
 ![Kontoentitätsobjekte auswählen. ](media/solution-segmentation-select-account-assets-admin.png "Kontoentitätsobjekte auswählen.")  
  
 Fügen Sie in Schritt 2 alle Objekte für die Entität **Fall** hinzu.  
  
 ![Fallentitätsobjekte auswählen.](media/solution-segmentation-select-case-assets-admin.png "Fallentitätsobjekte auswählen.")  
  
 Fügen Sie in Schritt 3 das Feld **Jahrestag** für die Entität **Kontakt** hinzu.  
  
 ![Kontaktentitätsobjekte auswählen.](media/solution-segmentation-select-contact-assets-admin.png "Kontaktentitätsobjekte auswählen.")  
  
 Infolgedessen enthält die erstellte segmentierte Lösung drei Entitäten, `Account`, `Case` und `Contact`. Jede Entität enthält nur die ausgewählten Objekte.  
  
 ![Lösung mit Entitäten.](media/solution-segmentation-solution-entities-admin.png "Lösung mit Entitäten.")  
  
## <a name="create-a-solution-patch"></a>Erstellen eines Lösungspatch  
 Ein Patch enthält Änderungen an der übergeordneten Lösung, wie das Hinzufügen oder Bearbeiten von Komponenten und Objekten. Sie müssen die Komponenten der übergeordneten Komponenten nicht einbeziehen, es sei denn, Sie planen, sie zu bearbeiten.  
  
 #### <a name="create-a-patch-for-an-unmanaged-solution"></a>Erstellen eines Patch für eine nicht verwaltete Lösung  
  
1. Wechseln Sie zu **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Lösungen**.   
  
2.  Wählen Sie in der Liste eine nicht verwaltete Lösung aus, um einen Patch dafür zu erstellen. Wählen Sie **Patch klonen** aus. Das sich öffnende Dialogfeld enthält den Namen der Basislösung und die Patchversionsnummer. Wählen Sie **Speichern**.  
  
3.  Suchen und öffnen Sie im Raster den neu erstellten Patch. Folgen Sie wie bei der Basislösung dem Assistenten, um die gewünschten Komponenten und Objekte hinzuzufügen.  
  
4.  Wählen Sie **Veröffentlichen**, für Ihre Änderungen zu übernehmen.  
  
 Die folgenden Abbildungen zeigen ein Beispiel für die Erstellung eines Patches für eine bestehende Lösung. Wählen Sie zunächst **Patch klonen** (in der komprimierten Ansicht wird das Symbol **Patch klonen** als zwei kleine Felder dargestellt, wie unten gezeigt).  
  
 ![Symbol „Patch klonen“.](media/solution-segmentation-click-patch-icon-admin.png "Symbol „Patch klonen“.")  
  
 Im Dialogfeld **Patch klonen** sehen Sie, dass die Versionsnummer für den Patch auf der Versionsnummer der übergeordneten Lösung basiert, aber die Buildnummer um eins erhöht wird. Jeder nachfolgende Patch hat eine höhere Build- oder Revisionsnummer als der vorherige Patch.  
  
 ![Dialogfeld „Patch klonen“.](media/solution-segmentation-clone-patch-dialog-admin.png "Dialogfeld „Patch klonen“.")  
  
 Der folgende Screenshot zeigt die Basislösung **SegmentedSolutionExample**, Version **1.0.1.0** und den Patch **SegmentedSolutionExample_Patch**, Version **1.0.2.0**.  
  
 ![Ein Raster mit Lösungen und Patches.](media/solution-segmentation-solution-patch-grid-admin.png "Ein Raster mit Lösungen und Patches.")  
  
 In dem Patch haben wir eine neue benutzerdefinierte Entität namens `Book` hinzugefügt und alle Objekte der Entität `Book` in den Patch aufgenommen.  
  
 ![Benutzerdefinierte Entität zum Patch hinzufügen.](media/solution-segmentation-add-book-patch-admin.png "Benutzerdefinierte Entität zum Patch hinzufügen.")  
  
## <a name="clone-a-solution"></a>Klonen einer Lösung  
 Wenn Sie eine nicht verwaltete Lösung klonen, werden alle mit dieser Lösung verbundenen Patches in der neu erstellten Version der ursprünglichen Lösung ausgeführt.  
  
1. Wechseln Sie zu **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Lösungen**.   
  
2.  Wählen Sie aus der Liste eine nicht verwaltete Lösung aus, die Sie klonen möchten. Wählen Sie **Lösung klonen** aus. Das sich öffnende Dialogfeld enthält den Namen der Basislösung und die neue Versionsnummer. Wählen Sie **Speichern**.  
  
3.  Wählen Sie **Veröffentlichen**, für Ihre Änderungen zu übernehmen.  
  
 Wenn Sie mit dem Beispiel fortfahren, sehen Sie das Dialogfeld **Lösung klonen** mit der neuen Versionsnummer der Lösung.  
  
 ![Dialogfeld „Lösung klonen“.](media/solution-segmentation-clone-solution-dialog-admin.png "Dialogfeld „Lösung klonen“.")  
  
 Nach dem Klonen enthält die neue Lösungsversion drei ursprüngliche Entitäten (`Account`, `Case` und `Contact`) und die benutzerdefinierte Entität namens `Book`, die im Patch hinzugefügt wurde. Jede Entität enthält nur die im Beispiel hinzugefügten Objekte.  
  
 ![Eine geklonte Lösung mit ausgeführtem Patch.](media/solution-segmentation-solution-rolled-up-patch-admin.png "Eine geklonte Lösung mit ausgeführtem Patch.")  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Übersicht über Lösungen](solutions-overview.md) [Erstellen von Patches zur Vereinfachung von Lösungsupdates]

