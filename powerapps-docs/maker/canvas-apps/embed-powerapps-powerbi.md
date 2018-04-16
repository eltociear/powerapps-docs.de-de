---
title: Einbetten einer neuen App in einen Power BI-Bericht | Microsoft-Dokumentation
description: Einbetten einer App mit derselben Datenquelle, die wie andere Berichtselemente gefiltert werden kann
services: powerapps
suite: powerapps
documentationcenter: na
author: mgblythe
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: tutorial
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/15/2018
ms.author: mblythe
ms.openlocfilehash: 839a9ce79f86fccd9fb91afe3938cc76160f0c08
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-embed-a-new-app-in-a-power-bi-report"></a>Tutorial: Einbetten einer neuen App in einen Power BI-Bericht

Mithilfe von Power BI können Sie die Funktionen erweitern, indem Sie *benutzerdefinierte Visuals* zu einem Bericht hinzufügen. In diesem Tutorial werden benutzerdefinierte PowerApps-Visuals verwendet, um eine neue App zu erstellen, die in einen Beispielbericht eingebettet ist. Diese App interagiert mit anderen Elementen in diesem Bericht.

Wenn Sie kein PowerApps-Abonnement besitzen, erstellen Sie ein [kostenloses Konto](../signup-for-powerapps.md), bevor Sie beginnen.

In diesem Tutorial erhalten Sie Informationen zu den folgenden Vorgängen:
> [!div class="checklist"]
> * Importieren von benutzerdefinierten PowerApps-Visuals in einen Power BI-Bericht
> * Erstellen einer neuen App, die Daten aus dem Bericht verwendet
> * Abrufen der App in dem Bericht

## <a name="prerequisites"></a>Voraussetzungen

