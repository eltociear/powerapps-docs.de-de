---
title: Definieren von Entitäts Formularen | MicrosoftDocs
description: Anweisungen zum Erstellen von Entitäts Formularen in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 79e6f02f9a13f1c828efe5c472d267e707b09576
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552702"
---
# <a name="about-entity-forms"></a>Informationen zu Entitäts Formularen

Eine datengesteuerte Konfiguration, mit der Endbenutzer ein Formular zum Erfassen von Daten im Portal hinzufügen können, ohne dass ein Entwickler das Formular im Portal verwenden muss, werden Entitäts Formulare in Common Data Service erstellt und dann im Portal in Webseiten abgelegt oder in Verbindung mit unter Raster und Entitäts Listen zum Erstellen kompletter Webanwendungen. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [zu Entitäts Listen](entity-lists.md) 

![Formular kontaktieren](../media/contact-us-form.png "Formular kontaktieren")  

## <a name="add-a-form-to-your-portal"></a>Hinzufügen eines Formulars zum Portal

Das Formular Entität enthält Beziehungen zu Webseiten und zusätzliche Eigenschaften, um die Initialisierung des Formulars im Portal zu steuern. Die Beziehung zu Webseiten ermöglicht das dynamische Abrufen der Formular Definition für einen bestimmten Seiten Knoten innerhalb der Website. 

Um vorhandene Entitäts Formulare anzuzeigen oder neue Entitäts Formulare zu erstellen, öffnen Sie die [Portal Verwaltungs-App](configure-portal.md) , und navigieren Sie zu **Portale** &gt; **Entitäts Formularen**.

Beim Erstellen eines neuen Entitäts Formulars besteht der erste Schritt darin, den Namen der **Entität** und des **Formulars** zu entscheiden, die Sie rendern, zusätzlich zum **Modus: INSERT, Edit oder Read Only**. Der ausgewählte Modus bestimmt, ob Sie einen neuen Datensatz aus dem Portal erstellen, einen vorhandenen Datensatz bearbeiten oder nur Informationen zu einem Datensatz im Portal anzeigen.

> [!Note]
> - Ein **Entitäts Formular** muss einer Webseite für eine bestimmte Website zugeordnet sein, damit das Formular innerhalb der Site angezeigt werden kann.
> - Die unter Raster der Verbindungs Entitäten werden in Entitäts Formularen nicht unterstützt. Wenn Sie dem Formular mithilfe des Formular-Designers ein unter Raster der Verbindungs Entität hinzufügen, werden Fehlermeldungen angezeigt, wenn Sie das Formular im Portal Rendering und die Verbindungs Entität verwenden.
> - Doppelte Felder, Optionen für Mehrfachauswahl, benutzerdefinierte Steuerelemente und Geschäftsregeln werden in Entitäts Formularen nicht unterstützt.
> - Geschäftsregeln und die Client-API können Gesperrte Felder in einem schreibgeschützten Formular aktivieren.
> - Wenn Sie ein Entitäts Formular im Einfügemodus erstellen, können Sie die Ausrichtung einer Schaltfläche nicht ändern oder eine Aktions Schaltfläche oberhalb des Entitäts Formulars platzieren.
> - Wenn Sie ein Nachschlage Steuerelement als Dropdown Liste im Formular darstellen, funktioniert der Filter für verknüpfte Datensätze nicht.

Die dem Entitäts Formular zugeordneten Webseiten können angezeigt werden, indem Sie den Link **Web Pages** auswählen, der in den **zugehörigen** Navigationslinks im linken Menü aufgeführt ist.

Beim Erstellen oder Bearbeiten einer Webseite kann ein **Entitäts Formular** im Suchfeld angegeben werden, das im Formular der Webseite bereitgestellt wird.

Die verschiedenen vom Portal verwendeten Masterseiten enthalten Deklarationen des **entityform** -Server Steuer Elements. Beim Rendern der Webseite, die die Seitenvorlage Page (~/Pages/Page.aspx) oder Full Page (~/pages/fullpage.aspx) enthält, bestimmen die Steuerelemente, ob die Entitäts Formular Suche einen Wert enthält. in diesem Fall wird das Formular gerendert.

