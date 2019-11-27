---
title: Walkthrough zu virtuellen Entitäten mit dem OData Data Provider in Common Data Service | MicrosoftDocs
description: Erfahren Sie, wie Sie den Datenanbieter ODatas v4-Clients mit der virtuellen Entität verwenden
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
- powerapps
ms.assetid: ''
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b7aa64e5ecdc620b5f376601ffb826c3708f98d3
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752104"
---
# <a name="virtual-entity-walkthrough-using-the-odata-v4-data-provider"></a>Virtuelle exemplarische Vorgehensweise mit dem OData-Datenanbieter

Stellen Sie sich vor, Sie möchten innerhalb Ihrer modellgetriebenen App auf Ticketinformationen aus einer externen Datenquelle zugreifen. In dieser einfachen exemplarischen Vorgehensweise modelliere Sie eine virtuelle Entität mit den Feldern, die zu externem Schema zugeordnet sind, das Ticketdaten zur Laufzeit von einem OData-Webdienst wird.

## <a name="data-source-details"></a>Datenquellendetails

Da die hier verwendete Datenquelle über einen OData v4-Webdienst verfügt, können wir den OData v4-Datenanbieter verwenden, der in Ihrer Umgebung  enthalten ist.

Web service url: `https://contosowebservice.azurewebsites.net/odata/` 

> [!IMPORTANT]
> Die Webdienst-URL für diese exemplarische Vorgehensweise ist kein funktionierender Webdienst.

Bei dieser Vorgehensweise wird eine einzelne virtuelle Entität benötigt, die die folgenden drei Felder enthält.

|Externer Feldname |Externer Datentyp |Virtueller Entitätsdatentyp |Zweck |
|---------|---------|---------|---------|
|TicketID |`Edm.Guid` |Primärschlüssel |Primärschlüssel für die Entität |
|Titel  |`Edm.String` |Einzelne Textzeile |Titel des Tickets |
|Schweregrad |`Edm.Int32`| Ganze Zahl |Zahlenwerte von 0 bis 4, die den Schweregrad des Tickets angeben |

Die OData-Metadaten der externen Datenquelle Ticketentität:

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

Erstellen Sie die Datenquelle für den OData v4-Datenanbieter, die den OASIS Open Data Protocol (OData)-Beispielwebdienst verwendet.

1. Wählen Sie **Einstellungen** > **Verwaltung** > **Datenquellen für virtuelle Entitäten**.
1. Wählen Sie **NEU**, **OData v4-Datenanbieter** und dann **OK** aus.
1. Geben Sie die folgenden Informationen ein bzw. wählen Sie diese aus.

    |Feld|Value|
    |--|--|
    |**Name**|Contoso-Beispieldatenquelle|
    |**URL**|`https://contosowebservice.azurewebsites.net/odata` |
    |**Timeout**|30|
    |**Inline-Anzahl zurückgeben**|True|

Belassen Sie die anderen Felder so, wie sie sind, und wählen Sie **Speichern und Schließen** aus.

> [!TIP]
> Wenn Sie einen eigenen Webdienst verwenden, stellen Sie sicher, dass die URL gültig ist, indem Sie sie in Ihren Webbrowser einfügen. 

## <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Ein Teil des Namens jeder benutzerdefinierten Entität, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diese Entität entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="create-the-virtual-entity"></a>Erstellen der virtuellen Entität

1. Klicken Sie im linken Navigationsbereich des Lösungs-Explorers auf **Entitäten** und wählen Sie dann im Hauptbereich **Neu** aus.
2. Klicken Sie im Formular **Entität: Neu** auf **Virtuelle Entität**, und geben Sie die folgenden Informationen ein: 

    |Feld|Value|
    |--|--|
    |**Datenquelle**|Contoso-Beispieldatenquelle|
    |**Anzeigename**|Ticket|
    |**Pluralname**|Tickets|
    |**Name**|new_ticket|
    |**Externer Name**|Ticket|
    |**Externer Sammlungsname**|Tickets|
    |**Notizen (enthält Anlagen)**|ausgewählt|
    |**Aktivitäten**|ausgewählt|

1. Klicken Sie neben **Bereiche, in denen diese Entität angezeigt wird** auf **Service** und dann auf **Speichern** (aber schließen Sie nicht das Entitätsformular).
    ![Definition der Ticketentität](media/ticket-entity.png)

## <a name="create-the-fields-for-the-virtual-entity"></a>Erstellen der Felder für die virtuelle Entität

