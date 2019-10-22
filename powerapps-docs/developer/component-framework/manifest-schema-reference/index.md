---
title: Schema Referenz für das powerapps-Komponenten Framework Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 045a395b-4475-48dd-8f67-6bc2b33cd89c
ms.openlocfilehash: 8f58f10f6a3695615ddc3b58b540c59240af9641
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346369"
---
# <a name="manifest-schema-reference"></a>Referenz zum Manifestschema

In diesem Abschnitt finden Sie die Referenzdokumentation für das Manifestschema, das mithilfe der PowerApps-CLI generiert wird.

> [!IMPORTANT]
> Die Registerkarte " **verfügbar** " zeigt an, welche Elemente von Modell gesteuerten apps und Canvas-Apps unterstützt werden (experimentelle Vorschau). Es wird empfohlen, den Abschnitt **verfügbar für** jede einzelne Eigenschaft zu überprüfen, unabhängig davon, ob Sie unterstützt wird. Beispielsweise wird das **Code** -Element sowohl für Modell gesteuerte Apps als auch für Canvas-Apps unterstützt, **HTML** -und **IMG** -Eigenschaften in **Code** Elementen unterstützen jedoch keine Canvas-apps. 

|Element|Beschreibung|Verfügbar für|
|----|-----------|-----|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|Modellgesteuerte Apps|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|Modellgesteuerte Apps|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|Modellgesteuerte Apps|
|[manifest](manifest.md)|Ein Manifest ist die Metadatendatei, die eine Komponente definiert. Dabei handelt es sich um ein XML-Dokument, das Folgendes beschreibt:<br/> – den Namespace der Komponente<br/> – die Art der Daten, für die es konfiguriert werden kann (Felder oder Datasets)<br/> – Eigenschaften, die in der Anwendung konfiguriert werden können, wenn die Komponente hinzugefügt wird<br/> – eine Liste der Ressourcendateien, die für die Komponente erforderlich sind<br/> – Bei einer der Ressourcendateien muss es sich um die JavaScript-Webressource handeln. Diese JavaScript-Ressource muss eine Funktion zum Instanziieren eines Objekts enthalten. Dadurch wird eine Schnittstelle implementiert, die die für die Komponente erforderlichen Methoden verfügbar macht. Diese wird als „Komponentenimplementierungsbibliothek“ bezeichnet.<br/> – Den Namen einer JavaScript-Funktion in der Komponentenimplementierungsbibliothek, die ein Objekt zurückgibt, das die erforderliche Schnittstelle anwendet.<br/> Wenn eine Komponente in der Anwendung konfiguriert wird, filtern die Daten im Manifest die verfügbaren Komponente, sodass nur für den jeweiligen Kontext gültige Komponenten konfiguriert werden können. Die Eigenschaften, die im Manifest für eine Komponente definiert werden, werden als Konfigurationsfelder gerendert, sodass die Person, die das Steuerelement konfiguriert, Werte angeben kann. Diese Eigenschaftswerte stehen für die Komponentenfunktion dann zur Laufzeit zur Verfügung.|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)|
|[property-set](property-set.md)|[!INCLUDE [property-set-description](includes/property-set-description.md)]|Modellgesteuerte Apps|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)|
|[Verwendung von Features](feature-usage.md)|Das Feature-Usage-Element fungiert als Wrapper um die `uses-feature` Elemente, die es Entwicklern ermöglichen, zu deklarieren, welche Funktionen von der Komponente verwendet werden sollen. Wenn keine use-Feature-Elemente definiert sind, ist das Feature-Usage-Element nicht erforderlich.|Modellgesteuerte Apps|

### <a name="related-topics"></a>Verwandte Themen

[Schema Referenz für das powerapps-Komponenten Framework](index.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)