## <a name="secure-your-forms"></a>Sichern Ihrer Formulare

Zum Schutz Ihrer Formulare müssen Sie Entitäts Berechtigungen erstellen, die den Zugriff und den Besitz der Datensätze gemäß Webrollen bestimmen. Wenn ein Benutzer in ein Entitäts Formular gelangt und nicht über die erforderlichen Berechtigungen verfügt, wird eine Fehlermeldung angezeigt. Um Berechtigungen für ein Entitäts Formular zu aktivieren, legen Sie **Entitäts Berechtigungen aktivieren** auf true fest. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Webrollen für Portale erstellen](create-web-roles.md).  

## <a name="entity-form-attributes-and-relationships"></a>Entitäts Formular Attribute und-Beziehungen

|Name|Beschreibung|
|-----|----------|
|Name|Der beschreibende Name des Datensatzes. Dieses Feld ist erforderlich.|
|Entitäts Name|Der Name der Entität, aus der das Formular geladen wird. Dieses Feld ist erforderlich.|
|Formularname| Der Name des Formulars in der Ziel Entität, die gerendert werden soll. Dieses Feld ist erforderlich.|
|Registerkarten Name|  Optionaler Name einer Registerkarte in einem Formular für eine angegebene Entität, die gerendert werden soll.|
|Modus|Einer der folgenden Werte:<ul><li>Setze</li><li>Bearbeiten</li><li>ReadOnly</li></ul>Durch die Auswahl von _Einfügen_ wird angegeben, dass das Formular beim Einreichen einen neuen Datensatz einfügen soll. Durch das Angeben von _Edit_ wird angegeben, dass das Formular einen vorhandenen Datensatz bearbeiten soll Durch _die Auswahl von_ "schreibgeschützt" wird angegeben, dass das Formular das nicht bearbeitbare Formular eines vorhandenen Datensatzes Die Felder " _Bearbeiten_ " und "schreibgeschützt _" erfordern,_ dass ein Quelldatensatz vorhanden ist, und Parameter, die in den Feldern "Daten Satz Quellentyp" und "Datensatz-ID-Abfrage Zeichenfolge-Parameter Name" angegeben sind.|
|Quelltyp aufzeichnen|Einer der folgenden Werte:<ul><li>Abfrage Zeichenfolge</li><li>Aktueller Portal Benutzer</li><li>Dem aktuellen Portal Benutzer zugeordneter Datensatz</li></ul>Die Auswahl der _Abfrage Zeichenfolge_ erfordert einen Parameternamen, der in der Abfrage Zeichenfolge der URL für das Formular bereitgestellt werden muss. Dies kann im Feld "Abfrage Zeichenfolgen-Parameter Name" für Datensatz-ID angegeben werden.<br>Wenn Sie _Aktueller Portal Benutzer_ auswählen, wird der Benutzerdaten Satz des Portals für den aktuellen authentifizierten Benutzer abgerufen.<br>Durch Auswählen des _dem aktuellen Portal Benutzer zugeordneten Daten_ Satzes wird der Benutzerdaten Satz des Portals für den aktuellen authentifizierten Benutzer abgerufen, und anschließend wird der Datensatz für die angegebene Beziehung entsprechend der Angabe im Feld "Beziehungs Name" abgerufen.|
|Name der Abfrage Zeichenfolge für Datensatz-ID| Ein Parameter Name, der in der Abfrage Zeichenfolge der URL der Webseite bereitgestellt wird, die dieses Entitäts Formular enthält.|
|Beziehungs Name| Erforderlich, wenn der Daten Satz Quellentyp Datensatz dem aktuellen Portal Benutzer zugeordnet ist. Der logische Name der Beziehung zwischen dem aktuellen Benutzerdaten Satz des Portals und dem Zieldatensatz. Dies muss den gleichen Entitätstyp zurückgeben, der im Feld Entitäts Name angegeben ist.|
|Create if NULL zulassen|  Ein optionaler boolescher Wert, der verfügbar ist, wenn der Datensatz-Quellentyp Datensatz dem aktuellen Portal Benutzer zugeordnet ist. Gibt an, dass, wenn der verknüpfte Datensatz nicht vorhanden ist, der Benutzer das erste Mal erstellen darf. andernfalls wird eine Ausnahme ausgelöst, wenn der Datensatz nicht bereits vorhanden ist, weil das Formular einen Datensatz für die Datenbindung benötigt.|
|Aktivieren von Entitäts Berechtigungen| Bewirkt, dass das Formular Entitäts Berechtigungen respektiert. Der Standardwert ist aus Gründen der Abwärtskompatibilität falsch. Wenn der Wert auf true festgelegt ist, sind explizite Berechtigungen für jeden Benutzer erforderlich, der auf das Formular zugreifen möchte.|
|||

