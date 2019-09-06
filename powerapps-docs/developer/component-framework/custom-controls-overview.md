---
title: Was sind benutzerdefinierte Komponenten? | Microsoft Docs
description: 'Verwenden Sie das PowerApps-Komponentenframework, um benutzerdefinierte Komponenten zu erstellen, um erweiterte Benutzererfahrung für Benutzer bereitzustellen, um Daten in Formularen, Ansichten und Dashboards anzuzeigen und zu bearbeiten.'
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 135481cd-4583-4e49-8f58-02f32a9b054a
ms.author: nabuthuk
author: Nkrb
---

# <a name="what-are-custom-components"></a>Was sind benutzerdefinierte Komponenten?

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Benutzerdefinierte Komponenten gehören zum Typ Lösungskomponente. Das bedeutet, dass sie in einer Lösung enthalten sein und in verschiedenen Umgebungen installiert werden können. Weitere Informationen: [Verpacken und Bereitstellen von Erweiterungen mithilfe von Lösungen](https://docs.microsoft.com/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions).

Sie fügen benutzerdefinierte Komponenten hinzu, indem Sie sie in einer Lösung einfügen und dann in das System importieren. Sobald sie im System sind, können Administrator- und Systemanpasser Formularfelder, Unterraster, Ansichten und Dashboard-Unterraster konfigurieren, um sie anstelle von Standardkomponenten zu verwenden.

Benutzerdefinierte Komponenten bestehen aus drei Bestandteilen:

1. Manifest
2. Komponentenimplementierungsbibliothek
3. Ressourcen

## <a name="manifest"></a>Manifest

Manifest ist die Metadatendatei, in der eine Komponente definiert wird. Es ist ein XML-Dokument, das Folgendes beschreibt:

- Den Namespace und den Namen der Komponente.
- Die Art der Daten, die konfiguriert werden können, entweder ein Feld oder ein Datensatz.
- Alle Eigenschaften, die in der Anwendung konfiguriert werden können, wenn die Komponente hinzugefügt wird.
- Eine Liste der Ressourcenfelder, die die Komponente benötigt. 
- Der Name einer TypeScript-Funktion in der Komponentenimplementierungsbibliothek, die ein Objekt zurückgibt, das die benötigte Komponentenschnittstelle anwendet.

Wenn jemand eine Komponente in der Anwendung konfiguriert, filtern die Daten in dem Manifest verfügbare Komponenten heraus, damit nur gültige Komponenten für den Kontext für die Konfiguration verfügbar sind. Die im Manifest definierten Eigenschaften für eine Komponente werden als Konfigurationsfelder gerendert, sodass die Person, die die Komponente konfiguriert, Werte angeben kann. Diese Eigenschaftswerte sind dann zur Laufzeit in Ihrer Komponentenfunktion verfügbar. Weitere Informationen: [Manifestdateiverweis](manifest-schema-reference/index.md)

## <a name="component-implementation-library"></a>Komponentenimplementierungsbibliothek

[!INCLUDE [component-implementation-library](control-implementation-library.md)]

### <a name="page-load"></a>Laden der Seite

Wenn die Seite geladen wird, erfordert die Anwendung ein Objekt, mit dem gearbeitet werden kann. Mithilfe von Daten aus dem Manifest, erhält der Code das Objekt durch Aufruf

```js
var obj =  new ["namespace on manifest"].["constructor on manifest"]();
```

Wenn die Namespace- und Konstruktorwerte aus dem Manifest je `MyNameSpace` und `LinearInputControl` lauten, sieht der Code zum Instanziieren des Objekts so aus:

```js
var controlObj = new MyNameSpace.LinearInputControl();
```

Wenn die Seite bereit ist, wird die Komponente durch Aufruf der [init](reference/control/init.md)-Funktion mit einem Satz von Parametern instanziiert.

```js
controlObj.init(context,notifyOutputChanged,state,container);
```

|Parameter|Beschreibung|
|---|---|
|Kontext| Enthält alle Informationen darüber, wie die Komponente konfiguriert ist und über alle Parameter, die in der Komponente zusammen mit den [Framework-APIs](reference/index.md) verwendet werden können. Zum Beispiel kann `context.parameters.["property name from manifest"]` verwendet werden, um auf die Eingabeeigenschaft zuzugreifen.|
|notifyOutputChanged |Funktion, die das Framework warnt, dass die Komponente über neue Ausgaben verfügt, die asynchron abgerufen werden können.|
|state|Enthält Komponentendaten vom Laden der vorherigen Seite in der aktuellen Sitzung, wenn die Komponente sie zuvor explizit mit `setControlState API` gespeichert hat.|
|Container|Ein HTML-div-Element, an das Sie die HTML-Elemente für die Benutzeroberfläche anhängen, die Ihre Umgebung definiert. Um die Werte in der Benutzeroberfläche anzuzeigen, müssen Sie die Daten aus `context.parameters.controlValue object` abrufen.|

### <a name="user-changes-data"></a>Benutzer ändert Daten

Nachdem die Seite geladen wurde, zeigt Ihre Komponente die Daten an, bis der Benutzer mit der Komponente interagiert, um die Daten zu ändern. Wenn dies auftritt, können Sie das auf eine gewünschte Art verwalten, aber Sie müssen die Funktion aufrufen, die als **notifyOutputChanged**-Parameter in die [init](reference/control/init.md)-Funktion übergeben wurde. Wenn Sie diese Funktion verwenden, reagiert die Plattform mit dem Aufruf der [getOutputs](reference/control/getoutputs.md)-Methode, die Sie implementieren müssen. Die [getOutputs](reference/control/getoutputs.md)-Methode gibt alle Werte zurück, die vom Benutzer vorgenommene Änderungen darstellen. Für eine Feldkomponente ist das in der Regel ein neuer Wert für die Komponente.

### <a name="app-changes-data"></a>App ändert Daten

Wenn die Daten von der Plattform geändert werden, ruft diese die [updateView](reference/control/updateview.md)-Methode Ihres Komponentenobjekts auf und übergibt sie als neues Kontextobjekt. Sie müssen diese Methode implementieren und dazu verwenden, den in der Komponente angezeigten Wert zu aktualisieren.

### <a name="page-close"></a>Seite wird geschlossen

Wenn der Benutzer von der Seite fort navigiert, verliert die Komponente den Umfang und in der Regel wird der auf der Seite für die Objekte in Ihrer Komponente zugewiesene Speicher gelöscht. Allerdings bleiben je nach dem Mechanismus der Browserimplementierung einige Elemente vorhanden und verbrauchen Speicher. In der Regel sind dies Ereignishandler. Wenn der Benutzer Informationen speichern möchte, sollte er die `setControlState`-Methode implementieren, damit die Informationen das nächste Mal in derselben Sitzung bereitgestellt werden.
Sie sollten eine [destroy](reference/control/destroy.md)-Methode in Ihrem Objekt definieren. Diese wird aufgerufen, wenn die Seite geschlossen wird, und Sie sollten sie verwenden, um jeglichen Bereinigungscode zu entfernen, z. B. alle Ereignishändler entfernen.

## <a name="resources"></a>Ressourcen

Jede benutzerdefinierte Komponente sollte über ein Ressourcendatei verfügen, um seine Visualisierung zu konstruieren. Sie können eine Ressourcendatei im Manifest definieren. Der Ressourcenknoten in der Manifestdatei verweist auf die Ressourcen, die die Komponente benötigt, um ihre Visualisierung zu implementieren. Weitere Informationen: [Resourcen](manifest-schema-reference/resources.md)

### <a name="related-topics"></a>Verwandte Themen

[Benutzerdefinierte Komponenten erstellen](create-custom-controls-using-pcf.md)
