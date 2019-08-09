---
title: Aktionen bei Visualisierungen (Diagramme) (modellgetriebene Anwendungen) | Microsoft Docs
description: Mit Common Data Service-Webdiensten können Sie folgende Aktionen in den Visualisierungsentitäten ausführen.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: c7eb3bdf-9d6f-9bcc-8114-4c3dc5be2976
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

# <a name="actions-on-visualizations-charts"></a>Aktionen für Visualisierungen (Diagramme)

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/actions-visualizations-charts -->

Mit Common Data Service-Webdiensten können Sie folgende Aktionen in den Visualisierungsentitäten ausführen.  
  
## <a name="actions-on-organization-owned-visualizations"></a>Aktionen für Visualisierungen im Besitz der Organisation  
 Um Aktionen für eine Visualisierung im Besitz der Organisation auszuführen (`SavedQueryVisualization`), müssen Sie über die Rolle "Systemadministrator" oder "Systemanpasser" verfügen. Sie können die folgenden Aktionen für eine Visualisierung im Besitz der Organisation ausführen:  
  
- Eine Visualisierung im Besitz der Organisation erstellen, abrufen, aktualisieren und löschen. Weitere Informationen: [Visualisierung erstellen](create-visualization-chart.md)  
  
  > [!NOTE]
  >  Nach der Aktualisierung einer Visualisierung im Besitz der Organisation müssen Sie die Metadatenänderungen veröffentlichen, um sie mithilfe der <xref:Microsoft.Crm.Sdk.Messages.PublishAllXmlRequest>-Nachricht in der ganzen Organisation sichtbar zu machen. Alternativ hierzu werden auch beim Veröffentlichen einer Entität alle nicht veröffentlichten Visualisierungen im Besitz der Organisation, die mit der Entität verknüpft sind, automatisch veröffentlicht.  
  
