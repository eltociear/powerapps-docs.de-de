---
title: Was sind Codekomponenten? | Microsoft Docs
description: Verwenden Sie das Power Apps Component Framework, um Code-Komponenten zu erstellen, um Benutzern ein verbessertes Erlebnis beim Anzeigen und Arbeiten mit Daten in Formularen, Ansichten und Dashboards zu bieten.
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 135481cd-4583-4e49-8f58-02f32a9b054a
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 6b563136dba6cc2144e66654860c1f760adbea60
ms.sourcegitcommit: 27cb5ad024d43f208ef6acfbea456a05df3edf8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "3082815"
---
# <a name="what-are-code-components"></a>Was sind Codekomponenten?

Codekomponenten sind eine Art Lösungskomponenten, d.h. sie können in eine Lösungsdatei aufgenommen und in verschiedenen Umgebungen installiert werden. Weitere Informationen: [Verpacken und Bereitstellen von Erweiterungen mithilfe von Lösungen](https://docs.microsoft.com/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions).

> [!div class="mx-imgBorder"] 
> ![Codekomponenten](media/code-components.gif "Code-Komponenten")

Sie fügen Codekomponenten hinzu, indem Sie sie in eine Lösung aufnehmen und dann in Common Data Service importieren. Sobald die Komponenten in Common Data Service sind, können Systemadministratoren und Systemanpasser Formularfelder, Unterraster, Ansichten und Dashboard-Unterraster konfigurieren, um sie anstelle von Standardkomponenten zu verwenden. Sie können diese Codekomponenten sowohl zu **modellgesteuerten als auch zu Canvas-Apps** hinzufügen. 

Codekomponenten bestehen aus drei Elemente:

- [Manifest](#manifest)
- [Komponentenimplementierung](#component-implementation)
- [Ressourcen](#resources)

> [!NOTE]
> Die Definition und Implementierung von Codekomponenten unter Verwendung des Power Apps component framework ist für modellgetriebene und Canvas-Anwendungen gleich. Der einzige Unterschied zwischen beiden ist der Konfigurationsteil. 

## <a name="manifest"></a>Manifest

Manifest ist die Metadatendatei, in der eine Komponente definiert wird. Es ist ein XML-Dokument, das Folgendes beschreibt:

- Der Name der Komponente.
- Die Art der Daten, die konfiguriert werden können, entweder ein Feld oder ein Datensatz.
- Alle Eigenschaften, die in der Anwendung konfiguriert werden können, wenn die Komponente hinzugefügt wird.
- Eine Liste der Ressourcenfelder, die die Komponente benötigt. 
- Der Name der TypeScript-Funktion in der Komponentenimplementierungsbibliothek, die ein Objekt zurückgibt, das das erforderliche Komponenten-Interface anwendet.

Wenn ein Benutzer eine Codekomponente konfiguriert, filtern die Daten in der Manifestdatei die verfügbaren Komponenten heraus, so dass nur gültige Komponenten für den Kontext für die Konfiguration verfügbar sind. Die in der Manifestdatei für eine Komponente definierten Eigenschaften werden als Konfigurationsfelder dargestellt, so dass der Benutzer, der die Komponente konfiguriert, die Werte angeben kann. Diese Eigenschaftswerte stehen der Komponente dann zur Laufzeit zur Verfügung. Weitere Informationen: [Manifestschemaverweis](manifest-schema-reference/index.md)

## <a name="component-implementation"></a>Komponentenimplementierung

Die Komponente zu implementieren ist eine der wichtigen Schritte, wenn Sie benutzerdefinierte Codekomponenten mithilfe des Power Apps component framework entwickeln. Entwickler können eine Komponente mithilfe von TypeScript implementieren. Jede Codekomponente muss über eine `index.ts`-Datei verfügen, die die Definition einer Funktion umfasst, die ein Objekt zurückgibt, das die Methoden implementiert, die in der Codekomponentenschnittstelle beschrieben werden. Diese Datei wird über das CLI-Tooling mit den Hauptstubmethoden automatisch generiert.

Das Objekt implementiert die folgenden Methoden:

- [init](reference/control/init.md) (erforderlich)
- [updateView](reference/control/updateview.md) (erforderlich)
- [getOutputs](reference/control/getoutputs.md) (optional)
- [destroy](reference/control/destroy.md) (erforderlich)

Diese Methode steuert den Lebenszyklus der Codekomponente.

### <a name="page-load"></a>Laden der Seite

Wenn die Seite geladen wird, benötigt die Anwendung ein Objekt, um zu funktionieren. Unter Verwendung der Daten aus der Manifestdatei erhält der Code das Objekt durch Aufruf:

```js
var obj =  new <"namespace on manifest">.<"constructor on manifest">();
```

Wenn die Werte für Namensraum und Konstruktor aus dem Manifest `SampleNameSpace` bzw. `LinearInputComponent` sind, wäre der Code zur Instanziierung des Objekts dieser:

```js
var controlObj = new SampleNameSpace.LinearInputComponent();
```

Wenn die Seite fertig ist, wird die Komponente initialisiert, indem die Methode [init](reference/control/init.md) mit einem Satz von Parametern aufgerufen wird.

```js
controlObj.init(context,notifyOutputChanged,state,container);
```

|Parameter|Beschreibung|
|---|---|
|Kontext| Enthält alle Informationen darüber, wie die Komponente konfiguriert ist und alle Parameter, die innerhalb der Komponente verwendet werden können, zusammen mit den [Power Apps component framework APIs](reference/index.md). Zum Beispiel kann `context.parameters.<"property name from manifest">` verwendet werden, um auf die Eingabeeigenschaft zuzugreifen.|
|notifyOutputChanged |Warnt das Framework, wenn die Codekomponente neue Ausgaben hat, die asynchron abgerufen werden können.|
|state|Enthält Komponentendaten aus dem vorherigen Seitenladen in der aktuellen Sitzung, wenn die Komponente diese explizit früher mit der Methode [setControlState](reference/mode/setcontrolstate.md) gespeichert hat.|
|Container|Ein HTML-Div-Element, an das Entwickler und App-Ersteller die HTML-Elemente für die UI anhängen können, die die Komponente definiert.|

### <a name="user-changes-data"></a>Benutzer ändert Daten

Wenn die Seite geladen wird, zeigt die Komponente die Daten an, bis der Benutzer mit der Komponente interagiert, um die Daten zu ändern. Wenn das geschieht, müssen Sie die aufgenomme Methode in *notifyOutputChanged* als Parameter in der [init](reference/control/init.md)-Methode benennen. Wenn Sie diese Methode verwenden, reagiert die Plattform dann mit dem Aufruf der Methode [getOutputs](reference/control/getoutputs.md). Die [getOutputs](reference/control/getoutputs.md)-Methode gibt Werte zurück, die die Änderungen, die vom Benutzer vorgenommen wurden, enthalten. Für eine Feldkomponente ist das in der Regel ein neuer Wert für die Komponente.

### <a name="app-changes-data"></a>App ändert Daten

Wenn die Plattform die Daten ändert, ruft sie die Methode [updateView](reference/control/updateview.md) der Komponente auf und übergibt das neue Kontextobjekt als Parameter. Diese Methode sollte implementiert werden, um die in der Komponente angezeigten Werte zu aktualisieren.

### <a name="page-close"></a>Seite wird geschlossen

Wenn ein Benutzer von der Seite fort navigiert, verliert die Codekomponente den Umfang und der gesamte Speicher auf der Seite für die Objekte wird gelöscht. Einige Methoden, die auf dem Browser-Implementierungsmechanismus basieren, können jedoch bestehen bleiben und Speicher verbrauchen. In der Regel sind dies Ereignishandler. Wenn der Benutzer diese Informationen speichern möchte, sollte er die Methode [setControlState](reference/mode/setcontrolstate.md) implementieren, so dass die Informationen beim nächsten Mal innerhalb derselben Sitzung ausgegeben werden.

Entwickler können die [Vernichten](reference/control/destroy.md)-Methode implementieren, die aufgerufen wird, wenn die Seite schließt, um einen beliebigen Bereinigungscode wie Ereignishandler zu entfernen.

## <a name="resources"></a>Ressourcen

Jede Codekomponente sollte eine Ressourcendatei haben, um ihre Visualisierung zu erstellen. Sie können eine Ressourcendatei im Manifest definieren. Der Ressourcenknoten in der Manifestdatei bezieht sich auf die Ressourcen, die die Komponente benötigt, um ihre Visualisierung zu implementieren. Weitere Informationen: [Ressourcenelement](manifest-schema-reference/resources.md)

### <a name="related-topics"></a>Verwandte Themen

[Erstellen und Entwickeln einer Code-Komponente](create-custom-controls-using-pcf.md)
