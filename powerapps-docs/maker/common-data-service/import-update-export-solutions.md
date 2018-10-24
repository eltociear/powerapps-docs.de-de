---
title: Importieren, Aktualisieren und Exportieren von Lösungen | Microsoft-Dokumentation
description: Informationen zum Importieren, Aktualisieren und Exportieren einer Lösung
ms.custom: ''
ms.date: 06/18/2018
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
ms.openlocfilehash: 89907e80085fe2bfcf3c38972724a0f9b55836c7
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683617"
---
# <a name="import-update-and-export-solutions"></a>Importieren, Aktualisieren und Exportieren von Lösungen 

 Sie können Lösungen manuell mithilfe der folgenden Schritte importieren. Importieren Sie nur Lösungen, die Sie aus einer vertrauenswürdigen Quelle erhalten haben. Anpassungen können Code enthalten, der Daten an externe Quellen senden kann. Sie können die Standardlösung nur in die Organisation importieren, aus der Sie sie exportiert haben, jedoch nicht in eine andere Organisation.  
  
1. Wechseln Sie zu **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Lösungen**.  
  
2.  Wählen Sie im Lösungenlistenmenü **Importieren** aus.  
  
3.  Navigieren Sie im Dialogfeld **Lösung importieren** im Schritt **Lösungspaket auswählen** zu der komprimierten Datei (ZIP- oder CAB), die die Lösung enthält, die Sie importieren möchten. 
  
4.  Wählen Sie **Weiter** aus.  
  
5.  Sie können Informationen zur Lösung anzeigen, bevor Sie **Importieren** auswählen.  
  
6.  Sie müssen möglicherweise einen Moment warten, während der Lösungsimport abgeschlossen wird. Wenn er erfolgreich ist, können Sie die Ergebnisse anzeigen und **Schließen** auswählen.  
  
 Wenn Sie Änderungen importiert haben, die veröffentlicht werden müssen, müssen Sie Anpassungen veröffentlichen, damit sie verfügbar sind. 
  
 Wenn der Importvorgang nicht erfolgreich ist, sehen Sie einen Bericht mit aufgezeichneten Fehlern oder Warnungen. Sie können **Protokolldatei herunterladen** auswählen, um Details zur Ursache des erfolglosen Imports zu erfahren. Die häufigste Ursache für einen erfolglosen Lösungsimport ist, dass die Lösung einige erforderliche Lösungskomponenten nicht enthalten hat.  
  
 Wenn Sie die Protokolldatei herunterladen, finden Sie eine XML-Datei, die Sie mit Office Excel öffnen können, um den Inhalt anzuzeigen.  
  
> [!NOTE]
>  Sie können einen aktiven Routingregelsatz nicht bearbeiten. Wenn Sie also eine Lösung, die einen aktiven Routingregelsatz enthält, in eine Organisation importieren, wo die Regel bereits mit der gleichen ID vorhanden ist, ist der Import der Lösung erfolglos. Weitere Informationen: [Regeln erstellen, um Anfragen automatisch weiterzuleiten](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/create-rules-automatically-route-cases)  
  
<a name="BKMK_UpdateSolutions"></a>   

## <a name="update-solutions"></a>Aktualisieren von Lösungen  
 Manchmal möchten Sie ein Update für eine vorhandene verwaltete Lösung installieren. Das Verfahren ähnelt dem Installieren einer neuen verwalteten Lösung, mit der Ausnahme, dass Sie einige andere Optionen auswählen können. Wenn Sie eine Lösung aktualisieren, die Sie von einer anderen Person erhalten haben, sollten Sie vom Herausgeber der Lösung Anleitungen zu den Optionen erhalten, aus denen Sie wählen können.  
  
1. Wechseln Sie zu **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Lösungen**.   
  
2.  Wählen Sie im Lösungenlistenmenü **Importieren** aus.  
  
3.  Navigieren Sie im Dialogfeld **Lösung importieren** im Schritt **Lösungspaket auswählen** zu der komprimierten Datei (ZIP- oder CAB), die die Lösung enthält, die Sie aktualisieren möchten.  
4.  Wählen Sie **Weiter** aus.  
  
