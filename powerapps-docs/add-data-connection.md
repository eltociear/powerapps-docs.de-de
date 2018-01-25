---
title: "Hinzufügen einer Datenverbindung in einer App | Microsoft-Dokumentation"
description: "Fügen Sie eine Datenverbindung in einer vorhandenen App oder einer leeren App hinzu"
services: 
suite: powerapps
documentationcenter: na
author: archnair
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/02/2017
ms.author: archanan
ms.openlocfilehash: b4377bd869e2b8879fd95d0a6729664104cd1368
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="add-a-data-connection-in-powerapps"></a>Hinzufügen einer Datenverbindung in PowerApps
Fügen Sie in PowerApps einer vorhandenen App oder einer von Grund auf neu erstellten App eine Datenverbindung hinzu. In diesem Artikel wird die Verwendung von PowerApps Studio beschrieben. Sie können jedoch auch [powerapps.com](https://web.powerapps.com) nutzen, wie im Artikel [Verwalten von Verbindungen](add-manage-connections.md) beschrieben.

Die Datenverbindung Ihrer App kann Verbindungen mit SharePoint, Salesforce, OneDrive und [vielen anderen Datenquellen](connections-list.md) herstellen.

Ihr [nächster Schritt](#next-steps) nach diesem Artikel besteht darin, Daten aus dieser Datenquelle in der App anzuzeigen und zu verwalten; siehe folgende Beispiele:

* Verbinden mit OneDrive und Verwalten von Daten in einer Excel-Arbeitsmappe in Ihrer App.
* Verbinden mit Twilio und Senden einer SMS-Nachricht von Ihrer App.
* Herstellen einer Verbindung mit SQL Server und Aktualisieren einer Tabelle aus Ihrer App.

## <a name="prerequisites"></a>Voraussetzungen
[Registrieren Sie sich](signup-for-powerapps.md) bei PowerApps, [installieren](http://aka.ms/powerappsinstall) und öffnen Sie PowerApps, und melden Sie sich mit den Anmeldeinformationen an, die Sie beim Registrieren angegeben haben.

## <a name="background-on-data-connections"></a>Hintergrundinformationen zu Datenverbindungen
Die meisten Apps in PowerApps nutzen externe Informationen, die als **Datenquellen** bezeichnet werden und in Clouddiensten gespeichert sind. Ein gängiges Beispiel ist eine Tabelle in einer Excel-Datei, die in OneDrive for Business gespeichert ist. Apps können über **Connectors** auf diese Datenquellen zugreifen.

Die geläufigsten Datenquellen sind Tabellen, die Sie zum Abrufen und Speichern von Informationen verwenden können. Mithilfe von Connectors zu Datenquellen können Sie Daten in Microsoft Excel-Arbeitsmappen, SharePoint-Listen, SQL-Tabellen und vielen anderen Formaten lesen und schreiben, die in Clouddiensten wie OneDrive for Business, DropBox, SQL Server usw. gespeichert sein können.

Andere Datenquellen als Tabellen sind E-Mail, Kalender, Twitter und Benachrichtigungen.

Mithilfe der Steuerelemente **[Katalog](controls/control-gallery.md)**, **[Anzeigeformular](controls/control-form-detail.md)** und **[Bearbeitungsformular](controls/control-form-detail.md)** ist es einfach, eine App zu erstellen, die Daten aus einer Datenquelle liest und in eine Datenquelle schreibt. Lesen Sie zunächst den Artikel [Understand data forms (Grundlegendes zu Datenformularen)](working-with-forms.md).

## <a name="add-a-connection"></a>Eine Verbindung hinzufügen
1. Klicken oder tippen Sie auf **New** im Menü **File** (am linken Rand).

    ![Option „New“ im Menü „File“](./media/add-data-connection/file-new.png)

2. Klicken oder tippen Sie in der Kachel **Leere App** auf **Telefonlayout**.

    ![App von Grund auf neu erstellen](./media/add-data-connection/blank-app.png)

3. Klicken oder tippen Sie im mittleren Bereich auf **Mit Daten verbinden**.

4. Wenn die gewünschte Verbindung in der Liste im Bereich **Daten** aufgeführt wird, klicken oder tippen Sie darauf, um sie der App hinzuzufügen. Andernfalls fahren Sie mit dem nächsten Schritt fort.

    ![Datenquelle hinzufügen](./media/add-data-connection/choose-existing-connections.png)

5. Klicken oder tippen Sie auf **Neue Verbindung**, um eine Liste der Connectors anzuzeigen.

    ![Hinzufügen einer Verbindung](./media/add-data-connection/new-connection.png)

6. Scrollen Sie durch die Liste der Connectors bis zum gewünschten Typ von Verbindung (z.B. **Office 365 Outlook**), und klicken oder tippen Sie darauf.

    ![Auswählen der Verbindung](./media/add-data-connection/choose-connection.png)

7. Klicken oder tippen Sie auf **Erstellen**, um die Verbindung zu erstellen und der App hinzuzufügen.

    Einige Connectors, z.B. **Microsoft Translator**, erfordern keine weiteren Schritte. Sie können sofort Daten von ihnen anzeigen. Andere Connectors fordern Sie auf, Anmeldeinformationen bereitzustellen, einen bestimmten Satz von Daten anzugeben oder weitere Schritte durchzuführen. In [SharePoint](connections/connection-sharepoint-online.md) und [SQL Server](connections/connection-azure-sqldatabase.md) sind z.B. zusätzliche Informationen erforderlich, bevor Sie sie verwenden können.

## <a name="view-or-change-a-data-source"></a>Anzeigen oder Ändern einer Datenquelle
Wenn Sie eine App aktualisieren, müssen Sie möglicherweise die im Katalog angezeigte Datenquelle, ein Formular oder ein anderes Steuerelement mit einer **Item**-Eigenschaft angeben oder ändern. Sie arbeiten beispielsweise mit einer App, die von einer anderen Person erstellt wurde, oder Sie möchten sich an eine Datenquelle erinnern, die Sie vor einer Weile konfiguriert haben.

1. Wählen Sie das Steuerelement aus, für das Sie die Datenquelle identifizieren möchten.

    Wählen Sie z.B. einen Katalog (und kein Steuerelement im Katalog) aus, indem Sie in der hierarchischen Liste der Bildschirme und Steuerelemente am linken Rand darauf klicken oder tippen.

    Der Name der Datenquelle wird im rechten Bereich auf der Registerkarte **Eigenschaften** angezeigt.

    ![Datenquelle auf der Registerkarte „Eigenschaften“](./media/add-data-connection/properties-tab.png)

2. Wenn Sie weitere Informationen zur Datenquelle anzeigen oder die Datenquelle ändern möchten, klicken oder tippen Sie im rechten Bereich auf **Daten**.

    ![Bereich „Daten“](./media/add-data-connection/data-pane.png)

3. Klicken oder tippen Sie zum Ändern der Datenquelle auf den nach unten weisenden Pfeil neben der Datenquelle, und wählen Sie eine andere Datenquelle aus, bzw. erstellen Sie eine andere Quelle.

## <a name="next-steps"></a>Nächste Schritte
* Zum Anzeigen und Aktualisieren von Daten in einer Quelle wie Excel, SharePoint oder SQL Server [fügen Sie einen Katalog hinzu](add-gallery.md), und [fügen Sie ein Formular hinzu](add-form.md).
* Verwenden Sie für die Daten in anderen Quellen Connector-spezifische Funktionen, z.B. für [Office 365 Outlook](connections/connection-office365-outlook.md), [Twitter](connections/connection-twitter.md) und [Microsoft Translator](connections/connection-microsoft-translator.md).
