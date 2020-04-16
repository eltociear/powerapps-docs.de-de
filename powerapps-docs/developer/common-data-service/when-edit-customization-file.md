---
title: Informationen zum Bearbeiten der Anpassungsdatei (Common Data Service) | MicrosoftDocs
description: Die Datei customizations.xml , die als Teil einer nicht verwalteten Lösung exportiert wird, kann bearbeitet werden, sodass bestimmte Anpassungsaufgaben ausgeführt werden. Nachdem Sie die Datei bearbeitet haben, können Sie die geänderte Datei zusammen mit anderen Dateien komprimieren, die in der nicht verwalteten Lösung exportiert werden. Sie übernehmen die Änderungen, indem Sie die geänderte nicht verwaltete Lösung importieren.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: cac303a6-70f9-3962-879a-fbf7fdc2364f
author: shmcarth
ms.author: jdaly
manager: ryjones
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e35d21cbb4dd9898ae7b535c052880fe61df647e
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154942"
---
# <a name="when-to-edit-the-customizations-file"></a>Informationen zum Bearbeiten der Anpassungsdatei

Die Datei customizations.xml , die als Teil einer nicht verwalteten Lösung exportiert wird, kann bearbeitet werden, sodass bestimmte Anpassungsaufgaben ausgeführt werden. Nachdem Sie die Datei bearbeitet haben, können Sie die geänderte Datei zusammen mit anderen Dateien komprimieren, die in der nicht verwalteten Lösung exportiert werden. Sie übernehmen die Änderungen, indem Sie die geänderte nicht verwaltete Lösung importieren.  
  
 Die Bearbeitung einer komplexen XML-Datei wie die Datei customizations.xml ist viel einfacher und weniger fehleranfällig, wenn Sie ein Programm verwenden, das für Schemaüberprüfung konzipiert ist. Die Datei kann zwar mithilfe eines einfachen Text-Editors wie Notepad bearbeitet werden. Dies wird jedoch nicht empfohlen, es sei denn, dass Sie mit dem Bearbeiten dieser Datei sehr vertraut sind. Weitere Informationen finden Sie unter [Bearbeiten der Anpassungsdatei mit Schemaüberprüfung](../model-driven-apps/edit-customizations-xml-file-schema-validation.md). 
  
> [!IMPORTANT]
>  Ungültige XML oder eine falsche Definition der Lösungskomponenten kann Fehler verursachen, die das Importieren einer manuell bearbeiteten nicht verwalteten Lösung verhindern.  
  
