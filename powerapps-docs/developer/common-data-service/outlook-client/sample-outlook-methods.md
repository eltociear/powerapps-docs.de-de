---
title: 'Beispiel: Verwenden von Dynamics 365 for Outlook-Methoden (Common Data Service) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie die Methoden in der `Microsoft.Crm.Outlook.Sdk.dll`-Assembly verwendet werden.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-use-dynamics-365-for-outlook-methods"></a>Beispiel: Verwendung von Dynamics 365 for Outlook Methoden

Dieser Beispielcode ist für Common Data Service. Um das Beispiel herunterzuladen, sehen Sie sich [Beispiel: Verwendung von Dynamics 365 for Outlook-Methoden](https://msdn.microsoft.com/library/gg309513.aspx) an.

## <a name="prerequisites"></a>Voraussetzungen

Um das Beispielprojekt herunterzuladen und die NuGet-Pakete wiederherzustellen, die im Beispielprojekt verwendet werden, ist eine Internetverbindung erforderlich.
  
## <a name="demonstrates"></a>Demonstriert  
 Dieses Beispiel zeigt, wie die Methoden in der `Microsoft.Crm.Outlook.Sdk.dll`-Assembly verwendet werden.  
  
## <a name="example"></a>Beispiel  

```csharp
// Set up the CRM Service.  
CrmOutlookService outlookService = new CrmOutlookService();

// Determine if the Outlook client is running
if (outlookService.IsCrmClientLoaded)
{
    if (outlookService.IsCrmDesktopClient)
    {
        // The desktop client cannot go offline
        Console.WriteLine("CRM Client Desktop URL: " +
            outlookService.ServerUri.AbsoluteUri);
        Console.WriteLine("CRM Client state: " +
            outlookService.State.ToString());
    }
    else
    {
        // See if laptop client is offline
        if (outlookService.IsCrmClientOffline)
        {
            Console.WriteLine("CRM Client Offline URL: " +
                outlookService.ServerUri.AbsoluteUri);
            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());

            // Take client online
            // NOTE: GoOnline() will automatically Sync up with CRM
            // database, no need to call Sync() manually
            Console.WriteLine("Going Online...");
            outlookService.GoOnline();

            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());
        }
        else
        {
            Console.WriteLine("CRM Client Online URL: " +
                outlookService.ServerUri.AbsoluteUri);
            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());

            // Take client offline 
            // NOTE: GoOffline triggers a synchronization of the
            // offline database with the online server.
            // If a sync is not required, you can use SetOffline().
            Console.WriteLine("Going Offline...");
            outlookService.GoOffline();

            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());
        }
    }
}
```
  
### <a name="see-also"></a>Siehe auch  

[Erweitern von Dynamics 365 for Outlook](extend-dynamics-365-outlook.md)<br />
<xref:Microsoft.Crm.Outlook.Sdk.CrmOutlookService><br />
<xref:Microsoft.Crm.Outlook.Sdk.CrmOutlookService.GoOnline><br />
<xref:Microsoft.Crm.Outlook.Sdk.CrmOutlookService.GoOffline>