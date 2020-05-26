---
title: Definieren von Menüband-Anzeigeregeln (modellgesteuerte Apps) | Microsoft Docs
description: 'Infos zum Festlegen bestimmter Regeln, die steuern, wann die Menübandelemente während des Konfigurierens von Menübandelementen angezeigt werden. '
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 70e5687f-4d0e-3d43-03f3-10e5aa5b0713
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 71fd2e8592622f894d3636610767c078e92a33e8
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275926"
---
# <a name="define-ribbon-display-rules"></a>Definieren von Menüband-Anzeigeregeln

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-display-rules -->

Wenn Sie Menübandelemente konfigurieren, können Sie bestimmte Regeln definieren, die steuern, wann die Menübandelemente angezeigt werden.  

-   Verwenden Sie das /`RuleDefinitions`/DisplayRules/`<DisplayRule>`-Element, um Regeln zu definieren, die steuern, wann das Menübandelement angezeigt werden soll.  

-   Verwenden Sie das /CommandDefinitions/`CommandDefinition`/DisplayRules/`<DisplayRule>`-Element, um spezifische Anzeigeregeln einer Befehlsdefinition zuzuordnen.  

## <a name="control-when-ribbon-elements-are-displayed"></a>Steuern, wann Menübandelemente angezeigt werden  
 Durch die Definition von Anzeigeregeln in Regeldefinitionen können Sie dieselbe Anzeigeregel für viele Befehlsdefinitionen verwenden. Wenn mehrere Anzeigeregeln für eine Befehlsdefinition definiert sind, müssen alle der Anzeigeregeln als "true" ausgewertet werden, damit das Menübandelement angezeigt wird.  

 Alle Anzeigeregeln bieten ein optionales Attribut, um anzugeben, ob der Standardwert der Regel "true" oder "false" ist, und ein optionales `InvertResult`-Attribut, das ermöglicht, dass ein negatives Ergebnis zurückgegeben wird, wenn das getestete Element "true" zurückgibt.  

 Das `/RuleDefinitions/DisplayRules/DisplayRule`-Element unterstützt die folgenden Regeltypen:  

 `<CommandClientTypeRule>`  
[!INCLUDE[ribbon_element_CommandClientTypeRule](../../includes/ribbon-element-commandclienttyperule.md)]

 Die `Type`-Werte entsprechen dem Folgenden:  


