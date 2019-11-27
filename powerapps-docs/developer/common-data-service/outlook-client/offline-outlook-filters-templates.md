---
title: Offline- und Outlook-Filter und -Vorlagen (Common Data Service) | Microsoft-Dokumentation
description: Daten, die zwischen Common Data Service und Dynamics 365 for Outlook synchronisiert werden sollen, werden durch Datenfilter für Outlook festgelegt
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b68f2013e49ce85d78efe588a9308efa55b361c8
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748674"
---
# <a name="offline-and-outlook-filters-and-templates"></a>Offline- und Outlook-Filter und -Vorlagen

Datenfilter für Office Outlook bestimmen, welche Daten zwischen Common Data Service und Dynamics 365 for Outlook synchronisiert werden sollen. Common Data Service unterstützen die Möglichkeit, den Standardfilter mithilfe des SDK zu ändern und die Änderungen an einen oder alle Benutzer zu übertragen.  
Sie können Code schreiben, der Administratoren ermöglicht, Filtervorlagen zu erstellen und zu veröffentlichen. Dies ermöglicht einem Common Data Service-Administrator, allgemeine oder erwünschte Filter zu erstellen, die für Benutzer für die Synchronisierung mit dem Outlook Store und der Offlinedatenbank veröffentlicht werden können. Dies bietet auch die Möglichkeit, eine Standardfiltervorlage anzupassen, die für Benutzer angewendet wird, die zum System hinzugefügt werden, nachdem die Vorlagen ursprünglich veröffentlicht wurden. Der Administrator besitzt auch die Möglichkeit, Benutzerfilter zu aktualisieren oder zu löschen, nachdem sie veröffentlicht wurden.  
Damit diese Anpassungen unterstützt werden, gibt es vier neue Abfragetypen für gespeicherte Abfragen (Ansicht). Wenn Sie einen gespeicherten Abfragedatensatz (Ansicht) erstellen, geben Sie einen dieser Typen im `SavedQuery.QueryType`-Attribut mithilfe der <xref:Microsoft.Crm.Sdk.SavedQueryQueryType>-Enumeration an. Der Zugriff ist nur möglich, indem Sie die hier beschriebenen Methoden verwenden. Es gibt keine Benutzeroberfläche, um ihn zu ändern. Sie können verschiedene Filter angeben, sodass Sie für Ihr Mobiltelefon nicht alles mit Outlook synchronisieren müssen. Filtervorlagen sind lösungsfähig, sodass sie zusammen mit einer Lösung exportiert werden können.  
  
 In der folgenden Tabelle sind die neuen Abfragetypen für Filter und Filtervorlagen aufgelistet.  
  
|Abfragetyp|Beschreibung|  
|----------------|-----------------|  
|<xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OutlookFilters>|Definiert eine Teilmenge einer Entität, die mit Dynamics 365 for Outlook synchronisiert wird. Die Teilmenge von Daten, die mithilfe dieser Filter definiert werden, werden für Outlook-Ordner, zum Beispiel Kontakte, Kalender usw., synchronisiert.|  
|<xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OfflineFilters>|Definiert eine Teilmenge einer Entität, die mit Dynamics 365 for Microsoft Office Outlook mit Offlinezugriff synchronisiert wird. Die Teilmenge von Daten, die mithilfe dieser Filter definiert werden, werden mit der Offlinedatenbank synchronisiert.|  
|<xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OutlookTemplate>|Definiert eine Filtervorlage, die auf neue Benutzer für die Synchronisierung mit Dynamics 365 for Outlook angewendet wird.|  
|<xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OfflineTemplate>|Definiert eine Filtervorlage, die auf neue Benutzer für die Synchronisierung mit Dynamics 365 for Microsoft Office Outlook mit Offlinezugriff angewendet wird.|  
  
## <a name="instantiate-a-filter"></a>Instanziieren eines Filters

Standardfiltervorlagen werden automatisch in die `UserQuery`-Entität für jeden Benutzer instanziiert, wenn das Synchronisierungsabonnement erstellt wird. Wenn die Synchronisierung mit Outlook oder der Offlinedatenbank instanziiert wird, werden die Filter für diesen Benutzer erfasst und verwendet, um die Sammlungen aus Einträgen und Attributen zu filtern, die synchronisiert werden. Wenn mehrere Filter für eine bestimmte Entität angegeben werden, ist der entstehende Satz aus Einträgen eine Kombination der Ergebnisse einzelner Filter.  

