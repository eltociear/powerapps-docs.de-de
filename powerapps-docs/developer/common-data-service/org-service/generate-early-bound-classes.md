---
title: Generieren von Klassen mit früher Bindung für den Organisationsservice (Common Data Service) | Microsoft Docs
description: CrmSvcUtil.exe ist ein Befehlszeilen-Codegenerierungstool für die Verwendung mit Common Data Service. Dieses Tool erstellt .NET-Framework-Klassen mit früher Bindung, die das Entitätsdatenmodell darstellen, das von Common Data Service verwendet wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6e8b739c7c3b5583b5e0cfe56f2211fbf70811de
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156050"
---
# <a name="generate-early-bound-classes-for-the-organization-service"></a>Generieren von Klassen mit früher Bindung für den Organisationsdienst

**CrmSvcUtil.exe** ist ein Befehlszeilen-Codegenerierungstool für die Verwendung mit Common Data Service. Dieses Tool erstellt .NET-Framework-Klassen mit früher Bindung, die das Entitätsdatenmodell darstellen, das von Common Data Service verwendet wird. Das Codegenerierungstool (CrmSvcUtil.exe) wird als Bestandteil des [Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools)-NuGet-Pakets verteilt. 

> [!NOTE]
> Informationen zum Herunterladen vom Codegenerierungstool (CrmSvcUtil.exe) finden Sie unter [Herunterladen von Tools von NuGet](../download-tools-NuGet.md).

## <a name="generate-entity-classes"></a>Generieren Sie Entitätsklassen

Das **CrmSvcUtil.exe**-Tool erstellt eine Microsoft Visual C# oder Visual Basic.NET-Ausgabedatei, die stark typisierte Klassen für Entitäten in Ihrer Organisation enthält. Dies umfasst benutzerdefinierte Entitäten und Attribute. Diese Ausgabedatei enthält eine Klasse für jede Entität, und stellt frühe Bindung und IntelliSense-Unterstützung in Visual Studio bereit, die Ihnen hilft, wenn Sie benutzerdefinierten Code schreiben. Die erstellten Klassen sind partielle Klassen, die mit benutzerdefinierter Geschäftslogik in den separaten Dateien erweitert werden können. Sie können auch Erweiterungen für dieses Tool erstellen. Weitere Informationen finden Sie unter [Erweiterungen für das Codegenerierungstool erstellen](extend-code-generation-tool.md).  

## <a name="generate-an-organizationservicecontext-class"></a>Erstellt eine OrganizationServiceContext-Klasse

Das Tool kann auch verwendet werden, um eine Klasse zu generieren, die von der <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>-Klasse abgeleitet ist, die als in Entitätscontainer im Entity Data Model auftritt. Der Servicekontext bietet die Einrichtungen für die Nachverfolgung von Änderungen und das Verwalten von Identitäten, Parallelität und Beziehungen. Diese Klasse stellt auch eine <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges>-Methode zur Verfügung, die in Common Data Service Datensätze schreibt, einfügt, aktualisiert und löscht. Weitere Informationen finden Sie unter [Die Organisationsdienst-Kontextklasse verwenden](organizationservicecontext.md).  

## <a name="use-generated-classes"></a>Verwenden von erstellten Klassen

Die Klassen, die vom Codegenerierungstool erstellt werden, sind konzipiert, um in eine Klassenbibliothek eigebaut zu werden, auf die in Projekten verwiesen wird, die Common Data Service verwenden. Nachdem Sie die Klassendatei mithilfe des Tools erstellt haben, sollten Sie die Datei dem Visual Studio-Projekt hinzufügen. Sie müssen auch einigen Assemblys Verweise hinzufügen, von denen die generierten Klassen abhängig sind.  

Die folgenden Liste führt Aassemblys auf, auf die in Ihrem Projekt verwiesen werden muss, wenn Sie die generierte Codedatei verwenden.  

- `Microsoft.Crm.Sdk.Proxy.dll`  
- `Microsoft.Xrm.Sdk.dll` 

Diese Assemblys sind im [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)-NuGet-Paket enthalten. Verwenden Sie diese NuGet-Pakete, um diese Assemblys Ihrem Visual Studio-Projekt hinzuzufügen.

<a name="bkmk_RuntheCodeGenerationUtility"></a>

## <a name="run-the-code-generation-tool"></a>Ausführen des Codegenerierungstools

