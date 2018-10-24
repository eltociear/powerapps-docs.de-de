---
title: Erstellen und Bearbeiten von Entitäten mit dem Lösungs-Explorer | Microsoft-Dokumentation
description: Erfahren Sie, wie mithilfe des Lösungs-Explorers eine Entität erstellt wird.
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.author: matp
manager: kvivek
ms.openlocfilehash: 48025088da85bf0685ba1a46efa4f3a989a20a58
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39682201"
---
# <a name="create-and-edit-entities-using-solution-explorer"></a>Erstellen und Bearbeiten von Entitäten mit dem Lösungs-Explorer

Sie können ganz einfach eine Entität über das PowerApps-Portal für die gängigsten Situationen erstellen, es sind jedoch nicht alle Funktionen im Portal implementiert. Wenn Sie die unter [Erstellen und Bearbeiten von Entitäten in Common Data Service für Apps](create-edit-entities.md) genannten Anforderungen erfüllen müssen, können Sie hierfür Entitäten mit dem Lösungs-Explorer erstellen oder bearbeiten.

## <a name="open-solution-explorer"></a>Öffnen des Lösungs-Explorers

Ein Teil des Namens einer Entität, die Sie erstellen, ist das Anpassungspräfix. Dieses wird basierend auf dem Lösungsherausgeber für die Lösung festgelegt, in der Sie momentan arbeiten. Wenn das Anpassungspräfix für Sie im Mittelpunkt steht, stellen Sie sicher, dass Sie in einer nicht verwalteten Lösung mit dem von Ihnen bevorzugten Anpassungspräfix für diese Entität arbeiten. Weitere Informationen finden Sie unter [Ändern des Präfixes für den Lösungsherausgeber](change-solution-publisher-prefix.md). 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entities"></a>Anzeigen von Entitäten

Klicken Sie im Lösungs-Explorer **Komponenten** auf den Knoten **Entitäten**.

![Anzeigen von Entitäten im Lösungs-Explorer](media/view-entities-solution-explorer.png)

## <a name="create-an-entity"></a>Erstellen einer Entität