Es gibt ein neues Recht, das es dem Administrator ermöglicht, auf die Filter anderer Benutzer zuzugreifen: `prvAdminFilter`. Dies wird in der Webanwendung als Verwalten von Benutzersynchronisierungsfilter bezeichnet. Die Systemadministratorrolle enthält dieses Recht, da ansonsten nur der Benutzer die Filter sehen kann. Ruft <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> Methode aus der Benutzerabfrage werden Datensätze nur für den besitzenden Benutzer abgerufen, sofern der Aufrufer das `prvAdminFilter`-Recht hat. Die Abfrage muss Bedingungen enthalten, in denen `QueryType` gleich <xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OutlookFilters> oder <xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OfflineFilters> UND `OwnerId` gleich , wobei `UserId` nicht dem `UserId` Aufrufer entspricht. Dies funktioniert nicht, wenn andere Bedingungen zur Abfrage hinzugefügt werden.  

Neue Benutzer erhalten automatisch die Filter aus den Filtervorlagen, die als Standard im Attribut `SavedQuery.IsDefault` markiert sind. Administratoren müssen wissen, dass sie den Wert ändern können. Jede Entität kann nur eine Filtervorlage haben, die als Standard markiert ist. Es kann keine Standardfilter geben, nur Filtervorlagen. Wenn Sie eine benutzerdefinierte Entität erstellen und die <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAvailableOffline>-Eigenschaft festlegen, wird eine Standardfiltervorlage automatisch erstellt.  

Es gibt einen neuen Filtertyp, den Administratoren definieren können und der als Systemfilter bezeichnet wird. Diese Filter werden als `SavedQuery`-Datensätze mit dem Abfragetyp <xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OutlookFilters> oder <xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OfflineFilters> definiert. Systemfilter gelten automatisch für alle Benutzer, und können von den Benutzern nicht geändert werden.  

Es gibt eine Beschränkung der Filteranzahl, die Sie hinzufügen können. Diese Einstellung wird vom Common Data Service-Bereitstellungsadministrator gesteuert, um Benutzer oder Administratoren davon abzuhalten, zu viele Filter zu erstellen, was die Serverleistung beeinträchtigt. Dieselbe Grenzeneinstellung wird auf alle Entitäten angewendet.  

Standardmäßig gibt es unbegrenzte Einstellungen für Systemfilter und Benutzerfilter.  

## <a name="instantiate-a-template"></a>Instanziieren einer Vorlage

Sie können einen oder mehrere Filter pro Benutzer instanziieren. Verwenden Sie die <xref:Microsoft.Crm.Sdk.Messages.InstantiateFiltersRequest>, um einen Filter zu instanziieren und einen Benutzerabfragedatensatz zu erstellen. Jeder Benutzerabfragedatensatz enthält einen Verweis zurück zum Filter. Wenn Sie den Filter aktualisieren, können Sie die Instanziierung erneut aufrufen, um die Änderungen des Benutzers am Filter (Benutzerabfragedatensatz) zu aktualisieren oder zu überschreiben.  
  
## <a name="reset-a-users-filters-to-the-default"></a>Zurücksetzen eines Benutzerfilters auf den Standard

Sie können die Filter für einen Benutzer mithilfe der <xref:Microsoft.Crm.Sdk.Messages.ResetUserFiltersRequest> auf den Standard zurücksetzen.  
  
### <a name="see-also"></a>Siehe auch

[Erweitern von Dynamics 365 for Outlook](extend-dynamics-365-outlook.md)<br />
[SavedQuery Entitätsreferenz](../reference/entities/savedquery.md)<br />
[Beispiel: Outlook-Filter erstellen und abrufen](sample-create-retrieve-outlook-filters.md)<br /> 
<xref:Microsoft.Crm.Sdk.Messages.InstantiateFiltersRequest><br />
<xref:Microsoft.Crm.Sdk.Messages.ResetUserFiltersRequest>