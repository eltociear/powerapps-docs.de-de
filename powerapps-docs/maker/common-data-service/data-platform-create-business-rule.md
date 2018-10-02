---
title: Erstellen einer Geschäftsregel in Common Data Service for Apps | MicrosoftDocs
description: Schrittweise Anweisungen zur Erstellung einer Geschäftsregel in Common Data Service (CDS) for Apps.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-a-business-rule-for-an-entity"></a>Geschäftsregel für eine Entität erstellen

Sie können Geschäftsregeln und Empfehlungen erstellen, um Logik und Validierungen anzuwenden, ohne -Code zu schreiben oder Plug-ins zu erstellen. Geschäftsregeln bieten eine einfache Schnittstelle, um sich schnell ändernden und häufig verwendeten Regeln zu implementieren und zu verwalten. 
  
Indem Sie Bedingungen und Aktionen kombinieren können Sie folgende Aktionen mit Geschäftsregeln ausführen:  
  
* Feldwerte festlegen  
* Klare Feldwerte  
* Festlegen von Felderforderlichkeitsstufen  
* Ein- oder Ausblenden von Feldern  
* Aktivieren oder Deaktivieren von Feldern  
* Überprüfen von Daten und Anzeigen von Fehlermeldungen  
* Erstellen von Geschäftsempfehlungen basierend auf Business Intelligence-Daten.  
  
## <a name="differences-between-canvas-and-model-driven-apps"></a>Unterschiede zwischen Canvas und modellgesteuerten Apps

Modellgesteuerte Apps können alle Aktionen verwenden, die in Geschäftsregeln verfügbar sind, jedoch sind derzeit nicht alle Geschäftsregelaktionen bei Canvas-Apps verfügbar. Die folgenden Aktionen sind **nicht** für Canvas-Apps verfügbar:

* Ein- oder Ausblenden von Feldern  
* Aktivieren oder Deaktivieren von Feldern  
* Erstellen von Geschäftsempfehlungen basierend auf Business Intelligence-Daten.  

## <a name="prerequisites"></a>Voraussetzungen
Um diesem Thema zu folgen, müssen Sie zu einer [Umgebung](../canvas-apps/working-with-environments.md) wechseln, in der Sie Entitäten erstellen und bearbeiten können.

## <a name="create-a-business-rule"></a>Geschäftsregel formulieren
  
