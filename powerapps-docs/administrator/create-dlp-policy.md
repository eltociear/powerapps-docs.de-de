---
title: 'Schnellstart: Erstellen einer Richtlinie zur Verhinderung von Datenverlust (DLP) | Microsoft-Dokumentation'
description: In diesem Schnellstart erhalten Sie Informationen zum Erstellen einer Richtlinie zur Verhinderung von Datenverlust (DLP) in PowerApps.
services: powerapps
suite: powerapps
documentationcenter: na
author: SKjerland
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: quickstart
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: sharik
ms.openlocfilehash: 651510bbe4ed71dbdb267ebee04e10ea13d36e15
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-create-a-data-loss-prevention-dlp-policy"></a>Schnellstart: Erstellen einer Richtlinie zur Verhinderung von Datenverlust (DLP)
Mithilfe von PowerApps können Sie zum Schutz von Unternehmensdaten Richtlinien zur Verhinderung von Datenverlust (DLP) erstellen und erzwingen, die definieren, für welche Verbraucherconnectors bestimmte Geschäftsdaten freigegeben werden können. Diese Richtlinien, die definieren, wie Daten freigegeben werden können, werden als Richtlinien zur Verhinderung von Datenverlust (DLP) bezeichnet. Mithilfe von DLP-Richtlinien wird sichergestellt, dass Daten in der gesamten Organisation auf einheitliche Weise verwaltet werden. Außerdem helfen sie zu vermeiden, dass wichtige Unternehmensdaten versehentlich auf Connectors wie Social Media-Websites veröffentlicht werden.

In diesem Schnellstart erfahren Sie, wie Sie eine DLP-Richtlinie erstellen, die verhindert, dass Daten, die in Ihren Common Data Service- und SharePoint-Datenbanken gespeichert werden, auf Twitter veröffentlicht werden.

## <a name="prerequisites"></a>Voraussetzungen
Für diesen Schnellstart sind die folgenden Elemente erforderlich:
* PowerApps-Plan 2 oder Flow-Tarif 2 Sie können sich alternativ auch für eine [kostenlose Testversion von PowerApps-Plan 2](https://web.powerapps.com/signup?redirect=marketing&email=) registrieren.
* PowerApps-Umgebungsadministratorberechtigungen oder Azure Active Directory-Mandantenadministratorberechtigungen sowie Berechtigungen für mindestens eine Umgebung. Weitere Informationen finden Sie unter [Environments administration in PowerApps (Verwalten von Umgebungen in PowerApps)](environments-administration.md).

## <a name="sign-in-to-the-powerapps-admin-center"></a>Anmelden im PowerApps Admin Center
Melden Sie sich unter [https://admin.powerapps.com]([https://admin.powerapps.com) im Admin Center an.

## <a name="create-a-dlp-policy"></a>Erstellen einer DLP-Richtlinie
1. Klicken oder tippen Sie zuerst im Navigationsbereich auf **Datenrichtlinien** und dann auf **Neue Richtlinie**.

    ![](./media/create-dlp-policy/new-data-policy.png)
2. Geben Sie als Namen für die Datenrichtlinien **Secure Data Access for Contoso** (Sicherer Datenzugriff für Contoso) ein.
3. Wählen Sie in der Registerkarte **Umgebungen** eine Umgebung aus der Dropdownliste aus, und klicken oder tippen Sie auf **Weiter**.

    ![](./media/create-dlp-policy/select-environment.png)
4. Klicken oder tippen Sie auf der Registerkarte **Datengruppen** unter **Business data only** (Nur Geschäftsdaten) auf **Hinzufügen**.

    ![](./media/create-dlp-policy/data-groups.png)
5. Klicken Sie im Fenster **Connectors hinzufügen** auf **Common Data Service** und **SharePoint**, und klicken oder tippen Sie anschließend auf **Connectors hinzufügen**, um die Connectors der Datengruppe **Business data only** (Nur Geschäftsdaten) hinzuzufügen.

    ![](./media/create-dlp-policy/add-connectors.png)

    Connectors können sich nicht in mehreren Datengruppen gleichzeitig befinden und werden standardmäßig zu der Gruppe **No business data allowed** (Keine Geschäftsdaten zugelassen) hinzugefügt. Wenn Sie Common Data Service und SharePoint der Gruppe **Business data only** (Nur Geschäftsdaten) hinzufügen, können Benutzer keine Flows und Apps mehr erstellen, die diese beiden Connectors mit einem beliebigen anderen Connector in der Gruppe **No business data allowed** (Keine Geschäftsdaten zugelassen) verbinden.
6. Klicken Sie auf **Richtlinie speichern**.

    ![](./media/create-dlp-policy/save-policy.png)

Dann wird die Richtlinie „Sicherer Datenzugriff für Contoso“ erstellt und in der Liste der DLP-Richtlinien angezeigt. Da sich der Twitter-Connector in der Datengruppe **No business data allowed** (Keine Geschäftsdaten zugelassen) befindet, wird durch diese Richtlinie sichergestellt, dass Common Data Service und SharePoint ihre Daten nicht für Twitter freigeben.

Administratoren geben häufig ihre Listen mit DLP-Richtlinien für Ihre Organisationen frei, damit Benutzer die Richtlinien beim Erstellen von Apps berücksichtigen können.

## <a name="next-steps"></a>Nächste Schritte
In diesem Schnellstart wurde erläutert, wie Sie eine DLP-Richtlinie erstellen können, um zu verhindern, dass wichtige Unternehmensdaten versehentlich auf Connectors wie Twitter veröffentlicht werden. Mehr Informationen zu DLP-Richtlinien erhalten Sie in dem Artikel, in dem das Verwalten dieser Richtlinien beschrieben wird.

> [!div class="nextstepaction"]
> [Manage data loss prevention (DLP) policies (Verwalten von Richtlinien zur Verhinderung von Datenverlust (DLP))](prevent-data-loss.md)
