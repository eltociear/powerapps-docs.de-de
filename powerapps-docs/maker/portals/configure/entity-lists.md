---
title: Hinzufügen einer Webseite zum Rendern einer Liste von Datensätzen in einem Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren von Entitätslisten zum Rendern eine Liste von Datensätzen zu einem Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 02/05/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 96c5ede672a57b6f01a87cf8aacf093db57ab234
ms.sourcegitcommit: 2d21c2c65875f97dff6d5843611d4221a4282f22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2020
ms.locfileid: "3027683"
---
# <a name="about-entity-lists"></a>Über Entitätslisten

Eine Entitätsliste ist eine datengesteuerte Konfiguration, die Ihnen die Möglichkeit gibt, eine Webseite hinzuzufügen, die eine Liste von Einträgen rendert, ohne dass ein Entwickler den Raster im Portal bearbeiten muss. Mithilfe der Entitätsliste können Sie Datensätze für die Anzeige auf Portalen verfügbar machen.

Der Raster unterstützt die Sortierung und passt die Seite an, wenn die Anzahl der Datensätze größer ist als die definierte Seitengröße. Wenn die **Webseite für die Detailansicht** definiert wurde, enthält jeder Datensatz einen Link zu der Seite und die ID des Datensatzes wird auf die Abfragezeichenfolge zusammen mit dem ID-Abfragezeichenfolgen-Parameternamen angefügt. Die Entitätsliste unterstützt auch mehrere Ansichten. Wenn mehrere Ansicht angegeben wurden, wird eine Dropdownliste gerendert, der es dem Benutzer ermöglicht, zwischen den verschiedenen Ansichten zu wechseln.

Die Daten können auch nach dem aktuellen Portalbenutzer, nach dem übergeordneten Kundenkonto des aktuellen Portalbenutzers und nach der aktuellen Portalwebseite gefiltert werden. Wenn ein Wert für die Filterbedingungen für **Portalbenutzer-Attribute** und **Firmenattribute** besteht, wird das Portal eine Dropdownliste rendern, die es dem Benutzer ermöglicht, eigene (Meine)-Daten oder die Daten des übergeordneten Kundenkontos zu sehen.

## <a name="add-an-entity-list-to-your-portal"></a>Hinzufügen einer Entitätsliste zu Ihrem Portal

Die Entitätsliste enthält die Beziehungen zu den Webseiten und den verschiedenen Eigenschaften, um die Initialisierung der Listeneinträge innerhalb des Portals zu steuern. Die Beziehung zu der Webseite ermöglicht ein dynamisches Abrufen der Listendefinitionen für einen bestimmten Seitenknoten innerhalb der Webseite. Um vorhandene Entitätsansichten anzuzeigen oder neue Entitätsansichten zu erstellen, navigieren Sie zu **Portale** > **Entitätsliste**.

> [!Note]
> - Eine Entitätsliste muss einer Webseite für eine bestimmte Website zugeordnet sein, damit die Liste innerhalb der Site angezeigt werden kann.
> - Mehrfachauswahl-Optionssatz wird in Entitätslisten nicht unterstützt.

Die Webseite, die mit der Entitätsformular verknüpft ist, kann durch klicken auf den Link **Webseite** in den Links **Verknüpfte** Navigation ganz links im Menü angezeigt werden. Wenn Sie Ihre Entitäts-Liste erstellen, muss zuerst die Entität ausgewählt werden, für die Sie eine Liste im Portal rendern möchten. Wählen Sie anschließend eine oder mehrere modellgsteuerte App-Ansichten zum Rendern.

Wenn Sie eine Webseite erstellen oder bearbeiten, kann eine Entitätsliste im Suchfeld auf dem Webseitenformular angegeben werden. Die Seiten-Vorlage ist in der Regel, die "Seiten"vorlage, kann jedoch eine von mehreren anderen Vorlagen sein für Inhalte, da die Hauptvorlagen die notwendige Logik enthalten, um zu ermitteln, ob eine Entitäts-Liste gerendert werden soll.

## <a name="entity-list-attributes-and-relationships"></a>Attribute und Beziehungen von Entitätslisten

|              Name              |                                                                                                                                                                                        Beschreibung                                                                                                                                                                                         |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              Name              |                                                                                                                                                                Der beschreibende Name des Datensatzes. In diesem Feld ist ein Eintrag erforderlich.                                                                                                                                                                 |
|          Entitätsname           |                                                                                                                                               Der Name der Entität, aus der die Ansicht "Gespeicherte Abfrage" geladen wird. In diesem Feld ist ein Eintrag erforderlich.                                                                                                                                               |
|              Anzeigen              |                                                                          Die Ansicht(en) "Gespeicherte Abfrage" auf der Zielentität, die gerendert werden soll. In diesem Feld ist ein Eintrag erforderlich. Wenn mehrere Ansicht angegeben wurden, enthält die Webseite eine Dropdownliste, der es dem Benutzer ermöglicht, zwischen den verschiedenen Ansichten zu wechseln.                                                                           |
|           Seitengröße            |                                                                                                                                            Ein ganzzahliger Wert, der die Anzahl der Datensätze pro Seite angibt. In diesem Feld ist ein Eintrag erforderlich. Standard: 10                                                                                                                                             |
|   Webseite für die Detailansicht    |                                                                                                        Eine optionale Webseite, die für jeden Datensatz verknüpft werden kann. Der Abfragezeichenfolge-Parametername für ID und die Datensatz-ID werden an die Abfragezeichenfolge der URL zu dieser Webseite angefügt.                                                                                                        |
|      Bezeichnung für Schaltfläche "Details"      |                     Der Text wird für die Schaltfläche "Detailansicht" angezeigt, wenn **Webseite für "Detailansicht"** angegeben wurde. Standard: Details anzeigen <br>**Hinweis**: Für jedes Language Pack, das für die Common Data Service-Umgebung installiert und aktiviert ist, ist ein Feld verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann.                      |
|      Webseite für Erstellung       |                                                                                                                                                             Eine optionale Webseite, die das Ziel der Schaltfläche "Erstellen" sein wird.                                                                                                                                                              |
|      Bezeichnung für Schaltfläche "Erstellen"       |                              Der Text wird für die Schaltfläche "Erstellen" angezeigt, wenn **Webseite für "Erstellen"** angegeben wurde. Standard: Erstellen <br>**Hinweis**: Für jedes Language Pack, das für die Common Data Service-Umgebung installiert und aktiviert ist, ist ein Feld verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann._                              |
| Abfragezeichenfolge-Parametername für ID |                                                                                                                                           Ein Parametername, der in der Abfragezeichenfolge der URL zur Webseite für "Detailansicht" angegeben wird. Standard: ID                                                                                                                                           |
|        Text für leere Liste         |  **Veraltet**.  Die Message wird angezeigt, wenn keine Datensätze vorhanden sind.<br>**Hinweis**: Für jedes Language Pack, das für die Common Data Service-Umgebung installiert und aktiviert ist, ist ein Feld verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann.                                                           |
|     Portalbenutzerattribut      |                                                                                      Ein optionales Suchattribut auf der primären Entität, die den Portalbenutzerdatensatz repräsentiert, entweder Kontakt oder Systembenutzer, auf den die ID des aktuellen Benutzers angewendet werden kann, um die Daten zu filtern, die in der Liste gerendert werden.                                                                                      |
|       Firmenattribut        |                                                                                       Ein optionales Suchattribut auf der primären Entität, die einen Firmendatensatz repräsentiert, dass der Wert des Kontos"Übergeordneter Kunde" des Kontakts angewendet werden kann, um die Daten zu filtern, die in der Liste gerendert werden.                                                                                       |
|       Website-Attribut        |                                                                                                          Ein optionales Suchattribut auf der primären Entität, die die Website repräsentiert, auf die die ID der aktuellen Website angewendet werden kann, um die Daten zu filtern, die in der Liste gerendert werden.                                                                                                          |
|         Suche aktiviert         | Ein optionaler boolescher Wert, der angibt, ob die Suche aktiviert werden soll. Ein Textfeld wird gerendert, um Benutzern eine Schnellsuche nach Datensätzen zu erlauben. Verwenden Sie ein Sternchen (\*) als Platzhalterzeichen, um nach Textteilen zu suchen. Die Suche fügt für jede Spalte in der Ansicht zu den vorhandenen vordefinierten Filterbedingungen "Or"-Bedingungsfiler hinzu, um die resultierenden Datensätze abzufragen und zurückzugeben. |
|    Platzhaltertext für Suche     |                                                                                                                                                      Eine optionale Zeichenfolge, die als die Beschriftung verwendet wird, die beim erstmaligen Laden im Textfeld angezeigt wird.                                                                                                                                                       |
|      QuickInfo-Text für Suche       |                                                                                                                                             Eine optionale Zeichenfolge, die als die QuickInfo verwendet wird, die angezeigt wird, wenn der Benutzer auf das Textfeld **Suche** verweist.                                                                                                                                              |
|                                |                                                                                                                                                                                                                                                                                                                                                                                            |