## <a name="supported-tasks"></a>Unterstützte Aufgaben  
 Sie können die Datei customization.xml bearbeiten, sodass die folgenden Aufgaben ausgeführt werden.  
  
 **Bearbeiten des Menübands**  
 Diese Dokumentation beschreibt den Vorgang zum Bearbeiten des Menübands durch direkte Bearbeitung der Datei customization.xml. Einige Benutzer haben Ribbon-Editoren erstellt, die eine Benutzeroberfläche bieten, die das Bearbeiten des Menübands vereinfacht. Die gängigste bisher ist das [Ribbon Workbench](https://www.develop1.net/public/rwb/ribbonworkbench.aspx). Um Support für die Verwendung der Software zu erhalten, setzen Sie sich mit dem Programmherausgeber in Verbindung.  
  
 Weitere Informationen zum Bearbeiten des Menübands durch manuelle Bearbeitung der Datei customization.xml finden Sie unter [Anpassen des Menübands für Microsoft Dynamics 365](../model-driven-apps/customize-commands-ribbon.md).  
  
 **Bearbeiten der Siteübersicht**  
 Das SDK beschreibt den Vorgang zum Bearbeiten des Menübands durch direkte Bearbeitung der Datei customization.xml. Allerdings wird empfohlen, den Siteübersichtdesigner in Common Data Service zu verwenden, um Siteübersichten zu erstellen oder zu aktualisieren. Weitere Informationen: [Erstellen einer Siteübersicht für eine App mithilfe des Siteübersichtsdesigners](../../maker/model-driven-apps/create-site-map-app.md)
  
 Sie können einen Community-entwickelten der Siteübersichtseditoren verwenden, wie den [XrmToolBox-Siteübersichts-Editor](https://www.xrmtoolbox.com/plugins/MsCrmTools.SiteMapEditor/).   
  
 Informationen hierzu finden Sie unter [Änderung der Anwendungsnavigation mithilfe von SiteMap](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap). 
 
  
 **Bearbeiten von FormXml**  
 FormXml wird verwendet, um Entitätsformulare und Dashboards zu definieren. Der Formular-Editor und der Dashboard-Designer in der Anwendung sind die am häufigsten verwendeten Tools für diesen Zweck. Alternativ kann die Datei customizations.xml bearbeitet werden. Weitere Informationen finden Sie unter [Anpassen von Entitätsformularen in Microsoft Dynamics 365](../model-driven-apps/customize-entity-forms.md) und [Erstellen eines Dashboards](../model-driven-apps/create-dashboard.md).
  
 **Bearbeiten von gespeicherten Abfragen**  
 Definitionen von Ansichten für Entitäten sind in der Datei customizations.xml enthalten und können manuell bearbeitet werden. Der Ansicht-Editor in der Anwendung ist das am häufigsten verwendeten Tool für diesen Zweck. Alternativ kann die Datei customizations.xml bearbeitet werden. Weitere Informationen finden Sie unter [Anpassen von Entitätsansichten in Microsoft Dynamics 365](../model-driven-apps/customize-entity-views.md).
  
 **Bearbeiten von ISV.config**  
 In älteren Versionen von Dynamics 365 Common Data Service diente ISV.Config zum Hinzufügen von Client-Anwendungserweiterungen und einigen anderen Konfigurationsoptionen. Für Microsoft Dynamics CRM 2011 und Microsoft Dynamics 365 Online stellt das Menüband die Möglichkeit bereit, die Anwendung zu erweitern. Die einzige verbleibenden Funktion in ISV.Config ist die Anpassung der Darstellung des Servicekalenders. Weitere Informationen finden Sie unter [Servicekalender-Darstellungskonfiguration](/dynamics365/customer-engagement/developer/customize-dev/service-calendar-appearance-configuration).
  
## <a name="unsupported-tasks"></a>Nicht unterstützte Aufgaben  
 Das Definieren anderer Lösungskomponenten durch Bearbeitung der exportierten Datei customizations.xml wird nicht unterstützt. Dies beinhaltet Folgendes:  
  
-   Entitäten  
  
-   Attribute  
  
-   Entitätsbeziehungen  
  
-   Entitätsmeldungen  
  
-   Optionssätze  
  
-   Webressourcen  
  
-   Prozesse (Workflows)  
  
-   Plug-In-Assemblys  
  
-   SDK-Nachrichtenverarbeitungsschritte  
  
-   Dienstendpunkte  
  
-   Berichte  
  
-   Verbindungsrollen  
  
-   Artikelvorlagen  
  
-   Vertragsvorlagen  
  
-   E-Mail-Vorlagen  
  
-   Seriendruckvorlagen  
  
-   Sicherheitsrollen  
  
-   Feldsicherheitsprofile  
  
### <a name="see-also"></a>Siehe auch  
 [Anpassen von Microsoft Dynamics 365 und Microsoft Dynamics 365 (online)](/dynamics365/customer-engagement/developer/customize-dev/customize-applications)   <!-- TODO Need to find the topic in powerapps repo-->
 [Anpassen der XML-Referenz](../model-driven-apps/customization-xml-reference.md) [Anpassen des Lösungsdateischemas](customization-solutions-file-schema.md)  
 [Menübandkernschema](../model-driven-apps/ribbon-core-schema.md) [Menübandtypenschema](../model-driven-apps/ribbon-types-schema.md) [Menüband-WSS-Schema](../model-driven-apps/ribbon-wss-schema.md)   
 [SiteMap-Schema](/dynamics365/customer-engagement/developer/customize-dev/sitemap-schema) [Formular-XML-Schema](../model-driven-apps/form-xml-schema.md)   
 [Schemaunterstützung für das Bearbeiten der Anpassungsdatei](../model-driven-apps/edit-customizations-xml-file-schema-validation.md)