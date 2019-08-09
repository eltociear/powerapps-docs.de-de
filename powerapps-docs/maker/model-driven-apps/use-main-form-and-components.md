---
title: Verwenden Sie das modellgesteuerte App-Hauptformular und seine Komponenten in PowerApps | Microsoft Docs
description: 'Wissen, wie das Hauptformular und die Komponenten in einer auf einheitlicher Schnittstelle basierter Apps verwendet werden'
keywords: Hauptformulare; Customer Service; Customer Service-Hub; Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: powerapps
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 43bfface-4dc2-411d-99a1-83e934646989
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-model-driven-app-main-form-and-its-components"></a>Verwenden Sie das modellgesteuerte App-Hauptformular und seine Komponenten.

Formulare haben eine verbesserte Benutzerfreundlichkeit, die für die Agentenproduktivität optimiert ist. Sie erleichtern das Verwalten des Kontexts, während gleichzeitig an zugehörigen Datensätzen gearbeitet wird. Die Formulare finden Sie im Projektmappen-Explorer im Bereich Lösungs-Anpassung. Der Formulartyp der neuen Formularen ist **Hauptformular**.

In diesem Thema wird beschrieben, wie ein Hauptformular bearbeitet werden kann und wie verschiedene Elemente des Formulars hinzugefügt werden.

## <a name="open-the-form-editor"></a>Öffnen des Formulareditors

Wenn Sie ein Formular bearbeiten möchten oder Elemente ändern möchten, verwenden Sie den Formular-Editor. Im Formular-Editor können Sie Formulare für alle einheitliche Schnittstelle basierten Apps bearbeiten.

Gehen Sie wie folgt vor, um auf den Formular-Editor zuzugreifen. 

> [!NOTE]
> Wenn Sie neue Lösungskomponenten bei der Bearbeitung des Formulars erstellen, verwenden die Namen der Komponenten das Anpassungspräfix des Lösungsherausgebers für die Standardlösung und diese Komponenten werden nur in der Standardlösung eingeschlossen. Wenn neue Lösungskomponenten in einer bestimmten nicht verwalteten Lösung eingeschlossen werden sollen, öffnen Sie den Formulareditor über diese nicht verwaltete Lösung.


### <a name="access-the-form-editor-through-app-designer-in-powerapps"></a>Zugriff auf den Formular-Editor über den App-Designer in PowerApps

1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Klicken Sie im linken Navigationsbereich die Option **Apps**, wählen die gewünschte App aus und klicken Sie dann auf der Symbolleiste die Option **Bearbeiten** an.  

3. Wählen Sie auf der App-Design-Canvas den Pfeil nach unten ![Pfeil nach unten für Anwendungs-Designer](media/down-arrow-app-designer.png) neben einer Entität, um die Formulare anzuzeigen, die für diese Entität verfügbar sind. 

4. Wählen Sie die Schaltfläche "Designer öffnen" ![Designer öffnen](media/site-map-designer.png)entsprechend dem zu bearbeitenden Formular.

   ![Im Anwendungs-Designer Formular-Editor](media/app-designer-forms.png)
 
5. Nehmen Sie im Formulardesigner Ihre Änderungen vor und wählen Sie dann **Speichern**, um die Änderungen zu speichern und **Veröffentlichen**, um sie zur Verwendung in der App zu veröffentlichen. 

> [!NOTE]
> Falls Sie weitere Änderungen an der App vorgenommen haben, veröffentlichen Sie sie mithilfe der App-Ebenenveröffentlichungsoption. Unter [Validieren und veröffentlichen einer App mit dem App-Designer](validate-app.md) finden Sie weitere Informationen.

> [!NOTE]
> Das Webclient-Hauptformular ist ebenfalls mit dem Customer Service Hub kompatibel und kann mit dem App Designer bearbeitet werden.


### <a name="access-the-form-editor-through-the-default-solution"></a>Zugiff auf den Formulareditor über die Standardlösung

