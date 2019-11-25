---
title: 'FAQs: Übergang Einheitliche Oberfläche | Microsoft-Dokumentation'
description: FAQs bezogen auf den automatischen Übergangsprozess zum Verschieben von Benutzern vom Vorgängerwebclienten zur Einheitlichen Oberfläche.
ms.custom: ''
ms.date: 11/04/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: haybass
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 373201de630b46adc80b25eed10686da9112bad6
ms.sourcegitcommit: c094590862142155cbafa91c6ee0ade975c82083
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "2769438"
---
# <a name="faqs-unified-interface-transition"></a>FAQs: Übergang Einheitliche Oberfläche

Dieses Thema enthält Antworten auf die am häufigsten gestellten Fragen zum Übergangsprozess zum Verschieben von Benutzern vom Vorgängerwebclienten zur Einheitlichen Oberfläche.

### <a name="where-can-i-go-to-see-the-transition-dates-that-have-been-assigned-to-my-environments"></a>Wo finde ich die Übergangsdatumsangaben, die meiner Umgebung zugewiesen wurden? 

Verwenden Sie das Auto-Übergangsportal, um Ihr Umgebungsübergangsdatum zu verwalten: <https://runone.powerappsportals.com>.

### <a name="how-do-i-gain-access-to-the-portal"></a>Wie erhalte ich Zugriff auf das Portal?

Führen Sie die folgenden Schritte aus:
1. Besuchen Sie <https://runone.powerappsportals.com>.
2. Melden Sie sich mit den Administrator-Anmeldeinformationen des Mandanten, den Sie verwalten möchten, an.
3. Wählen Sie **Meine Umgebungen** und überprüfen Sie alle Umgebungen, denen ein Stichdatum zugewiesen wurde.

### <a name="i-see-my-environment-has-a-date-for-auto-transition-can-i-change-this-date"></a>Ich sehe, dass meine Umgebung ein Datum für den automatischen Übergang hat. Kann ich dieses Datum ändern?

Ja, das ist möglich, wenn Sie die Rolle **Globaler Admin** oder **Service Admin** für den Mandanten besitzen. Zum Ändern des Datums wählen Sie das Dropdown-Symbol neben der Umgebung aus und zeigen Sie den Datensatz an. Mandantenadministratorrollen können dann ein Ausnahmeersuchen für früheres oder späterer Übergangsdatum einreichen.

- Für ein früheres Übergangsdatum aktualisieren Sie das vorhandene Datum durch Ihre bevorzugte Option in der Liste. Dies erfordert keinen Genehmigung. Sie können auch manuell wechseln, wenn Ihre Datumsangaben nicht geeignet sind.

- Für ein späteres Übergangsdatum können Sie eine Ausnahmeanforderung einreichen. Vorgeschlagene Datumsangaben sind im Dropdown verfügbar. Sobald genehmigt, wird das Datum entsprechend im Portal aktualisiert.

Sie können insgesamt zwei Ausnahmen pro Umgebung anfordern. Ausnahmen werden basierend auf der Unternehmensrechtfertigung neben dem vorgeschlagenen ausgewählten Datum gewährt. Das Datum wird nach der Bestätigung im Portal aktualisiert.

> [!NOTE]
> Wenn der geplante Übergang innerhalb von 48 Stunden ist, können Sie das Datum nicht ändern. Ebenso können Sie kein Datum nach dem 1. Oktober 2020 anfordern, da der Vorgängerwebclient nicht mehr verfügbar ist.

### <a name="my-auto-transition-date-is-within-48-hours-and-i-cant-change-the-date-within-the-portal-how-can-i-stop-transition-taking-place"></a>Mein automatisches Übergangsdatum ist innerhalb von 48 Stunden und ich kann das Datum innerhalb des Portals nicht ändern. Wie kann ich den laufenden Übergang stoppen?

Die Möglichkeit, das Übergangsdatum für eine Umgebung zu ändern, ist nur bis 48 Stunden vor dem Übergang verfügbar. Um den Prozess nach diesem Zeitraum zu beenden, bringen Sie eine Supportanfrage zur Sprache. 

> [!NOTE]
> Es wird keine Garantie übernommen, dass der Übergang gestoppt werden kann, wenn die Anforderungen nach der Sperrung im Portal gemacht wurde (48 Stunden oder weniger).

### <a name="i-have-environments-without-a-target-auto-transition-date-can-i-update-these-to-include-a-date"></a>Ich habe Umgebung ohne ein automatisches Übergangsdatumsziel. Kann ich diese aktualisieren, um ein Datum mit aufzunehmen?

Ja, wenn Sie **Globaler Administrator** oder **Serviceadministrator** für die Mandanten sind, wählen Sie die Umgebung aus, reichen eine Ausnahmeanforderung ein und aktualisieren Sie Ihren vorgeschlagenen Zeitrahmen mithilfe der Stichdatumsliste. 

Wir aktualisieren das Portal mit dem Datum, um es zu bestätigen. Zudem werden Benachrichtigungs-E-Mails an die globalen Mandantenadministratoren senden, wenn das Übergangsdatum kurz bevorsteht. Dies entspricht der Standarderinnerungsvorgehensweise, die im Rahmen dieses Dokuments aufgeführt ist.

### <a name="is-there-a-recommended-checklist-i-should-run-through-before-transition"></a>Gibt es eine empfohlene Prüfliste, die ich vor dem Übergang ausführen sollte?

