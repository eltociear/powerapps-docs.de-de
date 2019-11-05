---
title: Webformular-unter Raster Konfiguration für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren von Webformular-unter Raster für ein Portal.
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552955"
---
# <a name="configure-web-form-subgrids-for-portals"></a>Konfigurieren von Webformular-unter Raster für Portale

Webformular-unter Raster werden in gleicher Weise als Entitäts Formular-unter Raster konfiguriert: Erstellen Sie zunächst einen metadatendatensatz für den Webformular Schritt, der ein unter Raster enthält, und fügen Sie dann Konfigurations Metadaten hinzu.

Das Hinzufügen von Unterverzeichnissen zu Ihren verwalteten Formularen im Portal ist einfach – fügen Sie einfach das unter Raster dem Formular hinzu, das Sie mit dem fertigen Formular-Designer verwalten, und Sie sind fertig. Im Raster wird die Ansicht verwendet, die im Common Data Service Formular-Designer angegeben ist, nur verknüpfte Datensätze anzeigen, wenn diese Option ausgewählt wurde, optional eine Suchleiste anzeigen und sogar [Entitäts Berechtigungen für Portale](assign-entity-permissions.md)berücksichtigen. Es ist nicht einfacher, eine schreibgeschützte Liste von Datensätzen anzuzeigen. Zum Aktivieren von Aktionen für das Raster – erstellen, aktualisieren, löschen usw. – müssen Sie diese Aktionen mithilfe der Metadatenkonfiguration konfigurieren.

## <a name="add-subgrid-metadata-to-your-form"></a>Hinzufügen von Subgrid-Metadaten zum Formular

Wenn Sie einem Entitäts Formular Subgrid-Metadaten hinzufügen möchten, navigieren Sie zu den **Metadaten der Entität** , indem Sie entweder die Dropdown Liste oben oder das untergeordnete Element des Datensatzes verwenden, mit dem Sie arbeiten. Weitere Informationen finden Sie unter [Definieren von Entitäts Formularen](entity-forms.md).

Um einen neuen Datensatz hinzuzufügen, wählen Sie **neue Entitäts Formular Metadaten hinzufügen aus**.

Wählen Sie zum Bearbeiten eines vorhandenen Datensatzes den Datensatz im Raster aus. Wenn Sie **Subgrid** als **Type** -Wert auswählen, wird ein anderes Attribut, **Subgrid Name**, angezeigt.


|     Name     |                                                       Beschreibung                                                        |
|--------------|--------------------------------------------------------------------------------------------------------------------------|
| Name des subrasters | Der eindeutige Name des untergeordneten Rasters im verknüpften Formular der Entität. |
|              |                                                                                                                          |

Wenn Sie das unter Raster im Formular-Editor auswählen, wird ein Eigenschaften Fenster angezeigt. Diese enthält ein **namens** Feld, das verwendet werden soll, um dem Feld **unter Raster Name** im metadatendatensatz der Entitäts Form zuzuweisen.

![Subgrid-Metadaten hinzufügen](../media/add-subgrid-metadata.png "Subgrid-Metadaten hinzufügen")  

Wenn Sie einen gültigen Subgrid-Namen angeben, werden die Subgrid-Konfigurationseinstellungen angezeigt. Standardmäßig werden nur **grundlegende Einstellungen** angezeigt. Wählen Sie **Erweiterte Einstellungen** aus, um zusätzliche Einstellungen anzuzeigen.

Standardmäßig werden die meisten Einstellungen reduziert angezeigt, um Speicherplatz zu sparen. Wählen Sie * * * * aus, um einen Abschnitt zu erweitern und weitere Optionen anzuzeigen. Wählen Sie * * * * aus, um den Bereich zu reduzieren.

## <a name="attributes"></a>Attribute

