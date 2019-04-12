---
title: 'Exemplarische Vorgehensweise: Aktualisieren eines Dienstendpunkts, der aus einer Lösung importiert wurde (Common Data Service) | Microsoft Docs'
description: 'Diese exemplarische Vorgehensweise zeigt das Aktualisieren eines Dienstendpunkts, der aus einer Lösung importiert wurde.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 66795838-3b15-bfb3-6f59-68cfe2fe988e
author: brandonsimons
ms.author: jdaly
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-update-a-service-endpoint-imported-from-a-solution"></a>Tutorial: Aktualisieren eines Dienstendpunkts, der aus einer Lösung importiert wurde

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/walkthrough-update-service-endpoint-imported-solution -->

Ein extre Schritt ist nach dem Import einer Lösung, die mindestens einen Dienstendpunkt enthält, der für die SAS-Autorisierung konfiguriert ist in eine Organisation erforderlich. Wenn die Lösung mit den Dienstendpunkten exportiert wird, enthält die exportierte Lösung nicht den SAS-Schlüssel für jeden Dienstendpunkt. Nachdem Sie die Lösung in eine Organisation Importiert haben, müssen Sie einen weiteren Schritt ausführen, um den SAS-Schlüssel für jeden Dienstendpunkt bereitzustellen.  
  
 Gehen Sie folgendermaßen vor, um den SAS-Schlüssel für jeden Dienstendpunkt nach dem Lösungsimport festzulegen.  
  
### <a name="update-the-sas-key"></a>SAS-Schlüssel aktualisieren  
  
1.  Führen Sie das Plug-In-Registrierungstool aus. Sie finden es im Ordner "Tools" des SDK-Downloads Dynamics CRM 2016 Service Pack 1 On-Premises (oder höher). Vorherige Versionen des Tools unterstützen die SAS-Autorisierung nicht.  
  
2.  Verwenden Sie das Tools, um sich bei der Organisation anzumelden, die die importierte Lösung enthält.  
  
3.  Wählen Sie den Ziel-Dienstendpunkt in der Registerkartenansicht der Organisation aus.  
  
4.  Wählen Sie **Aktualisieren**. Sie sollten das folgende Formular mit ausgefüllten Feldern sehen.  
  
 ![Aktualisieren des SAS-Schlüsselwerts des Dienstendpunkts](media/sas-key.PNG "Aktualisieren des SAS-Schlüsselwerts des Dienstendpunkts")  
  
5.  Das Feld **SAS-Schlüssel** wird mit dem Wert "*******" angezeigt.  Ersetzen Sie diesen Wert durch den entsprechenden SAS-Schlüsselwert. Sie erhalten den SAS-Schlüssel für Ihre Azure-Messaging-Entität (Thema, Warteschlange usw.) im [klassischen Portal](http://manage.windowsazure.com) von Azure.  
  
6.  Wählen Sie **Speichern** aus.  
  
### <a name="see-also"></a>Siehe auch  
[Azure-Integration für Dynamics 365](azure-integration.md)

 [Service Bus-Authentifizierung und -Autorisierung](https://azure.microsoft.com/en-us/documentation/articles/service-bus-authentication-and-authorization/)
