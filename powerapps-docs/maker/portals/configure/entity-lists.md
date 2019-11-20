---
title: Hinzufügen einer Webseite zum Rendering einer Liste von Datensätzen in einem Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren von Entitäts Listen zum Rendering einer Liste von Datensätzen in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 1ab175f69fdcf292185fd96cb176045dccc3a70b
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552840"
---
# <a name="about-entity-lists"></a>Informationen zu Entitäts Listen

Eine Entitäts Liste ist eine datengesteuerte Konfiguration, mit der Sie eine Webseite hinzufügen, die eine Liste von Datensätzen Renderer, ohne dass ein Entwickler das Raster im Portal anzeigen muss. Mithilfe von Entitäts Listen können Sie Datensätze für die Anzeige in Portalen verfügbar machen.

Das Raster unterstützt das Sortieren und wird paginiert, wenn die Anzahl der Datensätze größer als die angegebene Seitengröße ist. Wenn eine **Webseite für die Detailansicht** angegeben wurde, enthält jeder Datensatz einen Link zur Seite, und die ID des Datensatzes wird zusammen mit dem Parameter Namen der ID-Abfrage Zeichenfolge an die Abfrage Zeichenfolge angehängt. Die Entitäts Liste unterstützt auch mehrere Ansichten. Wenn mehr als eine Ansicht angegeben wurde, wird eine Dropdown Liste gerendert, um dem Benutzer zu ermöglichen, zwischen den verschiedenen Ansichten zu wechseln.

Die Daten können auch nach dem aktuellen Portalbenutzer, dem übergeordneten Kundenkonto des aktuellen Portal Benutzers und der aktuellen Portal Website gefiltert werden. Wenn ein Wert sowohl für das **Portalbenutzer Attribut** als auch für das **Konto Attribut**für Filterbedingungen vorhanden ist, wird im Portal eine Dropdown Liste gerenbt, um dem Benutzer zu ermöglichen, eigene Daten (meine) oder die Daten des übergeordneten Kundenkontos anzuzeigen.

## <a name="add-an-entity-list-to-your-portal"></a>Hinzufügen einer Entitäts Liste zum Portal

Die Entitäts Liste enthält Beziehungen zu Webseiten und verschiedene Eigenschaften, um die Initialisierung der Liste von Datensätzen im Portal zu steuern. Die Beziehung zur Webseite ermöglicht das dynamische Abrufen der Listen Definition für einen bestimmten Seiten Knoten innerhalb der Website. Um vorhandene Entitäts Sichten anzuzeigen oder neue Entitäts Sichten zu erstellen, wechseln Sie zu **Portale** > **Entitäts Listen**.

> [!Note]
> - Eine Entitäts Liste muss einer Webseite in einer bestimmten Website zugeordnet werden, damit die Liste innerhalb der Site angezeigt werden kann.
> - Der Mehrfachauswahl-Options Satz wird in Entitäts Listen nicht unterstützt.

Die der Entitäts Liste zugeordneten Webseiten können angezeigt werden, indem Sie den Link **Webseiten** auswählen, der in den **zugehörigen** Navigationslinks im linken Menü aufgeführt ist. Beim Erstellen der Entitäts Liste müssen Sie im ersten Schritt die Entität auswählen, für die Sie eine Liste im Portal darstellen möchten. Anschließend wählen Sie eine oder mehrere Modell gesteuerte App-Ansichten zum Rendering aus.

Beim Erstellen oder Bearbeiten einer Webseite können Sie im Feld Suche eine Entitäts Liste angeben, die im Formular der Webseite bereitgestellt wird. Die Seitenvorlage ist in der Regel die Seitenvorlage, kann jedoch eine von mehreren anderen Vorlagen sein, die für den Inhalt entworfen wurden, da die Master Vorlagen die erforderliche Logik enthalten, um zu bestimmen, ob eine Entitäts Liste gerendert werden soll.

## <a name="entity-list-attributes-and-relationships"></a>Attribute und Beziehungen von Entitäts Listen

|              Name              |                                                                                                                                                                                        Beschreibung                                                                                                                                                                                         |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              Name              |                                                                                                                                                                Der beschreibende Name des Datensatzes. Dieses Feld ist erforderlich.                                                                                                                                                                 |
|          Entitäts Name           |                                                                                                                                               Der Name der Entität, von der die gespeicherte Abfrage Ansicht geladen wird. Dieses Feld ist erforderlich.                                                                                                                                               |
|              Anschauung              |                                                                          Die gespeicherten Abfrage Sichten der Ziel Entität, die gerendert werden soll. Dieses Feld ist erforderlich. Wenn mehr als eine Ansicht angegeben wurde, enthält die Webseite eine Dropdown Liste, die es dem Benutzer ermöglicht, zwischen den verschiedenen Ansichten zu wechseln.                                                                           |
|           Seitengröße            |                                                                                                                                            Ein ganzzahliger Wert, der die Anzahl der Datensätze pro Seite angibt. Dieses Feld ist erforderlich. Standardwert: 10                                                                                                                                             |
|   Webseite für die Detailansicht    |                                                                                                        Eine optionale Webseite, die für jeden Datensatz verknüpft werden kann. Der Parameter Name und die Datensatz-ID der ID-Abfrage Zeichenfolge werden an die Abfrage Zeichenfolge der URL zu dieser Webseite angehängt.                                                                                                        |
|      Bezeichnung "Details"      |                     Der Text, der für die Schaltfläche "Detailansicht" angezeigt wird, wenn **eine Webseite für die Detailansicht** angegeben wurde. Standard: Details anzeigen <br>**Hinweis**: für jedes Sprachpaket, das für die Common Data Service Umgebung installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann.                      |
|      Webseite für CREATE       |                                                                                                                                                             Eine optionale Webseite, die das Ziel der Schaltfläche erstellen ist.                                                                                                                                                              |
|      Schaltflächen Bezeichnung erstellen       |                              Der Text, der für die Schaltfläche "erstellen" angezeigt wird, wenn **eine Webseite für Create** angegeben wurde. Standard: Erstellen <br>**Hinweis**: für jedes Sprachpaket, das für die Common Data Service Umgebung installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann. _                              |
| ID-Abfrage Zeichen folgen Parameter Name |                                                                                                                                           Ein Parameter Name, der in der Abfrage Zeichenfolge der URL der Webseite für die Detailansicht bereitgestellt wird. Standard: ID                                                                                                                                           |
|        Leerer Listen Text         |  **Veraltet**.  Die Meldung, die angezeigt wird, wenn keine Datensätze vorhanden sind.<br>**Hinweis**: für jedes Sprachpaket, das für die Common Data Service Umgebung installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann.                                                           |
|     Portal Benutzer Attribut      |                                                                                      Ein optionales Nachschlage Attribut für die primäre Entität, das den Benutzerdaten Satz des Portals darstellt (entweder Kontakt oder Systembenutzer), auf den die ID des aktuellen Benutzers angewendet werden kann, um die in der Liste gerenderten Daten zu filtern.                                                                                      |
|       Konto Attribut        |                                                                                       Ein optionales Such Attribut für die primäre Entität, das einen Kontodaten Satz darstellt, auf den der Wert des übergeordneten Kundenkontos des aktuellen Benutzers angewendet werden kann, um die in der Liste gerenderten Daten zu filtern.                                                                                       |
|       Website Attribut        |                                                                                                          Ein optionales Such Attribut für die primäre Entität, das die Website darstellt, auf die die ID der aktuellen Website angewendet werden kann, um die in der Liste gerenderten Daten zu filtern.                                                                                                          |
|         Suche aktiviert         | Ein optionaler boolescher Wert, der angibt, ob die Suche aktiviert werden soll. Ein Textfeld wird gerendert, um Benutzern eine schnelle Suche nach Datensätzen zu ermöglichen. Verwenden Sie das Platzhalter Zeichen Sternchen (\*), um nach Teiltext zu suchen. Die Suche fügt die vorhandenen vordefinierten Filterbedingungen der Ansicht an die vorhandenen vordefinierten Filterbedingungen der Ansicht an, um Sie abzufragen und die resultierenden Datensätze zurückzugeben. |
|    Platzhalter Text suchen     |                                                                                                                                                      Eine optionale Zeichenfolge, die als Bezeichnung verwendet wird, die beim anfänglichen Laden im Textfeld angezeigt wird.                                                                                                                                                       |
|      QuickInfo-Text suchen       |                                                                                                                                             Eine optionale Zeichenfolge, die als QuickInfo verwendet wird, wenn der Benutzer auf das **Suchtextfeld** zeigt.                                                                                                                                              |
|                                |                                                                                                                                                                                                                                                                                                                                                                                            |

