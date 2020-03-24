---
title: Erstellen benutzerdefinierter Hilfeseiten | Microsoft-Dokumentation
description: Erstellen benutzerdefinierter Hilfeseiten auf UCI
ms.custom: ''
ms.date: 09/13/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: ''
caps.latest.revision: ''
author: matthewbolanos
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0ba852565acee10fc4c853eb185f552df6399fc9
ms.sourcegitcommit: d98dd90a7dda11f434a13a7f8976459856d6142b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/29/2020
ms.locfileid: "3093902"
---
# <a name="create-guided-help-for-your-unified-interface-app"></a>Erstellen Sie einen interaktiven Begleiter für Ihre App Einheitliche Oberfläche

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Verwenden Sie benutzerdefinierte Hilfebereiche und Aufgabenhilfen, um Ihrer Einheitliche Oberfläche Anwendung eine benutzerdefinierte, auf Ihr Unternehmen zugeschnittene Hilfefunktion, im Produkt zu bieten. Verwenden Sie benutzerdefinierte Hilfebereiche, um eine Entitäts-, Formular- und sprachspezifische Hilfe und Anleitung bereitzustellen, die Rich-Text-, Inhaltslinks, Bilder und Videoverknüpfungen enthält. 

> [!IMPORTANT]
> Benutzerdefinierte Hilfebereiche ersetzen die bisherige lernpfadgeführte Lernfunktion, die bei älteren Web-Client-Anwendungen verwendet wurde.

## <a name="custom-help-panes-and-learning-path"></a>Benutzerdefinierte Hilfebereiche und -Lernpfad
Die neue Implementierung des interaktiven Begleiters benutzerdefinierter Hilfebereiche unterscheidet sich von der vorherigen Funktion des interaktiven Lernpfadbegleiters. Beide Funktionen erlauben Ihnen die Erstellung benutzerdefinierter Hilfe für Ihre Anwendung. Allerdings werden benutzerdefinierte Hilfebereiche für die gängigsten Szenarien interaktiver Begleiter optimiert.   

Benutzerdefinierte Hilfebereiche bieten die folgenden Hauptfunktionen, die beim Lernpfad nicht verfügbar sind: 
- Frei definierbarer Rich-Text, einschließlich Aufzählungszeichen und Nummerierung.
- Sichtbar verknüpfte Trainermarkierungen und Hilfesprechblasen.
- Weitere Optionen für Videoquellen, einschließlich privater Quellen.
- Speicher des Hilfeinhalts im Common Data Service als Rahmen Ihrer Lösung. 

Benutzerdefinierte Hilfebereiche bieten nicht die folgenden Hauptfunktionen, die beim Lernpfad verfügbar sind: 
- Sequenzielle Hilfesprechblasen.
- Hilfeseiten pro Rolle.
- Hilfeseiten für ProGerät-Formfaktor, z. B. Smartphone. 

