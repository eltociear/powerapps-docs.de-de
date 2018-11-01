---
title: Zeitgeber-Steuerelement in modellgesteuerten Apps in PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie Sie das Zeitgeber-Steuerelement verwenden können'
ms.custom: ''
ms.date: 06/06/2018
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
ms.assetid: b2b64771-083b-42f9-a3d5-2218f9d8a713
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="model-driven-app-timer-control-overview"></a>Zeitgeber-Steuerelement in modellgesteuerten Apps im Überblick

 Verwenden Sie ein Zeitgebersteuerelement in Formularen, in denen für Datensätze spezifische zeitbasierte Meilenstein gelten. Ein Zeitgebersteuerelement zeigt Mitarbetiern an, wie viel Zeit verfügbar ist, um eine Aktion bei der Lösung eines aktiven Datensatzes abzuschließen, oder wie viel Zeit vergqangen ist, seitdem die Zeit zum Abzuschließen der Aktion verstrichen ist. Mindestens müssen Zeitgeberkontrollen konfiguriert sein, um den Erfolg oder Fehlschlag beim Ausführen der Aktion anzuzeigen. Zudem kann er so konfiguriert werden, dass Warnungen angezeigt werden, wenndie Bedingungen auf einen Fehlschlag zulaufen.  
  
 Ein Zeitgebersteuerelement kann zu einem Formular für eine beliebige Entität hinzugefügt werden, sie werden jedoch am häufigsten verwendet für die Entität "Anfrage", insbesondere wenn sie mit Feldern verknüpft sind, die Vereinbarungen zum Servicelevel nachverfolgen. Sie können mehrere Zeitgeberkontrollen im Text eines Formulars hinzufügen. Sie können sie nicht der Kopf- und Fußzeile hinzufügen.  
  
 **Datenquellen**-Eigenschaften des Zeitgeber-Steuerelements verwenden Felder für die Entität.  
  
-   Das **Feld "Fehlerzeit"** verwendet ein Datum-Zeit-Feld, um die Uhrzeit festzulegen.  
  
-   Die drei Bedingungsfelder verwenden eines der Felder **Optionssatz**, **Zwei Optionen** **Status** oder **Statusgrund** für die Entität.  

Um ein Zeitgeber-Steuerelement zu erstellen, wählen Sie im Formular-Designer die Registerkarte **Einfügen** und dann in der Symbolleiste **Zeitgeber**. 

  > [!div class="mx-imgBorder"] 
  > ![Fügen Sie ein Zeitgeber-Steuerelement ein.](media/insert-timer-control.png)

Geben Sie auf der Zeitgeber-Steuerelement-Eigenschaftenseite die gewünschten Eigenschaften ein oder wählen diese aus, und wählen Sie dann **OK**. 

  
<a name="BKMK_TimerControlProperties"></a>   

## <a name="timer-control-properties"></a>Zeitgeber-Steuerelement-Eigenschaften  
 Die folgende Tabelle beschreibt die Eigenschaften eines Zeitgeber-Steuerelements.  
  
|Gruppe|Name|Beschreibung|  
|-----------|----------|-----------------|  
|Name|Name|**Erforderlich** Ein eindeutiger Name für das Steuerlelement.|  
||Etikett|**Erforderlich** Die Beschriftung, die für das Zeitgebersteuerelement anzuzeigen ist.|  
|Datenquelle|Feld "Fehlerzeit"|**Erforderlich** Wählen Sie eines der Datum-Zeit-Felder, das für die Entität dargestellt wird, wenn ein Meilenstein erfolgreich abgeschlossen werden soll.|  
||Erfolgsbedingung|**Erforderlich** Wählen Sie ein Feld für die Entität aus, um den Erfolg des Meilensteines auszuwerten, dann wählen Sie aus, welche Option Erfolg angibt.|  
||Warnungsbedingung|Wählen Sie ein Feld für die Entität aus, um zu evaluietren, ob der Erfolg des Meilensteines gefährdet ist, sodass eine Warnung angezeigt wird, dann wählen Sie aus, welche Option angibt, dass eine Warnung angezeigt werden soll.|  
||Bedingung abbrechen|Wählen Sie ein Feld für die Entität aus, um zu evaluieren, ob das Erreichen des Meilensteines storniert werden soll, dann wählen Sie aus, welche Option kennzeichnet, dass der Meilenstein storniert wurde.|  

## <a name="next-steps"></a>Nächste Schritte

[Übersicht zur Formular-Editor-Benutzeroberfläche](form-editor-user-interface-legacy.md)
