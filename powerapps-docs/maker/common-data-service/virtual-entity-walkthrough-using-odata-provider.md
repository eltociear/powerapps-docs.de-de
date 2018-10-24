---
title: Exemplarische Vorgehensweise für virtuelle Entitäten mit dem OData-Datenanbieter in Common Data Service für Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie den OData v4-Datenanbieter mit einer virtuellen Entität verwenden
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
- powerapps
ms.assetid: ''
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
ms.openlocfilehash: ebdd8f80aad2d353d017626b7c403da93803c19b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683505"
---
# <a name="virtual-entity-walkthrough-using-the-odata-v4-data-provider"></a>Exemplarische Vorgehensweise für virtuelle Entitäten mit dem OData v4-Datenanbieter

Stellen Sie sich vor, Sie möchten innerhalb Ihrer modellgesteuerten App oder des Servicebereichs von Dynamics 365 für Customer Engagement auf Ticketinformationen aus einer externen Datenquelle zugreifen. In dieser einfachen exemplarischen Vorgehensweise modellieren Sie eine virtuelle Entität mit den Feldern, die dem externen Schema zugeordnet sind, das zur Runtime Ticketdaten von einem OData-Webdienst abruft.

## <a name="data-source-details"></a>Datenquellendetails

Da die hier verwendete Datenquelle über einen OData v4-Webdienst verfügt, können wir den OData v4-Datenanbieter verwenden, der in Ihrer Umgebung enthalten ist.

URL des Webdiensts: `http://contosowebservice.azurewebsites.net/odata/` 

> [!IMPORTANT]
> Die für diese exemplarische Vorgehensweise verwendete Webdienst-URL ist kein funktionierender Webdienst.

Bei dieser Vorgehensweise wird eine einzelne virtuelle Entität benötigt, die die folgenden drei Felder enthält.

|Externer Feldname |Externer Datentyp |Datentyp der virtuellen Entität |Zweck |
|---------|---------|---------|---------|
|TicketID |`Edm.Guid` |Primärer Schlüssel |Primärschlüssel für die Entität |
|Title  |`Edm.String` |Einzelne Textzeile |Titel des Tickets |
|Schweregrad |`Edm.Int32`| Ganze Zahl |Zahlenwert von 0 bis 4, der den Schweregrad des Tickets angibt |

Die OData-Metadaten der Ticket-Entität der externen Datenquelle:

```xml
<EntityType Name="Ticket">
  <Key>
    <PropertyRef Name="TicketID" />
  </Key>
  <Property Name="TicketID" Nullable="false" Type="Edm.Guid" />
  <Property Name="Title" Type="Edm.String" />
  <Property Name="Severity" Nullable="false" Type="Edm.Int32" />
</EntityType>
```

## <a name="create-the-data-source"></a>Erstellen der Datenquelle

Erstellen Sie die Datenquelle für den OData v4-Datenanbieter, die den OASIS Open Data Protocol-Beispielwebdienst (OData) verwendet.

1. Wählen Sie **Einstellungen** > **Verwaltung** > **Datenquellen für virtuelle Entitäten**.
1. Wählen Sie **NEU**, **OData v4-Datenanbieter** und dann **OK** aus.
1. Geben Sie die folgenden Informationen ein, oder wählen Sie sie aus:

    |Feld|Wert|
    |--|--|
    |**Name**|Contoso-Beispieldatenquelle|
    |**URL**|`http://contosowebservice.azurewebsites.net/odata` |
    |**Timeout**|30|
    |**Inlineanzahl zurückgeben**|True|

Belassen Sie die anderen Felder so, wie sie sind, und wählen Sie **SPEICHERN UND SCHLIESSEN** aus.

> [!TIP]
> Wenn Sie einen eigenen Webdienst verwenden, stellen Sie sicher, dass die URL gültig ist, indem Sie sie in Ihren Webbrowser einfügen. 

## <a name="open-solution-explorer"></a>Öffnen des Projektmappen-Explorers

Ein Teil des Namens einer benutzerdefinierten Entität, die Sie erstellen, ist das Anpassungspräfix. Dieses wird basierend auf dem Lösungsherausgeber für die Lösung festgelegt, in der Sie momentan arbeiten. Wenn das Anpassungspräfix für Sie im Mittelpunkt steht, stellen Sie sicher, dass Sie in einer nicht verwalteten Lösung mit dem von Ihnen bevorzugten Anpassungspräfix für diese Entität arbeiten. Weitere Informationen finden Sie unter [Ändern des Präfixes für den Lösungsherausgeber](change-solution-publisher-prefix.md). 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="create-the-virtual-entity"></a>Erstellen der virtuellen Entität

1. Wählen Sie im linken Navigationsbereich des Projektmappen-Explorers **Entitäten** und dann im Hauptbereich **Neu** aus.
2. Wählen Sie im Formular **Entität: Neu** die Option **Virtuelle Entität** aus, und geben Sie die folgenden Informationen ein: 

    |Feld|Wert|
    |--|--|
    |**Datenquelle**|Contoso-Beispieldatenquelle|
    |**Anzeigename**|Ticket|
    |**Pluralname**|Tickets|
    |**Name**|new_ticket|
    |**Externer Name**|Ticket|
    |**Externer Sammlungsname**|Tickets|
    |**Notizen (enthält Anlagen)**|Ausgewählt|
    |**Aktivitäten**|Ausgewählt|

