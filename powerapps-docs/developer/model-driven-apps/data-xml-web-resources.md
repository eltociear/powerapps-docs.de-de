---
title: Daten (XML)-Webressourcen (modellgesteuerte Apps) | Microsoft Docs
description: Infos zur Verwendung von Webressourcen von Daten (XML), um Daten sicher aufzurufen und zu speichern.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 2bf0d49f-8b6d-6d5b-0af5-edf6dd485fed
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bc5eeb970ecd8d54b7276e0f932e4822456e04e4
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276126"
---
# <a name="data-xml-web-resources"></a>Webressourcen von Daten (XML)

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/data-xml-web-resources -->

Verwenden Sie Webressourcen von Daten (XML), um Daten sicher aufzurufen und zu speichern.  
  
## <a name="capabilities-of-xml-web-resources"></a>Verwendungsmöglichkeiten für XML-Webressourcen  
 Verwenden Sie XML-Webressourcen, um Daten zwischenzuspeichern, die Sie in Ihrer Lösung verwenden möchten.  
  
### <a name="limitations-of-xml-web-resources"></a>Einschränkungen von XML-Webressourcen  
 Verwenden Sie XML-Webressourcen, um für Ihre Lösungen Konfigurationseinstellungen oder Metadaten zwischenzuspeichern.  
  
 Eine XML-Webressource ist keine robuste Lösung für Daten, die häufig von mehreren Benutzern aktualisiert werden. Während ein Benutzer eine XML-Webressource aktualisiert, könnten andere Benutzer (oder ein automatisch ablaufender Prozess) die Webressource ebenfalls aktualisieren. In einem solchen Fall gehen diese Daten verloren, wenn der erste Benutzer seine Änderungen speichert.  
  
 Alle XML-Dateien müssen die XML-Dateinamenerweiterung verwenden. Dateien, die XML-Daten ohne die XML-Dateinamenerweiterung verwenden, können nicht als Webressourcen hochgeladen werden, solange die Dateinamenerweiterung nicht geändert wird.  
  
### <a name="see-also"></a>Siehe auch  
 [Webressourcen](web-resources.md)   
 [Verwendung von Web-Seiten (HTML) Web-Ressourcen](webpage-html-web-resources.md)   
 [Verwendung von Style Sheet (CSS) Webressourcen](css-web-resources.md)   
 [Benutzung von Skript (JScript)-Webressourcen](script-jscript-web-resources.md)   
 [Verwendung von Bildern (JPG, PNG, GIF) Web-Ressourcen](image-web-resources.md)   
 [Benutzung von Silverlight (XAP)-Webressourcen](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)<br/>   <!-- TODO need to update the relevant link from the powerapps repo-->
 [Verwendung von Stylesheet (XSL)-Webressourcen](/dynamics365/customer-engagement/developer/stylesheet-xsl-web-resources) <!-- TODO need to update the relevant link from the powerapps repo-->
