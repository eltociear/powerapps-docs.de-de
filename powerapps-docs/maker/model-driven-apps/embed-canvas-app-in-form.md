---
title: Einbetten einer Canvas-App in ein modellgesteuertes Formular | MicrosoftDocs
ms.custom: ''
ms.date: 12/10/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="embed-a-canvas-app-on-a-model-driven-form"></a>Einbetten einer Canvas-App in einem modellgesteuerten Formular

Canvas-Apps ermöglichen es Herstellern, mit dem Low-Code, WYSIWYG Canvas-App-Designer einfach eigene Layouts zu entwerfen und zu erstellen. Canvas-Apps ermöglichen es den Herstellern auch, Daten aus über 200 Datenquellen in ihren Formularen zu verbinden und anzuzeigen.

> [!NOTE]
> Diese Funktion befindet sich derzeit in der Vorschau. <br />
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

Mit eingebetteten Canvas-Anwendungen können Hersteller die Leistungsfähigkeit von Canvas-Anwendungen in ihre modellgesteuerten Formulare integrieren. Mit eingebetteten Canvas-Apps können Sie auf einfache Weise umfangreiche visuelle Bereiche auf einem Formular erstellen und Daten aus einer Vielzahl von Quellen direkt neben Daten aus dem Common Data Service anzeigen.

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-canvas-app-in-form.png "Eingebettete Canvas-App in einem modelgestützten App-Formular")

Canvas-Anwendungen werden in modellgestützte Formulare eingebettet, genauso wie andere benutzerdefinierte Steuerelemente hinzugefügt werden. Eine eingebettete Canvas-App enthält umfangreiche Datenintegrationsfunktionen, die kontextuelle Daten aus dem Hostmodell-basierten Formular in die eingebettete Canvas-App einbringen.

Die Schritte zum Einbetten einer Canvas-Applikation in Ihr modellgestütztes Formular variieren je nach Datenkontext, den das Hostmodell-basierte Formular der eingebetteten Canvas-App zur Verfügung stellen soll.
-   Übergeben Sie den aktuellen Datensatz als Datenkontext. Weitere Informationen: [Den aktuellen Datensatz als Datenkontext mit einer eingebetteten Canvas-App übergeben](pass-current-embedded-canvas-app.md)
-   Übergeben Sie eine Liste von Datensätzen, die sich auf den aktuellen Datensatz beziehen, als Datenkontext. Weitere Informationen: [Eine Liste von aktuellen Datensätzen als Datenkontext mit einer eingebetteten Canvas-App übergeben ](pass-related-embedded-canvas-app.md) 

<!-- After you have added an embedded canvas app to your model-driven form, learn how to share your embedded canvas app with other users (LINK TO ARTICLE #4).  -->

<!-- For things to keep in mind when working with embedded canvas apps and to help troubleshoot any issues you might encounter, see (LINK TO ARTICLE #5). -->

## <a name="see-also"></a>Siehe auch
[Was sind Canvas-Apps in PowerApps?](../canvas-apps/getting-started.md) <br />
[Hinzufügen und konfigurieren eines CanvasApp-Steuerelements in PowerApps](../canvas-apps/add-configure-controls.md) <br />
[Übersicht über CanvasApp-Konnektoren für PowerApps](../canvas-apps/connections-list.md) 
