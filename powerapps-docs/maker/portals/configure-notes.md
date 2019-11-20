---
title: Konfigurieren von Anmerkungen zu Entitäts Formularen und Webformularen für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren von Notizen zu Entitäts Formularen und Web Forms in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 59ed66842874414737b7bdc04f0f4dfa51d212c8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542851"
---
# <a name="configure-notes-for-entity-forms-and-web-forms-on-portals"></a>Konfigurieren von Notizen für Entity Forms und Web Forms in Portalen

Ebenso wie bei Unterverzeichnissen ist das Hinzufügen von Notizen zu Ihren verwalteten Formularen im Portal ganz einfach&mdash;fügen Sie das Notizen-Steuerelement einfach über den Formular- [Designer](../model-driven-apps/create-design-forms.md) zu den App-Formularen für Modell Laufwerke hinzu, und Sie sind fertig. Sie können das Verhalten des Notes-Steuer Elements mithilfe von Metadaten konfigurieren.

> [!Note]                                                           
> Explizite [Entitäts Berechtigungen](configure/assign-entity-permissions.md) sind erforderlich, damit Notizen im Portal angezeigt werden. Zum Lesen und bearbeiten müssen Lese-und Schreibberechtigungen erteilt werden. Zum erstellen müssen zwei Berechtigungen vorhanden sein: eine Berechtigung mit den Berechtigungen "Create" und "append" muss für die Note-Entität (Anmerkung) erteilt werden. die zweite Berechtigung muss dem Entitätstyp zugewiesen werden, an den der Hinweis mit der gewährten Berechtigung Anhängen angefügt wird. Das Kontrollkästchen **Entitäts Berechtigungen aktivieren** muss im entsprechenden Entitäts Formular-oder Webformular Schritt ausgewählt werden, damit die Entitäts Berechtigungen wirksam werden.

## <a name="notes-configuration-for-entity-forms"></a>Hinweise zur Konfiguration von Entitäts Formularen

