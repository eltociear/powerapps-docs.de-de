---
title: Entitätmetadaten| Microsoft Docs
description: Weitere Informationen über die Verwendung von Attributmetadaten in Common Data Service.
services: ''
suite: powerapps
documentationcenter: na
author: mayadumesh
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7c6845a68f5f076b668f3604fe899991827077f2
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748293"
---
<!-- 
Was Mike Carter
This topic was not migrated it was written for PowerApps 

Overlap with content in https://docs.microsoft.com/dynamics365/customer-engagement/developer/introduction-entities

-->
# <a name="entity-metadata"></a>Entitätsmetadaten

Jede Entität enthält die Funktion, strukturierte Daten zu speichern. Für Entwickler entsprechen Entitäten den Klassen, die Sie beim Arbeiten mit Daten in Common Data Service verwenden.

## <a name="entity-names"></a>Entitätsnamen
Jede Entitäten hat einen eindeutig definierten Namen, wenn es erstellt wird, Dieser Name ist auf verschiedene Weise dargestellt:

|Eigenschaftenname |Beschreibung|
|---------|---------|
|`SchemaName`|In der Regel eine Pascal-umkleidete Version des logischen Namen. z. B.Debitorenkonto|
|`CollectionSchemaName`|Eine mehrzahlige Version des Anzeigenamens. z. B. Konto|
|`LogicalName`|Alle kleingeschriebene Version des Schemanamens. z. B. Konto|
|`LogicalCollectionName`|Alle kleingeschriebene Versionen des Schemanamens. z. B. Konto|
|`EntitySetName`|Verwendet. um Sammlungen mit Internet API zu identifizieren. Standardmäßig ist sie gleich wie der logische Sammlungsname.<br />Es ist möglich den Namen einer Entität zu ändern, indem programmgesteuert die Metadatenänderung aktualisiert wird. Dies sollte nur gemacht werden, bevor der Internet API-Code für die Entität erstellt wird. Weitere Informationen: [Web API Typen und Vorgänge > Änderung der Name eines Entitätssatzes](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations#change-the-name-of-an-entity-set)|

> [!NOTE]
> Wenn Sie ein benutzerdefiniertes Entität erstellen, wird der Name, den Sie auswählen, mit dem Anpassungspräfixwert des Lösungsherausgebers verwendet, der mit der Lösung zugeordnet wird, als die Entitä erstellt wurde. Im Gegensatz zum Festlegen des Namens der Entität können Sie den Namen der Entität nach dem Erstellen nicht mehr ändern. Wenn Sie konstante Namen für Metadatenelemente in der Lösung möchten, können Sie sie im Kontext einer Lösung erstellen, die Sie zu einem Lösungsherausgeber zuordnen, der das Anpassungspräfix enthält, das Sie verwenden möchten. Weitere Informationen: [Erstellen eines Lösungsherausgebers und eine Lösung](introduction-solutions.md#create-a-solution-publisher-and-solution)

Jedes Entität weist auch drei Eigenschaften auf, die lokalisierte Werte anzeigen.


|Name  |Beschreibung  |
|---------|---------|
|`DisplayName`|Normalerweise gleich wie der Schemaname, können aber Leerzeichen enthalten. z. B.Debitorenkonto|
|`DisplayCollectionName`|Eine mehrzahlige Version des Anzeigenamens. z. B. Konto|
|`Description`|Ein kurzer SAtz, der die Entität beschreibt, z.B. *Ein Geschäft, das einen Kunden oder einen potenziellen Kunden darstellt. Das Unternehmen, mit dem Geschäftstransaktionen abgerechnet werden.*|

Dies sind die Lokalisierungswerte, die verwendet werden, um sich auf die Entität in einer App zu beziehen. Diese Werte können jederzeit geändert werden. Um die lokalisierten Werte hinzuzufügen oder zu bearbeiten gehen Sie zu [Common Data Service-Anpassungs-Handbuch:  Angepassten Entitäts- und Feldtext in andere Sprachen übersetzen](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation).


## <a name="primary-key"></a>Primärschlüssel

Der `PrimaryIdAttribute`-Eigenschaftswert wird der logische Name des Attributs, des Primärschlüssels für die Entität.

Standardmäßig weisen alle Entitäten ein einzelnes Attribut des GUID- Bezeichners auf. Dies ist normalerweise *&lt; Entität logischer Name&gt;*+ `Id`.

## <a name="primary-name"></a>Primärer Name

Der `PrimaryNameAttribute`-Eigenschaftswert wird der logische Name des Attributs, der den Zeichenwert speichert, der den Entitätsdatensatz identifiziert. Dies ist der Wert, der in einen Hyperlink angezeigt wird, um den Datensatz in einer Benutzeroberfläche zu öffnen.

**Beispiel**: Die Kontaktentität nutzt das `fullname` Attritut als primäres Namensattribut.

> [!NOTE]
> Nicht jede Entität hat einen primären Namen. Einige Entitäten werden nicht in einer Benutzeroberfläche angezeigt.

## <a name="entity-images"></a>Entitätsbilder

Der `PrimaryImageAttribute`-Eigenschaftswert wird der logische Name des Attributs, der den Bildwert speichert, der den Entitätsdatensatz identifiziert. Jede Entität kann nur ein Bildattribut haben und der logische Name des Attributs ist immer `entityimage`.

**Beispiel**: Das [Kontaktentität](reference/entities/contact.md) [EntityImage](reference/entities/contact.md#BKMK_EntityImage) Attribut kann ein Bild des Kontakts speichern.

Für Leistungsgründe sind Entitätsbilder nicht in den Abrufvorgängen enthalten, es sei denn, sie werden explizit angefordert.

Jede Entität, die Entitätsbilder werden, bestehen aus drei unterstützenden Attributen.

|SchemaName|Typ|Beschreibung|
|--|--|--|
|`EntityImage_Timestamp` |`BigIntType`|Der Wert zeigt an, wenn das Bild zuletzt aktualisiert wurde, und wird verwendet, um sicherzustellen, dass die aktuelle Version des Bilds heruntergeladen und auf dem Client zwischengespeichert wird.|
|`EntityImage_URL`|`StringType`|Eine absolute URL, um das Entitätsbild in einem Client anzuzeigen.|
|`EntityImageId`|`UniqueIdentifierType`|Der eindeutige Bezeichner des Bilds|

Weitere Informationen: 
- [Common Data Service Entwicklerhandbuch-Bildattribute](/dynamics365/customer-engagement/developer/image-attributes)
- [Common Data Service Entwicklerhandbuchbeispiel: Festlegen und Abrufen von Entitätsbildern](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images)

> [!NOTE]
> Dies ist anders als das Symbol, das für eine Entität in Modell-angetriebenen Apps angezeigt wird. Die `IconVectorName`-Eigenschaft enthält den Namen der SVG-Webressource, die dieses festlegt.

## <a name="types-of-entities"></a>Arten von Entitäten

Für die Funktionen und das Verhalten von Entitäten hängt von einigen Entitätseigenschaften ab. Die meisten der Eigenschaften sind verhältnismäßig einfach und haben aussagekräftige Namen. Vier, die einige weitere Erklärung benötigen, können: *Besitz*, *Aktivitätsentitäten*, *Activityparty-Entität* und *Untergeordnete Entitäten*.

### <a name="entity-ownership"></a>Entitätsbesitz

Entitäten können kategorisiert werden, welchen Daten innerhalb sie gehören. Dies ist ein wichtiges Konzept, das zugeordnet wird, beispielsweise wie Sicherheit auf Entitäten angewendet werden. Diese Informationen ist die `OwnershipType`Eigenschaft. Die folgende Tabelle beschreibt die unterschiedlichen Besitztypen in :

|Besitztyp  |Beschreibung  |
|---------|---------|
|Geschäftlich|Daten gehören der Unternehmenseinheit. Zugriff auf die Daten kann auf der Unternehmenseinheitebene gesteuert werden.|
|Keine|Daten, die zu keiner anderen Entität gehören.|
|Organisation|Daten, die der Organisation gehören. Der Zugriff auf die Daten wird auf Organisationsebene gesteuert.|
|Benutzer oder Team|Daten, die zu einem Benutzer oder einem Team gehören. Aktionen, die für diese Datensätze ausgeführt werden, können auf Benutzerebene gesteuert werden.|

Wenn Sie neue Entitäten erstellen, sind die einzigen Besitzoptionen: **Organisation** oder **Benutzer oder Team**. Nachdem Sie eine Wahl für diese Option auswählen, können Sie sie nicht mehr geändert werden. Wählen Sie **Benutzer oder Team** für eine präzisste Kontrolle darüber, wem Aktionen für Datensätze anzuzeigen oder ausgeführt werden können. Wählen Sie **Organisation** wenn dieses Maß an Kontrolle nicht erforderlich. 

### <a name="activity-entities"></a>Aktivitätsentitäten

Eine Aktivität ist eine Aufgabe, die von einem Benutzer ausgeführt wurde oder auszuführen ist. Eine Aktivität ist eine beliebige Aktion, für die ein Eintrag in einem Kalender vorgenommen werden kann. 

Aktivitäten werden anders gestaltet als andere Arten Entitäten, die Geschäftsdaten speichern. Daten über Aktivitäten werden oft in einer Liste angezeigt, aber die Aktivität benötigt der eindeutige Eigenschaften. Anstelle einer einzelnen Aktivitätsentität mit beliebigen Eigenschaft gibt es separate Arten von Aktivitätsentitäten und jede von ihnen erbt Eigenschaften einer Genauigkeit [ActivityPointer-Entität](reference/entities/activitypointer.md). Die Entitäten mit dem `IsActivity`-Eigenschaftensatz legt den Wert true fest.


|Entität |Beschreibung  |
|---------|---------|
|[Termin](reference/entities/appointment.md)|Verpflichtung, die ein Zeitintervall mit Start-/Endzeit und Dauer darstellt.|
|[Email](reference/entities/email.md)|Aktivität, die unter Verwendung von E-Mail-Protokollen übermittelt wird.|
|[Fax](reference/entities/fax.md)|Aktivität, die das Anrufergebnis sowie die Anzahl der Seiten eines Fax nachverfolgt und optional eine elektronische Kopie des Dokuments speichert|
|[Brief](reference/entities/letter.md)|Aktivität, die die Zustellung eines Briefs nachverfolgt. Die Aktivität kann die elektronische Kopie des Briefs enthalten.|
|[PhoneCall](reference/entities/phonecall.md)|Aktivität zur Nachverfolgung eines Telefonanrufs.|
|[RecurringAppointmentMaster](reference/entities/recurringappointmentmaster.md)|Der Mastertermin einer Terminserie.|
|[Social Media-Aktivitäten](reference/entities/socialactivity.md)|Nur zur internen Verwendung.|
|[Aufgabe](reference/entities/task.md)|Allgemeine Aktivität, die die auszuführende Arbeit darstellt|

Immer wenn eine der folgenden Arten der Aktivitätsentitäts-Datensätzen erstellt wird, wird ein entsprechender `ActivityPointer`  Entitätsdatensatz erstellt mit dem gleichen eindeutigen `ActivityId` Attributwert des Bezeichners. Sie können keine Instanzen erstellen, löschen oder aktualisieren der `ActivityPointer` Entität, aber Sie können ihn abrufen. Damit können Aktivitätstypen in einer Liste angezeigt werden.

Sie können benutzerdefinierte Aktivitätsentitäten erstellen, die sich gleich verhalten.
<!-- TODO: Add link to topic about creating an activity entity -->

### <a name="activityparty-entity"></a>ActivityParty-Entität

Diese Entität wird verwendet, um die Struktur Aktivitätsentitätsattributen hinzuzufügen `PartyListType`, die Verweise in anderen Entitäten umfassen. Sie verwenden die Entität, wenn Sie Werte für Aktivitätsentitätsattribute wie oder `Email.to` . `PhoneCall.from` erstellen. Klicken Sie auf [ActivityParty-Entität](reference/entities/activityparty.md) legen Sie das [ParticipationTypeMask](reference/entities/activityparty.md#BKMK_ParticipationTypeMask)-Attribut fest, um die Rollen zu definieren, die den Verweis wiedergeben. Rollen umfassen `Sender``ToRecipient``Organizer` und mehr.

Sie können die Entität `ActivityParty` abfragen, aber Sie können eine Aktivitätspartei außerhalb der Aktivität nicht erstellen, abrufen, aktualisieren oder löschen, mit dem sie verknüpft ist.
Weitere Informationen: 
- [ActivityParty-Entität](/dynamics365/customer-engagement/developer/activityparty-entity)


### <a name="child-entities"></a>Untergeordnete Entitäten

Entitäten, in denen die `IsChildEntity` Eigenschaft wahr ist, hat nie definierte Rechte und wir nie vom Benutzer oder Team besessen. Vorgänge, die auf einer untergeordneten Entität ausgeführt werden, werden an die Entität gebunden, mit der sie über eine n: 1-Beziehung zugeordnet sind. Benutzer können Vorgänge in untergeordneten Entitäten nur ausführen, indem sie denselben Vorgang für die verknüpfte Entität ausführen. Untergeordnete Entitäten werden automatisch gelöscht, wenn der Datensatz von dem sie abhängen, gelöscht wird.

Beispielsweise `PostComment`, `PostLike`und `PostRole` sind alle untergeordneten Elemente der `Post` Entität.

## <a name="entity-keys"></a>Entitätsschlüssel

Jede Alternativschlüsseldefinition hat eine oder mehrere Attribute in Kombination, mit der eine Entitätsinstanz eindeutig identifiziert wird. Alternativschlüssel werden in der Regel nur für die Integration mit externen Systemen angewendet. Sie können Alternativschlüssel definieren, um einen Datensatz eindeutig zu identifizieren. Dies ist dann von Nutzen, wenn Sie Daten in ein einzelnes System integrieren, das nicht den Schlüssel des GUID- Bezeichnerwert unterstützt. Sie können einen einzelnen Feldwert oder einer Kombination von Feldwerten definieren, um eine Entität eindeutig zu identifizieren. Einen Alternativschlüssel hinzufügen, wird eine Eindeutigkeitseinschränkung für diese Attribute. Es ist nicht möglich, einen anderen Entitätsdatensatz zu erstellen oder zu aktualisieren, um die gleichen Werte zu haben.

Weitere Informationen: 
 - [Common Data Service Anpassungsleitfaden: Alternative Schlüssel zum Verweisen auf Common Data Service Datensätze definieren](/dynamics365/customer-engagement/customize/define-alternate-keys-reference-records)
 - [Definieren Sie Alternativschlüssel für eine Entität oder ein Entwicklerhandbuch: Synchronisieren von Common Data Service-Daten mit externen Systemen](/dynamics365/customer-engagement/developer/synchronize-dynamics-365-data-with-external-systems)

## <a name="entity-states"></a>Entitätsstatus

Die meisten Geschäftsentitäten haben zwei Eigenschaften zum Nachverfolgen des Zustands eines Datensatzes. Dies sind `StateCode`, für die **Status** in Modell-angetriebenen Apps und `StatusCode`,  die **Statusgrund** in Modell-angetriebenen Apps genannt werden. 

Beide Attribute enthalten einen Satz von Optionen, um die gültigen Werte anzuzeigen. Die `StateCode` und `StatusCode`-Attributwerte werden verknüpft, damit nur bestimmte `StatusCode` Optionen für ein gegebenes  `StateCode` gültig sind.

Dies kann nach Entität variieren, aber das allgemeine Muster für viele Entitäten und Standard- und  benutzerdefinierte Entitäten ist dies:

|StateCode-Optionen  |StateCode-Optionen  |
|---------|---------|
|0 : Aktiv|1 : Aktiv|
|1 : Inaktiv|2 : Inaktiv|

Für einige Entitäten gelten verschiedene Sätze von Optionen. 

**Beispiel**: `PhoneCall` Entität `StateCode` sowie `StatusCode` Optionen


|`StateCode`|`StatusCode`|
|---------|---------|
|0 : Offen|1 : Offen|
|1 : Abgeschlossen|2 : Erledigt <br />4 : Empfangen|
|2: Storniert|3: Storniert|

Der Satz gültiger Zustandscodes für eine Entität ist nicht anpassbar, aber die Statuscodes können angepasst werden. Sie können zusätzliche `StatusCode` Optionen für ein entsprechendes  `StateCode` hinzufügen.

Für die Entität "Anfrage" und benutzerdefinierte Entitäten können Sie zusätzliche Kriterien für gültige Wechsel zwischen Status definieren. Weitere Informationen: 
- [Anpassen von Entitätsattributmetadaten](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)
- [Definieren von benutzerdefinierten Statusmodellübergängen](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions)

### <a name="see-also"></a>Siehe auch

[Common Data Service-Entitäten](entities.md)