### <a name="form-options"></a>Formular Optionen

|Name|Beschreibung|
|----|---------|
|Hinzufügen von CAPTCHA|   Zeigt CAPTCHA an.|
|Anzeigen von CAPTCHA für authentifizierte Benutzer|  Zeigt CAPTCHA für authentifizierte Benutzer an.|
|Validierungs Gruppe|  Der Gruppenname, der Eingabe Steuerelementen zum Auswerten gültiger Eingaben benannter Gruppen zugewiesen wird.|
|Schritte zur automatischen Generierung von Registerkarten| Gibt an, dass mehrere Registerkarten in einem Entitäts Formular angezeigt werden, wobei jede Registerkarte als sequenzieller Schritt beginnend mit der ersten Registerkarte angezeigt wird Standardmäßig ist diese Option nicht ausgewählt. Der Standardwert gibt an, dass für den aktuellen Schritt nur eine Registerkarte oder ein Formular gerendert werden soll. Wenn der Registerkarten Name nicht angegeben wird, wird die erste Registerkarte angezeigt.|
|Webressourcen Inline Rendering|   Entfernt das IFRAME, das eine Webressource in einem Entitäts Formular umfasst.|
|Quick Infos aktiviert|  Die QuickInfo wird mithilfe der Beschreibung des Attributs für die Ziel Entität festgelegt.|
|Nicht unterstützte Felder anzeigen|   Zurzeit werden alle Felder unterstützt. Dies ist für potenzielle Änderungen reserviert Common Data Service die möglicherweise an Feldtypen vorgenommen werden.|
|Empfohlene Felder nach Bedarf festlegen|    Macht alle Attribute erforderlich, deren Feld Anforderungs Ebene auf "geschäftlich empfohlen" festgelegt ist.|
|Alle Felder erforderlich machen|  Macht alle Felder unabhängig von der Anforderungs Ebene des Felds erforderlich.|
|Überprüfungs Zusammenfassungs-CSS-Klasse|  Der CSS-Klassenname, der der Validierungs Zusammenfassung zugewiesen ist. Der Standardwert ist "Validierung-Zusammenfassungs Warnung-Fehler Warnung-Block"|
|Validierungs Zusammenfassungs Links aktivieren|   Der boolesche Wert true oder false, der angibt, ob Anker Verknüpfungen in der Validierungs Zusammenfassung gerendert werden sollen, um zu dem Feld zu scrollen, das einen Fehler enthält. Der Standardwert ist "true".|
|Link Text für die Validierungs Zusammenfassung|  Die den Überprüfungs Zusammenfassungs Links zugewiesene Bezeichnung. Der Standardwert ist "hier klicken".|
|Header Text für Validierungs Zusammenfassung|    Die Bezeichnung, die dem Validierungs Zusammenfassungs Header zugewiesen ist.|
|Anweisungen|  Anweisungen zum Arbeiten mit dem Formular.|
|Meldung "Datensatz nicht gefunden"|  Die Meldung, die angezeigt werden soll, wenn ein Datensatz nicht gefunden wird.|
|||

### <a name="on-success-settings"></a>Bei Erfolgs Einstellungen

