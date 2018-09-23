---
title: Modellgesteuerte Beispiel-Apps
description: Informationen zum Abrufen, Anpassen und Entfernen von modellgesteuerten Beispiel-Apps
documentationcenter: na
author: caburk
manager: kvivek
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/08/2018
ms.author: caburk
ms.openlocfilehash: 0b34a32281fb4f64bc918de81b3920edf5a7000b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39664425"
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

1. Melden Sie sich unter [powerapps.com](https://powerapps.com) an, und wählen Sie als Designmodus **Modellgesteuert** aus. 

    ![Designmodus auswählen](media/overview-model-driven-samples/choose-design-mode.png)

2. Zeigen Sie auf der Startseite auf die Beispiel-App, und klicken Sie auf **Anpassen**.
3. Dann sollte sich der App-Designer öffnen, und Sie können aus mehreren Optionen zum Anpassen Ihrer App auswählen. 
4. Klicken Sie im Portal im Navigationsbereich links auf **Erweitert**, wenn Sie zusätzliche Anpassungsoptionen benötigen.

## <a name="remove-sample-apps-and-data"></a>Entfernen von Beispiel-Apps und -Daten 
- Wenn Sie eine Beispiel-App löschen möchten, müssen Sie auch die zugehörige [verwaltete Lösung](https://docs.microsoft.com/dynamics365/customer-engagement/developer/uninstall-delete-solution) löschen. 
- Wenn Sie die Lösung löschen, werden auch alle Beispieldaten gelöscht, die zu den benutzerdefinierten Entitäten der App gehören.
- Wenn Sie Anpassungen an der Beispiel-App vornehmen, entstehen möglicherweise [Abhängigkeiten](https://docs.microsoft.com/dynamics365/customer-engagement/developer/dependency-tracking-solution-components), die entfernt werden müssen, bevor die Lösung gelöscht wird.

### <a name="steps"></a>Schritte
1. Melden Sie sich im [PowerApps Admin Center](https://admin.powerapps.com) an.

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
1. Führen Sie die obenstehend beschriebenen Schritte 1–4 aus.
2. Navigieren Sie zu **Settings/Data Management/Sample Data**.
3. Wenn Beispieldaten installiert sind, ist die Option zum Entfernen verfügbar. Andernfalls ist die Option zum Installieren verfügbar. 

    ![Beispieldaten entfernen](media/overview-model-driven-samples/remove-sample-data.png)




