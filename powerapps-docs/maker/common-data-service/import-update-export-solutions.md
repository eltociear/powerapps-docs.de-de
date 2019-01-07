---
title: 'Importieren, Aktualisieren und Exportieren von Lösungen | MicrosoftDocs'
description: 'Erfahren Sie, wie eine Lösung in PowerApps importiert, aktualisiert und exportiert wird'
ms.custom: ''
ms.date: 11/06/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 56363ea3-ea76-4311-9b7a-b71675e446fb
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="import-update-and-export-solutions"></a>Lösungen importieren, aktualisieren und exportieren 

 Sie können Lösungen mithilfe der unten angegebenen Schritte manuell importieren. Importieren Sie nur Lösungen, die von einer vertrauenswürdigen Quelle stammen. Anpassungen können Code enthalten, durch den Daten an externe Quellen gesendet werden. Sie können die **Standardlösung** nur in die Organisation importieren, von der sie exportiert wurde, aber nicht in eine andere Organisation.  
  
1.  Wählen Sie im linken Navigationsbereich die Option **Lösungen** aus.  
  
2.  Wählen Sie in der Lösungsliste die Option **Import** aus.  

    > [!div class="mx-imgBorder"]  
    > ![Lösung importieren](media/solution-import.png "Lösung importieren") 
  
3.  Navigieren Sie im Dialogfeld **Lösung importieren** , wählen Sie Schritt **Lösungspaket auswählen** und **wählen die Datei**, gehen Sie zur komprimierten Datei (ZIP- oder CAB-Datei), die die Lösung enthält, die Sie importieren möchten. 
  
4.  Wählen Sie **Weiter**.  
  
5.  Informationen über eine vorgeschlagene Lösung anzeigen. Klicken Sie auf **Importieren**.  
  
6. Möglicherweise müssen Sie einige Momente beim Lösungsimport warten. Anzeigen der Ergebnisse und wählen Sie dann **Schließen** aus.  
  
 Falls Sie Änderungen importiert haben, die veröffentlicht werden müssen, müssen Sie Anpassungen veröffentlichen, bevor diese verfügbar sind. 
  
 Wenn der Import nicht erfolgreich ist, sehen Sie einen Bericht mit allen Fehlern oder Warnhinweisen, die erfasst wurden. Wählen Sie **Protokolldatei herunterladen**, um Informationen zu den Gründen für das Fehlschlagen des Imports zu geben. Die häufigste Ursache für das Fehlschlagen eines Lösungsimports besteht darin, dass die Lösung einige erforderliche Lösungskomponenten nicht vollständig enthielt..  
  
 Wenn Sie die Protokolldatei herunterladen, sehen Sie eine XML-Datei, die Sie mit Office Excel öffnen können, um ihre Inhalte anzuzeigen.  
  
> [!NOTE]
>  Sie können einen aktiven Weiterleitungsregelsatz nicht bearbeiten. Wenn Sie eine Lösung, die einen aktiven Weiterleitungsregelsatz umfasst, in eine Organisation importieren, in der in der Regel mit derselben ID vorhanden ist, schlägt der Lösungsimport fehl. Weitere Informationen: [Regeln erstellen, um Anfragen automatisch weiterzuleiten](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/create-rules-automatically-route-cases)  
  
<a name="BKMK_UpdateSolutions"></a>   

## <a name="update-solutions"></a>Lösungen aktualisieren  
 Manchmal möchten Sie eine Aktualisierung zu einer vorhandenen verwalteten Lösung installieren. Die Vorgehensweise entspricht dem Installieren einer neuen verwalteten Lösung, mit Ausnahme einiger unterschiedlicher Optionen. Wenn Sie eine Lösung aktualisieren, die Sie von jemand anderem erhalten haben, sollten Sie den Lösungsherausgeber danach fragen, welche Optionen Sie auswählen sollten.  
  
1.  Wählen Sie im linken Navigationsbereich die Option **Lösungen** aus.
  
2.  Wählen Sie in der Lösungsliste die Option **Import** aus.  
  
