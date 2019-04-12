---
title: Menübandaktionen definieren (modellgesteuerte Apps) | Microsoft Docs
description: 'Infos zum Definieren der Aktionen, die durch Befehlsleisten- oder Menübandsteuerelemente in einem <CommandDefinition>-Element in Kombination mit Regeln ausgeführt werden, die steuern, ob das Steuerelement aktiviert bzw. im Menüband angezeigt wird.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: fbb7ff68-e4be-d8c2-069f-6a4a69665b56
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

# <a name="define-ribbon-actions"></a>Definieren von Menübandaktionen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-actions -->

Definieren Sie die Aktionen, die durch Befehlsleisten- oder Menübandsteuerelemente in einem `<CommandDefinition>`-Element in Kombination mit Regeln ausgeführt werden, die steuern, ob das Steuerelement aktiviert bzw. im Menüband angezeigt wird.  
  
 Ein Menüband-Steuerelement kann zwei Arten von Aktionen ausführen und umfasst möglicherweise mehrere Aktionen:  
  
- **JavaScript-Funktionen**: Ein `<JavaScriptFunction>`-Element verweist auf eine Funktion, die in einer Skript-Webressource definiert wird.  
  
- **Eine URL öffnen**: Das Menüband öffnet eine URL mithilfe des Werts aus einem Adressenattribut im `<Url>`-Element. Zusätzliche Parameter können Informationen dazu übergeben, welche querystring-Parameter übergeben werden und in welchem Modus das Fenster geöffnet wird.  
  
     Sie haben mehrere Möglichkeiten, Parameter an eine URL mithilfe des Menübands zu übergeben. Weitere Informationen: [Übergeben von Parametern an eineURL mithilfe des Menübands](pass-parameters-url-by-using-ribbon.md)  
  
### <a name="passing-parameters-to-ribbon-actions"></a>Übergeben von Parametern an Menübandaktionen  
 Verwenden Sie die folgenden Elemente ein, um Daten zu definieren, die an die benutzerdefinierte Aktion übergeben werden sollen:  
  
 `<BoolParameter>`  
[!INCLUDE[ribbon_element_BoolParameter](../../includes/ribbon-element-boolparameter.md)]
  
 `<CrmParameter>`  
 [!INCLUDE[ribbon_element_CrmParameter](../../includes/ribbon-element-crmparameter.md)] Weitere Informationen: [Übermitteln von -Daten von einer Seite als Parameter an Menüband-Aktionen](/dynamics365/customer-engagement/developer/customize-dev/pass-dynamics-365-data-page-parameter-ribbon-actionsd)<!-- TODO need to update the relevant link from the powerapps repo>
  
 `<DecimalParameter>`  
 [!INCLUDE[ribbon_element_DecimalParameter](../../includes/ribbon-element-decimalparameter.md)]
  
 `<IntParameter>`  
 [!INCLUDE[ribbon_element_IntParameter](../../includes/ribbon-element-intparameter.md)]
  
 `<StringParameter>`  
 [!INCLUDE[ribbon_element_StringParameter](../../includes/ribbon-element-stringparameter.md)]
  
 Wenn Parameter an ein `<Url>`-Element übergeben werden, werden sie als Abfragezeichenfolge übergeben. Daher müssen Sie einen Namenswert einschließen, um den "Schlüssel" in dem Paar aus Abfragezeichenfolgenschlüssel und -wert darzustellen.  
  
 Die Parameter, die an `<JavaScriptFunction>` übergeben werden, benötigen keinen Namen, aber sie müssen in folgender Reihenfolge eingeschlossen werden, die von der Funktion erwartet wird, und müssen vom richtigen Datentyp sein.  
  
### <a name="see-also"></a>Siehe auch  
 [Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)   
 [Definieren von Menüband-Anzeigeregeln](define-ribbon-display-rules.md)   
 [Daten von einer Seite als Parameter an Menüband-Aktionen übermitteln](/dynamics365/customer-engagement/developer/customize-dev/pass-dynamics-365-data-page-parameter-ribbon-actionsd)  <!-- TODO need to update the relevant link from the powerapps repo-->