## <a name="add-custom-javascript"></a>Hinzufügen von benutzerdefiniertem JavaScript

Die Registerkarte "Optionen" im Formular enthält einen Textbereich, in den Sie benutzerdefiniertes [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] eingeben können. Wenn Ihre Seite eine jQuery-Bibliothek enthält, können Sie diese hier auch verwenden. Der Skriptsatz wird unten zur Webseite hinzugefügt, direkt vor dem Tag zum Schließen der Seite.

![Benutzerdefiniertes JavaScript-Beispiel](../media/custom-javascript-example.png "Benutzerdefiniertes JavaScript-Beispiel")  

Die Liste ruft ihre asynchron ab, und wenn sie abgeschlossen ist, löst sie ein Ereignis `loaded` aus, nach dem Ihr benutzerdefiniertes [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] suchen kann und die Elemente im Raster bearbeiten kann. Der folgende Code ist ein triviales Beispiel:
```
$(document).ready(function (){
$(".entitylist.entity-grid").on("loaded", function () {
$(this).children(".view-grid").find("tr").each(function (){
// do something with each row
$(this).css("background-color", "yellow");
});
});
}); 
```

Suchen Sie ein bestimmtes Attributfeld und rufen Sie dessen Wert ab, um das Rendering des Werts möglicherweise zu ändern. Der folgende Code ruft jede Tabellenzelle ab, die den Wert des Attributs `accountnumber` enthält. Ersetzen Sie `accountnumber` durch ein Attribut, das für Ihre Entität und Ansicht geeignet ist.
```
$(document).ready(function (){
   $(".entitylist.entity-grid").on("loaded", function () {
      $(this).children(".view-grid").find("td[data-attribute='accountnumber']").each(function (i, e){
         var value = $(this).data(value);
         // now that you have the value you can do something to the value
      });
   });
});
```
## <a name="entity-list-configuration"></a>Konfiguration der Entitätsliste

Sie können Aktionen für Datensätze in einer Entitätsliste (Erstellen, Bearbeiten, Deaktivieren usw.) aktivieren und konfigurieren. Es ist auch möglich, Standardbeschriftungen, Größen und andere Attribute zu überschrieben, sodass die Entitätsliste genau wie gewünscht angezeigt wird.

Diese Einstellungen befinden sich im Konfigurationsabschnitt des Entitätslistenformulars. Standardmäßig werden nur **Grundlegende Einstellungen** angezeigt. Wählen Sie **Erweiterte Einstellungen** aus, um weitere Einstellungen anzuzeigen.

![Erstellen einer Entitätsliste](../media/configure-entitylist.png "Erstellen einer Entitätsliste")  

**Attribute**

|Name                   |Beschreibung|
|---------------------------|-----------|
|**Grundlegende Einstellungen**         |   |
| Aktionen anzeigen              |Ermöglicht Ihnen, Aktionsschaltflächen für Aktionen hinzuzufügen, die für den Entitätssatz anwendbar sind und über dem Raster angezeigt werden. Die folgenden Aktionen sind verfügbar: <ul><li>Erstellen</li> <li>Herunterladen</li></ul> Durch Auswahl einer dieser Optionen wird ein Konfigurationsbereich für diese Aktion angezeigt.|
| Elementaktionen             |Ermöglicht Ihnen, Aktionsschaltflächen für Aktionen hinzuzufügen, die für einen einzelnen Datensatz anwendbar sind und in jeder Zeile im Raster angezeigt werden, wenn das entsprechende Recht von Entitätsberechtigungen erteilt wurde. Die allgemein verfügbaren Aktionen sind:<ul><li>Details</li><li>Bearbeiten</li><li>Löschen</li><li>Workflow</li><li>Aktivieren</li><li>Deaktivieren</li></ul> Durch Auswahl einer dieser Optionen wird ein Konfigurationsbereich für diese Aktion angezeigt. Weitere Informationen für jede Aktion finden Sie unten. Außerdem haben bestimmte Entitäten spezielle Aktionen, die für sie auf einer Pro-Entitätsgrundlage verfügbar sind:<ul><li>Wert der Verkaufschance berechnen (Verkaufschance)</li><li>Anfrageaktion abbrechen (Vorfall)</li><li>Anfrageaktion (Vorfall) schließen (abschließen)</li><li>Angebot in einen Auftrag umwandeln (Angebot)</li><li>Angebot in eine Rechnung umwandeln (Vertriebsauftrag)</li><li>Angebot aus Verkaufschance generieren (Verkaufschance)</li><li>Verkaufschancenaktion verlieren (Verkaufschance)</li><li>Verkaufschancenaktion gewinnen (Verkaufschance)</li><li>Anfrageaktion erneut öffnen (Vorfall)</li><li>Verkaufschance zurückstellen (Verkaufschance)</li></ul>|
| Spaltenattribute überschreiben|Ermöglicht das Überschreiben von Anzeigeeinstellungen für die einzelnen Spalten im Raster.<ul><li>Attribut: Der logische Name der Spalte, die Sie überschreiben möchten.</li><li>Anzeigename: Neuer Spaltentitel zum Überschreiben der Standardwerte</li><li>Breite: Breite (in Prozent oder Pixel) der Spalte zum Überschreiben der Standardwerte. Vergleiche: Stil der Rasterspaltenbreite</li></ul> Zum Überschreiben von Einstellungen einer Spalte klicken Sie auf **+ Spalte** und geben Sie die Informationen ein.|
|**Erweiterte Einstellungen**      |  |
| Laden von Meldungen           |Überschreibt die Standard-HTML-Nachricht, die angezeigt wird, während das Raster lädt.|
| Fehlermeldung             |Überschreibt die Standard-HTML-Nachricht, die angezeigt wird, wenn ein Fehler auftritt, während das Raster lädt.|
| Meldung vom Typ \"Zugriff verweigert\"     |Überschreibt die Standard-HTML-Meldung, die angezeigt wird, wenn ein Benutzer keine ausreichenden Entitätsberechtigungen besitzt, um dieEntitätsliste anzuzeigen.|
| Leere Meldung             |Überschreibt die HTML-Meldung, die angezeigt wird, wenn das Raster keine Daten enthält.|
| Dialog \"Detailformular\"       |Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Details-Aktion aktiviert.|
| Dialog \"Formular bearbeiten\"          |Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Bearbeiten-Aktion aktiviert.|
| Dialog \"Formular erstellen\"        |Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Erstellen-Aktion aktiviert.|
| Dialog \"Löschen\"             |Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Löschen-Aktion aktiviert.|
| Fehlerdialog              |Steuert die Einstellungen für das Dialog, das angezeigt wird, wenn ein Fehler bei einer Aktion auftritt.|
| CSS Klasse                 |Geben Sie eine CSS-Klasse oder Klassen an, die für das HTML-Element angewendet werden, das den gesamten Rasterbereich enthält, u. a. die Raster- und Aktionsschaltflächen.|
| CSS-Klasse für Raster            |Geben Sie eine CSS-Klasse oder Klassen an, die auf das HTML-Element \<table\> der Entitätsliste angewendet werden.|
| Stil der Rasterspaltenbreite   |Konfiguriert, ob **Breite**-Werte in den Überschreiben-Spaltenattributen in **Pixel** oder **Prozent** angegeben werden.|