Klicken Sie beim [Anzeigen von Entitäten](#view-entities) auf **Neu**, um das neue Entitätsformular zu öffnen.

![Neues Entitätsformular im Lösungs-Explorer](media/new-entity-form-solution-explorer.png)

Das neue Entitätsformular enthält zwei Registerkarten: Die Registerkarte **Allgemein** ist für Entitätsoptionen bestimmt. Die Registerkarte **Hauptfeld** ist für Optionen für die jeweilige einzelne Textzeile bestimmt, die jede Entität enthält. Sie definieren den Text, der angezeigt wird, wenn ein Link zum Öffnen der Entität in einem Suchfeld vorhanden ist.

Im Folgenden werden die einzelnen Abschnitte erläutert:
- [Konfigurieren des Hauptfelds](#configure-the-primary-field)
- [Konfigurieren der Pflichtfelder](#configure-required-fields)

> [!NOTE]
> Sie können aus der Entität auch eine benutzerdefinierte Aktivität machen. Durch diese Auswahl werden einige Standardoptionswerte geändert. Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten Aktivitätsentität](#create-custom-activity-entity).

Nachdem Sie die erforderlichen Optionen für die Entität festgelegt haben, klicken Sie auf ![Speicherbefehl](media/save-entity-icon-solution-explorer.png) zum Erstellen der benutzerdefinierten Entität.

### <a name="configure-the-primary-field"></a>Konfigurieren des Hauptfelds

Auf der Registerkarte **Hauptfeld** können Sie in der Regel die Standardwerte für das Hauptfeld übernehmen, Sie haben jedoch die folgenden Optionen:

|Feld   |Beschreibung  |
|---------|---------|
|**Anzeigename**|Geben Sie die lokalisierbare Beschriftung ein, die für dieses Feld in Formularen und Listen angezeigt wird. Der Standardwert lautet **Name**.|
|**Name**|Legen Sie den Namen fest, der für dieses Feld im System verwendet wird. Der Standardwert ist `<customization prefix>_name`.|
|**Maximale Länge**|Geben Sie die maximale Länge für die Feldwerte ein. Der Standardwert ist „100“.|

> [!NOTE]
> Diese Optionen gelten nicht, wenn die Entität eine Aktivitätsentität ist. Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten Aktivitätsentität](#create-custom-activity-entity).

### <a name="configure-required-fields"></a>Konfigurieren der Pflichtfelder

Auf der Registerkarte **Allgemein** müssen einige Optionen festgelegt werden, bevor Sie die Entität speichern können.

|Feld   |Beschreibung  |
|---------|---------|
|**Anzeigename**|Dies ist der Name für die Entität im Singular, der in der App angezeigt wird.<br />Dieser kann später geändert werden.|
|**Pluralname**|Dies ist der Name für die Entität im Plural, der in der App angezeigt wird.<br />Dieser kann später geändert werden.|
|**Name**|Dieses Feld ist basierend auf dem Anzeigenamen, den Sie eingeben, vorab aufgefüllt. Er enthält das Anpassungspräfix des Lösungsherausgebers.|
|**Besitz**|Sie können entweder „Im Besitz eines Benutzers oder Teams“ oder „Im Besitz der Organisation“ auswählen. Weitere Informationen finden Sie unter [Besitz von Entitäten](types-of-entities.md#entity-ownership).|

## <a name="edit-an-entity"></a>Bearbeiten einer Entität

Wählen Sie beim [Anzeigen von Entitäten](#view-entities) die Entität aus, die Sie bearbeiten möchten, und fahren Sie mit der Bearbeitung einer neuen Entität fort, die Sie gerade gespeichert haben.

> [!NOTE]
> Standardentitäten oder benutzerdefinierte Entitäten, die Teil einer verwalteten Lösung sind, weisen möglicherweise Einschränkungen bezüglich der Änderungen auf, die Sie vornehmen können. Wenn die Option nicht verfügbar oder deaktiviert ist, ist es Ihnen nicht gestattet, die Änderung vorzunehmen.

#### <a name="set-once-options"></a>Einmalig festzulegende Optionen

Die folgenden Optionen können nur einmal festgelegt und danach nicht mehr geändert werden, sobald Sie diese festgelegt haben. Legen Sie diese Optionen nur fest, wenn Sie diese tatsächlich benötigen.

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

#### <a name="options-that-you-can-change"></a>Änderbare Optionen

Die folgenden Eigenschaften können jederzeit geändert werden.

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-changeable-options-table](../../includes/cc_entity-changeable-options-table.md)]

Sie können außerdem die folgenden Änderungen vornehmen:
- [Erstellen und Bearbeiten von Feldern für Common Data Service für Apps](create-edit-fields.md)
- [Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)
- [Erstellen und Entwerfen von Formularen](../model-driven-apps/create-design-forms.md)
- [Erstellen eines Geschäftsprozessflusses zur Standardisierung von Prozessen](/flow/create-business-process-flow)

## <a name="delete-an-entity"></a>Löschen einer Entität

Als Benutzer mit der Sicherheitsrolle „Systemadministrator“ können Sie benutzerdefinierte Entitäten löschen, die nicht Teil einer verwalteten Lösung sind.  
  
> [!IMPORTANT]
>  Wenn Sie eine benutzerdefinierte Entität löschen, werden die Datenbanktabellen gelöscht, die Daten für diese Entität speichern, und alle darin enthaltenen Daten gehen verloren. Zugehörige Datensätze, die eine übergeordnete Beziehung zu der benutzerdefinierten Entität aufweisen, werden ebenfalls gelöscht. Weitere Informationen zu übergeordneten Beziehungen finden Sie unter [Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md).  
  
> [!NOTE]
> Daten aus einer Entität können nur wiederhergestellt werden, indem die Datenbank vor dem Zeitpunkt, an dem die Entität gelöscht wurde, wiederhergestellt wird. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Instanzen](/dynamics365/customer-engagement/admin/backup-restore-instances).

Klicken Sie beim [Anzeigen von Entitäten](#view-entities) auf den ![Löschbefehl](media/delete.gif) in der Symbolleiste.

Verwenden Sie beim Anzeigen einer Entität den Löschbefehl in der Menüleiste.

![Löschbefehl](media/delete-custom-entity-solution-explorer.png)

> [!WARNING]
> Durch das Löschen einer Entität, die Daten enthält, werden alle Daten entfernt. Diese Daten können nur über die Sicherung der Datenbank abgerufen werden.

> [!NOTE]
> Wenn Entitätsabhängigkeiten vorhanden sind, wird folgende Fehlermeldung angezeigt: **Die Komponente kann nicht gelöscht werden.** Dabei wird ein Link namens **Details** angezeigt, der weitere Informationen darüber enthält, warum die Entität nicht gelöscht werden kann. In den meisten Fällen ist der Grund eine Abhängigkeit, die entfernt werden muss. 
>
> Möglicherweise wird das Löschen einer Entität durch mehrere Abhängigkeiten verhindert. In dieser Fehlermeldung wird eventuell nur die erste Abhängigkeit angezeigt. Eine alternative Möglichkeit zum Ermitteln von Abhängigkeiten finden Sie unter [Identifizieren von Entitätsabhängigkeiten](#identify-entity-dependencies).



### <a name="identify-entity-dependencies"></a>Identifizieren von Entitätsabhängigkeiten

Bevor Sie Abhängigkeiten löschen, können Sie sie identifizieren und so verhindern, dass eine Entität gelöscht wird. 

1. Klicken Sie im Lösungs-Explorer mit der markierten Entität auf **Abhängigkeiten anzeigen** in der Befehlsleiste.

![Befehl „Abhängigkeiten anzeigen“](media/entity-show-dependencies.png)

2. Scrollen Sie die Liste im Dialogfenster, das geöffnet wird, nach rechts, um die Spalte **Abhängigkeitstyp** anzuzeigen.

![Typ der veröffentlichten Abhängigkeit](media/published-entity-dependency.png)

Bei **veröffentlichten** Abhängigkeiten ist das Löschen einer Entität nicht möglich. **Interne** Abhängigkeiten müssen vom System aufgelöst werden.  

3. Wenn Sie diese veröffentlichten Abhängigkeiten entfernen, sollten Sie die Entität löschen können.

 > [!NOTE]
 > Eine sehr häufige Abhängigkeit ist, dass ein anderes Entitätsformular ein Suchfeld für die Entität enthält, die Sie löschen möchten. Durch das Entfernen des Suchfelds aus dem Formular wird die Abhängigkeit aufgelöst.

## <a name="create-custom-activity-entity"></a>Erstellen einer benutzerdefinierten Aktivitätsentität

Um die Entität als Aktivitätsentität zu erstellen, verwenden Sie die gleichen Schritte in diesem Thema, mit Ausnahme des Schritts zum Auswählen von **Als Aktivitätsentität definieren**.

![Definieren als Aktivitätsentität](media/create-activity-entity-solution-explorer.png)

Eine Aktivitätsentität ist eine besondere Art von Entität, die Aktionen nachverfolgt, für die ein Eintrag in einem Kalender erstellt werden kann. Weitere Informationen finden Sie unter [Aktivitätsentitäten](types-of-entities.md#activity-entities).

Einige Eigenschaften der Entität sind nicht kompatibel, wenn Sie diese Option festlegen. Eine Aktivitätsentität muss bestimmten Standardverhalten entsprechen, die alle Aktivitätsentitäten verwenden.

Das Hauptfeld **Name** und **Anzeigenamen** werden auf **Betreff** festgelegt. Dies kann nicht geändert werden.

Die folgenden Optionen werden standardmäßig festgelegt und können nicht geändert werden:

 - **Feedback**
 - **Notizen (enthält Anlagen)**
 - **Verbindungen**
 - **Warteschlangen**
 - **Offlinefunktion für Dynamics 365 für Outlook**

Folgende Optionen können nicht festgelegt werden:

- **Bereiche, in denen diese Entität angezeigt wird**
- **Aktivitäten**
- **E-Mail-Sendestatus**
- **Seriendruck**
- **Einzeldatensatzüberwachung**
- **Mehrfachdatensatzüberwachung**

## <a name="create-a-virtual-entity"></a>Erstellen einer virtuellen Entität

Einige Optionen werden nur bei der Erstellung einer virtuellen Entität verwendet.

|Option   |Beschreibung  |
|---------|---------|
|**Virtuelle Entität**|Gibt an, ob die Entität eine virtuelle Entität ist.|
|**Datenquelle**|Gibt die Datenquelle für die Entität an.|

Weitere Informationen finden Sie unter [Erstellen und Bearbeiten von virtuellen Entitäten, die Daten aus einer externen Datenquelle enthalten](create-edit-virtual-entities.md).

### <a name="see-also"></a>Siehe auch
[Erstellen und Bearbeiten von benutzerdefinierten Entitäten in Common Data Service for Apps](create-edit-entities.md)<br />
[Tutorial: Erstellen benutzerdefinierter Entitäten mit Komponenten in PowerApps](/powerapps/maker/common-data-service/create-custom-entity)<br />
[Erstellen einer Lösung](create-solution.md)