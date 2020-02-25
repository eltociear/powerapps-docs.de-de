---
title: Konfigurieren von Notizen in Entitätsformularen und Webformularen für ein Portal | MicrosoftDocs
description: Anweisungen, Notizen zu Entitätsformularen und Webformularen in einem Portal hinzuzufügen und zu konfigurieren.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: d1e8048f4cc4dbb2023788fcc3d3cf28fdfb7f7b
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979687"
---
# <a name="configure-notes-for-entity-forms-and-web-forms-on-portals"></a>Konfigurieren von Hinweisen für Entitätsformulare und Internetformulare in Portalen

Notizen zu verwalteten Formularen im Portal hinzuzufügen ist genauso einfach wie bei Unterrastern&mdash;, fügen Sie einfach das Notiz-Steuerelement den Formularen modellgesteuerter Apps über den [Formulardesigner hinzu](../model-driven-apps/create-design-forms.md); fertig. Sie können das Verhalten von Notizensteuerelementen über Metadaten konfigurieren.

> [!Note]                                                           
> Explizite [Entitätsberechtigungen](configure/assign-entity-permissions.md) sind Erforderlich, damit alle Notizen im Verwaltungsportal von angezeigt werden. Zum Lesen und Bearbeiten müssen die Rechte „Lesen“ und „Schreiben“ erteilt werden. Zum Erstellen müssen zwei Berechtigungen vorhanden sein: „Erstellen“ und „Anhängen" müssen für die Notizentität (Anmerkung) gewährt werden, und eine zweite Berechtigung muss dem Entitätstyp zugewiesen werden, an den die Notiz mit dem Recht „Anhängen“ angefügt ist. Das Kontrollkästchen **Entitätsberechtigungen aktivieren** muss auf dem entsprechenden Entitätsformular- oder Webformularschritt aktiviert sein, damit die Entitätsberechtigungen wirksam werden.

## <a name="notes-configuration-for-entity-forms"></a>Konfiguration von Notizen für Entitätsformulare

1. Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2. Gehen Sie auf **Portale** > **Inhalt** > **Entitätsformulare**. Eine Liste aktiver Entitätsformularen wird angezeigt.
3. Wählen Sie das Entitätsformular aus, dem Sie eine Hinweiskonfiguration hinzufügen möchten.
4. Navigieren Sie entweder mithilfe des oberen Dropdowns-Menüs oder des Unterrasters rechts im Hauptformular des Entitätsformulardatensatzes, an dem Sie arbeiten zu **Entitätsformular-Metadaten**.
5. Klicken Sie auf **Neue Entitätsformular-Metadaten hinzufügen**, um einen neuen Datensatz hinzuzufügen.
6. Wählen Sie aus der Dropdownliste **Typ** **Hinweise** aus. Die für die Hinweiskonfiguration&ndash;spezifischen Einstellungen werden angezeigt. Die meisten Einstellungen sind standardmäßig verkleinert. Sie können einen Bereich erweitern, um zusätzliche Einstellungen anzuzeigen.
7. Füllen Sie die Felder aus, indem Sie entsprechende Werte eingeben. [!include[](../../includes/proc-more-information.md)] [Attribute](#attributes), [Dialogoptionen erstellen](#create-dialog-options), [Dialogoptionen bearbeiten](#edit-dialog-options), und [Dialogoptionen löschen](#delete-dialog-options)
8. Speichern Sie das Formular.

    ![Konfiguration von Notizen zu Entitätsformularen hinzufügen](media/add-note-configuration.png "Konfiguration von Notizen zu Entitätsformularen hinzufügen")  

    Nach dem Hinzufügen der Konfiguration wird das Notizensteuerelement mit den entsprechenden Optionen im Portal dargestellt.

## <a name="attributes"></a>Attribute


| Name                  | Beschreibung                                                                                                                                                  |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**    |                                                                                                                                                              |
| \"Erstellen\" aktiviert        | Aktiviert die Möglichkeit neue Notizen zu einer Entität hinzuzufügen.                                                                                                          |
| Optionen des Dialogs \"Erstellen\" | Enthält Einstellungen zur Konfiguration des Dialogs, wenn **Erstellen aktiviert** aktiviert ist. Weitere Informationen finden Sie unter "Optionen des Dialogs 'Erstellen'".                                    |
| \"Bearbeiten\" aktiviert          | Aktiviert die Möglichkeit bestehende Notizen einer Entität zu bearbeiten.                                                                                                    |
| Optionen des Dialogs \"Bearbeiten\"   | Enthält Einstellungen zur Konfiguration des Dialogs, wenn **EditEnabled** aktiviert ist. Weitere Informationen finden Sie unter "Optionen des Dialogs 'Bearbeiten'".                                         |
| \"Löschen\" aktiviert        | Aktiviert die Möglichkeit Notizen aus einer Entität zu löschen.                                                                                                         |
| Optionen für Dialog \"Löschen\" | Enthält Einstellungen zur Konfiguration des Dialogs, wenn **DeleteEnabled** aktiviert ist. Weitere Informationen finden Sie unter "Optionen des Dialogs 'Löschen'".                                     |
|Speicherort für Dateianlagen | Wählen Sie den Speicherort für die Dateianlage aus.<ul><li>Hinweisanlage</li><li>Azure-Blobspeicher</li></ul>|
|MIME-Typ(en) akzeptieren | Ermöglicht Ihnen, eine Liste der akzeptierten MIME-Typen anzugeben. |
|MIME-Typen einschränken | Wählen Sie aus, ob MIME-Typen zugelassen oder eingeschränkt werden sollen.|
|Maximale Dateigröße (in KB) |Ermöglicht Ihnen, die maximale Größe einer Datei festzulegen, die angefügt werden kann. |
| **Erweiterte Einstellungen** |                                                                                                                                                              |
| Listentitel            | Überschreibt den Titel über dem Notizbereich.                                                                                                                     |
| Schaltflächenbezeichnung \"Notiz hinzufügen\" | Überschreibt die Beschriftung der Schaltfläche „Notizen hinzufügen“.                                                                                                                 |
| Hinweisdatenschutz-Bezeichnung    | Überschreibt die Beschriftung, die anzeigt, das eine Notiz privat ist.                                                                                                         |
| Laden von Meldungen       | Überschreibt die Meldung, die beim Laden einer Liste mit Notizen angezeigt wird.                                                                                              |
| Fehlermeldung         | Überschreibt die Nachricht, die angezeigt wird, wenn ein Fehler auftritt, während die Notizliste lädt.                                                                     |
| Meldung vom Typ "Zugriff verweigert" | Überschreibt die Meldung, die angezeigt wird, wenn ein Benutzer keine ausreichenden Berechtigungen zur Anzeige der Notizenliste besitzt.                                                    |
| Leere Meldung         | Überschreibt die angezeigte Meldung, wenn die aktuelle Entität keine Notizen besitzt, die angezeigt werden können.                                                              |
| Listenreihenfolgen           | Ermöglicht das Festlegen der Reihenfolge, in der Notizen angezeigt werden. Über die Einstellung zu Listenreihenfolgen können Sie Folgendes festlegen: <ul><li>Attribut: der logische Name der Spalte, nach der sortiert wird.</li><li>Alias: der Alias für das Attribut in der Abfrage</li><li>Sortierung: Wählen Sie „Aufsteigend“ (kleinste bis größte, oder erste bis letzte) oder „Absteigend“ (größte bis kleinste oder letzte bis erste) aus.</li></ul>  ![Festlegen von Attributen für Listenreihenfolgen](media/set-attributes-list-orders.png "Legen Sie Attribute für Listenreihenfolgen fest") Klicken Sie zum Hinzufügen einer Sortierregel auf Spalte (4), und füllen Sie die Details aus. Die Listensortierung wird von oben verarbeitet. Das oberste Element hat die höchste Priorität.|
||


## <a name="create-dialog-options"></a>Optionen des Dialogs \"Erstellen\"

| Name                               | Beschreibung                                                                                                                                 |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**                 |                                                                                                                                             |
| Feld \"Datenschutzoptionen\" anzeigen      | Aktiviert ein Kontrollkästchen im Dialogfeld „Notiz hinzufügen“, das dem Benutzer ermöglicht, eine Notiz als privat zu markieren.                                                   |
| Standardwert für Datenschutzoptionsfeld | Legt den Standardwert für das Kontrollkästchen „Feld 'Datenschutzoptionen' anzeigen“ fest. Der Standardwert dieses Felds ist „Falsch“.                     |
| \"Datei anfügen\" anzeigen                | Aktiviert ein Dateiuploadfeld im Dialogfeld „Notiz hinzufügen“, das einem Benutzer ermöglicht, eine Datei an eine Notiz anzuhängen.                                             |
| Datei anfügen: Akzeptieren                 | Der vom Dateiupload akzeptierte MIME-Typ.                                                                                            |
| **Erweiterte Einstellungen**              |                                                                                                                                             |
| Hinweisfeldbezeichnung                   | Überschreibt die Beschriftung für das Feld „Notiz“ im Dialogfeld „Notiz hinzufügen“.                                                                              |
| Hinweisfeldspalten                 | Legt den cols-Wert in der Notiz &lt;textarea&gt; fest                                                                                            |
| Hinweisfeldzeilen                    | Legt den rows-Wert in der Notiz &lt;textarea&gt; fest                                                                                            |
| Bezeichnung für Datenschutzoptionsfeld         | Überschreibt die Beschriftung für das Datenschutzoptionsfeld (wenn aktiviert).                                                                              |
| Datei anfügen: Bezeichnung                  | Überschreibt die Beschriftung für das Feld "Datei anfügen" (wenn aktiviert).                                                                                  |
| CSS-Klasse für linke Spalte              | Fügt die CSS-Klasse oder -Klassen mit Bezeichnungen im Dialogfeld „Notiz hinzufügen“ zur ganz linken Spalte hinzu.                                                  |
| CSS-Klasse für rechte Spalte             | Fügt die CSS-Klasse oder -Klassen mit Feldeingaben im Dialogfeld „Notiz hinzufügen“ zur ganz rechten Spalte hinzu.                                           |
| Titel                              | Überschreibt den HTML-Text in der Kopf des Dialogfelds „Notiz hinzufügen“.                                                                               |
| Text der primären Schaltfläche                | Überschreibt das HTML, das in der primären Schaltfläche (Notiz hinzufügen) des Dialogs angezeigt wird.                                                           |
| Den SR-Text der Schaltfläche verwerfen             | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche „Verwerfen“ des Dialogfelds zugeordnet ist.                                                               |
| Schaltflächentext schließen                  | Überschreibt das HTML, das in der primären Schließen-Schaltfläche (Abbrechen) des Dialogfelds angezeigt wird.                                                               |
| Größe                               | Gibt die Größe des Dialogfelds „Notiz hinzufügen“ an. Die Optionen sind „Standard“, „Groß“ und „Klein“. Die standardmäßige Größe des Dialogfelds „Notiz hinzufügen“ ist „Standard“. |
| CSS Klasse                          | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                |
| CSS-Klasse für Titel                    | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                                    |
| CSS-Klasse für primäre Schaltfläche           | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die primäre Schaltfläche (Notiz hinzufügen) des Dialogfelds angewendet werden.                                            |
| CSS-Klasse für Schaltfläche „Schließen”             | Geben Sie eine CSS-Klasse oder Klassen an, die für die primäre „Schließen”-Schaltfläche (Abbrechen) des Dialogfelds angewendet werden.                                                |
|||

## <a name="edit-dialog-options"></a>Optionen des Dialogs \"Bearbeiten\"

| Name                               | Beschreibung                                                                                                                                   |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| **Grundlegende Einstellungen**                 |                                                                                                                                               |
| Feld \"Datenschutzoptionen\" anzeigen      | Aktiviert ein Kontrollkästchen im Dialogfeld „Notiz bearbeiten“, das dem Benutzer ermöglicht, eine Notiz als privat zu markieren.  |
| Standardwert für Datenschutzoptionsfeld | Legt den Standardwert für das Kontrollkästchen „Feld 'Datenschutzoptionen' anzeigen“ fest. Der Standardwert dieses Felds ist „Falsch“.   |
| \"Datei anfügen\" anzeigen                | Aktiviert ein Dateiuploadfeld im Dialogfeld „Notiz bearbeiten“, das einem Benutzer ermöglicht, eine Datei an eine Notiz anzuhängen.                      |
| Datei anfügen: Akzeptieren                 | Der vom Dateiupload akzeptierte MIME-Typ. |
| **Erweiterte Einstellungen**              |                                                                                              |
| Hinweisfeldbezeichnung                   | Überschreibt die Beschriftung für das Feld „Notiz“ im Dialogfeld „Notiz bearbeiten“.|
| Hinweisfeldspalten                 | Legt den cols-Wert in der Notiz &lt;textarea&gt; fest                                                                                             |
| Hinweisfeldzeilen                    | Legt den rows-Wert in der Notiz &lt;textarea&gt; fest                                                                                             |
| Bezeichnung für Datenschutzoptionsfeld         | Überschreibt die Beschriftung für das Datenschutzoptionsfeld (wenn aktiviert).                                                                                
| Datei anfügen: Bezeichnung                  | Überschreibt die Beschriftung für das Feld "Datei anfügen" (wenn aktiviert).                                                                                   |
| CSS-Klasse für linke Spalte              | Fügt die CSS-Klasse oder -Klassen mit Bezeichnungen im Dialogfeld „Notiz bearbeiten“ zur ganz linken Spalte hinzu.                                                  |
| CSS-Klasse für rechte Spalte             | Fügt die CSS-Klasse oder -Klassen mit Feldeingaben im Dialogfeld „Notiz bearbeiten“ zur ganz rechten Spalte hinzu.                                           |
| Titel                              | Überschreibt den HTML-Text in der Kopf des Dialogfelds „Notiz bearbeiten“.                                                                               |
| Text der primären Schaltfläche                | Überschreibt das HTML, das in der primären Schaltfläche (Notiz aktualisieren) des Dialogs angezeigt wird.                                                         |
| Den SR-Text der Schaltfläche verwerfen             | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche „Verwerfen“ des Dialogfelds zugeordnet ist.                                                                |
| Schaltflächentext schließen                  | Überschreibt das HTML, das in der primären Schließen-Schaltfläche (Abbrechen) des Dialogfelds angezeigt wird.                                                                |
| Größe                               | Gibt die Größe des Dialogfelds „Notiz bearbeiten“ an. Die Optionen sind „Standard“, „Groß“ und „Klein“. Die standardmäßige Größe des Dialogfelds „Notiz bearbeiten“ ist „Standard“.|
| CSS Klasse                          | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                 |
| CSS-Klasse für Titel                    | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogs angewendet werden.                                                     |
| CSS-Klasse für primäre Schaltfläche           | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die primäre Schaltfläche (Notiz aktualisieren) des Dialogfelds angewendet werden.                                          |
| CSS-Klasse für Schaltfläche „Schließen”             | Geben Sie eine CSS-Klasse oder Klassen an, die für die primäre „Schließen”-Schaltfläche (Abbrechen) des Dialogfelds angewendet werden.                                                 |
|||

## <a name="delete-dialog-options"></a>Optionen für Dialog \"Löschen\"

| Name                     | Beschreibung                                                                                                                                       |
|--------------------------|------------------------------|
| **Grundlegende Einstellungen**       |                                                                                                                                                   |
| Bestätigung             | Überschreiben die Bestätigungsmeldung beim Löschen der Notiz.                                                                                             |
| **Erweiterte Einstellungen**    |                                                                                                                                                   |
| Titel                    | Überschreibt den HTML-Text in der Kopf des Dialogfelds „Notiz löschen“.                                                                                  |
| Text der primären Schaltfläche      | Überschreibt das HTML, das in der primären Schaltfläche (Löschen) des Dialogfelds angezeigt wird.                                                                   |
| Den SR-Text der Schaltfläche verwerfen   | Überschreibt den Text für die Sprachausgabe, der der Schaltfläche „Verwerfen“ des Dialogfelds zugeordnet ist.                                                                     |
| Schaltflächentext schließen        | Überschreibt das HTML, das in der primären Schließen-Schaltfläche (Abbrechen) des Dialogfelds angezeigt wird.                                                                     |
| Größe                     | Gibt die Größe des „Notiz löschen“-Dialogs an. Die Optionen sind „Standard“, „Groß“ und „Klein“. Die standardmäßige Größe des "„Notiz löschen“-Dialogs ist „Standard“. |
| CSS Klasse                | Geben Sie eine CSS-Klasse oder -Klassen an, die auf das resultierende Dialogfeld angewendet werden.                                                                      |
| CSS-Klasse für Titel          | Geben Sie eine CSS-Klasse oder -Klassen an, die auf die Titelleiste des resultierenden Dialogfelds angewendet werden.                                                          |
| CSS-Klasse für primäre Schaltfläche | Geben Sie eine CSS-Klasse oder Klassen an, die auf die primäre Schaltfläche (Löschen) des Dialogfelds angewendet werden.                                                    |
| CSS-Klasse für Schaltfläche „Schließen”   | Geben Sie eine CSS-Klasse oder Klassen an, die für die primäre „Schließen”-Schaltfläche (Abbrechen) des Dialogfelds angewendet werden.                                                      |
|||

### <a name="assign-entity-permissions"></a>Entitätsberechtigungen zuweisen

Sie müssen die entsprechenden Entitätsberechtigung erstellen und den Datensätzen zuweisen, wie folgt; andernfalls sind die Schaltflächen für **Hinzufügen**, **Bearbeiten** und **Löschen** ausgeblendet:

- Erstellen, Lesen, Schreiben, Anfügen und Anfügen an Rechte für die Entität **Aktivitätsentität (activitypointer)** mit dem Bereich **Global**. Die Entitätsberechtigung muss einer Webrolle für den Benutzer zugeordnet werden.
- Erstellen, Lesen, Schreiben, Anfügen und Anfügen an Rechte für die Entität in der das Hinweissteuerelement aktiviert ist. Der Umfang sollte auf **Global** festgelegt werden. Die Entitätsberechtigung muss einer Webrolle für den Benutzer zugeordnet werden.

    ![Entitätsberechtigungen hinzufügen](media/entity-permission.png "Entitätsberechtigungen hinzufügen")

    ![Hinzufügen von Webrollen zu einer Entitätsberechtigung](media/entity-permission-web-roles.png "Hinzufügen von Webrollen zu einer Entitätsberechtigung")

Wenn Sie ein benutzerdefiniertes Formular erstellt und den Abschnitt „Notizen“ diesem hinzugefügt haben, stellen Sie sicher, dass **Notizen** als die Standardregisterkarte ausgewählt ist, die angezeigt werden soll.

![Notizen in einem benutzerdefinierten Formular](media/notes-activities-tab.png "Notizen in einem benutzerdefinierten Formular")

## <a name="notes-configuration-for-web-forms"></a>Konfiguration von Notizen für Webformulare

Webformularnotizen werden genau wie [Entitätsformularnotizen](#notes-configuration-for-entity-forms) konfiguriert. Erstellen Sie zunächst einen Metadatendatensatz für den Webformularschritt, der eine Notiz aufweist, und fügen Sie Konfigurationsmetadaten hinzu.
