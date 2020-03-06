---
title: Erstellen und Bearbeiten von Feldern für Common Data Service über das powerapps-Portal | MicrosoftDocs
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
ms.openlocfilehash: c8788aea002942bae7828411cec298592ea6e872
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404159"
---
# <a name="create-and-edit-fields-for-common-data-service-using-power-apps-portal"></a>Erstellen und Bearbeiten von Feldern für Common Data Service über das powerapps-Portal

Das [powerapps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) bietet eine einfache Möglichkeit zum Erstellen und Bearbeiten von Entitäts Feldern mit dem Common Data Service.

Das Portal ermöglicht das Konfigurieren der am häufigsten verwendeten Optionen, aber bestimmte Optionen können nur mit dem Projektmappen-Explorer festgelegt werden. <br />Weitere Informationen: 
- [Erstellen und Bearbeiten von Feldern für Common Data Service](create-edit-fields.md)
- [Erstellen und Bearbeiten von Feldern für Common Data Service mithilfe des Projektmappen-Explorers](create-edit-field-solution-explorer.md)

## <a name="view-fields"></a>Felder anzeigen

1. Wählen Sie im [powerapps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)-Portal **Daten** > **Entitäten** aus, und wählen Sie die Entität aus, die die Felder enthält, die Sie anzeigen möchten.
2. Wenn die Registerkarte **Felder** ausgewählt ist, können Sie die folgenden Sichten auswählen: 

 |Anzeigen|Beschreibung|
 |--|--|
 |**Allen**| Zeigt alle Felder für die Entität an.|
 |**Ge**| Zeigt nur verwaltete Felder und Standard Felder für die Entität an.|
 |**Zollunion**|Zeigt nur benutzerdefinierte Felder für die Entität an.|
 |**Vorgegebene**|Zeigt nur die Standard Felder für die Entität an.|
<!-- TODO: What is the actual difference between All and Default? -->

## <a name="create-a-field"></a>Ein Feld erstellen

Klicken Sie beim Anzeigen der Felder in der Befehlsleiste auf **Feld hinzufügen** , um den **Bereich Feldeigenschaften** anzuzeigen.

![Feldeigenschaften](media/field-properties.png)

Anfänglich sind nur drei Feldeigenschaften verfügbar:

 |Eigenschaft|Beschreibung|
 |--|--|
 |**Anzeigename**|Der Text, der für das Feld in der Benutzeroberfläche angezeigt werden soll.|
 |**Name**|Der eindeutige Name in Ihrer Umgebung. Basierend auf dem anzeigen Amen, den Sie eingegeben haben, wird ein Name für Sie generiert, aber Sie können ihn vor dem Speichern bearbeiten. Nachdem ein Feld erstellt wurde, kann der Name nicht mehr geändert werden, da in Ihren Anwendungen oder Code darauf verwiesen werden kann. Der Name verfügt über das Anpassungs Präfix für den **Common Data Service Standard Herausgeber** , der ihm vorangestellt wird.|
 |**Datentyp**|Steuert, wie Werte gespeichert werden und wie Sie in einigen Anwendungen formatiert werden. Nachdem ein Feld gespeichert wurde, können Sie den Datentyp nicht mehr ändern, mit Ausnahme von Textfeldern in automatische Umber Felder.|
 |**Erforderlich**| Ein Datensatz kann in diesem Feld nicht ohne Daten gespeichert werden. |
 |**Durchsuchbaren**| Dieses Feld wird unter Erweiterte Suche angezeigt und ist verfügbar, wenn Ansichten angepasst werden. |
 |**Berechnetes oder Rollup**| Verwenden Sie, um manuelle Berechnungen zu automatisieren. Verwenden Sie Werte, Datumsangaben oder Text.|
 |**Erweiterte Optionen**| Fügen Sie eine Beschreibung hinzu, und geben Sie eine maximale Länge und einen IME-Modus für das Feld an.

Sie können zusätzliche Optionen abhängig von der Auswahl des **Datentyps**festlegen.

## <a name="field-data-types"></a>Feld Datentypen

Es gibt viele verschiedene Arten von Feldern, aber Sie können nur einige davon erstellen. Weitere Informationen zu allen Typen von Feldern finden Sie unter [Typen von Feldern und Feld Datentypen](types-of-fields.md).

Wenn Sie ein Feld erstellen, bietet der **Datentyp** die folgenden Optionen:

### <a name="text"></a>Text 

