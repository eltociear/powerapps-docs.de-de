---
title: Konfigurieren der Azure-Integration (Common Data Service) | Microsoft-Dokumentation
description: Das Thema beschreibt die Konfiguration der Azure-Integration mit Common Data Service.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: b030ca4e60d9f51f53706d682146c9acd46d5aa0
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748576"
---
# <a name="configure-azure-integration-with-common-data-service"></a>Konfigurieren der Azure-Integration in Common Data Service

Sie können die Daten der Nachrichtenanforderung für den aktuellen Kernbetrieb an Cloud-basierte Anwendungen posten, die Azure Service Bus überwachen. Um diese Funktion in Common Data Service zu aktivieren, führen Sie die Aufgaben aus, die in diesem Thema aufgeführt sind.

## <a name="configure-azure-for-common-data-service-integration"></a>Konfigurieren von Azure für die Common Data Service-Integration

Weil Sie SAS zur Autorisierung verwenden werden, müssen Sie die Regeln und die Aussteller Ihrer Azure-Lösung konfigurieren, eine Listener-Anwendung die Common Data Service-Mitteilung lesen zu lassen, die auf dem Azure Service Bus gepostet wurde. Darüber hinaus müssen Sie die Servicebusregeln konfigurieren, um den Common Data Service Anstelleranspruch zu akzeptieren. Die empfohlene Methode zum Konfigurieren von Azure ist, das Plug-In-Registrierungstool (PRT) zu benutzen.

Anleitungen zur Konfiguration der Berechtigung finden Sie im [Tutorial: Konfigurieren von Azure (SAS) für die Integration in Common Data Service](walkthrough-configure-azure-sas-integration.md).

## <a name="test-configuration"></a>Testkonfiguration

Nach der Konfiguration der Azure-Integration müssen Sie diese zusätzlichen Aufgaben ausführen.

1. Schreiben und registrieren Sie eine Listener-Anwendung mit einer Azure Service Bus-Endpunktlösung. Weitere Informationen finden Sie in der Azure Service Bus [-Dokumentation](/azure/service-bus-messaging/service-bus-messaging-overview).
1. Registrieren Sie ein Azure-fähiges Plug-In oder eine Azure-fähige benutzerdefinierte Workflowaktivität mit Common Data Service. Weitere Informationen finden Sie unter [Lernprogramm: Registrieren eines Azure-fähigen Plug-Ins mithilfe des Plug-In-Registrierungstools](walkthrough-register-azure-aware-plug-in-using-plug-in-registration-tool.md)
1. Führen Sie den gewünschten Common Data Service Vorgang aus, der das Plug-In oder die benutzerdefinierte Workflowaktivität auslöst.

Wenn alle vorangegangenen Schritte korrekt ausgeführt wurden, sollte eine Nachricht mit dem Common Data Service-Datenkontext an die Azure-Warteschlange oder das Thema gesendet werden und dann letztendlich von der Listener-Anwendung empfangen werden. Sie können zum Raster Systemaufträge in der Common Data Service-Webanwendung navigieren und den Status der verknüpften Systemaufträge überprüfen, um zu sehen, ob die Nachricht an den Azure Service Bus erfolgreich ausgeführt wurde. Bei Fehlern zeigt der Nachrichtenabschnitt Systemauftrag die Fehlerdetails an.

### <a name="see-also"></a>Siehe auch

[Azure-Integration](azure-integration.md)<br />
[Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen](plug-ins.md)<br />
[Arbeiten mit Common Data Service-Daten in Ihrer Azure-Lösung](work-data-azure-solution.md)<br />
[Schreiben einer Listener-Anwendung für eine Azure-Lösung](write-listener-application-azure-solution.md)<br />
[Was ist ein Azure Service Bus?](/azure/service-bus-messaging/service-bus-messaging-overview)