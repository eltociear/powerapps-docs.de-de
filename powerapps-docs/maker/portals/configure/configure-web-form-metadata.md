---
title: Webformular-Metadaten für ein Portal | MicrosoftDocs
description: Anweisungen, Webformular-Metadaten für ein Portal hinzuzufügen und zu konfigurieren.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 04201baf8406a6a9c9c66e1668406594334be754
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978983"
---
# <a name="configure-web-form-metadata-for-portals"></a>Konfigurieren von Webformular-Metadaten für Portale

Die Webformular-Metadaten enthalten eine zusätzliche Verhaltensänderungslogik, um die Funktionalität von Formularfeldern zu erweitern oder außer Kraft zu setzen, was anderenfalls mit den nativen Entitätsformular-Bearbeitungsfunktionen nicht möglich wäre.

## <a name="add-a-new-record"></a>Hinzufügen eines neuen Datensatzes

1. Im Webformularschritt mit Feldern, die Sie ändern möchten, gehen Sie auf **Verknüpfte** > **Metadaten** 

2. Wählen Sie **Neue Webformularmetadaten**.

## <a name="web-form-metadata-properties"></a>Eigenschaften von Webformularmetadaten

Die folgenden Attribute bieten zusätzliche Formatierungsfunktionalitäten für die Elementen in einem Formular.

| Name          | Beschreibung                                                                                                                                                                                                                                                                                                                                          |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Webformularschritt | Der dem Webformularmetadatensatz zugeordnete Webformularschritt.                                                                                                                                                                                                                                                                                      |
| Typ          | Verfügbare Optionen sind:<ul><li>Attribut</li><li>Abschnitt</li><li>Tabstopp</li></ul>Das Auswählen von "Attribut" als Typwert zeigt die entsprechenden Optionen zum Ändern der Felder im aktuellen Formular an, die für den verknüpften Schritt gerendert werden. Das Auswählen von "Abschnitt" als der Typwert zeigt die Optionen an, die zur Änderung eines Abschnitts im Formular verfügbar sind. Das Auswählen von "Registerkarte" als der Typwert zeigt die Optionen an, die zur Änderung einer Registerkarte im Formular verfügbar sind.  |

## <a name="web-form-metadata-type--attribute"></a>Webformular-Metadatentyp = Attribut

Die folgenden Eigenschaften werden angezeigt, wenn der Typ "Attribut" ausgewählt ist.


|          Name          |                                                                                                                                                    Beschreibung                                                                                                                                                     |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Logischer Name des Attributs |                                                                                                                              Der logische Name des zu ändernden Attributfelds.                                                                                                                               |
|         Bezeichnung          | Ersetzt die Standardbeschriftung, die dem Attribut in der Entität zugewiesen ist durch den hier angegebenen Text. Für jedes Language Pack, das für die Common Data Service-Umgebung installiert und aktiviert ist, ist ein Feld ist verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann. |

### <a name="control-style"></a>Steuerelementstil

Die folgenden Optionen ändern den Stil und die Funktionen des Felds eines Attributs.


