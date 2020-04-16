---
title: Übersicht über die modellgetriebene Benutzeroberfläche des App-Formular-Editors für Power Apps | MicrosoftDocs
description: Kenntnis der Benutzeroberfläche des Formular-Editors zum Bearbeiten von Formularen in Power Apps.
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.assetid: 146f8035-4fcd-4572-8e71-4270cd150495
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: dbd648bd96d087ce34d8482d96507fa2391902b6
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125131"
---
# <a name="overview-of-the-model-driven-app-form-editor-user-interface"></a>Übersicht der Benutzeroberfläche des Formulareditors in der modellgesteuerten App

Der Formular-Editor-Befehle werden in zwei Menübandregisterkarten angezeigt: **Datei**, **Start** und **Einfügen**.  

- [Registerkarte Datei](#file-tab)
- [Registerkarte "Start"](#home-tab)
- [Registerkarte "Einfügen"](#insert-tab)
  
Der Formular-Editor ist in drei Bereiche unterteilt: **Navigation**, **Textkörper** und **Explorer**.  

> [!div class="mx-imgBorder"] 
> ![Formular-Editor-Benutzeroberfläche](media/form-user-interface.png)
  
**Navigation**  
Verwenden Sie den Navigationsbereich auf der linken Seite zur Kontrolle des Zugriffs auf verknüpfte Entitäten oder zum Hinzufügen von Links zu URLs zur Anzeige im Hauptbereich des Formulars. Zum Bearbeiten der Navigation müssen Sie zuerst den Befehl **Navigation** in der Gruppe **Auswählen** auf der Registerkarte **Start** auswählen.

Interaktive Formulare bieten Navigationsoptionen über die Navigationsleiste, verwenden jedoch die gleichen Daten im Navigationsbereich, um zu steuern, welche Navigationsoptionen verfügbar sind. Weitere Informationen: [Bearbeiten Navigation](use-the-form-editor-legacy.md)  


**Textkörper** <br>
Verwenden Sie den Textbereich in der Mitte zur Steuerung des Layouts des Formulars. Sie können Formularelemente auswählen und zur Positionierung ziehen. Durch Doppelklick auf ein Element werden die Eigenschaften für das Element geöffnet. 

Stzandfardmäßig zeigt für die interakiven Formulare Anfrage, Kontakt und Konto der erste Abschnitt unter der Registerkarte **Zusamenfassung** die Konto- oder Kontaktkarte vom Typ **Schnellansicht** an. Bei benutzerdefinierten Entitäten wird diese Eigenschaft standardmäßig auf festgelegt. Sie köennen einen neuen Abschnitt und ein Schnellansichtsformular hinzufügen. Das Kartenformular enthält maximal fünf Felder. Anders als bei Felder ist es nicht möglich, weitere Steuerelemente in der blauen Kachel anzuzeigen, auch wenn das Schnellansichtsformular sie enthält. 
 
>[!NOTE] 
> Um das Kartenformat beizubehalten (wie im folgenden Bild gezeigt), sollten Sie das Schnellansichtsformular nicht in einen anderen Abschnitt im Formular verschieben.

> [!div class="mx-imgBorder"] 
> ![Kartenformulare](media/card-format.png)
   
Weitere Informationen: [Erstellen und Bearbeiten von Schnellansichtsformularen](create-edit-quick-view-forms.md)  
 
-   Wählen Sie zum Hinzufügen eines Felds das Feld im **Feld-Explorer** aus, und ziehen Sie es in einen Abschnitt.  
  
    -   Um ein Element hinzuzufügen, das kein Feld ist, wählen Sie den ort dafür aus, und wählen Sie den entsprechenden Befehl aus der Registerkarte **Einfügen**.  
  
    -   Um ein Element zu entfernen, wählen Sie es aus, und verwenden Sie den Befehl **Entfernen** in der Gruppe **Bearbeiten** der Registerkarte **Start**.  
  
    -   Zum Bearbeiten der **Kopfzeile** oder der **Fußzeile** des Formulars müssen Sie zuerst den entsprechenden Befehl in der Gruppe **Auswahl** der Registerkarte **Start** auswählen.  
  
**Explorer**  
Der Inhalt des Explorerbereichs auf der rechten Seite hängt vom Kontext ab.  
  
Wenn Sie **Textkörper**, **Kopfzeile** oder **Fußzeile** in der Gruppe **Auswählen** der Registerkarte **Start** auswählen, wird der **Feld-Explorer** angezeigt. Verwenden Sie den **Feld-Explorer**, um Felder zu ziehen, die in einem Abschnitt des Formulars oder im Kopf- oder Fußbereich angezeigt werden sollen. Sie können das gleiche Feld auch mehrmals in einem Formular hinzufügen. Verwenden Sie die Schaltfläche **Neues Feld**, um ein neues Feld erstellen.  
  
Wenn Sie **Navigation** in der Gruppe **Auswahl** der Registerkarte **Start** auswählen, sehen Sie den **Beziehungs-Explorer**. Ziehen Sie eine beliebige Beziehung in eine der Gruppen im Navigationsbereich. Sie können dieselbe Beziehung nicht zwei Mal hinzufügen. Die Verfügbarkeit von Beziehungen basiert darauf, wie sie konfiguriert sind. Wenn Sie eine Beziehung so konfigurieren, dass sie nicht angezeigt wird, wird sie nicht im **Beziehungs-Explorer** angezeigt. Informationen dazu, wie Standardanzeigenoptionen für Beziehungen konfiguriert werden, finden Sie unter [Navigationsbereichelement für primäre Entität](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity).
  
Sie können die Schaltflächen **Neue 1: n** und **Neue n: N** verwenden, um neue Entitätsbeziehungen hinzuzufügen.  

## <a name="file-tab"></a>Registerkarte Datei

Wählen Sie **Datei** Registerkarten/Entitätsansicht hinzuzufügen die folgenden Optionen aus:

- **Neue Aktivität** Hinzufügen einer neuen Aktivität hinzu
- **Neuer Datensatzh** Neu zu diesem Datensatz hinzufügen
- **Extras** Optionen wie Daten, und Massenlöschungsassistent und Duplikaterkennung
- **Optionen** Ändern Sie die Einstellungen für die Standardanzeige, um die Standardlösung individuell anzupassen, und verwalten Sie Ihre E-Mail-Vorlagen.
    - Allgemein
    - Synchronisierung
    - Aktivitäten
    - Formate
    - E-Mail-Vorlagen
    - E-Mail-Signaturen
    - E-Mail
    - Datenschutz
    - Sprachen
- Hilfe
- Schließen


## <a name="home-tab"></a>Registerkarte "Start"  
 Die Registerkarte **Start** zeigt die Befehle in der Auflistung der folgenden Tabelle an:

> [!div class="mx-imgBorder"] 
> ![Registerkarte "Start"](media/home-tab.png)

|Gruppe|Befehl|Beschreibung|
|-----------|-------------|-----------------| 
|**Speichern**|**Speichern** **(Strg+S)**|Speichern Sie das Formular.|
||**Speichern unter**|Erstellen einer Kopie des Formulars unter einem anderen Namen.|
||**Speichern und schließen**|Speichern des Formulars und Schließen des Formular-Editors.|
||**Veröffentlichen**|Veröffentlichen des Formulars. Weitere Informationen: Exportieren von Anpassungen|
|**Bearbeiten**|**Eigenschaften ändern**|Ändern der Eigenschaften des ausgewählten Elements im Textkörper.<br /><br /> Vgl. die folgenden Abschnitte, abhängig vom ausgewählten Element:<br /><br /> -   [Eigenschaften von Registerkarte](tab-properties-legacy.md)<br />-   [Abschnittseigenschaften](section-properties-legacy.md)<br />-   [Allgemeine Feldeigenschaften](common-field-properties-legacy.md)<br />-   [Spezielle Feldeigenschaften](special-field-properties-legacy.md)<br />-  [Unterrastereigenschaften](sub-grid-properties-legacy.md)<br />-   [Eigenschaften des Steuerelements für die Schnellansicht](quick-view-control-properties-legacy.md)|
||**Entfernen**|Entfernen Sie das ausgewählte Element.|
||**Rückgängig** **(Strg+Z)**|Macht die vorherige Aktion rückgängig.|
||**Wiederholen** **(Strg+Y)**|Wiederholt die vorherige Aktion.|
|**Auswählen**|**Textkörper**|Bearbeiten des Hauptteils des Formulars.|
||**Kopfzeile**|Bearbeiten der Kopfzeile des Formulars.|
||**Fußzeile**|Dient zum Bearbeiten der Fußzeile des Formulars.|
||**Navigation**|Dient zum Bearbeiten der Formularnavigation.<br /><br /> Weitere Informationen: [Bearbeiten Navigation](use-the-form-editor-legacy.md)
|**Formular**|**Geschäftsregeln**|Neue Geschäftsregeln mit dem Geschäftsregel-Explorer anzeigen, bearbeiten oder erstellen. **Hinweis:** Für die interaktiven Formulare werden nur die Bereiche "Entität" und "Alle Formulare" unterstützt.<br /><br /> Weitere Informationen [Erstellen und Bearbeiten von Geschäftsregeln](create-business-rules-recommendations-apply-logic-form.md)|
||**Formulareigenschaften**| Weitere Informationen: [Formulareigenschaften](form-properties-legacy.md)|  
||**Vorschau**|Verwenden Sie diesen Antworttyp, um festzustellen, wie das Formular nach der Veröffentlichung aussieht. Sie können außerdem in der Vorschau anzeigen, um die in Skripts testen, die mit von Ereignissen zugeordnet werden.|         
||**Sicherheitsrollen aktivieren**|Verwenden Sie dies, um einzustellen, welche Sicherheitsrollen auf die Formulare Zugriff haben. Weitere Informationen:  [Zugriff auf Formulare steuern](control-access-forms.md) **Wichtig:**  Wenn Sie ein neues Formular erstellen, haben nur die Sicherheitsrollen "Systemadministrator" und "Systemanpasser" Zugriff auf das Formular. Sie müssen anderen Sicherheitsrollen den Zugriff gewähren, damit Benutzer das Formular verwenden können.|  
||**Abhängigkeiten anzeigen**|Sehen Sie, welche Lösungskomponenten von diesem Formular abhängen, und welche Lösungskomponente für dieses Formular erforderlich sind. |  
||**Verwaltete Eigenschaften**|Verwalter besitzt zwei Eigenschaftenbefehl Eigenschaften **Anpassbar** und **Kann gelöscht werden** Das Setzen dieser Eigenschaften auf false bedeutet, dass das Formular nicht anpassbar ist und nicht gelöscht werden kann, nachdem Sie es in eine Lösung aufgenommen haben, diese Lösung als verwaltete Lösung exportieren und diese verwaltete Lösung in eine andere Umgebung importieren. Weitere Informationen: [Verwaltete Eigenschaften](../common-data-service/solutions-overview.md#managed-properties)| 
|**Upgraden**|**Formulare zusammenführen**|Ggf. können diese Option Sie das Formular mit einem Formular in einer früheren Version von Dynamics 365 Formular zusammenführen|
  

## <a name="insert-tab"></a>Registerkarte "Einfügen"  
> [!div class="mx-imgBorder"] 
> ![Registerkarte "Einfügen"](media/insert-tab.png)
 
Die Registerkarte Einfügen zeigt die Befehle in der folgenden Tabelle an:

|Gruppe|Befehl|Beschreibung|
|-----------|-------------|-----------------| 
||**Abschnitt**|Hinzufügen eines Abschnitts zu einer ausgewählten Registerkarte. Sie können festlegen, dass ein Abschnitt eine bis zu vier Spalten enthält.<br /><br /> Sie können auch einen Bezugsbereich in den interaktiven Formularen einfügen. Der Bereich "Verweise" wird auch als Abschnitt zum Formular vom Typ „Hauptbereich – Interaktive Funktionen“ hinzugefügt. Standardmäßig ist der Bereich "Verweise" den Formularen für Anfragen, Konto, Kontakt und Entität hinzugefügt.<br /><br /> Weitere Informationen: [Abschnittseigenschaften](section-properties-legacy.md)|  
|**3 Registerkarten**|**Drei Spalten**|Fügen Sie eine Registerkarte mit drei gleich breiten Spalten ein.<br /><br /> Weitere Informationen: [Registerkarteneigenschaften](tab-properties-legacy.md)|  
||**Drei Spalten**|Fügen Sie eine Registerkarte mit drei Spalten ein, die eine breitere mittlere Spalte aufweist.|  
|**2 Registerkarten**|**Zwei Spalten**|Fügen Sie eine Registerkarte mit zwei Spalten ein, die eine breitere rechte Spalte aufweist.|  
||**Zwei Spalten**|Fügen Sie eine Registerkarte mit zwei Spalten ein, die eine breitere linke Spalte aufweist.|  
||**Zwei Spalten**|Fügen Sie eine Registerkarte mit zwei gleich breiten Spalten ein.|  
|**1 Registerkarte**|**Eine Spalte**|Fügen Sie eine einspaltige Registerkarte ein.|  
|**Steuerelement**|**Unterraster**|Dient zum Formatieren eines Unterrasters und zum Einfügen des Unterrasters in das Formular.<br /><br /> Weitere Informationen: [Unterrastereigenschaften](sub-grid-properties-legacy.md)|  
||**Abstandhalter**|Fügt einen leeren Bereich ein.|  
||**Schnellansichtsformular**|Hinzufügen eines Schnellansichtsformular.<br /><br /> Weitere Informationen: [Eigenschaften zum Steuerelement für die Schnellansicht](quick-view-control-properties-legacy.md)|  
||**Webressource**|Fügen Sie eine Netzressource ein, um Inhalt von anderen Standorten in einer Seite einzubetten.<br /><br /> Weitere Informationen: [Webressourceneigenschaften](web-resource-properties-legacy.md)|  
||**IFRAME**|Sie können einen IFRAME einem Formular hinzufügen, um Inhalt von einer anderen Website in einem Formular zu integrieren.| 
||**Zeitplanung**|Hinzufügen eines Zeitplansteuerelement im Formular. Dieses Steuerelement zeigt den Zeitplan an Aktivitäten, die mit der Entität auf einem Formular zu tun haben.|  
||**Navigationslink**|Mithilfe dieser Option können Sie den Link in eine Formularnavigation einfügen.|  
||**Zeitgeber**|Hinzufügen eines Zeitgebersteuerelements zum Formular "Anfrage" zum Nachverfolgen von Zeit anhand eines SLA. Weitere Informationen: [Hinzufügen eines Zeitgeber-Steuerelements](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/add-timer-control-case-form-track-time-against-sla)|
||**Suche in der Wissensdatenbank**|Fügen Sie ein Suchsteuerelement ein, mit dem Benutzer nach Wissensartikeln suchen können. Weitere Informationen:  [Suchsteuerelement für die Wissensdatenbank](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/add-knowledge-base-search-control-forms).|  
||**Beziehungsassistent**|Mithilfe dieser Option können Sie ein Beziehungsassistent-Steuerelement in das Formular einfügen.|

>[!Note] 
>Die folgenden Komponenten werden nicht in Hauptformularen unterstützt:<br> <ul> <li>Bing Maps <br><li>Yammer <br><li>Aktivitätsfeeds <br> </li> </ul>


## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)  
