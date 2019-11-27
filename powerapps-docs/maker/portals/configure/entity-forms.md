---
title: Definieren von Entitätsformularen | Microsoft-Dokumentation
description: Anweisungen zu Erstellen von Entitätsformularen in einem Portal.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760450"
---
# <a name="about-entity-forms"></a>Über Entitätsformulare

Eine datengesteuerte Konfiguration, um den Endbenutzern zu erlauben, ein Formular hinzuzufügen, um Daten im Portal zu sammeln, ohne dass ein Entwickler das Formular im Portal zeigen muss. Entitätsformulare werden in Common Data Service erstellt und anschließend in Webseiten im Portal platziert oder zusammen mit Unterrastern und Entitätslisten verwendet, um eine vollständige Webanwendung aufzubauen. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Über Entitätslisten](entity-lists.md) 

![Formular Kontakt](../media/contact-us-form.png "Formular Kontakt")  

## <a name="add-a-form-to-your-portal"></a>Ihrem Portal ein Formular hinzufügen

Das Entitätsformular enthält Beziehungen zu Webseiten und zusätzliche Eigenschaften, um die Initialisierung des Formulars in einem Portal zu steuern. Die Beziehung der Webseite ermöglicht ein dynamisches Abrufen der Formulardefinition für einen bestimmten Seitenknoten innerhalb der Website. 

Um vorhandene Entitätsformulare anzuzeigen oder neue Entitätsformulare zu erstellen, öffnen Sie die [Portalverwaltungs-App](configure-portal.md) und gehen Sie zu **Portale** &gt; **Entitätsformulare**.

Wenn Sie ein neues Entitätsformular erstellen, müssen Sie als erstes die **Entität** und den **Formularname** festlegen, die Sie rendern werden, sowie den **Modus: Einfügen, Bearbeiten oder Schreibgeschützt** Der ausgewählte Modus bestimmt , ob Sie einen neuen Datensatz vom Portal erstellen, einen vorhandenen Datensatz bearbeiten oder lediglich Informationen zu einem Datensatz aus dem Portal anzeigen.

> [!Note]
> - Ein **Entitätsformular** muss einer Webseite auf einer bestimmten Website zugeordnet sein, damit das Formular auf der Website angezeigt wird.
> - Die Verbindungsentitätsunterraster werden in Entitätsformularen nicht unterstützt. Wenn Sie ein Verbindungsentitätsunterraster dem Formular mithilfe des Formulardesigners hinzufügen, werden Fehlermeldungen angezeigt, wenn Sie das Formular auf dem Portal rendern und die Verbindungsentität verwenden.
> - Doppelte Felder, verschiedene Optionssätze, benutzerdefinierte Steuerelemente und Geschäftsregeln werden nicht in Entitätsformularen unterstützt.
> - Geschäftsregeln und Client-API können gesperrte Felder in einem schreibgeschützten Formular aktivieren.
> - Wenn Sie ein Einfügemodus im Entitätsformular erstellen, können Sie jedoch die Ausrichtung eine Schaltfläche nicht mehr ändern und eine interaktiv Schaltfläche zu dem Entitätsformular platzieren.
> - Wenn Sie ein Nachschlagesteuerelement im Formular als Dropdownliste rendern, funktioniert der Filter der verknüpften Datensätze nicht.

Die Webseite, die mit der Entitätsformular verknüpft ist, kann durch klicken auf den Link **Webseite** in den Links **Verknüpfte** Navigation ganz links im Menü angezeigt werden.

Wenn Sie eine Webseite erstellen oder bearbeiten, kann ein **Entitätsformular** im Suchfeld auf dem Webseitenformular angegeben werden.

Die unterschiedlichen Masterseiten, die das Portal verwendet enthalten Deklarationen des **Entitätsformular**-Serversteuerelements. Wenn Sie die Webseite und die Page (~/Pages/Page.aspx) Seitenvorlage bzw. die Full Page (~/Pages/FullPage.aspx) Seitenvorlage rendern, ermitteln die Steuerelemente, ob die Entitätsformular-Suche einen Wert enthält. Erst dann wird das Formular gerendert.