| Name                       | Beschreibung                                                                                                                                                                                                                                                                                                                                                               |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**         |                                                                                                                                                                                                                                                                                                                                                                           |
| Aktionen anzeigen               | Verwenden Sie diese Schaltfläche, um Aktions Schaltflächen für Aktionen hinzuzufügen, die für die Entitätenmenge anwendbar sind und über dem unter Raster Folgende Aktionen sind verfügbar: <ul><li>Stelle</li><li>Download</li><li>Ierter</li></ul> Wenn Sie eine dieser Optionen auswählen, wird ein Konfigurationsbereich für diese Aktion angezeigt. Weitere Informationen zu den einzelnen Aktionen finden Sie unten.                                                                                                                                                                                                                                                   |
| Element Aktionen               | Verwenden Sie diese Schaltfläche, um Aktions Schaltflächen für Aktionen hinzuzufügen, die für einen einzelnen Datensatz anwendbar sind und in den einzelnen Zeilen des subrasters angezeigt werden, sofern die zugeordneten [Berechtigungen durch Entitäts Berechtigungen](assign-entity-permissions.md)erteilt wurden. Folgende Aktionen sind verfügbar: <ul><li>Details</li><li>Bearbeiten</li><li>Lösch</li><li>Workflow</li><li>Aufheben</li></ul> Wenn Sie eine dieser Optionen auswählen, wird ein Konfigurationsbereich für diese Aktion angezeigt. Weitere Informationen zu den einzelnen Aktionen finden Sie unten.                                                                                                                                                                                                                                                   |
| Spalten Attribute überschreiben | Verwenden Sie, um Anzeigeeinstellungen für einzelne Spalten im Raster zu überschreiben. <ul><li>Attribute: logischer Name der Spalte, die Sie überschreiben möchten.</li><li>Anzeige Name: neuer Spaltentitel, um den Standardwert zu überschreiben</li><li>Width: die Breite (in Prozent oder Pixel) der Spalte, um die Standardeinstellung zu überschreiben. Siehe auch Raster Spalten-breiten Stil. Um Einstellungen für eine Spalte zu überschreiben, wählen Sie **Spalte** aus, und geben Sie die Details ein.                                                                                                                                                                                                                                                                                             |
| **Erweiterte Einstellungen**      |                                                                                                                                                                                                                                                                                                                                                                           |
| Meldung wird geladen            | Überschreibt die HTML-Standardmeldung, die beim Laden des subrasters angezeigt wird.                                                                                                                                                                                                                                                                                             |
| Fehlermeldung              | Überschreibt die HTML-Standardmeldung, die angezeigt wird, wenn beim Laden des subrasters ein Fehler auftritt.                                                                                                                                                                                                                                                                           |
| Meldung "Zugriff verweigert"      | Überschreibt die HTML-Standardmeldung, die angezeigt wird, wenn ein Benutzer nicht über ausreichende [Berechtigungen](assign-entity-permissions.md) zum Lesen des dem subraster zugeordneten Entitäts Typs verfügt.                       |
| Leere Nachricht              | Überschreibt die HTML-Meldung, die angezeigt wird, wenn das zugehörige unter Raster keine Daten enthält.                                                                                                                                                                                                                                                                                     |
| Such Dialogfeld              | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Aktion "zuordnen" aktiviert.                                                                                                                                                                                                                                                                             |
| Dialog Feld "Details"        | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Detail Aktion aktiviert.                                                                                                                                                                                                                                                                                |
| Formular bearbeiten-Dialog Feld           | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Bearbeitungsaktion aktiviert.                                                                                                                                                                                                                                                                                   |
| Dialog Feld Create Form         | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die CREATE-Aktion aktiviert.                                                                                                                                                                                                                                                                                 |
| Dialog Feld löschen              | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn ein Benutzer die Löschaktion aktiviert.                                                                                                                                                                                                                                                                                 |
| Fehler Dialogfeld               | Steuert die Einstellungen für das Dialogfeld, das angezeigt wird, wenn während einer beliebigen Aktion ein Fehler auftritt.                                                                                                                                                                                                                                                                                 |
| CSS-Klasse                  | Geben Sie eine CSS-Klasse oder Klassen an, die auf das HTML-Element angewendet werden, das den gesamten Teil Raster Bereich enthält, einschließlich der Raster-und Aktions Schaltflächen.                                                                                                                                                                                                                     |
| Grid-CSS-Klasse             | Geben Sie eine CSS-Klasse oder Klassen an, die auf die HTML-&lt;Tabelle des subrasters&gt;-Elements angewendet werden.                                                                                                                                                                                                                                                                          |
| Breite der Raster Spaltenbreite    | Konfiguriert, ob die **breiten** Werte in den Attributen der Überschreibungs Spalte in **Pixel** oder **Prozent**angegeben werden.                                                                                                                                                                                                                                                             |
||

