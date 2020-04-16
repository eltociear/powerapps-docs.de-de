---
title: Sie können auf eine Modell-angetriebene App-Ansichtsdefinition über die Startseite zugreifen | MicrosoftDocs
description: In diesem Thema erfahren Sie, wie Sie auf Entitätsansichten zugreifen
ms.custom: ''
ms.date: 03/23/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: 034c8bef-0d1c-4ef9-8da7-f81343c4553a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 26d9abdd0703519d36c5f51a20a8617e4801f552
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166660"
---
# <a name="access-a-model-driven-app-view-definition-in-power-apps"></a>Zugriff auf eine modellgesteuerte App-Ansichtsdefinition in Power Apps

 In diesem Thema öffnen Sie eine Ansicht, um die Eigenschaften und Optionen anzuzeigen, um die Ansicht zu konfigurieren. Es gibt verschiedene Möglichkeiten, wie Sie auf Ansichtsdefinitionen in Power Apps zugreifen können. 
  
  
## <a name="open-a-view-for-editing-in-the-latest-view-designer"></a>Öffnen einer Ansicht zum Bearbeiten im aktuellen Ansicht-Designer

> [!IMPORTANT]
> Die neueste Version des Ansicht-Designers befindet sich derzeit in der Vorschau. Einige Funktionen wie erweiterte Filterung, benutzerdefinierte Steuerelemente und Spalteneigenschaften werden noch nicht unterstützt. Um diese Aufgaben durchzuführen, [Öffnen Sie eine Ansicht zum Bearbeiten im Lösungsexplorer](#open-a-view-for-editing-in-solution-explorer).

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die gewünschte Entität aus, beispielsweise die **Firma**-Entität.   

3. Klicken Sie auf die Registerkarte **Ansichten**.

    > [!div class="mx-imgBorder"] 
    > ![Firma-Ansicht Definitionen](media/account-view-definitions.png)

4. Wählen Sie die Ansicht, die Sie öffnen möchten, wie die Firmaenentität-Ansicht **Alle Firmen** aus.

    > [!div class="mx-imgBorder"] 
    > ![Alle Konten anzeigen](media/account-view-designer.png)

5. Im Ansichtseditor können Sie einige Aufgaben ausführen: 
 
- [Sortieren von Datensätzen in einer Ansicht](configure-sorting.md)
- [Spalten in Ansichten auswählen und konfigurieren](choose-and-configure-columns.md)

## <a name="open-a-view-for-editing-from-a-legacy-web-app"></a>Öffnen Sie eine Ansicht zum Bearbeiten aus einer älteren Webanwendung heraus.
In einer beliebigen Listenansicht für eine Entität in einer älteren Webanwendung finden Sie in der Befehlsleiste die folgenden Befehle, nachdem Sie auf die Schaltfläche mit den Auslassungspunkten (...) geklickt oder getippt haben:  

- **Ansicht**: Öffnet die Definition in der aktuellen Ansicht in der Standardlösung.  
  
- **Neue Systemansicht**: Öffnet ein neues Fenster, um eine neue Ansicht für die aktuelle Entität in der Standardlösung zu erstellen.  
  
- **Entität anpassen**: Führt Sie zur Definition der aktuellen Entität in der Standardlösung, in der Sie **Ansichten** auswählen können.  
  
- **Systemansichten**: Öffnet dasselbe Fenster wie **Entität anpassen** außer wenn **Ansichten** ausgewählt ist.  

   ![Öffnen Sie den Ansicht-Editor aus einer älteren Webanwendung heraus.](media/open-view-editor-from-view.png)

## <a name="open-a-view-for-editing-in-solution-explorer"></a>Öffnen einer Ansicht zum Bearbeiten im Projektmappen-Explorer 
1.  Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).  
  
2.  Erweitern Sie unter **Komponenten** den Ordner **Entitäten**, und erweitern Sie dann die gewünschte Entität.  
  
3.  Wählen Sie **Ansichten** aus.  
  
4.  Doppelklicken Sie auf die Ansicht, die Sie öffnen möchten. Dadurch wird der klassische Ansicht-Designer geöffnet.
    
    > [!div class="mx-imgBorder"] 
    > ![Alle Konten anzeigen](media/all-accounts-view.png)

 Diese Liste der Ansichten hat vier Filter, die Sie verwenden können, um die Ansichten, die Sie wünschen, einfacher zu finden:  
  
- **Alle aktiven Ansichten**  

- **Aktive öffentliche Ansichten**  

- **Inaktive öffentliche Ansichten**  

- **Aktive systemdefinierte Ansichten**  
  
 Falls die Entität, der die Ansicht zugeordnet ist, Teil einer nicht verwalteten Lösung ist, können Sie dennoch Ansichten fü diese Entität in der Standardlösung erstellen oder bearbeiten. Systemansichten sind einer Entität zugeordnet und sind nicht als separate Lösungskomponenten verfügbar. Anders als Felder verwenden Ansichten kein Anpassungspräfix in einem eindeutigen Namen, der in einer Lösung konsistent sein sollte, daher müssen Sie Ansichten im Kontext einer Lösung erstellen. 
 
## <a name="next-steps"></a>Nächste Schritte
[Ansichten verstehen](create-edit-views.md)


