---
title: 'Verwenden von Upsert, um einen Datensatz einzufügen oder zu aktualisieren (Common Data Service) | Microsoft Docs'
description: 'Die UpsertRequest(Update oder Insert)-Meldung hilft Ihnen, verschiedene Datenintegrationsszenarien zu vereinfachen, in denen Sie nicht wissen, ob ein Datensatz bereits in Dynamics 365 existiert. In solchen Fällen wissen Sie nicht, ob Sie einen UpdateRequest- oder CreateRequest-Vorgang aufrufen müssen. Dies führt dazu, dass bei der Abfrage des Datensatzes zuerst bestimmt werden muss, ob er vorhanden ist, bevor der entsprechende Vorgang ausgeführt wird. Die UpsertRequest-Meldung hilft Ihnen, dieses zu Problem beheben'
ms.custom: ''
ms.date: 02/23/2019
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
# <a name="use-upsert-to-insert-or-update-a-record"></a>Einen Datensatz mit Upsert einfügen oder aktualisieren

Sie können die Komplexität verringern, die in Datenintegrationsszenarien involviert ist, indem Sie die Nachricht <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> verwenden. Wenn Sie Daten in Common Data Service von einem externen System laden, beispielsweise in einem Massendaten-Integrationsszenario, wissen Sie möglicherweise nicht, ob ein Datensatz bereits in Common Data Service vorhanden ist. In solchen Fällen wissen Sie nicht, ob Sie einen <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>- oder <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>-Vorgang aufrufen müssen. Dies führt dazu, dass bei der Abfrage des Datensatzes zuerst bestimmt werden muss, ob er vorhanden ist, bevor der entsprechende Vorgang ausgeführt wird. Sie können jetzt diese Komplexität verringern und Daten effizienter in Common Data Service zu laden, indem die neue <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> (Aktualisieren oder Einfügen)-Message verwendet wird.  
  
<a name="BKMK_UsingUpsert"></a>   
## <a name="using-upsert"></a>Verwenden von Upsert  
 Es ist am besten, <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> nur zu verwenden, wenn Sie nicht sicher sind, ob der Datensatz vorhanden ist. Das bedeutet, wenn Sie nicht sicher sind, ob Sie einen <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>- oder <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>-Vorgang aufrufen sollten. Es gibt eine Leistungsabnahme beim Verwenden von <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> im Vergleich zum Verwenden von <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>. Wenn Sie sicher sind, dass der Datensatz nicht vorhanden ist, verwenden Sie <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>.  
  
 <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> enthält eine Eigenschaft namens <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest.Target>. Diese Eigenschaft enthält die Entitätsdefinition, die in einem <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>- oder <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>-Vorgang verwendet wird. Sie enthält auch alle Attribute, die von <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> für den Zielentitätstyp erforderlich sind, damit der Datensatz erstellt werden, wenn er nicht vorhanden ist.  
  
 Sie können <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.RecordCreated> überprüfen, um zu ermitteln, ob der Datensatz erstellt wurde. <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.RecordCreated> ist TRUE, wenn der Datensatz nicht vorhanden war und erstellt wurde. Es ist FALSE, wenn der Datensatz bereits vorhanden war und aktualisiert wurde. <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.Target> ist eine `EntityReference` für den Datensatz, der als vorhanden ermittelt wurde, oder für den Datensatz, der erstellt wurde.  
  
 Um zu verstehen, wie <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> funktioniert, vgl. folgenden Abschnitt.  
  
<a name="BKMK_upsert"></a>   
## <a name="understanding-the-upsert-process"></a>Grundlegendes zum Upsert-Prozesses  
 Im Folgenden wird die Ablauflogik bei Erhalt einer <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> beschrieben:  
  
1. Senden Sie <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> mit genügend Daten für einen Erstellungs- oder Einfügevorgang.  
  
2. Common Data Service sucht den Datensatz, auf den die Zielentität ausgerichtet ist.  
  
