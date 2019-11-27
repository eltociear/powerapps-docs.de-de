---
title: Herstellen einer Verbindung mit einer Oracle-Datenbank | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit einer Oracle-Datenbank herstellen und damit Apps in PowerApps erstellen.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/14/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: df9ad0aead9681d3458d70f44f929c15c073f35a
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73897807"
---
# <a name="connect-to-an-oracle-database-from-powerapps"></a>Herstellen einer Verbindung mit einer Oracle-Datenbank aus PowerApps
Nachdem Sie eine Verbindung mit einer Oracle-Datenbank hergestellt und eine App in PowerApps erstellt haben, können Sie Tabellen in der Oracle-Datenbank auflisten und Tabellenzeilen erstellen, lesen und aktualisieren. Die Verbindung mit der Oracle-Datenbank unterstützt die vollständige Delegierung von Filtern, Sortieren und weiteren Funktionen, jedoch keine Trigger und gespeicherten Prozeduren.

## <a name="prerequisites"></a>Voraussetzungen
* Oracle 9 und höher
* Oracle-Clientsoftware, Version 8.1.7 und höher
* Installation eines lokalen Datengateways
* Installation des Oracle-Client-SDK

### <a name="install-an-on-premises-data-gateway"></a>Installation eines lokalen Datengateways
Führen Sie zum Installieren eines Gateways die Schritte in [diesem Tutorial](../gateway-management.md) aus.

Ein lokales Daten Gateway fungiert als Brücke und bietet eine schnelle und sichere Datenübertragung zwischen lokalen Daten (Daten, die nicht in der Cloud sind) und den Power BI-, Energie automatisierten, Logic apps und powerapps-Diensten. Sie können dasselbe Gateway für mehrere Dienste und mehrere Datenquellen verwenden. Weitere Informationen finden Sie unter [Grundlegendes zu Gateways](../gateway-reference.md).

### <a name="install-oracle-client"></a>Installieren des Oracle-Clients
Installieren Sie auf dem Computer, auf dem sich das lokale Datengateway befindet, Oracle Data Access Components (ODAC) [64-Bit-ODAC 12c-Version 4 (12.1.0.2.4) für Windows x64](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html). Andernfalls wird ein Fehler angezeigt, wenn Sie versuchen, die Verbindung zu erstellen oder zu verwenden, wie in der Liste bekannter Probleme beschrieben.

## <a name="create-an-app-from-a-table-in-an-oracle-database"></a>Erstellen einer App aus einer Tabelle in einer Oracle-Datenbank
1. Klicken oder tippen Sie in PowerApps Studio im Menü **Datei** auf **Neu** (nahe dem linken Rand).
   
   ![Neue Option](./media/connection-oracledb/new-app.png)
2. Klicken oder tippen Sie auf den Pfeil unter **Mit eigenen Daten beginnen**.
   
      Eine Liste der bereits vorhandenen Verbindungen wird angezeigt.
3. Klicken oder tippen Sie auf **Neue Verbindung**.
   
   ![Neue Verbindung](./media/connection-oracledb/new-connection.png)
4. Klicken oder tippen Sie in der Liste der Verbindungen auf **Oracle Database**.
   
   ![Neue Datenbank](./media/connection-oracledb/oracle-db.png)
5. Geben Sie den Namen eines Oracle-Servers, einen Benutzernamen und ein Kennwort ein.
   
    Geben Sie einen Server im folgenden Format ein, wenn eine SID erforderlich ist:<br>
    *Servername*/*SID*
   
   ![Verbindungsparameter](./media/connection-oracledb/connection-params.png)
6. Klicken oder tippen Sie auf das Gateway, das Sie verwenden möchten, oder installieren Sie ein Gateway.
   
    Wenn Ihr Gateway nach der Installation nicht angezeigt wird, klicken Sie auf **Gatewayliste aktualisieren**.
   
   ![Neues Gateway](./media/connection-oracledb/choose-gateway.png)
7. Klicken oder tippen Sie auf **Erstellen**, um die Verbindung zu erstellen.
   
   ![Neu](./media/connection-oracledb/create-button.png)
8. Klicken oder tippen Sie auf das Dataset **Standard**.
   
   ![Neu](./media/connection-oracledb/choose-dataset.png)
9. Klicken oder tippen Sie in der Liste der Tabellen auf die Tabelle, die Sie verwenden möchten.
   
   ![Neu](./media/connection-oracledb/choose-table.png)
10. Klicken Sie auf **Verbinden**, um die App zu erstellen.
    
    ![Neu](./media/connection-oracledb/connect-button.png)

Es wird eine App erstellt, die drei Bildschirme enthält und in der Daten aus der von Ihnen ausgewählten Tabelle angezeigt werden:

* **BrowseScreen1** – Dort werden alle Einträge in der Tabelle aufgelistet.
* **DetailScreen1** – Bietet weitere Informationen über einen einzelnen Eintrag.
* **EditScreen1** – Dort können Benutzer einen Eintrag aktualisieren oder erstellen.

![Neu](./media/connection-oracledb/afd-app.png)

## <a name="next-steps"></a>Nächste Schritte
* Zum Speichern der App, die Sie gerade erstellt haben, drücken Sie STRG+S.
* Informationen zum Anpassen von **BrowseScreen1** (standardmäßig angezeigt) finden Sie unter [Anpassen eines Layouts](../customize-layout-sharepoint.md).
* Informationen zum Anpassen von **DetailsScreen1** oder **EditScreen1** finden Sie unter [Anpassen von Formularen](../customize-forms-sharepoint.md).

## <a name="known-issues-tips-and-troubleshooting"></a>Bekannte Probleme, Tipps und Problembehandlung
1. Das Gateway ist nicht erreichbar.
   
    Dieser Fehler wird angezeigt, wenn das lokale Datengateway keine Verbindung mit der Cloud herstellen kann. Um den Status des Gateways zu überprüfen, melden Sie sich bei „powerapps.microsoft.com“ an, klicken oder tippen Sie auf **Gateways**, und klicken oder tippen Sie auf das Gateway, das Sie verwenden möchten.
   
    Stellen Sie sicher, dass das Gateway ausgeführt wird und eine Verbindung mit dem Internet herstellen kann. Installieren Sie das Gateway nicht auf einem Computer, der möglicherweise ausgeschaltet oder in den Energiesparmodus versetzt wird. Möglicherweise können Sie das Problem auch durch einen Neustart des lokalen Datengatewaydiensts (PBIEgwService) beheben.
2. System.Data.OracleClient erfordert Version 8.1.7 oder höher der Oracle-Clientsoftware.
   
    Dieser Fehler wird angezeigt, wenn das Oracle-Client-SDK nicht auf demselben Computer wie das lokale Datengateway installiert ist. Um das Problem zu beheben, [installieren Sie die Software vom offiziellen Anbieter](https://go.microsoft.com/fwlink/p/?LinkID=272376).
3. Für die Tabelle „[Tabellenname]“ sind keine Schlüsselspalten definiert.
   
    Dieser Fehler wird angezeigt, wenn Sie eine Verbindung mit einer Tabelle herstellen, die keinen Primärschlüssel enthält. Dieser ist für die Verbindung mit der Oracle-Datenbank erforderlich.
4. Zum Zeitpunkt der Erstellung dieses Dokuments werden gespeicherte Prozeduren, Tabellen mit zusammengesetzten Schlüsseln und geschachtelte Objekttypen in Tabellen nicht unterstützt.

