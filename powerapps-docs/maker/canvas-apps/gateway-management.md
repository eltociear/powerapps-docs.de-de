---
title: Verwalten eines lokalen Datengateways für Canvas-Apps | Microsoft-Dokumentation
description: Ein lokales Datengateway und seine Verbindungen verwalten
author: arthiriyer
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/14/2020
ms.author: arthii
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0956668fa3576dca58c728396d0c4c08473df73f
ms.sourcegitcommit: c0508e233a03ac4846c04d5caae79eccca3e2843
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385210"
---
# <a name="manage-an-on-premises-data-gateway-in-power-apps"></a>Verwalten eines lokalen Daten Gateways in powerapps

Installieren Sie ein lokales Daten Gateway, um Daten schnell und sicher zwischen einer Canvas-APP zu übertragen, die in powerapps erstellt wurde, und einer Datenquelle, die sich nicht in der Cloud befindet, wie z. b. eine lokale SQL Server-Datenbank oder eine lokale SharePoint-Website. Zeigen Sie alle Gateways an, für die Sie Administratorberechtigungen haben, und verwalten Sie Berechtigungen und Verbindungen für diese Gateways.

Mit einem Gateway können Sie Verbindungen mit lokalen Daten herstellen. Diese Verbindungstypen können Sie verwenden:

* SharePoint
* SQL Server
* Oracle
* Informix
* Dateisystem
* DB2

## <a name="prerequisites"></a>Erforderliche Komponenten

* Der Benutzername und das Kennwort, die [Sie für die Registrierung bei Power](../signup-for-powerapps.md) Apps verwendet haben.
* Administrative Berechtigungen für ein Gateway (Sie verfügen über diese Berechtigungen standardmäßig für jedes Gateway, das Sie installieren, und ein Administrator eines anderen Gateways kann Ihnen diese Berechtigungen für jenes Gateway erteilen.)
* Eine Lizenz, die Zugriff auf lokale Daten über ein lokales Gateway unterstützt. Weitere Informationen finden Sie im Abschnitt "Verbindungen" auf der Seite mit den [Preisinformationen](https://powerapps.microsoft.com/pricing/).
* Gateways und lokale Verbindungen können nur in der [Standardumgebung](working-with-environments.md) des Benutzers erstellt und verwendet werden.

## <a name="install-a-gateway"></a>Gateway installieren

Führen Sie die Schritte unter [Installieren eines lokalen Datengateways](/data-integration/gateway/service-gateway-install) aus, um ein Gateway zu installieren. Installieren Sie das Gateway im Standardmodus, da das _lokale Datengateway (persönlicher Modus)_ nur für Power BI verfügbar ist.

## <a name="view-and-manage-gateway-permissions"></a>Anzeigen und Verwalten von Gatewayberechtigungen

1. Klicken oder tippen Sie unter [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) im linken Navigationsbereich auf **Gateways** und anschließend auf ein Gateway.

2. Fügen Sie einen Benutzer zu einem Gateway hinzu, indem Sie auf **Benutzer** klicken oder tippen, einen Benutzer oder eine Gruppe und anschließend eine Berechtigungsstufe angeben:

   * **Verwenden**: Benutzer, die Verbindungen im Gateway erstellen dürfen, die für Apps und Flows verwendet werden, aber das Gateway nicht freigeben dürfen. Wählen Sie diese Berechtigung für Benutzer, die Apps ausführen, aber nicht freigeben.
   * **Verwenden + freigeben**: Benutzer, die Verbindungen im Gateway erstellen dürfen, die für Apps und Flows verwendet werden, und das Gateway automatisch freigeben, wenn eine App freigegeben wird. Wählen Sie diese Berechtigung für Benutzer, die Apps für andere Benutzer oder die Organisation freigeben.
   * **Administrator**: Administratoren mit Vollzugriff auf das Gateway dürfen u. a. Benutzer hinzufügen, Berechtigungen festlegen, Verbindungen mit allen verfügbaren Datenquellen erstellen und das Gateway löschen.

Für die Berechtigungsstufen **Verwenden** und **Verwenden + freigeben** wählen Sie die Datenquellen, mit denen der Benutzer über das Gateway eine Verbindung herstellen kann.

> [!NOTE]
> **Kann verwenden** und **kann + Freigabe** nicht für benutzerdefinierte Connectors anwenden.

## <a name="view-and-manage-gateway-connections"></a>Anzeigen und Verwalten von Gatewayverbindungen

1. Klicken oder tippen Sie unter [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) im linken Navigationsbereich auf **Gateways** und anschließend auf ein Gateway.

2. Klicken oder tippen Sie auf **Verbindungen** und anschließend auf eine Verbindung, um ihre Details anzuzeigen, die Einstellungen zu bearbeiten oder sie zu löschen.

3. Um eine Verbindung freizugeben, klicken oder tippen Sie auf **Freigeben**, und fügen Sie anschließend Benutzer hinzu oder entfernen Sie Benutzer.

    > [!NOTE]
   > Sie können nur einige Arten von Verbindungen freigeben, z.B. SQL Server. Weitere Informationen finden Sie unter [Freigeben von App-Ressourcen](share-app-resources.md).

Weitere Informationen zum Verwalten einer Verbindung finden Sie unter [Verwalten von Verbindungen](add-manage-connections.md).

## <a name="troubleshooting-and-advanced-configuration"></a>Problembehandlung und erweiterte Konfiguration

Weitere Informationen zum Beheben von Problemen mit Gateways finden Sie unter Problembehandlung [beim lokalen Daten Gateway](/data-integration/gateway/service-gateway-tshoot). Weitere Informationen zur Konfiguration finden Sie unter [Verwenden der lokalen Daten Gateway-App](/data-integration/gateway/service-gateway-app).

## <a name="next-steps"></a>Nächste Schritte

* [Installieren Sie das lokale Daten Gateway](/data-integration/gateway/service-gateway-install).
* Erstellen Sie eine App, die eine Verbindung mit einer lokalen Datenquelle herstellt, z.B. [SQL Server](connections/connection-azure-sqldatabase.md) oder [SharePoint](connections/connection-sharepoint-online.md).
* [Geben Sie eine App frei](share-app.md), die eine Verbindung mit einer lokalen Datenquelle herstellt.
