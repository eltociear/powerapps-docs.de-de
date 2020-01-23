---
title: 'FAQs: Übergang zur einheitlichen Oberfläche | Microsoft-Dokumentation'
description: Häufig gestellte Fragen im Zusammenhang mit dem Übergangsprozess zum Verschieben von Benutzern vom Vorgänger-Webclient zu Einheitliche Oberfläche.
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: e06fa6901ec123307adaabdbbb6071e5a11c47cc
ms.sourcegitcommit: 41a78575a6533c45c7cf4c012f8ed30c4e43aae8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2918108"
---
# <a name="faqs-transition-to-unified-interface"></a>FAQs: Übergang zur einheitlichen Oberfläche

Dieses Thema enthält Antworten auf die häufigsten Fragen zu den Übergangsoptionen für das Verschieben von Benutzern vom Vorgänger-Webclient zu Einheitliche Oberfläche.

### <a name="where-can-i-go-to-see-the-transition-dates-that-have-been-suggested-for-my-environments"></a>Wo kann ich die Übergangstermine anzeigen, die für meine Umgebungen vorgeschlagen wurden? 

Verwenden Sie das Übergangsportal, um das Übergangsdatum Ihrer Umgebung zu verwalten: <https://runone.powerappsportals.com>.

### <a name="how-do-i-gain-access-to-the-portal"></a>Wie erhalte ich Zugriff auf das Portal?

Führen Sie die folgenden Schritte aus:
1. Besuchen Sie <https://runone.powerappsportals.com>.
2. Melden Sie sich mit den Administrator-Anmeldeinformationen des Mandanten, den Sie verwalten möchten, an.
3. Wählen Sie **Meine Umgebungen** aus, und überprüfen Sie alle Umgebungen, auf die ein vorgeschlagenes Datum angewendet wurde.

### <a name="i-see-my-environment-has-a-date-suggested-for-transition-can-i-change-this-date"></a>Ich sehe, dass meine Umgebung ein für den Übergang vorgeschlagenes Datum hat. Kann ich dieses Datum ändern?

Ja, das ist möglich, wenn Sie die Rolle **globaler Administrator**, **Dynamics 365-Dienstadministrator** oder **Power Platform-Administrator** für den Mandanten haben. 

Die Ihrer Umgebung zugeordneten Daten sind ein Vorschlag, für den eine Genehmigung zum Fortfahren erforderlich ist. Bitte genehmigen Sie, wenn das Datum für Ihre Organisation in Ordnung ist.  

Zum Ändern des Datums wählen Sie das Dropdown-Symbol neben der Umgebung aus und zeigen Sie den Datensatz an. Mandantenadministratorrollen können dann das Übergangsdatum auf ein früheres oder späteres Datum verschieben.

Um auf ein früheres Datum zu verschieben, aktualisieren Sie das vorhandene Datum zu Ihrer bevorzugten Option in der Liste. Sie können auch [manuell wechseln](transition-web-app.md) , wenn Ihre Datumsangaben nicht geeignet sind. 
 
Um einen späteren Zeitpunkt einzuplanen, wählen Sie die Schaltfläche „Übergangsdatum neu planen“ aus. Vorgeschlagene Datumsangaben sind im Dropdown verfügbar. Nach der Genehmigung wird das Datum im Portal entsprechend aktualisiert. Akzeptieren Sie dann das aktualisierte Datum, wenn Sie möchten, dass Ihre Umgebung umgestellt wird. 
 
Datumsänderungen werden überprüft und gewährt, wenn das Datum vor dem 1. Oktober 2020 liegt. Das Datum wird nach der Bestätigung im Portal aktualisiert. 

> [!NOTE]
> Wenn Sie einen genehmigten Übergang haben und das geplante Datum innerhalb von 48 Stunden liegt, können Sie das Datum nicht ändern. Ebenso können Sie kein Datum nach dem 1. Oktober 2020 anfordern, da der Vorgänger-Webclient dann nicht mehr verfügbar ist.

### <a name="what-will-happen-if-i-dont-opt-in-and-approve-a-suggested-transition-date-for-my-environment"></a>Was passiert, wenn ich kein Abonnement abschließe und kein vorgeschlagenes Übergangsdatum für meine Umgebung genehmige?

Es wird keine Änderung an Ihrer Umgebung geben, wenn Sie das vorgeschlagene Datum im Portal nicht genehmigt haben. Wenn das vorgeschlagene Datum verstrichen ist, werden wir versuchen, Ihnen ein weiteres Datum in der Zukunft Termin zur Verfügung zu stellen.  
 