**Allgemeine Aktionseinstellungen**

Im Allgemeinen haben Entitäts-Aktionen Einstellungen, die konfiguriert werden können. In allen Fällen hat dies den Zweck, Ihnen mehr Optionen hinsichtlich Anpassung zu bieten, und die Felder sind nicht erforderlich. Durch einfaches Hinzufügen der Aktion wird diese auf dem Portal durchgeführt, vorausgesetzt, die entsprechende Berechtigung wurde von den Entitätsberechtigungen gewährt.

Im Allgemeinen können Sie das entsprechende Dialogfeld für jede Aktion konfigurieren, das nur angezeigt wird, wenn Sie die Option **Bestätigung erforderlich** auswählen.


| Name                   | Beschreibung                                                                                                                                                                                                                   |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**         |                                                                                                                                                                                                                               |
| Bestätigung erforderlich? | Legt fest, ob eine Bestätigung den Benutzer auffordert zu bestätigen, wenn auf die Aktion geklickt wird.                                                                                                                                 |
| **Erweiterte Einstellungen**      |                                                                                                                                                                                                                               |
| Bestätigung           | Überschreibt die Bestätigungs-HTML-Nachricht an, die angezeigt wird, wenn der Benutzer die Aktion aktiviert.                                                                                                                                         |
| Schaltflächenbezeichnung           | Überschreibt die HTML-Beschriftung für diese Aktion, die in der Entitäslistenzeile angezeigt wird.                                                                                                                                                    |
| Schaltfläche \"QuickInfo\"         | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion, die in der Entitätslistezeile angezeigt wird, zeigt.                                                                                           |
| CSS-Klasse für Schaltfläche       | Fügt eine CSS-Klasse zur Schaltfläche hinzu.                                                                                                                                                      |
| Umleiten zu Webseite    | Einige Aktionen (nicht alle) ermöglichen eine Umleitung nach Abschluss der Aktion. In hohem Maße empfohlen für den Löschvorgang, optional in den meisten sonstigen Fällen, Sie können eine Webseite auswählen, an die weitergeleitet wird, wenn die Aktion abgeschlossen ist. |
| Umleitungs-URL           | Eine Alternative zur **Umleiten zu Webseite**-Option&mdash;ermöglicht das Umleiten an eine bestimmte URL.                                                                                                                                   |

**Einstellungen für das Dialogfeld "Allgemein" (erweitert)**

|**Name**                 |**Beschreibung**                                                                                                                         |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Position                    | Überschreibt das HTML, das in der Titelleiste des Dialogfelds angezeigt wird.|                                                                         
| Text der primären Schaltfläche      | Überschreibt das HTML, das in der primären Schaltfläche (Löschen) des Dialogfelds angezeigt wird.                                                         |
| Schaltflächentext schließen        | Überschreibt das HTML, das in der primären Schließen-Schaltfläche (Abbrechen) des Dialogfelds angezeigt wird.                                                           |
| Text für Screenreader-Schaltfläche \"Verwerfen\"   | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche "Verwerfen" des Dialogfelds zugeordnet ist.                                                           |
| Größe                     | Gibt die Größe des "Löschen"-Dialogfelds an. Die Optionen sind "Standard", "Groß" und "Klein". Die Standardgröße ist Standard. |
| CSS Klasse                | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                            |
| CSS-Klasse für Titel           | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                                |
| CSS-Klasse für primäre Schaltfläche | Geben Sie eine CSS-Klasse oder Klassen an, die auf die primäre Schaltfläche (Löschen) des Dialogfelds angewendet werden.                                          |
| CSS-Klasse für Schaltfläche „Schließen”   | Geben Sie eine CSS-Klasse oder Klassen an, die für die primäre „Schließen”-Schaltfläche (Abbrechen) des Dialogfelds angewendet werden.                                            |

**Aktion "Erstellen"-Einstellungen**

Durch Aktivieren von **Aktion erstellen** wird eine Schaltfläche über der Entitätsliste gerendert, die, wenn darauf geklickt wird, ein Dialogfeld mit einem Entitätsformular anzeigt, über das ein Benutzer einen neuen Datensatz erstellen kann, vorausgesetzt, die Berechtigung "Erstellen" wurde von den Entitäts-Berechtigungen erteilt.

| Name               | Beschreibung                          |
|--------------------|--------------------------------------|
| **Grundlegende Einstellungen**     |                                                                                                                                                                       |
| Entitätsformular     | Gibt das Entitätsformular an, das verwendet wird, um den neuen Datensatz zu erstellen. In der Dropdown-Liste werden alle Entitätsformulare aufgeführt, die für den Entitätstyp der Entitätsliste konfiguriert wurden. <br>**Hinweis**: Wenn der Entitätstyp der Entitätsliste keine Entitätsformulare aufweist, wird eine leere Dropdown-Liste angezeigt. Ohne Angabe eines Entitätsformulars für die Aktion "Erstellen" wird diese ignoriert, und die Schaltfläche wird nicht in der Entitätsliste des Unterrasters gerendert. |
| **Erweiterte Einstellungen**          |                                                                                                                                                                       |
| Schaltflächenbezeichnung                                                                                                                                                                                                                 | Überschreibt die HTML-Beschriftung, die in der "Erstellen"-Aktionsschaltfläche über der Liste angezeigt wird.                                                                                        |
| Schaltfläche \"QuickInfo\"                                                                                                                                                                                                               | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die "Erstellen"-Aktionsschaltfläche verweist.                                                                         |

**Einstellungen für das "Formular erstellen"-Dialogfeld (erweitert)**

|**Name**               |**Beschreibung**                                                                                                                                 |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Laden von Meldungen        | Überschreibt die Nachricht, die angezeigt wird, während das Dialogfeld geladen wird.                                                                                  |
| Position                  | Überschreibt das HTML, das in der Titelleiste des Dialogfelds angezeigt wird.                                                                                  |
| Text für Screenreader-Schaltfläche \"Verwerfen\" | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche "Verwerfen" des Dialogfelds zugeordnet ist.                                                                   |
| Größe                   | Gibt die Größe des "Formular erstellen"-Dialogfelds an. Die Optionen sind "Standard", "Groß" und "Klein". Die Standardgröße ist Groß. |
| CSS Klasse              | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                    |
| CSS-Klasse für Titel        | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                                        |

**Einstellungen für Herunterladen-Aktion**

Das Aktivieren der **Herunterladen-Aktion** rendert eine Schaltfläche über der Entitätsliste, die, wenn darauf geklickt wird, die Daten aus der Liste in eine [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)]-Datei (.xlsx) herunterlädt.

| Name              | Beschreibung                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                    |
| Keiner              |                                                                                                    |
| **Erweiterte Einstellungen** |                                                                                                    |
| Schaltflächenbezeichnung      | Überschreibt die HTML-Beschriftung, die in der "Herunterladen"-Aktionsschaltfläche über der Entitätsliste angezeigt wird.            |
| Schaltfläche \"QuickInfo\"    | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die "Herunterladen"-Aktionsschaltfläche verweist. |

**Detail-Aktion-Einstellungen**

Durch Aktivieren von **Detail-Aktion** kann ein Benutzer ein schreibgeschütztes Entitätsformular einer ausgewählten Zeile in der Entitätsliste anzeigen.


