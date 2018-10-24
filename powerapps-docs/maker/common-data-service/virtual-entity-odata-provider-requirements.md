---
title: Verwenden des OData v4-Datenanbieters für virtuelle Entitäten mit Common Data Service für Apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/04/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: ''
caps.latest.revision: ''
author: Mattp123
ms.author: matp
manager: brycho
ms.openlocfilehash: 0bd2aed852b5d7eb9b354f30978725b1386a89aa
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39687305"
---
# <a name="odata-v4-data-provider-configuration-requirements-and-best-practices"></a>Konfiguration, Anforderungen und bewährte Methoden für OData v4-Datenanbieter

In diesem Thema wird beschrieben, wie der OData v4-Datenanbieter konfiguriert wird. Außerdem werden die Anforderungen und die empfohlenen bewährten Methoden für die Verwendung des OData v4-Datenanbieters für eine Verbindung mit einem OData v4-Webdienst erläutert. 

## <a name="odata-v4-data-provider-best-practices"></a>Bewährte Methoden für OData v4-Datenanbieter

- Common Data Service für Apps erfordert, dass alle Entitäten ein ID-Attribut enthalten. Diese ID wird als eindeutiger Bezeichner bezeichnet, und ihr Wert muss eine GUID sein.  Sie können ID-Felder nur externen Feldern mit dem Datentyp `Edm.Guid` zuordnen.  Sie können keinen `Edm.Int32`-Datentyp dem Datentypfeld eines eindeutigen Bezeichners in CDS für Apps zuordnen.
-  OData-Entitäten mit Eigenschaften, die Nullwerte zulassen, müssen so festgelegt werden, dass sie dem zugeordneten Feld in der virtuellen Entität entsprechen. Beispiel: Für eine OData-Entitätseigenschaft mit „Nullable=False“ muss das zugeordnete Feld im CDS für Apps-Attribut **Feldanforderung** auf **Eingabe erforderlich** festgelegt sein. 
- Beim Abrufen mehrerer Abfragen, z.B. beim Laden von Daten in einem Raster, steuern Sie die Größe des Datasets, das von der externen Datenquelle zurückgegeben wird, mit den Auswahl- und Filterabfrageparametern.
- Wenn nicht bereits aktiviert, sollten Systemadministratoren die Plug-In-Ablaufverfolgung aktivieren. Nach der Aktivierung werden alle Fehler vom OData-Endpunkt im Plug-In-Ablaufverfolgungsprotokoll erfasst. Weitere Informationen finden Sie unter [Administratorhandbuch: Systemeinstellungen (Dialogfeld) – Anpassung (Registerkarte)](/dynamics365/customer-engagement/admin/system-settings-dialog-box-customization-tab) 

## <a name="data-type-mapping"></a>Datentypzuordnung

Die folgende Tabelle enthält die Datentypzuordnungen des OData Entity Data Model (EDM) zu CDS für Apps-Datentypen. 

|OData-Datentyp|CDS für Apps-Datentyp  |
|---------|---------|
|`Edm.Boolean`|Zwei Optionen|
|`Edm.DateTime`|Datum und Uhrzeit|
|`Edm.DateTimeOffset`|Datum und Uhrzeit|
|`Edm.Decimal`|Dezimalzahl oder Währung|
|`Edm.Double`|Gleitkommazahl|
|`Edm.Guid`|Eindeutiger Bezeichner|
|`Edm.Int32`|Ganze Zahl|
|`Edm.Int64`|Ganze Zahl|
|`Edm.String`|Einzelne Textzeile oder mehrere Textzeilen|


### <a name="odata-edm-data-types-that-are-not-supported-for-mapping-with-virtual-entities"></a>OData EDM-Datentypen, die für die Zuordnung zu virtuellen Entitäten nicht unterstützt werden 

- `Edm.Binary `
- `Edm.Time` 
- `Edm.Float `
- `Edm.Single` 
- `Edm.Int16` 
- `Edm.Byte` 
- `Edm.SByte`

 
## <a name="add-a-data-source-using-the-odata-v4-data-provider"></a>Hinzufügen einer Datenquelle mithilfe des OData v4-Datenanbieters