## <a name="create-action"></a>Aktion erstellen

Durch das Aktivieren einer **create-Aktion** wird eine Schaltfläche oberhalb des untergeordneten Rasters gerendert. wenn diese Option ausgewählt ist, wird ein Dialogfeld mit einem [Entitäts Formular](entity-forms.md) geöffnet, mit dem ein Benutzer einen neuen Datensatz  

### <a name="create-action-settings"></a>Aktions Einstellungen erstellen

| Name                  | Beschreibung                                                                                                                                                                                                                                                 |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                                                                                                                                             |
| Entitäts Formular           | Gibt die [Entitäts Formulare und die benutzerdefinierte Logik](entity-forms.md) an, die zum Erstellen des neuen Datensatzes verwendet werden. Die Dropdown Liste enthält alle Entitäts Formulare, die für den Entitätstyp des subrasters konfiguriert sind.<br>**Hinweis**: Wenn der Entitätstyp des subrasters keine Entitäts Formulare aufweist, wird die Dropdown Liste leer angezeigt. Wenn für die CREATE-Aktion kein Entitäts Formular bereitgestellt wird, wird es ignoriert, und die Schaltfläche wird nicht im Entitäts Formular des subrasters gerendert.                                |
| **Erweiterte Einstellungen** |                                                                                                                                                                                                                                                             |
| Schaltflächen Bezeichnung          | Überschreibt die HTML-Bezeichnung, die in der Schaltfläche Aktion erstellen oberhalb des untergeordneten Rasters angezeigt wird.                                                                                                                                                                           |
| QuickInfo        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche Aktion erstellen zeigt.                                                                                                                                                            |

### <a name="create-form-dialog-box-advanced-settings"></a>Dialogfeld ' Formular erstellen ' Erweiterte Einstellungen

| Name                   | Beschreibung                                                                                                                                     |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Meldung wird geladen        | Überschreibt die Meldung, die beim Laden des Dialog Felds angezeigt wird.                                                                                  |
| Title                  | Überschreibt den HTML-Code, der in der Titelleiste des Dialog Felds angezeigt wird.                                                                                 |
| SR-Text der Schaltfläche verwerfen | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                                   |
| Größe                   | Gibt die Größe des Dialog Felds Create Form an. Die Optionen lauten "Standard", "groß" und "klein". Die Standardgröße ist groß. |
| CSS-Klasse              | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                    |
| Title-CSS-Klasse        | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                                        |
||

## <a name="download-action"></a>Download Aktion

Durch das Aktivieren einer **Download Aktion** wird eine Schaltfläche oberhalb des subrasters gerendert, bei der die Daten aus dem subraster in eine [!INCLUDE[pn-excel-short](../../../includes/pn-excel-short.md)] Datei (. xlsx) heruntergeladen werden.

### <a name="download-action-settings"></a>Aktions Einstellungen herunterladen

