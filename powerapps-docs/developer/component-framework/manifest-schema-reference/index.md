---
title: Referenz zum Manifestschema für das PowerApps-Komponentenframework | Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
manager: ''
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 045a395b-4475-48dd-8f67-6bc2b33cd89c
ms.openlocfilehash: 7cf5f46fedc5708f4e2f30dc30140b8a8d9f3529
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63393852"
---
# <a name="manifest-schema-reference"></a>Referenz zum Manifestschema

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

In diesem Abschnitt finden Sie die Referenzdokumentation für das Manifestschema, das mithilfe der PowerApps-CLI generiert wird.

> [!IMPORTANT]
> - Beim PowerApps-Komponentenframework handelt es sich um eine Previewfunktion.
> - [!INCLUDE[cc_preview_features_definition](../../../includes/cc-preview-features-definition.md)] 
> - [!INCLUDE[cc_preview_features_no_MS_support](../../../includes/cc-preview-features-no-ms-support.md)]

|Element|Beschreibung|
|----|-----------|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|
|[manifest](manifest.md)|Ein Manifest ist die Metadatendatei, die eine Komponente definiert. Dabei handelt es sich um ein XML-Dokument, das Folgendes beschreibt:<br/> – den Namespace der Komponente<br/> – die Art der Daten, für die es konfiguriert werden kann (Felder oder Datasets)<br/> – Eigenschaften, die in der Anwendung konfiguriert werden können, wenn die Komponente hinzugefügt wird<br/> – eine Liste der Ressourcendateien, die für die Komponente erforderlich sind<br/> – Bei einer der Ressourcendateien muss es sich um die JavaScript-Webressource handeln. Diese JavaScript-Ressource muss eine Funktion zum Instanziieren eines Objekts enthalten. Dadurch wird eine Schnittstelle implementiert, die die für die Komponente erforderlichen Methoden verfügbar macht. Diese wird als „Komponentenimplementierungsbibliothek“ bezeichnet.<br/> – Den Namen einer JavaScript-Funktion in der Komponentenimplementierungsbibliothek, die ein Objekt zurückgibt, das die erforderliche Schnittstelle anwendet.<br/> Wenn eine Komponente in der Anwendung konfiguriert wird, filtern die Daten im Manifest die verfügbaren Komponente, sodass nur für den jeweiligen Kontext gültige Komponenten konfiguriert werden können. Die Eigenschaften, die im Manifest für eine Komponente definiert werden, werden als Konfigurationsfelder gerendert, sodass die Person, die das Steuerelement konfiguriert, Werte angeben kann. Diese Eigenschaftswerte stehen für die Komponentenfunktion dann zur Laufzeit zur Verfügung.|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|
|[property-set](property-set.md)|[!INCLUDE [property-set-description](includes/property-set-description.md)]|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|


### <a name="related-topics"></a>Verwandte Themen

[PowerApps component framework Manifest Schema Reference (Referenz zum Manifestschema für das PowerApps-Komponentenframework)](index.md)<br/>
[PowerApps component framework API Reference (API-Referenz zum PowerApps-Komponentenframework)](../reference/index.md)<br/>
[PowerApps component framework Overview (Übersicht: PowerApps-Komponentenframework)](../overview.md)