3.  Navigieren Sie im Dialogfeld **Lösung importieren** , wählen Sie Schritt **Lösungspaket auswählen** und **wählen die Datei**, gehen Sie zur komprimierten Datei (ZIP- oder CAB-Datei), die die Lösung enthält, die Sie updaten möchten.

4.  Wählen Sie **Weiter**.  
  
5.  Zeigen Sie die Informationen zur Lösung an und klicken Sie auf **Weiter**. Diese Seite zeigt einen gelben Balken mit der Meldung **Das Lösungspaket enthält ein Update für eine bereits installierte Lösung** an.  
  
6.  Sie haben die folgenden Optionen:  
  
    - **Anpassungen warten (empfohlen)**  
  
         Mit der Auswahl dieser Option werden alle unverwalteten Anpassungen gewartet, die auf Komponenten ausgeführt wurden. Allerdings werden nicht alle Updates in dieser Lösung angewendet.  
  
    - **Anpassungen überschreiben**  
  
         Diese Option überschreibt nicht verwaltete Anpassungen, die zuvor für Komponenten in dieser Lösung vorgenommen wurden. Alle in dieser Lösung enthaltenen Aktualisierungen werden wirksam.  
  
     Wählen Sie die entsprechende Option, und wählen Sie dann **Weiter**.  
  
7.  Möglicherweise müssen Sie einige Momente beim Lösungsimport warten. Anzeigen der Ergebnisse und wählen Sie dann **Schließen** aus.  
  
 Falls Sie Änderungen importiert haben, die veröffentlicht werden müssen, müssen Sie Anpassungen veröffentlichen, bevor diese verfügbar sind. 
  
 Lösungsherausgeber können Sie auffordern, Ihre vorhandenen nicht verwalteten Anpassungen zu exportieren, ihre verwaltete Lösung mit der Option zum Überschreiben von Anpassungen zu aktualisieren, und dann Ihre nicht verwalteten Anpassungen erneut zu importieren. Dadurch wird sichergestellt, dass die erwarteten Änderungen vorgenommen und Ihre Anpassungen beibehalten werden.  
  
<a name="BKMK_ExportSolutions"></a>   

## <a name="export-solutions"></a>Exportieren von Lösungen  
 Es wird empfohlen, dass Sie Ihre nicht verwalteten Anpassungen regelmäßig exportieren, damit Sie für alle Fälle über ein Backup verfügen. Verwaltete Lösungen können nicht exportiert werden. Sie können entweder PowerApps Lösungen exportieren, oder Sie können sie mithilfe der klassischen Erfahrung exportieren. 
 
### <a name="export-from-powerapps"></a>Exportieren aus PowerApps
  
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
  
7.  Der nächste Schritt ermöglicht es Ihnen, eine Ziellösung für eine bestimmte Dynamics 365 for Customer Engagement Version auszuwählen. Diese Option wird in der Regel von ISVs verwendet, die eine Lösung exportieren möchten, welche mit einer früheren Version kompatibel ist. Wenn Sie jedoch diese Lösung in eine Umgbun g importieren möchten, die nicht auf die gleiche Version wie die von Ihnen verwendete Umgebungsversion aktualisiert ist, übernehmen Sie die Standardeinstellung.   
  
8.  Wählen Sie **Exportieren** aus, um die Lösungsdatei herunterzuladen.  
  
 Die exakte Verhaltensweise beim Download von Dateien ist für verschiedene Web-Browser unterschiedlich.  

<a name="BKMK_SettingsOptionsOnSolutionExport"></a>  
 
## <a name="settings-options-for-solution-export"></a>Einstellungsoptionen für den Lösungsexport  
 Wenn Sie die Lösung aus PowerApps exportieren, missachten Sie diesen Abschnitt. In der folgenden Tabelle sind die verfügbaren Optionen beim Export von Lösungen in der klassischen Erfahrung aufgeführt.  
  
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
|Datumsformatcode|Informationen darüber, wie das Datum in Dynamics 365  for Customer Engagement angezeigt wird.|  
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

  
## <a name="next-steps"></a>Nächste Schritte

[Lösungen und Patches verteilen](use-segmented-solutions-patches-simplify-updates.md)