| Name                  | Beschreibung                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                    |
| Gar                  |                                                                                                    |
| **Erweiterte Einstellungen** |                                                                                                    |
| Schaltflächen Bezeichnung          | Überschreibt die HTML-Bezeichnung, die auf der Schaltfläche zum Herunterladen von Aktionen über dem unter Raster angezeigt wird                |
| QuickInfo        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche Download Aktion zeigt. |
||

## <a name="associate-action"></a>Aktion zuordnen

Beim Aktivieren einer Zuordnungs **Aktion** wird eine Schaltfläche oberhalb des untergeordneten Rasters angezeigt. wenn diese Option ausgewählt ist, wird eine Tabelle von Entitäten geöffnet, die der Benutzer dem derzeit vom [Entitäts Formular](entity-forms.md)angezeigten Entitäts Daten Satz zuordnen kann, sofern das Anfügen und das Appendto-Berechtigungen wurden durch [Entitäts Berechtigungen](assign-entity-permissions.md) für die entsprechenden Entitäts Typen erteilt.  

### <a name="associate-action-settings"></a>Aktions Einstellungen zuordnen

| Name                  | Beschreibung                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                                                                                                            |
| Anschauung                  | Gibt die Ansicht (gespeicherte Abfrage) an, die verwendet wird, um die Liste der berechtigten Entitäten zu suchen und anzuzeigen.<br>**Hinweis**: Wenn der Entitätstyp des subrasters keine gespeicherten Abfragen enthält, wird die Dropdown Liste leer angezeigt. Wenn für die Aktion "zuordnen" keine Ansicht bereitgestellt wird, wird Sie ignoriert, und die Schaltfläche wird nicht im Entitäts Formular des subrasters gerendert.  |
| **Erweiterte Einstellungen** |                                                                                                                                                                                                                            |
| Schaltflächen Bezeichnung          | Überschreibt die HTML-Bezeichnung, die in der Schaltfläche Aktion zuordnen oberhalb des subrasters angezeigt wird.                                                                                                                                       |
| QuickInfo        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche Aktion zuordnen zeigt.                                                                                                                        |
||

### <a name="lookup-dialog-box-advanced-settings"></a>Erweiterte Einstellungen für das Such Dialogfeld

| Name                     | Beschreibung                                                                                                                                 |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| Title                    | Überschreibt den HTML-Code, der in der Titelleiste des Dialog Felds angezeigt wird.                                                                             |
| Primärer Schaltflächen Text      | Überschreibt den HTML-Code, der in der primären Schaltfläche (hinzufügen) im Dialogfeld angezeigt wird.                                                                |
| Schaltflächen Text schließen        | Überschreibt den HTML-Code, der in der Schaltfläche Schließen (Abbrechen) im Dialogfeld angezeigt wird.                                                               |
| SR-Text der Schaltfläche verwerfen   | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                               |
| Größe                     | Gibt die Größe des Dialog Felds "zuordnen" an. Die Optionen lauten "Standard", "groß" und "klein". Die Standardgröße ist groß. |
| CSS-Klasse                | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                |
| Title-CSS-Klasse          | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                                    |
| CSS-Klasse der primären Schaltfläche | Geben Sie eine CSS-Klasse oder Klassen an, die auf die primäre Schaltfläche (hinzufügen) des Dialog Felds angewendet werden.                                                 |
| CSS-Klasse der Schaltfläche Schließen   | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Schaltfläche Schließen (Abbrechen) des Dialog Felds angewendet werden.                                                |
| Titel der Datensätze auswählen     | Überschreibt den HTML-Code, der im Titel des Auswahl Bereichs für den Datensatz angezeigt wird.                                                                  |
| Standard Fehlermeldung    | Überschreibt die Meldung, die angezeigt wird, wenn ein Fehler auftritt, während die ausgewählte Entität oder Entitäten zugeordnet werden.                                  |
| Raster Optionen             | Geben Sie Einstellungen für die Darstellung des Entitäts Rasters an. Weitere Optionen finden Sie unten.                                                              |
||

