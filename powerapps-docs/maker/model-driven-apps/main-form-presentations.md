---
title: Darstellung von Hauptformularen modellgesteuerter Apps in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Hauptformulare auf verschiedenen Geräten dargestellt werden.
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: da3ac59a-5413-46cb-b355-1987e42e3853
caps.latest.revision: 35
ms.author: matp
manager: kvivek
ms.openlocfilehash: b8dee40f6dbeba62128434b3eb122add9cb0b373
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39682754"
---
# <a name="how-model-driven-app-main-forms-appear-on-different-devices"></a>Gewusst wie: Darstellung von Hauptformularen modellgesteuerter Apps auf verschiedenen Geräten

Das Hauptformular wird von allen Clients für modellgesteuerte Apps verwendet. Dieses Formular bietet Benutzern eine konsistente Umgebung, ganz gleich, ob ein Webbrowser, Dynamics 365 für Smartphones, Dynamics 365 für Tablets oder Dynamics 365 für Outlook verwendet wird.  
  
<a name="BKMK_MainFormPresentations"></a>   
## <a name="main-forms"></a>Hauptformulare  
 Die Darstellung von Hauptformularen, die für eine Entität vorhanden sind, kann je nach den Faktoren in der folgenden Tabelle variieren. Beim Entwurf eines Hauptformulars sollten Sie beachten, wie es in den verschiedenen Darstellungsformen aussieht.  
  
