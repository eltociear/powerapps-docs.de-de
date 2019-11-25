---
title: Webformular-Unterrasterkonfiguration für ein Portal | MicrosoftDocs MicrosoftDocs
description: Anweisungen, Webformular-Unterraster für ein Portal hinzuzufügen und zu konfigurieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 210300d40742cbf2ca83f9d6c3b07cd580167eaa
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760455"
---
# <a name="configure-web-form-subgrids-for-portals"></a>Konfigurieren von Webformular-Unterrastern für Portale

Web Form-Unterraster werden in derselben Weise konfiguriert wie Entitätsformularunterraster: Erstellen Sie zunächst einen Metadatendatensatz für den Webformular-Schritt, der ein Unterraster hat, und fügen Sie dann Konfigurationsmetadaten hinzu.

Hinzufügen von Unterrastern zu Ihren verwalteten Formularen im Portal ist einfach – fügen Sie einfach das Unterraster zum Formular, das Sie verwalten, hinzu, indem Sie den vorkonfigurierten Formulardesigner verwenden und Sie sind fertig. Das Raster verwendet die Ansicht, die im Common Data Service-Formulardesigner angegeben wird, es zeigt nur verknüpfte Datensätze an, wenn diese Option ausgewählt wurde. Optional wird eine Suchleiste angezeigt und es werden sogar [Entitätsberechtigungen für Portale](assign-entity-permissions.md) respektiert. Einfach kann eine Schreibgeschütze Liste mit Datensätzen nicht angezeigt werden. Um Aktionen für das Raster zu ermöglichen – Erstellen, Aktualisieren, Löschen, usw., – müssen Sie diese Aktionen mithilfe der Metadatenkonfigurationen konfigurieren.

## <a name="add-subgrid-metadata-to-your-form"></a>Unterrastermetadaten zum Formular hinzufügen

Um Unterraster-Metadaten zu einem Entitätsformular hinzuzufügen, navigieren Sie entweder mithilfe der oberen Dropdownliste oder des Unterrasters des Entitätsformulardatensatzes, an dem Sie arbeiten zu **Entitätsformular-Metadaten**. Weitere Informationen: [Entitätsformulare definieren](entity-forms.md).

Um einen neuen Datensatz hinzuzufügen, klicken Sie auf **Neue Entitätsformular-Metadaten hinzufügen**.

Um einen vorhandenen Datensatz zu bearbeiten, klicken Sie auf eines Datensatz im Raster. Bei Auswahl von **Unterraster** als **Typ**-Wert wird ein anderes Attribut angezeigt, **Unterrastername**.


|     Name     |                                                       Beschreibung                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------|
| Unterrastername | Der eindeutige Name eines Unterrasters im verknüpften Formular der Entität. |
|              |                                                                                                                          |

Durch Auswahl des Unterrasters im Formular-Editor wird ein Eigenschaftenfenster angezeigt. Dies beinhaltet ein **Name**-Feld, das zum Zuweisen zum **Unterraster**-Namensfeld im Entitätsformular-Metadatendatensatz verwendet werden sollte.

![Unterrastermetadaten hinzufügen](../media/add-subgrid-metadata.png "Unterrastermetadaten hinzufügen")  

Beim Angeben eines gültigen Unterrasternamens werden die Unterrasterkonfigurationseinstellungen angezeigt. Standardmäßig werden nur **Grundlegende Einstellungen** angezeigt. Wählen Sie **Erweiterte Einstellungen** aus, um weitere Einstellungen anzuzeigen.

Standardmäßig werden die meisten Einstellungen reduziert angezeigt. Wählen Sie ****, um einen Abschnitt zu erweitern und Zusatzfunktionen anzuzeigen. Wählen Sie ****, um den Abschnitt zu verkleinern.

## <a name="attributes"></a>Attribute

