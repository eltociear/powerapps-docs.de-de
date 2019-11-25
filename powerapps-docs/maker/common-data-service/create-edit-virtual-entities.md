---
title: Erstellen und Bearbeiten virtueller Entitäten mit Common Data Service | MicrosoftDocs
description: Informationen zum Erstellen virtueller Entitäten
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ecb0731d3cbba030f3b819e2b2744cb6a7b29c20
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2706897"
---
# <a name="create-and-edit-virtual-entities-that-contain-data-from-an-external-data-source"></a>Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten

Eine virtuelle Entität ist eine benutzerdefinierte Entität in Common Data Service, die Felder mit Daten von einer externen Datenquelle enthält. Virtuelle Entitäten erscheinen Benutzern in Ihrer App als reguläre Entitätsdatensätze, enthalten aber Daten von einer externen Datenbank, z. B. einer Azure-SQL-Datenbank. Datensätze auf Grundlage virtueller Entitäten stehen in allen Clients zur Verfügung, einschließlich benutzerdefinierter Clients, die Common Data Service-Webdienste verwenden.  
  
In der Vergangenheit brauchte man für die Integration der separaten Datenquellen einen Konnektor, um die Daten zu verschieben, oder man musste ein benutzerdefiniertes Plug-In auf der Client- oder Serverseite erstellen. Mit virtuellen Entitäten können Sie zur Laufzeit direkt eine Verbindung zu einer externen Datenquelle einrichten, sodass spezifische Daten aus der externen Datenquelle in einer Umgebung zur Verfügung stehen, ohne dass eine Datenreplikation erforderlich ist.  

Virtuelle Entitäten bestehen aus drei Hauptkomponenten, einem *Datenanbieter*, einem *Datenquelldatensatz* und einer *virtuellen Entität*. Der Datenanbieter besteht aus Plug-Ins und einer Datenquellentität. Die Datenquelle ist ein Entitätsdatensatz in Common Data Service, der Metadaten enthält, die das Schema der Verbindungsparameter darstellen. Jede virtuelle Entität verweist auf eine Datenquelle in der Entitätendefinition.  
  
Common Data Service beinhaltet einen OData-Datenanbieter, den Sie verwenden können, um eine Verbindung mit einem OData v4-Webservice einzurichten, der auf die externen Daten zugreift. 
  
Alternativ können Entwickler ihre eigenen Datenanbieter erstellen. Datenanbieter werden in einer Umgebung als Lösung installiert. Weitere Informationen: [Entwicklerdokumentation: Erste Schritte mit virtuellen Entitäten fest](../../developer/common-data-service/virtual-entities/get-started-ve.md)
  
 ![Virtuelles Entitätsdiagramm](media/virtual-entity-diagram.png "Virtuelles Entitätsdiagramm")  
  
<a name="benefits"></a> 
  
## <a name="virtual-entity-benefits"></a>Vorteile der virtuellen Entität  
  
- Entwickler können Plug-Ins implementieren, um mit dem Common Data Service-Webdiense und dem -Plug-In-Registrierungstool externe Daten zu lesen.  
- Systemanpasser verwenden den PowerApps-Projektmappen-Explorer, um den Datenquelldatensatz zu konfigurieren und virtuelle Entitäten zu erstellen, die für den Zugriff auf externe Daten verwendet werden, ohne dafür Code schreiben zu müssen.  
- Endbenutzer verwenden die Datensätze, die von der virtuellen Entität erstellt wurden, um die Daten in Feldern, Rastern, Suchergebnissen und FetchXML-basierten Berichten sowie Dashboards zu betrachten.  
  
<a name="AddDataSource"></a> 
  
## <a name="add-a-data-source-to-use-for-virtual-entities"></a>Eine Datenquelle für virtuelle Entitäten hinzufügen 
 
 Entwickler erstellen ein benutzerdefiniertes Plug-In, das als Datenanbieter für eine virtuelle Entität verwendet wird. Alternativ können Sie den zur Verfügung gestellten OData v4-Datenanbieter verwenden. Weitere Informationen: [OData v4 Datenanbieterkonfiguration, Anforderungen und bewährten Methoden](virtual-entity-odata-provider-requirements.md)  
  
1. Wählen Sie **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Verwaltung** > **Datenquellen für virtuelle Entitäten** aus.  
1. Wählen Sie auf der Aktionssymbolleiste **Neu** aus.  
1. Wählen Sie im Dialogfeld **Datenanbieter auswählen** aus den folgenden Datenquellen aus, und wählen Sie dann **OK** aus.
 
    |Datenanbieter|Beschreibung|
    |--|--|
    |*Benutzerdefinierter Datenanbieter*|Wenn Sie ein Datenanbieter-Plug-In importiert haben, wird der Datenanbieter hier angezeigt. Weitere Informationen: [Entwicklerdokumentation: Erste Schritte mit virtuellen Entitäten fest](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)|
    |**OData v4-Datenanbieter**|Common Data Service enthält einen OData-Datenanbieter, der mit ODatas v4-Webdiensten verwendet werden kann. Weitere Informationen: [OData v4 Datenanbieterkonfiguration, Anforderungen und bewährten Methoden](virtual-entity-odata-provider-requirements.md)|

  
