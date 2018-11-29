---
title: SolutionPackager Tool (Common Data Service für Apps) | MicrosoftDocs
description: 'SolutionPackager ist ein Tool, mit dem eine komprimierte Dynamics 365 Customer Engagement-Lösungsdatei reversibel in mehrere XML-Dateien und andere Dateien zerlegt werden kann, so dass diese Dateien durch ein Quellcodeverwaltungssystem leicht verwaltet werden können.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="solutionpackager-tool"></a>SolutionPackager-Tool

SolutionPackager ist ein Tool, mit dem eine komprimierte Common Data Service (CDS) for Apps-Lösungsdatei reversibel in mehrere XML-Dateien und andere Dateien zerlegt werden kann, so dass diese Dateien durch ein Quellcodeverwaltungssystem leicht verwaltet werden können. Die folgenden Abschnitte zeigen, wie Sie das Tool ausführen und es mit verwalteten und nicht verwalteten Lösungen verwenden.  
  
<a name="bkm_where"></a>   

## <a name="where-to-find-the-solutionpackager-tool"></a>Wo Sie das SolutionPackager-Tool finden  

 Das SolutionPackager-Tool wird als Bestandteil des NuGet-Pakets [Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools) verteilt. Informationen zum Herunterladen des Tools erhalten Sie unter [Tools von NuGet herunterladen](download-tools-nuget.md).
  
<a name="arguments"></a>   

## <a name="solutionpackager-command-line-arguments"></a>SolutionPackager-Befehlszeilenargumente  

 SolutionPackager ist ein Befehlszeilentool, das mit den Parametern aufgerufen werden kann, die in der folgenden Tabelle identifiziert sind.  
  
