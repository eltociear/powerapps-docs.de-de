---
title: Entitäten erstellen und bearbeiten in Common Data Service | Microsoft-Dokumentation
description: Informationen zum Erstellen und Bearbeiten von Entitäten
ms.custom: ''
ms.date: 04/16/2019
ms.reviewer: ''
ms.service: powerapps
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
ms.openlocfilehash: d700c76009f45c4e28f78732e7ae52ab57693ccb
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040495"
---
# <a name="create-and-edit-entities-in-common-data-service"></a>Entitäten erstellen und bearbeiten in Common Data Service

Bevor Sie eine benutzerdefinierte Entität erstellen, prüfen Sie, ob die Verwendung einer vorhandenen Entität Ihre Anforderungen erfüllen könnte. Weitere Informationen [Neue Metadaten oder bestehende Metadaten erstellen](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Sie können zwei Designer verwenden, um eine Entität zu erstellen oder zu bearbeiten:

|Designer| Beschreibung|
|--|--|
|[Power Apps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Gibt eine einfache konzentrierte Erfahrung, aber einige besondere Einstellungen sind nicht verfügbar.<br />Weitere Informationen: <br />[Tutorial: Erstellen Sie eine benutzerdefinierte Entität, die Komponenten in Power Apps enthält](/powerapps/maker/common-data-service/create-custom-entity)<br />[Entitäten mit dem Power Apps-Portal erstellen und bearbeiten](create-edit-entities-portal.md)|
|Projektmappen-Explorer|Nicht so einfach, aber gibt mehr Flexibilität für weniger allgemeine Anforderungen. <br />Weitere Informationen: [Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer](create-edit-entities-solution-explorer.md)|

> [!NOTE]
> Sie können auch Entitäten in Ihrer Umgebung wie folgt erstellen:
> - Importieren Sie eine Lösung, die die Definition der Entität enthält.
> - Verwenden Sie Power-Abfrage, um neue Entitäten zu erstellen und diese mit Daten auszufüllen. Weitere Informationen: [Daten einer Entität in Common Data Service mithilfe von Power Query hinzufügen](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - Ein Entwickler kann [Metadatendienste](/powerapps/developer/common-data-service/use-web-services#metadata-services) verwenden, um ein Programm zu schreiben.

## <a name="entity-options-not-available-in-the-power-apps-portal"></a>Entitätsoptionen sind nicht verfügbar im Power Apps-Portal

Die Informationen in diesem Thema helfen Ihnen auswählen, welche Designer Sie verwenden können. Sie können das Power Apps-Portal verwenden, um die Entität zu erstellen, es sei denn, Sie müssen eine der folgenden Anforderungen erfüllen:

- Steuern des Anpassungspräfix

  Ein Teil des Namens jeder benutzerdefinierten Entität, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diese Entität entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](change-solution-publisher-prefix.md).

- Ändert die Symbole für eine benutzerdefinierte Entität

  Standardmäßig haben alle benutzerdefinierten Entitäten in der Modell-angetriebenen App die gleichen Symbole. Sie können die Symbole für Bildwebressourcen erstellen, die Sie für die benutzerdefinierten Entitäten möchten. Weitere Informationen: [Symbole für benutzerdefinierte Entitäten ändern](../model-driven-apps/change-custom-entity-icons.md). 

- Ändern Sie die folgenden Eigenschaften, die erst aktiviert werden können:

  [!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

- Ändern Sie die folgenden Eigenschaften:

  |Option   |Beschreibung  |
  |---------|---------|
  |**Bereiche, in denen diese Entität angezeigt wird**|In der Webanwendung können Sie eine der verfügbaren Siteübersichtsbereiche zum Anzeigen diese Entität auswählen. Dies gilt nicht für modellgestützte Apps.|
  |**Überwachung**|Sofern für Ihre Organisation eine Überwachung aktiviert ist, können im Laufe der Zeit Änderungen an Entitätsdatensätzen erfasst werden. Wird die Überwachung einer Entität aktiviert, gilt dies auch für alle Felder der Entität. Sie können Felder auswählen oder löschen, bei denen die Überwachung aktiviert werden soll.|
  |**Farbe**|Legen Sie eine Farbe für die Entität in modellgestützen Apps fest.|
  |**Dokumentenverwaltung**|Nachdem weitere Aufgaben zur Aktivierung der Dokumentenverwaltung für Ihre Organisation ausgeführt wurden, ermöglicht die Aktivierung dieser Funktion eine Integration der Entität in SharePoint. |
  |**Für mobile Nutzung aktivieren**|Machen Sie diese Entität für Dynamics 365 for Phones and Tablets-Apps verfügbar. Sie können dieser Entität den Status **Schreibgeschützt für Mobile** zuweisen.<br /><br /> Wenn für die Formulare einer Entität eine Erweiterung erforderlich ist, die von Apps für Dynamics 365 for Phones and Tablets nicht unterstützt wird, können Sie mit dieser Einstellung sicherstellen, dass die Daten für diese Entitäten nicht von Benutzern der mobilen App bearbeitet werden können.|
  |**Für Phone Express aktivieren**|Machen Sie diese Entität für die Dynamics 365 for Phones-App verfügbar.|
  |**Lesebereich in Dynamics 365 for Outlook**|Bestimmt, ob der Entität im Lesebereich der Dynamics 365 for Outlook-App angezeigt wird.|
  |**Benutzerdefinierte Hilfe verwenden**|Wenn diese Option aktiviert ist, legen Sie eine Hilfe-URL fest, um zu steuern, welche Seite Benutzern angezeigt wird, wenn sie in der Anwendung auf die Hilfe-Schaltfläche klicken. Verwenden Sie diesen Antworttyp, um Anweisungensbesonderen Ihren Unternehmensprozessen für die Entität angeben.|


### <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer](create-edit-entities-solution-explorer.md)<br />
[Tutorial: Erstellen Sie eine benutzerdefinierte Entität, die Komponenten in Power Apps enthält](/powerapps/maker/common-data-service/create-custom-entity)<br />
[Entität bearbeiten](edit-entities.md)<br />
[Entwicklerdokumentation: Kundenentität erstellen](/dynamics365/customer-engagement/developer/org-service/create-custom-entity)
