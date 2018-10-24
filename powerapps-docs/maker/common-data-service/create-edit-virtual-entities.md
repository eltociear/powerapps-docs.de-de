---
title: Erstellen und Bearbeiten von virtuellen Entitäten mit Common Data Service für Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie virtuelle Entitäten erstellt werden.
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 44834893-0bf6-4a64-8f06-7583fe08330d
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
ms.openlocfilehash: 675c0ac5763698c82a7d13bfc75f8b7357d6cf0b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39682962"
---
# <a name="create-and-edit-virtual-entities-that-contain-data-from-an-external-data-source"></a>Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten

Eine virtuelle Entität ist eine benutzerdefinierte Entität in Common Data Service für Apps, die Felder mit Daten aus einer externen Datenquelle enthält. Virtuelle Entitäten werden Benutzern in Ihrer App als reguläre Entitätsdatensätze angezeigt, enthalten jedoch Daten, die von einer externen Datenbank wie Azure SQL-Datenbank erstellt wurden. Datensätze auf Grundlage von virtuellen Entitäten sind in allen Clients verfügbar, einschließlich benutzerdefinierten Clients, die mithilfe von CDS für Apps-Webdienste entwickelt wurden.  
  
In der Vergangenheit hätten Sie für die Integration der unterschiedlichen Datenquellen einen Connector auf Client- oder Serverseite erstellen müssen, um Daten zu verschieben oder ein benutzerdefiniertes Plug-In zu entwickeln. Allerdings können Sie mit virtuellen Entitäten direkt eine Verbindung mit einer externen Datenquelle zur Laufzeit herstellen, damit bestimmte Daten aus der externen Datenquelle in einer Umgebung verfügbar sind. Datenreplikationen sind hierbei nicht notwendig.  

Virtuelle Entitäten bestehen aus drei Hauptkomponenten: einem *Datenanbieter*, einem *Datenquellen*-Datensatz und einer *virtuellen Entität*. Der Datenanbieter besteht aus Plug-Ins und einer Datenquellentität. Die Datenquelle ist ein Entitätsdatensatz in CDS für Apps mit Metadaten, die das Schema der Verbindungsparameter darstellen. Jede virtuelle Entität verweist auf eine Datenquelle in der Entitätsdefinition.  
  
CDS für Apps enthält einen OData-Datenanbieter, über den Sie eine Verbindung mit einem OData v4-Webdienst herstellen können, der auf die externen Daten zugreift. 
  
Alternativ dazu können Entwickler ihre eigenen Datenanbieter erstellen. Datenanbieter werden als Lösung in einer Umgebung installiert. Weitere Informationen finden Sie unter [Erste Schritte mit virtuellen Entitäten](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve).
  
 ![Abbildung zu virtuellen Entitäten](media/virtual-entity-diagram.png "Abbildung zu virtuellen Entitäten")  
  
<a name="benefits"></a> 
  
## <a name="virtual-entity-benefits"></a>Vorteile von virtuellen Entitäten  
  
- Entwickler können zum Lesen von externen Daten Plug-Ins mithilfe von CDS für Apps-Webdiensten und des Plug-In-Registrierungstools implementieren.  
- Systemanpasser konfigurieren mit dem PowerApps-Lösungs-Explorer den Datenquelldatensatz und erstellen virtuelle Entitäten, mit denen auf externe Daten zugegriffen wird, ohne Code schreiben zu müssen.  
- Endbenutzer arbeiten mit den Datensätzen, die von der virtuellen Entität erstellt werden, um die Daten in Feldern, Rastern, Suchergebnissen anzuzeigen und XML-basierte Berichte und Dashboards abzurufen.  
  
<a name="AddDataSource"></a> 
  
