---
ms.openlocfilehash: d74254f2536b78a0951c860d803519827d31e446
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678264"
---
## <a name="delegation"></a>Delegierung
Wenn möglich, delegieren Power apps Filter-und Sortiervorgänge an die Datenquelle und durchlaufen die Ergebnisse bei Bedarf. Wenn Sie beispielsweise eine App starten, in der ein mit Daten gefülltes **[Katalog](../maker/canvas-apps/controls/control-gallery.md)** -Steuerelement angezeigt wird, wird zuerst nur die erste Gruppe mit Datensätzen auf das Gerät übertragen. Wenn der Benutzer einen Bildlauf durchführt, werden zusätzliche Daten aus der Datenquelle abgerufen. Das Ergebnis ist eine kürzere Startdauer für die App und Zugriff auf sehr große Datasets.

Allerdings ist die Delegierung ggf. nicht immer möglich. Es variiert, welche Funktionen und Operatoren in Datenquellen für die Delegierung unterstützt werden. Falls die vollständige Delegierung einer Formel nicht möglich ist, wird der Teil, der nicht delegiert werden kann, in der Erstellungsumgebung mit einer Warnung versehen. Erwägen Sie nach Möglichkeit, die Formel zu ändern, um die Verwendung von Funktionen und Operatoren zu vermeiden, die nicht delegiert werden können.  Im Artikel mit der Liste der [delegierbaren Datenquellen](../maker/canvas-apps/delegation-list.md) ist beschrieben, welche Datenquellen und Vorgänge delegiert werden können.

Wenn eine Delegierung nicht möglich ist, ruft Power Apps nur eine kleine Gruppe von Datensätzen ab, um lokal zu arbeiten. Filter- und Sortierfunktionen werden also auf eine reduzierte Gruppe von Datensätzen angewendet. Die im **[Katalog](../maker/canvas-apps/controls/control-gallery.md)** verfügbaren Daten bilden unter Umständen nicht das Gesamtbild ab, und dies kann für Benutzer verwirrend sein. 

Weitere Informationen finden Sie unter [Grundlagen der Delegierung](../maker/canvas-apps/delegation-overview.md).

