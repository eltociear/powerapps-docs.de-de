---
title: Web Form-Metadaten für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren von Web Form-Metadaten für ein Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 63e64fe49d62be944cc040a3539b0b717f5c2f84
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552978"
---
# <a name="configure-web-form-metadata-for-portals"></a>Web Form-Metadaten für Portale konfigurieren

Die Web Form-Metadaten enthalten zusätzliche Logik zum Ändern des Verhaltens, um die Funktionalität von Formularfeldern zu vergrößern oder zu überschreiben, die andernfalls mit den systemeigenen Funktionen zum Bearbeiten von Entitäten möglich ist

## <a name="add-a-new-record"></a>Neuen Datensatz hinzufügen

1. Wechseln Sie im Webformular Schritt, der Felder enthält, die Sie ändern möchten, zu **Verwandte** > **Metadaten** . 

2. Wählen Sie **neue Web Form-Metadaten aus**.

## <a name="web-form-metadata-properties"></a>Web Form-Metadateneigenschaften

Die folgenden Attribute bieten zusätzliche Stile und Funktionen für Elemente in einem Formular.

| Name          | Beschreibung                                                                                                                                                                                                                                                                                                                                          |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Webformular Schritt | Der dem Web Form-metadatendatensatz zugeordnete Webformular Schritt.                                                                                                                                                                                                                                                                                      |
| Typ          | Folgende Optionen stehen zur Verfügung:<ul><li>Versehen</li><li>Abschnitt</li><li>Registerkarte</li></ul>Wenn Sie Attribute als Typwert auswählen, werden die entsprechenden Optionen zum Ändern der Felder auf dem aktuellen Formular angezeigt, das für den entsprechenden Schritt gerendert wird. Wenn Sie Abschnitt als Typwert auswählen, werden die verfügbaren Optionen zum Ändern eines Abschnitts im Formular angezeigt. Wenn Sie Tab als Typwert auswählen, werden die verfügbaren Optionen zum Ändern einer Registerkarte in einem Formular angezeigt.  |

## <a name="web-form-metadata-type--attribute"></a>Web Form Metadata Type = Attribute

Die folgenden Eigenschaften werden angezeigt, wenn der ausgewählte Typ ' Attribute ' ist.


|          Name          |                                                                                                                                                    Beschreibung                                                                                                                                                     |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Logischer Attribut Name |                                                                                                                              Der logische Name des Attribut Felds, das geändert werden soll.                                                                                                                               |
|         Bezeichnung          | Ersetzt die dem Attribut in der Entität zugewiesene Standard Bezeichnung durch den in dieser Eingabe angegebenen Text. Für jedes Sprachpaket, das für die Common Data Service Umgebung installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann. |

### <a name="control-style"></a>Steuerelement Stil

Die folgenden Optionen ändern den Stil und die Funktionalität des Felds eines Attributs.


