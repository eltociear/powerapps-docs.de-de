---
title: Verwendung eines lokalen Daten-Gateways in Power Platform Dataflows | MicrosoftDocs
description: Erfahren Sie, wie Sie ein lokales Daten-Gateway in Power Platform Dataflows verwenden.
ms.custom: ''
ms.date: 08/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4a47f082520b4680c9045209f85c26beb3586875
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752236"
---
# <a name="using-an-on-premises-data-gateway-in-power-platform-dataflows"></a>Verwendung eines lokalen Daten-Gateways in Power Platform Dataflows
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Installieren Sie ein lokales Daten-Gateway, um Daten schnell und sicher zwischen einem Power Platform-Dataflow und einer Datenquelle zu übertragen, die sich nicht in der Cloud befindet, wie beispielsweise eine lokale SQL-Server-Datenbank oder eine lokale SharePoint-Site.
Sie können alle Gateways anzeigen, für die Sie Administratorrechte haben, und Berechtigungen und Verbindungen für diese Gateways verwalten.

Mit einem Gateway können Sie sich über diese Verbindungen mit lokalen Daten verbinden:

-   SharePoint

-   SQL Server

-   Oracle

-   Informix

-   Dateisystem

-   DB2

## <a name="prerequisites"></a>Voraussetzungen

-   Ein PowerApps-Konto. Sie haben keins? [Melden Sie sich für 30 Tage kostenlos an](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps).

-   Administrative Berechtigungen auf einem Gateway. Diese Berechtigungen werden standardmäßig für von Ihnen installierte Gateways bereitgestellt. Administratoren können anderen Personen Berechtigungen für Gateways erteilen. 

