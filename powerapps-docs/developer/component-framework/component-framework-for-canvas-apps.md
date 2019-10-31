---
title: PowerApps component framework für Canvas-Apps | Microsoft-Dokumentation
description: Erstellen von Codekomponenten für Canvas-Apps
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 08/31/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
---

# <a name="powerapps-component-framework-for-canvas-apps"></a>PowerApps component framework für Canvas-Apps

> [!IMPORTANT]
> Diese Funktion ist weiterhin experimenteller Natur und standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Experimentelle und Vorschaufunktionen](../../maker/canvas-apps/working-with-experimental.md).

Das PowerApps component framework ermöglicht es App-Entwicklern, Codekomponenten für die Verwendung in einer App oder über Apps zu erstellen. Weitere Informationen: [Übersicht über das PowerApps component framework](overview.md) 

In dieser experimentellen Vorschau können App-Entwickler mit dem PowerApps component framework Codekomponenten erstellen, debuggen, importieren und zu Canvas-Apps mithilfe der PowerApps-CLI-Werkzeuge hinzuzufügen. Nur bestimmte APIs werden in dieser experimentellen Vorschau unterstützt. Es wird empfohlen, für jede API zu überprüfen, ob sie Canvas-Apps unterstützt oder nicht. 

> [!WARNING]
> Codekomponenten enthalten Code, der möglicherweise nicht von Microsoft generiert werden kann und ggf. auf Sicherheitstoken und Daten zugreifen kann. Wenn Sie Codekomponenten zu einer App hinzufügen, sollten Sie sicherstellen, dass die Codekomponentenlösungen von einer vertrauenswürdigen Quelle stammen.

## <a name="prerequisites"></a>Voraussetzungen

1. Es sind Systemadministratorrechte erforderlich, um die PowerApps-Komponentenfunktion in der Umgebung zu aktivieren.

> [!IMPORTANT]
> Standardmäßig ist das PowerApps component framework für modellgesteuerte Apps aktiviert.

## <a name="enable-powerapps-component-framework-feature"></a>Aktivieren der Funktion des PowerApps component framework

Um Codekomponenten zu einer App hinzuzufügen, müssen Sie die Funktion des PowerApps component framework in jeder Umgebung aktivieren, in der Sie sie verwenden möchten. So aktivieren Sie eine Umgebung für die Verwendung von Codekomponenten in ihren Apps:

