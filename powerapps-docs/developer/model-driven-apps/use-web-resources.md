---
title: Webressourcen verwenden | Microsoft Docs
description: Erfahren Sie, wie Entwickler Webressourcen innerhalb modellgesteuerter Apps verenden können
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8786c43f78438e993853b683e31a602bf86c3584
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748788"
---
# <a name="use-web-resources"></a>Webressourcen verwenden

Es gibt einen virtuellen Ordner mit Namen `webresources` innerhalb jeder Common Data Service-Instanz, wo Sie HTML-, JS-, CSS-, Bild- oder andere Dateien nach Namen anfordern können und auf sie in Ihrem Browser zugreifen können. Sie können diese Dateien mit der Anwendung hochladen oder sie programmbasiert als [WebResource-Entität](../common-data-service/reference/entities/webresource.md)-Datensätze hinzufügen. Der [XrmToolBox-WebResources-Manager](https://www.xrmtoolbox.com/plugins/MsCrmTools.WebResourcesManager/) ist ein Community-Tool, das die Arbeit mit diesen Datensätzen erleichtern kann.

Diese Datensätze können auf einander verweisen mithilfe relativer Pfadnamen in ihrem Inhalt. Diese Fähigkeit, Dateien hochzuladen und sie dem Namen nach anzufordern, bietet alle Bausteine, die Sie benötigen, um Webanwendungen mithilfe von Dateien zu erstellen, die innerhalb der authentifizierten Sitzung Ihres Browsers verarbeitet werden. Durch die ausschließliche Verwendung von clientseitigem Code mit AJAX-Techniken können Sie umfangreiche Anwendungen erstellen, die Sie innerhalb eines Browserfensters oder innerhalb eines IFrame in einem Formular oder Dashboard ausführen können. 

Am häufigsten werden Sie JavaScript-Webressourcen verwenden, um Ereignishandlerfunktionen Formularen und Befehlen hinzuzufügen.

Weitere Informationen:
- [Client-Skripterstellung mit modellgesteuerten Apps](client-scripting.md)
- [Webressourcen](/dynamics365/customer-engagement/developer/web-resources)
