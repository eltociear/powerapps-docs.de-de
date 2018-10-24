---
title: Entitätsmetadaten | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Entitätsmetadaten, die in Common Data Service für Apps verwendet werden.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/19/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 60fafa90df656bb6d135a8cf7e2c2f3b4f8457da
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42840744"
---
# <a name="entity-metadata"></a>Entitätsmetadaten

Jede Entität bietet die Möglichkeit, strukturierte Daten zu speichern. Für Entwickler entsprechen Entitäten den Klassen, die Sie verwenden, wenn Sie mit Daten in Common Data Service für Apps arbeiten.

## <a name="entity-names"></a>Entitätsnamen
Jeder Entität wird bei der Erstellung ein eindeutiger Name zugewiesen. Dieser Name wird auf verschiedene Weisen dargestellt:

|Eigenschaft des Namens |Beschreibung|
|---------|---------|
|`SchemaName`|In der Regel ist dies der logische Name in der Pascal-Schreibweise, z.B. „Account“.|
|`CollectionSchemaName`|Eine Pluralform des Schemanamens, z.B. „Accounts“.|
|`LogicalName`|Der Schemaname nur in Kleinbuchstaben, z.B. „account“.|
|`LogicalCollectionName`|Der Schemaname nur in Kleinbuchstaben, z.B. „accounts“|
|`EntitySetName`|Wird zum Identifizieren von Sammlungen mit der Web-API verwendet. Standardmäßig ist dieser identisch mit dem logischen Namen der Sammlung.<br />Der Name der Entitätenmenge kann durch programmgesteuertes Aktualisieren der Metadaten geändert werden. Dies sollte jedoch nur vorgenommen werden, bevor Web-API-Code für die Entität geschrieben wird. Weitere Informationen finden Sie unter [Dynamics 365 Customer Engagement Developer Guide: Web API types and operations > Change the name of an entity set (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Web-API-Typen und -Vorgänge > Ändern des Namens einer Entitätenmenge)](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations#change-the-name-of-an-entity-set).|

> [!NOTE]
> Wenn Sie eine benutzerdefinierte Entität erstellen, wird dem von Ihnen ausgewählten Namen der Anpassungspräfixwert des Lösungsherausgebers vorangestellt, der mit der Lösung verknüpft ist, in der die Entität erstellt wurde. Sie können den Namen einer Entität nicht wie den Namen der Entitätenmenge ändern, nachdem diese erstellt wurde. Wenn Sie Metadatenelemente in Ihrer Lösung konsistent benennen möchten, sollten Sie diese in dem Kontext einer Lösung erstellen, die Sie mit einer Verknüpfung mit einem Lösungsherausgeber erstellt haben, der das Anpassungspräfix enthält, das Sie verwenden möchten. Weitere Informationen finden Sie unter [Create a solution publisher and solution (Erstellen eines Lösungsherausgebers und einer Lösung)](introduction-solutions.md#create-a-solution-publisher-and-solution).

Außerdem verfügt jede Entität über drei Eigenschaften, die lokalisierte Werte anzeigen können:


|Name  |Beschreibung  |
|---------|---------|
|`DisplayName`|In der Regel mit dem Schemanamen identisch, kann aber auch Leerzeichen enthalten, z.B. „Account“.|
|`DisplayCollectionName`|Eine Pluralform des Anzeigenamens, z.B. „Accounts“.|
|`Description`|Ein kurzer Satz, der die Entität beschreibt, z.B. *Unternehmen, das einen Kunden oder einen potenziellen Kunden darstellt. Das Unternehmen, dem geschäftliche Transaktionen in Rechnung gestellt werden.*|

Dies sind lokalisierbare Werte, die verwendet werden, um auf die Entitäten in einer App zu verweisen. Diese Werte können jederzeit geändert werden. Informationen zum Hinzufügen oder Ändern von lokalisierten Werten finden Sie im [Handbuch für die Anpassung von Dynamics 365: Übersetzen von benutzerdefiniertem Entitäts- und Feldtext in andere Sprachen](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation).


## <a name="primary-key"></a>Primärer Schlüssel

Der Eigenschaftswert `PrimaryIdAttribute` ist der logische Name des Attributs, das der Primärschlüssel der Entität ist.

Standardmäßig verfügen alle Entitäten über ein einzelnes eindeutiges GUID-Bezeichnerattribut. In der Regel trägt dieses den Namen *&lt;logischer Name der Entität&gt;*+ `Id`.

## <a name="primary-name"></a>Primärer Name

Der Eigenschaftswert `PrimaryNameAttribute` ist der logische Name des Attributs, das den Zeichenfolgenwert speichert, der den Datensatz der Entität ermittelt. Dieser Wert wird in einem Link angezeigt, der den Datensatz in einer Benutzeroberfläche öffnet.

**Beispiel**: Die Kontaktentität verwendet das Attribut `fullname` als primäres Namensattribut.

> [!NOTE]
> Nicht jede Entität verfügt über einen primären Namen. Manche Entitäten sollten nicht auf einer Benutzeroberfläche angezeigt werden.

## <a name="entity-images"></a>Entitätsbilder

Der Eigenschaftswert `PrimaryImageAttribute` ist der logische Name des Attributs, das die Bilddaten für den Datensatz der Entität speichert. Jede Entität kann nur über ein Bildattribut verfügen, und der logische Name dieses Attributs ist immer `entityimage`.

**Beispiel**: Das [EntityImage](reference/entities/contact.md#BKMK_EntityImage)-Attribut der [Kontaktentität](reference/entities/contact.md) kann ein Bild des Kontakts speichern.

Aus Leistungsgründen sind Entitätsbilder nicht in Abrufvorgängen enthalten, sofern diese nicht explizit angefordert werden.

Jede Entität, die Entitätsbilder unterstützt, verfügt über drei unterstützende Attribute.

|SchemaName|Typ|Beschreibung|
|--|--|--|
|`EntityImage_Timestamp` |`BigIntType`|Der Wert stellt dar, wann das Bild zuletzt aktualisiert wurde und wird dazu verwendet, sicherzustellen, dass die neueste Version des Bilds heruntergeladen und auf dem Client zwischengespeichert wurde.|
|`EntityImage_URL`|`StringType`|Eine absolute URL zum Anzeigen eines Entitätsbilds in einem Client.|
|`EntityImageId`|`UniqueIdentifierType`|Der eindeutige Bezeichner des Bilds|

Weitere Informationen finden Sie unter: 
- [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Bildattribute](/dynamics365/customer-engagement/developer/image-attributes)
- [Entwicklerhandbuch zu Dynamics 365 Customer Engagement Beispiel: Festlegen und Abrufen von Entitätsbildern](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images)

> [!NOTE]
> Dies unterscheidet sich von dem Symbol, das für eine Entität in modellgesteuerten Apps angezeigt wird. Die Eigenschaft `IconVectorName` enthält den Namen der SVG-Webressource, die diese festlegt.

## <a name="types-of-entities"></a>Typen von Entitäten

Die Funktionen und das Verhalten von Entitäten hängt von verschiedenen Entitätseigenschaften ab. Die meisten dieser Eigenschaften sind relativ einfach aufgebaut und haben beschreibende Namen. Diese vier Eigenschaften erfordern zusätzliche Erläuterungen: *Besitz*, *Aktivitätsentitäten*, *ActivityParty-Entität* und *untergeordnete Entitäten*.

### <a name="entity-ownership"></a>Besitz von Entitäten

Entitäten können nach den Besitzern der Daten kategorisiert werden, die sie enthalten. Das ist ein wichtiges Konzept im Zusammenhang mit der Art und Weise, wie Sicherheit auf Entitäten angewendet wird. Diese Informationen befinden sich in der Eigenschaft `OwnershipType`. Die folgende Tabelle beschreibt die verschiedenen Besitztypen:

|Besitztyp  |Beschreibung  |
|---------|---------|
|Business|Daten, die einer Geschäftseinheit gehören. Der Zugriff auf diese Daten kann auf der Ebene der Geschäftseinheit gesteuert werden.|
|Keine|Daten, die keiner anderen Entität gehören.|
|Organisation|Daten, die der Organisation gehören. Der Zugriff auf diese Daten kann auf der Ebene der Organisation gesteuert werden.|
|Benutzer oder Team|Daten, die einem Benutzer oder einem Team gehören. Aktionen, die auf diese Datensätze verwendet werden können, können auf Benutzerebene gesteuert werden.|

Wenn Sie neue Entitäten erstellen, sind die Folgenden die einzigen verfügbaren Besitzoptionen: **Organisation** oder **Benutzer oder Team**. Sobald Sie sich für eine dieser Optionen entschieden haben, können Sie sie nicht mehr ändern. Wenn Sie auf **Benutzer oder Team** klicken, können Sie im Detail steuern, wer Aktionen für diese Datensätze anzeigen oder ausführen kann. Klicken Sie auf **Organisation**, wenn eine derartige Kontrolle nicht notwendig ist. 

### <a name="activity-entities"></a>Aktivitätsentitäten

Eine Aktivität ist eine Aufgabe, die von einem Benutzer ausgeführt wird oder ausgeführt werden soll. Eine Aktivität ist eine beliebige Aktion, für die ein Eintrag in einem Kalender erstellt werden kann. 

Aktivitäten werden anders als andere Arten von Entitäten modelliert, die Geschäftsdaten speichern. Daten zu Aktivitäten werden zwar häufig zusammen in einer Liste angezeigt, jedoch erfordert jede Aktivität eindeutige Eigenschaften. Sie müssen nicht für jede mögliche Eigenschaft über eine einzelne Aktivitätsentität verfügen: Es gibt separate Arten von Aktivitätsentitäten und jede erbt Eigenschaften von einer zugrunde liegenden [ActivityPoiner-Entität](reference/entities/activitypointer.md). Die Eigenschaft `IsActivity` dieser Aktivitäten ist auf TRUE festgelegt.


|Einrichtung |Beschreibung  |
|---------|---------|
|[Appointment](reference/entities/appointment.md)|Eine Verpflichtung, die ein Zeitintervall mit einer Anfangs- und Endzeit sowie einer Dauer darstellt.|
|[Email](reference/entities/email.md)|Eine Aktivität, die über E-Mail-Protokolle übermittelt wird.|
|[Fax](reference/entities/fax.md)|Eine Aktivität, die Aufrufergebnisse und Seitenanzahlen für ein Fax nachverfolgt und optional eine elektronische Kopie des Elements speichert.|
|[Letter](reference/entities/letter.md)|Eine Aktivität, die die Übermittlung einer Nachricht nachverfolgt. Diese Aktivität kann eine elektronische Kopie der Nachricht enthalten.|
|[PhoneCall](reference/entities/phonecall.md)|Eine Aktivität zum Nachverfolgen eines Anrufs.|
|[RecurringAppointmentMaster](reference/entities/recurringappointmentmaster.md)|Der Mastertermin einer Terminserie.|
|[SocialActivity](reference/entities/socialactivity.md)|Nur zur internen Verwendung.|
|[Task](reference/entities/task.md)|Eine generische Aktivität, die ausstehende Arbeit darstellt.|

Wenn jemand einen dieser Aktivitätsentitäten-Datensätze erstellt, wird eine zugehörige `ActivityPointer`-Entität mit dem gleichen Attributwert des eindeutigen Bezeichners `ActivityId` erstellt. Sie können Instanzen der `ActivityPointer`-Entität nicht erstellen, aktualisieren oder löschen, Sie können sie jedoch abrufen. Deshalb können alle Typen von Aktivitäten gemeinsam in einer Liste angezeigt werden.

Sie können benutzerdefinierte Aktivitätsentitäten erstellen, die dasselbe Verhalten aufweisen.
<!-- TODO: Add link to topic about creating an activity entity -->

### <a name="activityparty-entity"></a>ActivityParty-Entität

Diese Entität wird verwendet, um `PartyListType`-Attribute von Aktivitätsentitäten zu strukturieren, die Verweise auf andere Entitäten enthalten. Verwenden Sie diese Entität, wenn Sie Werte für Attribute von Aktivitätsentitäten festlegen, z.B. `Email.to` oder `PhoneCall.from`. Legen Sie das Attribut [ParticipationTypeMask](reference/entities/activityparty.md#BKMK_ParticipationTypeMask) in der [ActivityParty-Entität](reference/entities/activityparty.md) fest, um die Rolle des Verweises zu definieren. Rollen umfassen u.a. `Sender`, `ToRecipient` und `Organizer`.

Sie können zwar die `ActivityParty`-Entität abfragen, aber Sie können keine ActivityParty-Entität außerhalb einer zugehörigen Aktivität erstellen, abrufen, aktualisieren oder löschen.
Weitere Informationen finden Sie unter: 
- [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: ActivityParty-Entität](/dynamics365/customer-engagement/developer/activityparty-entity)


### <a name="child-entities"></a>Untergeordnete Entitäten

Für Entitäten, deren `IsChildEntity`-Eigenschaft auf TRUE festgelegt ist, werden keine Berechtigungen definiert, und ihr Besitzer ist nie ein Benutzer oder Team. Vorgänge, die auf eine untergeordnete Entität angewendet werden können, werden an eine Entität gebunden, der sie über eine n:1-Beziehung zugeordnet sind. Benutzer können Vorgänge nur auf eine untergeordnete Entität anwenden, wenn sie den gleichen Vorgang auf eine verknüpfte Entität anwenden können. Untergeordnete Entitäten werden automatisch gelöscht, wenn der Datensatz der Entität gelöscht wird, von dem sie abhängig sind.

Zum Beispiel sind `PostComment`, `PostLike` und `PostRole` untergeordnete Entitäten der `Post`-Entität.

## <a name="entity-keys"></a>Entitätsschlüssel

Jede alternative Schlüsseldefinition beschreibt mindestens ein Attribut, das eine Entitätsinstanz eindeutig identifiziert. Alternative Schlüssel werden in der Regel nur bei der Integration in externe Systeme angewendet. Sie können alternative Schlüssel definieren, um einen Datensatz eindeutig zu identifizieren. Das ist beim Integrieren von Daten in ein System hilfreich, das keine eindeutigen Schlüssel für GUID-Bezeichner unterstützt. Sie können einen einzelnen Feldwert oder eine Kombination von Feldwerten definieren, um eine Entität eindeutig zu identifizieren. Das Hinzufügen eines alternativen Schlüssels erzwingt eine Eindeutigkeitseinschränkung für diese Attribute. Sie können keinen weiteren Entitätsdatensatz erstellen oder aktualisieren, sodass dieser die gleichen Werte aufweist.

Weitere Informationen finden Sie unter: 
 - [Handbuch zur Anpassung von Dynamics 365 Customer Engagement: Definieren von Alternativschlüsseln für den Verweis auf Dynamics 365-Datensätze](/dynamics365/customer-engagement/customize/define-alternate-keys-reference-records)
 - [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Synchronisieren von Dynamics 365-Daten mit externen Systemen](/dynamics365/customer-engagement/developer/synchronize-dynamics-365-data-with-external-systems)

## <a name="entity-states"></a>Status von Entitäten

Die meisten Entitäten verfügen über zwei Eigenschaften, um den Status eines Datensatzes nachzuverfolgen. Diese sind in modellgesteuerten Apps `StateCode` mit dem Namen **Status** und `StatusCode` mit dem Namen **Statusursache**. 

Beide Attribute enthalten mehrere Optionen zum Anzeigen der gültigen Werte. Die Attributwerte `StateCode` und `StatusCode` sind miteinander verknüpft, sodass nur bestimmte `StatusCode`-Optionen für einen bestimmten `StateCode` gültig sind.

Dies kann zwar je nach Entität variieren, aber bei vielen Entitäten ist das Folgende das allgemeine Muster und der Standard für benutzerdefinierte Entitäten:

|StateCode-Optionen  |StatusCode-Optionen  |
|---------|---------|
|0: Aktiv|1: Aktiv|
|1: Inaktiv|2: Inaktiv|

Manche Entitäten verfügen über unterschiedliche Optionen. 

**Beispiel**: Die Optionen `StateCode` und `StatusCode` der `PhoneCall`-Entität


|`StateCode`|`StatusCode`|
|---------|---------|
|0: Offen|1: Offen|
|1: Abgeschlossen|2: Vorgenommen <br />4: Empfangen|
|2: Abgebrochen|3: Abgebrochen|

Die Gruppe der gültigen Statuscodes für eine Entität sind nicht anpassbar, die Statuscodes hingegen schon. Sie können zusätzliche `StatusCode`-Optionen für einen entsprechenden `StateCode` hinzufügen.

Bei benutzerdefinierten Entitäten können Sie zusätzliche Kriterien für gültige Übergänge zwischen Status definieren. Weitere Informationen finden Sie unter: 
- [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Anpassen von Entitätsattributmetadaten](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)
- [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Definieren von benutzerdefinierten Statusmodellübergängen](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions)

### <a name="see-also"></a>Siehe auch

[Entitäten in Common Data Service für Apps](entities.md)
