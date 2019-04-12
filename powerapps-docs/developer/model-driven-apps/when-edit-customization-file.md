---
title: Wann ist eine Anpassungsdatei zu bearbeiten (modellgesteuerte Apps) | Microsoft Docs
description: 'In diesem Thema wird behandelt, wann eine Anpassungsdatei zu bearbeiten ist sowie verschiedene mögliche Vorgehensweisen dabei'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="when-to-edit-the-customizations-file"></a>Informationen zum Bearbeiten der Anpassungsdatei

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/when-edit-customization-file -->

Die Datei customizations.xml , die als Teil einer nicht verwalteten Lösung exportiert wird, kann bearbeitet werden, sodass bestimmte Anpassungsaufgaben ausgeführt werden. Nachdem Sie die Datei bearbeitet haben, können Sie die geänderte Datei zusammen mit anderen Dateien komprimieren, die in der nicht verwalteten Lösung exportiert werden. Sie übernehmen die Änderungen, indem Sie die geänderte nicht verwaltete Lösung importieren.  
  
 Die Bearbeitung einer komplexen XML-Datei wie die Datei customizations.xml ist viel einfacher und weniger fehleranfällig, wenn Sie ein Programm verwenden, das für Schemaüberprüfung konzipiert ist. Die Datei kann zwar mithilfe eines einfachen Text-Editors wie Notepad bearbeitet werden. Dies wird jedoch nicht empfohlen, es sei denn, dass Sie mit dem Bearbeiten dieser Datei sehr vertraut sind. Weitere Informationen finden Sie unter [Bearbeiten der Anpassungsdatei mit Schemaüberprüfung](edit-customizations-xml-file-schema-validation.md).  
  
> [!IMPORTANT]
>  Ungültige XML oder eine falsche Definition der Lösungskomponenten kann Fehler verursachen, die das Importieren einer manuell bearbeiteten nicht verwalteten Lösung verhindern.  
  
## <a name="supported-tasks"></a>Unterstützte Aufgaben  
 Sie können die Datei customization.xml bearbeiten, sodass die folgenden Aufgaben ausgeführt werden.  
  
 **Bearbeiten des Menübands**  
 Diese Dokumentation beschreibt den Vorgang zum Bearbeiten des Menübands durch direkte Bearbeitung der Datei customization.xml. Einige Benutzer haben Ribbon-Editoren erstellt, die eine Benutzeroberfläche bieten, die das Bearbeiten des Menübands vereinfacht. Die gängigste bisher ist das [Ribbon Workbench](https://www.develop1.net/public/rwb/ribbonworkbench.aspx). Um Support für die Verwendung der Software zu erhalten, setzen Sie sich mit dem Programmherausgeber in Verbindung.  
  
 Weitere Informationen zum Bearbeiten des Menübands durch manuelle Bearbeitung der Datei customization.xml finden Sie unter [Das Menüband anpassen](customize-commands-ribbon.md).  
  
 **Bearbeiten der Siteübersicht**  
 Das SDK beschreibt den Vorgang zum Bearbeiten des Menübands durch direkte Bearbeitung der Datei customization.xml. Allerdings wird empfohlen, den Siteübersichts-Designer in modellgesteuerten Apps zu verwenden, um Siteübersichten zu erstellen oder zu aktualisieren. More information: [Tutorial: Erstellen einer Siteübersicht für modellgesteuerte Apps mithilfe des Siteübersichts-Designers](../../maker/model-driven-apps/create-site-map-app.md)  
  
 Sie können einen Community-entwickelten der Siteübersichtseditoren verwenden, wie den [XrmToolBox-Siteübersichts-Editor](https://www.xrmtoolbox.com/plugins/MsCrmTools.SiteMapEditor/).   
  
 Informationen hierzu finden Sie unter [Änderung der Anwendungsnavigation mithilfe von SiteMap](/developer/customize-dev/change-application-navigation-using-sitemap.md).  
  
 **Bearbeiten von FormXml**  
 FormXml wird verwendet, um Entitätsformulare und Dashboards zu definieren. Der Formular-Editor und der Dashboard-Designer in der Anwendung sind die am häufigsten verwendeten Tools für diesen Zweck. Alternativ kann die Datei customizations.xml bearbeitet werden. Weitere Informationen finden Sie unter [Entitätsformulare anpassen](customize-entity-forms.md) und [Dashboard erstellen](create-dashboard.md).  
  
 **Bearbeiten von gespeicherten Abfragen**  
 Definitionen von Ansichten für Entitäten sind in der Datei customizations.xml enthalten und können manuell bearbeitet werden. Der Ansicht-Editor in der Anwendung ist das am häufigsten verwendeten Tool für diesen Zweck. Alternativ kann die Datei customizations.xml bearbeitet werden. Weitere Informationen finden Sie unter [Anpassen von Entitätsansichten](customize-entity-views.md).  
  
 **Bearbeiten von ISV.config**  
  Bei Common Data Service bietet das Menüband die Möglichkeit, die Anwendung zu erweitern. Die einzige verbleibenden Funktion in ISV.Config ist die Anpassung der Darstellung des Servicekalenders. Weitere Informationen finden Sie unter [Servicekalender-Darstellungskonfiguration](/dynamics365/customer-engagement/developer/customize-dev/service-calendar-appearance-configuration).  
  
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
  
-   Mail Merge Templates  
  
-   Sicherheitsrollen  
  
-   Feldsicherheitsprofile  
  

### <a name="see-also"></a>Siehe auch  
 [Anpassungs-XML-Verweis](customization-xml-reference.md)   
 [Anpassungslösungsdateischema](../common-data-service/customization-solutions-file-schema.md)   
 [Menübandkernschema](ribbon-core-schema.md) [Menübandtypenschema](ribbon-types-schema.md) [Menüband-WSS-Schema](ribbon-wss-schema.md)   
 [Formular-XML-Schema](form-xml-schema.md)   
 [Schemaunterstützung für das Bearbeiten der Anpassungsdatei](edit-customizations-xml-file-schema-validation.md)