| Name                       | Beschreibung                                                                                                                                                                                                                                                                                                                                                               |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**         |                                                                                                                                                                                                                                                                                                                                                                           |
| Aktionen anzeigen               | Ermöglicht Ihnen, Aktionsschaltflächen für Aktionen hinzuzufügen, die für den Entitätssatz anwendbar sind und über dem Unterraster angezeigt werden. Die folgenden Aktionen sind verfügbar: <ul><li>Erstellen</li><li>Herunterladen</li><li>Zuordnen</li></ul> Durch Auswahl einer dieser Optionen wird ein Konfigurationsbereich für diese Aktion angezeigt. Weitere Informationen für jede Aktion finden Sie unten.                                                                                                                                                                                                                                                   |
| Elementaktionen               | Ermöglicht Ihnen, Aktionsschaltflächen für Aktionen hinzuzufügen, die für einen einzelnen Datensatz anwendbar sind und in jeder Zeile im Raster angezeigt werden, wenn das entsprechende Recht von [Entitätsberechtigungen](assign-entity-permissions.md) erteilt wurde. Die folgenden Aktionen sind verfügbar: <ul><li>Details</li><li>Bearbeiten</li><li>Löschen</li><li>Workflow</li><li>Zuordnung aufheben</li></ul> Durch Auswahl einer dieser Optionen wird ein Konfigurationsbereich für diese Aktion angezeigt. Weitere Informationen für jede Aktion finden Sie unten.                                                                                                                                                                                                                                                   |
| Spaltenattribute überschreiben | Ermöglicht das Überschreiben von Anzeigeeinstellungen für die einzelnen Spalten im Raster. <ul><li>Attribut: Der logische Name der Spalte, die Sie überschreiben möchten.</li><li>Anzeigename: Neuer Spaltentitel zum Überschreiben der Standardwerte</li><li>Breite: Breite (in Prozent oder Pixel) der Spalte zum Überschreiben der Standardwerte. Vergleiche: Stil der Rasterspaltenbreite. Zum Überschreiben von Einstellungen einer Spalte klicken Sie auf **Spalte** und geben Sie die Informationen ein.                                                                                                                                                                                                                                                                                             |
| **Erweiterte Einstellungen**      |                                                                                                                                                                                                                                                                                                                                                                           |
| Laden von Meldungen            | Überschreibt die Standard-HTML-Nachricht, die angezeigt wird, während das Unterraster lädt.                                                                                                                                                                                                                                                                                             |
| Fehlermeldung              | Überschreibt die Standard-HTML-Nachricht, die angezeigt wird, wenn ein Fehler auftritt, während das Unterraster geladen wird.                                                                                                                                                                                                                                                                           |
| Meldung vom Typ \"Zugriff verweigert\"      | Überschreibt die Standard-HTML-Nachricht, die angezeigt wird, wenn ein Benutzer nicht genügende [Berechtigungen](assign-entity-permissions.md) aufweist, um den Entitätstyp zu lesen, der dem Unterraster zugeordnet ist.                       |
| Leere Meldung              | Überschreibt die HTML-Nachricht, die angezeigt wird, wenn das zugeordnete Unterraster keine Daten enthält.                                                                                                                                                                                                                                                                                     |
| Dialog \"Suche\"              | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Zuordnen-Aktion aktiviert.                                                                                                                                                                                                                                                                             |
| Dialog \"Detailformular\"        | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Details-Aktion aktiviert.                                                                                                                                                                                                                                                                                |
| Dialog \"Formular bearbeiten\"           | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Bearbeiten-Aktion aktiviert.                                                                                                                                                                                                                                                                                   |
| Dialog \"Formular erstellen\"         | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Erstellen-Aktion aktiviert.                                                                                                                                                                                                                                                                                 |
| Dialog \"Löschen\"              | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Löschen-Aktion aktiviert.                                                                                                                                                                                                                                                                                 |
| Fehlerdialog               | Steuert die Einstellungen für das Dialog, das angezeigt wird, wenn ein Fehler bei einer Aktion auftritt.                                                                                                                                                                                                                                                                                 |
| CSS Klasse                  | Geben Sie eine CSS-Klasse oder Klassen an, die für das HTML-Element angewendet werden, das den gesamten Unterrasterbereich enthält, u. a. die Raster- und Aktionsschaltflächen.                                                                                                                                                                                                                     |
| CSS-Klasse für Raster             | Geben Sie eine CSS-Klasse oder Klassen an, die auf das HTML-Element &lt;table&gt; des Unterrasters angewendet werden.                                                                                                                                                                                                                                                                          |
| Stil der Rasterspaltenbreite    | Konfiguriert, ob **Breite**-Werte in den Überschreiben-Spaltenattributen in **Pixel** oder **Prozent** angegeben werden.                                                                                                                                                                                                                                                             |
||

