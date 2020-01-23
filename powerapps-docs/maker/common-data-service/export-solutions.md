---
title: Exportieren von Lösungen | MicrosoftDocs
description: Erfahren Sie, wie eine Lösung exportiert in Power Apps exportiert wird
ms.custom: ''
ms.date: 09/30/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3ab3bc284b6bc9e6749d8aabae5e0fbd7a1edbec
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2914335"
---
# <a name="export-solutions"></a>Exportieren von Lösungen  
 Wir empfehlen Ihnen, eine nicht verwaltete Lösung zu erstellen, die Sie für den Export Ihrer Anpassungen verwenden können. Exportieren Sie dann Ihre Anpassungen regelmäßig, so dass Sie ein Backup haben, falls etwas passiert. Verwaltete Lösungen können nicht exportiert werden. Sie können entweder Lösungen von Power Apps exportieren oder mit der klassischen Erfahrung exportieren. 
 
> [!IMPORTANT]
> Der Export der Standardlösung wird nicht unterstützt. 

### <a name="export-from-power-apps"></a>Exportieren von Power Apps aus
  
1.  Wählen Sie im linken Navigationsbereich die Option **Lösungen** aus.   
  
2.  Wählen Sie in der Liste die Lösung aus, die Sie exportieren möchten, und wählen Sie dann **Export**. 

3.  Wählen Sie den Pakettyp **nicht verwaltet** oder **verwaltet** aus. Dies startet den Export, der mehrere Minuten dauern kann, um den Vorgang abzuschließen. Nach Abschluss ist die Exportzip-datei im Downloadordner verfügbar, der über den Webbrowser angegeben ist.

    > [!div class="mx-imgBorder"]  
    > ![Lösung exportieren](media/solution-export.png "Lösung exportieren") 

### <a name="export-from-the-classic-experience"></a>Export in der klassischen Erfahrung

1.  Wählen Sie **Lösungen** in der linken Navigation und dann **Zu den Klassiker wechseln**. 
  
2.  Wählen Sie in der Liste die Lösung aus, die Sie exportieren möchten, und wählen Sie dann **Export**. 
  
3.  Im Schritt **Anpassungen veröffentlichen** werden Sie daran erinnert, dass nur veröffentlichte Anpassungen exportiert werden und Sie die Option **Alle Anpassungen veröffentlichen** haben, bevor Sie auf **Weiter** klicken.  
  
4.  Wenn Ihre Lösung fehlende erforderliche Komponenten enthält, sehen Sie den Schritt **Fehlende erforderliche Komponenten** Sie können diese Warnung nur dann ignorieren, wenn Sie diese Lösung als nicht verwaltete Lösung in die ursprüngliche Umgebung zurückimportieren wollen. Befolgen Sie andernfalls die Anweisungen im Dialogfeld, um den Export abzubrechen und die erforderlichen Komponenten hinzuzufügen.  
  
5.  Im Schritt **Systemeinstellungen (Erweitert) exportieren** können Sie Systemeinstellungen auswählen, die in Ihre Lösung eingefügt werden. Wenn Ihre Lösung auf einer der Systemeinstellungsgruppen basiert, wählen Sie sie und wählen Sie **Weiter** aus.  
  
     Siehe **Einstellungsoptionen für den Lösungsexport** unten für Details zu den Einstellungen, die für jede Option enthalten sind.  
  
6.  Im Schritt **Pakettyp** müssen Sie auswählen, ob die Lösung als **Nicht verwaltete** oder **Verwaltete** exportiert werden soll..  
  
7.  Im nächsten Schritt können Sie eine Ziellösung für eine bestimmte Version auswählen. Diese Option wird in der Regel von ISVs verwendet, die eine Lösung exportieren möchten, welche mit einer früheren Version kompatibel ist. Wenn Sie jedoch diese Lösung in eine Umgbun g importieren möchten, die nicht auf die gleiche Version wie die von Ihnen verwendete Umgebungsversion aktualisiert ist, übernehmen Sie die Standardeinstellung.   
  
