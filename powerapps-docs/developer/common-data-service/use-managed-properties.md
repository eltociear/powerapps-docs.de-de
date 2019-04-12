---
title: Verwaltete Eigenschaften nutzen (Common Data Service) | Microsoft Docs
description: 'Mit verwalteten Eigenschaften können Sie definieren, welche der verwalteten Lösungskomponenten anpassbar sind.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-managed-properties"></a>Verwaltete Eigenschaften nutzen

Sie können steuern, welche der von Ihnen verwalteten Lösungskomponenten mithilfe von verwalteten Eigenschaften anpassbar sind. Sie sollten so viele Anpassungen wie möglich für diejenigen Lösungskomponenten zulassen, die Geschäftsentitäten repräsentieren. Damit können Organisationen Ihre Lösung entsprechend ihren Anforderungen anpassen. Schränken Sie Anpassung von kritischen Lösungskomponenten, die die Kernfunktionen Ihrer Lösung sicherstellen ein oder lassen Sie diese nicht zu, sodass Sie diese vorhersagbar unterstützen und verwalten können.  
  
 Verwaltete Eigenschaften dienen dazu, Ihre Lösung vor Änderungen zu schützen, die möglicherweise die Funktion unterbrechen. Verwaltete Eigenschaften bieten keine digitale Rechteverwaltung (DRM) oder Möglichkeiten, Ihre Lösung oder Steuerung, die Sie installieren, zu lizenzieren.  
  
## <a name="apply-managed-properties"></a>Verwaltete Eigenschaften anwenden  
 Sie wenden verwaltete Eigenschaften an, wenn die Lösung nicht verwaltet ist. Die verwalteten Eigenschaften werden erst nach dem Packen und der Installation der verwalteten Lösung in einer anderen Organisation wirksam. Nachdem die verwaltete Lösung installiert ist, können verwaltete Eigenschaften nicht mehr aktualisiert werden, außer durch eine Aktualisierung durch den ursprünglichen Herausgeber.  
  
 Die meisten Lösungskomponenten verfügen über eine Schaltfläche **Verwaltete Eigenschaften**, wenn eine Liste der Lösungskomponenten angezeigt wird. Sie können die verwalteten Eigenschaften für eine Lösungskomponente anzeigen oder aktualisieren, wenn Sie auf diese Schaltfläche klicken. Wenn Sie auf verwaltete Eigenschaften für Lösungen zugreifen, die auf dieser Schaltfläche nicht angezeigt werden, klicken Sie auf **Verwaltete Eigenschaften** in der Dropdownliste und wählen **Weitere Aktionen**.  
  
 Standardmäßig sind alle benutzerdefinierten Lösungskomponenten anpassbar. Um die verwalteten Eigenschaften für eine Lösungskomponente zu ändern, klicken Sie auf die Schaltfläche **Verwaltete Eigenschaften** in der Symbolleiste für die Lösungskomponente. Alle Lösungskomponenten verfügen über die Eigenschaft **Kann angepasst werden** (`IsCustomizable`). Solange diese Eigenschaft zutrifft, können aber auch weitere Eigenschaften, die auf die Lösungskomponente zutreffen, definiert werden. Wenn Sie die `IsCustomizable.Value`-Eigenschaft auf falsch setzen, nachdem die Lösung als verwaltete Lösung installiert wurde, kann die Lösungskomponente nicht mehr angepasst werden. Die folgende Tabelle enthält die verwalteten Eigenschaften für eine Lösungskomponente.  
  
|Komponente|Name anzeigen|Eigenschaft|  
|---------------|------------------|--------------|  
|Entity|Kann angepasst werden|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsCustomizable>.                                 `Value`|  
|Entity|Anzeigename kann geändert werden|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsRenameable>.                              `Value`|  
|Entity|Kann verknüpfte Entität in Beziehung sein|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanBeRelatedEntityInRelationship>.                                 `Value` (Schreibgeschützt)|  
|Entity|Kann primäre Entität in Beziehung sein|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanBePrimaryEntityInRelationship>.                                 `Value` (Schreibgeschützt)|  
|Entity|Kann in viele-zu-viele-Beziehung sein|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanBeInManyToMany>.                               `Value` (Schreibgeschützt)|  
|Entity|Neue Formulare können erstellt werden|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanCreateForms>.                              `Value`|  
|Entity|Neue Diagramme können erstellt werden|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanCreateCharts>.                               `Value`|  
|Entity|Neue Ansichten können erstellt werden|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanCreateViews>.                              `Value`|  
|Entity|Kann alle anderen Entitätseigenschaften ändern, die nicht in einer verwalteten Eigenschaft vorkommen.|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanModifyAdditionalSettings>.                                `Value`|  
|Feld (Attribut)|Kann angepasst werden|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.IsCustomizable>.                                 `Value`|  
|Feld (Attribut)|Anzeigename kann geändert werden|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.IsRenameable>.                              `Value`|  
|Feld (Attribut)|Kann Erforderlichkeitsstufe ändern|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.RequiredLevel>.                                `CanBeChanged`<br /><br /> Hinweis:<br /><br /> `RequiredLevel` ist die einzige verwaltete Eigenschaft, die die `CanBeChanged`-Eigenschaft verwendet.|  
|Feld (Attribut)|Kann alle anderen Entitätseigenschaften ändern, die nicht in einer verwalteten Eigenschaft vorkommen.|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.CanModifyAdditionalSettings>.                                 `Value`|  
|Entitätsbeziehung|Kann angepasst werden|<xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase.IsCustomizable>.                              `Value`|  
|Formular|Kann angepasst werden|`SystemForm.IsCustomizable.Value`|  
|Diagramm|Kann angepasst werden|`SavedQueryVisualization.IsCustomizable.Value`|  
|Ansicht|Kann angepasst werden|`SavedQuery.IsCustomizable.Value`|  
|Optionssatz|Kann angepasst werden|<xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadataBase.IsCustomizable>.                              `Value`|  
|Webressource|Kann angepasst werden|`WebResource.IsCustomizable.Value`|  
|Workflow|Kann angepasst werden|`Workflow.IsCustomizable.Value`|  
|Assembly|Kann angepasst werden|`SdkMessageProcessingStep.IsCustomizable.Value`|  
|Assembly-Registrierung|Kann angepasst werden|`ServiceEndpoint.IsCustomizable.Value`|  
|E-Mail-Vorlage|Kann angepasst werden|`Template.IsCustomizable.Value`|  
|Vorlage für Wissensdatenbankartikel|Kann angepasst werden|`KbArticleTemplate.IsCustomizable.Value`|  
|Vertragsvorlage|Kann angepasst werden|`ContractTemplate.IsCustomizable.Value`|  
|Seriendruckvorlage|Kann angepasst werden|`MailMergeTemplate.IsCustomizable.Value`|  
|Dashboard|Kann angepasst werden|`SystemForm.IsCustomizable.Value`|  
|Sicherheitsrollen|Kann angepasst werden|`Role.IsCustomizable.Value`|  
  