Klicken Sie im linken Navigationsbereich der Seite **Entität: Ticket** auf **Felder**. Im Rahmen dieser exemplarischen Vorgehensweise bearbeiten Sie zwei vorhandene Felder und fügen ein drittes hinzu.

> [!IMPORTANT]
> Bei externen Namen wird die Groß-/Kleinschreibung beachtet. Sehen Sie in Ihren Webdienstmetadaten nach, um sicherzustellen, dass Sie den korrekten Namen verwenden.
> Ein Nullwert von "false" weist darauf hin, dass das Attribut erforderlich ist. Beachten Sie, dass Primärschlüsselfelder stets vom System benötigt werden.

1. Öffnen Sie das Feld **new_ticketid**, und ändern Sie das folgende Attribut mit dem hier angegebenen Wert:  **Externer Name**: TicketID  ![TicketID field](media/ticketid-field.png)
1. Klicken Sie auf **Speichern und schließen**.
1. Öffnen Sie das Feld **new_name**, und ändern Sie die folgenden Attribute so, dass die hier angegebenen Werte verwendet werden:
    - **Anzeigename**: Titel
    - **Externer Name**: Titel ![Title field](media/title-field.png)
1. Klicken Sie auf **Speichern und schließen**.
1. Wählen Sie **Neu** aus und geben Sie auf der Seite für **Feld: Neu für Ticket** die folgenden Informationen ein:

    |Feld|Value|
    |--|--|
    |**Anzeigename**|Schweregrad|
    |**Name**|new_severity|
    |**Externer Name**|Schweregrad|
    |**Feldanforderung**|Eingabe erforderlich|
    |**Datentyp**|Ganze Zahl|
    |**Mindestwert**|0|
    |**Maximalwert**|4|

  ![Schwergradfeld](media/severity-field.png)
1. Klicken Sie auf **Speichern und schließen**.

## <a name="add-the-fields-to-the-main-form"></a>Hinzufügen der Felder zum Hauptformular

1. Klicken Sie im Ticketentitätsfenster auf **Formulare**
1. Öffnen Sie das Hauptformular, und verschieben Sie das Feld **Schweregrad** aus dem rechten Bereich auf das Formular im Bereich **Allgemein** unter dem Feld **Titel**. 
    ![Schweregradfeld zum Hauptformular hinzugefügt](media/drop-severity-field.png)
1. Klicken Sie im Ticketentitätsfenster auf **Speichern und schließen**

## <a name="configure-the-default-view"></a>Konfigurieren der Standardansicht

1. Klicken Sie im linken Bereich des Lösungs-Explorers unter **Ticketentität** auf **Ansichten**.
1. Öffnen Sie die Ansicht für **Alle Tickets**.
1. Klicken Sie im Bereich **Allgemeine Aufgaben** auf **Spalten hinzufügen**.
    ![Spalten zur Ansicht hinzufügen](media/addcolumns.png)
1. Wählen Sie **Schweregrad** aus, und klicken Sie dann auf **OK**.
1. Klicken Sie im Fenster für **Ansicht: Alle Tickets** auf **Speichern und Schließen**.
1. Klicken Sie im Projektmappen-Explorer-Fenster auf **Alle Anpassungen veröffentlichen**.
    ![Alle Anpassungen veröffentlichen](media/publishall.png)
1. Schließen Sie das Projektmappen-Explorer-Fenster, nachdem alle Anpassungen veröffentlicht wurden.

## <a name="view-the-virtual-entity-in-action-with-dynamics-365"></a>Sehen Sie die virtuelle Entität in Aktion mit Dynamics 365.

1. Gehen Sie zu **Service** > **Erweiterungen** > **Tickets**.
    
    ![Ticketbereich](media/ticket-area.png)

    Die Ansicht **Alle Tickets** erscheint. Beachten Sie, dass Sie möglicherweise Ihren Browser aktualisieren müssen, um die Entität aus dem Bereich **Service** anzuzeigen.

    ![Ansicht "Alle Tickets"](media/all-tickets-view.png)
1. Öffnen Sie einen **Ticket**-Datensatz, um das Formular anzuzeigen, das die Felder **Titel** und **Schweregrad** für den betreffenden Datensatz enthält.
    ![Ticketdatensatz](media/ticket-record.png)

### <a name="see-also"></a>Siehe auch

[ OData v4 Datenanbieterkonfiguration, Anforderungen und bewährten Methoden](virtual-entity-odata-provider-requirements.md)<br />
[Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten](create-edit-virtual-entities.md)
