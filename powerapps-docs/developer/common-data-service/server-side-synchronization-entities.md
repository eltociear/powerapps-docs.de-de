---
title: Serverseitige Synchronisationsentitäten (Common Data Service) | Microsoft-Dokumentation
description: Serverseitige Synchronisierung bietet eine Schnittstelle zwischen Common Data Service und mindestens einem Exchange-Server oder POP3-Server für eingehende E-Mails und mindestens einem SMTP- oder Exchange-Server für ausgehende E-Mails.
ms.custom: ''
ms.date: 02/21/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: mayadu
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5c0a12acd097c477860e2f472055ec47ca259493
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2859919"
---
# <a name="server-side-synchronization-entities"></a>Serverseitige Synchronisierungsentitäten

In Power Apps bietet die serverseitige Synchronisierung eine Schnittstelle zwischen dem Common Data Service-System und mindestens einem Exchange-Server oder POP3-Server für eingehende E-Mails und mindestens einem SMTP- oder Exchange-Server für ausgehende E-Mails. Er ruft E-Mails ab und bewertet ihre Relevanz für Common Data Service und erstellt entsprechende E-Mail-Aktivitäten in Common Data Service. Er entnimmt auch E-Mails aus Common Data Service und sendet sie über den konfigurierten E-Mail-Server für Benutzer und Warteschlangen. Es ermöglicht auch die Synchronisierung von Terminen, Kontakten und Aufgaben mit Exchange Server 2010 und Exchange Server 2013.  
  
 Mit der zentralisierten E-Mail-Konfiguration ermöglicht das Common Data Service-Entitätenmodell übliche Benutzeroberflächen-Einstellungen (wie: Benutzername, Kennwort, E-Mail-Adresse und Synchronisierungsmethoden) für Benutzer, Warteschlangen und Weiterleitungspostfächer. Jeder Benutzer oder jede Warteschlange kann über Postfächer verfügen, die mit Hilfe von serverseitiger Synchronisierung oder Microsoft Dynamics 365 for Outlook überwacht werden können. Die [EmailServerProfile](/powerapps/developer/common-data-service/reference/entities/emailserverprofile)-Entität stellt das E-Mail-Serverprofil einer Organisation dar. Die [Mailbox](/powerapps/developer/common-data-service/reference/entities/mailbox)-Entität stellt die Termine, Kontakten und Aufgabenzustellungsmethode des Postfachs dar. Aktuell ist die Benutzerentität auf einen Postfachdatensatz pro Benutzer beschränkt und die Warteschlangenentität ist auf einen Postfachdatensatz pro Warteschlange beschränkt, wie in der folgenden Abbildung gezeigt.  
  
 ![E-Mail-Konnektorentitätenmodell](media/email-connector-entity-model.png "E-Mail-Konnektorentitätenmodell")  
  
 Serverseitige Synchronisierung bietet die folgenden Funktionen:  
  
- Prozess-E-Mails eines Benutzers und einer Warteschlange mittels der E-Mail-Adresse, der E-Mail-Zustellungsmethode und der Anmeldeinformationen aus dem verknüpften Postfachdatensatz.  
  
- Prozesstermine, Kontakte und Aufgaben  
  
- Verwenden Sie Postfachdatensätze, um E-Mails für Benutzer und Warteschlangen zu verarbeiten, wobei die Zustellungsmethode auf Weiterleitungspostfach festgelegt wurde.  
  
- Verwenden Sie die Informationen aus einem verknüpften E-Mail-Profildatensatz, um alle E-Mails für alle Postfächer zu verarbeiten.  
  
- Verhindern Sie die Verarbeitung von E-Mails für inaktive Postfächer oder für Postfächer, die über kein zugeordnetes E-Mail-Profil verfügen.  
  
- Verknüpfen Sie ein zugeordnetes Postfach automatisch mit dem Standard-E-Mail-Profil, wenn ein Benutzer oder eine Warteschlange mit der E-Mail-Zustellungsmethode erstellt wurde, die als serverseitige Synchronisierung festgelegt wurde.  
  
- Verfolgen Sie Microsoft Exchange-E-Mails in Power Apps für einen Benutzer automatisch anhand der Regeln für die Nachverfolgung auf Ordnerebene.  
  
### <a name="related-topics"></a>Verwandte Themen  
 [Nachverfolgungsregeln auf Ordnerebene konfigurieren](configure-exchange-folder-level-tracking-rules.md) 