|Name|Beschreibung|
|----|----------|
|Bei Erfolg|    Einer der folgenden Werte:<ul><li>Erfolgsmeldung anzeigen (Standard)</li><li>Ausrichten</li></ul>|
|Formular bei Erfolg ausblenden|  Erfordert bei erfolgreicher Festlegung, dass die Erfolgsmeldung angezeigt wird. Wenn diese Option ausgewählt ist, wird das Formular nach erfolgreicher Übermittlung des Formulars ausgeblendet.|
|Erfolgsmeldung|   Erfordert bei erfolgreicher Festlegung, dass die Erfolgsmeldung angezeigt wird. Die Meldung, die dem Benutzer nach erfolgreicher Übermittlung angezeigt wird. Wenn kein Wert angegeben ist, wird eine Standardmeldung (Übermittlung erfolgreich abgeschlossen) angezeigt. Für jedes Sprachpaket, das für die Organisation installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann.|
|Externe URL|Erfordert bei erfolgreicher Umleitung eine Umleitung. Geben Sie eine URL für eine externe Ressource im Web an.
|oder Webseite|Erfordert bei erfolgreicher Umleitung eine Umleitung. Wählen Sie eine Webseite auf der aktuellen Website aus.|
|Vorhandene Abfrage Zeichenfolge anfügen|  Erfordert bei erfolgreicher Umleitung eine Umleitung. Wenn diese Option ausgewählt ist, werden die vorhandenen Abfrage Zeichen folgen Parameter vor der Umleitung der Ziel-URL hinzugefügt.|
|Datensatz-ID an Abfrage Zeichenfolge anfügen|  Erfordert bei erfolgreicher Umleitung eine Umleitung. Wenn diese Option ausgewählt ist, wird die ID des erstellten Datensatzes an die Abfrage Zeichenfolge der URL angehängt, an die umgeleitet wird.|
|Name der Abfrage Zeichenfolge für Datensatz-ID|     Erfordert bei erfolgreicher Umleitung eine Umleitung. Der Name des ID-Parameters in der Abfrage Zeichenfolge der URL, an die umgeleitet wird.|
|Benutzerdefinierte Abfrage Zeichenfolge anfügen|    Erfordert bei erfolgreicher Umleitung eine Umleitung. Eine benutzerdefinierte Zeichenfolge, die an die vorhandene Abfrage Zeichenfolge der Umleitungs-URL angefügt werden kann.|
|Attribut Wert an Abfrage Zeichenfolge anfügen-Parameter Name|   Erfordert bei erfolgreicher Umleitung eine Umleitung. Ein Name, der an den Parameter übergeben wird, der mit dem Attribut Wert der Ziel Entität korreliert, der an die Abfrage Zeichenfolge der Umleitungs-URL angefügt wird.|
|Attribut Wert an Abfrage Zeichenfolge anfügen-logischer Name des Attributs|Erfordert bei erfolgreicher Umleitung eine Umleitung. Ein logischer Name eines Attributs in der Ziel Entität, um den Wert zu erhalten, der an die Abfrage Zeichenfolge der Umleitungs-URL angehängt werden soll.|
|||

### <a name="additional-settings"></a>Zusätzliche Einstellungen

