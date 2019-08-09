---
title: Alternative Schlüssel für Datensätze definieren mit Common Data Service | MicrosoftDocs
description: 'Erfahren Sie, wie Alternativschlüssel definiert werden, die verwendet werden können, um auf Datensätze in Common Data Service zu verweisen'
ms.custom: ''
ms.date: 06/04/2019
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
ms.assetid: 29e53691-0b18-4fde-a1d0-7490aa227898
caps.latest.revision: 10
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="define-alternate-keys-to-reference-records"></a>Definieren von Alternativschlüsseln für den Verweis auf Datensätze

*Alternativschlüsseln* bieten eine genaue und effiziente Methode der Integration mit Daten aus externen Systemen. Wenn ein externes System die IDs des Globally Unique Identifier (GUID) nicht speichern, ist es von größter Wichtigkeit, dass die Datensätze in Common Data Service eindeutig identifiziert werden. 

Ein Datenintegrationssystem verwendet Alternativschlüssel, um Datensätze mit einem oder mehreren Entitätsfeldwerten, die eine eindeutige Kombination darstellen, eindeutig zu identifizieren. Jeder Alternativschlüssel hat einen eindeutigen Namen. 

Möchten Sie beispielsweise einen Firmendatensatz mit einem Alternativschlüssel identifizieren, können Sie die Firmennummer oder das Firmennummernfeld in Verbindung mit mehreren anderen Feldern verwenden, die Werte enthalten, die nicht geändert werden sollten.

