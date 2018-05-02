---
title: Hinzufügen einer Datenverbindung in einer App | Microsoft-Dokumentation
description: Fügen Sie eine Datenverbindung in einer vorhandenen App oder einer leeren App hinzu
services: ''
suite: powerapps
documentationcenter: na
author: archnair
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/06/2018
ms.author: archanan
ms.openlocfilehash: e4d2e881a058ea8f265a858f54af81674d8c1296
ms.sourcegitcommit: 4710a56d308efe67fe60a7688143e61f5e5f2b44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="add-a-data-connection-in-powerapps"></a>Hinzufügen einer Datenverbindung in PowerApps
Fügen Sie in PowerApps einer vorhandenen App oder einer von Grund auf neu erstellten App eine Datenverbindung hinzu. Ihre App kann eine Verbindung zu SharePoint, Salesforce, OneDrive oder [vielen anderen Datenquellen](connections-list.md) herstellen.

Ihr [nächster Schritt](#next-steps) nach diesem Artikel besteht darin, Daten aus dieser Datenquelle in der App anzuzeigen und zu verwalten; siehe folgende Beispiele:

* Verbinden mit OneDrive und Verwalten von Daten in einer Excel-Arbeitsmappe in Ihrer App.
* Verbinden mit Twilio und Senden einer SMS-Nachricht von Ihrer App.
* Herstellen einer Verbindung mit SQL Server und Aktualisieren einer Tabelle aus Ihrer App.

## <a name="prerequisites"></a>Voraussetzungen
[Registrieren Sie sich](../signup-for-powerapps.md) für PowerApps, und [melden Sie sich an](http://web.powerapps.com), indem Sie dieselben Anmeldeinformationen bereitstellen, die Sie bei der Registrierung angegeben haben.

## <a name="add-a-data-source"></a>Datenquelle hinzufügen
1. Zeigen Sie auf der Registerkarte **Start** auf die Kachel **Mit leerer App starten**, und klicken Sie auf **Diese App erstellen**.

    ![App von Grund auf neu erstellen](./media/add-data-connection/blank-app-tile.png)

1. Falls das Dialogfeld **Willkommen bei PowerApps Studio** angezeigt wird, klicken Sie auf **Überspringen**.

3. Klicken oder tippen Sie im mittleren Bereich auf **Mit Daten verbinden**.

4. Wenn die gewünschte Verbindung in der Liste im Bereich **Daten** aufgeführt wird, klicken Sie darauf, um sie der App hinzuzufügen. Andernfalls fahren Sie mit dem nächsten Schritt fort.

    ![Datenquelle hinzufügen](./media/add-data-connection/choose-existing-connections.png)

5. Klicken Sie auf **Neue Verbindung**, um eine Liste der Connectors anzuzeigen.

    ![Hinzufügen einer Verbindung](./media/add-data-connection/new-connection.png)

6. Scrollen Sie durch die Liste der Connectors bis zum gewünschten Verbindungstyp (z.B. **Office 365 Outlook**), und klicken Sie darauf.

    ![Auswählen der Verbindung](./media/add-data-connection/choose-connection.png)

7. Klicken Sie auf **Erstellen**, um die Verbindung zu erstellen und der App hinzuzufügen.

    Einige Connectors wie **Office 365 Outlook** erfordern keine weiteren Schritte, und Sie können sofort Daten daraus anzeigen. Andere Connectors fordern Sie auf, Anmeldeinformationen bereitzustellen, einen bestimmten Satz von Daten anzugeben oder weitere Schritte durchzuführen. In [SharePoint](connections/connection-sharepoint-online.md) und [SQL Server](connections/connection-azure-sqldatabase.md) sind z.B. zusätzliche Informationen erforderlich, bevor Sie sie verwenden können.

## <a name="add-another-data-source"></a>Hinzufügen einer anderen Datenquelle
1. Fügen Sie ein Steuerelement hinzu, dem Sie eine Datenquelle hinzufügen möchten.

    Das Steuerelement muss so wie Kataloge und Listenfelder über eine **Items**-Eigenschaft oder so wie Formulare über eine **Item**-Eigenschaft verfügen.

1. Öffnen Sie im Bereich **Daten** (wird automatisch geöffnet) die Liste unter **Datenquelle**, und klicken Sie auf **Datenquelle hinzufügen**.

1. Führen Sie die vorherige Anleitung ab Schritt 4 aus.

## <a name="identify-or-change-a-data-source"></a>Identifizieren oder Ändern einer Datenquelle
Wenn Sie eine App aktualisieren, müssen Sie möglicherweise die im Katalog angezeigte Datenquelle, ein Formular oder ein anderes Steuerelement angeben oder ändern. Beispiel: Beim Aktualisieren einer App müssen Sie eine Datenquelle identifizieren, die von jemand anderem vor Kurzem oder von Ihnen selbst vor längerer Zeit erstellt wurde.

1. Wählen Sie das Steuerelement aus, für das Sie die Datenquelle identifizieren oder ändern möchten.

    Wählen Sie z.B. einen Katalog (und kein Steuerelement im Katalog) aus, indem Sie in der hierarchischen Liste der Bildschirme und Steuerelemente am linken Rand darauf klicken oder tippen.

    Der Name der Datenquelle wird im rechten Bereich auf der Registerkarte **Eigenschaften** angezeigt.

2. Wählen Sie die Datenquelle aus, um sie zu ändern oder um weitere Informationen dazu anzuzeigen.

    ![Bereich „Daten“](./media/add-data-connection/data-pane.png)

3. Um die Datenquelle zu ändern, öffnen Sie die Liste der Datenquellen, und wählen Sie eine andere Quelle aus, oder erstellen Sie eine neue.

     ![Bereich „Daten“](./media/add-data-connection/datasource-list.png)

## <a name="next-steps"></a>Nächste Schritte
* Zum Anzeigen und Aktualisieren von Daten in einer Quelle wie Excel, SharePoint oder SQL Server [fügen Sie einen Katalog hinzu](add-gallery.md), und [fügen Sie ein Formular hinzu](add-form.md).
* Verwenden Sie für die Daten in anderen Quellen Connector-spezifische Funktionen, z.B. für [Office 365 Outlook](connections/connection-office365-outlook.md), [Twitter](connections/connection-twitter.md) und [Microsoft Translator](connections/connection-microsoft-translator.md).
