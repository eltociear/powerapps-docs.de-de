---
title: Schema-Referenz des PowerApps-Komponenten-Frameworks | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: null
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 045a395b-4475-48dd-8f67-6bc2b33cd89c
---

# <a name="manifest-schema-reference"></a>Manifestschemareferenz

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Dieser Abschnitt enthält Referenzdokumentation für das Manifestschema, das mithilfe der PowerApps-CLI generiert wird.

|Element|Beschreibung|
|----|-----------|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|
|[Steuerelement](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|
|[Datensatz](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|
|[Manifest](manifest.md)|Manifest ist die Metadatendatei, in der eine Komponente definiert wird. Es handelt sich um ein XML-Dokument, das Folgendes beschriebt:<br/> - Der Namespace der Komponente.<br/> - Die Art der Daten, die konfiguriert werden können, entweder ein Feld oder ein Datensatz.<br/> - Alle Eigenschaften, die in der Anwendung konfiguriert werden können, wenn die Komponente hinzugefügt wird.<br/> - Eine Liste der Ressourcenfelder, die die Komponente benötigt.<br/> - Eine davon muss eine JavaScript-Webressource sein. Dies JavaScript muss eine Funktion enthalten, die ein Objekt instanziiert. Dies implementiert eine Schnittstelle, die Methoden zur Verfügung stellt, die obligatorisch sind, damit die Komponente funktioniert. Dies wird als Komponentenimplementierungsbibliothek bezeichnet.<br/> - Der Name einer JavaScript-Funktion in der Komponentenimplementierungsbibliothek, die ein Objekt zurückgibt, das die erforderlichen Komponente anwendet.<br/> Wenn eine Komponente in der Anwendung konfiguriert wird, filtern die Daten im Manifest verfügbare Komponenten aus, damit nur gültige Komponenten für den Kontext für die Konfiguration verfügbar sind. Die Eigenschaften, die im Manifest für eine Komponente definiert werden, werden als Konfigurationsfelder gerendert, sodass die Person, die das Steuerelement konfiguriert, Werte angeben kann. Diese Eigenschaftswerte sind dann zur Laufzeit in Ihrer Komponentenfunktion verfügbar.|
|[Eigenschaft](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|
|[Eigenschaftssatz](property-set.md)|[!INCLUDE [property-set-description](includes/property-set-description.md)]|
|[Ressourcen](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|
|[Typ-Gruppe](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|


### <a name="related-topics"></a>Verwandte Themen

[Schema-Referenz des PowerApps Komponenten-Frameworks](index.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)