Sehen Sie sich den unterstützenden Inhalt an, der auf der [Community-Site](https://community.dynamics.com/365/unified-interface/) zur Verfügung steht. Wir haben auch eine [Übergangscheckliste](https://aka.ms/UIChecklist), mit deren Hilfe Sie effektiv planen können. Überprüfen Sie sie sorgfältig, um sicherzustellen, dass Sie mit dem Übergang zur Einheitlichen Oberfläche vertraut sind.

### <a name="my-environment-has-been-transitioned-but-i-am-finding-blocking-issues-for-my-users-and-wish-to-move-back-to-the-legacy-web-client-is-this-possible"></a>Meine Umgebung hat den Übergang passiert, aber ich stoße auf Blockierprobleme für meine Benutzer und möchte auf den Vorgängerwebclienten zurückgehen. Ist das möglich?

Ja, Sie können wieder in den Vorgängerwebclienten bis maximal 10 Tage nach dem Übergang wechseln. Sie können den [Wechsel manuell](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only) während der ersten 4 Tage durchführen; danach stellen Sie eine Supportanfrage über Ihren üblichen Kanal, da der manuelle Wechsel deaktiviert wird. 

> [!NOTE]
> Die 10 Tage müssen vor dem 1. Oktober 2020 sein, da der Vorgängerwebclient nach diesem Datum nicht mehr zur Verfügung steht.

### <a name="i-want-to-transition-after-october-1-2020-is-that-possible"></a>Ich möchte den Übergang nach dem 1. Oktober 2020 machen. Ist das möglich?

Der verfügbare Vorgängerwebclient wird nach dem 1. Oktober 2020 nicht mehr zur Verfügung stehen. Wir verfügen nicht über die Möglichkeit, den Übergang über dieses Datum hinaus zu verzögern.

Falls blockierenden Elemente, auftreten, protokollieren Sie diese mithilfe des Standardunterstützungsprozesses so schnell wie möglich.

### <a name="what-is-the-standard-reminder-procedure-throughout-this-process"></a>Was ist die Standarderinnerungsvorgehensweise während des Prozesses?

Microsoft sendet folgende Kommunikation:

-   Erste Meldung für jede Umgebung, der ein Übergangsdatum zugewiesen wurde
-   Erinnerungsnachricht 2 Tage bevor die Daten im Portal gesperrt werden
-   Abschließende Erinnerung zur Angabe des Übergangsdatum wird blockiert und fortgesetzt.
-   Abschließende Meldung, um den Erfolg zu bestätigen (oder ob ein Problem auftrat)

Meldungen können mithilfe des folgenden Kanäle angesehen werden:
-   Nachrichten-Center innerhalb des Mandanten Microsoft 365. Dies ist normalerweise für Rollen wie globalem Administrator, Service-Administrator, Bedienungsmeldungs-Leser sichtbar.
-   Direkte E-Mail.  E-Mails werden nur an die Systemadministratorrolle für die bestimmte betreffende Umgebung oder an die E-Mail-Adresse gesendet, die an die Registerkarte "Benachrichtigung" im Umgebungsadministratorportal hinzugefügt wurde.

> [!NOTE]
> Sie erhalten eine E-Mail für jede Umgebung, in der Ihr Benutzerkonto über die Systemadministratorrolle verfügt.

### <a name="i-have-requested-a-date-to-postpone-but-still-receiving-e-mails-and-message-center-posts-that-my-environment-is-set-to-transition-should-i-be-concerned"></a>Ich habe ein Datum angefordert, zurückstellen aber erhalte immer noch E-Mails und Nachrichten aus dem Message-Center, dass meine Umgebung auf Übergang festgelegt ist. Sollte ich beunruhigt sein?

Als erstes empfehlen wir, das Übergangsportal (<https://runone.powerappsportals.com/>) zu prüfen, da dieses die einzige Quelle der Wahrheit für alle Ihre Umgebungen ist. Falls das Datum aktualisiert wurde, ist es sehr wahrscheinlich, dass unser Kommunikationssystem die Meldung gesendet hat, bevor wir die Kommunikationsliste aktualisiert haben. 

Wenn das Datum im Portal nicht auf das neue Datum aktualisiert ist, reichen Sie eine Supportanfrage nach der Standardvorgehensweise ein.

### <a name="if-i-already-have-an-environment-transitioned-to-unified-interface-will-i-still-be-able-to-switch-back-to-the-legacy-web-client-manually"></a>Wenn ich bereits eine Umgebung habe, die zur Einheitlichen Oberfläche übergegangen ist, kann ich noch manuell in den Vorgängerwebclienten wechseln?

Wenn Ihre Umgebung seit mindestens 4 Tagen übergegangen ist, versuchen wir den manuellen Wechsel zurück zum Vorgängerwebclienten zu deaktivieren. 

Sollte dies deaktiviert worden sein und Sie eine Anfrage zum Zurückwechseln laufen haben, reichen Sie eine Supportanfrage über Ihren üblichen Kanal zur Auswertung ein.

### <a name="is-there-a-specific-day-and-time-when-automatic-transitions-will-take-place"></a>Gibt es einen bestimmten Tag und eine bestimmte Uhrzeit, wann die automatischen Übergänge stattfinden? 

Wir erwarten keine Ausfallzeit, wenn wir den Übergang vornehmen. Allerdings werden wir einen automatischen Übergang nur an einem Freitag durchführen und dabei den gleichen Wartungszeitplänen folgen, die in unseren Standardrichtlinien und Kommunikation erklärt sind. Weitere Informationen: [Wartungszeitplan ](https://docs.microsoft.com/power-platform/admin/policies-communications#maintenance-timeline)




