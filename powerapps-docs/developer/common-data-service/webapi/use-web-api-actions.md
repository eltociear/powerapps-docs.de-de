---
title: Nutzen von Web-API-Aktionen (Common Data Service) | Microsoft Docs
descriptions: Actions are reusable operations that can be performed using the Web API. These are used with a POST request to modify data on Common Data Service
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 53eafd67-385a-485b-9022-5127df08ea2f
caps.latest.revision: 14
author: brandonsimons
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-web-api-actions"></a>Nutzen von Web-API-Aktionen

Aktionen und Funktionen stellen wiederverwendbare Vorgänge dar, die Sie mithilfe derb Web-API ausführen können. Nutzen Sie eine POST-Anforderung mit den Aktionen, die in <xref:Microsoft.Dynamics.CRM.ActionIndex> aufgeführt sind, um Vorgänge auszuführen, die keine Nebenwirkungen haben. Sie können benutzerdefinierte Aktionen definieren, die für Ihre Verwendung bereitstehen.

<a name="bkmk_unboundActions"></a>

## <a name="unbound-actions"></a>Ungebundene Aktionen

Aktionen werden definiert im [CSDL-Metadatendokument](web-api-types-operations.md#bkmk_csdl). Beispielsweise ist das Folgende eine Definition der <xref href="Microsoft.Dynamics.CRM.WinOpportunity?text=WinOpportunity Action" />, die im Metadaten-Dokument dargestellt wird.

```xml
<Action Name="WinOpportunity">
  <Parameter Name="OpportunityClose" Type="mscrm.opportunityclose" Nullable="false" />
  <Parameter Name="Status" Type="Edm.Int32" Nullable="false" />
</Action>
```

Die <xref href="Microsoft.Dynamics.CRM.WinOpportunity?text=WinOpportunity Action" /> entspricht der <xref:Microsoft.Crm.Sdk.Messages.WinOpportunityRequest>, bei der der Organisationsdienst verwendet wird. Verwenden Sie diese Aktion, um den Status einer Verkaufschance auf "Gewonnen" festzulegen und einen <xref href="Microsoft.Dynamics.CRM.opportunityclose?text=opportunityclose EntityType" />-Datensatz zur Aufzeichnung des Ereignisses zu erstellen. Diese Aktion umfasst keinen Rückgabewert. Wenn der Vorgang erfolgreich ausgeführt wird, ist er abgeschlossen.

Der Parameter `OpportunityClose` erfordert eine JSON-Darstellung der opportunityclose-Entität, um den Vorgang zu erstellen. Diese Entität muss mit der Verkaufschance verbunden sein, die die opportunityid einzelbewertete Navigationseigenschaft ausstellt. In JSON wird dies mit der `@odata.bind`-Anmerkung festgelegt, wie in [Entitäten bei Erstellung zuordnen](create-entity-web-api.md#bkmk_associateOnCreate) beschrieben.

Der Parameter `Status` muss auf den Status für die Verkaufschance gesetzt werden, wenn er geschlossen ist. Sie finden den Standardwert dafür in der <xref href="Microsoft.Dynamics.CRM.opportunity?text=opportunity EntityType" /> statuscode-Eigenschaft. Die Option **Gewonnen** hat einen Wert von 3. Sie fragen sich möglicherweise, warum der Wert festgelegt werden muss, wenn es nur eine Statusgrund-Option gibt, die **Gewonnen** darstellt. Der Grund dafür ist, dass Sie möglicherweise benutzerdefinierte Statusoptionen definieren, um einen Gewinn darzustellen, beispielsweise **einen großen** oder **kleinen Gewinn**, sodass sich der Wert in dieser Situation möglicherweise von drei unterscheidet.

Das folgende Beispiel zeigt die HTTP-Anforderung und -Antwort zum Aufruf der `WinOpportunity`-Aktion für eine Verkaufschance mit einem opportunityid-Wert von `b3828ac8-917a-e511-80d2-00155d2a68d2`.

 **Anforderung**

```http
POST [Organization URI]/api/data/v9.0/WinOpportunity HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "Status": 3,
 "OpportunityClose": {
  "subject": "Won Opportunity",
  "opportunityid@odata.bind": "[Organization URI]/api/data/v9.0/opportunities(b3828ac8-917a-e511-80d2-00155d2a68d2)"
 }
}

```

 **Antwort**

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
```

<a name="bkmk_boundActions"></a>

## <a name="bound-actions"></a>Gebundene Aktionen

Im [CSDL-Metadatendokument](web-api-types-operations.md#bkmk_csdl), wenn ein `Action`-Element eine gebundene Aktion darstellt, besitzt es ein `IsBound`-Attribut mit dem Wert `true`. Das erste definierte `Parameter`-Element innerhalb der Aktion repräsentiert die Entität, an die die Operation geknüpft ist. Wenn das Attribut `Type` des Parameters eine Sammlung ist, wird der Vorgang an eine Entitätssammlung gebunden. Als Beispiel wird die folgende Definition der <xref href="Microsoft.Dynamics.CRM.AddToQueue?text=AddToQueue Action" /> in der CSDL dargestellt:

```xml
 <ComplexType Name="AddToQueueResponse">
 <Property Name="QueueItemId" Type="Edm.Guid" Nullable="false" />
 </ComplexType>
 <Action Name="AddToQueue" IsBound="true">
  <Parameter Name="entity" Type="mscrm.queue" Nullable="false" />
  <Parameter Name="Target" Type="mscrm.crmbaseentity" Nullable="false" />
  <Parameter Name="SourceQueue" Type="mscrm.queue" />
  <Parameter Name="QueueItemProperties" Type="mscrm.queueitem" />
  <ReturnType Type="mscrm.AddToQueueResponse" Nullable="false" />
</Action>
```

Diese Bindungsaktion ähnelt <xref:Microsoft.Crm.Sdk.Messages.AddToQueueRequest>, was vom Organisationsservice verwendet wird. In der Web-API ist diese Aktion an <xref href="Microsoft.Dynamics.CRM.queue?text=queue EntityType" />) gebunden, der <xref:Microsoft.Crm.Sdk.Messages.AddToQueueRequest>.<xref:Microsoft.Crm.Sdk.Messages.AddToQueueRequest.DestinationQueueId>- darstellt. -Eigenschaft verfügbar. Diese Aktion akzeptiert mehrere zusätzliche Parameter und gibt dann eine <xref href="Microsoft.Dynamics.CRM.AddToQueueResponse?text=AddToQueueResponse ComplexType" /> entsprechend der <xref:Microsoft.Crm.Sdk.Messages.AddToQueueResponse> vom Organisationsservice zurück. Wenn eine Aktion einen komplexen Datentyp zurückgibt, so wird dessen Definition direkt über der Definition der Aktion in CSDL angezeigt.

Eine Aktion muss mithilfe einer URI aufgerufen werden, um den ersten Parameterwert festzulegen. Sie können es nicht als Parameterwert mit Namen festlegen.

Beim Aufruf einer gebundenen Funktion müssen Sie den vollständigen Namen der Funktion einschließlich den `Microsoft.Dynamics.CRM`-Namespace angeben. Wenn Sie nicht den vollständigen Namen einschließen, wird eine Fehlermeldung ähnlich der folgenden angezeigt: Statuscode: 400 Die angeforderte Nachricht enthält nicht aufgelöste Parameter.

Im folgenden Beispiel wird das Hinzufügen eines Schreibens zu einer Warteschlange mittels <xref href="Microsoft.Dynamics.CRM.AddToQueue?text=AddToQueue Action" /> gezeigt. Da der Typ des `Target`-Parametertyps nicht spezifisch ist,(`mscrm.crmbaseentity`), müssen Sie explizit den typ des Objekts deklarierten, indem Sie den `@odata.type`-Eigenschaftswert des vollständigen Namens der Entität verwenden, einschließlich des `Microsoft.Dynamics.CRM`-Namespace. In diesem Fall: `Microsoft.Dynamics.CRM.letter`. Weitere Informationen:[Entitätsparametertyp angeben](#bkmk_specifyentityparametertype)

 **Anforderung**

```http
POST [Organization URI]/api/data/v9.0/queues(56ae8258-4878-e511-80d4-00155d2a68d1)/Microsoft.Dynamics.CRM.AddToQueue HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "Target": {
  "activityid": "59ae8258-4878-e511-80d4-00155d2a68d1",
  "@odata.type": "Microsoft.Dynamics.CRM.letter"
 }
}
```

 **Antwort**

```http

HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.AddToQueueResponse",
 "QueueItemId": "5aae8258-4878-e511-80d4-00155d2a68d1"
}
```

<a name="bkmk_customActions"></a>

## <a name="use-a-custom-action"></a>Nutzen einer benutzerdefinierten Aktion

<!-- TODO: 
If you define custom actions for your organization or solution these will also be included in the [CSDL metadata document](web-api-types-operations.md#bkmk_csdl). For information about creating actions using the customization tools in the application, see the TechNet topic [Actions](/dynamics365/customer-engagement/customize/actions). For information about creating and using your own custom actions, see [Create your own actions](../create-own-actions.md). -->

Unabhängig davon, ob die Vorgänge in der benutzerdefinierten Aktion Nebenwirkungen haben, können sie möglicherweise Daten ändern und gelten daher eher als Aktionen und nicht als Funktionen. Es gibt keine Möglichkeit, eine benutzerdefinierte Funktion zu erstellen.

### <a name="custom-action-example-add-a-note-to-a-contact"></a>Benutzerdefiniertes Aktionsbeispiel: Hinzufügen einer Notiz zu einem Kontakt

 Nehmen wir an, dass Sie eine benutzerdefinierte Aktion erstellen möchten, mit der eine neue Notiz zu einem bestimmten Kontakt hinzugefügt wird. Sie können eine benutzerdefinierte Aktionsgrenze zur Kontaktentität mit den folgenden Eigenschaften erstellen.

|UI-Beschriftung|Wert|
|--------------|-----------|
|**Prozessname**|AddNoteToContact|
|**Eindeutiger Name**|new_AddNoteToContact|
|**Entität**|Kontakt|
|**Kategorie**|Aktion|

 **Argumente verarbeiten**

|Name|Typ|Erforderlich|Richtung|
|----------|----------|--------------|---------------|
|Notizentitel|Zeichenfolge|Erforderlich|Eingabe|
|Notizentext|Zeichenfolge|Erforderlich|Eingabe|
|Notizenreferenz|EntityReference|Erforderlich|Ausgabe|

 **Schritte**

|Name|Schritt-Typ|Beschreibung|
|----------|---------------|-----------------|
|Erstellen der Notiz|Datensatz erstellen|Titel = {NoteTitle(Argumente)}<br /> Notizen-Text = (Anfragen {NoteText})<br /> Bezug = {Contact{Contact}}|
|Rückgabe eines Verweises zur Notiz|Wert zuweisen|NoteReference-Wert = {Erstellen der Notiz (Hinweis)}|

 Nachdem Sie die angepasste Aktion veröffentlicht und aktiviert haben, finden Sie, wenn Sie das CSDL herunterladen, diese neue Aktion definiert.

```xml

