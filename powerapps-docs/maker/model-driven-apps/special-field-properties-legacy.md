---
title: Spezielle Feldeigenschaften für Hauptformulare in modellgesteuerten Apps in PowerApps | MicrosoftDocs
description: Grundlegendes zu speziellen Feldeigenschaften für Hauptformulare
Keywords: Hauptformulare; Besondere Feldeigenschaften; Dynamics 365
author: Mattp123
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 6ad7e43c-b6a1-48c4-9dfb-ed830142a841
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="overview-of-model-driven-app-special-field-properties"></a>Überblick über besondere Feldeigenschaften in modellgesteuerten Apps

 Alle Felder haben die Eigenschaften, die in [Allgemeine Feldeigenschaften](common-field-properties-legacy.md) aufgelistet sind, aber bestimmte Felder haben zusätzliche Eigenschaften, wie beispielsweise dieses Berechtigungsfeld, das vom Hauptanfrageformular aus für die Anfrageentität geöffnet werden kann.  

![Spezieller Feldeigenschaftendialog](media/special-properties.png)
  
<a name="BKMK_LookupFieldProperties"></a>  
 
## <a name="lookup-field-properties"></a>Suche-Feldeigenschaften  
  
> [!NOTE]
>  Die Optionen, die in der Tabelle unten beschrieben werden, sind nur für Suchfelder von Einzel-Entitäten verfügbar.  
  
|Abschnitt|Eigenschaft|Beschreibung|  
|-------------|--------------|-----------------|  
|**Nach verknüpften Datensätzen filtern**|**Nur Datensätze anzeigen, für die Folgendes zutrifft:**|Wenn dies aktiviert ist, wird auf die Datensätze, die angezeigt werden, wenn Benutzer nach einem Datensatz suchen, ein zusätzlicher Filter angewendet. Dies hilft bei relevanteren Suchaktionen, wenn der Wert der Suche eingestellt wird.<br /><br /> Diese Option ist standardmäßig deaktiviert.<br /><br /> Die Beziehungskombinationen, die möglich sind, wenn Sie zugehörige Datensätze filtern, sind in der folgenden Tabelle aufgeführt*.<br /><br /> Die erste Liste wird mit allen potenziellen Beziehungen gefüllt, die Sie zum Filtern dieser Suche verwenden können. Eins auswählen.<br /><br /> Die zweite Liste wird dann mit allen Beziehungen gefüllt, die die (in der ersten Liste ausgewählte) verknüpfte Entität mit der Zielentität verbinden. Eins auswählen.<br /><br /> Aktivieren Sie das Kontrollkästchen **Zulassen, dass Benutzer den Filter ausschalten**, um Benutzern die Möglichkeit zu geben, den Filter auszuschalten, den Sie hier definieren.<br /><br /> Wenn Benutzer die Option **Weitere Datensätze nachschlagen** auswählen, während sie den Wert für eine Suche festlegen, sehen sie dieses Dialogfeld.<br /><br /> ![Weitere Datensätze nachschlagen](media/crm-ua-v-8-1-look-up-more-records.png) <br /><br /> Wenn Sie die Option **Zulassen, dass Benutzer den Filter ausschalten** ausgewählt haben, während Sie das Suchfeld konfigurieren, sehen Benutzer das Kontrollkästchen, um den Filter auszuschalten.  Das ermöglicht es ihnen, einen weiteren Bereich von Datensätzen zu sehen. Wenn Sie sicherstellen möchten, dass Benutzer nur einen begrenzten Bereich von Datensätzen sehen, der durch diesen Filter definiert wird, deaktivieren Sie das Kontrollkästchen  **Zulassen, dass Benutzer den Filter ausschalten**.|  
|**Zusätzliche Eigenschaften**|**Suchfeld im Suchdialogfeld anzeigen**|Sie können wählen, dass das Suchfeld im Suchdialogfeld nicht angezeigt werden soll.|  
||**Standardansicht**|Diese Ansicht wird verwendet, um die Ergebnisse der Inlinesuche zu filtern und die Standardansicht festzulegen, die im Suchdialog angezeigt wird, wenn Benutzer die Option **Weitere Datensätze suchen** auswählen.<br /><br /> Die Standardansicht steuert auch, welche Felder in die Inline-Suche einbezogen werden.<br /><br /> Für Suchen, die nur die Auswahl eines einzigen Entitätstyps zulassen, werden die Felder, die in der Inline-Suche angezeigt werden, als erste beiden Felder festgelegt, die in die Standardansicht einbezogen werden. In diesem Beispiel sind **Telefon 1** und **E-Mail** die ersten zwei Spalten, die in der Standardansicht für eine Firmensuche konfiguriert sind.<br /><br /> Für Systemsuchen, die mehrere Entitätstypen zulassen, werden die ersten beiden Spalten der Entitätssuchanzeige angezeigt.|  
||**Ansichtsauswahl**|Sie können aus drei Optionen auswählen:<br /><br /> -   **Deaktiviert**: Lassen Sie nicht zu, dass Benutzer eine andere Ansicht auswählen.<br />-   **Alle Ansichten anzeigen**: Alle Ansichten sind verfügbar.<br />-   **Ausgewählte Ansichten anzeigen**: Wenn Sie diese Option auswählen, können Sie die STRG-Taste und Ihren Cursor verwenden, um anzugeben, welche Ansichten angezeigt werden sollen. Die Suchansicht kann für die nicht Entität abgewählt werden.|  
  
 **\*Mögliche Beziehungskombinationen**  
  
|Erste Liste - Beziehung|Zweite Liste - Beziehung|Verfügbar?|  
|-----------------------------|------------------------------|----------------|  
|n:1|1:n|Ja|  
|n:1|n:1|Ja|  
|n:1|n:n|Ja|  
|1:n|1:n|Ja|  
|1:n|n:1|No|  
|1:n|n:n|No|  
|n:n|1:n|Ja|  
|n:n|n:1|No|  
|n:n|n:n|No|  
  
<a name="BKMK_TwoOptionProperties"></a>   

### <a name="two-option-field-properties"></a>Zwei Optionsfeldeigenschaften  
 Auf der Formatierungsregisterkarte haben zwei Optionsfelder die folgende Formatierungsauswahl:  
  
- **Zwei Optionsfelder**: Zwei beschriftete Steuerelemente. Nur eines davon kann ausgewählt werden.  
  
- **Kontrollkästchen**: Ein einzelnes Kontrollkästchen, um den Wert "true" anzugeben; ansonsten gilt "false".  
  
- **Liste**: Eine Dropdownliste mit beiden Werten.  
  
<a name="BKMK_MultipleLinesOfTextProperties"></a>   

### <a name="multiple-lines-of-text-field-properties"></a>Mehrere Textzeilenfeldeigenschaften  
 Felder mit mehreren und solche mit einer Textzeile, die das `Text Area`-Format verwenden, verfügen über die Eigenschaft **Zeilenlayout**. Damit können Sie einen Wert für **Anzahl der Zeilen** angeben oder **Automatisch erweitern, um verfügbaren Bereich auszufüllen** auswählen.  

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)
