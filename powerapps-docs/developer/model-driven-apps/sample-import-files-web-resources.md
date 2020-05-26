---
title: 'Beispiel: Importieren von Dateien als Webressourcen (modellgestützte Apps) | Microsoft Docs'
description: Das Beispiel bietet ein vereinfachtes Beispiel des Importierens von Dateien als Webressourcen.
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
ms.openlocfilehash: f8662e7462ef54fa39084cf311faf756680505e7
ms.sourcegitcommit: 6c73e316f866af6a34619f95a5ac64ad1664b48a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "3326428"
---
# <a name="sample-import-files-as-web-resources"></a>Beispiel: Importieren von Dateien als Webressourcen

Wenn Sie viele Dateien entwickeln, die als Webressourcen verwendet werden sollen, können Sie sich das manuelle Hinzufügen über die Anwendung sparen. Viele Webressourcen können außerhalb von modellgestützten Apps entwickelt und getestet und dann importiert werden.  
  
 Dieses Beispiel bietet ein vereinfachtes Beispiel dieses Prozesses.  
 
 Laden Sie das Beispiel: [Dateien als Webressourcen importieren](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ImportWebResources) herunter. 

## <a name="prerequisites"></a>Voraussetzungen
[!INCLUDE[sdk-prerequisite](../../includes/sdk-prerequisite.md)]
  
## <a name="requirements"></a>Anforderungen  


<!-- TODO: This should be written so that the connection helper code is not required. [!INCLUDE[sdk_SeeConnectionHelper](../../includes/sdk-seeconnectionhelper.md)] -->
  
 Der Beispielcode, der im SDK-Downloadpaket enthalten ist, enthält die folgenden Dateien, die in diesem Beispiel erforderlich sind:  
  
 **ImportJob.xml**  
 Diese Datei enthält Daten zu den Webressourcendatensätzen, die erstellt werden. Sie enthält die folgenden Daten für jede Datei:  
  
- **path:** Der Pfad zu jeder Datei vom FilesToImport-Ordner.  
  
- **displayName:** Der Anzeigename für die Webressource.  
  
- **description:** Eine Beschreibung des Zwecks jeder Datei.  
  
- **name:** Der Name, der für die Webressource verwendet wird.  
  
  > [!NOTE]
  > - Jeder dieser Namen beginnt mit einem Unterstrich. Das Anpassungspräfix für den Lösungsherausgeber wird dem Namen vorangestellt, wenn die Webressource erstellt wird. Anstelle der Hartcodierung eines spezifischen Anpassungspräfixes erkennt dieses Beispiel das aktuelle Anpassungspräfix eines Herausgeberdatensatzes, das in der Organisation möglicherweise bereits vorhanden ist.  
  >   - Da jede dieser Dateien außerhalb von modellgestützten Apps entwickelt wurde und für den Zugriff auf eine der anderen Dateien von relativen Pfaden abhängt, enthalten die Namen Schrägstriche "/", damit eine virtuelle Ordnerstruktur erstellt werden kann und die relativen Links in modellgestützten Apps weiterhin verwendet werden können.  
  
