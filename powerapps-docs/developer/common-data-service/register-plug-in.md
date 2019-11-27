---
title: Registrieren eines Plug-Ins (Common Data Service) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Plug-In registrieren, um benutzerdefinierte Geschäftslogik auf Common Data Service anzuwenden.
ms.custom: ''
ms.date: 02/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 893e10844ee6e4c5f4e35b228d23ddf06e3c90e7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748659"
---
# <a name="register-a-plug-in"></a>Registrieren eines Plug-Ins


Der Prozess des Schreibens, Registrierens und Debuggens eines Plugins ist:

1. Erstellen Sie ein .NET Framework-Klassenbibliotheksprojekt in Visual Studio
1. Fügen Sie das `Microsoft.CrmSdk.CoreAssemblies` NuGet-Paket dem Projekt hinzu
1. Implementieren Sie die <xref:Microsoft.Xrm.Sdk.IPlugin>-Schnittstelle in Klassen, die als Schritte registriert werden.
1. Fügen Sie Ihren Code der <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*>-Methode hinzu, die für die Schnittstelle erforderlich ist
    1. Rufen Sie Referenzen auf Dienste ab, die Sie benötigen
    1. Fügen Sie Ihre Geschäftslogik hinzu
1. Signieren und erstellen Sie die Assembly
1. Testen des Assemblys.
    1. **Registrieren der Assembly in einer Testumgebung**
    1. **Hinzufügen der registrierten Assembly und Schritte zu einer nicht verwalteten Lösung**
    1. Testen des Verhaltens der Assembly
    1. Überprüfen, ob erwartete Ablaufverfolgungsprotokolle geschrieben werden
    1. Debuggen der Assembly nach Bedarf


Inhalt in diesem Thema beschreibt die Schritte **in fett** oben und unterstützt die folgenden Tutorials:

- [Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md)
- [Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md)
- [Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md)

## <a name="plugin-registration-tool-prt"></a>Plugin Registration Tool (PRT)

Sie verwenden das Plugin Registration Tool (PRT), um Ihre Plug-In-Assemblys und Schritte zu registrieren.

PRT ist eines der Tools, die als Download von NuGet verfügbar sind. Führen Sie die Anweisungen unter [Herunterladen von Tools von NuGet](download-tools-nuget.md) aus. Dieses Thema enthält Anweisungen zur Verwendung eines PowerShell-Skripts, um die aktuellen Tools von NuGet herunterzuladen.

