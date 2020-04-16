---
title: Allgemeine Feldeigenschaften für modellgesteuerte Apps in Power Apps | Microsoft-Dokumentation
description: Verstehen der allgemeinen Feldeigenschaften für Hauptformulare
Keywords: Hauptformular; Allgemeine Feldeigenschaften; Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 02/25/2020
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 2b91ee28-7f09-435e-9fae-5225aa698e22
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8729292ca14cff762b31ef886ecdc0c90856110e
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136431"
---
# <a name="model-driven-app-common-field-properties"></a>Modell-angetriebene App mit allgemeinen Feldeigenschaften

Sie können allgemeine Eigenschaften von Entitätsfeldern für eine modellgesteuerte App mithilfe von Power Apps-Projektmappen-Explorer oder Power Apps-Portal anzeigen und bearbeiten. Das Power Apps-Portal stellt eine einfache Möglichkeit dar, Entitätsfelder mit dem Common Data Service zu erstellen und zu bearbeiten.
Das Portal aktiviert das Konfigurieren der gängigsten Optionen, aber bestimmte Optionen können nur mithilfe des Lösungs-Explorers festgelegt werden.

## <a name="common-field-properties-in-power-apps-portal"></a>Häufige Feldeigenschaften in Power Apps-Portal

1. Wählen Sie im [Power Apps Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) **Daten** > **Entitäten** und wählen Sie die Entität mit den Feldern, die Sie anzeigen möchten.

2. Wählen Sie das Feld aus, das Sie anzeigen möchten.

    > [!div class="mx-imgBorder"]
    > <img src="media/common-field-prop-powerapps.png" alt="Common field properties in Power Apps portal" height="658" width="300">


In der folgenden Tabelle werden die allgemeinen Eigenschaften von Feldern beschrieben. Bestimmte Feldtypen haben spezielle Eigenschaften. Diese werden in [Erstellen und Bearbeiten von Feldern für Common Data Service](../common-data-service/create-edit-field-portal.md) beschrieben.

 |Eigenschaft|Beschreibung|
 |--|--|
 |**Anzeigename**|Der Text für das Feld auf der Benutzeroberfläche, der angezeigt werden soll.|
 |**Name**|Der eindeutige Name Ihrer Umgebung. Ein Name wird für Sie basierend auf dem Anzeigenamen generiert, die Sie eingegeben haben, aber Sie können ihn ändern, bevor Sie ihn speichern. Sobald ein Feld erstellt wurde, kann der Name nicht geändert werden, da er unter Umständen auf die Anwendungen oder Code verweist. Der Name hat folgendes Anpassungspräfix für den **Common Data Service Standardherausgeber** verwendet.|
 |**Datentyp**|Steuert, wie Werte gespeichert werden sowie wie sie in einigen Anwendungen formatiert werden. Sobald ein Feld gespeichert ist, können Sie den Datentyp nicht ändern, abgesehen von der Konvertierung von Feldern mit automatischer Nummerierung.|
 |**Erforderlich**| Ein Datensatz kann ohne Daten in diesem Feld nicht gespeichert werden. |
 |**Durchsuchbar**| Dieses Feld erscheint in der erweiterten Suche und ist beim Anpassen von Ansichten verfügbar. |
 |**Berechnet oder Rollup**| Zur Automatisierung von manuellen Berechnungen. Verwenden Sie Werte, Daten oder Text.|
 |**Erweiterte Optionen**| Fügen Sie eine Beschreibung hinzu und geben Sie eine maximale Länge und den IME-Modus für das Feld an.

Es gibt zahlreiche unterschiedlichen Arten Felder, aber Sie können nur einige davon erstellen. Weitere Informationen für alle Feldtypen unter [Feldttypen und Datenfeldertypen](../common-data-service/types-of-fields.md) Sie können auch weitere Optionen abhängig von der Auswahl von **Datentyp** festlegen.

## <a name="common-field-properties-in-solution-explorer"></a>Allgemeine Feldeigenschaften in Projektmappen-Explorer
 
Felder in einem Formular zeigen Steuerelemente an, mit denen Benutzer Daten in einem Entitätsdatensatz anzeigen oder bearbeiten. Felder können bis zu vier Spalten in einem Abschnitt einnehmen.  

Sie können auf **Allgemeine Feldeigenschaften** im Projektmappen-Explorer zugreifen. Erweitern Sie unter **Komponenten** **Entitäten**, und dann die gewünschte Entität, und wählen Sie **Formulare** aus. Öffnen Sie in der Liste der Formulare das Formular des Typs **Haupt**. Doppelklicken Sie dann auf eines der Felder, um „Allgemeine Feldeigenschaften” anzuzeigen.

