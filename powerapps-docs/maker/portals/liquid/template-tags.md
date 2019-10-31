---
title: Vorlagen-Tags für ein Portal verwenden | MicrosoftDocs
description: Lesen Sie mehr zu den verschiedenen verfügbaren Vorlage-Tags in einem Portal
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="template-tags"></a>Vorlagentags

Vorlagentags steuern die Ausgabe einer Vorlage auf verschiedene Arten und ermöglichen die Kombinationen mehrerer Vorlagen in einer einzigen Ausgabe.

## <a name="include"></a>einschließlich

Integriert die Contents einer Vorlage in eine andere nach Name. In PowerApps Portalen ist die Quelle dieser anderen Vorlage in der Regel eine [Webvorlage](store-content-web-templates.md). Dadurch können die gängigen Vorlagenfragmenten an mehreren Orten wieder verwendet werden.  

Wenn eine Vorlage in einer anderen enthalten ist, hat die integrierte Vorlage Zugang zu Variablen, die in der übergeordneten Vorlage definiert sind.

`{% include 'My Template' %}`

Es ist ebenfalls möglich, eine beliebige Zahl von benannten Parametern im Tag einzuschließen. Diese werden dann als Variablen in der integrierten Vorlage definiert.

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>Block

Wird in Verbindung mit „extends” verwendet, um den Vorlagen-Vererbungsstatus bereitzustellen. Siehe „extends” zur Verwendung.

## <a name="extends"></a>erweitern

Wird in Verbindung mit dem „block”-Tag verwendet, stellt die Vorlagenvererbung bereit. Dadurch können mehrere Vorlagen ein freigegebenes Layout verwenden, während spezifische Bereiche des übergeordneten Layouts überschrieben werden.

In PowerApps Portalen bezieht sich der Name der übergeordneten Vorlage, der dem Tag zugewiesen wird, im Allgemeinen auf den Namen einer [Webvorlage](store-content-web-templates.md).  

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

### <a name="see-also"></a>Siehe auch

[Ablaufsteuerungstags](control-flow-tags.md)<br>
[Iterationstags](iteration-tags.md)<br>
[Variable Tags](variable-tags.md)<br>
[PowerApps Common Data Service-Entitäts-Tags](portals-entity-tags.md)