Dieses Verfahren zeigt, wie Sie den sofort einsetzbaren OData-Datenanbieter als virtuelle Entitätsdatenquelle verwenden können.   
  
1. Wechseln Sie zu  **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Verwaltung** > **Virtuelle Entitätsdatenquellen**.  
1. Klicken Sie auf der Aktionssymbolleiste auf **Neu**.  
1. Wählen Sie im Dialogfeld **Datenanbieter auswählen** aus den folgenden Datenquellen, und klicken Sie dann auf **OK**.  
  
    - **OData v4-Datenanbieter**. CDS für Apps enthält einen Odata v4-Datenanbieter, der für Verbindungen mit Datenquellen verwendet werden kann, die den offenen OData v4-Standard unterstützen.  
    - *Benutzerdefinierter Datenanbieter*. Wenn Sie ein Datenanbieter-Plug-In importiert haben, wird der Datenanbieter hier angezeigt. Weitere Informationen finden Sie unter [Dokumentation für Entwickler: Erste Schritte mit virtuellen Entitäten](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)  
    
1. Füllen Sie auf der Eigenschaftenseite **Neue Datenquelle** die folgenden Felder aus, und speichern Sie dann den Datensatz.  
  
    - **Name**. Geben Sie einen Namen ein, der die Datenquelle beschreibt.  
    - **URI**. Wenn Sie den OData-Datenanbieter verwenden, geben Sie den URI für den OData-Webdienst ein. Beispiel: Wenn Sie mit dem OData-Anbieter eine Verbindung mit einem in Azure gehosteten Webdienst herstellen, kann der URI *`http://contosodataservice.azurewebsites.net/odata/`* lauten.  
    - **Timeout in Sekunden**. Geben Sie die Anzahl von Sekunden ein, die auf eine Antwort vom Webdienst gewartet werden soll, bevor ein Timeout der Datenanforderung eintritt. Geben Sie beispielsweise 30 ein, um maximal 30 Sekunden zu warten, bevor ein Timeout eintritt.  
    - **Auslagerungsmodus**. Wählen Sie, ob clientseitige oder serverseitige Auslagerung verwendet wird, um zu steuern, wie die Abfrageergebnisse ausgelagert werden. Der Standardwert ist eine clientseitige Auslagerung. Bei der serverseitigen Auslagerung steuert der Server die Auslagerung der Ergebnisse mit dem Parameter „$skiptoken“, der der Abfragezeichenfolge hinzugefügt wird. Weitere Informationen finden Sie unter [Skip Token System Query Option ($skiptoken)](https://msdn.microsoft.com/library/dd942121.aspx) (Systemabfrageoption zum Überspringen von Token ($skiptoken))  
        -  **Inlineanzahl zurückgeben**. Gibt die Gesamtanzahl der Datensätze im Resultset zurück. Diese Einstellung wird verwendet, um die Funktionalität für die nächste Seite beim Zurückgeben von Daten in ein Raster zu aktivieren. Verwenden Sie den Wert „false“, wenn Ihr OData-Endpunkt den OData-Parameter „$inclinecount“ nicht unterstützt. Der Standardwert ist „false“.
    - **Anforderungsparameter**. Optional können Sie benutzerdefinierte Header- oder Abfragezeichenfolgen-Parameter für die Verbindung mit dem OData-Webdienst hinzufügen, z.B. Authentifizierungsparameter für den externen Dienst. Klicken Sie auf **Abfragezeichenfolge**, um zwischen Header- und Abfragezeichenfolgen-Parameter und Wert umzuschalten. Bis zu 10 Header- oder Abfragezeichenfolgen können hinzugefügt werden. 
        ![Datensatz einer virtuellen Entitätsdatenquelle](media/virtual-entity-data-source.png) 


## <a name="see-also"></a>Siehe auch  

[Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten](create-edit-virtual-entities.md) <br/>
[TechNet Blog: Interact with data from external systems using the new virtual entities](https://blogs.technet.microsoft.com/lystavlen/2017/09/08/virtual-entities/) (TechNet-Blog: Interagieren mit Daten aus externen Systemen über neue virtuelle Entitäten)
