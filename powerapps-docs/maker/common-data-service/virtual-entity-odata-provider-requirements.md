---
title: Verwenden von Virtual Entity OData v4 Data Provider mit Common Data Service | MicrosoftDocs
ms.custom: ''
ms.date: 06/04/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: null
caps.latest.revision: null
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="odata-v4-data-provider-configuration-requirements-and-best-practices"></a> OData v4 Datenanbieterkonfiguration, Anforderungen und bewährten Methoden

In diesem Thema wird beschrieben, wie Sie den OData v4-Datenanbieter konfigurieren sowie Anforderungen und empfohlenen bewährte Methoden für die Verwendung des Datenanbieters ODatas v4 verwenden, um eine Verbindung mit einem OData v4-Webdienst herzustellen. 

## <a name="odata-v4-data-provider-best-practices"></a>OData v4-Datenanbieter - bewährte Methoden

- Common Data Service erfordert, dass alle Entitäten ein ID-Attribut haben. Diese ID ist bekannt als eindeutiger Bezeichner und der Wert muss ein GUID sein.  Sie können nur ID-Felder zu externen Feldern mit dem `Edm.Guid`-Datentyp zuordnen.  Sie können einen `Edm.Int32`-Datentyp nicht einem eindeutigen Bezeichner-Datentypfeld in Common Data Service zuordnen.
-  OData-Entitäten mit auf NULL festlegbaren Eigenschaften müssen so festgelegt werden, dass sie dem zugeordneten Feld in der virtuellen Entität entsprechen. Zum Beispiel muss bei einer OData-Entitätseigenschaft mit Nullable=False das zugeordnete Feld in Common Data Service **Feldanforderung**-Attribut auf **Eingabe erforderlich** festgelegt sein. 
- Für mehrere Abfragen, erhalten Sie, wenn Sie z.B. Daten in einem Raster laden, die Größe des von der externen Datenquelle zurückgegeben Datensets steuern, mithilfe der ausgewählten Filterabfrageparameter.
- Wenn noch nicht aktiviert, sollten Systemadministratoren Plug-in-Ablaufverfolgung aktivierten. Sobald aktiviert, werden alle Fehler im OData-Endpunkt im Plug-in Ablaufverfolgungsprotokoll aufgezeichnet. Weitere Informationen:  [Administratoren-Handbuch: Systemeinstellungen (Dialogfeld) – Anpassung (Registerkarte)](/dynamics365/customer-engagement/admin/system-settings-dialog-box-customization-tab). 

## <a name="data-type-mapping"></a>Datentypzuordnungen

Die folgende Tabelle enthält die OData-EntityData Model (EDM)-Datentypzuordnungen mit Common Data Service-Datentypen. 

|OData-Datentyp|Common Data Service- Datentyp  |
|---------|---------|
|`Edm.Boolean`|Zwei Optionen|
|`Edm.DateTime`|Datum und Uhrzeit|
|`Edm.DateTimeOffset`|Datum und Uhrzeit|
|`Edm.Decimal`|Dezimalzahl oder Währung|
|`Edm.Double`|Gleitkommazahl|
|`Edm.Guid`|Eindeutiger Bezeichner|
|`Edm.Int32`|Ganze Zahl|
|`Edm.Int64`|Ganze Zahl|
|`Edm.String`|Einzelnen Textzeile oder mehrere Textzeilen|


### <a name="odata-edm-data-types-that-are-not-supported-for-mapping-with-virtual-entities"></a>ODate EDM-Datentypen, die nicht zum Zuordnen mit virtuellen Entitäten unterstützt werden 

- `Edm.Binary `
- `Edm.Time` 
- `Edm.Float `
- `Edm.Single` 
- `Edm.Int16` 
- `Edm.Byte` 
- `Edm.SByte`

 
## <a name="add-a-data-source-using-the-odata-v4-data-provider"></a>Hinzufügen einer Datenquelle mithilfe des Datenanbieters OData v4

Dieses Verfahren zeigt, wie Sie den OData-Standarddatenanbieter als virtuelle Datenquelle verwenden.   
  
