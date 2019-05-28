---
ms.openlocfilehash: 7b0f9ce710887c870d22a6362f9cd28245d72519
ms.sourcegitcommit: d87b2068a63e416e2814791328a3a47bbcb5bb48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "62089608"
---
## <a name="delegation"></a>Delegierung
Nach Möglichkeit werden Filter- und Sortiervorgänge von PowerApps an die Datenquelle delegiert und die Seiten mit den Ergebnissen nur bei Bedarf bereitgestellt. Wenn Sie beispielsweise eine App starten, in der ein mit Daten gefülltes **[Katalog](../maker/canvas-apps/controls/control-gallery.md)** -Steuerelement angezeigt wird, wird zuerst nur die erste Gruppe mit Datensätzen auf das Gerät übertragen. Wenn der Benutzer einen Bildlauf durchführt, werden zusätzliche Daten aus der Datenquelle abgerufen. Das Ergebnis ist eine kürzere Startdauer für die App und Zugriff auf sehr große Datasets.

Allerdings ist die Delegierung ggf. nicht immer möglich. Es variiert, welche Funktionen und Operatoren in Datenquellen für die Delegierung unterstützt werden. Falls die vollständige Delegierung einer Formel nicht möglich ist, wird der Teil, der nicht delegiert werden kann, in der Erstellungsumgebung mit einer Warnung versehen. Erwägen Sie nach Möglichkeit, die Formel zu ändern, um die Verwendung von Funktionen und Operatoren zu vermeiden, die nicht delegiert werden können.  Im Artikel mit der Liste der [delegierbaren Datenquellen](../maker/canvas-apps/delegation-list.md) ist beschrieben, welche Datenquellen und Vorgänge delegiert werden können.

Wenn die Delegierung nicht möglich ist, wird von PowerApps nur eine kleine Gruppe von Datensätzen zur lokalen Verarbeitung abgerufen. Filter- und Sortierfunktionen werden also auf eine reduzierte Gruppe von Datensätzen angewendet. Die im **[Katalog](../maker/canvas-apps/controls/control-gallery.md)** verfügbaren Daten bilden unter Umständen nicht das Gesamtbild ab, und dies kann für Benutzer verwirrend sein. 

Weitere Informationen finden Sie unter [Grundlagen der Delegierung](../maker/canvas-apps/delegation-overview.md).