### <a name="lookup-dialog-box-advanced-grid-options-settings"></a>Dialogfeld "Suche" Erweiterte Raster Options Einstellungen

| Name                  | Beschreibung                                                                                                              |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------|
| Meldung wird geladen       | Überschreibt die Meldung, die angezeigt wird, während das Raster der Entitäten geladen wird.                                                |
| Fehlermeldung         | Überschreibt die Meldung, die angezeigt wird, wenn ein Fehler beim Laden des Raster von Entitäten auftritt.                               |
| Meldung "Zugriff verweigert" | Überschreibt die Meldung, die angezeigt wird, wenn ein Benutzer nicht über ausreichende Entitäts Berechtigungen zum Anzeigen des Raster von Entitäten verfügt. |
| Leere Nachricht         | Überschreibt die Meldung, die angezeigt wird, wenn keine Entitäten vorhanden sind, die mit dem aktuellen Entitäts Formular verknüpft werden können.       |
| CSS-Klasse             | Geben Sie eine CSS-Klasse oder Klassen an, die auf den Bereich "zuordnen" angewendet werden.                                          |
| Grid-CSS-Klasse        | Geben Sie eine CSS-Klasse oder Klassen an, die auf die &lt;Tabelle&gt;-Elements des verknüpften Rasters angewendet werden.                       |
||

## <a name="details-action"></a>Detail Aktion

Durch das Aktivieren einer **Detail Aktion** kann ein Benutzer ein Schreib geschütztes [Entitäts Formular](entity-forms.md) anzeigen, das an den Datensatz der ausgewählten Zeile des subrasters gebunden ist.  

### <a name="details-action-settings"></a>Details zu Aktions Einstellungen

|                 Name                  |                                                                                                                                                                                                                        Beschreibung                                                                                                                                                                                                                        |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Grundlegende Einstellungen**           |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|              Entitäts Formular              | Gibt das [Entitäts Formular](entity-forms.md) an, das zum Anzeigen der Details des ausgewählten Datensatzes verwendet wird. Die Dropdown Liste enthält alle Entitäts Formulare, die für den Entitätstyp des subrasters konfiguriert sind. <br>**Hinweis**: Wenn der Entitätstyp des subrasters keine Entitäts Formulare aufweist, wird die Dropdown-Anzeige leer angezeigt. Wenn für die Detail Aktion kein Entitäts Formular bereitgestellt wird, wird es ignoriert, und die Schaltfläche wird nicht im subraster gerendert. |
|         **Erweiterte Einstellungen**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Name der Abfrage Zeichenfolge für Datensatz-ID |                                                                      Gibt den Namen des Abfrage Zeichenfolgen-Parameters an, der verwendet wird, um die Entität auszuwählen, die im ausgewählten Entitäts Formular angezeigt werden soll. Dieser Wert muss mit dem Wert in der Abfrage Zeichenfolge des Datensatz-ID-Abfrage Zeichenfolgen für den Datensatz Der Standardwert für dieses Feld ist sowohl hier als auch in der Formular Konfiguration der Entität " **ID**".                                                                       |
|             Schaltflächen Bezeichnung              |                                                                                                                                                                                          Überschreibt die HTML-Bezeichnung für diese Aktion, die in der unter Raster Zeile angezeigt wird.                                                                                                                                                                                           |
|            QuickInfo             |                                                                                                                                                                 Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion zeigt, die in der unter Raster Zeile angezeigt wird.                                                                                                                                                                  |
|                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

### <a name="details-form-dialog-box-advanced-settings"></a>Dialogfeld "Detail Formular" Erweiterte Einstellungen

