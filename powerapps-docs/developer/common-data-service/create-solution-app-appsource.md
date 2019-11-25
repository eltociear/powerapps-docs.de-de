---
title: 'Schritt 3: Erstellen einer verwalteten Lösung für Ihre App (Common Data Service) | Microsoft-Dokumentation'
description: Lernen Sie, wie Sie eine verwaltete Lösung erstellen, sodass die App alle Komponenten einschließt. Dies ist für das Veröffentlichen einer serverseitigen Synchronisierung Appsource erforderlich.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8115e17ef999834e2134ef41c2a8472bf539438b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748424"
---
# <a name="step-3-create-a-managed-solution-for-your-app"></a>Schritt 3: Erstellen einer verwalteten Lösung für die App

Erstellen Sie eine verwaltete Lösung, sodass die App alle Komponenten einschließt. Sie finden möglicherweise diese Themen hilfreich, während Sie eine verwaltete Lösung planen und erstellen, um die App-Komponenten zu integrieren:
- [Einführung in Lösungen](introduction-solutions.md)
- [Planen einer Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development) 
- [Eine verwaltete Lösung erstellen, installieren und aktualisieren](create-install-update-managed-solution.md)

## <a name="display-name-and-description-of-your-solution"></a>Anzeigename und Beschreibung der Lösung

Beim Erstellen einer Lösung, um die App-Komponenten zu integrieren, stellen Sie sicher, dass die entsprechenden Werte in den Feldern **Anzeigename** und **Beschreibung** für die neue Lösung bereitgestellt werden, die Sie dann den Kunden anzeigen möchten.

![Erstellen einer Lösung](media/appsource-new-solution.png)

Die Werte **Anzeigename** und **Beschreibung** für eine Lösung werden Kunden im Portal **Dynamics 365 Administration Center** angezeigt.

![Lösungen](media/appsource-solution-names.png)

## <a name="supporting-data-for-your-solution"></a>Sichern von Daten für die Lösung

Wenn die Lösung Demodaten oder Support erfordert:
1. Erstellen von Unterstützungs-/Demodaten in der Testumgebung.
2. Verwenden Sie das [Konfigurationsmigrations-Tool](/dynamics365/customer-engagement/admin/manage-configuration-data), um ein Schema für die Support-/Demodaten zu erstellen. 
3. Speichern Sie die Schemadatei, damit Sie sie später erneut verwenden können, um die Daten zu aktualisieren, wenn Ihre Demodaten ändern.
4. Sie können das Schema später verwenden, um die Daten zu exportieren. Stellen Sie sicher, dass Sie einen beschreibenden Namen in der Exportdatei angeben. Die Menübanddaten werden als komprimierte Datei exportiert.

Ausführliche Informationen zum Erstellen von Berichten mithilfe des Configuration Migration tool, um ein Schema zu erstellen und die Daten exportieren zu können, finden Sie unter [Erstellen Sie ein Schema, um Konfigurationsdaten zu exportieren](/dynamics365/customer-engagement/admin/create-schema-export-configuration-data)

## <a name="at-the-end-of-this-step"></a>Am Ende dieses Schritts

Sie haben eine Lösungsdatei (Beispiel: *SampleSolution.zip*) und optional eine Demodatendatei (Beispiel: *SampleData.zip*) für die App.


> [!div class="nextstepaction"]
> [Step 4: Erstellen eines AppSource-Pakets für die App](create-package-app-appsource.md) 
  