3. Wenn der Datensatz vorhanden ist:  
  
   1.  Legen Sie die ID-Eigenschaft der Zielentität mit der ID des gefundenen Datensatzes fest.  
  
   2.  Rufen Sie das Update auf.  
  
   3.  Legen Sie den <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.RecordCreated> auf `false` fest.  
  
   4.  Erstellen Sie ein <xref:Microsoft.Xrm.Sdk.EntityReference> aus der Zielentität des Updates als Wert für <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.Target>.  
  
   5.  Geben Sie den <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse> zurück.  
  
4. Wenn der Datensatz nicht vorhanden ist:  
  
   1.  Kopieren Sie alle Alternativschlüsselwerte in die Zielentitätsattribute.  
  
   2.  Rufen Sie `Create` auf.  
  
   3.  Legen Sie den <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.RecordCreated> auf `true` fest.  
  
   4.  Erstellen Sie einen <xref:Microsoft.Xrm.Sdk.EntityReference> aus dem Zielentitätstyp und ID-Ergebnis der `Create`-Anfrage als Wert für <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.Target>.  
  
   5.  Geben Sie den <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse> zurück.  
  
   Die folgende Abbildung zeigt den Prozess an, der aufgeklappt wird, wenn ein <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> empfangen wird.  
  
   ![Upsert-Prozessfluss](media/upsert-flowchart-dynamics-crm-2015.png "Upsert-Prozessfluss")  
  
<a name="BKMK_SampleCode"></a>   
## <a name="sample-code"></a>Beispielcode  
 Die Datei [ProductUpsertSample.cs](https://code.msdn.microsoft.com/Insert-or-update-a-record-aa160870/sourcecode?fileId=136218&pathId=1243320355) des Beispiels [Einen Datensatz mit Upsert einfügen oder aktualisieren](http://go.microsoft.com/fwlink/p/?LinkId=532924) enthält die folgende `ProcessUpsert`-Methode, um die `UpsertRequest`-Meldung auf den Inhalt einer XML-Datei anzuwenden, um neue Datensätze zu erstellen oder vorhandene zu aktualisieren.  
  
```csharp
public void ProcessUpsert(String Filename)
{
    Console.WriteLine("Executing upsert operation.....");
    XmlTextReader tr = new XmlTextReader(Filename);
    XmlDocument xdoc = new XmlDocument();
    xdoc.Load(tr);
    XmlNodeList xnlNodes = xdoc.DocumentElement.SelectNodes("/products/product");

    foreach (XmlNode xndNode in xnlNodes)
    {
        String productCode = xndNode.SelectSingleNode("Code").InnerText;
        String productName = xndNode.SelectSingleNode("Name").InnerText;
        String productCategory = xndNode.SelectSingleNode("Category").InnerText;
        String productMake = xndNode.SelectSingleNode("Make").InnerText;

        //use alternate key for product
        Entity productToCreate = new Entity("sample_product", "sample_productcode", productCode);

        productToCreate["sample_name"] = productName;
        productToCreate["sample_category"] = productCategory;
        productToCreate["sample_make"] = productMake;
        UpsertRequest request = new UpsertRequest()
        {
            Target = productToCreate
        };

        try
        {
            // Execute UpsertRequest and obtain UpsertResponse. 
            UpsertResponse response = (UpsertResponse)_serviceProxy.Execute(request);
            if (response.RecordCreated)
                Console.WriteLine("New record {0} is created!", productName);
            else
                Console.WriteLine("Existing record {0} is updated!", productName);
        }

        // Catch any service fault exceptions that Microsoft Dynamics CRM throws.
        catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault>)
        {
            throw;
        }

    }
    // Prompts to view the sample_product entity records.
    // If you choose "y", IE will be launched to display the new or updated records.
    if (PromptForView())
    {
        ViewEntityListInBrowser();
    }

}
```
  
### <a name="see-also"></a>Siehe auch  
 [Synchronisieren von Daten mit externen Systemen mithilfe der Änderungsnachverfolgung](use-change-tracking-synchronize-data-external-systems.md)   
 [Definieren von Alternativschlüsseln für eine Entität](define-alternate-keys-entity.md)   
 [Verwenden von Alternativschlüsseln](use-alternate-key-create-record.md)
