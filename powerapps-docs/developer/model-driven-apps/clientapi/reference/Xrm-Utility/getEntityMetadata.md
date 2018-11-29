---
title: getEntityMetadata (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getentitymetadata"></a>getEntityMetadata



[!INCLUDE[./includes/getEntityMetadata-description.md](./includes/getEntityMetadata-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.Utility.getEntityMetadata(entityName,attributes).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|entityName|String|Ja|Der logische Name der Entität.|
|Attribute|Zeichenfolgenarray|Nr.|Die Attribute, für die Metadaten abgerufen werden.|
|successCallback|Funktion|Nr.|Ein Funktion, die bei der Rückgabe der Entitätsmetadaten aufzurufen ist.|
|errorCallback|Funktion|Nr.|Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug.|

## <a name="returns"></a>Gibt zurück

**Typ:**: Objekt.

**Beschreibung**: Ein Objekt, das die Entitätsmetadateninformationen mit folgenden Attributen enthält.

<table>
<tr>
<th>Attributname</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>ActivityTypeMask</td>
<td>Zahl</td>
<td>Ob eine benutzerdefinierte Aktivität in den Aktivitätsmenüs in der Webanwendung angezeigt werden soll. 0 gibt an, dass die benutzerdefinierte Aktivität nicht angezeigt wird; 1 gibt an, dass sie angezeigt wird.</td>
</tr>
<tr>
<td>AutoRouteToOwnerQueue</td>
<td>Boolean</td>
<td>Gibt an, ob Datensätze automatisch in die Standardwarteschlange des Besitzers verschoben werden sollen, wenn ein Datensatz dieses Typs erstellt oder zugewiesen wird. </td>
</tr>

<tr>
<td>CanEnableSyncToExternalSearchIndex</td>
<td>Boolean</td>
<td>Nur zur internen Verwendung</td>
</tr>
<tr>
<td>CanTriggerWorkflow</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität einen Workflowprozess auslösen kann.</td>
</tr>
<tr>
<td>Beschreibung</td>
<td>String</td>
<td>Beschreibung für die Entität.</td>
</tr>
<tr>
<td>DisplayCollectionName</td>
<td>String</td>
<td>Pluralanzeigename für die Entität.</td>
</tr>
<tr>
<td>DisplayName</td>
<td>String</td>
<td>Anzeigename für die Entität.</td>
</tr>
<tr>
<td>EnforceStateTransitions</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität benutzerdefinierte Statusübergänge erzwingt.</td>
</tr>
<tr>
<td>EntityColor</td>
<td>String</td>
<td>Der Hexadezimalcode, der die für diese Entität in der Anwendung zu verwendende Farbe darstellt.</td>
</tr>
<tr>
<td>EntitySetName</td>
<td>String</td>
<td>Der Name der Web-API-Entität, die für diese Entität festgelegt ist.</td>
</tr>
<tr>
<td>HasActivities</td>
<td>Boolean</td>
<td>Gibt an, ob Aktivitäten dieser Entität zugeordnet sind.</td>
</tr>
<tr>
<td>IsActivity</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität eine Aktivität ist.</td>
</tr>
<tr>
<td>IsActivityParty</td>
<td>Boolean</td>
<td>Gibt an, ob die E-Mail-Nachricht an eine E-Mail-Adresse gesendet werden kann, die in einem Datensatz dieses Typs gespeichert ist.</td>
</tr>
<tr>
<td>IsBusinessProcessEnabled</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität für Geschäftsprozessflüsse aktiviert ist.</td>
</tr>
<tr>
<td>IsBPFEntity</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität eine Geschäftsprozessfluss-Entität ist.</td>
</tr>
<tr>
<td>IsChildEntity</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität eine untergeordnete Entität ist.</td>
</tr>
<tr>
<td>IsConnectionsEnabled</td>
<td>Boolean</td>
<td>Gibt an, ob Verbindungen für diese Entität aktiviert sind.</td>
</tr>
<tr>
<td>IsCustomEntity</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität eine benutzerdefinierte Entität ist.</td>
</tr>
<tr>
<td>IsCustomizable</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität angepasst werden kann.</td>
</tr>
<tr>
<td>IsDocumentManagementEnabled</td>
<td>Boolean</td>
<td>Gibt an, ob die Dokumentverwaltung aktiviert ist.</td>
</tr>
<tr>
<td>IsDocumentRecommendationsEnabled</td>
<td>Boolean</td>
<td>Gibt an, ob die Dokumentempfehlungen aktiviert sind.</td>
</tr>
<tr>
<td>IsDuplicateDetectionEnabled</td>
<td>Boolean</td>
<td>Gibt an, ob die Duplikaterkennung aktiviert ist.</td>
</tr>
<tr>
<td>IsEnabledForCharts</td>
<td>Boolean</td>
<td>Gibt an, ob Diagramme aktiviert sind.</td>
</tr>
<tr>
<td>IsImportable</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität mithilfe des Import-Assistenten importiert werden kann.</td>
</tr>
<tr>
<td>IsInteractionCentricEnabled</td>
<td>Boolean</td>
<td>Gibt an, dass die Entität für interaktive Funktionen aktiviert ist.</td>
</tr>
<tr>
<td>IsKnowledgeManagementEnabled</td>
<td>Boolean</td>
<td>Gibt an, ob das Wissensmanagement für die Entität aktiviert ist.</td>
</tr>
<tr>
<td>IsMailMergeEnabled</td>
<td>Boolean</td>
<td>Gibt an, ob Seriendruck für diese Entität aktiviert ist.</td>
</tr>
<tr>
<td>IsManaged</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität Teil einer verwalteten Lösung ist.</td>
</tr>
<tr>
<td>IsOneNoteIntegrationEnabled</td>
<td>Boolean</td>
<td>Gibt an, ob OneNote-Integration für die Entität aktiviert ist.</td>
</tr>
<tr>
<td>IsOptimisticConcurrencyEnabled</td>
<td>Boolean</td>
<td>Gibt an, ob optimistische Parallelität für die Entität aktiviert ist.</td>
</tr>
<tr>
<td>IsQuickCreateEnabled</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität für Schnellerfassungsformulare aktiviert ist.</td>
</tr>
<tr>
<td>IsStateModelAware</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität die Festlegung von benutzerdefinierten Statusübergängen unterstützt.</td>
</tr>
<tr>
<td>IsValidForAdvancedFind</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität in „Erweiterte Suche” angezeigt wird.</td>
</tr>
<tr>
<td>IsVisibleInMobileClient</td>
<td>Boolean</td>
<td>Gibt an, ob Benutzer von Microsoft Dynamics 365 für Tablets Daten für diese Entität anzeigen können.</td>
</tr>
<tr>
<td>IsEnabledInUnifiedInterface</td>
<td>Boolean</td>
<td>Gibt an, ob die Entität für „Einheitliche Oberfläche” aktiviert ist.</td>
</tr>
<tr>
<td>LogicalCollectionName</td>
<td>String</td>
<td>Der logische Sammlungsname.</td>
</tr>
<tr>
<td>LogicalName</td>
<td>String</td>
<td>Der logische Name für die Entität.</td>
</tr>
<tr>
<td>ObjectTypeCode</td>
<td>Zahl</td>
<td>Der Entitätstypcode.</td>
</tr>
<tr>
<td>OwnershipType</td>
<td>String</td>
<td>Der Besitztyp für die Entität: „UserOwned” oder „OrganizationOwned”.</td>
</tr>
<tr>
<td>PrimaryIdAttribute</td>
<td>String</td>
<td>Der Name des Attributs, das die primäre ID für die Entität ist.</td>
</tr>
<tr>
<td>PrimaryImageAttribute</td>
<td>String</td>
<td>Der Name des primären Bildattributs für eine Entität.</td>
</tr>
<tr>
<td>PrimaryNameAttribute</td>
<td>String</td>
<td>Der Name des primären Attributs für eine Entität.</td>
</tr>
<tr>
<td>Rechte</td>
<td>Array von Objekten</td>
<td>Die Rechtsmetadaten für die Entität, bei der *jedes* Objekt die folgenden Attribute enthält, um das Sicherheitsrecht für den Zugriff auf eine Entität zu definieren:
<ul>
<li><b>CanBeBasic</b>: Boolescher Wert. Ob das Recht eine Basiszugriffsebene sein kann.</li>
<li><b>CanBeDeep</b>: Boolescher Wert. Ob das Recht tiefe Zugriffsebene sein kann.</li>
<li><b>CanBeEntityReference</b>: Boolescher Wert. Ob das Recht für eine externe Partei die Basiszugriffsebene sein kann.</li>
<li><b>CanBeGlobal</b>: Boolescher Wert. Ob das Recht die globale Zugriffsebene sein kann.</li>
<li><b>CanBeLocal</b>: Boolescher Wert. Ob das Recht die lokale Zugriffsebene sein kann.</li>
<li><b>CanBeParentEntityReference</b>: Boolescher Wert. Ob das Recht für eine externe Partei die übergeordnete Zugriffsebene sein kann.</li>
<li><b>Name</b>: Zeichenfolge. Der Name des Rechts.</li>
<li><b>PrivilegeId</b>: Zeichenfolge. Die ID des Rechts.</li>
<li><b>PrivilegeType</b>: Zahl. Der Typ des Rechts, das eines der Folgenden ist:</li>
<ul>
<li>0: Keine</li>
<li>1: Erstellen</li>
<li>2: Lesen</li>
<li>3: Schreiben</li>
<li>4: Löschen</li>
<li>5: Zuweisen</li>
<li>6: Freigeben</li>
<li>7: Anfügen</li>
<li>8: AppendTo</li>
</ul>
</ul></td>
</tr>
<tr>
<td>Attribute</td>
<td>Abholung</td>
<td>Eine Sammlung von Attributmetadatenobjekten. Das zurückgegebene Objekt hängt vom Typ der Attributmetadaten ab.
<p><b>Attributmetadaten für den <i>Basis</i>-Typ</b><br/>
Ein mit den folgenden Eigenschaften zurückgegebenes Objekt:</p>
<ul>
<li><b>AttributeType</b>: Zahl. Typ eines Attributs. Eine Liste mit Attributtypwerten finden Sie unter <a href="https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.attributetypecode">AttributeTypeCode</a></li>
<li><b>DisplayName</b>: Zeichenfolge. Anzeigename für das Attribut.</li>
<li><b>EntityLogicalName</b>: Zeichenfolge Logischer Name der Entität, die das Attribut enthält.</li>
<li><b>LogicalName</b>: Zeichenfolge. Logischer Name für das Attribut.</li></ul>

<p><b>Attributmetadaten für den <i>Booleschen</i> Typ</b><br/>
Ein Objekt, das mit den folgenden Eigenschaften zusätzlich zu den Attributmetadatentypeigenschaften <i>Basis</i> zurückgegeben wird:</p>
<ul>
<li><b>DefaultFormValue</b>: Boolescher Wert. Standardwert für einen Booleschen Optionssatz.</li>
<li><b>OptionSet</b>: Objekt. Optionen für das boolesche Attribut, bei denen jede Option ein key:value-Paar ist.</li></ul>

<p><b>Attributmetadaten für den <i>Enum</i>-Typ</b><br/>
Ein Objekt, das mit den folgenden Eigenschaften zusätzlich zu den Attributmetadatentypeigenschaften <i>Basis</i> zurückgegeben wird:</p>
<ul>
<li><b>OptionSet</b>: Objekt. Optionen für das Attribut, bei denen jede Option ein key:value-Paar ist.</li></ul>

<p><b>Attributmetadaten für den <i>Auswahlliste</i>-Typ</b><br/>
Ein Objekt, das mit den folgenden Eigenschaften zusätzlich zu den Attributmetadatentypeigenschaften <i>Basis</i> zurückgegeben wird:</p>
<ul>
<li><b>DefaultFormValue</b>: Zahl. Standardformularwert für das Attribut.</li>
<li><b>OptionSet</b>: Objekt. Optionen für das Attribut, bei denen jede Option ein key:value-Paar ist.</li></ul>

<p><b>Attributmetadaten für den <i>Status</i>-Typ</b><br/>
Ein Objekt, das mit den folgenden Eigenschaften zusätzlich zu den Attributmetadatentypeigenschaften <i>Basis</i> zurückgegeben wird:</p>
<ul>
<li><b>OptionSet</b>: Objekt. Optionen für das Attribut, bei denen jede Option ein key:value-Paar ist.</li></ul>
<p>Das Objekt enthält auch die folgenden Methoden:</p>
<ul>
<li><b>getDefaultStatus(arg)</b>: Gibt den standardmäßigen Status (Zahl) basierend auf dem übergebenen Statuswert für eine Entität zurück. Informationen zu Standardstatus und Statuswerten für eine Entität finden Sie unter den Entitätsmetadateninformationen der Entität in <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference">Entitätsreferenz</a>.</li>
<li><b>getStatusValuesForState(arg)</b>: Gibt mögliche Statuswerte (Array von Zahlen) für einen angegebenen Statuswert zurück. Informationen zu Status und Statuswerten für eine Entität finden Sie unter Entitätsmetadateninformationen der Entität in <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference">Entitätsreferenz</a>.</li></ul>

<p><b>Attributmetadaten für den <i>Status</i>-Typ</b><br/>
Ein Objekt, das mit den folgenden Eigenschaften zusätzlich zu den Attributmetadatentypeigenschaften <i>Basis</i> zurückgegeben wird:</p>
<ul>
<li><b>OptionSet</b>: Objekt. Optionen für das Attribut, bei denen jede Option ein key:value-Paar ist.</li></ul>
<p>Das Objekt enthält auch die folgende Methode:</p>
<ul>
<li><b>getState(arg)</b>: Gibt den Statuswert (Zahl) für den angegebenen Statuswert (Zahl) zurück. Informationen zu Standardstatus und Statuswerten für eine Entität finden Sie unter den Entitätsmetadateninformationen der Entität in <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference">Entitätsreferenz</a>.</li>
</ul>
</td>
</tr>
</table>

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility](../xrm-utility.md)

