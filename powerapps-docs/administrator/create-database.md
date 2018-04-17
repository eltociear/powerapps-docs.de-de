---
title: Erstellen einer Common Data Service-Datenbank | Microsoft-Dokumentation
description: Erstellen Sie eine Common Data Service-Datenbank.
services: powerapps
documentationcenter: na
author: manasmams
manager: kfend
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: manasma
ms.openlocfilehash: 2215d02af78d0983292cfca8c9f8ac4f6737a3d0
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="create-a-common-data-service-database"></a>Erstellen einer Common Data Service-Datenbank
Mithilfe von Common Data Service als Datenspeicher können Sie eine Datenbank erstellen und Apps entwickeln. Sie können entweder Ihre eigenen benutzerdefinierten Entitäten erstellen oder die vordefinierten Entitäten verwenden. Um eine Datenbank erstellen zu können, müssen Sie zunächst eine Umgebung erstellen oder einer bereits vorhandenen Umgebung als **Umgebungsadministrator** zugewiesen sein. Darüber hinaus müssen Sie der entsprechenden Lizenz zugewiesen werden. Informationen zum Erwerb eines Plans für die Verwendung von Common Data Service finden Sie unter [Pricing Info (Preise)](pricing-billing-skus.md).

Es gibt drei Möglichkeiten zum Erstellen einer Datenbank:

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



## <a name="create-a-database-in-the-entities-pane-of-powerappscom"></a>Erstellen einer Datenbank im Bereich „Entitäten“ von powerapps.com
1. Erweitern Sie unter [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.

2. Klicken Sie auf **Datenbank erstellen**, um die Datenbank zu erstellen.

    ![](./media/create-database/Create-DB-From-Entities.png)


## <a name="security-model-for-the-databases"></a>Sicherheitsmodell für die Datenbanken
Wenn eine Datenbank erstellt wird, können die Benutzer, denen Umgebungsrollen zugewiesen sind, weiterhin diese Berechtigungen verwalten.  
    Benutzern mit der Rolle **Umgebungsadministrator** ist jetzt die Rolle **Systemadministrator** zugewiesen. Benutzer mit der Rolle **Umgebungsersteller** behalten diese Rolle.

Sie können vordefinierten Rollen zusätzliche Benutzer zuweisen oder sogar [benutzerdefinierte Rollen][1] erstellen. Weitere Informationen finden Sie unter [Database Security (Datenbanksicherheit)](create-database.md).

> [!NOTE]
> Sobald die Datenbank erstellt wurde, werden sämtliche Sicherheitsgruppen, die dem Umgebungsadministrator oder der Umgebungserstellerrolle zugewiesen sind, nicht mehr berücksichtigt. Derzeit werden AAD-Sicherheitsgruppen beim Zuweisen von Berechtigungen in Datenbanken nicht unterstützt.


## <a name="license-and-security-permissions"></a>Lizenz- und Sicherheitsberechtigungen
Um eine Datenbank erstellen zu können, müssen Sie Administrator in der ausgewählten Umgebung sein, und Sie müssen der entsprechenden Lizenz zugewiesen werden. Über die Umgebung können Sie mithilfe der Registerkarte **Sicherheit** weitere Sicherheitsberechtigungen für andere Benutzer konfigurieren. Weitere Informationen finden Sie unter [Datenbanksicherheit konfigurieren](database-security.md) und [Sicherheitsmodell](https://docs.microsoft.c../maker/common-data-service/entity-reference/security-model).

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfassen und speichern wir benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen.  Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller schaffen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und in Lücken in der Abdeckung der Standardentität des Diensts ermittelt werden, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.


<!--Reference links in article-->
[1]: https://technet.microsoft.com/library/dn531130.aspx