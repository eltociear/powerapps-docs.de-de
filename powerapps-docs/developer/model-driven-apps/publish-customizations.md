---
title: Veröffentlichen von Anpassungen (modellgestützte Apps) | Microsoft Docs
description: Das Veröffentlichen von Anpassungen macht die Webanwendung auf Änderungen an den Daten aufmerksam, die sich auf die Benutzeroberfläche auswirken.
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
ms.openlocfilehash: 27809198af9348b246dd7d0c2a5401880c13eb73
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748442"
---
# <a name="publish-customizations"></a>Veröffentlichen von Anpassungen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/publish-customizations -->

Das Veröffentlichen von Anpassungen macht die Webanwendung auf Änderungen an den Daten aufmerksam, die sich auf die Benutzeroberfläche auswirken.  
  
<a name="BKMK_WhenToPublishCustomizations"></a>   
## <a name="when-to-publish-customizations"></a>Gründe für das Veröffentlichen von Anpassungen  
 Anpassungen werden automatisch veröffentlicht, wenn neue Elemente erstellt oder vorhandene Elemente gelöscht werden.  
  
 Sie müssen Änderungen veröffentlichen, nachdem Sie Schemametadaten oder Entitäten aktualisiert haben, die sich auf die Benutzeroberfläche auswirken. Sie können auch warten, um eine Menge von zugehörigen Änderungen zusammen zu veröffentlichen.  
  
 Mit einer Lösung werden nur veröffentlichte Anpassungen exportiert. Sie sollten Anpassungen immer veröffentlichen, bevor Sie eine Lösung exportieren.  
  
 Wenn Sie Anpassungen ausführen, die in Dynamics 365 for tablets erscheinen, sollten Sie Ihre Anpassungen immer explizit veröffentlichen, um sicherzustellen, dass jedes Element mit der Dynamics 365 for tablets-Anwendung synchronisiert wird.  
  
> [!NOTE]
>  Das Veröffentlichen von Anpassungen kann sich auf den normalen Systembetrieb auswirken. In einer Produktionsumgebung wird empfohlen, die Veröffentlichung von Anpassungen für einen Zeitraum zu planen, in dem sich möglichst wenig Unterbrechungen für Benutzer ergeben.  
  
## <a name="publishing-programmatically"></a>Programmgesteuertes Veröffentlichen  
 Die folgende Tabelle enthält die beiden Nachrichten, die Sie verwenden können, um Anpassungen zu veröffentlichen.  
  
|Meldung|Beschreibung|  
|-------------|-----------------|  
|<xref:Microsoft.Crm.Sdk.Messages.PublishAllXmlRequest>|Veröffentlicht alle Anpassungen|  
|<xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest>|Veröffentlicht die angegebenen Anpassungen.|  
  
 Wenn Sie die Meldung `PublishXmlRequest` verwenden, geben Sie an, welche Elemente Sie veröffentlichen möchten, indem Sie den Parameter <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest.ParameterXml> verwenden. `ParameterXML` muss dem [Veröffentlichungs-Anforderungsschema](publish-request-schema.md) entsprechen.  
  
<a name="BKMK_RetrieveUnpublishedMetadata"></a>   
## <a name="retrieving-unpublished-metadata"></a>Abrufen von nicht veröffentlichten Metadaten  
 Wenn Sie eine Anwendung erstellen möchten, um anpassbare Elemente in modellgestützten Apps zu bearbeiten, müssen Sie alle nicht veröffentlichten Definitionen dieser Elemente abrufen. Wenn ein Entwickler Änderungen definiert, sie jedoch nicht veröffentlicht, muss die Anwendung in der Lage sein, sie abzurufen, um sie in der Benutzeroberfläche anzuzeigen. 
  
 Verwenden Sie die folgenden zwei Möglichkeiten, um nicht veröffentlichte Metadaten abzurufen:  
  
 **Parameter RetrieveAsIfPublished**  
 Ruft Entitäts-, Attributs-, Entitätsbeziehungs- und Optionssatzdaten mithilfe der folgenden Meldungen ab:  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest>  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllOptionSetsRequest>  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest>  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest>  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveOptionSetRequest>  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRelationshipRequest>  
  
  **RetrieveUnpublished-Anforderung**  
  Ruft Benutzeroberflächenelemente, wie beispielsweise Formular-, Vorlagen-, Visualisierungs- und Webressourcendefinitionen, mithilfe der folgenden Meldungen ab:  
  
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveUnpublishedRequest>  
  
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveUnpublishedMultipleRequest>  
  
### <a name="see-also"></a>Siehe auch  
 [Anpassen modellgestützter Apps](/dynamics365/customer-engagement/developer/customize-dev/customize-applications)<br/>
 [Erweitern des Metadatenmodells](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)<br/>
 [Veröffentlichen des Anforderungsschemas](publish-request-schema.md)<br/>
 [Anpassen von Entitätsformularen](customize-entity-forms.md)<br/>
 [Anpassen von Entitätsansichten](customize-entity-views.md)<br/>
 [Anpassen von globalen Optionssätzen](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)<br/>
 [Anwendungsnavigation mithilfe von SiteMap ändern](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap)

