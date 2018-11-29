---
title: Sie können auf eine Modell-angetriebene App-Ansichtsdefinition über die Startseite zugreifen | MicrosoftDocs
description: 'In diesem Thema erfahren Sie, wie Sie auf Entitätsansichten zugreifen'
ms.custom: ''
ms.date: 06/12/2018
ms.reviewer: ''
ms.service: crm-online
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
---
# <a name="access-a-model-driven-app-view-definition-in-powerapps"></a>Zugriff auf eine Modell-angetriebene App-Ansichtsdefinition in PowerApps.

 In diesem Thema öffnen Sie eine Ansicht, um die Eigenschaften und Optionen anzuzeigen, um die Ansicht zu konfigurieren. Es gibt verschiedene Möglichkeiten, wie Sie auf Ansichtsdefinitionen in PowerApps zugreifen können. 
  
  
## <a name="open-a-view-in-powerapps"></a>Öffnen einer Ansicht in PowerApps

1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  


    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2.  Erweitern Sie **Daten**, wählen Sie **Entitäten** aus, und wählen Sie dann die Entität **Firma** aus.   
3. Wählen Sie die Registerkarte **Anischt**, und wählen Sie dann **Filter entfernen** aus.

    > [!div class="mx-imgBorder"] 
    > ![Firma-Ansicht Definitionen](media/account-view-definitions.png)

4. Wählen Sie die Ansicht, die Sie öffnen möchten, wie die Firmaenentität-Ansicht **Alle Firmen** aus.

    > [!div class="mx-imgBorder"] 
    > ![Alle Konten anzeigen](media/all-accounts-view.png)

5. Im Ansichtseditor können Sie einige Aufgaben ausführen: 
 
- [Sortieren von Datensätzen in einer Ansicht](configure-sorting.md)
- [Aktivieren und Konfigurieren von Spalten in Ansichten](choose-and-configure-columns.md)
- [Verwenden benutzerdefinierter Steuerelemente für Datenvisualisierungen](use-custom-controls-data-visualizations.md) 

## <a name="open-a-view-from-an-app"></a>Öffnen Sie eine Ansicht aus eine App

In einer beliebigen Listenansicht für eine Entität finden Sie in der Befehlsleiste die folgenden Befehle, nachdem Sie auf die Schaltfläche mit den Auslassungspunkten (...) geklickt oder getippt haben:  
- **Ansicht**: Öffnet die Definition in der aktuellen Ansicht in der Standardlösung.  
  
- **Neue Systemansicht**: Öffnet ein neues Fenster, um eine neue Ansicht für die aktuelle Entität in der Standardlösung zu erstellen.  
  
- **Entität anpassen**: Führt Sie zur Definition der aktuellen Entität in der Standardlösung, in der Sie **Ansichten** auswählen können.  
  
- **Systemansichten**: Öffnet dasselbe Fenster wie **Entität anpassen** außer wenn **Ansichten** ausgewählt ist.  

## <a name="open-a-view-in-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer und zeigen Sie ihn an. 
  
1.  Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).  
  
2.  Erweitern Sie unter **Komponenten** den Ordner **Entitäten**, und erweitern Sie dann die gewünschte Entität.  
  
3.  Wählen Sie **Ansichten** aus.  
  
4.  Doppelklicken Sie auf die Ansicht, die Sie öffnen möchten.  
  
 Diese Liste der Ansichten hat vier Filter, die Sie verwenden können, um die Ansichten, die Sie wünschen, einfacher zu finden:  
  
    - **Alle aktiven Ansichten**  
  
    - **Aktive öffentliche Ansichten**  
  
    - **Inaktive öffentliche Ansichten**  
  
    - **Aktive systemdefinierte Ansichten**  
  
 Falls die Entität, der die Ansicht zugeordnet ist, Teil einer nicht verwalteten Lösung ist, können Sie dennoch Ansichten fü diese Entität in der Standardlösung erstellen oder bearbeiten. Systemansichten sind einer Entität zugeordnet und sind nicht als separate Lösungskomponenten verfügbar. Anders als Felder verwenden Ansichten kein Anpassungspräfix in einem eindeutigen Namen, der in einer Lösung konsistent sein sollte, daher müssen Sie Ansichten im Kontext einer Lösung erstellen. 
 
## <a name="next-steps"></a>Nächste Schritte
[Ansichten verstehen ](create-edit-views.md)


