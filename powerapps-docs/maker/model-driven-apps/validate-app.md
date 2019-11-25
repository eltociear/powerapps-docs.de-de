---
title: Überprüfen und Veröffentlichen Sie ein modellgetriebenes App mithilfe des Anwendungs-Designers | MicrosoftDocs
description: Erfahren Sie, wie Sie eine modellgetriebene App überprüfen und veröffentlichen
keywords: ''
ms.date: 06/08/2018
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2e6ae7ac84710e6558adde2949025868e6da6930
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2710285"
---
# <a name="validate-and-publish-a-model-driven-app-using-the-app-designer"></a>Überprüfen und Veröffentlichen einer modellgesteuerten App mithilfe des App-Designers

Validieren Sie eine App, indem Sie die Ressourcenabhängigkeiten prüfen, die für die Funktion der App obligatorisch sind, jedoch noch nicht zur App hinzugefügt wurden. Nach erfolgreicher Überprüfung veröffentlichen Sie die App. 
  
Beispielsweise haben Sie ein Customer Service-Leistungsdashboard zur App hinzugefügt, das Diagramme wie Anfragemix (nach Priorität) oder Anfrageabschlusstrend (nach Tag) verwendet, die Sie nicht hinzugefügt haben. Wenn Sie diese App überprüfen, erhalten Sie eine Liste aller fehlenden, erforderlichen Ressourcen.  
  
Wenn Sie die App überprüfen, zeigt Ihnen die App-Designer-Canvas Details zu den Ressourcen an, die fehlen.  
  
1.  Im App-Designer wählen Sie **Überprüfen** aus.  
  
     Eine Benachrichtigungsleiste wird angezeigt, die mitteilt, ob die App Fehler oder Warnhinweise aufweist. Die Benachrichtigungsleiste zeigt Warnungen an, beispielsweise für Fälle, in denen eine Entität keine Formulare oder Ansichten besitzt oder die App keine Komponenten enthält. Ein Fehler kann angezeigt werden, wenn keine Sitemap für die Siteübersicht konfiguriert wurde. Sie können eine App ohne Warnmeldungen veröffentlichen, jedoch müssen Sie Fehler behoben haben, bevor Sie die App veröffentlichen können.  
  
     ![Benachrichtigungsleiste zeigt Warnungen in der App](media/app-designer-warning-notification.png "Benachrichtigungsleiste zeigt Warnungen in der App")  
  
     Der App-Designer zeigt darüber hinaus ein Warnsymbol mit der Anzahl der Abhängigkeiten für alle Artefakte oder Anlagenkacheln an, bei denen eine erforderliche Ressource fehlt.  
  
     ![Fehlende Komponentenwarnung auf der App-Designer-Kachel](media/warning--button-on-app-designer-tile.png "Fehlende Komponentenwarnung auf der App-Designer-Kachel")  
  
2.  Um die erforderlichen Ressourcen hinzuzufügen, wählen Sie auf der rechten Seite des Canvas **Erforderlich** aus. Die Registerkarte **Erforderlich** ist sichtbar, wenn mindestens ein erforderliches Objekt in der App fehlt.  
  
     Auf der Registerkarte wird eine Liste der erforderlichen Komponenten angezeigt.  
  
     ![Die Registerkarte "Erforderlich" zeigt eine Liste der fehlenden Komponenten der App an](media/app-designer-required-components-tab.png "Die Registerkarte "Erforderlich" zeigt eine Liste der fehlenden Komponenten der App an")  
  
3.  Wählen Sie die Ressourcen aus, die Sie hinzufügen möchten, und wählen Sie dann **Abhängigkeiten hinzufügen** aus. Wenn Sie eine erforderliche Ressource hinzufügen, erhöht sich die Anzahl auf der Kachel, zu der Sie die Anlage hinzugefügt haben.  
  
    > [!NOTE]
    >  Ist eine allgemeine Anlage für verschiedene App-Komponenten erforderlich, beispielsweise ein Formular, das für ein Dashboard und eine Entität erforderlich ist, und Sie fügen die Anlage nur zum Dashboard-Abhängigkeitsbaum hinzu, dann wird die Abhängigkeitsanzahl nur für die Dashboardkachel aber nicht für die Entitätskachel reduziert. Jedoch wird die Abhängigkeit für beide verwendet.  
    >   
    >  Wählen Sie **Aktuelle Abhängigkeiten abrufen** ![Schaltfläche zum Abrufen der aktuellen Abhängigkeiten im App-Designer](media/app-designer-get-latest-dependencies.png "Rufen Sie die aktuelle Abhängigkeitsschaltfläche im Anwendungs-Designer ab") oder erneut **Überprüfen** aus, um den neuesten Satz an Abhängigkeiten abzurufen. Sie können diese Schaltflächen erst anzeigen, nachdem Sie Ihre App gespeichert haben.  
  
     Wählen Sie **Abhängigkeiten ausblenden** aus, wenn Sie die vorgeschlagenen erforderlichen Komponenten nicht hinzufügen möchten. Nicht gelöste Warnungen werden erneut angezeigt, wenn Sie die App im App-Designer öffnen und **Überprüfen** oder **Aktuelle Abhängigkeiten abrufen** ![Schaltfläche zum Abrufen der aktuellen Abhängigkeiten im App-Designer](media/app-designer-get-latest-dependencies.png "Rufen Sie die aktuelle Abhängigkeitsschaltfläche im Anwendungs-Designer ab") auswählen.  
  
    > [!NOTE]
    >  Wenn Sie jetzt Abhängigkeiten ausblenden und die App später exportieren möchten, werden diese Abhängigkeiten erneut angezeigt.  
  
## <a name="publish-an-app-using-the-app-designer"></a>Veröffentlichen einer App mit dem App-Designer

Veröffentlichen Sie eine App, um sie Benutzern zur Verfügung zu stellen.  
  
 Nachdem Sie Komponenten hinzugefügt, überprüft und die App gespeichert haben, wählen Sie auf der Befehlsleiste **Veröffentlichen** aus. Sie können die App auch über die App-Kachel auf der der Seite [Meine Apps](advanced-navigation.md#apps) veröffentlichen. In der Ansicht **Apps werden bearbeitet** in der unteren rechten Ecke der App-Kachel, die Sie veröffentlichen möchten, klicken Sie auf die Schaltfläche **Weitere Optionen** (**...**) und wählen dann **Veröffentlichen** aus.  
  
 Der Status der App wird auf "Veröffentlicht" geändert. Sie können dies in der oberen rechten Ecke des Anwendungs-Designers sehen. Die App wird von der Ansicht **Apps, die bearbeitet werden** in die Ansicht **Veröffentlichte Apps** verschoben und auf der App-Kachel wird das Publikationsdatum angezeigt.  
  
> [!NOTE]
> - Wenn die App einen Überprüfungsfehler hat, finden Sie die Fehlermeldung auf einer Benachrichtigungsleiste. Es ist nicht möglich, die App zu veröffentlichen, solange Sie den Fehler nicht korrigiert haben.  
> - Sie können eine App nicht veröffentlicht, wenn Sie sie noch nicht gespeichert haben.  

## <a name="next-steps"></a>Nächste Schritte  
[Gemeinsame Nutzung einer modellgesteuerten App mit PowerApps](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app) <br/>
 [Ausführen einer modellgesteuerten App auf einem mobilen Gerät](https://docs.microsoft.com/powerapps/user/run-app-client-model-driven)   
 
