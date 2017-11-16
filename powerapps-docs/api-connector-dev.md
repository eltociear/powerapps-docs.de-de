---
title: Entwickeln eines API-Connectors | Microsoft-Dokumentation
description: Beschreiben Sie Ihre API, legen Sie den Authentifizierungstyp fest, erstellen Sie Trigger und Aktionen, und testen Sie.
services: 
suite: powerapps
documentationcenter: na
author: asavaritayal
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/06/2017
ms.author: astay
ms.openlocfilehash: 68a0be6c6be91ff5b89b3e06aecc242f987a4cf4
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="develop-an-api-connector-powerapps"></a>Entwickeln eines API-Connectors (PowerApps)
Das Erstellen eines Connectors beinhaltet mehrere Schritte. So fangen Sie an: Klicken oder tippen Sie in [PowerApps](https://web.powerapps.com/) auf die Schaltfläche **Einstellungen** (das Zahnradsymbol) oben rechts auf der Seite. Klicken oder tippen Sie dann auf **Benutzerdefinierte Connectors**.

![Suchen von API-Connectors](./media/api-connectors-dev/finding-custom-apis.png)

## <a name="describe-your-api"></a>Beschreiben der API
API-Connectors werden mithilfe des [OpenAPI-Standards](https://swagger.io/) beschrieben, um die Schnittstelle einer HTTP-API zu definieren. Sie können beim Erstellen auf einer vorhandenen OpenAPI-Datei aufbauen oder eine [Postman-Sammlung](https://www.getpostman.com/docs/collections) (Postman Collection) importieren, mit der die OpenAPI-Datei automatisch für Sie erstellt wird. 

![Definieren des API-Diagramms](./media/api-connectors-dev/build-your-api-updated.png)

Wenn Sie von einer dieser API-Beschreibungen ausgehen, werden die Metadatenfelder im Assistenten automatisch aufgefüllt. Sie können sie jederzeit bearbeiten.  

## <a name="build-security"></a>Erstellen von Sicherheit
Wählen Sie den von Ihrem Dienst unterstützten Authentifizierungstyp aus, und geben Sie zusätzliche Details an, um den entsprechenden Fluss der Identität zwischen Ihrem Dienst und sämtlichen Clients zu ermöglichen. 

![Sicherheitsdiagramm](./media/api-connectors-dev/security.png)

[Weitere Informationen](register-custom-api.md) zur Connectorsicherheit.

## <a name="build-triggers-and-actions"></a>Erstellen von Triggern und Aktionen
1. Um die Trigger und Aktionen für den Connector zu erstellen, wechseln Sie zur Registerkarte **Definition**. 
   
    ![Definitionsdiagramm](./media/api-connectors-dev/definition.png)
2. Mithilfe des Assistenten können Sie neue Operationen hinzufügen oder das Schema und die Reaktion für vorhandene bearbeiten. In den **Allgemeinen** Eigenschaften für die einzelnen Operationen können Sie das Verhalten Ihres Connectors aus der Sicht des Endbenutzers steuern. Weitere Informationen über die verschiedenen Operationsarten erhalten Sie über die Links unten:
   
   * [Trigger](https://flow.microsoft.com/documentation/customapi-webhooks) (in PowerApps nicht sichtbar)
   * [Aktionen](register-custom-api.md)
     
     Informationen zum Implementieren von erweiterten Funktionen für Microsoft Flow finden Sie unter [OpenAPI-Erweiterungen für API-Connectors](https://flow.microsoft.com/documentation/customapi-how-to-swagger/). 
3. Klicken oder tippen Sie schließlich auf **Connector erstellen**, um den API-Connector zu registrieren.

Wenden Sie sich wegen weiterer Funktionen, die nicht im Assistenten verfügbar sind, an [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com).

## <a name="test-the-connector"></a>Testen des Connectors
Testen Sie Ihren API-Connector vor der Einreichung auf eine oder mehrere Weisen: 

* Mithilfe des [Test--Assistenten](https://flow.microsoft.com/blog/new-updates-custom-api/) für API-Connectors können Sie jede Operation aufrufen, um ihre Funktionalität und das Reaktionsschema zu überprüfen.
* Im Designer für Microsoft Flow können Sie Flows mithilfe Ihres API-Connector visuell erstellen. Diese Testmethode gibt Ihnen Einblick in die Funktionalität der Benutzeroberfläche und die Funktionen Ihres Connectors.
* In PowerApps Studio können Sie jeden Vorgang mithilfe der Bearbeitungsleiste aufrufen und die Reaktion an Steuerelemente auf Ihrem Bildschirm anbinden.

Dieses Thema stellt eine Übersicht dar; weitere Informationen finden Sie unter [Registrieren und Verwenden eines benutzerdefinierten Connectors](register-custom-api.md).