1. Wählen Sie neben **Bereiche, in denen diese Entität angezeigt wird** die Option **Dienst** und dann **Speichern** aus (aber schließen Sie nicht das Entitätsformular).
    ![Definition der Ticket-Entität](media/ticket-entity.png)

## <a name="create-the-fields-for-the-virtual-entity"></a>Erstellen der Felder für die virtuelle Entität

Wählen Sie im linken Navigationsbereich der Seite **Entität: Ticket** die Option **Felder** aus. Im Rahmen dieser exemplarischen Vorgehensweise bearbeiten Sie zwei vorhandene Felder und fügen ein drittes hinzu.

> [!IMPORTANT]
> Bei externen Namen wird die Groß-/Kleinschreibung beachtet. Sehen Sie in Ihren Webdienstmetadaten nach, um sicherzustellen, dass Sie den korrekten Namen verwenden.
> Ein NULL-Wert von „False“ weist darauf hin, dass das Attribut erforderlich ist. Beachten Sie, dass Primärschlüsselfelder stets vom System benötigt werden.

1. Öffnen Sie das Feld **new_ticketid**, und ändern Sie das folgende Attribut mit dem hier angegebenen Wert: **Externer Name**: TicketID ![TicketID-Feld](media/ticketid-field.png)
1. Klicken Sie auf **Speichern und schließen**.
1. Öffnen Sie das Feld **new_name**, und ändern Sie die folgenden Attribute so, dass die hier angegebenen Werte verwendet werden:
    - **Anzeigename:** Titel
    - **Externer Name**: Titel ![Titelfeld](media/title-field.png)
1. Klicken Sie auf **Speichern und schließen**.
1. Wählen Sie **Neu** aus, und geben Sie auf der Seite **Feld: Neu für Ticket** die folgenden Informationen ein:

    |Feld|Wert|
    |--|--|
    |**Anzeigename**|Schweregrad|
    |**Name**|new_severity|
    |**Externer Name**|Schweregrad|
    |**Feldanforderung**|Eingabe des Unternehmens als erforderlich markiert|
    |**Datentyp**|Ganze Zahl|
    |**Minimalwert**|0|
    |**Maximalwert**|4|

  ![Feld „Schweregrad“](media/severity-field.png)
1. Klicken Sie auf **Speichern und schließen**.

## <a name="add-the-fields-to-the-main-form"></a>Hinzufügen der Felder zum Hauptformular

1. Wählen Sie im Fenster der Ticket-Entität die Option **Formulare** aus.
1. Öffnen Sie das Hauptformular, und verschieben Sie das Feld **Schweregrad** mit Drag & Drop aus dem rechten Bereich auf das Formular im Bereich **Allgemein** unter dem Feld **Titel**. 
    ![Dem Hauptformular hinzugefügtes Feld „Schweregrad“](media/drop-severity-field.png)
1. Wählen Sie im Fenster der Ticket-Entität die Option **Speichern und schließen** aus.

## <a name="configure-the-default-view"></a>Konfigurieren der Standardansicht

1. Wählen Sie im linken Bereich des Projektmappen-Explorers unter **Ticket-Entität** die Option **Ansichten** aus.
1. Öffnen Sie die Ansicht **Alle Tickets**.
1. Wählen Sie im Bereich **Allgemeine Aufgaben** die Option **Spalten hinzufügen** aus.
    ![Hinzufügen von Spalten für die Ansicht](media/addcolumns.png)
1. Wählen Sie **Schweregrad** und dann **OK** aus.
1. Wählen Sie im Fenster **Ansicht: Alle Tickets** die Option **Speichern und schließen** aus.
1. Wählen Sie im Projektmappen-Explorer-Fenster **Alle Anpassungen veröffentlichen** aus.
    ![Alle Anpassungen veröffentlichen](media/publishall.png)
1. Schließen Sie nach dem Veröffentlichen aller Anpassungen das Projektmappen-Explorer-Fenster.

## <a name="view-the-virtual-entity-in-action-with-dynamics-365-customer-engagement"></a>Anzeigen der virtuellen Entität in Aktion mit Dynamics 365 Customer Engagement

1. Wechseln Sie zu **Dienst** > **Erweiterungen** > **Tickets**.
    
    ![Ticketbereich](media/ticket-area.png)

    Die Ansicht **Alle Tickets** wird angezeigt. Beachten Sie, dass Sie möglicherweise Ihren Browser aktualisieren müssen, um die Entität aus dem Bereich **Dienst** anzuzeigen.

    ![Ansicht „Alle Tickets“](media/all-tickets-view.png)
1. Öffnen Sie einen **Ticket**-Datensatz, um das Formular anzuzeigen, das die Felder **Titel** und **Schweregrad** für den betreffenden Datensatz enthält.
    ![Ticket-Datensatz](media/ticket-record.png)

### <a name="see-also"></a>Siehe auch

[Konfiguration, Anforderungen und bewährte Methoden für OData v4-Datenanbieter](virtual-entity-odata-provider-requirements.md)<br />
[Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten](create-edit-virtual-entities.md)