1. Wählen Sie **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Verwaltung** > **Datenquellen für virtuelle Entitäten** aus.  
1. Klicken Sie auf der Aktionssymbolleiste auf **Neu**.  
1. Wählen Sie im Dialogfenster **Datenanbieter auswählen** aus den folgenden Datenquellen und klicken Sie dann auf **OK**.  
  
    - **OData v4-Datenanbieter**. Common Data Service beinhaltet einen OData v4-Datenanbieter, der verwendet werden kann, um eine Verbindung mit Datenquellen einzurichten, die den offenen Standard OData v4 unterstützen.  
    - *Benutzerdefinierter Datenanbieter*. Wenn Sie ein Datenanbieter-Plug-In importiert haben, wird der Datenanbieter hier angezeigt. Weitere Informationen:  [Entwicklerdokumentation: Erste Schritte mit virtuellen Entitäten](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)  
    
1. Füllen Sie auf der Seite **Neue Datenquelle** Eigenschaften die folgenden Felder aus und speichern Sie den Datensatz.  
  
    - **Name** Geben Sie einen beschreibenden Namen für die Datenquelle ein.  
    - **URI**. Wenn Sie den OData-Datenanbieter verwenden, geben Sie die URI für den OData-Webservice ein. Wenn Sie beispielsweise den OData-Anbieter verwenden, um eine Verbindung zu einem Webservice einzurichten, der in Azure gehostet wird, kann die URI etwa wie folgt aussehen: *`http://contosodataservice.azurewebsites.net/odata/`*  
    - **Timeout in Sekunden**. Geben Sie die Anzahl der Sekunden ein, um auf eine Antwort des Webdiensts zu warten, bevor Timeout Daten erfordern. Geben Sie z.B. 30 ein, um maximal dreißig Sekunden zu warten, bevor ein Timeout auftritt.  
    - **Auslagerungsmodus**. Wählen Sie aus, ob die clientseitige oder serverseitige Auslagerung verwendet wird, um zu steuern, wie Abfrageergebnisse ausgelagert werden. Der Standardwert ist clientseitige Auslagerung. Mit serverseitiger Auslagerung steuert der Server Server, wie Ergebnisse ausgelagert werden, indem der $skiptoken-Parameter verwendet wird, der zur Abfragezeichenfolge hinzugefügt wird. Weitere Informationen:  [Überspringen der Tokensystem-Abfrageoption ($skiptoken)](https://msdn.microsoft.com/library/dd942121.aspx)  
        -  **Inline-Anzahl zurückgeben**. Gibt die Gesamtanzahl Datensätze im Ergebnissatz wieder. Diese Einstellung wird verwendet, um die Funktionalität der nächsten Seite zu aktivieren, wenn Sie Daten zu einem Raster zurückgeben. Verwenden Sie den Wert false, wenn Ihr OData-Endpunkt den Parameter $inclinecount nicht unterstützt. Der Standardwert ist false.
    - **Anforderungsparameter**. Optional können Sie benutzerdefinierte Kopfzeilen- oder Abfragezeichenfolgenparameter hinzufügen, die für die Verbindung mit dem OData-Webservice verwendet werden, wie beispielsweise Authentifizierungsparameter für den externen Service. Klicken Sie auf **Abfragezeichenfolge**, um zwischen dem Kopfzeilen- und Abfragezeichenfolgeparameter und dem Wert umzuschalten. Es können bis zu 10 Kopfzeilen- oder Abfragezeichenfolgen hinzugefügt werden. 
        > [!div class="mx-imgBorder"] 
        > ![Virtuelle Entitätsdatenquellendatensatz](media/virtual-entity-data-source.png) 


## <a name="see-also"></a>Siehe auch  

[Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten](create-edit-virtual-entities.md) <br/>
[TechNet Blog: Interaktion mit Daten aus externen Systemen dank neuer „virtueller“ Entitäten](https://blogs.technet.microsoft.com/lystavlen/2017/09/08/virtual-entities/)
