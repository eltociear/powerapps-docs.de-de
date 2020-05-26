---
title: SQL zum Abfragen von Daten verwenden (Common Data Service) | Microsoft Docs
description: Lernen Sie, wie man mit SQL Common Data Service-Entitätsdaten abfragt.
ms.custom: ''
ms.date: 05/05/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: phecke
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b464b1cd4a64e9f33919567da15d10d7e50d9dd2
ms.sourcegitcommit: 0ede8e3bc795e151aa94ffcbce15cff7a949c57a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "3335342"
---
# <a name="use-sql-to-query-data-preview"></a>SQL zum Abfragen von Daten verwenden (Vorschau)

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Am Endpunkt Common Data Service steht eine SQL-Datenverbindung zur Verfügung. Die SQL-Verbindung ermöglicht den schreibgeschützten Zugriff auf die Entitätsdaten der Common Data Service-Zielumgebung. Dies ermöglicht Ihnen das Schreiben und Ausführen von SQL-Abfragen gegen die Datentabelle der Entitäten. Die Tabellenspalten enthalten die Attributdaten der Entitäten. Es wurden keine benutzerdefinierten Ansichten der Daten zur Verfügung gestellt.

> [!IMPORTANT]
> - Dies ist eine Vorschaufunktion und nicht in allen Regionen verfügbar.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]

## <a name="applications-support"></a>Unterstützung von Anwendungen

Sie können die **Analyse in Power BI** Option  (**Daten** > **Entitäten** > **Analyse in Power BI**) in Power Apps (https://make.powerapps.com) verwenden, um die SQL-Verbindungsfunktion zur Analyse von Daten in Power BI Desktop zu verwenden. Weitere Informationen: [Entitätsdaten in Power BI Desktop anzeigen](/powerapps/maker/common-data-service/view-entity-data-power-bi)

> [!NOTE]
> Wenn Sie die Option **In Power BI analysieren** nicht in Ihrer Power Apps-Umgebung haben, haben Sie noch keinen Zugriff auf die SQL-Verbindungsfunktion.

Sie können auch [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms) (SSMS) Version 18.4 oder höher mit der Common Data Service-Endpunkt-SQL-Verbindung verwenden. Beispiele für die Verwendung von SSMS mit der SQL-Datenverbindung sind unten aufgeführt.

![Erweiterte Kontentabelle](media/ssms-table-expanded.PNG)

## <a name="security-and-authentication"></a>Sicherheit und Authentifizierung

Die SQL-Endpunktverbindung Common Data Service verwendet das Sicherheitsmodell Common Data Service für den Datenzugriff. Daten können für alle Entitäten erhalten werden, auf die ein Benutzer in Common Data Service Zugriff hat.

Es wird nur die Azure Active Directory-Authentifizierung unterstützt. SQL-Authentifizierung und Windows-Authentifizierung werden nicht unterstützt. Unten finden Sie ein Beispiel für die Anmeldung an der SQL-Verbindung in SSMS. Beachten Sie, dass der Servername die URL der Organisationsadresse ist, gefolgt von einem Komma und dem Port-Wert 5558.

![Connec-Dialog](media/ssms-connect-dialog.PNG)

## <a name="example-entity-data-queries"></a>Beispiel für Entitätsdatenabfragen

Nachfolgend finden Sie ein paar Beispielabfragen, die in SSMS verfasst wurden. Das erste Bild zeigt eine einfache Abfrage mit Aliasen und Ergebnisreihenfolge.

```tsql
select top 5 a.name as [VIP customer], a.address1_postalcode as [ZIP code] from account a order by a.address1_postalcode desc
```

![Einfache Abfrage mithilfe von Aliasen und Sortierung](media/ssms-simple-query.PNG)

Diese nächste Abfrage zeigt einen JOIN an.

```tsql
select name, fullname from account a inner join contact c on a.primarycontactid = c.contactid
```

![Eine weitere Abfrage mit einem JOIN](media/ssms-join-query.PNG)

## <a name="supported-operations-and-data-types"></a>Unterstützte Operationen und Datentypen

Die Liste der unterstützten SQL-Operationen umfasst:

- Batch-Operationen
- AUSWÄHLEN
- Aggregationsfunktionen (d.h. Count()- und Max()-Funktionen)
- UNIONs und JOINs
- Filtern

Jede Operation, die versucht, Daten zu ändern (d.h. INSERT, UPDATE), funktioniert nicht, da es sich um eine schreibgeschützte SQL-Datenverbindung handelt. Common Data Service-Optionssätze werden als \<Optionssatz\>Name und \<Optionssatz\>Label in einer Ergebnismenge dargestellt.

Die folgenden Common Data Service-Datentypen werden von der SQL-Verbindung nicht unterstützt: binary, image, ntext, sql_variant, varbinary, virtual, HierarchyId, managedproperty, file, xml, partylist, timestamp.

### <a name="see-also"></a>Siehe auch

[Verwenden von FetchXML zum Erstellen einerAbfrage](use-fetchxml-construct-query.md)
