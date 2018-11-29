---
title: Erstellen von Erweiterungen für die Generierung von Codetools (Common Data Service for Apps) | Microsoft Docs
description: 'Das SDK-Downloadpaket enthält eine Erweiterung für das CrmSvcUtil-Codegenerierungstool, das Sie verwenden können, um Enumerationen für alle Optionssatzwerte, einschließlich globaler Optionssätze, Auswähllisten, Status und Statuswerte zu generieren.'
ms.custom: ''
ms.date: 10/31/2018
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
# <a name="create-extensions-for-the-code-generation-tool"></a>Erstellen von Erweiterungen für das Codegenerierungstool

Sie können die Funktionalität des Codegenerierungstools erweitern, indem Sie zusätzliche Befehlszeilenparameter und Parameterwerte angeben. Um einen Parameter anzugeben, fügen Sie der Eingabeaufforderung Folgendes hinzu: /\<*parametername*>:\<*class name*>,\<*assembly name*>. Beachten Sie, dass assembly name nicht die .dll-Erweiterung enthält. Alternativ können Sie den Gegenwert der CONFIG-Datei im Format “<add key=”\<*parametername*>” value=”\<*class name*>,\<*assembly name*>” />” hinzufügen.  

In der folgenden Tabelle werden die Parameter aufgeführt, die Sie verwenden können:  

|Parametername|Schnittstellenname|Beschreibung|  
|--------------------|--------------------|-----------------|  
|/codecustomization|ICustomizeCodeDomService|Aufgerufen, nachdem die CodeDOM-Generierung abgeschlossen wurde, nimmt die Standardinstanz von `ICodeGenerationService` an. Dies ist nützlich zum Erstellen von zusätzlichen Klassen, wie die Konstanten in Auswahllisten.|  
|/codewriterfilter|ICodeWriterFilterService|Angerufen während des Vorgangs der CodeDOM-Generierung, nimmt die Standardinstanz von `ICodeGenerationService` an, um zu bestimmen, ob ein bestimmtes Objekt oder eine Eigenschaft generiert werden soll.|  
|/codewritermessagefilter|ICodeWriterMessageFilterService|Angerufen während des Vorgangs der CodeDOM-Generierung, nimmt die Standardinstanz von `ICodeGenerationService` an, um zu bestimmen, ob eine bestimmte Nachricht generiert werden soll. Dies sollte nicht verwendet für Anforderungen und Antworten, da diese bereits in Microsoft.Crm.Sdk.Proxy.dll und in Microsoft.Xrm.Sdk.dll generiert werden.|  
|/metadataproviderservice|IMetadataProviderService|Aufgerufen, um Metadaten vom Server abzurufen. Dies kann mehrmals während des Generierungsprozesses aufgerufen werden, daher sollten die Daten zwischengespeichert werden.|  
|/codegenerationservice|ICodeGenerationService|Kernimplementierung der CodeDOM-Generierung. Wenn dieses geändert wird, verhalten sich unter Umständen die anderen Erweiterungen nicht in der beschriebenen Weise.|  
|/namingservice|INamingService|Angerufen während der CodeDOM-Generierung, um den Namen für Objekte zu bestimmen, die Standardimplementierung vorausgesetzt.|

Die Implementierung dieser Schnittstellen muss einen der folgenden Konstruktoren haben:

`MyNamingService`()<br />
`MyNamingService`(`INamingService``defaultService`)<br />
`MyNamingService`(`IDictionary`<`string`, `string`> `parameters`)<br />
`MyNamingService`(`INamingService``defaultService`, `IDictionary`<`string`, `string`> `parameters`)

Der `Microsoft.Crm.Services.Utility`-Namespace wird in CrmSvcUtil.exe definiert. Fügen einen Verweis auf CrmSvcUtil.exe in Ihren Visual Studio-Codegenerierungstool-Erweiterungsprojekten hinzu.

<a name="Generate_Enums"></a>

## <a name="sample-extension-to-generate-enumerations-for-option-sets"></a>Beispielerweiterung, um Enumerationen für Optionssätze zu generieren

Der folgende Beispielcode zeigt, wie eine Erweiterung geschrieben wird.  

