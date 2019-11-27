---
title: Definieren von benutzerdefinierten Statusmodellübergängen (Common Data Service) | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Definition von benutzerdefinierten Statusmodellübergängen für die Vorfall (Anfrage)-Entität oder benutzerdefinierte Entitäten.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a7172755f75a2d39ff1ad2b0bf7dcbfb88bdf72d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752990"
---
# <a name="define-custom-state-model-transitions"></a>Definieren von benutzerdefinierten Statusmodellübergängen

In `Incident` können Sie benutzerdefinierte Statusübergänge für die (**Anfrage**)-Entität oder benutzerdefinerte Entitäten angeben. Im <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsStateModelAware> Eigenschaft ist `true` für Entitäten, die Statusmodellübergänge unterstützen.  
  
 Benutzerdefinierte Statusübergänge sind eine optionale Filterebene zum Definieren, welche Statusübergänge für einen Datensatz in einem gegebenen Status gültig sind. Insbesondere bei einer großen Anzahl von Kombinationen für gültige Status und Statuswerte kann die Definition einer begrenzten Liste von Optionen es für Benutzer einfacher machen, den korrekten Status für einen Datensatz auszuwählen.  

<a name="BKMK_StateModel"></a>
   
## <a name="what-is-the-state-model"></a>Was ist das Statusmodell?  
 Entitäten, die das Statuskonzept unterstützten, verfügen über ein Paar von Attributen, die diese Daten aufnehmen, wie in der folgenden Tabelle gezeigt.  
  
|Logischer Name|Anzeigename|Beschreibung|  
|------------------|------------------|-----------------|  
|`statecode`|**Status**|Stellt den Status des Datensatzes dar. Für benutzerdefinierte Entitäten ist dies **Aktiv** oder **Inaktiv**. Beispielsweise verwendet die Entität "Anfrage" **Aktiv**, **Gelöst** und **Storniert**. Sie können keine weiteren Statusoptionen hinzufügen, aber Sie können die Optionsbeschriftungen ändern.|  
|`statuscode`|**Statusgrund**|Stellt einen Status dar, der mit einem bestimmten Status verknüpft ist. Jeder Status muss mindestens einen möglichen Status haben. Sie können zusätzliche Statusoptionen hinzufügen und die Bezeichnungen von vorhandenen Optionen ändern.|  
  
 Die Metadaten für die Attribute definieren, welche Statuswerte für einen bestimmten Status gültig sind. Beispielsweise werden für die Entität `Incident` (**Anfrage**) der Standardstatus und die -statusoptionen in der folgenden Tabelle gezeigt.  
  
|Zustand|Status|  
|-----------|------------|  
|`Label`: **Aktiv**<br /><br /> `Value`: 0|`Label`: **In Bearbeitung**<br /><br /> `Value`: 1<br /><br /> `State`: 0|  
|`Label`: **Aktiv**<br /><br /> `Value`: 0|`Label`: **Zurückgestellt**<br /><br /> `Value`: 2<br /><br /> `State`: 0|  
|`Label`: **Aktiv**<br /><br /> `Value`: 0|`Label`: **Warten auf Details**<br /><br /> `Value`: 3<br /><br /> `State`: 0|  
|`Label`: **Aktiv**<br /><br /> `Value`: 0|Beschriftung: **Recherche**<br /><br /> `Value`: 4<br /><br /> `State`: 0|  
|`Label`: **Behoben**<br /><br /> `Value`: 1|`Label`: **Problem behoben**<br /><br /> `Value`: 5<br /><br /> `State`: 1|  
|`Label`: **Behoben**<br /><br /> `Value`: 1|Beschriftung: **Bereitgestellte Informationen**<br /><br /> `Value`: 1000<br /><br /> `State`: 1|  
|Beschriftung: **Storniert**<br /><br /> `Value`: 2|`Label`: **Storniert**<br /><br /> `Value`: 6<br /><br /> `State`: 2|  
|Beschriftung: **Storniert**<br /><br /> `Value`: 2|`Label`: **Zusammengeführt**<br /><br /> `Value`: 2000<br /><br /> `State`: 2|  
  
 Diese Daten werden in der Klasse <xref:Microsoft.Xrm.Sdk.Metadata.StatusOptionMetadata> gespeichert, die die Optionen in der Klasse <xref:Microsoft.Xrm.Sdk.Metadata.StatusAttributeMetadata> darstellt.  
  