|                      Name                       |                                                                                                                                                                                                                                                                                                                                       Beschreibung                                                                                                                                                                                                                                                                                                                                       |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                      Vorbild                      | Eins der folgenden Elemente:<ul><li>Option als vertikale Optionsfeld Liste festlegen</li><li>Options Satz als horizontale Optionsfeld Liste</li><li>Eine Textzeile, bei der es sich um eine Überprüfung der Geolokation-Suche handelt (erfordert [!INCLUDE[pn-bing](../../../includes/pn-bing.md)] Maps-Einstellungen-Details hier</li><li>Gesamtzahl der Gruppe als Konstante Summe (erfordert Gruppen Name)</li><li>Gruppieren ganzer Zahlen als Rangfolge keine Verknüpfungen (erfordert den Gruppennamen)</li><li>Gruppieren ganzer Zahlen als Anordnen von Rang Folge Größen zulassen (erfordert Gruppennamen)</li><li>Mehrfachauswahl Matrix (erfordert einen Gruppennamen)</li><li>Mehrfachauswahl (erfordert Gruppennamen)</li><li>Ganze Zahl als Stapel Rang gruppieren (erfordert Gruppennamen)</li></u> |
|                   Gruppen Name                    |                                                                                                                                                                                                                                                                                                             Ein Name, der zum Gruppieren von Steuerelementen als zusammengesetztes Steuerelement verwendet wird.                                                                                                                                                                                                                                                                                                              |
| Mehrere ausgewählte mindestens erforderliche Anzahl |                                                                                                                                                                                                                                                                      Dies sind die erforderlichen minimalen Werte, die in der Frage Multiple Choice ausgewählt werden. Nur erforderlich, wenn die Steuerelement Art ' Mehrfachauswahl ' ausgewählt ist.                                                                                                                                                                                                                                                                       |
|       Maximale Anzahl ausgewählter Auswahlmöglichkeiten        |                                                                                                                                                                                                                                                          Dies ist die maximale Anzahl von Werten, die in der Frage "Multiple Choice" ausgewählt werden darf. Nur erforderlich, wenn die Steuerelement Art ' Mehrfachauswahl ' ausgewählt ist.                                                                                                                                                                                                                                                          |
|           Mindestsumme der Konstanten Gesamtsumme            |                                                                                                                                                                                                                                                             Dies ist der erforderliche Mindestwert, der auf ein konstantes Summen Antwortfeld angewendet wird. Nur erforderlich, wenn die Steuerelement Formatvorlage "Gruppen ganze Zahl als Konstante Summe" ausgewählt ist.                                                                                                                                                                                                                                                              |
|           Konstante maximale Gesamtsumme            |                                                                                                                                                                                                                                                 Dies ist die maximale Anzahl von Werten, die auf ein konstantes Sum-Antwortfeld angewendet werden darf. Nur erforderlich, wenn die Steuerelement Formatvorlage "Gruppen ganze Zahl als Konstante Summe" ausgewählt ist.                                                                                                                                                                                                                                                 |
|           Zufällige Options Satz Werte           |                                                                                                                                                                                                                                                                     Durch die Angabe von "yes" werden zufällig geordnete Optionen für ein Options Satz-Steuerelement aufgelistet. Gilt nur für Attribute vom Typ "Options Satz".                                                                                                                                                                                                                                                                     |
|                    CSS-Klasse                    |                                                                                                                                                                                                                                                                                                                      Fügt dem-Steuerelement einen benutzerdefinierten CSS-Klassennamen hinzu.                                                                                                                                                                                                                                                                                                                       |

### <a name="prepopulate-field"></a>Feld vorab auffüllen

Die folgenden Optionen stellen einen Standardwert für Felder im Formular bereit.


|         Name         |                                                                                                                                                                                                                                                                Beschreibung                                                                                                                                                                                                                                                                 |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Standardwert ignorieren |                                                                              Ignoriert den Standardwert des angegebenen Attribut Felds. Nützlich für Attribute, bei denen es sich um zwei Options Felder handelt, die als Ja und ohne Options Felder gerendert werden Da der Wert Ja oder Nein standardmäßig automatisch zugewiesen wird, können Sie mit dieser Option Ja/Nein-Fragen ohne vordefinierte Antwort anzeigen.                                                                               |
|         Typ         | Eins der folgenden Elemente:<ul><li>Value</li><li>Das heutige Datum</li><li>Kontakt des aktuellen Benutzers</li></ul>Die Auswahl von Wert erfordert, dass im Feld **Wert** ein Wert angegeben wird, der dem Feld beim Laden des Formulars zugewiesen wird. Wenn Sie das heutige Datum auswählen, werden das aktuelle Datum und die aktuelle Uhrzeit dem Attribut Feld zugewiesen. Zum Auswählen des Kontakts des aktuellen Benutzers ist ein **from-Attribut** erforderlich, das ein Attribut für die Entität "Contact" ist, das aus dem Kontaktdaten Satz des aktuellen Benutzers abgerufen und für das angegebene Attribut Feld festgelegt wird. |
|        Value         |                                                                                                                                                                                                                                        Ein Wert, der dem Feld zugewiesen werden soll, wenn das Formular geladen wird.                                                                                                                                                                                                                                        |
|    From-Attribut    |                                                                                                                                                                                             Ein Attribut für die Entität "Contact", das aus dem Datensatz des aktuellen Portal Benutzers abgerufen und dem Feld zugewiesen wird, wenn das Formular geladen wird.                                                                                                                                                                                             |

### <a name="set-value-on-save"></a>Wert beim Speichern festlegen

Die folgenden Optionen geben einen Wert an, der festgelegt werden soll, wenn das Formular gespeichert wird.

| Name              | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Wert beim Speichern festlegen | Yes gibt an, dass dem Attribut ein Wert mithilfe der im Feld **Wert** bereitgestellten Eingabe zugewiesen werden soll. <br>**Hinweis**: Alle Attributtypen werden unterstützt, mit Ausnahme der folgenden: eindeutiger Bezeichner.       |
| Typ              | Eins der folgenden Elemente:<ul><li>Value</li><li>  Das heutige Datum</li><li>Kontakt des aktuellen Benutzers</li></ul>Die Auswahl von Wert erfordert, dass im Feld **Wert** ein Wert angegeben wird, der dem Feld beim Laden des Formulars zugewiesen wird. Wenn Sie das heutige Datum auswählen, werden das aktuelle Datum und die aktuelle Uhrzeit dem Attribut Feld zugewiesen. Zum Auswählen des Kontakts des aktuellen Benutzers ist ein **from-Attribut** erforderlich, das ein Attribut für die Entität "Contact" ist, das aus dem Kontaktdaten Satz des aktuellen Benutzers abgerufen und für das angegebene Attribut Feld festgelegt wird.  |
| Value             | Der dem Attribut zugewiesene Wert, wenn das Formular gespeichert wird.<br>Verwenden Sie für zwei Options Felder (boolesche Felder "true" oder "false").<br>Verwenden Sie für options Satz Feld den ganzzahligen Wert für die Option.<br>Verwenden Sie für Suchfelder (EntityReference) die GUID.<br>**Hinweis**: Wenn sich das Attribut auch auf dem Formular befindet, wird der Wert des Benutzers mit diesem Wert überschrieben.|
| From-Attribut    | Ein Attribut für die Entität "Contact", das aus dem Datensatz des aktuellen Portal Benutzers abgerufen und dem Feld während der Speicherung zugewiesen wird. |

### <a name="validation"></a>Validierung

Der folgende Abschnitt enthält Eigenschaften, mit denen verschiedene Validierungs Parameter und Fehlermeldungen geändert werden.

Für jedes Sprachpaket, das für die Common Data Service Umgebung installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann.

| Name                                        | Beschreibung                                                                                                                                                                                                                                                      |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Validierungs Fehlermeldung                    | Überschreibt die standardmäßige Validierungs Fehlermeldung für das Feld.                                                                                                                                                                                                    |
| Reguläre Ausdrücke                          | Ein regulärer Ausdruck, der hinzugefügt wird, um das Feld zu validieren                                                                                                                                                                                                          |
| Validierungs Fehlermeldung für reguläre Ausdrücke | Die Validierungs Fehlermeldung, die angezeigt wird, wenn der reguläre Ausdruck überprüft wird.                                                                                                                                                                               |
| Das Feld ist erforderlich.                           | Aktivieren Sie diese Option, damit das Attribut Feld einen Wert enthalten muss.                                                                                                                                                                                                   |
| Fehlermeldung zur erforderlichen Feld Validierung     | Überschreibt die standardmäßige erforderliche Feld Fehlermeldung, wenn das Feld keinen Wert enthält.                                                                                                                                                                        |
| Bereichs Validierungs Fehlermeldung              | Überschreibt die standardmäßige Bereichs Validierungs Fehlermeldung, die angezeigt wird, wenn der Wert des Felds außerhalb der entsprechenden minimalen und maximalen Werte liegt, die für das Entitäts Attribut vom Typ ganze Zahl, Dezimalzahl, Gleit Komma Zahl oder Währung angegeben sind. |
| Fehlermeldung zur geolozierungsbestätigung         | Anwendbar, wenn es sich bei dem Attribut um eine einzelne Textzeile handelt und das angegebene Steuerelement Format eine einzelne Textzeile ist, wenn die Überprüfung der Geolokation-Lookup-Validierung fehlschlägt. |
| Fehlermeldung zur konstanten Summen Validierung       | Anwendbar, wenn es sich bei dem Attribut um einen ganzzahligen Datentyp handelt und die angegebene Steuerelement Eigenschaft als Konstante Summe eine Gruppen Ganzzahl ist, wird die Standard Fehlermeldung überschrieben, wenn die Eingabevalidierung fehlschlägt.                    |
| Mehrfachauswahl-Überprüfungs Fehlermeldung    | Anwendbar, wenn es sich bei dem Attribut um zwei Options Typen handelt und der angegebene Steuerelement Stil mehrfach ausgewählt ist, wird die Standard Fehlermeldung, die angezeigt wird, wenn die Eingabe Überprüfung fehlschlägt.                                         |
| Bestellungs Fehlermeldung "keine Verknüpfungen" | Anwendbar, wenn es sich bei dem Attribut um einen ganzzahligen Datentyp handelt und das angegebene Steuerelement Format die ganze Zahl der Gruppen als Rang Folge nicht gleich ist, dann wird die Standard Fehlermeldung, die angezeigt wird, wenn die Eingabevalidierung              |

### <a name="description-and-instructions"></a>Beschreibung und Anweisungen

Die folgenden Eigenschaften geben den Speicherort und den Inhalt benutzerdefinierter Beschreibungen oder Anweisungen an.


|                 Name                 |                                                                                                                                                           Beschreibung                                                                                                                                                           |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Beschreibung hinzufügen            |                                                                                                                        Ja führt dazu, dass benutzerdefinierter Text auf dem Formular an der angegebenen Position angezeigt wird.                                                                                                                        |
|               Position               |                                                                                                             Eins der folgenden Elemente:<ul><li>Oberhalb des Felds</li><li>Unterhalb des Felds</li><li>Oberhalb der Bezeichnung</li></ul>                                                                                                              |
| Description-Eigenschaft des Attributs verwenden |                                                                                       Wählen Sie "Ja" aus, um die Beschreibung zu verwenden, die den Attribut Metadaten für die Entität zugewiesen ist. Wählen Sie "Nein", um eine benutzerdefinierte Beschreibung bereitzustellen. Der Standardwert ist ' No '.                                                                                       |
|             Beschreibung              | Benutzerdefinierter Text, der auf dem Formular angezeigt werden soll. Wird verwendet, wenn die Description-Eigenschaft des Attributs auf "No" festgelegt ist. Für jedes Sprachpaket, das für die Common Data Service Umgebung installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann. |

## <a name="web-form-metadata-type--section"></a>Web Form Metadata Type = section

Die folgenden Eigenschaften werden angezeigt, wenn der ausgewählte Typ ' section ' ist.


|     Name     |                                                                                                                                                   Beschreibung                                                                                                                                                    |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Abschnitts Name |                                                                                           Der Name des Abschnitts im Formular der Entität, der geändert werden soll.                                                                                            |
|    Bezeichnung     | Ersetzt die Standard Bezeichnung, die dem Abschnitt der Entität zugewiesen ist, durch den in dieser Eingabe angegebenen Text. Für jedes Sprachpaket, das für die Common Data Service Umgebung installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann. |

## <a name="web-form-metadata-type--tab"></a>Web Form Metadata Type = Registerkarte

Die folgenden Eigenschaften werden angezeigt, wenn der ausgewählte Typ ' Tab ' ist.


|   Name   |                                                                                                                                                 Beschreibung                                                                                                                                                  |
|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Registerkarten Name |                                                                                           Der Name der Registerkarte im Formular der Entität, die geändert werden soll.                                                                                            |
|  Bezeichnung   | Ersetzt die Standard Bezeichnung, die der Registerkarte in der Entität zugewiesen ist, durch den in dieser Eingabe angegebenen Text. Für jedes Sprachpaket, das für die Common Data Service Umgebung installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann. |

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Portals](configure-portal.md)  
[Definieren von Entitäts Formularen](entity-forms.md)  
[Web Form-Eigenschaften für Portale](web-form-properties.md)  
[Webformular Schritte für Portale](web-form-steps.md)  
[Webformular-unter Raster Konfiguration für Portale](configure-web-form-subgrid.md)  
[Hinweise zur Konfiguration für Web Forms für Portale](../configure-notes.md)  

