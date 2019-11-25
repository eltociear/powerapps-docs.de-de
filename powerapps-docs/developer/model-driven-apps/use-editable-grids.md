---
title: Verwenden bearbeitbarer Raster in modellgestützten Apps | Microsoft Docs
description: Bearbeitbare Raster ist ein benutzerdefiniertes Steuerelement, das umfangreiche Inline-Bearbeitungsfunktionen auf Internet- und mobilen Clienten (Dynamics 365 for phones und Dynamics 365 for tablets) einschließlich der Möglichkeit, Daten innerhalb der gleichen Rasters zu gruppieren, zu sortieren und zu filtern, um nicht zwischen Datensätzen oder Ansichten zu wechseln.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0798cdda5cac68396c1f0502d80096f69ee29838
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748791"
---
# <a name="use-editable-grids"></a>Bearbeitbare Raster verwenden

Bearbeitbare Raster ist ein benutzerdefiniertes Steuerelement, das umfangreiche Inline-Bearbeitungsfunktionen auf Internet- und mobilen Clienten (Dynamics 365 for phones und Dynamics 365 for tablets) einschließlich der Möglichkeit, Daten innerhalb der gleichen Rasters zu gruppieren, zu sortieren und zu filtern, um nicht zwischen Datensätzen oder Ansichten zu wechseln. Das bearbeitbare Unterrastersteuerelement wird im Hauptraster, in den Formularrastern und im Unterraster im Webclient und in Dashboards und im Formularraster auf dem mobilen Clients unterstützt. Obwohl das bearbeitbare Unterrastersteuerelement Bearbeitungsfunktion enthält, sind die schreibgeschützten Rastermetadaten und die Sicherheitsebenen-Einstellungen zentral. Bearbeitbare Raster unterstützen Unternehmensregeln und Formularskripts, damit Sie benutzerdefinierte Geschäftslogik für die Anforderungen Ihrer Organisation anwenden können.  

> [!NOTE] 
> Wenn Sie Vorgängerformulare verwenden (Versionen vor Dynamics CRM 2016) und ein bearbeitbares Raster für ein Unterraster aktivieren, wird das bearbeitbare Unterraster nicht gerendert. Systemadministratoren können Vorgängerformulare in den Systemeinstellungen nach Bedarf deaktivieren. 

<a name="Enable"></a>   
## <a name="enable-editable-grids"></a>Bearbeitbare Raster aktivieren  
 Sie können bearbeitbare Entitätsebenenraster auf der Entitätsebene aktivieren, um den Hauptraster zu verwenden oder auf Formularebene schreibgeschützte Raster und Unterraster (zugeordnete Raster) über einen bearbeitbaren Raster auf dem Menüband zu ersetzen.  
  
 Sie können das Steuerelement für bearbeitbare Raster für eine Entität aktivieren, indem Sie das Anpassungstool in modellgestützten Apps verwenden (**Einstellungen** > **Anpassungen**  > **System anpassen** > **Entitäten** > *[Entity_Name]* > Registerkarte **Steuerelemente**).  
  
 Um den bearbeitbaren Raster für einen Raster zu aktivieren, öffnen Sie den Formular-Editor, doppelklicken auf den schreibgeschützten Raster, den Sie mit dem bearbeitbaren Raster ersetzen möchten und fügen Sie den bearbeitbaren Raster in der Registerkarte **Steuerelemente** hinzu oder aktivieren Sie ihn.  
  
 Sie können den nicht-bearbeitbaren Raster und die verknüpften Raster jederzeit auf dem Hauptraster wiederherstellen, falls erforderlich. Zur Ausführungszeit können Benutzer auch zwischen schreibgeschützten Rastern und bearbeitbaren Rastern umschalten.  
  
 Weitere Informationen: [Modellgetriebene App-Raster (Listen) editierbar machen mit Benutzerdefiniertes Steuerelement für bearbeitbares Raster](../../maker/model-driven-apps/make-grids-lists-editable-custom-control.md)  
  
<a name="FormScripting"></a>   
## <a name="form-scripting-support"></a>Formularskript-Unterstützung  
 Die bearbeitbaren Raster unterstützen clientseitige Ereignisse und Methoden, die verwendet werden, um benutzerdefinierte Clienterweiterungen gemäß Ihren Geschäftsanforderungen zu schreiben. Weitere Informationen: [Raster und Unterraster in modellgestützten Apps (Client-API-Referenz)](clientapi/reference/grids.md)
  
<a name="EntitiesSupported"></a>   
## <a name="entities-and-views-supported-by-editable-grid"></a>Erstellen von Ansichten, die von bearbeitbaren Raster unterstützt werden  
 Nicht alle Entitäten und Ansichten unterstützen die Verwendung der bearbeitbaren Raster.  
  
 Im Webclient wird eine Entität einen bearbeitbaren Raster unterstützen, wenn die folgenden Bedingungen erfüllt sind:  
  
- Die Entität ist anpassbar (IsCustomizable = true)  
  
- Die Entität ist entweder aktualisiert (IsAIRUpdated = true) oder eine benutzerdefinierte Entität (IsCustomEntity = true)  
  