## <a name="add-custom-javascript"></a>Hinzufügen benutzerdefinierter JavaScript

Die Registerkarte Optionen im Formular enthält einen Textbereich, in den Sie benutzerdefinierte [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)]eingeben können. Wenn Ihre Seite die jQuery-Bibliothek enthält, können Sie diese hier ebenfalls verwenden. Der Skriptblock wird am unteren Rand der Webseite direkt vor dem schließenden Formular Tag der Seite hinzugefügt.

![Beispiel für benutzerdefinierte JavaScript](../media/custom-javascript-example.png "Beispiel für benutzerdefinierte JavaScript")  

Die Daten werden asynchron in der Liste abgerufen, und nach Abschluss des Vorgangs wird ein Ereignis `loaded`, das Ihre benutzerdefinierte [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] lauschen und mit Elementen im Raster ausführen kann. Der folgende Code ist ein einfaches Beispiel:
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

Suchen Sie nach einem bestimmten Attribut Feld, und legen Sie dessen Wert fest, um das Rendering des Werts möglicherweise zu ändern. Der folgende Code ruft jede Tabellenzelle ab, die den Wert des `accountnumber`-Attributs enthält. Ersetzen Sie `accountnumber` durch ein entsprechendes Attribut für die Entität und die Ansicht.
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
## <a name="entity-list-configuration"></a>Konfiguration der Entitäts Liste

Sie können Aktionen (erstellen, bearbeiten, löschen usw.) für Datensätze in einer Entitäts Liste problemlos aktivieren und konfigurieren. Es ist auch möglich, Standard Bezeichnungen,-Größen und andere Attribute zu überschreiben, sodass die Entitäts Liste genau so angezeigt wird, wie Sie möchten.

Diese Einstellungen finden Sie im Abschnitt "Konfiguration" im Formular für die Entitäts Liste. Standardmäßig werden nur **grundlegende Einstellungen** angezeigt. Wählen Sie **Erweiterte Einstellungen** aus, um weitere Einstellungen anzuzeigen.

![Konfigurieren einer Entitäts Liste](../media/configure-entitylist.png "Konfigurieren einer Entitäts Liste")  

**Legt**

|Name                   |Beschreibung|
|---------------------------|-----------|
|**Grundlegende Einstellungen**         |   |
| Aktionen anzeigen              |Verwenden Sie, um Aktions Schaltflächen für Aktionen hinzuzufügen, die für die Entitätenmenge anwendbar sind und über dem Raster angezeigt werden. Folgende Aktionen sind verfügbar: <ul><li>Stelle</li> <li>Download</li></ul> Wenn Sie eine dieser Optionen auswählen, wird ein Konfigurationsbereich für diese Aktion angezeigt.|
| Elemente Aktionen             |Verwenden Sie diese Schaltfläche, um Aktions Schaltflächen für Aktionen hinzuzufügen, die für einen einzelnen Datensatz anwendbar sind und für jede Zeile im Raster angezeigt werden, sofern die entsprechenden Berechtigungen durch Entitäts Berechtigungen erteilt wurden. Die folgenden Aktionen sind allgemein verfügbar:<ul><li>Details</li><li>Bearbeiten</li><li>Lösch</li><li>Workflow</li><li>Aktivieren</li><li>Deaktivieren</li></ul> Wenn Sie eine dieser Optionen auswählen, wird ein Konfigurationsbereich für diese Aktion angezeigt. Weitere Informationen zu den einzelnen Aktionen finden Sie unten. Darüber hinaus weisen bestimmte Entitäten spezielle Aktionen auf, die für Sie pro Entität verfügbar sind:<ul><li>Berechnen des Werts der Verkaufschance (Chance)</li><li>Fall Aktion abbrechen (Incident)</li><li>Schließen (auflösen) der Fall Aktion (Incident)</li><li>Anführungszeichen in Bestellung konvertieren (Anführungszeichen)</li><li>Bestellung in Rechnung konvertieren (SalesOrder)</li><li>Zitat aus Verkaufschance generieren (Gelegenheit)</li><li>Gelegenheit zum Verlust der Chance (Gelegenheit)</li><li>Win Chance-Aktion (Gelegenheit)</li><li>Fall Aktion erneut öffnen (Incident)</li><li>Verkaufschance festlegen (Gelegenheit)</li></ul>|
| Spalten Attribute überschreiben|Verwenden Sie, um Anzeigeeinstellungen für einzelne Spalten im Raster zu überschreiben.<ul><li>Attribut: logischer Name der Spalte, die Sie überschreiben möchten.</li><li>Anzeige Name: neuer Spaltentitel, um den Standardwert zu überschreiben</li><li>Width: die Breite (in Prozent oder Pixel) der Spalte, um die Standardeinstellung zu überschreiben. Siehe auch Breite der Raster Spaltenbreite</li></ul> Um Einstellungen für eine Spalte zu überschreiben, wählen Sie **+ Spalte** aus, und geben Sie die Details ein.|
|**Erweiterte Einstellungen**      |  |
| Meldung wird geladen           |Überschreibt die HTML-Standardmeldung, die beim Laden des Rasters angezeigt wird.|
| Fehlermeldung             |Überschreibt die HTML-Standardmeldung, die angezeigt wird, wenn ein Fehler beim Laden des Rasters auftritt.|
| Meldung "Zugriff verweigert"     |Überschreibt die HTML-Standardmeldung, die angezeigt wird, wenn ein Benutzer nicht über ausreichende Entitäts Berechtigungen zum Anzeigen der Entitäts Liste verfügt.|
| Leere Nachricht             |Überschreibt die HTML-Meldung, die angezeigt wird, wenn das Raster keine Daten enthält.|
| Dialog Feld "Details"       |Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Detail Aktion aktiviert.|
| Formular bearbeiten-Dialog Feld          |Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Bearbeitungsaktion aktiviert.|
| Dialog Feld Create Form        |Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die CREATE-Aktion aktiviert.|
| Dialog Feld löschen             |Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Löschaktion aktiviert.|
| Fehler Dialogfeld              |Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn während einer beliebigen Aktion ein Fehler auftritt.|
| CSS-Klasse                 |Geben Sie eine CSS-Klasse oder Klassen an, die auf das HTML-Element angewendet werden, das den gesamten Raster Bereich enthält, einschließlich der Raster-und Aktions Schaltflächen.|
| Grid-CSS-Klasse            |Geben Sie eine CSS-Klasse oder Klassen an, die auf die HTML-\<Tabelle\>-Elements der Entitäts Liste angewendet werden.|
| Breite der Raster Spaltenbreite   |Konfiguriert, ob die **breiten** Werte in den Attributen der Überschreibungs Spalte in **Pixel** oder **Prozent**angegeben werden.|