|                      Name                       |                                                                                                                                                                                                                                                                                                                                       Beschreibung                                                                                                                                                                                                                                                                                                                                       |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                      Format                      | Eine der folgenden Komponenten:<ul><li>Optionssatz als vertikale Optionsfeldliste</li><li>Optionssatz als horizontale Optionsfeldliste</li><li>Einzelne Textzeile als Suchfunktion für den Geolokalisierungs-Validator (benötigt [!INCLUDE[pn-bing](../../../includes/pn-bing.md)]-Karteneinstellungen – Details dazu finden Sie hier)</li><li>Ganzzahl als konstante Summe gruppieren (Gruppenname erforderlich)</li><li>Ganzzahl als "Rangfolgenskalierung – keine Verknüpfungen" gruppieren (Gruppenname erforderlich)</li><li>Ganzzahl als "Rangfolgenskalierung – mit Verknüpfungen" gruppieren (Gruppenname erforderlich)</li><li>Multiple-Choice-Matrix (Gruppenname erforderlich)</li><li>Multiple-Choice (Gruppenname erforderlich)</li><li>Ganzzahl als Stapelrang gruppieren (Gruppenname erforderlich)</li></u> |
|                   Gruppenname                    |                                                                                                                                                                                                                                                                                                             Ein Name wird zur Gruppierung von Steuerelementen als zusammengesetztes Steuerelement verwendet.                                                                                                                                                                                                                                                                                                              |
| Zahl für erforderliche Mindestauswahl bei Multiple-Choice-Optionen |                                                                                                                                                                                                                                                                      Die erforderlichen Mindestwerte, die in einer Multiple-Choice-Frage ausgewählt werden müssen. Nur erforderlich, wenn der Steuerelementstil "Multiple-Choice" ausgewählt wird.                                                                                                                                                                                                                                                                       |
|       Zahl für erforderliche Höchstauswahl bei Multiple-Choice-Optionen        |                                                                                                                                                                                                                                                          Dies ist der maximale Anzahl von Werten, die in der Multiple-Choice-Frage ausgewählt werden dürfen. Nur erforderlich, wenn der Steuerelementstil "Multiple-Choice" ausgewählt wird.                                                                                                                                                                                                                                                          |
|           Minimale konstante Gesamtsumme            |                                                                                                                                                                                                                                                             Dies ist der erforderliche minimale Wert, der auf ein Konstantensummenantwortfeld angewandt wird. Nur erforderlich, wenn der Steuerelementstil "Ganzzahl als konstante Summe gruppieren" ausgewählt ist.                                                                                                                                                                                                                                                              |
|           Maximale konstante Gesamtsumme            |                                                                                                                                                                                                                                                 Dies ist der maximale Anzahl von Werten, die auf ein Konstantensummenantwortfeld angewendet werden können. Nur erforderlich, wenn der Steuerelementstil "Ganzzahl als konstante Summe gruppieren" ausgewählt ist.                                                                                                                                                                                                                                                 |
|           Optionssatzwerte nach dem Zufallsprinzip anordnen           |                                                                                                                                                                                                                                                                     Mit "Ja" werden die Ergebnisse für ein Optionssatzsteuerelement zufällig aufgeführt. Nur anwendbar auf Attribute, die vom Typ Optionssatz sind.                                                                                                                                                                                                                                                                     |
|                    CSS Klasse                    |                                                                                                                                                                                                                                                                                                                      Fügt einen benutzerdefiniert CSS-Klassennamen zum Steuerelement hinzu.                                                                                                                                                                                                                                                                                                                       |

### <a name="prepopulate-field"></a>Feld auffüllen

Folgende Optionen stellen einen Standardwert für Felder im Formular bereit.


|         Name         |                                                                                                                                                                                                                                                                Beschreibung                                                                                                                                                                                                                                                                 |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Standardwert ignorieren |                                                                              Ignoriert den Standardwerte des angegebenen Attributfelds. Nützlich für Attribute, die Zwei Optionen-Felder sind, die als Optionsfelder für „Ja” und „Nein” gerendert werden. Da standardmäßig automatisch der Wert „Ja” oder „Nein” zugewiesen wird, ermöglicht es diese Option, Ja/Nein-Fragen ohne eine vordefinierte Antwort anzuzeigen.                                                                               |
|         Typ         | Eine der folgenden Komponenten:<ul><li>Wert</li><li>Aktuelles Datum</li><li>Kontakt des aktuellen Benutzers</li></ul>Bei Auswahl von "Wert" ist ein Wert im Feld **Wert** erforderlich, der dem Feld zugewiesen wird, wenn das Formular geladen wird. Bei "Heutiges Datum" wird das aktuelle Datum und die Uhrzeit zum Attributfeld zugewiesen. Bei "Kontakt des aktuellen Benutzers" ist ein **Von-Attribut** erforderlich. Dieses ist ein Attribut für die Kontaktentität, das aus dem Kontaktdatensatz des aktuellen Benutzers abgerufen und für das angegebene Attributfeld festgelegt wird. |
|        Wert         |                                                                                                                                                                                                                                        Ein Wert, der dem Feld zugewiesen wird, wenn das Formular geladen wird.                                                                                                                                                                                                                                        |
|    "Von"-Attribut    |                                                                                                                                                                                             Ein Attribut in der Kontaktentität, das beim Laden des Formulars aus aus dem Datensatz des aktuellen Portalbenutzers abgerufen und dem Feld zugewiesen wird.                                                                                                                                                                                             |