Nachdem Sie das PRT heruntergeladen haben, führen Sie die Schritte unter [Herstellen einer Verbindung über das Plugin Registration Tool (PRT)](tutorial-write-plug-in.md#connect-using-the-plug-in-registration-tool) im [Lernprogramm: Schreiben und Registrieren eines Plug-Ins](tutorial-write-plug-in.md) aus, um eine Verbindung zu Ihrer Common Data Service-Umgebung herzustellen.

## <a name="register-an-assembly"></a>Registrieren einer Assembly

Eine Assembly zu registrieren, ist der Prozess des Hochladens der Assembly in die Common Data Service-Datenbank. Lesen Sie die Anweisungen unter [Registrieren der Assembly](tutorial-write-plug-in.md#register-your-assembly) im [Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md)

> [!NOTE]
> Sie finden die Optionen, die mit dem *Isolationsmodus* und *Speicherort* der Assembly verknüpft sind. Diese beziehen sich auf Optionen, die für lokale Bereitstellungen gelten. Common Data Service ist nicht für lokale Bereitstellungen verfügbar. Deshalb akzeptieren Sie immer die Standardoptionen **SandBox** und **Datenbank** für diese Optionen.

Wenn eine Assembly hochgeladen wird, wird sie in der Entität `PluginAssembly` gespeichert. Die meisten Eigenschaften werden mithilfe der Reflektion der importierten Entität festgelegt. Die base64-codierten Bytes der Assembly werden im Attribut `Content` gespeichert. Beim Anzeigen der **Eigenschaften** der Assembly im PRT können Sie nur den Attributwert **Description** bearbeiten.

### <a name="view-registered-assemblies"></a>Anzeigen registrierter Assemblys

Sie können Informationen zu registrierten Assemblys im Anwendungsprojektmappen-Explorer anzeigen, ohne das PRT zu verwenden.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

> [!NOTE]
> Jede Assembly, die Sie mithilfe des PRT hinzufügen, wird zur **Standardlösung** des Systems hinzugefügt, (nicht zu verwechseln mit der **Standardlösung von Common Data Services**). Um die **Standardlösung** anzuzeigen, wählen Sie **Alle Lösungen** unter **Lösungen** und ändern die Ansicht zu **Alle Lösungen – intern**.
> 
> Weitere Informationen zu Lösungen finden Sie unter [Einführung in Lösungen](introduction-solutions.md).

![Alle Lösungen – intern](media/all-solutions-internal-view.png)

Hier können Sie alle Assemblys suchen, die für diese Umgebung registriert sind.

![Alle registrierten Assemblys anzeigen](media/view-plug-in-assemblies-default-solution.png)

### <a name="query-registered-assemblies-with-code"></a>Registrierte Assemblys mit Code abfragen

Um Informationen zu registrierten Assemblys ohne das PRT oder die Anwendung anzuzeigen, verwenden Sie die folgende Web API-Abfrage in Ihrem Browser:

```
[org uri]]/api/data/v9.0/pluginassemblies
?$filter=ishidden/Value eq false
&$select=
createdon,
culture,
customizationlevel,
description,
isolationmode,
major,
minor,
modifiedon,
name,
pluginassemblyid,
publickeytoken,
version
```

Oder verwenden Sie das folgende FetchXml, um sie in einem von Ihnen geschriebenen Programm abzurufen:

```xml
<fetch>
  <entity name='pluginassembly' >
    <attribute name='createdon' />
    <attribute name='culture' />
    <attribute name='customizationlevel' />
    <attribute name='description' />
    <attribute name='isolationmode' />
    <attribute name='major' />
    <attribute name='minor' />
    <attribute name='modifiedon' />
    <attribute name='name' />
    <attribute name='pluginassemblyid' />
    <attribute name='publickeytoken' />
    <attribute name='version' />
    <filter type='and' >
      <filter>
        <condition attribute='ishidden' operator='eq' value='false' />
      </filter>
    </filter>
  </entity>
</fetch>
```
Weitere Informationen: [Verwendung von FetchXML mit FetchExpression](org-service/entity-operations-query-data.md#use-fetchxml-with-fetchexpression)

## <a name="add-your-assembly-to-a-solution"></a>Hinzufügen der Assembly zu einer Lösung

Wie in [Anzeigen registrierter Assemblys](#view-registered-assemblies) beschrieben, wurde die Assemblyregistrierung, die Sie erstellt haben, der **Standardlösung** des Systems hinzugefügt. Sie sollten die Assembly einer nicht verwalteten Lösung hinzufügen, sodass Sie sie an andere Organisationen verteilen können.

Innerhalb der nicht verwalteten Lösung, die Sie verwenden, wechseln Sie mithilfe des Projektmappen-Explorers zu **Plug-In-Assemblys**. Wählen Sie im Listenmenü **Vorh. hinzufügen** aus.

![Hinzufügen einer vorhandenen Plug-In-Assembly](media/add-existing-plug-in-assembly.png)

Fügen Sie die Assembly anschließend als Komponente zur Lösung hinzu.

![Plug-In-Assembly als Lösungskomponente auswählen](media/select-plug-in-assembly-as-solution-component.png)

Wenn Sie die Plug-In-Assembly auswählen, die Sie hinzugefügt haben, können Sie die Plug-In-Klassen anzeigen, die in ihr enthalten sind.

![Plug-In-Assemblys und -Klassen](media/view-plug-in-classes-solution-explorer.png)

> [!NOTE]
> Vorhandene oder nachfolgende Schrittregistrierungen werden nicht zur nicht verwalteten Lösung hinzugefügt, die die Plug-In-Assemblys enthält. Sie müssen der Lösung jeden registrierten Schritt separat hinzufügen. Weitere Informationen: [Hinzufügen eines Schritts zur Lösung](#add-step-to-solution)

## <a name="register-plug-in-step"></a>Registrieren des Plug-In-Schritts

Wenn eine Assembly geladen oder aktualisiert wird, sind alle Klassen, die <xref:Microsoft.Xrm.Sdk.IPlugin> implementieren, im PRT verfügbar. Verwenden Sie die Anweisungen unter [Registrieren eines neuen Schritts](tutorial-write-plug-in.md#register-a-new-step) im [Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md), um eine neue Schrittregistrierung zu erstellen.

Wenn Sie einen Schritt registrieren, gibt es viele Optionen, die für Sie verfügbar sind, die von der Phase der Ereignispipeline und die Art des Vorgangs abhängen, für die Sie eine Reaktion Ihres Codes registrieren können.

### <a name="general-configuration-information-fields"></a>Allgemeine Konfigurationsinformaitonsfelder

|Feld|Beschreibung|
|--|--|
|**Meldung**|PRT vervollständigt automatisch verfügbare Nachrichtennamen im System. Weitere Informationen: [Verwenden von Meldungen mit dem Organisationsservice](org-service/use-messages.md)|
|**Primäre Entität**|PRT vervollständigt automatisch gültige Entitäten, die für die ausgewählte Message gelten. Diese Meldungen enthalten einen `Target`-Parameter, der als Typ <xref:Microsoft.Xrm.Sdk.Entity> oder <xref:Microsoft.Xrm.Sdk.EntityReference> akzeptiert. Wenn gültige Entitäten zutreffen, sollten Sie diese festlegen, wenn Sie die Häufigkeit der Plug-In-Aufrufe beschränken möchten. <br />Wenn Sie dies für Kernentitätsmeldungen wie `Update`, `Delete`, `Retrieve` und `RetrieveMultiple` freilassen, oder für Meldungen, die mit der Message angewendet werden können, wird das Plug-In für alle Entitäten aufgerufen, die diese Message unterstützen.|
|**Sekundäre Entität**|Dieses Feld wird für Abwärtskompatibilität für veraltete Meldungen beibehalten, die den Array <xref:Microsoft.Xrm.Sdk.EntityReference> als `Target`-Parameter akzeptierten. Dieses Feld wird in der Regel nicht mehr verwendet.|
|**Filterattribute**|Wenn Sie bei der Message `Update` die **Primäre Entität** festlegen, wird durch Filtern von Attributen die Ausführung des Plug-Ins auf solche Fälle eingeschränkt, bei denen die ausgewählten Attribute im Update enthalten sind. Dies ist eine bewährte Methode für die Leistung. |
|**Ereignishandler**|Dieser Wert wird anhand des Namens der Assembly und der Plug-In-Klasse automatisch aufgefüllt. |
|**Schrittname**|Der Name des Schritts. Ein Wert wird auf der Basis der Konfiguration des Schritts automatisch aufgefüllt, aber dieser Wert kann überschrieben werden.|
|**Im Kontext des Benutzers ausführen**|Stellt Optionen zum Anwenden des Identitätswechsels für den Schritt bereit. Der Standardwert ist **Aufrufender Benutzer**. Wenn der aufrufende Benutzer keine ausreichenden Rechte besitzt, um Vorgänge im Schritt auszuführen, müssen Sie dies ggf. für einen Benutzer mit solchen Rechten festlegen. Weitere Informationen: [Annehmen der Identität eines Benutzers](impersonate-a-user.md) |
|**Ausführungsreihenfolge**|Mehrere Schritte können für dieselbe Phase derselben Nachricht registriert werden. Der Wert in diesem Feld bestimmt die Reihenfolge, in der sie vom niedrigsten bis hin zum höchsten angewendet werden. <br/> **Hinweis**: Sie sollten dies einstellen, um die Reihenfolge zu steuern, in der Plug-Ins im Stadium angewendet werden. Es wird nicht empfohlen, einfach den Standardwert zu übernehmen. Wenn alle Plugins für die gleiche Stufe, Entität und Nachricht den gleichen Wert haben, bestimmt der Wert von [SdkMessageProcessingStep.SdkMessageFilterId](/dynamics365/customer-engagement/developer/entities/sdkmessageprocessingstep#BKMK_SdkMessageFilterId) die Reihenfolge, in der sie ausgeführt werden.|
|**Beschreibung**|Eine Beschreibung des Schritts. Dieser Wert ist vorbelegt, kann aber überschrieben werden.|

> [!NOTE]
> Es gibt bestimmte Fälle, in denen für das Ereignis `Update` registrierte Plugins zweimal aufgerufen werden können. Weitere Informationen: [Verhalten spezieller Vorgänge mithilfe Update](special-update-operation-behavior.md)


### <a name="event-pipeline-stage-of-execution"></a>Ereignis-Pipeline-Phase der Ausführung

Wählen Sie die Phase in der Ereignis-Pipeline aus, die für den Zweck Ihres Plug-Ins optimal geeignet ist.

|Option|Beschreibung|
|--|--|
|**PreValidation**|[!INCLUDE [cc-prevalidation-description](../../includes/cc-prevalidation-description.md)]|
|**PreOperation**|[!INCLUDE [cc-preoperation-description](../../includes/cc-preoperation-description.md)]|
|**PostOperation**|[!INCLUDE [cc-postoperation-description](../../includes/cc-postoperation-description.md)]|

Weitere Informationen: [Ereignisausführungspipeline](event-framework.md#event-execution-pipeline)

### <a name="execution-mode"></a>Ausführungsmodus

Es gibt zwei Modi der Ausführung, asynchron und synchron.

|Option|Beschreibung|
|--|--|
|**Asynchron**|Der Ausführungskontext und die Definition der Geschäftslogik, die angewendet werden soll, werden zum Systemauftrag verschoben, der ausgeführt wird, wenn der Vorgang abgeschlossen wurde.|
|**Synchron**|Plug-Ins werden sofort gemäß der Phase der Ausführung und der Ausführungsreihenfolge ausgeführt. Der gesamte Vorgang wartet, bis sie ausgeführt wurden.|

Asynchrone Plug-Ins können nur für die Phase **PostOperation** registriert werden. Weitere Informationen darüber, wie Systemaufträge funktionieren, finden Sie unter [Asynchroner Service](asynchronous-service.md).

### <a name="deployment"></a>Bereitstellung

|Option|Beschreibung|
|--|--|
|**Server**|Das Plug-In wird auf dem Common Data Service-Server ausgeführt.|
|**Offline**|Das Plug-In wird innerhalb des Dynamics 365 for Outlook-Clients ausgeführt, wenn der Benutzer im Offlinemodus ist.|

<!-- TODO Add link to where more information about offline-plugins will be documented -->

### <a name="set-configuration-data"></a>Konfigurationsdaten festlegen

Die Felder **Unsichere Konfiguration** und **Sichere Konfiguration** ermöglichen Ihnen, Konfigurationsdaten anzugeben, die dem Plug-In für einen bestimmten Schritt zu übergeben sind.

Sie können Ihr Plug-In so schreiben, dass es Zeichenfolgenwerte im Konstruktor annimmt, um mit diesen Daten zu steuern, wie das Plug-In für den Schritt verwendet werden soll. Weitere Informationen: [Konfigurationsdaten Ihrem Plug-In übergeben](write-plug-in.md#pass-configuration-data-to-your-plug-in)

### <a name="define-entity-images"></a>Definieren von Entitätsbildern

Innerhalb des Plug-Ins sollten Sie auf Eigenschaftswerte der primären Entität verweisen, die in einem Vorgang nicht enthalten waren. Beispielweise möchten Sie in einem `Update`-Vorgang ggf. wissen, was der Wert war, bevor er geändert wurde, aber der Ausführungskontext bietet diese Informationen nicht, er enthält lediglich den geänderten Wert. 

Wenn das Plug-In in den Phasen **PreValidation** oder **PreOperation** der Ausführungspipeline registriert ist, können Sie den Organisationsservice verwenden, um den aktuellen Wert der Eigenschaft abzurufen, dies ist jedoch keine bewährte Methode für die Leistung. Eine bessere Methode ist, ein Vorentitätsbild mit der Schrittregistrierung des Plug-Ins zu definieren. Dadurch wird eine Momentaufnahme der Entität mit den Feldern erfasst, für die Sie sich interessieren, so wie sie vor dem Vorgang existierten, und die Sie verwenden können, um sie mit den geänderten Werten zu vergleichen. 

#### <a name="messages-that-support-entity-images"></a>Nachrichten, die Entitätsbilder unterstützen

In Common Data Service unterstützen nur die folgenden Meldungen Entitätsbilder:

|Meldung|Anforderungs-Klassen-Eigenschaft| Beschreibung|
|--|--|--|
|`Assign`|`Target`|Die zugewiesene Entität.|
|`Create`|`Target`|Die erstellte Entität.|
|`Delete`|`Target`|Die gelöschte Entität.|
|`DeliverIncoming`|`EmailId`|Die zugestellte E-Mail-ID.|
|`DeliverPromote`|`EmailId`|Die zugestellte E-Mail-ID.|
|`Merge`|`Target` oder `SubordinateId`|   Die übergeordnete Entität, in der die Daten aus der untergeordneten Entität zusammengeführt werden, oder die untergeordnete Entität, die in der übergeordneten Entität zusammengeführt wird.|
|`Route`|`Target`|Das Element, das weitergeleitet wird.|
|`Send`|`FaxId`, `EmailId` oder `TemplateId` |Das Element, das gesendet wird.|
|`SetState`|`EntityMoniker`|Die Entität, für die der Status festgelegt ist.|
|`Update`|`Target`|Die aktualisierte Entität.|


#### <a name="types-of-entity-images"></a>Typen von Entitätsbildern

Es gibt zwei Typen von Entitätsbildern: **Vorheriges Bild** und **Späteres Bild**. Wenn Sie sie konfigurieren, sind diese Bilder im Ausführungskontext als Eigenschaft <xref:Microsoft.Xrm.Sdk.IExecutionContext.PreEntityImages> bzw. Eigenschaft <xref:Microsoft.Xrm.Sdk.IExecutionContext.PostEntityImages> verfügbar. Wie die Namen schon sagen, stellen diese Momentaufnahmen dar, wie die Entität vor und nach dem Vorgang aussieht. Wenn Sie ein Entitätsbild konfigurieren, definieren Sie einen *Entitätsalias*-Wert, der wie ein Schlüsselwert ist, den Sie verwenden, um auf ein bestimmtes Entitätsbild von den Eigenschaften `PreEntityImages` oder `PostEntityImages` zuzugreifen.

#### <a name="availability-of-images"></a>Verfügbarkeit von Bildern

Wenn Sie ein Entitätsbild konfigurieren, ist es wichtig, zu erkennen, dass der Typ der verfügbaren Entitätsbildern von der Phase des registrierten Schritts und vom Typ des Vorgangs abhängig ist. Beispiel:

- Sie können kein **Vorheriges Bild** für die `Create`-Message haben, da die Entität noch nicht vorhanden ist.
- Sie können kein **Späteres Bild** für die `Delete`-Message haben, da die Entität nicht mehr vorhanden sein wird.
- Sie können nur ein **Späteres Bild** für Schritte haben, die in der Phase **PostOperation** der Ausführungspipeline registriert sind, da es keine Möglichkeit gibt, zu wissen, was die Entitätseigenschaften sein werden, bis die Transaktion abgeschlossen ist.
- Für einen `Update`-Vorgang, der in der Phase **PostOperation** registriert ist, können Sie ein **Vorheriges Bild** UND ein **Späteres Bild** haben.


#### <a name="add-an-entity-image"></a>Hinzufügen eines Entitätsbilds

Unter dem Schritt [Hinzufügen eines Bilds](tutorial-update-plug-in.md#add-an-image)im [Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md) finden Sie die Schritte, um ein Entitätsbild hinzuzufügen.

### <a name="add-step-to-solution"></a>Hinzufügen eines Schritts zur Lösung

Wie unter [Hinzufügen einer Assembly zu einer Lösung ](#add-your-assembly-to-a-solution) beschrieben, sind **Plug-In-Assemblys** Lösungskomponenten, die einer nicht verwalteten Lösung hinzugefügt werden können. **SDK-Nachrichtenverarbeitungsschritte** sind auch Lösungskomponenten und müssen zu einer nicht verwalteten Lösung hinzugefügt werden, damit sie verteilt werden können.

Die Vorgehensweise zum Hinzufügen eines Schritts zu einer Lösung ist mit dem Hinzufügen einer Assembly vergleichbar. Sie verwenden den Befehl **Vorhandenes Element hinzufügen**, um ihn zur gewünschten, nicht verwalteten Lösung zu verschieben. Der einzige Unterschied ist, dass Sie, wenn Sie versuchen, einen Schritt hinzuzufügen, ohne zuvor die Assembly hinzugefügt zu haben, die die im Schritt verwendete Klasse enthält, aufgefordert werden, fehlende erforderliche Komponenten hinzuzufügen.

![Dialogfeld "Fehlende erforderliche Komponenten"](media/missing-required-component.png)

Wenn dies auftritt, sollten Sie gewöhnlich **OK** auswählen, um die Assembly mit der nicht verwalteten Lösung zu übertragen. Der einzige Umstand, unter dem Sie dies nicht wählen würden, ist, wenn Ihre Lösung zur Installation in einer Umgebung konzipiert ist, in der eine andere Lösung, welche die Assembly enthält, bereits installiert ist.

Entsprechend sollten Sie beachten, dass durch Entfernen der Assembly aus der Lösung keine Schritte entfernt werden, die von ihr abhängig sind.

## <a name="update-an-assembly"></a>Aktualisieren einer Assembly

Wenn Sie eine Assembly ändern und neu erstellen, die Sie bereits registriert haben, müssen Sie sie aktualisieren. Weitere Schritte finden Sie unter dem Schritt [Aktualisieren der Plug-In-Assemblyregistrierung](tutorial-update-plug-in.md#update-the-plug-in-assembly-registration) im [Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md).

### <a name="assembly-versioning"></a>Assemblyversionsverwaltung

Wenn Sie Änderungen an einer Plug-In-Assembly vornehmen, die Teil einer vewalteten Lösung ist, die bereitgestellt wurde, müssen Sie die möglichen Auswirkungen Ihrer Änderungen berücksichtigen, wenn Sie diese verwaltete Lösung aktualisieren. Die Version der Assembly steuert das Verhalten.

Die Version von Plug-In-Assemblys kann mit Hilfe des semantischen Versionsverwaltungsformats `major.minor.build.revision` verwaltet werden, das in der Datei `Assembly.info` des Microsoft Visual Studio-Projekts definiert wurde. Abhängig vom Teil der Assemblyversionsnummer, der für eine neuere Lösung geändert wird, gilt das folgende Verhalten, wenn eine vorhandene Lösung durch einen Import aktualisiert wird.

- **Die Versionsnummer des Builds oder der Revisionsassembly wird geändert**

  Dies wird als direktes Upgrade bezeichnet. Die ältere Version der Assembly wird beim Import der Lösung entfernt, die die aktualisierte Assembly enthält. Alle bereits vorhandenen Schritte der älteren Lösung werden automatisch auf die neuere Version der Assembly geändert.

- **Die Haupt- oder Nebenversionsnummer wird geändert**

  Wenn eine aktualisierte Lösung importiert wird, in der die überarbeitete Assembly enthalten ist, wird die Assembly als eine völlig andere Assembly eingestuft, als die frühere Version dieser Assembly in der vorhandenen Lösung. Die Registrierungsschritte für Plug-Ins in der vorhandenen Lösung beziehen sich weiterhin auf die frühere Version der Assembly. Wenn Sie möchten, dass die von der vorherigen Assembly vorhandenen Registrierungsschritte des Plug-Ins auf die bearbeitete Assembly verweisen, müssen Sie das Plug-In-Registrierungstool zur manuellen Änderung der Schrittkonfiguration verwenden, damit diese auf den bearbeiteten Assemblytyp verweist. Dies sollte durchgeführt werden, bevor Sie die aktualisierte Assembly für den späteren Import in eine Lösung exportieren.


## <a name="unregister-or-disable-plug-in-components"></a>Aufheben der Registrierung oder Deaktivieren von Plug-In-Komponenten

Sie können Plug-In-Komponenten abmelden oder deaktivieren.

### <a name="unregister-components"></a>Aufheben der Registrierung von Komponenten

Das PRT bietet Befehle zum Aufheben der Registrierung von Assemblys, Typen, Schritten und Images. Die Vorgehensweise finden Sie unter den Anweisungen [Aufheben der Registrierung für Assembly, Plug-In und Schritt](tutorial-update-plug-in.md#unregister-assembly-plug-in-and-step) im [Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md).

Dies sind Löschvorgänge für die Entitäten [PluginAssembly](reference/entities/pluginassembly.md), [PluginType](reference/entities/plugintype.md), [SdkMessageProcessingStep](reference/entities/sdkmessageprocessingstep.md) und [SdkMessageProcessingStepImage](reference/entities/sdkmessageprocessingstepimage.md).

Sie können auch **Plug-In-Assemblys** und **SDK-Nachrichtenverarbeitungsschritte** im Projektmappen-Explorer löschen, um dasselbe Ergebnis zu erzielen.

![Löschen eines Schritts im Projektmappen-Explorer](media/delete-sdk-message-processing-step.png)

> [!NOTE]
> Sie können keine **Plug-In-Assemblys** löschen, während vorhandene **SDK-Nachrichtenverarbeitungsschritte** davon abhängig sind. Entitätsbilder sind nicht zum separaten Löschen verfügbar, aber sie werden gelöscht, wenn Schritte, die sie verwenden, gelöscht werden.

### <a name="disable-steps"></a>Deaktivieren von Schritten

Das PRT bietet Befehle zum Dekativieren und Aktivieren von Schritten.

![Deaktivieren eines Schritts mit dem PRT](media/disable-step-prt.png)

![Aktivieren eines Schritts mit dem PRT](media/enable-step-prt.png)

Sie können auch Schritte im Projektmappen-Explorer deaktivieren, indem Sie die Befehle **Aktivieren** und **Deaktivieren** verwenden.

![foo](media/step-activate-deactivate-commands-solution-explorer.png)

## <a name="next-steps"></a>Nächste Schritte

[Debuggen von Plug-Ins](debug-plug-in.md)

### <a name="see-also"></a>Siehe auch
[Schreiben von Plug-Ins, um Geschäftsprozesse zu erweitern](plug-ins.md)<br />
[Schreiben eines Plug-Ins](write-plug-in.md)<br />
[Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md)<br />
[Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md)<br />
[Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md)<br />
