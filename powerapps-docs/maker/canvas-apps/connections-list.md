---
title: Übersicht über Connectors für Canvas-Apps | Microsoft-Dokumentation
description: Übersicht über alle verfügbaren Connectors, die Sie verwenden können, um Canvas-Apps zu erstellen
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/10/2019
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d78ce9b571ed925e68747f2307d59f5f143e13eb
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78403420"
---
# <a name="overview-of-canvas-app-connectors-for-power-apps"></a>Übersicht über Canvas-App-Connectors für Power apps
Die Daten sind der Kern der meisten apps, einschließlich derjenigen, die Sie in Power Apps erstellen. Daten werden in einer *Datenquelle* gespeichert, und Sie übergeben diese Daten an Ihre App, indem Sie eine *Verbindung* erstellen. Die Verbindung verwendet einen bestimmten *Connector* für die Kommunikation mit der Datenquelle. Powerapps verfügt über Connectors für viele beliebte Dienste und lokale Datenquellen, einschließlich SharePoint, SQL Server, Office 365, Salesforce und Twitter. Informationen zu den ersten Schritten beim Hinzufügen von Daten zu einer Canvas-App finden Sie unter [Hinzufügen einer Datenverbindung in powerapps](add-data-connection.md).

Ein Connector kann **Tabellen** mit Daten oder **Aktionen** bereitstellen. Einige Connectors stellen nur Tabellen bereit, einige nur Aktionen, einige beides. Bei Ihrem Connector kann es sich außerdem um einen standardmäßigen oder einen benutzerdefinierten Connector handeln.

## <a name="tables"></a>Tabellen

Wenn Ihr Connector Tabellen bereitstellt, fügen Sie Ihre Datenquelle hinzu und wählen dann die Tabelle in der Datenquelle aus, die Sie verwalten möchten. Mit Power apps werden Tabellendaten in Ihre APP abgerufen und Daten in Ihrer Datenquelle für Sie aktualisiert. Sie können z.B. eine Datenquelle hinzufügen, die eine Tabelle namens **Lessons** enthält, und dann in der Formularleiste die **Items**-Eigenschaft eines Steuerelements, etwa einen Katalog oder ein Formular, auf diesen Wert festlegen:

 ![Items-Eigenschaft für Quelle mit einfachen Daten](./media/connections-list/ItemPropertyPlain.png)

Sie können die Daten angeben, die Ihre APP abruft, indem Sie die **Items** -Eigenschaft des Steuer Elements anpassen, das Ihre Daten anzeigt. Als Fortführung des vorherigen Beispiels können Sie die Daten in der Tabelle **Lessons** sortieren oder filtern, indem Sie diesen Namen als Argument für die Funktionen **Search** und **SortByColumn** verwenden. In dieser Abbildung wird durch die Formel, auf die die **Items**-Eigenschaft festgelegt ist, angegeben, dass die Daten basierend auf dem Text in **TextSearchBox1** sortiert und gefiltert werden sollen. 

 ![Items-Eigenschaft für Quelle mit erweiterten Daten](./media/connections-list/ItemPropertyExpanded.png)

Weitere Informationen zum Anpassen der Formel mit Tabellen finden Sie in den folgenden Themen:

  [Grundlegendes zu Datenquellen in Power apps](working-with-data-sources.md)<br> 
  [Generieren einer App aus Excel-Daten](get-started-create-from-data.md)<br> 
  [App von Grund auf neu erstellen](get-started-create-from-blank.md)<br>
  [Grundlegendes zu Tabellen und Datensätzen in powerapps](working-with-tables.md)

  > [!NOTE]
  > Zum Herstellen einer Verbindung mit Daten in einer Excel-Arbeitsmappe muss die Arbeitsmappe in einem Cloudspeicherdienst wie OneDrive gehostet werden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit cloudspeicher aus Power apps](connections/cloud-storage-blob-connections.md).

## <a name="actions"></a>Aktionen

