---
title: Doppelte Regelentitäten (Common Data Service) | Microsoft-Dokumentation
description: Diese Entitäten enthalten Daten, die Duplikaterkennungsregeln definieren.
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
ms.openlocfilehash: 7434dd58137919d81486539d1ab843ad0c4aaf1f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748222"
---
# <a name="duplicate-rule-entities"></a>Duplikatregelentitäten

Informationen dazu, wie Duplikatregeln in der Anwendung konfiguriert werden, siehe [Administratorhandbuch: Einrichten von Duplikaterkennungsregeln, um Ihre Daten sauber zu halten](/dynamics365/customer-engagement/admin/set-up-duplicate-detection-rules-keep-data-clean).

Duplikaterkennungsregeln werden mit den folgenden Entitäten definiert:

- [Duplikatregel](reference/entities/duplicaterule.md): Erstellen Sie eine *Duplikaterkennungsregel* für einen bestimmten Entitätstyp, um im System Duplikate zu erkennen. Sie können mehrere Erkennungsregeln für denselben Entitätstyp erstellen. Sie können jedoch maximal fünf Duplikaterkennungsregeln pro Entitätstyp gleichzeitig veröffentlichen.  
- [DuplicateRuleCondition](reference/entities/duplicaterulecondition.md): Eine Regel kann mindestens eine *Duplikaterkennungsregelbedingung* haben, die von der Entität dargestellt wird. Die Bedingungen werden vom System als logischer `AND` Vorgang kombiniert. Eine Duplikaterkennungsregel gibt einen Entitätstyp und einen entsprechenden Basisentitätstyp an. Eine Duplikatregelbedingung gibt den Namen eines Basisattributes und den Namen eines entsprechenden Attributes an. Geben Sie zum Beispiel eine Firma als Basisentität und einen Kontakt als entsprechende Entität an, um Nachnamen sowie Adressen zu vergleichen. Die Entsprechungskriterien bestehen aus Operatoren wie genauer Entsprechung, erster N-Anzahl von Zeichen oder letzten N-Zahl von Zeichen. 


