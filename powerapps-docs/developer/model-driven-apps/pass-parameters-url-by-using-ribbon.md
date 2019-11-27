---
title: Übergeben von Parametern mit dem Menüband an eine URL (modellgestützte Apps) | Microsoft Docs
description: Infos zum Übergeben von Parametern an eine URL mit dem Menüband
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a8c24b6d48b5d9330cdc3761cad458e399aec898
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754579"
---
# <a name="pass-parameters-to-a-url-by-using-the-ribbon"></a>Parameter mit dem Menüband an eine URL übergeben

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/pass-parameters-url-by-using-ribbon -->

Menübandaktionen werden im `<Actions>`-Element eines`<CommandDefinition>`-Elements definiert. Es gibt mehrere Möglichkeiten, kontextbezogene Informationen modellgestützter Apps mit dem Menüband als Abfragezeichenfolgenparameter an eine URL zu übergeben.  
  
-   Verwenden sie ein `<Url>`-Element. Innerhalb des `Url`-Elements verwenden das Attribut **PassParams**.  
  
-   Verwenden Sie ein `<Url>`-Element zusammen mit einem `<CrmParameter>`-Element. Wenn es von einem `Url`-Element verwendet wird, muss der Namensattributwert festgelegt werden.  
  
-   Verwenden Sie ein `<JavaScriptFunction>`-Element zusammen mit einem `<CrmParameter>`-Element.  
  
## <a name="use-the-passparams-attribute-to-set-dynamic-values"></a>Das PassParams-Attributm verwenden, um dynamische Werte festzulegen  
 Das Übermitteln von Parametern an ene Ziel-URL unter Verwendung des **PassParams**-Attributs stellt der Ziel-Anwendung Informationen zum Kontext des Benutzers oder des Datensatzes bereit. Alle Parameter werden übermittelt, wenn das Menübandsteuerelement konfiguriert wurde, indem das Attribut **PassParams** verwendet wurde. In der folgenden Tabelle werden die übermittelten Parameter aufgeführt:  
  
|Parameter|Name|Beschreibung|  
|---------------|----------|-----------------|  
|`typename`|Entitätsname|Name der Entität. Bei benutzerdefinierten Entitäten zählen dazu beispielsweise Anpassungspräfix, z. B. new_entityname.|  
|`type`|Entitätstypcode|Eine ganze Zahl, die eindeutig die Entität in der aktuellen Organisation identifiziert. **Hinweis:** `Entity Type Code`-Werte werden durch die Reihenfolge bestimmt, in der eine Entität in einer Organisation erstellt wurde. `Entity Type Codes` für benutzerdefinierte Entitäten sind gewöhnlich in verschiedenen Organisationen verschieden.|  
|`id`|Objekt-GUID|Globally Unique Identifier (GUID), der einen Datensatz darstellt.|  
|`orgname`|Organisationsname|Eindeutiger Name der Organisation.|  
|`userlcid`|Benutzersprachcode|Die Sprachcode-ID, die vom aktuellen Benutzer verwendet wird.|  
|`orglcid`|Organisationssprachcode|Die Sprachcode-ID, die die Ausgangssprache für die Organisation darstellt.|  
  
[!INCLUDE[languagecode](../../includes/languagecode.md)]
  
> [!NOTE]
>  Es ist empfehlenswert, den Entitätsnamen statt des Entitätstypcodes zu verwenden, da der Entitätstypcode möglicherweise je nach MDA-Installation verschieden ist.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die URL ohne Parameter gezeigt:  
  
```  
https://myserver/mypage.aspx  
```  
  
 Das folgenden Beispiel veranschaulicht die Parameter, die enthalten sind, wenn das Menübandsteuerelement für die Account-Entität dargestellt wird, für eine Organisation namens "AdventureWorksCycle ", wenn die Sprache des Benutzers und die Organisationsausgangssprache Englisch ist, und die GUID für den Account-Datensatz DBD5DBFB-0666-DC11-A5D9-0003FF9CE217 ist:  
  
```  
https://myserver/mypage.aspx?orgname=AdventureWorksCycle&userlcid=1033&orglcid=1033&type=1&typename=account&id=%7BDBD5DBFB-0666-DC11-A5D9-0003FF9CE217%7D  
```  
  
## <a name="use-a-querystring-parameter-in-the-url"></a>Verwenden eines Abfragelzeichenfolgenparameters in der URL  
 Sie können einen `querystring`-Parameter in das URL-Attribut einschließen. Dies kann dann nützlich sein, wenn Sie einen bestimmten Datensatz öffnen oder anzeigen möchten, indem Sie [Öffnen von Formularen, Ansichten, Dialogen und Berichten mit einer URL](open-forms-views-dialogs-reports-url.md) verwenden.  
  
> [!NOTE]
>  Sie können das Menüband nicht importieren, wenn die URL das kaufmännischen Und-Zeichen (&) enthält., das verwendet wird, um mehrere `querystring`-Parameter in der URL zu trennen. Dieses Zeichen macht die XML-Datei ungültig. Sie müssen das kaufmännische Und-Zeichen im URL-Attributwert mit "&amp;" umgehen.  
  
## <a name="reading-passed-parameters"></a>Lesen von übergebenen Parametern  
 Übergebene Parameter werden in der Regel auf der ASPX-Zielseite unter Verwendung der Eigenschaft `HttpRequest.QueryString` gelesen. Weitere Informationen: [HttpRequest.QueryString-Eigenschaft](https://msdn.microsoft.com/library/system.web.httprequest.querystring.aspx)  
  
> [!NOTE]
>  Wenn das Ziel Ihrer URL eine Webressource ist, kann sie lediglich die Parameter übernehmen, die im Thema [Übergeben von Parametern an HTMLWeb Resources](webpage-html-web-resources.md#BKMK_PassingParametersToWebResources) identifiziert werden. Die einzige Möglichkeit, benutzerdefinierte Werte zu übermitteln ist, sie in den `data`-Parameter einzuschließen. Spezielle Behandlung ist erforderlich, um mehrere Werte in einem einzigen Parametern einzuschließen. Weitere Informationen: [Beispiel: Übergeben mehrerer Werte über den Datenparameter an eine Webseiten-Webressource](sample-pass-multiple-values-web-resource-through-data-parameter.md)  
  
### <a name="see-also"></a>Siehe auch

 [Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)   
 [Öffnen von Formularen und Ansichten mit einer URL](open-forms-views-dialogs-reports-url.md)    
 [Definieren von Menüband-Registerkartenanzeigenregeln](define-ribbon-tab-display-rules.md)   
 [Beispiel: Exportieren von Menübanddefinitionen](sample-export-ribbon-definitions.md)


