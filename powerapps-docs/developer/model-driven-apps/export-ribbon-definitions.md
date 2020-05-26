---
title: Menübanddefinitionen exportieren (Modell-angetriebene Apps) | Microsoft Docs
description: Infos zum Exportieren der Menübanddefinitionen.
ms.custom: ''
ms.date: 04/30/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: nkrb
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2b0ca0fb153813a0ed5b48e9df8344d3b6741057
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341363"
---
# <a name="export-ribbon-definitions"></a>Exportieren von Menübanddefinitionen

Wenn Sie Änderungen am Standard-RibbonXml effektiv definieren wollen, müssen Sie die RibbonXml-Daten referenzieren können, die diese Menübänder definieren.  
  
## <a name="access-the-ribbon-definitions-for-your-organization"></a>Zugriff auf die Menübanddefinitionen für Ihre Organisation  

Wenn für Ihre Organisation das Menüband geändert wurde, sollten Sie die aktuellen Definitionen exportieren, wenn mit den benutzerdefinierten Menübandelementen arbeiten möchten. Verwenden Sie dazu das Beispiel [Export Ribbon xml](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportRibbonDefinitions).  
  
## <a name="access-the-default-ribbon-data"></a>Zugriff auf die Menüband-Standarddaten  

 Die Standarddefinitionen von Menübändern für modellbasierte Apps können unter [Microsoft Downloads heruntergeladen werden: ExportedRibbonXml.zip](https://download.microsoft.com/download/C/2/A/C2A79C47-DD2D-4938-A595-092CAFF32D6B/ExportedRibbonXml.zip) heruntergeladen werden. 
  
 Die applicationRibbon.xml-Datei enthält die Definition der Kernanwendungsmenübänder.  
  
 Der übrigen Dateien enthalten die Definitionen, die von Entitäten verwendet werden, die Menübanddefinitionen haben, die von der Entitätsvorlage abweichen. Jede Datei wird gemäß dem Namen der Entität benannt: logischer Entitätsname + Ribbon.xml.  
  
 Diese Dateien repräsentieren die Ausgabe zweier Meldungen mit den [Beispiel: Export von Menübanddefinitionen](sample-export-ribbon-definitions.md):  
  
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveApplicationRibbonRequest>  
 Diese Meldung ruft die Menübänder der Kernanwendung ab, einschließlich der Entitätsvorlage.  
  
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest>  
 Diese Meldung ruft die Menübanddefinition ab, die für eine bestimmte Entität verwendet wird.  
  
### <a name="decompress-the-ribbon-data"></a>Dekomprimieren der Menübanddaten  

 Die Menübanddaten werden als komprimierte Datei exportiert. Um die Datei in XML zu dekomprimieren, müssen Sie die Klasse [System.IO.Packaging.ZipPackage](https://msdn.microsoft.com/library/system.io.packaging.zippackage.aspx) verwenden. Das folgende Beispiel ist eine Hilfsmethode, die im SDK-Beispiel verwendet wird, um die Datei zu dekomprimieren.  

 ``` C# 
/// <summary>
/// A helper method that decompresses the Ribbon data returned
/// </summary>
/// <param name="data">The compressed ribbon data</param>
/// <returns></returns>
public byte[] unzipRibbon(byte[] data)
{
 System.IO.Packaging.ZipPackage package = null;
 MemoryStream memStream = null;

 memStream = new MemoryStream();
 memStream.Write(data, 0, data.Length);
 package = (ZipPackage)ZipPackage.Open(memStream, FileMode.Open);

 ZipPackagePart part = (ZipPackagePart)package.GetPart(new Uri("/RibbonXml.xml", UriKind.Relative));
 using (Stream strm = part.GetStream())
 {
  long len = strm.Length;
  byte[] buff = new byte[len];
  strm.Read(buff, 0, (int)len);
  return buff;
 }
}

```

### <a name="retrieve-the-application-ribbon-data"></a>Abrufen der Anwendungsmenübanddaten  

 Das Anwendungsmenüband kann mithilfe von <xref:Microsoft.Crm.Sdk.Messages.RetrieveApplicationRibbonRequest> wie im folgenden Beispiel angezeigt abgerufen werden.  

 ```C# 
 //Retrieve the Application Ribbon
var appribReq = new RetrieveApplicationRibbonRequest();
var appribResp = (RetrieveApplicationRibbonResponse)service.Execute(appribReq);

System.String applicationRibbonPath = Path.GetFullPath(exportFolder + "\\applicationRibbon.xml");
File.WriteAllBytes(applicationRibbonPath, unzipRibbon(appribResp.CompressedApplicationRibbonXml)); 
```
  
### <a name="retrieve-entity-ribbons"></a>Abrufen von Entitätsmenübändern  

 Um die Menübanddefinition für Entitäten abzurufen, können Sie einfach den Namen der Entität als Parameter in <xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest> einschließen.  
  
 Um die Menüband-Definitionen für alle Entitäten abzurufen, die das Menüband unterstützen, benötigen Sie eine Liste der Systemeinheiten, deren Menüband-Definitionen von der Vorlage für das Entitäten-Menüband abweichen. Das folgende Beispiel zeigt eine Reihe aller Systementitäten, die Menübanddefinitionen haben.  

 ```C# 
 //This array contains all of the system entities that use the ribbon.
public System.String[] entitiesWithRibbons = {"account",
"activitymimeattachment",
"activitypointer",
"appointment",
"bulkoperation",
"calendar",
"campaign",
"campaignactivity",
"campaignresponse",
"competitor",
"connection",
"contact",
"contract",
"contractdetail",
"convertrule",
"convertruleitem",
"customeraddress",
"discount",
"discounttype",
"email",
"emailserverprofile",
"entitlement",
"entitlementchannel",
"entitlementtemplate",
"entitlementtemplatechannel",
"fax",
"goal",
"goalrollupquery",
"importfile",
"incident",
"invoice",
"invoicedetail",
"kbarticle",
"kbarticlecomment",
"lead",
"letter",
"list",
"listmember",
"mailbox",
"metric",
"opportunity",
"opportunityproduct",
"partnerapplication",
"phonecall",
"postfollow",
"pricelevel",
"product",
"productpricelevel",
"queue",
"queueitem",
"quote",
"quotedetail",
"recurringappointmentmaster",
"report",
"rollupfield",
"routingrule",
"routingruleitem",
"salesliterature",
"salesliteratureitem",
"salesorder",
"salesorderdetail",
"service",
"serviceappointment",
"sharepointdocument",
"sharepointdocumentlocation",
"sharepointsite",
"site",
"sla",
"slaitem",
"socialactivity",
"socialprofile",
"systemuser",
"task",
"team",
"teamtemplate",
"territory",
"uom",
"uomschedule",
"userquery"};
 ```
  
Das folgende Beispiel zeigt, wie Sie die Menübanddefinitionen für einen Satz von Entitäten abrufen. 

```csharp
//Retrieve system Entity Ribbons
var entRibReq = new RetrieveEntityRibbonRequest() { RibbonLocationFilter = RibbonLocationFilters.All };
foreach (System.String entityName in entitiesWithRibbons)
{
 entRibReq.EntityName = entityName;
 var entRibResp = (RetrieveEntityRibbonResponse)service.Execute(entRibReq);

 System.String entityRibbonPath = Path.GetFullPath(exportFolder + "\\" + entityName + "Ribbon.xml");
 File.WriteAllBytes(entityRibbonPath, unzipRibbon(entRibResp.CompressedEntityXml));
 //Write the path where the file has been saved.
 Console.WriteLine(entityRibbonPath);
} 
``` 
Alle benutzerdefinierten Entitäten unterstützen auch Menübandanpassungen. Zum Anzeigen einer Liste von benutzerdefinierten Entitäten verwenden Sie  <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest>, und rufen Sie die Namen von benutzerdefinierten Entitäten ab. Das folgende Beispiel zeigt, wie Sie die Menübanddefinitionen für alle benutzerdefinierten Entitäten abrufen.  

```csharp 
//Check for custom entities
 var raer = new RetrieveAllEntitiesRequest() { EntityFilters = EntityFilters.Entity };
 var resp = (RetrieveAllEntitiesResponse)service.Execute(raer);
 foreach (EntityMetadata em in resp.EntityMetadata)
 {
  if (em.IsCustomEntity == true && em.IsIntersect == false)
  {
   entRibReq.EntityName = em.LogicalName;
   var entRibResp = (RetrieveEntityRibbonResponse)service.Execute(entRibReq);
   System.String entityRibbonPath = Path.GetFullPath(exportFolder + "\\" + em.LogicalName + "Ribbon.xml");
   File.WriteAllBytes(entityRibbonPath, unzipRibbon(entRibResp.CompressedEntityXml));
   //Write the path where the file has been saved.
   Console.WriteLine(entityRibbonPath);
  }
 } 
``` 

## <a name="troubleshoot-ribbon-issues"></a>Beheben von Menübandproblemen

Wenn bei Ihnen ein Problem mit einer Schaltfläche in der Menüband-Befehlsleiste auftritt, verwenden Sie diesen [Fehlerbehebungsleitfaden](https://support.microsoft.com/help/4552163), um das Problem zu finden und zu lösen.

### <a name="see-also"></a>Siehe auch  
 [Anpassen des Menübands](customize-commands-ribbon.md)   
 [Darstellen von Befehlsleisten und Menübändern](command-bar-ribbon-presentation.md)   
 [Exportieren, zum Bearbeiten vorbereiten und Importieren des Menübandes](export-prepare-edit-import-ribbon.md)