> [!NOTE]
> Obwohl Sie Alternativschlüssel mit PowerApps definieren können, können diese aber nur programmgesteuert im Code verwendet werden. Weitere Informationen über die programmgesteuerte Verwendung von Alternativschlüsseln finden Sie unter:   
> - [Entwicklerdokumentation: Verwenden Sie einen Alternativschlüssel, um Datensätze zu erstellen](/dynamics365/customer-engagement/developer/use-alternate-key-create-record) 
> - [Dokumentation für Entwickler: Abrufen eines Datensatzes mit Web-API mithilfe eines Alternativschlüssels](/dynamics365/customer-engagement/developer/webapi/retrieve-entity-using-web-api#retrieve-using-an-alternate-key)

Einige Vorteile der Alternativschlüsselfunktion sind nachfolgend aufgeführt:  
  
- Schnellere Suche der Datensätze.  
- Leistungsfähigere Massendatenvorgänge.  
- Vereinfachte Programmierung mit Daten, die aus externen Systemen ohne -Datensatz-IDs importiert werden.  
  

## <a name="creating-an-alternate-key"></a>Erstellen eines Alternativschlüssels

Sie können zwei Designer verwenden, um Alternativschlüssel zu erstellen:

|Designer| Beschreibung|
|--|--|
|[PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Gibt eine einfache konzentrierte Erfahrung, aber einige Optionen sind nicht verfügbar.<br />Weitere Informationen [Alternativschlüssel mithilfe von PowerApps-Portalen festlegen](define-alternate-keys-portal.md)|
|Projektmappen-Explorer|Nicht so einfach, aber gibt mehr Flexibilität für weniger allgemeine Anforderungen.<br />Weitere Informationen: [Alternativschlüssel mithilfe des Projektmappen-Explorers festlegen](define-alternate-keys-solution-explorer.md) |

> [!NOTE]
> Sie können auch einen Alternativschlüssel in Ihrer Umgebung wie folgt erstellen:
> - Importieren Sie eine Lösung, die die Definition des Alternativschlüssels enthält.
> - Ein Entwickler kann auch Code schreiben, um sie zu erstellen. Weitere Informationen: [Entwicklerdokumentation: Definieren eines Alternativschlüssels für eine Entität](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)

Die Informationen in diesem Thema helfen Ihnen auswählen, welche Designer Sie verwenden können. 

Sie sollten das [PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) verwenden, um Alternative Schlüssel zu erstellen, es sei denn, Sie müssen eine der folgenden Anforderungen erfüllen:

- Erstellen eines Alternativschlüssels in einer Lösung die keine Common Data Service-Standardlösung ist
- Sie möchten den erstellten Systemauftrag, der den Status der Erstellung der unterstützenden Indizes nachverfolgt, ganz leicht nachverfolgen


## <a name="limits-in-creating-alternate-keys"></a>Beschränkungen, bei der Erstellung von Alternativschlüsseln

Es gibt Einschränkungen bei der Alternativschlüsselerstellung.

### <a name="fields-that-can-be-used-for-alternate-keys"></a>Felder, die für Alternativschlüssel verwendet werden können

Nur diese Feldtypen können verwendet werden, um Alternativschlüssel zu erstellen:
 - Decimal
 - Ganze Zahl (Integer)
 - Einzelne Textzeile (String)
 - Datum und Uhrzeit
 - Suchfeld
 - Optionssatz

### <a name="number-of-keys"></a>Anzahl der Schlüssel

Sie können bis zu fünf verschiedene Schlüssel für eine Entität definieren.
 
### <a name="valid-key-size"></a>Gültige Schlüsselgröße

Wenn ein Schlüssel erstellt wurde, überprüft das System, ob dieser Schlüssel von der Plattform unterstützt werden kann, u. a. auch, ob die Gesamtschlüsselgröße nicht gegen die SQL-basierten Indexeinschränkungen verstößt, zum Beispiel 900 Bytes pro Schlüssel und 16 Spalten pro Schlüssel. Wenn die Schlüsselgröße die Einschränkungen nicht erfüllt, wird eine Fehlermeldung angezeigt.

### <a name="unicode-characters-in-key-value"></a>Unicode-Zeichen im Schlüsselwert

Wenn die Daten innerhalb eines Felds, das in einem Alternativschlüssel verwendet wird, eines der folgenden Zeichen enthält `<`,`>`,`*`,`%`,`&`,`:`,`/`,`\\` funktionieren Patarbeiten, und patch- oder upsert-Aktionen nicht. 

Wenn Sie nur Eindeutigkeit benötigen, reicht dieser Ansatz aus, wenn Sie jedoch diese Schlüssel im Rahmen der Datenintegration benötigen, sollten Sie den Schlüssel besser in Feldern ohne Daten mit diesen Zeichen erstellen.

## <a name="track-the-status-of-the-creation-of-the-alternate-key"></a>Verfolgen Sie den Status der Erstellung des Alternativschlüssels nach

Wenn ein Alternativschlüssel erstellt wird, initiiert er einen Systemauftrag, um Indizes für die Datenbanktabellen zu erstellen, um einzigartige Einschränkungen auf den Feldern zu erzwingen, die vom Alternativschlüssel verwendet werden. Der Alternativschlüssel wird nicht wirksam, bis diese Indizes erstellt wurden. Die Erstellung dieser Indizes dauert möglicherweise einige Zeit je nach der Menge der Daten im System. 

Der Status des Systemauftrags legt den Status des Alternativschlüssels fest. Der Alternativschlüssel kann die folgenden Statuswerte aufweisen:
- **Ausstehend**
- **In Bearbeitung**
- **Active**
- **Fehlgeschlagen**

Wenn der Systemauftrag abgeschlossen wurde, ist der Alternativschlüsselstatus **Aktiv** und er kann verwendet werden.

Wenn der Systemauftrag fehlschlägt, suchen Sie den Systemauftrag, um Fehler anzuzeigen. Der Systemauftrag hat einen Namen, der diesem Muster folgt: `Create index for {0} for entity {1}` wobei `0` der **Anzeigename** des Alternativschlüssels ist und `1` der Namen der Entität.


> [!NOTE]
> Wenn Sie den Status des Systemauftrags überwachen möchten, müssen Sie den Projektmappen-Explorer verwenden, um den Index zu erstellen. Er enthält einen Link zum Systemauftrag, um ihn zu überwachen. Weitere Informationen: [(Optional) Zeigen Sie die Indexerstellung bei der Systemauftragsnachverfolgung an](define-alternate-keys-solution-explorer.md#optional-view-the-system-job-tracking-creation-of-indexes)
  
  
### <a name="see-also"></a>Siehe auch  

[Alternativschlüssel mithilfe von PowerApps-Portalen festlegen](define-alternate-keys-portal.md)<br />
[Alternativschlüssel mithilfe des Projektmappen-Explorers festlegen](define-alternate-keys-solution-explorer.md)<br />
[Entwicklerdokumentation: Definieren eines Alternativschlüssels für eine Entität](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)<br />
[Entwicklerdokumentation: Verwenden Sie einen Alternativschlüssel, um Datensätze zu erstellen](/dynamics365/customer-engagement/developer/use-alternate-key-create-record)
