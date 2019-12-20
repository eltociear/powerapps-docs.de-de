---
title: Erstellen und Bearbeiten von Feldern für Common Data Service mit dem Power Apps-Portal | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/13/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 21e0d713608b2c0bddcf9dc7d292973f0f58259f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861425"
---
# <a name="create-and-edit-fields-for-common-data-service-using-power-apps-portal"></a>Erstellen und Bearbeiten von Feldern für Common Data Service mit dem Power Apps-Portal

Das [Power Apps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) stellt eine einfache Möglichkeit zur Verfügung, Entitätsfelder mit dem Common Data Service zu erstellen und zu bearbeiten.

PowerApps-Portal aktiviert das  Konfigurieren der allgemeinen Optionen, jedoch bestimmte Optionen können nur mithilfe des Lösungs-Explorers festgelegt werden. <br />Weitere Informationen: 
- [Erstellen und Bearbeiten von Feldern für Common Data Service](create-edit-fields.md)
- [Erstellen und Bearbeiten von Feldern für Common Data Service mithilfe des Power Apps-Projektmappen-Explorers](create-edit-field-solution-explorer.md)

## <a name="view-fields"></a>Ansichtsfelder

1. Wählen Sie im [Power Apps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) entweder den Entwurfsmodus **Modellgesteuert** oder **Canvas** aus.
2. Wählen Sie > **Daten** und **Entitäten** wählen Sie die Entität aus, die die Felder enthält, die Sie anzeigen möchten.
3. Wenn die Registerkarte **Felder** ausgewählt ist, können Sie die folgenden Ansichten auswählen: 

 |Ansicht|Beschreibung|
 |--|--|
 |**Alle**| Zeigt alle Felder der Entität an|
 |**Benutzerdefiniert**|Zeigt nur benutzerdefinierte Felder der Entität an|
 |**Standard**|Zeigt nur Standard-Felder der Entität an|
<!-- TODO: What is the actual difference between All and Default? -->

## <a name="create-a-field"></a>Erstellen Sie ein neues Feld

Während Felder angezeigt werden in der Befehlsleiste, klicken Sie auf  **Feld hinzufügen** um den Bereich **Feldeigenschaften** anzuzeigen.

![Feldeigenschaften](media/field-properties.png)


Es sind nur drei Feldeigenschaften verfügbar:

 |Eigenschaft|Beschreibung|
 |--|--|
 |**Anzeigename**|Der Text für das Feld auf der Benutzeroberfläche, der angezeigt werden soll.|
 |**Name**|Der eindeutige Name Ihrer Umgebung. Ein Name wird für Sie basierend auf dem Anzeigenamen generiert, die Sie eingegeben haben, aber Sie können ihn ändern, bevor Sie ihn speichern. Sobald ein Feld erstellt wurde, kann der Name nicht geändert werden, da er unter Umständen auf die Anwendungen oder Code verweist. Der Name hat folgendes Anpassungspräfix für den **Common Data Service Standardherausgeber** verwendet.|
 |**Datentyp**|Steuert, wie Werte gespeichert werden sowie wie sie in einigen Anwendungen formatiert werden. Sobald ein Feld gespeichert ist, können Sie den Datentyp nicht ändern, abgesehen von der Konvertierung von Feldern mit automatischer Nummerierung.|

Sie können auch weitere Optionen abhängig von der Auswahl von **Datentyp** festlegen.

## <a name="field-data-types"></a>Felddatentypen

Es gibt zahlreiche unterschiedlichen Arten Felder, aber Sie können nur einige davon erstellen. Weitere Informationen für alle Feldtypen unter [Feldttypen und Datenfeldertypen](types-of-fields.md)

Wenn ein Feld erstellt wird gibt**Datentyp** die folgenden Optionen:

### <a name="text"></a>Text 