### <a name="update-managed-properties"></a>Verwaltete Eigenschaften bearbeiten  
 Wenn Sie die verwaltete Lösung freigeben, können Sie entscheiden, ob Sie die verwalteten Eigenschaften ändern möchten. Sie können lediglich verwaltete Eigenschaften ändern, damit sie weniger restriktiv sind. Beispielsweise können Sie nach der erstmaligen Freigabe entscheiden, alle Anpassungen einer Entität zuzulassen.  
  
 Aktualisieren Sie verwaltete Eigenschaften für Ihre Lösung, indem Sie eine Aktualisierung Ihrer Lösung mit den veränderten verwalteten Eigenschaften machen. Ihre verwaltete Lösung kann nur über eine andere verwaltete Lösung aktualisiert werden, die demselben Herausgeberdatensatz wie die ursprüngliche verwaltete Lösung zugeordnet ist. Wenn Ihre Aktualisierung eine Änderung in den verwalteten Eigenschaften umfasst, um sie restriktiver zum machen, werden diese verwalteten Eigenschaftenänderungen ignoriert, doch andere Änderungen in der Aktualisierung werden angewendet.  
  
 Weil der Originalherausgeber erforderlich ist, um verwaltete Eigenschaften für eine verwaltete Lösung zu aktualisieren, können keine nicht verwalteten Lösungen einem Herausgeber zugeordnet werden, der dazu verwendet wurde, eine verwaltete Lösung zu installieren.  
  
> [!NOTE]
>  Das bedeutet, dass Sie keine Aktualisierung für Ihre Lösung entwickeln können, indem Sie eine Organisation verwenden, in der die verwaltete Lösung installiert wurde.  
  
## <a name="check-managed-properties"></a>Verwaltete Eigenschaften überprüfen  
 Verwenden Sie <xref:Microsoft.Crm.Sdk.Messages.IsComponentCustomizableRequest>, um zu prüfen, ob die Lösungskomponente anpassbar ist. Alternativ können Sie die Lösungskomponenteneigenschaften überprüfen, doch Sie müssen sicherstellen, dass die ultimative Bestimmung der Bedeutung von Werten mehrerer Eigenschaften abhängt. Jede Lösungskomponente hat eine `IsCustomizable`-Eigenschaft. Wenn einer Lösungskomponente als Teil einer verwalteten Lösung installiert wurde, ist die Eigenschaft `IsManaged` erfüllt. Verwaltete Eigenschaften werden ausschließlich für verwaltete Lösungen erzwungen. Wenn Sie verwaltete Eigenschaften überprüfen, um zu ermitteln, ob eine bestimmte Lösungskomponente anpassbar ist, müssen Sie die `IsCustomizable`- und `IsManaged`-Eigenschaften überprüfen. Eine Lösungskomponente, bei der `IsCustomizable` fehlerhaft ist und `IsManaged` falsch ist, kann angepasst werden.  
  
 Entität und Attribut haben zusätzlich zu `IsCustomizable` weitere verwaltete Eigenschaften. Die verwalteten Eigenschaften werden nicht aktualisiert, wenn `IsCustomizable` falsch ist. Das bedeutet, dass zum Überprüfen der einzelnen verwalteten Eigenschaft die `IsCustomizable`-Eigenschaft überprüft werden muss, um zu sehen, ob die verwaltete Eigenschaft erzwungen wird.  
  
### <a name="see-also"></a>Siehe auch  
 [Verwaltete Eigenschaften](/dynamics365/customer-engagement/developer/introduction-solutions#BKMK_ManagedProperties)   
 [Planen einer Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Pflegen von verwalteten Lösungen](maintain-managed-solutions.md)   
 [Packen und Verteilen von Erweiterungen mithilfe von Dynamics 365-Lösungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 <xref:Microsoft.Crm.Sdk.Messages.IsComponentCustomizableRequest>