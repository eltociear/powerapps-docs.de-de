---
title: Aktionen für Dashboards (modellgesteuerte Anwendungen) | Microsoft Docs
description: Erfahren Sie, wie die Aktionen wie Erstellen, Abrufen, Aktualisieren oder Löschen für Dashboards im Besitz der Organisation und im Besitz des Benutzers auszuführen.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 339eb79d-5dec-885b-496f-bfa26e9cae08
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fdb1fc5ceb8ec5ead1b5e43bc79e500de0f6a39a
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276134"
---
# <a name="actions-on-dashboards"></a>Aktionen für Dashboards

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/actions-dashboards -->

Sie können fAktionen ausführen, wie Dashboards im Besitz der Organisation und im Besitz des Benutzers erstellen, abrufen, aktualisieren oder löschen.  
  
## <a name="actions-on-an-organization-owned-dashboard"></a>Aktionen für ein Dashboard im Besitz der Organisation  
 Damit Sie die folgenden Aktionen für ein Dashboard im Besitz der Organisation (`SystemForm`) ausführen können, muss Ihrem Konto in Common Data Service die Rolle "Systemadministrator" oder "Systemanpasser" zugewiesen sein:  
  
- Erstellen, Abrufen, Aktualisieren und Löschen. Sie können ein Dashboard im Besitz der Organisation erstellen oder aktualisieren, indem Sie die Common Data Service-Webdienste verwenden oder das Entitätsformular anpassen. Weitere Informationen zum Erstellen eines Systemdashboards finden Sie unter [Erstellen eines Dashboards](create-dashboard.md).  
  
- Legen Sie ein Dashboards im Besitz der Organisation als Standarddashboard für eine Organisation fest, indem Sie beim Erstellen oder Aktualisieren des Dashboards den Attributwert `SystemForm.IsDefault` auf `true` festlegen.  
  
  > [!IMPORTANT]
  >  Mithilfe der Methoden, die in Common Data Service-Webdiensten verfügbar sind, ist es möglich, zwei Dashboards als Standarddashboard festlegen. Stellen Sie sicher, dass kein anderes Dashboard als Standarddashboard für die Organisation festgelegt wurde, bevor Sie diese Einstellung programmgesteuert festlegen.  
  
  Nachdem Sie ein organisationseigenes Dashboard aktualisiert haben, müssen Sie die Metadatenänderungen veröffentlichen, damit sie organisationsweit zu sehen sind. Sie können die Meldung <xref:Microsoft.Crm.Sdk.Messages.PublishAllXmlRequest> oder die Meldung <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest> verwenden, um die Änderungen zu veröffentlichen, die für ein organisationseigenes Dashboard vorgenommen wurden. Einen Beispielcode, der dies darstellt, finden Sie unter [Beispiel: Ein Dashboard erstellen, abrufen, aktualisieren und löschen (EAAL)](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-dashboard).<!-- TODO Need to update the powerapps repo's topic link. As of now not found-->.  
  
  Eine Liste der unterstützten Meldungen für die organisationseigene Dashboardentität finden Sie unter [SystemForm Entity](../common-data-service/reference/entities/systemform.md).  
  
## <a name="actions-on-a-user-owned-dashboard"></a>Aktionen für ein Dashboard im Besitz des Benutzers  
 Sie können die folgenden Schritte für ein Dashboard im Besitz des Benutzers (`UserForm`) ausführen:  
  
- Erstellen, Abrufen, Aktualisieren und Löschen. Weitere Informationen zum Erstellen eines Systemdashboards im Besitz des Benutzers finden Sie unter [Erstellen eines Dashboards](create-dashboard.md).  
  
- Ändern Sie den Besitzer eines Benutzerdashboards, indem Sie es mithilfe der Meldung <xref:Microsoft.Crm.Sdk.Messages.AssignRequest> einem anderen Benutzer oder Team zuweisen.  
  
- Rufen Sie die Zugriffsrechte ab, über die der angegebene Sicherheitsprinzipal (Benutzer oder Team) für ein Dashboard im Besitz des Benutzers verfügt, indem Sie die Meldung <xref:Microsoft.Crm.Sdk.Messages.RetrievePrincipalAccessRequest> verwenden. Sie können auch alle Sicherheitsprinzipale (Benutzer oder Teams), die über Zugriff auf ein Dashboard im Besitz des Benutzers verfügen, zusammen mit ihren Zugriffsrechten für das Benutzerdashboard abrufen, indem Sie die Meldung <xref:Microsoft.Crm.Sdk.Messages.RetrieveSharedPrincipalsAndAccessRequest> verwenden.  
  
- Arbeiten Sie mit anderen Benutzern und Teams in bestimmten Bereichen zusammen, indem Sie ein Dashboard im Besitz des Benutzers mithilfe der Meldungen <xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest>, <xref:Microsoft.Crm.Sdk.Messages.ModifyAccessRequest> und <xref:Microsoft.Crm.Sdk.Messages.RevokeAccessRequest> freigeben.  
  
  Eine Liste der unterstützten Meldungen für die benutzereigene Dashboardentität finden Sie unter [UserForm Entity](../common-data-service/reference/entities/userform.md).  
  
### <a name="see-also"></a>Siehe auch  

 [Dashboards für Microsoft Dynamics 365](analyze-data-with-dashboards.md)   
 [Nutzung der FormXML-Datei für Dashboards](understand-dashboards-dashboard-components-formxml.md)   
 [Erstellen eines Dashboards](create-dashboard.md)   
 [Beispiel-Dashboards](sample-dashboards.md)   
 [Dashboardentitäten](/dynamics365/customer-engagement/developer/customize-dev/dashboard-entities) <!-- TODO Need to update the powerapps repo's topic link. As of now not found-->  
 [Beispiel: Ein Dashboard erstellen, abrufen, aktualisieren und löschen (EAAL)](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-dashboard) <!-- TODO Need to update the powerapps repo's topic link. As of now not found-->   
 [Beispiel: Zuweisen eines Dashboards im Besitz eines Benutzers an einen anderen Benutzer](/dynamics365/customer-engagement/developer/customize-dev/sample-assign-user-owned-dashboard-another-user) <!-- TODO Need to update the powerapps repo's topic link. As of now not found-->