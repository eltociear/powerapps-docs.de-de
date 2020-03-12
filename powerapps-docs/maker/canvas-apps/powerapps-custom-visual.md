---
title: Powerapps-Visualisierung für Power BI | Microsoft-Dokumentation
description: Verfahren und Einschränkungen für das Einbetten einer Canvas-App, die die gleiche Datenquelle wie andere Berichtselemente in Power BI verwendet und ebenfalls gefiltert werden kann
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/11/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b3678c01210d5cb0398ce12e2111dba516404cfe
ms.sourcegitcommit: d500f44e77747a3244b6691ad9b3528e131dbfa5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2020
ms.locfileid: "79133604"
---
# <a name="power-apps-visual-for-power-bi"></a>Powerapps-Visualisierung für Power BI

Power BI ermöglicht Einblicke in die Daten und bessere Entscheidungsfindung, während mit Power apps Apps erstellt und verwendet werden können, die eine Verbindung mit Geschäftsdaten herstellen. Mithilfe der Visualisierung von powerapps können Sie kontextabhängige Daten an eine Canvas-App übergeben, die in Echtzeit aktualisiert wird, wenn Sie Änderungen am Bericht vornehmen. Dadurch können die Benutzer der App Einblicke in das Unternehmen gewinnen und innerhalb der Power BI-Berichte und -Dashboards Aktionen durchführen.

## <a name="using-the-power-apps-visual"></a>Verwenden der visuellen powerapps-Visualisierung

Sehen wir uns nun die Schritte an, die erforderlich sind, um das Visual apps-Visual in Ihrem Power BI Bericht zu verwenden.

1. Powerapps Visual ist standardmäßig im Power BI-Dienst verfügbar. Wenn Sie Power BI Desktop verwenden und nicht sehen, müssen Sie ein Upgrade auf die neueste Version von Power BI Desktop durchführen.

2. Fügen Sie dem Bericht die Visualisierung "powerapps" hinzu, und legen Sie die zugeordneten Datenfelder fest.

    ![Auswählen der Berichtsdaten](./media/powerapps-custom-visual/add-visual-set-data.png)

    Sie können eine vorhandene App auswählen oder eine neue erstellen, aber der Bericht muss mit dem Power BI-Dienst veröffentlicht und in Microsoft Edge oder Google Chrome geöffnet werden.

