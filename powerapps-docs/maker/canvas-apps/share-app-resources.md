---
title: Freigeben von in der Canvas-Apps verwendeten Ressourcen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Ressourcen freigeben, die ihre Canvas-app in Power Apps verwendet.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/03/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a1385e45fbbd932e0575c5c5b69b051dc292c824
ms.sourcegitcommit: eda3382ade50efe66611518c8f36e3a2ada7a91d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77282330"
---
# <a name="share-canvas-app-resources-in-power-apps"></a>Freigeben von Canvas-App-Ressourcen in Power apps

Beachten Sie vor dem [Freigeben einer Canvas-App](share-app.md) die Typen von Ressourcen, von denen sie abhängt. Dabei kann es sich z.B. um eine oder mehrere der folgenden handeln:

* Entitäten in Common Data Service

    (weitere Informationen darüber, wie Sie Benutzern Zugriff auf diese Daten gewähren, finden Sie unter [Verwalten von Entitätsberechtigungen](share-app.md#manage-entity-permissions))
    
* eine Verbindung mit einer Datenquelle
* ein lokales Datengateway
* ein benutzerdefinierter Connector
* eine Excel-Arbeitsmappe oder einen anderen Dienst
* einen Flow

Einige dieser Ressourcen werden automatisch freigegeben, wenn Sie die App freigeben. Andere Ressourcen erfordern, dass Sie oder die Personen, für die Sie App freigeben, zusätzliche Schritte unternehmen, damit die App erwartungsgemäß ausgeführt wird.

Sie können auch Verbindungen, benutzerdefinierte Connectors und ein lokales Datengateway für die gesamte Organisation freigeben.

## <a name="connections"></a>Verbindungen

Einige Verbindungen (z. b. SQL Server mit SQL-oder Windows-Authentifizierung) werden implizit für die APP frei [gegeben](share-app-resources.md#implicit-sharing) , wenn Sie die APP für andere Benutzer freigeben. Andere Verbindungen erfordern, dass Benutzer eigene Verbindungen erstellen (z. b. onedrive for Business oder SQL Server mit Azure AD Authentifizierung).

Sie können bestimmen, ob eine Verbindung automatisch als Teil der APP freigegeben wird, wenn Sie die APP für andere Benutzer freigeben. ermöglicht Ihnen das Aktualisieren von Freigabe Berechtigungen. Wechseln Sie zu diesem Zweck zu make.powerapps.com, und wählen Sie **Daten** -> **Verbindungen** von Links Navigation aus. Wählen Sie dann die erforderliche Verbindung aus. Wenn die Schaltfläche **Freigeben** bei der oberen Navigation angezeigt wird oder wenn die Option **Freigeben** angezeigt wird, wenn Sie *Weitere Befehle* (...) auswählen, kann die ausgewählte Verbindung für andere Benutzer freigegeben werden.

  ![Keine Freigabe für onedrive for Business](./media/share-app-resources/shared-connections-odb.png)

  ![SQL-Authentifizierungs Verbindung für SQL Server freigeben](./media/share-app-resources/shared-connections-sqlauth.png)

### <a name="implicit-sharing"></a>Implizite Freigabe

Wenn Sie eine APP freigeben, die eine Verbindung verwendet, die freigegeben werden kann, wird die APP-Verbindung implizit gemeinsam mit der APP frei **gegeben** . Beispielsweise wird die folgende Meldung angezeigt, wenn Sie zu make.powerapps.com wechseln, **apps**auswählen, eine App auswählen, die eine solche Verbindung verwendet, *Weitere Befehle* auswählen (...) und dann **Freigeben**:

  ![Warnung zur impliziten Berechtigung](./media/share-app-resources/share-app-implicit-permission.png)

Wenn Sie die ausgewählte APP **bestätigen** und für andere Benutzer freigeben auswählen, wird die APP-Verbindung implizit für diese Benutzer gemeinsam mit der APP freigegeben.

## <a name="on-premises-data-gateways"></a>Lokale Datengateways
Wenn Sie eine App erstellen und freigeben, die Daten aus einer lokalen Quelle enthält, werden das [lokale Datengateway](gateway-management.md) selbst und bestimmte Typen von Verbindungen mit diesem Gateway automatisch freigegeben. Sie können jede Verbindung, die nicht automatisch freigegeben wird, manuell freigeben (wie im vorherigen Abschnitt gezeigt) oder die Benutzer durch die App auffordern lassen, eigene Verbindungen zu erstellen. So zeigen Sie die Verbindung(en) an, mit denen ein Gateway konfiguriert wurde:

1. Öffnen Sie [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), klicken oder tippen Sie in der linken Navigationsleiste auf **Verwalten**, und klicken oder tippen Sie dann auf **Gateways**.
2. Klicken oder tippen Sie auf ein Gateway, und klicken oder tippen Sie dann auf die Registerkarte **Verbindungen**.

> [!NOTE]
> Wenn Sie eine oder mehrere Verbindungen manuell freigeben, müssen Sie diese ggf. unter den folgenden Umständen erneut freigeben:

* Sie fügen einer App, die Sie bereits freigegeben haben, ein lokales Datengateway hinzu.
* Sie ändern den Satz der Personen oder Gruppen, für die Sie eine App, die über ein lokales Datengateway verfügt, freigegeben haben.

## <a name="custom-connectors"></a>Benutzerdefinierte Connectors
Wenn Sie eine App freigeben, die einen benutzerdefinierten Connector verwendet, wird sie automatisch freigegeben, die Benutzer müssen jedoch eigene Verbindungen mit der App erstellen.

Auf [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) können Sie Berechtigungen für einen benutzerdefinierten Connector anzeigen und aktualisieren. Klicken oder tippen Sie in der linken Navigationsleiste auf **Verwalten**, klicken oder tippen Sie auf **Verbindungen**, und klicken oder tippen Sie dann auf **Neue Verbindung** (in der rechten oberen Ecke). Klicken oder tippen Sie auf **Custom** (Benutzerdefiniert), und klicken oder tippen Sie dann auf einen benutzerdefinierten Connector, um Details zu ihr anzuzeigen.

## <a name="excel-workbooks"></a>Excel-Arbeitsmappen
Wenn eine freigegebene App Daten verwendet, auf die nicht alle Benutzer Zugriff haben (z. B. eine Excel-Arbeitsmappe in einem Cloudspeicherkonto), [geben Sie die Daten frei](share-app-data.md).

## <a name="flows"></a>Flows
Wenn Sie eine App freigeben, die einen Flow enthält, werden Benutzer, die die App ausführen, aufgefordert, alle Flows zu bestätigen oder zu aktualisieren, die für den Flow erforderlich sind. Außerdem kann nur die Person, die den Flow erstellt hat, dessen Parameter anpassen. Beispielsweise können Sie einen Flow erstellen, der E-Mails an eine von Ihnen angegebene Adresse sendet, diese Adresse kann jedoch von anderen Benutzern nicht geändert werden.