## <a name="create-action"></a>Erstellen-Aktion

Das Aktivieren der **Erstellen-Aktion** rendert eine Schaltfläche über dem Unterraster, die, wenn darauf geklickt wird, ein Dialogfeld mit einem [Entitätsformular](entity-forms.md) öffnet, das einem Benutzer ermöglicht, einen neuen Datensatz zu erstellen.  

### <a name="create-action-settings"></a>Aktion "Erstellen"-Einstellungen

| Name                  | Beschreibung                                                                                                                                                                                                                                                 |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                                                                                                                                             |
| Entitätsformular           | Gibt die [Entitätsformulare und benutzerdefinierte Logik](entity-forms.md) an, die verwendet werden, um den neuen Datensatz zu erstellen. In der Dropdown-Liste werden alle Entitätsformulare aufgeführt, die für den Entitätstyp des Unterrasters konfiguriert wurden.<br>**Hinweis**: Wenn der Entitätstyp des Unterrasters keine Entitätsformulare aufweist, wird eine leere Dropdown-Liste angezeigt. Ohne Angabe eines Entitätsformulars für die Aktion "Erstellen" wird diese ignoriert, und die Schaltfläche wird nicht im Entitätsformular des Unterrasters gerendert.                                |
| **Erweiterte Einstellungen** |                                                                                                                                                                                                                                                             |
| Schaltflächenbezeichnung          | Überschreibt die HTML-Beschriftung, die in der "Erstellen"-Aktionsschaltfläche über dem Unterraster angezeigt wird.                                                                                                                                                                           |
| Schaltfläche \"QuickInfo\"        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die "Erstellen"-Aktionsschaltfläche verweist.                                                                                                                                                            |

### <a name="create-form-dialog-box-advanced-settings"></a>Einstellungen für das "Formular erstellen"-Dialogfeld (erweitert)

| Name                   | Beschreibung                                                                                                                                     |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Laden von Meldungen        | Überschreibt die Nachricht, die angezeigt wird, während der Dialog lädt.                                                                                  |
| Position                  | Überschreibt das HTML, das in der Titelleiste des Dialogfelds angezeigt wird.                                                                                 |
| Text für Screenreader-Schaltfläche \"Verwerfen\" | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche "Verwerfen" des Dialogfelds zugeordnet ist.                                                                   |
| Größe                   | Gibt die Größe des "Formular erstellen"-Dialogfelds an. Die Optionen sind "Standard", "Groß" und "Klein". Die Standardgröße ist Groß. |
| CSS Klasse              | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                    |
| CSS-Klasse für Titel        | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                                        |
||

## <a name="download-action"></a>Herunterladen-Aktion

Das Aktivieren der **Herunterladen-Aktion** rendert eine Schaltfläche über dem Unterraster, die, wenn darauf geklickt wird, die Daten vom Unterraster in eine [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)]-Datei (.xlsx) herunterlädt.

### <a name="download-action-settings"></a>Einstellungen für Herunterladen-Aktion

| Name                  | Beschreibung                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                    |
| Keiner                  |                                                                                                    |
| **Erweiterte Einstellungen** |                                                                                                    |
| Schaltflächenbezeichnung          | Überschreibt die HTML-Beschriftung, die in der "Herunterladen"-Aktionsschaltfläche über dem Unterraster angezeigt wird.                |
| Schaltfläche \"QuickInfo\"        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die "Herunterladen"-Aktionsschaltfläche verweist. |
||