* [Google Chrome](https://www.google.com/chrome/browser/) oder [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge)
* Ein [Power BI-Abonnement](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi), für das das [Analysebeispiel für Opportunity](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample) installiert ist.
* Ein Grundverständnis der Vorgehensweise beim [Erstellen von Apps in PowerApps](data-platform-create-app-scratch.md) und beim [Bearbeiten von Power BI-Berichten](https://docs.microsoft.com/power-bi/service-the-report-editor-take-a-tour).

## <a name="import-the-powerapps-custom-visual"></a>Importieren des benutzerdefinierten PowerApps-Visuals

Importieren Sie als ersten Schritt das benutzerdefinierte PowerApps-Visual, damit Sie es im Beispielbericht verwenden können.

1. Klicken oder tippen Sie im Analysebeispiel für Opportunity auf die Registerkarte **Upcoming Opportunities** (Anstehende Verkaufschancen).

2. Klicken oder tippen Sie im oberen Bereich auf **Bericht bearbeiten**.

3. Klicken oder tippen Sie im Bereich **Visualisierungen** auf die Auslassungspunkte (**...**) und anschließend auf **Aus Marketplace importieren**. 

    ![Aus Marketplace importieren](media/embed-powerapps-powerbi/import-visual.png)

4. Suchen Sie auf der Anzeige **Power BI-Visuals** nach „PowerApps“, und klicken oder tippen Sie anschließend auf **Hinzufügen**. Power BI fügt dann im unteren Bereich der **Visualisierungen** ein Symbol für benutzerdefinierte Visuals hinzu.

    ![Symbol für benutzerdefinierte PowerApps-Visuals](media/embed-powerapps-powerbi/powerapps-icon.png)

5. Speichern Sie den Bericht.

## <a name="create-a-new-app"></a>Erstellen einer neuen App
Im Folgenden erfahren Sie, wie Sie das benutzerdefinierte Visual zu Ihrem Bericht hinzufügen und eine neue App erstellen können, die auf Daten aus dem Bericht basiert. Wenn Sie die App erstellen, wird PowerApps Studio mit einer Livedatenverbindung zwischen PowerApps und Power BI gestartet.

1. Bewegen Sie einige Berichtskacheln, und ändern Sie deren Größe, um Platz für eine App zu schaffen.

    ![Berichtskacheln bewegen und deren Größe ändern](media/embed-powerapps-powerbi/move-resize.png)

2. Klicken oder tippen Sie auf das Symbol des benutzerdefinierten PowerApps-Visuals, und ändern Sie anschließend die Größe der Kachel, damit diese an die von Ihnen vorgesehene Stelle passt.

3. Wählen Sie im Bereich **Felder** **Name**, **Produktcode** und **Vertriebsphase** aus. 

    ![Felder auswählen](media/embed-powerapps-powerbi/select-fields.png)

4. Wählen Sie in der Kachel für das benutzerdefinierte Visual eine PowerApps-Umgebung aus, in der Sie die App erstellen wollen. Klicken oder tippen Sie anschließend auf **Neu erstellen**.

    ![Neue Rolle erstellen](media/embed-powerapps-powerbi/create-new-app.png)

    In PowerApps Studio können Sie sehen, dass eine Basis-App erstellt wurde. Es wird ein *Katalog* angezeigt, in dem eins der in Power BI ausgewählten Felder aufgeführt wird.

5.  Ändern Sie die Größe des Katalogs, sodass dieser nur die Hälfte des Bildschirms einnimmt. 

6. Klicken oder tippen Sie links auf **Screen1**, und legen Sie anschließend die **Fill**-Eigenschaft der Anzeige auf „Hellblau“ fest, damit diese im Bericht besser zu erkennen ist.

    ![App mit Katalog, dessen Größe geändert wurde](media/embed-powerapps-powerbi/app-gallery.png)

6. Fügen Sie unterhalb des Katalogs ein Bezeichnungssteuerelement hinzu. Legen Sie dabei für die **Text**-Eigenschaft `"Opportunity Count: " & CountRows(Gallery1.AllItems)` fest. Jetzt sollte die Gesamtanzahl der Verkaufsmöglichkeiten im Dataset angezeigt werden.

    ![Anzahl der Verkaufsmöglichkeiten](media/embed-powerapps-powerbi/opportunity-count.png)

7. Speichern Sie die App mit dem Namen „Opportunies“ (Verkaufsmöglichkeiten). 


## <a name="view-the-app-in-the-report"></a>Abrufen der App in dem Bericht
Die App ist jetzt in dem Bericht verfügbar und interagiert mit anderen Visuals, die die gleiche Datenquelle haben.

Klicken Sie im Power BI-Bericht im Slicer auf **Jan**. Dadurch wird der gesamte Bericht einschließlich der Daten in der App gefiltert.

![Gefilterter Bericht](media/embed-powerapps-powerbi/filtered-report.png)

Achten Sie darauf, dass die Anzahl der Verkaufsmöglichkeiten in der App mit der Anzahl übereinstimmt, die im oberen linken Bereich des Berichts angezeigt wird. Sie können auch andere Elemente aus dem Bericht auswählen. Dann werden die Daten in der App aktualisiert.


## <a name="clean-up-resources"></a>Bereinigen von Ressourcen
Wenn Sie das Analysebeispiel für Opportunity nicht mehr verwenden möchten, können Sie das Dashboard, den Bericht und das Dataset löschen.


## <a name="next-steps"></a>Nächste Schritte
In diesem Tutorial haben Sie Informationen zu den folgenden Vorgängen erhalten:
> [!div class="checklist"]
> * Importieren von benutzerdefinierten PowerApps-Visuals in einen Power BI-Bericht
> * Erstellen einer neuen App, die Daten aus dem Bericht verwendet
> * Abrufen der App in dem Bericht

Gehen Sie weiter zum nächsten Artikel, wenn Sie mehr erfahren möchten.
> [!div class="nextstepaction"]
> [Benutzerdefinierte PowerApps-Visuals für Power BI](powerapps-custom-visual.md)