|                 Name                  |                                                                                                                                                                                                                      Beschreibung                                                                                                                                                                                                                      |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Grundlegende Einstellungen**           |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              Entitätsformular              | Gibt das Entitätsformular an, das zum Anzeigen der Details der ausgewählten Entität verwendet wird. In der Dropdown-Liste werden alle Entitätsformulare aufgeführt, die für den Entitätstyp der Entitätsliste konfiguriert wurden. <br> **Hinweis**: Wenn der Entitätstyp der Entitätsliste keine Entitätsformulare aufweist, wird eine leere Dropdown-Liste angezeigt. Ohne Angabe eines Entitätsformulars für die Details-Aktion wird diese ignoriert, und die Schaltfläche wird nicht in der Entitätsliste gerendert. |
|         **Erweiterte Einstellungen**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Abfragezeichenfolgen-Parametername für Datensatz-ID |                                                                    Gibt den Namen des Abfragezeichenfolgenparameters an, das verwendet wird, um die Entität auszuwählen, die im ausgewählten Entitätsformular angezeigt werden soll. Dies sollte dem Wert des Abfragezeichenfolgen-Parameternamens für Datensatz-ID dieses Entitätsformulars entsprechen. Der Standardwert für dieses Feld, sowohl hier als auch in der Entitätsformularkonfiguration, ist **id**.                                                                     |
|             Schaltflächenbezeichnung              |                                                                                                                                                                                      Überschreibt die HTML-Beschriftung für diese Aktion, die in der Entitäslistenzeile angezeigt wird.                                                                                                                                                                                       |
|            Schaltfläche "QuickInfo"             |                                                                                                                                                             Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion, die in der Entitätslistezeile angezeigt wird, zeigt.                                                                                                                                                              |

**Einstellungen für das Dialogfeld "Details" (erweitert)**

|**Name**               |**Beschreibung**                                                                                                                         |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Laden von Meldungen        | Überschreibt das HTML, das angezeigt wird, während das Dialogfeld geladen wird.                                                                             |
| Position                  | Überschreibt das HTML, das in der Titelleiste des Dialogfelds angezeigt wird.                                                                         |
| Text für Screenreader-Schaltfläche \"Verwerfen\" | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche "Verwerfen" des Dialogfelds zugeordnet ist.                                                           |
| Größe                   | Gibt die Größe des "Detail"-Dialogfelds an. Die Optionen sind "Standard", "Groß" und "Klein". Die Standardgröße ist Groß. |
| CSS Klasse              | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                            |
| CSS-Klasse für Titel        | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                                |

**Einstellungen der Bearbeiten-Aktion**

Durch Aktivieren einer **Bearbeiten-Aktion** kann ein Benutzer ein bearbeitbares Entitätsformular anzeigen, das an den Datensatz der ausgewählten Zeile der Entitätsliste datengebunden ist, wenn das Recht "Schreiben" von Datensatzbasierte Sicherheit mithilfe der Entitätsberechtigungen für Portale hinzufügen gewährt wurde.


|                 Name                  |                                                                                                                                                                                                             Beschreibung                                                                                                                                                                                                             |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Grundlegende Einstellungen**           |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|              Entitätsformular              | Gibt das Entitätsformular an, das verwendet wird, um die ausgewählte Entität zu bearbeiten. In der Dropdown-Liste werden alle Entitätsformulare aufgeführt, die für den Entitätstyp der Entitätsliste konfiguriert wurden. <br> **Hinweis**: Wenn der Entitätstyp der Entitätsliste keine Entitätsformulare aufweist, wird eine leere Dropdown-Liste angezeigt. Ohne Angabe eines Entitätsformulars für die Bearbeiten-Aktion wird diese ignoriert, und die Schaltfläche wird nicht in der Entitätsliste gerendert. |
|         **Erweiterte Einstellungen**         |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Abfragezeichenfolgen-Parametername für Datensatz-ID |                                                           Gibt den Namen des Abfragezeichenfolgenparameters an, das verwendet wird, um die Entität auszuwählen, die im ausgewählten Entitätsformular bearbeitet werden soll. Dies sollte dem Wert des Abfragezeichenfolgen-Parameternamens für Datensatz-ID dieses Entitätsformulars entsprechen. Der Standardwert für dieses Feld, sowohl hier als auch in der Entitätsformularkonfiguration, ist **id**.                                                            |
|             Schaltflächenbezeichnung              |                                                                                                                                                                             Überschreibt die HTML-Beschriftung für diese Aktion, die in der Entitäslistenzeile angezeigt wird.                                                                                                                                                                              |
|            Schaltfläche \"QuickInfo\"             |                                                                                                                                                    Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion, die in der Entitätslistezeile angezeigt wird, zeigt.                                                                                                                                                     |

**Einstellungen für das Dialogfeld "Formular bearbeiten" (erweitert)**

|**Name**               |**Beschreibung**                                                                                                                   |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Laden von Meldungen        | Überschreibt das HTML, das angezeigt wird, während das Dialogfeld geladen wird.                                                                       |
| Position                  | Überschreibt das HTML, das in der Titelleiste des Dialogfelds angezeigt wird.                                                                   |
| Text für Screenreader-Schaltfläche \"Verwerfen\" | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche "Verwerfen" des Dialogfelds zugeordnet ist.                                                     |
| Größe                   | Gibt die Größe des "Bearbeiten"-Dialogfelds an. Die Optionen sind "Standard", "Groß" und "Klein". Die Standardgröße ist Groß. |
| CSS Klasse              | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                      |
| CSS-Klasse für Titel        | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                          |

**Einstellungen der Löschen-Aktion**

Bei Aktivierung der Aktion **Löschen** kann ein Benutzer den Datensatz der ausgewählten Zeile aus der Entitätsliste dauerhaft löschen, wenn das Recht "Löschen" von den Entitätsberechtigungen gewährt wurde.

| Name              | Beschreibung                                                                                                                         |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                     |
| keine              |                                                                                                                                     |
| **Erweiterte Einstellungen** |                                                                                                                                     |
| Bestätigung      | Überschreibt die Bestätigungs-HTML-Nachricht, die angezeigt wird, wenn der Benutzer die Löschen-Aktion aktiviert.                                        |
| Schaltflächenbezeichnung      | Überschreibt die HTML-Beschriftung für diese Aktion, die in der Entitäslistenzeile angezeigt wird.                                                          |
| Schaltfläche \"QuickInfo\"    | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion, die in der Entitätslistezeile angezeigt wird, zeigt. |

**Einstellungen für das Dialogfeld "Löschen" (erweitert)**

|**Name**                 |**Beschreibung**                                                                                                                         |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Position                    | Überschreibt das HTML, das in der Titelleiste des Dialogfelds angezeigt wird.                                                                         |
| Text der primären Schaltfläche      | Überschreibt das HTML, das in der primären Schaltfläche (Löschen) des Dialogfelds angezeigt wird.                                                         |
| Schaltflächentext schließen        | Überschreibt das HTML, das in der primären Schließen-Schaltfläche (Abbrechen) des Dialogfelds angezeigt wird.                                                           |
| Text für Screenreader-Schaltfläche \"Verwerfen\"   | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche "Verwerfen" des Dialogfelds zugeordnet ist.                                                           |
| Größe                     | Gibt die Größe des "Löschen"-Dialogfelds an. Die Optionen sind "Standard", "Groß" und "Klein". Die Standardgröße ist Standard. |
| CSS Klasse                | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                            |
| CSS-Klasse für Titel          | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                                |
| CSS-Klasse für primäre Schaltfläche | Geben Sie eine CSS-Klasse oder Klassen an, die auf die primäre Schaltfläche (Löschen) des Dialogfelds angewendet werden.                                          |
| CSS-Klasse für Schaltfläche „Schließen”   | Geben Sie eine CSS-Klasse oder Klassen an, die für die primäre „Schließen”-Schaltfläche (Abbrechen) des Dialogfelds angewendet werden.                                            |

**Einstellungen der Workflowaktion**