> [!NOTE]
> Nach dem 1. Oktober 2020 werden alle Umgebungen auf Einheitliche Oberfläche aktualisiert, gemäß der Release-Welle von Oktober 2020.

### <a name="my-transition-date-is-within-48-hours-and-i-cant-change-the-date-within-the-portal-how-can-i-stop-the-transition-from-taking-place"></a>Mein Übergangsdatum liegt innerhalb von 48 Stunden, und ich kann das Datum im Portal nicht ändern. Wie kann ich verhindern, dass der Übergang stattfindet?

Die Möglichkeit, das Übergangsdatum für eine Umgebung zu ändern, ist nur bis 48 Stunden vor dem Übergang verfügbar. Um den Prozess nach diesem Zeitraum zu beenden, bringen Sie eine Supportanfrage zur Sprache. 

> [!NOTE]
> Es wird keine Garantie übernommen, dass der Übergang gestoppt werden kann, wenn die Anforderungen nach der Sperrung im Portal gemacht wurde (48 Stunden oder weniger).

### <a name="i-have-environments-without-a-scheduled-date-can-i-update-these-to-include-a-date"></a>Ich habe Umgebungen ohne geplantes Datum. Kann ich diese aktualisieren, um ein Datum mit aufzunehmen?

Ja, wenn Sie die Rolle **globaler Administrator**, **Dynamics 365-Dienstadministrator** oder **Power Platform-Administrator** für den Mandaten haben, wählen Sie die Umgebung aus, und wählen Sie ein Datum aus, indem Sie auf die Schaltfläche „Übergangsdatum neu planen“ klicken.

Wir aktualisieren das Portal mit dem Datum, um es zu bestätigen. Zudem werden Benachrichtigungs-E-Mails an die globalen Mandantenadministratoren senden, wenn das Übergangsdatum kurz bevorsteht. Dies entspricht der Standarderinnerungsvorgehensweise, die im Rahmen dieses Dokuments aufgeführt ist.

### <a name="is-there-a-recommended-checklist-i-should-run-through-before-transition"></a>Gibt es eine empfohlene Prüfliste, die ich vor dem Übergang ausführen sollte?

