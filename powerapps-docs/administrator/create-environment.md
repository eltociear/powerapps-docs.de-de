---
title: Erstellen einer Umgebung | Microsoft-Dokumentation
description: In diesem Schnellstart erhalten Sie Informationen zum Erstellen einer Umgebung.
author: jimholtz
ms.service: powerapps
ms.component: pa-admin
ms.topic: quickstart
ms.date: 03/21/2018
ms.author: jimholtz
ms.openlocfilehash: eefcd30e4f5e6ec7441147c157cbb46864ebf718
ms.sourcegitcommit: 2e7b621066cdc3e7be329d5213ecfee0b4223641
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2018
ms.locfileid: "39349246"
---
# <a name="create-an-environment"></a>Erstellen einer Umgebung
Eine Umgebung ist ein Bereich zum Speichern, Verwalten und Freigeben der Geschäftsdaten, Apps und Flows Ihres Unternehmens. Sie dient außerdem als Container zum Trennen von Apps, die unterschiedliche Rollen oder Sicherheitsanforderungen aufweisen oder sich an verschiedene Zielgruppen richten. Für jeden Mandanten erstellt PowerApps automatisch eine Standardumgebung, die von allen Benutzern dieses Mandanten gemeinsam verwendet wird.

Jede Umgebung kann über eine Common Data Service-Datenbank verfügen, die Speicher für Ihre Apps bereitstellt. Wenn Benutzer eine App in einer Umgebung erstellen, kann diese App eine Verbindung mit jeder beliebigen Datenquelle herstellen, einschließlich Gateways und Flows. Die App darf jedoch nur Verbindungen mit den Common Data Service-Datenbanken in derselben Umgebung herstellen. In welcher Weise Sie Umgebungen nutzen, hängt von Ihrer Organisation und den Apps ab, die Sie erstellen möchten. Weitere Informationen finden Sie unter [Übersicht zu Umgebungen](environments-overview.md).

In diesem Artikel erfahren Sie, wie Sie eine Umgebung sowie eine Datenbank für diese Umgebung erstellen.

## <a name="prerequisites"></a>Voraussetzungen
 Folgendes ist für die Ausführung der in diesem Artikel beschriebenen Vorgehensweise erforderlich:
 * Entweder eine Lizenz von PowerApps-Plan 2 oder von Microsoft Flow-Tarif 2. Sie können sich alternativ auch für eine [kostenlose Testversion von PowerApps-Plan 2](https://web.powerapps.com/signup?redirect=marketing&email=) registrieren.
 * PowerApps-Umgebungsadministratorberechtigungen, globale Office 365-Administratorberechtigungen oder Azure Active Directory-Mandantenadministratorberechtigungen. Weitere Informationen finden Sie unter [Environments administration in PowerApps (Verwalten von Umgebungen in PowerApps)](environments-administration.md).

## <a name="sign-in-to-the-powerapps-admin-center"></a>Anmelden im PowerApps Admin Center
Melden Sie sich unter [https://admin.powerapps.com](https://admin.powerapps.com) im Admin Center an.

## <a name="create-an-environment-and-database"></a>Erstellen einer Umgebung und einer Datenbank
1. Klicken oder tippen Sie im Navigationsbereich erst auf **Umgebungen** und anschließend auf **Neue Umgebung**.

    ![Datei > Freigeben](./media/create-environment/new-environment.png)
2. Geben Sie im Dialogfeld **Neue Umgebung** einen Namen für die Umgebung ein, und wählen Sie aus den Dropdownlisten eine Region und einen Umgebungstypen aus. Die Region ist zwar standardmäßig auf die Region des Azure Active Directory-Mandanten eingestellt, Sie können jedoch auch eine beliebige andere Region aus der Dropdownliste auswählen. Nachdem die Umgebung erstellt wurde, können Sie die Region nicht mehr ändern. Wenn Sie fertig sind, klicken oder tippen Sie auf **Umgebung erstellen**.

    ![Datei > Freigeben](./media/create-environment/new-environment-dialog.png)
3. Sobald die Umgebung erstellt wurde, erhalten Sie in einem Dialogfeld eine Bestätigungsmeldung, und Sie werden aufgefordert, eine Datenbank zu erstellen. Klicken oder tippen Sie auf **Datenbank erstellen**, um den Zugriff auf Common Data Service zu gewähren.

    **Hinweis:** Derzeit können Sie nur in der Region des Azure Active Directory-Mandanten eine Datenbank erstellen.

    ![Datei > Freigeben](./media/create-environment/create-database-dialog.png)
4. Wählen Sie für die in der Datenbank gespeicherten Daten eine Währung und eine Sprache aus. Nachdem die Datenbank erstellt wurde, können Sie die Währung und die Sprache nicht mehr ändern. Wenn Sie fertig sind, klicken oder tippen Sie auf **Datenbank erstellen**.

    ![Datei > Freigeben](./media/create-environment/create-database-dialog2.png)

    Es kann einige Minuten dauern, bis die Datenbank in Common Data Service erstellt wird. Sobald die Datenbank erstellt wurde, wird die neue Umgebung auf der Seite **Umgebungen** in der Liste mit den Umgebungen angezeigt.

    ![Datei > Freigeben](./media/create-environment/new-environment-created.png)

    Klicken oder tippen Sie auf die Umgebung, um die Umgebungsinformationen abzurufen.

## <a name="next-steps"></a>Nächste Schritte
In diesem Artikel haben Sie gelernt, wie Sie eine Umgebung sowie eine Datenbank für diese Umgebung erstellen. Als Nächstes erhalten Sie Informationen zum Verwalten von Umgebungen in Ihrer Organisation.

> [!div class="nextstepaction"]
> [Administer environments in PowerApps (Verwalten von Umgebungen in PowerApps)](environments-administration.md)
