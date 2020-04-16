---
title: Verhalten und Format des Datums- und Uhrzeitfelds in Common Data Service | MicrosoftDocs
ms.custom: ''
ms.date: 05/25/2018
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
ms.assetid: 73d691c7-344e-4c96-8979-c661c290bf81
caps.latest.revision: 47
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d89f040bf7030706f9f7288021249e3b78dcd3e5
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "3167056"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>Funktionsweise und Format des Datums- und Uhrzeitfelds

In Common Data Service wird der Datum und Uhrzeit-Datentyp in vielen Standardentitätsfeldern verwendet. Je nachdem, was das Feld darstellt, können Sie viele andere Feldverhalten auswählen: **Ortszeit Benutzer**, **Nur Datum** oder **zeitzonenunabhängig**.  
  
<a name="Behavior"></a>   

## <a name="date-and-time-field-behavior-and-format"></a>Verhalten und Format des Datums- und Uhrzeitfelds  

Die folgende Tabelle enthält Informationen zum Verhalten und Format des Datums- und Uhrzeitfelds.  
  
|Verhalten|Format|Beschreibung|  
|--------------|------------|-------------------------------|  
|**Ortszeit Benutzer** |**Nur Datum**<br />- oder -<br />**Datum und Uhrzeit**|Dies sind die standardmäßig benutzerdefinierten Datums- und Zeitfelder.<br /><br />Die Feldwerte werden auch in der Ortszeit des aktuellen Benutzers angezeigt.<br />In Webdiensten werden diese Werte mithilfe eines allgemeinen UTC-Zeitzonenformats zurückgegeben.<br /><br />Sie können dies ein Mal festlegen, wenn Sie das Standardverhalten auswählen. Weitere Informationen [Ortszeit Benutzerverhalten ändern](#change-user-local-behavior)|  
|**Nur Datum**|**Nur Datum**|Keine Zeitzonen-Konvertierung<br /><br />Der Zeitteil des Werts ist immer 00:00 Uhr.<br />Der Datumsteil des Werts wird gespeichert und abgerufen, wie in der Benutzeroberfläche und in den Webdiensten angegeben.|  
|**Zeitzonenunabhängig**|**Nur Datum**<br />- oder -<br />**Datum und Uhrzeit**|Keine Zeitzonen-Konvertierung<br /><br />Die Datums- und Uhrzeitwerte werden gespeichert und abgerufen, wie in der Benutzeroberfläche und in den Webdiensten angegeben.|  

## <a name="change-user-local-behavior"></a>Ortszeit Benutzerverhalten ändern:

Sofern der Herausgeber einer verwalteten Lösung dies verhindert, können Sie das Verhalten eines vorhandenen benutzerdefinierten Datumsfeldes von **Ortszeit Benutzer** zu **Nur Datum** oder **Zeitzonenunabhängig** ändern. Dies ist eine einmalige Änderung.

Das Ändern des Feldverhaltens wirkt sich auf die Feldwerte aus, die hinzugefügt oder geändert werden, nachdem das Feldverhalten geändert wurde. Die vorhandenen Werte des Felds bleiben in der Datenbank im UTC-Zeitzonenformat. Um das Verhalten der vorhandenen Feldwerte von UTC in "Nur Datum" zu ändern, benötigen Sie unter Umständen Unterstützung eines Entwicklers, der dies programmgesteuert bearbeitet. Weitere Information: [Konvertieren des Verhaltens von Datums- und Uhrzeitwerten in der Datenbank](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#convert-behavior-of-existing-date-and-time-values-in-the-database). 

> [!WARNING]
> Bevor Sie das Verhalten eines Datums- und Zeitfelds ändern, sollten Sie alle Abhängigkeiten des Felds wie Geschäftsregeln, Workflows und berechnete oder Rollupfelder überprüfen, um sicherzustellen, dass als Ergebnis der Änderung des Verhaltens keine Probleme auftreten. Nach der Änderung des Verhaltens eines Datums- und Uhrzeitfelds sollten Sie alle Geschäftsregeln, Workflows, berechneten Felder und Rollupfelder öffnen, die von dem geänderten Feld abhängig sind, die Informationen überprüfen und speichern, um sicherzustellen, dass das aktuelle Verhalten eines Datums- und Uhrzeitfelds und der aktuelle Wert verwendet werden. 

### <a name="change-behavior-during-a-solution-import"></a>Änderungsverhalten während eines Imports

Wenn Sie eine Lösung importieren, die ein Datenfeld enthält, mithilfe des Verhaltens **Ortszeit Benutzer**-Verhalten enthält, haben Sie die Option, das Verhalten für **Nur Datum** oder **Zeitzonen-Unabhängiger** zu ändern.  

### <a name="prevent-changing-behavior"></a>Verhindert das Ändern des Verhaltens

Wenn Sie ein benutzerdefiniertes Datumsfeld in einer verwalteten Lösung verteilen, können Sie verhindern, dass Personen mithilfe Ihrer Lösung das Verhaltens ändern, indem Sie die Einstellung **CanChangeDateTimeBehavior** auf **False** festlegen. Weitere Informationen: [Verwaltete Eigenschaften für Felder festlegen](set-managed-properties-for-field.md)
  
## <a name="use-cases"></a>Anwendungsfälle 

Überprüfen Sie die folgenden Anwendungsfälle für **Nur Datum** und **Zeitzonenunabhängig**.

### <a name="date-only-scenario-birthdays-and-anniversaries"></a>Nur Datum Szenario: Geburtstage und Jahrestage

Das „Nur Datum“-Verhalten ist gut für Anfragen, wenn Informationen zur Uhrzeit des Tages und die Zeitzone nicht erforderlich sind, wie Geburtstage oder Jahrestage. Dank dieser Option sehen alle App-Benutzer auf der ganzen Welt den exakt gleichen Datumswert.  
  
### <a name="time-zone-independent-scenario-hotel-check-in"></a>Zeitzonenunabhängigs Szenario: Einchecken im Hotel

Sie können dieses Verhalten verwenden, wenn keine Zeitzoneninformationen erforderlich sind, wie die Hoteleincheckzeit. Dank dieser Option sehen alle App-Benutzer auf der ganzen Welt den exakt gleichen Datums- und Uhrzeitwert.  


## <a name="best-practices-for-using-time-zone"></a>Bewährte Methoden für die Verwendung der Zeitzone

### <a name="for-my-datetime-field-i-was-expecting-utclocal-and-i-am-seeing-the-opposite-value"></a>Für mein Feld Datum/Uhrzeit habe ich die Anzeige von (UTC/Lokal) erwartet, sehe aber den entgegengesetzten Wert

Dies wird durch eine mangelnde Parität zwischen der Entitätsfeldeinstellung und der App-Formulareinstellung verursacht. Wenn ein Entitätsfeld für „Zeitzonenunabhängig“ oder „Ortszeit Benutzer“ konfiguriert ist, wird bestimmt, ob die Zeitzonenverschiebung berücksichtigt wird oder nicht, wenn die Daten aus dem Speicher abgerufen werden. Das App-Formular hat jedoch auch die Einstellung UTC oder Lokal. 
 
Dies teilt dem Formular mit, wie die von ihm aus dem Common Data Service empfangenen Daten zu interpretieren sind. Wenn die aus dem Speicher abgerufenen Daten zeitzonenunabhängig sind, das Formular jedoch auf lokal eingestellt ist, werden die UTC-Daten basierend auf der Zeitzone des Benutzers in seinem Profil als lokale Ortszeit des Benutzers angezeigt. Das Gegenteil ist auch der Fall. Ein Wert für „Ortszeit Benutzer“ aus dem Speicher wird als UTC angezeigt, wenn das Formular auf UTC eingestellt ist. Glücklicherweise können die Datums- und Zeitzonenwerte des Formulars geändert werden, ohne die vorhandenen Datensätze zu stören.

### <a name="i-picked-date-only-in-my-entity-field-but-my-form-is-showing-a-time-picker-along-with-the-date"></a>Ich habe in meinem Entitätsfeld die Option „Nur Datum“ ausgewählt, aber in meinem Formular wird eine Zeitauswahl zusammen mit dem Datum angezeigt

Dies würde passieren, wenn Sie für Ihr Feld „Nur Datum“ ein Verhalten wie „Zeitzonenunabhängig“ oder „Ortszeit Benutzer“ auswählen. In Common Data Service wird standardmäßig eine Zeit von 00:00:00 gespeichert, aber wenn Sie das Feld einem Formular hinzufügen, wird davon ausgegangen, dass Sie auch die Zeit einstellen müssen. Wenn Sie die Zeitauswahl im Formular belassen, können Benutzer eine Zeit eingeben, die als etwas anderes als 00:00:00 gespeichert wird. So können Sie das beheben
* Bearbeiten Sie das Formular und entfernen Sie die Zeitauswahl und die zugehörigen Formeln. Dadurch wird die Zeit als 00:00:00 gespeichert und es können weiterhin zeitzonenbasierte Datumsberechnungen durchgeführt werden.
* Wenn Ihr Feld derzeit auf „Ortszeit Benutzer“ eingestellt ist und das Datum nicht zur Berechnung der Zeitzone benötigt wird, können Sie es auf „Nur Datum“ ändern. Dies ist eine dauerhafte Änderung und kann nicht rückgängig gemacht werden. Diese Änderung kann nicht für zeitzonenunabhängige Verhaltensfelder durchgeführt werden. Seien Sie immer vorsichtig, wenn Sie das Verhalten ändern, da andere Apps, Plug-Ins oder Workflows möglicherweise auf die Daten angewiesen sind.

### <a name="i-have-a-date-only-field-but-it-is-showing-the-wrong-date-for-some-users"></a>Ich habe ein Feld „Nur Datum“, aber für einige Benutzer wird das falsche Datum angezeigt
Überprüfen Sie in diesem Fall das Verhalten, das für das Feld „Nur Datum“ eingerichtet wurde. Wenn das Feld auf „Zeitzonenunabhängig“ oder „Ortszeit Benutzer“ eingestellt ist, führt der enthaltene Zeitstempel dazu, dass das Datum für verschiedene Benutzer unterschiedlich angezeigt wird. Die Einstellungen für die Formularanzeige von UTC oder Lokal bestimmen, ob das angezeigte Datum anhand der Zeitzoneneinstellungen des Benutzers berechnet wird oder ob es als UTC-Wert angezeigt wird. Durch Ändern der Formularwerte in UTC anstelle von „Ortszeit Benutzer“ werden Zeitzonenverschiebungsberechnungen verhindert und das UTC-Datum für den gespeicherten Datensatz angezeigt. Wenn dies ein statisches Datum sein soll, das sich nicht ändert, und das Feld derzeit auf „Ortszeit Benutzer“ eingestellt ist, können Sie alternativ das Feldverhalten in „Nur Datum“ ändern. Seien Sie jedoch vorsichtig, da dies nicht rückgängig gemacht werden kann.

### <a name="my-scriptplug-in-is-supposed-to-intercept-the-date-submitted-using-the-universal-client-before-the-user-local-conversion-occurs-but-instead-it-is-being-treated-as-user-local-data"></a>Mein (Skript/Plug-In) sollte das mit dem Universalclient übermittelte Datum abfangen, bevor zu „Ortszeit Benutzer“ gewechselt wird; stattdessen wird es als „Ortszeit Benutzer“-Daten behandelt 

Der Webclient und der Universalclient verhalten sich geringfügig unterschiedlich, wenn Daten zwischen UTC und „Ortszeit Benutzer“ konvertiert werden. Im Webclient werden Daten in den Client eingegeben, wie angegeben an die API übergeben und später in die Ortszeit des Benutzers konvertiert. Auf diese Weise können Skripte/Plug-Ins die Daten abrufen und Maßnahmen ergreifen, bevor die Daten an die Plattformdienste übergeben und in die Ortszeit des Benutzers konvertiert werden. Im Universalclient erfolgt die Konvertierung eines Datums in Werte von „Ortszeit Benutzer“, bevor die Daten an die API übergeben werden. Aus diesem Grund handelt es sich bei den bereitgestellten Daten nicht um ein UTC-Datum, sondern um ein Datum in der Ortszeit des Benutzers, das auf dem Benutzer basiert, der es abgerufen oder geposted hat. Um dies zu beheben, kann ein Benutzer entweder:

* Das Formular in eine zeitzonenunabhängige Form ändern, die den UTC-Wert beibehält. Dies funktioniert nur, wenn der Benutzer das Formular nicht zur Anzeige in der Ortszeit des Benutzers benötigt.
* Das Skript ändern, um die verwendete Zeitzonenverschiebung zu ermitteln, innerhalb des Skripts neu auf UTC berechnen und dann Maßnahmen ergreifen.

## <a name="date-and-time-query-operators-not-supported-for-date-only-behavior"></a>Datums- und Uhrzeitabfrageoperatoren für "Nur Datum"-Verhalten werden nicht unterstützt  

Die folgenden datums- und uhrzeitbezogenen Abfrageoperatoren sind ungültig für das Verhalten **Nur Datum**. Ein "Ungültiger Operator"-Ausnahmefehler wird ausgelöst, wenn einer dieser Operatoren in der Abfrage verwendet wird.  
  
- Älter als X Minuten  
- Älter als X Stunden  
- Letzte X Stunden  
- Nächste X Stunden  

  
### <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von Feldern](create-edit-fields.md)<br />
[Definition berechneter Felder für das Automatisieren von manuellen Berechnungen](define-calculated-fields.md)<br />
[Feld Verwaltete Eigenschaften](set-managed-properties-metadata.md#view-and-edit-field-managed-properties)<br />
[Verwaltete Eigenschaften](solutions-overview.md#managed-properties)  
[Blog: Arbeiten mit Zeitzonen in Common Data Service](https://powerapps.microsoft.com/en-us/blog/working-with-time-zones-in-the-common-data-service/)