3.  Wenn Sie eine neue App erstellen, können Sie auswählen, in welcher Umgebung diese erstellt werden soll.

    ![Neue oder vorhandene App](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    Wenn Sie sich dafür entscheiden, eine vorhandene APP zu verwenden, werden Sie vom visuellen Element aufgefordert, die app in powerapps zu öffnen. Das visuelle Element richtet dann die erforderlichen Komponenten in der APP ein, damit Power BI Daten an Power apps senden kann.

    Wenn Sie eine neue APP erstellen, erstellt Power apps eine einfache APP mit den erforderlichen Komponenten, die bereits eingerichtet sind.

    > [!NOTE]
    > Sie müssen eine neue APP aus der powerapps-Visualisierung in Power BI Bericht erstellen, damit die `PowerBIIntegration.Refresh()`-Funktion in der app verfügbar ist.

    ![Neue App](./media/powerapps-custom-visual/new-app.png)

4. In powerapps Studio können Sie jetzt die Datenfelder verwenden, die Sie in Schritt 2 festgelegt haben. Das `PowerBIIntegration`-Objekt verhält sich wie jede andere schreibgeschützte Datenquelle oder Sammlung von powerapps. Sie können das Objekt verwenden, um ein beliebiges Steuerelement aufzufüllen oder um Steuerelemente mit anderen Datenquellen zu verknüpfen oder zu filtern.

    ![Benutzerdefinierte Formel](./media/powerapps-custom-visual/custom-formula.png)

    Diese Formel verknüpft Power BI-Daten mit der benutzerdefinierten Datenquelle: `LookUp(Customer,Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`.

   Der Power BI Bericht und die Instanz von powerapps Studio, die gestartet wurde, haben eine Live Datenverbindung gemeinsam. Obwohl beide offen sind, können Sie die Daten im Bericht filtern oder ändern, damit die aktualisierten Daten sofort in der app in powerapps Studio angezeigt werden.

5. Nachdem Sie die Erstellung oder Änderung Ihrer APP abgeschlossen haben, speichern und veröffentlichen Sie die app in powerapps, um Ihre APP im Power BI Bericht anzuzeigen.

6. Wenn Sie mit Ihren Änderungen zufrieden sind, stellen Sie sicher, dass Sie die powerapps-App für Benutzer Ihres Berichts freigeben und dann den Bericht speichern.

7. Dadurch haben Sie einen Bericht erstellt, in dem Ihre Benutzer Aktionen durchführen können, während Sie Einsicht in Ihre Daten haben.

    ![Bearbeiten eines Berichts](./media/powerapps-custom-visual/working-report.gif)

    Wenn Sie Änderungen an einer APP vornehmen müssen, öffnen Sie den Bericht im Bearbeitungsmodus, klicken oder tippen Sie auf **Weitere Optionen** ( **...** ) in der Visualisierung von powerapps, und wählen Sie **Bearbeiten**aus.

    ![Bearbeiten einer App](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-power-apps-visual"></a>Einschränkungen der visuellen powerapps-Visualisierung

Die folgenden Einschränkungen gelten für die Visual apps-Visualisierung:

- Wenn Sie die mit dem Visual verknüpften Datenfelder ändern, müssen Sie die App innerhalb des Power BI-Diensts bearbeiten, indem Sie auf die Auslassungspunkte (...) und dann auf **Bearbeiten** klicken. Andernfalls werden die Änderungen nicht an Power apps weitergegeben, und die APP verhält sich auf unerwartete Weise.
- Das Visual apps-Visual kann keine Aktualisierung von Power BI Berichten und Power BI Datenquellen innerhalb Power BI Desktop auslöst. Wenn Sie Daten aus der app in dieselbe Datenquelle wie den Bericht zurückschreiben, werden die Änderungen nicht sofort in Power BI Desktop angezeigt. Die Änderungen werden bei der nächsten geplanten Aktualisierung übernommen.
- Das Visual apps-Visual kann die Daten nicht filtern oder Daten an den Bericht zurücksenden.
- Sie müssen die powerapps-App getrennt von Ihrem Bericht freigeben. Erfahren Sie mehr über das Freigeben von [apps in powerapps](share-app.md).
- Die Visual apps-Visualisierung wird von Power BI-Berichtsserver nicht unterstützt.
- Die folgenden Einschränkungen gelten, wenn die `PowerBIIntegration.Refresh()`-Funktion verwendet wird:
    - Sie müssen eine neue APP aus Power apps-Visualisierung in Power BI Bericht erstellen, damit diese Funktion in der app verfügbar ist.
    - Sie müssen eine Quelle verwenden, die [directquery](https://docs.microsoft.com/power-bi/desktop-directquery-data-sources) unterstützt, und die Datenverbindung muss mithilfe der directquery-Methode erstellt werden.
- Power apps in Power BI Desktop stellen Daten für Power apps Studio bereit, wenn Sie Apps erstellen, aber nicht während der Bearbeitung. Verwenden Sie Power BI Web, um beim Bearbeiten von apps eine Vorschau der Daten anzuzeigen.
- Die Power BI Mobile App unterstützt das Mikrofon-Steuerelement in Power apps-Visuals nicht.

> [!NOTE]
> Es wird empfohlen, zuerst den Bericht auf dem Power BI-Dienst zu veröffentlichen und dann apps zu erstellen oder zu ändern.

## <a name="browser-support"></a>Browserunterstützung

In der folgenden Tabelle sind die Browserunterstützung für die Anzeige, Erstellung und Änderung von powerapps-Visualisierungen aufgeführt. Unterstützte Browser und Aktionen werden durch ein Häkchen (&check;) identifiziert.

|Browser|Anzeigen|Erstellen|Ändern
|-|-|-|-
|Microsoft Edge|&check;|&check;|&check;
|Internet Explorer 11|&check;
|Google Chrome|&check;|&check;|&check;
|Safari-\*|&check;
|Mozilla Firefox
|Alle anderen Browser

\* in Safari müssen Sie die standortübergreifende Überwachung aktivieren (**Einstellungen** > **Datenschutz**und Deaktivieren von **Standort übergreifender Überwachung**), um das visuelle Element von powerapps anzuzeigen.

## <a name="accessibility-support"></a>Barrierefreiheits Unterstützung

Führen Sie die folgenden Schritte aus, um die Visual apps-Visualisierung mithilfe der Tastatur zu navigieren:

1. Fokus Auswahl im Power BI Bericht für die gewünschte Visualisierung von powerapps.
2. Verwenden Sie die **Tab** -Taste auf der Tastatur, bis die Visualisierung hervorgehoben ist.
3. Verwenden Sie die Tastenkombination **Strg + Rechts** auf der Tastatur, um das visuelle Element einzugeben.
3. Verwenden Sie die **Tab** -Taste auf der Tastatur, bis die gewünschte Komponente des visuellen Elements ausgewählt ist.

Weitere Informationen finden Sie unter [Power BI-Dokumentation zur Barrierefreiheit]( https://docs.microsoft.com/power-bi/desktop-accessibility) .


## <a name="next-steps"></a>Nächste Schritte

* Befolgen Sie ein einfaches, [ausführliches Tutorial](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-powerapp).
* Sehen Sie sich unser [Video](https://aka.ms/powerappscustomvisualvideo)an.