## <a name="associate-action"></a>Zuordnen-Aktion

Das Aktivieren von **Aktion zuordnen** zeigt eine Schaltfläche über dem Unterraster an, die, wenn darauf geklickt wird, einen Dialog mit einer Tabelle der Entitäten öffnet, die der Benutzer zu dem Entitätsdatensatz zuordnen kann, der aktuell vom [Entitätsformular](entity-forms.md) angezeigt wird, wenn das Recht "Anfügen" und "Anfügen an" von den [Entitätsberechtigungen](assign-entity-permissions.md) für die anwendbaren Entitätstypen gewährt wurde.  

### <a name="associate-action-settings"></a>Einstellungen für die Zuordnen-Aktion

| Name                  | Beschreibung                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                                                                                                            |
| Anzeigen                  | Gibt die Ansicht (Gespeicherte Abfrage) an, die verwendet wird, um die Liste der berechtigten Entitäten zu suchen und anzuzeigen.<br>**Hinweis**: Wenn der Entitätstyp des Unterrasters keine gespeicherten Abfragen aufweist, wird eine leere Dropdown-Liste angezeigt. Ohne Angabe einer Ansicht für die Aktion "Zuordnen" wird diese ignoriert, und die Schaltfläche wird nicht im Entitätsformular des Unterrasters gerendert.  |
| **Erweiterte Einstellungen** |                                                                                                                                                                                                                            |
| Schaltflächenbezeichnung          | Überschreibt die HTML-Beschriftung, die in der "Zuordnen"-Aktionsschaltfläche über dem Unterraster angezeigt wird.                                                                                                                                       |
| Schaltfläche \"QuickInfo\"        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die "Zuordnen"-Aktionsschaltfläche verweist.                                                                                                                        |
||

### <a name="lookup-dialog-box-advanced-settings"></a>Einstellungen für den Dialog "Suchen" (erweitert)

| Name                     | Beschreibung                                                                                                                                 |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| Position                    | Überschreibt das HTML, das in der Titelleiste des Dialogfelds angezeigt wird.                                                                             |
| Text der primären Schaltfläche      | Überschreibt das HTML, das in der primären Schaltfläche (Hinzufügen) des Dialogfelds angezeigt wird.                                                                |
| Schaltflächentext schließen        | Überschreibt das HTML, das in der primären Schließen-Schaltfläche (Abbrechen) des Dialogfelds angezeigt wird.                                                               |
| Text für Screenreader-Schaltfläche \"Verwerfen\"   | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche "Verwerfen" des Dialogfelds zugeordnet ist.                                                               |
| Größe                     | Gibt die Größe des "Zuordnen"-Dialogfelds an. Die Optionen sind "Standard", "Groß" und "Klein". Die Standardgröße ist Groß. |
| CSS Klasse                | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                |
| CSS-Klasse für Titel          | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                                    |
| CSS-Klasse für primäre Schaltfläche | Geben Sie eine CSS-Klasse oder Klassen an, die auf die primäre Schaltfläche (Hinzufügen) des Dialogfelds angewendet werden.                                                 |
| CSS-Klasse für Schaltfläche „Schließen”   | Geben Sie eine CSS-Klasse oder Klassen an, die für die primäre „Schließen”-Schaltfläche (Abbrechen) des Dialogfelds angewendet werden.                                                |
| Titel für Datensätze auswählen     | Überschreibt das HTML, das im Titel des Bereichs "Datensatzauswahl" angezeigt wird.                                                                  |
| Standardfehlermeldung    | Überschreibt die Meldung, die angezeigt wird, wenn ein Fehler beim Zuordnen der ausgewählten Entität oder Entitäten auftritt.                                  |
| Rasteroptionen             | Geben Sie Einstellungen für die Darstellung des Entitätsrasters an. Optionen finden Sie unten.                                                              |
||

