---
title: Menübanddefinitionen definieren (modellgesteuerte Apps) | Microsoft Docs
description: 'Infos zum Festlegen bestimmter Regeln, die steuern, wann die Menübandelemente während des Konfigurierens von Menübandelementen aktiviert werden.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 201f5db9-be65-7c3b-8202-822d78338bd6
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="define-ribbon-enable-rules"></a>Definieren von Menüband-Aktivierungsregeln

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-enable-rules -->

Wenn Sie Menübandelemente konfigurieren, können Sie bestimmte Regeln definieren, die steuern, wann die Menübandelemente aktiviert werden. Das `<EnableRule>`-Element wird wie folgt verwendet:  

-   Verwenden Sie das `/RuleDefinitions/EnableRules/EnableRule`-Element, um Regeln zu definieren, die steuern, wann das Menübandelement aktiviert werden soll.  

-   Verwenden Sie das `/CommandDefinitions/CommandDefinition/EnableRules/EnableRule`-Element, um spezifische Aktivierungsregeln einer Befehlsdefinition zuzuordnen.  

## <a name="what-does-enabled-mean"></a>Was bedeutet "aktiviert"?  
 Mithilfe der Befehlsleiste werden Befehle ein- oder ausgeblendet. Mit dem Menüband sind deaktivierte Befehle zwar sichtbar, reagieren jedoch nicht auf Ereignisse.  

## <a name="control-when-ribbon-elements-are-enabled"></a>Steuern, wann Menübandelemente aktiviert werden  
 Aktivierungsregeln sind zur Wiederverwendung gedacht Durch die Definition von Aktivierungsregeln mit Regeldefinitionen können Sie dieselbe Aktivierungsregel für viele Befehlsdefinitionen verwenden. Wenn mehrere Aktivierungsregeln für eine Befehlsdefinition definiert sind, müssen alle Aktivierungsregeln als "true" ausgewertet werden, damit das Menübandelement aktiviert wird.  

 Alle Aktivierungsregeln bieten ein optionales Attribut, um anzugeben, ob der Standardwert der Regel "true" oder "false" ist, und ein optionales `InvertResult`-Attribut, das ermöglicht, dass ein negatives Ergebnis zurückgegeben wird, wenn das getestete Element "true" zurückgibt.  

 Das `/RuleDefinitions/EnableRules/EnableRule`-Element unterstützt die folgenden Regeltypen:  

### <a name="command-client-type-rule"></a>Befehls-Clienttyp-Regel
 Verwendet das `<CommandClientTypeRule>`-Element. [!INCLUDE[ribbon_element_CommandClientTypeRule](../../includes/ribbon-element-commandclienttyperule.md)]  

 Die `Type`-Werte entsprechen dem Folgenden:  