**Allgemeine Aktions Einstellungen**

Im Allgemeinen verfügen entitätenaktionen über Einstellungen, die konfiguriert werden können. In allen Fällen werden Ihnen dadurch weitere Optionen in Bezug auf die Anpassung zur Verfügung stehen, und die Felder sind nicht erforderlich. Wenn Sie die Aktion einfach hinzufügen, kann die Aktion im Portal ausgeführt werden, sofern die entsprechenden Berechtigungen durch Entitäts Berechtigungen erteilt wurden.

Im Allgemeinen können Sie das entsprechende Dialogfeld für jede Aktion konfigurieren, die nur angezeigt wird, wenn Sie die Option **Bestätigung erforderlich**auswählen.


| Name                   | Beschreibung                                                                                                                                                                                                                   |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**         |                                                                                                                                                                                                                               |
| Bestätigung erforderlich? | Bestimmt, ob eine Bestätigung den Benutzer zur Bestätigung auffordert, wann die Aktion ausgewählt wird.                                                                                                                                 |
| **Erweiterte Einstellungen**      |                                                                                                                                                                                                                               |
| Bestätigt           | Überschreibt die HTML-Bestätigungsmeldung, die angezeigt wird, wenn der Benutzer die Aktion aktiviert.                                                                                                                                         |
| Schaltflächen Bezeichnung           | Überschreibt die HTML-Bezeichnung für diese Aktion, die in der Entitäts Listen Zeile angezeigt wird.                                                                                                                                                    |
| QuickInfo         | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion zeigt, die in der Entitäts Listen Zeile angezeigt wird                                                                                           |
| CSS-Klasse für das       | Fügt der Schaltfläche eine CSS-Klasse hinzu.                                                                                                                                                      |
| An Webseite umleiten    | Einige Aktionen (nicht alle) lassen eine Umleitung nach Abschluss der Aktion zu. Empfohlen für die DELETE-Aktion, die in den meisten anderen Fällen optional ist, können Sie eine Webseite auswählen, zu der umgeleitet werden soll, wenn die Aktion abgeschlossen ist. |
| Umleitungs-URL           | Eine Alternative zur Option **Umleitung an Webseite**&mdash;die die Umleitung an eine bestimmte URL ermöglicht.                                                                                                                                   |

**Allgemeine Dialogfeld "Erweiterte Einstellungen"**

|**Name**                 |**Description** (Beschreibung)                                                                                                                         |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Title                    | Überschreibt den HTML-Code, der in der Titelleiste des Dialog Felds angezeigt wird.|                                                                         
| Primärer Schaltflächen Text      | Überschreibt den HTML-Code, der in der primären Schaltfläche (Löschen) im Dialogfeld angezeigt wird.                                                         |
| Schaltflächen Text schließen        | Überschreibt den HTML-Code, der in der Schaltfläche Schließen (Abbrechen) im Dialogfeld angezeigt wird.                                                           |
| SR-Text der Schaltfläche verwerfen   | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                           |
| Größe                     | Gibt die Größe des Dialog Felds löschen an. Die Optionen lauten "Standard", "groß" und "klein". Die Standardgröße ist default. |
| CSS-Klasse                | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                            |
| Tile-CSS-Klasse           | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                                |
| CSS-Klasse der primären Schaltfläche | Geben Sie eine CSS-Klasse oder Klassen an, die auf die primäre Schaltfläche (Löschen) des Dialog Felds angewendet werden.                                          |
| CSS-Klasse der Schaltfläche Schließen   | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Schaltfläche Schließen (Abbrechen) des Dialog Felds angewendet werden.                                            |

**Aktions Einstellungen erstellen**

Durch das Aktivieren einer **create-Aktion** wird eine Schaltfläche oberhalb der Entitäts Liste gerendert. wenn diese Option ausgewählt ist, wird ein Dialogfeld mit einem Entitäts Formular geöffnet, mit dem der Benutzer einen neuen Datensatz erstellen kann, vorausgesetzt, die CREATE-Berechtigung wurde durch Entitäts Berechtigungen

| Name               | Beschreibung                          |
|--------------------|--------------------------------------|
| **Grundlegende Einstellungen**     |                                                                                                                                                                       |
| Entitäts Formular     | Gibt das Entitäts Formular an, das zum Erstellen des neuen Datensatzes verwendet wird. Die Dropdown Liste enthält alle Entitäts Formulare, die für den Entitätstyp der Entitäts Liste konfiguriert sind. <br>**Hinweis**: Wenn der Entitätstyp der Entitäts Liste keine Entitäts Formulare aufweist, wird die Dropdown Liste leer angezeigt. Wenn für die CREATE-Aktion kein Entitäts Formular bereitgestellt wird, wird es ignoriert, und die Schaltfläche wird nicht in der Entitäts Liste gerendert. |
| **Erweiterte Einstellungen**          |                                                                                                                                                                       |
| Schaltflächen Bezeichnung                                                                                                                                                                                                                 | Überschreibt die HTML-Bezeichnung, die in der Schaltfläche Aktion erstellen über der Liste angezeigt wird.                                                                                        |
| QuickInfo                                                                                                                                                                                                               | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche Aktion erstellen zeigt.                                                                         |

**Dialogfeld "Formular erstellen" mit den Einstellungen**

|**Name**               |**Description** (Beschreibung)                                                                                                                                 |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Meldung wird geladen        | Überschreibt die Meldung, die beim Laden des Dialog Felds angezeigt wird.                                                                                  |
| Title                  | Überschreibt den HTML-Code, der in der Titelleiste des Dialog Felds angezeigt wird.                                                                                  |
| SR-Text der Schaltfläche verwerfen | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                                   |
| Größe                   | Gibt die Größe des Dialog Felds Create Form an. Die Optionen lauten "Standard", "groß" und "klein". Die Standardgröße ist groß. |
| CSS-Klasse              | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                    |
| Title-CSS-Klasse        | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                                        |

**Aktions Einstellungen herunterladen**

Durch das Aktivieren einer **Download Aktion** wird eine Schaltfläche oberhalb der Entitäts Liste gerendert, bei der die Daten aus der Liste in eine [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)] Datei (. xlsx) heruntergeladen werden.

| Name              | Beschreibung                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                    |
| Gar              |                                                                                                    |
| **Erweiterte Einstellungen** |                                                                                                    |
| Schaltflächen Bezeichnung      | Überschreibt die HTML-Bezeichnung, die in der Schaltfläche Download Aktion oberhalb der Entitäts Liste angezeigt wird.            |
| QuickInfo    | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche Download Aktion zeigt. |

