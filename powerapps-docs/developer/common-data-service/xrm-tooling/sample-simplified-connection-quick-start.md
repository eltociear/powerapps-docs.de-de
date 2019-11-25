---
title: 'Beispiel: Schnellstart für vereinfachte Verbindung (Entwicklerhandbuch für Common Data Service) | MicrosoftDocs'
description: 'In diesem Beispiel wird gezeigt, wie Sie eine Verbindung mit den Common Data Service-Webdiensten mithilfe der CrmServiceClient-Klasse herstellen und einfache Erstellungs-, Aktualisierungs-, Abruf- und Löschvorgänge für eine Entität ausführen. '
ms.custom: ''
ms.date: 03/27/2019
author: Nkrb
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Common Data Service (online)
ms.assetid: a4fb3634-948e-4bac-a32f-f626c78d83a0
caps.latest.revision: 29
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- D365CE
- PowerApps
ms.openlocfilehash: aec27b41272c83a3baa1e35c39b757d1225ac20c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748326"
---
# <a name="sample-simplified-connection-quick-start-using-common-data-service"></a>Beispiel: Erste Schritte für einfacheres Herstellen von Verbindungen mithilfe von Common Data Service

In diesem Beispiel wird gezeigt, wie Sie eine Verbindung mit den Common Data Service-Webdiensten mithilfe der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse herstellen und einfache Erstellungs-, Aktualisierungs-, Abruf- und Löschvorgänge für eine Entität ausführen. Weitere Informationen zu <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> finden Sie unter [Verwenden von CrmServiceClient-Konstruktoren zur Herstellung einer Verbindung mit Common Data Service](use-crmserviceclient-constructors-connect.md).

## <a name="requirements"></a>Anforderungen

Der vollständige Beispielcode befindet sich hier [Beispiel: Schnellstart für Common Data Service](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/Xrm%20Tooling/QuickStartCS) 

Sie müssen die Datei `app.config` mit den Verbindungsinformationen für die Common Data Service-Instanz ändern, bevor Sie das Beispiel ausführen. 

## <a name="demonstrates"></a>Demonstriert

Dieses Beispiel authentifiziert den Benutzer bei den Common Data Service-Webdiensten durch Anwendung der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse und -Methoden. Nachdem ein Verweis auf den Organisationswebdienst abgerufen wurde, führt das Beispiel einfache Erstellungs-, Aktualisierungs-, Abruf- und Löschvorgänge für eine `account`-Entität aus. Das Beispiel behandelt zudem allgemeine Ausnahmen. Zum Einrichten einer Verbindung mit dem Organisationswebdienst wird kein Hilfscode verwendet.  

