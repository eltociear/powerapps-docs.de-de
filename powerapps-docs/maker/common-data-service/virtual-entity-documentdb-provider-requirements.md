---
title: Verwenden Sie den Azure Cosmos DB for SQL API Datenanbieter mit Common Data Service for Apps | MicrosoftDocs
description: 'Erfahren Sie, wie Sie die Azure Cosmos Datenbank für SQL API Datenanbieter mit virtuellen Entitäten verwenden.'
keywords: SQL API
ms.date: 06/27/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: d0031ffc-8754-4a12-b8c1-e08edc49ff73
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: null
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="preview-feature-azure-cosmos-db-sql-api-data-provider-requirements"></a>Vorschau-Funktion: Azure Cosmos DB für SQL API Datenanbieteranforderungen

Dieses Thema beschreibt die Anforderungen an den Azure Cosmos DB for SQL API Datenanbieter sowie die Konfiguration und die empfohlenen bewährten Methoden bei der Verwendung des Azure Cosmos DB for SQL API Datenanbieters mit virtuellen Entitäten. 

> [!IMPORTANT]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-no-ms-support.md)]


## <a name="what-is-azure-cosmos-db"></a>Was ist Azure Cosmos Datenbank?

Azure Cosmos DB ist Microsofts weltweit verteilter Multi-Model-Datenbankdienst für unternehmenskritische Anwendungen. Sie stellt die umfassenden und konsistenten SQL-Abfragen-Funktionen mit niedrigen Wartezeiten zu Schema-losen JSON-Daten bereit. Weitere Informationen: [Einführung in die Azure Cosmos Datenbank: SQL-API](https://docs.microsoft.com/azure/cosmos-db/sql-api-introduction)

## <a name="requirements"></a>Anforderungen

- Azure Abonnement mit Azure Cosmos DB.
- Eine Azure Cosmos DB SQL API Sammlung.
- Der Datenbanktyp Azure Cosmos DB sollte SQL sein. 

## <a name="data-type-mapping"></a>Datentypzuordnungen

Angenommen, Sie haben ein Azure Cosmos DB-Dokument in einer Sammlung mit dem Namen *Orders*, das die folgende JSON-Struktur hat.

![Beispiel JSON für SQL-API-Dokument.](media/documentdbexample.png)

Diese Tabelle zeigt die Datentypzuordnungen für das SQL-API-Dokument in der Sammlung *Orders* mit Common Data Service for Apps.

|SQL API-Daten|CDS for Apps|
|--|--|
|`id`|Primärschlüssel|
|`name`|Einzelne Textzeile|
|`quantity`|Ganze Zahl|
|`orderid`|Einzelne Textzeile|
|`ordertype`|Optionssatz|
|`amount`|Dezimalzahl oder Währung|
|`delivered`|Zwei Optionen|
|`datetimeoffset`|Datum und Uhrzeit|

> [!NOTE]
> - Attribute mit dem Präfix des Unterstrichs (_) werden durch die SQL API generiert«».
> - Attribute, die im SQL API-Dokument als optional konfiguriert sind und in CDS for Apps als **Eingabe erforderlich** zugeordnet sind, werden einen Laufzeitfehler verursachen.
> - ID-Attributwerte müssen Guids sein.
> - Weitere Informationen zur Nutzung von Daten in SQL API finden Sie unter [Arbeiten mit Daten in Azure Cosmos DB](https://azure.microsoft.com/blog/working-with-dates-in-azure-documentdb-4/).

## <a name="supported-sql-query-filtering"></a>Unterstützte SQL Abragefilter

SQL-Abfragefilter unterstützt die folgenden Zeichen. 

- Vergleichsoperatoren:`<`,`>`,`<=`, `>=`,`!=`
- Logische Operatoren: `and`, `or` 
- Satzoperatoren: `in`, `not in`
- Zeichenfolgeoperatoren: `like`, `contains`, b`egins with`, `ends with`

> [!NOTE]
> Die Verwendung des Gleich-Operators wird in die entsprechenden `contains`/`begins with`/`ends with` Operatoren übersetzt. Die SQL-API unterstützt keine Musterargumente wie im Thema [Like (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql) beschrieben. Der Azure Cosmos DB for SQL API Data Provider kann den einzelnen Sonderfall `Like('[aA]%')` in `BeginsWith('a')` ODER `BeginsWith('A')` übersetzen. Beachten Sie, dass beim Zeichenfolgenvergleich in SQL API die Groß-/Kleinschreibung beachtet werden muss.

## <a name="add-a-data-source-using-the-azure-cosmos-db-for-sql-api-data-provider"></a>Fügen Sie einen Datenquelle mithilfe dem Azure Cosmos DB für SQL-API Datenanbieter hinzu.

1. Gehen Sie zu [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.documentdb_data_provider?tab=Overview), klicken Sie auf **JETZT ABRUFEN**, und folgen Sie den Anweisungen, um die Anwendung Ihrer Umgebung mit v9x oder höher hinzuzufügen.
2. Wenn die Lösung installiert wurde, melden Sie an bei der Umgebung an navigieren Sie auf **Einstellungen** >  **Verwaltung** > **Virtuelle Entitäts-Datenquelle**.
3. Auf der Aktionssymbolliste klicken Sie auf **NEU** und im Dialogfeld **Datenanbieter auswählen** die Option **Azure Cosmos DB für DocumentDB API Datenanbieter** und anschließend auf **OK**
![Wählen Sie den Azure Cosmos DB für SQL API-Datenanbieter](media/createdatasource.png)
1. Geben Sie die folgenden Informationen ein und klicken Sie dann auf **Speichern und beenden**.

    |Feld|Beschreibung|
    |--|--|
    |**Name**|Geben Sie einen beschreibenden Namen für die Datenquelle ein.|
    |**Sammlungsname**|Die ID der Azure Cosmos DB Datenbank-Sammlung, die die Daten enthält, die in einer virtuellen Entität auftauchen sollen.  |
    |**Autorisierungsschlüssel**|Der Primär- oder Sekundärschlüssel für das Azure Cosmos DB-Konto. Sie finden den Schlüssel aus dem Azure Admin-Portal unter der **Schlüssel**-Einstellung in Ihrem Azure Cosmos DB-Konto.|
    |**Uri**|Die URI der Ressourcengruppe, in der sich die Azure Cosmos DB-Sammlung befindet. Die URL wird ähnlich gebildet`https://contoso/documents.azure.com:443`. Sie finden die URI aus dem Azure Admin-Portal unter der **Schlüssel**-Einstellung für Ihr Azure Cosmos DB-Konto. |
    |**Timeout in Sekunden**|Geben Sie die Anzahl der Sekunden ein, die auf eine Antwort des Azure Cosmos DB-Dienstes gewartet werden soll, bevor eine Zeitüberschreitung bei der Datenanforderung eintritt. Geben Sie beispielsweise 30 ein, um maximal 30 Sekunden zu warten, bevor ein Timeout eintritt. Die Standardverzögerung beträgt 120 Sekunden.|

    > [!div class="mx-imgBorder"] 
    > ![So erstellen Sie die Datenquelle mithilfe des SQL-API Datenanbieters.](media/cosmosdb-datasource.png)

## <a name="best-practices-and-limitations"></a>Bewährte Methoden und Einschränkungen

- Beachten Sie Folgendes, wenn Sie Azure Cosmos DB als Datenquelle verwenden:
   - Jede Azure Cosmos DB-Datenquelle kann nur einer einzelnen virtuellen Entität zugeordnet werden.
   - Sie können mehrere Datenquellen mit derselben Sammlung in Azure Cosmos DB verbinden.
- Sie können die Daten in einer Sammlung nicht nach Entität segmentieren.
- Azure Cosmos DB-Datenbanken benötigen kein Schema, aber die Daten in Azure Cosmos DB müssen mithilfe eines vorhersagbaren Schemas strukturiert werden. 
- Obwohl der Azure Cosmos DB for SQL API-Datenanbieter die Anfrage in einen Projektions-, Filter- und Sortieroperator übersetzt, unterstützt er keine verknüpften Operationen.
- Mit der SQL API können Sie nur nach einer einzigen Spalte filtern.

## <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten](create-edit-virtual-entities.md)