5.  Sie können Informationen zur Lösung anzeigen, bevor Sie **Weiter** auswählen. Auf dieser Seite wird ein gelber Balken mit dem Text **Dieses Lösungspaket enthält ein Update für eine Lösung, die bereits installiert ist** angezeigt.  
  
6.  Sie haben folgende Optionen:  
  
    - **Anpassungen warten (empfohlen)**  
  
         Nach Auswahl dieser Option werden nicht verwaltete Anpassungen für Komponenten ausgeführt, aber sie beinhaltet auch, dass einige der in dieser Lösung enthaltenen Updates nicht wirksam sind.  
  
    - **Anpassungen überschreiben**  
  
         Diese Option überschreibt alle nicht verwalteten Anpassungen, die zuvor an Komponenten ausgeführt wurden, die in dieser Lösung enthalten sind. Alle in dieser Lösung enthaltenen Updates werden wirksam.  
  
     Wählen Sie die entsprechende Option und dann **Weiter** aus.  
  
7.  Sie müssen möglicherweise einen Moment warten, während der Lösungsimport abgeschlossen wird. Wenn er erfolgreich ist, können Sie die Ergebnisse anzeigen und **Schließen** auswählen.  
  
 Wenn Sie Änderungen importiert haben, die veröffentlicht werden müssen, müssen Sie Anpassungen veröffentlichen, damit sie verfügbar sind. 
  
 Lösungsherausgeber könnten Sie auffordern, Ihre vorhandenen nicht verwalteten Anpassungen zu exportieren, ihre verwaltete Lösung mit der Option zum Überschreiben von Anpassungen zu aktualisieren und dann Ihre nicht verwalteten Anpassungen erneut zu importieren. Dadurch wird sichergestellt, dass die erwarteten Änderungen angewendet und gleichzeitig Ihre Anpassungen beibehalten werden.  
  
<a name="BKMK_ExportSolutions"></a>   

## <a name="export-solutions"></a>Exportieren von Lösungen  
 Sie sollten Ihre nicht verwalteten Anpassungen in regelmäßigen Abständen exportieren, damit Sie über eine Sicherung verfügen für den Fall, dass etwas passiert. Sie können verwaltete Lösungen nicht exportieren.  
  
1. Wechseln Sie zu **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Lösungen**.   
  
2.  Wählen Sie in der Liste die Lösung, die Sie exportieren möchten, und dann **Exportieren** aus.  
  
3.  Im Schritt **Anpassungen veröffentlichen** werden Sie daran erinnert, dass nur veröffentlichte Anpassungen exportiert werden, und Sie können **Alle Anpassungen veröffentlichen**, bevor Sie **Weiter** auswählen.  
  
4.  Wenn in Ihrer Lösung erforderliche Komponenten fehlen, wird Ihnen der Schritt **Fehlende erforderliche Komponenten** angezeigt. Sie können diese Warnung nur ignorieren, wenn Sie dies als eine nicht verwaltete Lösung wieder in die ursprüngliche Organisation importieren möchten. Führen Sie andernfalls die Anweisungen im Dialogfeld aus, um den Export abzubrechen, und fügen Sie die erforderlichen Komponenten hinzu.  
  
5.  Im Schritt **Systemeinstellungen (Erweitert) exportieren** können Sie Systemeinstellungen auswählen, die in Ihre Lösung eingefügt werden. Wenn Ihre Lösung auf einer der Systemeinstellungsgruppen basiert, wählen Sie sie aus, und wählen Sie **Weiter** aus.  
  
     Siehe **Einstellungsoptionen für den Lösungsexport** unten für Details zu den Einstellungen, die für jede Option enthalten sind.  
  
6.  Im Schritt **Pakettyp** müssen Sie auswählen, ob die Lösung als **Nicht verwaltet** oder **Verwaltet** exportiert werden soll.  
  