### <a name="lookup-dialog-box-advanced-grid-options-settings"></a>Rasteroptions-Einstellungen für den Dialog "Suchen" (erweitert)

| Name                  | Beschreibung                                                                                                              |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------|
| Laden von Meldungen       | Überschreibt die Nachricht, die angezeigt wird, während das Entitätenraster lädt.                                                |
| Fehlermeldung         | Überschreibt die Nachricht, die angezeigt wird, wenn ein Fehler auftritt, während das Entitätenraster lädt.                               |
| Meldung vom Typ \"Zugriff verweigert\" | Überschreibt die Meldung, die angezeigt wird, wenn ein Benutzer keine ausreichenden Entitätsberechtigungen besitzt, um das Raster von Entitäten anzuzeigen. |
| Leere Meldung         | Überschreibt die Meldung, die angezeigt wird, wenn keine Entitäten vorhanden sind, die dem aktuellen Entitätsformular zugeordnet werden können.       |
| CSS Klasse             | Geben Sie eine CSS-Klasse oder Klassen an, die auf den Bereich „Raster zuordnen” angewendet werden.                                          |
| CSS-Klasse für Raster        | Geben Sie eine CSS-Klasse oder Klassen an, die auf das Element &lt;table&gt; des zugehörigen Rasters angewendet werden.                       |
||

## <a name="details-action"></a>Details-Aktion

Bei der Aktivierung von **Details-Aktion** kann ein Benutzer ein schreibgeschütztes [Entitätsformular](entity-forms.md) anzeigen, das mit dem Datensatz der ausgewählten Zeile des Unterrasters datengebunden ist.  

### <a name="details-action-settings"></a>Detail-Aktion-Einstellungen

|                 Name                  |                                                                                                                                                                                                                        Beschreibung                                                                                                                                                                                                                        |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Grundlegende Einstellungen**           |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|              Entitätsformular              | Gibt das [Entitätsformular](entity-forms.md) an, das zum Anzeigen der Details des ausgewählten Datensatzes verwendet wird. In der Dropdown-Liste werden alle Entitätsformulare aufgeführt, die für den Entitätstyp des Unterrasters konfiguriert wurden. <br>**Hinweis**: Wenn der Entitätstyp des Unterrasters keine Entitätsformulare aufweist, wird eine leere Dropdown-Liste angezeigt. Ohne Angabe eines Entitätsformulars für "Detail-Aktion" wird diese ignoriert, und die Schaltfläche wird nicht im Unterraster gerendert. |
|         **Erweiterte Einstellungen**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Abfragezeichenfolgen-Parametername für Datensatz-ID |                                                                      Gibt den Namen des Abfragezeichenfolgenparameters an, das verwendet wird, um die Entität auszuwählen, die im ausgewählten Entitätsformular angezeigt werden soll. Dies sollte dem Wert des Abfragezeichenfolgen-Parameternamens für Datensatz-ID dieses Entitätsformulars entsprechen. Der Standardwert für dieses Feld, sowohl hier als auch in der Entitätsformularkonfiguration, ist **id**.                                                                       |
|             Schaltflächenbezeichnung              |                                                                                                                                                                                          Überschreibt die HTML-Beschriftung für diese Aktion, die in der Unterrasterzeile angezeigt wird.                                                                                                                                                                                           |
|            Schaltfläche \"QuickInfo\"             |                                                                                                                                                                 Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion, die in der Unterrasterzeile angezeigt wird, zeigt.                                                                                                                                                                  |
|                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

### <a name="details-form-dialog-box-advanced-settings"></a>Einstellungen für den Dialog "Detail-Formular" (erweitert)