- Die Entität ist keine untergeordnete Entität (IsChildEntity = false)  
  
  Auf dem mobilen Client unterstützt eine Entität bearbeitbare Raster, wenn die Entität auf dem mobilen Client in der Siteübersicht angezeigt wird.  
  
  Informationen zu den Entitäten, die bearbeitbare Raster unterstützen, siehe Abschnitt **Unterstützte vorgefertigte Entitäten** in [Modellgetriebene App-Raster (Listen) editierbar machen mit Benutzerdefiniertes Steuerelement für bearbeitbares Raster](../../maker/model-driven-apps/make-grids-lists-editable-custom-control.md) 
   
  Bearbeitbare Raster unterstützen keine zugeordneten Roll-up-Ansichten (**Rollup-Typ** = `Related`).  
  
  Verwenden Sie den folgenden Beispielcode, um eine XML-Datei zu generieren, die Sie in Excel als XML-Kalkulationstabelle öffnen können, um die Entitätsunterstützungs-Informationen für bearbeitbare Steuerelemente anzuzeigen. Excel findet das Schema automatisch und zeigt die Informationen unter den folgenden Spalten:  
  
- `LogicalName`Logischer Entitätsname  
  
- `DisplayName`Anzeigename der Entität.  
  
- `CanEnableEditableGridWeb`: Anzeigenstatus (True oder False) oder ob bearbeitbare Raster für die Entität im Webclient unterstützt werden.  
  
- `CanEnableEditableGridMobile`: Anzeigenstatus (True oder False) oder ob bearbeitbare Raster für die Entität im Webclient unterstützt werden. (Dynamics 365 for phones und Dynamics 365 for tablets).  
  