## <a name="secure-your-forms"></a>Formulare sichern

Um Ihre Formulare zu sichern, müssen Sie Entitätsberechtigungen erstellen, die den Zugriff und den Besitz der Datensätze gemäß der Webrollen bestimmen. Wenn ein Benutzer ein Entitätsformular öffnen möchte, aber die Berechtigungen nicht besitzt, wird eine Fehlermeldung angezeigt. Um Berechtigungen für ein Entitätsformular zu aktivieren, legen Sie **Entitätsberechtigungen aktivieren** auf true fest. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Erstellen Sie Webrollen für Portale](create-web-roles.md).  

## <a name="entity-form-attributes-and-relationships"></a>Attribute und Beziehungen von Entitätsformularen

|Name|Beschreibung|
|-----|----------|
|Name|Der beschreibende Name des Datensatzes. In diesem Feld ist ein Eintrag erforderlich.|
|Entitätsname|Der Name der Entität, aus der das Formular geladen wird. In diesem Feld ist ein Eintrag erforderlich.|
|Formularname| Der Name des Formulars auf der Zielentität, das gerendert werden soll. In diesem Feld ist ein Eintrag erforderlich.|
|Registerkartenname|  Optionaler Name einer Registerkarte in einem Formular, das für eine bestimmte Entität gerendert werden soll.|
|Modus|Einer der folgenden Werte:<ul><li>Einfügen</li><li>Bearbeiten</li><li>Schreibgeschützt</li></ul>Die Auswahl _Einfügen_ zeigt an, dass das Formular nach der Übermittlung einen neuen Datensatz einfügen soll. Die Angabe _Bearbeiten_ zeigt an, dass das Formular einen vorhandenen Datensatz bearbeiten soll. Die Auswahl _Schreibgeschützt_ gibt an, dass das Formular ein nicht bearbeitbares Formular eines vorhandenen Datensatzes anzeigen soll. _Bearbeiten_ und _Schreibgeschützt_ erfordern, dass ein Quelldatensatz vorhanden ist und die Parameter in den Feldern "Datensatzquelltyp" und "Abfragezeichenfolgen-Parametername für Datensatz-ID" angegeben werden, um den entsprechenden Datensatz auszuwählen, wenn das Formular Portal geladen wird.|
|Datensatzquelltyp|Einer der folgenden Werte:<ul><li>Abfragezeichenfolge</li><li>Aktueller Portalbenutzer</li><li>Dem aktuellen Portalbenutzer zugeordneter Datensatz</li></ul>Das Auswählen der _Abfragezeichenfolge_ erfordert einen Parameternamen, der in der Abfragezeichenfolge derURL des Formulars angegeben werden muss. Dies kann im Feld "Abfragezeichenfolgen-Parametername für Datensatz-ID"angegeben werden.<br>Die Auswahl _Aktueller Portalbenutzer_ ruft den Portalbenutzerdatensatz des aktuellen authentifizierten Benutzers ab.<br>Die Auswahl von _Datensatz aktuellem Portalbenutzer zugeordnet_ ruft den Portalbenutzerdatensatz für den aktuellen authentifizierten Benutzer ab und ruft dann den Datensatz für die bestimmte Beziehung ab, wie im Feld "Beziehungsname" angegeben.|
|Abfragezeichenfolgen-Parametername für Datensatz-ID| Ein Parametername, der in der Abfragezeichenfolge der URL der Webseite angegeben wird und dieses Entitätsformular umfasst.|
|Beziehungsname| Erforderlich, wenn der Datensatzquelltyp ein Datensatz ist, der dem aktuellen Portalbenutzer zugeordnet ist. Der logische Name der Beziehung zwischen dem aktuellen Portalbenutzerdatensatz und dem Zieldatensatz. Hier muss derselbe Entitätstyp zurückgegeben werden, wie im Feld "Entitätsname" angegeben.|
|Erstellen zulassen, falls NULL|  Ein optionaler Boolescher Wert ist verfügbar, wenn der Datensatzquelltyp "Dem aktuellen Portalbenutzer zugeordneter Datensatz" ist. "Aktiviert" gibt an, dass der Benutzer Datensätze erstmalig erstellen kann, wenn der verknüpfte Datensatz nicht vorhanden ist. Wenn kein Datensatz vorhanden ist, wird eine Ausnahme ausgelöst, da das Formular einen Datensatz zur Datenbindung benötigt.|
|Entitätsberechtigungen aktivieren| Veranlaßt das Formular, Entitäts-Berechtigungen zu berücksichtigen. Der Standard für Abwärtskompatibilitätsgründe ist false. Wenn der Wert "true" festgelegt ist, sind explizite Berechtigungen für jeden Benutzer ERFORDERLICH, der auf das Formular zugreifen will.|
|||

