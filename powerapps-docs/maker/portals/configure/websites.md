---
title: Websites in Portalen verwalten | MicrosoftDocs
description: Erfahren Sie, wie Sie Websites in Portalen verwalten.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/30/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: ce0b60b8801873376696c446a56e28ffa69b8d80
ms.sourcegitcommit: 8e76afb331745f1da929a39e831634680dfa6008
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "3346933"
---
# <a name="manage-websites"></a>Verwalten von Websites

Eine Website ist die Kernentität der Portal-Anwendung. Eine Portal-Anwendung wählt einen einzelnen Website-Datensatz aus, und damit wird bestimmt, welche Portalentitäten, z. B. [Webseiten](web-page.md), [Webdateien](web-files.md), [Webrollen](create-web-roles.md) und [Inhaltsausschnitte](customize-content-snippets.md) usw. bei der Anwendung anwendbar sind.

Da eine Website einen Anwendungsbereich bereitstellt, können mehrere verschiedene Portalanwendungen mit einem einzigen Unternehmen verbunden werden.

> [!NOTE]
> Die Ermittlung, an welchen Websitedatensatz eine bestimmte Portal-Anwendung gebunden wird, hängt gewöhnlich vom Namen der Website ab, der in der Konfiguration der Portalbereitstellung angegeben wird.
Es ist jedoch auch möglich, dies durch Domänennamen oder Websitebindungen zu steuern.

## <a name="manage-websites"></a>Verwalten von Websites

Websites werden erstellt, wenn Sie ein neues Portal erstellen. Die erweiterte Website-Verwaltung kann jedoch über die Portal-Management-App ausgeführt werden. 

> [!WARNING]
> Wenn Sie einen Website-Datensatz löschen, werden auch Daten gelöscht, die sich auf den Website-Datensatz in Portal-Metadaten-Entitäten beziehen, z. B. Webseiten und Weblinks. Dies ist im Allgemeinen das gewünschte Verhalten, da es bedeutet, dass eine vollständige Website und alle zugehörigen Daten von einer Organisation in einem einzelnen Vorgang entfernt werden können.

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Navigieren Sie zu **Portale** > **Websites**.

3. Zur Bearbeitung einer vorhandenen Website wählen Sie den Website-Namen aus.

4. Hinzufügen der entsprechenden Werte zu den Feldern.

5. Klicken Sie auf **Speichern und schließen**.

### <a name="website-attributes"></a>Website-Attribute

|Name|Beschreibung|
|-|-|
|Name|Der beschreibende Name der Website. In diesem Feld ist ein Eintrag erforderlich.|
| Standardsprache | Standardsprache für das ausgewählte Portal. Bevor Sie die Standardsprache ändern, müssen Sie Folgendes tun: <br> - [Die Sprache in der Common Data Service-Umgebung hinzufügen](https://docs.microsoft.com/power-platform/admin/enable-languages). <br> - [Die Sprache im Bereich „Unterstützte Sprachen“](enable-multiple-language-support.md) für den Websites-Datensatz hinzufügen.
| Besitzer  | Der Besitzerkontaktdatensatz für den ausgewählten Website-Datensatz.
|Primärer Domänenname|Der primäre Domänenname des Portals, dem dieser Websitedatensatz hinzugefügt wird.|
|Übergeordnete Website\*|Die übergeordnete Website der Website. Dieses Feld kann im Allgemeinen ignoriert werden, außer in bestimmten erweiterten Portalkonfigurationen, bei denen eine einzelne Portal-Anwendung am Anwendungsstammpfad an eine Master-Website gebunden ist, wobei mindestens eine untergeordnete Website an bestimmten Unterpfaden verfügbar ist. <br>\* Nur aus Gründen der Abwärtskompatibilität, nicht für neue oder vorhandene Portale. |
| Kopf- und Fußzeilenvorlagen | Die [Webvorlagen für Kopf- und Fußzeilen](../liquid/store-content-web-templates.md#web-templates-as-page-templates) überschreiben globale Kopf- und Fußzeilen.
| Unterstützte Sprachen | Die [unterstützten Sprachen](enable-multiple-language-support.md) für den ausgewählten Website-Datensatz.

### <a name="see-also"></a>Siehe auch

[Websitebindungen](website-bindings.md)