- Mit dem `SavedQueryVisualization.PrimaryEntityTypeCode`-Attribut können Sie alle Visualisierungen im Besitz der Organisation, die an eine Entität angefügt sind, abfragen und abrufen. Mehrere Visualisierungen im Besitz der Organisation können an eine einzelne Entität angefügt werden. Eine Liste der Entitäten, an die Sie eine Visualisierung anhängen können, finden Sie unter [Für Visualisierungen unterstützte Entitäten](view-data-with-visualizations-charts.md#SupportedVisualizationEntities). Ein Codebeispiel, das veranschaulicht, wie Sie alle Visualisierungen im Besitz der Organisation abrufen, die an eine Entität angefügt wurden, finden Sie unter [Beispiel: Alle an eine Entität angefügten Diagramme abrufen](/dynamics365/customer-engagement/developer/customize-dev/sample-retrieve-all-charts-attached-entity).
  
  > [!NOTE]
  >  Sie können keine Visualisierung ändern oder aktualisieren, um sie einer anderen Entität anzufügen, nachdem Sie die Visualisierung erstellt haben. Da bedeutet, dass das `SavedQueryVisualization.PrimaryEntityTypeCode`-Attribut nicht gültig ist, um die Visualisierung im Besitz der Organisation zu aktualisieren.
  
- Geben Sie eine Visualisierung im Besitz der Organisation als die Standardvisualisierung für die zugeordnete Entität an, indem Sie das `SavedQueryVisualization.IsDefault`-Attribut auf `true` festlegen. Wenn Sie eine Visualisierung im Besitz der Organisation als die Standardvisualisierung für eine Entität festlegen, dann wird die Visualisierung standardmäßig angezeigt, wenn Sie festlegen, die Visualisierungen für diese Entität in Common Data Service anzuzeigen.
  
  > [!NOTE]
  >  Wenn Sie unter Verwendung von Common Data Service-Webdiensten eine Visualisierung im Besitz der Organisation als Standard für eine Entität festlegen, für die bereits eine andere Visualisierung als Standard festgelegt wurde, dann werden beide Visualisierungen als Standardvisualisierungen für die Entität gekennzeichnet.  Um eine Visualisierung als Standardvisualisierung für eine Entität festzulegen, müssen Sie sicherstellen, dass keine Visualisierung als Standardvisualisierung für die Entität festgelegt ist.  
  
  Eine Liste der unterstützten Meldungen für die organisationseigene Visualisierungsentität finden Sie unter [SavedQueryVisualization-Entität](../common-data-service/reference/entities/savedqueryvisualization.md).
  
## <a name="actions-on-user-owned-visualizations"></a>Aktionen für Visualisierungen im Besitz des Benutzers  
 Sie können die folgenden Aktionen für eine Visualisierung im Besitz des Benutzers (`UserQueryVisualization`) ausführen:  
  
- Eine Visualisierung im Besitz des Benutzers erstellen, abrufen, aktualisieren und löschen. Weitere Informationen: [Visualisierung erstellen](create-visualization-chart.md)  
  
- Mit dem `UserQueryVisualization.PrimaryEntityTypeCode`-Attribut können Sie alle Visualisierungen im Besitz des Benutzers, die an eine Entität angefügt sind, abfragen und abrufen. Mehrere Visualisierungen im Besitz des Benutzers können an eine Entität angefügt werden. Eine Liste der Entitäten, an die Sie eine Visualisierung anhängen können, finden Sie unter [Für Visualisierungen unterstützte Entitäten](view-data-with-visualizations-charts.md#SupportedVisualizationEntities).  
  
  > [!NOTE]
  >  Sie können keine Visualisierung ändern oder aktualisieren, um sie einer anderen Entität anzufügen, nachdem Sie die Visualisierung erstellt haben. Da bedeutet, dass das `UserQueryVisualization.PrimaryEntityTypeCode`-Attribut nicht gültig ist, um die Visualisierung im Besitz des Benutzers zu aktualisieren.
  
- Den Besitz an einer Visualisierung im Besitz des Benutzers ändern, indem Sie die Visualisierung einem anderen Benutzer oder Team mithilfe von <xref:Microsoft.Crm.Sdk.Messages.AssignRequest> zuweisen.  
  
- Mithilfe von <xref:Microsoft.Crm.Sdk.Messages.RetrievePrincipalAccessRequest> den Zugriff abrufen, über den der angegebene Sicherheitsprinzipal (Benutzer oder Team) für eine Visualisierung im Besitz des Benutzers verfügt. Mit <xref:Microsoft.Crm.Sdk.Messages.RetrieveSharedPrincipalsAndAccessRequest> können Sie auch alle Sicherheitsprinzipale (Benutzer oder Teams), die über einen Zugriff auf eine Visualisierung im Besitz des Benutzers verfügen, zusammen mit ihren Zugriffsrechten für die Visualisierung im Besitz des Benutzers abrufen.  
  
- Zusammenarbeiten mit anderen Benutzern und Teams in bestimmten Bereichen, indem Sie eine Visualisierung im Besitz des Benutzers mithilfe von <xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest>, <xref:Microsoft.Crm.Sdk.Messages.ModifyAccessRequest> und <xref:Microsoft.Crm.Sdk.Messages.RevokeAccessRequest> freigeben.  
  
  Eine Liste der unterstützten Meldungen für die benutzereigene Visualisierungsentität finden Sie unter [UserQueryVisualization-Entität](../common-data-service/reference/entities/userqueryvisualization.md).

### <a name="see-also"></a>Siehe auch  
 [Diagramme](view-data-with-visualizations-charts.md)   
 [Diagramme verstehen: Zugrunde liegende Daten und Diagrammdarstellung](understand-charts-underlying-data-chart-representation.md)   
 [Erstellen eines Diagramms](create-visualization-chart.md)   
 [Beispieldiagramme](sample-charts.md)   
 [Beispiel: Erstellen, Abrufen, Aktualisieren und Löschen (CRUD) eines Diagramms](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-chart)  <!--TODO: Need to find the topic in Powerapps repo to link --> 
 [Beispiel: Abrufen aller Diagramme, die an eine Entität angehängt sind](/dynamics365/customer-engagement/developer/customize-dev/sample-retrieve-all-charts-attached-entity)   <!--TODO: Need to find the topic in Powerapps repo to link -->
 [Beispiel: Zuweisen eines Diagramms zu einem anderen Benutzer](/dynamics365/customer-engagement/developer/customize-dev/sample-assign-chart-another-user)   <!--TODO: Need to find the topic in Powerapps repo to link -->
 [SavedQueryVisualization-Entität](../common-data-service/reference/entities/savedqueryvisualization.md)   
 [UserQueryVisualization-Entität](../common-data-service/reference/entities/userqueryvisualization.md)