### <a name="form-options"></a>Formularoptionen

|Name|Beschreibung|
|----|---------|
|Captcha hinzufügen|   Zeigt das Captcha an.|
|Captcha für authentifizierte Benutzer anzeigen|  Zeigt Captcha für authentifizierte Benutzer an.|
|Überprüfungsgruppe|  Der Gruppenname, der Eingabesteuerelemente zum Auswerten einer gültigen Eingabe der benannter Gruppen.|
|Schritte aus Registerkarten automatisch generieren| Zeigt an, dass in einem Entitätsformular mehrere Registerkarten angezeigt werden, die, beginnend mit der ersten Registerkarte, der Reihe nach bearbeitet werden müssen und bei denen nach dem Absenden der Letzten Registerkarte ein Datensatz eingefügt wird. Dies ist standardmäßig nicht ausgewählt. Der Standardwert zeigt an, dass nur eine Registerkarte oder ein Formular für den Schritt gerendert werden soll. Wenn kein Registerkarten-Name angegeben ist, wird die erste Registerkarte angezeigt.|
|Webressourcen inline rendern|   Beseitigt den IFrame, der in einem Entitätsformular eine Webressource umfasst.|
|QuickInfos aktiviert|  Die QuickInfo wird mithilfe der Beschreibung des Attributs in der Zielentität festgelegt.|
|Nicht unterstützte Felder anzeigen|   Alle Felder werden derzeit unterstützt. Dies ist für potentielle Änderungen reserviert, die möglicherweise durch Common Data Service an den Feldtypen vorgenommen werden.|
|Empfohlene Felder nach Bedarf festlegen|    Erfordert die Eingabe aller Attribute, deren Feldanforderungsstufe auf "Eingabe empfohlen" festgelegt ist.|
|Alle Felder als Pflichtfelder aktivieren|  Erfordert die Eingabe aller Felder, unabhängig von der Feldanforderungsstufe.|
|CSS-Klasse für Überprüfungszusammenfassung|  CSS-Klassenname, der der Überprüfungszusammenfassung zugewiesen ist. Standard ist "Überprüfungszusammenfassungswarnung Warnung-Fehler Warnung-Blockiert"|
|Links für Überprüfungszusammenfassung aktivieren|   Ein Boolescher Wert von "true" oder "false" gibt an, ob Ankerlinks in der Überprüfungszusammenfassung so gerendert werden sollen, dass das Feld, welches den Fehler enthält, zu scrollen ist. Standardwert ist true.|
|Linktext für Überprüfungszusammenfassung|  Die Beschriftung, die den Links zur Überprüfungszusammenfassung zugeordnet ist. Standardwert ist "Klicken Sie hier".|
|Kopfzeilentext für Überprüfungszusammenfassung|    Die Beschriftung, die den Header zur Überprüfungszusammenfassung zugeordnet ist.|
|Anweisungen|  Anweisungen, die mit der Formular arbeiten sollen.|
|Meldung „Datensatz nicht gefunden“|  Nachricht, die angezeigt werden soll, wenn ein Datensatz nicht gefunden wird.|
|||

### <a name="on-success-settings"></a>Einstellungen für "Bei Erfolg"

