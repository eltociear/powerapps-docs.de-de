---
title: Freigeben von in der Canvas-Apps verwendeten Ressourcen | Microsoft-Dokumentation
description: So geben Sie Ressourcen frei, die Ihre Canvas-App in PowerApps verwendet
author: archnair
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/28/2016
ms.author: archanan
ms.openlocfilehash: 881a0eb85d252131d6249c171c95c0711e4887d4
ms.sourcegitcommit: e3f5a2bef64085d02aec82e62ff94ae8a4d01d24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39471395"
---
# <a name="share-canvas-app-resources-in-powerapps"></a>Freigeben von Canvas-App-Ressourcen in PowerApps

Beachten Sie vor dem [Freigeben einer Canvas-App](share-app.md) die Typen von Ressourcen, von denen sie abhängt. Dabei kann es sich z.B. um eine oder mehrere der folgenden handeln:

* eine Verbindung mit einer Datenquelle
* ein lokales Datengateway
* ein benutzerdefinierter Connector
* eine Excel-Arbeitsmappe oder einen anderen Dienst
* einen Flow

Einige dieser Ressourcen werden automatisch freigegeben, wenn Sie die App freigeben. Andere Ressourcen erfordern, dass Sie oder die Personen, für die Sie App freigeben, zusätzliche Schritte unternehmen, damit die App erwartungsgemäß ausgeführt wird.

Sie können auch Verbindungen, benutzerdefinierte Connectors und ein lokales Datengateway für die gesamte Organisation freigeben.

## <a name="connections"></a>Verbindungen

Einige Typen von Verbindungen, z. B. SQL Server, werden automatisch freigegeben. Andere erfordern jedoch, dass Benutzer eigene Verbindungen mit der Datenquelle oder den Datenquellen in der App erstellen.

Auf [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) können Sie bestimmen, ob eine Verbindung automatisch freigegeben wird, und Sie können Freigabeberechtigungen aktualisieren. Klicken oder tippen Sie in der linken Navigationsleiste auf **Verwalten**, und klicken oder tippen Sie anschließend auf **Verbindungen**. Wenn die Registerkarte **Freigabe** angezeigt wird, wird die Verbindung automatisch freigegeben.

  ![Registerkarte „Freigeben“ auf der Seite für Verbindungsdetails](./media/share-app-resources/shared-connections.png)

## <a name="on-premises-data-gateways"></a>Lokale Datengateways
Wenn Sie eine App erstellen und freigeben, die Daten aus einer lokalen Quelle enthält, werden das [lokale Datengateway](gateway-management.md) selbst und bestimmte Typen von Verbindungen mit diesem Gateway automatisch freigegeben. Sie können jede Verbindung, die nicht automatisch freigegeben wird, manuell freigeben (wie im vorherigen Abschnitt gezeigt) oder die Benutzer durch die App auffordern lassen, eigene Verbindungen zu erstellen. So zeigen Sie die Verbindung(en) an, mit denen ein Gateway konfiguriert wurde:

1. Öffnen Sie [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), klicken oder tippen Sie in der linken Navigationsleiste auf **Verwalten**, und klicken oder tippen Sie dann auf **Gateways**.
2. Klicken oder tippen Sie auf ein Gateway, und klicken oder tippen Sie dann auf die Registerkarte **Verbindungen**.

> [!NOTE]
> Wenn Sie eine oder mehrere Verbindungen manuell freigeben, müssen Sie diese ggf. unter den folgenden Umständen erneut freigeben:

* Sie fügen einer App, die Sie bereits freigegeben haben, ein lokales Datengateway hinzu.
* Sie ändern den Satz der Personen oder Gruppen, für die Sie eine App, die über ein lokales Datengateway verfügt, freigegeben haben.

## <a name="custom-connectors"></a>Benutzerdefinierte Connectors
Wenn Sie eine App freigeben, die einen benutzerdefinierten Connector verwendet, wird sie automatisch freigegeben, die Benutzer müssen jedoch eigene Verbindungen mit der App erstellen.

Auf [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) können Sie Berechtigungen für einen benutzerdefinierten Connector anzeigen und aktualisieren. Klicken oder tippen Sie in der linken Navigationsleiste auf **Verwalten**, klicken oder tippen Sie auf **Verbindungen**, und klicken oder tippen Sie dann auf **Neue Verbindung** (in der rechten oberen Ecke). Klicken oder tippen Sie auf **Custom** (Benutzerdefiniert), und klicken oder tippen Sie dann auf einen benutzerdefinierten Connector, um Details zu ihr anzuzeigen.

## <a name="excel-workbooks"></a>Excel-Arbeitsmappen
Wenn eine freigegebene App Daten verwendet, auf die nicht alle Benutzer Zugriff haben (z. B. eine Excel-Arbeitsmappe in einem Cloudspeicherkonto), [geben Sie die Daten frei](share-app-data.md).

## <a name="flows"></a>Flows
Wenn Sie eine App freigeben, die einen Flow enthält, werden Benutzer, die die App ausführen, aufgefordert, alle Flows zu bestätigen oder zu aktualisieren, die für den Flow erforderlich sind. Außerdem kann nur die Person, die den Flow erstellt hat, dessen Parameter anpassen. Beispielsweise können Sie einen Flow erstellen, der E-Mails an eine von Ihnen angegebene Adresse sendet, diese Adresse kann jedoch von anderen Benutzern nicht geändert werden.