Bei der Aktivierung der **Aktion "Workflow"** kann ein Benutzer einen bedarfsgesteuerten Workflow für den Datensatz der ausgewählten Zeile aus der Entitätsliste ausführen. Sie können eine beliebige Anzahl Workflow-Aktionen zur Entitätsliste hinzufügen.///


|         Name          |                                                                                                                                                           Beschreibung                                                                                                                                                           |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Grundlegende Einstellungen**   |                                                                                                                                                                                                                                                                                                                                 |
|       Workflow        | Gibt den bedarfsgesteuerten Workflow an, der ausgeführt wird, wenn der Benutzer diese Aktion aktiviert. <br> **Hinweis**: Wenn der Entitätstyp der Entitätsliste keine Workflows aufweist, wird eine leere Dropdown-Liste angezeigt. Ohne Angabe eines Workflows für die Aktion "Workflow" wird diese ignoriert, und die Schaltfläche wird nicht in der Entitätsliste gerendert. |
|     Schaltflächenbezeichnung      |                                                                                                                 Legt die HTML-Beschriftung für diese Aktion fest, die in der Entitäslistenzeile angezeigt wird. In diesem Feld ist ein Eintrag erforderlich.                                                                                                                 |
| **Erweiterte Einstellungen** |                                                                                                                                                                                                                                                                                                                                 |
|    Schaltfläche \"QuickInfo\"     |                                                                                                  Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion, die in der Entitätslistezeile angezeigt wird, zeigt.                                                                                                   |

## <a name="securing-entity-lists"></a>Sichern von Entitätslisten

Um eine Entitätsliste zu speichern, müssen Sie die Entitätsberechtigungen für die Entität konfigurieren, für die Datensätze angezeigt werden, und auch den booleschen Wert **Entitätsberechtigungen aktivieren** auf dem Entitätslisten-Datensatz auf „true” setzen.

Das Sichern einer Entitätsliste stellt sicher, dass für beliebige Benutzer, die auf die Seite zugreifen, nur Datensätze angezeigt werden, für die Sie eine Berechtigung haben. Dies wird durch einen zusätzlichen Filter erreicht, der zu den modellgesteuerten App-Ansichten hinzugefügt wird, die über die Liste eingeblendet werden. Diese Filter filtern nur Datensätze, die für den Benutzer zugänglich sind, über die Berechtigung **Lesen**.

Außerdem beachten alle Aktionen, die für die Liste definiert sind, die entsprechenden Berechtigungen für diese Aktion auf einer Pro-Datensatz-Grundlage. D.h., wenn Sie über "Bearbeiten" für einen Datensatz verfügen, wird die Bearbeiten-Aktion für diesen Datensatz aktiviert. Dasselbe gilt für "Löschen", "Erstellen" usw. Beachten Sie, dass wenn keine Datensätzen zur Verfügung stehen, eine Nachricht mit dieser Information angezeigt wird, wenn die Liste geladen wird.

Ein guter Websiteentwurf erfordert jedoch, dass wenn ein Benutzer nicht in einer Rolle ist, die Berechtigungen für die Entität hat, (d. h. es wird niemals zu einer Situation kommen, in der sie Datensätzen sehen sollten), sie überhaupt keinen Zugriff zur Seite haben sollten. Idealerweise sollte die Seite mit Webseiten-Zugriffsberechtigungen geschützt werden.

Wenn Sie eine Entitätsliste durch Auswahl von **Entitätsberechtigungen aktivieren** gesichert haben und die Aktionen auf Datensatzebene anzeigen möchten, die für den angemeldeten Benutzer gelten, müssen Sie den Wert von der **EntityList/ShowRecordLevelActions** Website-Einstellung auf **wahr** festlegen. Zum Beispiel gibt es zwei Benutzer: Preston und Teddy. Preston hat auf Kontaktebene den gesamten Zugriff auf die Fall-Entität, während Teddy globalen Lesezugriff hat. Wenn eine Entitätsliste erstellt wird, in der alle Falldatensätze angezeigt werden, sieht Preston alle Aktionen (Anzeigen, Bearbeiten und Löschen) für die Datensätze, die mit seinem Kontakt verknüpft sind. Auf anderen Datensätzen würde er nur die Aktion **Anzeigen** sehen. Auf der anderen Seite würde Teddy nur die Aktion **Anzeigen** auf allen Datensätzen sehen.

Wenn die **EntityList/ShowRecordLevelActions** Standorteinstellung auf **falsch** eingestellt ist und die Entität mehrere Berechtigungen hat, sind alle Aktionen auf Datensatzebene sichtbar. Wenn ein Benutzer jedoch versucht, eine Aktion auszuführen, für die er nicht autorisiert ist, wird ein Fehler angezeigt.

## <a name="adding-a-view-details-page"></a>Hinzufügen einer Ansichtsdetailseite

Durch das Einstellen der Webseite für die Detailansichtssuche auf einer Webseite können die Details des Datensatzes, der im Raster aufgeführt ist, als schreibgeschützt oder bearbeitet angezeigt werden, je nach der Konfiguration des zugeordneten Formulars oder der zugeordneten Seite.

Diese Seite kann eine komplett benutzerdefinierte Seitenvorlage sein, vielleicht mit Liquid erstellt. Das häufigste Szenario ist wahrscheinlich, wenn die Detailseites eine Webseite ist, die entweder ein Entitätsformular oder ein Webformular enthält.

Die wichtige Punkt, auf den geachtet werden muss, ist, dass jeder Datensatz im Raster einen Hyperlink zur Detailseite hat, und der Link enthält einen benannten Zeichenfolgenparameter mit der ID des Datensatzes. Der Name des Abfragezeichenfolgenparameters hängt vom ID-Abfragezeichenfolgen-Parameternamen ab, der in der Entitätsliste angegeben ist. Schließlich muss noch beachtet werden, dass die Ziekdetailwebseite auch den Namen dieses Abfragezeichenfolgenparameters kennen muss, um die ID des Datensatzes anzuzeigen, der abgefragt und in den die Daten geladen werden müssen.

![Hinzufügen einer Ansichtsdetailseite](../media/add-view-details-page.png "Hinzufügen einer Ansichtsdetailseite")  

**Verwenden eines Entitätsformulars zum Anzeigen von Details**

Um ein Entitätsformular zu erstellen, sehen Sie sich die Anweisungen an, die auf der Seite [Entitätsformular](entity-forms.md) vorhanden sind.

Die Folgenden sind wichtige Einstellungen, die berücksichtigt werden müssen, um sicherzustellen, dass der Datensatz aus der Entitätsliste in das Entitätsformular geladen wird.

Der Datensatz-ID-Abfragezeichenfolgenparametername auf dem Entitätsformular muss mit dem Abfragezeichenfolgen-Parameternamen auf der Entitätsliste übereinstimmen.

Der Modus kann entweder oder Bearbeiten oder ReadOnly sein, je nach Ihren Anforderungen.

**Verwenden eines Webformulars zum Anzeigen von Details**

Die Folgenden sind wichtige Einstellungen, die berücksichtigt werden müssen, um sicherzustellen, dass der Datensatz aus der Entitätsliste in das Webformular geladen wird.

Der Primärschlüssel-Abfragezeichenfolgenparametername auf dem Webformularschritt muss mit dem Abfragezeichenfolgen-Parameternamen auf der Entitätsliste übereinstimmen.

Der Modus kann entweder oder Bearbeiten oder ReadOnly sein, je nach Ihren Anforderungen.

**Verwenden einer Detailseite für die Erstellen-Funktion**

Sie können eine benutzerdefinierte Seite, ein Entitätsformulars oder ein Webformular in der gleichen Weise für die Erstellungsfunktion verwenden. Dies stellt eine Alternative zum Definieren einer Erstellen-Aktion auf dem Formular dar. Sie können nicht eine Erstellen-Aktion *und* eine benutzerdefinierte Seiten für "Erstellen" verwenden: Das Definieren einer benutzerdefinierten Aktion hat Vorrang.

