---
title: Keine doppelte Registrierung von Plug-in-Schritten | MicrosoftDocs
description: 'Die Registrierung eines doppelten Plug-in-Schrittes bewirkt, dass das Plug-in bei derselben Nachricht/Ereignis mehrmals ausgelöst wird.'
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="do-not-duplicate-plug-in-step-registration"></a>Keine Registrierung von Plug-in-Schritten duplizieren

**Kategorie**: Leistung

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Die Registrierung eines doppelten Plug-in-Schrittes bewirkt, dass das Plug-in bei derselben Nachricht/Ereignis mehrmals ausgelöst wird. Dies könnte zu Folgendem führen:

- Verzögerte Verarbeitung von asynchronen Aufträgen, wenn sie als asynchroner Ausführungsmodus registriert sind.
- Beeinträchtigte Benutzerleistung, wenn sie als synchroner Ausführungsmodus registriert sind. Zu den Erfahrungen gehören:
    - Nicht reaktionsfähige, modellgetriebene Anwendungen
    - Langsame Kundeninteraktionen
    - Der Browser reagiert nicht mehr.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Stellen Sie sicher, dass Sie bestehende Registrierungsschritte für Plugins aktualisieren, anstatt sie zu löschen und neu zu erstellen.  Darüber hinaus sollten Sie Plug-in-Registrierungsschritte nur auf unterstützte Weise erstellen und aktualisieren.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

> [!WARNING]
> Diese Muster sollten vermieden werden.

Das Löschen und Wiederherstellen eines Schrittes in der Quellinstanz (test, dev, preprod) erzeugt auch einen doppelten Schritt, der in der Zielumgebung registriert wird, wenn dieser Schritt zuvor registriert wurde.

![Registrierung von doppelten Plug-in-Schritten](../media/duplicate-plugin-registration-step.png)

Das manuelle Erstellen der `SDKMessageProcessingSteps` mit einer neuen GUID oder das Aktualisieren der bestehenden GUID innerhalb der Datei `customizations.xml` führt zur Registrierung eines doppelten Schrittes. Diese Art von Aufgaben wird nicht unterstützt, wie in [Wann soll die Anpassungsdatei bearbeitet werden?](/powerapps/developer/model-driven-apps/when-edit-customization-file)

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Die doppelte Registrierung von Plug-in-Schritten kann zu SQL-Deadlocking führen, wenn die Ereignisse in einer Update-Meldung registriert werden. Wenn Sie eine Aktualisierung für einen Datensatz ausgeben, erstellt SQL eine Zeilensperre für diesen Datensatz. Wenn eine andere Transaktion versucht, den gleichen Datensatz zu aktualisieren, muss sie warten, bis die Sperre freigegeben ist, bevor sie die Aktualisierung durchführen kann. Wenn ein Timeout eintritt, wird die Transaktion zurückgesetzt und das Update wird nicht in die SQL-Datenbank übertragen.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Registrieren eines Plugins](../../register-plug-in.md)
[Deadlocking](https://technet.microsoft.com/library/ms177433.aspx)<br />