**Details zu Aktions Einstellungen**

Wenn Sie eine **Detail Aktion** aktivieren, kann ein Benutzer ein Schreib geschütztes Entitäts Formular einer ausgewählten Zeile in der Entitäts Liste anzeigen.


|                 Name                  |                                                                                                                                                                                                                      Beschreibung                                                                                                                                                                                                                      |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Grundlegende Einstellungen**           |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              Entitäts Formular              | Gibt das Entitäts Formular an, das zum Anzeigen der Details der ausgewählten Entität verwendet wird. Die Dropdown Liste enthält alle Entitäts Formulare, die für den Entitätstyp der Entitäts Liste konfiguriert sind. <br> **Hinweis**: Wenn der Entitätstyp der Entitäts Liste keine Entitäts Formulare aufweist, wird die Dropdown Liste leer angezeigt. Wenn für die Detail Aktion kein Entitäts Formular bereitgestellt wird, wird es ignoriert, und die Schaltfläche wird nicht in der Entitäts Liste gerendert. |
|         **Erweiterte Einstellungen**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Name der Abfrage Zeichenfolge für Datensatz-ID |                                                                    Gibt den Namen des Abfrage Zeichenfolgen-Parameters an, der verwendet wird, um die Entität auszuwählen, die im ausgewählten Entitäts Formular angezeigt werden soll. Dieser Wert muss mit dem Wert in der Abfrage Zeichenfolge des Datensatz-ID-Abfrage Zeichenfolgen für den Datensatz Der Standardwert für dieses Feld ist sowohl hier als auch in der Formular Konfiguration der Entität " **ID**".                                                                     |
|             Schaltflächen Bezeichnung              |                                                                                                                                                                                      Überschreibt die HTML-Bezeichnung für diese Aktion, die in der Entitäts Listen Zeile angezeigt wird.                                                                                                                                                                                       |
|            QuickInfo             |                                                                                                                                                             Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion zeigt, die in der Entitäts Listen Zeile angezeigt wird                                                                                                                                                              |

**Erweiterte Einstellungen im Dialogfeld "Details"**

|**Name**               |**Description** (Beschreibung)                                                                                                                         |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Meldung wird geladen        | Überschreibt den HTML-Code, der beim Laden des Dialog Felds angezeigt wird.                                                                             |
| Title                  | Überschreibt den HTML-Code, der in der Titelleiste des Dialog Felds angezeigt wird.                                                                         |
| SR-Text der Schaltfläche verwerfen | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                           |
| Größe                   | Gibt die Größe des Dialog Felds "Details" an. Die Optionen lauten "Standard", "groß" und "klein". Die Standardgröße ist groß. |
| CSS-Klasse              | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                            |
| Title-CSS-Klasse        | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                                |

**Aktions Einstellungen bearbeiten**

Durch das Aktivieren einer **Bearbeitungsaktion** kann ein Benutzer ein bearbeitbares Entitäts Formular anzeigen, das an den Datensatz der ausgewählten Zeile aus der Entitäts Liste Daten gebunden ist, vorausgesetzt, die Schreib Berechtigung wurde durch Entitäts Berechtigungen erteilt.


|                 Name                  |                                                                                                                                                                                                             Beschreibung                                                                                                                                                                                                             |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Grundlegende Einstellungen**           |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|              Entitäts Formular              | Gibt das Entitäts Formular an, das verwendet wird, um die ausgewählte Entität zu bearbeiten. Die Dropdown Liste enthält alle Entitäts Formulare, die für den Entitätstyp der Entitäts Liste konfiguriert sind. <br> **Hinweis**: Wenn der Entitätstyp der Entitäts Liste keine Entitäts Formulare aufweist, wird die Dropdown Liste leer angezeigt. Wenn für die Aktion bearbeiten keine Entitäts Form bereitgestellt wird, wird diese ignoriert, und die Schaltfläche wird nicht in der Entitäts Liste gerendert. |
|         **Erweiterte Einstellungen**         |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Name der Abfrage Zeichenfolge für Datensatz-ID |                                                           Gibt den Namen des Abfrage Zeichenfolgen-Parameters an, der verwendet wird, um die Entität auszuwählen, die im ausgewählten Entitäts Formular bearbeitet werden soll. Dieser Wert muss mit dem Wert in der Abfrage Zeichenfolge des Datensatz-ID-Abfrage Zeichenfolgen für den Datensatz Der Standardwert für dieses Feld ist sowohl hier als auch in der Formular Konfiguration der Entität " **ID**".                                                            |
|             Schaltflächen Bezeichnung              |                                                                                                                                                                             Überschreibt die HTML-Bezeichnung für diese Aktion, die in der Entitäts Listen Zeile angezeigt wird.                                                                                                                                                                              |
|            QuickInfo             |                                                                                                                                                    Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion zeigt, die in der Entitäts Listen Zeile angezeigt wird                                                                                                                                                     |

**Dialogfeld "Formular bearbeiten" Erweiterte Einstellungen**

|**Name**               |**Description** (Beschreibung)                                                                                                                   |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Meldung wird geladen        | Überschreibt den HTML-Code, der beim Laden des Dialog Felds angezeigt wird.                                                                       |
| Title                  | Überschreibt den HTML-Code, der in der Titelleiste des Dialog Felds angezeigt wird.                                                                   |
| SR-Text der Schaltfläche verwerfen | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                     |
| Größe                   | Gibt die Größe des Dialog Felds bearbeiten an. Die Optionen lauten "Standard", "groß" und "klein". Die Standardgröße ist groß. |
| CSS-Klasse              | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                      |
| Title-CSS-Klasse        | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                          |

**Aktions Einstellungen löschen**

Durch das Aktivieren einer **Löschaktion** kann ein Benutzer den Datensatz der ausgewählten Zeile endgültig aus der Entitäts Liste löschen, sofern die Berechtigung Löschen durch Entitäts Berechtigungen erteilt wurde.

| Name              | Beschreibung                                                                                                                         |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                     |
| Gar              |                                                                                                                                     |
| **Erweiterte Einstellungen** |                                                                                                                                     |
| Bestätigt      | Überschreibt die HTML-Bestätigungsmeldung, die angezeigt wird, wenn der Benutzer die DELETE-Aktion aktiviert.                                        |
| Schaltflächen Bezeichnung      | Überschreibt die HTML-Bezeichnung für diese Aktion, die in der Entitäts Listen Zeile angezeigt wird.                                                          |
| QuickInfo    | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion zeigt, die in der Entitäts Listen Zeile angezeigt wird |

**Dialogfeld "Löschen" (Erweiterte Einstellungen)**

|**Name**                 |**Description** (Beschreibung)                                                                                                                         |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Title                    | Überschreibt den HTML-Code, der in der Titelleiste des Dialog Felds angezeigt wird.                                                                         |
| Primärer Schaltflächen Text      | Überschreibt den HTML-Code, der in der primären Schaltfläche (Löschen) im Dialogfeld angezeigt wird.                                                         |
| Schaltflächen Text schließen        | Überschreibt den HTML-Code, der in der Schaltfläche Schließen (Abbrechen) im Dialogfeld angezeigt wird.                                                           |
| SR-Text der Schaltfläche verwerfen   | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                           |
| Größe                     | Gibt die Größe des Dialog Felds löschen an. Die Optionen lauten "Standard", "groß" und "klein". Die Standardgröße ist default. |
| CSS-Klasse                | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                            |
| Title-CSS-Klasse          | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                                |
| CSS-Klasse der primären Schaltfläche | Geben Sie eine CSS-Klasse oder Klassen an, die auf die primäre Schaltfläche (Löschen) des Dialog Felds angewendet werden.                                          |
| CSS-Klasse der Schaltfläche Schließen   | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Schaltfläche Schließen (Abbrechen) des Dialog Felds angewendet werden.                                            |

