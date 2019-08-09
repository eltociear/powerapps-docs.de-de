---
title: Datenanalyse mit Dashboards (modellgesteuerte Anwendungen) | Microsoft Docs
description: 'Die Dashboardentitäten in Dynamics 365 Common Data Service ermöglichen Ihnen, Daten aus verschiedenen Diagrammen, Rastern, IFRAMES oder Webressourcen gleichzeitig anzuzeigen. Dashboards erlauben Ihnen, verschiedene Kundeninformation zu vergleichen und zu analysieren, und sie geben Ihnen Datenmomentaufnahmen.'
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 4b54597b-5603-2e6e-4630-bc120f711707
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

# <a name="analyze-data-with-dashboards"></a>Analysieren von Daten mit Dashboards

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/analyze-data-with-dashboards -->

Die Dashboardentitäten in Common Data Service ermöglichen Ihnen, Daten aus verschiedenen Diagrammen, Rastern, IFRAMES oder Webressourcen gleichzeitig anzuzeigen. Dashboards erlauben Ihnen, verschiedene Kundeninformation zu vergleichen und zu analysieren, und sie geben Ihnen Datenmomentaufnahmen.  
  
## <a name="types-of-dashboards"></a>Dashboardtypen  
Es stehen zwei Arten von Dashboards zur Verfügung: Dashboards im Besitz der Organisation und Dashboards im Besitz des Benutzers.  
  
**Dashboard im Besitz der Organisation.**

Ein Dashboard im Besitz der Organisation wird durch die `SystemForm`-Entität dargestellt und kann nicht zugewiesen oder freigegeben werden. Diese Dashboards sind lösungfähige Entitäten. Wenn Sie einen Aktualisierungsvorgang für diese Entität ausführen, müssen Sie die Änderungen veröffentlichen, damit die Updates in der gesamten Organisation verfügbar sind. Wenn Sie Anpassungen mithilfe der <xref:Microsoft.Crm.Sdk.Messages.PublishAllXmlRequest>-Nachricht veröffentlichen, werden die neu erstellten Dashboards im Besitz der Organisation ebenfalls veröffentlicht und werden in der gesamten Organisation verfügbar. Alternativ können Sie die Änderungen veröffentlichen, die an einem bestimmten Dashboard vorgenommen wurden, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest>-Nachricht verwenden, und die Dashboard-ID als Parameter in der Anforderungsnachricht angeben.  
  
**Dashboards im Besitz des Benutzers.**

Ein Dashboard im Besitz des Benutzers wird durch die `UserForm`-Entität dargestellt, kann anderen Benutzern zugewiesen und für diese freigegeben werden, und kann von anderen Benutzern abhängig von den Zugriffsrechten des Dashboards angezeigt werden.  
  
> [!NOTE]
> Sie können die neuen interaktiven Dashboards nicht programmgesteuert erstellen oder verwalten. Informationen zum Arbeiten mit interaktiven Dashboards mithilfe des Webclients finden Sie unter [Konfigurieren von Dashboards für interaktive Funktionen](../../maker/model-driven-apps/configure-interactive-experience-dashboards.md). 
  
### <a name="see-also"></a>Siehe auch  
 [Nutzung der FormXML-Datei für Dashboards](understand-dashboards-dashboard-components-formxml.md)   
 [Aktionen für Dashboards](actions-dashboards.md)   
 [Erstellen eines Dashboards](create-dashboard.md)   
 [Beispiel-Dashboards](sample-dashboards.md)   
 [Dashboardentitäten](/dynamics365/customer-engagement/developer/customize-dev/dashboard-entities)   <!-- TODO: Need to find the topic in powerapps repo to link-->
 [Beispiel: Ein Dashboard erstellen, abrufen, aktualisieren und löschen (EAAL)](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-dashboard) <!-- TODO: Need to find the topic in powerapps repo to link-->  
 [Beispiel: Zuweisen eines Dashboards im Besitz eines Benutzers an einen anderen Benutzer](/dynamics365/customer-engagement/developer/customize-dev/sample-assign-user-owned-dashboard-another-user)  <!-- TODO: Need to find the topic in powerapps repo to link--> 
 [Visualisierungsdaten-Beschreibungsschema](visualization-data-description-schema.md)     
 [Anpassen von Visualisierungen und Dashboards](customize-visualizations-dashboards.md)
