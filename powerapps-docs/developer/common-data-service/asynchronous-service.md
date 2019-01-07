---
title: Asynchroner Dienst (Common Data Service for Apps)  | Microsoft Docs
description: 'Erfahren Sie grundlegendes Asynchrone Dienste, die den Systemauftrag verwalten.'
ms.custom: ''
ms.date: 11/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="asynchronous-service"></a>Asynchroner Service

Der asynchrone Service führt die Vorgänge mit langer Laufzeit unabhängig vom hauptsächlichen Common Data Service for Apps-Kernvorgang aus. Dies führt zu einer optimierten Gesamtsystemleistung und Skalierbarkeit. Der asynchrone Dienst verfügt über eine verwaltete First-In, First-Out (FIFO)-Warteschlange für die Ausführung von asynchron registrierten Plug-Ins, Workflows und Operationen wie Massenmail, Massenimport und Verbreitung von Aktivitätsweitergaben. Diese Vorgänge werden beim asynchronen Dienst registriert und in regelmäßigen Intervallen ausgeführt, wenn der Dienst die Warteschlange verarbeitet.


Nachdem ein Ereignis eingetreten ist und alle synchronen Erweiterungen verarbeitet wurden, serialisiert die Plattform den Kontext für alle asynchronen Erweiterungen und speichert ihn als **Systemauftrag** in der [AsyncOperation-Entität](reference/entities/asyncoperation.md) in der Datenbank. Der Systemauftrag definiert und verfolgt die Ausführung des asynchronen Betriebs. Wenn Ressourcen verfügbar werden, werden Systemaufträge verarbeitet und die von ihnen definierten Operationen ausgeführt. Alle in der Erweiterung definierten Datenoperationen werden erneut von der Ereignisausführungspipeline verarbeitet, diesmal jedoch als synchrone Operation.

## <a name="execution-order-and-dependencies"></a>Ausführungsauftrag und Abhängigkeiten

