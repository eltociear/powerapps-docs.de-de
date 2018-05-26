---
title: 'Schnellstart: Erstellen einer Richtlinie zur Verhinderung von Datenverlust (DLP) | Microsoft-Dokumentation'
description: In diesem Schnellstart erhalten Sie Informationen zum Erstellen einer Richtlinie zur Verhinderung von Datenverlust (DLP) in PowerApps.
author: jimholtz
ms.service: powerapps
ms.component: pa-admin
ms.topic: quickstart
ms.date: 03/30/2018
ms.author: jimh
ms.openlocfilehash: da4be42ea0374d6cb50da2f9a9b17eef15d5b316
ms.sourcegitcommit: 3f5adf07cac1c798f3d4843ed5928505becde30e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2018
---
# <a name="quickstart-create-a-data-loss-prevention-dlp-policy"></a>Schnellstart: Erstellen einer Richtlinie zur Verhinderung von Datenverlust (DLP)
Mithilfe von PowerApps können Sie zum Schutz von Unternehmensdaten Richtlinien zur Verhinderung von Datenverlust (DLP) erstellen und erzwingen, die definieren, für welche Verbraucherconnectors bestimmte Geschäftsdaten freigegeben werden können. Diese Richtlinien, die definieren, wie Daten freigegeben werden können, werden als Richtlinien zur Verhinderung von Datenverlust (DLP) bezeichnet. Mithilfe von DLP-Richtlinien wird sichergestellt, dass Daten in der gesamten Organisation auf einheitliche Weise verwaltet werden. Außerdem helfen sie zu vermeiden, dass wichtige Unternehmensdaten versehentlich auf Connectors wie Social Media-Websites veröffentlicht werden.

In diesem Schnellstart erfahren Sie, wie Sie eine DLP-Richtlinie für eine einzelne Umgebung erstellen, die verhindert, dass Daten, die in Ihren Common Data Service- und SharePoint-Datenbanken gespeichert werden, auf Twitter veröffentlicht werden.

## <a name="prerequisites"></a>Voraussetzungen
Für diesen Schnellstart ist **eines** der folgenden Elemente erforderlich:
* Azure Active Directory-Mandantenadministratorberechtigungen
* Globale Office 365-Administratorberechtigungen
* PowerApps-Umgebungsadministratorberechtigungen sowie eine Lizenz von PowerApps-Plan 2, Microsoft Flow-Tarif 2 oder eine [Testversion von PowerApps-Plan 2](https://web.powerapps.com/signup?redirect=marketing&email=)

Weitere Informationen finden Sie unter [Environments administration in PowerApps (Verwalten von Umgebungen in PowerApps)](environments-administration.md).

## <a name="sign-in-to-the-powerapps-admin-center"></a>Anmelden im PowerApps Admin Center
Melden Sie sich unter [https://admin.powerapps.com]([https://admin.powerapps.com) im Admin Center an.

## <a name="create-a-dlp-policy"></a>Erstellen einer DLP-Richtlinie
1. Klicken oder tippen Sie zuerst im Navigationsbereich auf **Datenrichtlinien** und dann auf **Neue Richtlinie**.

    ![](./media/create-dlp-policy/new-data-policy.png)
2. Das Feld **Name der Datenrichtlinie** wird automatisch mit einem Namen aufgefüllt, der auf der Uhrzeit und dem Datum der Erstellung der Richtlinie basiert. Ersetzen Sie ihn durch **Secure Data Access for Contoso** (Sicherer Datenzugriff für Contoso).

    ![](./media/create-dlp-policy/policy-name.png)
3. Die Optionen auf der Registerkarte **Umgebungen** unterscheiden sich, je nachdem, ob Sie ein Umgebungsadministrator oder ein Mandantenadministrator sind. Wenn Sie ein Umgebungsadministrator sind, wählen Sie in der Dropdownliste eine Umgebung aus, und klicken oder tippen Sie auf **Weiter**.

    ![](./media/create-dlp-policy/select-environment.png)

    Wenn Sie ein Mandantenadministrator sind, können Sie DLP-Richtlinien erstellen, die für mindestens eine Umgebung oder für alle Umgebungen im Mandanten gelten (einschließlich der Umgebungen, die mit einer Testlizenz erstellt wurden). Klicken oder tippen Sie für diesen Schnellstart auf **NUR auf ausgewählte Umgebungen anwenden**, wählen Sie eine Umgebung aus der Dropdownliste aus, und klicken oder tippen Sie dann auf **Weiter**.

    ![](./media/create-dlp-policy/select-environment-tenant.png)

    Beachten Sie, dass DLP-Richtlinien für Umgebungen mandantenweite DLP-Richtlinien nicht überschreiben können.
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
In diesem Schnellstart wurde erläutert, wie Sie eine DLP-Richtlinie für eine einzelne Umgebung erstellen, um zu verhindern, dass wichtige Unternehmensdaten versehentlich auf Connectors wie Twitter veröffentlicht werden. Mehr Informationen zu DLP-Richtlinien erhalten Sie in dem Artikel, in dem das Verwalten dieser Richtlinien beschrieben wird.

> [!div class="nextstepaction"]
> [Manage data loss prevention (DLP) policies (Verwalten von Richtlinien zur Verhinderung von Datenverlust (DLP))](prevent-data-loss.md)
