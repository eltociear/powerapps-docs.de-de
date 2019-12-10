---
title: Erstellen einer Canvas-App aus Excel | Microsoft-Dokumentation
description: Verwenden von powerapps zum automatischen Erstellen einer Canvas-App mithilfe einer Excel-Datei, die in einem cloudspeicherkonto gespeichert ist
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/05/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2199d94938e51154d0f616f424f674c408277b52
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959424"
---
# <a name="create-a-canvas-app-from-excel-in-power-apps"></a>Erstellen einer Canvas-App aus Excel in Power apps

In diesem Thema erstellen Sie Ihre erste Canvas-app in Power Apps mithilfe von Daten aus einer Excel-Tabelle. Wählen Sie eine Excel-Datei aus, erstellen Sie eine APP, und führen Sie dann die APP aus, die Sie erstellt haben. Jede erstellte App umfasst Bildschirme zum Durchsuchen von Datensätzen, Anzeigen von Daten Satz Details und erstellen oder Aktualisieren von Datensätzen. Indem Sie eine App generieren, können Sie mithilfe von Excel-Daten schnell eine funktionierende App erstellen. Diese können Sie anschließend an Ihre Anforderungen anpassen. 

Die Excel-Datei muss sich in einem Cloudspeicherkonto (z.B. OneDrive, Google Drive oder Dropbox) befinden. In diesem Artikel wird „OneDrive for Business“ verwendet.

Wenn Sie nicht über eine Lizenz für Power apps verfügen, können Sie [sich kostenlos registrieren](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Voraussetzungen

Laden Sie die Datei [Flooring Estimates](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) in Excel herunter, und speichern Sie diese in Ihrem [Cloudspeicherkonto](connections/cloud-storage-blob-connections.md), um diesem Artikel genau zu folgen.

> [!IMPORTANT]
> Sie können eine eigene Excel-Datei verwenden, dafür müssen die Daten jedoch als Tabelle formatiert sein. Weitere Informationen finden Sie unter [Format a table (Formatieren einer Tabelle)](how-to-excel-tips.md). 

## <a name="create-the-app"></a>App erstellen

1. Melden Sie sich bei [powerapps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)an.

1. Zeigen Sie unter **Eigene App erstellen** auf **Mit Daten beginnen**, und wählen Sie dann **Diese App erstellen** aus.

    ![Option zum Erstellen einer App](./media/get-started-create-from-data/start-from-data.png)

1. Klicken oder tippen Sie auf der Kachel für Ihr Cloudspeicherkonto unter **Von Ihren Daten ausgehen** auf **Smartphonelayout**.

    ![Option zum Erstellen einer App](./media/get-started-create-from-data/odfb-tile.png)

1. Wenn Sie dazu aufgefordert werden, klicken Sie auf **Verbinden**, und geben Sie Ihre Anmeldeinformationen für dieses Konto ein.

1. Navigieren Sie unter **Choose an Excel file** zu **FlooringEstimates.xlsx**, und klicken oder tippen Sie darauf. 

1. Klicken oder tippen Sie unter **Choose a table** auf **FlooringEstimates**, und klicken oder tippen Sie anschließend auf **Connect**.

    ![Option zum Erstellen einer App](./media/get-started-create-from-data/choose-table.png)

## <a name="run-the-app"></a>Ausführen der App

1. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Klicken oder Tippen auf das Wiedergabe-Symbol in der Nähe der oberen rechten Ecke).

    ![Vorschau öffnen](./media/get-started-create-from-data/open-preview.png)

1. Ändern Sie die Sortierreihenfolge, indem Sie auf das Sortieren-Symbol in der oberen rechten Ecke klicken oder tippen.

    ![Sortieren-Symbol](./media/get-started-create-from-data/sort-icon.png)

1. Filtern Sie die Liste, indem Sie Zeichen in das Suchfeld eingeben und einfügen.

    Geben Sie z. b. **Honey** ein, oder fügen Sie ihn ein, um den einzigen Datensatz anzuzeigen, für den diese Zeichenfolge im Produktnamen, der Kategorie oder der Übersicht angezeigt wird.

    ![Filterbeispiel](./media/get-started-create-from-data/filter-example.png)

1. Einen Datensatz hinzufügen:

    1. Wählen Sie das Plus Symbol aus.

        ![Pluszeichen](./media/get-started-create-from-data/plus-icon.png)

    1. Fügen Sie beliebige Daten hinzu, und klicken Sie dann auf das Häkchensymbol, um die Änderungen zu speichern.

        ![Symbol "Speichern"](./media/get-started-create-from-data/save-icon.png)

1. Einen Datensatz bearbeiten:

    1. Wählen Sie den Pfeil für den Datensatz aus, den Sie bearbeiten möchten.

        ![Pfeil „Weiter“](./media/get-started-create-from-data/next-arrow.png)

    1. Klicken Sie auf das Stiftsymbol.

        ![Stiftsymbol](./media/get-started-create-from-data/pencil-icon.png)

    1. Aktualisieren Sie mindestens ein Feld, und klicken Sie dann auf das Häkchensymbol, um die Änderungen zu speichern.

        ![Symbol "Speichern"](./media/get-started-create-from-data/save-icon.png)

        Wählen Sie alternativ das Symbol Abbrechen aus, um die Änderungen zu verwerfen.

1. Löschen eines Datensatzes:

    1. Wählen Sie den nächsten Pfeil für den Datensatz aus, den Sie löschen möchten.

        ![Pfeil „Weiter“](./media/get-started-create-from-data/next-arrow.png)

    1. Wählen Sie das Papierkorb Symbol aus.

        ![Papierkorbsymbol](./media/get-started-create-from-data/trash-icon.png)

## <a name="next-steps"></a>Nächste Schritte

Passen Sie den Standardbildschirm zum Durchsuchen an Ihre Anforderungen an. Beispielsweise können Sie die Liste nur nach Produktnamen sortieren und Filtern, nicht nach Kategorie oder Übersicht.

> [!div class="nextstepaction"]
> [Anpassen des Standardbildschirms zum Durchsuchen](customize-layout-sharepoint.md)
