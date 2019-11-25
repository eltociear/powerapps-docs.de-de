---
title: Menübanddefinitionen exportieren (Modell-angetriebene Apps) | Microsoft Docs
description: Infos zum Exportieren der Menübanddefinitionen.
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
ms.openlocfilehash: d6c342d1b5c3b5864aaf556af800c0f439a3e272
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753618"
---
# <a name="export-ribbon-definitions"></a>Exportieren von Menübanddefinitionen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/export-ribbon-definitions -->

Wenn Sie Änderungen am Standard-RibbonXml effektiv definieren wollen, müssen Sie die RibbonXml-Daten referenzieren können, die diese Menübänder definieren.  
  
<a name="BKMK_AccessRibbonDefinitionsForYourOrganization"></a>   
## <a name="access-the-ribbon-definitions-for-your-organization"></a>Zugriff auf die Menübanddefinitionen für Ihre Organisation  
 Wenn für Ihre Organisation das Menüband geändert wurde, sollten Sie die aktuellen Definitionen exportieren, wenn mit den benutzerdefinierten Menübandelementen arbeiten möchten. Verwenden Sie dazu das exportribbonxml-Beispiel unter `SampleCode\CS\Client\Ribbon\ExportRibbonXml`.  
  
<a name="BKMK_AccessDefaultRibbonData"></a>   
## <a name="access-the-default-ribbon-data"></a>Zugriff auf die Menüband-Standarddaten  
 Die standardmäßigen Menübanddefnitionen für modellgetriebene Apps können heruntergeladen werden von [Microsoft Downloads: ExportedRibbonXml.zip](https://download.microsoft.com/download/C/2/A/C2A79C47-DD2D-4938-A595-092CAFF32D6B/ExportedRibbonXml.zip) 
  
 Die applicationRibbon.xml-Datei enthält die Definition der Kernanwendungsmenübänder.  
  
 Der übrigen Dateien enthalten die Definitionen, die von Entitäten verwendet werden, die Menübanddefinitionen haben, die von der Entitätsvorlage abweichen. Jede Datei wird gemäß dem Namen der Entität benannt: logischer Entitätsname + Ribbon.xml.  
  
 Diese Dateien repräsentieren die Ausgabe zweier Meldungen mit den [Beispiel: Export von Menübanddefinitionen](sample-export-ribbon-definitions.md):  
  
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveApplicationRibbonRequest>  
 Diese Meldung ruft die Menübänder der Kernanwendung ab, einschließlich der Entitätsvorlage.  
  
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest>  
 Diese Meldung ruft die Menübanddefinition ab, die für eine bestimmte Entität verwendet wird.  
  
### <a name="decompress-the-ribbon-data"></a>Dekomprimieren der Menübanddaten  
 Die Menübanddaten werden als komprimierte Datei exportiert. Zur Dekomprimierung der Datei in XML müssen Sie die [System.IO.Packaging.ZipPackage](https://msdn.microsoft.com/library/system.io.packaging.zippackage.aspx)-Klasse verwenden. Das folgende Beispiel ist eine Hilfsmethode, die im SDK-Beispiel verwendet wird, um die Datei zu dekomprimieren.  
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
 //Retrieve the Appliation Ribbon
RetrieveApplicationRibbonRequest appribReq = new RetrieveApplicationRibbonRequest();
RetrieveApplicationRibbonResponse appribResp = (RetrieveApplicationRibbonResponse)_serviceProxy.Execute(appribReq);

System.String applicationRibbonPath = Path.GetFullPath(exportFolder + "\\applicationRibbon.xml");
File.WriteAllBytes(applicationRibbonPath, unzipRibbon(appribResp.CompressedApplicationRibbonXml)); 
```
  
### <a name="retrieve-entity-ribbons"></a>Abrufen von Entitätsmenübändern  
 Um die Menübanddefinition für Entitäten abzurufen, können Sie einfach den Namen der Entität als Parameter in <xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest> einschließen.  
  
 Zum Abrufen der Menübanddefinitionen für alle Entitäten, die das Menüband unterstützen, benötigen Sie eine Liste der Systementitäten, die Menübanddefinitionen haben, die von der Entitätsmenübandvorlage abweichen. Das folgende Beispiel zeigt eine Reihe aller Systementitäten, die Menübanddefinitionen haben.  
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
  ```C#
 //Retrieve system Entity Ribbons
RetrieveEntityRibbonRequest entRibReq = new RetrieveEntityRibbonRequest() { RibbonLocationFilter = RibbonLocationFilters.All };

foreach (System.String entityName in entitiesWithRibbons)
{
 entRibReq.EntityName = entityName;
 RetrieveEntityRibbonResponse entRibResp = (RetrieveEntityRibbonResponse)_serviceProxy.Execute(entRibReq);

 System.String entityRibbonPath = Path.GetFullPath(exportFolder + "\\" + entityName + "Ribbon.xml");
 File.WriteAllBytes(entityRibbonPath, unzipRibbon(entRibResp.CompressedEntityXml));
 //Write the path where the file has been saved.
 Console.WriteLine(entityRibbonPath);
} 
 ``` 
 Alle benutzerdefinierten Entitäten unterstützen auch Menübandanpassungen. Zum Anzeigen einer Liste von benutzerdefinierten Entitäten verwenden Sie  <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest>, und rufen Sie die Namen von benutzerdefinierten Entitäten ab. Das folgende Beispiel zeigt, wie Sie die Menübanddefinitionen für alle benutzerdefinierten Entitäten abrufen.  
```C#  
//Check for custom entities
 RetrieveAllEntitiesRequest raer = new RetrieveAllEntitiesRequest() { EntityFilters = EntityFilters.Entity };

 RetrieveAllEntitiesResponse resp = (RetrieveAllEntitiesResponse)_serviceProxy.Execute(raer);

 foreach (EntityMetadata em in resp.EntityMetadata)
 {
  if (em.IsCustomEntity == true && em.IsIntersect == false)
  {
   entRibReq.EntityName = em.LogicalName;
   RetrieveEntityRibbonResponse entRibResp = (RetrieveEntityRibbonResponse)_serviceProxy.Execute(entRibReq);

   System.String entityRibbonPath = Path.GetFullPath(exportFolder + "\\" + em.LogicalName + "Ribbon.xml");
   File.WriteAllBytes(entityRibbonPath, unzipRibbon(entRibResp.CompressedEntityXml));
   //Write the path where the file has been saved.
   Console.WriteLine(entityRibbonPath);
  }
 }
}  
```  
### <a name="see-also"></a>Siehe auch  
 [Anpassen des Menübands](customize-commands-ribbon.md)   
 [Darstellen von Befehlsleisten und Menübändern](command-bar-ribbon-presentation.md)   
 [Exportieren, Vorbereitung der Bearbeitung und Importieren des Menübands](export-prepare-edit-import-ribbon.md)
