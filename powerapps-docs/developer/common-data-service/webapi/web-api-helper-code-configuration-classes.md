---
title: 'Web-API-Hilfsprogrammcode: Konfigurationsklassen (Common Data Service für Apps) | Microsoft Docs'
description: 'Die Konfigurationsklassenhierarchie kann verwendet werden, um die erforderlichen Verbindungsdaten für den Zugriff auf "Common Data Service für Apps"-Webdienste aus Ihrer Anwendung anzugeben.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 3b86c11a-15e1-40a1-aca0-34a9bab2f04a
caps.latest.revision: 14
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-helper-code-configuration-classes"></a>Web API-Hilfecode: Konfigurationsklassen

Verwenden Sie die Konfigurationsklassenhierarchie, um die erforderlichen Verbindungsdaten für den Zugriff auf "Common Data Service für Apps"-Webdienste aus Ihrer Anwendung anzugeben. Sie können diese Verbindungsdaten eingeben, indem Sie Werte mithilfe der `Configuration`-Basisklasse direkt in Ihrem Code einrichten, z. B. über die Benutzereingabe. Normalerweise geben Sie diese Informationen in den Einstellungen, die in der Anwendungskonfigurationsdatei gespeichert sind, mithilfe der abgeleiteten Klasse `FileConfiguration`an.  
  
