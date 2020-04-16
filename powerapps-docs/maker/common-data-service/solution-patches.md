---
title: Erstellen von Lösungspatches | Microsoft-Dokumentation
description: Erfahren Sie, wie Lösungspatches erstellt werden
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
ms.assetid: ''
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9bddae4295a891d4c4dd86593b4fa27815b2b03c
ms.sourcegitcommit: 3f89b04359df19f8fa5167e2607509bb97e60fe0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/25/2020
ms.locfileid: "3165261"
---
# <a name="create-solution-patches"></a>Lösungspatches erstellen  
Sie können einen Patch für eine übergeordnete Lösung erstellen und ihn als ein Nebenupdate für die Basislösung exportieren. Wenn Sie eine Lösung klonen, führt das System ein Rollup für alle verknüpften Patches in die Basislösung aus, und es erstellt eine neue Version.

> [!WARNING]
> Die Verwendung von „Einen Patch klonen“ und „Lösung klonen“ zum Aktualisieren einer Lösung wird nicht empfohlen, da dies die Teamentwicklung einschränkt und die Komplexität beim Speichern Ihrer Lösung in einem Quellcodeverwaltungssystem erhöht. Weitere Informationen zum Aktualisieren einer Lösung finden Sie unter [Upgraden oder Aktualisieren einer Lösung](update-solutions.md).


## <a name="creating-updates-using-clone-solution-and-clone-to-patch"></a>Erstellen von Updates mit „Lösung klonen“ und „Zu patchender Klon“
 Wenn Sie mit Patches und geklonten Lösungen arbeiten, berücksichtigen Sie die folgenden Informationen:  
  
-   Ein Patch stellt ein inkrementelles Nebenupdate für die übergeordnete Lösung dar. Ein Patch kann Komponenten und Anlagen in der übergeordneten Lösung hinzufügen oder aktualisieren, wenn es auf dem Zielsystem installiert ist, es kann aber keine Komponenten oder Anlagen aus der übergeordneten Lösung löschen.  
  
-   Ein Patch kann nur eine übergeordnete Lösung haben, aber eine übergeordnete Lösung kann ein oder mehrere Patches haben.  
  
-   Ein Patch wird aus einer nicht verwalteten Lösung erstellt. Sie können keinen Patch aus einer verwalteten Lösung erstellen.  
  
-   Wenn Sie einen Patch in ein Zielsystem importieren, sollten Sie ihn als verwalteten Patch exportieren. Verwenden Sie keine unverwalteten Patches in Produktionsumgebungen.  
  
-   Die übergeordnete Lösung muss im Zielsystem vorhanden sein, um ein Patch zu installieren.  
  
-   Sie können ein Patch löschen oder aktualisieren.  
  
-   Wenn Sie eine übergeordnete Lösung löschen, werden auch alle untergeordneten Patches gelöscht. Das System gibt Ihnen eine Warnmeldung, dass Sie den Löschvorgang nicht rückgängig machen können. Das Löschen wird in einer einzigen Transaktion ausgeführt. Wenn eines der Patches oder die übergeordnete Lösung nicht gelöscht werden kann, wird für die gesamte Transaktion ein Rollback ausgeführt.  
  
-   Wenn Sie das erste Patch für übergeordnete Lösung erstellt haben, wird die Lösung gesperrt, und Sie können keine Änderungen in dieser Lösung vornehmen oder sie exportieren. Wenn Sie jedoch alle ihre untergeordneten Patches löschen, wird die übergeordnete Lösung entsperrt.  
  
-   Wenn Sie eine Basislösung klonen, wird für alle untergeordneten Patches ein Rollup in die Basislösung ausgeführt, und sie wird zu einer neuen Version. Sie können Komponenten und Anlagen in der geklonten Lösung hinzufügen, bearbeiten oder löschen.  
  
-   Eine geklonte Lösung stellt einen Ersatz der Basislösung dar, wenn sie im Zielsystem als verwaltete Lösung installiert wird. Normalerweise verwenden Sie eine geklonte Lösung, um ein Hauptupdate an die vorhergehende Lösung zu versenden.  