|   Value   |                                                                               Präsentation                                                                               |
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Modern`  |                                       Die Befehlsleiste wird mit Dynamics 365 for tablets dargestellt.                                       |
| `Refresh` |                                                      Die Befehlsleiste wird mithilfe der aktualisierten Benutzeroberfläche angezeigt.                                                      |
| `Legacy`  | Das Menüband wird in Formularen für Entitäten, die nicht aktualisiert wurden, oder in einer Listenansicht in Dynamics 365 for Outlook angezeigt. |

### <a name="crm-client-type-rule"></a>Crm-Clienttyp-Regel
Verwendet das `<CrmClientTypeRule>`-Element, um die Definition von Regeln abhängig vom Typ des verwendeten Clients zu erlauben. Die Typoptionen lauten wie folgt:  

-   `Web`  

-   `Outlook`  

### <a name="crm-offline-access-state-rule"></a>Crm-Offlinezugriff-Zugriffsstatusregel
 Verwendet das `<CrmOfflineAccessStateRule>`-Element. Verwenden Sie diese Kriterien, um ein Menübandelement zu aktivieren, je nachdem, ob Dynamics 365 for Microsoft Office Outlook mit Offline-Zugriff derzeit offline ist.  

### <a name="crm-outlook-client-type-rule"></a>Crm Outlook-Clienttyp-Regel
 Verwendet das `<CrmOutlookClientTypeRule>`-Element. Verwenden Sie diese Regel, wenn Sie eine Schaltfläche nur für einen spezifischen Dynamics 365 for Outlook-Typ anzeigen möchten. Die Typoptionen lauten wie folgt:  

-   `CrmForOutlook`  

-   `CrmForOutlookOfflineAccess`  

### <a name="custom-rule"></a>Benutzerdefinierte Regel
 Verwendet das `<CustomRule>`-Element. Verwenden Sie diese Art von Regel, um eine Funktion in einer JavaScript-Bibliothek aufzurufen, die einen Booleschen Wert zurückgibt.  

> [!NOTE]
>  Benutzerdefinierte Regeln, die nicht schnell einen Wert zurückgeben, können sich auf die Leistung des Menübands auswirken. Wenn Sie Logik ausführen müssen, die möglicherweise einige Zeit in Anspruch nimmt, verwenden Sie die folgende Strategie, um Ihre benutzerdefinierte Regel asynchron zu machen:  
>   
> 1.  Definieren Sie eine Regel, die ein benutzerdefiniertes Objekt überprüft. Sie können auf ein Objekt wie `Window.ContosoCustomObject.RuleIsTrue` prüfen, das Sie einfach an das Fenster anhängen.  
> 2.  Wenn dieses Objekt vorhanden ist, geben Sie es zurück.  
> 3.  Wenn das Objekt nicht vorhanden ist, definieren Sie das Objekt und legen Sie den Wert als "False" fest.  
> 4.  Bevor Sie einen Wert zurückgeben, verwenden Sie [settimeout](https://msdn.microsoft.com/library/ms536753\(VS.85\).aspx) <!-- TODO not sure about this link-->, um eine asynchrone Rückruffunktion auszuführen, um das Objekt zurückzusetzen. Geben Sie dann "False" zurück.  
> 5.  Nachdem die Rückruffunktion die Vorgänge durchgeführt hat, die nötig sind, um das richtige Resultat zu bestimmen, setzt sie den Wert des Objekts fest und verwendet die `refreshRibbon`-Methode, um das Menüband zu aktualisieren.  
> 6.  Wenn das Menüband aktualisiert ist, erkennt es das Objekt zusammen mit dem korrekten Wertesatz, und die Regel wird geprüft.  

### <a name="entity-rule"></a>Entitätsregel
 Verwendet das `<EntityRule>`-Element. Entitätsregeln lassen die Evaluierung der aktuellen Entität zu. Dies ist hilfreich, wenn Sie benutzerdefinierte Aktionen definieren, die für die Entitätsvorlage gelten, statt für bestimmte Entitäten. Beispielsweise möchten Sie möglicherweise ein Menübandelement für alle Entitäten hinzufügen, mit Ausnahme einiger bestimmter Entitäten. Es ist einfacher, die benutzerdefinierte Aktion für die Entitätsvorlage zu definieren, die für alle Entitäten gilt, und dann eine Entitätsregel zu verwenden, die die Entitäten herausfiltert, die ausgeschlossen werden sollen.  

 Die Entitätsregel enthält auch ein optionales Kontextattribut, um anzugeben, ob die Entität im Formular oder in einer Liste angezeigt wird (HomePageGrid). Das optionale `AppliesTo`-Attribut kann auf `PrimaryEntity` oder `SelectedEntity` festgelegt werden, um zu unterscheiden, ob die Entität in einem Unterraster angezeigt wird.  

### <a name="form-state-rule"></a>Formularstatusregel
 Verwendet das `<FormStateRule>`-Element. Verwenden Sie die `FormState`-Regel, um den aktuellen Formulartyp zu bestimmen, in dem ein Datensatz angezeigt wird. Die Statusoptionen lauten wie folgt:  

-   `Create`  

-   `Existing`  

-   `ReadOnly`  

-   `Disabled`  

-   `BulkEdit`  

### <a name="or-rule"></a>Oder-Regel
 Verwendet das `<OrRule>`-Element. Mit der `OrRule`-Regel können Sie den standardmäßigen UND-Vergleich für mehrere Aktivierungsregeltypen überschreiben. Verwenden Sie das `OrRule`-Element, um mehrere mögliche gültige Kombinationen zu definieren, die zu überprüfen sind.

### <a name="outlook-item-tracking-rule"></a>Outlook-Element-Nachverfolgungsregel
 Verwendet das `<OutlookItemTrackingRule>`-Element. Verwenden Sie das `TrackedInCrm`-Attribut für dieses Element, um festzulegen, ob der Datensatz in Common Data Service for Apps nachverfolgt wird.  

### <a name="outlook-version-rule"></a>Outlook-Versionsregel
 Verwendet das `<OutlookVersionRule>`-Element. Verwenden Sie dies, um ein Menübandelement für eine bestimmte Version von Office Outlook anzuzeigen wie folgt:  

-   `2003`  

-   `2007`  

-   `2010`  

### <a name="page-rule"></a>Seitenregel
 Verwendet das `<PageRule>`-Element. Diese Art von Regel überprüft, ob die URL der Seite angezeigt wird. Sie gibt "true" zurück, wenn die `Address` übereinstimmt.  

### <a name="record-privilege-rule"></a>Datensatzberechtigungsregel
 Verwendet das `<RecordPrivilegeRule>`-Element. Verwenden Sie diese Regel, um zu bestimmen, ob der aktuelle Benutzer über Rechte für einen bestimmten Datensatz verfügt. Diese Rechte unterscheiden sich von einem Entitätsrecht, da sie Rechte beinhalten können, die von einem anderen Benutzer erworben wurden, der den Datensatz gemeinsam mit dem aktuellen Benutzer verwendet.  

### <a name="selection-count-rule"></a>Auswahlzählungsregel
 Verwendet das `<SelectionCountRule>`-Element. Verwenden Sie diese Art von Regel mit einem für eine Liste angezeigten Menüband, um eine Schaltfläche zu aktivieren, wenn bestimmte Höchst- und Mindestzahlen von Datensätzen in dem Raster ausgewählt werden. Zum Beispiel: Wenn Ihre Schaltfläche Datensätze zusammenführt, sollten Sie sicherstellen, dass mindestens zwei Datensätze ausgewählt werden, bevor  das Menübandsteuerelement aktiviert wird.  

### <a name="sku-rule"></a>Sku-Regel
 Verwendet das `<SkuRule>`-Element. Verwenden Sie diese Art von Regel, um ein Menübandelement für eine bestimmte SKU-Version von Dynamics 365 wie folgt zu aktivieren:  

-   `OnPremise`  

-   `Online`  

-   `Spla`  

### <a name="value-rule"></a>Wertregel
Verwendet das `<ValueRule>`-Element. Verwenden Sie diese Regel, um den Wert eines bestimmten Felds im Datensatz zu suchen, der im Formular angezeigt wird. Sie müssen für die Prüfung das `Field` und den `Value` angeben.  

### <a name="see-also"></a>Siehe auch  
 [Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)   
 [Menübandbefehle definieren](define-ribbon-commands.md)   
 [Definieren von Menüband-Anzeigeregeln](define-ribbon-display-rules.md)
