---
title: Allgemeine Feldeigenschaften für modellgesteuerte Apps in PowerApps | Microsoft-Dokumentation
description: Verstehen der allgemeinen Feldeigenschaften für Hauptformulare
Keywords: Hauptformular; Allgemeine Feldeigenschaften; Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
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
ms.openlocfilehash: e30d84206e92162327f1faf0035450ede9c05a8a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2701309"
---
# <a name="model-driven-app-common-field-properties"></a>Modell-angetriebene App mit allgemeinen Feldeigenschaften

 Felder in einem Formular zeigen Steuerelemente an, mit denen Benutzer Daten in einem Entitätsdatensatz anzeigen oder bearbeiten. Felder können bis zu vier Spalten in einem Abschnitt einnehmen.  

Sie können auf **Allgemeine Feldeigenschaften** im Projektmappen-Explorer zugreifen. Erweitern Sie unter **Komponenten** **Entitäten**, und dann die gewünschte Entität, und wählen Sie **Formulare** aus. Öffnen Sie in der Liste der Formulare das Formular des Typs **Haupt**. Doppelklicken Sie dann auf eines der Felder, um „Allgemeine Feldeigenschaften” anzuzeigen.

![Allgemeine Feldeigenschaften](media/common-field-properties.png)
  
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
|**Details**|**Anzeigename**, **Name** und **Beschreibung**|Diese schreibgeschützten Felder dienen nur als Referenz. Klicken Sie auf die Schaltfläche **Bearbeiten** für problemlosen Zugriff auf die Felddefinition, wenn Sie sie bearbeiten möchten.<br /><br /> Jede Instanz eines Felds im Formular eine Namenseigenschaft, damit auf sie in Formularskripten verwiesen werden kann; dieser Name wird jedoch von der Anwendung verwaltet. Die erste Instanz des Felds ist der Name des Felds, der beim Erstellen angegeben wurde. Weitere Informationen: [Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-fields.md)<br /><br /> Für jeden weiteren Einschluss des Feldes in einem Formular wird dem Namen eine Nummer ab 1 hinzugefügt. Wenn der Feldname "Neue Kosten" ist, ist die erste Instanz "Neue_Kosten", dann folgt "Neue_Kosten1" usw. für jede Instanz des Feldes auf dem Formular.<br /><br />**Hinweis:** Der Wert des Feldes **Beschreibung** zeigt Tooltipps an, wenn der Cursor darauf gesetzt wird.|  
|**Ereignisse**|**Formularbibliotheken**|Geben Sie gegebenenfalls JavaScript-Webressourcen an, die im Ereignishandler des Felds `OnChange` verwendet werden sollen.<br /><br />|  
||**Ereignishandler**|Konfigurieren Sie die Funktionen aus den Formularbibliotheken, die für das Feld `OnChange`-Ereignis aufgerufen werden sollen. Weitere Informationen: [Konfigurieren Sie Ereignishandler](configure-event-handlers-legacy.md)|  
|**Geschäftsregeln**|**Geschäftsregeln**|Anzeigen und Verwalten von Unternehmensregeln die auf dieses Feld verweisen. Weitere Informationen [Erstellen von Geschäftsregeln und Empfehlungen](create-business-rules-recommendations-apply-logic-form.md)|  
|**Steuerelemente**|**Steuerelemente**|Steuerelemente hinzufügen und ihre Verfügbarkeit in Web, Smartphone und Tablet angeben|  

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)
