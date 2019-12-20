---
title: Hauptformulardarstellung in modellgesteuerten Apps in Power Apps | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Hauptformulare aussehen, wenn sie auf verschiedenen Geräten angezeigt werden
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: da3ac59a-5413-46cb-b355-1987e42e3853
caps.latest.revision: 35
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 03eca0ade83c4d241eca9e4f7a6004232aac2b87
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860101"
---
# <a name="how-model-driven-app-main-forms-appear-on-different-devices"></a>Wie Hauptformulare in modelgesteuerten Apps auf verschiedenen Geräten erscheinen

Das Hauptformular wird von allen modellgesteuerten App-Clients verwendet. Dieses Formular bietet eine konsistente Benutzererfahrung, unabhängig davon, ob jemand einen Webbrowser, Dynamics 365 für Smartphones, Dynamics 365 für Tablets oder Dynamics 365 for Outlook verwendet.  
  
<a name="BKMK_MainFormPresentations"></a>   
## <a name="main-forms"></a>Hauptformulare  
 Alle Hauptformulare, die für eine Entität vorhanden sind, können je nach den Faktoren in der folgenden Tabelle unterschiedlich angezeigt werden. Wenn Sie ein Hauptformular entwerfen, sollten Sie überlegen, wie es in den unterschiedlichen Präsentationen funktioniert.  
  