Das Codegenerierungstool nimmt einige Parameter, die die Inhalte der Datei bestimmen, die erstellt wird. Die Parameter in können über die Befehlszeile übergeben werden, wenn Sie das Tool ausführen, oder in einer mit .NET verbundenen Anwendungskonfigurationsdatei. 

Führen Sie das `CrmSvcUtil.exe`-Tool im `Tools\CoreTools`-Ordner aus, der erstellt wurde, als Sie die Tools mithilfe des Skripts, das in [Tools von NuGet herunterladen](../download-tools-NuGet.md)beschrieben wird, heruntergeladen haben. Wenn Sie das Tool in einem anderen Ordnerspeicherort ausführen, stellen Sie sicher, dass eine Kopie der `Microsoft.Xrm.Sdk.dll`-Assemblys sich in dem gleichen Ordner befindet.  

Im folgenden Beispiel wird das Format für die Ausführung von Tools in der Befehlszeile mit Common Data Service gezeigt. Um die interaktiven Anmeldung zu verwenden, können Sie diese einfach Optionen zur Verfügung stellen:

```ms-dos
CrmSvcUtil.exe /interactivelogin ^
/out:<outputFilename>.cs ^
/namespace:<outputNamespace> ^
/serviceContextName:<serviceContextName> ^
/generateActions
```

Wenn Sie das Tool mit der `interactivelogin` (Verknüpfungs `il`) Option verwenden, öffnen Sie einen Dialogs und können Ihre Anmeldeinformationen angeben und den Server mit dem Sie sich verbinden möchten.

Sie können auch die Parameter angeben, die Sie direkt in der Befehlszeile ausführen möchten, oder in einer Datei vom Batchs (BAT) ausführen können, um neue Klassen zu generieren.

```ms-dos
CrmSvcUtil.exe ^
/url:https://<organizationUrlName>.api.crm.dynamics.com/XRMServices/2011/Organization.svc ^
/out:<outputFilename>.cs ^
/username:<username> ^
/password:<password> ^
/namespace:<outputNamespace> ^
/serviceContextName:<serviceContextName>
```
Beispiel:

```ms-dos
CrmSvcUtil.exe ^
/url:https://myorganization.api.crm.dynamics.com/XRMServices/2011/Organization.svc ^
/out:MyOrganizationSdkTypes.cs ^
/username:you@yourOrg.onmicrosoft.com ^
/password:myp455w0rd ^
/namespace:MyOrg ^
/serviceContextName:MyContext
```


> [!NOTE]
> Die oben aufgeführten Beispiele nutzen dasTabstoppzeichen des Karat (`^`), um die Liste von Parametern für Lesbarkeit oben zu unterbrechen. Sie können die Befehlsparameter mit Argumenten mithilfe des Notizblockes verfassen und ihn in der Befehlszeile einfügen.

- Bei den `username`- und `password`-Parametern geben Sie den Benutzernamen bzw. das Kennwort ein, das verwendet wird, um sich für Common Data Service anzumelden. 
- Für die `url` Parameter können Sie die korrekte URL der Webanwendung finden, indem Sie **Einstellungen** auswählen, zu **Anpassungen** navigieren, und dann **Entwickleressourcen** schließen. Die URL wird unter **Organisationsservice** angezeigt.  

Verwenden Sie den folgenden Befehl, um die unterstützten Befehlszeilenparameter anzuzeigen.

```ms-dos
CrmSvcUtil.exe /?  
```

<a name="bkmk_parameters"></a>

## <a name="parameters"></a>Parameter

Die folgende Tabelle enthält die Codegenerierungstoolparameter und gibt eine kurze Beschreibung ihrer Verwendung.  
  
