---
title: Designüberlegungen für modellgetriebene App-Hauptformulare mit PowerApps | MicrosoftDocs
description: 'Hier erfahren Sie, wie Sie Hauptformulare entwickeln'
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: a83872f4-9e36-413b-8561-41a1e5ffe5dd
caps.latest.revision: 17
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="design-considerations-for-model-driven-app-main-forms"></a>Designüberlegungen für modellgesteuerte App-Hauptformulare

Hauptformulare sind die Hauptbenutzerschnittstelle, auf der Personen Daten anzeigen und damit interagieren. Hauptformulare bieten die größte Auswahl an Optionen und sind für modellgetriebene Anwendungen verfügbar, mit Ausnahme von Dynamics 365 for phones.  
  
 Zu den wichtigsten Designzielen der Hauptformulare gehört, dass sie einmal entworfen und überall bereitgestellt werden. Das gleiche Hauptformular, das Sie für eine modellgetriebene App entwerfen, wird auch in Dynamics 365 for Outlook und Dynamics 365 für Tablets verwendet. Der Vorteil für dieses Ansatzes ist, dass Sie Änderungen nicht in drei verschiedenen Formularen integrieren müssen. Allerdings gibt es beim Entwickeln dieser Formulare einige wichtige Faktoren zu berücksichtigen.  
  
<a name="BKMK_CustomFormsForGroups"></a>   

## <a name="custom-forms-for-different-groups"></a>Benutzerdefinierte Formulare für verschiedene Gruppen  
 Da Sie mehrere Hauptformulare erstellen und unterschiedliche Sicherheitsrolle für jedes Formular zuweisen können, können Sie anderen Gruppen in der Organisation ein Formular präsentieren, das für die Art optimiert ist, wie sie die Anwendung verwenden. Sie können jeder Gruppe verschiedene Optionen zur Verfügung stellen, sodass sie unter verschiedenen Formularen wählen können. Weitere Informationen: [Steuern des Zugriffs auf Formulare](control-access-forms.md)  
  
 Sie können erwarteten, dass Manager und Entscheidungsträger Formulare benötigen, die für eine schnelle Übersicht zu den wichtigsten Datenpunkten optimiert sind. Diese möchten möglicherweise eher Diagramme als Listen sehen und führen wahrscheinlich nicht viel Dateneingabe durch.  
  
 Benutzer, die direkt mit Kunden interagieren, benötigen Formulare, die für die Aufgaben angepasst sind, die sie am häufigsten ausführen. Sie wünschen Formulare, die eine effiziente Dateneingabe ermöglichen.  
  
 Sie müssen ermitteln, was die Personen in der Organisation verwenden möchten und benötigen. Dies ist oft ein iterativer Prozess, bei dem Sie Input sammeln, verschiedene Dinge ausprobieren, und Formulare entwickeln, die Benutzer verwenden können. Beachten Sie, dass Sie über eine Reihe von Tools verfügen,und dass nicht alles im Formular ausgeführt werden muss. Verwenden Sie Unternehmensregeln, Workflowprozesse, Dialogfelder und Geschäftsprozessflüsse zusammen mit den Formulare, um eine Lösung bereitzustellen, die für die Organisation funktioniert.  
  
 Sie müssen dieses mit der Zeit ausgleichen, die Sie zum Verwalten von Formularen möchten. Formulare zu erstellen und zu bearbeiten ist relativ einfach, aber wenn Sie mehr Formulare erstellen, müssen Sie mehr Formulare verwalten.  
  
<a name="BKMK_PresentationDifferences"></a>   
## <a name="presentation-differences"></a>Präsentationsunterschiede  
 Obwohl Sie nicht für jede Präsentation mehrere Formulare verwalten müssen, müssen Sie überlegen, wie Unterschiede in der Darstellung im Hauptformular berücksichtigt werden können. [Hauptformularpräsentationen](main-form-presentations.md) beschreibt die verschiedenen Arten, in denen das Hauptformular dargestellt werden kann. Die wichtigsten zu berücksichtigenden Dinge sind:  
  
- Dynamics 365 for tablets unterstützt nicht das Hinzufügen von Bild, HTML oder Silverlight-Webressourcen zu Formularen.  
  
-   Das Layout von Dynamics 365 for tablets-Formularen wird auf dem Hauptformular basierend automatisch generiert. Es gibt keinen speziellen Formular-Editor für Dynamics 365 for tablets-Formulare. Sie müssen überprüfen, ob die Formularpräsentation für beide Clients funktioniert.  
  
-   Wenn Sie über nicht unterstützte Skripts haben, die mit DOM-Elementen interagieren, die in der Webanwendung vorhanden sind, werden diese nicht in Dynamics 365 for tablets-Formularen funktionieren, da die gleichen DOM-Elemente nicht verfügbar sind.  
  
- Dynamics 365 for Outlook-Lesebereichsformulare erlauben kein Skripting. Die Sichtbarkeit von Formularelementen hängt von den Standardeinstellungen ab und kann nicht zur Laufzeit mithilfe von Skripts geändert werden.  
  
<a name="BKMK_FormPerformance"></a>   
## <a name="form-performance"></a>Formularleistung  
 Formulare, die langsam geladen werden oder nicht schnell reagieren, wirken sich mit Sicherheit auf die Produktivität und die Annahme der App durch die Benutzer aus. [Optimieren der Formularleistung](optimize-form-performance.md) bietet eine Reihe von Empfehlungen, die Sie berücksichtigen sollten, wenn Sie Formulare entwerfen, sodass sich Anpassungen nicht negativ auf die Formularleistung auswirken.  
  
### <a name="next-steps"></a>Nächste Schritte 
 [Erstellen und Gesalten von Formularen](create-design-forms.md)    
 [Erstellen und Bearbeiten von Schnellerstellungsformularen](create-edit-quick-create-forms.md)   

 
