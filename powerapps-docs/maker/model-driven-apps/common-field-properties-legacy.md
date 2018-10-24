---
title: Allgemeine Feldeigenschaften in modellgesteuerter App in PowerApps | Microsoft-Dokumentation
description: Informationen über die allgemeine Feldeigenschaften für das Hauptformular in Dynamics 365 für Customer Engagement
Keywords: Main form; Common field properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 2b91ee28-7f09-435e-9fae-5225aa698e22
ms.openlocfilehash: 74e67dd4299d06a54d5ec85765e4e5d03710b432
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683113"
---
# <a name="model-driven-app-common-field-properties"></a>Allgemeine Feldeigenschaften in modellgesteuerter App

 Felder in einem Formular zeigen Steuerelemente an, mit denen Benutzer Daten in einem Entitätsdatensatz anzeigen oder bearbeiten können. Felder können so formatiert werden, dass bis zu vier Spalten in einem Abschnitt ausgefüllt sind.  

Sie können im Projektmappen-Explorer auf die **Allgemeine Feldeigenschaften** zugreifen. Erweitern Sie unter **Komponenten** die Option **Einheiten**, erweitern Sie die gewünschte Entität, und wählen Sie dann **Formulare**. Öffnen Sie in der Liste der Formulare den Formulartyp **Haupt**. Doppelklicken Sie dann auf eines der Felder, um „Allgemeine Feldeigenschaften” anzuzeigen.

![common-field-properties](media/common-field-properties.png)
  
Die folgende Tabelle beschreibt die Eigenschaften aller Felder. Bestimmte Feldtypen haben spezielle Eigenschaften. Diese werden in [Spezielle Feldeigenschaften](special-field-properties-legacy.md) beschrieben.  
  
|Registerkarte|Eigenschaft|Beschreibung|  
|---------|--------------|-----------------|  
|**Anzeige**|**Bezeichnung**|**Erforderlich**: Standardmäßig entspricht die Beschriftung dem Anzeigenamen des Felds. Sie können diesen Namen für das Formular überschreiben, indem Sie hier eine andere Bezeichnung eingeben.|  
||**Bezeichnung im Formular anzeigen**|Sie können auswählen, dass die Bezeichnung nicht angezeigt wird.|  
||**Feldverhalten**|Geben Sie das Feldebenenverhalten mithilfe der Kontrollkästchen an.|  
||**Sperrung**|Diese Eigenschaft verhindert, dass das Feld versehentlich aus dem Formular entfernt werden. Auf diese Weise wird verhindert, dass eine Konfiguration, die Sie für das Feld angewendet haben, wie etwa Ereignishandler, gelöscht wird, wenn das Feld entfernt werden sollte. Um dieses Feld zu entfernen, muss der Anpasser zuerst diese Einstellung löschen.|  
||**Sichtbarkeit**|Die Anzeige des Felds ist optional und kann mithilfe von Skripts gesteuert werden. Weitere Informationen: [Sichtbarkeitsoptionen](visibility-options-legacy.md)|  
||**Verfügbarkeit**|Wählen Sie, ob die Registerkarte auf dem Smartphone verfügbar sein soll.|
|**Formatierung**|**Wählen Sie die Anzahl der Spalten aus, die vom Steuerelement belegt werden.**|Wenn der Abschnitt mit dem Feld mehrere Spalten enthält, können Sie die Anzahl der zu belegenden Felder bis zu der Anzahl der im Abschnitt enthaltenen Spalten festlegen.|  
|**Details**|**Anzeigename**,**Name** und **Beschreibung**|Diese schreibgeschützte Felder dienen als Referenz. Klicken Sie auf die Schaltfläche **Bearbeiten** für problemlosen Zugriff auf die Felddefinition, wenn Sie sie bearbeiten möchten.<br /><br /> Jede Instanz eines Felds im Formular eine Namenseigenschaft, damit auf sie in Formularskripten verwiesen werden kann; dieser Name wird jedoch von der Anwendung verwaltet. Die erste Instanz des Felds ist der Name des Felds, der beim Erstellen angegeben wurde. Weitere Informationen: [Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-fields.md)<br /><br /> Für jeden weiteren Einschluss des Feldes in einem Formular wird dem Namen eine Nummer ab 1 hinzugefügt. Wenn der Feldname "Neue Kosten" ist, ist die erste Instanz „Neue_Kosten“, dann folgt „Neue_Kosten1“ usw. für jede Instanz des Feldes auf dem Formular.<br /><br />**Hinweis:** Der Wert des Feldes **Beschreibung** zeigt Tooltipps an, wenn der Cursor darauf gesetzt wird.|  
|**Ereignisse**|**Formularbibliotheken**|Geben Sie gegebenenfalls JavaScript-Webressourcen an, die im Ereignishandler des Felds `OnChange` verwendet werden sollen.<br /><br />|  
||**Ereignishandler**|Konfigurieren Sie die Funktionen aus den Formularbibliotheken, die für das Feld `OnChange`-Ereignis aufgerufen werden sollen. Weitere Informationen: [Konfigurieren von Ereignishandler](configure-event-handlers-legacy.md)|  
|**Geschäftsregeln**|**Geschäftsregeln**|Anzeigen und Verwalten von Geschäftsregeln die auf dieses Feld verweisen. Weitere Informationen [Erstellen von Geschäftsregeln und Empfehlungen](create-business-rules-recommendations-apply-logic-form.md)|  
|**Steuerelemente**|**Steuerelemente**|Steuerelemente hinzufügen und ihre Verfügbarkeit in Web, Smartphone und Tablet angeben.|  

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars der modellgesteuerten App und seiner Komponenten](use-main-form-and-components.md)
