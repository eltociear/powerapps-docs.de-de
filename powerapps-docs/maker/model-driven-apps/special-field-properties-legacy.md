---
title: Spezielle Feldeigenschaften von modellgesteuerten Apps für Hauptformulare in PowerApps | Microsoft-Dokumentation
description: Informationen zu speziellen Feldeigenschaften für Hauptformulare
Keywords: Main forms; Special field properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 6ad7e43c-b6a1-48c4-9dfb-ed830142a841
ms.openlocfilehash: 0c4e67b14816ae6eaf100221ac0ac29269000f9b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39682153"
---
# <a name="overview-of-model-driven-app-special-field-properties"></a>Übersicht über spezielle Feldeigenschaften von modellgesteuerten Apps

 Alle Felder weisen die unter [Allgemeine Feldeigenschaften](common-field-properties-legacy.md) aufgeführten Eigenschaften auf, aber bestimmte Felder verfügen über zusätzliche Eigenschaften. Dies ist etwa bei diesem Berechtigungsfeld der Fall, das vom Hauptformular aus für die Fallentität geöffnet werden kann.  

![special-properties-dialog](media/special-properties.png)
  
<a name="BKMK_LookupFieldProperties"></a>  
 
## <a name="lookup-field-properties"></a>Eigenschaften des Suchfelds  
  
> [!NOTE]
>  Die in der folgenden Tabelle beschriebenen Optionen sind nur für Suchfelder von einzelnen Entitäten verfügbar.  
  
|Abschnitt|Eigenschaft|Beschreibung|  
|-------------|--------------|-----------------|  
|**Nach verknüpften Datensätzen filtern**|**Nur Datensätze anzeigen, für die Folgendes zutrifft**|Wenn diese Option aktiviert ist, werden zusätzliche Filter auf Datensätze angewendet, die angezeigt werden, wenn der Benutzer nach einem Datensatz sucht. Wenn Sie den Wert der Suche festlegen, erhalten Sie somit Suchergebnisse mit höherer Relevanz.<br /><br /> Standardmäßig ist dieser deaktiviert.<br /><br /> Die Beziehungskombinationen, die möglich sind, wenn Sie verknüpfte Datensätze filtern, sind in der Tabelle nach dieser Tabelle aufgeführt.*<br /><br /> Die erste Liste wird mit allen möglichen Beziehungen aufgefüllt, die Sie zum Filtern dieser Suche verwenden können. Wählen Sie eine Option aus.<br /><br /> Die zweite Liste wird dann mit allen Beziehungen aufgefüllt, die die verknüpfte Entität (in der ersten Liste ausgewählt) mit der Zielentität verbindet. Wählen Sie eine Option aus.<br /><br /> Aktivieren Sie das Kontrollkästchen **Zulassen, dass Benutzer den Filter ausschalten**, um Benutzern die Möglichkeit zu bieten, den hier definierten Filter zu deaktivieren.<br /><br /> Wenn Benutzer die Option **Datensätze suchen** beim Festlegen des Werts für eine Suche auswählen, wird dieses Dialogfeld angezeigt.<br /><br /> ![look-up-more-records](media/crm-ua-v-8-1-look-up-more-records.png) <br /><br /> Wenn Sie die Option **Zulassen, dass Benutzer den Filter ausschalten** beim Konfigurieren des Suchfelds ausgewählt haben, wird Benutzern das Kontrollkästchen angezeigt, um den Filter zu deaktivieren.  Dadurch können diese eine größere Anzahl von Datensätzen anzeigen. Wenn Sie sicherstellen möchten, dass Benutzer nur einen begrenzten Bereich von Datensätzen sehen, der mit diesem Filter definiert wird, deaktivieren Sie das Kontrollkästchen **Zulassen, dass Benutzer den Filter ausschalten**.|  
|**Zusätzliche Eigenschaften**|**Suchfeld im Suchdialogfeld anzeigen**|Sie können festlegen, dass das Suchfeld nicht im Suchdialogfeld angezeigt wird.|  
||**Standardansicht**|In dieser Ansicht werden die Ergebnisse der Inlinesuche gefiltert und die Standardansicht festgelegt, die im Suchdialogfeld angezeigt wird, wenn Benutzer auf die Option **Datensätze suchen** klicken.<br /><br /> Die Standardansicht steuert zudem, welche Felder in die Inlinesuche eingeschlossen werden.<br /><br /> Bei Suchvorgängen, die lediglich die Auswahl eines einzelnen Entitätstyps zulassen, werden die in der Inlinesuche angezeigten Felder so konfiguriert, dass die ersten beiden Felder in der Standardansicht eingeschlossen werden. In diesem Beispiel sind **Telefon 1** und **E-Mail** die ersten beiden Spalten in der Standardansicht, die für eine Firmensuche konfiguriert sind.<br /><br /> Bei Systemsuchen, die mehrere Entitätstypen zulassen, werden die ersten beiden Spalten der Entitätssuchansicht angezeigt.|  
||**Ansichtsauswahl**|Sie können aus drei Optionen auswählen:<br /><br /> -   **Aus**: Benutzern ist es nicht erlaubt, eine andere Ansicht auszuwählen.<br />-   **Alle Ansichten anzeigen**: Alle Ansichten sind verfügbar.<br />-   **Ausgewählte Ansichten anzeigen**: Bei Auswahl dieser Option können Sie mit der STRG-TASTE und dem Cursor festlegen, welche Ansichten angezeigt werden sollen. Die Suchansicht für die Entität kann nicht deaktiviert werden.|  
  
 **\*Mögliche Beziehungskombinationen**  
  
|Beziehung der ersten Liste|Beziehung der zweiten Liste|Verfügbar?|  
|-----------------------------|------------------------------|----------------|  
|n:1|1:n|Ja|  
|n:1|n:1|Ja|  
|n:1|m:n|Ja|  
|1:n|1:n|Ja|  
|1:n|n:1|Nein|  
|1:n|m:n|Nein|  
|m:n|1:n|Ja|  
|m:n|n:1|Nein|  
|m:n|m:n|Nein|  
  
<a name="BKMK_TwoOptionProperties"></a>   

### <a name="two-option-field-properties"></a>Feldeigenschaften mit zwei Optionen  
 Auf der Registerkarte „Formatierung“ sind zwei Optionsfelder mit den Formatierungsoptionen verfügbar:  
  
- **Zwei Optionsfelder**: Zwei Steuerelemente mit Beschriftungen. Es kann nur ein Steuerelement ausgewählt werden.  
  
- **Kontrollkästchen**: Ein einzelnes Kontrollkästchen, um den Wert „true“ oder „false“ festzulegen.  
  
- **Liste**: Eine Dropdownliste, die beide Werte enthält.  
  
<a name="BKMK_MultipleLinesOfTextProperties"></a>   

### <a name="multiple-lines-of-text-field-properties"></a>Feldeigenschaften mit mehreren Textzeilen  
 Felder mit mehreren Textzeilen und einer einzelnen Textzeile, die das `Text Area`-Format aufweisen, besitzen die Eigenschaft **Zeilenlayout**. Mit dieser Eigenschaft können Sie einen Wert für **Zeilenanzahl** angeben oder **Automatisch erweitern, um verfügbaren Bereich auszufüllen** wählen.  

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars der modellgesteuerten App und seiner Komponenten](use-main-form-and-components.md)
