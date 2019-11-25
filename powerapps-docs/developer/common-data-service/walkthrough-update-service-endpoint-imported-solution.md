---
title: 'Exemplarische Vorgehensweise: Aktualisieren eines Dienstendpunkts, der aus einer Lösung importiert wurde (Common Data Service) | Microsoft Docs'
description: Diese exemplarische Vorgehensweise zeigt das Aktualisieren eines Dienstendpunkts, der aus einer Lösung importiert wurde.
keywords: ''
ms.date: 10/06/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 66795838-3b15-bfb3-6f59-68cfe2fe988e
author: JimDaly
ms.author: jdaly
manager: ryjones
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 969660edb15b7be94921e4d16050699ca145ec4a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748502"
---
# <a name="tutorial-update-a-service-endpoint-imported-from-a-solution"></a>Tutorial: Aktualisieren eines Dienstendpunkts, der aus einer Lösung importiert wurde

Ein extre Schritt ist nach dem Import einer Lösung, die mindestens einen Dienstendpunkt enthält, der für die SAS-Autorisierung konfiguriert ist in eine Organisation erforderlich. Wenn die Lösung mit den Dienstendpunkten exportiert wird, enthält die exportierte Lösung nicht den SAS-Schlüssel für jeden Dienstendpunkt. Nachdem Sie die Lösung in eine Organisation Importiert haben, müssen Sie einen weiteren Schritt ausführen, um den SAS-Schlüssel für jeden Dienstendpunkt bereitzustellen.  
  
Gehen Sie folgendermaßen vor, um den SAS-Schlüssel für jeden Dienstendpunkt nach dem Lösungsimport festzulegen.  
  
## <a name="update-the-sas-key"></a>SAS-Schlüssel aktualisieren  
  
1. Führen Sie das Plugin Registration Tool aus, das unter NuGet heruntergeladen werden kann. Weitere Informationen: [Tools von NuGet herunterladen](download-tools-nuget.md)
  
1. Melden Sie sich über das Plugin Registration Tool bei der Organisation an, die die importierte Lösung enthält.  
  
1. Wählen Sie den Ziel-Dienstendpunkt in der Registerkartenansicht der Organisation aus.  
  
1. Wählen Sie **Aktualisieren**. Sie sollten das folgende Formular mit ausgefüllten Feldern sehen.  
  
    ![SAS-Schlüsselwert zum Aktualisieren des Dienstendpunkts](media/sas-key.PNG "SAS-Schlüsselwert zum Aktualisieren des Dienstendpunkts")  
  
1. Das Feld **SAS-Schlüssel** wird mit dem Wert "*******" angezeigt.  Ersetzen Sie diesen Wert durch den entsprechenden SAS-Schlüsselwert. Sie erhalten den SAS-Schlüssel für Ihre Azure-Messaging-Entität (Warteschlange, Thema usw.) im [Azure-Portal](https://portal.azure.com).  
  
1. Wählen Sie **Speichern** aus.  
  
### <a name="see-also"></a>Siehe auch

[Azure-Integration](azure-integration.md)<br />
[Service Bus-Authentifizierung und -Autorisierung](/azure/service-bus-messaging/service-bus-authentication-and-authorization)<br />
[Service Bus Access Control mit Shared Access Signatures](/azure/service-bus-messaging/service-bus-sas)
