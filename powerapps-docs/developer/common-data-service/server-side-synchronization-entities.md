---
title: Serverseitige Synchronisationsentitäten (Common Data Service) | Microsoft Docs
description: Die serverseitige Synchronisation bietet eine Schnittstelle zwischen dem Common Data Service und einem oder mehreren Exchange-Servern oder POP3-Servern für eingehende E-Mails und einem oder mehreren SMTP- oder Exchange-Servern für ausgehende E-Mails.
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
---
# <a name="server-side-synchronization-entities"></a>Serverseitige Synchronisierungsentitäten

In PowerApps bietet die serverseitige Synchronisation eine Schnittstelle zwischen dem Common Data Service und einem oder mehreren Exchange-Servern oder POP3-Servern für eingehende E-Mails und einem oder mehreren SMTP- oder Exchange-Servern für ausgehende E-Mails. Es ruft E-Mails ab und wertet sie nach Relevanz für den Common Data Service aus und erstellt entsprechend entsprechende E-Mail-Aktivitäten im Common Data Service. Außerdem werden E-Mails vom Common Data Service ausgewählt und über den konfigurierten E-Mail-Server an Benutzer und Warteschlangen gesendet. Es ermöglicht auch die Synchronisierung von Terminen, Kontakten und Aufgaben mit Exchange Server 2010 und Exchange Server 2013.  
  
 Mit der zentralisierten E-Mail-Konfiguration ermöglicht das Entitätsmodell des Common Data Service die Festlegung von Einstellungen der Benutzeroberfläche (wie Benutzername, Passwort, E-Mail-Adresse und Synchronisationsmethoden) für Benutzer, Warteschlangen und Weiterleitungspostfächer. Jeder Benutzer oder eine Warteschlange kann Postfächer haben, die entweder durch serverseitige Synchronisation oder Microsoft Dynamics 365 for Outlook überwacht werden können. Die [EmailServerProfile](/powerapps/developer/common-data-service/reference/entities/emailserverprofile)-Entität stellt das E-Mail-Serverprofil einer Organisation dar. Die [Mailbox](/powerapps/developer/common-data-service/reference/entities/mailbox)-Entität stellt die Termine, Kontakten und Aufgabenzustellungsmethode des Postfachs dar. Aktuell ist die Benutzerentität auf einen Postfachdatensatz pro Benutzer beschränkt und die Warteschlangenentität ist auf einen Postfachdatensatz pro Warteschlange beschränkt, wie in der folgenden Abbildung gezeigt.  
  
 ![E-Mail-Konnektorentitätenmodell](media/email-connector-entity-model.png "E-Mail-Konnektorentitätenmodell")  
  
 Serverseitige Synchronisierung bietet die folgenden Funktionen:  
  
- Prozess-E-Mails eines Benutzers und einer Warteschlange mittels der E-Mail-Adresse, der E-Mail-Zustellungsmethode und der Anmeldeinformationen aus dem verknüpften Postfachdatensatz.  
  
- Prozesstermine, Kontakte und Aufgaben  
  
- Verwenden Sie Postfachdatensätze, um E-Mails für Benutzer und Warteschlangen zu verarbeiten, wobei die Zustellungsmethode auf Weiterleitungspostfach festgelegt wurde.  
  
- Verwenden Sie die Informationen aus einem verknüpften E-Mail-Profildatensatz, um alle E-Mails für alle Postfächer zu verarbeiten.  
  
- Verhindern Sie die Verarbeitung von E-Mails für inaktive Postfächer oder für Postfächer, die über kein zugeordnetes E-Mail-Profil verfügen.  
  
- Verknüpfen Sie ein zugeordnetes Postfach automatisch mit dem Standard-E-Mail-Profil, wenn ein Benutzer oder eine Warteschlange mit der E-Mail-Zustellungsmethode erstellt wurde, die als serverseitige Synchronisierung festgelegt wurde.  
  
- Verfolgen Sie Microsoft Exchange-E-Mails in PowerApps für einen Benutzer automatisch anhand der Regeln für die Nachverfolgung auf Ordnerebene.  
  
### <a name="related-topics"></a>Verwandte Themen  
 [Nachverfolgungsregeln auf Ordnerebene konfigurieren](configure-exchange-folder-level-tracking-rules.md) 