|Argument|Beschreibung|  
|--------------|-----------------|  
|/action: {Extract&#124;Pack}|Erforderlich. Die auszuführende Aktion. Die Aktion kann das Extrahieren einer Lösungs-ZIP-Datei in einen Ordner oder das Packen eines Ordners in eine ZIP-Datei sein.|  
|/zipfile: \<file path>|Erforderlich. Der Pfad und der Name einer Lösungs-ZIP-Datei. Beim Extrahieren muss die Datei vorhanden sein, und aus ihr wird gelesen. Beim Packen wird die Datei ersetzt.|  
|/folder: \<folder path>|Erforderlich. Der Pfad zu einem Ordner. Beim Extrahieren wird dieser Ordner erstellt und mit Komponentendateien aufgefüllt. Beim Packen muss dieser Ordner bereits vorhanden sein und vorher extrahierte Komponentendateien enthalten.|  
|/packagetype: {Unmanaged&#124;Managed&#124;Both}|(Optional). Der Typ des zu verarbeitenden Pakets. Der Standardwert ist "Nicht verwaltet". Dieses Argument kann in den meisten Fällen weggelassen werden, da der Pakettyp aus der ZIP-Datei oder den Komponentendateien gelesen werden kann. Beim Extrahieren, wenn der Pfad angegeben sind, müssen verwaltete und nicht verwaltete ZIP-Lösungsdateien vorhanden sein und werden in einem einzelnen Ordner verarbeitet. Beim Packen, wenn der Pfad angegeben ist, werden verwaltete und nicht verwaltete ZIP-Dateien aus demselben Ordner hergestellt. Weitere Informationen finden Sie im Abschnitt zur Arbeit mit verwaltete und nicht verwalteten Lösungen weiter unten in diesem Thema.|  
|/allowWrite:{Yes&#124;No}|(Optional). Der Standardwert ist Ja. Dieses Argument wird nur während einer Extraktion verwendet. Wenn /allowWrite:No angegeben ist, führt das Tool alle Vorgänge aus, kann aber keine Dateien schreiben oder löschen. Der Extrahierungsvorgang kann sicher geprüft werden, ohne dass vorhandene Dateien überschrieben oder gelöscht werden.|  
|/allowDelete:{Yes&#124;No&#124;Prompt}|(Optional). Der Standardwert ist Prompt. Dieses Argument wird nur während einer Extraktion verwendet. Wenn /allowDelete:Yes angegeben ist, werden alle Dateien, die im vom /folder-Parameter angegebenen Ordner vorhanden sind und die nicht erwartet werden, automatisch gelöscht. Wenn /allowDelete:No angegeben ist, wird nichts gelöscht. Wenn /allowDelete:Prompt angegeben ist, wird der Benutzer von der Konsole aufgefordert, alle Operationen zuzulassen oder abzulehnen. Wenn /allowWrite:No angegeben ist, finden keine Löschungen statt, auch wenn /allowDelete:Yes ebenfalls angegeben ist.|  
|/clobber|(Optional). Dieses Argument wird nur während einer Extraktion verwendet. Wenn /clobber angegeben ist, werden Dateien, für die das Schreibschutzattribut gesetzt ist, überschrieben oder gelöscht. Wenn dies nicht der Fall ist, geschieht dies nicht.|  
|/errorlevel: {Off&#124;Error&#124;Warning&#124;Info&#124;Verbose}|(Optional). Der Standardwert ist Info. Dieses Argument zeigt die Ebene der auszugebenden Protokollierungsinformationen an.|  
|/map: \<file path>|(Optional). Der Pfad und der Name einer XML-Datei, die Dateizuordnungsdirektiven enthält. Bei Verwendung während einer Extrahierung werden Dateien, die typischerweise aus einem Ordner, der vom /folder-Parameterer angegeben wurde, von anderen Orten aus gelesen, die in der Zuordnungsdatei angegeben sind. Während eines Verpackungsvorgangs werden Dateien, die den Direktiven entsprechen, nicht geschrieben.|  
|/nologo|(Optional). Das Banner zur Laufzeit unterdrücken.|  
|/log: \<file path>|(Optional). Ein Pfad und ein Name einer Protokolldatei. Wenn die Datei bereits vorhanden ist, werden der Datei neue Protokollierungsinformationen angehängt.|  
|@ \<file path>|(Optional). Ein Pfad und ein Name einer Datei, die die Befehlszeilenargumente für das Tool enthält.|  
|/sourceLoc: \<string>|(Optional). Dieses Argument generiert eine Vorlagenressourcendatei und ist nur bei Extrahierungen gültig.<br /><br /> Mögliche Werte lauten `auto` oder ein LCID-/ISOcode für die Sprache, die Sie exportieren möchten. Wenn dieses Argument verwendet wird, werden die Zeichenfolgenressourcen des gegebenen Gebietsschemas als neutrale .resx-Datei extrahiert. Wenn `auto` oder nur die Lang- oder Kurzform des Switches angegeben ist, wird das Basisgebietsschema oder die Lösung verwendet. Sie können die Kurzform des Befehls verwenden: /src.|  
|/localize|Optional Extrahieren Sie alle Zeichenfolgenressourcen in .resx-Dateien, oder führen Sie sie zusammen. Sie können die Kurzform des Befehls verwenden: /loc.|  
  
<a name="use_command"></a>   

## <a name="use-the-map-command-argument"></a>Verwenden des Befehlsarguments /map  

Nachfolgend wird die Verwendung des /map-Arguments für das SolutionPackager-Tool erläutert.  
  
Dateien, die in einem automatischen System erstellt werden, wie etwa .xap Silverlight-Dateien und Plug-in-Assemblys, werden normalerweise nicht in das Quellcodeverwaltungssystem eingecheckt. Webressourcen können sich bereits in der Quellcodeverwaltung an Orten befinden, die nicht direkt kompatibel mit dem SolutionPackager-Tool sind. Durch das Einschließen des /map-Parameters kann das SolutionPackager-Tool angewiesen werden, solche Dateien von anderen Orten zu lesen und zu packen, und nicht aus dem Extrahierungs-Ordner wie sonst. Der /map-Parameter muss den Pfad und den Namen einer XML-Datei angeben, die Zuordnungsdirektiven enthält, die SolutionPackager anweisen, diese Dateien nach dem Namen und Pfad zueinander zuzuordnen und den alternativen Ort für die Suche nach der zugeordneten Datei angeben. Die folgenden Informationen gelten gleichermaßen für alle Direktiven.  
  
- Es können mehrere Direktivenaufgeführt werden, einschließlich solcher, die identische Dateien zuordnen. Früh in der Datei aufgeführte Direktiven haben Vorrang gegenüber den später aufgeführten Direktiven.  
  
- Wenn eine Datei einer Direktove zugeordnet wird, muss sie sich an mindestens einem alternativen Ort befinden. Wenn keine entsprechenden Alternativen gefunden werden, gibt der SolutionPackager einen Fehler aus.  
  
- Ordner- und Dateipfade können absolut oder relativ sein. Relative Pfade werden immer von dem im /folder-Parameter angegebenen Ordner evaluiert.  
  
- Umgebungsvariablen können mit einem %variable%-Syntax angegeben werden.  
  
- Ein „**”-Ordnerplatzhalter kann mit der Bedeutung „in beliebigem Ordner” verwendet werden. Dieser kann nur als letzter Teil eines Pfads verwendet werden, beispielsweise: „c:\folderA\\\*\*”.  
  
- Dateinamenplatzhalter können nur in den Formularen „*.ext” oder „\*.\*” verwendet werden. Kein anderes Muster wird unterstützt.  
  
  Die drei Typen von Direktivenzuordnungen werden hier beschrieben, zusammen mit einem Beispiel für ihre Verwendung.  
  
<a name="Folder_mapping"></a>   

### <a name="folder-mapping"></a>Ordnerzuordnung  

Nachfolgend sind detaillierte Informationen zur Ordnerzuordnung.  
  
**Xml-Format**

`<Folder map="folderA" to="folderB" />`  
  
**Beschreibung**

Dateipfade, die „folderA” entsprechen, werden auf „folderB” geändert.  
  
- Die Hierarchie der Unterordner muss exakt übereinstimmen.  
  
- Ordnerplatzhalter werden nicht unterstützt.  
  
- Es können keine Dateinamen angegeben werden.  
  
  **Beispiele**

  ```xml  
  <Folder map="folderA" to="folderB" />  
  <Folder map="folderA\folderB" to="..\..\folderC\" />  
  <Folder map="WebResources\subFolder" to="%base%\WebResources" />  
  ```  
  
<a name="file_mapping"></a>   

### <a name="file-to-file-mapping"></a>Datei-zu-Datei-Zuordnung  

Nachfolgend sind detaillierte Informationen zur Datei-zu-Datei-Zuordnung.  
  
 **Xml-Format**

`<FileToFile map="path\filename.ext" to="path\filename.ext" />`  
  
**Beschreibung**

Jede beliebige Datei, die dem Parameter `map` entspricht, wird von dem im Parameter `to` angegebenen Namen und Pfad gelesen.  
  
 Für den Parameter `map`:  
  
- Ein Dateiname muss angegeben werden. Der Pfad ist optional. Falls kein Pfad angegeben wird, können Dateien aus allen Ordnern zugeordnet werden.  
  
- Dateinamenplatzhalter werden nicht unterstützt.  
  
- Der Ordnerplatzhalter wird unterstützt.  
  
  Für den Parameter `to`:  
  
- Ein Dateiname und ein Pfad muss angegeben werden.  
  
- Der Dateiname weicht möglicherweise von dem Namen im Parameter `map` ab.  
  
- Dateinamenplatzhalter werden nicht unterstützt.  
  
- Der Ordnerplatzhalter wird unterstützt.  
  
**Beispiele**

```xml  
  <FileToFile map="assembly.dll" to="c:\path\folder\assembly.dll" />  
  <FileToFile map="PluginAssemblies\**\this.dll" to="..\..\Plugins\**\that.dll" />  
  <FileToFile map="Webresrouces\ardvark.jpg" to="%SRCBASE%\CrmPackage\WebResources\JPG format\aardvark.jpg" />  
```  
  
<a name="file_path_mapping"></a>   

### <a name="file-to-path-mapping"></a>Datei-zu-Pfad-Zuordnung  

Nachfolgend sind detaillierte Informationen zur Datei-zu-Pfad-Zuordnung.  
  
**Xml-Format**

`<FileToPath map="path\filename.ext" to="path" />`  
  
**Beschreibung**  
 
Jede beliebige Datei, die dem Parameter `map` entspricht, wird von dem im Parameter `to` angegebenen Pfad gelesen.  
  
Für den Parameter `map`:  
  
- Ein Dateiname muss angegeben werden. Der Pfad ist optional. Falls kein Pfad angegeben wird, können Dateien aus allen Ordnern zugeordnet werden.  
  
- Dateinamenplatzhalter werden unterstützt.  
  
- Der Ordnerplatzhalter wird unterstützt.  
  
Für den Parameter `to`:  
  
- Ein Pfad muss angegeben werden.  
  
- Der Ordnerplatzhalter wird unterstützt.  
  
- Ein Dateiname darf nicht angegeben werden.  
  
  **Beispiele**

```xml  
  <FileToPath map="assembly.dll" to="c:\path\folder" />  
  <FileToPath map="PluginAssemblies\**\this.dll" to="..\..\Plugins\bin\**" />  
  <FileToPath map="*.jpg" to="%SRCBASE%\CrmPackage\WebResources\JPG format\" />  
  <FileToPath map="*.*" to="..\..\%ARCH%\%TYPE%\drop" />  
```  
  
<a name="Example_mapping"></a>   

### <a name="example-mapping"></a>Zuordnungsbeispiel  
Das folgende XML-Codebeispiel zeigt eine vollständige Zuordnungsdatei, die das SolutionPackager-Tool in die Lage versetzt, jede Webressource und die beiden generierten Standardassemblys aus einem Developer Toolkit-Projekt mit dem Namen CRMDevTookitSample zu lesen.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Mapping>  
       <!-- Match specific named files to an alternate folder -->  
       <FileToFile map="CRMDevTookitSamplePlugins.dll" to="..\..\Plugins\bin\**\CRMDevTookitSample.plugins.dll" />  
       <FileToFile map="CRMDevTookitSampleWorkflow.dll" to="..\..\Workflow\bin\**\CRMDevTookitSample.Workflow.dll" />  
       <!-- Match any file in and under WebResources to an alternate set of sub-folders -->  
       <FileToPath map="WebResources\*.*" to="..\..\CrmPackage\WebResources\**" />  
       <FileToPath map="WebResources\**\*.*" to="..\..\CrmPackage\WebResources\**" />  
</Mapping>  
```  
  
<a name="managed"></a>   

## <a name="managed-and-unmanaged-solutions"></a>Verwaltete und nicht verwaltete Lösungen  

 Eine for Apps komprimierte Lösungs (.zip)-Datei kann auf eine von zwei Weisen exportiert werden.  
  
 **Verwaltete Lösung**  
 Eine abgeschlossene Lösung, die bereit ist, in eine Organisation importiert zu werden. Nach dem Importieren können keine Komponenten hinzugefügt oder entfernt werden, aber sie können optional weitere Anpassung erlauben. Dies wird empfohlen, nachdem die Entwicklung der Lösung abgeschlossen ist.  
  
 **Nicht verwaltete Lösung**  
 Eine offene Lösung ohne Einschränkungen dahingehend, was hinzugefügt, entfernt oder geändert werden kann. Dieses wird während der Entwicklung einer Lösung empfohlen.  
  
 Das Format einer komprimierten Lösungsdatei basiert auf dem Typ,verwaltet oder nicht verwaltet. Der SolutionPackager kann komprimierte Lösungsdateien beider Typen verarbeiten. Das Tool kann jedoch nicht einen Typ mzu einem anderen konvertieren. Die einzige Möglichkeit, Lösungsdateien zu einem anderen Typs zu konvertieren, etwa von verwaltete zu nicht verwaltete, besteht im Import der nicht verwalteten Lösungs-ZIP-Datei in einen CDS for Apps-Server und dem anschließenden Export der Lösung als verwaltete Lösung.  
  
 Der SolutionPackager kann verwaltete und nicht verwaltete Lösungs-ZIP-Dateien als kombinierten Satz über den /PackageType:Both-Parameter verarbeiten. Dazu ist es erforderlich, Ihre Lösung zweimal in jedem Typ zu exportieren, wobei die ZIP-Dateien wie folgt benannt werden.  
  
|||  
|-|-|  
|Nicht verwaltete ZIP-Datei: AnyName.zip|Verwaltete ZIP-Datei: AnyName_managed.zip|  
  
 Das Tool nimmt das Vorhandensein der verwalteten ZIP-Datei im gleichen Ordner wie die nicht verwaltete Datei an und extrahiert beide Dateien in einen einzelnen Ordner, wobei die Unterschiede beibehalten werden, wo verwaltete und nicht verwaltete Komponenten vorhanden sind.  
  
 Nachdem eine Lösung als nicht verwaltet und verwaltet extrahiert wurde, ist es möglich, beide aus diesem Ordner zu verpacken (oder beide einzeln), indem der /PackageType-Parameter für die Angabe verwendet wird, welcher Typ erstellt werden soll. Wenn beide angegeben werden, werden zwei ZIP-Dateien mit der gleichen Namenskonvention wie oben erstellt. Wenn der /PackageType-Parameter bei Packen von einem dualen Ordner (verwaltet und nicht verwaltet) fehlt, ist das Standardvorgehen die Erstellung einer einzelnen nicht verwalteten ZIP-Datei.  
  
## <a name="troubleshooting"></a>Problembehandlung  

Wenn Sie Visual Studio 2012 verwenden, um die Ressourcendateien zu bearbeiten, die vom Lösungspacker erstellt werden, wird möglicherweise eine Meldung angezeigt, wenn Sie ähnlich erneut einpacken werden: `“Failed to determine version id of the resource file <filename>.resx the resource file must be exported from the solutionpackager.exe tool in order to be used as part of the pack process.”` Dies tritt auf, weil Visual Studio die Metadatentags der Ressourcendatei mit Datenentags ersetzt.  
  
#### <a name="workaround"></a>Problemumgehung  
  
1. Öffnen Sie die Ressourcendatei in einem Texteditor Ihrer Wahl, und suchen und aktualisieren Sie die folgenden Tags:  
  
   ```xml  
   <data name="Source LCID" xml:space="preserve">  
   <data name="Source file" xml:space="preserve">  
   <data name="Source package type" xml:space="preserve">  
   <data name="SolutionPackager Version" mimetype="application/x-microsoft.net.object.binary.base64">  
  
   ```  
  
2. Ändern Sie den Knotennamen von `<data>` zu `<metadata>`.  
  
    Zum Beispiel: Die Zeichenfolge:  
  
   ```xml  
   <data name="Source LCID" xml:space="preserve">  
     <value>1033</value>  
   </data>  
  
   ```  
  
    wird geändert zu:  
  
   ```xml  
   <metadata name="Source LCID" xml:space="preserve">  
     <value>1033</value>  
   </metadata>  
  
   ```  
  
   Dies ermöglicht dem Lösungspacker, die Ressourcendatei zu lesen und zu importieren. Dieses Problem wurde nur beobachtet, wenn der Visual Studio-Ressourceneditor verwendet wurde.  
  
### <a name="see-also"></a>Siehe auch  
 [Verwendung der Quellverwaltung mit Lösungsdateien](use-source-control-solution-files.md)<br/>   
 [Dateireferenz von Lösungskomponenten](solution-component-file-reference-solutionpackager.md)<br/>   
 [Einführung in die Lösungen](introduction-solutions.md)
