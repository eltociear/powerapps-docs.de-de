---
title: Übersicht über die Benutzeroberfläche des Formular-Editors einer modellgesteuerten App für PowerApps | Microsoft-Dokumentation
description: Informationen zur Benutzeroberfläche des Formular-Editors zum Bearbeiten von Formularen in PowerApps
keywords: Formulare; Hauptformular; einheitliche App-Oberfläche; Dynamics 365 for Customer Engagement
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.assetid: 146f8035-4fcd-4572-8e71-4270cd150495
ms.openlocfilehash: a44987e7b8809dea46f164224974a21a2d9a5010
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39688552"
---
# <a name="overview-of-the-model-driven-app-form-editor-user-interface"></a>Überblick über die Benutzeroberfläche des Formular-Editors einer modellgesteuerten App

Der Formular-Editor zeigt Befehle auf drei Registerkarten an: **Datei**, **Start** und **Einfügen**.  

- [Registerkarte „Datei“](#file-tab)
- [Registerkarte „Start“](#home-tab)
- [Registerkarte „Einfügen“](#insert-tab)
  
Der Formular-Editor ist in drei Bereiche unterteilt: **Navigation**, **Text** und **Explorer**.  

![Benutzeroberfläche des Formular-Editors](media/form-user-interface.png)
  
**Navigation**  
Verwenden Sie den Navigationsbereich auf der linken Seite, um den Zugriff auf verknüpfte Entitäten zu steuern oder um URLs Links hinzuzufügen, die im Hauptbereich des Formulars angezeigt werden. Um die Navigation zu bearbeiten, müssen Sie zunächst auf der Registerkarte **Start** in der Gruppe **Auswählen** den Befehl **Navigation** auswählen.

Hauptformulare bieten Navigationsoptionen über die Navigationsleiste, verwenden aber die gleichen Daten im Navigationsbereich, um die verfügbaren Navigationsoptionen zu steuern. Weitere Informationen finden Sie unter [Bearbeiten der Navigation](use-the-form-editor-legacy.md).  


**Text** <br>
Verwenden Sie den Textbereich in der Mitte, um das Formularlayout zu bestimmen. Sie können Formularelemente auswählen und verschieben, um sie anzuordnen. Durch Doppelklicken auf ein Element öffnen Sie die Eigenschaften des Elements. 

Standardmäßig wird für die Hauptformulare „Fall“, „Kontakt“ und „Konto“ im ersten Abschnitt auf der Registerkarte **Zusammenfassung** das Konto- oder Kontaktkartenformular vom Typ **Schnellansicht** angezeigt. Für benutzerdefinierte Entitäten ist dieser Abschnitt standardmäßig nicht verfügbar. Sie können einen neuen Abschnitt mit einem entsprechenden Schnellansichtsformular einfügen. Das Kartenformular zeigt höchstens fünf Felder an. In der blauen Kachel können keine anderen Steuerelemente als Felder angezeigt werden, selbst wenn sie im Schnellansichtsformular enthalten sind. 
 
>[!NOTE] 
> Um das Kartenformat (s. Abb.) zu erhalten, wird empfohlen, das Schnellansichtsformular nicht in einen anderen Abschnitt des Formulars zu verschieben.

![Kartenformat](media/card-format.png)
   
Weitere Informationen finden Sie unter [Erstellen und Bearbeiten von Schnellansichtsformularen](create-edit-quick-view-forms.md).  
 
-   Um ein Feld hinzuzufügen, wählen Sie es im **Feld-Explorer** aus, und ziehen Sie es in einen Abschnitt.  
  
    -   Um ein Element hinzuzufügen, das kein Feld ist, wählen Sie aus, wo Sie es platzieren möchten, und verwenden Sie zum Hinzufügen den entsprechenden Befehl aus der Registerkarte **Einfügen**.  
  
    -   Um ein Element zu entfernen, markieren Sie es und verwenden Sie auf der Registerkarte **Start** in der Gruppe **Bearbeiten** den Befehl **Entfernen**.  
  
    -   Um die **Kopfzeile** oder die **Fußzeile** des Formulars zu bearbeiten, müssen Sie zunächst auf der Registerkarte **Start** den entsprechenden Befehl in der Gruppe **Auswählen** auswählen.  
  
**Explorer**  
Auf der rechten Seite befindet sich der Inhalt des Explorer-Bereichs, der vom Kontext abhängt.  
  
Wenn Sie **Text**, **Kopfzeile** oder **Fußzeile** in der Gruppe **Auswählen** auf der Registerkarte **Start** auswählen, wird der **Feld-Explorer** angezeigt. Verwenden Sie den **Feld-Explorer**, um Felder, die Sie anzeigen möchten, in einen Abschnitt im Formular oder in die Kopf- bzw. Fußzeile zu ziehen. Das gleiche Feld kann mehrmals in einem Formular enthalten sein. Verwenden Sie die Schaltfläche **Neues Feld** als Verknüpfung zum Erstellen eines neuen Felds.  
  
Wenn Sie **Navigation** in der Gruppe **Auswählen** auf der Registerkarte **Start** auswählen, wird der **Beziehungs-Explorer** angezeigt. Ziehen Sie eine der Beziehungen in eine der Gruppen im Navigationsbereich. Die gleiche Beziehung lässt sich nicht zweimal hinzufügen. Beziehungen sind basierend auf ihrer Konfiguration verfügbar. Wenn Sie eine Beziehung so konfigurieren, dass sie nicht angezeigt wird, wird sie im **Beziehungs-Explorer** nicht angezeigt. Informationen zum Konfigurieren der Standardanzeigeoptionen für Beziehungen finden Sie unter [Element im Navigationsbereich für die primäre Entität](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity).
  
Sie können die Schaltflächen **Neu 1:n** und **Neu n:n** als Verknüpfung verwenden, um neue Entitätsbeziehungen hinzuzufügen.  

## <a name="file-tab"></a>Registerkarte „Datei“

Wählen Sie die Registerkarte **Datei** aus, um die folgenden Optionen hinzuzufügen/anzuzeigen:

- **Neue Aktivität**: Hinzufügen einer neuen Aktivität
- **Neuer Datensatz**: Hinzufügen eines neuen Datensatzes
- **Tools**: Optionen wie Datenimport, Duplikaterkennung und Massenlöschungs-Assistent
- **Optionen**: Personalisieren der Standardlösung durch Ändern der Standardanzeigeeinstellungen und E-Mail-Vorlagenverwaltung
    - Allgemein
    - Synchronisierung
    - Aktivitäten
    - Formate
    - E-Mail-Vorlagen
    - E-Mail-Signaturen
    - E-Mail-Adresse
    - Datenschutz
    - Sprachen
- Hilfe
- Schließen


## <a name="home-tab"></a>Registerkarte „Start“  
 Die Registerkarte **Start** zeigt die Befehle in dieser Tabelle an:

![Registerkarte „Start“](media/home-tab.png)

|Gruppe|Befehl|Beschreibung|
|-----------|-------------|-----------------| 
|**Speichern**|**Speichern** **(STRG+S)**|Speichert das Formular.|
||**Speichern unter**|Erstellt eine Kopie dieses Formulars mit einem anderen Namen.|
||**Speichern und schließen**|Speichert das Formular und schließt den Formular-Editor.|
||**Veröffentlichen**|Veröffentlicht das Formular. Weitere Informationen finden Sie unter „Veröffentlichen von Anpassungen“.|
|**Bearbeiten**|**Eigenschaften ändern**|Ändert die Eigenschaften des ausgewählten Elements im Text.<br /><br /> In den folgenden Abschnitten finden Sie weitere Informationen zum ausgewählten Element:<br /><br /> -   [Registerkarteneigenschaften](tab-properties-legacy.md)<br />-   [Abschnittseigenschaften](section-properties-legacy.md)<br />-   [Allgemeine Feldeigenschaften](common-field-properties-legacy.md)<br />-   [Spezielle Feldeigenschaften](special-field-properties-legacy.md)<br />-  [Unterrastereigenschaften](sub-grid-properties-legacy.md)<br />-   [Eigenschaften zum Steuerelement für die Schnellansicht](quick-view-control-properties-legacy.md)|
||**Entfernen**|Entfernt das ausgewählte Element.|
||**Rückgängig** **(STRG+Z)**|Macht die vorherige Aktion rückgängig.|
||**Wiederholen** **(STRG+Y)**|Wiederholt die vorherige Aktion.|
|**Auswählen**|**Text**|Bearbeitet den Hauptteil des Formulars.|
||**Kopfzeile**|Bearbeitet die Kopfzeile des Formulars.|
||**Fußzeile**|Bearbeitet die Fußzeile des Formulars.|
||**Navigation**|Bearbeitet die Formularnavigation.<br /><br /> Weitere Informationen finden Sie unter [Bearbeiten der Navigation](use-the-form-editor-legacy.md).
|**Formular**|**Geschäftsregeln**|Anzeigen und Bearbeiten von oder Erstellen neuer Geschäftsregeln mit dem Geschäftsregel-Explorer. **Hinweis:** Für interaktive Formulare werden nur die Bereiche „Entität“ und „Alle Formulare“ unterstützt.<br /><br /> Weitere Informationen finden Sie unter [Erstellen und Bearbeiten von Geschäftsregeln](create-business-rules-recommendations-apply-logic-form.md).|
||**Formulareigenschaften**| Weitere Informationen finden Sie unter [Formulareigenschaften](form-properties-legacy.md).|  
||**Vorschau**|Zeigt eine Vorschau des Formulars nach seiner Veröffentlichung an. Sie können auch eine Vorschau anzeigen, um Skripts zu testen, die mit Ereignissen verknüpft sind.|         
||**Sicherheitsrollen aktivieren**|Legt fest, welche Sicherheitsrollen Zugriff auf die Formulare haben. Weitere Informationen finden Sie unter [Steuern des Zugriffs auf Formulare](control-access-forms.md). **Wichtig:** Wenn Sie ein neues Formular erstellen, haben nur die Sicherheitsrollen „Systemadministrator“ und „Systemanpasser“ Zugriff auf das Formular. Sie müssen anderen Sicherheitsrollen Zugriff zuweisen, bevor sie verwendet werden können.|  
||**Abhängigkeiten anzeigen**|Zeigt an, welche Lösungskomponenten von diesem Formular abhängen und welche Lösungskomponenten dieses Formular erfordert. Weitere Informationen finden Sie unter [Lösungsabhängigkeiten](../common-data-service/overview.md).|  
||**Verwaltete Eigenschaften**|Dieser Befehl verfügt über zwei Eigenschaften: **Anpassbar** und **Kann gelöscht werden**. Wenn Sie für diese Eigenschaften FALSE festlegen, lässt sich das Formular weder anpassen noch löschen, nachdem es in eine Lösung integriert wurde. Exportieren Sie diese Lösung als verwaltete Lösung und importieren Sie diese verwaltete Lösung in eine andere Umgebung. Weitere Informationen finden Sie unter [Verwaltete Eigenschaften](../common-data-service/solutions-overview.md#managed-properties).| 
|**Upgrade**|**Formulare zusammenführen**|Falls verfügbar, führt diese Option dieses Formular mit einem Formular aus einer früheren Version des Dynamics 365-Formulars zusammen.|
  

## <a name="insert-tab"></a>Registerkarte „Einfügen“  
![Registerkarte „Einfügen“](media/insert-tab.png)
 
Die Registerkarte „Einfügen“ zeigt die Befehle in dieser Tabelle an:

|Gruppe|Befehl|Beschreibung|
|-----------|-------------|-----------------| 
||**Abschnitt**|Fügt der ausgewählten Registerkarte einen Abschnitt hinzu. Dieser kann bis zu vier Spalten umfassen.<br /><br /> Sie können ebenfalls einen Bereich „Verweise“ in interaktive Formulare einfügen. Der Bereich „Verweise“ wird auch als Abschnitt dem Hauptformular für interaktive Funktionen hinzugefügt. Standardmäßig wird der Bereich „Verweise“ den Formularen „Fall“, „Konto“, „Kontakt“ und „Benutzerdefinierte Entität“ hinzugefügt.<br /><br /> Weitere Informationen finden Sie unter [Abschnittseigenschaften](section-properties-legacy.md).|  
|**3 Registerkarten**|**Drei Spalten**|Fügt eine Registerkarte mit drei Spalten mit gleicher Breite ein.<br /><br /> Weitere Informationen finden Sie unter [Registerkarteneigenschaften](tab-properties-legacy.md).|  
||**Drei Spalten**|Fügt eine Registerkarte mit drei Spalten mit einer breiteren mittleren Spalte ein.|  
|**2 Registerkarten**|**Zwei Spalten**|Fügt eine Registerkarte mit zwei Spalten mit einer breiteren rechten Spalte ein.|  
||**Zwei Spalten**|Fügt eine Registerkarte mit zwei Spalten mit einer breiteren linken Spalte ein.|  
||**Zwei Spalten**|Fügt eine Registerkarte mit zwei Spalten mit gleicher Breite ein.|  
|**1 Registerkarte**|**Eine Spalte**|Fügt eine Registerkarte mit einer Spalte ein.|  
|**Steuerelement**|**Unterraster**|Formatiert ein Unterraster und fügen es in das Formular ein.<br /><br /> Weitere Informationen finden Sie unter [Unterrastereigenschaften](sub-grid-properties-legacy.md).|  
||**Spacer**|Fügt ein Leerzeichen ein.|  
||**Schnellansichtsformular**|Fügt ein Schnellansichtsformular ein.<br /><br /> Weitere Informationen finden Sie unter [Eigenschaften zum Steuerelement für die Schnellansicht](quick-view-control-properties-legacy.md).|  
||**Webressource**|Fügt eine Webressource ein, um Inhalte aus anderen Speicherorten in eine Seite einzubetten.<br /><br /> Weitere Informationen finden Sie unter [Webressourceneigenschaften](web-resource-properties-legacy.md).|  
||**IFRAME**|Fügt einem Formular ein IFRAME-Element hinzu, um Inhalte von einer anderen Website in ein Formular zu integrieren.| 
||**Zeitachse**|Fügt ein Zeitachsen-Steuerelement in das Formular ein. Dieses Steuerelement zeigt die Zeitachse von Aktivitäten im Zusammenhang mit der Entität in einem Formular an.|  
||**Navigationslink**|Fügt einen Link in eine Formularnavigation ein.|  
||**Zeitgeber**|Fügt einem Entitätsformular ein Zeitgebersteuerelement zum Nachverfolgen von Zeit anhand einer SLA hinzu. Weitere Informationen finden Sie unter [Hinzufügen eines Zeitgebersteuerelements](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customer-service/add-timer-control-case-form-track-time-against-sla).|
||**Suche in der Wissensdatenbank**|Fügt ein Suchsteuerelement hinzu, mit dem Benutzer Artikel der Wissensdatenbank durchsuchen können. Weitere Informationen finden Sie unter [Wissensdatenbank-Suchsteuerelement](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customer-service/add-knowledge-base-search-control-forms).|  
||**Beziehungsassistent**|Fügt ein Beziehungsassistenten-Steuerelement in das Formular ein.|

>[!Note] 
>Die folgenden Komponenten werden in Hauptformularen nicht unterstützt:<br> <ul> <li>Bing Karten <br><li>Yammer <br><li>Aktivitätsfeeds <br> </li> </ul>


## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)  