Die zwei Entitäten werden mit der Beziehung [DuplicateRule_DuplicateRuleConditions](/reference/entities/duplicaterule.md#BKMK_DuplicateRule_DuplicateRuleConditions) verknüpft.

Die Duplikaterkennung arbeitet durch Vergleichen von Webressourcen generierten Übereinstimmungscodes der vorhandenen Datensätze mit jedem neuen Datensatz, der erstellt wird. Diese Übereinstimmungscodes werden erstellt, wenn der neue Datensatz erstellt wird. Daher ist es möglich, dass mindestens doppelten Datensätze erstellt werden sollen, indem sie am genau der gleiche Moment verarbeitet werden. Zusätzlich zum Erkennen der Duplikaterkennung, die erstellt, können Sie einen Auftrag zur Duplikaterstellung planen, für andere potenzielle doppelte Datensätze zu überprüfen.
 
 Die Duplikaterkennungsregeln gelten systemweit. Sie müssen diese veröffentlichen, bevor Sie einen Duplikaterkennungsauftrag ausführen, um Duplikate für Massendaten zu erkennen oder Duplikate für einen bestimmten Entitätsdatensatz abzurufen. Um eine Duplikaterkennungsregel zu veröffentlichen, verwenden Sie die `PublishDuplicateRule`-Message (<xref href="Microsoft.Dynamics.CRM.PublishDuplicateRule?text=PublishDuplicateRule Action" /> oder <xref:Microsoft.Crm.Sdk.Messages.PublishDuplicateRuleRequest>). Das Veröffentlichen von Dupplikatregeln ist ein asynchroner Vorgang, der im Hintergrund ausgeführt wird.

Die folgenden schreibbaren Attribute in diesen Entitäten steuern das Verhalten von Duplikaterkennungsregeln.

## <a name="duplicaterule"></a>DuplicateRule

|Attribut|Beschreibung|
|-|-|
|[BaseEntityName](/reference/entities/duplicaterule.md#BKMK_BaseEntityName)| Datensatztyp des Datensatzes, der in Bezug auf potenzielle Duplikate ausgewertet wird.|
|[Beschreibung](/reference/entities/duplicaterule.md#BKMK_Description)|Beschreibung der Duplikaterkennungsregel.|
|[DuplicateRuleId](/reference/entities/duplicaterule.md#BKMK_DuplicateRuleId)|Eindeutiger Bezeichner der Duplikaterkennungsregel.|
|[ExcludeInactiveRecords](/reference/entities/duplicaterule.md#BKMK_ExcludeInactiveRecords)|Legt fest, ob inaktive Datensätze als Duplikate gekennzeichnet werden.<br /> **Hinweis**: <br />Der Standardwert ist `false`. Setzen Sie ihn auf `true`, wenn Sie nicht wollen, dass inaktive Datensätze als Duplikate gekennzeichnet werden soll, auch wenn sie Verdopplungserkennungsregelkriterien erfüllen. <br /> Weitere Informationen: [Inaktive Zustände](#inactive-states)|
|[IsCaseSensitive](/reference/entities/duplicaterule.md#BKMK_IsCaseSensitive)|Gibt an, ob bei dem Operator die Groß-/Kleinschreibung beachtet wird.|
|[MatchingEntityName](/reference/entities/duplicaterule.md#BKMK_MatchingEntityName)|Datensatztyp der Datensätze, die als potenzielle Duplikate ausgewertet werden.|
|[Name](/reference/entities/duplicaterule.md#BKMK_Name)|Name der Duplikaterkennungsregel.|
|[OwnerId](/reference/entities/duplicaterule.md#BKMK_OwnerId)|Eindeutiger Bezeichner des für die Duplikaterkennungsregel zuständigen Benutzers oder Teams.|
|[OwnerIdType](/reference/entities/duplicaterule.md#BKMK_OwnerIdType)|Ob der Besitzer ein Benutzer oder ein Team ist.|
|[StatusCode](/reference/entities/duplicaterule.md#BKMK_StatusCode)|Grund für den Status der Duplikaterkennungsregel.|

### <a name="inactive-states"></a>Inaktive Status

Die meisten Systementitäten und alle benutzerdefinierten Entitäten weisen zwei `StateCode`-Attributoptionen auf:

- `Value`: 0 `InvariantName`: `Active`
- `Value`: 1 `InvariantName`: `Inactive`

Die Beschriftung der Option wird geändert, aber der `InvariantName`-Wert nicht.

Einige Systementitäten haben mehr als einen aktiven oder inaktiven Zustand. Die folgende Tabelle enthält Beispiele von Entitäten mit mehr als einem aktiven oder inaktiven Zustand.

|Entität StateCode |Aktive(r) Status|Inaktive(r) Status|  
|--|--|--|  
|[Appointment.StateCode](/reference/entities/appointment.md#BKMK_StateCode)|`Open`, `Scheduled`|`Completed`, `Canceled`|  
|[CampaignActivity.StateCode](/reference/entities/CampaignActivity.md#BKMK_StateCode)|`Open`|`Closed`, `Canceled`|  
|[CampaignResponse.StateCode](/reference/entities/CampaignResponse.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  
|[Contract.StateCode](/reference/entities/Contract.md#BKMK_StateCode)|`Draft`, `Invoiced`, `On Hold`|`Canceled`, `Expired`|  
|[ContractDetail.StateCode](/reference/entities/ContractDetail.md#BKMK_StateCode)|`Existing`, `Renewed`|`Canceled`, `Expired`|  
|[Email.StateCode](/reference/entities/Email.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  
|[Fax.StateCode](/reference/entities/Fax.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  
|[Incident.StateCode](/reference/entities/Incident.md#BKMK_StateCode)|`Active`|`Resolved`, `Canceled`, `Closed`|  
|[Invoice.StateCode](/reference/entities/Invoice.md#BKMK_StateCode)|`Active`|`Closed`, `Paid`, `Canceled`|  
|[KbArticle.StateCode](/reference/entities/KbArticle.md#BKMK_StateCode)|`Draft`, `Unapproved`, `Published`|Nicht zutreffend|  
|[Lead.StateCode](/reference/entities/Lead.md#BKMK_StateCode)|`Open`|`Qualified`, `Disqualified`|  
|[Letter.StateCode](/reference/entities/Letter.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  
|[Opportunity.StateCode](/reference/entities/Opportunity.md#BKMK_StateCode)|`Open`|`Won`, `Lost`|  
|[PhoneCall.StateCode](/reference/entities/PhoneCall.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  
|[Quote.StateCode](/reference/entities/Quote.md#BKMK_StateCode)|`Draft`, `Active`|`Won`, `Closed`|  
|[SalesOrder.StateCode](/reference/entities/SalesOrder.md#BKMK_StateCode)|`Active`, `Submitted`, `Invoiced`|`Canceled`, `Fulfilled`|  
|[ServiceAppointment.StateCode](/reference/entities/ServiceAppointment.md#BKMK_StateCode)|`Open`, `Scheduled`|`Closed`, `Canceled`|  
|[Task.StateCode](/reference/entities/Task.md#BKMK_StateCode)|`Open`|`Completed`, `Canceled`|  

 Wenn Sie zum Beispiel das Attribut `ExcludeInactiveRecords` auf `true` gesetzt wird, werden nur `Active`, `Submitted` und `Invoiced` Vertriebsaufträgen von der Duplikaterkennung berücksichtigt. 


> [!NOTE]
> Sie können die verfügbaren `StateCode`-Optionen für eine Entität mit dem Metadatenbrowser überprüfen, der in [Durchsuchen der Metadaten für die Organisation](browse-your-metadata.md) beschrieben wird.
>
> Um die `StateCode`-Optionen für eine Entität anzurufen, können Sie die folgenden API-Abfrage verwenden, indem Sie den `LogicalName` der Entität durch den unten verwendeten `appointment` ersetzen:
> ```HTTP
> GET [organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='appointment')/Attributes(LogicalName='statecode')/Microsoft.Dynamics.CRM.StateAttributeMetadata/OptionSet?$select=Options
> ```

## <a name="duplicaterule-special-messages"></a>DuplicateRule-Sondermeldungen

[DuplicateRule](/reference/entities/duplicaterule.md) ist eine benutzereigene Entitäten und es sind normale Erstellen-, Abrufen-, Aktualisieren-, Zuweisen-, Löschen-Vorgänge sowie Vorgänge zur Zugriffssteuerung zulässig. Weitere Informationen: [DuplicateRule-Nachrichten](/reference//reference/entities/duplicaterule.md#messages)

Die folgenden Sondermeldungen können auch verwendet werden:

|Meldung|Web-API-Vorgang|SDK-Assembly|
|-|-|-|
|CompoundUpdateDuplicateDetectionRule|<xref href="Microsoft.Dynamics.CRM.CompoundUpdateDuplicateDetectionRule?text=CompoundUpdateDuplicateDetectionRule Action" />|<xref:Microsoft.Crm.Sdk.Messages.CompoundUpdateDuplicateDetectionRuleRequest>|
|PublishDuplicateRule|<xref href="Microsoft.Dynamics.CRM.PublishDuplicateRule?text=PublishDuplicateRule Action" />|<xref:Microsoft.Crm.Sdk.Messages.PublishDuplicateRuleRequest>|
|PublishXml|<xref href="Microsoft.Dynamics.CRM.PublishXml?text=PublishXml Action" />|<xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest>|
|UnpublishDuplicateRule|<xref href="Microsoft.Dynamics.CRM.UnpublishDuplicateRule?text=UnpublishDuplicateRule Action" />|<xref:Microsoft.Crm.Sdk.Messages.UnpublishDuplicateRuleRequest>|


## <a name="duplicaterulecondition"></a>DuplicateRuleCondition

|Attribut|Beschreibung|
|-|-|
|[BaseAttributeName](/reference/entities/duplicaterulecondition.md#BKMK_BaseAttributeName)|Das zu vergleichende Feld.|
|[DuplicateRuleConditionId](/reference/entities/duplicaterulecondition.md#BKMK_DuplicateRuleConditionId)|Eindeutiger Bezeichner der Bedingung.|
|[IgnoreBlankValues](/reference/entities/duplicaterulecondition.md#BKMK_IgnoreBlankValues)|Legt fest, ob leere Werte als eindeutige Werte gewertet werden. <br /> **Hinweis**: <br />Der Standardwert dieses Attributs ist `false`. Setzen Sie es zu `true` fest, wenn Sie nicht wollen, dass die Duplikatserkennungsregel `null` Werte als gleichgestellt betrachtet. <br /> **Wichtig**: <br /> Für eine Duplikaterkennungsregel mit einer Bedingung, wenn Sie den Attributwert auf `false` setzten, wird es vom System als `true` Wert behandelt. |
|[MatchingAttributeName](/reference/entities/duplicaterulecondition.md#BKMK_MatchingAttributeName)|Das Feld, das mit dem Ausgangsfeld verglichen wird.|
|[OperatorCode](/reference/entities/duplicaterulecondition.md#BKMK_OperatorCode)|Operator für diese Regelbedingung.<br /> **Wichtig**: <br />Wenn Sie das `OperatorCode`-Attribut auf `ExactMatch` setzen, setzen Sie das Attribut `OperatorParam` auf keinen Wert.|
|[OperatorParam](/reference/entities/duplicaterulecondition.md#BKMK_OperatorParam)|Parameterwert von 'N', falls der Operator 'Gleiche Anfangszeichen' oder 'Gleiche Endzeichen' ist.<br /> **Wichtig**: <br />Setzen Sie den `OperatorParam` nicht während Aktualisierungs- oder Erstellungsvorgängen auf Null.|
|[RegardingObjectId](/reference/entities/duplicaterulecondition.md#BKMK_RegardingObjectId)|Eindeutiger Bezeichner des Objekts, dem die Bedingung zugeordnet ist.|

## <a name="duplicaterulecondition-special-messages"></a>DuplicateRuleCondition-Sondermeldungen

[DuplicateRuleCondition](/reference/entities/duplicaterulecondition.md) ist eine untergeordnete Entität zu `DuplicateRule`. Der Zugriff, um diese Entitäten anzuzeigen oder zu ändern, hängt vom Zugriff auf die `DuplicateRule` an, der sie zugeordnet ist. Weitere Informationen: [DuplicateRuleCondition-Nachrichten](/reference/entities/duplicaterulecondition.md#messages)

Die folgenden Sondermeldungen können auch verwendet werden:

|Meldung|Web-API-Vorgang|SDK-Assembly|
|-|-|-|
|CompoundUpdateDuplicateDetectionRule|<xref href="Microsoft.Dynamics.CRM.CompoundUpdateDuplicateDetectionRule?text=CompoundUpdateDuplicateDetectionRule Action" />|<xref:Microsoft.Crm.Sdk.Messages.CompoundUpdateDuplicateDetectionRuleRequest>|


### <a name="see-also"></a>Siehe auch
<xref href="Microsoft.Dynamics.CRM.duplicaterule?text=duplicaterule EntityType" /><br/><xref href="Microsoft.Dynamics.CRM.duplicaterulecondition?text=duplicaterulecondition EntityType" /><br/><a href="detect-duplicate-data-with-code.md" data-raw-source="[Detect duplicate data](detect-duplicate-data-with-code.md)">Doppelte Daten erkennen</a><br />
<a href="enable-disable-duplicate-detection.md" data-raw-source="[Enable and disable duplicate detection](enable-disable-duplicate-detection.md)">Aktivieren und Deaktivieren der Duplikaterkennung</a><br />
<a href="run-duplicate-detection.md" data-raw-source="[Run duplicate detection](run-duplicate-detection.md)">Duplikaterkennung ausführen</a><br />
<a href="duplicate-detection-messages.md" data-raw-source="[Duplicate detection messages](duplicate-detection-messages.md)">Duplikaterkennungsmeldungen</a><br />
<a href="org-service/samples/enable-duplicate-detection-and-retrieve-duplicates.md" data-raw-source="[Sample: Enable duplicate detection and retrieve duplicates](org-service/samples/enable-duplicate-detection-and-retrieve-duplicates.md)">Beispiel: Duplikaterkennung aktivieren und Duplikate abrufen</a><br />
<a href="org-service/samples/use-duplicate-detection-when-creating-and-updating-records.md" data-raw-source="[Sample: Use duplicate detection when creating and updating records](org-service/samples/use-duplicate-detection-when-creating-and-updating-records.md)">Beispiel: Verwenden der Duplikaterkennung für die Erstellung und Aktualisierung von Datensätzen</a><br />
<a href="/dynamics365/customer-engagement/developer/org-service/sample-detect-multiple-duplicate-records" data-raw-source="[Sample: Detect multiple duplicate records](org-service/samples/detect-multiple-duplicate-records.md)">Beispiel: Erkennen von mehreren doppelten Datensätzen</a><br />