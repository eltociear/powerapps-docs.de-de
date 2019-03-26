---
title: Erstellen oder bearbeiten von modellgesteuerten Schnellerstellungsformularen in PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie Sie ein Schnellerfassungsformular erstellen oder bearbeiten'
ms.custom: ''
ms.date: 01/25/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 68ca9059-cc5a-45e7-88bd-cc57186bbb48
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-model-driven-app-quick-create-forms-for-a-streamlined-data-entry-experience"></a>Erstellen oder Bearbeiten von modellgesteuerten Schnellerstellungsformularen für eine optimierte Dateneingabeerfahrung

In diesem Thema erstellen und bearbeiten Sie ein Schnellerfassungsformular.

 Mit Schnellerfassungsformularen kann Ihre App einen optimierten Dateneingabekomfort mit vollständiger Unterstützung für durch Formularskripts und Geschäftsregeln definierte Logik. In einer modellgesteuerten PowerApps-App werden Schnellerstellungsformulare angezeigt, wenn Sie die Schaltfläche **Erstellen** in der Navigationsleiste auswählen oder wenn Sie **+ Neu** auswählen, wenn Sie einen neuen Datensatz aus einer Suche oder einem Unterraster erstellen.
  
 Die mobilen Dynamics 365 Customer Engagement-Apps verwenden Schnellerfassungsformulare zum Erstellen neuer Datensätze. Wenn für eine Entität bereits ein Schnellerstellungsformular konfiguriert ist, verwenden die mobilen Apps dieses Formular. Wenn eine Entität kein konfiguriertes Schnellerstellungsformular hat, generiert PowerApps ein Schnellerfassungsformular für das Erstellen von Datensätzen in mobilen Apps anhand der Hauptformulardefinition.  
  
<a name="BKMK_QuickCreateFormEntities"></a>   
## <a name="entities-with-quick-create-forms"></a>Entitäten mit Schnellerfassungsformularen  
 Standardmäßig verfügen nur die folgenden Systementitäten über Schnellerfassungsformulare.  
  
|||||  
|-|-|-|-|  
|Firma|Kampagnenreaktion|Anfrage|Mitbewerber|  
|Kontakt|Lead|Verkaufschance||  
  
Obwohl Sie, mit Ausnahme der Terminentität, Schnellerfassungsformulare für Systemaktivitätsentitäten erstellen können, unterstützen sie keine Schnellerfassungsformulare. Mit der Veröffentlichung von Dynamics 365, Version 9.0 enthält die Terminentität ein Schnellerfassungsformular für die Verwendung mit der einheitlichen Oberfläche. Derzeit wird die Option zur Deaktivierung des Schnellerfassungsformulars für die Terminentität nicht unterstützt. Alle anderen [Aktualisierten Entitäten](create-design-forms.md) sowie alle benutzerdefinierten Entitäten können zur Unterstützung dieser Formulare aktiviert werden, indem in der Entitätsdefinition **Schnellerfassung erlauben** ausgewählt und für die Entität ein Schnellerfassungsformular erstellt wird. 

Sie können benutzerdefinierte Aktivitätsentitäten aktivieren, um Schnellerfassungsformulare zu unterstützen, und Sie können Schnellerfassungsformulare für diese Entitäten erstellen. Jedoch wird das Schnellerfassungsformular für benutzerdefinierte Aktivitätsentitäten nicht verwendet, wenn Personen **Erstellen** auf der Navigationsleiste auswählen. Diese Schnellerfassungsformulare können nur verwendet werden, wenn Benutzer einen neuen Datensatz für ein Unterraster hinzufügen, das diese bestimmte angepasste Aktivitätsentität anzeigt.  
  
<a name="BKMK_CreateQuickCreate"></a>   
## <a name="create-a-quick-create-form"></a>Erstellen eines Schnellerfassungsformulars  
 Obwohl Sie mehrere Schnellerfassungsformulare definieren können, kann nur ein Schnellerfassungsformular von jedem Benutzer verwendet werden. Das Formular, das jeder verwenden wird, wird mithilfe der Formularreihenfolge festgelegt. Schnellerfassungsformulare können nicht Sicherheitsrollen zugewiesen werden, und sie ermöglichen dem Benutzer nicht, Formulare zu wechseln.  
  
> [!NOTE]
>  - Für die Entität muss die Option **Schnellerfassung erlauben** aktiviert sein, damit das Schnellerfassungsformular angezeigt werden kann. 
>  - Einige Felder wie das CREATEDON Feld, können nicht in einem Schnellerfassungsformular hinzuzugefügt werden.  
  
### <a name="how-to-create-a-quick-create-form"></a>So erstellen Sie ein Schnellerfassungsformular  
  
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.


> [!IMPORTANT]
> "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).     
  
2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.  

3.  Wählen Sie in der Symbolleiste **Formular hinzufügen** > **Schnellerfassungsformular** aus.  
  
4.  Ziehen Sie im Formulardesigner beliebige Felder aus dem **Feld-Explorer** in die Abschnitte im Formular.  
  
5.  Wenn Sie fertig sind, wählen Sie **Speichern** aus.  
  
6.  Wählen Sie **Veröffentlichen**, damit das neue Formular in der Anwendung angezeigt wird.  
  
<a name="BKMK_EditQuickCreate"></a>   
## <a name="edit-a-quick-create-form"></a>Bearbeiten eines Schnellerfassungsformulars  
 Während Schnellerfassungsformulare Formularskripts und Geschäftsregeln unterstützen, verfolgen sie einen anderen Zweck als Hauptformulare und unterstützen nicht alle Funktionen von Hauptformularen. Schnellerfassungsformulare haben immer einen Abschnitt mit drei Spalten. Sie können keine zusätzlichen Abschnitte oder Spalten hinzufügen.  
  
 Die folgenden Steuerelemente können Schnellerfassungsformularen nicht hinzugefügt werden:  
  
-   Unterraster  
  
-   Schnellansichtsformulare  
  
-   Webressourcen  
  
-   iFrames  
  
-   Notizen  
  
-   Bing Maps  
  
Wenn Sie einem Schnellerfassungsformular ein zusammengesetztes Feld hinzufügen, wird es als separates Feld angezeigt.  
  
### <a name="to-edit-a-quick-create-form"></a>Bearbeiten eines Schnellerfassungsformulars  
  
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

> [!IMPORTANT]
> "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).    
  
2. Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.    

3. Wählen Sie in der Formularliste, in der sich das Formular **Typ** befindet **Schnellerfassung** aus.  
  
3.  Ziehen Sie Felder aus dem **Feld-Explorer** in die Abschnitte im Formular.  
  
     Informationen zum Bearbeiten von Ereignishandlern für Formularskripts finden Sie unter [Konfigurieren von Ereignishandlern](configure-event-handlers-legacy.md).  
  
4.  Wenn Sie fertig sind, wählen Sie **Speichern** aus.  
  
5.  Wählen Sie **Veröffentlichen**, damit das geänderte Formular in der Anwendung angezeigt wird.  
  
### <a name="next-steps"></a>Nächste Schritte  
[Übersicht zur Formular-Editor-Benutzeroberfläche](form-editor-user-interface-legacy.md)