**Workflow Aktions Einstellungen**

Durch das Aktivieren einer **Workflow Aktion** kann ein Benutzer einen bedarfsgesteuerten Workflow für den Datensatz der ausgewählten Zeile aus der Entitäts Liste ausführen. Sie können der Entitäts Liste eine beliebige Anzahl von Workflow Aktionen hinzufügen.


|         Name          |                                                                                                                                                           Beschreibung                                                                                                                                                           |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Grundlegende Einstellungen**   |                                                                                                                                                                                                                                                                                                                                 |
|       Workflow        | Gibt den bedarfsgesteuerten Workflow an, der ausgeführt wird, wenn der Benutzer diese Aktion aktiviert. <br> **Hinweis**: Wenn der Entitätstyp der Entitäts Liste keine Workflows enthält, wird die Dropdown Liste leer angezeigt. Wenn für die Workflow Aktion kein Workflow bereitgestellt wird, wird er ignoriert, und die Schaltfläche wird nicht in der Entitäts Liste gerendert. |
|     Schaltflächen Bezeichnung      |                                                                                                                 Legt die HTML-Bezeichnung für diese Aktion fest, die in der Entitäts Listen Zeile angezeigt wird. Diese Einstellung ist erforderlich.                                                                                                                 |
| **Erweiterte Einstellungen** |                                                                                                                                                                                                                                                                                                                                 |
|    QuickInfo     |                                                                                                  Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion zeigt, die in der Entitäts Listen Zeile angezeigt wird                                                                                                   |

## <a name="securing-entity-lists"></a>Sichern von Entitäts Listen

Zum Sichern einer Entitäts Liste müssen Sie Entitäts Berechtigungen für die Entität konfigurieren, für die Datensätze angezeigt werden, und auch den booleschen Wert **Entitäts Berechtigungen aktivieren** für den Entitäts Listen Daten Satz auf true festlegen.

Durch das Sichern einer Entitäts Liste wird sichergestellt, dass für jeden Benutzer, der auf die Seite zugreift, nur Datensätze angezeigt werden, für die Ihnen die Berechtigung erteilt wurde. Dies wird durch einen zusätzlichen Filter erreicht, der den Modell gesteuerten App-Ansichten hinzugefügt wird, die über die Liste angezeigt werden. Dieser Filter filtert nur nach Datensätzen, die für den Benutzer über die **Lese** Berechtigung zugänglich sind.

Außerdem werden für alle Aktionen, die für die Liste definiert sind, die entsprechenden Berechtigungen für diese Aktion auf Datensatzebene berücksichtigt. Das heißt, wenn Sie über die Berechtigung Bearbeiten für einen Datensatz verfügen, wird die Bearbeitungsaktion für diesen Datensatz aktiviert. Das gleiche gilt für DELETE, CREATE und so weiter. Beachten Sie, dass eine Meldung angezeigt wird, wenn keine Datensätze verfügbar sind, wenn die Liste geladen wird.

Ein guter Website Entwurf erfordert jedoch, dass ein Benutzer, der nicht in einer Rolle vorhanden ist, die über Berechtigungen für die Entität verfügt (das heißt, es wird nie eine Situation, in der er Datensätze sehen sollte), keinen Zugriff auf die Seite haben sollte. Im Idealfall sollte die Seite mithilfe von Webseiten Zugriffsberechtigungen geschützt werden.

## <a name="adding-a-view-details-page"></a>Hinzufügen einer Ansichts Detailseite

Durch Festlegen der Webseite für die Detailansicht Suche auf eine Webseite können die Details eines Datensatzes, der im Raster aufgelistet ist, je nach Konfiguration der zugeordneten Form oder Seite als schreibgeschützt oder bearbeitet angezeigt werden.

Diese Seite kann eine vollständig angepasste Seitenvorlage sein, die möglicherweise mithilfe von Liquid erstellt wurde. Das häufigste Szenario ist, dass es sich bei der Detailseite um eine Webseite handelt, die entweder ein Entitäts Formular oder ein Webformular enthält.

Wichtig zu beachten ist, dass jeder Datensatz, der im Raster aufgelistet ist, einen Hyperlink zur Detailseite enthält und dass der Link einen benannten Abfrage Zeichen folgen Parameter mit der ID des Datensatzes enthält. Der Name des Abfrage Zeichen folgen Parameters hängt vom Parameternamen der ID-Abfrage Zeichenfolge ab, der in der Entitäts Liste angegeben ist. Beachten Sie abschließend, dass die Ziel Detail Webseite auch den Namen dieses Abfrage Zeichenfolgen-Parameters beachten muss, um die ID des Datensatzes zu erhalten, der zum Abfragen und Laden der Daten benötigt wird.

![Seite "Details anzeigen" hinzufügen](../media/add-view-details-page.png "Seite Details anzeigen hinzufügen")  

**Anzeigen von Details mithilfe eines Entitäts Formulars**

Informationen zum Erstellen eines Entitäts Formulars finden Sie in den Anweisungen auf der Formularseite für [Entitäten](entity-forms.md) .

Beachten Sie die folgenden wichtigen Einstellungen, um sicherzustellen, dass der Datensatz aus der Entitäts Liste im Entitäts Formular geladen wird.

Der Name der Abfrage Zeichenfolgen-Parameter für die Datensatz-ID im Entitäts Formular muss mit dem Parameternamen der ID-Abfrage Zeichenfolge

Der Modus kann abhängig von Ihren Anforderungen entweder "Bearbeiten" oder "schreibgeschützt" lauten.

**Anzeigen von Details mithilfe eines Webformulars**

Beachten Sie die folgenden wichtigen Einstellungen, um sicherzustellen, dass der Datensatz aus der Entitäts Liste in das Webformular geladen wird.

Der Parameter Name der PRIMARY KEY-Abfrage Zeichenfolge in Web Form-Schritt muss mit dem Parameternamen der ID-Abfrage Zeichenfolge in der Entitäts

Der Modus kann abhängig von Ihren Anforderungen entweder "Bearbeiten" oder "schreibgeschützt" lauten.

**Verwenden einer Detailseite für die Create-Funktion**

Sie können eine benutzerdefinierte Seite, ein Entitäts Formular oder ein Webformular für die Create-Funktion auf die gleiche Weise verwenden. Dies ist eine Alternative zum Definieren einer CREATE-Aktion im Formular. Sie können nicht sowohl eine Create *-Aktion als auch* eine benutzerdefinierte Seite für Create definieren: das Definieren einer benutzerdefinierten Aktion hat Vorrang.

