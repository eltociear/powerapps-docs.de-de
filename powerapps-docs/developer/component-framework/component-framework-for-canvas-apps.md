---
title: Powerapps-Komponenten Framework für Canvas-apps | Microsoft-Dokumentation
description: Erstellen von Code Komponenten für Canvas-apps
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
ms.openlocfilehash: e1c6b4bad1280bdabf8c27e30396b368276ff10b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347220"
---
# <a name="powerapps-component-framework-for-canvas-apps"></a>Powerapps-Komponenten Framework für Canvas-apps

> [!IMPORTANT]
> Diese Funktion ist in der Standardeinstellung immer noch experimentell und deaktiviert. Weitere Informationen finden Sie unter [experimentelle Features und Vorschau Features](../../maker/canvas-apps/working-with-experimental.md).

Mit dem powerapps-Komponenten Framework können App-Entwickler Code Komponenten erstellen, die in einer APP oder in den apps verwendet werden. Weitere Informationen: [Übersicht über das powerapps-Komponenten Framework](overview.md) 

In dieser experimentellen Vorschau ermöglicht das powerapps-Komponenten Framework es App-Herstellern, Code Komponenten zu erstellen, Sie zu debuggen, zu importieren und zu Canvas-Apps mithilfe der CLI-Tools von powerapps hinzuzufügen. In dieser experimentellen Vorschau werden nur bestimmte APIs unterstützt. Es wird empfohlen, jede API zu überprüfen, um zu bestimmen, ob Sie Canvas-Apps unterstützt. 

> [!WARNING]
> Code Komponenten enthalten Code, der möglicherweise nicht von Microsoft generiert wird und potenziell auf Sicherheits Token und Daten zugreifen kann. Stellen Sie beim Hinzufügen von Code Komponenten zu einer APP sicher, dass die Code Komponentenlösungen von einer vertrauenswürdigen Quelle stammen.

## <a name="prerequisites"></a>Voraussetzungen

System Administrator Berechtigungen sind erforderlich, um die Funktion "powerapps-Komponente" in der Umgebung zu aktivieren.

> [!IMPORTANT]
> Standardmäßig ist das powerapps-Komponenten Framework für Modell gesteuerte apps aktiviert.

## <a name="enable-powerapps-component-framework-feature"></a>Powerapps-Komponenten Framework-Feature aktivieren

Um einer APP Code Komponenten hinzuzufügen, müssen Sie die Funktion "powerapps-Komponenten Framework" in jeder Umgebung aktivieren, in der Sie Sie verwenden möchten. So aktivieren Sie eine Umgebung, um Code Komponenten in ihren apps zu verwenden:

1. Melden Sie sich bei [PowerApps](https://powerapps.microsoft.com/en-us/) an.

2. Wählen Sie das Symbol **Einstellungen** aus, und wählen Sie dann **Admin Center**aus.
    
    ![Einstellungen und Admin Center](media/select-admin-center-from-settings.png "-Einstellungen und Admin Center") 

3. Wählen Sie die Umgebung aus, in der Sie dieses Feature aktivieren möchten, wählen Sie die Auslassungs Punkte ( **...** ) aus, und wählen Sie dann **Einstellungen**aus.

4. Wählen Sie auf der Registerkarte **Produkte** die Option **Features**aus.

   ![Aktivieren von powerapps Component Framework](media/enable-pcf-feature.png "Aktivieren von powerapps-Komponenten Framework")

5. Legen Sie in der Liste der verfügbaren Features **für Canvas-apps in powerapps Component Framework**den Switch auf **on** fest.

6. Öffnen Sie nun die APP, der Sie die Code Komponente hinzufügen möchten, und navigieren Sie zu **Datei**  > **App-Einstellungen** , und wählen Sie **Erweiterte Einstellungen**aus.

   ![Aktivieren von Komponenten für das powerapps-Komponenten Framework](media/enable-components-for-pcf.png "Aktivieren von Komponenten für das powerapps") -Komponenten Framework
   
7. Schalten Sie den **Komponenten** Wechsel **im Abschnitt** " **experimentelle Funktion** " auf ein.

## <a name="implementing-code-components"></a>Implementieren von Code Komponenten

Nachdem Sie das Feature "powerapps-Komponenten Framework" in Ihrer Umgebung aktiviert haben, können Sie mit der Implementierung der Logik für Code Komponenten beginnen. Das Thema [Implementieren von Beispiel Komponenten](implementing-controls-using-typescript.md) veranschaulicht den Schritt-für-Schritt-Prozess zum Erstellen von Code Komponenten, die die benutzerdefinierte Logik und die Manifest-Datei implementieren, den Debugprozess ausführen, eine Projektmappen-ZIP-Datei erstellen und die Lösung in Common importieren Datendienst.

> [!NOTE]
> Das Implementieren von Code Komponenten ist für Modell gesteuerte apps und Canvas-apps identisch (experimentelle Vorschau). Der einzige Unterschied besteht darin, die Code Komponenten hinzuzufügen. 

## <a name="add-components-to-a-canvas-app"></a>Hinzufügen von Komponenten zu einer Canvas-App

> [!NOTE]
> Informationen zum Hinzufügen von Code Komponenten zu einem Feld oder einer Entität für Modell gesteuerte apps finden Sie unter [Hinzufügen von Code Komponenten zu Modell gesteuerten apps](add-custom-controls-to-a-field-or-entity.md) .

So fügen Sie einer Canvas-app Code Komponenten hinzu:

1. Navigieren Sie zu PowerApps Studio.
2. Erstellen Sie eine neue Canvas-APP, oder bearbeiten Sie eine vorhandene APP, der Sie die Code Komponente hinzufügen möchten.

   > [!IMPORTANT]
   > Stellen Sie sicher, dass die ZIP-Datei der Projekt Mappe bereits in Common Data Service [importiert](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/import-update-export-solutions) wurde, bevor Sie mit dem nächsten Schritt fortfahren.

3. Wechseln Sie zu **Insert**  > **Components**  > **Import Component**. 
 
    Komponenten(media/insert-components-import.png "Einfügen") ![Komponenten einfügen]

4. Wählen Sie die Registerkarte **Code (experimentell)** aus, fügen Sie eine Komponente aus der Liste hinzu, und klicken Sie dann auf **importieren**. Dadurch wird die Beispiel Komponente im Menü **Komponenten** hinzugefügt.

    Beispiel Komponente zum Importieren von ![Beispiel Komponenten](media/import-component-add-sample-component.png "importieren")

5. Navigieren Sie zu **Komponenten** , und wählen Sie die Komponente aus, um Sie der APP hinzuzufügen.

   Beispiel Komponente hinzufügen ![Beispiel](media/add-sample-component-from-list.png "Komponente hinzu") fügen

## <a name="delete-a-code-component"></a>Löschen einer Code Komponente 

Wenn Sie eine Code Komponente aus einer Canvas-app löschen möchten, wählen Sie die zu löschende Code Komponente aus, und wählen Sie dann im Menü die Schaltfläche **Löschen** aus. Wenn die Code Komponente aus der APP gelöscht wird, werden alle Code Komponenten Elemente aus der APP und dem App-Paket gelöscht. 

## <a name="update-existing-code-components"></a>Aktualisieren vorhandener Code Komponenten

Wenn Sie die Code Komponenten aktualisieren, geben wir das *Versions* Attribut in der Manifest-Datei an, damit die aktuellen Änderungen in der Laufzeit übernommen werden. Wenn Sie für Canvas-Apps die vorhandenen Code Komponenten aktualisieren, müssen Sie das *Versions* Attribut nicht aktualisieren. Der Canvas-app-Code übernimmt die neueste Code Komponente und zeigt Sie zur Laufzeit an. In Canvas-apps kann nur eine einzige Version der gleichen Komponente vorhanden sein.

> [!NOTE]
> Vorhandene Code Komponenten werden nur aktualisiert, wenn die app in PowerApps Studio geschlossen oder erneut geöffnet wird. Wenn Sie die APP erneut öffnen, werden Sie aufgefordert, die Code Komponenten zu aktualisieren. Wenn Sie die Code Komponenten einfach löschen oder die Code Komponente wieder in der APP hinzufügen, werden die Komponenten nicht aktualisiert.

## <a name="see-also"></a>Siehe auch

[Übersicht über das powerapps-Komponenten Framework](overview.md)<br/>
[Implementieren der Beispiel Komponente](implementing-controls-using-typescript.md)

