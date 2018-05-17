---
title: Erstellen einer Common Data Service-Datenbank (CDS) für Apps | Microsoft-Dokumentation
description: Exemplarische Vorgehensweise zur Erstellung einer Common Data Service-Datenbank (CDS) für Apps
services: powerapps
author: manasmams
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: manasma
ms.openlocfilehash: 3343e8cd81e23d4938466d12ddca2e0a85dc12c8
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2018
---
# <a name="create-a-common-data-service-for-apps-database"></a>Erstellen einer Common Data Service-Datenbank für Apps
Mithilfe von Common Data Service für Apps als Datenspeicher können Sie eine Datenbank erstellen und Apps entwickeln. Sie können entweder Ihre eigenen benutzerdefinierten Entitäten erstellen oder die vordefinierten Entitäten verwenden. Um eine Datenbank erstellen zu können, müssen Sie zunächst eine Umgebung erstellen oder einer bereits vorhandenen Umgebung als **Umgebungsadministrator** zugewiesen sein. Darüber hinaus müssen Sie der entsprechenden Lizenz zugewiesen werden. Informationen zum Erwerb eines Plans für die Verwendung von CDS für Apps finden Sie unter [Pricing Info (Preise)](pricing-billing-skus.md).

Es gibt verschiedene Möglichkeiten zum Erstellen einer Datenbank:

* Im PowerApps Admin Center
* Im Bereich **Entities** (Entitäten)von powerapps.com

## <a name="create-a-database-in-the-admin-center"></a>Erstellen einer Datenbank im Admin Center
1. Klicken Sie im [Admin Center](https://admin.powerapps.com) im linken Navigationsbereich auf **Environments** (Umgebungen).
    
2. Wählen Sie die Umgebung aus, in der Sie die Datenbank erstellen möchten.
    
    ![](./media/create-database/environment-list-new.png)

3. Klicken Sie auf der Registerkarte **Details** auf **Datenbank erstellen**. 
    
    ![](./media/create-database/Create-DB-From-Details.png)

4. Wählen Sie die richtige Währung und Sprache aus, um mit der Datenbankerstellung fortzufahren. 
    
    ![](./media/create-database/DB-Choose-options.png)



## <a name="create-a-database-in-the-entities-pane-of-powerapps"></a>Erstellen einer Datenbank im Bereich „Entitäten“ von PowerApps
1. Erweitern Sie unter [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.

2. Klicken Sie auf **Datenbank erstellen**, um die Datenbank zu erstellen.

    ![](./media/create-database/Create-DB-From-Entities.png)

> [!NOTE]
> Derzeit ist es nicht möglich, eine Datenbank außerhalb Ihrer Azure AD-Region zu erstellen. Sie werden bald in einer anderen Region als Ihrer eigenen Azure AD-Region eine Datenbank erstellen können, aber stellen Sie vorläufig sicher, dass Sie eine Datenbank in einer Umgebung erstellen, deren Region mit Ihrer eigenen Azure AD-Region identisch ist.

## <a name="security-model-for-the-databases"></a>Sicherheitsmodell für die Datenbanken
Wenn eine Datenbank erstellt wird, können die Benutzer, denen Umgebungsrollen zugewiesen sind, weiterhin diese Berechtigungen verwalten.  
    Benutzern mit der Rolle **Umgebungsadministrator** ist jetzt die Rolle **Systemadministrator** zugewiesen. Benutzer mit der Rolle **Umgebungsersteller** behalten diese Rolle.

Sie können vordefinierten Rollen zusätzliche Benutzer zuweisen oder sogar [benutzerdefinierte Rollen][1] erstellen. Weitere Informationen finden Sie unter [Database Security (Datenbanksicherheit)](database-security.md).

> [!NOTE]
> Sobald die Datenbank erstellt wurde, werden sämtliche Sicherheitsgruppen, die dem Umgebungsadministrator oder der Umgebungserstellerrolle zugewiesen sind, nicht mehr berücksichtigt. Derzeit werden AAD-Sicherheitsgruppen beim Zuweisen von Berechtigungen in Datenbanken nicht unterstützt.


## <a name="license-and-security-permissions"></a>Lizenz- und Sicherheitsberechtigungen
Um eine Datenbank erstellen zu können, müssen Sie Administrator in der ausgewählten Umgebung sein, und Sie müssen der entsprechenden Lizenz zugewiesen werden. Über die Umgebung können Sie mithilfe der Registerkarte **Sicherheit** weitere Sicherheitsberechtigungen für andere Benutzer konfigurieren. Weitere Informationen finden Sie unter [Datenbanksicherheit konfigurieren](database-security.md) und [Sicherheitsmodell](https://docs.microsoft.c../maker/common-data-service/entity-reference/security-model).

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfassen und speichern wir benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen.  Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller schaffen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und in Lücken in der Abdeckung der Standardentität des Diensts ermittelt werden, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.


<!--Reference links in article-->
[1]: https://technet.microsoft.com/library/dn531130.aspx