| Name                   | Beschreibung                                                                                                                             |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Meldung wird geladen        | Überschreibt den HTML-Code, der beim Laden des Dialog Felds angezeigt wird.                                                                             |
| Title                  | Überschreibt den HTML-Code, der in der Titelleiste des Dialog Felds angezeigt wird.                                                                         |
| SR-Text der Schaltfläche verwerfen | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                           |
| Größe                   | Gibt die Größe des Dialog Felds "Details" an. Die Optionen lauten "Standard", "groß" und "klein". Die Standardgröße ist groß. |
| CSS-Klasse              | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                            |
| Title-CSS-Klasse        | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                                |
||

## <a name="edit-action"></a>Aktion bearbeiten

Durch das Aktivieren einer **Bearbeitungsaktion** kann ein Benutzer ein bearbeitbares [Entitäts Formular](entity-forms.md) anzeigen, das an den Datensatz der ausgewählten Zeile des subrasters gebunden ist, wenn die Schreib Berechtigung durch [Entitäts Berechtigungen](assign-entity-permissions.md)erteilt wurde.  

### <a name="edit-action-settings"></a>Aktions Einstellungen bearbeiten

| Name                                  | Beschreibung                                                                                                                                                                                                                                                                                                  |
|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**                    |                                                                                                                                                                                                                                                                                                              |
| Entitäts Formular                           | Gibt das [Entitäts Formular](entity-forms.md) an, das verwendet wird, um den ausgewählten Datensatz zu bearbeiten. Die Dropdown Liste enthält alle Entitäts Formulare, die für den Entitätstyp des subrasters konfiguriert sind.<br>**Hinweis**: Wenn der Entitätstyp des subrasters keine Entitäts Formulare aufweist, wird die Dropdown Liste leer angezeigt. Wenn für die Aktion bearbeiten keine Entitäts Form bereitgestellt wird, wird diese ignoriert, und die Schaltfläche wird nicht im subraster gerendert.                                                                                                 |
| **Erweiterte Einstellungen**                 |                                                                                                                                                                                                                                                                                                              |
| Name der Abfrage Zeichenfolge für Datensatz-ID | Gibt den Namen des Abfrage Zeichenfolgen-Parameters an, der verwendet wird, um die Entität auszuwählen, die im ausgewählten Entitäts Formular bearbeitet werden soll. Dieser Wert muss mit dem Wert in der Abfrage Zeichenfolge des Datensatz-ID-Abfrage Zeichenfolgen für den Datensatz Der Standardwert für dieses Feld ist sowohl hier als auch in der Formular Konfiguration der Entität " **ID**". |
| Schaltflächen Bezeichnung                          | Überschreibt die HTML-Bezeichnung für diese Aktion, die in der unter Raster Zeile angezeigt wird.                                                                                                                                                                                                                                       |
| QuickInfo                        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion zeigt, die in der unter Raster Zeile angezeigt wird.                                                                                                                                                                              |
||

### <a name="edit-form-dialog-box-advanced-settings"></a>Dialogfeld "Formular bearbeiten" Erweiterte Einstellungen

| Name                   | Beschreibung                                                                                                                       |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Meldung wird geladen        | Überschreibt den HTML-Code, der beim Laden des Dialog Felds angezeigt wird.                                                                       |
| Title                  | Überschreibt den HTML-Code, der in der Titelleiste des Dialog Felds angezeigt wird.                                                                   |
| SR-Text der Schaltfläche verwerfen | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                     |
| Größe                   | Gibt die Größe des Dialog Felds bearbeiten an. Die Optionen lauten "Standard", "groß" und "klein". Die Standardgröße ist groß. |
| CSS-Klasse              | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                      |
| Title-CSS-Klasse        | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                          |
||

## <a name="delete-action"></a>DELETE-Aktion

Durch das Aktivieren einer **DELETE-Aktion** kann ein Benutzer die Entität, die durch eine Zeile im subraster dargestellt wird, endgültig löschen, wenn die Berechtigungen zum Löschen durch [Entitäts Berechtigungen](assign-entity-permissions.md)erteilt wurden.  

### <a name="delete-action-settings"></a>Aktions Einstellungen löschen