Wenn Sie eine Webseite zur Erstellen-Suche in der Entitätsliste hinzufügen und keine Erstellen-Aktion angeben, indem Sie die Konfiguration verwenden, wird eine Erstellen-Schaltfläche auf der Liste gerendert, die den Benutzern mit der benutzerdefinierten Seite verknüpft, die Sie für "Erstellen" festgelegt haben.

## <a name="entity-list-filter-configuration"></a>Konfiguration des Entitätslistenfilters

Das Hinzufügen der Möglichkeit, Datensätze auf einer Entitätsliste zu filtern, ist einfach: Aktivieren Sie lediglich die Filteroption und wählen Sie dann einen oder mehrere Filtertypen, die den Benutzern angezeigt werden. Es ist möglich, nach einem Attribut zu filtern, der mit einem beliebigen Text übereinstimmt, der vom Benutzer bereitgestellt wird, oder aus einer Reihe von Optionen auszuwählen. Sie können sogar jeden beliebigen Filtertyp entwerfen, indem Sie „Erweiterte Suche” verwenden.

**Aktivieren des Entitätslistenfilters**

Im **Metadatenfilter**-Abschnitt aktivieren Sie das Kontrollkästchen **Aktiviert**. Dadurch wird der Filterbereich zur Entitätsliste hinzugefügt, falls sie angezeigt wird. Bis Sie mindestens einen Filtertyp definiert haben, wird das Feld leer gelassen.

Sie können festlegen, wie der Filterbereich auf der Entitätsliste gerendert wird, indem Sie die Ausrichtung verwenden. Der Standard, "Horizontal", rendert den Filterbereich über der Entitätsliste. Die vertikale Ausrichtung rendert den Filterbereich als Feld links neben der Entitätsliste.

![Standard-Metadateneinstellungen](../media/metadata-filter-settings.png "Standard-Metadateneinstellungen")  

**Filtertypen**

|**Filtertyp**      |**Beschreibung**                                                                                                                                                                                                                               |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Textfilter          | Filtern Sie die Entitätsliste mithilfe des Textfelds, um übereinstimmenden Text in einem ausgewählten Attribut der betreffenden Entität zu suchen.                                                                                                                               |
| Attributfiltersatz | Filtern Sie die Entitätsliste mithilfe einer Reihe von Kontrollkästchen, von denen jedes versucht, seine Bedingung mit einem bestimmten Attribut der betreffenden Entität abzustimmen.                                                                                           |
| Suchsatz           | Filtern Sie die Entitätsliste mithilfe einer Reihe von Kontrollkästchen, von denen jedes eine Beziehung zwischen einem Datensatz für eine bestimmte Entität und einem Datensatz für eine zugehörige Entität darstellt.                                                                         |
| Bereichsfiltersatz     | Ähnlich wie der Attributfiltersatz, außer dass jedes Kontrollkästchen zwei Bedingungen und nicht nur eine darstellen kann (z. B. größer als oder gleich 0 UND weniger als 100).                                                                    |
| Dynamischer Auswahllistensatz | Ähnlich wie das Auswählen eines Auswahllistenwerts auf einem Attributfiltersatz. Der dynamische Auswahllistensatz erfordert nicht, dass Sie die Auswahllistenoptionen angeben, nach denen gefiltert werden soll. Stattdessen erstellt er eine vollständige Liste von Optionen, wenn die Entitätsliste geladen wird. |
| Dynamischer Suchsatz   | Ähnlich wie der Suchsatz. Der dynamische Suchsatz erfordert nicht, dass Sie die Suchoptionen angeben, nach denen gefiltert werden soll. Stattdessen erstellt er eine vollständige Liste von Optionen, wenn die Entitätsliste geladen wird.                                           |
| FetchXML-Filter      | Filtern Sie die Entitätsliste mithilfe einer FetchXML-Filterbedingung.                                                                                                                                                                                     |

**Textfilter**

Der Textfilter fügt ein Textfeld zum Entitätslisten-Filterbereich hinzu, der mit einem Attribut des Entitätstyps der Entitätsliste zusammenhängt. Wenn ein Benutzer den Filter anwendet, zeigt die Entitätsliste nur diese Datensätze an, deren ausgewähltes Attribut den Wert enthält.

Klicken Sie zum Hinzufügen eines Textfilters auf **+Text Filter**.

![Hinzufügen eines Textfilters](../media/add-text-filter.png "Hinzufügen eines Textfilters")  

Der Textfilter verwendet die folgenden Attribute:

|**Name**     |**Beschreibung**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Attribut    | Der Name des Entitätslistenattributs zum ausgewählten Entitätstyp der Entitätsliste, nach dem gefiltert werden soll. *Nur Attribute vom Typ "Zeichenfolge" sind für einen Textfilter gültig.*                                                                                   |
| Anzeigename | Überschreiben Sie die Beschriftung für den Filter, wenn die Entitäsliste angezeigt wird. Standardmäßig ist diese automatisch auf den Namen des ausgewählten Attributs festgelegt. |

**Attributfiltersatz**

Der Attributfiltersatz fügt eine Reihe von Optionen, nach denen die Entitätsliste gefiltert werden kann, hinzu. Diese sind gebunden an ein einzelnes Attribut des ausgewählten Entitätstyps der Entitätsliste. Wenn ein Benutzer den Filter anwendet, zeigt die Entitätsliste nur diese Datensätze an, die genau mit mindestens einer der ausgewählten Optionen übereinstimmt.

![Attributfiltereinstellungen](../media/set-attribute-filter.png "Attributfiltereinstellungen")

Der Attributfiltersatz verwendet die folgenden Attribute:

|**Name**     |**Beschreibung**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Attribut    | Der Name des Entitätslistenattributs zum ausgewählten Entitätstyp der Entitätsliste, nach dem gefiltert werden soll. Nur Attribute mit folgenden Typen sind für einen Textfilter gültig: Zeichenfolge, BigInt, dezimal, doppelt, Ganzzahl, Geld, Auswahlliste, DateTime und boolesche.
|Anzeigename | Überschreiben Sie die Beschriftung für den Filter, wenn die Entitäsliste angezeigt wird. Standardmäßig ist diese automatisch auf den Namen des ausgewählten Attributs festgelegt.
| Optionen |      Eine Sammlung die Werte, nach denen gefiltert werden kann. Weitere Details finden Sie unten.                                                                              |

**Attributfiltersatzoptionen**

Ein Attributfiltersatz kann gewöhnlich eine beliebige Anzahl von Optionen haben, mit Ausnahme von Auswahllisten- und booleschen Attributen. Ein boolescher Attributfiltersatz kann nur eine oder zwei Optionen haben&mdash;eine true-Option und eine "false"-Option. Ein Auswahllisten-Attributfiltersatz kann höchstens eine Option für jeden möglichen Wert in der Auswahlliste haben.

Optionen haben die folgenden Attribute:

|**Name**     |**Beschreibung**                                                                                                                                                                                  |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operator     | Der Vergleichsoperator, der verwendet wird, um Ergebnisse zu filtern, zum Beispiel "Gleich", "Weniger als" usw. Die Liste der Operatoren für die Option hängt vom Typ des Attributs ab, der für den Filter ausgewählt ist. Beispielsweise verfügen numerische Typen ("Dezimalzahl") über Operatoren wie "Kleiner als" oder "Größer als", während die Attribute vom Typ "Zeichenfolge" Operatoren wie "Beginnt mit" oder "Enthält" verwenden. Operatoren vom Typ "Auswahlliste" und "boolesch" sind immer "Gleich".                                                                                                                                               |
| Wert        | Der tatsächliche Wert, der für diese Filterbedingung verwendet wird.                                                                                                                                                 |
| Anzeigename | Überschreibt den Anzeigenamen für diese Option im Filterfeld. Standardmäßig ist dies auf die gleichen Werte wie die Wertattribute festgelegt.                                                             |

**Suchsatz**