| Name                   | Beschreibung                                                                                                                             |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Laden von Meldungen        | Überschreibt das HTML, das angezeigt wird, während das Dialogfeld geladen wird.                                                                             |
| Position                  | Überschreibt das HTML, das in der Titelleiste des Dialogfelds angezeigt wird.                                                                         |
| Text für Screenreader-Schaltfläche \"Verwerfen\" | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche "Verwerfen" des Dialogfelds zugeordnet ist.                                                           |
| Größe                   | Gibt die Größe des "Detail"-Dialogfelds an. Die Optionen sind "Standard", "Groß" und "Klein". Die Standardgröße ist Groß. |
| CSS Klasse              | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                            |
| CSS-Klasse für Titel        | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                                |
||

## <a name="edit-action"></a>Bearbeiten-Aktion

Durch Aktivieren einer **Bearbeiten-Aktion** kann ein Benutzer ein bearbeitbares [Entitätsformular](entity-forms.md), das an den Datensatz der ausgewählten Zeile der Entitätsliste datengebunden ist, wenn das Recht "Schreiben" von Datensatzbasierte Sicherheit mithilfe der [Entitätsberechtigungen](assign-entity-permissions.md) gewährt wurde.  

### <a name="edit-action-settings"></a>Einstellungen der Bearbeiten-Aktion

| Name                                  | Beschreibung                                                                                                                                                                                                                                                                                                  |
|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**                    |                                                                                                                                                                                                                                                                                                              |
| Entitätsformular                           | Gibt das [Entitätsformular](entity-forms.md) an, das verwendet wird, um den ausgewählten Datensatz zu bearbeiten. In der Dropdown-Liste werden alle Entitätsformulare aufgeführt, die für den Entitätstyp des Unterrasters konfiguriert wurden.<br>**Hinweis**: Wenn der Entitätstyp des Unterrasters keine Entitätsformulare aufweist, wird eine leere Dropdown-Liste angezeigt. Ohne Angabe eines Entitätsformulars für die "Bearbeiten-Aktion" wird diese ignoriert, und die Schaltfläche wird nicht im Unterraster gerendert.                                                                                                 |
| **Erweiterte Einstellungen**                 |                                                                                                                                                                                                                                                                                                              |
| Abfragezeichenfolgen-Parametername für Datensatz-ID | Gibt den Namen des Abfragezeichenfolgenparameters an, das verwendet wird, um die Entität auszuwählen, die im ausgewählten Entitätsformular bearbeitet werden soll. Dies sollte dem Wert des Abfragezeichenfolgen-Parameternamens für Datensatz-ID dieses Entitätsformulars entsprechen. Der Standardwert für dieses Feld, sowohl hier als auch in der Entitätsformularkonfiguration, ist **id**. |
| Schaltflächenbezeichnung                          | Überschreibt die HTML-Beschriftung für diese Aktion, die in der Unterrasterzeile angezeigt wird.                                                                                                                                                                                                                                       |
| Schaltfläche \"QuickInfo\"                        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion, die in der Unterrasterzeile angezeigt wird, zeigt.                                                                                                                                                                              |
||

### <a name="edit-form-dialog-box-advanced-settings"></a>Einstellungen für das Dialogfeld "Formular bearbeiten" (erweitert)

| Name                   | Beschreibung                                                                                                                       |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Laden von Meldungen        | Überschreibt das HTML, das angezeigt wird, während das Dialogfeld geladen wird.                                                                       |
| Position                  | Überschreibt das HTML, das in der Titelleiste des Dialogfelds angezeigt wird.                                                                   |
| Text für Screenreader-Schaltfläche \"Verwerfen\" | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche "Verwerfen" des Dialogfelds zugeordnet ist.                                                     |
| Größe                   | Gibt die Größe des "Bearbeiten"-Dialogfelds an. Die Optionen sind "Standard", "Groß" und "Klein". Die Standardgröße ist Groß. |
| CSS Klasse              | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                      |
| CSS-Klasse für Titel        | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                          |
||

## <a name="delete-action"></a>Löschen-Aktion

Durch Aktivieren von **Aktion löschen** kann ein Benutzer die Entität, die von einer Zeile im Unterraster dargestellt wird, dauerhaft löschen, wenn das Recht [Entitätsberechtigungen](assign-entity-permissions.md) gewährt wurde.  

