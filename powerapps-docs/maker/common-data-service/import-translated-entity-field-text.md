---
title: Übersetzten Entitäts- und Feldtext mit PowerApps importieren | MicrosoftDocs
description: 'Erfahren Sie, wie übersetzter Entitäts- und Feldtext importiert wird'
ms.custom: ''
ms.date: 06/19/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 3d77d149-819b-45e6-8e70-1fbe54d5c153
caps.latest.revision: 19
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="import-translated-entity-and-field-text-back-into-an-app"></a>Importieren von übersetztem Entitäts- und Feldtext zurück in eine App

Wenn Sie Text für Entitäten oder Felder, z. B. Feldbeschriftungen oder Werte in Dropdownlisten, angepasst haben, können Sie den Benutzern in Ihrer Organisation, die nicht die Ausgangssprachversion Ihrer Umgebung verwenden, diesen angepassten Text auch in deren eigenen Sprachen zur Verfügung stellen. Um dies zu tun, exportieren Sie die Textzeichenfolgen für sämtliche Anpassungen, damit sie in die Sprachen übersetzt werden können, die in Ihrer Organisation verwendet werden.  
  
 Nach der Übersetzung müssen Sie die übersetzten Textzeichenfolgen in Ihre Umgebung importieren, bevor Benutzer die Änderungen nutzen können.  
  
> [!IMPORTANT]
> - Die Datei, die Sie importieren, muss eine komprimierte Datei sein, in der die CrmTranslations.xml und die Datei [Content_Types].xml im Stammverzeichnis enthalten ist.  
> - Sie können keinen übersetzten Text mit mehr als 500 Zeichen importieren. Wenn Elemente in Ihrer Übersetzung eine Länge von 500 Zeichen überschreiten, tritt beim Importvorgang ein Fehler auf. Überprüfen Sie bei Auftreten eines Importfehlers die Zeile in der Datei, durch die der Fehler verursacht wurde, verringern Sie die Zeichenanzahl, und führen Sie einen erneuten Importvorgang aus. Beachten Sie ebenfalls, dass Sie nach dem Importieren des übersetzten Texts die Anpassungen erneut veröffentlichen müssen.  
  
1. Öffnen Sie den [Lösungs-Explorer](../model-driven-apps/advanced-navigation.md#solution-explorer).  
  
2. Wählen Sie im Projektmappen-Explorer auf der Aktionssymbolleiste **Übersetzungen importieren** aus.  
3.  Geben Sie im Dialogfeld **Übersetzten Text importieren** die Datei mit dem übersetzten Text an, und wählen Sie dann **Importieren** aus.  
  
4.  Sobald der Import abgeschlossen ist, wählen Sie **Schließen** aus.  
  
> [!NOTE]
>  Das Veröffentlichen von Anpassungen kann sich auf den normalen Systembetrieb auswirken. Wir empfehlen, dass Sie Veröffentlichungen für einen Zeitpunkt planen, wenn dies die Benutzer am wenigsten stört.  

## <a name="community-tools"></a>Community-Tools

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) ist ein Tool, das XrmToolBox-Community für Dynamics 365 Customer Engagement entwickelte. Verwenden Sie den einfachen Übersetzer, um Übersetzungen mit kontextbezogenen Informationen zu exportieren und zu importieren. 

> [!NOTE]
> Die Community-Tools werden von Microsoft nicht unterstützt. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com).

## <a name="next-steps"></a>Nächste Schritte  
 [Exportieren von benutzerdefiniertem Entitäts- und Feldtext zur Übersetzung](export-customized-entity-field-text-translation.md)