Standardtextfelder können bis zu 4.000 Zeichen speichern. Die Standardoption [Maximal zulässige Dauer](#max-length) wird auf einen niedrigeren Wert festgelegt, den Sie anpassen können.

|Datentyp|Beschreibung|
|--|--|
|**Text**|Ein beabsichtigte Textwert, um ein einzeiliges Textfeld anzuzeigen.|
|**Textbereich**|Ein beabsichtigte Textwert, um ein emehrzeiliges Textfeld anzuzeigen. Wenn Sie mehr als 4.000 Zeichen brauchen, verwenden Sie einen [Mehrzeiliger Text](#multi-line-field) Datentyp.|
|**Email**|Ein Textwert überprüft die E-Mail-Adresse und wird als mailto Link im Feld gerendert. |
|**URL**|Ein Textwert als URL validiert und gerendert als Link, um die URL zu öffnen.|
|**Tickersymbol**|Ein Textwert für ein Tickersymbol, das einen Link anzeigt, der geöffnet wird, um ein Angebot für ein Börsentickersymbol anzuzeigen. |
|**Telefonnummer**|Ein als Textwert überprüfte Telefonnummer gerendert als Link, um einen Telefonanruf einzuleiten mithilfe von Skype. |
|**Automatische Nummerierung**|Eine anpassbare Kombination von Zahlen und Buchstaben, die automatisch von Server generiert wird, wenn der Datensatz erstellt wird. Weitere Informationen: [Felder mit automatischer Nummerierung](autonumber-fields.md). |

#### <a name="max-length"></a> Max. Länge 

Felder, die Text speichern, haben ein absolutes Maximum, abhängig vom Typ. Die **Maximal Länge** von Optionen legt einen Werst fest, der niedriger als die maximal bestimmte der Umgebung ist. Sie können dieses Maximum erhöhen, aber Sie sollten es nicht senken, wenn Sie Daten im System haben, die den niedrigeren Wert übersteigen.

### <a name="whole-number"></a>Ganze Zahl

Diese Felder speichern Daten als Zahlen aber enthalten andere Darstellungs- und Überprüfungsoptionen.

|Datentyp|Beschreibung|
|--|--|
|**Ganze Zahl**|Ein Zahlenwert dargestellt in einem Textfeld.|
|**Dauer**|Ein Zahlenwert dargestellt als Dropdownliste, die Zeitintervalle enthält. Ein Benutzer kann einen Wert in der Liste auswählen oder einen ganzzahligen Wert eingeben, der die Anzahl von Minuten darstellt. Die Dauer muss im folgenden Format eingegeben werden: "x Minuten", "x Stunden" oder "x Tage". Stunden und Tagen können auch mit Dezimalstellen eingegeben werden, z. B. "x,x Stunden" oder "x,x Tage". Die Werte müssen in Minuten eingegeben werden. Unterminütige Werte werden auf die nächste Minute gerundet.|
|**Zeitzone**|Ein Zahlenwert dargestellt als Dropdownliste, die Zeitzonen enthält.|
|**Sprache**|Ein Zahlenwert als Dropdownliste, die eine Liste von Sprachen enthält, die für die Organisation aktiviert sind. Wenn keine anderen Sprachen aktiviert sind, ist die einzige Option die Ausgangssprache. Der gespeicherte Wert ist der Locale Identifier (LCID)-Wert für die Sprache.|


### <a name="date-time"></a>Datum/Uhrzeit

Verwenden Sie diese Felder, um Zeitwerte zu speichern. Sie können Werte so früh wie 1/1/1753 12:00 AM speichern.

|Datentyp|Beschreibung|
|--|--|
|**Datum und Uhrzeit**|Geben Sie ein Datum und einen Wert ein.|
|**Nur Datum**|Ein Datums- und Uhrzeitwert, der nur ein Datum anzeigt. Der Zeitwert wird gespeichert als 12:00 morgens (00:00: 00) im System.|

Sie können bestimmte **Verhalten** für Datum-Zeit-Fenster unter **Erweiterte Optionen** festlegen.

- **Ortszeit Benutzer** : Zeigt die Werte an, die in der aktuellen lokalen Zeitzone des Benutzers umgewandelt werden. Dies ist Standardeinstellung für dieses neue Feld.
- **Nur Datum**: Dieses Verhalten ist für den Typ **Nur Datum** verfügbar. Zeigt Werte ohne Zeitzonenkonvertierung an. Verwenden Sie diese Option für Daten wie Geburtstage und Jahrestage.
- **Zeitzonen unabhängig**: Zeigt Werte ohne Zeitzonenkonvertierung an.

Weitere Informationen: [Verhalten und Format des Datums- und Uhrzeitfelds](behavior-format-date-time-field.md)

### <a name="other-data-types"></a>Andere Datentypen

|Datentyp|Beschreibung|
|--|--|
|**Währung**|Ein Geldbetrag für die Währung für die Umgebung konfiguriert. Sie können eine Präzisionsebene angeben, die Präzision auf einer bestimmten Währung basieren oder eine von der Organisation genutzte einzelne Standardpräzision verwenden. Mehr Informationen [Währungsfelder verwenden](types-of-fields.md#using-currency-fields)|
|**Dezimalzahl**| Ein Dezimalwert mit bis zu 10 Dezimalpräzisionspunkten. Weitere Informationen: [Mithilfe des richtigen Typ der Anzahl](types-of-fields.md#using-the-right-type-of-number)|
|**Gleitkommazahl**|Ein fließender Dezimalwert mit bis zu 5 Dezimalpräzisionspunkten. Weitere Informationen: [Mithilfe des richtigen Typ der Anzahl](types-of-fields.md#using-the-right-type-of-number)|
|**Bild**|Zeigt ein einzelnes Bild pro Datensatz in der Anwendung an. Jede Entität kann über ein Bildfeld verfügen. Der **Name** den Sie eingeben, wenn ein Bildfeld ignoriert wird. Bildfelder werden immer 'EntityImage' genannt.|
|**Mehrfachauswahl-Optionssatz**|Zeigt eine Liste von Optionen an, in der mehr als eine ausgewählt werden kann.|
|<a name="multi-line-field"></a>**Mehrzeiliger Text**|Ein beabsichtigte Textwert, um ein emehrzeiliges Textfeld anzuzeigen. Beschränkt auf 1.048.576 Zeichen. Sie können eine tiefere [maximale Länge](#max-length) festlegen. |
|**Optionssatz**|Zeigt eine Liste der Optionen an, n der nur eine ausgewählt werden kann.|
|**Zwei Optionen**|Zeigt zwei Optionen an, von denen eine ausgewählt werden kann. Wählen Sie aus, welche Optionen für jede Option angezeigt werden soll. Die Standardwerte sind **Ja** und **Nein**.|

## <a name="save-new-field"></a>Neues Feld speichern

Nachdem Sie den **Anzeigename**, **Name** und **Datentyp** ausgewählt haben, können Sie **Fertig** klicken, um den Bereich **Feldeigenschaften** zu schließen. 

Sie können den Vorgang fortsetzen, um die Entität zu bearbeiten und zusätzliche Felder hinzuzufügen oder das Bearbeiten des Felds in den Entwurfsstatus zurückversetzen und fortsetzen. Die Felder werden nicht erstellt, bis Sie **Entität speichern** klicken, sodass alle Änderungen für die Entität gespeichert werden.

![Speichern der Entitäts-Schaltfläche](media/save-entity-button.png)

Sie können auch **Verwerfen** klicken, um die Änderungen zu verwerfen, die Sie ausgeführt haben.
 
## <a name="edit-a-field"></a>Bearbeiten eines Felds

Während dem Anzeigen von Feldern klicken Sie auf das Feld, das Sie bearbeiten möchten. Sie können die Angaben zu **Anzeigename** ändern, aber Sie können **Name** und **Datentyp** nicht ändern, falls Sie Änderungen an der Entität gespeichert haben, die dem Feld hinzugefügt werden.

### <a name="general-properties"></a>Allgemeine Eigenschaften
Jedes Feld hat folgende Feldeigenschaften, die Sie ändern können:

|Eigenschaft|Beschreibung|
|--|--|
|**Erforderlich**|Wenn dies ausgewählt ist, kann der Datensatz nicht ohne Daten in diesem Feld gespeichert werden.|
|**Durchsuchbar**|Legen Sie das auf Nein für Felder für die Entität fest, die Sie nicht verwenden.  Wenn ein Feld durchsuchbar ist, wird es in der **erweiterten Suche** angezeigt und ist verfügbar, wenn Ansichten angepasst werden. Durch die Einstellung auf Nein wird die Anzahl von Optionen reduziert, die den Benutzern angezeigt werden, wenn sie die erweiterte Suche verwenden.|
|**Beschreibung**|Gesucht in **Erweiterte Optionen**. Geben Sie Instruktionen für den Benutzer ein, um was es sich beim Feld handelt. Diese Beschreibung erscheint als Quickinfo für den Benutzer in Modell-angetriebenen Apps, wenn diese mit der Maus über die Beschriftung des Felds fahren.|

> [!NOTE]
> **Felder erforderlich machen**: Geben Sie acht, wenn Sie die erforderlichen Felder erstellen. Benutzer werden die Anwendung nicht nutzen, wenn sie Datensätze nicht speichern können, weil ihnen die für ein erforderliches Feld benötigten Daten fehlen. Möglicherweise geben sie dann einfach falsche Daten ein, nur, um weiterarbeiten zu können.
>
>**Anforderungen dynamisch festlegen**: In Modell-angetriebenen Apps können Sie Geschäftsregeln oder Formularskripts verwenden, um die Erforderlichkeitsstufe zu ändern, wenn sich die Daten in dem Datensatz ändern. Weitere Informationen: [Erstellen von Geschäftsregeln und Empfehlungen zur Anwendung einer Logik in einem Formular](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)
>
>**Verfügbarkeit der erweiterten Suche**: Die erweiterte Suche ist nur für Modell-angetriebene Apps mithilfe des Webclients derzeit verfügbar. Die erweiterte Suche ist zurzeit in Einheitlichen Oberflächen Clients nicht verfügbar.

## <a name="calculated-or-rollup"></a>Berechnet oder Rollup

Sie können ein benutzerdefiniertes Feld als **berechnet** oder als **Rollup**-Feld festlegen. Felder, die keine berechneten oder Rollup-Felder sind werden manchmal *einfache* Felder genannt.

### <a name="calculated"></a>Berechnet

Mit einem berechneten Feld können Sie eine Formel eingeben, um einen Wert für das Feld zuzuweisen. Diese Daten können auf berechnete Felder festgelegt werden: **Währung**, **Datum und Uhrzeit**, **Nur Datum**, **Dezimalzahl**, **Dauer**, **E-Mail**, **Sprache**, **mehrfach ausgewählter Optionssatz**, **Optionssatz**, **Text**, **Textbereich**, **Börsenkürzel**, **Zeitzone**, **Zwei Optionen**, **URL** und **Ganze Zahl**.

Weitere Informationen [Definition berechneter Felder für das Automatisieren von manuellen Berechnungen](define-calculated-fields.md)

### <a name="rollup"></a>Rollup

Mit ein Rollupfeld können Sie Aggregationsfunktionen festlegen, die regelmäßig ausgeführt werden, um einen Zahlenwert für das Feld festlegen. Diese Daten können auf ein berechnetes Feld festgelegt werden: **Währung**, **Datum und Uhrzeit**, **Nur Datum**, **Dezimalzahl**, **Dauer**, **Sprache**, **Zeitzone** und **Ganze Zahl**.

Weitere Informationen: [Definieren der Rollupfelder für die Gesamtwerte](define-rollup-fields.md)

## <a name="number-field-options"></a>Nummernfeldoptionen

Jeder Typ Zahlenfeld hat absolute minimale und maximale Werte. Sie können einen entsprechenden **Minimalen Wert** und **Maximalen Wert** in diesen absoluten Werte festlegen. Tun Sie dies, um Common Data Service die Werte für die Daten prüfen zu lassen, die Sie im Feld speichern möchten.

Für **Gleitkommazahl** und **Dezimalzahl** Datentypen können Sie einige **Dezimalstellen** angeben.


## <a name="option-set-field-options"></a>Optionssatzfeldoptionen

Felder, die einen Satz von Optionen bereitstellen, können ihren eigenen Satz von *lokalen* Optionen haben oder sich auf *globale* Optionen festlegen, die in mehreren Feldern verwendet werden können.

Verwenden eines globalen Optionssatzes ist dann von Nutzen, wenn Sie denselben Satz von Optionen für mehrere Felder erstellen möchten. Durch einen globalen Optionssatzes müssen Sie nur die Gruppe von Optionen von einem Ort verwalten. 

Wenn Sie **mehrfach ausgewählter Optionssatz** oder **Optionssatz** auswählen, ist der Datentyp der Liste eine Ansicht, die die verfügbaren globalen Optionssätze festlegt, damit Sie die Option auswählen und bereitstellen können als **Neuer Optionssatz**.

![Optionssatz-Typ wählen](media/option-set-options.png)

Wenn Sie **Neuer Optionssatz** auswählen, wird basierend darauf ein neuer globaler Optionssatz erstellt.

> [!NOTE]
> Wenn Sie die Optionen für einen  neuen globalen Optionssatz bearbeiten, sind **Anzeigename** und **Name**-Wert für den globalen Optionssatz anstelle für das Feld. Die Standardwerte entsprechen dem Feldwert, jedoch können Sie sie ändern, während Sie den globalen Optionssatz bearbeiten, sodass Sie sich vom Feld unterscheiden, das Sie gerade erstellen.

Wenn Sie einen lokalen Optionssatz erstellen möchten, müssen Sie **Weitere anzeigen** klicken und **Lokaler Optionssatz** auswählen.

![Lokaler Optionssatz](media/local-option-set.png)

> [!NOTE]
> Wenn Sie jeden Optionssatz als globalen Optionssatz in der Liste der globalen Optionssätze definieren, wächst diese Liste und könnte zum Verwalten schwierig werden. Wenn Sie wissen, dass der Datensatz von Optionen nur an einer Stelle verwendet wird, verwenden Sie einen lokalen Optionssatz.

[!INCLUDE [cc_remove-option-warning](../../includes/cc_remove-option-warning.md)]

## <a name="delete-a-field"></a>Löschen eines Felds

Als Benutzer mit der Sicherheitsrolle "Systemadministrator" können Sie benutzerdefinierte Felder löschen, die nicht Teil einer verwalteten Lösung sind. Wenn Sie Felder löschen, werden alle Daten in den Feldern gelöscht. Die einzige Möglichkeit, Daten aus einem Feld wiederherzustellen, das entfernt wurde, besteht darin, die Datenbank von einem Zeitpunkt wiederherzustellen, bevor das Feld gelöscht wurde.

> [!NOTE]
> Vor dem Löschen eines benutzerdefinierten Feldes müssen Sie alle Abhängigkeiten in anderen Lösungskomponenten entfernen. 

Während dem [Anzeigen von Feldern](#view-fields) wählen Sie ein benutzerdefiniertes Feld aus, das in der Liste gelöscht werden kann und klicken auf die Schaltfläche **Befehl löschen** in der Befehlsleiste.

![Löschen eines Felds mithilfe des Portals](media/delete-field-portal.png)

Verwenden Sie den Befehl **Feld löschen**, um das Feld zu löschen. Wenn Sie das Feld gelöscht haben, müssen Sie die Änderungen an der Entität speichern.

![Speichern einer Entität, nach dem das Feld gelöscht wurde](media/delete-field-portal-save-entity.png)

> [!NOTE]
> Wenn eine Fehlermeldung angezeigt, die zu den Abhängigkeiten verknüpft ist, müssen Sie den Lösungsexplorer verwenden, um die Abhängigkeiten zu ermitteln. Weitere Informationen: [Feldabhängigkeiten überprüfen](create-edit-field-solution-explorer.md#check-field-dependencies)

## <a name="ime-mode"></a>IME-Modus

Alle Felder, die direkte Texteingabe ermöglichen, haben einen IME-Modus. Der Eingabemethoden-Editor (IME) wird für ostasiatische Sprachen wie Japanisch verwendet. IMEs ermöglichen Benutzern die Eingabe von Tausenden von ostasiatischen Schriftzeichen über eine normale Tastatur mit 101 Tasten.



### <a name="see-also"></a>Siehe auch  
[Erstellen und Bearbeiten von Feldern für Common Data Service](create-edit-fields.md)<br />
[Erstellen und Bearbeiten von Feldern für Common Data Service mithilfe des Power Apps-Projektmappen-Explorers](create-edit-field-solution-explorer.md)<br />
[Feldtypen und Felddatentypen](types-of-fields.md)<br />
[Definition berechneter Felder für das Automatisieren von manuellen Berechnungen](define-calculated-fields.md)<br />
[Definition von Rollupfeldern, die Werte aggregieren](define-rollup-fields.md)<br />
[ Verhalten und Format des Datums- und Uhrzeitfelds.](behavior-format-date-time-field.md)
