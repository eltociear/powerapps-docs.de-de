---
title: Was sind Code Komponenten? | MicrosoftDocs
description: Verwenden Sie das powerapps-Komponenten Framework zum Erstellen von Code Komponenten, um Benutzern eine verbesserte Benutzererfahrung zum Anzeigen und Bearbeiten von Daten in Formularen, Ansichten und Dashboards zu bieten.
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 135481cd-4583-4e49-8f58-02f32a9b054a
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 08a2043dfb92634837c367e664306d9c100632d6
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346967"
---
# <a name="what-are-code-components"></a>Was sind Code Komponenten?

Code Komponenten sind ein Typ von Lösungskomponenten, d. h., Sie können in eine Projektmappendatei aufgenommen und in verschiedenen Umgebungen installiert werden. Weitere Informationen finden [Sie unter Verpacken und Verteilen von Erweiterungen mithilfe von Lösungen](https://docs.microsoft.com/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions).

Sie fügen Code Komponenten hinzu, indem Sie Sie in eine Projekt Mappe einschließen und anschließend in Common Data Service importieren. Wenn sich die Komponenten in Common Data Service befinden, können Systemadministratoren und Systemanpassungen Felder, unter Raster, Ansichten und dashboardsubraster so konfigurieren, dass Sie anstelle von Standardkomponenten verwendet werden. Sie können diese Code Komponenten auch in Canvas-apps hinzufügen. 

Code Komponenten bestehen aus drei Elementen:

1. [Kundiger](#manifest)
2. [Komponenten Implementierungs Bibliothek](#component-implementation-library)
3. [Resources](#resources)

## <a name="manifest"></a>Kundiger

Ein Manifest ist die Metadatendatei, die eine Komponente definiert. Es ist ein XML-Dokument, das Folgendes beschreibt:

- Der Name der Komponente.
- Die Art der Daten, die konfiguriert werden können, entweder ein Feld oder ein Datenset.
- Alle Eigenschaften, die in der Anwendung konfiguriert werden können, wenn die Komponente hinzugefügt wird.
- Eine Liste von Ressourcen Dateien, die von der Komponente benötigt werden. 
- Der Name der typescript-Funktion in der Komponenten Implementierungs Bibliothek, die ein Objekt zurückgibt, das die erforderliche Komponentenschnittstelle anwendet.

Wenn ein Benutzer eine Code Komponente konfiguriert, werden die verfügbaren Komponenten von den Daten in der Manifest-Datei herausgefiltert, sodass nur gültige Komponenten für den Kontext für die Konfiguration verfügbar sind. Die in der Manifest-Datei für eine Komponente definierten Eigenschaften werden als Konfigurations Felder gerendert, sodass der Benutzer, der die Komponente konfiguriert, die Werte angeben kann. Diese Eigenschaftswerte sind dann zur Laufzeit für die Komponente verfügbar. Weitere Informationen: [Manifest-Schema Referenz](manifest-schema-reference/index.md)

## <a name="component-implementation-library"></a>Komponenten Implementierungs Bibliothek

Das Implementieren der Komponentenbibliothek ist einer der wichtigsten Schritte beim Entwickeln von Code Komponenten mithilfe des powerapps-Komponenten-Frameworks. Entwickler können mithilfe von typescript eine Komponentenbibliothek implementieren. Jede Code Komponente muss über eine Bibliothek verfügen, die die Definition einer Funktion enthält, die ein Objekt zurückgibt, das die in der Code Component-Schnittstelle beschriebenen Methoden implementiert. 

Das-Objekt implementiert die folgenden Methoden:

- [Init](reference/control/init.md) (erforderlich)
- [UpdateView](reference/control/updateview.md) (erforderlich)
- [getoutputs](reference/control/getoutputs.md) (optional)
- [zerstören](reference/control/destroy.md) (erforderlich)

Diese Methoden steuern den Lebenszyklus der Code Komponente.

### <a name="page-load"></a>Seiten Ladevorgang

Wenn die Seite geladen wird, benötigt die Anwendung ein Objekt, damit Sie funktioniert. Wenn Sie die Daten aus der Manifestressource verwenden, ruft der Code das Objekt durch Aufrufen von ab:

```js
var obj =  new <"namespace on manifest">.<"constructor on manifest">();
```

Wenn die Namespace-und konstruktorwerte aus dem Manifest `SampleNameSpace` und `LinearInputComponent` werden, ist der Code zum Instanziieren des Objekts Folgendes:

```js
var controlObj = new SampleNameSpace.LinearInputComponent();
```

Wenn die Seite bereit ist, wird die Komponente initialisiert, indem die [Init](reference/control/init.md) -Methode mit einem Satz von Parametern aufgerufen wird.

```js
controlObj.init(context,notifyOutputChanged,state,container);
```

|Parameter|Beschreibung|
|---|---|
|Kontext| Enthält alle Informationen über die Konfiguration der Komponente und alle Parameter, die in der Komponente zusammen mit den [powerapps-Komponenten Framework-APIs](reference/index.md)verwendet werden können. Beispielsweise kann der `context.parameters.<"property name from manifest">` verwendet werden, um auf die Input-Eigenschaft zuzugreifen.|
|notitputchanged |Benachrichtigt das Framework, wenn für die Code Komponente neue Ausgaben bereit stehen, die asynchron abgerufen werden können.|
|Land|Enthält Komponenten Daten aus dem vorherigen Seiten Ladevorgang in der aktuellen Sitzung, wenn die Komponente Sie mithilfe der [setcontrolstate](reference/mode/setcontrolstate.md) -Methode explizit zuvor gespeichert hat.|
|Kum|Ein HTML-div-Element, dem Entwickler und App-Ersteller die HTML-Elemente für die Benutzeroberfläche anfügen können, die die Komponente definiert.|

### <a name="user-changes-data"></a>Benutzer Änderungs Daten

Wenn die Seite geladen wird, werden die Daten von der Komponente angezeigt, bis der Benutzer mit der Komponente interagiert, um die Daten zu ändern. Wenn dies auftritt, müssen Sie die Methode aufrufen, die als *notifyoutputchanged* -Parameter in der [Init](reference/control/init.md) -Methode übergeben wird. Wenn Sie diese Methode verwenden, antwortet die Plattform, indem Sie die [getoutputs](reference/control/getoutputs.md) -Methode aufrufen. Die [getoutputs](reference/control/getoutputs.md) -Methode gibt Werte zurück, die die vom Benutzer vorgenommenen Änderungen enthalten. Bei einer Feld Komponente wäre dies normalerweise der neue Wert für die Komponente.

### <a name="app-changes-data"></a>App-Änderungs Daten

Wenn die Plattform die Daten ändert, ruft Sie die [UpdateView](reference/control/updateview.md) -Methode der Komponente auf und übergibt das neue Kontext Objekt als Parameter. Diese Methode sollte implementiert werden, um die in der Komponente angezeigten Werte zu aktualisieren.

### <a name="page-close"></a>Seite schließen

Wenn ein Benutzer von der Seite Weg geht, verliert die Code Komponente den Bereich, und der gesamte Arbeitsspeicher, der auf dieser Seite für die Objekte zugeordnet ist, wird gelöscht. Einige Methoden, die auf dem Implementierungsmechanismus des Browsers basieren, werden jedoch möglicherweise beibehalten und belegen Arbeitsspeicher. In der Regel handelt es sich hierbei um Ereignishandler. Wenn der Benutzer diese Informationen speichern möchte, sollte er die [setcontrolstate](reference/mode/setcontrolstate.md) -Methode implementieren, damit die Informationen das nächste Mal innerhalb derselben Sitzung angegeben werden.

Entwickler sollten die [Destroy](reference/control/destroy.md) -Methode implementieren, die aufgerufen wird, wenn die Seite geschlossen wird, um jeglichen Bereinigungs Code (z. b. Ereignishandler) zu entfernen.

## <a name="resources"></a>Ressourcen

Jede Code Komponente sollte über eine Ressourcen Datei verfügen, um die Visualisierung zu erstellen. Sie können eine Ressourcen Datei im Manifest definieren. Der Ressourcenknoten in der Manifest-Datei bezieht sich auf die Ressourcen, die die Komponente zum Implementieren der Visualisierung benötigt. Weitere Informationen: [Resources-Element](manifest-schema-reference/resources.md)

### <a name="related-topics"></a>Verwandte Themen

[Erstellen und Erstellen einer Code Komponente](create-custom-controls-using-pcf.md)
