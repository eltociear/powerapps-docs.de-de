---
title: 'Exemplarische Vorgehensweise: Konfigurieren von Microsoft Azure (SAS) für die Integration (Common Data Service) | Microsoft Docs'
description: Die exemplarische Vorgehensweise führt Sie durch die Schritte zum Konfigurieren des Azure Service Bus-Austellers, -Bereichs und der -Regeln, damit eine Listener-Anwendung die Common Data Service-Messages lesen kann, die an den Azure Service Bus übermittelt werden.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: d7b24b11-57f0-ab05-4bec-0b64efee178d
author: JimDaly
ms.author: jdaly
manager: ryjones
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a6d6e12e07174d67afc3fa1461767eca284c0015
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748504"
---
# <a name="tutorial-configure-azure-sas-for-integration-with-common-data-service"></a>Lernprogramm: Konfigurieren von Azure (SAS) für die Integration in Common Data Service

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/walkthrough-configure-azure-sas-integration -->

Diese exemplarische Vorgehensweise führt Sie durch die Schritte zum Konfigurieren des Azure Service Bus-Austellers, -Bereichs und der -Regeln, damit eine Listener-Anwendung die Common Data Service-Messages lesen kann, die an den Azure Service Bus übermittelt werden.  
  
> [!NOTE]
>  Dieser Vorgehensweise gilt für eine beliebige Common Data Service-Bereitstellung, wenn die SAS-Autorisierung für das Azure-Messaging verwendet wird. Weitere Informationen zur Azure Service Bus-Authentifizierung finden Sie unter: [Service Bus-Authentifizierung und -Autorisierung](https://azure.microsoft.com/documentation/articles/service-bus-authentication-and-authorization/).  
>   
> Sie müssen das Plug-In-Registrierungstool verwenden. Um das Plugin Registration Tool herunterzuladen, gehen sie zu [Tools herunterlae von NuGet](download-tools-NuGet.md).
  
## <a name="prerequisites"></a>Voraussetzungen  
  
-   Ein Azure-Konto mit einer Lizenz zum Erstellen von Service Bus-Entitäten.
  
-   Ein SAS-konfigurierter Service Bus-Namespace
  
-   Eine SAS-konfigurierte Service Bus-Messaging-Entität: Warteschlange, Thema, Relay oder Ereignishub
  
-   Die Messaging-Entität erfordert mindestens die `Send`-Richtlinienberechtigung. Für ein bidirektionales Relay benötigt die Richtlinie auch die `Listen`-Berechtigung.  
-  Die Autorisierungs-Verbindungszeichenfolge für Ihre Messaging-Entität 
  
 ![Definieren der Azure-Richtlinienberechtigungen](media/policy-permissions.png "Definieren der Azure-Richtlinienberechtigungen")  
  
 Anweisungen zur Erstellung eines Service Bus-Namespace und einer Messaging-Entität finden Sie unter [Erstellen eines Service Bus-Namespace mit dem Azure-Portal](/azure/service-bus-messaging/service-bus-create-namespace-portal).  
  
## <a name="create-a-service-endpoint"></a>Erstellt eines Dienstendpunkts

Eine [ServiceEndpoint-Entität ](reference/entities/serviceendpoint.md) enthält Konfigurationsdaten, die für ein externes Messaging mit einem Azure Service Bus-Lösungsendpunkt erforderlich sind. Indem Sie das Plug-In-Registrierungstool verwenden, können Sie einfach eine Dienstendpunkt-Entität in einer Common Data Service-Organisation erstellen und den Aussteller, den Umfang und die Regeln für den Service Bus-Endpunkt konfigurieren.
  
### <a name="register-a-service-endpoint"></a>Registrieren eines Dienstendpunkts  
  
1.  Führen Sie das Plug-In-Registrierungstool aus, und melden Sie sich bei Ihrer Common Data Service-Zielorganisation an.  
  
2.  Wählen Sie **Registrieren > Neuen Dienstendpunkt registrieren**.  
  
3.  Überprüfen Sie **Beginnen mit der Verbindungszeichenfolge aus dem Azure Service Bus-Portal**, und fügen Sie die Verbindungszeichenfolge Ihrer Service Bus-Messaging-Entität ein.  
  
 ![Bereitstellen einer Autorisierungsverbindungszeichenfolge](media/sas-connection-string.PNG "Bereitstellen einer Autorisierungsverbindungszeichenfolge")  
  
4.  Wählen Sie **Weiter**.  
  
5.  Füllen Sie das Formular **Dienstendpunktregistrierung** aus, indem Sie den **Kennzeichnungstyp**, das **Nachrichtenformat** und optional die Felder **Gesendete Benutzerinformationen** und **Beschreibung** ausfüllen.  
  
 ![Service-Endpunktregistrierung](media/service-endpoint-registration.PNG "Service-Endpunktregistrierung")  
  
   Mehr Information über das Nachrichtenformat finden Sie unter [Listener-Anwendung für eine Azure-Lösung schreiben](write-listener-application-azure-solution.md).  
  
6.  Wählen Sie **Speichern** aus.  
  
7.  Nach einigen Sekunden sehen Sie den neuen Dienstendpunkt in der Liste **Registrierte Plug-ins und benutzerdefinierte Workflowaktivitäten**.  
  
 ![Neuer Dienstendpunkt](media/new-service-endpoint.PNG "Neuer Dienstendpunkt")  
  
### <a name="see-also"></a>Siehe auch

[Azure-Integration](azure-integration.md)<br />
[Azure Service Bus](/azure/service-bus-messaging/service-bus-fundamentals-hybrid-solutions.md)