Der Suchsatz fügt eine Reihe von Optionen, nach denen die Entitätsliste gefiltert werden kann, hinzu. Diese sind gebunden an eine zugehörige Entität des ausgewählten Entitätstyps der Entitätsliste. Wenn ein Benutzer den Filter anwendet, zeigt die Entitätsliste nur diese Datensätze an, die genau mit mindestens einer der ausgewählten zugehörigen Datensätze übereinstimmt.

![Suchsatz](../media/lookup-set.png "Suchsatz")  

Der Suchsatz verwendet die folgenden Attribute:

|**Name**     |**Beschreibung**                                                                                                                                           |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Beziehung | Der Name der verknüpften Entität zum ausgewählten Entitätstyp der Entitätsliste, nach dem gefiltert werden soll. Nur mit Entitäten einer 1: n- oder n: n-Beziehung mit den ausgewählten Entitätstyp der Entitätsliste werden als Optionen für diesen Filtertyp angezeigt.          |
| Anzeigename | Überschreiben Sie die Beschriftung für den Filter, wenn die Entitäsliste angezeigt wird. Standardmäßig ist diese automatisch auf den Namen der ausgewählten Beziehung festgelegt. |
| Optionen      | Eine Sammlung die Werte, nach denen gefiltert werden kann. Weitere Details finden Sie unten.                                                                                 |

**Suchsatzoptionen**

Ein Suchsatz kann eine beliebige Anzahl an Optionen, wobei die einzige Beschränkung die Anzahl der verknüpften Datensätze des ausgewählten zugehörigen Typs ist.

Optionen haben die folgenden Attribute:

|**Name**     |**Beschreibung**                                                                                                                      |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------|
| Wert        | Der Datensatz des ausgewählten zugehörigen Typs, nach dem gefiltert werden soll.                                                                                |
| Anzeigename | Überschreibt den Anzeigenamen für diese Option im Filterfeld. Standardmäßig ist dies auf die gleichen Werte wie die Wertattribute festgelegt. |

**Bereichsfiltersatz**

Der Bereichsfiltersatz fügt eine Reihe von Optionen, jede mit einer oder zwei Bedingungen, zum Filterbereich hinzu. Wenn ein Benutzer den Filter anwendet, zeigt die Entitätsliste nur diese Datensätze an, die genau mit allen Bedingungen mindestens einer der ausgewählten Optionen übereinstimmt.

![Bereichsfiltereinstellungen](../media/set-range-filter.png "Bereichsfiltereinstellungen")  

Der Bereichsfiltersatz verwendet die folgenden Attribute:

|**Name**     |**Beschreibung**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Attribut    | Der Name des Entitätslistenattributs zum ausgewählten Entitätstyp der Entitätsliste, nach dem gefiltert werden soll. Nur Attribute mit folgenden Typen sind für einen Textfilter gültig: Zeichenfolge, BigInt, dezimal, doppelt, Ganzzahl, Geld, DateTime.                       |
| Anzeigename | Überschreiben Sie die Beschriftung für den Filter, wenn die Entitäsliste angezeigt wird. Standardmäßig ist diese automatisch auf den Namen des ausgewählten Attributs festgelegt. |
| Optionen      | Eine Sammlung die Werte, nach denen gefiltert werden kann. Weitere Details finden Sie unten.                                                                              |

**Bereichsfiltersatzoptionen**

Ein Bereichsfiltersatz kann eine beliebige Anzahl an Optionen haben. Jede Option erzeugt eine Filterbedingung mit einer oder zwei Unterbedingungen, die beide erfüllt sein müssen, damit die Bedingung "true" ist.

Optionen haben die folgenden Attribute:

|**Name**              |**Beschreibung**                                                                                                                                                                                |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operator 1            | Der erste Vergleichsoperator, der verwendet wird, um Ergebnisse zu filtern, zum Beispiel "Gleich" und "Weniger als". Die Liste der Operatoren für die Option hängt vom Typ des Attributs ab, der für den Filter ausgewählt ist. Beispielsweise verfügen numerische Typen ("Dezimalzahl") über Operatoren wie "Kleiner als" oder "Größer als", während die Attribute vom Typ "Zeichenfolge" Operatoren wie "Beginnt mit" oder "Enthält" verwenden. Operatoren vom Typ "Auswahlliste" und "boolesch" sind immer "Gleich".                                                                                                                                             |
| Wert 1               | Der erste Wert, der für diese Filterbedingung verwendet wird.                                                                                                                                                |
| Operator 2 (optional) | Der zweite Vergleichsoperator, der verwendet wird, um Ergebnisse zu filtern, zum Beispiel "Gleich" und "Weniger als". Die Liste der Operatoren für die Option hängt vom Typ des Attributs ab, der für den Filter ausgewählt ist. Beispielsweise verfügen numerische Typen ("Dezimalzahl") über Operatoren wie "Kleiner als" oder "Größer als", während die Attribute vom Typ "Zeichenfolge" Operatoren wie "Beginnt mit" oder "Enthält" verwenden. Operatoren vom Typ "Auswahlliste" und "boolesch" sind immer "Gleich".                                                                                                                                             |
| Wert 2 (optional)    | Der zweite Wert, der für diese Filterbedingung verwendet wird.                                                                                                                                               |
| Anzeigename          | Überschreibt den Anzeigenamen für diese Option im Filterfeld. Standardmäßig wird dies dynamisch anhand der ausgewählten Operatoren und Werte festgelegt.                                         |

**Dynamischer Auswahllistensatz**

Mit dem dynamischen Auswahllistensatz wird eine Reihe von Optionen zum Filtern hinzugefügt, die alle Werte eines angegebenen Auswahllistenfelds darstellen. Dies unterscheidet sich vom Auswählen einer Auswahlliste im Attributfiltesatz. Im Attributfiltersatz müssen Sie einen Satz von Optionen angeben, der für den Benutzer verfügbar gemacht wird, um danach zu filtern. Im dynamischen Auswahllistensatz müssen Sie nur das Auswahllistenfeld angeben und die gesamte Satz von Optionen wird automatisch bereitgestellt. Wenn Sie mehr Kontrolle benötigen, wird empfohlen, den Attributfiltersatz zu verwenden.

![Dynamische Auswahllisteneinstellungen](../media/set-dynamic-picklist.png "Dynamische Auswahllisteneinstellungen")  

Der dynamische Auswahllistensatz verwendet die folgenden Optionen:

|**Name**     |**Beschreibung**                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Attribut    | Der Name des Auswahllistenattributs zum ausgewählten Entitätstyp der Entitätsliste, nach dem gefiltert werden soll.                                                             |
| Anzeigename | Überschreiben Sie die Beschriftung für den Filter, wenn die Entitäsliste angezeigt wird. Standardmäßig ist diese automatisch auf den Namen des ausgewählten Attributs festgelegt. |

**Dynamischer Suchsatz**

Der dynamische Suchsatz fügt eine dynamische Reihe von Optionen, nach denen die Entitätsliste gefiltert werden kann, hinzu. Diese sind gebunden an eine zugehörige Entität des ausgewählten Entitätstyps der Entitätsliste. Wenn ein Benutzer den Filter anwendet, zeigt die Entitätsliste nur diese Datensätze an, die genau mit mindestens einer der ausgewählten zugehörigen Datensätze übereinstimmt.

Dies unterscheidet sich von einem Suchsatz. Im Suchen-Satz müssen Sie verknüpften Entitäten manuell angeben, nach denen gefiltert wird. Im dynamischen Suchsatz müssen Sie nur die Beziehung angeben, nach der gefiltert werden soll, und eine Liste von Optionen wird basierend auf der angegebenen Ansicht an verknüpften Entitäten generiert.

![Dynamische Sucheinstellungen](../media/set-dynamic-lookup.png "Dynamische Sucheinstellungen")  

Der dynamische Suchsatz verwendet die folgenden Optionen:

