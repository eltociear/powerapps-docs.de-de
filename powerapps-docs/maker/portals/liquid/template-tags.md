---
title: Vorlagen-Tags für ein Portal verwenden | MicrosoftDocs
description: Lesen Sie mehr zu den verschiedenen verfügbaren Vorlage-Tags in einem Portal
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/24/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: a152fc23b71b2e564bad28a9f1717c15acfe9a60
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108297"
---
# <a name="template-tags"></a>Vorlagentags

Vorlagentags steuern die Ausgabe einer Vorlage auf verschiedene Arten und ermöglichen die Kombinationen mehrerer Vorlagen in einer einzigen Ausgabe.

## <a name="fetchxml"></a>fetchxml

Ermöglicht es dem Benutzer, Daten aus dem CDS abzufragen und die Ergebnisse auf einer Seite darzustellen.

> [!NOTE]
> Mehr über die Abfrage der Daten mit fetchxml erfahren Sie unter [Daten mit FetchXML abfragen ](https://docs.microsoft.com/powerapps/developer/common-data-service/use-fetchxml-construct-query).

```
{% fetchxml resultVariable %}
<!— Fetchxml query -->
...
{% endfetchxml %}
```

### <a name="results-attribute"></a>Ergebnis-Attribut

Das Ergebnis-Attribut in der bereitgestellten Variable (wie z. B. 'resultVariable' in obigem Beispiel) enthält FetchXML-Abfrageergebnisse und einige andere Attribute.

- *Entitäten*

    Dieses Attribut enthält das Ergebnis der fetchxml-Abfrage. Sie können das Ergebnis iterieren und in Ihrer Webvorlage verwenden.

    ```
    <table> 
    {% for entityVariable in resultVariable.results.entities %} 
    <tr> 
    <td>Attribut-1: {{ entityVariable.attribute1 }}</td> 
    <td>Attribut-2: {{ entityVariable.attribute2 }}</td> 
    </tr> 
    {% endfor %} 
    </table> 
    ```

- *EntityName*

    Ruft den logischen Namen der Entität ab.

- *ExtensionData*

    Ruft die Struktur ab, die zusätzliche Daten enthält.

- *MinActiveRowVersion*

    Ruft den niedrigsten aktiven Zeilenversionswert ab.

- *MoreRecords*

    Ruft ab, ob mehr Datensätze verfügbar sind.

- *PagingCookie*

    Ruft die aktuellen Paging-Informationen ab.

- *TotalRecordCount*

    Ruft die Gesamtzahl der Datensätze in der Sammlung ab. <br/>
    ReturnTotalRecordCount war wahr, als die Abfrage ausgeführt wurde.

- *TotalRecordCountLimitExceeded*

    Ruft ab, ob das Ergebnis der Abfrage die Gesamtzahl der Datensätze überschreitet.

### <a name="xml-attribute"></a>XML-Attribut

Das XML-Attribut in der bereitgestellten Variable (wie z. B. 'resultVariable' in obigem Beispiel) enthält die resultierende Abfrage, die verwendet werden kann, um Daten von Common Data Service zu erhalten. Dieses Attribut ist für Debugging-Zwecke nützlich, wenn Sie verstehen wollen, wie die Entitätsberechtigung auf dieses *fetchxml*-Tag angewendet wird.  

## <a name="include"></a>einschließlich

Integriert die Contents einer Vorlage in eine andere nach Name. In Power Apps-Portalen ist die Quelle dieser anderen Vorlage in der Regel eine [Webvorlage](store-content-web-templates.md). Dadurch können die gängigen Vorlagenfragmenten an mehreren Orten wieder verwendet werden.  

Wenn eine Vorlage in einer anderen enthalten ist, hat die integrierte Vorlage Zugang zu Variablen, die in der übergeordneten Vorlage definiert sind.

`{% include 'My Template' %}`

Es ist ebenfalls möglich, eine beliebige Zahl von benannten Parametern im Tag einzuschließen. Diese werden dann als Variablen in der integrierten Vorlage definiert.

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>Block

Wird in Verbindung mit „extends” verwendet, um den Vorlagen-Vererbungsstatus bereitzustellen. Siehe „extends” zur Verwendung.

## <a name="extends"></a>erweitern

Wird in Verbindung mit dem „block”-Tag verwendet, stellt die Vorlagenvererbung bereit. Dadurch können mehrere Vorlagen ein freigegebenes Layout verwenden, während spezifische Bereiche des übergeordneten Layouts überschrieben werden.

In Power Apps-Portalen bezieht sich der für den Tag angegebene Name der übergeordneten Vorlage im Allgemeinen auf einen Namen für eine [Webvorlage](store-content-web-templates.md).  

Wenn „extends” verwendet wird, muss es der erste Inhalt in der Vorlage sein und kann nur von einem oder mehreren „block”-Tags gefolgt werden.

Wenn ein in der übergeordneten Vorlage definierter Block nicht überschrieben wird, wird der Inhalt in der übergeordneten Vorlage (sofern vorhanden) gerendert.

## <a name="comment"></a>Kommentar

Ermöglicht es Ihnen, ungerenderte Codes in einer Liquid-Vorlage zu belassen. Der Content innerhalb des Blocks wird nicht gerendert und der Liquid-Code darin wird nicht ausgeführt.

**Code**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**Ausgabe**

`Hello. My name is Charles.`

## <a name="raw"></a>unformatiert

Ermöglicht die Ausgabe des Liquid-Codes auf einer Seite, ohne dass Sie analysiert und ausgeführt werden muss.

**Ausgabe**

`Hello, {{ user.fullname }}. My name is Charles.`

## <a name="substitution"></a>Ersatz

Wenn der Benutzer das Zwischenspeichern von Kopf- und Fußzeilen aktiviert hat und das Zwischenspeichern bestimmter Abschnittsausgaben vermeiden möchte, kann er dieses Tag verwenden. Dieses Tag stellt den Inhaltsblock in der Kopf- oder Fußzeile bereit, in der die Ausgabe des umbrochenen Inhaltsblocks nicht zwischengespeichert wird. Dies ist hilfreich in Szenarien, in denen der Benutzer ein Objekt verwendet, das häufig aktualisiert werden kann, z. B. Anforderung, Seite, Sprache und Datum. In den Szenarien zur Aktualisierung des Quellcodes von Webvorlagen für Kopf- und Fußzeilen wird beispielsweise angegeben, wenn [das Zwischenspeichern von Kopf- und Fußzeilen aktiviert ist](../configure/enable-header-footer-output-caching.md).

### <a name="see-also"></a>Siehe auch

[Ablaufsteuerungstags](control-flow-tags.md)<br>
[Iterationstags](iteration-tags.md)<br>
[Variable Tags](variable-tags.md)<br>
[Power Apps Common Data Service-Entitäts-Tags](portals-entity-tags.md)