## <a name="add-a-data-source-to-use-for-virtual-entities"></a>Hinzufügen einer Datenquelle für die Verwendung für virtuelle Entitäten 
 
 Entwickler erstellen ein benutzerdefiniertes Plug-In für eine virtuelle Entität als Datenanbieter. Alternativ können Sie den bereitgestellten OData v4-Datenanbieter verwenden. Weitere Informationen finden Sie unter [OData v4-Datenanbieterkonfiguration, Anforderungen und bewährte Methoden](virtual-entity-odata-provider-requirements.md).  
  
1. Navigieren Sie zu  **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Verwaltung** > **Virtuelle Entitätsdatenquellen**.  
1. Klicken Sie auf der Aktionssymbolleiste auf **Neu**.  
1. Wählen Sie im Dialogfeld **Datenanbieter auswählen** aus den folgenden Datenquellen, und klicken Sie dann auf **OK**.
 
    |Datenanbieter|Beschreibung|
    |--|--|
    |*Benutzerdefinierter Datenanbieter*|Wenn Sie ein Datenanbieter-Plug-In importiert haben, wird der Datenanbieter hier angezeigt. Weitere Informationen finden Sie unter [Dokumentation für Entwickler: Erste Schritte mit virtuellen Entitäten](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve).|
    |**OData v4-Datenanbieter**|CDS für Apps enthält einen OData-Datenanbieter, der mit OData v4-Webdiensten verwendet werden kann. Weitere Informationen finden Sie unter [OData v4-Datenanbieterkonfiguration, Anforderungen und bewährte Methoden](virtual-entity-odata-provider-requirements.md).|

  
### <a name="add-a-secured-field-to-a-data-source"></a>Hinzufügen eines geschützten Felds zu einer Datenquelle

Sie können Felder für eine Datenquelle auf die gleiche Weise wie bei jeder anderen Entität erstellen. Aktivieren Sie für Daten, die verschlüsselt oder sensibel sind, das Attribut „Geheimer Schlüssel für Datenquelle“ für das benutzerdefinierte Feld der Datenquelle. Dies ist beispielsweise beim Schutz eines Felds der Fall, das eine Datenbankverbindungszeichenfolge enthält. 

> [!NOTE]
> Das Attribut „Geheimnis für Datenquelle“ ist nur mit Feldern verfügbar, die zu einem Formular für die Datenquelle hinzugefügt wurden.

![Attribut „Geheimnis für Datenquelle“](media/datasourcesecret.png)
  
<a name="createVirtualEntity"></a> 
  
## <a name="create-a-virtual-entity"></a>Erstellen einer virtuellen Entität
  
Sie können genau wie jede andere Entität in CDS für Apps eine virtuelle Entität erstellen. Sie müssen lediglich ein paar zusätzliche Attribute hinzufügen, die im Folgenden beschrieben werden. Virtuelle Entitäten müssen mit dem Lösungs-Explorer erstellt werden.