1.  Melden Sie sich bei [PowerApps](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.  

3. Öffnen Sie in der Liste der Formulare das Formular des Typs **Haupt**.

### <a name="access-the-form-editor-for-an-unmanaged-solution"></a>Zugriff auf den Formulareditor für eine nicht verwaltete Lösung

1. Öffnen Sie die [Lösung](advanced-navigation.md#solutions).
2. Doppelklicken Sie auf die nicht verwaltete Lösung, die Sie verwenden möchten. Der Lösungstyp, verwaltet oder nicht verwaltet, wird in der Spalte **Pakettyp** angezeigt.
3. Suchen Sie in der Liste der Komponenten die Entität mit dem Formular, das Sie bearbeiten möchten. Falls die Entität nicht vorhanden ist, müssen Sie sie hinzufügen möchten.

#### <a name="add-an-entity-to-an-unmanaged-solution"></a>Hinzufügen einer Entität zu einer nicht verwalteten Lösung

1. Wenn nun die nicht verwaltete Lösung im Lösungsexplorer geöffnet ist, wählen Sie den Knoten **Entitäten** und in der Symbolleiste oberhalb der Liste **Vorhandenes Element hinzufügen**.

     > [!div class="mx-imgBorder"] 
     > ![Vorhandene Entitäten hinzufügen](media/add-existing-entity.png)

2. Wählen Sie im Dialogfeld **Lösungskomponenten auswählen**, wenn die Auswahl **Komponententyp** auf **Entität** festgelegt ist, die Entität aus, die Sie hinzufügen möchten, und klicken Sie auf **OK**.

3. Wenn das Dialogfeld **Fehlende erforderliche Komponenten** angezeigt wird, können Sie auf **Nein, erforderliche Komponenten nicht einschließen** klicken, wenn Sie diese nicht verwaltete Lösung nicht in eine andere Organisation importieren möchten. Wenn Sie die fehlenden erforderlichen Komponenten derzeit nicht einschließen möchten, können Sie sie später hinzufügen. Sie erhalten erneut eine Benachrichtigung, wenn Sie diese Lösung später exportieren.

4. Erweitern Sie im Lösungsexplorer die Entität mit dem Formular, das Sie bearbeiten wollen, und wählen Sie **Formulare**.

5. Öffnen Sie in der Liste der Formulare das Formular des Typs **Haupt**.

#### <a name="publish-the-changes-for-use-in-the-app"></a>Veröffentlichen der Änderungen in der App

Bestimmte Anpassungen, die Änderungen an der Benutzeroberfläche vornehmen, erfordern, dass sie veröffentlicht werden, bevor Benutzern sie in der Anwendung verwenden können. Um ihre Anpassung zu veröffentlichen, wählen Sie in der Symbolleiste des Lösungsexplorers **Alle Anpassungen veröffentlichen**.

## <a name="form-editor-user-interface"></a>Formular-Editor-Benutzeroberfläche

Um die Benutzeroberfläche des Formular-Editors im Detail zu verstehen, siehe [Übersicht zur Formular-Editor-Benutzeroberfläche](form-editor-user-interface-legacy.md).

## <a name="form-properties"></a>Formulareigenschaften

Für Details zu den Formulareigenschaften siehe [Formulareigenschaften](form-properties-legacy.md).

## <a name="visibility-options"></a>Sichtbarkeitsoptionen  
 Einige Arten von Formularelementen können standardmäßig ein- oder ausgeblendet werden. Felder, Abschnitte, Felder bieten alle diese Option. Das Verwenden von Skripts oder Geschäftsregeln steuert die Sichtbarkeit diese Elemente, um ein dynamisches Formular erstellen, das eine Oberfläche bietet, die sich an die Bedingungen in dem Formular anpasst. 
  
> [!NOTE]
>  Das Ausblenden von Formularelementen ist keine empfohlene Möglichkeit zur Durchsetzung von Sicherheitsprinzipien. Es gibt verschiedene Möglichkeiten, mit denen Benutzer alle Elemente und Daten im Formular anzeigen können, wenn Elemente ausgeblendet werden. Weitere Informationen finden Sie unter: [Anzeigen oder Ausblenden von Formularelementen](visibility-options-legacy.md) 
  
## <a name="tab-properties"></a>Eigenschaften der Registerkarte  

Im Textkörper der Formularregisterkarten steht eine horizontale Trennung zur Verfügung. Registerkarten haben eine Beschriftung, die angezeigt werden kann. Wenn die Beschriftung angezeigt wird, können Registerkarten erweitert oder reduziert werden, um ihre Inhalte ein- oder auszublenden, indem Sie die Beschriftung auswählen. Für Details zu den Formulareigenschaften siehe [Registerkarteneigenschaften](tab-properties-legacy.md).


## <a name="section-properties"></a>Abschnittseigenschaften  

Ein Abschnitt in einem Formular nimmt den in einer Registerkartenspalte verfügbaren Raum ein. Abschnitte enthalten eine Beschriftung, die angezeigt werden kann, sowie eine Zeile, die unter der Beschriftung angezeigt werden kann. Für Details zu den Abschnitteigenschaften siehe [Abschnitteigenschaften](section-properties-legacy.md).
  
## <a name="timeline"></a>Zeitleiste  
 Der Zeitplan zeigt verknüpfte Aktivitäten für eine bestimmten Entität an.  
  
 Folgende Aktivitätstypen werden unterstützt: Aufgabe, Termin, Telefonanruf, E-Mail, soziale Aktivität, benutzerdefinierte Aktivität.  
  
 Die Timeline zeigt ebenfalls alle verknüpften Systembeiträge oder Notizen an. Es zeigt die Aktivitäten an, bei denen das Feld **Bezug** auf die Entität festgelegt ist, die Sie anzeigen. Für Notizen wird dem Benutzer das Feld **Bezug** nicht angezeigt. Es ist implizit, wenn es aus der Interaktionspinnwand erstellt wird.  
  
 Jede der Aktivität, die in der Timeline wird, verfügt über dieselben raschen Aktionen, die auf der Befehlsleiste der Aktivität zur Verfügung stehen.  

## <a name="common-field-properties"></a>Feldeigenschaften  

Für Details zu den gemeinsamen Feldeigenschaften siehe [Gemeinsame Feldeigenschaften](common-field-properties-legacy.md). 
  
## <a name="special-field-properties"></a>Spezielle Feldeigenschaften  
 Alle Felder haben die unter [Allgemeine Feldeigenschaften](common-field-properties-legacy.md) aufgeführten Eigenschaften, bestimmte Felder verfügen jedoch über zusätzliche Eigenschaften. Weitere Informationen finden Sie unter [Spezielle Feldeigenschaften](special-field-properties-legacy.md).

  
## <a name="sub-grid-properties"></a>Unterrastereigenschaften  

Sie können ein Unterraster auf einem Formular konfigurieren, um eine Liste von Datensätzen oder ein Diagramm anzuzeigen. Für Details zu den Unterrastereigenschaften siehe [Unterrastereigenschaften](sub-grid-properties-legacy.md).

## <a name="quick-view-control-properties"></a>Eigenschaften des Steuerelements für die Schnellansicht  

Ein Steuerelement für die Schnellansicht in einem Formular zeigt Daten aus einem Datensatz an, der bei einer Suche im Formular ausgewählt wurde. Um die Steuerelement für die Schnellansicht-Steuereigenschaften zu suchen, gehen Sie zu [Schnellansicht-Steuereigenschaften](quick-view-control-properties-legacy.md).
  
## <a name="web-resource-properties"></a>Webressourceneigenschaften  

Webressourcen können Sie in einem Formular hinzufügen oder bearbeiten, um sie für mehr App-Benutzer anziehend oder nützlich zu gestalten. Formularfähige Webressourcen sind Bilder, HTML-Dateien oder Silverlight-Steuerelemente. Lernen Sie die Details über Webressourceneigenschaften. Gehen Sie zu [Webressourceneigenschaften](web-resource-properties-legacy.md). 
  
## <a name="iframe-properties"></a>IFRAME-Eigenschaften  

Sie können iFrames einem Formular hinzufügen, um Inhalt von einer anderen Website in einem Formular zu integrieren. Für Details zu den IFRAME-Eigenschaften siehe [IFRAME-Eigenschaften](iframe-properties-legacy.md). 
  
## <a name="edit-navigation"></a> Bearbeiten der Navigation  
 Die Navigation innerhalb des Formulars ermöglicht die Anzeige einer Liste verknüpfter Datensätze. Jede Entitätsbeziehung verfügt über Eigenschaften, die steuern, ob sie angezeigt werden soll. Weitere Informationen: [Navigationsbereichselement für die primäre Entität ](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)
  
 Alle Entitätsbeziehungen, die so konfiguriert werden, dass sie angezeigt werden, können im Formular-Editor überschrieben werden.  
  
 Ausführliche Anleitungen finden Sie unter [Hinzufügen oder Bearbeiten der Formularnavigation für verknüpfte Entitäten](add-edit-form-navigation-related-entities.md).
  
 Zur Aktivierung der Bearbeitung der Navigation müssen Sie zuerst den Befehl **Navigation** in der Gruppe **Auswählen** auf der Registerkarte **Start** auswählen.  
  
 Im **Beziehungs-Explorer** können Sie nach 1:n- oder n:n-Beziehungen filtern oder alle verfügbaren Beziehungen anzeigen Das Kontrollkästchen **Nur nicht verwendete Beziehungen anzeigen** ist aktiviert und ausgewählt. Sie können daher nur jeweils eine Beziehung gleichzeitig hinzufügen.  
  
 Um eine Beziehung aus dem **Beziehungs-Explorer** hinzuzufügen, doppelklicken Sie einfach darauf; sie wird dann unter der aktuell ausgewählten Beziehung im Navigationsbereich hinzugefügt. Doppelklicken Sie auf eine Beziehung im Navigationsbereich und Sie können die Bezeichnung auf **Anzeigen** festlegen. Auf der Registerkarte **Name** können Sie Informationen zur Beziehung finden. Verwenden Sie die Schaltfläche **Bearbeiten**, um die Definition der Entität zu öffnen.  
  
 Es stehen fünf Gruppen im Navigationsbereich zur Verfügung. Sie können sie ziehen, um sie neu zu positionieren, und doppelklicken, um die Bezeichnung ändern, Sie können sie jedoch nicht entfernen. Diese Gruppen werden nur angezeigt, wenn sie Inhalte haben. Wenn Sie nicht möchten, dass eine Gruppe angezeigt wird, fügen Sie ihr einfach nichts hinzu.  
  
## <a name="configure-event-handlers"></a>Konfigurieren von Ereignishandlern  

Ein Ereignishandler besteht aus einem Verweis auf eine JavaScript-Webressource und eine Funktion, die innerhalb dieser Webressource definiert ist und ausgeführt wird, wenn das Ereignis auftritt. Weitere Informationen zum Konfigurieren von Ereignishandlern finden Sie unter [Konfigurieren von Ereignishandler](configure-event-handlers-legacy.md). 
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen und Gesalten von Formularen](create-design-forms.md)   
 [Erstellen und Bearbeiten von Schnellerstellungsformularen](create-edit-quick-view-forms.md)   
 [Erstellen und Bearbeiten von Schnellansichtsformularen](create-edit-quick-view-forms.md)