### <a name="set-value-on-save"></a>Wert beim Speichern setzen

Folgende Optionen geben einen Wert an, der festgelegt wird, wenn das Formular gespeichert ist.

| Name              | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Wert beim Speichern setzen | "Ja" gibt an, dass ein Wert aus der Eingabe im Feld **Wert** dem Attribut zugewiesen werden soll. <br>**Hinweis**: Alle Attributtypen mit Ausnahme der folgenden werden unterstützt: Eindeutiger Bezeichner.       |
| Typ              | Eine der folgenden Komponenten:<ul><li>Wert</li><li>  Aktuelles Datum</li><li>Kontakt des aktuellen Benutzers</li></ul>Bei Auswahl von "Wert" ist ein Wert im Feld **Wert** erforderlich, der dem Feld zugewiesen wird, wenn das Formular geladen wird. Bei "Heutiges Datum" wird das aktuelle Datum und die Uhrzeit zum Attributfeld zugewiesen. Bei "Kontakt des aktuellen Benutzers" ist ein **Von-Attribut** erforderlich. Dieses ist ein Attribut für die Kontaktentität, das aus dem Kontaktdatensatz des aktuellen Benutzers abgerufen und für das angegebene Attributfeld festgelegt wird.  |
| Wert             | Der Wert, der dem Attribut zugewiesen wird, wenn das Formular gespeichert wird.<br>Für "Zwei Optionen"-Felder (Boolean) verwenden Sie true oder false.<br>Bei Optionssatzfelder verwenden Sie den ganzzahlige Wert für die Option.<br>Für Suchfelder (EntityReference) verwenden Sie die GUID.<br>**Hinweis**: Beachten Sie, wenn das Attribut ebenfalls im Formular vorhanden ist, wird der Wert des Benutzers mit diesem Wert überschrieben.|
| "Von"-Attribut    | Ein Attribut in der Kontaktentität, das beim Speichern des Formulars aus dem Datensatz des aktuellen Portalbenutzers abgerufen und dem Feld zugewiesen wird. |

### <a name="validation"></a>Überprüfung

Der folgende Abschnitt enthält Eigenschaften, die verschiedene Validierungsparameter und Fehlermeldungen ändern.

Für jedes Language Pack, das für die Common Data Service-Umgebung installiert und aktiviert ist, ist ein Feld ist verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann.

| Name                                        | Beschreibung                                                                                                                                                                                                                                                      |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fehlermeldung für Überprüfung                    | Überschreibt die Fehlermeldung zur Standardüberprüfung für das Feld.                                                                                                                                                                                                    |
| Regulärer Ausdruck                          | Ein regulärer Ausdruck, der zum überprüfen des Felds hinzugefügt wird.                                                                                                                                                                                                          |
| Fehlermeldung für Überprüfung regulärer Ausdrücke | Die Validierungsfehlermeldung, die angezeigt werden soll, wenn die Überprüfung durch den regulären Ausdruck fehlschlägt.                                                                                                                                                                               |
| Pflichtfeld                           | Aktivieren, um das Attributfeld als Pflichtfeld zu markieren.                                                                                                                                                                                                   |
| Fehlermeldung für Überprüfung des Pflichtfelds     | Überschreibt die standardmäßige Fehlermeldung, die angezeigt wird, wenn ein erforderliches Feld keinen Wert enthält.                                                                                                                                                                        |
| Fehlermeldung für Überprüfung des Bereichs              | Überschreibt die Standard-Bereichsüberprüfungsfehlermeldung, die angezeigt werden soll, wenn der Wert des Felds außerhalb des minimalen und maximalen Wert liegt, der im Entitätsattribut ist, das den Typ Zahl, Dezimalzahl, Gleitkommazahl oder Währung hat. |
| Fehlermeldung für Geolocation-Überprüfung         | Anwendbar, wenn das Attribut wird, eine einzelne Textzeile ist und der angegebene Stil des Steuerelements "Einzelne Textzeile als Geolocation-Suchüberprüfung" ist. In diesem Fall wir die Standard-Fehlermeldung überschrieben, wenn die Eingabeüberprüfung fehlschlägt. |
| Fehlermeldung für Überprüfung der konstanten Summe       | Anwendbar, wenn das Attribut den Typ "Ganzzahl" hat und der angegebene Stil des Steuerelements "Ganzzahl als konstante Summe gruppieren" ist. In diesem Fall wir die Standard-Fehlermeldung überschrieben, wenn die Eingabeüberprüfung fehlschlägt.                    |
| Fehlermeldung für Überprüfung der Multiple-Choice-Optionen    | Anwendbar, wenn das Attribut den Typ "Zwei Optionen" hat, und der Stil des Steuerelements "Multiple-Choice" ist. In diesem Fall überschreibt dies die Standard-Fehlermeldung, wenn die Eingabeüberprüfung fehlschlägt.                                         |
| Fehlermeldung für Überprüfung der Rangfolge – keine Verknüpfungen | Anwendbar, wenn das Attribut den Typ "Ganzzahl" hat und der Stil des Steuerelements "Ganzzahl als "Rangfolgenskalierung – keine Verknüpfungen" ist. In diesem Fall überschreibt dies die Standard-Fehlermeldung, wenn die Eingabeüberprüfung fehlschlägt.              |