```csharp
using System;

using Microsoft.Crm.Services.Utility;
using Microsoft.Xrm.Sdk.Metadata;

/// <summary>
/// Sample extension for the CrmSvcUtil.exe tool that generates early-bound
/// classes for custom entities.
/// </summary>
public sealed class BasicFilteringService : ICodeWriterFilterService
{
    public BasicFilteringService(ICodeWriterFilterService defaultService)
    {
        this.DefaultService = defaultService;
    }

    private ICodeWriterFilterService DefaultService { get; set; }

    bool ICodeWriterFilterService.GenerateAttribute(AttributeMetadata attributeMetadata, IServiceProvider services)
    {
        return this.DefaultService.GenerateAttribute(attributeMetadata, services);
    }

    bool ICodeWriterFilterService.GenerateEntity(EntityMetadata entityMetadata, IServiceProvider services)
    {
        if (!entityMetadata.IsCustomEntity.GetValueOrDefault()) { return false; }
        return this.DefaultService.GenerateEntity(entityMetadata, services);
    }

    bool ICodeWriterFilterService.GenerateOption(OptionMetadata optionMetadata, IServiceProvider services)
    {
        return this.DefaultService.GenerateOption(optionMetadata, services);
    }

    bool ICodeWriterFilterService.GenerateOptionSet(OptionSetMetadataBase optionSetMetadata, IServiceProvider services)
    {
        return this.DefaultService.GenerateOptionSet(optionSetMetadata, services);
    }

    bool ICodeWriterFilterService.GenerateRelationship(RelationshipMetadataBase relationshipMetadata, EntityMetadata otherEntityMetadata,
    IServiceProvider services)
    {
        return this.DefaultService.GenerateRelationship(relationshipMetadata, otherEntityMetadata, services);
    }

    bool ICodeWriterFilterService.GenerateServiceContext(IServiceProvider services)
    {
        return this.DefaultService.GenerateServiceContext(services);
    }
}

```

Laden Sie das Beispiel herunter: [CrmSvcUtilExtensions](https://code.msdn.microsoft.com/Create-extensions-for-the-b8b24d1d) und [GeneratePickListEnums](https://code.msdn.microsoft.com/Create-extensions-for-the-3dd56a27). 

Die **GeneratePicklistEnums**-Beispielerweiterung gibt eine Quellcodedatei aus, die Enumerationn fü alle Optionssätze, Zustandscodes und Statuscodes enthält. Ein Beispiel dafür, wie diese Enumerationen verwendet werden, finden Sie im `SampleCode\CS\QuickStart`-Beispiel.  

Außerdem enthält es ein Hilfecodedatei, die Enumerationen enthält, die für alle angepassten Werte generiert werden. Diese Enumerationen können in Ihrem Code verwendet werden, indem die Datei `SampleCode\CS\HelperCode\OptionSets.cs` oder `SampleCode\VB\HelperCode\OptionSets.vb` dem Projekt hinzugefügt werden.

Jede Enumeration kann dazu verwendet werden, den Wert für eine Eigenschaft zu testen oder festzulegen. Normalerweise ist diese Eigenschaft ein Entitätsattribut, aber es gibt einige, die für andere Eigenschaften verwendet werden.

### <a name="usage-example"></a>Verwendungsbeispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie eine dieser Enumerationen verwendet können, um einen Wert in der Entität `Account` festzulegen.

```csharp
// Instantiate an account object. Note the use of the option set enumerations defined
// in OptionSets.cs.
Account account = new Account { Name = "Fourth Coffee" };
account.AccountCategoryCode = new OptionSetValue((int)AccountAccountCategoryCode.PreferredCustomer);
account.CustomerTypeCode = new OptionSetValue((int)AccountCustomerTypeCode.Investor);

// Create an account record named Fourth Coffee.
// Save the record reference so we can delete it during cleanup later.
Guid accountId = service.Create(account);
```

### <a name="see-also"></a>Siehe auch

 [Entitätsklassen mit früher Bindung mit dem Codegenerierungstool erstellen (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/create-early-bound-entity-classes-code-generation-tool)<br />
 [Verwenden der Entitätsklassen mit früher Bindung zum Erstellen, Löschen und Aktualisieren](/dynamics365/customer-engagement/developer/use-entity-class-create-update-delete)<br />
 [Problembehandlungs-Tipps](/dynamics365/customer-engagement/developer/troubleshooting-tips)<br />
 [Ausführen eines einfachen Programms mit Webdiensten](/dynamics365/customer-engagement/developer/simple-program-web-services)
