---
title: Erstellen und bearbeiten Sie Entitäten in Common Data Service for Apps | MicrosoftDocs
description: Informationen zum Erstellen und Bearbeiten von Entitäten
ms.custom: ''
ms.date: 05/11/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: fa04f99d-a5f9-48cb-8bfb-f0f50718ccee
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-entities-in-common-data-service-for-apps"></a>Erstellen und bearbeiten Sie Entitäten in Common Data Service for Apps | MicrosoftDocs

Bevor Sie eine benutzerdefinierte Entität erstellen, prüfen Sie, ob die Verwendung einer vorhandenen Entität Ihre Anforderungen erfüllen könnte. Weitere Informationen [Neue Metadaten oder bestehende Metadaten erstellen](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Sie können zwei Designer verwenden, um eine Entität zu erstellen oder zu bearbeiten:

|Designer| Beschreibung|
|--|--|
|[PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Gibt eine einfache konzentrierte Erfahrung, aber einige besondere Einstellungen sind nicht verfügbar.<br />Weitere Informationen: <br />[Lernprogramm: Benutzerdefinierte Entität mit Komponenten in PowerApps erstellen](/powerapps/maker/common-data-service/create-custom-entity)<br />[Entitäten mit dem PowerApps-Portal erstellen und bearbeiten](create-edit-entities-portal.md)|
|Projektmappen-Explorer|Nicht so einfach, aber gibt mehr Flexibilität für weniger allgemeine Anforderungen. <br />Weitere Informationen: [Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer](create-edit-entities-solution-explorer.md)|

> [!NOTE]
> Sie können auch Entitäten in Ihrer Umgebung wie folgt erstellen:
> - Importieren Sie eine Lösung, die die Definition der Entität enthält.
> - Verwenden Sie Power-Abfrage, um neue Entitäten zu erstellen und diese mit Daten auszufüllen. Weitere Informationen:  [Daten einer Entität in Common Data Service für Apps mithilfe der Power-Abfrage hinzufügen](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - Ein Entwickler kann [Metadatendienste](/powerapps/developer/common-data-service/use-web-services#metadata-services) verwenden, um ein Programm zu schreiben.


## <a name="entity-options-not-available-in-the-powerapps-portal"></a>Entitätsoptionen sind nicht verfügbar in PowerApps-Portal

Die Informationen in diesem Thema helfen Ihnen auswählen, welche Designer Sie verwenden können. Sie können das PowerApps-Portal verwenden, um mit globalen Optionssätzen zu arbeiten, es sei denn, Sie müssen eine der folgenden Anforderungen erfüllen:

- Steuern des Anpassungspräfix

  Ein Teil des Namens jeder benutzerdefinierten Entität, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diese Entität entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md).

- Entität im Besitz der Organisation erstellen

  Standardmäßig erstellt das PowerApps-Portal **Benutzer oder Team** Entitäten. Verwendungsprojektmappen-explorer, um des Besitz auf **Organisation** festzulegen. Weitere Informationen finden Sie unter [Entitätsbesitz](types-of-entities.md#entity-ownership).

- Erstellen einer Aktivitätenentität

  Die Aktivitätsentität ist eine spezielle Art von Entität, die Aktionen nachverfolgt, für die ein Eintrag in einem Kalender vorgenommen werden kann. Mehr Informationen: [Aktivitäten-Entitäten](types-of-entities.md#activity-entities).

- Ändert die Symbole für eine benutzerdefinierte Entität

  Standardmäßig haben alle benutzerdefinierten Entitäten in der Modell-angetriebenen App die gleichen Symbole. Sie können die Symbole für Bildwebressourcen erstellen, die Sie für die benutzerdefinierten Entitäten möchten. Weitere Informationen: [Symbole für benutzerdefinierte Entitäten ändern](../model-driven-apps/change-custom-entity-icons.md). 

- Ändern Sie die folgenden Eigenschaften, die erst aktiviert werden können:

  [!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

- Ändern Sie die folgenden Eigenschaften:

  <!-- Based on ../../includes/cc_entity-changeable-options-table.md 
Removed these:

  /|**Description**/|Provide a meaningful description of the purpose of the entity./|

  /|**Primary Image**/|System entities that support images will already have an **Image** field. You can choose whether to display data in this field as the image for the record by setting this field to **[None]** or **Default Image**.<br /><br /> For custom entities you must first create an image field. Each entity can have only one image field. After you create one, you can change this setting to set the primary image. More information: [Image fields](../maker/common-data-service/types-of-fields.md#image-fields) /|-->

  |Option   |Beschreibung  |
  |---------|---------|
  |**Zugriffsteams**|Erstellen von Teamvorlagen für diese Entität. |
  |**Schnellerfassung erlauben**|Nachdem Sie ein **Formular für Schnellerfassung** für diese Entität erstellt und veröffentlicht haben, haben Personen die Möglichkeit, einen neuen Datensatz mithilfe der Schaltfläche **Erstellen** im Navigationsbereich zu schaffen. Weitere Informationen: [Erstellen und Entwerfen von Formularen](../model-driven-apps/create-design-forms.md)<br /><br /> Wenn dies für eine benutzerdefinierte Aktivitätsentität aktiviert ist, ist die benutzerdefinierte Aktivität in der Gruppe der Aktivitätsentitäten sichtbar, wenn Benutzer die Schaltfläche **Erstellen** im Navigationsbereich verwenden. Da Aktivitäten keine Schnellerfassungsformulare unterstützten, wird jedoch das Hauptformular verwendet, wenn man auf das Symbol der benutzerdefinierten Entität klickt.|
  |**Bereiche, in denen diese Entität angezeigt wird**|In der Webanwendung können Sie eine der verfügbaren Siteübersichtsbereiche wählen, um diese Entität anzuzeigen. Dies gilt nicht für Modell-angetriebene Apps.|
  |**Überwachung**|Ist die Überwachung für Ihre Organisation aktiviert, können im Laufe der Zeit Änderungen an Entitätsdatensätzen erfasst werden. Wenn Sie die Überwachung für eine Entität aktivieren, wird standardmäßig auch die Überwachung für alle Felder der Entität aktiviert. Sie können Felder auswählen, für die Sie die Überwachung aktivieren möchten, bzw. die Auswahl von Feldern aufheben.|
  |**Änderungsnachverfolgung**|Mit der neuen Änderungsnachverfolgungsfunktion  können die Daten auf leistungsorientierte Art synchronisiert werden, indem festgestellt wird, welche Daten geändert wurden, nachdem die Daten ursprünglich extrahiert oder zuletzt synchronisiert wurden.  |
  |**Farbe**|Legen Sie eine Farbe fest, die für die Modell-angetriebenen App verwendet wird.|
  |**Dokumentenverwaltung**|Nachdem weitere Aufgaben zur Aktivierung der Dokumentenverwaltung für Ihre Organisation ausgeführt wurden, ermöglicht die Aktivierung dieser Funktion die Teilnahme an der Integration mit SharePoint. |
  |**Duplikaterkennung**|Wenn die Duplikaterkennung für die Organisation aktiviert ist, ermöglicht die Aktivierung dieser Funktion die Erstellung von Duplikaterkennungsregeln für diese Entität.|
  |**Für mobile Nutzung aktivieren**|Machen Sie diese Entität für Apps von Dynamics 365 für Smartphones und Tablets verfügbar. Sie haben auch die Möglichkeit, der Entität **Schreibgeschützt für Mobile** zuzuweisen.<br /><br /> Wenn die Formulare für eine Entität eine Erweiterung erfordern, die nicht in Dynamics 365 for phones and tablets unterstützt wird, wird diese Einstellung verwendet, um sicherzustellen, dass die Daten für diese Entitäten von Benutzern der mobile App nicht bearbeitet werden können.|
  |**Für Phone Express aktivieren**|                                                                                                                                                                                                                                                                                                                                                                                                                                                  Machen Sie diese Entität für Dynamics 365 for Phones App verfügbar.|
  |**Seriendruck**|Benutzer können diese Entität mit dem Seriendruck verwenden.|
  |**Offlinefunktion für Dynamics 365 für Outlook**|Ob Daten in dieser Entität verfügbar sind, da Dynamics 365 for Outlook nicht mit dem Netzwerk verbunden ist.|
  |**Lesebereich in Microsoft Dynamics 365 für Outlook**|Ob der Entität im Lesebereich von Dynamics 365 for Outlook-App angezeigt wird.|
  |**Benutzerdefinierte Hilfe verwenden**|Wenn aktiviert legen Sie eine Hilfe-URL fest, um zu steuern, welche Seitenbenutzer sehen, wenn sie auf die Hilfeschaltfläche in der Anwendung klicken. Verwenden Sie diesen Antworttyp, um Anweisungensbesonderen Ihren Unternehmensprozessen für die Entität angeben.|


### <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer](create-edit-entities-solution-explorer.md)<br />
[Lernprogramm: Benutzerdefinierte Entität mit Komponenten in PowerApps erstellen](/powerapps/maker/common-data-service/create-custom-entity)<br />
[Bearbeiten einer Entität](edit-entities.md)<br />
[Entwicklerdokumentation: Kundenentität erstellen](/dynamics365/customer-engagement/developer/org-service/create-custom-entity)
