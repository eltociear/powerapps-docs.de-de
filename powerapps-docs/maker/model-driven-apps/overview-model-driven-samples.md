---
title: Modellgesteuerte Beispiel-Apps
description: Informationen zum Abrufen, Anpassen und Entfernen von modellgesteuerten Beispiel-Apps
documentationcenter: na
author: mr-dang-msft
manager: kvivek
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/08/2018
ms.author: brdang
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 13ec511c692af8694012f94f881cb02ee1280ee2
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404505"
---
# <a name="model-driven-sample-apps"></a>Modellgesteuerte Beispiel-Apps

Verwenden Sie unter [powerapps.com](https://powerapps.com) eine Beispiel-App, um Designmöglichkeiten und Konzepte zu entdecken, die Sie anwenden können, wenn Sie Ihre eigenen Apps entwickeln. Jede Beispiel-App verwendet fiktive Daten, um ein Szenario aus der realen Welt darzustellen. 

Wenn Sie mehr erfahren möchten, sollten Sie die Dokumentation zu den einzelnen Beispiel-Apps lesen. 

![Beispiel-App zum Sammeln von Spenden](media/overview-model-driven-samples/fundraiser-app1.png)


## <a name="get-sample-apps"></a>Abrufen von Beispiel-Apps

Damit modellgesteuerte Apps ausgeführt oder verändert werden können, müssen diese Apps zuerst in einer Common Data Service-Datenbank bereitgestellt werden. Erstellen Sie zunächst eine Testumgebung und eine Datenbank, und achten Sie dabei darauf, das Feld **Include sample apps and data** (Beispiel-Apps und -Daten hinzufügen).

![Datenbank erstellen](media/overview-model-driven-samples/create-database1.png)


> [!IMPORTANT]
> Über diese Option werden alle in Ihrer Datenbank verfügbaren Beispiel-Apps installiert. Beispiel-Apps sind für das Lernen und Vorführen konzipiert und sollten nicht in Produktionsdatenbanken installiert werden. 

## <a name="customize-a-sample-app"></a>Anpassen einer Beispiel-App

1. Melden Sie sich bei [powerapps.com](https://powerapps.com) an.  

    

2. Zeigen Sie auf der Seite **Erstellen** auf die Beispiel-APP, und klicken Sie **dann auf diese APP erstellen**.

![Modell-Beispiel-App](media/overview-model-driven-samples/model-driven-create-page-sample.png)

3. Dann sollte sich der App-Designer öffnen, und Sie können aus mehreren Optionen zum Anpassen Ihrer App auswählen. 
4. Klicken Sie im Portal im linken Navigationsbereich auf **erweitert** , um zusätzliche Anpassungsoptionen zu erhalten.

## <a name="remove-sample-apps-and-data"></a>Entfernen von Beispiel-Apps und -Daten 
- Zum Löschen einer Beispiel-app muss die entsprechende [verwaltete Lösung](https://docs.microsoft.com/dynamics365/customer-engagement/developer/uninstall-delete-solution)gelöscht werden. 
- Wenn Sie die Lösung löschen, werden auch alle Beispieldaten gelöscht, die zu den benutzerdefinierten Entitäten der App gehören.
- Wenn Sie Anpassungen an der Beispiel-App vornehmen, entstehen möglicherweise [Abhängigkeiten](https://docs.microsoft.com/dynamics365/customer-engagement/developer/dependency-tracking-solution-components), die entfernt werden müssen, bevor die Lösung gelöscht wird.

### <a name="steps"></a>Schritte
1. Melden Sie sich beim [powerapps-Verwaltungs Portal](https://admin.powerapps.com)an.

2. Wählen Sie eine Umgebung aus.

3. Klicken Sie auf **Dynamics 365 Admin Center**. 

    ![Dynamics 365 Admin Center](media/overview-model-driven-samples/admin-center.png)

4. Suchen Sie Ihre Datenbank in der Liste, und klicken Sie auf **ÖFFNEN**.

    ![Datenbank auswählen](media/overview-model-driven-samples/select-database.png)

5. Navigieren Sie zu **Settings/Solutions** (Einstellungen/Lösungen).

6. Suchen Sie die Lösung zu der App, die gelöscht werden soll, und klicken Sie auf **Löschen**.

    ![Lösung löschen](media/overview-model-driven-samples/delete-solution.png)

*Stattdessen können Sie auch in der Liste der Lösungen navigieren, indem Sie im Maker-Portal auf **Erweitert** klicken, und aus der URL alle Zeichen löschen, die auf .dynamics.com/* folgen.

> [!IMPORTANT]
> Löschen Sie keine anderen Systemlösungen, wenn Sie nicht wissen, welche Folgen dies haben kann.

## <a name="install-or-uninstall-sample-data"></a>Installieren oder Deinstallieren der Beispieldaten
1. Führen Sie die oben aufgeführten Schritte 1 bis 4 aus.
2. Navigieren Sie zu **Settings/Data Management/Sample Data**.
3. Wenn Beispieldaten installiert sind, ist die Option zum Entfernen verfügbar. Andernfalls ist die Option zum Installieren verfügbar. 

    ![Beispieldaten entfernen](media/overview-model-driven-samples/remove-sample-data.png)