## <a name="prerequisites"></a>Voraussetzungen 
Zum Verfassen benutzerdefinierter Hilfebereiche müssen Sie Folgendes tun: 
- Version 9.1.0.10300 oder höher.
- Globales Erstellen, Lesen, Schreiben, Löschen, Anfügen und Anfügen an Berechtigungen auf der **Hilfeseite** Recht. Die Sicherheitsrollen Systemadministrator und Systemanpasser verfügen standardmäßig über diese Rechte.  
- [Ihre Umgebung muss die benutzerdefinierten Hilfebereiche aktiviert haben.](#enable-custom-help-panes-for-your-environment)

## <a name="enable-custom-help-panes-for-your-environment"></a>Benutzerdefinierte Hilfebereiche für Ihre Umgebung aktivieren.
1. Öffnen Sie eine modellgesteuerte App und wählen Sie dann in der Befehlsleiste **Einstellungen** ![Einstellungen](../model-driven-apps/media/powerapps-gear.png) > **Erweiterte Einstellungen** aus.
2. Gehen Sie zu **Einstellungen** > **System** > **Verwaltung**.  
3. Wählen Sie auf der **Verwaltungsseite** den Eintrag **Systemeinstellungen**.
4. Wählen Sie auf der Registerkarte **Allgemein** unter **Benutzerdefinierte Hilfe-URL einrichten** **Ja** für **Benutzerdefinierte Hilfebereiche und Aufgabenhilfen aktivieren**, und klicken Sie dann auf **OK**.

    > [!div class="mx-imgBorder"] 
    > ![Benutzerdefinierte Hilfebereiche aktivieren](media/enable-custom-help-panes.png "Benutzerdefinierte Hilfebereiche aktivieren")

> [!IMPORTANT]
> Sie können benutzerdefinierte Hilfebereiche oder die benutzerdefinierte Hilfe aktiveren, aber nicht beide gleichzeitig. Bestätigen Sie, dass **Benutzerdefinierte Hilfe für anpassbare Entitäten verwenden** und **Parameter an URL anfügen** beide auf **Nein** gesetzt wurden.  
 
## <a name="context-sensitive-custom-help"></a>Kontextbezogene benutzerdefinierte Hilfe
Jeder Hilfebereich für diese Kontexte ist eindeutig: 
- Anwendung 
- Entität
- Formular 
- Language   

## <a name="help-pane-navigation"></a>Hilfebereichnavigation
Standardmäßig bleibt ein Hilfebereich geöffnet und in dem Hilfsinhalt, mit dem Sie ihn zuerst geöffnet haben, auch wenn Sie zu einem anderen Formular navigieren. Auf diese Weise bleibt der Hilfeinhalt erhalten, während Sie die Benutzer zu verschiedenen Teilen der App leiten. 

### <a name="to-author-help-pane-content"></a>Hilfebereichsinhalt verfassen
1.  Um einen Hilfebereich anzuzeigen öffnen Sie eine modellgesteuerte App und wählen Sie dann **Hilfe** auf der Befehlsleiste aus. 

    ![Hilfe](media/help-command.png)   
2.  Klicken Sie im Hilfebereich auf die vertikalen Auslassungszeichen und wählen Sie dann **Bearbeiten** aus. 

    ![Hilfe bearbeiten](media/help-edit-command.png)
    
    Der Hilfebereich ist jetzt im Bearbeitungsmodus und der Cursor ist auf dem Hilfebereichstitel positioniert.
3.  Aus dem Bearbeitungsbereich können Sie die folgenden Aufgaben ausführen: 
    - Geben Sie den Text ein, indem Sie direkt im Hilfebereich schreiben. 
    - Formatieren Sie Text, indem Sie die Rich-Text-Befehle, wie Fett, Kursiv, Durchgestrichen verwenden und Listen erstellen. 
    - Wählen Sie die Registerkarte **Einfügen** aus, um Video, Bilder, Links, Trainermarkierungen und Sprechblasenhilfe hinzuzufügen. 
<!-- confirm the image is safe for use
    > [!div class="mx-imgBorder"] 
    > ![Custom help pane edit](media/custom-help-pane-edit.png)  -->
4.  Wählen Sie **Speichern** aus, um Ihre Änderungen zu speichern.  

### <a name="free-form-text"></a>Freihandtext
Text kann an einer beliebigen Stelle im Hilfebereich platziert werden. Geben Sie Freihandtext vor, in oder nach Abschnitten ein. Text unterstützt die Schriftartformate Fett, Kursiv, Unterstrichen und Durchgestrichen. Ausschneiden, Kopieren und Einfügen können ebenso wie Rückgängig machen über mehrere Schritte verwendet werden. 

### <a name="bullets-and-numbered-lists"></a>Aufzählungszeichen und nummerierte Listen
Das Auswählen des Aufzählungszeichens oder Zahlensymbols wechselt auf der aktuellen Schreibzeile, um diese als Aufzählung oder Nummerierung zu formatieren. Wenn Sie in einer Liste mehrere Zeilen ausgewählt haben, wird jede Zeile aufgezählt oder nummeriert. Das Tabulieren und Einrücken führt zur Unternummerierung einer Zeile innerhalb der Liste.  

### <a name="sections"></a>Abschnitte
Ein Abschnitt ist ein reduzierbares Textfeld.  Sie können Links oder Freihandtext darin eingeben. Verwenden Sie einen Abschnitt, um ähnliche Elemente zu gruppieren. Ein Abschnitt kann standardmäßig geöffnet oder reduziert werden. 

### <a name="video-and-static-images"></a>Video und statische Bilder
Sie können Videos und statische Bilder in Ihren Hilfebereich einfügen. Videos und Bilder sind Links zu Internet-Inhalten. Benutzerdefinierte Hilfebereiche speichern nicht die Video- und Bilddateien in Ihrem Hilfebereich. Wenn der Hilfebereich geöffnet ist bringen benutzerdefinierte Hilfebereiche Inhalte aus dem Link, um sie anzuzeigen. Sie können einen Link mit einem Video Microsoft Stream verwenden, wenn Sie auf korporativen privaten Inhalt verweisen möchten. 

> [!TIP]
> Vergessen Sie nicht, die Link-URL für das gewünschte Video oder Bild zu kopieren, damit Sie es in Ihren Hilfebereich einfügen können. 

Benutzerdefinierte Hilfebereiche unterstützen die folgenden Videoquellen:
- Microsoft Stream (für privaten Inhalt verwenden) 
- YouTube
- Facebook
- Vimeo


### <a name="links"></a>Links
Links können sich auf Websites beziehen und im gleichen Fenster (Standard) oder in einem separaten Fenster öffnen. Die Möglichkeit der Verknüpfung zu einer vorhandenen Hilfeseite ist noch nicht aktiviert.   

### <a name="balloons-and-coach-marks"></a>Sprechblasen und Trainermarkierungen
Sprechblasen und Trainermarkierungen können verwendet werden, um auf bestimmten Benutzeroberflächenelementen zu verweisen. Eine Sprechblase kann Text enthalten. Eine Trainermarkierung hebt einfach ein Element mit einem Trainermauszeiger hervor. Eine Methode, mehrere Benutzeroberflächenelemente sequentiell zu veranschaulichen ist die Sammlung von Links in einer Liste, die ein Benutzer auswählen kann. Beispielsweise:

1. Verknüpfung zum ersten Benutzeroberflächenelement mit Anweisungen oder Kommentaren.
2. Verknüpfung zum zweiten Benutzeroberflächenelement mit Anweisungen oder Kommentaren.
3. Verknüpfung zum dritten Benutzeroberflächenelement mit Anweisungen oder Kommentaren.

Ein Benutzer kann ein Element entweder der Reihe nach auswählen oder zu einem bestimmten Element zurückgehen und es hervorheben.

## <a name="solutions-and-custom-help-pane-content"></a>Lösungen und benutzerdefinierter Hilfebereichsinhalt
Alle Inhalte der Hilfe werden in einer Hilfeseitenkomponente in Common Data Service als Teil Ihrer Lösung gespeichert. Wenn Sie eine Lösung von einer Umgebung auf eine andere verschieben, wie vom Versuch zur Produktion, können Sie definieren, dass Ihre Hilfedatensätze exportiert werden, damit sie in der Lösung enthalten sind. Dies ermöglicht Ihnen, Ihren Hilfeinhalt konsistent mit Funktionen in Ihrer Lösung zu halten, wenn er in verschiedene Umgebungen verschoben wird. Als Bestandteil Ihrer Lösung unterstützen benutzerdefinierte Hilfebereiche alle Funktionen der Standardlösung von ALM.

### <a name="moving-content-via-solutions"></a>Inhalt über Lösungen verschieben
Standardmäßig erscheinen alle neuen Hilfeseiten in der Standardlösung. Wenn Sie Ihre Inhalte auf eine andere Umgebung verschieben möchten, fügen Sie zunächst Ihre vorhandenen Hilfeseiten einer nicht verwalteten Lösung hinzu, bevor Sie sie exportieren. um eine Hilfeseite einer nicht verwalteten Lösung hinzufügen, gehen Sie folgendermaßen vor:

1. Navigieren Sie zu einer nicht verwalteten Lösung.
2. Wählen Sie **In klassischen Modus wechseln** aus den Auslassungszeichen in der Befehlsleiste.
3. Wählen Sie **Vorhandenes Element hinzufügen**.
4. Wählen Sie **Hilfeseite**.
5. Wählen Sie die Hilfeseiten aus, die Sie hinzufügen möchten, und wählen Sie dann **OK** aus.

> [!NOTE]
> Derzeit können Sie vorhandene Hilfebereiche einer nicht verwalteten Lösung im modernen Projektmappen-Explorer nicht hinzufügen. 


## <a name="help-page-documentation-automation"></a>Automatisierung der Hilfeseitendokumentation
Sie sollten Ihren Inhalt in einem Quellcodeverwaltungssystem sichern oder speichern. Sie sollten auch möglicherweise Tools zur Dokumentationsautomatisierung wie Übersetzungstools oder Prüffunktionen für Hilfebereichsinhalte verwenden. Benutzerdefinierte Hilfebereichsdaten werden direkt in Common Data Service gespeichert und können deshalb exportiert und importiert werden.  

Benutzerdefinierte Hilfebereiche unterstützen ein benutzerdefiniertes XML-Format. Dieses Format wird unten dokumentiert. Weitere Informationen: [Benutzerdefinierte Hilfe XML-Definition](#custom-help-xml-definition)  

Beim exportieren wird jede Hilfeseite als separate Datei exportiert.   

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
In diesem Abschnitt werden häufig gestellte Fragen zu benutzerdefinierten Hilfeseiten behandelt. 

### <a name="are-custom-help-pages-the-same-as-customizable-help"></a>Sind benutzerdefinierte Hilfeseiten identisch mit anpassbarer Hilfe?

Benutzerdefinierte Hilfebereiche und Aufgabenhilfen sind eine Option im Abschnitt **Benutzerdefinierte Hilfe-URL festlegen** der Systemeinstellungen. Benutzerdefinierte Hilfebereiche und Aufgabenhilfen aktivieren einen anpassbaren Hilfebereich, der rechts neben dem Formular des Benutzers erscheint.  Die anderen Optionen in diesen Systemeinstellungen zum Einstellen des benutzerdefinierten Hilfeabschnitts enthalten die anpassbaren Hilfefunktionen. Mit der anpassbaren Hilfe ist es möglich, die standardmäßige Apps-Hilfe zu überschreiben und Benutzer in Ihrer Organisation an eine andere URL für die Hilfe zu verweisen. Alternativ können Sie auch die Hilfe für eine stark angepasste Entität überschreiben, damit Sie Ihren Workflow besser beschreiben können.

Weitere Informationen zu anpassbaren Hilfen finden Sie unter [Anpassbare Hilfe aktivieren und verwenden](../model-driven-apps/use-customizable-help.md).


### <a name="how-do-i-migrate-my-data-from-learning-path-to-custom-help-pages"></a>Wie migriere ich meine Daten vom Lernpfad zu den benutzerdefinierten Hilfeseiten? 
Der Lernpfad enthält zwei Arten von Hilfe: Hilfebereiche und sequenzielle Hilfesprechblasen. Die sequenziellen Hilfesprechblasenspeicherorte sind tief in der bestehenden Benutzeroberfläche des Webclient integriert und lassen sich somit nicht zu den neuen benutzerdefinierten Hilfebereichen übertragen.  

Je nachdem, wieviel Text Ihr interaktiver Begleiter enthält, können Sie die Informationen möglicherweise am einfachsten direkt von der Lernpfadbenutzeroberfläche zur neuen benutzerdefinierten Hilfebereichsbenutzeroberfläche kopieren. Sie können jedoch Ihre Lernpfadhilfeinhalt auch exportieren.  Die einfachste Methode zum Exportieren Ihres Inhalts ist die Verwendung der Funktion **Lernpfad** > **Inhaltsbibliothek** > **Lokalisieren** > **Exportieren**. Wählen Sie die gewünschten Datensätze aus, und exportieren Sie diese dann. Damit wird eine XLIFF-Datei für jeden Hilfebereich und Aufgabenhilfe erstellt.  Verwenden Sie dann einen öffentlich verfügbar XLIFF-Editor oder XLIFF zu HTML-Wandler, um Ihren Inhalt abzurufen. 

## <a name="custom-help-xml-definition"></a>XML-Definition für benutzerdefinierte Hilfe
Dieser Abschnitt beschreibt die benutzerdefinierte Hilfe XML-Definition. 

### <a name="pphml"></a>PPHML

```
<pphml>
    <h1>FAQ</h1>
    <collapsible title="What is PPHML?">
        <p>PPHML is a domain specific language for help content. It is used to create help content that includes elements such as images, videos, balloons, coach marks, etc.</p>
    </collapsible>
    <collapsible title="What does PPHML stand for?">
        <p>PPHML stands for Power Platform Help Markup Language</p>
    </collapsible>
</pphml>
```

#### <a name="definition-and-usage"></a>Definition und Verwendung

Das `<pphml>`-Element sagt dem Hilfebrowser, dass es sich hier um ein PPHML-Dokument handelt.

Das `<pphml>`-Element stellt den Stamm eines PPHML-Dokuments dar.

Das `<pphml>`-Element ist der Container für alle anderen PPHML-Elemente.

### <a name="title"></a>Titel
Stellt einen Titel in einer Hilfeseite dar.

```
<h1>This will be displayed at the top of the help page</h1>
```

#### <a name="definition-and-usage"></a>Definition und Verwendung
Das **`<h1>`**-Element definiert den Titel einer Hilfeseite.

`<h1>` Das muss das erste interne Element sein `<pphml>`.

### <a name="image"></a>Bild
Stellt ein Bild in einer Hilfeseite dar.

```
<img src="smiley.gif" alt="Smiley face" title="Smiley face"/>
```

#### <a name="definition-and-usage"></a>Definition und Verwendung
Das **`<img>`**-Element bettet ein Bild in einer Hilfeseite ein.

#### <a name="attributes"></a>Attribute
- `src`: Gibt die URL eines Bildes an. Dieses Attribut ist erforderlich.

- `title`: Gibt einen Titel an, der zusammen mit dem Bild angezeigt wird, in der Regel als darauf zeigende QuickInfo.

- `alt`: Gibt einen Alternativtext für ein Bild an. Dieser Text wird von Screenreadern verwendet.

### <a name="video"></a>Video
Stellt ein Video in einer Hilfeseite dar.

```
<video src="https://www.youtube.com/watch?v=WSWmn7WM3i4" />
```

#### <a name="definition-and-usage"></a>Definition und Verwendung

Das **`<video>`**-Element bettet ein Video, wie etwa ein Tutorial oder einen Schulungsfilm, in einer Hilfeseite ein.

##### <a name="supported-sources"></a>Unterstützte Quellen

- Microsoft Stream
- YouTube
- Facebook
- Vimeo

#### <a name="attributes"></a>Attribute
- `src`: Gibt die URL des Videos an. Dieses Attribut ist erforderlich.

- `allowFullScreen`: Gibt an, ob der Benutzer das Video zur Vollbildanzeige wechseln kann. Mögliche Werte lauten "True" oder "False". Dieses Attribut wird nicht für alle Videoquellen unterstützt.

- `autoplay`: Gibt an, dass die Wiedergabe des Videos beginnt, sobald die Hilfeseite geladen wird. Mögliche Werte lauten "True" oder "False". Dieses Attribut wird nicht für alle Videoquellen unterstützt.

- `startTime`: Spezifiziert, in Sekunden, ab welchem Punkt die Wiedergabe des Videos startet.

### <a name="paragraph"></a>Absatz
Stellt einen Abschnitt in einer Hilfeseite dar.

```
<p>This is some text in a paragraph.</p>
```

#### <a name="definition-and-usage"></a>Definition und Verwendung
Das **`<p>`**-Element definiert einen Absatz.

Text in einem Absatzes kann folgendermaßen hervorgehoben werden:
- Fett, mit `<strong>`-Element
- Kursiv, mit `<em>`-Element
- Durchgestrichen, mit `<del>`-Element
- Unterstrichen, mit `<u>`-Element

Diese Hervorhebungen können kombiniert werden. Beispielsweise können Sie ein Textfragment darstellen, das sowohl fett als auch unterstrichen ist.

### <a name="bulleted-list"></a>Aufzählung
Stellt eine Aufzählung in einer Hilfeseite dar.

```
<ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ul>
```

#### <a name="definition-and-usage"></a>Definition und Verwendung
Das **`<ul>`**-Element definiert eine Aufzählung.

Verwenden Sie das `<ul>`-Element zusammen mit dem `<li>`-Element, um Aufzählungen zu erstellen.

### <a name="numbered-list"></a>Nummerierte Liste
Stellt eine nummerierte Liste in einer Hilfeseite dar.

```
<ol>
    <li>First step</li>
    <li>Second step</li>
    <li>Third step</li>
</ol>
```

#### <a name="definition-and-usage"></a>Definition und Verwendung
Das **`<ol>`**-Element definiert eine geordnete (nummerierte) Liste.
Verwenden Sie die `<ol>`-Markierung zusammen mit dem `<li>`-Element, um nummerierte Listen zu erstellen.

### <a name="collapsible"></a>Reduzierbar
Stellt einen reduzierbaren Abschnitt in einer Hilfeseite dar.

```
<collapsible title="This is a Section">
    <p>This is a paragraph inside a section</p>
    <img src=smiley.gif" title="This is an image inside a section" />
</collapsible>
```

#### <a name="definition-and-usage"></a>Definition und Verwendung
Das **`<collapsible>`**-Element definiert einen Abschnitt des Inhalts, den der Benutzer bei Bedarf ein- oder ausblenden kann.

#### <a name="attributes"></a>Attribute
- `collapsed`: Gibt an, ob der Abschnitt zuerst reduziert oder erweitert wird. Mögliche Werte sind "True" (reduziert) oder "False" (erweitert).

### <a name="link"></a>Link
Stellt einen Link in einer Hilfeseite dar.

Verknüpfung mit einer Website, die in einem neuen Browserfenster geöffnet wird:

```
<a href="https://www.microsoft.com" target="_blank">Microsoft Home Page</a>
```

Verknüpfung mit einer anderen Hilfeseite:

```
<a href="./LearnMore">Learn More</a>
```

#### <a name="definition-and-usage"></a>Definition und Verwendung
Das `<a>`-Tag definiert einen Link, der dem Benutzer ermöglicht, von einer Hilfeseite zu einer Website oder einer anderen Hilfeseite zu navigieren.

#### <a name="attributes"></a>Attribute

- `href`: Gibt die URL der Website oder einer Hilfeseite an, zu der navigiert werden soll. Dieses Attribut ist erforderlich.
- `target`: Gibt an, wo die verknüpfte URL geöffnet werden soll.
   - Sofern nicht vorhanden oder `_self`, wird angenommen, dass der Link zu einer anderen Hilfeseite verweist und im Hilfebrowser geöffnet wird.
   - Wenn `_blank`, wird der Link in einem neuen Browserfenster geöffnet.
   - Wenn `_top`, wird der Link im aktuellen Browserfenster geöffnet.
   - Wenn der Wert der Name eines `iframe` ist, wird der Link in dem IFrame geöffnet.

### <a name="coach-mark"></a>Trainermarkierung
Stellt eine Trainermarkierung in einer Hilfeseite dar.

```
<coachmark target="#my-html-button">Click to highlight the HTML element with id [my-html-button]</coachmark>
```

#### <a name="definition-and-usage"></a>Definition und Verwendung
Eine Trainermarkierung ist ein interaktives Element, das verwendet werden kann, um die Aufmerksamkeit des Benutzers auf einen bestimmten Punkt in der Benutzeroberfläche der Anwendung, die den Hilfebrowser hostet, zu lenken.

#### <a name="attributes"></a>Attribute

- `target`: [CSS Auswahl](https://www.w3schools.com/cssref/css_selectors.asp), die das HTML-Element angibt, über dem die Trainermarkierung angezeigt wird. Dieses Attribut ist erforderlich.

### <a name="balloon"></a>Sprechblase
Stellt eine Sprechblase in einer Hilfeseite dar.

```
<balloon target="#my-html-button" title="This button submits the form" details="Please click this button to continue and submit the form">Click to show a balloon over the HTML element with id [my-html-button]</balloon>
```

#### <a name="definition-and-usage"></a>Definition und Verwendung
Eine Sprechblase ist ein interaktives Element, das verwendet werden kann, um dem Benutzers bei der Ausführung einer Aktion in der Benutzeroberfläche der Anwendung, die den Hilfebrowser hostet, hilft.

#### <a name="attributes"></a>Attribute
- `target`: CSS-Auswahl, die das HTML-Element angibt, über dem der Sprechblasenlink angezeigt wird. Dieses Attribut ist erforderlich.
- `title`: Gibt den Titel der Sprechblase an.
- `details`: Gibt den Inhalt an, der in der Sprechblase angezeigt werden soll.