1. Melden Sie sich in [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und klicken oder tippen Sie auf den Abwärtspfeil für **Daten** neben dem linken Rand.

2. In der Liste, der angezeigt wird, klicken oder tippen Sie auf **Entitäten**.
  
3. Öffnen Sie die Entität, für die Sie die Geschäftsregel erstellen möchten (öffnen Sie z.B. die Entität **Firma**), und doppelklicken Sie dann auf die Registerkarte **Geschäftsregeln**.  

4. Klicken Sie auf **Neu**.  
  
    Das Geschäftsregeldesignerfenster wird mit einer einzelnen Bedingung geöffnet, die bereits für Sie erstellt wurde. Jede Regel startet mit einer Bedingung. Die Geschäftsregel führt eine oder mehrere diese Aktionen basierend auf der Bedingung durch.  

    > [!TIP]
    > Wenn Sie eine vorhandene Geschäftsregel ändern möchten, müssen Sie sie deaktivieren, bevor Sie sie bearbeiten können.  
  
5. Fügen Sie eine Beschreibung im Beschreibungsfeld in der oberen linken Ecke des Fensters hinzu.
  
6. Legen Sie den Bereich nach folgendem Bedingungen fest:  
  
    |||  
    |-|-|  
    |**Wenn Sie dieses Element auswählen...**|**Ist der Bereich...**|  
    |**Entität**|Modellgesteuerte Formulare und Server|  
    |**Alle Formulare**|Modellgesteuerte Formulare|  
    |Bestimmtes Formular (z. B. **Firma**-Formular)|Nur das modellgesteuerte Formular|  

    > [!TIP]
    > Wenn Sie eine Canvas-App erstellen, müssen Sie als Bereich eine Entität verwenden.
  
7. **Bedingungen hinzufügen.** Um Ihrer Geschäftsregel weitere Bedingungen hinzuzufügen:  
  
    1. Ziehen Sie die **Bedingung**-Komponente von der Registerkarte **Komponenten** auf ein Pluszeichen (+) zwischen im Designer.  
  
        ![Einer Geschäftsregel eine Bedingung hinzufügen](./media/data-platform-cds-create-business-rule/add-condition-business-rule.png "Einer Geschäftsregel eine Bedingung hinzufügen")  
  
    2. Sie können die Eigenschaften der Bedingung festlegen. Klicken Sie dazu auf die **Bedingung**-Komponente im Design, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften** auf der rechten Seite des Bildschirms fest. Wenn Sie die Eigenschaften festlegen, erstellt der Common Data Service einen Ausdruck unten auf der Registerkarte **Eigenschaften**.  
  
    3. Um eine Zusatzbestimmung (UND oder ODER) der Bedingung hinzuzufügen, klicken Sie auf **Neu** auf der Registerkarte **Eigenschaften**, um eine neue Regel zu erstellen, und legen Sie dann Eigenschaften für diese Regel fest. Im Feld **Regel-Logik** können Sie angeben, ob die neue Regel als UND oder ODER hinzugefügt werden soll.  
  
        ![Einer Bedingung eine neue Regel hinzufügen](./media/data-platform-cds-create-business-rule/add-new-rule-condition.png "Einer Bedingung eine neue Regel hinzufügen")  
  
    4. Wenn Sie die Eigenschaften für die Bedingung festgelegt haben, klicken Sie auf **Übernehmen**.  
  
8. **Aktionen hinzufügen.** Eine Aktion hinzufügen:  
  
    1. Ziehen Sie eine der Aktionskomponenten von der **Komponenten**-Registerkarte auf ein Pluszeichen neben **Bedingung**-Komponente. Ziehen Sie die Aktionen auf ein Pluszeichen neben ein Häkchen, wenn die Geschäftsregel die Aktion ausführen soll, sofern die Bedingung erfüllt wird, oder auf ein Pluszeichen neben einem x, wenn Sie die Geschäftsregel die Aktion ausführen soll, sofern die Bedingung nicht erfüllt ist.
  
        ![Eine Aktion auf eine Geschäftsregel ziehen](./media/data-platform-cds-create-business-rule/drag-an-action-business-rule.png "Eine Aktion auf eine Geschäftsregel ziehen")  
  
    2. Sie können die Eigenschaften der Aktion festlegen. Klicken Sie dazu auf die **Aktion**-Komponente im Design, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften**.  
  
    3. Wenn Sie die Eigenschaften festgelegt haben, klicken Sie auf **Übernehmen**.  
  
9. **Hinzufügen einer Unternehmensempfehlung. (Nur modellgestützt)** Um eine Unternehmensempfehlung hinzuzufügen:  
  
    1. Ziehen Sie eine der **Empfehlung**-Komponente von der **Komponenten**-Registerkarte auf eine **Bedingung**-Komponente. Ziehen Sie die **Empfehlung** -Komponente auf ein Pluszeichen neben ein Häkchen, wenn die Geschäftsregel die Aktion ausführen soll, sofern die Bedingung erfüllt wird, oder auf ein Pluszeichen neben einem x, wenn Sie die Geschäftsregel die Aktion ausführen soll, sofern die Bedingung nicht erfüllt ist.  
  
    2. Sie können die Eigenschaften der Empfehlung festlegen. Klicken Sie dazu auf die **Empfehlung**-Komponente im Designer, und legen Sie die Eigenschaften auf der Registerkarte **Eigenschaften**.  
  
    3. Um weitere Aktionen zur Empfehlung hinzuzufügen, ziehen Sie sie auf die Registerkarte **Komponenten**, und legen Sie dann auf Eigenschaften für jede Aktion auf der Registerkarte **Eigenschaften** fest.  
  
        > [!NOTE]
        >  Wenn Sie eine Empfehlung erstellen, fügt der Common Data Service standardmäßig eine einzelne Aktion hinzu. Um alle Aktionen in einer Empfehlung anzuzeigen, klicken Sie auf der Seite **Details** auf die **Empfehlung**-Komponente.  
  
    4. Wenn Sie die Eigenschaften festgelegt haben, klicken Sie auf **Übernehmen**.  
  
10. Um die Geschäftsregel zu überprüfen, klicken Sie auf **Überprüfen** auf der Aktionsleiste.  
  
11. Um die Geschäftsregel zu speichern, klicken Sie auf **Speichern** auf der Aktionsleiste.  
12. Um die Geschäftsregel zu aktivieren, wählen Sie sie im Lösungsexplorer-Fenster aus, und klicken Sie dann auf **Aktivieren**. Sie können die Geschäftsregel nicht über das Designer-Fenster aktivieren.  
  
    > [!TIP]
    >  Hier sind ein paar Tipps für die Arbeit mit den Geschäftsregeln im Designerfenster:  
    >   
    > - Um eine Momentaufnahme aller Elemente im Geschäftsregelnfenster durchzuführen, klicken Sie auf **Momentaufnahme** in der Aktionsleiste. Dies ist beispielsweise hilfreich, wenn Sie die Geschäftsregel freigeben und Kommentare von Teammitgliedern haben möchten.  
    > - Verwenden Sie die Minimap, um schnell zu anderen Teilen des Prozesses zu navigieren. Dies ist hilfreich, wenn Sie einen komplizierten Prozess haben, der nicht komplett angezeigt wird.  
    > - Wenn Sie Bedingungen, Aktionen und Unternehmensempfehlungen der Geschäftsregel hinzufügen, erstellt Common Data Service den Code für die Geschäftsregel am unteren Rand des Designerfensters. Dieser Code ist nur lesbar.  
  
## <a name="localize-error-messages-used-in-business-rules"></a>Lokalisieren der Fehlermeldungen in Geschäftsregeln  
 Sind mehrere Sprache für Ihre Organisation bereitgestellt, können Sie Ihre Fehlermeldungen lokalisieren. Bei jeder Meldung generiert das System eine Beschriftung. Wenn Sie die Übersetzungen in Ihrer Organisation exportieren, können Sie lokalisierte Versionen Ihrer Meldungen hinzufügen und diese Beschriftungen wieder im Common Data Service importieren, so dass Personen, die andere Sprachen als Ihre Ausgangssprache verwenden, die übersetzten Meldungen sehen.  
  