|Name|Beschreibung|
|----|----------|
|Bei Erfolg|    Einer der folgenden Werte:<ul><li>Erfolgsmeldung anzeigen (Standard)</li><li>Umleiten</li></ul>|
|Formular bei Erfolg ausblenden|  Erfordert, dass "Bei Erfolg" auf "Erfolgsmeldung anzeigen" festgelegt ist. Wenn diese Option ausgewählt ist, wird das Formular bei erfolgreichem Übermitteln des Formulars ausgeblendet.|
|Erfolgsmeldung|   Erfordert, dass "Bei Erfolg" auf "Erfolgsmeldung anzeigen" festgelegt ist. Die Meldung, die dem Benutzer bei erfolgreicher Übermitteln angezeigt wird. Wenn keine angegeben ist, wird die Standardnachricht (Übermittlung erfolgreich abgeschlossen") angezeigt. Für jedes Language Pack, das für die Organisation installiert und aktiviert ist, ist ein Feld ist verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann.|
|Externe URL|Erfordert, das "On Success" auf "Redirect" festgelegt ist. Geben Sie eine URL für eine externe Webressource an.
|oder Webseite|Erfordert, das "On Success" auf "Redirect" festgelegt ist. Wählen Sie eine Webseite der aktuellen Webseite aus.|
|Vorhandene Abfragezeichenfolge anfügen|  Erfordert, das "On Success" auf "Redirect" festgelegt ist. Wenn ausgewählt, werden die vorhandenen Abfragezeichenfolgenparameter zur Ziel-URL vor der Umleitung hinzugefügt.|
|Datensatz-ID an Abfragezeichenfolge anfügen|  Erfordert, das "On Success" auf "Redirect" festgelegt ist. Wenn ausgewählt, wird die ID des erstellten Datensatzes zur Abfragezeichenfolge der URL an die umgeleitet wird angefügt.|
|Abfragezeichenfolgen-Parametername für Datensatz-ID|     Erfordert, das "On Success" auf "Redirect" festgelegt ist. Der Name des ID-Parameters in der Abfragezeichenfolge der URL, an die umgeleitet wird.|
|Benutzerdefinierte Abfragezeichenfolge anfügen|    Erfordert, das "On Success" auf "Redirect" festgelegt ist. Eine benutzerdefinierte Zeichenfolge, die an die Abfragezeichenfolge der Umleitungs-URL angefügt werden kann.|
|Attributwert an Abfragezeichenfolge anfügen – Parametername|   Erfordert, das "On Success" auf "Redirect" festgelegt ist. Ein Name für den Parameter, der mit dem Attributwert der Zielentität übereinstimmt, die der Abfragezeichenfolge der Umleitungs-URL angefügt wird.|
|Attributwert an Abfragezeichenfolge anfügen – Logischer Attributname|Erfordert, das "On Success" auf "Redirect" festgelegt ist. Ein logischer Name eines Attributs der Zielentität, um den Wert an die Abfragezeichenfolge der Umleitungs-URL anzufügen.|
|||

### <a name="additional-settings"></a>Weitere Einstellungen

|Name|Beschreibung|
|----|----------|
|Aktuellen Portalbenutzer zuordnen| Gibt an, ob der Datensatz des geraden angemeldeten Benutzers dem Zielentitätsdatensatz zugeordnet werden soll.|
|Suchattribut: Portalbenutzer für Zielentität|    Der logische Name des Attributs in der Zielentität, die den Portalbenutzer speichert.|
|Ist Aktivitätspartei| Boolesche Werte geben an, ob das Suchattribut: Portalbenutzer für Zielentität ein ActivityParty-Typ ist.|
|Datei anfügen|   Wird aktiviert, um ein Dateiuploadsteuerelement unten im Formular hinzuzufügen, dass es ermöglicht, dem Datensatz Dateien anzufügen.|
|Datei anfügen: Speicherort|  Optionen: Notizanlage, Azure-Blob-Speicher. Wenn Ihre Organisation zur Verwendung von Azure Storage konfiguriert ist, können Sie hochgeladenen Dateien für dieses Entitätsformular dort speichern. Andernfalls werden Dateien als Notizanlagen gespeichert.|
|Mehrere Dateien zulassen|Boolescher Wert, der angibt, ob der Benutzer mehrere Dateien hochladen kann oder nicht.|
|Akzeptieren|    Das "Akzeptieren"-Attribut gibt die MIME-Typen von Dateien an, die der Server beim Dateiupload annimmt. Um mehr als einen Wert anzugeben, trennen Sie die Werte mit einem Komma (z.B. audio/*,video/*,image/*).|
|Beschriftung| Der Text wird neben dem Dateiuploadsteuerelement angezeigt . Für jedes Language Pack, das für die Organisation installiert und aktiviert ist, ist ein Feld ist verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann.|
|Datei anfügen: Erforderlich| Ermöglicht das Verarbeiten eines Dateianhangs.|
|Fehlermeldung für "Erforderlich"|Die Nachricht, die während der Formularüberprüfung angezeigt wird, wenn "Ist erforderlich" auf "True"gesetzt ist und der Benutzer keine Datei angefügt hat. Für jedes Language Pack, das für die Organisation installiert und aktiviert ist, ist ein Feld ist verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann.|
|Dateien auf akzeptierte Typen beschränken|  Erzwingt die Überprüfung des Felds "Akzeptieren". Wenn nicht ausgewählt, wird das Akzeptieren-Attribut nur als ein Vorschlag für den Dateiupload-Dialog verwendet.|
|Fehlermeldung für "Dateityp"|Die Meldungen, die bei der Überprüfung des Formular angezeigt wird, wenn "Dateien auf akzeptierte Typen beschränken" wahr ist und der Benutzer versucht hat, einen ungültigen Dateityp hochzuladen. Für jedes Language Pack, das für die Organisation installiert und aktiviert ist, ist ein Feld ist verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann.|
|Maximale Dateigröße (in Kilobyte)|  Erzwingt die Überprüfung der maximal zulässigen Größe der hochgeladenen Datei.|
|Fehlermeldung für "Dateigröße"|   Die Meldungen, die bei der Überprüfung des Formulars angezeigt werden, wenn "Maximale Dateigröße (in Kilobyte)" wahr ist und der Benutzer versucht hat, eine zu große Datei hochzuladen. Für jedes Language Pack, das für die Organisation installiert und aktiviert ist, ist ein Feld ist verfügbar, in das die Nachricht in der zugehörigen Sprache eingeben werden kann.|
|Benutzerdefiniertes JavaScript| Ein benutzerdefinierter JavaScript-Satz wird unten an der Seite platziert, direkt vor dem Tag zum Schließen des Elements. Die HTML-Eingabe-ID eines Entitätsfelds wird auf den logischen Namen des Attributs festgelegt. Dadurch wird das Auswählen von Feldern, Einstellungswerten oder anderen clientseitigen Änderungen mit jQuery erleichtert.<br>`$(document).ready(function() {   $(“#address1_stateorprovince”).val(“Saskatchewan”);});`|
|||

### <a name="entity-reference"></a>Entitätsreferenz

Die folgenden Parameter betreffen das Einrichten einer Entitätsreferenz beim Speichern des Formulars.

Dies bietet eine Möglichkeit, den aktuellen Datensatz, der durch das Formular erstellt oder aktualisiert wurde, einem weiteren Zieldatensatz zuzuordnen. Dies ist hilfreich, wenn Sie die mehrere Schritte mit mehreren Entitätstypen haben und die daraus entstehenden Datensätze verknüpfen möchten oder die Seite eine Abfragezeichenfolge einer Datensatz-ID übergeben möchte, die Sie zuordnen wollen. Wenn wir beispielsweise Karriereseite haben, auf der jede Stellenausschreibung über einen Link zu einem Bewerbungsformular verfügt, das wiederum die ID der Stellenausschreibung beinhaltet, sodass beim Erstellen der Bewerbung die Stellenausschreibung direkt dem Datensatz zugeordnet wird. 

|Name|Beschreibung|
|-----|---------|
|Entitätsreferenz auf "Beim Speichern" festlegen|Ja oder Nein. Der Wert "Ja" gibt an, dass eine Entitätsreferenz zugewiesen werden soll, sobald das Formular gespeichert wird; andernfalls wird "Keine" festgelegt.|
|Beziehungsname|Der Beziehungsdefinitionsname für eine jeweilige Beziehung zwischen zwei Entitätstypen.|
|Logischer Entitätsname|Der logische Name der Referenzentität.|
|Logischer Name des Zielsuchattributs|Logischer Name des Suchattributs in der Zielentität wird erstellt oder aktualisiert.|
|Suchfeld auffüllen| Wenn sich die Suche bezüglich der Referenzentität im Formular befindet, wird bei er Aktivierung dieses Wertes der über die Einstellungen unten abgerufene Wert in das Feld im Formular eingetragen.|
|Referenzentitäts-Quelltyp|  Einer der folgenden Werte:<ul><li>Abfragezeichenfolge</li><li>Aktueller Portalbenutzer</li><li>Ergebnis aus vorherigem Schritt</li></ul> Das Auswählen der _Abfragezeichenfolge_ erfordert einen Parameternamen, der in der Abfragezeichenfolge derURL des Formulars angegeben werden muss. Dies kann im Feld **Abfragezeichenfolgenname** angegeben werden. Wenn dieser Parameter der Primärschlüssel ist, dann wählen Sie "Ja" für **Abfragezeichenfolge ist Primärschlüssel**, andernfalls wählen Sie "Nein" und geben den logischen Namen des Attributs an, der in der im Feld **Logischer Name des Abfrageattributs** festgelegten Zielentität abgefragt werden soll.  Die Auswahl Aktueller Portalbenutzer ruft den Kontaktdatensatz des aktuell authentifizierten Benutzers ab. Die Auswahl Ergebnis aus vorherigem Schritt ruft den Datensatz ab, der als Ergebnis des vorherigen Schrittes oder eines bestimmten Schrittes auf der Grundlage des Schrittes erstellt wurde, der dem Entitätsquellschritt zugeordnet ist.|
|Referenzentitätsschritt| Der Webformular-Schrittdatensatz eines vorherigen Schritt, der benötigt wird, um die Entität abzurufen, die in diesem Schritt erstellt oder bearbeitet wurde und sie dem Datensatz des aktuellen Schritts zuzuordnen.|
|Abfragezeichenfolgenname| Ein Parametername, der in der Abfragezeichenfolge der URL der Webseite angegeben wird und das Webformular umfasst.|
|Abfragezeichenfolge ist Primärschlüssel|   "Ja" gibt an, dass der Abfragezeichenfolgenwert dem Primärschlüsselwert entspricht. Kein gibt an, dass der Abfragezeichenfolgenwert ein anderer Attributtyp als der Primärschlüssel ist.|
|Logischer Name des Abfrageattributs|  Logischer Name des Attributs zum Abfragen des Datensatzes.|
|Details für Schreibschutz anzeigen| Gibt an, dass ein Formular oben auf der Seite gerendert wird und schreibgeschützte Informationen des Referenzdatensatzes anzeigt. Benötigt einen Formular-Namen.|
|Formularname| Der Name des Formulars auf der Referenzentität, die verwendet werden soll, um schreibgeschützte Details anzuzeigen.|
|||


## <a name="entity-form-action-configuration"></a>Konfigurationen der Entitätsformularaktion

Standardmäßig können erlaubt ein Entitätsformular das Lesen oder Aktualisieren eines vorhandenen Datensatzes oder die Einfügung eines neuen Datensatzes.  Sie können allerdings auch leicht weitere Aktionen für Datensätze in einem Entitätsformular aktivieren und konfigurieren (löschen, aktivieren, deaktivieren., usw.). Es auch Möglich, Standardbeschriftungen, Größen und anderer Attribute zu überschrieben, die angezeigt werden, wenn Aktionen aktiviert sind.

Diese Einstellungen befinden sich im Abschnitt **Zusätzliche Einstellungen** des Entitätsformulars. Standardmäßig werden nur **Grundlegende Einstellungen** angezeigt. Sie können **Erweiterte Einstellungen** auswählen, um weitere Einstellungen anzuzeigen.

Sie können Aktionsschaltflächen für die Aktionen hinzuzufügen, die für einen einzelnen Datensatz anwendbar sind und in jeder Zeile im Raster angezeigt werden, wenn das entsprechende Recht von [Entitätsberechtigungen](assign-entity-permissions.md) erteilt wurde. Die folgenden Aktionen stehen zur Verfügung:

- Löschen
- Workflow
- Verknüpften Datensatz erstellen
- Aktivieren
- Deaktivieren

Durch Klicken auf eine der Optionen wird ein Konfigurationsbereich für diese Aktion angezeigt. Außerdem haben bestimmte Entitäten spezielle Aktionen, die für sie auf einer Pro-Entitätsgrundlage verfügbar sind:

- Wert der Verkaufschance berechnen (Verkaufschance)
- Anfrageaktion abbrechen (Vorfall)
- Anfrageaktion (Vorfall) schließen (abschließen)
- Angebot in einen Auftrag umwandeln (Angebot)
- Angebot in eine Rechnung umwandeln (Vertriebsauftrag)
- Angebot aus Verkaufschance generieren (Verkaufschance)
- Verkaufschancenaktion verlieren (Verkaufschance)
- Verkaufschancenaktion gewinnen (Verkaufschance)
- Anfrageaktion erneut öffnen (Vorfall)
- Verkaufschance zurückstellen (Verkaufschance)

> [!NOTE]
> Er empfiehlt sich, einen Workflow zu erstellen, anstatt eine **Aktivieren**- oder **Deaktivieren**-Schaltfläche für standardmäßige Entitäten hinzuzufügen, bei denen bestimmte **Status**- und **Statuscode**-Werte definiert werden, die sie für ihre Geschäftsprozesse benötigen. Beispiel: Vorfall ([Statusoptionen](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/incident#statuscode-options)), Verkaufschance ([Statusoptionen](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/opportunity#statuscode-options)), Berechtigungen ([Statusoptionen](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/entities/entitlement#statuscode-options)). 


## <a name="geolocation-configuration-for-entity-forms"></a>Geolocation-Konfiguration für Entitätsformulare

Ein verwaltetes Formular kann so konfiguriert werden, dass es ein Kartensteuerelement anzeigt, das entweder einen vorhandenen Standort als Stecknadel auf einer Karte anzeigt oder dem Benutzer die Möglichkeit bereitstellt, einen Standort anzugeben. Siehe [Hinzufügen einer Geolocation](add-geolocation.md).

Das Kartensteuerelement des Formulars erfordert eine zusätzliche Konfiguration, um die IDs der verschiedenen Standortfelder anzugeben, damit diesen Werte zugewiesen bzw. Werte von diesen abgerufen werden können. Der Entitätsformulardatensatz besitzt einen Konfigurationsabschnitt, der die Feldzuordnungen definiert, die Sie angeben müssen. Die Feldnamen sind von dem von Ihnen erstellten Schema abhängig.

![Geolocation-Daten im Entitätsformular](../media/geolocation-managed-form.png "Geolocation-Daten im Entitätsformular") 

> [!Note]
> - Das Adressfeld in einem schreibgeschützten Entitätsformular wird durch die Zuordnung ersetzt, wenn Geolocation aktiviert ist.
> - Der Geolocation-Abschnitt wird in der deutschen Sovereign Cloud-Umgebung nicht angezeigt. Wenn ein Benutzer Geolocation mithilfe eines anderen Formulars aktiviert hat, wird es während des Renderings im Portal nicht angezeigt.

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Webformulareigenschaften für Portale](web-form-properties.md)  
[Webformularschritte für Portale](web-form-steps.md)  
[Web-Formulare-Metadaten für Portale](configure-web-form-metadata.md)  
[Webformular-Unterrasterkonfiguration für Portale](configure-web-form-subgrid.md)  
[Konfigurieren von Hinweisen für Entitätsformulare und Internetformulare in Portalen](../configure-notes.md)
