---
title: Verhalten und Format des Datums- und Uhrzeitfelds in Common Data Service für Apps | Microsoft-Dokumentation
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
ms.openlocfilehash: 2f62f2433fe959e3713df544628db186b801731e
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39688564"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>Verhalten und Format des Datums- und Uhrzeitfelds

In Common Data Service für Apps wird der Datentyp Datum/Uhrzeit in vielen Standardentitätsfeldern verwendet. Je nachdem, welche Art von Datum das Feld repräsentiert, können Sie unterschiedliches Feldverhalten auswählen: **Ortszeit Benutzer**, **Nur Datum** oder **Zeitzonenunabhängig**.  
  
<a name="Behavior"></a>   

## <a name="date-and-time-field-behavior-and-format"></a>Verhalten und Format des Datums- und Uhrzeitfelds  

Die folgende Tabelle enthält Informationen zu Verhalten und Format des Datums- und Uhrzeitfelds.  
  
|Verhalten|Format|Beschreibung|  
|--------------|------------|-------------------------------|  
|**Ortszeit Benutzer** |**Nur Datum**<br />oder<br />**Datum und Uhrzeit**|Dies ist das Standardverhalten von benutzerdefinierten Datums- und Uhrzeitfeldern.<br /><br />Die Feldwerte werden in der Ortszeit des aktuellen Benutzers angezeigt.<br />In Webdiensten werden diese Werte in einem allgemeinen UTC-Zeitzonenformat zurückgegeben.<br /><br />Sie können dies einmalig ändern, wenn Sie das Standardverhalten auswählen. Weitere Informationen finden Sie unter [Ändern des Verhaltens „Ortszeit Benutzer“](#change-user-local-behavior).|  
|**Nur Datum**|**Nur Datum**|Keine Zeitzonenkonvertierung.<br /><br />Der Zeitbereich des Werts ist immer 00:00 Uhr.<br />Der Datumsbereich des Werts wird gespeichert und abgerufen, wie in der Benutzeroberfläche und in den Webdiensten angegeben.|  
|**Zeitzonenunabhängig**|**Nur Datum**<br />oder<br />**Datum und Uhrzeit**|Keine Zeitzonenkonvertierung.<br /><br />Die Werte für Datum und Uhrzeit werden gespeichert und abgerufen, wie in der Benutzeroberfläche und in den Webdiensten angegeben.|  

## <a name="change-user-local-behavior"></a>Ändern des Verhaltens „Ortszeit Benutzer“

Wenn der Herausgeber einer verwalteten Lösung es zulässt, können Sie das Verhalten eines vorhandenen benutzerdefinierten Datumsfelds von **Ortszeit Benutzer** auf **Nur Datum** oder **Zeitzonenunabhängig** ändern. Dies ist eine einmalige Änderung.

Die Änderung des Feldverhaltens wirkt sich auf die Feldwerte aus, die nach der Änderung des Verhaltens hinzugefügt oder geändert werden. Die vorhandenen Feldwerte bleiben in der Datenbank im UTC-Zeitzonenformat gespeichert. Wenn Sie das Verhalten der vorhandenen Feldwerte von „UTC“ auf „Nur Datum“ ändern möchten, muss dies ggf. ein Entwickler programmgesteuert für Sie tun. Weitere Informationen finden Sie unter [Konvertieren des Verhaltens von vorhandenen Datums- und Uhrzeitwerten in der Datenbank](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#convert-behavior-of-existing-date-and-time-values-in-the-database). 

> [!WARNING]
> Bevor Sie das Verhalten eines vorhandenen Datums- und Uhrzeitfelds ändern, sollten Sie alle Abhängigkeiten des Feldes überprüfen, z.B. Geschäftsregeln, Workflows, berechnete Felder oder Rollupfelder, um sicherzustellen, dass keine Probleme durch eine Verhaltensänderung auftreten. Nachdem Sie das Verhalten eines Datums- und Uhrzeitfelds geändert haben, sollten Sie jede Geschäftsregel, jeden Workflow, jedes berechnete Feld und jedes Rollupfeld abhängig vom geänderten Feld öffnen, die Informationen überprüfen und speichern, um sicherzustellen, dass das Verhalten und der Wert des neuesten Datums- und Uhrzeitfelds verwendet werden. 

### <a name="change-behavior-during-a-solution-import"></a>Ändern des Verhaltens beim Importieren einer Lösung

Wenn Sie eine Lösung importieren, die ein Datumsfeld mit dem Verhalten **Ortszeit Benutzer** enthält, können Sie ggf. das Verhalten auf **Nur Datum** oder **Zeitzonenunabhängig** ändern.  

### <a name="prevent-changing-behavior"></a>Verhindern von Änderungen am Verhalten

Wenn Sie ein benutzerdefiniertes Datumsfeld in einer verwalteten Lösung verteilen, können Sie verhindern, dass Benutzer, die Ihre Lösung verwenden, das Verhalten ändern. Legen Sie dazu die verwaltete Eigenschaft **CanChangeDateTimeBehavior** auf **FALSE** fest. Weitere Informationen finden Sie unter [Feld „Verwaltete Eigenschaften“](set-managed-properties-metadata.md#field-managed-properties).
  
## <a name="use-cases"></a>Anwendungsfälle

Betrachten Sie die folgenden Anwendungsfälle für das Verhalten **Nur Datum** und **Zeitzonenunabhängig**.

### <a name="date-only-scenario-birthdays-and-anniversaries"></a>Szenario „Nur Datum“: Geburtstage und Jahrestage

Das Verhalten „Nur Datum“ eignet sich für Fälle, in denen keine Informationen zu Tageszeit und Zeitzone benötigt werden, z.B. bei Geburts- oder Jahrestagen. Mit dieser Auswahl sehen alle App-Benutzer weltweit den gleichen Datumswert.  
  
### <a name="time-zone-independent-scenario-hotel-check-in"></a>Szenario „Zeitzonenunabhängig“: Check-in im Hotel

Sie können dieses Verhalten verwenden, wenn keine Zeitzoneninformationen benötigt werden, z.B. Check-in-Uhrzeit im Hotel. Mit dieser Auswahl sehen alle App-Benutzer weltweit den gleichen Datums- und Uhrzeitwert.  


## <a name="date-and-time-query-operators-not-supported-for-date-only-behavior"></a>Abfrageoperatoren für Datum und Uhrzeit: Nicht unterstützt für „Nur Datum“  

Die folgenden Abfrageoperatoren für Datum und Uhrzeit sind für das **Nur Datum**-Verhalten ungültig. Ein ungültiger Operatorausnahmefehler wird ausgelöst, wenn einer dieser Operatoren in der Abfrage verwendet wird.  
  
- Älter als x Minuten  
- Älter als x Stunden  
- Letzte x Stunden  
- Nächste x Stunden  

  
### <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von Feldern](create-edit-fields.md)<br />
[Definieren berechneter Felder zum Automatisieren von manuellen Berechnungen](define-calculated-fields.md)<br />
[Feld „Verwaltete Eigenschaften“](set-managed-properties-metadata.md#field-managed-properties)<br />
[Verwaltete Eigenschaften](solutions-overview.md#managed-properties)