Systemaufträge werden als Warteschlange mithilfe des Datums [CreatedOn](reference/entities/asyncoperation.md#BKMK_CreatedOn) ausgewertet. Wenn es keine Bedingungen für eine Verschiebung der Ausführung gibt, werden diese ausgeführt, sobald Ressourcen verfügbar sind. Es ist nicht garantiert, dass die Ausführung in der bis zum `CreatedOn` Datum festgelegten Reihenfolge erfolgt, da verschiedene Arten von Operationen unterschiedliche Ressourcen erfordern.

Ein Systemauftrag kann von einem anderen Systemauftrag abhängig sein, so dass er erst beginnt, wenn der andere Systemauftrag abgeschlossen ist. Diese Abhängigkeit wird durch den Attributwert [DependencyToken](reference/entities/asyncoperation.md#BKMK_DependencyToken) festgelegt. Abhängigkeiten werden beim Anlegen eines Systemauftrags hergestellt. Wenn der `DependencyToken`-Wert Null ist, hat der Systemauftrag keine Abhängigkeiten. Abhängige Systemaufträge haben den gleichen `DependencyToken`-Wert und werden in der Reihenfolge ihrer Erstellung ausgeführt. Wenn ein Systemauftrag verschoben wird, warten alle nachfolgenden abhängigen Systemaufträge weiterhin, bis der aufgeschobene Systemauftrag ausgeführt wird.

> [!NOTE]
> Dieses Abhängigkeitssystem kann nicht von Plug-Ins verwendet werden, die für den asynchronen Betrieb registriert sind, da die Systemaufträge für sie vom System erstellt werden.

## <a name="managing-system-jobs"></a>Verwalten von Systemaufträgen

Sie können die folgenden Aktionen ausführen, um Systemaufträge mit der [AsyncOperation Entität](reference/entities/asyncoperation.md) zu verwalten.

- Abrufen von Systemaufträgen
- Systemaufträge löschen
- Verwalten von Systemauftragsstatus
- Verschieben von Systemaufträgen

> [!NOTE]
> Das Erstellen von Systemaufträgen mit Code wird nicht unterstützt. Obwohl die `AsyncOperation`-Entität mehrere schreibbare Attribute unterstützt und Operationen erstellt, werden für die Aktualisierung nur die folgenden Attribute unterstützt:
> - [StateCode](reference/entities/asyncoperation.md#BKMK_StateCode)
> - [StatusCode](reference/entities/asyncoperation.md#BKMK_StatusCode)
> - [PostPoneUntil](reference/entities/asyncoperation.md#BKMK_PostponeUntil)



## <a name="retrieve-system-jobs"></a>Abrufen von Systemaufträgen

Sie können Systemaufträge in der Anwendung anzeigen, indem Sie zu **Einstellungen** > **System** > **Systemauftrag** navigieren und sie auch über die erweiterte Suche suchen.

Mit Hilfe von Code können Sie Systemaufträge wie jede andere Entität abrufen. In der folgenden Tabelle sind die Attribute aufgeführt, die für das Verständnis von Systemaufträgen wichtig sind:

|**Attribut**|**Beschreibung**|
|--|--|
|`AsyncOperationId`|Eindeutiger Bezeichner des Systemauftrags.|
|`CompletedOn`|Datum und Uhrzeit der Fertigstellung des Systemauftrags.|
|`CreatedBy`|Eindeutiger Bezeichner des Benutzers, der den Systemauftrag erstellt hat.|
|`CreatedOn`|Datum und Uhrzeit der Erstellung des Systemauftrags.|
|`Data`|Dem Systemauftrag zugeordnete unstrukturierte Daten.|
|`DependencyToken`|Die Ausführung aller Vorgänge mit demselben Abhängigkeitstoken wird serialisiert. Weitere Informationen: [Ausführungsauftrag und Abhängigkeiten](#execution-order-and-dependencies) |
|`Depth`|Anzahl von SDK-Aufrufen seit dem ersten Aufruf.|
|`ErrorCode`|Fehlercode, der von einem abgebrochenen Systemauftrag zurückgegeben wurde.|
|`ExecutionTimeSpan`|Die zur Ausführung des Systemauftrags benötigte Zeit.|
|`FriendlyMessage`|Die vom Systemauftrag ausgegebene Meldung.|
|`IsWaitingForEvent`|Gibt an, dass der Systemauftrag auf ein Ereignis wartet.|
|`Message`|Nachricht zum Systemauftrag.|
|`MessageName`|Der Name der Nachricht, von der dieser Systemauftrag aufgerufen wurde.|
|`ModifiedBy`|Eindeutiger Bezeichner des Benutzers, der den Systemauftrag zuletzt geändert hat.|
|`ModifiedOn`|Datum und Uhrzeit der letzten Änderung des Systemauftrags.|
|`Name`|Name des Systemauftrags.|
|`OperationType`|Typ des Systemauftrags. Weitere Informationen finden Sie unter [Vorgangstypen](#operation-types).|
|`OwnerId`|Eindeutiger Bezeichner des für den Systemauftrag zuständigen Benutzers oder Teams.|
|`OwningBusinessUnit`|Eindeutiger Bezeichner der Unternehmenseinheit, die im Besitz des Systemauftrags ist.|
|`OwningExtensionId`|Eindeutiger Bezeichner der besitzenden Erweiterung, der der Systemauftrag zugeordnet ist.|
|`OwningTeam`|Eindeutiger Bezeichner des Teams, das im Besitz des Datensatzes ist.|
|`OwningUser`|Eindeutiger Bezeichner des Benutzers, der im Besitz des Datensatzes ist.|
|`PostponeUntil`|Zeigt an, ob der Systemauftrag nach dem angegebenen Datum und der angegebenen Uhrzeit ausgeführt werden soll. Weitere Informationen: [Verschieben von Systemaufträgen](#postpone-system-jobs)|
|`PrimaryEntityType`|Entitätstyp, dem der Systemauftrag in erster Linie zugeordnet ist.|
|`RecurrencePattern`|Serienmuster von Systemaufträgen. Weitere Informationen: [Wiederholungsstartzeiten und -Muster](#recurrence-start-times-and-patterns)|
|`RecurrenceStartTime`|Startzeit in UTC für das Serienmuster. Weitere Informationen: [Wiederholungsstartzeiten und -Muster](#recurrence-start-times-and-patterns)|
|`RegardingObjectId`|Eindeutiger Bezeichner des Objekts, dem der Systemauftrag zugeordnet ist.|
|`RetryCount`|Anzahl der Wiederholungsversuche für den Systemauftrag.|
|`Sequence` |Reihenfolge, in der Vorgänge übermittelt wurden.|
|`StartedOn`|Datum und Uhrzeit des Starts des Systemauftrags.|
|`StateCode`|Status des Systemauftrags. Weitere Informationen: [Verwalten von Systemauftragsstatus](#manage-system-job-states)|
|`StatusCode`|Grund für den Status des Systemauftrags. Weitere Informationen: [Verwalten von Systemauftragsstatus](#manage-system-job-states)|
|`UTCConversionTimeZoneCode` |Zeitzonencode, der bei Erstellung des Datensatzes verwendet wurde.|
|`WorkflowStageName` |Name einer Workflowphase. |

### <a name="examples"></a>Beispiele

Sie können die folgenden Beispiele verwenden, um Systemauftragsdaten abzurufen

#### <a name="web-api"></a>Web-API

Verwenden Sie die folgende Web-API-Query, um die Attribute in der obigen Tabelle abzurufen. Mehr Informationen: [Datenabfrage über die Web API](webapi/query-data-web-api.md).

```
<organization URL>/api/data/v9.0/asyncoperations?
$select=
asyncoperationid,
completedon,
createdon,
data,
dependencytoken,
depth,
errorcode,
executiontimespan,
friendlymessage,
iswaitingforevent,
message,
messagename,
modifiedon,
name,
operationtype,
_ownerid_value,
postponeuntil,
primaryentitytype,
recurrencepattern,
recurrencestarttime,
_regardingobjectid_value,
retrycount,
sequence,
startedon,
statecode,
utcconversiontimezonecode,
workflowstagename
&$expand=
createdby($select=fullname),
modifiedby($select=fullname),
owningbusinessunit($select=name),
owningextensionid($select=name),
owningteam($select=name),
owninguser($select=fullname)

```

> [!NOTE]
> Mit der Web API gibt es für jede Entität, die Systemaufträge unterstützt, eine einzelwertige Navigationseigenschaft. Der Name dieser Navigationseigenschaft folgt dem Muster `regardingobjectid_<entity logical name>`.

#### <a name="fetchxml"></a>FetchXML

Verwenden Sie das folgende FetchXML, um die Attribute in der obigen Tabelle abzurufen. Weitere Informationen finden Sie unter [Verwendung von FetchXML, um eine Abfrage zu erstellen](use-fetchxml-construct-query.md).

```xml
<fetch>
  <entity name="asyncoperation" >
    <attribute name="asyncoperationid" />
    <attribute name="completedon" />
    <attribute name="createdby" />
    <attribute name="createdon" />
    <attribute name="data" />
    <attribute name="dependencytoken" />
    <attribute name="depth" />
    <attribute name="errorcode" />
    <attribute name="executiontimespan" />
    <attribute name="friendlymessage" />
    <attribute name="iswaitingforevent" />
    <attribute name="message" />
    <attribute name="messagename" />
    <attribute name="modifiedby" />
    <attribute name="modifiedon" />
    <attribute name="name" />
    <attribute name="operationtype" />
    <attribute name="ownerid" />
    <attribute name="owningbusinessunit" />
    <attribute name="owningextensionid" />
    <attribute name="owningteam" />
    <attribute name="owninguser" />
    <attribute name="postponeuntil" />
    <attribute name="primaryentitytype" />
    <attribute name="recurrencepattern" />
    <attribute name="recurrencestarttime" />
    <attribute name="regardingobjectid" />
    <attribute name="retrycount" />
    <attribute name="sequence" />
    <attribute name="startedon" />
    <attribute name="statecode" />
    <attribute name="utcconversiontimezonecode" />
    <attribute name="workflowstagename" />
  </entity>
</fetch>
```

> [!NOTE]
> Jede Entität, die Systemaufträge unterstützt, hat eine aufgelistete n:1-Beziehung mit der `AsyncOperation`-Entität über das `RegardingObjectId`-Suchattribut. Der Name dieser Beziehung folgt dem Muster `<entity schema name>_AsyncOperations`.

### <a name="operation-types"></a>Vorgangstypen

Das [OperationType](reference/entities/asyncoperation.md#BKMK_OperationType)-Attribut beschriebt Kategorien von Systemaufträgen. Viele dieser Typen werden von der Plattform initiiert, um Wartungsaufgaben durchzuführen. 

> [!NOTE]
> Sie können keine Abbruch-, Halte- oder Fortsetzungsvorgänge für von der Plattform generierte Systemaufträge durchführen. 

Einige der Typen dieser plattformgenerierten Aufträge sind in der folgenden Tabelle aufgeführt:

|**OperationType-Wert**|**OperationType-Beschriftung**|
|--|--|
|9|SQM-Datensammlung|
|16|Organisationsstatistiken werden gesammelt.|
|18|Speicherplatzgröße der Organisation wird berechnet.|
|19|Organisationsdatenbankstatistiken werden gesammelt.|
|20|Statistiken zur Organisationsgröße werden gesammelt.|
|22 |Maximale Speicherplatzgröße der Organisation wird berechnet.|
|24|Statistikintervalle werden aktualisiert.|
|25 |Volltextkatalog-Index der Organisation|
|27|Vertragsstatus aktualisieren|
|31|Speicherlimitbenachrichtigung|

### <a name="recurrence-start-times-and-patterns"></a>Wiederholungsstartzeiten und -muster

Wiederkehrende Systemaufträge benötigen Informationen darüber, wann sie beginnen sollten und wie oft sie wiederkehren. Diese Werte sind in den `AsyncOperation` Entitäten `RecurrenceStartTime` und `RecurrencePattern` Attributen gespeichert.

Da Sie `AsyncOperation` Entitäten nicht direkt mit Code erstellen, müssen Sie diese Werte nur interpretieren, wenn Sie die Daten abrufen. Diese Eigenschaften werden Sie nur indirekt festlegen, indem Sie Meldungen verwenden, die neue Systemaufträge erstellen. Die `BulkDelete`- und `BulkDeleteDuplicates`-Meldungen enthalten beide Parameter oder Eigenschaften in den entsprechenden Web-API-Aktionen oder Organisationsservice-anforderungsklassen. Weitere Informationen: <xref:Microsoft.Crm.Sdk.Messages.BulkDetectDuplicatesRequest> Klasse, <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates Action" />, <xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest> Klasse und <xref href="Microsoft.Dynamics.CRM.BulkDelete?text=BulkDelete Action" />

Der `RecurrenceStartTime` ist lediglich ein Datumszeitwert, der angibt, wann der Systemauftrag gestartet werden soll. Wenn er nicht festgelegt ist, wird erwartet, dass der Systemauftrag sofort gestartet wird.

Das Attribut `RecurrencePattern` speichert Informationen darüber, wie häufig wiederkehrende Systemaufträge auftreten. Dieser Wert kann von der Plattform festgelegt werden, wenn eine neue Asynchronisations-Entität erstellt wird. Sie können diesen Wert festlegen, um das Muster zu ändern.

Die Werte für dieses Attribut verwenden Teile des [Internetstandards RFC2445 (Internet Calendaring and Scheduling Core Object Specification)](http://www.rfc-editor.org/info/rfc2445).

Die folgende Tabelle enthält einige Beispiele:

|Serienmuster|Häufigkeit der Auftragsausführung|
|--|--|
|`FREQ=MONTHLY;`|Einmal im Monat|
|`FREQ=WEEKLY;`|Einmal die Woche|
|`FREQ=DAILY;`|Einmal täglich|
|`FREQ=DAILY;INTERVAL=3;`|Alle drei Tage|
|`FREQ=HOURLY;`|Einmal pro Stunde|

Wenn kein `INTERVAL`-Wert festgelegt, wird er als `1` interpretiert.

## <a name="delete-system-jobs"></a>Systemaufträge löschen

Sie können Systemaufträge in der Anwendung oder im Code wie jede andere Entität löschen, wenn Sie über die erforderlichen Berechtigungen verfügen.

> [!NOTE]
> Bei der Registrierung von asynchronen Plugins gibt es die Möglichkeit, erfolgreiche Operationen automatisch zu löschen. Die Verwendung wird empfohlen. Weitere Informationen: [Schreiben eines Plug-Ins](write-plug-in.md)

Die gängige Praxis ist es, einen wiederkehrenden Massenlöschauftrag zu erstellen, der die erfolgreichen Aufträge löscht. Weitere Informationen [Entfernen einer großen Menge spezifischer, gezielter Daten mit Massenlöschung](/dynamics365/customer-engagement/admin/delete-bulk-records)

## <a name="manage-system-job-states"></a>Verwalten von Systemauftragsstatus

Der Status des Systemauftrags ändert sich mehrmals, bis der Vorgang abgeschlossen ist. Nachfolgend sind die `StateCode`- und `StatusCode`-Optionen aufgeführt, die die verfügbaren Werte für Zustand und Statusgrund darstellen:

|StateCode-Wert|StateCode-Beschriftung|StatusCode-Wert|StatusCode-Beschriftung|
|--|--|--|--|
|`0`|Bereit|`0`|Auf Ressourcen wird gewartet|
|`1`|Angehalten|`10`|Es wird gewartet|
|`2`|Gesperrt|`20`|In Bearbeitung|
|`2`|Gesperrt|`21`|Wird angehalten|
|`2`|Gesperrt|`22`|Wird storniert|
|`3`|Abgeschlossen|`30`|Erfolgreich|
|`3`|Abgeschlossen|`31`|Fehler|
|`3`|Abgeschlossen|`32`|Abgesagt|

Sie können den Status von Systemaufträgen in der Anwendung ändern, indem Sie zu **Einstellungen** > **System** > **Systemauftrag** navigieren und die im Menü **Weitere Aktionen** verfügbaren Befehle verwenden.

![Aktionsbefehle, die für Systemaufträge in der Anwendung verfügbar sind.](media/system-jobs-more-actions-commands.png)

> [!NOTE]
> Jede Aktion, die Sie über diese Benutzeroberfläche ausführen können, kann auch per Code durchgeführt werden. Sie können keine Abbruch-, Halte- oder Fortsetzungsvorgänge für von der Plattform generierte Systemaufträge durchführen. Weitere Informationen finden Sie unter [Vorgangstypen](#operation-types).

Zusammen mit den Optionen zur Verwaltung von Ansichten stehen die folgenden Optionen zur Verfügung, um Systemaufträge zu verwalten: 

|Option|Beschreibung|
|--|--|
|Löschen|Verwenden des s ![Befehl löschen](../../maker/common-data-service/media/delete.gif) Befehl.<br />Löscht einen Systemauftrag|
|Massenlöschung|Verwenden des Menüs **Weitere Aktionen**.<br />Öffnet einen Assistenten, um Bedingungen zu definieren und einen neuen Systemauftrag Massenlöschung zu erstellen, um die passenden Systemaufträge zu löschen.|
|Abbrechen|Verwenden des Menüs **Weitere Aktionen**.<br />Storniert den Systemauftrag.|
|Weiter|Verwenden des Menüs **Weitere Aktionen**.<br />Setzt einen angehaltenen Systemauftrag fort.|
|Später durchführen|Verwenden des Menüs **Weitere Aktionen**.<br />Terminiert einen Systemauftrag neu|
|Anhalten|Verwenden des Menüs **Weitere Aktionen**.<br />Pausiert einen Systemauftrag.|

Ob der angeforderte Vorgang eintritt, hängt vom Zustand des Systemauftrags ab. Beispielsweise können Sie einen Auftrag, der bereits abgeschlossen ist oder noch nicht gestartet wurde, nicht pausieren. Die folgende Tabelle beschreibt die Bedingungen für jede Änderung und was passiert, wenn sie ausgewählt wird.

|Option|Gültige StateCode-Werte|Ändern|
|--|--|--|
|Löschen|Beliebig|Systemauftrag wurde gelöscht|
|Abbrechen|0 (Bereit) <br /> 1 (Unterbrochen) <br /> 2 (Gesperrt)|`StateCode` geändert auf 3 (Abgeschlossen) und `StatusCode` geändert auf 32 (Storniert)|
|Weiter|1 (Unterbrochen)|StateCode geändert auf 0 (Bereit)|
|Später durchführen|0 (Bereit) <br />2 (Gesperrt)|Der Zurückstellen eines Auftrags-Dialog fordert den Benutzer auf, den Datums-Zeitwert einzugeben, um den Systemauftrag zu verschieben. Weitere Informationen: [Verschieben von Systemaufträgen](#postpone-system-jobs)|
|Anhalten|2 (Gesperrt)|StateCode geändert auf 1 (Unterbrochen)|


## <a name="postpone-system-jobs"></a>Verschieben von Systemaufträgen

Das `PostPoneUntil`-Attribut enthält einen Datums-Zeitwert, wenn der Systemauftrag den Zustand von 1 (Unterbrochen) auf 0 (Bereit) ändert. Zusammen mit den Attributen `StateCode` und `StatusCode` sind dies die einzigen Attribute, die bei der Verwendung der `AsyncOperation`-Entität zur Aktualisierung unterstützt werden.

### <a name="see-also"></a>Siehe auch

[Schreiben eines Plug-Ins](write-plug-in.md)<br />
[Schreiben von Plug-Ins, um Geschäftsprozesse zu erweitern](plug-ins.md) <br />