Außerdem unterstützt dieses Beispiel `OAuth`-Authentifizierung und erweiterte Verbindungsdiagnose. Weitere Informationen zur Verwendung der Diagnose, siehe [Konfigurieren der Nachverfolgung für XRM Tooling](configure-tracing-xrm-tooling.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt `app.config file` Um dies zu verwenden, entfernen Sie die Kommentarzeichen “<!- -” am Anfang von \<add … />-Zeile und “- ->” am Ende der Zeile für die Zeile, die für den Server und die Organisation relevant ist. Ändern Sie als Nächstes die Attributwerte entsprechend Ihrer Konfiguration.

```xml
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <connectionStrings>  
    <!-- Online using Office 365 -->  
    <!-- <add name="Server=CRM Online, organization=contoso, user=someone"  
         connectionString="Url=https://contoso.crm.dynamics.com; Username=someone@contoso.onmicrosoft.com; Password=password; authtype=Office365"/> -->  
  </connectionStrings>  
  <startup>  
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.2" />  
  </startup>  
<system.diagnostics>  
    <trace autoflush="true"/>  
    <sources>  
      <source name="Microsoft.Xrm.Tooling.Connector.CrmServiceClient" switchName="Microsoft.Xrm.Tooling.Connector.CrmServiceClient" switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="fileListener"/>  
        </listeners>  
      </source>  
      <source name="Microsoft.Xrm.Tooling.CrmConnectControl" switchName="Microsoft.Xrm.Tooling.CrmConnectControl" switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="fileListener"/>  
        </listeners>  
      </source>  
      <source name="CrmSvcUtil" switchName="CrmSvcUtil" switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="fileListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  

      <!--Possible values for switches: Off, Error, Warning, Information, Verbose  
                        Verbose:      includes Error, Warning, Info, Trace levels  
                        Information:  includes Error, Warning, Info levels  
                        Warning:      includes Error, Warning levels  
                        Error:        includes Error level-->  

      <add name="Microsoft.Xrm.Tooling.CrmConnectControl" value="Off"/>  
      <add name="Microsoft.Xrm.Tooling.Connector.CrmServiceClient" value="Error"/>  
      <add name="CrmSvcUtil" value="Off"/>  
    </switches>  

    <sharedListeners>  
      <add name="fileListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="CrmSvcUtil.log"/>  
    </sharedListeners>  

  </system.diagnostics>  
  <runtime>  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <dependentAssembly>  
        <assemblyIdentity name="Microsoft.Xrm.Sdk" publicKeyToken="31bf3856ad364e35" culture="neutral" />  
        <bindingRedirect oldVersion="0.0.0.0-7.0.0.0" newVersion="8.0.0.0" />  
      </dependentAssembly>  
      <dependentAssembly>  
        <assemblyIdentity name="Microsoft.Xrm.Sdk.Deployment" publicKeyToken="31bf3856ad364e35" culture="neutral" />  
        <bindingRedirect oldVersion="0.0.0.0-7.0.0.0" newVersion="8.0.0.0" />  
      </dependentAssembly>  
      <dependentAssembly>  
        <assemblyIdentity name="Microsoft.ServiceBus" publicKeyToken="31bf3856ad364e35" culture="neutral" />  
        <bindingRedirect oldVersion="0.0.0.0-2.4.0.0" newVersion="2.4.0.0" />  
      </dependentAssembly>  
    </assemblyBinding>  
  </runtime>  
</configuration>  
```

## <a name="example"></a>Beispiel

```csharp
using Microsoft.Crm.Sdk.Messages;
using Microsoft.Xrm.Sdk;
using Microsoft.Xrm.Sdk.Query;
using Microsoft.Xrm.Tooling.Connector;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace PowerApps.Samples
{
   public partial class SampleProgram
    {
        [STAThread] // Added to support UX
        static void Main(string[] args)
        {
            CrmServiceClient service = null;

            try
            {
                service = SampleHelpers.Connect("Connect");
                if (service.IsReady)
                {
                    #region Sample Code
                    ////////////////////////////////////
                    #region Set up
                    SetUpSample(service);
                    #endregion Set up
                    #region Demonstrate
                    // Obtain information about the logged on user from the web service.
                    Guid userid = ((WhoAmIResponse)service.Execute(new WhoAmIRequest())).UserId;
                    SystemUser systemUser = (SystemUser)service.Retrieve("systemuser", userid,
                        new ColumnSet(new string[] { "firstname", "lastname" }));
                    Console.WriteLine("Logged on user is {0} {1}.", systemUser.FirstName, systemUser.LastName);

                    // Retrieve the version of Microsoft Dynamics CRM.
                    RetrieveVersionRequest versionRequest = new RetrieveVersionRequest();
                    RetrieveVersionResponse versionResponse =
                        (RetrieveVersionResponse)service.Execute(versionRequest);
                    Console.WriteLine("Microsoft Dynamics CRM version {0}.", versionResponse.Version);

                    // Instantiate an account object. Note the use of option set enumerations defined in OptionSets.cs.
                    // Refer to the Entity Metadata topic in the SDK documentation to determine which attributes must
                    // be set for each entity.
                    Account account = new Account { Name = "Fourth Coffee" };
                    account.AccountCategoryCode = new OptionSetValue((int)AccountAccountCategoryCode.PreferredCustomer);
                    account.CustomerTypeCode = new OptionSetValue((int)AccountCustomerTypeCode.Investor);

                    // Create an account record named Fourth Coffee.
                    _accountId = service.Create(account);

                    Console.Write("{0} {1} created, ", account.LogicalName, account.Name);

                    // Retrieve the several attributes from the new account.
                    ColumnSet cols = new ColumnSet(
                        new String[] { "name", "address1_postalcode", "lastusedincampaign" });

                    Account retrievedAccount = (Account)service.Retrieve("account", _accountId, cols);
                    Console.Write("retrieved, ");

                    // Update the postal code attribute.
                    retrievedAccount.Address1_PostalCode = "98052";

                    // The address 2 postal code was set accidentally, so set it to null.
                    retrievedAccount.Address2_PostalCode = null;

                    // Shows use of a Money value.
                    retrievedAccount.Revenue = new Money(5000000);

                    // Shows use of a Boolean value.
                    retrievedAccount.CreditOnHold = false;

                    // Update the account record.
                    service.Update(retrievedAccount);
                    Console.WriteLine("and updated.");

                #region Clean up
                CleanUpSample(service);
                    #endregion Clean up
                }
                #endregion Demonstrate
                #endregion Sample Code
                else
                {
                    const string UNABLE_TO_LOGIN_ERROR = "Unable to Login to Dynamics CRM";
                    if (service.LastCrmError.Equals(UNABLE_TO_LOGIN_ERROR))
                    {
                        Console.WriteLine("Check the connection string values in cds/App.config.");
                        throw new Exception(service.LastCrmError);
                    }
                    else
                    {
                        throw service.LastCrmException;
                    }
                }
            }
            catch (Exception ex)
            {
                SampleHelpers.HandleException(ex);
            }

            finally
            {
                if (service != null)
                    service.Dispose();

                Console.WriteLine("Press <Enter> to exit.");
                Console.ReadLine();
            }
        }
            }
}

```

### <a name="see-also"></a>Siehe auch

[Verwenden von Verbindungszeichenfolgen im XRM-Tooling zur Herstellung einer Verbindung mit Common Data Service](use-connection-strings-xrm-tooling-connect.md)<br />
[Beispiel: Schnellstart für XRM Tooling API](sample-quick-start-xrm-tooling-api.md)<br />