|**Name**                      |**Beschreibung**                                                                                                                                                                      |
|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Beziehung                  | Der Name der verknüpften Entität zum ausgewählten Entitätstyp der Entitätsliste, nach dem gefiltert werden soll. Nur mit Entitäten einer 1: n- oder n: n-Beziehung mit den ausgewählten Entitätstyp der Entitätsliste werden als Optionen für diesen Filtertyp angezeigt.                                     |
| Anzeigen                          | Die Ansicht (gespeicherte Abfrage), die als Quelle für die dynamische Liste der Entitäten wird, nach denen gefiltert werden soll.                                                                                              |
| Bezeichnungsspalte                  | Das Feld aus der Ansicht, die den "Namen"-Wert jeder Entität angibt.                                                                                                                    |
| Filtersuche bei Beziehung | Gibt eine Beziehung zwischen der Entität an, die das Beziehungsfeld angegeben wurden, und dem angemeldeten Benutzer. Wenn die Entität, die vom Beziehungsfeld angegeben wird, auch eine Beziehung zu einem Kontakt hat, können Sie die Liste der Filteroptionen auf diejenigen eingrenzen, die mit dem angemeldeten Benutzer verknüpft sind.  |
| Anzeigename                  | Überschreiben Sie die Beschriftung für den Filter, wenn die Entitäsliste angezeigt wird. Standardmäßig ist diese automatisch auf den Namen der ausgewählten Beziehung festgelegt.                            |

**FetchXML-Filter**

Der Bereichsfilter kann einen einfachen Textfeldfilter wie den Textfilter erstellen oder einen Satz von Optionen wie die anderen Filtertypen. Dies ermöglicht, manuell praktisch jeden Filtertyp für die Entitätsliste zu erstellen, indem FetchXML verwendet wird.

![FetchXML-Filtereinstellungen](../media/set-fetchxml-filter.png "FetchXML-Filtereinstellungen")

Der FetchXML-Filter verwendet nur ein Attribut:

|**Name** |**Beschreibung**                            |
|----------|--------------------------------------------|
| FetchXML | Die XML-Bestimmung, die den Filter darstellt. |

## <a name="entity-list-map-view"></a>Kartenansicht der Entitätsliste

Mit Entitätslisten ist es möglich, eine Kartenansicht der Daten zu aktivieren und zu konfigurieren, die von [!INCLUDE[pn-bing](../../../includes/pn-bing.md)]-Karten mit Suchfunktionen zum Suchen von Standorten in der Nähe einer Adresse betrieben wird. Wenn Sie die Datensätze mit Breiten- und Längenkoordinatenwerten ausfüllen und die erforderlichen Konfigurationsoptionen angebene, die in diesem Abschnitt aufgeführt sind, können Ihre Datensätze als Punkt auf einer Karte gerendert werden. Jeder Datensatz, der keinen Breiten- oder Längenwert hat, wird von der Suche ausgeschlossen. Beim erstmaligen Laden der Seite werden alle Datensätze innerhalb des Anfangswerts des Abstands-Wertfelds (in Meilen oder Kilometer abhängig von den angegebenen Längenmaßeinheiten) der standardmäßigen mittleren Längenkoordinaten und Breitenkoordinaten angezeigt. Die angegebene Ansicht wird ignoriert, wenn eine Kartenansicht verwendet wird, und die Abstandsabfrage wird auf den Datensatz angewendet, um die anzeigbaren Ergebnisse anzuzeigen.
>[!Note] 
>Diese Option wird in der deutschen Sovereign Cloud nicht unterstützt. Der Abschnitt zur Kartenansicht wird in dieser Umgebung nicht angezeigt.


## <a name="entity-list-calendar-view"></a>Entitätenliste (Kalenderansicht)

Die Kalenderansicht der Entitätsliste ermöglicht das Rendern einer Entitätsliste als Kalender, wobei jeder einzelne konfigurierte Datensatz als einzelnes Ereignis agiert.

Damit Datensätze mithilfe eines Kalenders angezeigt werden, müssen diese Datensätze mindestens ein Datumsfeld haben. Damit die Ereignisse genaue Start- und Endzeiten haben, müssen die entsprechenden Felder vorhanden sein usw. Angenommen diese Felder sind konfiguriert, dann wird eine Entitätslistenskalenderansicht auf dem Portal angezeigt.

## <a name="entity-list-odata-feeds"></a>Entitätslisten-OData-Feeds

Wenn diese Option aktiviert ist, kann eine Entität in einem OData-Feed veröffentlicht werden. Das OData-Protokoll ist ein Protokoll auf Anwendungsebene zum Interagieren mit Daten über RESTful-Webdienste. Daten aus diesem Feed können in einem Webbrowser angezeigt, von einer clientseitige Webanwendung belegt oder in [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)] importiert werden.

> [!Note]
> Der OData-Feed, der veröffentlicht wurde, ist anonym und verfügt über keine Berechtigungsprüfungen. Daher ist es wichtig, keine oData-Feeds für Daten zu aktivieren, die für einen anonymen Portalzugriff ungeeignet sind.

## <a name="enhanced-view-filter-for-entity-lists"></a>Verbesserte Ansichtsfilter für Entitätslisten

Sie können Entitäts-Berechtigungen verwenden, wenn Sie Datensätze in speichern möchten, aber wenn Sie einen Filter als Teil eines Satz von Filteroptionen einfach bereitstellen möchten, die für den aktuellen Portalbenutzer relevant sind, können Sie die Entitätslistenfunktion verwenden. Diese Funktionen unterstützt Filterung des aktuellen Benutzers, des übergeordneten Kontos des Benutzers oder der Website mit beliebiger Tiefe. Erstellen Sie einfach den Ansichtsfilter, entsprechend den einzelnen Kontaktdatensätze, und der Code ersetzt den zugehörigen Wert durch den tatsächlichen Wert zur Laufzeit&mdash;es ist nicht erforderlich, Werte für die Felder im Abschnitt „Filterbedingungen” zuzuweisen.

- Das Steuerelement findet alle Bedingungselemente, bei denen uitype="contact" ist, und setzt den Wert auf den tatsächlichen Wert der Kontakt-ID des aktuellen Portalbenutzers.
- Das Steuerelement findet alle Bedingungselemente, bei denen uitype="account" ist, und setzt den Wert auf den tatsächlichen Wert der übergeordneten Konto-ID des aktuellen Portalbenutzers.
- Das Steuerelement findet alle Bedingungselemente, bei denen uitype="adx_website" ist, und setzt den Wert auf den tatsächlichen Wert der Website-ID.

Beispiel "Filterkriterien anzeigen"

Das folgende Bild zeigt einen beliebigen Kontakt, der einer Filterbedingung zugewiesen ist. Dieser Kontakt ist zufällig ein Blindkontakt, dies kann jedoch ein beliebiger Kontaktdatensatz sein. Die ID dieses Datensatzes wird durch den tatsächlichen Wert der ID des Benutzers ersetzt, der die Seite anzeigt. Wenn der Benutzer nicht angemeldet ist, werden keine Datensätze zurückgegeben. Dies bietet eine größere Flexibilität beim Filtern der Daten basierend auf dem Benutzer und der Website im Kontext.

> [!NOTE]
> Wenn Sie nach dem Kontakt des aktuellen Portalbenutzers oder nach dem übergeordneten Konto filtern, wird empfohlen, dass Sie eine [Zugriffsregel für Webseiten](webpage-access-control.md) der Webseite zuordnen, um den Benutzer zur Anmeldung zu zwingen. Sie würden eine [Webrolle](create-web-roles.md) mit aktivierter "Authentifizierte Benutzerrolle" erstellen. Erstellen Sie eine Zugriffssteuerungsregel für Webseiten mit dem Recht "Lesen einschränken" und ordnen Sie die Webrolle zu. Dadurch werden Benutzer gezwungen, sich anzumelden, um die Seite anzuzeigen, und die Daten können dementsprechend ausgefüllt werden.

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Umleiten zu einer neuen URL auf einem Portal](add-redirect-url.md)  