|Präsentation|Beschreibung|  
|------------------|-----------------|  
|**Aktualisiert**|Für [Aktualisierte Entitäten und klassische Entitäten](create-design-forms.md#updated-versus-classic-entities) und alle benutzerdefinierten Entitäten in Dynamics 365 (online) und Dynamics 365 On-premises bietet das aktualisierte Formular eine neue Benutzererfahrung. Diese Formulare haben das neuere Befehlsleistendesign und erlauben zusätzliche Funktionalität wie automatisches Speichern und Geschäftsprozessflüsse.|  
|**Dynamics 365 for Tablets**| Dynamics 365 for tablets stellt den Inhalt des Hauptformulars in einer für Tablets optimierten Form dar.|  
|**Dynamics 365 for Phones**| Dynamics 365 for phones stellt den Inhalt des Hauptformulars in einer für Smartphones optimierten Form dar.|  
|**Klassisch**|Diese Formulare sind für noch nicht aktualisierte Entitäten bestimmt. Sie verwenden das Menüband und nicht die Befehlsleiste und den Navigationsbereich auf der linken Seite des Formulars.<br /><br /> Diese Formulare haben ein zweispaltiges Layout.|  
  
<a name="BKMK_MainFormComponentsForUpdatedEntities"></a>   
## <a name="updated-forms"></a>Aktualisierte Formulare  
 Dieses Diagramm zeigt die allgemeinen Komponenten an, die in aktualisierten Entitätsformularen vorhanden sind.  
  
 ![Diagramm zeigt aktualisierte Entitätsformularstruktur in Dynamics 365](media/updated-form-diagram.png "Diagramm zeigt aktualisierte Entitätsformularstruktur in Dynamics 365")  
  
 Bei aktualisierten Entitäten funktioniert das Layout der Formulare mit einer breiten Palette von Anzeigen und Fenstergrößen. Die Breite von Fensterabnahmen nimmt ab, Registerkartenspalten bewegen sich nach unten, sodass dass Sie einen Bildlauf nach unten durchführen können, und mit ihnen zu arbeiten, anstatt komprimiert zu werden, oder einen Bildlauf nach rechts zu erfordern.  
  
 In der folgenden Tabelle werden die verfügbaren Komponenten des Hauptformulars für aktualisierte Entitäten zusammengefasst.  
  
|Komponente|Zusammenfassung|  
|---------------|-------------|  
|**Navigationsleiste**|Verwendet die Daten in der SiteMap, um die Fähigkeit bereitzustellen, sich zu verschiedenen Bereichen der Anwendung zu bewegen.<br /><br /> Der Navigationsbereich, der in klassischen Formularen verwendet wurde, ist im aktualisierten Formular nicht enthalten. Im Rahmen eines Datensatzes bietet die Navigationsleiste Zugriff auf Ansichten der verknüpften Datensätze. Anstatt zu den verknüpften Datensätzen mithilfe des Navigationsbereichs oder der Navigationsleiste zu navigieren, bietet das Hinzufügen von Unterrastern, die so konfiguriert werden, dass sie nützliche verknüpfte Entitätsdatensätze anzeigen, eine bessere Umgebung für die meisten Benutzer.|  
|**Befehlsleiste**|Verwendet die Daten, auf für Menübänder definiert wurden, um relevante Befehle für den Datensatz zur Verfügung zu stellen.<br /><br /> Die ersten fünf Befehle werden gefolgt von Auslassungspunkten (![Schaltfläche „Weitere Befehle“](media/not-available.gif "MSchaltfläche "Weitere Befehle")) angezeigt, die ein Flyoutmenü bereitstellen, um zusätzliche Befehle auszuwählen.|  
|**Bild**|Wenn eine Entität eine Bildfeld hat und die Option **Primäres Bild** der Entität auf **Standardbild** festgelegt wurde, kann ein Bild in der Kopfzeile angezeigt werden, wenn das Formular so konfiguriert ist, um das Bild anzuzeigen.|  
|**Kopfzeile**|Felder, die in die Kopfzeile platziert sind, bleiben sichtbar, wenn Mitarbeiter nach unten durch den Text des Formulars scrollen.<br /><br /> Bis zu vier Felder können in die Kopfzeilen platziert werden. Mehrere Textzeilen,Webressourcen oder iFrames sind in der Kopfzeile nicht zulässig. Kopf- und Fußzeilen haben einige Eigenschaften mit Abschnitten gemein.|  
|**Prozesssteuerung**|Wenn eine Entität über aktive Geschäftsprozessflüsse verfügt, wird die Prozesssteuerung unter der Kopfzeile angezeigt. Weitere Informationen: [Geschäftsprozessflüsse](/flow/business-process-flows-overview)|  
|**Textkörper**|Der Text ist der bildlauffähige Teil des Formulars, der die Registerkarten enthält.|  
|**Registerkarten**|Im Textkörper der Formularregisterkarten steht eine horizontale Trennung zur Verfügung. Registerkarten haben eine Beschriftung, die angezeigt werden kann. Wenn die Beschriftung angezeigt wird, können Registerkarten erweitert oder reduziert werden, um ihre Inhalte ein- oder auszublenden, indem Sie die Beschriftung auswählen.<br /><br /> Registerkarten enthalten bis zu drei Spalten, und die Breite der Spalten kann auf einen Prozentsatz der Gesamtbreite festgelegt werden. Wenn Sie eine neue Registerkarte erstellen, wird die Spalte mit Abschnitt vorab ausgefüllt.|  
|**Abschnitte**|Ein Abschnitt nimmt den in einer Registerkartenspalte verfügbaren Raum ein. Abschnitte enthalten eine Beschriftung, die angezeigt werden kann, sowie eine Zeile, die unter der Beschriftung angezeigt werden kann.<br /><br /> Abschnitte können bis zu vier Spalten enthalten und enthalten Optionen für die Anzeigen von Bezeichnungen für Felder im Abschnitt.|  
|**Felder**|Felder zeigen Steuerelemente an, mit denen Benutzer Daten in einem Entitätsdatensatz anzeigen oder bearbeiten. Felder können bis zu vier Spalten in einem Abschnitt einnehmen.|  
|**Abstandhalter**|Ein Abstandhalter ermöglicht die Hinzufügung eines Leerzeichens zu einer Abschnittsspalte.|  
|**Unterraster**|Unterraster erlauben die Anzeige einer Liste innerhalb des Formulars. Die Fähigkeit, Diagramme mithilfe eines Unterrasters anzuzeigen ist in Formularen für aktualisierte Entitäten nicht verfügbar.|  
|**Schnellansichtsformular**|Eine Schnellansicht zeigt Daten aus einem Datensatz an, auf den von einem Suchfeld im Formular verwiesen wird. Die Entität, die das Ziel der Suche ist, muss ein Schnellansichtsformular haben, bevor dem Formular eines hinzugefügt werden kann. Weitere Informationen: [Erstellen und Bearbeiten von Schnellansichtsformularen](create-edit-quick-view-forms.md)|  
|**Webressourcen**|HTML- und Microsoft Silverlight-Webressourcen können zu den Hauptformularen hinzugefügt werden, aber sie werden nicht angezeigt, wenn Sie Dynamics 365 for phones and tablets verwenden.|  
|**iFrame**|Ein InlineFrame, der konfiguriert wird, um eine Webseite eine andere Website aus anzuzeigen. **Wichtig:**  <ul><li>Wenn die Seite, die in einem iFrame angezeigt wird, sich auf einer anderen Domäne befindet, wenden Browser einen höheren Grad der Sicherheit an. Dies kompliziert möglicherweise die Anforderungen für die Inhalte eines iFrames, um mit Daten im Formular zu interagieren.</li><li>Beim Anzeigen eines Entitätsformulars mit einem iFrame, der eingebettet in einem anderen Entitätsformular ist, wird nicht unterstützt. 
|**Bing Maps**|Wenn dieses Steuerelement in einem Formular für eine aktualisierte Entität vorhanden ist und die Systemeinstellung **Bing Maps aktivieren** mit einem gültigen Bing Maps-Schlüssel aktiviert ist, kann dieses Steuerelement verwendet werden, um den Speicherort für eine der Adressen in der aktualisierten Entität anzuzeigen. Weitere Informationen: [Bing Maps konfigurieren](configure-bing-maps-legacy.md)|  
|**Fußzeile**|Eine beliebige Anzahl von Feldern, Webressourcen oder iFrames kann der Fußzeile hinzugefügt werden. Felder sind schreibgeschützt, wenn sie in der Fußzeile angezeigt werden. Kopf- und Fußzeilen haben einige Eigenschaften mit Abschnitten gemein.|  
|**Statusleiste**|Die Statusleiste zeigt das Feld Status für den Datensatztyp, einen Infobereich und eine Speicherung an.|  
  
<a name="BKMK_CRMforTabletsPresentation"></a>   
## <a name="dynamics-365-for-phones-and-tablets-forms"></a>Dynamics 365 für Smartphones- und Tabletsformulare  
 Die meisten Systementitäten und benutzerdefinierten Entitäten sind für Dynamics 365 for phones and tablets verfügbar. Das Hauptformular für diese Entitäten wird in eine Präsentation umgewandelt, die für Smartphones oder Tablets optimiert ist.  
  
<a name="BKMK_EntitiesEnabledForCRMForTablets"></a>   
### <a name="entities-enabled-for-dynamics-365-for-phones-and-tablets"></a>Für Dynamics 365 für Smartphones und Tablets aktivierte Entitäten  
 Nur Entitäten, die für Dynamics 365 for phones and tablets aktiviert sind, verwenden diese Darstellung des Hauptformulars. Weitere Informationen: [Entitäten, die in Dynamics 365 for phones and tablets angezeigt werden](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_CustomEntity).  
  
### <a name="form-design"></a>Formulardesign  
 Dynamics 365 for phones and tablets nimmt viele der Hauptformularelemente und präsentiert sie in einer für Smartphones und Tablets optimierten Weise. Die folgenden Diagramme zeigen den Umbruch von der Web-App zu den Tablet- und Smartphone-Apps.  
  
 **Web-App**  
  
 ![Dynamics 365-Formularumbruch zur Web-App](media/custon-reflow-web-app.png "Dynamics 365-Formularumbruch zur Web-App")  
  
 **Tablet-App**  
  
 ![Dynamics 365-Formularumbruch zur Tablet-App](media/reflow-tablet-app.png "Dynamics 365-Formularumbruch zur Tablet-App")  
  
 **Smartphone-App**  
  
 ![Dynamics 365 Formularumbruch zur Telefon-App](media/custon-reflow-phone-app.png "Dynamics 365 Formularumbruch zur Telefon-App")  
  
 Die Formularelemente sind in Dynamics 365 for tablets in ein Panoramalayout transformiert, auf dem Benutzer den Bildschirm wischen können, um die Artikel zu ändern, die in einem Viewport sichtbar sind. In Dynamics 365 for phones wischen die Benutzer über den Bildschirm, um eine andere Spalte oder Bereich von Elementen anzuzeigen, und das Prozesssteuerelement wird über jeder Spalte angezeigt.  
  
### <a name="view-port-element"></a>Viewportelement  
 Folgende Elemente werden immer im Viewports im Kontext eines Formulars angezeigt:  
  
 **Navigationsleiste**  
 Die Navigationsleiste ist eine Darstellung der Sitemap, die für Touch optimiert wurde. Weitere Informationen: [Navigationsoptionen ändern](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_NavigationOptions)  
  
 **Startseite**  
 Über die Startschaltfläche gelangen Benutzer zum Dashboard, der Startseite von Dynamics 365 for phones and tablets.  
  
 **Prozesssteuerung**  
 Wenn die Entität einen Geschäftsprozess aktiviert hat, wird er oben rechts neben dem Suchfeld in Dynamics 365 for tablets und oben auf dem Bildschirm in Dynamics 365 for phones angezeigt.  
  
 **Suchen**  
 Benutzer können auf das Suchsteuerelement tippen, um den Bildschirm für die Datensatzsuche zu öffnen.  
  
 **Befehlsleiste**  
 Standardmäßig werden einige der Befehle, die in der in einem Webbrowser ausgeführten App angezeigt werden, nicht in der Dynamics 365 for phones and tablets-App angezeigt. Ähnlich wie bei der Webanwendung ist die Befehlsleiste kontextsensitiv, und die verfügbaren Befehle unterscheiden sich je nach der aktuellen Anzeige oder Auswahl. Weitere Informationen: [Befehle ändern](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_ChangeCommands)  
  
### <a name="form-elements"></a>Formularelemente  
 Die angezeigten Formularelementen gehören zum Hauptformular und werden als Serie von Bereichen angezeigt, die Benutzer über den Viewport anzeigen.  
  
 In Dynamics 365 for tablets zeigt der erste Bereich Kontaktinformationen zu Beziehungen an, die für den Datensatz vorhanden sind. In Dynamics 365 for phones zeigt der erste Bereich auch Kopfzeilenfelder vom Formular über den Beziehungskacheln an.  
  
 ![Bereich „Dynamics 365 für Tablets-Beziehungen“](media/mobile-app-form-relationships.png "Bereich „Dynamics 365 für Tablets-Beziehungen“")  
  
 Für Kontakt- und Benutzerformulare zeigt das oberste Element eine Kommunikationskarte für den Datensatz an. Die Kommunikationskarte bietet Schaltflächen, um die Kommunikation mit der Person einzuleiten. Für andere Entitäten wird eine Kommunikationskarte angezeigt, wenn ein Kontakt-Schnellansichtsformular in das Hauptformular eingebettet ist.  
  
 Sie können zusätzliche Kacheln anhand der Entitätsbeziehungen anzeigen, aber die Kacheln für folgende Entitäten nicht anpassen:  
  
|Entität|Kacheln|  
|------------|-----------|  
|Firmen|Bes.|  
|Kontakt|Unternehmensname, Besitzer|  
|Lead|Bes.|  
|Verkaufschance|Konto, Besitzer|  
  
 Sie können die verbleibenden Kacheln mit dem Formular-Editor anpassen. Die Reihenfolge ist festgelegt, aber Sie können festlegen, welche Elemente im Beziehungsbereich sichtbar sind.  
  
 In Dynamics 365 for tablets beginnt der zweite Bereich mit dem Namen der ersten Registerkarte im Formular. Alle Felder, die in die Kopfzeile einbezogen sind, werden in die Inhalte der ersten Registerkarte einbezogen. In Dynamics 365 for phones erscheinen Kopfzeilen in der ersten Spalte.  
  
 ![CRM für Tablets-Formular erster Bereich](media/mobile-app-form-first-panel.png "CRM für Tablets-Formular erster Bereich")  
  
 Liegt ein aktiver Prozessfluss für das Formular vor, zeigt die dritte Registerkarte Aufgaben für den aktuellen Status für den Prozess in Dynamics 365 for tablets an. In Dynamics 365 for phones gleitet das Prozesssteuerelement über den Bereichen, wird über dem aktuellen Bereich des Benutzers erweitert (wenn ausgewählt) und ist immer sichtbar und handlungsrelevant.  
  
 Die übrigen Bereiche des Formulars enthalten die Inhalte der Registerkarten im Formular. Alle gefundenen Unterraster werden als separater Bereich angezeigt.  
  
 Das Dynamics 365 for phones and tablets-Formular zeigt immer die Bezeichnungen für Registerkarten und Unterraster an. Die Einstellung **Beschriftung im Formular anzeigen** wird nicht angewendet.  
  
> [!NOTE]
>  Um auf mobilen Geräten die Leistung zu optimieren, wird die Anzahl von Objekten auf 5 Registerkarten bzw. 75 Felder und 10 Unterraster beschränkt.  
  
 Formulare für Dynamics 365 for phones and tablets unterstützen Folgendes nicht:  
   
-   Bing Maps  
  
-   Yammer
  
-   Aktivitätsfeeds  
  
-   Designverwendung  
  
 Entitätsbilder werden zudem in Listenansichten und Kontaktkarten angezeigt, jedoch nicht im eigentlichen Formular.  
  
<a name="BKMK_MultipleForms"></a>   
### <a name="multiple-forms"></a>Mehrere Formulare  
 Dynamics 365 for phones and tablets unterstützt mehrere Formulare, stellt jedoch keine Methode zur Verfügung, nach der Benutzer zwischen Formularen wechseln können, wenn sie auf mehr als eines zugreifen können. Benutzer sehen das erste Formular in dem Formularauftrag, auf das sie Zugriff besitzen.  
  
 Wenn Sie zum Beispiel die folgenden Hauptformulare für die Verkaufschancenentität haben und die folgenden Sicherheitsrollen für jedes zugewiesen haben, sehen Sie den Formularauftrag, der in der folgenden Tabelle gezeigt wird.  
  
|Formularreihenfolge|Formularname|Sicherheitsrollen|  
|----------------|---------------|--------------------|  
|1|**Vertriebsformular eins**|Vertriebsmitarbeiter|  
|2|**Vertriebsformular zwei**|Vertriebsmitarbeiter und Vertriebsmanager|  
|3|**Vertriebsformular drei**|Vertriebsmanager|  
|4|**Vertriebsformular vier**|Vertriebsleiter|  
  
-   Benutzer mit der Rolle "Vertriebsmitarbeiter" sehen immer **Vertriebsformular eins**.  
  
-   Benutzer mit der Rolle "Vertriebsmanager" sehen immer **Vertriebsformular zwei**.  
  
-   Benutzer mit der Rolle "Vertriebsleiter" sehen immer **Vertriebsformular vier**.  
  
<a name="BKMK_ClassicPresentation"></a>   
## <a name="classic-forms"></a>Klassische Formulare  
 Das folgende Diagramm zeigt die Komponenten des Hauptformular an, die in der klassischen Präsentation verwendet werden.  
  
 ![Hauptformularelement](media/elements.png "Hauptformularelement")  
  
 Die Formulare für aktualisierte Entitäten haben viele Komponenten der klassischen Formulare geerbt, es gibt aber Unterschiede.  
  
 Formulare , die die klassische Präsentation verwenden, enthalten nicht die Navigationsleiste, und das Menüband wird anstelle der Befehlsleiste verwendet. Diese Formulare unterstützen keine Entitätsbilder, Prozesssteuerung, Schnellansichtsformulare, automatische Speicherung oder Bing Maps. Felder in der Kopfzeile können nicht bearbeitet werden.  
  
 Der Formularassistent wird für bestimmte Entitäten, z. B. `Article` verfügbar gemacht.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Formulare erstellen und gestalten](create-design-forms.md)   

 