Wenn Sie eine Webseite zum Erstellen der Suche in der Entitäts Liste zuweisen und keine CREATE-Aktion mithilfe der Konfiguration angeben, wird die Schaltfläche erstellen in der Liste gerendert. mit dieser Schaltfläche wird der Benutzer mit der benutzerdefinierten Seite verknüpft, die Sie für die Erstellung festgelegt haben.

## <a name="entity-list-filter-configuration"></a>Konfiguration der Entitäts Listen Filter

Das Hinzufügen der Möglichkeit zum Filtern von Datensätzen in einer Entitäts Liste ist einfach: Aktivieren Sie einfach die Filteroption, und wählen Sie einen oder mehrere Filtertypen aus, die Benutzern angezeigt werden sollen. Es ist möglich, nach einem Attribut zu filtern, das mit dem vom Benutzer bereitgestellten Text übereinstimmt, oder aus einer Reihe von Optionen auszuwählen. Sie können sogar praktisch jeden Filtertyp entwerfen, den Sie sich vorstellen können, indem Sie die erweiterte Suche verwenden.

**Aktivieren des Filter für die Entitäts Liste**

Aktivieren Sie im Abschnitt metadatenfilter das Kontrollkästchen aktiviert. Dadurch wird der Filter Bereich der Entitäts Liste hinzugefügt, wenn er angezeigt wird. Wenn Sie mindestens einen Filtertyp definiert haben, wird das Feld leer angezeigt.

Mithilfe der Orientation-Einstellung können Sie definieren, wie der Filter Bereich in der Entitäts Liste gerendert wird. Der Standardwert (horizontal) rendert den Filter Bereich oberhalb der Entitäts Liste. Die vertikale Ausrichtung rendert den Filter Bereich als Feld links neben der Entitäts Liste.

![Metadatenfiltereinstellungen](../media/metadata-filter-settings.png "Metadatenfiltereinstellungen")  

**Filter Typen**

|**Filtertyp**      |**Description** (Beschreibung)                                                                                                                                                                                                                               |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Text Filter          | Filtern Sie die Entitäts Liste, indem Sie ein Textfeld verwenden, um nach übereinstimmenden Text in einem ausgewählten Attribut der angegebenen Entität zu suchen.                                                                                                                               |
| Attribut Filter Satz | Filtern Sie die Entitäts Liste, indem Sie eine Reihe von Kontrollkästchen verwenden, von denen jeder versucht, die Bedingung mit einem bestimmten Attribut der angegebenen Entität abzugleichen.                                                                                           |
| Nachschlage Satz           | Filtern Sie die Entitäts Liste, indem Sie eine Reihe von Kontrollkästchen verwenden, von denen jedes eine Beziehung zwischen einem Datensatz für die angegebene Entität und einem Datensatz für eine verknüpfte Entität darstellt.                                                                         |
| Bereichs Filter Satz     | Vergleichbar mit dem Attribut Filter Satz, mit dem Unterschied, dass jedes Kontrollkästchen zwei Bedingungen darstellen kann, anstatt eins (z. b. größer als oder gleich 0 und kleiner als 100).                                                                    |
| Dynamischer Auswahllisten Satz | Ähnlich wie bei der Auswahl eines Auswahllisten Werts für einen Attribut Filter Satz. Der dynamische Auswahlliste-Satz erfordert nicht, dass Sie die Auswahllisten Optionen angeben, nach denen gefiltert werden soll. Stattdessen wird die vollständige Liste der Optionen generiert, wenn die Entitäts Liste geladen wird. |
| Dynamischer Nachschlage Satz   | Vergleichbar mit dem Nachschlage Satz. Der dynamische Nachschlage Satz erfordert nicht, dass Sie die Suchoptionen angeben, nach denen gefiltert werden soll. Stattdessen wird die vollständige Liste der Optionen generiert, wenn die Entitäts Liste geladen wird.                                           |
| Fetchxml-Filter      | Filtern Sie die Entitäts Liste mithilfe einer fetchxml-Filterbedingung.                                                                                                                                                                                     |

**Text Filter**

Mit dem Textfilter wird dem Filterbereich für die Entitäts Liste ein Textfeld hinzugefügt, das an ein Attribut des Entitäts Typs der Entitäts Liste gebunden ist. Wenn ein Benutzer den Filter anwendet, zeigt die Entitäts Liste nur die Datensätze an, deren ausgewähltes Attribut den Wert enthält.

Um einen Textfilter hinzuzufügen, wählen Sie **+ Text Filter**aus.

![Hinzufügen eines Textfilters](../media/add-text-filter.png "Hinzufügen eines Text Filters")  

Der Text Filter verwendet die folgenden Attribute:

|**Name**     |**Description** (Beschreibung)                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Versehen    | Der Name des Attributs für den ausgewählten Entitätstyp der Entitäts Liste, nach dem gefiltert werden soll. *Nur Attribute mit der type-Zeichenfolge sind für einen Text Filter gültig.*                                                                                   |
| Anzeigename | Überschreiben Sie die Bezeichnung für den Filter, wenn die Entitäts Liste angezeigt wird. Standardmäßig wird dieser automatisch auf den Namen des ausgewählten Attributs festgelegt. |

**Attribut Filter Satz**

Der Attribut Filtersatz fügt eine Reihe von Optionen hinzu, um die Entitäts Liste nach zu filtern, die an ein einzelnes Attribut des ausgewählten Entitäts Typs der Entitäts Liste gebunden ist. Wenn ein Benutzer den Filter anwendet, zeigt die Entitäts Liste nur die Datensätze an, die genau mit mindestens einer der ausgewählten Optionen übereinstimmen.

![Attribut Filtereinstellungen](../media/set-attribute-filter.png "Attribut Filtereinstellungen")

Der Attribut Filter Satz verwendet die folgenden Attribute:

|**Name**     |**Description** (Beschreibung)                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Versehen    | Der Name des Attributs für den ausgewählten Entitätstyp der Entitäts Liste, nach dem gefiltert werden soll. Nur Attribute mit den folgenden Typen sind für einen Text Filter gültig: String, bigint, Decimal, Double, Integer, Money, picklist, DateTime und Boolean.
|Anzeigename | Überschreiben Sie die Bezeichnung für den Filter, wenn die Entitäts Liste angezeigt wird. Standardmäßig wird dieser automatisch auf den Namen des ausgewählten Attributs festgelegt.
| Optionen |      Eine Auflistung möglicher Werte, nach denen gefiltert werden soll. Weitere Informationen finden Sie weiter unten.                                                                              |

**Optionen für Attribut Filter Sätze**

Ein Attribut Filter Satz kann in der Regel über eine beliebige Anzahl von Optionen verfügen, mit Ausnahme von "Auswahlliste"-und "Boolean"-Attributen. Ein boolesches Attribut Filter kann nur über eine oder zwei Optionen&mdash;eine true-Option und eine false-Option verfügen. Ein picklist-Attribut Filter Satz kann höchstens eine Option für jeden möglichen Wert in der Auswahlliste enthalten.

Optionen verfügen über die folgenden Attribute:

|**Name**     |**Description** (Beschreibung)                                                                                                                                                                                  |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| KOM     | Der Vergleichs Operator, der zum Filtern von Ergebnissen verwendet wird, z. b. "ist gleich", "kleiner als" usw. Die Liste der Operatoren für die Option hängt vom Typ des Attributs ab, das für den Filter ausgewählt ist. Numerische (dezimal-) Typen verfügen z. b. über Operatoren wie kleiner als oder größer als, wohingegen Zeichen folgen Attribute Operatoren wie z. b. beginnt mit oder enthält. Picklist-und boolesche Operatoren sind immer.                                                                                                                                               |
| Value        | Der tatsächliche Wert, der für diese Filterbedingung verwendet wird.                                                                                                                                                 |
| Anzeigename | Überschreibt den anzeigen Amen für diese Option im Filter Feld. Standardmäßig wird dieser Wert auf denselben Wert festgelegt wie das value-Attribut.                                                             |

**Nachschlage Satz**

Der Nachschlage Satz fügt eine Reihe von Optionen hinzu, um die Entitäts Liste nach zu filtern, die an eine verknüpfte Entität an den ausgewählten Entitätstyp der Entitäts Liste gebunden ist. Wenn ein Benutzer den Filter anwendet, zeigt die Entitäts Liste nur die Datensätze an, die genau mit mindestens einem der ausgewählten verknüpften Datensätze übereinstimmen.

![Nachschlage Satz](../media/lookup-set.png "Nachschlage Satz")  

Der Nachschlage Satz verwendet die folgenden Attribute:

|**Name**     |**Description** (Beschreibung)                                                                                                                                           |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Beziehung | Der Name der verknüpften Entität für den ausgewählten Entitätstyp der Entitäts Liste, nach dem gefiltert werden soll. Nur Entitäten mit einer 1: n-oder m:n-Beziehung mit dem ausgewählten Entitätstyp der Entitäts Liste werden als Optionen für diesen Filtertyp angezeigt.          |
| Anzeigename | Überschreiben Sie die Bezeichnung für den Filter, wenn die Entitäts Liste angezeigt wird. Standardmäßig wird dieser Wert automatisch auf den Namen der ausgewählten Beziehung festgelegt. |
| Optionen      | Eine Auflistung möglicher Werte, nach denen gefiltert werden soll. Weitere Informationen finden Sie weiter unten.                                                                                 |

**Optionen für Such Sätze**

Ein Nachschlage Satz kann in der Regel über eine beliebige Anzahl von Optionen verfügen, wobei das einzige Limit die Anzahl der verknüpften Datensätze des ausgewählten zugehörigen Typs ist.

Optionen verfügen über die folgenden Attribute:

|**Name**     |**Description** (Beschreibung)                                                                                                                      |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------|
| Value        | Der Datensatz des ausgewählten verknüpften Typs, nach dem gefiltert werden soll.                                                                                |
| Anzeigename | Überschreibt den anzeigen Amen für diese Option im Filter Feld. Standardmäßig wird dieser Wert auf denselben Wert festgelegt wie das value-Attribut. |

**Bereichs Filter Satz**

Der Bereichs Filtersatz fügt dem Filter Bereich eine Reihe von Optionen mit jeweils einer oder zwei Bedingungen hinzu. Wenn ein Benutzer den Filter anwendet, zeigt die Entitäts Liste nur die Datensätze an, die genau mit allen Bedingungen für mindestens eine der ausgewählten Optionen übereinstimmen.

![Bereichs Filtereinstellungen](../media/set-range-filter.png "Bereichs Filtereinstellungen")  

Der Bereichs Filter Satz verwendet die folgenden Attribute:

|**Name**     |**Description** (Beschreibung)                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Versehen    | Der Name des Attributs für den ausgewählten Entitätstyp der Entitäts Liste, nach dem gefiltert werden soll. Nur Attribute mit den folgenden Typen sind für einen Text Filter gültig: String, bigint, Decimal, Double, Integer, Money, DateTime.                       |
| Anzeigename | Überschreiben Sie die Bezeichnung für den Filter, wenn die Entitäts Liste angezeigt wird. Standardmäßig wird dieser automatisch auf den Namen des ausgewählten Attributs festgelegt. |
| Optionen      | Eine Auflistung möglicher Werte, nach denen gefiltert werden soll. Weitere Informationen finden Sie weiter unten.                                                                              |

**Optionen für Bereichs Filter Sätze**

Ein Bereichs Filter Satz kann über eine beliebige Anzahl von Optionen verfügen. Mit jeder Option wird eine Filterbedingung mit einer oder zwei unter Bedingungen erzeugt, die beide erfüllt werden müssen, damit die Bedingung wahr ist.

Optionen verfügen über die folgenden Attribute:

|**Name**              |**Description** (Beschreibung)                                                                                                                                                                                |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operator 1            | Der erste Vergleichs Operator, der zum Filtern von Ergebnissen verwendet wird, z. b. ist gleich und kleiner als. Die Liste der Operatoren für die Option hängt vom Typ des Attributs ab, das für den Filter ausgewählt ist. Numerische (dezimal-) Typen verfügen z. b. über Operatoren wie kleiner als oder größer als, wohingegen Zeichen folgen Attribute Operatoren wie z. b. beginnt mit oder enthält. Picklist-und boolesche Operatoren sind immer.                                                                                                                                             |
| Wert 1               | Der erste Wert, der für diese Filterbedingung verwendet wird.                                                                                                                                                |
| Operator 2 (optional) | Der zweite Vergleichs Operator, der zum Filtern von Ergebnissen verwendet wird, z. b. ist gleich und kleiner als. Die Liste der Operatoren für die Option hängt vom Typ des Attributs ab, das für den Filter ausgewählt ist. Numerische (dezimal-) Typen verfügen z. b. über Operatoren wie kleiner als oder größer als, wohingegen Zeichen folgen Attribute Operatoren wie z. b. beginnt mit oder enthält. Picklist-und boolesche Operatoren sind immer.                                                                                                                                             |
| Wert 2 (optional)    | Der zweite Wert, der für diese Filterbedingung verwendet wird.                                                                                                                                               |
| Anzeigename          | Überschreibt den anzeigen Amen für diese Option im Filter Feld. Standardmäßig wird dies basierend auf den ausgewählten Operatoren und Werten dynamisch festgelegt.                                         |

**Dynamischer Auswahllisten Satz**

Der dynamische picklist-Satz fügt eine Reihe von Optionen hinzu, nach denen gefiltert werden soll, die alle Werte eines angegebenen picklist-Felds darstellen. Dies unterscheidet sich von der Auswahl einer Auswahlliste im Attribut Filter Satz. Im Attribut Filter Satz müssen Sie eine Reihe von Optionen angeben, die dem Benutzer zur Verfügung gestellt werden, um nach zu filtern. im Set Dynamic picklist müssen Sie nur das Feldauswahl Liste angeben, und der gesamte Satz von Optionen wird automatisch bereitgestellt. Wenn Sie ein höheres Steuerelement benötigen, empfiehlt es sich, den Attribut Filter Satz zu verwenden.

![Dynamische Auswahllisten Einstellungen](../media/set-dynamic-picklist.png "Dynamische Auswahllisten Einstellungen")  

Der dynamische picklist-Satz verwendet die folgenden Optionen:

|**Name**     |**Description** (Beschreibung)                                                                                                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Versehen    | Der Name des picklist-Attributs für den ausgewählten Entitätstyp der Entitäts Liste, nach dem gefiltert werden soll.                                                             |
| Anzeigename | Überschreiben Sie die Bezeichnung für den Filter, wenn die Entitäts Liste angezeigt wird. Standardmäßig wird dieser automatisch auf den Namen des ausgewählten Attributs festgelegt. |