Standard Textfelder können bis zu 4.000 Zeichen speichern. Die Option [maximale Standardlänge](#max-length) ist auf einen niedrigeren Wert festgelegt, den Sie anpassen können.

|Datentyp|Beschreibung|
|--|--|
|**Text**|Ein Textwert, der in einem einzeiligen Textfeld angezeigt werden soll.|
|**Text Bereich**|Ein Textwert, der in einem mehrzeiligen Textfeld angezeigt werden soll. Wenn Sie mehr als 4.000 Zeichen benötigen, verwenden Sie einen [mehrzeiligen Text](#multi-line-field) Datentyp.|
|**Email**|Ein Textwert, der als e-Mail-Adresse überprüft und als mailto-Link im Feld gerendert wird. |
|**URL**|Ein Textwert, der als URL validiert und als Link zum Öffnen der URL gerendert wird.|
|**Ticker-Symbol**|Ein Textwert für ein Ticker-Symbol, das einen Link anzeigt, der zum Anzeigen eines Angebots für das Aktien Ticker Symbol geöffnet wird. |
|**Smartphone**|Ein Textwert, der als Link zum Initiieren eines Telefonanrufs mithilfe von Skype überprüft wird. |
|**AutoNumber**|Eine anpassbare Kombination aus Zahlen und Buchstaben, die automatisch vom Server generiert wird, wenn der Datensatz erstellt wird. Weitere Informationen: [autonome Felder](autonumber-fields.md) |

#### <a name="max-length"></a>Maximale Länge

Felder, in denen Text gespeichert ist, haben je nach Typ einen absoluten Höchstwert. Die Option **Max. Länge** legt einen niedrigeren Wert als den für Ihre Umgebung spezifischen maximalen Wert fest. Sie können diese maximale Länge erhöhen, Sie sollten Sie jedoch nicht verringern, wenn Sie über Daten im System verfügen, die den niedrigeren Wert überschreiten.

### <a name="whole-number"></a>Ganze Zahl

In diesen Feldern werden Daten als Zahl gespeichert, aber es sind unterschiedliche Präsentations-und Validierungs Optionen enthalten.

|Datentyp|Beschreibung|
|--|--|
|**Ganze Zahl**|Ein Zahlenwert, der in einem Textfeld angezeigt wird.|
|**Auf**|Ein Zahlenwert, der als Dropdown Liste angezeigt wird, die Zeitintervalle enthält. Ein Benutzer kann einen Wert aus der Liste auswählen oder einen Ganzzahlwert eingeben, der die Anzahl von Minuten darstellt. Die Dauer muss im folgenden Format eingegeben werden: "x Minutes", "x Hours" oder "x Days". Stunden und Tage können auch mithilfe von Dezimalstellen eingegeben werden, z. b. "x. x Stunden" oder "x. x Tage". Die eingegebenen Werte müssen in Minuten ausgedrückt werden, und die Werte der untergeordneten Minute werden auf die nächste Minute gerundet.|
|**Zeitzone**|Ein Zahlenwert, der als Dropdown Liste angezeigt wird, die eine Liste von Zeitzonen enthält.|
|**Sprache**|Ein Zahlenwert, der als Dropdown Liste angezeigt wird, die eine Liste von Sprachen enthält, die für die Umgebung aktiviert wurden. Wenn keine anderen Sprachen aktiviert wurden, ist die Basissprache die einzige Option. Der gespeicherte Wert ist der Gebiets Schema Bezeichner (Locale Identifier, LCID) für die Sprache.|


### <a name="date-time"></a>Datum / Uhrzeit

Verwenden Sie diese Felder, um Zeit Werte zu speichern. Sie können Werte so früh wie 1/1/1753 12:00 Uhr speichern.

|Datentyp|Beschreibung|
|--|--|
|**Datum und Uhrzeit**|Ein Datums- und Uhrzeitwert.|
|**Nur Datum**|Ein Datums-und Uhrzeitwert, der nur ein Datum anzeigt. Der Uhrzeitwert wird als 12:00 Uhr (00:00:00) im System gespeichert.|

Sie können auch ein bestimmtes **Verhalten** für Datums-/Uhrzeitfelder in den **erweiterten Optionen**festlegen.

- **Lokaler Benutzer** : zeigt Werte an, die in in der lokalen Zeitzone des aktuellen Benutzers konvertiert werden. Dies ist die Standardeinstellung für neue Felder.
- **Nur Datum**: Dieses Verhalten ist für den Typ " **nur Datum** " verfügbar. Zeigt Werte ohne Zeit Zonen Konvertierung an. Verwenden Sie dies für Daten wie Geburtstage und Jubiläen.
- **Zeit Zonen unabhängig**: zeigt Werte ohne Zeit Zonen Konvertierung an.

Weitere Informationen: [Verhalten und Format des Datums- und Uhrzeitfelds](behavior-format-date-time-field.md)

### <a name="other-data-types"></a>Andere Datentypen

|Datentyp|Beschreibung|
|--|--|
|**Währung**|Ein Geld Wert für alle Währungen, die für die Umgebung konfiguriert sind. Sie können einen Genauigkeits Grad festlegen oder festlegen, dass die Genauigkeit auf eine bestimmte Währung oder eine einzelne von der Organisation verwendete Standardgenauigkeit basieren soll. Weitere Informationen: [Verwenden von Währungs Feldern](types-of-fields.md#using-currency-fields)|
|**Dezimalzahl**| Ein Dezimalwert mit bis zu 10 Genauigkeits Punkten. Weitere Informationen: [Verwenden des richtigen Typs der Zahl](types-of-fields.md#using-the-right-type-of-number)|
|**Datei**| Zum Speichern von Binärdaten.|
|**Gleitkommazahl**|Eine Gleit Komma Zahl mit bis zu 5 Genauigkeits Punkten. Weitere Informationen: [Verwenden des richtigen Typs der Zahl](types-of-fields.md#using-the-right-type-of-number)|
|**Bild**|Zeigt ein einzelnes Bild pro Datensatz in der Anwendung an. Jede Entität kann über ein Bildfeld verfügen. Der **Name** , den Sie beim Erstellen eines Bildfelds eingeben, wird ignoriert. Bildfelder werden immer als "entityimage" bezeichnet.|
|**Nachschlagen**| Erstellt einen Verweis auf einen einzelnen Datensatz für einen einzelnen Zieldatensatz Typen.|
|**Mehrfachauswahl-Options Satz**|Zeigt eine Liste von Optionen an, in denen mehrere Optionen ausgewählt werden können.|
|<a name="multi-line-field"></a>**Mehrzeiligen Text**|Ein Textwert, der in einem mehrzeiligen Textfeld angezeigt werden soll. Auf maximal 1.048.576 Zeichen beschränkt. Sie können auch eine niedrigere [Maximale Länge](#max-length)festlegen. |
|**Optionssatz**|Zeigt eine Liste von Optionen an, in denen nur eine ausgewählt werden kann.|
|**Zwei Optionen**|Zeigt zwei Optionen an, in denen nur eine ausgewählt werden kann. Sie wählen aus, welche Bezeichnungen für die einzelnen Optionen angezeigt werden. Die Standardwerte **lauten "Yes** " und " **No**".|

## <a name="save-new-field"></a>Neues Feld Speichern

Nachdem Sie die Eigenschaften " **Anzeige Name**", " **Name** " und " **Datentyp** " festgelegt haben, können Sie auf " **durch** klicken" klicken, um den **Bereich** 

Sie können die Entität weiter bearbeiten und weitere Felder hinzufügen oder zurückkehren und die Bearbeitung dieses Felds fortsetzen. Die Felder werden erst erstellt, wenn Sie auf **Entität speichern** klicken, um alle Änderungen an der Entität zu speichern.

![Schaltfläche Entität speichern](media/save-entity-button.png)

Sie können auch auf **verwerfen** klicken, um die vorgenommenen Änderungen zu verwerfen.
 
## <a name="edit-a-field"></a>Feld bearbeiten

Wählen Sie beim Anzeigen der Felder das Feld aus, das Sie bearbeiten möchten. Sie können den **anzeigen Amen** ändern, aber Sie können den **Namen** und den **Datentyp** nicht ändern, wenn Sie Änderungen an der Entität gespeichert haben, um das Feld hinzuzufügen.

### <a name="general-properties"></a>Allgemeine Eigenschaften
Jedes Feld verfügt über die folgenden Eigenschaften, die Sie ändern können:

|Eigenschaft|Beschreibung|
|--|--|
|**Erforderlich**|Wenn diese Option ausgewählt ist, kann ein Datensatz nicht ohne Daten in diesem Feld gespeichert werden.|
|**Durchsuchbaren**|Deaktivieren Sie diese Option für Felder für die Entität, die Sie nicht verwenden.  Wenn ein Feld durchsuchbar ist, wird es unter **Erweiterte Suche** angezeigt und ist verfügbar, wenn Ansichten angepasst werden. Wenn Sie diese Option deaktivieren, wird die Anzahl der Optionen verringert, die Personen mithilfe der erweiterten Suche angezeigt werden.|
|**Beschreibung**|Gefunden in **erweiterten Optionen**. Geben Sie dem Benutzeranweisungen zum Zweck des Felds. Diese Beschreibungen werden als Quick Infos für den Benutzer in Modell gesteuerten apps angezeigt, wenn Sie mit der Maus auf die Bezeichnung des Felds zeigen.|

> [!NOTE]
> **Erstellen von Feldern erforderlich**: gehen Sie vorsichtig vor, wenn Sie Felder benötigen. Personen können die Anwendung nicht verwenden, wenn Sie keine Datensätze speichern können, weil Sie nicht über die richtigen Informationen verfügen, um Sie in ein Pflichtfeld einzugeben. Personen können falsche Daten eingeben, um den Datensatz zu speichern und mit der Arbeit zu arbeiten.
>
>**Dynamische Festlegung von Anforderungen**: in Modell gesteuerten Apps können Sie Geschäftsregeln oder Formular Skripts verwenden, um die Anforderungs Ebene zu ändern, da die Daten im Datensatz geändert werden, wenn Benutzer daran arbeiten. Weitere Informationen: [Erstellen von Geschäftsregeln und Empfehlungen zum Anwenden von Logik in einem Formular](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)
>
>**Erweiterte Such Verfügbarkeit**: die erweiterte Suche ist derzeit nur für Modell gesteuerte apps verfügbar, die den WebClient verwenden. Die erweiterte Suche ist derzeit nicht in Unified Interface-Clients verfügbar.

## <a name="calculated-or-rollup"></a>Berechnetes oder Rollup

Sie können ein benutzerdefiniertes Feld als **berechnetes** Feld oder **Rollup** -Feld festlegen. Felder, bei denen es sich nicht um berechnete oder Rollup-Felder handelt, werden mitunter als *einfache* Felder bezeichnet.

### <a name="calculated"></a>Berechnet

Mit einem berechneten Feld können Sie eine Formel eingeben, um dem Feld einen Wert zuzuweisen. Diese Datentypen können auf berechnete Felder festgelegt werden: **Währung**, **Datum und Uhrzeit**, **nur Datum**, **Dezimalzahl**, **Dauer**, **e-Mail**, **Sprache**, **Mehrfachauswahl-Options Satz**, **options Satz**, **Text**, **Textbereich**, **ticksymbol**, **Zeitzone**, **zwei Optionen**, **URL**und **ganze Zahl**.

Weitere Informationen: [Definieren von berechneten Feldern zum Automatisieren manueller Berechnungen](define-calculated-fields.md)

### <a name="rollup"></a>Rollup

Mit einem Rollup-Feld können Sie Aggregations Funktionen festlegen, die regelmäßig ausgeführt werden, um einen Zahlenwert für das Feld festzulegen. Diese Datentypen können auf berechnete Felder festgelegt werden: **Währung**, **Datum und Uhrzeit**, **nur Datum**, **Dezimalzahl**, **Dauer**, **Sprache**, **Zeitzone**und **ganze Zahl**.

Weitere Informationen: [Definieren von Rollupfeldern, die Werte aggregieren](define-rollup-fields.md)

## <a name="number-field-options"></a>Zahlenfeld Optionen

Jede Art von Zahlenfeld hat absolute Mindest-und Höchstwerte. Sie können den entsprechenden **Minimal** -und **Maximalwert** in diesen absoluten Werten festlegen. Damit Common Data Service die Werte für die Daten überprüfen, die Sie im Feld speichern möchten.

Für Gleit **Komma Zahlen** -und **Dezimalzahl** Datentypen können Sie eine Anzahl von **Dezimalstellen**angeben.


## <a name="option-set-field-options"></a>Optionsfeld Optionen festlegen

Felder, die eine Reihe von Optionen bereitstellen, können Ihren eigenen Satz *lokaler* Optionen einschließen oder auf einen gemeinsamen Satz *globaler* Optionen verweisen, die von mehreren Feldern verwendet werden können.

Die Verwendung eines globalen Options Satzes ist wertvoll, wenn Sie den gleichen Satz von Optionen für mehrere Felder erstellen. Wenn eine globale Option festgelegt ist, müssen Sie den Satz von Optionen nur an einem Ort aufbewahren. 

Wenn Sie die **Option Mehrfachauswahl festlegen** oder Datentyp **festlegen** auswählen, listet der Designer eine Reihe von verfügbaren globalen Options Sätzen auf, aus denen Sie wählen können. Sie können auch die Option zum Erstellen eines **neuen Options Satzes**angeben.

![Options fest gelegungstyp auswählen](media/option-set-options.png)

Wenn Sie die **Option neu** auswählen, legen Sie das Standardverhalten fest, um einen neuen globalen Options Satz zu erstellen.

> [!NOTE]
> Beim Bearbeiten von Optionen für einen neuen globalen Options Satz sind der **Anzeige Name** und die **namens** Werte für die globale Options Menge und nicht für das Feld. Die Standardwerte entsprechen den Feldwerten, aber Sie können Sie bearbeiten, während Sie die globale Option so bearbeiten, dass Sie sich von dem Feld unterscheidet, das Sie gerade erstellen.

Wenn Sie einen lokalen Options Satz erstellen möchten, klicken Sie auf **mehr anzeigen** , und wählen Sie **lokale Options Satz**aus.

![Lokaler Options Satz](media/local-option-set.png)

> [!NOTE]
> Wenn Sie jede Option festlegen, die als globale Option festgelegt ist, wird die Liste der globalen Optionssätze vergrößert, und es kann schwierig sein, Sie zu verwalten. Wenn Sie wissen, dass der Satz von Optionen nur an einem Ort verwendet wird, verwenden Sie einen lokalen Options Satz.

[!INCLUDE [cc_remove-option-warning](../../includes/cc_remove-option-warning.md)]

## <a name="delete-a-field"></a>Löschen eines Felds

Mit der Sicherheitsrolle "Systemadministrator" können Sie alle benutzerdefinierten Felder löschen, die nicht Teil einer verwalteten Lösung sind. Wenn Sie Felder löschen, werden alle in den Feldern gespeicherte Daten gelöscht. Daten aus einem gelöschten Feld können nur durch Wiederherstellen der Datenbank von einem Zeitpunkt vor dem Löschen des Felds wiederhergestellt werden.

> [!NOTE]
> Bevor Sie ein benutzerdefiniertes Feld löschen können, müssen Sie alle Abhängigkeiten entfernen, die möglicherweise in anderen Lösungskomponenten vorhanden sind. 

Wenn Sie beim [Anzeigen von Feldern](#view-fields)ein benutzerdefiniertes Feld auswählen, das in der Liste gelöscht werden kann, wird der Befehl **Feld löschen** angezeigt, und ist aktiviert.

![Löschen eines Felds mithilfe des Portals](media/delete-field-portal.png)

Verwenden Sie den Befehl **Feld löschen** , um das Feld zu löschen. Nachdem Sie das Feld gelöscht haben, müssen Sie die Änderungen an der Entität speichern.

![Entität nach dem Löschen des Felds speichern](media/delete-field-portal-save-entity.png)

> [!NOTE]
> Wenn ein Fehler im Zusammenhang mit Abhängigkeiten auftritt, müssen Sie den Projektmappen-Explorer verwenden, um Abhängigkeiten zu erkennen. Weitere Informationen: [Überprüfen von Feld Abhängigkeiten](create-edit-field-solution-explorer.md#check-field-dependencies)

## <a name="ime-mode"></a>IME-Modus

Jedes der Felder, die eine direkte Texteingabe bereitstellen, verfügt über einen IME-Modus. Der Eingabemethoden-Editor (IME) wird für ostasiatische Sprachen wie Japanisch verwendet. Mit "IMEs" kann der Benutzer die Tausenden verschiedener Zeichen, die in ostasiatischen Sprachen geschrieben wurden, mithilfe einer Standardtastatur für 101-Tasten eingeben.



### <a name="see-also"></a>Siehe auch  
[Erstellen und Bearbeiten von Feldern für Common Data Service](create-edit-fields.md)<br />
[Erstellen und Bearbeiten von Feldern für Common Data Service mithilfe des Projektmappen-Explorers](create-edit-field-solution-explorer.md)<br />
[Typen von Feldern und Feld Datentypen](types-of-fields.md)<br />
[Definieren berechneter Felder zum Automatisieren von manuellen Berechnungen](define-calculated-fields.md)<br />
[Definieren von Rollup-Feldern, die Werte aggregieren](define-rollup-fields.md)<br />
[Verhalten und Format des Felds „Datum und Uhrzeit“](behavior-format-date-time-field.md)
