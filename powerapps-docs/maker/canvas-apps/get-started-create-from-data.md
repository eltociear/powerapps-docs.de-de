---
title: Generieren einer Canvas-App aus Excel | Microsoft-Dokumentation
description: Verwenden von PowerApps zum automatischen Generieren einer Canvas-App mithilfe einer Excel-Datei, die in einem Cloudspeicherkonto gespeichert ist
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/14/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7ab85f09ebf88c30b35c963242895cd74ca6a966
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61555047"
---
# <a name="generate-a-canvas-app-from-excel-in-powerapps"></a>Generieren einer Canvas-App aus Excel in PowerApps

In diesem Artikel generieren Sie Ihre erste Canvas-App automatisch in PowerApps, indem Sie Daten aus einer Excel-Tabelle verwenden. Sie wählen eine Excel-Datei aus, generieren eine App und führen die generierte App dann aus. Jede generierte App enthält Bildschirme zum Durchsuchen von Datensätzen, Anzeigen von Details der Datensätze sowie zum Erstellen oder Aktualisieren von Datensätzen. Indem Sie eine App generieren, können Sie mithilfe von Excel-Daten schnell eine funktionierende App erstellen. Diese können Sie anschließend an Ihre Anforderungen anpassen. 

Die Excel-Datei muss sich in einem Cloudspeicherkonto (z.B. OneDrive, Google Drive oder Dropbox) befinden. In diesem Artikel wird „OneDrive for Business“ verwendet.

Wenn Sie nicht eine Lizenz für PowerApps verfügen, können Sie sich [kostenlos registrieren](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Voraussetzungen

Laden Sie die Datei [Flooring Estimates](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) in Excel herunter, und speichern Sie diese in Ihrem [Cloudspeicherkonto](connections/cloud-storage-blob-connections.md), um diesem Artikel genau zu folgen.

> [!IMPORTANT]
> Sie können eine eigene Excel-Datei verwenden, dafür müssen die Daten jedoch als Tabelle formatiert sein. Weitere Informationen finden Sie unter [Format a table (Formatieren einer Tabelle)](how-to-excel-tips.md). 

## <a name="generate-the-app"></a>Generieren der App

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

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

    Beispielsweise geben oder fügen Sie **Honig** dem einzigen Eintrag für die angezeigt wird, dass die Zeichenfolge im Namen des Produkts, Kategorie oder Übersicht angezeigt wird.

    ![Filterbeispiel](./media/get-started-create-from-data/filter-example.png)

1. Fügen Sie einen Eintrag hinzu:

    1. Wählen Sie das Pluszeichen.

        ![Pluszeichen](./media/get-started-create-from-data/plus-icon.png)

    1. Fügen Sie beliebige Daten, die Sie möchten, und wählen Sie dann auf das Häkchen, um die Änderungen zu speichern.

        ![Symbol "Speichern"](./media/get-started-create-from-data/save-icon.png)

1. Bearbeiten eines Datensatzes:

    1. Wählen Sie den Pfeil für den Datensatz, den Sie bearbeiten möchten.

        ![Pfeil „Weiter“](./media/get-started-create-from-data/next-arrow.png)

    1. Wählen Sie das Stiftsymbol.

        ![Stiftsymbol](./media/get-started-create-from-data/pencil-icon.png)

    1. Aktualisieren Sie ein oder mehrere Felder aus, und wählen Sie dann auf das Häkchen, um die Änderungen zu speichern.

        ![Symbol "Speichern"](./media/get-started-create-from-data/save-icon.png)

        Wählen Sie alternativ das Symbol "Abbrechen", um Ihre Änderungen zu verwerfen.

1. Löschen Sie Datensatz:

    1. Wählen Sie den weiter-Pfeil für den Datensatz, den Sie löschen möchten.

        ![Pfeil „Weiter“](./media/get-started-create-from-data/next-arrow.png)

    1. Wählen Sie das Papierkorbsymbol.

        ![Papierkorbsymbol](./media/get-started-create-from-data/trash-icon.png)

## <a name="next-steps"></a>Nächste Schritte

Passen Sie den Standardbildschirm zum Durchsuchen an Ihre Anforderungen an. Sie können z. B. sortieren und Filtern Sie die Liste nach Produktname nur, nicht auf Kategorie oder Übersicht.

> [!div class="nextstepaction"]
> [Anpassen des Standardbildschirms zum Durchsuchen](customize-layout-sharepoint.md)