Wenn Ihr Connector Aktionen bereitstellt, müssen Sie trotzdem weiterhin wie oben die Datenquelle auswählen. Sie wählen allerdings als nächsten Schritt keine Tabelle aus, sondern stellen manuell eine Verbindung zwischen einem Steuerelement und einer Aktion her, indem Sie die **Items**-Eigenschaft des Steuerelements bearbeiten, das Ihre Daten anzeigen soll. Die Formel, auf die Sie die **Items**-Eigenschaft festlegen, gibt die Aktion an, die Daten abruft. Die App ruft beispielsweise keine Daten ab, wenn Sie eine Verbindung mit Yammer herstellen und dann die **Items**-Eigenschaft auf den Namen der Datenquelle festlegen. Um ein Steuerelement mit Daten aufzufüllen, geben Sie eine Aktion an, wie z.B. **GetMessagesInGroup(5033622).messages**.

![Items-Eigenschaft für Datenquelle für Aktionen](./media/connections-list/ItemPropertyAction.png)

Wenn Sie benutzerdefinierte Datenupdates für Aktionsconnectors verarbeiten müssen, erstellen Sie eine Formel, die die **Patch**-Funktion enthält. Geben Sie in der Formel die Aktion und die Felder an, die Sie an die Aktion binden.  

Weitere Informationen zum Anpassen der Formel für benutzerdefinierte Updates finden Sie in den folgenden Themen:

[Patch](functions/function-patch.md)<br>[Collect](functions/function-clear-collect-clearcollect.md)<br>[Update](functions/function-update-updateif.md)

> [!NOTE]
>  **Powerapps funktioniert nicht mit dynamischem Schema**. Der Ausdruck Dynamic Schema bezieht sich auf die Möglichkeit, dass dieselbe Aktion eine andere Tabelle mit unterschiedlichen Spalten zurückgeben kann. Bedingungen, die dazu führen können, dass sich die Spalten in den Tabellen unterscheiden, sind u. a. die Aktions Eingabeparameter, der Benutzer oder die Rolle, der die Aktion ausführt, und die Gruppe, in der der Benutzer arbeitet. Beispielsweise können SQL Server gespeicherten Prozeduren andere Spalten zurückgeben, wenn Sie mit unterschiedlichen Eingaben ausgeführt werden. Für Aktionen mit dynamischem Schema zeigt die Connector-Dokumentation an, dass **die Ausgaben dieses Vorgangs dynamisch sind.** als Rückgabewert. Im Gegensatz dazu funktioniert die Energie Automatisierung mit dynamischem Schema und bietet möglicherweise eine Problem Umgehung für Ihr Szenario.

## <a name="popular-connectors"></a>Gängige Connectors