7.  Im nächsten Schritt können Sie eine Ziellösung für eine bestimmte Dynamics 365-Version auswählen. Diese Option wird in der Regel von ISVs verwendet, die eine Lösung exportieren möchten, welche mit einer früheren Version kompatibel ist. Sofern Sie diese Lösung nicht in eine Organisation importieren möchten, die nicht auf die gleiche Version aktualisiert ist, die Ihre Organisation verwendet, übernehmen Sie die Standardeinstellung.   
  
8.  Wählen Sie **Exportieren** aus, um die Lösungsdatei herunterzuladen.  
  
 Die exakte Verhaltensweise beim Download von Dateien ist bei verschiedenen Browsern unterschiedlich.  

<a name="BKMK_SettingsOptionsOnSolutionExport"></a>  
 
## <a name="settings-options-for-solution-export"></a>Einstellungsoptionen für den Lösungsexport  
 In der folgenden Tabelle sind die verfügbaren Optionen beim Export von Lösungen aufgeführt:  
  
|Gruppe|Einstellung|Beschreibung|  
|-----------|-------------|-----------------|  
|Automatische Nummerierung|Präfix für Kampagnen|Präfix, das für die Nummerierung von Kampagnen verwendet wird.|  
|Präfix für Anfragen|Präfix, das für alle Anfragen in der gesamten App zu verwenden ist.|  
|Präfix für Verträge|Präfix, das für alle Verträge in der gesamten App zu verwenden ist.|  
|Rechnungspräfix|Präfix, das für alle Rechnungsnummern in der gesamten App zu verwenden ist.|  
|Artikelpräfix|Präfix, das für alle Artikel in der App zu verwenden ist.|  
|Auftragspräfix|Präfix, das für alle Aufträge in der gesamten App zu verwenden ist.|  
|Eindeutige Zeichenfolgenlänge|Anzahl der Zeichen, die Rechnungs-, Angebots- und Auftragsnummern angefügt werden.|  
|Kalender|Kalendertyp|Kalendertyp für das System. Standardmäßig Gregorianisch US|  
|Datumsformatcode|Informationen darüber, wie das Datum in Dynamics 365 angezeigt wird.|  
|Datumstrennzeichen|Zeichen, das zur Trennung von Monat, Tag und Jahr in Datumsangaben in der gesamten App verwendet wird.|  
|Max. Termindauer|Maximale Anzahl von Tagen für die Termindauer.|  
|Wochennummer anzeigen|Informationen, die angeben, ob die Wochennummer in Kalenderanzeigen in der gesamten App angezeigt werden soll.|  
|Zeitformatcode|Informationen, die angeben, wie die Uhrzeit in der gesamten App angezeigt wird.|  
|Code für ersten Tag der Woche|Festgelegter erster Wochentag in der gesamten App.|  
|Anpassung|Ist Anwendungsmodus aktiviert|Gibt an, ob das Laden der App in einem Browserfenster ohne Adress-, Symbol- und Menüleiste aktiviert ist.|  
|E-Mail-Nachverfolgung|E-Mail-Versand an nicht aufgelöste Adressen zulassen|Gibt an, ob das Senden von E-Mails an nicht aufgelöste Parteien durch die Benutzer zulässig ist. (Für die Parteien ist weiterhin eine E-Mail-Adresse erforderlich.)|  
|Interne E-Mail ignorieren|Gibt an, ob von App-Benutzern oder -Warteschlangen gesendete eingehende E-Mails nachverfolgt werden sollen.|  
|Max. Nachverfolgungsnummer|Maximale Nachverfolgungsnummer, bevor Recycling ausgeführt wird.|  
|Sicheren Frame für E-Mail anzeigen|Flag, um den Text einer E-Mail im Webformular in einem IFRAME mit dem Sicherheitsattribut „restricted“ wiederzugeben. Dies ist eine zusätzliche Sicherheitsmaßnahme, die jedoch zu einer Aufforderung zur Eingabe von Anmeldeinformationen führen kann.|  
|Nachverfolgungspräfix|Verlaufsliste der Nachverfolgungstoken-Präfixe.|  
|Nachverfolgungstoken-Basis|Basisnummer zur Bereitstellung separater Nachverfolgungstoken-Bezeichner für Benutzer, die zu verschiedenen Bereitstellungen gehören.|  
|Nachverfolgungstoken-Stellen|Anzahl der Stellen zur Darstellung eines Nachverfolgungstoken-Bezeichners.|  
|Allgemein|Anlagen blockieren|Verhindern des Uploads oder Downloads bestimmter Anlagentypen, die als gefährlich eingestuft werden.|  
|Währungsformatcode|Informationen darüber, wie Währungssymbole in der gesamten App verwendet werden.|  
|Währungssymbol|Währungssymbol|  
|Reihenfolge für Anzeige des vollständigen Namens|Reihenfolge, in der Namen in der gesamten App anzuzeigen sind.|  
|Präsenz aktiviert|Informationen darüber, ob die Instant Messaging-Präsenz aktiviert ist.|  
|Negativformat|Informationen, die angeben, wie negative Zahlen in der gesamten App angezeigt werden.|  
|Zahlenformat|Gibt an, wie Zahlen in der gesamten App angezeigt werden.|  
|Preisdezimalstellen|Anzahl der Dezimalstellen, die für Preise verwendet werden können.|  
|Bei Zuweisung für bisherigen Besitzer freigeben|Informationen, die angeben, ob bei der Zuweisung eine Freigabe für den bisherigen Besitzer erteilt wird.|  
|Marketing|Automatische Reaktionserstellung zulassen|Gibt an, ob die automatische Erstellung von Reaktionen zulässig ist.|  
|Automatische Kündigung zulassen|Gibt an, ob die automatische Kündigung von Abonnements zulässig ist.|  
|Automatische Kündigungsbestätigung zulassen|Gibt an, ob das Senden einer E-Mail zur automatischen Bestätigung der Kündigung von Abonnements zulässig ist.|  
|Marketing-E-Mail-Ausführung zulassen|Gibt an, ob die Ausführung von Marketing-E-Mails zulässig ist.|  
| Outlook-Synchronisierung|Adressbuchsynchronisierung zulassen|Gibt an, ob in Microsoft Office Outlook die Adressbuchsynchronisierung im Hintergrund zulässig ist.|  
|Geplante Offlinesynchronisierung zulassen|Gibt an, ob in Office Outlook die Offlinesynchronisierung im Hintergrund zulässig ist.|  
|Geplante Synchronisierung zulassen|Gibt an, ob geplante Synchronisierungsvorgänge mit Outlook zulässig sind.|  
|Abruffrequenz für E-Mail-Versand|Normale Abruffrequenz zum Senden von E-Mails in Outlook.|  
|Mindestfrequenz für Adressensynchronisierung|Normale Abruffrequenz für Adressbuchsynchronisierung in Outlook.|  
|Mindestfrequenz für Offlinesynchronisierung|Normale Abruffrequenz für Hintergrund-Offlinesynchronisierung in Outlook.|  
|Mindestfrequenz für Synchronisierung|Kürzeste zulässige Zeitspanne zwischen geplanten [!INCLUDEOutlook-Synchronisierungsvorgängen.|  
|Max. Zyklen für automatische Kennzeichnung|Maximale Anzahl aggressiver Abrufzyklen, die für die automatische E-Mail-Kennzeichnung beim Empfang neuer E-Mails ausgeführt werden.|  
|Intervall für automatische Kennzeichnung|Normale Abruffrequenz für die automatische E-Mail-Kennzeichnung in Outlook.|  
|ISV-Konfiguration|Servicekalender-Darstellungs-Konfiguration|Sie können visuelle Stile für Dienst-Kalender definieren.

Weitere Informationen: [Servicekalender-Darstellungs-Konfiguration](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/service-calendar-appearance-configuration)|

  
## <a name="next-steps"></a>Nächste Schritte

[Lösungen und Patches verteilen](use-segmented-solutions-patches-simplify-updates.md)