**Dynamischer Nachschlage Satz**

Der dynamische Nachschlage Satz fügt eine dynamische Reihe von Optionen hinzu, um die Entitäts Liste nach zu filtern, die an eine verknüpfte Entität an den ausgewählten Entitätstyp der Entitäts Liste gebunden ist. Wenn ein Benutzer den Filter anwendet, zeigt die Entitäts Liste nur die Datensätze an, die genau mit mindestens einem der ausgewählten verknüpften Datensätze übereinstimmen.

Dies unterscheidet sich von einem Nachschlage Satz. In der suchgruppe müssen Sie die verknüpften Entitäten, nach denen gefiltert werden soll, manuell angeben. Im dynamischen Nachschlage Satz muss nur die Beziehung angegeben werden, nach der gefiltert werden soll, und es wird eine Liste der Optionen basierend auf der angegebenen Ansicht verwandter Entitäten generiert.

![Einstellungen für die dynamische Suche](../media/set-dynamic-lookup.png "Einstellungen für die dynamische Suche")  

Der dynamische Nachschlage Satz verwendet die folgenden Optionen:

|**Name**                      |**Description** (Beschreibung)                                                                                                                                                                      |
|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Beziehung                  | Der Name der verknüpften Entität für den ausgewählten Entitätstyp der Entitäts Liste, nach dem gefiltert werden soll. Nur Entitäten mit einer 1: n-oder m:n-Beziehung mit dem ausgewählten Entitätstyp der Entitäts Liste werden als Optionen für diesen Filtertyp angezeigt.                                     |
| Anschauung                          | Die Ansicht (gespeicherte Abfrage), die als Quelle für die dynamische Liste der zu filternden Entitäten verwendet werden soll.                                                                                              |
| Spalte "Bezeichnung"                  | Das Feld aus der Ansicht, das den Namen der einzelnen Entitäten bereitstellt.                                                                                                                    |
| Suche nach der Beziehung Filtern | Gibt eine Beziehung zwischen der Entität an, die durch das Beziehungsfeld und den angemeldeten Benutzer angegeben wird. Wenn die durch das Beziehungsfeld angegebene Entität auch eine Beziehung zu einem Kontakt hat, können Sie die Liste der Filteroptionen auf die für den angemeldeten Benutzer bezogenen Werte eingrenzen.  |
| Anzeigename                  | Überschreiben Sie die Bezeichnung für den Filter, wenn die Entitäts Liste angezeigt wird. Standardmäßig wird dieser automatisch auf den Namen der ausgewählten Beziehung festgelegt.                            |

**Fetchxml-Filter**

Der Bereichs Filter kann entweder einen einfachen Text Feld Filter wie den Textfilter oder eine Reihe von Optionen wie die anderen Filtertypen erstellen. Mit dieser Option können Sie mit fetchxml praktisch jeden Filtertyp für die Entitäts Liste manuell erstellen.

![Filtereinstellungen für fetchxml](../media/set-fetchxml-filter.png "Filtereinstellungen für fetchxml")

Der fetchxml-Filter verwendet nur ein Attribut:

|**Name** |**Description** (Beschreibung)                            |
|----------|--------------------------------------------|
| FetchXML | Die XML-Anweisung, die den Filter darstellt. |

## <a name="entity-list-map-view"></a>Zuordnungs Ansicht für Entitäts Listen

Mithilfe von Entitäts Listen ist es möglich, eine Kartenansicht der Daten zu aktivieren und zu konfigurieren, unter [!INCLUDE[pn-bing](../../../includes/pn-bing.md)] Maps mit Suchfunktionen, um Orte in der Nähe einer Adresse zu finden. Wenn Sie Ihre Datensätze mit Koordinaten Werten für breiten-und Längengrad auffüllen und die in diesem Abschnitt aufgeführten Konfigurationsoptionen angeben, können Ihre Datensätze als Pushpins auf einer Karte gerendert werden. Alle Datensätze, die keinen breiten-oder Längengrad aufweisen, werden von der Suche ausgeschlossen. Beim erstmaligen Laden der Seite werden alle Datensätze im Anfangswert des Felds "Entfernungs Werte" (in Meilen oder km, abhängig von den angegebenen Entfernungs Einheiten) aus den standardmäßigen mittelbreiten-und standardmäßigen Längenkoordinaten angezeigt. Die angegebene Sicht wird ignoriert, wenn die Kartenansicht verwendet wird, und es wird eine Entfernungs Abfrage auf das DataSet angewendet, um die mappable-Ergebnisse zurückzugeben.
>[!Note] 
>Diese Option wird in der deutschen unabhängigen Cloud-Umgebung nicht unterstützt. Der Karten Ansichts Abschnitt wird in dieser Umgebung nicht angezeigt.


## <a name="entity-list-calendar-view"></a>Ansicht "Entitäts Listen Kalender"

Verwenden Sie die Kalenderansicht der Entitäts Liste, um eine Entitäts Liste als Kalender zu verwenden, wobei jeder einzelne Datensatz so konfiguriert ist, dass er als einzelnes Ereignis fungiert.

Zum Anzeigen von Datensätzen mithilfe eines Kalenders müssen diese Datensätze mindestens ein Datumsfeld enthalten. Damit Ereignisse genaue Start-und Endzeit haben, müssen die entsprechenden Felder vorhanden sein usw. Wenn diese Felder konfiguriert sind, wird im Portal eine Ansicht der Ansicht "Entitäts Liste" angezeigt.

## <a name="enhanced-view-filter-for-entity-lists"></a>Verbesserter Ansichts Filter für Entitäts Listen

Wenn diese Option aktiviert ist, kann eine Entität in einem odata-Feed veröffentlicht werden. Das odata-Protokoll ist ein Protokoll auf Anwendungsebene für die Interaktion mit Daten über die Rest-Webdienste. Daten aus diesem Feed können in einem Webbrowser angezeigt, von einer Client seitigen Webanwendung genutzt oder in [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)]importiert werden.

## <a name="entity-list-odata-feeds"></a>Entitäts Liste odata-Feeds

Sie können Entitäts Berechtigungen verwenden, wenn Sie Datensätze sichern möchten, aber wenn Sie einen Filter einfach als Teil des Satzes von Filteroptionen angeben möchten, der für den aktuellen Portalbenutzer relevant ist, können Sie die Funktion für die Entitäts Liste verwenden. Diese Funktion unterstützt das Filtern des aktuellen Benutzers, des übergeordneten Kontos oder der Website des aktuellen Benutzers in beliebiger Tiefe. Erstellen Sie einfach den Ansichts Filter so, dass er mit einem einzelnen Kontaktdaten Satz identisch ist, und der Code ersetzt seinen Wert durch den tatsächlichen Wert zur Laufzeit,&mdash;keine Werte für Felder im Abschnitt Filterbedingungen zugewiesen werden müssen.

> [!Note]
> Der veröffentlichte odata-Feed ist anonym und besitzt keine Autorisierungs Überprüfungen. Daher ist es wichtig, odata-Feeds nicht für Daten zu aktivieren, die für den Zugriff auf anonyme Portale ungeeignet sind.

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Portals](configure-portal.md)  
[Umleiten zu einer neuen URL in einem Portal](add-redirect-url.md)  