Sehen Sie sich den unterstützenden Inhalt an, der auf der [Community-Site](https://community.dynamics.com/365/unified-interface/) zur Verfügung steht. Wir haben auch eine [Übergangscheckliste](https://aka.ms/UIChecklist), mit deren Hilfe Sie effektiv planen können. Überprüfen Sie sie sorgfältig, um sicherzustellen, dass Sie mit dem Übergang zur Einheitlichen Oberfläche vertraut sind.

### <a name="my-environment-has-been-transitioned-but-i-am-finding-blocking-issues-for-my-users-and-want-to-move-back-to-the-legacy-web-client-is-this-possible"></a>Meine Umgebung wurde umgestellt, aber ich stelle Blockierprobleme für meine Benutzer fest und möchte zum Vorgänger-Webclient zurückkehren. Ist das möglich?

Ja, Sie können wieder in den Vorgängerwebclienten bis maximal 10 Tage nach dem Übergang wechseln. Sie können den [Wechsel manuell](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only) während der ersten 4 Tage durchführen; danach stellen Sie eine Supportanfrage über Ihren üblichen Kanal, da der manuelle Wechsel deaktiviert wird. 

> [!NOTE]
> Die 10 Tage müssen vor dem 1. Oktober 2020 sein, da der Vorgängerwebclient nach diesem Datum nicht mehr zur Verfügung steht.

### <a name="i-want-to-transition-after-october-1-2020-is-that-possible"></a>Ich möchte den Übergang nach dem 1. Oktober 2020 machen. Ist das möglich?

Der Vorgänger-Webclient wird nach der Release-Welle von Oktober 2020 für Endbenutzer nicht mehr verfügbar sein. Wir können das Datum nicht über diesen Zeitraum hinaus verschieben.

Falls blockierenden Elemente, auftreten, protokollieren Sie diese mithilfe des Standardunterstützungsprozesses so schnell wie möglich.

### <a name="what-is-the-standard-reminder-procedure-throughout-this-process"></a>Was ist die Standarderinnerungsvorgehensweise während des Prozesses?

Die Kommunikation findet in Wellen, mindestens 30 Tage vor dem vorgeschlagenen Zeitrahmen, statt. Sie können sich jedoch im Portal (<https://runone.powerappsportals.com>) jederzeit anmelden, um den Status anzuzeigen. Microsoft sendet folgende Kommunikation:

-   Anfangsnachricht für jede Umgebung, die über ein vorgeschlagenes Übergangsdatum verfügt.
-   Wenn Sie das Datum genehmigt haben, erhalten Sie 2 Tage vor der Sperrung des Datums/der Daten im Portal eine Erinnerungsmeldung. 
-   Die letzte Erinnerung wird 2 Tage vor dem Übergang versandt. Hiermit wird angegeben, dass das Übergangsdatum gesperrt ist und der Übergang erfolgen wird.
-   Nach dem Übergang wird eine Abschlussmeldung angezeigt, um den Erfolg zu bestätigen (oder ob ein Problem aufgetreten ist)

Meldungen können mithilfe des folgenden Kanäle angesehen werden:
-   Nachrichten-Center innerhalb des Mandanten Microsoft 365. Dies ist normalerweise für Rollen wie globalem Administrator, Service-Administrator, Bedienungsmeldungs-Leser sichtbar.
-   Direkte E-Mail.  E-Mails werden nur an die Systemadministratorrolle für die bestimmte betreffende Umgebung oder an die E-Mail-Adresse gesendet, die an die Registerkarte "Benachrichtigung" im Umgebungsadministratorportal hinzugefügt wurde.

> [!NOTE]
> Sie erhalten eine E-Mail für jede Umgebung, in der Ihr Benutzerkonto über die Systemadministratorrolle verfügt.

### <a name="i-have-requested-a-date-to-postpone-but-still-receiving-e-mails-and-message-center-posts-that-my-environment-is-set-to-transition-should-i-be-concerned"></a>Ich habe ein Datum angefordert, zurückstellen aber erhalte immer noch E-Mails und Nachrichten aus dem Message-Center, dass meine Umgebung auf Übergang festgelegt ist. Sollte ich beunruhigt sein?

Als erstes empfehlen wir, das Übergangsportal (<https://runone.powerappsportals.com/>) zu prüfen, da dieses die einzige Quelle der Wahrheit für alle Ihre Umgebungen ist. Falls das Datum aktualisiert wurde, ist es sehr wahrscheinlich, dass unser Kommunikationssystem die Meldung gesendet hat, bevor wir die Kommunikationsliste aktualisiert haben. 

Wenn das Datum im Portal nicht auf das neue Datum aktualisiert ist, reichen Sie eine Supportanfrage nach der Standardvorgehensweise ein.

Nur vom Administrator genehmigte Daten (Datumsangaben) werden umgestellt. 

### <a name="if-i-already-have-an-environment-transitioned-to-unified-interface-will-i-still-be-able-to-switch-back-to-the-legacy-web-client-manually"></a>Wenn ich bereits eine Umgebung habe, die zur Einheitlichen Oberfläche übergegangen ist, kann ich noch manuell in den Vorgängerwebclienten wechseln?

Wenn Ihre Umgebung seit mindestens 4 Tagen übergegangen ist, versuchen wir den manuellen Wechsel zurück zum Vorgängerwebclienten zu deaktivieren. 

Sollte dies deaktiviert worden sein und Sie eine Anfrage zum Zurückwechseln laufen haben, reichen Sie eine Supportanfrage über Ihren üblichen Kanal zur Auswertung ein.

### <a name="is-there-a-specific-day-and-time-when-approved-transitions-will-take-place"></a>Gibt es einen bestimmten Tag und eine bestimmte Uhrzeit für genehmigte Übergänge? 

Wir erwarten keine Ausfallzeit, wenn wir den Übergang vornehmen. Übergänge erfolgen jedoch nur an einem Freitag, wobei dieselbe Wartungszeitskalen eingehalten werden, die in unseren Standardrichtlinien und Mitteilungen dargelegt sind. Weitere Informationen: [Wartungszeitplan ](https://docs.microsoft.com/power-platform/admin/policies-communications#maintenance-timeline)

### <a name="are-environments-from-all-data-centers-included-within-this-transition-service"></a>Sind Umgebungen aus allen Rechenzentren in diesem Übergangsdienst enthalten?

Derzeit sind Umgebungen aus spezifischen Rechenzentren, wie z. B. Government Community Cloud (GCC), nicht im Portal einbezogen worden. Wir werden die vorgeschlagenen Übergangstermine für diese Umgebungen bis Juni 2020 bereitstellen. Kunden, die zu Einheitliche Oberfläche wechseln möchten, können jederzeit [manuell wechseln](/power-platform/admin/enable-unified-interface-only#how-to-enable-unified-interface-only-mode) zu jedem Zeitpunkt vor dem 1. Oktober 2020.