1. Melden Sie sich bei [PowerApps](https://powerapps.microsoft.com/en-us/) an.

2. Klicken Sie auf das Symbol **Einstellungen** und dann auf **Admin Center**.
    
    ![Admin Center-Einstellungen](media/select-admin-center-from-settings.png "Admin Center-Einstellungen") 

3. Wählen Sie die Umgebung aus, in der Sie diese Funktion aktivieren möchten, und klicken Sie auf **...** und dann auf **Einstellungen**.

4. Wählen Sie auf der Registerkarte **Produkte** die Option **Funktionen** aus.

   ![Aktivieren von PCF](media/enable-pcf-feature.png "Aktivieren von PCF")

5. Aktivieren Sie in der Liste der verfügbaren Funktionen den Schalter unter dem **PowerApps component framework für Canvas-Apps**.

6. Öffnen Sie nun die App, der Sie die Codekomponente hinzufügen möchten, und navigieren Sie zu **Datei** >  **App-Einstellungen**. Wählen Sie dann **Erweiterte Einstellungen** aus.

   ![Aktivieren der Komponenten für PCF](media/enable-components-for-pcf.png "Aktivieren der Komponenten für PCF")
   
7. Aktivieren Sie den Schalter **Komponenten** unter dem Abschnitt **Experimentelles Feature**.

## <a name="implementing-code-components"></a>Implementieren von Codekomponenten

Nachdem Sie das Feature des PowerApps component framework in Ihrer Umgebung aktiviert haben, können Sie mit der Implementierung der Logik für Codekomponenten beginnen. Das Thema [Beispielkomponente für die Implementierung](implementing-controls-using-typescript.md) zeigt die schrittweise Vorgehensweise zum Erstellen von Codekomponenten von der Implementierung der benutzerdefinierten Logik, der Manifestdatei und des Debug-Prozesses über die Erstellung einer Lösungs-ZIP-Datei bis zum Importieren der Lösung in Common Data Service.

> [!NOTE]
> Die Implementierung von Codekomponenten ist für modellgesteuerte Apps und Canvas-Apps identisch (experimentelle Vorschau). Der einzige Unterschied ist das Hinzufügen der Codekomponenten. 

## <a name="add-components-to-a-canvas-app"></a>Hinzufügen von Komponenten zu einer Canvas-App

So fügen Sie Codekomponenten zu einer Canvas-App hinzu:

> [!NOTE]
> Um Codekomponenten zu einem Feld oder einer Entität für modellgesteuerte Apps hinzuzufügen, lesen Sie [Hinzufügen von Codekomponenten zu modellgesteuerten Apps](add-custom-controls-to-a-field-or-entity.md)

1. Navigieren zu PowerApps Studio.
2. Erstellen Sie eine neue Canvas-App, oder bearbeiten Sie eine vorhandene App, die Sie zur Codekomponente hinzufügen möchten.

   > [!IMPORTANT]
   > Stellen Sie sicher, dass die ZIP-Datei der Lösung bereits in Common Data Service [importiert](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/import-update-export-solutions) wurde, bevor Sie mit dem nächsten Schritt fortfahren.

3. Klicken Sie auf **Einfügen** > **Komponenten** > **Komponente importieren**. 
 
    ![Einfügen der Komponenten](media/insert-components-import.png "Einfügen der Komponenten")

4. Wählen Sie die Registerkarte **Code (experimentell)** aus, fügen Sie eine Komponente aus der Liste hinzu, und klicken Sie auf **Importieren**. Dadurch wird die Beispielkomponente im Menü **Komponenten** hinzugefügt.

    ![Beispiel zum Importieren von Komponenten](media/import-component-add-sample-component.png "Beispiel zum Importieren von Komponenten")

5. Navigieren Sie zu **Komponenten**, und wählen Sie die Komponente aus, um sie der App hinzuzufügen.

   ![Beispiel zum Hinzufügen von Komponenten](media/add-sample-component-from-list.png "Beispiel zum Hinzufügen von Komponenten")

## <a name="delete-a-code-component"></a>Löschen einer Codekomponente 

Um eine Codekomponente aus einer Canvas-App zu löschen, wählen Sie die Codekomponente aus, und wählen Sie die Schaltfläche **Löschen** im Menü. Wenn die Codekomponente von der App gelöscht wird, werden alle Codekomponentenelemente von der App und dem App-Paket gelöscht. 

## <a name="updating-existing-code-components"></a>Aktualisieren vorhandener Codekomponenten

Wenn Sie Codekomponenten aktualisieren, geben Sie in der Manifestdatei das Attribut *Version* an, sodass aktuelle Änderungen während der Laufzeit angezeigt werden. Wenn Sie für Canvas-Apps die vorhandenen Codekomponenten aktualisieren, müssen Sie das Attribut *Version* nicht aktualisieren. Standardmäßig wählen Canvas-Apps die letzte Codekomponente aus und zeigen sie während der Laufzeit an. Nur eine einzige Version derselben Komponente kann in Canvas-Apps vorhanden sein.

> [!NOTE]
> Vorhandene Codekomponenten werden nur dann aktualisiert, wenn die App geschlossen oder erneut in PowerApps Studio geöffnet wird. Wenn Sie die App erneut öffnen, werden sie aufgefordert, die Codekomponenten zu aktualisieren. Wenn Sie die Codekomponenten einfach löschen oder sie wieder in die App hinzufügen, werden die Komponenten nicht aktualisiert.

## <a name="see-also"></a>Siehe auch

[Übersicht über das PowerApps component framework](overview.md)<br/>
[Beispielkomponente für die Implementierung](implementing-controls-using-typescript.md)

