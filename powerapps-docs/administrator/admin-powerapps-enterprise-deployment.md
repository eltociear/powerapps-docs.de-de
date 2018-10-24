---
title: Verwalten einer PowerApps Enterprise-Bereitstellung | Microsoft-Dokumentation
description: Lesen Sie das Whitepaper zum Verwalten einer PowerApps Enterprise-Bereitstellung.
ms.custom: ''
ms.date: 08/09/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 83200632-a36b-4401-ba41-952e5b43f939
caps.latest.revision: 31
author: jimholtz
ms.author: jimholtz
manager: kvivek
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: ce8daad960834c2965e2a5432ccaf2a3f515e503
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42857492"
---
# <a name="administering-a-powerapps-enterprise-deployment"></a>Verwalten einer PowerApps Enterprise-Bereitstellung

PowerApps ist eine produktive Anwendungsentwicklungsplattform von Microsoft.  Microsoft verwendet die Plattform, um die eigenen Anwendungen für Dynamics 365 for Sales, Service, Field Service, Marketing und Talent zu erstellen.  Dies bedeutet, dass die Anwendungen nativ auf der Plattform erstellt werden.   Enterprise-Kunden können auch eigene benutzerdefinierte Branchenanwendungen mithilfe der Technologie erstellen.  Einzelne Benutzer und Teams in Ihrer Organisation können auch Anwendungen für die persönliche oder die Teamproduktivität mit keinem oder geringem Programmieraufwand erstellen. 

Laden Sie das zugehörige Whitepaper herunter: [Verwalten einer PowerApps Enterprise-Bereitstellung](https://aka.ms/powerappsadminwhitepaper)

Das Whitepaper wendet sich an den Unternehmensanwendungsadministrator, der für die Planung, den Schutz, die Bereitstellung und die Unterstützung von Anwendungen verantwortlich ist, die auf der PowerApps-Plattform erstellt wurden.  Das Whitepaper soll die Bestandteile Ihrer Umgebung veranschaulichen und aufzeigen, wie Sie proaktiv für Anwendungen planen, die entwickelt und bereitgestellt werden, und wie Sie die täglichen administrativen Aufgaben zum Verwalten von Bereitstellungen durchführen können.
In diesem Whitepaper werden zentrale Konzepte, die Plattformarchitektur und notwendige Entscheidungen behandelt.  Nach Möglichkeit helfen wir Ihnen bei der Entwicklung von Best Practices für Ihre Organisation aus, um erfolgreiche Bereitstellungen und hohe Produktivität für die Benutzer sicherzustellen, die die Plattform verwenden.

Die PowerApps-Plattform ist Teil der größeren Microsoft Power-Plattform, zu der auch die Power BI und Microsoft Flow gehören, die die allgemeine Infrastruktur von Common Data Service für Apps und Datenconnectors nutzen. Diese Funktionen basieren auf und nutzen die Microsoft Azure Cloud Services.  Auf der PowerApps-Plattform erstellte Anwendungen können auch Azure Cloud Services für die Skalierung von Anwendungen für die individuelle Produktivität bis hin zu unternehmenskritischen Branchenanwendungen enthalten.

![Microsoft Power-Plattform](media/ms-power-platform.png "Microsoft Power-Plattform")
