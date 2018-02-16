---
title: Erstellen einer Common Data Service-Datenbank | Microsoft-Dokumentation
description: Erstellen Sie eine Common Data Service-Datenbank.
services: powerapps
documentationcenter: na
author: nimakms
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: 892f434d54c723d8de4ad6e9a48ced05cf23b311
ms.sourcegitcommit: e827813cd898ca9a1046b5952ea5e32ce2989a65
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="create-a-common-data-service-database"></a>Erstellen einer Common Data Service-Datenbank
Mithilfe von Common Data Service als Datenspeicher können Sie eine Datenbank erstellen und Apps entwickeln. Sie können entweder Ihre eigenen benutzerdefinierten Entitäten erstellen oder die vordefinierten Entitäten verwenden. Um eine Datenbank erstellen zu können, müssen Sie zunächst eine Umgebung erstellen oder als Administrator zu einer vorhandenen Umgebung zugewiesen werden. Darüber hinaus müssen Sie der entsprechenden Lizenz zugewiesen werden. Informationen zum Erwerb eines Plans für die Verwendung von Common Data Service finden Sie unter [Pricing Info (Preise)](pricing-billing-skus.md).

Es gibt drei Möglichkeiten zum Erstellen einer Datenbank:

* Im Admin Center
* Im Bereich **Home** (Start) von powerapps.com
* Im Bereich **Entities** (Entitäten)von powerapps.com

## <a name="create-a-database-in-the-admin-center"></a>Erstellen einer Datenbank im Admin Center
1. Klicken Sie im [Admin Center](https://admin.powerapps.com) im linken Navigationsbereich auf **Environments** (Umgebungen).
2. Wählen Sie die Umgebung aus, oder erstellen Sie bei Bedarf eine neue Umgebung.
3. Klicken Sie auf der Registerkarte **Database** (Datenbank) auf **Create a database** (Datenbank erstellen). Standardmäßig wird die Datenbank im Open-Zugriffsmodus erstellt.
4. Wenn Sie Sicherheit erzwingen möchten, wählen Sie **Restrict access** (Zugriff einschränken) aus.

## <a name="create-a-database-in-the-home-pane-of-powerappscom"></a>Erstellen einer Datenbank im Bereich „Start“ von powerapps.com
1. Klicken oder tippen Sie auf [powerapps.com](https://web.powerapps.com) im linken Navigationsbereich auf **Home**.
2. Suchen Sie im Abschnitt **Use Microsoft Common Data Service (Microsoft Common Data Service verwenden)** nach einer Schaltfläche mit dem Namen **Create database** (Datenbank erstellen) oder **Get started** (Erste Schritte). Der Name der Schaltfläche hängt von Ihrer Lizenz und den Berechtigungszuweisungen ab. Sie verfügen möglicherweise nicht über eine Berechtigung zum Erstellen einer Datenbank in der aktuellen Umgebung.

### <a name="create-database-in-current-environnmet"></a>Erstellen einer Datenbank in der aktuellen Umgebung
1. Klicken Sie auf **Create database** (Datenbank erstellen).
2. Aktivieren Sie im Dialogfeld das Kontrollkästchen **Restrict access to database** (Zugriff auf Datenbank einschränken), wenn Sie Sicherheit erzwingen möchten.
3. Klicken Sie auf **Create my database**. (Meine Datenbank erstellen)

### <a name="get-started-by-creating-a-new-environment"></a>Erste Schritte durch Erstellen einer neuen Umgebung
1. Klicken Sie auf **Get started** (Erste Schritte).
2. Klicken Sie im Dialogfeld auf **Neue Umgebung erstellen** zum Erstellen einer neuen Umgebung und Datenbank.
3. Geben Sie im Feld **Umgebungsname** einen eindeutigen Namen ein. Wählen Sie im Feld **Region** die entsprechende Region aus.
4. Aktivieren Sie das Kontrollkästchen **Restrict access to database** (Zugriff auf Datenbank einschränken), wenn Sie Sicherheit erzwingen möchten.
5. Klicken Sie auf **Erstellen**.

## <a name="create-a-database-in-the-entities-pane-of-powerappscom"></a>Erstellen einer Datenbank im Bereich „Entitäten“ von powerapps.com
1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com) den Bereich **Common Data Service**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entities** (Entitäten).
2. Klicken Sie auf **Get started** (Erste Schritte). Die Datenbank wird im Open-Zugriffsmodus erstellt.

## <a name="open-and-restricted-databases"></a>Offene und eingeschränkte Datenbanken
Standardmäßig wird eine Datenbank im Open-Zugriffsmodus erstellt. In diesem Modus wird die Sicherheit für den Zugriff auf Entitäten nicht erzwungen. Der Umgebungsadministrator kann die Datenbank auf einen beschränken Zugriffsmodus festlegen. In diesem Modus wird die Sicherheit für den Zugriff auf Entitäten basierend auf Berechtigungssätzen und -Rollen erzwungen.

1. Klicken Sie im [Admin Center](https://admin.powerapps.com) im linken Navigationsbereich auf **Umgebungen**.
2. Wählen Sie die Umgebung aus.
3. Führen Sie in der Registerkarte **Datenbank** einen der folgenden Schritte aus:
   * Wählen Sie zum Erzwingen der Sicherheit **Zugriff beschränken** aus.
   * Wählen Sie zur Deaktivierung der Sicherheit **Open access** (offener Zugriff) aus.

## <a name="license-and-security-permissions"></a>Lizenz- und Sicherheitsberechtigungen
Um eine Datenbank erstellen zu können, müssen Sie Administrator in der ausgewählten Umgebung sein, und Sie müssen der entsprechenden Lizenz zugewiesen werden. Über die Umgebung können Sie mithilfe der Registerkarte **Sicherheit** weitere Sicherheitsberechtigungen für andere Benutzer konfigurieren. Weitere Informationen finden Sie unter [Datenbanksicherheit konfigurieren](database-security.md) und [Sicherheitsmodell](https://docs.microsoft.com/common-data-service/entity-reference/security-model).

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfassen und speichern wir benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen.  Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller schaffen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und in Lücken in der Abdeckung der Standardentität des Diensts ermittelt werden, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

