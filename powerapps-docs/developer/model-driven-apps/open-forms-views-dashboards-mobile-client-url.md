---
title: Öffnen von Formularen, Ansichten und Dashboards im mobilen Dynamics 365-Client mit einer URL (modellgestützte Apps) | Microsoft Docs
description: Verwenden Sie den Anwendungshandler für mobile Dynamics 365-Clients, um direkt mit Dynamics 365-Formularen, -ansichten und -Dashboards aus externen Anwendungen zu verknüpfen. So wird bei einem Klick auf eine externen Anwendung das Zielelement in Dynamics 365 für Smartphones oder Dynamics 365 für Tablets geöffnet.
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
ms.openlocfilehash: 0c4e3c0fe4188b3b9f2d95cb479a23f6e54c193b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748271"
---
# <a name="open-forms-views-and-dashboards-in-mobile-client-with-a-url"></a>Öffnen von Formularen, Ansichten und Dashboards im mobilen Client mit einer URL

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/open-forms-views-dashboards-mobile-client-url

At this point I understand this mobile client is still branded as 'Dynamics 365'
 -->
 
 Verwenden Sie den neuen Anwendungshandler für mobile Clients, um direkt Formulare, Ansichten und Dashboards aus externen Anwendungen zu verknüpfen. So wird bei einem Klick auf eine externen Anwendung das Zielelement in Dynamics 365 for Phones oder Dynamics 365 for tablets geöffnet. Außerdem können Sie ein leeres Formular öffnen, um ein Entitätsformular zu erstellen.  
  
 Falls Sie bereits bei Ihrer Instanz in Dynamics 365 for phones oder Dynamics 365 for tablets angemeldet sind, wird der Zieldatensatz im mobilen Client angezeigt, wenn Sie auf den Link in der externen Anwendung klicken. Andernfalls werden Sie aufgefordert, sich an der Instanz im mobilen Client anzumelden; dabei wird das Zielelement angezeigt. Sie müssen Dynamics 365 for phones oder Dynamics 365 for tablets auf Ihrem Mobilgerät installieren, um diese Funktion verwenden zu können.  
  
<a name="Parameters"></a>

## <a name="query-string-parameters-for-the-url"></a>Abfragezeichenfolgenparameter für die URL

 Verwenden Sie die folgenden Anwendungshandler- und Abfragezeichenfolgenparameter, um die URL zu verfassen.  
  
```  
ms-dynamicsxrm://?pagetype=<VALUE>&etn=<VALUE>&id=<VALUE>  
```  
  
 Die Abfragezeichenfolgen-Parameter aus der folgenden Tabelle werden verwendet.  
  
|Abfragezeichenfolgeparameter|Beschreibung|  
|----------------------------|-----------------|  
|pagetype|Geben Sie die zu öffnende Seite an. Gültige Werte sind `entity`, `view`, `dashboard` und `create`.<br /><br /> Dieser Parameter ist erforderlich.|  
|etn|Geben Sie den logischen Entitätsnamen an, das Sie öffnen möchten oder erstellen Sie einen Datensatz.  Logische Namen von Entitäten werden kleingeschrieben und in der <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.LogicalName> definiert. -Eigenschaft verfügbar.<br /><br /> Dieser Parameter ist erforderlich, falls der `pagetype`-Parameter auf `entity`, `view` oder `create` festgelegt ist.|  
|ID|Geben Sie die ID der Entität, die Ansicht oder des Dashboard-Datensatzes an, das Sie öffnen möchten.<br /><br /> Dieser Parameter ist erforderlich, falls der `pagetype`-Parameter auf `entity` oder `dashboard` festgelegt ist.<br /><br /> Es ist optional, wenn der Parameter `pagetype` auf `view` festgelegt ist. Wenn Sie keine Ansichts-ID angeben, wird die Standardansicht für die Entität angezeigt, die im Parameter `etn` angegeben ist.|  
  
<a name="Example"></a>

## <a name="example-urls"></a>Beispiel-URLs

 Hier sind einige Beispiel-URLs für das Öffnen von Formularen, Ansichten und Dashboards.  
  
|Aktion|Beispiel-URL|  
|------------|-----------------|  
|Öffnen einer Firmenentität mit der Firmendatensatz-ID 91330924-802A-4B0D-A900-34FD9D790829|`ms-dynamicsxrm://?pagetype=entity&etn=account&id=91330924-802A-4B0D-A900-34FD9D790829`|  
|Öffnen einer Ansicht mit der Ansichtsdatensatz-ID 899D4FCF-F4D3-E011-9D26-00155DBA3819 für die Kontaktentität|`ms-dynamicsxrm://?pagetype=view&etn=contact&id=899D4FCF-F4D3-E011-9D26-00155DBA3819`|  
|Öffnen der Standardansicht für eine Firmenentität|`ms-dynamicsxrm://?pagetype=view&etn=account`|  
|Öffnen eines Dashboards mit der Dashboarddatensatz-ID 2E3D0841-FA6D-DF11-986C-00155D2E3002|`ms-dynamicsxrm://?pagetype=dashboard&id=2E3D0841-FA6D-DF11-986C-00155D2E3002`|  
|Öffnen eines Formulars für die Erstellung eines Firmendatensatzes|`ms-dynamicsxrm://?pagetype=create&etn=account`|  
  
### <a name="see-also"></a>Siehe auch

 [Öffnen von Formularen, Ansichten, Dialogen und Berichten mit einer URL](open-forms-views-dialogs-reports-url.md)  
 [Erweitern des Clients](/dynamics365/customer-engagement/developer/extend-client)