|Parameter|Verknüpfung|Beschreibung|Erforderlich|
|--|--|--|--|
|`deviceid`|`di`|Nicht mehr interessiert|False|
|`devicepassword`|`dp`|Nicht mehr interessiert|False|
|`domain`|`d`|Die Domäne, anhand derer authentifiziert wird, wenn Sie eine Verbindung lokal herstellen.|False|
|`url`||Die URL für den Organisationsservice.|True, es sei denn, Sie verwenden `interactivelogin`|
|`out`|`o`|Der Dateinamen für den erstellten Code.|True|
|`language`|`l`|Die Sprache, in dem der Code zu generieren ist. Das kann entweder „CS” oder „VB” sein. Der Standardwert ist „CS”.|False|
|`namespace`|`n`|Der Namespace für den erstellten Code. Standard ist der globale Namespace.|False|  
|`username`|`u`|Der Benutzername, der verwendet wird, wenn Sie eine Verbindung mit dem Server für die Authentifizierung herstellen.|False|  
|`password`|`p`|Das Kennwort, das verwendet wird, wenn Sie eine Verbindung mit dem Server für die Authentifizierung herstellen.|False|  
|`servicecontextname`||Der Name der Kontextklasse des generierten Organisationsservice. Wenn kein Wert angegeben ist, wird kein Servicekontext erstellt.|False|
|`help`|`?`|Verwendungsinformationen anzeigen.|False|
|`nologo`||Das Banner zur Laufzeit unterdrücken.|False|
|`generateActions`||Generieren Sie Anforderungs- und Antwortklassen für benutzerdefinierte Aktionen.|False|
|`interactivelogin`|`il`|Wenn es verwendet wird, wird ein Dialog zur Anmeldung im Common Data Service-Service angezeigt. Alle anderen Parameter, die mit der Verbindung zusammen hängen, die auf der Befehlszeile angegeben wurden, werden ignoriert.|False|  
|`connectionstring`|`connstr`|Enthält Informationen, als einzelne Zeichenfolge bereitgestellt, zur Verbindung mit einer Common Data Service-Organisation. Alle anderen Parameter, die mit der Verbindung zusammen hängen, die auf der Befehlszeile angegeben wurden, werden ignoriert. Weitere Informationen finden Sie unter [Verbindungszeichenfolgen in XRM-Tooling verwenden, um eine Verbindung mit Common Data Service herzustellen](../xrm-tooling/use-connection-strings-xrm-tooling-connect.md).|False|


<a name="bkmk_sampleconfig"></a>

## <a name="use-the-configuration-file"></a>Verwenden der Konfigurationsdatei

Die CrmSvcUtil.exe.config-Konfigurationsdatei muss im gleichen Ordner wie das CrmSvcUtil.exe-Tool sein. Die Konfigurationsdatei verwendet die Standardschlüssel-Wert-Paare im Abschnitt `appSettings`. Wenn Sie einen Wert über die Befehlszeile eingeben, wird dieser Wert anstelle des Werts in der Konfigurationsdatei verwendet. Alle Schlüssel-Wert-Paare, die in der Anwendungskonfigurationsdatei gefunden werden, die nicht einem der erwarteten Parameter entsprechen, werden ignoriert.  

Schließen Sie die Parameter `url` und `namespace` nicht in die XML-Konfigurationsdatei ein. Diese müssen über die Befehlszeile eingegeben werden, wenn das CrmSvcUtil.exe-Tool ausgeführt wird.  

Das folgende Beispiel zeigt, wie die Ausgabedatei und die Domänennamenparameter in der Anwendungskonfigurationsdatei mithilfe von Tastenkombinationen konfiguriert werden.  

```xml
<appSettings>    
    <add key="o" value="CrmProxy.cs"/>    
    <add key="d" value="mydomain"/>
</appSettings>  
```

<a name="bkmk_enabletrace"></a>

## <a name="enable-tracing"></a>Aktivieren der Ablaufverfolgung
 Um die Ablaufverfolgung zu aktivieren, wenn Sie das Tool ausführen, fügen Sie die folgenden Zeilen der XML-Konfigurationsdatei hinzu:  

```xml
<system.diagnostics>   
   <trace autoflush="false" indentsize="4">   
      <listeners>   
         <add name="configConsoleListener" type="System.Diagnostics.ConsoleTraceListener">   
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />   
         </add>   
      </listeners>   
   </trace>   
</system.diagnostics>  
```

Weitere Informationen zur Verwendung der Nachverfolgungsoptionen finden Sie unter [Konfigurieren der Nachverfolgung für XRM Tooling](../xrm-tooling/configure-tracing-xrm-tooling.md).  

## <a name="community-tools"></a>Community-Tools

**Früh gebundener Generator** ist eine Xrm Tolbox-Community. Weitere Informationen finden Sie im Thema [Entwicklertools und Ressourcen](../developer-tools.md) für von der Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von Microsoft und es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com). 


### <a name="see-also"></a>Siehe auch

[Entwicklertools und -ressourcen](../developer-tools.md)<br />
[Erstellen von Erweiterungen für das Codegenerierungstool](extend-code-generation-tool.md)<br />
[Herunterladen von Tools von NuGet](../download-tools-NuGet.md)