Der Quellcode der Konfigurationsklassenhierarchie befindet sich in der Datei "Configuration.cs" in der [CRM SDK-Web-API Hilfe-Bibliothek](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode/). Die Konfigurationsklassenhierarchie wurde entworfen, um in Verbindung mit der `Authentication`-Klasse verwendet zu werden, um die Einrichtung einer sicheren Verbindung mit Ihrem "Common Data Service für Apps"-Service zu gewährleisten. Weitere Informationen finden Sie unter [Verwenden der "Common Data Service für Apps"-Web-API-Hilfsprogrammbibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
<a name="bkmk_Connectiondata"></a>

## <a name="connection-data"></a>Verbindungsdaten

Die `Configuration`-Klasse liest und analysiert die Anwendungskonfigurationsdatei, um die folgenden Verbindungsdaten zu erhalten.  
  
|Verbindungsdaten|Bereitstellungen|Beschreibung|  
|---------------------|-----------------|-----------------|  
|Dienst-URL|Alle|Die Basis-URL zum Common Data Service für Apps-Service|  
|Benutzername|Alle|Der in CDS für Apps registrierte Benutzername|  
|Kennwort|Alle|Das Kennwort für den Benutzer|  
|Domäne|Alle|Die Domäne des Common Data Service für Apps-Service zur Active Directory-Authentifizierung|  
|Client-ID|Nur Online und IFD|Die Client-ID der Anwendung, wie sie bei Azure AD für "Common Data Service für Apps" registriert wurde|  
|Umleitungs-URL|Nur Online und IFD|Eine Callback-URI für die aktuelle Anwendung.|  
  
<!-- TODO:
For more information on obtaining a client ID and a redirection URL for an application, see [Walkthrough: Register a Common Data Service for Apps app with Azure Active Directory](../walkthrough-register-app-azure-active-directory.md).  
   -->
<a name="bkmk_FileConfigconnectionsettings"></a>

### <a name="fileconfiguration-connection-settings"></a>FileConfiguration-Verbindungseinstellungen

Die meisten "Common Data Service für Apps"-Web-API-Beispiele nutzen die abgeleitete Klasse, `FileConfiguration`, um die Verbindungsdaten aus der Anwendungskonfigurationsdatei "App.config" zu extrahieren. Diese Datei enthält mehrere Anwendungseinstellungen, die für die unterschiedlichen „Common Data Service für Apps”-Serverbereitstellungsmodi gelten. Die `connectionString`-Einstellung enthält die Service-URL und den Benutzernamen. Zusätzlich sind die `ClientId`- und `RedirectUrl`-Einstellungen für Onlinebereitstellungen oder Bereitstellungen mit Internetzugriff (Internet-Facing Deployments, IFDs) erforderlich. Die folgenden Zeilen, stammen aus der standardmäßigen App.config-Datei, die für die meisten Web-API-Beispiele bereitgestellt wird und diese Verbindungsdaten als Platzhalterwerte enthält. Sie müssen diese Platzhalter durch die Werte ersetzen, die spezifisch für den aktuellen Benutzer, Ihren "Common Data Service für Apps"-Server und Ihre Client-Anwendung gelten.  
  
```xml  
<connectionStrings> 
    <add name="default" connectionString="Url=http://myserver/myorg/; Username=name; Password=password; Domain=domain" /> 
</connectionStrings> 
<appSettings> 
    <add key="ClientId" value="e5cf0024-a66a-4f16-85ce-99ba97a24bb2" /> 
    <add key="RedirectUrl" value="http://localhost/SdkSample" /> 
</appSettings>  
```  
  
Die vollständigen Inhalte der Standardkonfigurationsdatei sind unter [Standardkonfigurationsdatei-Auflistung](#bkmk_Defaultconfigurationfilelisting) zu finden.  
  
<a name="bkmk_Classhierarchyandmembers"></a>
 
## <a name="class-hierarchy-and-members"></a>Klassenhierarchie und -mitglieder

Das folgende Diagramm gibt Aufschluss über öffentliche Mitglieder der Konfigurationsklassenhierarchie.  
  
 <!-- TODO:
![Common Data Service for Apps Web API Helper Library&#45;Configuration Class Diagram](../media/web-api-helper-library-configuration-class-diagram.png "Common Data Service for Apps Web API Helper Library-Configuration Class Diagram")   -->
  
 **Konfigurationsklasse**  
  
 *Eigenschaften:*  
  
 Alle Eigenschaften sind direkt zu den entsprechenden Verbindungsdaten im vorherigen Abschnitt zugeordnet.  
  
 *Methoden*  
  
 Der Standardkonstruktor initialisiert keine Eigenschaften (Null).  
  
 **FileConfiguration-Klasse**  
  
 *Eigenschaften:*  
  
 `Name` ist der Name des Verbindungszeichenfolgen-Einstellungseintrags.  
  
 `PathToConfig` ist der vollständige oder relative Pfad zur Anwendungskonfigurationsdatei.  
  
 *Methoden*  
  
 Der Standardkonstruktor initialisiert keine Eigenschaften (Null).  
  
 Der Nicht-Standardkonstruktor nimmt einen einzelnen Zeichenfolgenparameter entgegen, der die benannten Verbindungszeichenfolge angibt. Eine leere Zeichenfolge oder ein Null-Zeichenfolgewert führt dazu, dass der erste Verbindungszeichenfolgeneintrag verwendet wird.  
  
 Die `Load`-Methode öffnet, liest und analysiert die angegebene Konfigurationsdatei. Sie wird vom Nicht-Standardkonstruktor verwendet.  
  
<a name="bkmk_usage"></a>

## <a name="usage"></a>Verwendung

 Die `FileConfiguration`- und `Authentication`-Klassen sind so konzipiert, dass sie gemeinsam verwendet werden, um die Informationen in App.config zu lesen und dann eine sichere Verbindung zum Ziel-"Common Data Service für Apps"-Dienst einzurichten. Kann mit folgenden Anweisungen implementiert werden.  
  
```csharp  
FileConfiguration config = new FileConfiguration(null); Authentication auth = new Authentication(config); httpClient = new HttpClient(auth.ClientHandler, true);  
```  
  
 Der Nicht-Standardkonstruktor in der `Configuration`-Klasse ermöglicht die Verwendung einer benannten Verbindungszeichenfolge, beispielsweise:  
  
```csharp  
Configuration config = new FileConfiguration(“TestServer”);  
```  
  
 Wenn eine Null- oder leere Verbindungszeichenfolgen an den `FileConfiguration`-Klassenkonstruktor übergeben wird, wird die erste Verbindungszeichenfolge der Konfigurationsdatei verwendet.  
  
 Außerdem unterstützen die SDK-Beispiele einen Run-Time-Befehlsparameter, der den Namen der gewünschten Verbindungszeichenfolge für die Übergabe an den Konstruktor darstellt. Diese Option wird über den folgenden Code implementiert:  
  
```csharp  
if (cmdargs.Length > 0) { config = new FileConfiguration(cmdargs[0]); } else { config = new FileConfiguration(null); }  
```  
  
<a name="bkmk_Configurationsearchorder"></a>

### <a name="configuration-search-order"></a>Konfigurationssuchreihenfolge

 Egal, ob die Standard. oder eine benutzerdefinierte Anwendungskonfigurationsdatei verwendet wird, die optionale `AlternateConfig`-Anwendungseinstellung kann in der Datei angegeben werden, um eine anderen Konfigurationsdatei anzugeben. Wenn diese Datei vorhanden ist, werden ihre Verbindungseinstellungen verwendet.  
  
```xml  
<add key="AlternateConfig" value="C:\Temp\crmsample.exe.config"/>  
```  
  
 Eine häufige Verwendung dieser Einstellung ist, eine globale Konfigurationsdatei bereitzustellen, die von mehreren Anwendungen genutzt wird, statt die einzelnen App.config-Dateien zu bearbeiten. Dies ist besonders für die gemeinsame Nutzung der Konfigurations- und Registrierungsinformationen von mehreren Anwendungen bei der Entwicklung und dem Testen hilfreich. Nur für die Produktionsversion werden dann eindeutige Konfigurations- und treten Registrierungsinformationen für jede Anwendung bereitgestellt.  
  
<a name="bkmk_Defaultconfigurationfilelisting"></a>

## <a name="default-configuration-file-listing"></a>Standardkonfigurationsdatei

 Die Datei App.config, die mit den meisten "Common Data Service für Apps"-Web-API-Beispielen bereitgestellt wird, enthält Platzhalter-Verbindungswerte, die vom Entwickler oder Standortsadministrator bearbeitet werden müssen.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5.2" />
   </startup>
   <connectionStrings>
      <clear />
      <!-- When providing a password, make  
                sure to set the app.config file's security so that only you can read it. -->
      <add name="default" connectionString="Url=http://myserver/myorg/; Username=name; Password=password; Domain=domain" />
      <add name="CrmOnline" connectionString="Url=https://mydomain.crm.dynamics.com/;                   Username=someone@mydomain.onmicrosoft.com; Password=password" />
   </connectionStrings>
   <appSettings>
      <!--For information on how to register an app and obtain the ClientId and RedirectUrl values see https://msdn.microsoft.com/dynamics/crm/mt149065  
                -->
      <!--Active Directory application registration. -->
      <!--These are dummy values and should be replaced with your actual app registration values.-->
      <add key="ClientId" value="e5cf0024-a66a-4f16-85ce-99ba97a24bb2" />
      <add key="RedirectUrl" value="http://localhost/SdkSample" />
      <!-- Use an alternate configuration file for connection string and setting values. This optional setting enables use of an app.config file shared among multiple applications. If the specified file does not exist,  
                this setting is ignored.-->
      <add key="AlternateConfig" value="C:\Temp\crmsample.exe.config" />
   </appSettings>
</configuration>  
```  
  
## <a name="class-listing"></a>Klassenlisten

 Den aktuellen Code für diese Klasse finden Sie im [CRM SDK-Web-API-Hilfebibliothek](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode) NuGet-Paket.  
  
```csharp  
using System;
using System.IO;
using System.Security;
using System.Configuration;

namespace Microsoft.Crm.Sdk.Samples.HelperCode
{
    /// <summary>
    /// An application configuration containing user logon, application, and web service information
    /// as required for CRM Web API authentication.
    /// </summary>
    public class Configuration
    {
        #region Properties
        /// <summary>
        /// The root address of the Dynamics CRM service.
        /// </summary>
        /// <example>https://myorg.crm.dynamics.com</example>
        public string ServiceUrl { get; set; }

        /// <summary>
        /// The redirect address provided when the application was registered in Microsoft Azure
        /// Active Directory or AD FS.
        /// </summary>
        /// <remarks>Required only with a web service configured for OAuth authentication.</remarks>
        /// <seealso cref="https://msdn.microsoft.com/library/dn531010.aspx#bkmk_redirect"/>
        public string RedirectUrl { get; set; }

        /// <summary>
        /// The client ID that was generated when the application was registered in Microsoft Azure
        /// Active Directory or AD FS.
        /// </summary>
        /// <remarks>Required only with a web service configured for OAuth authentication.</remarks>
        public string ClientId { get; set; }

        /// <summary>
        /// The user name of the logged on user or null.
        /// </summary>
        public string Username { get; set; }

        /// <summary>
        ///  The password of the logged on user or null.
        /// </summary>
        public SecureString Password { get; set; }

        /// <summary>
        ///  The domain of the logged on user account or null.
        /// </summary>
        /// <remarks>Required only with a web service configured for Active Directory authentication.</remarks>
        public string Domain { get; set; }

        #endregion Properties

        #region Constructors

        /// <summary>
        /// Constructs a configuration object.
        /// </summary>
        public Configuration() { }

        #endregion Constructors
    }

    /// <summary>
    /// A configuration that is persisted to file storage.
    /// </summary>
    /// <remarks>This implementation defaults to using an app.config file. However, you
    /// can derive a subclass and override the virtual methods to make use of other
    /// file formats.
    /// 
    /// One set of application registration settings and multiple named connection strings are supported.</remarks>
    public class FileConfiguration : Configuration
    {
        #region Properties
        /// <summary>
        /// The full or relative path to the application's configuration file.
        /// </summary>
        /// <remarks>The file name is in the format <appname>.exe.config.</appname></remarks>
        public string PathToConfig { get; set; }

        /// <summary>
        /// The name of the connection.
        /// </summary>
        public string Name { get; set; }

        #endregion Properties

        #region Constructors
        /// <summary>
        /// Constructs a file configuration.
        /// </summary>
        public FileConfiguration()
            : base()
        { }

        /// <summary>
        /// Loads a named connection string and application settings from persistent file storage.
        /// The configuration file must have the same name as the application and be located in the 
        /// run-time folder.
        /// </summary>
        /// <param name="name">The name of the target connection string. An empty or null string value 
        /// results in the first named configuration being used.</param>
        /// <remarks>The app.config file must exist in the run-time folder and have the name
        /// <appname>.exe.config. To specify an app.config file path, use the Load() method.</remarks>
        public FileConfiguration(string name)
            : base()
        {
            var path = System.IO.Path.Combine(Directory.GetCurrentDirectory(), Environment.GetCommandLineArgs()[0]);

            Load(name, String.Concat(path, ".config"));
        }

        #endregion Constructors

        #region Methods
        /// <summary>
        /// Loads server connection information and application settings from persistent file storage.
        /// </summary>
        /// <remarks>A setting named OverrideConfig can optionally be added. If a config file that this setting
        /// refers to exists, that config file is read instead of the config file specified in the path parameter.
        /// This allows for an alternate config file, for example a global config file shared by multiple applications.
        /// </summary>
        /// <param name="connectionName">The name of the connection string in the configuration file to use. 
        /// Each CRM organization can have its own connection string. A value of null or String.Empty results
        /// in the first (top most) connection string being used.</param>
        /// <param name="path">The full or relative pathname of the configuration file.</param>
        public virtual void Load(string connectionName, string path)
        {
            // Check passed parameters.
            if (string.IsNullOrEmpty(path) || !System.IO.File.Exists(path))
                throw new ArgumentException("The specified app.config file path is invalid.", this.ToString());
            else
                PathToConfig = path;

            try
            {
                // Read the app.config file and obtain the app settings.
                System.Configuration.Configuration config = null;
                ExeConfigurationFileMap configFileMap = new ExeConfigurationFileMap();
                configFileMap.ExeConfigFilename = PathToConfig;
                config = ConfigurationManager.OpenMappedExeConfiguration(configFileMap, ConfigurationUserLevel.None);

                var appSettings = config.AppSettings.Settings;

                // If an alternate config file exists, load that configuration instead. Note the test
                // for redirectTo.Equals(path) to avoid an infinite loop.
                if (appSettings["AlternateConfig"] != null)
                {
                    var redirectTo = appSettings["AlternateConfig"].Value;
                    if (redirectTo != null && !redirectTo.Equals(path) && System.IO.File.Exists(redirectTo))
                    {
                        Load(connectionName, redirectTo);
                        return;
                    }
                }

                // Get the connection string.
                ConnectionStringSettings connection;
                if (string.IsNullOrEmpty(connectionName))
                {
                    // No connection string name specified, so use the first one in the file.
                    connection = config.ConnectionStrings.ConnectionStrings[0];
                    Name = connection.Name;
                }
                else
                {
                    connection = config.ConnectionStrings.ConnectionStrings[connectionName];
                    Name = connectionName;
                }

                // Get the connection string parameter values.
                if (connection != null)
                {
                    var parameters = connection.ConnectionString.Split(';');
                    foreach (string parameter in parameters)
                    {
                        var trimmedParameter = parameter.Trim();
                        if (trimmedParameter.StartsWith("Url="))
                            ServiceUrl = parameter.Replace("Url=", String.Empty).TrimStart(' ');

                        if (trimmedParameter.StartsWith("Username="))
                            Username = parameters[1].Replace("Username=", String.Empty).TrimStart(' ');

                        if (trimmedParameter.StartsWith("Password="))
                        {
                            var password = parameters[2].Replace("Password=", String.Empty).TrimStart(' ');

                            Password = new SecureString();
                            foreach (char c in password) Password.AppendChar(c);
                        }
                        if (trimmedParameter.StartsWith("Domain="))
                            Domain = parameter.Replace("Domain=", String.Empty).TrimStart(' ');
                    }
                }
                else
                    throw new Exception("The specified connection string could not be found.");

                // Get the Azure Active Directory application registration settings.
                RedirectUrl = appSettings["RedirectUrl"]?.Value;
                ClientId = appSettings["ClientId"]?.Value;
            }
            catch (InvalidOperationException e)
            {
                throw new Exception("Required setting in app.config does not exist or is of the wrong type.", e);
            }
        }

        /// <summary>
        /// Save the current configuration to persistent file storage.
        /// </summary>
        /// <remarks>Any existing configuration is overwritten.</remarks>
        public virtual void Save()
        {
            throw new NotImplementedException();
        }

        /// <summary>
        /// Add a named connection string to persistent file storage.
        /// </summary>
        /// <remarks>A named connection string from the current configuration is added to an existing
        /// configuration file./remarks>
        public virtual void AddConnection()
        {
            throw new NotImplementedException();
        }

        #endregion Methods
    }
} 
```  
  
### <a name="see-also"></a>Siehe auch

[Erste Schritte mit dem Web API (C#)](get-started-dynamics-365-web-api-csharp.md)<br />
[Starten eines Web-API-Projekts in Visual Studio (C#)](start-web-api-project-visual-studio-csharp.md)<br />
[Verwenden der Common Data Service für Apps-Web-API-Hilfe-Bibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md)<br />
[Hilfecode: Authentifizierungsklasse](web-api-helper-code-authentication-class.md)<br />
[Hilfecode: CrmHttpResponseException-Klasse](web-api-helper-code-crmhttpresponseexception-class.md)<br />
[SDK-Beispielhilfecode für Organisationsdienstendpunkt](https://www.nuget.org/packages/Microsoft.CrmSdk.Samples.HelperCode-CS)  