Zum Anzeigen der Entitätsmetadaten für Ihre Organisation installieren Sie die Metadatenbrowserlösung, die in [Durchsuchen der Metadaten für Ihre Organisation](browse-your-metadata.md) beschrieben ist. Sie können die Referenzdokumentation für Entitäten auch in der [Entitätsreferenz](/reference/about-entity-reference.md) durchsuchen.
  
<a name="BKMK_DetectValidStatusTransitions"></a>   

## <a name="detect-valid-status-transitions"></a>Erkennen von gültigen Statusübergängen  
 Sie können das `statuscode`-Attribut ändern, um zu definieren, welche anderen Statusoptionen gültige Übergänge aus dem aktuellen Status darstellen. Anweisungen dazu finden Sie in der Anleitung zur Anpassung in folgendem Thema: [Festlegen von Statusgrundübergängen](https://go.microsoft.com/fwlink/p/?LinkId=393657)  
  
 Wenn benutzerdefinierte Statusübergänge auf eine Entität angewendet werden, muss die <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.EnforceStateTransitions> Eigenschaft ist `true`. Auch jede <xref:Microsoft.Xrm.Sdk.Metadata.StatusOptionMetadata> innerhalb der <xref:Microsoft.Xrm.Sdk.Metadata.StatusAttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadata.Options> Sammlung enthält eine neue <xref:Microsoft.Xrm.Sdk.Metadata.StatusOptionMetadata.TransitionData>-Eigenschaft. Diese Eigenschaft enthält einen Zeichenfolgenwert, der ein XML-Dokument darstellt. Dieses Dokument enthält die Definition der zulässigen Übergänge. Beispielsweise kann die standardmäßige `Incident` (**Anfrage**) `StatusCode`-Attributoption den folgenden `TransitionData`-Wert haben.  
  
```xml  
<allowedtransitions xmlns="https://schemas.microsoft.com/crm/2009/WebServices">  
<allowedtransition sourcestatusid="1" tostatusid="6" />  
<allowedtransition sourcestatusid="1" tostatusid="1000" />   
<allowedtransition sourcestatusid="1" tostatusid="2000" />  
<allowedtransition sourcestatusid="1" tostatusid="5" />  
</allowedtransitions>  
```  
  
> [!NOTE]
>  Wenn diese Daten in nicht verwaltetem Code von dem Webdienst abgerufen werden, beispielsweise bei Verwendung von JavaScript, werden sie umgangen und erscheinen wie im folgenden Beispiel.  
  
```xml  
<allowedtransitions xmlns="https://schemas.microsoft.com/crm/2009/WebServices">  
<allowedtransition sourcestatusid="1" tostatusid="6">  
<allowedtransition sourcestatusid="1" tostatusid="1000">  
<allowedtransition sourcestatusid="1" tostatusid="2000">  
<allowedtransition sourcestatusid="1" tostatusid="5">  
</allowedtransitions>  
```  
  
 Wenn diese Daten vorhanden sind und die Entitätseigenschaft `EnforceStateTransitions` auf `true` festgelegt ist, kann eine Vorfallinstanz nur in einen der zulässigen `statuscode`-Werte geändert werden. Sie können<xref:Microsoft.Xrm.Sdk.IOrganizationService> verwenden.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> können Sie `statuscode`<xref:Microsoft.Xrm.Sdk.OptionSetValue> für einen der zulässigen Werte verwenden, die keine Statusänderung darstellen. Um den Status zu ändern, verwenden Sie <xref:Microsoft.Crm.Sdk.Messages.SetStateRequest> zum Festlegen der zulässigen Eigenschaftswerte <xref:Microsoft.Crm.Sdk.Messages.SetStateRequest.State> und <xref:Microsoft.Crm.Sdk.Messages.SetStateRequest.Status> oder <xref:Microsoft.Crm.Sdk.Messages.CloseIncidentRequest> zum Festlegen der Eigenschaft <xref:Microsoft.Crm.Sdk.Messages.CloseIncidentRequest.Status> auf einen der Werte, die für den aktuellen `statuscode`-Wert zulässig sind. Wenn Sie versuchen, einen ungültigen Wert festzulegen, wird ein Fehler ausgelöst.  
  
### <a name="see-also"></a>Siehe auch  
 [Beispiel: Abrufen gültiger Statusübergänge](org-service/samples/retrieve-valid-status-transitions.md)   
 [Datensatzzustand und -status](/dynamics365/customer-engagement/developer/introduction-entities#bkmk_RecordStateandStatus)   
 [Abrufen und Erkennen von Änderungen bei Metadaten](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata)   
 [Festlegen von Statusgrundübergängen](https://go.microsoft.com/fwlink/p/?LinkId=393657)
