---
title: Verhalten und Format des Datums- und Uhrzeitfelds in Common Data Service for PowerApps | MicrosoftDocs
ms.custom: ''
ms.date: 05/25/2018
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
ms.assetid: 73d691c7-344e-4c96-8979-c661c290bf81
caps.latest.revision: 47
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>Verhalten und Format des Datums- und Uhrzeitfelds

Im Common Data Service für Apps wird der Datums- und Uhrzeitdatentyp in vielen Standardentitätsfeldern verwendet. Je nachdem, was das Feld darstellt, können Sie viele andere Feldverhalten auswählen: **Ortszeit Benutzer**, **Nur Datum** oder **zeitzonenunabhängig**.  
  
<a name="Behavior"></a>   

## <a name="date-and-time-field-behavior-and-format"></a>Verhalten und Format des Datums- und Uhrzeitfelds  

Die folgende Tabelle enthält Informationen zum Verhalten und Format des Datums- und Uhrzeitfelds.  
  
|Verhalten|Format|Beschreibung|  
|--------------|------------|-------------------------------|  
|**Ortszeit Benutzer** |**Nur Datum**<br />- oder -<br />**Datum und Uhrzeit**|Dies sind die standardmäßig benutzerdefinierten Datums- und Zeitfelder.<br /><br />Die Feldwerte werden auch in der Ortszeit des aktuellen Benutzers angezeigt.<br />In Webdiensten werden diese Werte mithilfe eines allgemeinen UTC-Zeitzonenformats zurückgegeben.<br /><br />Sie können dies ein Mal festlegen, wenn Sie das Standardverhalten auswählen. Weitere Informationen [Ortszeit Benutzerverhalten ändern](#change-user-local-behavior)|  
|**Nur Datum**|**Nur Datum**|Keine Zeitzonen-Konvertierung<br /><br />Der Zeitteil des Werts ist immer 00:00 Uhr.<br />Der Datumsteil des Werts wird gespeichert und abgerufen, wie in der Benutzeroberfläche und in den Webdiensten angegeben.|  
|**Zeitzonenunabhängig**|**Nur Datum**<br />- oder -<br />**Datum und Uhrzeit**|Keine Zeitzonen-Konvertierung<br /><br />Die Datums- und Uhrzeitwerte werden gespeichert und abgerufen, wie in der Benutzeroberfläche und in den Webdiensten angegeben.|  

## <a name="change-user-local-behavior"></a>Ortszeit Benutzerverhalten ändern:

Sofern der Herausgeber einer verwalteten Lösung dies verhindert, können Sie das Verhalten von vorhandene benutzerdefinierte Datumsfelder von **Ortszeit Benutzer** **Nur Datum** oder **Zeitzonenunabhängig** ändern. Dies ist eine einmalige Änderung.

Das Ändern des Feldverhaltens wirkt sich auf die Feldwerte aus, die hinzugefügt oder geändert werden, nachdem das Feldverhalten geändert wurde. Die vorhandenen Werte des Felds bleiben in der Datenbank im UTC-Zeitzonenformat. Um das Verhalten der vorhandenen Feldwerte von UTC in "Nur Datum" zu ändern, benötigen Sie unter Umständen Unterstützung eines Entwicklers, der dies programmgesteuert bearbeitet. Weitere Information: [Konvertieren des Verhaltens von Datums- und Uhrzeitwerten in der Datenbank](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#convert-behavior-of-existing-date-and-time-values-in-the-database). 

> [!WARNING]
> Bevor Sie das Verhalten eines Datums- und Zeitfelds ändern, sollten Sie alle Abhängigkeiten des Felds wie Geschäftsregeln, Workflows und berechnete oder Rollupfelder überprüfen, um sicherzustellen, dass als Ergebnis der Änderung des Verhaltens keine Probleme auftreten. Nach der Änderung des Verhaltens eines Datums- und Uhrzeitfelds sollten Sie alle Geschäftsregeln, Workflows, berechneten Felder und Rollupfelder öffnen, die von dem geänderten Feld abhängig sind, die Informationen überprüfen und speichern, um sicherzustellen, dass das aktuelle Verhalten eines Datums- und Uhrzeitfelds und der aktuelle Wert verwendet werden. 

### <a name="change-behavior-during-a-solution-import"></a>Änderungsverhalten während eines Imports

Wenn Sie eine Lösung importieren, die ein Datenfeld enthält, mithilfe des Verhaltens **Ortszeit Benutzer**-Verhalten enthält, haben Sie die Option, das Verhalten für **Nur Datum** oder **Zeitzonen-Unabhängiger** zu ändern.  

### <a name="prevent-changing-behavior"></a>Verhindert das Ändern des Verhaltens

Wenn Sie ein benutzerdefiniertes Datumsfeld in einer verwalteten Lösung verteilen, können Sie verhindern, dass Personen mithilfe Ihrer Lösung das Verhaltens ändern, indem Sie die Einstellung **CanChangeDateTimeBehavior** auf **False** festlegen. Weitere Informationen: [Feld verwaltete Eigenschaften](set-managed-properties-metadata.md#field-managed-properties)
  
## <a name="use-cases"></a>Anwendungsfälle

Überprüfen Sie die folgenden Anwendungsfälle für **Nur Datum** und **Zeitzonenunabhängig**.

### <a name="date-only-scenario-birthdays-and-anniversaries"></a>Nur Datum Szenario: Geburtstage und Jahrestage

Das "Nur Datum"-Verhalten ist gut für Anfragen, wenn Informationen zur Uhrzeit des Tages und die Zeitzone nicht erforderlich sind, wie Geburtstage oder Jahrestage. Dank dieser Option sehen alle App-Benutzer auf der ganzen Welt den exakt gleichen Datumswert.  
  
### <a name="time-zone-independent-scenario-hotel-check-in"></a>Zeitzonenunabhängigs Szenario: Einchecken im Hotel

Sie können dieses Verhalten verwenden, wenn keine Zeitzoneninformationen erforderlich sind, wie die Hoteleincheckzeit. Dank dieser Option sehen alle App-Benutzer auf der ganzen Welt den exakt gleichen Datums- und Uhrzeitwert.  


## <a name="date-and-time-query-operators-not-supported-for-date-only-behavior"></a>Datums- und Uhrzeitabfrageoperatoren für "Nur Datum"-Verhalten werden nicht unterstützt  

Die folgenden datums- und uhrzeitbezogenen Abfrageoperatoren sind ungültig für das Verhalten **Nur Datum**. Ein "Ungültiger Operator"-Ausnahmefehler wird ausgelöst, wenn einer dieser Operatoren in der Abfrage verwendet wird.  
  
- Älter als X Minuten  
- Älter als X Stunden  
- Letzte X Stunden  
- Nächste X Stunden  

  
### <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von Feldern](create-edit-fields.md)<br />
[Definition berechneter Felder für das Automatisieren von manuellen Berechnungen](define-calculated-fields.md)<br />
[Feld Verwaltete Eigenschaften](set-managed-properties-metadata.md#field-managed-properties)<br />
[Verwaltete Eigenschaften](solutions-overview.md#managed-properties)

