---
title: Benutzerdefinierte PowerApps-Visuals für Power BI | Microsoft-Dokumentation
description: Verfahren und Einschränkungen für das Einbetten einer Canvas-App, die die gleiche Datenquelle wie andere Berichtselemente in Power BI verwendet und ebenfalls gefiltert werden kann
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/30/2019
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 562811ebce59660d6033585868afd42da46442d5
ms.sourcegitcommit: 25a85b462515cb64f3f2b114864a682abf803f4a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2019
ms.locfileid: "70213921"
ms.PowerAppsDecimalTransform: true
---
# <a name="powerapps-custom-visual-for-power-bi"></a>Benutzerdefinierte PowerApps-Visuals für Power BI

Power BI ermöglicht Einblicke in die Daten und eine bessere Entscheidungsfindung, während durch PowerApps jeder Apps erstellen und verwenden kann, die mit Unternehmensdaten verbunden werden. Wenn Sie das benutzerdefinierte PowerApps-Visual verwenden, können Sie kontextabhängige Daten an eine Canvas-App übergeben, die in Echtzeit aktualisiert wird, während Sie Änderungen am Bericht vornehmen. Dadurch können die Benutzer der App Einblicke in das Unternehmen gewinnen und innerhalb der Power BI-Berichte und -Dashboards Aktionen durchführen.

## <a name="using-the-powerapps-custom-visual"></a>Verwenden des benutzerdefinierten PowerApps-Visuals

Im Folgenden werden die erforderlichen Schritte für das Verwenden des benutzerdefinierten PowerApps-Visuals in Ihren Power BI-Berichten erläutert.

