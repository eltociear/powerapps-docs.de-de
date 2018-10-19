## <a name="delegation"></a>Delegierung
Sofern möglich erfolgt in PowerApps eine Filterdelegation und Vorgangssortierung bei Bedarf anhand der Ergebnisse entsprechend der Datenquelle. Wenn Sie beispielsweise eine App starten, in der ein **[Galerie](../maker/canvas-apps/controls/control-gallery.md)**-Steuerelementfeld mit Daten enthalten ist, wird anfänglich nur die erste Datensatzgruppe zum Gerät übertragen. Beim Scrollen werden weitere Daten aus der Datenquelle übertragen. Das führt bei der App zu einer schnelleren Startzeit und einem schnelleren Zugriff auf umfangreiche Datensets.

Allerdings ist eine Delegierung gegebenenfalls nicht immer möglich. Die von Datenquellen in Bezug auf Delegation unterstützten Funktionen und Operatoren unterscheiden sich. Falls die vollständige Delegierung einer Formel nicht möglich ist, wird der Anteil, der nicht delegiert werden kann, in der Erstellungsumgebung mit einer Warnung gekennzeichnet. Denken Sie möglichst über eine Änderung der Formel nach, um Funktionen und Operatoren zu vermeiden, die nicht delegiert werden können.  In der [Delegierungsliste](../maker/canvas-apps/delegation-list.md) werden die Datenquellen und Vorgänge, die nicht delegiert werden können, genau aufgeführt.

Wenn keine Delegierung möglich ist, überträgt PowerApps nur wenige Datensatzgruppen zur lokalen Bearbeitung. Filter- und Sortierungsfunktionen arbeiten dann mit weniger Datensatzgruppen. In der **[Galerie](../maker/canvas-apps/controls/control-gallery.md)** ist möglicherweise nicht alles verfügbar und das könnte für Benutzer verwirrend sein. 

Weitere Informationen finden Sie unter [Überblick über Delegation](../maker/canvas-apps/delegation-overview.md).

