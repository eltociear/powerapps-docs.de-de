---
title: Bearbeiten der Anpassungs-XML-Datei mit Schemaüberprüfung (modellgestützte Apps) | Microsoft Docs
description: 'Die Datei customizations.xml ist in der komprimierten ZIP-Datei enthalten, die als Lösung exportiert wird. Bestimmte Teile der Datei customizations.xml können manuell bearbeitet werden. Informationen zum Schema helfen dabei, sicherzustellen, dass alle Änderungen, die Sie vornehmen, gültig sind.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: b77d962e-6e3c-bd28-d03c-cf2e23cd742d
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="edit-the-customizations-xml-file-with-schema-validation"></a>Bearbeiten der XML-Datei für Anpassungen mit Schemaüberprüfung

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/edit-customizations-xml-file-schema-validation -->

Die Datei customizations.xml ist in der komprimierten ZIP-Datei enthalten, die als Lösung exportiert wird. Bestimmte Teile der Datei customizations.xml können manuell bearbeitet werden. Informationen zum Schema helfen dabei, sicherzustellen, dass alle Änderungen, die Sie vornehmen, gültig sind.  
  
## <a name="xsd-schema-files"></a>XSD-Schemadateien:  
 [!INCLUDE[schema_download](../../includes/schema-download.md)] für die XCD-Schemadateien verwendet, um die customizations.xml Datei in einer Lösung zu validieren. Die erforderlichen Dateien sind:  
  
- CustomizationsSolution.xsd  
  
- fetch.xsd  
  
- FormXml.xsd  
  
- isv.config.xsd  
  
- RibbonCore.xsd  
  
- RibbonTypes.xsd  
  
- RibbonWSS.xsd  
  
- SiteMap.xsd  
  
- SiteMapType.xsd  
  
- VisualizationDataDescription.xsd  
  
  Diese Dateien werden auch auf dem lokalen allgemeinen [!INCLUDE[pn_dynamics_crm_online](../../includes/pn-dynamics-crm-online.md)] Common Data Service für App-Server installiert: `[Install Drive]\Program Files\Microsoft Dynamics CRM\Server\ApplicationFiles`  
  
[!INCLUDE[cc_sdk_onpremises_note](../../includes/cc-sdk-onpremises-note.md)] CustomizationsSolution.xsd ist das Schema für die exportierte Lösung. Es enthält Verweise auf andere XSD-Dateien. Alle Dateien müssen sich im selben Ordner befinden.  
  
<a name="BKMK_UseSchemaValidation"></a>   
## <a name="using-schema-validation"></a>Verwenden von Schemaüberprüfung  
 Da die exportierte XML-Datei eine Textdatei ist, können Sie sie mithilfe eines Text-Editors wie [!INCLUDE[pn_Notepad](../../includes/pn-notepad.md)] bearbeiten. Es wird jedoch unbedingt empfohlen, dass Sie eine Anwendung verwenden, die die Überprüfung von XSD-Schemas unterstützt, wie z. B. [!INCLUDE[pn_Visual_Studio](../../includes/pn-visual-studio.md)]. XSD-Überprüfung bietet [!INCLUDE[pn_Visual_Studio](../../includes/pn-visual-studio.md)] <!-- TODO - need to fix this link. The page is not available (or [Visual Studio Express 2012 for Web](http://www.microsoft.com/visualstudio/eng/products/visual-studio-express-for-web))--> Schemaüberprüfung, Informationen in [!INCLUDE[pn_IntelliSense](../../includes/pn-intellisense.md)], um Fehler zu vermeiden.  
  
 Die XCD-Schemadateien, die verwendet werden, um die Datei customizations.xml in einer Lösung zu validieren, stehen unter  zur Verfügung. [!INCLUDE[schema_download](../../includes/schema-download.md)]. Stellen Sie sicher, dass Sie alle Dateien aus diesem Ordner in dasselbe Verzeichnis kopieren. Sie müssen die Datei customizations.xml mit der Datei CustomizationsSolution.xsd verknüpfen. Diese Datei enthält Verweise auf alle anderen XSD-Dateien im Ordner.  
  
1. Laden Sie die XSD-Schemadateien herunter und kopieren Sie alle auf Ihren Computer. Speichern Sie diese an dem Ort, den [!INCLUDE[pn_Visual_Studio](../../includes/pn-visual-studio.md)] für XSD-Überprüfungsdateien verwendet. Dieser Speicherort ist wahrscheinlich `[install drive]\Program Files (x86)\Microsoft Visual Studio X.0\Xml\Schemas`, wobei `X` auf die [!INCLUDE[pn_Visual_Studio_short](../../includes/pn-visual-studio-short.md)]-Version verweist.  
  
2. Klicken Sie mit der rechten Maustaste auf die Datei customizations.xml; wählen Sie **Öffnen mit**, und wählen Sie dann die Version von [!INCLUDE[pn_Visual_Studio_short](../../includes/pn-visual-studio-short.md)] aus.  
  
3. Wählen Sie **Ansicht** und anschließend **Eigenschaftenfenster** aus.  
  
4. Klicken Sie im Fenster **Eigenschaften** im Feld **Schemas** auf die Schaltfläche mit den Auslassungszeichen [**...**].  
  
5. Im Dialogfeld **Xml-Schemas** sollte die Datei customizationsSolution.xsd angezeigt werden. Wählen Sie in der Spalte **Verwenden** die Option **Dieses Schema verwenden** aus.  
  
   > [!NOTE]
   >  Wenn sie es nicht finden können, klicken Sie auf **Hinzufügen** und navigieren Sie zu dem Speicherort, an dem Sie es gespeichert haben.  
  
6. Klicken Sie auf **OK**.  
  
   Nun können damit beginnen, die XML-Datei mit XSD-Überprüfung zu bearbeiten.  
  
### <a name="see-also"></a>Siehe auch

[Wann die Anpassungsdatei bearbeitet ist für Common Data Service für Apps](when-edit-customization-file.md)<br/> 
[Menüband-Core-Schema](ribbon-core-schema.md)<br/>
[Menübandtypenschema](ribbon-types-schema.md)<br/>
[Menüband-WSS-Schema](ribbon-wss-schema.md)<br/>
[SiteMap-Schema](/dynamics365/customer-engagement/developer/customize-dev/sitemap-schema)<br/>   <!-- TODO need to fix link relevant to the topic in powerapps repo-->
[Formular-XML-Schema](form-xml-schema.md)     
[ISV-Konfigurationsdateischema](/dynamics365/customer-engagement/developer/customize-dev/isv-configuration-file-schema)<br/>   <!-- TODO need to fix link relevant to the topic in powerapps repo-->
[Abfragen erstellen mit FetchXML](/dynamics365/customer-engagement/developer/org-service/build-queries-fetchxml) <!-- TODO need to fix link relevant to the topic in powerapps repo-->