<Action Name="new_AddNoteToContact" IsBound="true">
  <Parameter Name="entity" Type="mscrm.contact" Nullable="false" />
  <Parameter Name="NoteTitle" Type="Edm.String" Nullable="false" Unicode="false" />
  <Parameter Name="NoteText" Type="Edm.String" Nullable="false" Unicode="false" />
  <ReturnType Type="mscrm.annotation" Nullable="false" />
</Action>

```

Die folgende HTTP-Anforderung und -Antwort zeigt, wie die benutzerdefinierte Aktion und Antwort, die bei Erfolg zurückgegeben wird, aufgerufen werden.  

 **Anforderung**

```http
POST [Organization URI]/api/data/v9.0/contacts(94d8c461-a27a-e511-80d2-00155d2a68d2)/Microsoft.Dynamics.CRM.new_AddNoteToContact HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "NoteTitle": "New Note Title",
 "NoteText": "This is the text of the note"
}
```


 **Antwort**

```http

HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#annotations/$entity",
 "annotationid": "9ad8c461-a27a-e511-80d2-00155d2a68d2"
}
```

<a name="bkmk_specifyentityparametertype"></a>

## <a name="specify-entity-parameter-type"></a>Geben Sie Entitätsparametertyp an

Wenn bei einer Aktion eine Entität erforderlich ist, weil ein Parameter und die Verwendungsart der Entität mehrdeutig ist, müssen Sie die `@odata.type`-Eigenschaft verwenden, um den Typ der Entität anzugeben. Der Wert dieser Eigenschaft ist der vollqualifizierte Name der Entität, der diesem Muster folgt: `Microsoft.Dynamics.CRM.`+*\<entity logical name>*.

Wie im Abschnitt [Gebundene Aktionen](#bkmk_boundActions) oben gezeigt, ist der `Target`-Parameter für <xref href="Microsoft.Dynamics.CRM.AddToQueue?text=AddToQueue Action" /> eine Aktivität. Aber da alle Aktivitäten von <xref href="Microsoft.Dynamics.CRM.activitypointer?text=activitypointer EntityType" /> erben, müssen Sie folgende Eigenschaft in der Entität JSON aufnehmen, um zu definieren, dass der Typ der Entität ein Buchstabe ist: `"@odata.type": "Microsoft.Dynamics.CRM.letter"`.

Zwei weitere Beispiele sind <xref href="Microsoft.Dynamics.CRM.AddMembersTeam?text=AddMembersTeam Action" /> und <xref href="Microsoft.Dynamics.CRM.RemoveMembersTeam?text=RemoveMembersTeam Action" /> weil der `Members` Parameter eine Sammlung von  <xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" /> die den `ownerid` Primärschlüssel von <xref href="Microsoft.Dynamics.CRM.principal?text=principal EntityType" /> erben. Wenn Sie die folgende JSON ausführen, um einem einzelnen Benutzer in der Sammlung anzuzeigen, ist es klar, dass die Entität ein Systemnutzer und nicht ein <xref href="Microsoft.Dynamics.CRM.team?text=team EntityType" /> ist, der auch von Haupt-Entitätstyp erbt.

```json
{
 "Members": [{
  "@odata.type": "Microsoft.Dynamics.CRM.systemuser",
  "ownerid": "5dbf5efc-4507-e611-80de-5065f38a7b01"
 }]
}
```

Wenn Sie nicht den Typ der Entität in dieser Situation angeben, erhalten Sie möglicherweise folgenden Fehler: `"EdmEntityObject passed should have the key property value set."`.

### <a name="see-also"></a>Siehe auch

[Internet-API-Funktionen- und Aktionen-Beispiel (C#)](samples/functions-actions-csharp.md)<br />
[Beispiele von Web API-Funktionen und Aktionen (clientseitiges JavaScript)](samples/functions-actions-client-side-javascript.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)<br />
