---
title: Kalender-Entitäten (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie, wie Sie Daten für Kundenservice- und Feiertagskalender mit den Kalenderentitäten speichern können.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="calendar-entities"></a>Kalenderentitäten

Der Kalenderentität speichert Daten für Kundenservicekalender und Feiertagskalender zusätzlich zum Unternehmen. Jeder Kalender wird für eine bestimmte Zeitzone festgelegt.  
  
 Ein Kalender beschreibt die Verfügbarkeit eines Service oder einer Ressource. Kalender sind mit `calendarrule`-Datensätzen verknüpft, die Details über die Dauer, die Start- und Endzeiten und wiederkehrende Muster von Ereignissen im Kalender enthalten.  
  
 Es gibt zwei Typen von Kalenderregeln im Common Data Service:  
  
- **Stamm**: Eine Kalenderregel, die einen inneren Kalender enthält oder geschachtelte (Blatt-) Regeln umfasst. Sie können einen inneren Kalender für eine Stammkalenderregel angeben, indem Sie das `CalendarRule.InnerCalendarId`-Attribut verwenden. Der Attributwert `CalendarRule.InnerCalendarId` einer Stammregel ist mit dem Attributwert `CalendarRule.CalendarId` der zugehörigen Blattregeln identisch.  
  
- **Blatt**: Eine Kalenderregel, die keinen inneren Kalender enthält und daher das Ende der "Verzweigung" darstellt.  
  
 Kalenderregeln werden geordnet, oder eingestuft, um ihre Rangfolge zu beschreiben, und Regeln können sich überschneiden. Die geschachtelte Regelerweiterung definiert die Dauer, oder den Umfang, einer Regel. Sie können das `CalendarRule.ExtentCode`-Attribut verwenden, um zu definieren, wie eine Regelerweiterungsüberschneidung behandelt wird, beispielsweise, ob sowohl die Dauer als auch der Umfang einer Regel gezeigt wird oder ob nur eins davon enthalten ist. Diese Funktionen ermöglichen Serienmuster, beispielsweise verschiedene Schichtzeitpläne für Winter- und Sommermonate, in einem einzigen Servicekalender.  
  
 Ein Kalender kann eine komplexe Struktur von Regeln und geschachtelten Kalendern sein, die eine Zusammenfassung des Arbeitsplans auf hoher Ebene darstellt. Die Kalenderentität unterstützt die <xref:Microsoft.Crm.Sdk.Messages.ExpandCalendarRequest>-Meldung für die Konvertierung in eine einfache Ansicht, bei der es sich um ein Array von Zeitblöcken handelt, die die Verfügbarkeit in bestimmten Bereichen bestimmen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Kalendertypen](types-calendars.md)  
  
 [Kalenderentität](/reference/entities/calendar.md)  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Terminentitäten](/dynamics365/customer-engagement/developer/appointment-entities)  
  
 [Serienterminentitäten](/dynamics365/customer-engagement/developer/recurring-appointment-entities)  
  
 [Ressourcenentitäten](/dynamics365/customer-engagement/developer/resource-entities)  
  
 [Serviceentität](/dynamics365/customer-engagement/developer/service-entity)  
  
 [Beispielcode für Zeitplan- und Terminentitäten](/dynamics365/customer-engagement/developer/sample-code-schedule-appointment-entities)