### <a name="delete-action-settings"></a>Einstellungen der Löschen-Aktion

| Name                  | Beschreibung                                                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                 |
| Keiner                  |                                                                                                                                 |
| **Erweiterte Einstellungen** |                                                                                                                                 |
| Bestätigung          | Überschreibt die Bestätigungs-HTML-Nachricht, die angezeigt wird, wenn der Benutzer die Löschen-Aktion aktiviert.                                    |
| Schaltflächenbezeichnung          | Überschreibt die HTML-Beschriftung für diese Aktion, die in der Unterrasterzeile angezeigt wird.                                                          |
| Schaltfläche \"QuickInfo\"        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion, die in der Unterrasterzeile angezeigt wird, zeigt. |
||

### <a name="delete-dialog-box-advanced-settings"></a>Einstellungen für das Dialogfeld "Löschen" (erweitert)

| Name                     | Beschreibung                                                                                                                             |
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
||

## <a name="workflow-action"></a>Workflowaktion

Bei der Aktivierung der **Aktion "Workflow"** kann ein Benutzer einen bedarfsgesteuerten Workflow für den ausgewählten Datensatz im Unterraster ausführen. Sie können eine beliebige Anzahl Workflow-Aktionen zu Unterraster-Metadaten hinzufügen.

### <a name="workflow-action-settings"></a>Einstellungen der Workflowaktion

| Name                  | Beschreibung                                                                                                                                                                                                     |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                                                                                                 |
| Workflow              | Gibt den bedarfsgesteuerten Workflow an, der ausgeführt wird, wenn der Benutzer diese Aktion aktiviert.<br>**Hinweis**: Wenn der Entitätstyp des Unterrasters keine Workflows aufweist, wird eine leere Dropdown-Liste angezeigt. Ohne Angabe eines Workflows für die Aktion "Workflow" wird diese ignoriert, und die Schaltfläche wird nicht im Unterraster gerendert.  |
| Schaltflächenbezeichnung          | Legt die HTML-Beschriftung für diese Aktion fest, die in der Unterrasterzeile angezeigt wird. In diesem Feld ist ein Eintrag erforderlich.                                                                                                                     |
| **Erweiterte Einstellungen** |                                                                                                                                                                                                                 |
| Schaltfläche \"QuickInfo\"        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion, die in der Unterrasterzeile angezeigt wird, zeigt.                                                                                 |
||

## <a name="disassociate-action"></a>Aktion "Zuordnung aufheben"

Bei Aktivierung der Aktion **Zuordnung aufheben** kann ein Benutzer den Link zwischen dem Datensatz, der vom aktuell angezeigten [Entitätsformular](entity-forms.md) dargestellt wird, und dem Datensatz, der von der ausgewählten Zeile im Unterraster dargestellt wird, entfernen, wenn das Recht "Anfügen" und "Anfügen an" von den [Entitätsberechtigungen](assign-entity-permissions.md) für die anwendbaren Entitätstypen gewährt wurde.

### <a name="disassociate-action-settings"></a>Einstellungen der Aktion "Zuordnung aufheben"

| Name                  | Beschreibung                                                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                 |
| Keiner                  |                                                                                                                                 |
| **Erweiterte Einstellungen** |                                                                                                                                 |
| Schaltflächenbezeichnung          | Überschreibt die HTML-Beschriftung für diese Aktion, die in der Unterrasterzeile angezeigt wird.                                                          |
| Schaltfläche \"QuickInfo\"        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion, die in der Unterrasterzeile angezeigt wird, zeigt. |
||

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Entitätsformulare definieren](entity-forms.md)  
[Webformulareigenschaften für Portale](web-form-properties.md)  
[Webformularschritte für Portale](web-form-steps.md)  
[Web-Formulare-Metadaten für Portale](configure-web-form-metadata.md)  
[Notizkonfiguration für Webformular für Portale](../configure-notes.md)  