|   Value   |                                                                               Präsentation                                                                               |
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Modern`  |                                       Die Befehlsleiste wird mit Dynamics 365 for tablets dargestellt.                                       |
| `Refresh` |                                                      Die Befehlsleiste wird mithilfe der aktualisierten Benutzeroberfläche angezeigt.                                                      |
| `Legacy`  | Das Menüband wird in Formularen für Entitäten, die nicht aktualisiert wurden, oder in einer Listenansicht in Dynamics 365 for Outlook angezeigt. |

 `<CrmClientTypeRule>`  
 Ermöglicht die Definition von Regeln abhängig vom Typ des verwendeten Clients. Die `Type`-Optionen lauten wie folgt:  

- Web  

- Outlook  

  `<CrmOfflineAccessStateRule>`  
  Verwenden Sie diese Kriterien, um ein Menübandelement abhängig davon anzuzeigen, ob Dynamics 365 for Microsoft Office Outlook mit Offlinezugriff derzeit im Offlinemodus ist.  

  `<CrmOutlookClientTypeRule>`  
  Verwenden Sie diese Regel, wenn Sie eine Schaltfläche für den spezifischen Dynamics 365 for Outlook-Typ anzeigen möchten. Die `Type`-Optionen lauten wie folgt:  

- CrmForOutlook  

- CrmForOutlookOfflineAccess  

  `<CrmOutlookClientVersionRule>`  
  [!INCLUDE[ribbon_element_CrmOutlookClientVersionRule](../../includes/ribbon-element-crmoutlookclientversionrule.md)]

  Gültige Werte:  

- 2003  

- 2007  

- 2010  

  `<EntityPrivilegeRule>`  
  Verwenden Sie diese Art von Regel, um Menübandelemente anzuzeigen, wenn ein Benutzer spezielle Rechte für eine Entität besitzt. Sie müssen die Berechtigungstiefe und die gewünschte Berechtigung angeben, die Sie überprüfen möchten.  

  `<EntityPropertyRule>`  
  Ermöglicht die Definition von Regeln abhängig von den booleschen Werten der spezifischen Entitätseigenschaften. Die `PropertyName`-Optionen lauten wie folgt:  

- DuplicateDetectionEnabled  

- GridFiltersEnabled  

- HasStateCode  

- IsConnectionsEnabled  

- MailMergeEnabled  

- WorksWithQueue  

- HasActivities  

- IsActivity  

- HasNotes  

  `<EntityRule>`  
  Entitätsregeln lassen die Evaluierung der aktuellen Entität zu. Dies ist hilfreich, wenn Sie benutzerdefinierte Aktionen definieren, die für die Entitätsvorlage gelten, statt für bestimmte Entitäten. Beispielsweise möchten Sie möglicherweise ein Menübandelement für alle Entitäten hinzufügen, mit Ausnahme einiger bestimmter Entitäten. Es ist einfacher, die benutzerdefinierte Aktion für die Entitätsvorlage zu definieren, die für alle Entitäten gilt, und dann eine Entitätsregel zu verwenden, die die Entitäten herausfiltert, die ausgeschlossen werden sollen.  

  Die Entitätsregel enthält auch ein optionales Kontextattribut, um anzugeben, ob die Entität im Formular oder in einer Liste angezeigt wird (HomePageGrid). Das optionale `AppliesTo`-Attribut kann auf `PrimaryEntity` oder `SelectedEntity` festgelegt werden, um zu unterscheiden, ob die Entität in einem Unterraster angezeigt wird.  

  `<FormEntityContextRule>`  
  [!INCLUDE[ribbon_element_FormEntityContextRule](../../includes/ribbon-element-formentitycontextrule.md)]

  `<FormStateRule`  
  Verwenden Sie die Formularstatus-Regel, um den aktuellen Formulartyp zu bestimmen, in dem ein Datensatz angezeigt wird. Die `State`-Optionen lauten wie folgt:  

- Erstellen  

- Vorhanden  

- Schreibgeschützt  

- Deaktiviert  

- BulkEdit  

  `<FormTypeRule>`  
  [!INCLUDE[ribbon_element_FormTypeRule](../../includes/ribbon-element-formtyperule.md)]

  Die `Type`-Werte entsprechen dem Folgenden:  

|Value|Präsentation|  
|-----------|------------------|  
|`Main`|Ein Entitätsformular, das in der Anwendung angezeigt wird.|  
|`Preview`|Das Entitätsvorschauformular, das als erweiterndes Element im Raster angezeigt wird.|  
|`AppointmentBook`|Wird mit den Termin-, Arbeitsgerät-, serviceappointment- und systemuser-Entitäten für die Serviceplanungs-Benutzeroberfläche verwendet.|  
|`Dashboard`|Das Formular definiert ein Dashboard.|  
|`Quick`|Ein Schnellansichtsformular.|  
|`QuickCreate`|Ein Formular für die Schnellerfassung.|  

 `<HideForTabletExperienceRule>`  
 [!INCLUDE[ribbon_element_HideForTabletExperienceRule](../../includes/ribbon-element-hidefortabletexperiencerule.md)]

 `<MiscellaneousPrivilegeRule>`  
 Verwenden Sie diese Art von Regel, um nach Rechten zu suchen, die nicht für eine bestimmte Entität gelten, zum Beispiel ExportToExcel, MailMerge oder GoOffline.  

 `<OrganizationSettingRule>`  
 Verwenden Sie diese Regel, um ein Menübandelement anzuzeigen, wenn bestimmte Organisationseinstellungen aktiviert sind. Die Einstellungsoptionen lauten wie folgt:  

- IsSharepointEnabled  

- IsSOPIntegrationEnabled  

- IsFiscalCalendarDefined  

  `<OrRule>`Mit dieser Regel können Sie den standardmäßigen UND-Vergleich für mehrere Anzeigeregeltypen überschreiben. Verwenden Sie das `OrRule`-Element, um mehrere mögliche gültige Kombinationen zu definieren, die zu überprüfen sind.  

  `<OutlookRenderTypeRule>`  
  Verwenden Sie diese Regel, um ein Menübandelement anzuzeigen, wenn das Menüband in [!INCLUDE[pn_MS_Outlook_Short](../../includes/pn-ms-outlook-short.md)] auf eine bestimmte Art angezeigt wird. Die `Type`-Optionen lauten wie folgt:  

- Web  

- Outlook  

  `<OutlookVersionRule>`  
  Verwenden Sie dies, um ein Menübandelement für eine bestimmte Version von Outlook anzuzeigen. Die `Version`-Optionen lauten wie folgt:  

- 2003  

- 2007  

- 2010  

  `<PageRule>`  
  Diese Art von Regel überprüft, ob die URL der Seite angezeigt wird. Sie gibt "true" zurück, wenn die Adresse übereinstimmt.  

  `<RelationshipTypeRule>` Diese Art von Regel wird auf Datensätze angewendet, die im Raster ausgewählt sind. Mit der Regel können Sie den Typ der Beziehung wie folgt bestimmen:  

- OneToMany  

- ManyToMany  

- NoRelationship  

  `<SkuRule>`  
  Verwenden Sie diese Art von Regel, um ein Menübandelement für eine bestimmte SKU-Version von Common Data Service wie folgt anzuzeigen,:  

- OnPremise  

- OnLine  

- Spla  

  `<ValueRule>`  
  Verwenden Sie diese Regel, um den Wert eines bestimmten Felds im Datensatz zu suchen, der im Formular angezeigt wird.  

> [!NOTE]
>  Bei Befehlen, die für das Unterraster für Formulare mithilfe der aktualisierten Benutzererfahrung definiert werden, können Werteregeln nicht innerhalb von Anzeigeregeln verwendet werden. Verwenden Sie dieses Element innerhalb von `<EnableRule>`, um ein Element auszublenden.  

### <a name="see-also"></a>Siehe auch  
 [Befehle und das Menüband anpassen](customize-commands-ribbon.md)   
 [Freigaberegeln für Menüband definieren](define-ribbon-enable-rules.md)   
 [Definieren von Menüband-Aktionen](define-ribbon-actions.md)
