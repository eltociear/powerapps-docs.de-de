---
title: Menübanddefinitionen definieren (modellgesteuerte Apps) | Microsoft Docs
description: Infos zum Festlegen bestimmter Regeln, die steuern, wann die Menübandelemente während des Konfigurierens von Menübandelementen aktiviert werden.
keywords: ''
ms.date: 02/08/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 201f5db9-be65-7c3b-8202-822d78338bd6
author: JesseParsons
ms.author: jeparson
manager: annbe
ms.reviewer: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8c22ec2532371093afbe224a5ea12c44652a30cc
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748466"
---
# <a name="define-ribbon-enable-rules"></a>Definieren von Menüband-Aktivierungsregeln

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
| `Modern`  |                                       Die Befehlsleiste wird mithilfe von [!INCLUDE[pn_moca_full](../../includes/pn-moca-full.md)] dargestellt.                                       |
| `Refresh` |                                                      Die Befehlsleiste wird mithilfe der aktualisierten Benutzeroberfläche angezeigt.                                                      |
| `Legacy`  | Das Menüband wird in Formularen für Entitäten, die nicht aktualisiert wurden, oder in einer Listenansicht in [!INCLUDE[pn_crm_for_outlook_full](../../includes/pn-crm-for-outlook-full.md)] angezeigt. |

### <a name="crm-client-type-rule"></a>Crm-Clienttyp-Regel
Verwendet das `<CrmClientTypeRule>`-Element, um die Definition von Regeln abhängig vom Typ des verwendeten Clients zu erlauben. Die Typoptionen lauten wie folgt:  

-   `Web`  

-   `Outlook`  

### <a name="crm-offline-access-state-rule"></a>Crm-Offlinezugriff-Zugriffsstatusregel
 Verwendet das `<CrmOfflineAccessStateRule>`-Element. Verwenden Sie diese Kriterien, um ein Menübandelement abhängig davon zu aktivieren, ob [!INCLUDE[pn_crm_outlook_offline_access](../../includes/pn-crm-outlook-offline-access.md)] derzeit im Offlinemodus ist.  

### <a name="crm-outlook-client-type-rule"></a>Crm Outlook-Clienttyp-Regel
 Verwendet das `<CrmOutlookClientTypeRule>`-Element. Verwenden Sie diese Regel, wenn Sie eine Schaltfläche nur für rinrn spezifischen [!INCLUDE[pn_crm_for_outlook_full](../../includes/pn-crm-for-outlook-full.md)]-Typ anzeigen möchten. Die Typoptionen lauten wie folgt:  

-   `CrmForOutlook`  

-   `CrmForOutlookOfflineAccess`  

### <a name="custom-rule"></a>Benutzerdefinierte Regel
 Verwendet das `<CustomRule>`-Element. Verwenden Sie diese Art von Regel, um eine Funktion in einer JavaScript-Bibliothek aufzurufen, die ein Promise (Einheitliche Oberfläche) oder Boolean (Einheitliche Oberfläche und Web Client) zurückgibt.

```JavaScript
function EnableRule()
{
    const value = Xrm.Page.getAttribute("field1").getValue();
    return value === "Active";
}
```

> [!NOTE]
>  Benutzerdefinierte Regeln, die nicht schnell einen Wert zurückgeben, können sich auf die Leistung des Menübands auswirken. Wenn Sie eine Logik ausführen müssen, deren Ausführung einige Zeit in Anspruch nehmen kann (z. B. eine Netzwerkanforderung), verwenden Sie die folgende Strategie, um Ihre benutzerdefinierte Regel asynchron zu machen.

 Einheitliche Oberfläche-Regeln unterstützen die Rückgabe eines Promises und nicht boolesch für die asynchrone Regelauswertung. Wenn das Versprechen nicht innerhalb von 10 Sekunden aufgelöst wird, löst die Regel mit einem falschen Wert auf.
 > [!NOTE]
>  Versprechungsbasierte Regeln funktionieren nur auf der Einheitliche Oberfläche, sodass sie nicht verwendet werden können, wenn der klassische Web Client weiterhin verwendet wird.
 ```JavaScript
function EnableRule()
{
    const request = new XMLHttpRequest();
    request.open('GET', '/bar/foo');

    return new Promise((resolve, reject) =>
    {
        request.onload = function (e)
        {
            if (request.readyState === 4)
            {
                if (request.status === 200)
                {
                    resolve(request.responseText === "true");
                }
                else
                {
                    reject(request.statusText);
                }
            }
        };
        request.onerror = function (e)
        {
            reject(request.statusText);
        };

        request.send(null);
    });
}
```


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
 Verwendet das `<OutlookItemTrackingRule>`-Element. Verwenden Sie das `TrackedInCrm`-Attribut für dieses Element, um festzulegen, ob der Datensatz in PowerApps nachverfolgt wird.  

### <a name="outlook-version-rule"></a>Outlook-Versionsregel
 Verwendet das `<OutlookVersionRule>`-Element. Verwenden Sie diesl, um ein Menübandelement für eine bestimmte Version von [!INCLUDE[pn_MS_Outlook_Full](../../includes/pn-ms-outlook-full.md)] anzuzeigen wie folgt:  

-   `2003`  

-   `2007`  

-   `2010`  

### <a name="page-rule"></a>Seitenregel
 Verwendet das `<PageRule>`-Element. Diese Art von Regel überprüft, ob die URL der Seite angezeigt wird. Sie gibt "true" zurück, wenn die `Address` übereinstimmt.  

### <a name="record-privilege-rule"></a>Datensatzberechtigungsregel
 Verwendet das `<RecordPrivilegeRule>`-Element. Verwenden Sie diese Regel, um zu bestimmen, ob der aktuelle Benutzer über Rechte für einen bestimmten Datensatz verfügt. Diese Rechte unterscheiden sich von einem Entitätsrecht, da sie Rechte beinhalten können, die von einem anderen Benutzer erworben wurden, der den Datensatz gemeinsam mit dem aktuellen Benutzer verwendet.  

### <a name="selection-count-rule"></a>Auswahlzählungsregel
 Verwendet das `<SelectionCountRule>`-Element. Verwenden Sie diese Art von Regel mit einem für eine Liste angezeigten Menüband, um eine Schaltfläche zu aktivieren, wenn bestimmte Höchst- und Mindestzahlen von Datensätzen in dem Raster ausgewählt werden. Zum Beispiel: Wenn Ihre Schaltfläche Datensätze zusammenführt, sollten Sie sicherstellen, dass mindestens zwei Datensätze ausgewählt werden, bevor  das Menübandsteuerelement aktiviert wird.  

### <a name="value-rule"></a>Wertregel
Verwendet das `<ValueRule>`-Element. Verwenden Sie diese Regel, um den Wert eines bestimmten Felds im Datensatz zu suchen, der im Formular angezeigt wird. Sie müssen für die Prüfung das `Field` und den `Value` angeben.

### <a name="see-also"></a>Siehe auch  
 [Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)   
 [Menübandbefehle definieren](define-ribbon-commands.md)   
 [Definieren von Menüband-Anzeigeregeln](define-ribbon-display-rules.md)