1. Öffnen Sie die [Portal Verwaltungs-App](configure/configure-portal.md).
2. Wechseln Sie zu **Portale** > **Inhalts** > **Entitäts Formularen**. Eine Liste aktiver Entitäts Formulare wird angezeigt.
3. Wählen Sie das Entitäts Formular aus, dem Sie die Hinweis Konfiguration hinzufügen möchten.
4. Wechseln Sie zu den **Entitäts Formular Metadaten** , indem Sie entweder die Dropdown Liste oben oder das unter Raster im Hauptformular des Formulardaten Satzes der Entität verwenden, mit dem Sie arbeiten.
5. Wählen Sie **neue Entitäts Formular Metadaten hinzufügen aus** , um einen neuen Datensatz hinzuzufügen.
6. Wählen Sie in der Dropdown Liste **Typ** die Option **Notizen**aus. Die Notizen Konfigurations&ndash;bestimmte Einstellungen werden angezeigt. Die meisten Einstellungen sind standardmäßig reduziert. Sie können einen Abschnitt erweitern, um weitere Einstellungen anzuzeigen.
7. Füllen Sie die Felder aus, indem Sie die entsprechenden Werte eingeben. [!include[](../../includes/proc-more-information.md)] [Attribute](#attributes), [Dialog Optionen erstellen](#create-dialog-options), [Dialogfeld Optionen bearbeiten](#edit-dialog-options)und [Dialogfeld Optionen löschen](#delete-dialog-options)
8. Speichert das Formular.

    ![Hinweise zur Konfiguration von Entitäts Formularen hinzufügen](media/add-note-configuration.png "Hinweise zur Konfiguration von Entitäts Formularen hinzufügen")  

    Nachdem Sie die Konfiguration hinzugefügt haben, wird das Notiz Steuerelement mithilfe der im Portal aktivierten geeigneten Optionen gerendert.

## <a name="attributes"></a>Attribute


| Name                  | Beschreibung                                                                                                                                                  |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                                              |
| Erstellen aktiviert        | Ermöglicht das Hinzufügen neuer Notizen zur Entität.                                                                                                          |
| Dialog Feld Optionen erstellen | Enthält Einstellungen zum Konfigurieren des Dialog Felds, wenn **Create** "true" lautet. Weitere Informationen finden Sie unter CREATE Dialog Options.                                    |
| Bearbeitung aktiviert          | Ermöglicht das Bearbeiten vorhandener Notizen in der Entität.                                                                                                    |
| Dialog Feld Optionen bearbeiten   | Enthält Einstellungen zum Konfigurieren des Dialog Felds, wenn **editenabled** den Wert true aufweist. Weitere Informationen finden Sie unter Dialog Feld Optionen bearbeiten.                                         |
| Löschvorgang aktiviert        | Ermöglicht das Löschen von Notizen aus der Entität.                                                                                                         |
| Dialog Feld Optionen löschen | Enthält Einstellungen zum Konfigurieren des Dialog Felds, wenn **deleteaktivitrue** ist. Weitere Informationen finden Sie unter Dialog Feld "Optionen".                                     |
|Speicherort der Datei Anlage | Wählen Sie den Speicherort der Datei Anlage aus:<ul><li>Hinweis Anlage</li><li>Azure Blob Storage</li></ul>|
|MIME-Typen akzeptieren | Ermöglicht das Angeben einer Liste akzeptierter MIME-Typen. |
|MIME-Typen einschränken | Wählen Sie aus, ob MIME-Typen zugelassen oder eingeschränkt werden sollen.|
|Maximale Dateigröße (in KB) |Ermöglicht es Ihnen, die maximale Größe einer Datei anzugeben, die angefügt werden kann. |
| **Erweiterte Einstellungen** |                                                                                                                                                              |
| Listen Titel            | Überschreibt den Titel über den Bereich Notizen.                                                                                                                     |
| Bezeichnung für Hinweis Taste hinzufügen | Überschreibt die Bezeichnung auf der Schaltfläche Notizen hinzufügen.                                                                                                                 |
| Datenschutz Bezeichnung notieren    | Überschreibt die Bezeichnung, die anzeigt, dass ein Hinweis privat ist.                                                                                                         |
| Meldung wird geladen       | Überschreibt die Meldung, die angezeigt wird, während die Liste der Notizen geladen wird.                                                                                              |
| Fehlermeldung         | Überschreibt die Meldung, die angezeigt wird, wenn ein Fehler auftritt, wenn versucht wird, die Liste der Notizen zu laden.                                                                     |
| Meldung "Zugriff verweigert" | Überschreibt die Meldung, die angezeigt wird, wenn der Benutzer nicht über ausreichende Berechtigungen zum Anzeigen der Liste der Notizen verfügt.                                                    |
| Leere Nachricht         | Überschreibt die Meldung, die angezeigt wird, wenn die aktuelle Entität keine Notizen hat, die angezeigt werden können.                                                              |
| Auflisten von Aufträgen           | Ermöglicht es Ihnen, die Reihenfolge festzulegen, in der Notizen angezeigt werden. Mit der Einstellung Bestellungen auflisten können Sie Folgendes festlegen: <ul><li>Attribute: der logische Name der Spalte, nach der sortiert werden soll.</li><li>Alias: der Alias für das Attribut in der Abfrage.</li><li>Orientierung Aufsteigend (aufsteigend zum größten oder ersten bis letzten) oder absteigend (von der größten zur kleinsten bzw. letzten bis zum ersten).</li></ul> ![Attribute für Listen Bestellungen festlegen](media/set-attributes-list-orders.png "Set-Attribute für Listen Bestellungen ") Wählen Sie zum Hinzufügen einer Sortier Regel "Spalte" (4) aus, und geben Sie die Details ein. Listen Bestellungen werden von oben nach oben in der Liste mit der höchsten Priorität verarbeitet.|
||


## <a name="create-dialog-options"></a>Dialog Feld Optionen erstellen

| Name                               | Beschreibung                                                                                                                                 |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**                 |                                                                                                                                             |
| Datenschutzoptionen anzeigen (Feld)      | Aktiviert ein Kontrollkästchen im Dialogfeld Hinweis hinzufügen, das es dem Benutzer ermöglicht, einen Hinweis als privat zu markieren.                                                   |
| Standardwert für das Datenschutz Optionsfeld | Gibt den Standardwert für das Kontrollkästchen Datenschutzoptionen anzeigen an. Der Standardwert dieses Felds ist false.                     |
| Anfüge Datei anzeigen                | Aktiviert ein Feld zum Hochladen von Dateien im Dialogfeld Hinweis hinzufügen, sodass ein Benutzer eine Datei an eine Notiz anfügen kann.                                             |
| Datei Annahme anfügen                 | Der von der dateiuploadeingabe akzeptierte MIME-Typ.                                                                                            |
| **Erweiterte Einstellungen**              |                                                                                                                                             |
| Feld Bezeichnung "Hinweis"                   | Überschreibt die Bezeichnung für das Feld "Hinweis" im Dialogfeld "Hinweis hinzufügen".                                                                              |
| Feld Spalten des Hinweises                 | Legt den cols-Wert im Hinweis &lt;Textarea fest&gt;                                                                                            |
| Hinweisfeld Zeilen                    | Legt den Zeilen Wert im Hinweis &lt;Textarea fest&gt;                                                                                            |
| Feld Bezeichnung für Datenschutz Option         | Überschreibt die Bezeichnung für das Optionsfeld "Datenschutz" (sofern aktiviert).                                                                              |
| Datei Bezeichnung anfügen                  | Überschreibt die Bezeichnung für das Feld "Datei anfügen" (sofern aktiviert).                                                                                  |
| CSS-Klasse der linken Spalte              | Fügt die CSS-Klasse bzw. die CSS-Klassen der äußersten linken Spalte mit Bezeichnungen im Dialogfeld Hinweis hinzufügen hinzu.                                                  |
| CSS-Klasse für die Rechte Spalte             | Fügt der Spalte ganz rechts die CSS-Klasse oder-Klassen hinzu, die Feld Eingaben im Dialogfeld Hinweis hinzufügen enthält.                                           |
| Title                              | Überschreibt den HTML-Text in der Kopfzeile des Dialog Felds Hinweis hinzufügen.                                                                               |
| Primärer Schaltflächen Text                | Überschreibt den HTML-Code, der in der primären Schaltfläche (Hinweis hinzufügen) im Dialogfeld angezeigt wird.                                                           |
| SR-Text der Schaltfläche verwerfen             | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                               |
| Schaltflächen Text schließen                  | Überschreibt den HTML-Code, der in der Schaltfläche Schließen (Abbrechen) im Dialogfeld angezeigt wird.                                                               |
| Größe                               | Gibt die Größe des Dialog Felds "Hinweis hinzufügen" an. Die Optionen lauten "Standard", "groß" und "klein". Im Dialogfeld Hinweis hinzufügen ist die Standardgröße default. |
| CSS-Klasse                          | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                |
| Title-CSS-Klasse                    | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                                    |
| CSS-Klasse der primären Schaltfläche           | Geben Sie eine CSS-Klasse oder Klassen an, die auf die primäre Schaltfläche des Dialog Felds (Hinweis hinzufügen) angewendet werden.                                            |
| CSS-Klasse der Schaltfläche Schließen             | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Schaltfläche Schließen (Abbrechen) des Dialog Felds angewendet werden.                                                |
|||

## <a name="edit-dialog-options"></a>Dialog Feld Optionen bearbeiten

| Name                               | Beschreibung                                                                                                                                   |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**                 |                                                                                                                                               |
| Datenschutzoptionen anzeigen (Feld)      | Aktiviert ein Kontrollkästchen im Dialogfeld Notiz bearbeiten, in dem der Benutzer einen Hinweis als privat markieren kann.  |
| Standardwert für das Datenschutz Optionsfeld | Gibt den Standardwert für das Kontrollkästchen Datenschutzoptionen anzeigen an. Der Standardwert dieses Felds ist false.   |
| Anfüge Datei anzeigen                | Aktiviert ein Feld zum Hochladen von Dateien im Dialogfeld "Anmerkung bearbeiten", sodass ein Benutzer eine Datei an eine Notiz anfügen kann.                      |
| Datei Annahme anfügen                 | Der von der dateiuploadeingabe akzeptierte MIME-Typ. |
| **Erweiterte Einstellungen**              |                                                                                              |
| Feld Bezeichnung "Hinweis"                   | Überschreibt die Bezeichnung für das Feld Hinweis im Dialogfeld Hinweis bearbeiten.|
| Feld Spalten des Hinweises                 | Legt den cols-Wert im Hinweis &lt;Textarea fest&gt;                                                                                             |
| Hinweisfeld Zeilen                    | Legt den Zeilen Wert im Hinweis &lt;Textarea fest&gt;                                                                                             |
| Feld Bezeichnung für Datenschutz Option         | Überschreibt die Bezeichnung für das Optionsfeld "Datenschutz" (sofern aktiviert).                                                                                
| Datei Bezeichnung anfügen                  | Überschreibt die Bezeichnung für das Feld "Datei anfügen" (sofern aktiviert).                                                                                   |
| CSS-Klasse der linken Spalte              | Fügt die CSS-Klasse bzw. die CSS-Klassen der Spalte ganz links im Dialogfeld Hinweis Bearbeiten hinzu.                                                  |
| CSS-Klasse für die Rechte Spalte             | Fügt der Spalte ganz rechts die CSS-Klasse oder-Klassen hinzu, die Feld Eingaben im Dialogfeld Hinweis Bearbeiten enthält.                                           |
| Title                              | Überschreibt den HTML-Text in der Kopfzeile des Dialog Felds Edit Note.                                                                               |
| Primärer Schaltflächen Text                | Überschreibt den HTML-Code, der in der primären Schaltfläche (Update Hinweis) im Dialogfeld angezeigt wird.                                                         |
| SR-Text der Schaltfläche verwerfen             | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                                |
| Schaltflächen Text schließen                  | Überschreibt den HTML-Code, der in der Schaltfläche Schließen (Abbrechen) im Dialogfeld angezeigt wird.                                                                |
| Größe                               | Gibt die Größe des Dialog Felds für den Bearbeitungs Hinweis an. Die Optionen lauten "Standard", "groß" und "klein". Im Dialogfeld Hinweis bearbeiten ist die Standardgröße default.|
| CSS-Klasse                          | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                 |
| Title-CSS-Klasse                    | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                                     |
| CSS-Klasse der primären Schaltfläche           | Geben Sie eine CSS-Klasse oder Klassen an, die auf die primäre Schaltfläche des Dialog Felds (Update Hinweis) angewendet werden.                                          |
| CSS-Klasse der Schaltfläche Schließen             | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Schaltfläche Schließen (Abbrechen) des Dialog Felds angewendet werden.                                                 |
|||

## <a name="delete-dialog-options"></a>Dialog Feld Optionen löschen

| Name                     | Beschreibung                                                                                                                                       |
|--------------------------|------------------------------|
| **Grundlegende Einstellungen**       |                                                                                                                                                   |
| Bestätigt             | Überschreiben Sie die Bestätigungsmeldung, um den Hinweis zu löschen.                                                                                             |
| **Erweiterte Einstellungen**    |                                                                                                                                                   |
| Title                    | Überschreibt den HTML-Text in der Kopfzeile des Dialog Felds DELETE Note.                                                                                  |
| Primärer Schaltflächen Text      | Überschreibt den HTML-Code, der in der primären Schaltfläche (Löschen) im Dialogfeld angezeigt wird.                                                                   |
| SR-Text der Schaltfläche verwerfen   | Überschreibt den Text für die Bildschirm Anzeige, der der Schaltfläche Verwerfen des Dialog Felds zugeordnet ist.                                                                     |
| Schaltflächen Text schließen        | Überschreibt den HTML-Code, der in der Schaltfläche Schließen (Abbrechen) im Dialogfeld angezeigt wird.                                                                     |
| Größe                     | Gibt die Größe des Dialog Felds für den Lösch Hinweis an. Die Optionen lauten "Standard", "groß" und "klein". Im Dialogfeld DELETE Note ist die Standardgröße default. |
| CSS-Klasse                | Geben Sie eine CSS-Klasse oder Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                      |
| Title-CSS-Klasse          | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Titelleiste des resultierenden Dialog Felds angewendet werden.                                                          |
| CSS-Klasse der primären Schaltfläche | Geben Sie eine CSS-Klasse oder Klassen an, die auf die primäre Schaltfläche (Löschen) des Dialog Felds angewendet werden.                                                    |
| CSS-Klasse der Schaltfläche Schließen   | Geben Sie eine CSS-Klasse oder Klassen an, die auf die Schaltfläche Schließen (Abbrechen) des Dialog Felds angewendet werden.                                                      |
|||

### <a name="assign-entity-permissions"></a>Zuweisen von Entitätsberechtigungen

Sie müssen den Datensätzen wie folgt die entsprechende Entitäts Berechtigung erstellen und zuweisen. andernfalls werden die Schaltflächen **Hinzufügen**, **Bearbeiten**und **Löschen** für den Hinweis ausgeblendet:

- Lese-, Schreib-, Erstellungs-, Anfüge-und Anfügen an Berechtigungen für die Activity-Entität **(activitypointer)** mit dem Bereich als **Global**. Diese Entitäts Berechtigung muss einer webrolle für den Benutzer zugeordnet werden.
- Lesen, schreiben, erstellen, Anfügen und Anfügen an Berechtigungen für die Entität, für die das Notizen-Steuerelement aktiviert ist. Der Bereich sollte auf **Global**festgelegt werden. Diese Entitäts Berechtigung muss einer webrolle für den Benutzer zugeordnet werden.

    ![Entitäts Berechtigungen hinzufügen](media/entity-permission.png "Entitäts Berechtigungen hinzufügen")

    ![Hinzufügen von Webrollen zu einer Entitäts Berechtigung](media/entity-permission-web-roles.png "Hinzufügen von Webrollen zu einer Entitäts Berechtigung")

Wenn Sie ein benutzerdefiniertes Formular erstellt und diesem den Abschnitt Notizen hinzugefügt haben, achten Sie darauf, dass Sie **Notizen** als Standard Registerkarte auswählen, die Sie sichtbar machen möchten.

![Hinweise in einem benutzerdefinierten Formular](media/notes-activities-tab.png "Hinweise in einem benutzerdefinierten Formular")

## <a name="notes-configuration-for-web-forms"></a>Hinweise zur Konfiguration für Web Forms

Webformular Notizen werden auf die gleiche Weise konfiguriert wie die Anmerkungen zu dieser [Entität](#notes-configuration-for-entity-forms). Sie müssen zunächst einen Metadateneintrag für den Webformular Schritt erstellen, der Notizen enthält, und dann die Notizen der Notizen-Konfiguration hinzufügen.