1. Rufen Sie das benutzerdefinierte Visual von [AppSource](https://appsource.microsoft.com/product/power-bi-visuals/WA104381378?tab=Overview) ab, oder importieren Sie es direkt in den Power BI-Dienst.

    ![Benutzerdefinierte Visuals im Marketplace](./media/powerapps-custom-visual/powerapps-store.png) 

2. Fügen Sie das PowerApps-Visual zu Ihrem Bericht hinzu, und legen Sie die Datenfelder fest, die mit diesem verknüpft sind.

    ![Auswählen der Berichtsdaten](./media/powerapps-custom-visual/add-visual-set-data.png)

    Sie können eine vorhandene App auswählen oder eine neue erstellen, aber der Bericht muss mit dem Power BI-Dienst veröffentlicht und in Microsoft Edge oder Google Chrome geöffnet werden.

3.  Wenn Sie eine neue App erstellen, können Sie auswählen, in welcher Umgebung diese erstellt werden soll.

    ![Neue oder vorhandene App](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    Wenn Sie eine vorhandene App verwenden, fordert das Visual Sie dazu auf, die App in PowerApps zu öffnen. Das Visual richtet anschließend die erforderlichen Komponenten in Ihrer App ein, sodass Power BI Daten an PowerApps senden kann.

    Wenn Sie eine neue App erstellen, erstellt PowerApps eine einfache App mit den bereits eingerichteten erforderlichen Komponenten.

    ![Neue App](./media/powerapps-custom-visual/new-app.png)

4. In PowerApps Studio können Sie nun die Datenfelder verwenden, die Sie in Schritt 2 festgelegt haben. Die `PowerBIIntegration`-Objekte fungieren wie jede andere schreibgeschützte PowerApps-Datenquelle oder -Auflistung. Sie können das Objekt verwenden, um ein beliebiges Steuerelement aufzufüllen oder um Steuerelemente mit anderen Datenquellen zu verknüpfen oder zu filtern.

    ![Benutzerdefinierte Formel](./media/powerapps-custom-visual/custom-formula.png)

    Diese Formel verknüpft Power BI-Daten mit der benutzerdefinierten Datenquelle: `LookUp(Customer;Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`.

   Der Power BI-Bericht und die gestartete Instanz von PowerApps Studio verwenden eine gemeinsame Livedatenverbindung. Während beide Programme geöffnet sind, können Sie filtern oder Daten in Ihrem Bericht ändern. Sie werden dann feststellen, dass die aktualisierten Daten sofort in Ihrer App in PowerApps Studio angezeigt werden.

5. Nachdem Sie mit dem Erstellen oder Aktualisieren Ihrer App fertig sind, speichern Sie die App, und veröffentlichen Sie diese in PowerApps, damit sie im Power BI-Bericht angezeigt wird.

6. Sobald Sie mit Ihren Änderungen zufrieden sind, geben Sie die PowerApps-App für die Benutzer Ihres Berichts frei, und speichern Sie Ihren Bericht anschließend.

7. Dadurch haben Sie einen Bericht erstellt, in dem Ihre Benutzer Aktionen durchführen können, während Sie Einsicht in Ihre Daten haben.

    ![Bearbeiten eines Berichts](./media/powerapps-custom-visual/working-report.gif)

    Wenn Sie Änderungen an einer App vornehmen müssen, öffnen Sie den Bericht im Bearbeitungsmodus, klicken oder tippen Sie im PowerApps-Visual auf **Weitere Optionen** ( **...** ), und klicken Sie dann auf **Bearbeiten**.

    ![Bearbeiten einer App](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-powerapps-custom-visual"></a>Einschränkungen des benutzerdefinierten PowerApps-Visuals

Die folgenden Einschränkungen gelten für die benutzerdefinierte powerapps-Visualisierung:

- Wenn Sie die mit dem Visual verknüpften Datenfelder ändern, müssen Sie die App innerhalb des Power BI-Diensts bearbeiten, indem Sie auf die Auslassungspunkte (...) und dann auf **Bearbeiten** klicken. Andernfalls werden die Änderungen nicht in PowerApps übernommen, und die App weist unerwartetes Verhalten auf.
- Das benutzerdefinierte powerapps-Visual kann keine Aktualisierung von Power BI Berichten und Power BI Datenquellen innerhalb Power BI Desktop auslöst. Wenn Sie Daten aus der app in dieselbe Datenquelle wie den Bericht zurückschreiben, werden die Änderungen nicht sofort in Power BI Desktop angezeigt. Die Änderungen werden bei der nächsten geplanten Aktualisierung übernommen.
- Das benutzerdefinierte PowerApps-Visual kann die Daten nicht filtern oder wieder an den Bericht senden.
- Sie müssen die PowerApps-App getrennt von Ihrem Bericht freigeben. Weitere Informationen dazu finden Sie unter [sharing apps in PowerApps (Freigeben von Apps in PowerApps)](share-app.md).
- Power BI-Berichtsserver und die Mobile App für Power BI unterstützen die benutzerdefinierte powerapps-Visualisierung nicht.
- Wenn Sie die powerbiintegration. Refresh ()-Funktion verwenden, müssen Sie eine Quelle verwenden, die [directquery](https://docs.microsoft.com/en-us/power-bi/desktop-directquery-data-sources) unterstützt, und die Datenverbindung muss mithilfe der directquery-Methode erstellt werden.

> [!NOTE]
> Es wird empfohlen, zuerst den Bericht auf dem Power BI-Dienst zu veröffentlichen und dann apps zu erstellen oder zu ändern.

## <a name="browser-support"></a>Browser Unterstützung

In der folgenden Tabelle sind die Browserunterstützung für das anzeigen, erstellen und Ändern von Aktionen der benutzerdefinierten powerapps-Visualisierung aufgeführt. Unterstützte Browser und Aktionen werden durch ein Häkchen &check; () identifiziert.

|Browser|Ansicht|Stelle|Veränderung
|-|-|-|-
|Microsoft Edge|&check;|&check;|&check;
|Internet Explorer 11|&check;
|Google Chrome|&check;|&check;|&check;
|SK|&check;
|Mozilla Firefox
|Alle anderen Browser

## <a name="next-steps"></a>Nächste Schritte

* Befolgen Sie ein einfaches, [ausführliches Tutorial](embed-powerapps-powerbi.md).
* Sehen Sie sich unser [Video](https://aka.ms/powerappscustomvisualvideo)an.
