---
title: Hinzufügen einer Datenverbindung in einer Canvas-App | Microsoft-Dokumentation
description: Hinzufügen einer Datenverbindung in einer vorhandenen Canvas-App oder in einer leeren App
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/06/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 43832847f447a9af8a05d149b0d6f3b564b770e1
ms.sourcegitcommit: 0267e58b305f9fb0a4b32130fb149cd6e34b3354
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59993801"
---
# <a name="add-a-data-connection-to-a-canvas-app-in-powerapps"></a>Hinzufügen einer Datenverbindung in einer Canvas-App in PowerApps

Fügen Sie in PowerApps einer vorhandenen Canvas-App oder einer von Grund auf neu erstellten App eine Datenverbindung hinzu. Ihre App kann eine Verbindung zu SharePoint, Salesforce, OneDrive oder [vielen anderen Datenquellen](connections-list.md) herstellen.

Ihr [nächster Schritt](#next-steps) nach diesem Artikel besteht darin, Daten aus dieser Datenquelle in der App anzuzeigen und zu verwalten; siehe folgende Beispiele:

* Verbinden mit OneDrive und Verwalten von Daten in einer Excel-Arbeitsmappe in Ihrer App.
* Verbinden mit Twilio und Senden einer SMS-Nachricht von Ihrer App.
* Herstellen einer Verbindung mit SQL Server und Aktualisieren einer Tabelle aus Ihrer App.

## <a name="prerequisites"></a>Voraussetzungen

[Registrieren Sie sich](../signup-for-powerapps.md) für PowerApps, und [melden Sie sich an](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen bereitstellen, die Sie bei der Registrierung angegeben haben.

## <a name="open-a-blank-app"></a>Öffnen einer leeren App

1. Auf der **Startseite** Registerkarte **Canvas-app mit leerer App**.

1. Geben Sie einen Namen für Ihre app, und wählen Sie dann **erstellen**.

1. Falls das Dialogfeld **Willkommen bei PowerApps Studio** angezeigt wird, klicken Sie auf **Überspringen**.

## <a name="add-data-source"></a>Datenquelle hinzufügen

1. Wählen Sie im mittleren Bereich **Verbinden mit Daten** zum Öffnen der **Daten** Bereich.

    Wenn dies wäre eine vorhandene app und der Bildschirm bereits ein Steuerelement enthalten, wählen Sie **Ansicht** > **Datenquellen** auf den gleichen Bereich zu öffnen.

1. Wählen Sie **Datenquelle hinzufügen**.

1. Wenn die Liste der Verbindungen das enthält, die Sie möchten, wählen Sie es, um es der app hinzuzufügen. Andernfalls fahren Sie mit dem nächsten Schritt fort.

    ![Wählen Sie eine vorhandene Verbindung](./media/add-data-connection/choose-existing-connection.png)

1. Wählen Sie **neue Verbindung** eine Liste der Verbindungen angezeigt.

    ![Hinzufügen einer Verbindung](./media/add-data-connection/add-connection.png)

1. Klicken Sie in der Suchleiste Geben Sie oder fügen Sie die ersten Buchstaben der gewünschten Verbindung, und wählen Sie dann die Verbindung aus, wenn es angezeigt wird.

    ![Suchen Sie nach einer Verbindung](./media/add-data-connection/search-connections.png)

1. Klicken Sie auf **Erstellen**, um die Verbindung zu erstellen und der App hinzuzufügen.

    Einige Connectors wie **Office 365 Outlook** erfordern keine weiteren Schritte, und Sie können sofort Daten daraus anzeigen. Andere Connectors fordern Sie auf, Anmeldeinformationen bereitzustellen, einen bestimmten Satz von Daten anzugeben oder weitere Schritte durchzuführen. In [SharePoint](connections/connection-sharepoint-online.md) und [SQL Server](connections/connection-azure-sqldatabase.md) sind z.B. zusätzliche Informationen erforderlich, bevor Sie sie verwenden können.

## <a name="identify-or-change-a-data-source"></a>Identifizieren oder Ändern einer Datenquelle
Wenn Sie eine App aktualisieren, müssen Sie möglicherweise die im Katalog angezeigte Datenquelle, ein Formular oder ein anderes Steuerelement angeben oder ändern. Beispielsweise müssen Sie eine Datenquelle zu identifizieren, wie Sie einer app bereits erstellte oder aktualisieren, die Sie vor kurzem erstellt haben.

1. Wählen Sie das Steuerelement, z. B. einen Katalog, die für den Sie angeben oder die Datenquelle ändern möchten.

    Der Name der Datenquelle wird im rechten Bereich auf der Registerkarte **Eigenschaften** angezeigt.

    ![Identifizieren Sie eine Verbindung](./media/add-data-connection/identify-connection.png)

1. Wählen Sie den Pfeil nach unten neben dem Namen, um weitere Informationen zur Datenquelle anzuzeigen oder um ihn zu ändern.

    Weitere Informationen über die aktuelle Datenquelle angezeigt, und Sie können auswählen, oder erstellen Sie eine andere Quelle.

    ![Ändern einer Verbindung](./media/add-data-connection/change-connection.png)

## <a name="next-steps"></a>Nächste Schritte

* Zum Anzeigen und Aktualisieren von Daten in einer Quelle wie Excel, SharePoint oder SQL Server [fügen Sie einen Katalog hinzu](add-gallery.md), und [fügen Sie ein Formular hinzu](add-form.md).
* Verwenden Sie für die Daten in anderen Quellen Connector-spezifische Funktionen, z.B. für [Office 365 Outlook](connections/connection-office365-outlook.md), [Twitter](connections/connection-twitter.md) und [Microsoft Translator](connections/connection-microsoft-translator.md).