|Darstellung|Beschreibung|  
|------------------|-----------------|  
|**Aktualisiert**|Für [aktualisierte und klassische Entitäten](create-design-forms.md#updated-versus-classic-entities) sowie benutzerdefinierte Entitäten in Dynamics 365 (online) und Dynamics 365 (lokal) bietet das aktualisierte Formular eine neue Benutzeroberfläche. Diese Formulare weisen den neueren Entwurf für die Befehlsleiste auf und ermöglichen zusätzliche Features wie das automatische Speichern und Geschäftsprozessflüsse.|  
|**Dynamics 365 für Tablets**| Dynamics 365 für Tablets stellt den Inhalt des Hauptformulars auf eine für Tablets optimierte Weise dar.|  
|**Dynamics 365 für Smartphones**| Dynamics 365 für Smartphones stellt den Inhalt des Hauptformulars auf eine für Smartphones optimierte Weise dar.|  
|**Klassisch**|Diese Formulare sind für die Entitäten bestimmt, die nicht aktualisiert wurden. Diese weisen anstelle der Befehlsleiste und des Navigationsbereichs auf der linken Seite des Formulars das Menüband auf.<br /><br /> Diese Formulare weisen ein zweispaltiges Layout auf.|  
  
<a name="BKMK_MainFormComponentsForUpdatedEntities"></a>   
## <a name="updated-forms"></a>Aktualisierte Formulare  
 Die folgende Abbildung zeigt gemeinsame Komponenten, die in aktualisierten Entitätsformularen vorhanden sind.  
  
 ![Abbildung zur Struktur eines Formulars für aktualisierte Entitäten in Dynamics 365](media/updated-form-diagram.png "Abbildung zur Struktur eines Formulars für aktualisierte Entitäten in Dynamics 365")  
  
 Bei aktualisierten Entitäten ist das Layout des Formulars mit einer Vielzahl von Bildschirmen und Fenstergrößen kompatibel. Mit abnehmender Fensterbreite verschieben sich Registerkartenspalten nach unten, sodass Sie mit diesen arbeiten können und diese nicht komprimiert werden oder Sie nach rechts scrollen müssen.  
  
 In der folgenden Tabelle werden die verfügbaren Komponenten des Hauptformulars für aktualisierte Entitäten aufgeführt.  
  
|Komponente|Zusammenfassung|  
|---------------|-------------|  
|**Navigationsleiste**|Bietet anhand der Daten in der Siteübersicht die Möglichkeit, zu verschiedenen Bereichen der Anwendung zu navigieren.<br /><br /> Der in klassischen Formularen verwendete Navigationsbereich ist nicht im aktualisierten Formular enthalten. Im Kontext eines Datensatzes bietet die Navigationsleiste Zugriff auf Ansichten der verknüpften Datensätze. Statt über den Navigationsbereich oder die Navigationsleiste zu den verknüpften Datensätzen zu navigieren, verbessert das Hinzufügen von Unterrastern, die für die Anzeige von nützlichen verknüpften Entitätsdatensätzen konfiguriert sind, die Benutzererfahrung für die meisten Benutzer.|  
|**Befehlsleiste**|Stellt mit den für Menübänder definierten Daten Befehle bereit, die für den Datensatz relevant sind.<br /><br /> Die ersten fünf Befehle werden angezeigt, gefolgt von Auslassungszeichen (![Schaltfläche „Weitere Befehle“](media/not-available.gif "Schaltfläche „Weitere Befehle“")), die ein Menü-Flyout zur Auswahl zusätzlicher Befehle bereitstellt.|  
|**Bild**|Wenn eine Entität ein Bildfeld enthält und die Entitätsoption **Primäres Bild** auf **Standardbild** festgelegt ist, kann ein Bild in der Kopfzeile angezeigt werden, wenn das Formular für die Anzeige des Bilds konfiguriert ist.|  
|**Kopfzeile**|Die in der Kopfzeile eingefügten Felder bleiben sichtbar, wenn Benutzer im Text des Formulars nach unten scrollen.<br /><br /> In der Kopfzeile können bis zu vier Felder platziert werden. Mehrere Textzeilen, Webressourcen oder iFrames in der Kopfzeile sind unzulässig. Die Kopf- und Fußzeile weisen einige gemeinsame Eigenschaften mit Abschnitten auf.|  
|**Prozesssteuerung**|Wenn eine Entität aktive Geschäftsprozessabläufe aufweist, wird die Prozesssteuerung unterhalb der Kopfzeile angezeigt. Weitere Informationen finden Sie unter [Übersicht über Geschäftsprozessflüsse](/flow/business-process-flows-overview).|  
|**Text**|Der Text ist der scrollbare Bereich des Formulars, der die Registerkarten enthält.|  
|**Registerkarten**|Innerhalb des Formulartexts ermöglichen Registerkarten eine horizontale Trennung. Registerkarten sind mit einer Beschriftung versehen, die angezeigt werden kann. Wenn die Beschriftung angezeigt wird, können Registerkarten erweitert oder reduziert werden, um den jeweiligen Inhalt durch Auswahl der Beschriftung ein- oder auszublenden.<br /><br /> Registerkarten enthalten bis zu drei Spalten und die Breite jeder Spalte kann auf einen Prozentsatz der Gesamtbreite festgelegt werden. Wenn Sie eine neue Registerkarte erstellen, ist jede Spalte mit einem Abschnitt bereits aufgefüllt.|  
|**Abschnitte**|Ein Abschnitt füllt den in einer Registerkartenspalte verfügbaren Platz aus. Abschnitte sind mit einer Beschriftung, die angezeigt werden kann, und eventuell einer Linie unter der Beschriftung versehen.<br /><br /> Abschnitte können bis zu vier Spalten und Optionen dafür enthalten, wie Beschriftungen für Felder im Abschnitt angezeigt werden.|  
|**Felder**|Felder zeigen Steuerelemente an, mit denen Benutzer Daten in einem Entitätsdatensatz anzeigen oder bearbeiten können. Felder können so formatiert werden, dass bis zu vier Spalten in einem Abschnitt ausgefüllt sind.|  
|**Abstandhalter**|Ein Abstandhalter fügt einer Abschnittsspalte einen leeren Bereich hinzu.|  
|**Unterraster**|Unterraster ermöglichen die Anzeige einer Liste innerhalb des Formulars. Die Möglichkeit, Diagramme mithilfe eines Unterrasters anzuzeigen, steht nicht in Formularen für aktualisierte Entitäten zur Verfügung.|  
|**Schnellansichtsformular**|Ein Schnellansichtsformular zeigt Daten aus einem Datensatz an, auf das über ein Suchfeld im Formular verwiesen wird. Die Entität, die das Ziel der Suche ist, benötigt ein Schnellansichtsformular, bevor sie dem Formular hinzugefügt werden kann. Weitere Informationen finden Sie unter [Erstellen eines Schnellansichtsformulars für eine modellgesteuerte App für die Anzeige von Informationen zu einer verknüpften Entität](create-edit-quick-view-forms.md).|  
|**Webressourcen**|Hauptformularen können HTML- und Microsoft Silverlight-Webressourcen hinzugefügt werden, werden allerdings nicht bei Dynamics 365 für Smartphones und Tablets angezeigt.|  
|**iFrame**|Ein Inlineframe, das Sie konfigurieren können, um eine Webseite von einer anderen Website anzuzeigen. **Wichtig**:  <ul><li>Wenn die in einem iFrame angezeigte Seite in einer anderen Domäne enthalten ist, wenden Browser einen höheren Sicherheitsgrad an. Dies kann die Anforderungen für den Inhalt eines iFrame, um mit Daten im Formular zu interagieren, erschweren.</li><li>Die Anzeige eines Entitätsformulars in einem iFrame, das in einem anderen Entitätsformular eingebettet ist, wird nicht unterstützt. 
|**Bing Karten**|Wenn dieses Steuerelement in einem Formular für eine aktualisierte Entität vorhanden ist und die Systemeinstellung **Bing Karten aktivieren** mit einem gültigen Bing Karten-Schlüssel aktiviert ist, kann dieses Steuerelement einmalig in einem Formular verwendet werden, um den Standort für eine der Adressen in einer aktualisierten Entität anzuzeigen. Weitere Informationen finden Sie unter [Konfigurieren von Bing Karten in einer modellgesteuerten App](configure-bing-maps-legacy.md).|  
|**Fußzeile**|Der Fußzeile kann eine beliebige Anzahl von Feldern, Webressourcen oder iFrames hinzugefügt werden. Felder sind schreibgeschützt, wenn Sie in der Fußzeile angezeigt werden. Die Kopf- und Fußzeile weisen einige gemeinsame Eigenschaften mit Abschnitten auf.|  
|**Statusleiste**|Die Statusleiste zeigt das Statusfeld für den Datensatz, einen Infobereich und ein Schaltfläche zum Speichern an.|  
  
<a name="BKMK_CRMforTabletsPresentation"></a>   
## <a name="dynamics-365-for-phones-and-tablets-forms"></a>Formulare von Dynamics 365 für Smartphones und Tablets  
 Für Dynamics 365 für Smartphones und Tablets stehen die meisten Systementitäten und benutzerdefinierten Entitäten zur Verfügung. Das Hauptformular für diese Entitäten wird in eine für Smartphones oder Tablets optimierte Darstellung transformiert.  
  
<a name="BKMK_EntitiesEnabledForCRMForTablets"></a>   
### <a name="entities-enabled-for-dynamics-365-for-phones-and-tablets"></a>Für Dynamics 365 für Smartphones und Tablets aktivierte Steuerelemente  
 Nur bei Entitäten, die für Dynamics 365 für Smartphones und Tablets aktiviert sind, kommt diese Darstellung des Hauptformulars vor. Weitere Informationen finden Sie unter [Entitäten, die in Dynamics 365 für Smartphones und Tablets angezeigt werden](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_CustomEntity).  
  
### <a name="form-design"></a>Formularentwurf  
 Dynamics 365 für Smartphones und Tablets stellt zahlreiche Elemente des Hauptformulars in einer Weise dar, die für Smartphones oder Tablets optimiert ist. Die folgenden Abbildungen zeigen den geänderten Prozessfluss von der Web-App zu Tablet- und Smartphone-Apps.  
  
 **Web-App**  
  
 ![Geänderter Prozessfluss des Dynamics 365-Formulars von der Web-App](media/custon-reflow-web-app.png "Geänderter Prozessfluss des Dynamics 365-Formulars von der Web-App")  
  
 **Tablet-App**  
  
 ![Geänderter Prozessfluss des Dynamics 365-Formulars zur Tablet-App](media/reflow-tablet-app.png "Geänderter Prozessfluss des Dynamics 365-Formulars zur Tablet-App")  
  
 **Smartphone-App**  
  
 ![Geänderter Prozessfluss des Dynamics 365-Formulars zur Smartphone-App](media/custon-reflow-phone-app.png "Geänderter Prozessfluss des Dynamics 365-Formulars zur Smartphone-App")  
  
 Die Formularelemente werden in Dynamics 365 für Tablets in ein breites Panoramalayout transformiert, sodass Benutzer durch Wischbewegungen auf dem Bildschirm die in einem Viewport sichtbaren Elemente ändern können. In Dynamics 365 für Smartphones können Benutzer durch Wischbewegungen auf dem Bildschirm eine andere Spalte oder einen anderen Bereich von Elementen anzeigen. Die Prozesssteuerung wird oberhalb von jeder Spalte angezeigt.  
  
### <a name="view-port-element"></a>Viewportelement  
 Die folgenden Elemente sind immer innerhalb des Viewports im Kontext eines Formulars sichtbar:  
  
 **Navigationsleiste**  
 Die Navigationsleiste ist eine Darstellung der Sitemap, die für Touchgeräte optimiert ist. Weitere Informationen finden Sie unter [Ändern von Navigationsoptionen für Dynamics 365 für Smartphones und Tablets](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_NavigationOptions).  
  
 **Start**  
 Die Schaltfläche „Start“ leitet Benutzer zum Dashboard weiter, das die Startseite für Dynamics 365 für Smartphones und Tablets darstellt.  
  
 **Prozesssteuerung**  
 Wenn für die Entität ein Geschäftsprozess aktiviert ist, wird er in Dynamics 365 für Tablets in der oberen rechten Ecke neben dem Steuerelement für die Suche und in Dynamics 365 für Smartphones am oberen Rand des Bildschirms angezeigt.  
  
 **Suche**  
 Benutzer können auf das Steuerelement tippen, um die Ansicht für die Suche nach Datensätzen zu öffnen.  
  
 **Befehlsleiste**  
 Standardmäßig werden einige der Befehle, die in der im Webbrowser ausgeführten App angezeigt werden, nicht in den Apps Dynamics 365 für Smartphones und Tablets angezeigt. Ähnlich wie die Webanwendung ist die Befehlsleiste kontextbezogen, weshalb die verfügbaren Befehle je nach der momentanen Ansicht oder Auswahl variieren. Weitere Informationen finden Sie unter [Ändern von Befehlen für Dynamics 365 für Smartphones und Tablets](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_ChangeCommands).  
  
### <a name="form-elements"></a>Formularelemente  
 Die angezeigten Formularelemente stammen aus dem Hauptformular und werden als eine Reihe von Bereichen dargestellt, die Benutzer über den Viewport anzeigen können.  
  
 In Dynamics 365 für Tablets zeigt der erste Bereich Kontaktinformationen über Beziehungen an, die für den Datensatz vorhanden sind. In Dynamics 365 für Smartphones zeigt der erste Bereich auch Kopfzeilenfelder aus dem Formular über den Beziehungskacheln an.  
  
 ![Bereich „Beziehungen“ in Dynamics 365 für Tablets](media/mobile-app-form-relationships.png "Bereich „Beziehungen“ in Dynamics 365 für Tablets")  
  
 In den Formularen „Kontakt“ und „Benutzer“ zeigt das oberste Element eine Kommunikationskarte für den Datensatz an. Die Kommunikationskarte enthält Schaltflächen, um die Kommunikation mit der Person zu initiieren. Bei anderen Entitäten wird eine Kommunikationskarte angezeigt, wenn ein Schnellansichtsformular im Hauptformular eingebettet ist.  
  
 Sie können zusätzliche Kacheln basierend auf Entitätsbeziehungen anzeigen, jedoch nicht die Kacheln für die folgenden Entitäten anpassen:  
  
|Einrichtung|Kacheln|  
|------------|-----------|  
|Konto|Owner|  
|Kontakt|Name des Unternehmens, Besitzer|  
|Lead|Owner|  
|Opportunity|Firma, Besitzer|  
  
 Sie können die verbleibenden Kacheln mit dem Formular-Editor anpassen. Die Reihenfolge ist festgelegt, aber Sie können festlegen, welche Elemente im Bereich „Beziehungen“ sichtbar sind.  
  
 In Dynamics 365 für Tablets beginnt der zweite Bereich mit dem Namen der ersten Registerkarte im Formular. Alle in der Kopfzeile enthaltenen Felder und der Inhalt der ersten Registerkarte sind enthalten. In Dynamics 365 für Smartphones werden Kopfzeilen in der ersten Spalte angezeigt.  
  
 ![Erster Bereich des Formulars von CRM für Tablets](media/mobile-app-form-first-panel.png "Erster Bereich des Formulars von CRM für Tablets")  
  
 Falls ein Prozessfluss für das Formular aktiviert ist, zeigt die dritte Registerkarte Aufgaben für die aktuelle Phase des Prozesses in Dynamics 365 für Tablets an. In Dynamics 365 für Smartphones schwebt die Prozesssteuerung über den Bereichen, wird bei Auswahl über dem aktuellen Bereich des Benutzers erweitert und ist immer sichtbar und ausführbar.  
  
 Die verbleibenden Bereiche des Formulars enthalten den Inhalt der Registerkarten im Formular. Vorhandene Unterraster werden als separater Bereich angezeigt.  
  
 Das Formular von Dynamics 365 für Smartphones und Tablets zeigt immer die Beschriftungen für Registerkarten und Unterraster an. Die Einstellung **Beschriftung im Formular anzeigen** wird nicht angewendet.  
  
> [!NOTE]
>  Um die Leistung auf Mobilgeräten zu optimieren, ist die Anzahl der Objekte auf 5 Registerkarten oder 75 Felder und 10 Unterraster beschränkt.  
  
 Formulare für Dynamics 365 für Smartphones und Tablets unterstützen Folgendes nicht:  
   
-   Bing Karten  
  
-   Yammer
  
-   Aktivitätsfeeds  
  
-   Design  
  
 Darüber hinaus sind Entitätsbilder in Listenansichten und Kontaktkarten sichtbar, jedoch nicht innerhalb des eigentlichen Formulars.  
  
<a name="BKMK_MultipleForms"></a>   
### <a name="multiple-forms"></a>Mehrere Formulare  
 Dynamics 365 für Smartphones und Tablets unterstützt mehrere Formulare, bietet jedoch keine Möglichkeit für Benutzer, zwischen Formularen zu wechseln, wenn sie auf mehrere zugreifen können. Benutzer sehen das erste Formular in der Formularreihenfolge, in der sie Zugriff auf diese haben.  
  
 Wenn Sie z.B. über die folgenden Hauptformulare für die Verkaufschancenentität verfügen und die folgenden Sicherheitsrollen für diese zugewiesen haben, sehen Sie die in der folgenden Tabelle angezeigte Formularreihenfolge.  
  
|Formularreihenfolge|Formularname|Sicherheitsrollen|  
|----------------|---------------|--------------------|  
|1|**Verkaufsformular 1**|Vertriebsmitarbeiter|  
|2|**Verkaufsformular 2**|Vertriebsmitarbeiter und Vertriebsprozess-Manager|  
|3|**Verkaufsformular 3**|Vertriebsprozess-Manager|  
|4|**Verkaufsformular 4**|Vertriebsleiter|  
  
-   Benutzern mit der Rolle „Vertriebsmitarbeiter“ wird immer das **Verkaufsformular 1** angezeigt.  
  
-   Benutzern mit der Rolle „Vertriebsprozess-Manager“ wird immer das **Verkaufsformular 2** angezeigt.  
  
-   Benutzern mit der Rolle „Vertriebsleiter“ wird immer das **Verkaufsformular 4** angezeigt.  
  
<a name="BKMK_ClassicPresentation"></a>   
## <a name="classic-forms"></a>Klassische Formulare  
 Die folgende Abbildung zeigt die Komponenten des Hauptformulars, die in der klassischen Darstellung verwendet werden.  
  
 ![Elemente des Hauptformulars](media/elements.png "Elemente des Hauptformulars")  
  
 Die Formulare für aktualisierte Entitäten haben viele Komponenten aus den klassischen Formularen geerbt, es gibt jedoch wesentliche Unterschiede.  
  
 Formulare mit der klassischen Darstellung enthalten keine Navigationsleiste und weisen anstelle der Befehlsleiste ein Menüband auf. Diese Formulare bieten keine Unterstützung für Entitätsbilder, die Prozesssteuerung, Schnellansichtsformulare, automatisches Speichern oder Bing Karten. Felder in der Kopfzeile können nicht bearbeitet werden.  
  
 Der Formular-Assistent wird für bestimmte Entitäten wie `Article` verfügbar gemacht.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen und Entwerfen von Formularen](create-design-forms.md)   

 
