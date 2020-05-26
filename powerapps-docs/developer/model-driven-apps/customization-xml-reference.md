---
title: Anpassungs-XML-Verweis (modellgesteuerte Apps) | Microsoft Docs
description: Die customizations.xml -Datei ist eine der Dateien, die in einer exportierten nicht verwalteten Lösung enthalten sind. Die Datei enthält alle oder ausgewählte Bereiche der Anpassung und Konfigurationen für Ihr System
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 864699de-c22f-3504-f120-84ca5a4aeca6
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 28bf6d2499cf5739421a548d0ac9e8030e95a6cb
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275950"
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
 [Informationen zum Bearbeiten der Anpassungsdatei](../common-data-service/when-edit-customization-file.md)  
[Bearbeiten Sie die Anpassungsdatei mit Schemavalidierung](edit-customizations-xml-file-schema-validation.md)  
 [Anpassen des Menübands für Dynamics 365](customize-commands-ribbon.md)  
 [Änderungsantragnavigation mithilfe von SiteMap](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap) <!-- TODO need to fix the link--> 