> [!NOTE]
>  Sie können zwar eine virtuelle Entität mit der Einstellung **Keine** für Datenquelle erstellen, eine virtuelle Entität benötigt für den Datenabruf jedoch eine Datenquelle. Weitere Informationen finden Sie unter [Hinzufügen einer Datenquelle für die Verwendung für virtuelle Entitäten](#AddDataSource).

### <a name="open-solution-explorer"></a>Öffnen des Lösungs-Explorers

Ein Teil des Namens einer virtuellen Entität, die Sie erstellen, ist das Anpassungspräfix. Dieses wird basierend auf dem Lösungsherausgeber für die Lösung festgelegt, in der Sie momentan arbeiten. Wenn das Anpassungspräfix für Sie im Mittelpunkt steht, stellen Sie sicher, dass Sie in einer nicht verwalteten Lösung mit dem von Ihnen bevorzugten Anpassungspräfix für diese virtuelle Entität arbeiten. Weitere Informationen finden Sie unter [Ändern des Präfixes für den Lösungsherausgeber](change-solution-publisher-prefix.md). 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="create-a-virtual-entity"></a>Erstellen einer virtuellen Entität
  
1. Erstellen Sie im Lösungs-Explorer eine neue Entität. Klicken Sie hierfür im linken Navigationsbereich auf **Entitäten** und dann auf **Neu**.  
2. Klicken Sie auf der Registerkarte **Allgemein** auf die **Entitätsdefinition**, wählen Sie **virtuelle Entität** aus, und wählen Sie dann in der Dropdownliste **Datenquelle** die gewünschte Datenquelle aus.  
  
    ![Option „Virtuelle Entität“ in der Entitätsdefinition](media/virtual-entity-click-option.png)  
  
1. Füllen Sie in der Entitätsdefinition die folgenden Pflichtfelder aus.
  
    |Feld|Beschreibung|
    |--|--|
    |**Externer Name**|Geben Sie den Namen der Tabelle in die externe Datenquelle ein, der diese Entität zugeordnet ist.|
    |**Externer Sammlungsname**|Geben Sie den Pluralnamen der Tabelle in die externe Datenquelle ein, der diese Entität zugeordnet ist.|
      
    Im Folgenden sehen Sie ein Beispiel für eine virtuelle Entität mit dem Namen *Movie*, die einen Azure Cosmos DB-Datenanbieter für den Zugriff auf Dokumentdateien verwendet.  
      
    ![Virtuelle Entitätsdefinition mithilfe des Azure Cosmos DB-Datenanbieters](media/virtual-entity-definition.PNG)  
      
    > [!IMPORTANT]
    > Bei virtuellen Entitäten stehen mehrere Optionen wie Zugriffsteams, Warteschlangen und Schnellerfassung nicht zur Verfügung. Weitere Informationen [Überlegungen bei der Verwendung von virtuellen Entitäten](#considerations)  
      
    Füllen Sie nach Bedarf die zusätzlichen erforderlichen und optionalen Eigenschaften aus, z.B. „Anzeigename“ und „Pluralname“. Weitere Informationen zu diesen Eigenschaften finden Sie unter [Erstellen und Bearbeiten von Entitäten in Common Data Service für Apps](create-edit-entities.md).  
  
1. Erstellen Sie mindestens ein Feld für die virtuelle Entität, und fügen Sie es hinzu. Neben den Standardfeldeigenschaften, die zum Erstellen eines benutzerdefinierten Felds erforderlich sind, sind diese optionalen Eigenschaften für benutzerdefinierte Felder verfügbar, die Sie für eine virtuelle Entität erstellen.

    |Feld|Beschreibung|
    |--|--|
    |**Externer Name**|Dies ist in der Regel der eindeutige Name, um die Daten zu identifizieren, die Sie im Feld anzeigen möchten.|
    |**Externer Typname**|Wenn der von Ihnen erstellte Feldtyp „OptionSet“ lautet, gilt Folgendes: Diese Eigenschaft entspricht dem externen Namen der Wertgruppe im externen Dienst für den Optionssatz.  Dies kann in der Regel eine Enumeration oder ein Name einer Zeichenfolgenwertklasse sein. Der externe Typname kann verwendet werden, wenn ein vollqualifizierter Name erforderlich ist.  Beispielsweise kann er als *Typname* mit OData verwendet werden, bei dem Parameter in einer Abfrage den vollqualifizierten Namen benötigen, z.B. [*Typname*].[*Wert*].|
    |**Externer Wert**|Wenn der von Ihnen erstellte Feldtyp „OptionSet“ lautet, gilt Folgendes: Diese Eigenschaft entspricht dem jeweiligen Wert in der externen Datenquelle für den Optionssatz.  Mit dem eingegebenen Wert wird bestimmt, welches Optionssatzelement in der App angezeigt wird.  |

    Füllen Sie nach Bedarf die zusätzlichen Eigenschaften aus. Weitere Informationen zu diesen Eigenschaften finden Sie unter [Gewusst wie: Erstellen und Bearbeiten von Feldern](create-edit-fields.md).  
  
1. Klicken Sie auf der Eigenschaftenseite **Feld** auf **Speichern und schließen**.  
1. Klicken Sie auf der Symbolleiste des Lösungs-Explorers auf **Speichern**.  
1. Klicken Sie auf der Symbolleiste des Lösungs-Explorers auf **Veröffentlichen**.  
1. Schließen Sie den Lösungs-Explorer.  

<a name="considerations"></a>
   
## <a name="considerations-when-you-use-virtual-entities"></a>Überlegungen bei der Verwendung von virtuellen Entitäten  

Virtuelle Entitäten weisen die folgenden Einschränkungen auf:  
  
- Alle virtuellen Entitäten sind schreibgeschützt.  
- Vorhandene Entitäten können nicht in virtuelle Entitäten konvertiert werden.  
- Standardmäßig enthalten virtuelle Entitäten lediglich ein Name- und ein Id-Feld.  Es werden keine anderen verwalteten Systemfelder wie „Status“ oder „Erstellt/Geändert am“ unterstützt.
- Virtuelle Entitäten unterstützen keine benutzerdefinierten Felder mit den Datentypen „Currency“, „Image“ oder „Customer“.
- Virtuelle Entitäten unterstützen keine Überwachung.  
- Virtuelle Entitätsfelder können nicht in Rollups oder berechneten Feldern verwendet werden.
- Eine virtuelle Entität kann kein Aktivitätstyp der Entität sein.  
- Viele Features, die sich auf Zeilen einer Entitätstabelle auswirken, können nicht mit virtuellen Entitäten aktiviert werden.  Hierzu zählen beispielsweise Warteschlangen, das Wissensmanagement, SLAs, die Duplikaterkennung, die Änderungsnachverfolgung, Mobile Offline-Funktionen, Sicherheit auf Feldebene, Relevanzsuche, Portale für Dynamics 365-Webportallösungen und m:n-Beziehungen zwischen virtuellen Entitäten.  
- Virtuelle Entitäten stehen im Besitz einer Organisation und unterstützen keine Konzepte von Common Data Service für Apps, die auf Sicherheit auf Zeilenebene basieren. Es wird empfohlen, ein eigenes Sicherheitsmodell für die externe Datenquelle zu implementieren.  
- Es wird empfohlen, bei der Verwendung von virtuellen Entitäten in der erweiterten Suche eine einzelne Datenquelle als Ziel festzulegen. Beispielsweise wird keine Unterstützung für das Erstellen einer erweiterten Suche geboten, die letztlich eine Verknüpfung zwischen den nativen Daten von Common Data Service für Apps und den externen Daten der virtuellen Entität herstellt.  
- Feldmetadateneigenschaften, die auf Updates prüfen, gelten nicht für virtuelle Entitäten. Beispielsweise kann ein Feld namens „Ganze Zahl“ für ein virtuelles Entitätsfeld mit dem Mindestwert 0 festgelegt werden. Da der Wert jedoch von einer externen Quelle stammt, gibt eine Abfrage bei einer virtuellen Entität Werte kleiner als 0 zurück.  Die Mindestwerteigenschaft ist nicht in der Abfrage impliziert.  Sie müssen ggf. weiterhin die Werte filtern, die größer als 0 sein sollen.
- Virtuelle Entitäten unterstützen keine Änderungsnachverfolgung und können nicht mit einem CDS für Apps-Feature synchronisiert werden, z.B. dem Data Export Service.
  
### <a name="see-also"></a>Siehe auch  

[OData v4-Datenanbieterkonfiguration, Anforderungen und bewährte Methoden](virtual-entity-odata-provider-requirements.md)</br> 
[Erstellen und Bearbeiten von Feldern in Common Data Service für Apps](create-edit-entities.md)</br>
[Erstellen und Bearbeiten von Feldern](create-edit-fields.md)
