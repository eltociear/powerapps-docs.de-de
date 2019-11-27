---
title: 'Vorschau-Funktion: Verwenden Sie Azure Cosmos DB für SQL-API-Datenanbieter mit Common Data Service | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie die Azure Cosmos DB für SQL-API-Datenanbieter für virtuelle Entitäten konfigurieren.
keywords: SQL API
ms.date: 02/15/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: d0031ffc-8754-4a12-b8c1-e08edc49ff73
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3e9594ada54fb89f77298a4077281dcedbb8c656
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705665"
---
# <a name="preview-feature-azure-cosmos-db-sql-api-data-provider-requirements"></a>Vorschau-Funktion: Azure Cosmos DB für SQL-API-Datenanbieteranforderungen

Dieses Thema beschreibt die Anforderungen für die Azure Cosmos DB für SQL-API-Datenanbieter sowie die Konfiguration und die empfohlenen bewährten Methoden bei der Verwendung der Azure Cosmos DB für SQL-API-Datenanbieter mit virtuellen Entitäten. 

> [!IMPORTANT]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-no-ms-support.md)]


## <a name="what-is-azure-cosmos-db"></a>Was ist Azure Cosmos DB?

Die Azure Cosmos DB ist der global verteilte Multi-Modell-Datenbankservice für funktionskritische Anwendungen von Microsoft. Sie stellt die umfassenden und konsistenten SQL-Abfragen-Funktionen mit niedrigen Wartezeiten zu Schema-losen JSON-Daten bereit. Weitere Informationen: [Einführung in Azure Cosmos DB: SQL-API](https://docs.microsoft.com/azure/cosmos-db/sql-api-introduction)

## <a name="requirements"></a>Anforderungen

- Azure-Abonnement, das Azure Cosmos DB enthält.
- Eine Azure Cosmos DB-SQL-API-Sammlung.
- Der Azure Cosmos DB-Datenbanktyp sollte SQL sein. 

## <a name="data-type-mapping"></a>Datentypzuordnungen

Nehmen wir an, Sie haben ein Azure Cosmos DB-Dokument in einer Sammlung, die *Aufträge* lautet und die die folgende JSON-Struktur hat.

![Beispiel JSON für SQL-API-Dokument.](media/documentdbexample.png)

In dieser Tabelle sind die Datentypzuordnungen für das SQL-API-Dokument in der Sammlung *Aufträge* mit Common Data Service angezeigt.

|SQL API-Daten|Common Data Service|
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
> - Attribute, die im SQL-API-Dokument als optional konfiguriert sind und in Common Data Service als **Eingabe erforderlich** zugeordnet sind, werden einen Laufzeitfehler verursachen.
> - ID-Attributwerte müssen Guids sein.
> - Weitere Informationen zur Nutzung von Daten in SQL-API finden Sie unter [Arbeiten mit Daten in Azure Cosmos DB](https://azure.microsoft.com/blog/working-with-dates-in-azure-documentdb-4/).

## <a name="supported-sql-query-filtering"></a>Unterstützte SQL Abragefilter

SQL-Abfragefilter unterstützt die folgenden Zeichen. 

- Vergleichsoperatoren:`<`,`>`,`<=`, `>=`,`!=`
- Logische Operatoren: `and`, `or` 
- Satzoperatoren: `in`, `not in`
- Zeichenfolgeoperatoren: `like`, `contains`, `begins with`, `ends with`

> [!NOTE]
> Die Verwendung des Gleich-Operators wird in die entsprechenden `contains`/`begins with`/`ends with` Operatoren übersetzt. Die SQL-API unterstützt keine Musterargumente wie im Thema [Like (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql) beschrieben. Die Azure Cosmos DB für SQL-API-Datenanbieter kann den einzelnen Sonderfall `Like('[aA]%')` in `BeginsWith('a')` ODER `BeginsWith('A')` übersetzen. Beachten Sie, dass beim Zeichenfolgenvergleich in SQL API die Groß-/Kleinschreibung beachtet werden muss.

## <a name="add-a-data-source-using-the-azure-cosmos-db-for-sql-api-data-provider"></a>Fügen Sie einen Datenquelle mithilfe der Azure Cosmos DB für SQL-API Datenanbieter hinzu

1. Gehen Sie zu [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.documentdb_data_provider?tab=Overview), wählen Sie **JETZT ABRUFEN** aus, und folgen Sie den Anweisungen, um die Anwendung Ihrer Umgebung mit v9x oder höher hinzuzufügen.
2. Wenn die Lösung installiert wurde, melden Sie an bei der Umgebung an navigieren Sie auf **Einstellungen** >  **Verwaltung** > **Virtuelle Entitäts-Datenquelle**.
3. Wählen Sie auf der Aktionssymbolliste **NEU** und im Dialogfeld **Datenanbieter auswählen** die Option **Azure Cosmos DB für SQL-API-Datenanbieter** aus, und wählen Sie dann **OK** aus.
![Wählen Sie den Azure Cosmos DB für SQL-API-Datenanbieter aus.](media/createdatasource.png)
1. Geben Sie die folgenden Informationen ein und klicken Sie dann auf **Speichern und beenden**.

    |Feld|Beschreibung|
    |--|--|
    |**Name**|Geben Sie einen beschreibenden Namen für die Datenquelle ein.|
    |**Sammlungsname**|Der Name der Azure Cosmos DB-*Datenbank*, die die Sammlung enthält, die in einer virtuellen Entität auftauchen sollen.  |
    |**Autorisierungsschlüssel**|Der primäre oder sekundäre Schlüssel für das Azure Cosmos DB-Konto. Sie können den Schlüssel im Azure-Verwaltungsportal in den **Schlüssel**-Einstellungen im Azure Cosmos DB-Konto anzeigen.|
    |**Uri**|Der URI der Ressourcengruppe, in der sich die Azure Cosmos DB-Sammlung befindet. Die URL wird ähnlich gebildet`https://contoso/documents.azure.com:443`. Sie können die URL im Azure Verwaltungsportal in den **Schlüssel**-Einstellungen für Ihr Azure Cosmos DB-Konto anzeigen. |
    |**Timeout in Sekunden**|Geben Sie die Anzahl der Sekunden ein, um auf eine Antwort des Azure Cosmos DB-Dienstes zu warten, bevor die Datenanfrage beendet wird. Geben Sie z. B. 30 ein, um maximal dreißig Sekunden zu warten, bevor ein Timeout auftritt. Die Standardverzögerung beträgt 120 Sekunden.|

    > [!div class="mx-imgBorder"] 
    > ![So erstellen Sie die Datenquelle mithilfe des SQL-API Datenanbieters.](media/cosmosdb-datasource.png)

## <a name="best-practices-and-limitations"></a>Bewährte Methoden und Einschränkungen

- Beachten Sie Folgendes, wenn Sie Azure Cosmos DB als Datenquelle verwenden:
   - Jede Azure Cosmos DB-Datenquelle kann nur einer virtuellen Entität zugeordnet werden.
   - Sie können mehrere Datenquellen mit derselben Sammlung in Azure Cosmos DB verbinden.
- Sie können die Daten in einer Sammlung nicht nach Entität segmentieren.
- Azure Cosmos DB-Datenbanken benötigen kein Schema, aber die Daten in der Azure Cosmos DB müssen mit Hilfe eines vorhersagbaren Schemas strukturiert werden. 
- Obwohl die Azure Cosmos DB für SQL-API-Datenanbieter die Abfrageübersetzung von Projektions-, Filter- und Sortieroperatoren implementiert, unterstützt sie keine verknüpften Operationen.
- Mit der SQL API können Sie nur nach einer einzigen Spalte filtern.

## <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten](create-edit-virtual-entities.md)