### <a name="add-a-secured-field-to-a-data-source"></a>Hinzufügen eines gesicherten Felds zu einer Datenquelle

Sie erstellen Felder für eine Datenquelle auf die gleiche Weise wie für jede andere Entität. Für Daten, die vertraulich oder verschlüsselt sind, aktivieren Sie das Attribut "Datenquelle geheim" auf dem benutzerdefinierten Feld der Datenquelle. Beispielsweise zum Speichern eines Felds, das eine Datenbankverbindungszeichenfolge enthält. 

> [!NOTE]
> Das Attribut "Datenquelle geheim" ist nur verfügbar bei den Feldern, die einem Datenquellenformular hinzugefügt werden.

> [!div class="mx-imgBorder"] 
> ![Attribut „Datenquelle geheim“](media/datasourcesecret.png)
  
<a name="createVirtualEntity"></a> 
  
## <a name="create-a-virtual-entity"></a>Eine virtuelle Entität erstellen
  
Sie erstellen eine virtuelle Entität genauso wie jede andere Entität in Common Data Service mit einigen zusätzlichen Attributen, die hier beschrieben werden. Virtuelle Entitäten müssen mit dem Projektmappen-Explorer erstellt werden.

> [!NOTE]
>  Obwohl Sie eine virtuelle Entität erstellen können, indem Sie **Keine** als Datenquelle auswählen, ist für eine virtuelle Entität, um Daten abzurufen, eine Datenquelle erforderlich. Weitere Informationen: [Eine Datenquelle für virtuelle Entitäten hinzufügen](#AddDataSource)

### <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Ein Teil des Namens jeder virtuellen Entität, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diese virtuelle Entität entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="create-a-virtual-entity"></a>Eine virtuelle Entität erstellen
  
1. Erstellen Sie im Projektmappen-Explorer eine neue Entität. Wählen Sie dazu im linken Navigationsbereich die Option **Entitäten** aus, und wählen Sie anschließend **Neu** aus.  
2. Wählen Sie auf der Registerkarte **Allgemein** der **Entitätsdefinition** die Option **Virtuelle Entität** aus, und wählen Sie dann in der Dropdownliste **Datenquelle** die gewünschte Datenquelle aus.  

    > [!div class="mx-imgBorder"] 
    > ![Virtuelle Entitätsoption bei Entitätsdefinition](media/virtual-entity-click-option.png)  
  
1. Füllen Sie in der Entitätsdefinition die folgenden erforderlichen Felder aus.
  
    |Feld|Beschreibung|
    |--|--|
    |**Externer Name**|Geben Sie den Namen der Tabelle in die externe Datenquelle ein, die dieser Entität zugeordnet ist.|
    |**Externer Sammlungsname**|Geben Sie den Plural-Namen der Tabelle in die externe Datenquelle ein, die dieser Entität zugeordnet ist.|
      
    Nachfolgend sehen Sie ein Beispiel für eine virtuelle Entität mit dem Namen *Movie*, die einen Azure Cosmos DB-Datenanbieter verwendet, um auf Dokumentdateien zuzugreifen.  
      
    > [!div class="mx-imgBorder"] 
    > ![Virtuelle Entitätsdefinition mithilfe des Azure Cosmos DB-Datenanbieters](media/virtual-entity-definition.PNG)  
      
    > [!IMPORTANT]
    > Einige Optionen stehen nicht für virtuelle Entitäten zur Verfügung, wie beispielsweise Zugriffsteams, Warteschlangen und Schnellerfassung. Weitere Informationen: [Überlegungen bei der Verwendung virtueller Entitäten](#considerations)  
      
    Ergänzen Sie die zusätzlichen erforderlichen und optionalen Eigenschaften nach Bedarf, wie beispielsweise Anzeige- und Pluralnamen. Weitere Informationen über diese Eigenschaften finden Sie unter [Erstellen und Bearbeiten von Entitäten](create-edit-entities.md).  
  
1. Erstellen Sie ein oder mehrere Felder für die virtuelle Entität, und fügen Sie diese hinzu. Neben den Standardfeldeigenschaften, die für die Erstellung eines benutzerdefinierten Felds erforderlich sind, stehen diese optionalen Eigenschaften für jedes benutzerdefinierte Feld zur Verfügung, das Sie für eine virtuelle Entität erstellen.

    |Feld|Beschreibung|
    |--|--|
    |**Externer Name**|Dies ist normalerweise der eindeutige Name, der die Daten identifiziert, die Sie in dem Feld anzeigen wollen.|
    |**Externer Typname**|Wenn der Feldtyp, den Sie erstellen "OptionSet" ist: Diese Eigenschaft wird auf den externen Namen der Wertemenge im externen Service für den Optionssatz abgebildet.  Dies kann eine Auflistung oder der Name einer Zeichenfolgenwerteklasse sein. Der externe Typname kann verwendet werden, wenn ein vollständig qualifizierter Name benötigt wird.  Wie beispielsweise der *Typname* bei OData, wo Parameter in einer Warteschlange den vollständig qualifizierten Namen benötigen, z. B. [*Typname*].[*Wert*].|
    |**Externer Wert**|Wenn der Feldtyp, den Sie erstellen "OptionSet" ist: Diese Eigenschaft wird dem entsprechenden Wert in der externen Datenquelle für das Optionssatzelement zugewiesen.  Anhand dieses eingegebenen Werts wird bestimmt, welches Optionssatzelement in der App angezeigt werden soll.  |

    Tragen Sie nach Bedarf weitere Eigenschaften ein. Weitere Informationen über diese Eigenschaften finden Sie unter [Erstellen und Bearbeiten von Feldern](create-edit-fields.md).  
  
1. Wählen Sie **Speichern und schließen** auf der Eigenschaftsseite **Feld** aus.  
1. Wählen Sie auf der Symbolleiste des Projektmappen-Explorers **Speichern** aus.  
1. Wählen Sie auf der Symbolleiste des Projektmappen-Explorers **Veröffentlichen** aus.  
1. Schließen Sie den Projektmappen-Explorer.  

<a name="considerations"></a>
   
## <a name="considerations-when-you-use-virtual-entities"></a>Überlegungen bei der Verwendung virtueller Entitäten  

Virtueller Entitäten haben die folgenden Einschränkungen.  
  
- Alle virtuellen Entitäten sind schreibgeschützt.  
- Vorhandene Entitäten können zu virtuellen Entitäten konvertiert werden.  
- Standardmäßig enthalten virtuelle Entitäten nur ein Namens- und ein Kennungsfeld.  Es werden keine anderen vom System verwalteten Felder unterstützt, wie beispielsweise „Status” oder „Erstellt am/Geändert am”.
- Virtuelle Entitäten unterstützen keine benutzerdefinierten Felder mit den Datentypen „Währung”, „Bild” oder „Kunde”.
- Virtuelle Entitäten unterstützen keine Überwachung.  
- Die Felder virtueller Entitäten können nicht in Rollups oder berechneten Feldern verwendet werden.
- Eine virtuelle Entität kann kein Aktivitätstyp einer Entität sein.  
- Viele Funktionen, die sich Entitätstabellenzeilen auswirken, können nicht mit virtuellen Entität aktiviert werden.  Zu den Beispielen zählen Warteschlangen, Wissensmanagement, SLA, Duplikaterkennung, Änderungsnachverfolgung, Mobile offline, Funktion, Feldsicherheit, Relevanzsuche, Portale für Dynamics 365-Webportallösungen und N:N-Beziehungen zwischen virtuellen Entitäten.  
- Virtuelle Entitäten sind im Besitz der Organisation und unterstützen und nicht die Common Data Service-Sicherheitskonzepte auf Zeilenebene. Wir empfehlen, ein eigenes Sicherheitsmodell für die externe Datenquelle zu implementieren.  
- Wir empfehlen, bei Verwendung von virtuellen Entitäten in erweiterten Suchen nur eine Datenquelle anzusprechen. Beispielsweise wird das Erstellen einer erweiterten Suche, durch die letztendlich eine Verbindung zwischen Daten im Eigenformat des Common Data Service und den externen Daten der virtuellen Entität hergestellt wird, nicht unterstützt.  
- Feldmetadateneigenschaften, die bei Update validiert werden, gelten nicht für virtuelle Entitäten. Beispielsweise kann ein Ganzzahlenfeld in einem virtuellen Entitätsfeld so festgelegt werden, dass es einen Minimalwert Null hat. Allerdings, da der Wert aus einer externen Datenquelle kommt, gibt eine Abfrage Werte zurück, die weniger als null sind, wenn sie von einer virtuellen Entität abgerufen wird.  Die Minimalwert-Eigenschaft ist in der Abfrage nicht impliziert.  Sie müssten die Werte filtern, die größer als null sind, wenn diese gewünscht werden.
- Virtuelle Entitäten unterstützen nicht Änderungsnachverfolgung und können nicht synchronisiert werden mithilfe eines Common Data Service-Features, wie Datenexportservice.
  
### <a name="see-also"></a>Siehe auch  

[OData v4 Datenanbieterkonfiguration, Anforderungen und bewährten Methoden](virtual-entity-odata-provider-requirements.md)</br> 
[Entitäten erstellen und bearbeiten](create-edit-entities.md)</br>
[Erstellen und Bearbeiten von Feldern](create-edit-fields.md)