Diese Tabelle enthält Links zu weiteren Informationen zu den am häufigsten verwendeten Connectors. Eine vollständige Liste der Connectors finden Sie unter [Alle Connectors](https://docs.microsoft.com/connectors/).

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](connections/connection-common-data-service.md) |&nbsp; |![Cloud-Speicher](./media/connections-list/onedrive.png) |[**Cloud-Speicher**](connections/cloud-storage-blob-connections.md) ** |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; | ![Dynamics AX](./media/connections-list/dynamics-ax.png) |[**Dynamics AX**](connections/connection-dynamicsax.md) |
|![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |&nbsp; |![Microsoft Translator](./media/connections-list/microsoft-translator.png) |[**Microsoft Translator**](connections/connection-microsoft-translator.md) |
|![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |&nbsp; | ![Office 365-Benutzer](./media/connections-list/office365.png) |[**Office 365-Benutzer**](connections/connection-office365-users.md) |
| ![Oracle](./media/connections-list/oracle-icon.png) |[**Orakel**](connections/connection-oracledb.md) |&nbsp; | ![Power BI](./media/connections-list/powerbi.png) |[**Power BI**](connections/connection-powerbi.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; | ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) 
|![Twitter](./media/connections-list/twitter.png) |[**Twitter**](connections/connection-twitter.md)

\* * Gilt für Azure-BLOB, Box, Dropbox, Google Drive, onedrive und onedrive for Business

## <a name="standard-and-custom-connectors"></a>Standardmäßige und benutzerdefinierte Connectors
Powerapps bietet *Standardconnectors* für viele häufig verwendete Datenquellen, z. b. die oben aufgeführten Datenquellen. Wenn Power Apps über einen Standardconnector für den Typ der Datenquelle verfügt, den Sie verwenden möchten, sollten Sie diesen Connector verwenden. Wenn Sie eine Verbindung mit anderen Arten von Datenquellen herstellen möchten, z.B. mit einem von Ihnen erstellten Dienst, finden Sie weitere Informationen unter [Registrieren und Verwenden von benutzerdefinierten Connectors](../canvas-apps/register-custom-api.md).

## <a name="all-standard-connectors"></a>Alle Standardconnectors
Eine vollständige Liste aller Standardconnectors finden Sie in der [Microsoft-Referenz zu Connectors](https://docs.microsoft.com/connectors/). Premium-Connectors erfordern den Plan "powerapps pro App-Plan" oder "Power apps pro Benutzer". Weitere Informationen finden Sie unter [powerapps-Pläne](https://powerapps.microsoft.com/pricing/).

Sie können Fragen zu einem bestimmten Connector in den [Power apps-Foren](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)stellen, und Sie können Connectors vorschlagen, um in den [Ideen von Power apps](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas)weitere Verbesserungen vorzunehmen.

## <a name="security-and-types-of-authentication"></a>Sicherheit und Authentifizierungs Typen

Wenn Sie Ihre APP erstellen und eine Verbindung mit einer Datenquelle herstellen, sehen Sie möglicherweise, dass Sie mit Ihrer Connector-Auswahl verschiedene Authentifizierungsmöglichkeiten verwenden können. Beispielsweise können Sie mit dem SQL Server-Connector Azure AD integrierte, SQL Server Authentifizierung und Windows-Authentifizierung verwenden. Jedem Authentifizierungstyp sind unterschiedliche Sicherheitsstufen zugeordnet.  Es ist wichtig zu verstehen, welche Informationen und Rechte Sie für Benutzer freigeben, die Ihre Anwendung verwenden. Das primäre Beispiel in diesem Artikel ist SQL Server, aber die Prinzipien gelten für alle Verbindungstypen.

### <a name="azure-ad-integrated"></a>Azure AD integriert

Dies ist ein sicherer Verbindungstyp.  Beispielsweise verwendet SharePoint diesen Authentifizierungstyp.  SQL Server ermöglicht auch diesen Authentifizierungstyp.  Wenn Sie eine Verbindung herstellen, identifiziert der Azure AD-Dienst Sie getrennt von SharePoint in Ihrem Namen.  Sie müssen keinen Benutzernamen oder ein Kennwort angeben.  Als Autor können Sie die Datenquelle mit Ihren Anmelde Informationen erstellen und mit Ihnen arbeiten.  Wenn Sie Ihre Anwendung veröffentlichen und sich der Anwendungs Benutzer anmeldet, wird dies mit Ihren Anmelde Informationen durchführen. Wenn die Daten auf einem Back-End ordnungsgemäß gesichert werden, können Ihre Benutzer auf der Grundlage Ihrer Anmelde Informationen nur anzeigen, welche Berechtigungen Ihnen zur Verfügung stehen.   Diese Art von Sicherheit ermöglicht es Ihnen, die Rechte für bestimmte Anwendungs Benutzer in der Back-End-Datenquelle zu ändern, nachdem die Anwendung veröffentlicht wurde.  Beispielsweise können Sie Zugriff gewähren, Zugriff verweigern oder verfeinern, was ein Benutzer oder eine Gruppe von Benutzern in der Back-End-Datenquelle sehen kann.

### <a name="open-standard-authorization-oauth"></a>Open-Standard-Autorisierung (OAuth)

Diese Art von Verbindung ist ebenfalls sicher.  Beispielsweise verwendet Twitter diesen Authentifizierungstyp.  Wenn Sie eine Verbindung herstellen, müssen Sie Ihren Benutzernamen und Ihr Kennwort angeben.  Als Autor können Sie die Datenquelle mit Ihren Anmelde Informationen erstellen und mit Ihnen arbeiten.  Wenn Sie Ihre Anwendung veröffentlichen und sich der Anwendungs Benutzer anmeldet, müssen Sie auch Ihre Anmelde Informationen angeben.  Daher ist dieser Verbindungstyp sicher, da die Benutzer ihre eigenen Anmelde Informationen verwenden müssen, um auf den Datenquellen Dienst zuzugreifen. 

### <a name="sql-user-name-and-password-authentication"></a>SQL-Benutzername-und Kenn Wort Authentifizierung

Diese Art von Verbindung ist nicht sehr sicher, da Sie nicht von der Authentifizierung durch Endbenutzer abhängig ist.  SQL Server ermöglicht auch diesen Authentifizierungstyp.  In SQL Server dieser Authentifizierungstyp als **SQL Server Authentifizierung**bezeichnet.  Viele andere Datenquellen der-Datenbank bieten eine ähnliche Funktion.  Wenn Sie Ihre Anwendung veröffentlichen, müssen die Benutzer keinen eindeutigen Benutzernamen und kein Kennwort angeben.  Sie verwenden den Benutzernamen und das Kennwort, die Sie beim Erstellen der Anwendung angeben.  Die Verbindungs Authentifizierung für die Datenquelle wird **implizit** für die Benutzer freigegeben.  Nachdem die Anwendung veröffentlicht wurde, wird die Verbindung auch veröffentlicht und für Ihre Benutzer verfügbar.  Ihre Endbenutzer können auch Anwendungen mithilfe einer beliebigen Verbindung erstellen, indem Sie SQL Server Authentifizierung verwenden, die für Sie freigegeben ist.  Die Benutzer können den Benutzernamen des Kennworts nicht sehen, aber die Verbindung ist für Sie verfügbar.  Es gibt sicherlich gültige Szenarien für diese Art von Verbindung.  Wenn Sie beispielsweise über eine schreibgeschützte Datenbank verfügen, die für alle Benutzer im Unternehmen verfügbar ist, ist dieser Verbindungstyp möglicherweise gültig. 

### <a name="windows-authentication"></a>Windows-Authentifizierung

Diese Art von Verbindung ist nicht sehr sicher, da Sie sich auch nicht auf die Authentifizierung durch Endbenutzer verlassen muss.  Wenn Sie eine **Verbindung mit einer**lokalen Datenquelle herstellen müssen, verwenden Sie die Windows-Authentifizierung.  Ein Beispiel für diese Art von Verbindung ist ein lokaler Server, der über eine SQL Server verfügt.  Die Verbindung muss über ein Gateway durchlaufen werden.  Da es ein Gateway durchläuft, hat der Connector Zugriff auf alle Daten in der Datenquelle. Daher stehen alle Informationen, auf die Sie mit den von Ihnen bereitgestellten Windows-Anmelde Informationen zugreifen können, dem Connector zur Verfügung. Nachdem die Anwendung veröffentlicht wurde, wird die Verbindung auch veröffentlicht und für Ihre Benutzer verfügbar.   Dies bedeutet, dass Ihre Endbenutzer auch Anwendungen erstellen können, die dieselbe Verbindung verwenden, und auf die Daten auf diesem Computer zugreifen.  Verbindungen mit der Datenquelle werden auch **implizit** für die Benutzer freigegeben, für die die APP freigegeben ist.  Diese Art von Verbindung ist möglicherweise gültig, wenn Ihre Datenquelle nur auf einem lokalen Server gespeichert ist und die Daten auf dieser Quelle frei freiwillig sind.