- **type:** Gibt den Typ der Webressource an, die mithilfe der ganzzahligen Werte in [Webressourcentypen](web-resources.md#BKMK_WebResourceTypes) gefunden wurde.
  
  **FilesToImport/ShowData.htm**  
  Diese HTML-Webressource erfordert, dass in jeder der anderen Dateien die folgende Tabelle angezeigt wird.  
  
|||  
|-|-|  
|**Vorname**|**Nachname**|  
|Apurva|Dalia|  
|Ofer|Daliot|  
|Jim|Daly|  
|Ryan|Danner|  
|Mike|Danseglio|  
|Alex|Darrow|  
  
 **FilesToImport/CSS/Styles.css**  
 Diese Datei enthält die CSS Stylesheets, die in ShowData.htm verwendet werden.  
  
 **FilesToImport/Data/Data.xml**  
 Diese Datei enthält die Liste mit den Namen, die in der Tabelle angezeigt werden.  
  
 **FilesToImport/Script/Script.js**  
 Diese Datei enthält eine JScript-Bibliothek, die Informationen zum relativen Speicherort der Data.xml- und der Transform.xslt-Datei enthält. Sie enthält außerdem die `showData`-Funktion, die die Daten transformiert und zur ShowData.htm-Seite hinzufügt.  
  
 **FilesToImport/XSL/Transform.xslt**  
 Diese Datei enthält die XSL-Definition für die Transformierung der Daten in eine HTML-Tabelle.  
  
## <a name="demonstrates"></a>Demonstriert  
  
### <a name="creating-web-resources-in-the-context-of-a-solution"></a>Erstellen von Webressourcen im Kontext einer Lösung  
 Webressourcen sind Datensätze im Besitz der Organisation, sodass sie mithilfe der<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> Methode oder mit der <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>-Nachricht und der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> erstellt werden können. Methode. In diesem Beispiel wird gezeigt, wie der optionale Parameter `SolutionUniqueName` verwendet wird, um eine Webressource einer bestimmten Lösung zuzuordnen, wenn sie erstellt wird. Dies erfordert die Verwendung der <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>-Meldung.  
  
### <a name="uploading-files-from-disk"></a>Hochladen von Dateien von einem Datenträger  
 Die WebResource.Content-Eigenschaft erfordert eine Base64-Zeichenfolge, die die binären Inhalte der Datei darstellt. Das folgende Beispiel zeigt die Methode, die verwendet wird, um die Datei in den erforderlichen Typ zu konvertieren.  
  
```C#
//Encodes the Web Resource File
static public string getEncodedFileContents(String pathToFile)
{
    FileStream fs = new FileStream(pathToFile, FileMode.Open, FileAccess.Read);
    byte[] binaryData = new byte[fs.Length];
    long bytesRead = fs.Read(binaryData, 0, (int)fs.Length);
    fs.Close();
    return System.Convert.ToBase64String(binaryData, 0, binaryData.Length);
}
```
  
### <a name="combining-web-resource-record-data-with-file-data"></a>Kombinieren von Webressourcen-Datensatzdaten mit Dateidaten  
 Die ImportJob.xml-Datei veranschaulicht, wie die Daten zu den Dateien, die importiert werden, und die Daten zu der Webressource, die erstellt wird, kombiniert werden. Damit die relativen Links zwischen den verknüpften Dateien weiterhin verwendet werden können, müssen im Namen der Webressourcen, die Sie erstellen, Informationen zur relativen Position der Dateien auf dem Datenträger mithilfe von simulierten Verzeichnissen im Dateinamen beibehalten werden. Aufgrund der Daten in der ImportJob.xml-Datei werden alle verknüpften Webressourcedateien in einem allgemeinen virtuellen Ordner erstellt.  
  
> [!NOTE]
>  Es ist nicht erforderlich, die Webressourcen zu veröffentlichen, wenn sie erstellt werden. Es ist erforderlich, sie zu veröffentlichen, wenn sie aktualisiert werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Teil der ImportWebResources.cs-Datei werden die folgenden Variablen erwartet:  
  
- `_customizationPrefix` : Das Anpassungspräfix des **SDK-Beispiele**-Veröffentlichers. Wenn dieser Herausgeber nicht vorhanden ist, wird er mit dem Anpassungspräfix "sample" erstellt.  
  
- `_ImportWebResourcesSolutionUniqueName`: Der eindeutige Name der **Beispiellösung zum Importieren von Webressourcen**, die in diesem Beispiel erstellt wird. Der Wert ist `ImportWebResourcesSample`.  
  
```C#
//Read the descriptive data from the XML file
XDocument xmlDoc = XDocument.Load("../../ImportJob.xml");

//Create a collection of anonymous type references to each of the Web Resources
var webResources = from webResource in xmlDoc.Descendants("webResource")
                   select new
                   {
                       path = webResource.Element("path").Value,
                       displayName = webResource.Element("displayName").Value,
                       description = webResource.Element("description").Value,
                       name = webResource.Element("name").Value,
                       type = webResource.Element("type").Value
                   };

// Loop through the collection creating Web Resources
int counter = 0;
foreach (var webResource in webResources)
{
    //Set the Web Resource properties
    WebResource wr = new WebResource
    {
        Content = getEncodedFileContents(@"../../" + webResource.path),
        DisplayName = webResource.displayName,
        Description = webResource.description,
        Name = _customizationPrefix + webResource.name,
        LogicalName = WebResource.EntityLogicalName,
        WebResourceType = new OptionSetValue(Int32.Parse(webResource.type))
    };

    // Using CreateRequest because we want to add an optional parameter
    CreateRequest cr = new CreateRequest
    {
        Target = wr
    };
    //Set the SolutionUniqueName optional parameter so the Web Resources will be
    // created in the context of a specific solution.
    cr.Parameters.Add("SolutionUniqueName", _ImportWebResourcesSolutionUniqueName);

    CreateResponse cresp = (CreateResponse)_serviceProxy.Execute(cr);
    // Capture the id values for the Web Resources so the sample can delete them.
    _webResourceIds[counter] = cresp.id;
    counter++;
    Console.WriteLine("Created Web Resource: {0}", webResource.displayName);
}
```
  
  Es ist nicht erforderlich, die Webressourcen zu veröffentlichen, wenn sie erstellt werden. Es ist erforderlich, sie zu veröffentlichen, wenn sie aktualisiert werden.  
  
### <a name="see-also"></a>Siehe auch  
 [WebResource-Entitätsreferenz](../common-data-service/reference/entities/webresource.md)<br/>
 [Webressourcen](web-resources.md)
