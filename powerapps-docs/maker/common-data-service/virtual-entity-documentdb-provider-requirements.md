---
title: 'Previewfunktion: Verwenden des Azure Cosmos DB für SQL-API-Datenanbieters mit Common Data Service für Apps | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie den Azure Cosmos DB für SQL-API-Datenanbieter für die Verwendung mit virtuellen Entitäten konfigurieren.
keywords: SQL-API
ms.date: 06/27/2018
ms.service: crm-online
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
ms.openlocfilehash: fa45376dff85205a0dfbf28334c678293528d00e
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39688594"
---
# <a name="preview-feature-azure-cosmos-db-sql-api-data-provider-requirements"></a>Previewfunktion: Azure Cosmos DB für SQL-API-Datenanbieter – Anforderungen

In diesem Thema werden die Anforderungen an den Azure Cosmos DB für SQL-API-Datenanbieter, seine Konfiguration und empfohlene Best Practices für seine Verwendung mit virtuellen Entitäten beschrieben. 

> [!IMPORTANT]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-no-ms-support.md)]


## <a name="what-is-azure-cosmos-db"></a>Was ist Azure Cosmos DB?

Azure Cosmos DB ist der global verteilte Datenbankdienst von Microsoft mit mehreren Modellen für unternehmenskritische Anwendungen. Er stellt umfassende und vertraute SQL-Abfragefunktionen mit einheitlich geringen Latenzen für schemalose JSON-Daten bereit. Weitere Informationen finden Sie unter [Einführung in Azure Cosmos DB: SQL-API](https://docs.microsoft.com/azure/cosmos-db/sql-api-introduction).

## <a name="requirements"></a>Anforderungen

- Ein Azure-Abonnement mit Azure Cosmos DB
- Eine SQL-API-Sammlung von Azure Cosmos DB
- Der Azure Cosmos DB-Datenbanktyp muss SQL sein 

## <a name="data-type-mapping"></a>Zuordnen von Datentypen

Angenommen, Sie haben ein Azure Cosmos DB-Dokument in einer Sammlung namens *Aufträge* mit der folgenden JSON-Struktur:

![JSON-Beispiel für SQL-API-Dokument](media/documentdbexample.png)

Diese Tabelle zeigt die Datentypzuordnungen für das SQL-API-Dokument in der Sammlung *Aufträge* mit Common Data Service (CDS) für Apps.

|SQL-API-Daten|CDS für Apps|
|--|--|
|`id`|Primärschlüssel|
|`name`|Eine Textzeile|
|`quantity`|Ganze Zahl|
|`orderid`|Eine Textzeile|
|`ordertype`|Optionssatz|
|`amount`|Dezimalzahl oder Währung|
|`delivered`|Zwei Optionen|
|`datetimeoffset`|Datum und Uhrzeit|

> [!NOTE]
> - Attribute mit einem Unterstrich (_) als Präfix werden mit der SQL-API generiert.
> - Attribute, die im SQL-API-Dokument als optional konfiguriert sind und in CDS für Apps als **Eingabe erforderlich** zugeordnet werden, verursachen einen Laufzeitfehler.
> - ID-Attributwerte müssen GUIDs sein.
> - Weitere Informationen zum Verwenden von Datumsangaben in SQL-API finden Sie unter [Datumsangaben in Azure Cosmos DB](https://azure.microsoft.com/blog/working-with-dates-in-azure-documentdb-4/).

## <a name="supported-sql-query-filtering"></a>Unterstützte SQL-Abfragefilter

Die SQL-Abfragefilter unterstützen die folgenden Operatoren. 

- Vergleichsoperatoren: `<`, `>`, `<=`, `>=`, `!=`
- Logische Operatoren: `and`, `or` 
- Mengenoperatoren: `in`, `not in`
- Zeichenfolgenoperatoren: `like`, `contains`, b`egins with`, `ends with`

> [!NOTE]
> Beim Verwenden des „like“-Operators wird dieser in den entsprechenden Operator `contains`/`begins with`/`ends with` konvertiert. Die SQL-API unterstützt keine Musterargumente, wie im Thema [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql) erläutert. Azure Cosmos DB für SQL-API-Datenanbieter kann die einzige Ausnahme `Like('[aA]%')` in `BeginsWith('a')` ODER `BeginsWith('A')` konvertieren. Beachten Sie, dass der Zeichenfolgenvergleich in der SQL-API die Groß-/Kleinschreibung berücksichtigt.

## <a name="add-a-data-source-using-the-azure-cosmos-db-for-sql-api-data-provider"></a>Hinzufügen einer Datenquelle mit dem Azure Cosmos DB für SQL-API-Datenanbieter

1. Öffnen Sie [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.documentdb_data_provider?tab=Overview), wählen Sie **JETZT HOLEN** aus, und befolgen Sie die Anweisungen, um die Anwendung mit v9x oder höher Ihrer Umgebung hinzuzufügen.
2. Wenn die Lösung installiert wurde, melden Sie sich in der Umgebung an, und rufen Sie **Einstellungen** > **Verwaltung** > **Virtuelle Entitätsdatenquellen** auf.
3. Wählen Sie in der Aktionssymbolleiste **NEU** und im Dialogfeld **Datenanbieter auswählen** **Azure Cosmos DB für SQL-API-Datenanbieter** und dann **OK** aus.
![Auswählen des Azure Cosmos DB für SQL-API-Datenanbieters](media/createdatasource.png)
1. Geben Sie die folgenden Informationen ein, und wählen Sie dann **Speichern und Schließen** aus.

    |Feld|Beschreibung|
    |--|--|
    |**Name**|Geben Sie einen Namen ein, der die Datenquelle beschreibt.|
    |**Sammlungsname**|Die ID der Azure Cosmos DB-Datenbanksammlung, die die Daten enthält, die Sie in einer virtuellen Entität anzeigen möchten.  |
    |**Autorisierungsschlüssel**|Der Primär- oder sekundäre Schlüssel für das Azure Cosmos DB-Konto. Sie finden den Schlüssel im Azure-Verwaltungsportal in der Einstellung **Schlüssel** für Ihr Azure Cosmos DB-Konto.|
    |**URI**|Der URI der Ressourcengruppe, in der sich die Azure Cosmos DB-Sammlung befindet. Der URI hat etwa diese Struktur: `https://contoso/documents.azure.com:443`. Sie finden den URI im Azure-Verwaltungsportal in der Einstellung **Schlüssel** für Ihr Azure Cosmos DB-Konto. |
    |**Timeout in Sekunden**|Geben Sie die Anzahl von Sekunden ein, die auf eine Antwort vom Azure Cosmos DB-Dienst gewartet werden soll, bevor ein Timeout der Datenanforderung eintritt. Geben Sie beispielsweise „30“ ein, um maximal 30 Sekunden zu warten, bevor ein Timeout eintritt. Das Standardtimeout beträgt 120 Sekunden.|

    ![Erstellen der Datenquelle mit dem SQL-API-Datenanbieter](media/cosmosdb-datasource.png)

## <a name="best-practices-and-limitations"></a>Best Practices und Einschränkungen

- Beachten Sie Folgendes, wenn Sie Azure Cosmos DB als Datenquelle verwenden:
   - Jede Azure Cosmos DB-Datenquelle kann nur einer einzelnen virtuellen Entität zugeordnet werden.
   - Sie können mehrere Datenquellen mit derselben Sammlung in Azure Cosmos DB verbinden.
- Sie können die Daten in einer Sammlung nicht nach Entität segmentieren.
- Azure Cosmos DB-Datenbanken benötigen kein Schema. Allerdings müssen die Daten in der Azure Cosmos DB-Instanz nach einem vorhersehbaren Schema strukturiert werden. 
- Obwohl der Azure Cosmos DB für SQL-API-Datenanbieter die Abfrageübersetzung von Projektions-, Filter- und Sortieroperatoren implementiert, unterstützt er keine JOIN-Vorgänge.
- Mit der SQL-API können Sie nur nach einer einzelnen Spalte filtern.

## <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten](create-edit-virtual-entities.md)