### <a name="description-and-instructions"></a>Beschreibung und Anweisungen

Die folgenden Eigenschaften geben den Speicherort und den Inhalt von benutzerdefiniertem Beschreibung bzw. Anweisungen an.


|                 Name                 |                                                                                                                                                           Beschreibung                                                                                                                                                           |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Beschreibung hinzufügen            |                                                                                                                        "Ja" führt dazu, das benutzerdefinierter Text im Formular der angegebenen Position angezeigt wird.                                                                                                                        |
|               Position               |                                                                                                             Eine der folgenden Komponenten:<ul><li>Über dem Feld</li><li>Unter dem Feld</li><li>Über der Beschriftung</li></ul>                                                                                                              |
| Eigenschaft für Attributbeschreibung verwenden |                                                                                       Wählen Sie ""Ja" aus, um eine Beschreibung zu den Attributmetadaten der Entität zuzuweisen. Wählen Sie "Nein" aus, um eine benutzerdefinierte Beschreibung anzugeben. Der Standardwert ist "Nein".                                                                                       |
|             Beschreibung              | Benutzerdefinierter Text, der im Formular angezeigt werden soll. Wird verwendet, wenn "Eigenschaft für Attributbeschreibung verwenden" auf "Nein" festgelegt wird. Für jedes Language Pack, das für die Common Data Service-Umgebung installiert und aktiviert ist, ist ein Feld ist verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann. |

## <a name="web-form-metadata-type--section"></a>Web-Formular-Metadatentyp = Abschnitt

Die folgenden Eigenschaften werden angezeigt, wenn der Typ "Abschnitt" ausgewählt ist.


|     Name     |                                                                                                                                                   Beschreibung                                                                                                                                                    |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Abschnittsname |                                                                                           Der Name des Abschnitts auf dem Formular für die Entität, der geändert werden soll.                                                                                            |
|    Beschriftung     | Ersetzt die Standardbeschriftung, die dem Abschnitt in der Entität zugewiesen ist durch den hier angegebenen Text. Für jedes Language Pack, das für die Common Data Service-Umgebung installiert und aktiviert ist, ist ein Feld ist verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann. |

## <a name="web-form-metadata-type--tab"></a>Web-Formular-Metadatentyp = Registerkarte

Die folgenden Eigenschaften werden angezeigt, wenn der Typ "Registerkarte" ausgewählt ist.


|   Name   |                                                                                                                                                 Beschreibung                                                                                                                                                  |
|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Registerkartenname |                                                                                           Der Name der Registerkarte auf dem Formular für die Entität, der geändert werden soll.                                                                                            |
|  Beschriftung   | Ersetzt die Standardbeschriftung, die der Registerkarte in der Entität zugewiesen ist durch den hier angegebenen Text. Für jedes Language Pack, das für die Common Data Service-Umgebung installiert und aktiviert ist, ist ein Feld ist verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann. |

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Entitätsformulare definieren](entity-forms.md)  
[Webformulareigenschaften für Portale](web-form-properties.md)  
[Webformularschritte für Portale](web-form-steps.md)  
[Webformular-Unterrasterkonfiguration für Portale](configure-web-form-subgrid.md)  
[Notizkonfiguration für Webformular für Portale](../configure-notes.md)  

