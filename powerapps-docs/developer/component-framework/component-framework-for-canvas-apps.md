---
title: PowerApps component framework für Canvas-Apps | Microsoft-Dokumentation
description: Erstellen von Codekomponenten für Canvas-Apps
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 08/31/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: e7671c01a9c21dda56579801b77e1480abab5e29
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753962"
---
# <a name="powerapps-component-framework-for-canvas-apps"></a>PowerApps component framework für Canvas-Apps

> [!IMPORTANT]
> Diese Funktion ist weiterhin experimenteller Natur und standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Experimentelle und Vorschaufunktionen](../../maker/canvas-apps/working-with-experimental.md).

Das PowerApps component framework ermöglicht es App-Entwicklern, Codekomponenten für die Verwendung in einer App oder über Apps zu erstellen. Weitere Informationen: [Übersicht über das PowerApps component framework](overview.md) 

In dieser experimentellen Vorschau können App-Entwickler mit dem PowerApps component framework Codekomponenten erstellen, debuggen, importieren und zu Canvas-Apps mithilfe der PowerApps-CLI-Werkzeuge hinzuzufügen. Nur bestimmte APIs werden in dieser experimentellen Vorschau unterstützt. Es empfiehlt sich, jede einzelne API zu überprüfen, um zu ermitteln, ob sie Canvas-Apps unterstützt. 

> [!WARNING]
> Codekomponenten enthalten Code, der möglicherweise nicht von Microsoft generiert werden kann und ggf. auf Sicherheitstoken und Daten zugreifen kann. Wenn Sie Codekomponenten zu einer App hinzufügen, sollten Sie sicherstellen, dass die Codekomponentenlösungen von einer vertrauenswürdigen Quelle stammen.

## <a name="prerequisites"></a>Voraussetzungen

Es sind Systemadministratorrechte erforderlich, um die PowerApps-Komponentenfunktion in der Umgebung zu aktivieren.

> [!IMPORTANT]
> Standardmäßig ist das PowerApps Component Framework für modellgesteuerte Apps aktiviert.

## <a name="enable-powerapps-component-framework-feature"></a>Aktivieren der Funktion des PowerApps component framework

Um Codekomponenten zu einer App hinzuzufügen, müssen Sie die Funktion des PowerApps component framework in jeder Umgebung aktivieren, in der Sie sie verwenden möchten. So aktivieren Sie eine Umgebung für die Verwendung von Codekomponenten in ihren Apps:

1. Melden Sie sich bei [PowerApps](https://powerapps.microsoft.com/) an.

2. Klicken Sie auf das Symbol **Einstellungen** und wählen dann **Admin Center** aus.
    
    ![Einstellungen und Admin Center](media/select-admin-center-from-settings.png "Einstellungen und Admin Center") 

3. Wählen Sie die Umgebung aus, in der Sie diese Funktion aktivieren wollen. Wählen Sie das Auslassungssymbol (**...**) und dann **Einstellungen** aus.

4. Wählen Sie auf der Registerkarte **Produkte** die Option **Funktionen** aus.

   ![Aktivieren von PowerApps Component Framework](media/enable-pcf-feature.png "Aktivieren des PowerApps Component Framework")

5. Setzen Sie aus der Liste der verfügbaren Funktionen den Schalter auf **Ein** unter **PowerApps Component Framework für Canvas-Apps**.

6. Öffnen Sie nun die App, der Sie die Codekomponente hinzufügen möchten, und navigieren Sie zu **Datei** >  **App-Einstellungen**. Wählen Sie dann **Erweiterte Einstellungen** aus.

   ![Aktivieren Sie Komponenten für das PowerApps Component Framework](media/enable-components-for-pcf.png "Aktivieren Sie Komponenten für PowerApps Component Framework")
   
7. Setzen Sie den **Komponenten**-Schalter auf **Ein** unter dem Abschnitt **Experimentelle Funktion**.

## <a name="implementing-code-components"></a>Implementieren von Codekomponenten

Nachdem Sie das Feature des PowerApps component framework in Ihrer Umgebung aktiviert haben, können Sie mit der Implementierung der Logik für Codekomponenten beginnen. Das Thema [Beispielkomponente implementieren](implementing-controls-using-typescript.md) zeigt den schrittweisen Vorgang zum Erstellen von Codekomponenten mit Implementierung der benutzerdefinierten Logik und der Manifestdatei, die den Debuggingsprozess ausführt, eine ZIP-Datei der Lösung erstellt und den Abschluss nach Common Data Service importiert.

> [!NOTE]
> Codekomponenten zu implementieren ist gleich für modellgesteuerte Apps und Canvas-Apps (experimentelle Vorschau). Der einzige Unterschied ist das Hinzufügen der Codekomponenten. 

## <a name="add-components-to-a-canvas-app"></a>Hinzufügen von Komponenten zu einer Canvas-App

> [!NOTE]
> Um Codekomponenten zu einem Feld oder einer Entität für modellgesteuerte Apps hinzuzufügen, lesen Sie [Hinzufügen von Codekomponenten zu modellgesteuerten Apps](add-custom-controls-to-a-field-or-entity.md)

So fügen Sie Codekomponenten zu einer Canvas-App hinzu:

1. Navigieren zu PowerApps Studio.
2. Erstellen einer neuen Canvas-App oder Bearbeiten einer vorhandenen App, der Sie die Codekomponente hinzufügen möchten.

   > [!IMPORTANT]
   > Stellen Sie sicher, dass die Lösungs-ZIP-Datei bereits nach Common Data Service [importiert](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) wurde, bevor Sie mit dem nächsten Schritt fortfahren.

3. Gehen Sie zu **Einfügen** > **Komponenten** > **Importkomponente**. 
 
    ![Komponenten einfügen](media/insert-components-import.png "Komponenten einfügen")

4. Wählen Sie die Registerkarte **Code (experimentell)** aus, fügen Sie eine Komponente aus der Liste hinzu, und wählen Sie dann **Importieren** aus. Dadurch wird die Beispielkomponente im Menü **Komponenten** hinzugefügt.

    ![Beispielkomponente importieren](media/import-component-add-sample-component.png "Beispielkomponente importieren")

5. Navigieren Sie zu **Komponenten**, und wählen Sie die Komponente aus, um sie der App hinzuzufügen.

   ![Beispielkomponente hinzufügen](media/add-sample-component-from-list.png "Beispielkomponente hinzufügen")

## <a name="delete-a-code-component"></a>Löschen einer Codekomponente 

Wenn Sie eine Codekomponente aus einer Canvas-App löschen möchten, wählen Sie die Codekomponente, die Sie löschen möchten und dann die Schaltfläche **Löschen** aus dem Menü aus. Wenn die Codekomponente aus der App gelöscht wird, werden alle Codekomponentenelemente der App und dem App-Paket gelöscht. 

## <a name="update-existing-code-components"></a>Aktualisieren vorhandener Codekomponenten

Wenn Sie die Codekomponenten aktualisieren, geben wir das Attribut *Version* in der Manifestdatei an, damit die neuesten Änderungen in der Laufzeit wiedergegeben werden. Wenn Sie für Canvas-Apps die vorhandenen Codekomponenten aktualisieren, müssen Sie das Attribut *Version* nicht aktualisieren. Standardmäßig wählen Canvas-Apps die letzte Codekomponente aus und zeigen sie während der Laufzeit an. Nur eine einzige Version derselben Komponente kann in Canvas-Apps vorhanden sein.

> [!NOTE]
> Vorhandene Codekomponenten werden nur aktualisiert, sofern die App geschlossen oder in PowerApps Studio erneut geöffnet wird. Wenn Sie die App erneut öffnen, werden sie aufgefordert, die Codekomponenten zu aktualisieren. Wenn Sie die Codekomponenten einfach löschen oder sie wieder in die App hinzufügen, werden die Komponenten nicht aktualisiert.

## <a name="see-also"></a>Siehe auch

[Übersicht über das PowerApps component framework](overview.md)<br/>
[Beispielkomponente für die Implementierung](implementing-controls-using-typescript.md)