Wenn Sie eine Lösung klonen, enthält die von Ihnen angegebene Versionsnummer die Haupt- und Nebenpositionen. 

   > [!div class="mx-imgBorder"]
   > <img src="media/clone-solution.png" alt="Clone a patch major and minor version" height="560" width="307"> 

 Wenn Sie einen Patch klonen, enthält die von Ihnen angegebene Versionsnummer die Build- und Revisionspositionen. 

   > [!div class="mx-imgBorder"] 
   > <img src="media/clone-a-patch2.png" alt="Clone a patch build and revision version" height="560" width="307">

Im Artikel [Versionsnummern der geklonten Lösung und des geklonten Patches](#clone-solution-and-clone-patch-version-numbers) finden Sie weitere Informationen zu Versionsnummern.
  
## <a name="create-a-solution-patch"></a>Einen Lösungspatch erstellen  
 Ein Patch enthält Änderungen an der übergeordneten Lösung, wie beispielsweise das Hinzufügen oder Bearbeiten von Komponenten und Anlagen. Sie müssen die Komponenten des übergeordneten Elements nicht einfügen, es sei denn, Sie planen, Sie zu bearbeiten.  
  
## <a name="create-a-patch-for-an-unmanaged-solution"></a>Ein Patch für eine nicht verwaltete Lösung erstellen  
  
1. Gehen Sie zum Portal Power Apps und wählen Sie dann **Lösungen**.   
  
2. Wählen Sie in der Lösungsliste eine nicht verwaltete Lösung aus, für die Sie einen Patch erstellen möchten. Wählen Sie in der Befehlsleiste **Klonen** und wählen Sie dann **Klonen Sie einen Patch**. Das rechte Fenster, das sich öffnet, enthält den Namen der Basislösung und die Patch-Versionsnummer. Wählen Sie **Speichern** aus.  
   > [!div class="mx-imgBorder"] 
   > <img src="media/clone-a-patch.png" alt="Clone a patch" height="735" width="408">
 
3. Suchen Sie in der Lösungsliste den neu erstellten Patch und öffnen Sie ihn. Beachten Sie, dass der eindeutige Name der Lösung mit _Patch_*Hex-Nummer* angehängt wurde. Fügen Sie wie bei der Basislösung die gewünschten Komponenten und Assets hinzu.  
  
### <a name="create-a-patch-using-solution-explorer"></a>Erstellen Sie einen Patch mit dem Lösungsexplorer
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
> Durch das Klonen einer Lösung werden die ursprüngliche Lösung und die zugehörigen Patches zu einer neuen Basislösung zusammengeführt und die ursprüngliche Lösung und die Patches entfernt. 
  
1. Gehen Sie zum Portal Power Apps und wählen Sie dann **Lösungen**.   
  
2.  Wählen Sie in der Lösungsliste eine nicht verwaltete Lösung aus, um einen Klon zu erstellen. Wählen Sie in der Befehlsleiste **Klonen** und wählen Sie dann **Lösung klonen**. Im rechten Fensterbereich werden der Name der Basislösung und die neue Versionsnummer angezeigt. Wählen Sie **Speichern** aus.  

## <a name="clone-solution-and-clone-patch-version-numbers"></a>Versionsnummern der geklonten Lösung und des geklonten Patches
Ein Patch muss eine höhere Build- oder Revisionsnummer als die übergeordnete Lösung haben. Es kann keine höhere Haupt- oder Nebenversion haben. Beispielsweise bei einer Basislösung mit Version 3.1.5.7 könnte ein Patch Version 3.1.5.8 oder Version 3.1.7.0 sein, aber nicht Version 3.2.0.0. Eine geklonte Lösung muss die Versionsnummer haben, die höher oder gleich der Versionsnummer der Basislösung ist. Beispielsweise bei einer Basislösungsversion 3.1.5.7 könnte eine geklonte Lösung Version 3.2.0.0 oder Version 3.1.5.7 sein. Wenn Sie eine Lösung oder einen Patch klonen, legen Sie die Werte für die Haupt- und Nebenversion für eine geklonte Lösung sowie die Build- oder Revisionswerte für einen Patch fest.  
  
### <a name="see-also"></a>Siehe auch
[Upgraden oder Aktualisieren einer Lösung](update-solutions.md)