|Name|Beschreibung|
|----|----------|
|Aktuellen Portal Benutzer zuordnen| Gibt an, dass der aktuell angemeldete Benutzer Datensatz dem Ziel Entitäts Daten Satz zugeordnet werden soll.|
|Benutzer Such Attribut für das Ziel Entitäts Portal|    Der logische Name des Attributs in der Ziel Entität, in der der Portalbenutzer gespeichert wird.|
|Ist Aktivitäts Partei| Boolescher Wert, der angibt, ob das Ziel Entitäts Portal-Benutzer Such Attribut ein Aktivitäts parteientyp ist.|
|Datei anfügen|   Überprüfen Sie, ob das Formular ein Dateiuploadsteuerelement am unteren Rand des Formulars enthalten soll, damit eine Datei an den Datensatz angefügt werden kann.|
|File Storage Speicherort anfügen|  Optionen: Hinweis Anlage, Azure BLOB Storage. Wenn Ihre Organisation für die Verwendung von Azure Storage konfiguriert ist, können Sie dort hochgeladene Dateien für dieses Entitäts Formular speichern. Andernfalls werden Dateien, die als Hinweis Anlagen gespeichert werden.|
|Mehrere Dateien zulassen|Boolescher Wert, der angibt, ob der Benutzer mehr als eine Datei hochladen kann.|
|erst|    Das ACCEPT-Attribut gibt die MIME-Typen von Dateien an, die der Server durch Datei Upload akzeptiert. Wenn Sie mehr als einen Wert angeben möchten, trennen Sie die Werte durch ein Komma (z. b. Audiodatei/ *, Video/* , Bild/*).|
|Bezeichnung| Der neben dem Dateiuploadsteuerelement angezeigte Text. Für jedes Sprachpaket, das für die Organisation installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann.|
|Datei anfügen erforderlich| Macht die Anlage einer Datei erforderlich, damit der Vorgang fortgesetzt werden kann.|
|Erforderliche Fehlermeldung|Die während der Formular Validierung angezeigte Meldung, wenn erforderlich ist, ist true, und der Benutzer hat keine Datei angefügt. Für jedes Sprachpaket, das für die Organisation installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann.|
|Beschränken von Dateien auf akzeptierte Typen|  Erzwingt die Validierung für das Accept-Feld. Wenn diese Option nicht ausgewählt ist, wird das Accept-Attribut nur als Vorschlag für das Dialogfeld zum Hochladen von Dateien verwendet.|
|Dateityp-Fehlermeldung|Die während der Formular Überprüfung angezeigte Meldung, wenn Dateien auf akzeptierte Typen beschränken den Wert true haben und der Benutzer versucht hat, einen ungültigen Dateityp hochzuladen. Für jedes Sprachpaket, das für die Organisation installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann.|
|Maximale Dateigröße (in Kilobyte)|  Erzwingt die Überprüfung der maximal zulässigen Größe der hochgeladenen Datei.|
|Dateigröße (Fehlermeldung)|   Die Meldung, die während der Formular Überprüfung angezeigt wird, wenn die maximale Dateigröße (in Kilobyte) "true" ist und der Benutzer versucht hat, eine Datei hochzuladen, die zu groß ist. Für jedes Sprachpaket, das für die Organisation installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann.|
|Benutzerdefiniertes JavaScript| Ein benutzerdefinierter Block von JavaScript, der am unteren Rand der Seite direkt vor dem schließenden Form-TagElement hinzugefügt wird. Die HTML-Eingabe-ID eines Entitäts Felds wird auf den logischen Namen des Attributs festgelegt. Dies ermöglicht die Auswahl eines Felds, das Festlegen von Werten oder eine andere Client seitige Bearbeitung mit jQuery.<br>`$(document).ready(function() {   $(“#address1_stateorprovince”).val(“Saskatchewan”);});`|
|||

### <a name="entity-reference"></a>Entitäts Verweis

Die folgenden Parameter beziehen sich auf das Festlegen eines Entitäts Verweises, wenn das Formular gespeichert wird.

Dies bietet eine Möglichkeit, den aktuellen Datensatz, der vom Formular erstellt oder aktualisiert wird, mit einem anderen Zieldatensatz zuzuordnen. Dies ist hilfreich, wenn Sie mehrere Schritte mit mehreren Entitäts Typen ausführen und die resultierenden Datensätze miteinander verknüpfen möchten oder wenn der Seite eine Abfrage Zeichenfolge mit einer Datensatz-ID, die Sie zugeordnet werden sollen, übermittelt wird. Wir haben beispielsweise eine Seite "Karrieren", die Auftrags Beiträge auflistet, jeweils mit einem Link zu einer Anwendung für den Auftrag, der die ID des Auftrags enthält, der an das Anwendungs Formular gepostet wird, sodass die Auftrags Bereitstellung dem Datensatz zugeordnet ist, wenn die Anwendung erstellt wird. 

|Name|Beschreibung|
|-----|---------|
|Entitäts Verweis beim Speichern festlegen|Ja oder nein. Der Wert yes gibt an, dass ein Entitäts Verweis zugewiesen werden soll, wenn das Formular gespeichert wird. andernfalls wird None festgelegt.|
|Beziehungs Name|Der Beziehungs Definitions Name für eine gegebene Beziehung zwischen zwei Entitäts Typen.|
|Logischer Name der Entität|Der logische Name der Verweis Entität.|
|Logischer Name des Ziel Such Attributs|Logischer Name des Such Attributs für die Ziel Entität, die erstellt oder aktualisiert wird.|
|Nachschlage Feld Auffüllen| Wenn sich die Suche bezüglich der Verweis Entität im Formular befindet, füllt die Überprüfung dieses Werts das Feld im Formular mit dem Wert auf, der mithilfe der folgenden Einstellung abgerufen wird.|
|Quelltyp der Referenz Entität|  Einer der folgenden Werte:<ul><li>Abfrage Zeichenfolge</li><li>Aktueller Portal Benutzer</li><li>Ergebnis des vorherigen Schritts</li></ul> Die Auswahl der _Abfrage Zeichenfolge_ erfordert einen Parameternamen, der in der Abfrage Zeichenfolge der URL für das Formular bereitgestellt werden muss. Dies kann im Feld Name der **Abfrage Zeichenfolge** angegeben werden. Wenn dieser Parameter der Primärschlüssel ist, wählen Sie für **Abfrage Zeichenfolge**die Option Ja aus, und wählen Sie andernfalls Nein aus, und geben Sie den logischen Namen des Attributs für die Ziel Entität an, die Sie Abfragen möchten, indem Sie im Feld **logischer Name des Abfrage Attributs**  Wenn Sie aktueller Portal Benutzer auswählen, wird der Kontaktdaten Satz für den aktuellen authentifizierten Benutzer abgerufen. Durch die Auswahl von Ergebnis aus dem vorherigen Schritt wird der Datensatz, der als Ergebnis des Schritts vor dem aktuellen Schritt erstellt wurde, oder ein bestimmter Schritt basierend auf dem Schritt abgerufen, der dem Entitäts Quell Schritt zugeordnet ist.|
|Verweis Entitäts Schritt| Der Webformular-Schritt Datensatz eines vorherigen Schritts zum Abrufen der Entität, die in diesem Schritt erstellt oder bearbeitet wurde, um Sie dem Datensatz für diesen aktuellen Schritt zuzuordnen.|
|Abfrage Zeichen folgen Name| Parameter Name, der in der Abfrage Zeichenfolge der URL der Webseite bereitgestellt wird, die das Webformular enthält.|
|Abfrage Zeichenfolge ist Primärschlüssel|   Ja gibt an, dass der Wert der Abfrage Zeichenfolge der Primärschlüssel Wert ist. Nein gibt an, dass der Wert der Abfrage Zeichenfolge ein anderer Attributtyp als der Primärschlüssel ist.|
|Logischer Name des Abfrage Attributs|  Der logische Name des Attributs, um den Datensatz abzufragen.|
|Schreibgeschützte Details anzeigen| Gibt an, dass am oberen Rand der Seite ein Formular gerendert werden soll, das schreibgeschützte Informationen im Zusammenhang mit dem Verweis Daten Satz anzeigt. Erfordert einen Formular Namen.|
|Formularname| Der Name des Formulars in der Verweis Entität, das verwendet werden soll, um schreibgeschützte Details anzuzeigen.|
|||


## <a name="entity-form-action-configuration"></a>Konfiguration von Entitäts Formular Aktionen

Standardmäßig ermöglicht ein Entitäts Formular das Lesen oder Aktualisieren eines vorhandenen Datensatzes oder das Einfügen eines neuen Datensatzes.  Sie können jedoch problemlos zusätzliche Aktionen für Datensätze in einem Entitäts Formular aktivieren und konfigurieren (löschen, aktivieren, deaktivieren usw.). Es ist auch möglich, Standard Bezeichnungen,-Größen und andere Attribute zu überschreiben, die angezeigt werden, wenn Aktionen aktiviert sind.

Diese Einstellungen finden Sie im Abschnitt " **zusätzliche Einstellungen** " im Formular "Entität". Standardmäßig werden nur **grundlegende Einstellungen** angezeigt. Sie können **Erweiterte Einstellungen** auswählen, um zusätzliche Einstellungen anzuzeigen.

Sie können Aktions Schaltflächen für die Aktionen hinzufügen, die für einen einzelnen Datensatz anwendbar sind und für jede Zeile im Raster angezeigt werden, sofern die entsprechenden [Berechtigungen durch Entitäts Berechtigungen](assign-entity-permissions.md)erteilt wurden. Die folgenden Aktionen sind verfügbar:

- Lösch
- Workflow
- Verknüpften Datensatz erstellen
- Aktivieren
- Deaktivieren

Wenn Sie auf eine dieser Optionen klicken, wird ein Konfigurationsbereich für diese Aktion angezeigt. Darüber hinaus weisen bestimmte Entitäten spezielle Aktionen auf, die für Sie pro Entität verfügbar sind:

- Berechnen des Werts der Verkaufschance (Chance)
- Fall Aktion abbrechen (Incident)
- Schließen (auflösen) der Fall Aktion (Incident)
- Anführungszeichen in Bestellung konvertieren (Anführungszeichen)
- Bestellung in Rechnung konvertieren (SalesOrder)
- Zitat aus Verkaufschance generieren (Gelegenheit)
- Gelegenheit zum Verlust der Chance (Gelegenheit)
- Win Chance-Aktion (Gelegenheit)
- Fall Aktion erneut öffnen (Incident)
- Verkaufschance festlegen (Gelegenheit)

> [!NOTE]
> Es wird empfohlen, einen Workflow zu erstellen, anstatt eine Schaltfläche zum **aktivieren** oder **Deaktivieren** für Out-of-Box-Entitäten hinzuzufügen, die bestimmte **Zustands** -und **Statuscode** Werte definiert haben, die Sie für Ihre Geschäftsprozesse benötigen. Beispiel: Incident ([Status Optionen](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/incident#statuscode-options)), Verkaufschance ([Status](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/opportunity#statuscode-options)Optionen), Berechtigungen ([Status Optionen](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/entitlement#statuscode-options)). 


## <a name="geolocation-configuration-for-entity-forms"></a>Geolozierungkonfiguration für Entitäts Formulare

Ein verwaltetes Formular kann so konfiguriert werden, dass ein Karten Steuerelement angezeigt wird, um entweder einen vorhandenen Speicherort als PIN auf einer Karte anzuzeigen oder den Benutzer zum Angeben eines Speicher Orts zu sorgen. Siehe [Hinzufügen von Geolokation](add-geolocation.md).

Das Karten Steuerelement des Formulars erfordert eine zusätzliche Konfiguration, um ihm mitzuteilen, was die IDs der verschiedenen Speicherort Felder sind, um Ihnen Werte zuzuweisen oder um Werte abzurufen. Der Formulardaten Satz der Entität verfügt über einen Konfigurations Abschnitt, mit dem diese Feld Zuordnungen definiert werden, die Sie angeben müssen. Die Feldnamen variieren je nach Schema, das Sie erstellt haben.

![Geolozierungdaten in Entitäts Form](../media/geolocation-managed-form.png "Geolozierungdaten in Entitäts Form") 

> [!Note]
> - Das Adressfeld in einem schreibgeschützten Entitäts Formular wird durch die Zuordnung ersetzt, wenn die geolozierung aktiviert ist.
> - Der Abschnitt "Geolokation" ist in der deutschen unabhängigen cloudumgebung nicht sichtbar. Wenn ein Benutzer die geolozierung mit einer anderen Form aktiviert hat, wird er während des Renderings im Portal nicht angezeigt.

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Portals](configure-portal.md)  
[Web Form-Eigenschaften für Portale](web-form-properties.md)  
[Webformular Schritte für Portale](web-form-steps.md)  
[Web Forms von Metadaten für Portale](configure-web-form-metadata.md)  
[Webformular-unter Raster Konfiguration für Portale](configure-web-form-subgrid.md)  
[Hinweise zur Konfiguration von Entitäts Formularen und Web Forms für Portale](../configure-notes.md)
