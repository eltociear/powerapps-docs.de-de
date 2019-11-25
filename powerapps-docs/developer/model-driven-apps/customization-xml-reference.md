---
title: Anpassungs-XML-Verweis (modellgesteuerte Apps) | Microsoft Docs
description: Die customizations.xml -Datei ist eine der Dateien, die in einer exportierten nicht verwalteten Lösung enthalten sind. Die Datei enthält alle oder ausgewählte Bereiche der Anpassung und Konfigurationen für Ihr System
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 864699de-c22f-3504-f120-84ca5a4aeca6
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a5e4a9a44c7b3dcfb7131e5782bc680c114665e7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748475"
---
# <a name="customization-xml-reference"></a>Anpassungs-XML-Verweis

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customization-xml-reference -->

Die customizations.xml -Datei ist eine der Dateien, die in einer exportierten nicht verwalteten Lösung enthalten sind. Die Datei enthält alle oder ausgewählte Bereiche und Konfigurationen für Ihr System. 
  
 Die Lösungsdatei wird als komprimierte ZIP-Datei exportiert. Die Inhalte der Datei einer nicht verwalteten Lösung müssen extrahiert werden, bevor die Anpassungsdatei bearbeitet werden kann. Alle Dateien einer nicht verwalteten Lösung müssen in einer komprimierten .zip-Datei hinzugefügt werden, bevor sie wieder importiert werden.  

> [!NOTE]
> - Das Bearbeiten einer verwalteten Lösungsdatei wird nicht unterstützt.  
> - Nicht alle Elemente der Datei customizations.xml können bearbeitet werden. Weitere Informationen: [Support für die Bearbeitung der Anpassungs-Datei](../common-data-service/when-edit-customization-file.md).

## <a name="in-this-section"></a>In diesem Abschnitt

 [Menüband-Core-Schema](ribbon-core-schema.md) [Menübandtypenschema](ribbon-types-schema.md)  
 [Menüband-WSS-Schema](ribbon-wss-schema.md)  
 [SiteMap-Schema](/dynamics365/customer-engagement/developer/customize-dev/sitemap-schema)<br/> <!-- TODO need to fix the link--> 
 [Formular-XML-Schema](form-xml-schema.md)<br/> 
 [FetchXML-Schema](../common-data-service/fetchxml-schema.md) 

## <a name="related-sections"></a>Verwandte Abschnitte

 [In Dynamics 365 verwendete Schemas](/dynamics365/customer-engagement/developer/schemas-used-dynamics-365)<br/> <!-- TODO need to fix the link--> 
 [Wann Anpassungsdatei zu bearbeiten ist](../common-data-service/when-edit-customization-file.md)  
[Bearbeiten der Anpassungsdatei mit Schemaüberprüfung](edit-customizations-xml-file-schema-validation.md)  
 [Anpassen des Menübands für Dynamics 365](customize-commands-ribbon.md)  
 [Anwendungsnavigation mithilfe von SiteMap ändern](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap) <!-- TODO need to fix the link--> 