| Name                  | Beschreibung                                                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                 |
| Gar                  |                                                                                                                                 |
| **Erweiterte Einstellungen** |                                                                                                                                 |
| Bestätigt          | Überschreibt die HTML-Bestätigungsmeldung, die angezeigt wird, wenn der Benutzer die DELETE-Aktion aktiviert.                                    |
| Schaltflächen Bezeichnung          | Überschreibt die HTML-Bezeichnung für diese Aktion, die in der unter Raster Zeile angezeigt wird.                                                          |
| QuickInfo        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion zeigt, die in der unter Raster Zeile angezeigt wird. |
||

### <a name="delete-dialog-box-advanced-settings"></a>Erweiterte Dialogfeld Einstellungen löschen

| Name                     | Beschreibung                                                                                                                             |
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
||

## <a name="workflow-action"></a>Workflow Aktion

Durch das Aktivieren einer **Workflow Aktion** kann ein Benutzer einen bedarfsgesteuerten Workflow für den ausgewählten Datensatz im unter Raster ausführen. Sie können den Subgrid-Metadaten beliebig viele Workflow Aktionen hinzufügen.

### <a name="workflow-action-settings"></a>Workflow Aktions Einstellungen

| Name                  | Beschreibung                                                                                                                                                                                                     |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                                                                                                 |
| Workflow              | Gibt den bedarfsgesteuerten Workflow an, der ausgeführt wird, wenn der Benutzer diese Aktion aktiviert.<br>**Hinweis**: Wenn der Entitätstyp des subrasters keine Workflows enthält, wird die Dropdown Liste leer angezeigt. Wenn für die Workflow Aktion kein Workflow bereitgestellt wird, wird er ignoriert, und die Schaltfläche wird nicht im subraster gerendert.  |
| Schaltflächen Bezeichnung          | Legt die HTML-Bezeichnung für diese Aktion fest, die in der unter Raster Zeile angezeigt wird. Diese Einstellung ist erforderlich.                                                                                                                     |
| **Erweiterte Einstellungen** |                                                                                                                                                                                                                 |
| QuickInfo        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion zeigt, die in der unter Raster Zeile angezeigt wird.                                                                                 |
||

## <a name="disassociate-action"></a>Aufheben der Zuordnung von Aktionen

Durch das Aktivieren einer **diszuordnungs Aktion** kann ein Benutzer die Verknüpfung zwischen dem Datensatz, der durch das aktuell angezeigte [Entitäts Formular](entity-forms.md) dargestellt wird, und dem Datensatz entfernen, der von der ausgewählten Zeile im subraster dargestellt wird, solange die Anfüge-und appendto-Berechtigungen wurde durch [Entitäts Berechtigungen](assign-entity-permissions.md) für die entsprechenden Entitäts Typen erteilt.

### <a name="disassociate-action-settings"></a>Trennen von Aktions Einstellungen

| Name                  | Beschreibung                                                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                 |
| Gar                  |                                                                                                                                 |
| **Erweiterte Einstellungen** |                                                                                                                                 |
| Schaltflächen Bezeichnung          | Überschreibt die HTML-Bezeichnung für diese Aktion, die in der unter Raster Zeile angezeigt wird.                                                          |
| QuickInfo        | Überschreibt den QuickInfo-Text, der angezeigt wird, wenn der Benutzer auf die Schaltfläche für diese Aktion zeigt, die in der unter Raster Zeile angezeigt wird. |
||

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Portals](configure-portal.md)  
[Definieren von Entitäts Formularen](entity-forms.md)  
[Web Form-Eigenschaften für Portale](web-form-properties.md)  
[Webformular Schritte für Portale](web-form-steps.md)  
[Web Forms von Metadaten für Portale](configure-web-form-metadata.md)  
[Hinweise zur Konfiguration für Web Forms für Portale](../configure-notes.md)  

