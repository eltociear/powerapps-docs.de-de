---
title: Überprüfen und veröffentlichen einer modellgesteuerten App mit App-Designer | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine modellgesteuerte App überprüfen und veröffentlichen.
keywords: ''
ms.date: 06/08/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 5a9ec120-9ddc-4d92-b48c-0fee8c57d3c3
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 10
topic-status: Drafting
ms.openlocfilehash: e3802ef423e7012974c24311c36b78cd56f8ed06
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39685634"
---
# <a name="validate-and-publish-a-model-driven-app-using-the-app-designer"></a>Überprüfen und veröffentlichen einer modellgesteuerten App mit App-Designer

Validieren Sie eine App, um nach Objektabhängigkeiten zu suchen, die für die Funktion der App erforderlich sind, aber noch nicht zur App hinzugefügt wurden. Nach einer erfolgreichen Überprüfung können Sie die App veröffentlichen. 
  
Beispielsweise haben Sie der App ein Dashboard für die Kundendienstleistung hinzugefügt, das Diagramme wie Fallmischung (nach Priorität) oder Fallauflösungstrend (nach Tag) verwendet, die Sie nicht hinzugefügt haben. Wenn Sie diese App überprüft haben, erhalten Sie eine Liste mit allen fehlenden, erforderlichen Objekten.  
  
Wenn Sie die App überprüfen, zeigt Ihnen die App-Designer-Canvas Details zu den fehlenden Objekten.  
  
1.  Wählen Sie im App-Designer **Überprüfen** aus.  
  
     Es wird eine Benachrichtigungsleiste angezeigt, in der Sie sehen, ob für die App Fehler oder Warnungen vorliegen. Die Benachrichtigungsleiste zeigt Warnungen an, wenn beispielsweise eine Entität keine Formulare oder Ansichten hat oder die App keine Komponenten enthält. Ein Fehler kann auftreten, wenn eine Sitemap nicht für die App konfiguriert ist. Sie können eine App veröffentlichen, ohne Warnungen zu berücksichtigen, aber Fehler müssen vor der Veröffentlichung behoben werden.  
  
     ![Benachrichtigungsleiste mit Warnungen in der App](media/app-designer-warning-notification.png "Benachrichtigungsleiste mit Warnungen in der App")  
  
     Der App-Designer zeigt auch ein Warnsymbol mit der Anzahl der Abhängigkeiten von jedem Artefakt oder jeder Objektkachel an, der ein benötigtes Objekt fehlt.  
  
     ![Warnung zu fehlender Komponente in der App-Designer-Kachel](media/warning--button-on-app-designer-tile.png "Warnung zu fehlender Komponente in der App-Designer-Kachel")  
  
2.  Um die erforderlichen Objekte hinzuzufügen, wählen Sie die Registerkarte **Erforderlich** auf der rechten Seite der Canvas. Die Registerkarte **Erforderlich** wird angezeigt, wenn mindestens ein erforderliches Objekt in der App fehlt.  
  
     Die Registerkarte enthält eine Liste der erforderlichen Komponenten.  
  
     ![Registerkarte „Erforderlich“ mit einer Liste der fehlenden Komponenten in der App](media/app-designer-required-components-tab.png "Registerkarte „Erforderlich“ mit einer Liste der fehlenden Komponenten in der App")  
  
3.  Wählen Sie die Objekte aus, die Sie hinzufügen möchten, und wählen Sie dann **Abhängigkeiten hinzufügen**. Wenn Sie eine erforderliche Ressource hinzufügen, verringert die Anzahl die auf die Kachel, die Sie das Medienobjekt hinzugefügt haben.  
  
    > [!NOTE]
    >  Wenn ein gemeinsames Objekt für verschiedene Anwendungskomponenten hinweg benötigt wird, z.B. ein Formular für ein Dashboard und einen Entität, und Sie dieses Objekt nur einmal aus dem Dashboard-Abhängigkeitsbaum hinzufügen, verringert sich die Anzahl der Abhängigkeiten nur auf der Dashboardkachel, nicht aber auf der Entitätskachel. Die Abhängigkeit wird jedoch für beide aufgelöst.  
    >   
    >  Wählen Sie **Aktuelle Abhängigkeiten abrufen** ![Schaltfläche „Aktuelle Abhängigkeiten abrufen“ im App-Designer](media/app-designer-get-latest-dependencies.png "Schaltfläche „Aktuelle Abhängigkeiten abrufen“ im App-Designer"), oder wählen Sie **Überprüfen** erneut aus, um den neuesten Satz von Abhängigkeiten zu erhalten. Diese Schaltflächen werden erst angezeigt, nachdem Sie Ihre App gespeichert haben.  
  
     Wählen Sie **Abhängigkeiten ausblenden**, wenn Sie die empfohlenen erforderlichen Komponenten nicht hinzuzufügen möchten. Alle nicht aufgelösten Warnungen werden wieder angezeigt, wenn Sie die App im App-Designer öffnen und **Überprüfen** oder **Aktuelle Abhängigkeiten abrufen** auswählen. ![Schaltfläche „Aktuelle Abhängigkeiten abrufen“ im App-Designer](media/app-designer-get-latest-dependencies.png "Schaltfläche „Aktuelle Abhängigkeiten abrufen“ im App-Designer").  
  
    > [!NOTE]
    >  Wenn Sie Abhängigkeiten jetzt ausblenden und diese Anwendung später exportieren möchten, werden alle diese Abhängigkeiten wieder angezeigt.  
  
## <a name="publish-an-app-using-the-app-designer"></a>Veröffentlichen einer App mithilfe des App-Designers

Veröffentlichen Sie eine App, um sie für Benutzer verfügbar zu machen.  
  
 Nachdem Sie Komponenten hinzugefügt, überprüft und die App gespeichert haben, wählen Sie in der Befehlsleiste **Veröffentlichen**. Sie können die App auch aus dem Appkachel auf der Seite [Meine Apps](advanced-navigation.md#my-apps) veröffentlichen. Wählen Sie in der Ansicht **Apps in Bearbeitung** in der unteren rechten Ecke der Appkachel, die Sie veröffentlichen möchten, die Schaltfläche **Mehr Optionen** (**...**), und wählen Sie dann **Veröffentlichen**.  
  
 Der Status der App ändert sich in „Veröffentlicht“. Sie sehen dies in der rechten oberen Ecke des App-Designers. Die App wechselt von der Ansicht **Apps in Bearbeitung** zur Ansicht **Veröffentliche Apps**, und das Veröffentlichungsdatum wird auf dem Appkachel angezeigt.  
  
> [!NOTE]
> - Wenn Ihre Anwendung einen Überprüfungsfehler aufweist, wird dieser in einer Benachrichtigungsleiste angezeigt. Sie können die App erst nach Auflösung des Fehlers veröffentlichen.  
> - Sie können eine App erst nach dem Speichern veröffentlichen.  

## <a name="next-steps"></a>Nächste Schritte  
[Freigeben einer modellgesteuerten App mit PowerApps](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app) <br/>
 [Ausführen modellgesteuerter Apps auf einem mobilen Gerät](https://docs.microsoft.com/powerapps/user/run-app-client-model-driven)   
 
