---
title: Erstellen und Bearbeiten von Feldern für Common Data Service für Apps mit PowerApps Projektmappen-Explorer | MicrosoftDocs
ms.custom: ''
ms.date: 05/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.author: matp
manager: brycho
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-fields-for-common-data-service-for-apps-using-powerapps-solution-explorer"></a>Erstellen und Bearbeiten von Feldern für Common Data Service für Apps mit PowerApps Lösungs-Explorer

Projektmappen-Explorer bietet eine Möglichkeit, um Felder für Common Data Service für Apps zu erstellen und zu bearbeiten.

[PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können mithilfe des Lösungs-Explorers nur festgelegt werden. <br />Weitere Informationen: 
- Weitere Informationen:  [Erstellen und Bearbeiten von Feldern für Common Data Service for Apps](create-edit-fields.md)
- [Erstellen und Bearbeiten von Feldern für Common Data Service für Apps mit PowerApps-Portals](create-edit-field-portal.md)
  
## <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Ein Teil des Namens jedes benutzerdefinierten Feldes, das Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diese Entität entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="view-fields"></a>Ansichtsfelder

Mit geöffnetem Projektmappen-Explorer erweitern Sie unter **Komponenten** die Option **Entitäten** und wählen Sie die Entität aus, in der Sie das Feld erstellen oder bearbeiten möchten.

![Projektmappen-Explorer-Feldansicht](media/solution-explorer-fields-view.png)

Sie können eine der folgenden Ansichten auswählen: 

 |Ansicht|Beschreibung|
 |--|--|
 |**Alle**| Zeigt alle Felder der Entität an|
 |**Benutzerdefiniert**|Zeigt nur benutzerdefinierte Felder der Entität an|
 |**Anpassbar**|Zeigt nur die Felder an, die bearbeitet werden können|

## <a name="create-a-field"></a>Erstellen Sie ein neues Feld

Während Sie Felder anzeigen, klicken Sie in der Befehlsleiste auf **Neu**, wodurch das neue Feldformular geöffnet wird.  Einige Standardentitäten oder benutzerdefinierte Entitäten, die in eine verwaltete Lösung eingebunden sind, erlauben möglicherweise nicht, neue Felder hinzuzufügen.

> [!NOTE]
> Für modellgesteuerte Apps können Sie auch ein neues Feld im Formulareditor erstellen. Im Formular-Editor, und klicken Sie unter **Feld-Explorer** auf **Neues Feld**, um ein neues Feld zu erstellen. Weitere Informationen: [Hinzufügen von Feldern zu einem Formular](../model-driven-apps/add-field-form.md)

![Neue Projektmappen-Explorer-Feldansicht](media/solution-explorer-new-field-form.png)

Sie müssen Daten eingeben und die Standardwerte bestätigen, die für die die folgenden Eigenschaften festgelegt werden, um zu speichern.

|Eigenschaft|Beschreibung|
|--|--|
|**Anzeigename**|Der Text für das Feld auf der Benutzeroberfläche, der angezeigt werden soll. Sie können dies ändern, nachdem Sie speichern, aber der Wert, den Sie eingeben, erstellt einen Wert für das Feld **Name**.|
|**Feldanforderung**|Ob Daten zum Speichern des Datensatzes im Feld erforderlich sind. Weitere Informationen: [Feldanforderungsoptionen](#field-requirement-options)|
|**Name**|Der eindeutige Name Ihrer Umgebung. Ein Name wird für Sie basierend auf dem Anzeigenamen generiert, die Sie eingegeben haben, aber Sie können ihn ändern, bevor Sie ihn speichern. Sobald ein Feld erstellt wurde, kann der Name nicht geändert werden, da er unter Umständen auf die Anwendungen oder Code verweist. Der Name hat folgendes Anpassungspräfix für den der Herausgeber der aktuellen Lösung vorangestellt ist.|
|**Durchsuchbar**|Legen Sie das auf **Nein** für Felder für die Entität fest, die Sie nicht verwenden.  Wenn ein Feld durchsuchbar ist, wird es in der **Erweiterten Suche** in modellgesteuerten Apps angezeigt und ist verfügbar, wenn Ansichten angepasst werden. Durch die Einstellung auf Nein wird die Anzahl von Optionen reduziert, die den Benutzern angezeigt werden, wenn sie die erweiterte Suche verwenden.|
|**Feldsicherheit**|Ob die Daten im Feld auf einer höheren Stufe gesichert sind als die Entität. Weitere Informationen: [Feldsicherheit, um den Zugriff zu steuern](/dynamics365/customer-engagement/admin/field-level-security)|
|**Überwachung**|Ob Daten für dieses Feld geprüft werden, wenn die Entität zur Prüfung aktiviert ist. Weitere Informationen: [Überwachen von Daten und Benutzeraktivität für Sicherheit und Kompatibilität](/customer-engagement/admin/audit-data-user-activity)|
|**Beschreibung**|Geben Sie Instruktionen für den Benutzer ein, um was es sich beim Feld handelt. Diese Beschreibung erscheint als Quickinfo für den Benutzer in Modell-angetriebenen Apps, wenn diese mit der Maus über die Beschriftung des Felds fahren.|
|**Wird im globalen Filter in interaktiven Funktionen angezeigt**|Weitere Informationen: [Dashboards für Interaktive Funktionen konfigurieren](/dynamics365/customer-engagement/customize/configure-interactive-experience-dashboards) |
|**Im Dashboard für interaktive Funktionen sortierbar**|Weitere Informationen: [Dashboards für Interaktive Funktionen konfigurieren](/dynamics365/customer-engagement/customize/configure-interactive-experience-dashboards)|
|**Datentyp**|Steuert, wie Werte gespeichert werden sowie wie sie in einigen Anwendungen formatiert werden. Sobald ein Feld gespeichert ist, können Sie den Typ nicht mehr ändern, da sich das möglicherweise auf die Daten in der Entität auswirkt. Weitere Informationen: [Felddatentypen](#field-data-types).|
|**Feldtyp**|Ob das Feld **Einfach**, **Berechnet** oder **Rollup** ist. Weitere Informationen: [Feldtypen](#field-type).|
|**Format**|So wird das Feld formatiert. Die verfügbaren Formatierungsoptionen hängen von dem **Datentyp** ab.|

Sie können auch weitere Optionen abhängig von der Auswahl von **Datentyp** festlegen. Weitere Informationen: [Felddatentypen](#field-data-types).

## <a name="field-requirement-options"></a>Feldanforderungsoptionen

Es stehen drei Feldanforderungsoptionen zur Verfügung:
- **Optional**: Der Datensatz kann gespeichert werden, auch wenn keine Daten in diesem Feld vorhanden sind.
- **Eingabe empfohlen**: Der Datensatz kann gespeichert werden, auch wenn keine Daten in diesem Feld vorhanden sind. Allerdings wird ein blaues Symbol neben dem Feld angezeigt, um anzugeben, dass es wichtig ist.
- **Eingabe erforderlich**: Der Datensatz kann gespeichert werden, wenn keine Daten in diesem Feld vorhanden sind.
> [!NOTE]
> Gehen Sie vorsichtig vor, wenn Sie Felder für geschäftlich erforderlich erklären. Benutzer werden die Anwendung nicht nutzen, wenn sie Datensätze nicht speichern können, weil ihnen die für ein erforderliches Feld benötigten Daten fehlen. Möglicherweise geben sie dann einfach falsche Daten ein, nur, um weiterarbeiten zu können. Sie können Unternehmensregeln oder Formularskripts verwenden, um die Erforderlichkeitsstufe zu ändern, wenn sich die Daten in dem Datensatz ändern. Weitere Informationen: [Erstellen von Geschäftsregeln und Empfehlungen zur Anwendung einer Logik in einem Formular](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

## <a name="field-data-types"></a>Felddatentypen

Es gibt zahlreiche unterschiedlichen Arten Felder, aber Sie können nur einige davon erstellen. Weitere Informationen für alle Feldtypen unter [Feldttypen und Datenfeldertypen](types-of-fields.md)

Wenn ein Feld erstellt wird gibt**Datentyp** die folgenden Optionen:

|Option|Beschreibung|
|--|--|
|**Einzelne Textzeile**|Bis zu 4000 Textzeichen können in diesem Feld enthalten sein. Sie können eine geringere Maximallänge als das festlegen. Dieses Feld hat verschiedene Formatoptionen, die die Textanzeige ändern.  Weitere Informationen: [Einzeilen-Textoptionen](#single-line-of-text-options)|
|**Optionssatz**|Zeigt eine Liste der Optionen an, in der eine ausgewählt werden kann. Weitere Informationen: [Feldoptionen für Optionssätze](#option-set-field-options)|
|**MultiSelect-Optionssatz**|Zeigt eine Liste von Optionen an, in der mehr als eine ausgewählt werden kann. Weitere Informationen: [Feldoptionen für Optionssätze](#option-set-field-options)|
|**Zwei Optionen**|Zeigt eine Liste von Optionen an, in der eine von zwei ausgewählt werden kann.<br /><br /> Felder mit zwei Optionen bieten keine Formatoptionen auf Feldebene. Wenn Sie jedoch ein solches Feld einem Formular hinzufügen, können Sie es als Optionsfelder, Kontrollkästchen oder Auswahlliste anzeigen.|
|**Bild**|Zeigt ein einzelnes Bild pro Datensatz in der Anwendung an. Jede Entität kann über ein Bildfeld verfügen. Bildfelder werden immer `EntityImage` genannt.|
|**Ganze Zahl**|Ganze Zahlen mit einem Wert zwischen -2.147.483.648 und 2.147.483.647 können in diesem Feld verwendet werden.  Dieses Feld enthält Optionen, die sich abhängig davon ändern, wie das Feld dargestellt wird. Weitere Informationen: [Ganzzahloptionen](#whole-number-options)|
|**Gleitkommazahl**|Es können bis zu 5 Dezimalstellen für Werte zwischen -100.000.000.000 und -100.000.000.000 in diesem Feld verwendet werden. Sie können die Präzisionsebene und die Maximal- und Minimalwerte angeben. Weitere Informationen: [Mithilfe des richtigen Typ der Anzahl](types-of-fields.md#using-the-right-type-of-number)|
|**Dezimalzahl**|Es können bis zu 10 Dezimalstellen für Werte zwischen -100.000.000.000 und -100.000.000.000 in diesem Feld verwendet werden. Sie können die Präzisionsebene und die Maximal- und Minimalwerte angeben. Weitere Informationen: [Mithilfe des richtigen Typ der Anzahl](types-of-fields.md#using-the-right-type-of-number)|
|**Währung**|Geldbeträge zwischen -922.337.203.685.477 und 922.337.203.685.477 können in diesem Feld verwendet werden. Sie können eine Präzisionsebene angeben, die Präzision auf einer bestimmten Währung basieren oder eine von der Organisation genutzte einzelne Standardpräzision verwenden. Weitere Informationen: [Verwenden der Währungsfelder](types-of-fields.md#using-currency-fields)|
|**Mehrere Textzeilen**|Bis zu 1.048.576 Textzeichen können in diesem Feld enthalten sein. Sie können die maximale Länge als weniger festlegen. Wenn Sie das Feld einer modellgesteuerten App hinzufügen, können Sie die Dimensionen des Felds angeben.|
|**Datum und Uhrzeit**|Verwenden Sie diese Felder, um Zeitwerte zu speichern. Sie können Werte so früh wie 1/1/1753 12:00 AM speichern. Weitere Informationen: [Datums- und Zeitoptionen](#date-and-time-options)|
|**Suche**|Ein Feld, das die Einrichtung einer Referenz zu einem einzelnen Datensatz eines bestimmten Entitätstyps erlaubt. Einige Systemsuchfelder verhalten sich unterschiedlich. Weitere Informationen: [Unterschiedliche Suchmethoden](types-of-fields.md#different-types-of-lookups)|
|**Kunde**|Ein Suchfeld, das Sie verwenden können, um einen Kunden anzugeben, der ein Konto oder ein Kontakt sein kann.  Weitere Informationen: [Unterschiedliche Suchmethoden](types-of-fields.md#different-types-of-lookups)|

### <a name="single-line-of-text-options"></a>Einzeilen-Textoptionen

Der Datentyp "Einzelne Textzeile" hat folgende Formatoptionen:

|Format|Beschreibung|
|--|--|
|**Text**|Ein beabsichtigte Textwert, um ein einzeiliges Textfeld anzuzeigen.|
|**Textbereich**|Ein beabsichtigte Textwert, um ein emehrzeiliges Textfeld anzuzeigen. Wenn Sie mehr als 4.000 Zeichen brauchen, verwenden Sie einen **Mehrere Textzeilen** Datentyp.|
|**Email**|Ein Textwert überprüft die E-Mail-Adresse und wird als mailto Link im Feld gerendert. |
|**URL**|Ein Textwert als URL validiert und gerendert als Link, um die URL zu öffnen.|
|**Tickersymbol**|Ein Textwert für ein Tickersymbol, das einen Link anzeigt, der geöffnet wird, um ein Angebot für ein Börsentickersymbol anzuzeigen. |
|**Telefonnummer**|Ein als Textwert überprüfte Telefonnummer gerendert als Link, um einen Telefonanruf einzuleiten mithilfe von Skype. |

Sie können auch eine **Maximallänge** festlegen, sodass das System keine Textwerte zulässt, die länger als von Ihnen angegeben sind.

### <a name="option-set-field-options"></a>Optionssatzfeldoptionen

Felder, die einen Satz von Optionen bereitstellen, können ihren eigenen Satz von *lokalen* Optionen haben oder sich auf *globale* Optionen festlegen, die in mehreren Feldern verwendet werden können.

Verwenden eines globalen Optionssatzes ist dann von Nutzen, wenn Sie denselben Satz von Optionen für mehrere Felder erstellen möchten. Durch einen globalen Optionssatzes müssen Sie nur die Gruppe von Optionen von einem Ort verwalten. 

Wenn Sie den Datentyp **Mehrfachauswahl-Optionssatz** oder **Optionssatz** auswählen, stellt der Projektmappen-Explorer-Designer die Option für einen lokalen Optionssatz standardmäßig bereit.

![Konfigurieren eines lokalen Optionssatzes](media/local-option-set-solution-explorer.png)

#### <a name="configure-local-options"></a>Konfigurieren lokaler Optionen

[!INCLUDE [cc_configure-option-set-options-solution-explorer](../../includes/cc_configure-option-set-options-solution-explorer.md)]

#### <a name="use-existing-option-set"></a>Vorhandenen Optionssatz verwenden

Wenn Sie **Vorhandenen Optionssatz verwenden** wählen, zeigt der Designer eine Liste vorhandener *globaler Optionssätze* und schließt Schaltflächen zum **Bearbeiten** und **Neu** ein, um die globalen Optionen zu konfigurieren, die dieses Felds verwendet sollte.

![Konfigurieren eines globalen Optionssatzes](media/global-option-set-solution-explorer.png)

Sie können globale Optionssätze auch separat konfigurieren. Weitere Informationen: [Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service for Apps (Auswahl)](create-edit-global-option-sets.md)

> [!NOTE]
> Wenn Sie jeden Optionssatz als globalen Optionssatz in der Liste der globalen Optionssätze definieren, wächst diese Liste und könnte zum Verwalten schwierig werden. Wenn Sie wissen, dass der Datensatz von Optionen nur an einer Stelle verwendet wird, verwenden Sie einen lokalen Optionssatz.


### <a name="whole-number-options"></a>Ganzzahloptionen

Ganzzahlfelder haben die folgenden Formatmöglichkeiten:

|Format|Beschreibung|
|--|--|
|**Keine**|Ein Zahlenwert dargestellt in einem Textfeld.|
|**Dauer**|Ein Zahlenwert dargestellt als Dropdownliste, die Zeitintervalle enthält. Ein Benutzer kann einen Wert in der Liste auswählen oder einen ganzzahligen Wert eingeben, der die Anzahl von Minuten darstellt.|
|**Zeitzone**|Ein Zahlenwert dargestellt als Dropdownliste, die Zeitzonen enthält.|
|**Sprache**|Ein Zahlenwert als Dropdownliste, die eine Liste von Sprachen enthält, die für die Organisation aktiviert sind. Wenn keine anderen Sprachen aktiviert sind, ist die einzige Option die Ausgangssprache. Der gespeicherte Wert ist der Locale Identifier (LCID)-Wert für die Sprache.|

Sie können auch die zulässigen Maximal- und Minimalwerte einschränken.

### <a name="date-and-time-options"></a>Datums- und Zeitoptionen

Datums- und Zeitfelder haben die folgenden Optionen:

|Format |Beschreibung|
|--|--|
|**Datum und Uhrzeit**|Geben Sie ein Datum und einen Wert ein.|
|**Nur Datum**|Ein Datums- und Uhrzeitwert, der nur ein Datum anzeigt. Der Zeitwert wird gespeichert als 12:00 morgens (00:00: 00) im System.|

Sie können bestimmte **Verhalten** für Datum-Zeit-Fenster unter **Erweiterte Optionen** festlegen.

- **Ortszeit Benutzer** : Zeigt die Werte an, die in der aktuellen lokalen Zeitzone des Benutzers umgewandelt werden. Dies ist Standardeinstellung für dieses neue Feld.
- **Nur Datum**: Dieses Verhalten ist für den Typ **Nur Datum** verfügbar. Zeigt Werte ohne Zeitzonenkonvertierung an. Verwenden Sie diese Option für Daten wie Geburtstage und Jahrestage.
- **Zeitzonen unabhängig**: Zeigt Werte ohne Zeitzonenkonvertierung an.

Weitere Informationen: [Verhalten und Format des Datums- und Uhrzeitfelds](behavior-format-date-time-field.md)

## <a name="field-type"></a>Field-Typ

Sie können ein benutzerdefiniertes Feld **Feldtyp** festlegen, dass ein **Einfach**, **Berechnet** oder **Rollup** Feld ist. 

### <a name="simple"></a>Einfach

Einfach heißt, dass das Feld kein berechnetes oder Rollupfeld ist.

### <a name="calculated"></a>Berechnet

Mit einem berechneten Feld können Sie eine Formel eingeben, um einen Wert für das Feld zuzuweisen. Diese Datentypen können auf berechnete Felder festgelegt werden: **Währung**, **Datum und Uhrzeit**, **Dezimalzahl**, **Multi ausgewählter Optionssatz**, **Optionssatz**, **Einzelne Textzeile**, **Zwei Optionen** und **Ganze Zahl**.

Weitere Informationen [Definition berechneter Felder für das Automatisieren von manuellen Berechnungen](define-calculated-fields.md)

### <a name="rollup"></a>Rollup

Mit ein Rollupfeld können Sie Aggregationsfunktionen festlegen, die regelmäßig ausgeführt werden, um einen Zahlenwert für das Feld festlegen. Diese Daten können auf berechnetes Feld festgelegt werden: **Währung**, **Datum und Uhrzeit**, **Dezimalzahl** und **Ganze Zahl**.

Weitere Informationen: [Definieren der Rollupfelder für die Gesamtwerte](define-rollup-fields.md)

## <a name="save-new-field"></a>Neues Feld speichern

Nachdem Sie das Feld konfiguriert haben, verwenden Sie einen aus drei Befehle in der Befehlsleiste:

|Befehl|Beschreibung|
|--|--|
|**Speichern**|Sichern Sie die Felddefinition und lassen Sie das Formularfenster geöffnet.|
|**Speichern und schließen**|Sichern Sie die Felddefinition und schließen Sie das Fenster.|
|**Speichern Neu erstellen**|Speichern Sie die Felddefinition und öffnen Sie ein neues Formular, um ein neues Feld zu erstellen.|


## <a name="edit-a-field"></a>Bearbeiten eines Felds 

Während dem [Anzeigen von Feldern](#view-fields) klicken Sie auf das Feld, das Sie bearbeiten möchten. Einige Standardfelder oder benutzerdefinierte Felder, die in eine verwaltete Lösung eingebunden sind, können möglicherweise nicht bearbeitet werden.

> [!NOTE]
> Beim Bearbeiten eines Formular für ein beliebiges Feld, das bereits für dem Formular hinzugefügt ist, können Sie auf das Feld **Feldeigenschaften**, doppelklicken, um es anzuzeigen. Klicken Sie auf der Registerkarte **Details** auf **Bearbeiten**. Weitere Informationen: [Hinzufügen von Feldern zu einem Formular](../model-driven-apps/add-field-form.md)

Nachdem Sie Änderungen an einem Feld vorgenommen haben, müssen Sie Anpassungen veröffentlichen. 

- Um die Änderungen für eine Entität zu veröffentlichen, wählen Sie unter **Komponenten** die Option **Entitäten** aus, und anschließend die Entität, in der Sie die Änderungen vorgenommenen haben. Wählen Sie auf der **Aktionssymbolleiste** die Option **Veröffentlichen** aus.  
  
- Wenn Sie alle Änderungen veröffentlichen möchten, die an mehreren Entitäten oder Komponenten vorgenommen wurden, wählen Sie auf der **Aktionssymbolleiste** die Schaltfläche **Alle Anpassungen veröffentlichen** aus.  
  
> [!NOTE]
>  Das Installieren einer Lösung oder Veröffentlichen von Anpassungen kann den normalen Systembetrieb stören. Wir empfehlen, dass Sie die Veröffentlichung einer Lösung dann planen, wenn sie die Benutzer am wenigsten stört.  

### <a name="edit-multiple-fields"></a>Mehrere Felder bearbeiten

Wenn Sie ein Feld oder mehrere Felder bearbeiten möchten, wählen Sie das Feld oder die Felder aus (mithilfe der UMSCHALTTASTE), die Sie bearbeiten möchten, und wählen Sie dann auf der **Aktionssymbolleiste** die Option **Bearbeiten** aus. 
  
Wenn Sie mehrerer Felder zum Bearbeiten auswählen, wird das Dialogfeld **Mehrere Felder bearbeiten** angezeigt. Sie können **Feldanforderung**, **Durchsuchbar** und **Überwachung** bearbeiten. 

## <a name="delete-a-field"></a>Löschen eines Felds

Als Benutzer mit der Sicherheitsrolle "Systemadministrator" können Sie benutzerdefinierte Felder löschen, die nicht Teil einer verwalteten Lösung sind. Wenn Sie Felder löschen, werden alle Daten in den Feldern gelöscht. Die einzige Möglichkeit, Daten aus einem Feld wiederherzustellen, das entfernt wurde, besteht darin, die Datenbank von einem Zeitpunkt wiederherzustellen, bevor das Feld gelöscht wurde.

> [!NOTE]
> Vor dem Löschen eines benutzerdefinierten Feldes müssen Sie alle Abhängigkeiten in anderen Lösungskomponenten entfernen. 

1. Während dem [Anzeigen von Feldern](#view-fields) wählen Sie ein benutzerdefiniertes Feld aus, das in der Liste gelöscht werden kann und klicken auf die Schaltfläche ![Befehl löschen](../model-driven-apps/media/delete.gif) in der Befehlsleiste.
2. Wählen Sie im Dialog **Löschen bestätigen** die Option **Löschen**.

> [!TIP]
> Sie können mehrere benutzerdefinierte Felder auswählen, die in einem Vorgang gelöscht werden.

### <a name="check-field-dependencies"></a>Feldabhängigkeiten prüfen 

Wählen Sie das Feld in der Liste aus. Wählen Sie im Menü **Weitere Aktionen** **Abhängigkeiten anzeigen** aus.

![Abhängigkeiten für das Feld anzeigen](media/check-field-dependencies.png)

Abhängigkeiten sind alle zugehörigen Verwendungen des Felds, die verhindern würden, dass es gelöscht wird. Wenn das Feld beispielsweise in einem Formular oder in einer Ansicht verwendet wird, müssen Sie zunächst Verweise auf das Feld in diesen Lösungskomponenten entfernen.  
  
Wenn Sie ein Suchfeld löschen, wird die 1: N-Entitätsbeziehung für dieses automatisch gelöscht.  

## <a name="ime-mode"></a>IME-Modus

Alle Felder, die direkte Texteingabe ermöglichen, haben einen IME-Modus. Der Eingabemethoden-Editor (IME) wird für ostasiatische Sprachen wie Japanisch verwendet. IMEs ermöglichen Benutzern die Eingabe von Tausenden von ostasiatischen Schriftzeichen über eine normale Tastatur mit 101 Tasten.


### <a name="see-also"></a>Siehe auch  
Weitere Informationen:  [Erstellen und Bearbeiten von Feldern für Common Data Service for Apps](create-edit-fields.md)<br />
[Erstellen und Bearbeiten von Feldern für Common Data Service für Apps mit PowerApps-Portals](create-edit-field-portal.md)<br />
[Feldtypen und Felddatentypen](types-of-fields.md)<br />
[Definition berechneter Felder für das Automatisieren von manuellen Berechnungen](define-calculated-fields.md)<br />
[Definition von Rollupfeldern, die Werte aggregieren](define-rollup-fields.md)<br />
[ Verhalten und Format des Datums- und Uhrzeitfelds.](behavior-format-date-time-field.md)
