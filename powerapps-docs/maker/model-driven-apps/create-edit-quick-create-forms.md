---
title: Erstellen oder Bearbeiten von modellgesteuerten Schnellerstellungsformularen in Power Apps | MicrosoftDocs
description: Erfahren Sie, wie Sie ein Schnellerfassungsformular erstellen oder bearbeiten
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
ms.openlocfilehash: e6f3c1313ad006d9280145fd2802f83369410ec3
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166924"
---
# <a name="create-or-edit-model-driven-app-quick-create-forms-for-a-streamlined-data-entry-experience"></a>Erstellen oder Bearbeiten von modellgesteuerten Schnellerstellungsformularen für eine optimierte Dateneingabeerfahrung

In diesem Thema erstellen und bearbeiten Sie ein Schnellerfassungsformular.

 Mit Schnellerfassungsformularen kann Ihre App einen optimierten Dateneingabekomfort mit vollständiger Unterstützung für durch Formularskripts und Geschäftsregeln definierte Logik. In einer modellgesteuerten Power Apps-App werden Schnellerstellungsformulare angezeigt, wenn Sie die Schaltfläche **Erstellen** in der Navigationsleiste auswählen oder wenn Sie **+ Neu** auswählen, wenn Sie einen neuen Datensatz aus einer Suche oder einem Unterraster erstellen.
  
 Die mobilen Apps in Dynamics 365 verwenden Schnellerstellungsformulare zum Erstellen neuer Datensätze. Wenn für eine Entität bereits ein Schnellerstellungsformular konfiguriert ist, verwenden die mobilen Apps dieses Formular. Wenn eine Entität kein konfiguriertes Schnellerstellungsformular hat, generiert Power Apps ein Schnellerfassungsformular für das Erstellen von Datensätzen in mobilen Apps anhand der Hauptformulardefinition.  
  
<a name="BKMK_QuickCreateFormEntities"></a>   
## <a name="entities-with-quick-create-forms"></a>Entitäten mit Schnellerfassungsformularen  
 Standardmäßig verfügen nur die folgenden Systementitäten über Schnellerfassungsformulare.  
  
|||||  
|-|-|-|-|  
|Firma|Kampagnenreaktion|Anfrage|Mitbewerber|  
|Kontakt|Lead|Verkaufschance||  
  
Obwohl Sie, mit Ausnahme der Terminentität, Schnellerfassungsformulare für Systemaktivitätsentitäten erstellen können, unterstützen sie keine Schnellerfassungsformulare. Derzeit wird die Option zur Deaktivierung des Schnellerfassungsformulars für die Terminentität nicht unterstützt. Alle anderen [aktualisierten Entitäten](create-design-forms.md) sowie alle benutzerdefinierten Entitäten können zur Unterstützung dieser Formulare aktiviert werden, indem in der Entitätsdefinition die Option **Schnellerfassungsformulare aktivieren** ausgewählt und für die Entität ein Schnellerfassungsformular erstellt wird. 

Sie können benutzerdefinierte Aktivitätsentitäten aktivieren, um Schnellerfassungsformulare zu unterstützen, und Sie können Schnellerfassungsformulare für diese Entitäten erstellen. Jedoch wird das Schnellerfassungsformular für benutzerdefinierte Aktivitätsentitäten nicht verwendet, wenn Personen **Erstellen** auf der Navigationsleiste auswählen. Diese Schnellerfassungsformulare können nur verwendet werden, wenn Benutzer einen neuen Datensatz für ein Unterraster hinzufügen, das diese bestimmte angepasste Aktivitätsentität anzeigt.  
  
<a name="BKMK_CreateQuickCreate"></a>   
## <a name="create-a-quick-create-form"></a>Erstellen eines Schnellerfassungsformulars  
 Obwohl Sie mehrere Schnellerfassungsformulare definieren können, kann nur ein Schnellerfassungsformular von jedem Benutzer verwendet werden. Das Formular, das jeder verwenden wird, wird mithilfe der Formularreihenfolge festgelegt. Schnellerfassungsformulare können nicht Sicherheitsrollen zugewiesen werden, und sie ermöglichen dem Benutzer nicht, Formulare zu wechseln.  
  
> [!NOTE]
>  - Für die Entität muss die Option **Schnellerfassungsformulare aktivieren** aktiviert sein, damit das Schnellerfassungsformular angezeigt werden kann. 
>  - Sie müssen ebenfalls die Entität und das Schnellerfassungsformular Ihrer App hinzufügen.
>  - Einige Felder wie das CREATEDON-Feld können nicht in einem Schnellerfassungsformular hinzugefügt werden.  
  
### <a name="how-to-create-a-quick-create-form"></a>So erstellen Sie ein Schnellerfassungsformular  
  
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

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
  
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2. Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.    

3. Wählen Sie in der Formularliste, in der sich das Formular **Typ** befindet **Schnellerfassung** aus.  
  
3.  Ziehen Sie Felder aus dem **Feld-Explorer** in die Abschnitte im Formular.  
  
     Informationen zum Bearbeiten von Ereignishandlern für Formularskripts finden Sie unter [Konfigurieren von Ereignishandlern](configure-event-handlers-legacy.md).  
  
4.  Wenn Sie fertig sind, wählen Sie **Speichern** aus.  
  
5.  Wählen Sie **Veröffentlichen**, damit das geänderte Formular in der Anwendung angezeigt wird.  

