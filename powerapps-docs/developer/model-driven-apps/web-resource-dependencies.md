---
title: Webressourcenabhängigkeiten (modellgesteuerte Apps) | Microsoft Docs
description: Erfahren Sie über das Definieren von Abhängigkeiten zwischen Webressourcen in Common Data Service
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4c48a508a9e42e60dc3b9e9e0e374c7d72f1b11c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748792"
---
# <a name="web-resource-dependencies"></a>Abhängigkeiten von Webressourcen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/web-resource-dependencies -->

Sie können anderen Abhängigkeiten zwischen Webressourcen definieren. Hauptzweck der Funktionen ist es, Zuordnung von Webressourcen der Zeichenfolge (RESX) mit der JavaScript-Webressourcen zu erlauben, die sie verwendet. Dies ist auch der Weg, um Webressourcen, die HTML-Webressourcen für die Offline-Vewendung erfordern, auch für die oiffline Verfügbarkeit zu konfigurieren. 

Es gibt jedoch einige andere Verhalten, die Entwickler, die JavaScript-Webressourcen verwenden, nutzen können.

Das Bild zeigt die folgende Abhängigkeitsregisterkarte innerhalb des Webressourceformulars an. Abhängigkeiten zwischen Webressourcen sind in der oberen Liste festgelegt. Attributabhängigkeiten werden mithilfe der unteren Liste festgelegt. Attributabhängigkeiten sind für JavaScript-Webressourcen nur verfügbar. Weitere Informationen: [Attributabhängigkeiten](#attribute-dependencies)

![Registerkarte Abhängigkeiten von Webressourcen](media/web-resource-dependencies.PNG)

Innerhalb einer Lösung können Sie Abhängigkeiten innerhalb von Lösungskomponenten definieren. Bis zu den modusgesteuerten Apps war der Hauptzweck dieser Abhängigkeiten, das Verhindern von Löschen einer Lösungskomponente, wenn eine andere Lösungskomponente von ihr abhing. Mit modusgesteuerten Apps wird das Verhalten für JavaScript-Webressourcen erweitert, damit jede andere Webressource, die als Abhängigkeit für die JavaScript-Webressource aufgeführt ist, zusammen mit der JavaScript-Webressource geladen wird. 

> [!NOTE]
> Die Abhängigkeit wird nur eingerichtet, nachdem diese konfiguriert ist und die Webressource veröffentlicht wurde. Abhängigkeiten für unveröffentlichte Webressourcen treten nicht in Kraft, wenn die Webressource veröffentlicht wurde.

Das häufigste Szenario ist es, Webressourcen der Zeichenfolge (RESX) mit einer JavaScript-Webressource zuzuordnen, die davon abhängig ist. Es gibt eine Zeichenfolgen (RESX) Webressource für jede Sprache, die der JavaScript-Webressource zugeordnet ist, die sie verwendet. Wenn diese JavaScript-Webressource berechnet wird, werden die Werte automatisch auch für die bevorzugte Sprache des Benutzers lokalisiert und die Organisationsausgangssprache geladen, sodass sie für alle Verwendungen verfügbar sind. Da sie Lösungsabhängigkeiten zwischen diesen Ressourcen erstellen möchten, haben Sie weiter den Vorteil, dass Sie die abhängige RESX Ressource kennen, die automatisch geladen wird, wenn Sie diese benötigen.

Allerdings werden Webressourceabhängigkeiten nicht auf RESX-Webressourcen beschränkt. Sie können eine JavaScript-Webressource einer beliebigen anderen Webressource zuordnen, um Abhängigkeiten zu erstellen, die dafür sorgen, dass zugeordnete Webressource zusammen mit der JavaScript-Webressource geladen werden. Dies spart Zeit, da Sie nicht mehrere Webressourcen explizit laden müssen, wenn Sie ein Skript in einem Formularereignis registrieren. Sie müssen nur das primäre Skript registrieren und die Abhängigkeitskonfiguration lädt den Rest. Sie können eine Kette von Abhängigkeiten auch erstellen, da alle JavaScript-Webressourcen, die auf der primären JavaScript-Webressource berechnet werden, die Webressourcen enthalten, die für sie zugeordnet sind.

> [!IMPORTANT]
> Webressourcenabhängigkeiten bieten keine Steuerung über die Reihenfolge, in der die Webressourcen geladen werden. Alle Webressourcen werden asynchron und parallel geladen. Wenn Sie eine JavaScript-Webressource haben, die von mindestens einer anderen abhängt bzw. von ihr geladen und initialisiert wird, bevor die JavaScript-Webressource initialisiert werden kann, müssen Sie diese Abhängigkeit zuerst anders verwalten.

<a name="attribute-dependencies"></a>

## <a name="attribute-dependencies"></a>Attributabhängigkeiten
<!--TODO: Add links to the attribute and attribute.controls collection definitions in the Client API reference -->
 Beginnend mit modellgesteuerten Apps, wenn die JavaScript-Webressource von einem Entitätsattributwert abhängt, den Sie nicht im Formular anzeigen möchten, können Sie das Attribut als Abhängigkeit für die JavaScript-Webressource festlegen. Das bedeutet, dass das Attribut im Client API-Attributsammlung zur Verfügung steht sodass Sie den benötigten Wert in Ihrem Code abrufen oder festlegen können. Wenn Sie eine Abhängigkeit auf diese Weise hinzufügen, ist die Kontrollensammlung des Attributs leer, da nur vorhandene Einheiten im Formular vorhanden sind.

Vor dieser Funkltion müssen Sie manuell das Attribut dem Formular hinzufügen und dann die Steuerelement konfigurieren, die Sie verbergen möchten. Jetzt können Sie diese Abhängigkeit direkter einrichten und die Möglichkeit eliminieren, dass jemand das ausgeblendete Feld aus dem Formular entfernt. 


### <a name="see-also"></a>Siehe auch
[Webressourcen](web-resources.md)<br />
[Erstellen von barrierefreien Webressourcen](create-accessible-web-resources.md)<br />
[Webressourcen der Webseite (HTML)](webpage-html-web-resources.md)<br />
[Webressourcen für Skripts (JScript)](script-jscript-web-resources.md)<br />
[Bild- (JPG, PNG, GIF, ICO)-Webressourcen](image-web-resources.md)<br />
[XSL-Webressourcen (Stylesheet)](stylesheet-xsl-web-resources.md)<br />
[Webressourcen von Daten (XML)](data-xml-web-resources.md)<br />
[CSS Webressourcen](css-web-resources.md)<br />
[RESX Webressourcen](resx-web-resources.md)<br />
[WebResource-Entitätsreferenz](../common-data-service/reference/entities/webresource.md)<br />
[Beispiel: Mehrere Werte über den Datenparameter an eine Webressource übergeben](sample-pass-multiple-values-web-resource-through-data-parameter.md)<br />
[Beispiel: Importieren von Dateien als Webressourcen](sample-import-files-web-resources.md)<br />