```csharp  
using System;  
using System.Linq;  
using System.Xml.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.Collections.Generic;  
using System.Xml.Serialization;  
using System.Xml;  
using System.IO;  
  
// These namespaces are found in the Microsoft.Xrm.Sdk.dll assembly  
// found in the SDK\bin folder.  
using Microsoft.Xrm.Sdk;  
using Microsoft.Xrm.Sdk.Query;  
using Microsoft.Xrm.Sdk.Metadata;  
using Microsoft.Xrm.Sdk.Client;  
using Microsoft.Xrm.Sdk.Messages;  
  
// This namespace is found in Microsoft.Crm.Sdk.Proxy.dll assembly  
// found in the SDK\bin folder.  
using Microsoft.Crm.Sdk.Messages;  
  
namespace Microsoft.Crm.Sdk.Samples  
{  
    /// <summary>  
    /// This sample generates an XML table to display the entity-support information for   
    ///  editable controls.  
    /// </summary>  
    public class DumpEditableGridEntityInfo  
    {  
        #region Class Level Members  
  
        /// <summary>  
        /// Stores the organization service proxy.  
        /// </summary>  
        OrganizationServiceProxy _serviceProxy;  
  
        // Create storage for new attributes being created  
        public List<AttributeMetadata> addedAttributes;  
  
        // Specify which language code to use in the sample. If you are using a language  
        // other than US English, you will need to modify this value accordingly.  
        // See https://msdn.microsoft.com/library/0h88fahh.aspx  
        public const int _languageCode = 1033;  
  
        // Define the IDs/variables needed for this sample.  
        public int _insertedStatusValue;  
  
        #endregion Class Level Members  
  
        #region How To Sample Code  
        /// <summary>  
        /// </summary>  
        /// <param name="serverConfig">Contains server connection information.</param>  
        /// <param name="promptForDelete">When True, the user will be prompted to delete all  
        /// created entities.</param>  
        public void Run(ServerConnection.Configuration serverConfig, bool promptForDelete)  
        {  
            try  
            {  
  
                // Connect to the Organization service.   
                // The using statement assures that the service proxy will be properly disposed.  
                using (_serviceProxy = new OrganizationServiceProxy(serverConfig.OrganizationUri, serverConfig.HomeRealmUri, serverConfig.Credentials, serverConfig.DeviceCredentials))  
                {  
                    // This statement is required to enable early-bound type support.  
                    _serviceProxy.EnableProxyTypes();  
  
                    //<snippetDumpEditableGridEntityInfo1>  
                    RetrieveAllEntitiesRequest request = new RetrieveAllEntitiesRequest()  
                    {  
                        EntityFilters = EntityFilters.Entity,  
                        RetrieveAsIfPublished = true  
                    };  
  
                    // Retrieve the MetaData.  
                    RetrieveAllEntitiesResponse response = (RetrieveAllEntitiesResponse)_serviceProxy.Execute(request);  
  
                    // Create an instance of StreamWriter to write text to a file.  
                    // The using statement also closes the StreamWriter.  
                    // To view this file, right click the file and choose open with Excel.   
                    // Excel will figure out the schema and display the information in columns.  
  
                    String filename = String.Concat("EditableGridEntityInfo.xml");  
                    using (StreamWriter sw = new StreamWriter(filename))  
                    {  
                        // Create Xml Writer.  
                        XmlTextWriter metadataWriter = new XmlTextWriter(sw);  
  
                        // Start Xml File.  
                        metadataWriter.WriteStartDocument();  
  
                        // Metadata Xml Node.  
                        metadataWriter.WriteStartElement("Metadata");  
  
                        foreach (EntityMetadata currentEntity in response.EntityMetadata)  
                        {  
                            // Start Entity Node  
                            metadataWriter.WriteStartElement("Entity");  
  
                            bool canBeDisplayedInSitemap = currentEntity.IsCustomizable.Value;  
  
                            if (canBeDisplayedInSitemap)  
                            {  
                                metadataWriter.WriteElementString("LogicalName", currentEntity.LogicalName);  
                                metadataWriter.WriteElementString("DisplayName", currentEntity.DisplayName.UserLocalizedLabel?.Label);  
                                metadataWriter.WriteElementString("CanEnableEditableGridWeb", (!(bool)currentEntity.IsChildEntity && ((bool)currentEntity.IsAIRUpdated || (bool)currentEntity.IsCustomEntity)).ToString());  
                                metadataWriter.WriteElementString("CanEnableEditableGridMobile", (currentEntity.IsVisibleInMobileClient.Value || currentEntity.IsVisibleInMobileClient.CanBeChanged).ToString());  
                            }  
  
                            // Write the Entity's Information.  
  
                            //End Entity Node  
                            metadataWriter.WriteEndElement();  
                        }  
  
                        // End Metadata Xml Node  
                        metadataWriter.WriteEndElement();  
                        metadataWriter.WriteEndDocument();  
  
                        // Close xml writer.  
                        metadataWriter.Close();  
                        Console.WriteLine("Dumped information in the EditableGridEntityInfo.xml file");  
                    }  
                }  
            }  
  
            // Catch any service fault exceptions that Microsoft Dynamics CRM throws.  
            catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault>)  
            {  
                // You can handle an exception here or pass it back to the calling method.  
                throw;  
            }  
        }  
        #endregion How To Sample Code  
  
        #region Main  
        /// <summary>  
        /// Standard Main() method used by most SDK samples.  
        /// </summary>  
        /// <param name="args"></param>  
        static public void Main(string[] args)  
        {  
            try  
            {  
                // Obtain the target organization's Web address and client logon   
                // credentials from the user.  
                ServerConnection serverConnect = new ServerConnection();  
                ServerConnection.Configuration config = serverConnect.GetServerConfiguration();  
                DumpEditableGridEntityInfo app = new DumpEditableGridEntityInfo();  
                app.Run(config, false);                  
            }  
            catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex)  
            {  
                Console.WriteLine("The application terminated with an error.");  
                Console.WriteLine("Timestamp: {0}", ex.Detail.Timestamp);  
                Console.WriteLine("Code: {0}", ex.Detail.ErrorCode);  
                Console.WriteLine("Message: {0}", ex.Detail.Message);  
                Console.WriteLine("Plugin Trace: {0}", ex.Detail.TraceText);  
                Console.WriteLine("Inner Fault: {0}",  
                    null == ex.Detail.InnerFault ? "No Inner Fault" : "Has Inner Fault");  
            }  
            catch (System.TimeoutException ex)  
            {  
                Console.WriteLine("The application terminated with an error.");  
                Console.WriteLine("Message: {0}", ex.Message);  
                Console.WriteLine("Stack Trace: {0}", ex.StackTrace);  
                Console.WriteLine("Inner Fault: {0}",  
                    null == ex.InnerException.Message ? "No Inner Fault" : ex.InnerException.Message);  
            }  
            catch (System.Exception ex)  
            {  
                Console.WriteLine("The application terminated with an error.");  
                Console.WriteLine(ex.Message);  
  
                // Display the details of the inner exception.  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine(ex.InnerException.Message);  
  
                    FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> fe  
                        = ex.InnerException  
                        as FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault>;  
                    if (fe != null)  
                    {  
                        Console.WriteLine("Timestamp: {0}", fe.Detail.Timestamp);  
                        Console.WriteLine("Code: {0}", fe.Detail.ErrorCode);  
                        Console.WriteLine("Message: {0}", fe.Detail.Message);  
                        Console.WriteLine("Plugin Trace: {0}", fe.Detail.TraceText);  
                        Console.WriteLine("Inner Fault: {0}",  
                            null == fe.Detail.InnerFault ? "No Inner Fault" : "Has Inner Fault");  
                    }  
                }  
            }  
            // Additional exceptions to catch: SecurityTokenValidationException, ExpiredSecurityTokenException,  
            // SecurityAccessDeniedException, MessageSecurityException, and SecurityNegotiationException.  
  
            finally  
            {  
  
                Console.WriteLine("Press <Enter> to exit.");  
                Console.ReadLine();  
            }  
  
        }  
        #endregion Main  
  
    }  
}  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Raster und Unterraster in modellgestützten Apps (Client-API-Referenz)](clientapi/reference/grids.md)   
 [Modellgetriebene App-Raster (Listen) editierbar machen mit Benutzerdefiniertes Steuerelement für bearbeitbares Raster](../../maker/model-driven-apps/make-grids-lists-editable-custom-control.md)