## <a name="enable-quick-create-form-property-behavior-for-activities"></a>Eigenschaftsverhalten „Schnellerfassungsformular aktivieren“ für Aktivitäten
Die Eigenschaft **Schnellerfassungsformulare aktivieren** kann für alle Standardaktivitäten außer wiederkehrenden Terminen aktiviert oder deaktiviert werden. Mit dieser Eigenschaft können Sie das angezeigte Formular standardmäßig für die meisten Aktivitäten ändern. Standardmäßig wird die Eigenschaft **Schnellerfassungsformulare aktivieren** aktiviert und das Schnellerfassungsformular ist das Formular, das in App-Bereichen und unterstützenden Aktivitätsentitäten angezeigt wird. 

> [!div class="mx-imgBorder"] 
> ![](media/allow-quick-create.png "Allow Quick Create property on appointment entity")


### <a name="unified-interface-client-form-display-behavior"></a>Einheitliche Oberfläche-Clientformular – Anzeigeverhalten
Die folgende Tabelle gibt an, welches Formular standardmäßig angezeigt wird, wenn die Eigenschaft **Schnellerfassungsformulare aktivieren** im Client der einheitlichen Oberfläche *aktiviert* ist.
 
|Speicherort, an dem auf das Formular zugegriffen wird  |Angezeigtes Formular  |
|---------|---------|
|Zugeordnetes Raster für spezifische Entität  | Schnellerfassung      |
|Untergeordnetes Raster der spezifischen Aktivität   |  Schnellerfassung     |
|Aktivitäten (activitypointer)-Raster     | Schnellerfassung     |
|Verknüpftes Aktivitäten (activitypointer)-Raster   | Schnellerfassung    |
|Aktivitäten (activitypointer)-Unterraster  | Schnellerfassung    |
|Globale Befehlsleiste + Schaltfläche<sup>1</sup>    | Schnellerfassung    |
|Zeitachsenpinnwand   | Schnellerfassung    |
|Aktivitäten (activitypointer)-Raster   | Hauptbereich   |
|Raster der spezifischen Aktivität    | Hauptbereich   |

<sup>1</sup>Aktivitäten werden auf den globalen Schaltflächen **Erstellen** oder **+ Neu** angezeigt, wenn die Eigenschaft **Schnellerfassungsformulare aktivieren** aktiviert ist. In diesem Fall wird das Schnellerfassungsformular verwendet, wenn es vorhanden ist, anderenfalls das Hauptformular. Wenn die Option **Schnellerfassungsformulare aktivieren** deaktiviert ist, wird der Eintrag für die Entität nicht angezeigt.

### <a name="classic-web-client-form-display-behavior"></a>Klassisches Webclientformular-Anzeigeverhalten

Die folgende Tabelle gibt an, welches Formular standardmäßig angezeigt wird, wenn die Eigenschaft **Schnellerfassungsformulare aktivieren** im klassischen Webclient *aktiviert* ist.

|Speicherort, an dem auf das Formular zugegriffen wird  |Angezeigtes Formular  |
|---------|---------|
|Zugeordnetes Raster für spezifische Entität  | Schnellerfassung      |
|Untergeordnetes Raster der spezifischen Aktivität   |  Schnellerfassung     |
|Aktivitäten (activitypointer)-Raster     | Hauptbereich     |
|Verknüpftes Aktivitäten (activitypointer)-Raster   | Hauptbereich    |
|Aktivitäten (activitypointer)-Unterraster  | Hauptbereich    |
|Globale Befehlsleiste + Schaltfläche    | Hauptbereich    |
|Raster der spezifischen Aktivität   | Hauptbereich    |

 #### <a name="classic-web-client-social-pane-behavior"></a>Social Media-Bereich des klassischen Webclients – Verhalten
 
Der Social Media-Bereich ist ein Sonderfall, da er die Eigenschaft **Schnellerfassungsformulare aktivieren** nicht verwendet. Er verwendet aber unterschiedliche Formulare für unterschiedliche Aktivitätsentitäten, wie hier angegeben.


|Aktivität  |Angezeigtes Formular  |
|---------|---------|
|Aufgabe     | Schnellerfassung    |
|Telefonanruf   | Schnellerfassung     |
|E-Mail   | Hauptbereich     |
|Termin  | Hauptbereich     |
|Benutzerdefinierte Aktivitäten     | Hauptbereich      |

### <a name="solution-import-allow-quick-create-value-behavior"></a>Lösungsimport "Schnellerfassung zulassen"-Wertverhalten

Wenn Sie eine Lösung aus Version 8.2 importieren, werden die folgenden Entitäten, unabhängig vom Wert der Eigenschaft **Schnellerfassungsformulare aktivieren** in der Lösung, auf den Standardformular-Anzeigewert zurückgesetzt und das Hauptformular zeigt: Aufgabe, Telefonanruf, E-Mail und Termin. In dieser Situation muss nach dem Import die Option **Schnellerfassungsformulare aktivieren** für diese Aktivitätsentitäten zurück auf *aktiviert* gesetzt werden.
 
Wenn eine Anpassung in einer Version 9.0-Lösung für Entitäten durchgeführt wird, bei denen die Option **Schnellerfassungsformulare aktivieren** aktiviert ist, ändert sich der Wert nach dem Import nicht.  Wenn Sie die Option **Schnellerfassungsformulare aktivieren** aber für die Entitäten Aufgabe, Telefonanruf, E-Mail und Termin auf *deaktiviert* gesetzt haben, wird der Wert in „aktiviert“ geändert. In dieser Situation muss nach dem Import die Option **Schnellerfassungsformulare aktivieren** für diese Aktivitätsentitäten zurück auf „deaktiviert“ gesetzt werden. 
  
### <a name="see-also"></a>Siehe auch  
[Übersicht zur Formular-Editor-Benutzeroberfläche](form-editor-user-interface-legacy.md)
