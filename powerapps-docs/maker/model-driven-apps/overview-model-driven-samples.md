---
title: Modellgesteuerte Beispielapps
description: Erfahren Sie, wie Sie modelgesteuerte Beispiel-Apps erhalten, anpassen und entfernen können.
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
ms.openlocfilehash: 5e579b7054171222819b2d1dd6bb21d9cb7400a9
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711561"
---
# <a name="model-driven-sample-apps"></a>Modellgesteuerte Beispielapps

In [powerapps.com](https://powerapps.com) verwenden Sie eine Beispielanwendung, um Designmöglichkeiten kennenzulernen und Konzepte zu entdecken, die Sie bei der Entwicklung Ihrer eigenen Apps anwenden können. Jede Beispiel-App verwendet fiktive Daten, um ein reales Szenario darzustellen. 

Schauen Sie sich die Dokumentation zu jeder Beispiel-App an, um weitere Details zu erfahren. 

![Beispiel-App zur Mittelbeschaffung](media/overview-model-driven-samples/fundraiser-app1.png)


## <a name="get-sample-apps"></a>Beispiel-Apps herunterladen

Um modellgesteuerte Beispiel-Apps abspielen oder bearbeiten zu können, müssen die Apps zunächst in einer Common Data Service-Datenbank bereitgestellt werden. Erstellen Sie zunächst eine Testumgebung und eine Datenbank und stellen Sie sicher, dass Sie **Beispiel-Apps und Daten einschließen**.

![Datenbank erstellen](media/overview-model-driven-samples/create-database1.png)


> [!IMPORTANT]
> Diese Option installiert alle verfügbaren Beispiel-Apps in Ihrer Datenbank. Beispielapps sind für Schulungs- und Demonstrationszwecke gedacht und wir empfehlen nicht, sie in Produktionsdatenbanken zu installieren. 

## <a name="customize-a-sample-app"></a>Anpassen einer Beispiel-App

1. Anmelden bei [powerapps.com](https://powerapps.com)  

    

2. Fahren Sie auf der Seite **Erstellen** mit der Maus über die Beispiel-App und klicken Sie auf **Diese App erstellen**.

![Entwicklen einer Beispiel-App](media/overview-model-driven-samples/model-driven-create-page-sample.png)

3. Der App-Designer öffnet sich und bietet mehrere Optionen zum Anpassen der App. 
4. Für zusätzliche Anpassungsoptionen klicken Sie auf **Erweitert** in der linken Navigation im Portal.

## <a name="remove-sample-apps-and-data"></a>Entfernen von Beispiel-Apps und -Daten 
- Das Löschen einer Beispielanwendung erfordert das Löschen der entsprechenden  [verwalteten Lösung](https://docs.microsoft.com/dynamics365/customer-engagement/developer/uninstall-delete-solution). 
- Das Löschen der Lösung löscht auch alle Beispieldaten, die für die benutzerdefinierten Entitäten der App spezifisch sind.
- Wenn Anpassungen an der Beispielanwendung vorgenommen wurden, kann es [Abhängigkeiten](https://docs.microsoft.com/dynamics365/customer-engagement/developer/dependency-tracking-solution-components) geben, die vor dem Löschen der Lösung entfernt werden müssen.

### <a name="steps"></a>Schritte
1. Melden Sie sich am [PowerApps-Verwaltungsportal](https://admin.powerapps.com) an.

2. Wählen Sie eine Umgebung aus.

3. Klicken Sie auf **Dynamics 365 Administration Center** 

    ![Dynamics 365 Administration Center](media/overview-model-driven-samples/admin-center.png)

4. Wählen Sie Ihre Datenbank aus der Liste aus und klicken Sie **ÖFFNEN**.

    ![Datenbank auswählen](media/overview-model-driven-samples/select-database.png)

5. Navigieren Sie zu **Einstellungen/Lösungen**.

6. Wählen Sie die Lösung für die App, die gelöscht werden soll und klicken Sie auf **Löschen**.

    ![Lösung löschen](media/overview-model-driven-samples/delete-solution.png)

*Alternativ navigieren Sie zur Liste der Lösungen, indem Sie auf **Erweitert** im Herstellerportal klicken und alles in der URL nach .dynamics.com/ löschen*

> [!IMPORTANT]
> Löschen Sie keine anderen Systemlösungen, es sei denn, Ihnen sind die Auswirkungen bekannt.

## <a name="install-or-uninstall-sample-data"></a>Installieren oder deinstallieren von Beispieldaten
1. Führen Sie die oben genannten Schritte 1-4 aus.
2. Navigieren Sie zu **Einstellungen/Datenverwaltung/Beispieldaten**.
3. Wenn Beispieldaten installiert sind, ist die Option zum Entfernen verfügbar. Andernfalls ist diese Option zum Installieren verfügbar. 

    ![Beispieldaten entfernen](media/overview-model-driven-samples/remove-sample-data.png)