![Allgemeine Feldeigenschaften in Projektmappen-Explorer](media/common-field-properties.png "Allgemeine Feldeigenschaften in Projektmappen-Explorer")
  
Die folgende Tabelle beschreibt die Eigenschaften aller Felder. Bestimmte Feldtypen haben spezielle Eigenschaften. Diese werden in [Spezielle Feldeigenschaften](special-field-properties-legacy.md) beschrieben.  
  
|Tabstopp|Eigenschaft|Beschreibung|  
|---------|--------------|-----------------|  
|**Anzeige**|**Bezeichnung**|**Erforderlich**: Standardmäßig entspricht die Beschriftung dem Anzeigenamen des Felds. Sie können diesen Namen für das Formular überschreiben, indem Sie hier eine andere Beschriftung eingeben.|  
||**Beschriftung im Formular anzeigen**|Sie können auch angeben, dass die Beschriftung nicht angezeigt werden soll.|  
||**Verhalten des Felds**|Geben Sie das Feldebenenverhalten mithilfe der Kontrollkästchen an.|  
||**Sperrung**|Auf diese Weise wird verhindert, dass das Feld versehentlich aus dem Formular entfernt wird. Auf diese Weise wird verhindert, dass eine Konfiguration, die Sie für das Feld angewendet haben, wie etwa Ereignishandler, gelöscht wird, wenn das Feld entfernt werden sollte. Um dieses Feld zu entfernen, muss der Anpasser zuerst diese Einstellung löschen.|  
||**Sichtbarkeit**|Die Anzeige des Felds ist optional und kann durch Skripts gesteuert werden. Weitere Informationen: [Sichtbarkeitsoptionen](visibility-options-legacy.md)|  
||**Verfügbarkeit**|Wählen Sie, ob Sie möchten, dass die Registerkarte auf dem Smartphone verfügbar ist.|
|**Formatierung**|**Wählen Sie die Anzahl der Spalten, die vom Steuerelement belegt werden**|Wenn der Abschnitt, der die Felder enthält, mehr als eine Spalte enthält, können Sie festlegen, dass das Feld die Anzahl von Spalten belegt, die der Abschnitt enthält.|  
|**Details**|**Anzeigename**, **Name** und **Beschreibung**|Diese schreibgeschützten Felder dienen nur als Referenz. Klicken Sie auf die Schaltfläche **Bearbeiten** für problemlosen Zugriff auf die Felddefinition, wenn Sie sie bearbeiten möchten.<br /><br /> Jede Instanz eines Felds im Formular eine Namenseigenschaft, damit auf sie in Formularskripten verwiesen werden kann; dieser Name wird jedoch von der Anwendung verwaltet. Die erste Instanz des Felds ist der Name des Felds, der beim Erstellen angegeben wurde. Weitere Informationen: [Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-fields.md)<br /><br /> Für jeden weiteren Einschluss des Feldes in einem Formular wird dem Namen eine Nummer ab 1 hinzugefügt. Wenn der Feldname „new_cost“ ist, ist die erste Instanz „new_cost“, die zweite „new_cost1“ usw. für jede Instanz des Feldes im Formular.<br /><br />**Hinweis:** Der Wert des Feldes **Beschreibung** zeigt Tooltipps an, wenn der Cursor darauf gesetzt wird.|  
|**Ereignisse**|**Formularbibliotheken**|Geben Sie gegebenenfalls JavaScript-Webressourcen an, die im Ereignishandler des Felds `OnChange` verwendet werden sollen.<br /><br />|  
||**Ereignishandler**|Konfigurieren Sie die Funktionen aus den Formularbibliotheken, die für das Feld `OnChange`-Ereignis aufgerufen werden sollen. Weitere Informationen: [Konfigurieren Sie Ereignishandler](configure-event-handlers-legacy.md)|  
|**Geschäftsregeln**|**Geschäftsregeln**|Anzeigen und Verwalten von Unternehmensregeln die auf dieses Feld verweisen. Weitere Informationen [Erstellen von Geschäftsregeln und Empfehlungen](create-business-rules-recommendations-apply-logic-form.md)|  
|**Steuerelemente**|**Steuerelemente**|Steuerelemente hinzufügen und ihre Verfügbarkeit in Web, Smartphone und Tablet angeben|  

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)