-   Eine Lizenz, die den Zugriff auf lokale Daten über ein lokales Gateway unterstützt. Weitere Informationen finden Sie im Abschnitt "Verbinden mit Ihren Daten und Systemen" des Abschnitts [Finden Sie die richtige PowerApps Planseite](https://powerapps.microsoft.com/pricing/).

-   Gateways und lokale Verbindungen können nur in der Standardumgebung des Benutzers erstellt und verwendet werden. Mehr Informationen: [Arbeiten mit Umgebungen und Microsoft PowerApps](../canvas-apps/working-with-environments.md).

## <a name="install-a-gateway"></a>Ein Gateway installieren
1.  Wählen Sie im linken Navigationsbereich von [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) **Gateways**.

    ![Gateways in der linken Navigationsleiste](media/nav-pane-gateways.png)

2.  Wählen Sie ein Gateway aus der Liste aus. Wenn Sie keine Administratorrechte für ein Gateway haben, wählen Sie [Installieren Sie ein Gateway jetzt](https://go.microsoft.com/fwlink/?LinkID=820931), und folgen Sie dann den Anweisungen des Assistenten.

     ![Gateways installieren](media/install-gateway-now.png)

     Weitere Informationen zur Installation eines Gateways finden Sie unter [Wissenswertes über lokale Daten-Gateways](../canvas-apps/gateway-reference.md).

## <a name="use-an-on-premises-data-source-in-a-dataflow"></a>Verwenden einer lokalen Datenquelle in einem Dataflow
1. Wählen Sie eine lokale Datenquelle aus der Liste der Datenquellen aus.

   ![Auswahl einer lokalen Datenquelle](media/on-premises-data-sources.png)

2. Geben Sie die Verbindungsdetails für das Unternehmensgateway an, das für den Zugriff auf die lokalen Daten verwendet wird. Sie müssen das Gateway selbst auswählen und Anmeldeinformationen für das ausgewählte Gateway bereitstellen. In der Liste erscheinen nur Gateways, für die Sie ein Administrator sind.

    ![Geben Sie die Verbindungsdaten an](media/connection-creds.png)

Sie können das für einen bestimmten Dataflow verwendete Unternehmensgateway und das allen Ihren Abfragen zugeordnete Gateway mit dem Autorentool für Dataflow ändern.

> [!NOTE]
> Der Dataflow versucht, die benötigten Datenquellen mit dem neuen Gateway zu finden oder zu erstellen. Wenn dies nicht möglich ist, können Sie das Gateway nicht ändern, bis alle benötigten Dataflows vom ausgewählten Gateway verfügbar sind.


## <a name="view-and-manage-gateway-permissions"></a>Anzeigen und Verwalten von Gateway-Berechtigungen
1.  Wählen Sie im linken Navigationsbereich von [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) **Gateways** und wählen Sie dann das gewünschte Gateway aus.

2.  Um einen Benutzer zu einem Gateway hinzuzufügen, wählen Sie **Benutzer**, geben Sie einen Benutzer oder eine Gruppe an und geben Sie dann eine Berechtigungsstufe an:

    -   **Nutzung möglich.** Benutzer mit dieser Berechtigung können Verbindungen auf dem Gateway erstellen, um sie für Anwendungen und Abläufe zu verwenden, können das Gateway aber nicht gemeinsam nutzen. Verwenden Sie diese Berechtigung für Benutzer, die Apps ausführen, aber nicht freigeben.

    -   **Nutzung + Freigabe möglich.** Benutzer mit dieser Berechtigung können eine Verbindung auf dem Gateway erstellen, die für Anwendungen und Abläufe verwendet werden soll, und das Gateway automatisch freigeben, wenn sie eine Anwendung freigeben. Verwenden Sie diese Berechtigung für Benutzer, die Anwendungen mit anderen Benutzern oder mit dem Unternehmen teilen müssen.

    -   **Admin.** Administratoren haben die volle Kontrolle über das Gateway, einschließlich dem Hinzufügen von Benutzern, dem Setzen von Berechtigungen, dem Erstellen von Verbindungen zu allen verfügbaren Datenquellen und dem Löschen des Gateways.

      Wählen Sie für die Berechtigungsstufen **Nutzung möglich** und **Nutzung + Freigabe möglich** die Datenquellen aus, mit denen sich der Benutzer über das Gateway verbinden kann.

## <a name="view-and-manage-gateway-connections"></a>Anzeigen und Verwalten von Gateway-Verbindungen
1.  Wählen Sie in der linken Navigationsleiste von *powerapps.com* **Gateways**, und wählen Sie dann das gewünschte Gateway.

2.  Führen Sie die gewünschte Aktion aus: 
    - Um Details anzuzeigen, die Einstellungen zu bearbeiten oder ein Gateway zu löschen, wählen Sie **Verbindungen** und dann eine Verbindung aus.
    - Um eine Verbindung freizugeben, wählen Sie **Freigeben** und fügen Sie dann Benutzer hinzu oder entfernen Sie sie.

      > [!NOTE]
      > Sie können nur bestimmte Arten von Verbindungen freigeben, z.B. eine SQL-Server-Verbindung. Weitere Informationen finden Sie unter [Canvas-App-Ressourcen in PowerApps freigeben](../canvas-apps/share-app-resources.md). <br />
      >
      > Weitere Informationen zum Verwalten einer Verbindung finden Sie unter [Verwalten von Canvas-App-Verbindungen unter PowerApps](../canvas-apps/add-manage-connections.md).


## <a name="limitations"></a>Einschränkungen
Es gibt einige bekannte Einschränkungen bei der Verwendung von Enterprise Gateways und Dataflows.

-   Jeder Dataflow kann nur ein Gateway verwenden. Daher sollten alle Abfragen über das gleiche Gateway konfiguriert werden.

-   Eine Änderung des Gateways wirkt sich auf den gesamten Dataflow aus.

-   Wenn mehrere Gateways benötigt werden, ist es am besten, mehrere Dataflows zu erstellen (einen für jedes Gateway) und die Rechen- oder Entitätsreferenzfunktionen zur Vereinheitlichung der Daten zu nutzen.

-   Dataflows werden nur über Enterprise Gateways unterstützt. Persönliche Gateways stehen in den Dropdown-Listen und Einstellungsbildschirmen nicht zur Auswahl.

Informationen zur Fehlerbehebung bei Problemen mit Gateways oder zur Konfiguration des Gateway-Dienstes für Ihr Netzwerk finden Sie unter [Verstehen von lokalen Daten-Gateways](../canvas-apps/gateway-reference.md).

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen und Verwenden von Dataflows in PowerApps](create-and-use-dataflows.md)

- [Daten zu einer Entität in Common Data Service hinzufügen, indem Sie Power Query verwenden](data-platform-cds-newentity-pq.md)

- [Verbinden von Azure Data Lake Storage Gen2 für Dataflow-Speicher](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)


