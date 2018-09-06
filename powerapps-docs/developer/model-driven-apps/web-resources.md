---
title: Verwenden von Webressourcen | Microsoft-Dokumentation
description: Erfahren Sie, wie Entwickler Webressourcen in modellgesteuerten Apps verwenden.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/17/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 88e51e4547732bed2d3e7ef3290bc8d933afded3
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849909"
---
# <a name="use-web-resources"></a>Verwenden von Webressourcen

In jeder Instanz von Common Data Service für Apps gibt es einen virtuellen Ordner mit dem Namen `webresources`, in dem Sie HTML-, JS- und CSS-Dateien sowie Bilddateien und andere Dateien anfordern und auf diese in Ihrem Browser zugreifen können. Sie können diese Dateien mithilfe der Anwendung hochladen oder sie programmgesteuert als [WebResource Entity](../common-data-service/reference/entities/webresource.md)-Einträge hinzufügen. [XrmToolBox WebResources Manager](https://www.xrmtoolbox.com/plugins/MsCrmTools.WebResourcesManager/) ist ein Communitytool, das das Arbeiten mit Einträgen erleichtern kann.

Diese Einträge können inhaltlich über relative Pfadnamen aufeinander verweisen. Dadurch, dass Sie Dateien hochladen und diese anhand ihrer Namen anfordern können, werden sämtliche Bausteine zur Verfügung gestellt, die Sie benötigen, um Webanwendungen mithilfe von Dateien zu erstellen, die in der authentifizierten Browsersitzung verarbeitet werden. Wenn Sie nur clientseitigen Code in Kombination mit AJAX-Techniken verwenden, können Sie umfassende Anwendungen erstellen, die in Form eines Dashboards in einem Browserfenster oder in einem IFrame-Element ausgeführt werden können. 

In der Regel werden JavaScript-Webressourcen verwendet, um Ereignishandlerfunktionen zu Formularen und Befehlen hinzuzufügen.

Weitere Informationen finden Sie unter:
- [Client scripting with model-driven apps (Erstellen von Clientskripts mit modellgesteuerten Apps)](client-scripting.md)
- [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Webressourcen](/dynamics365/customer-engagement/developer/web-resources)