8.  Wählen Sie **Exportieren** aus, um die Lösungsdatei herunterzuladen.  
  
 Die exakte Verhaltensweise beim Download von Dateien ist für verschiedene Web-Browser unterschiedlich.  

<a name="BKMK_SettingsOptionsOnSolutionExport"></a>  
 
## <a name="settings-options-for-solution-export"></a>Einstellungsoptionen für den Lösungsexport  
 Wenn Sie die Lösung von Power Apps exportieren, beachten Sie bitte diesen Abschnitt nicht. In der folgenden Tabelle sind die verfügbaren Optionen beim Export von Lösungen in der klassischen Erfahrung aufgeführt.  
  
|Gruppe|Einstellung|Beschreibung|  
|-----------|-------------|-----------------|  
|Automatische Nummerierung|Präfix für Kampagnen|Präfix, das für die Nummerierung von Kampagnen verwendet wird.|  
|Präfix für Anfragen|Präfix, das für alle Anfragen in der gesamten App zu verwenden ist.|  
|Präfix für Verträge|Präfix, das für alle Verträge in der gesamten App zu verwenden ist.|  
|Rechnungspräfix|Präfix, das für alle Rechnungsnummern in der gesamten App zu verwenden ist.|  
|Artikelpräfix|Präfix, das für alle Artikel in der App zu verwenden ist.|  
|Auftragspräfix|Präfix, das für alle Aufträge in der gesamten App zu verwenden ist.|  
|Eindeutige Zeichenfolgenlänge|Anzahl der Zeichen, die an Rechnungs-, Angebots- und Auftragsnummern angefügt werden.|  
|Kalender|Kalendertyp|Kalendertyp für das System. Standardmäßig Gregorianisch US|  
|Datumsformatcode|Informationen darüber, wie das Datum während der Common Data Service angezeigt wird.|  
|Datumstrennzeichen|Zeichen, das zur Trennung von Monat, Tag und Jahr in Datumsangaben in der gesamten App verwendet wird.|  
|Max. Termindauer|Maximale Anzahl von Tagen für einen Termin.|  
|Wochennummer anzeigen|Informationen, durch die angegeben wird, ob die Wochennummer in Kalenderanzeigen in der gesamten App angezeigt werden soll.|  
|Zeitformatcode|Informationen, durch die angegeben wird, wie die Uhrzeit in der gesamten App angezeigt wird.|  
|Code für ersten Tag der Woche|Festgelegter erster Wochentag in der gesamten App.|  
|Anpassung|Ist Anwendungsmodus aktiviert|Gibt an, ob das Laden eine App in einem Browserfenster ohne Adress-, Symbol- und Menüleiste aktiviert ist.|  
|E-Mail-Nachverfolgung|E-Mail-Versand an nicht aufgelöste Adressen zulassen|Gibt an, ob das Senden von E-Mails an nicht aufgelöste Parteien durch die Benutzer zulässig ist. (Für die Parteien ist weiterhin eine E-Mail-Adresse erforderlich.)|  
|Interne E-Mail ignorieren|Gibt an, ob von App-Benutzern oder -Warteschlangen gesendete eingehende E-Mails nachverfolgt werden sollen.|  
|Max. Nachverfolgungsnummer|Maximale Nachverfolgungsnummer, bevor Recycling ausgeführt wird.|  
|Sicheren Frame für E-Mail anzeigen|Flag, um den Text einer E-Mail im Webformular in einem IFRAME mit dem Sicherheitsattribut "restricted" wiederzugeben. Dies ist eine zusätzliche Sicherheitsmaßnahme, die jedoch zu einer Aufforderung zur Eingabe von Verbindungsdaten führen kann.|  
|Nachverfolgungspräfix|Verlaufsliste der Nachverfolgungstokenpräfixe.|  
|Nachverfolgungstoken-Basis|Basisnummer zur Bereitstellung separater Nachverfolgungstoken-Bezeichner für Benutzer, die zu verschiedenen Bereitstellungen gehören.|  
|Nachverfolgungstoken-Stellen|Anzahl der Stellen zur Darstellung eines Nachverfolgungstoken-Bezeichners.|  
|Allgemein|Anlagen blockieren|Verhindern des Uploads oder Downloads bestimmter Anlagentypen, die als gefährlich eingestuft werden.|  
|Währungsformatcode|Informationen darüber, wie Währungssymbole in der gesamten App verwendet werden.|  
|Währungssymbol|Währungssymbol|  
|Reihenfolge für Anzeige des vollständigen Namens|Reihenfolge, in der Namen in der gesamten App anzuzeigen sind.|  
|Präsenz aktiviert|Informationen darüber, ob die Instant Messaging-Präsenz aktiviert ist.|  
|Negativformat|Informationen, durch die angegeben wird, wie negative Zahlen in der gesamten App angezeigt werden.|  
|Zahlenformat|Gibt an, wie Zahlen in der gesamten App angezeigt werden.|  
|Preisdezimalstellen|Anzahl der Dezimalstellen, die für Preise verwendet werden können.|  
|Bei Zuweisung für bisherigen Besitzer freigeben|Informationen, durch die angegeben wird, ob bei der Zuweisung eine Freigabe für den bisherigen Besitzer erteilt wird.|  
|Marketing|Automatische Reaktionserstellung zulassen|Gibt an, ob die automatische Erstellung von Reaktionen zulässig ist.|  
|Automatische Kündigung zulassen|Gibt an, ob die automatische Kündigung von Abonnements zulässig ist.|  
|Automatische Kündigungsbestätigung zulassen|Gibt an, ob das Senden einer E-Mail zur automatischen Bestätigung der Kündigung von Abonnements zulässig ist.|  
|Marketing-E-Mail-Ausführung zulassen|Gibt an, ob die Ausführung von Marketing-E-Mails zulässig ist.|  
| Outlook-Synchronisierung|Adressbuchsynchronisierung zulassen|Gibt an, ob in Microsoft Office Outlook die Adressbuchsynchronisierung im Hintergrund zulässig ist.|  
|Geplante Offlinesynchronisierung zulassen|Gibt an, ob in Outlook die Offlinesynchronisierung im Hintergrund zulässig ist.|  
|Geplante Synchronisierung zulassen|Gibt an, ob geplante Synchronisierungsvorgänge mit Outlook zulässig sind.|  
|Abruffrequenz für E-Mail-Versand|Normale Abruffrequenz zum Senden von E-Mails in Outlook.|  
|Mindestfrequenz für Adressensynchronisierung|Normale Abruffrequenz für Adressbuchsynchronisierung in Outlook.|  
|Mindestfrequenz für Offlinesynchronisierung|Normale Abruffrequenz für Hintergrund-Adressbuchsynchronisierung in Outlook .|  
|Mindestfrequenz für Synchronisierung|Kürzeste zulässige Zeitspanne zwischen geplanten Outlook-Synchronisierungsvorgängen.|  
|Max. Zyklen für automatische Kennzeichnung|Maximale Anzahl aggressiver Abrufzyklen, die für die automatische E-Mail-Kennzeichnung beim Empfang neuer E-Mails ausgeführt werden.|  
|Intervall für automatische Kennzeichnung|Normale Abruffrequenz für die automatische Kennzeichnung von E-Mails in Outlook.|  
|ISV-Konfiguration|Servicekalender-Darstellungs-Konfiguration|Sie können visuelle Stile für Servicekalender definieren.

Weitere Informationen:   [Servicekalender-Darstellungs-Konfiguration](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/service-calendar-appearance-configuration)|

### <a name="see-also"></a>Siehe auch
[Lösung importieren](import-update-export-solutions.md) <br />
[Lösungen aktualisieren](update-solutions.md)