---
title: Websites in Portalen verwalten | MicrosoftDocs
description: Erfahren Sie, wie Sie Websites in Portalen verwalten.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/14/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8f085f6958be120d689d04cad904804b8f891530
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2019
ms.locfileid: "2817653"
---
# <a name="manage-websites"></a>Verwalten von Websites

Eine Website ist die Kernentität der Portal-Anwendung. Eine Portal-Anwendung wählt einen einzelnen Website-Datensatz aus, und damit wird bestimmt, welche Portalentitäten [Webseiten](web-page.md), [Webdateien](web-files.md), [Webrollen](create-web-roles.md), [Inhaltsausschnitte](customize-content-snippets.md) usw. bei der Anwendung anwendbar sind.

Da eine Website einen Anwendungsbereich bereitstellt, können mehrere verschiedene Portalanwendungen mit einem einzigen Unternehmen verbunden werden.

> [!NOTE]
> Die Ermittlung, an welchen Websitedatensatz eine bestimmte Portal-Anwendung gebunden wird, hängt gewöhnlich vom Namen der Website ab, der in der Konfiguration der Portalbereitstellung angegeben wird.
Es ist jedoch auch möglich, dies durch einen URL-Pfad-Präfix (siehe die Beschreibung der übergeordneten Website und Teil-URL unter) [Website-Attribute](#website-attributes)) oder nach Domäne, mithilfe von Website-Bindungen zu steuern.

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
|-----|----------|
|Name|Der beschreibende Name der Website. In diesem Feld ist ein Eintrag erforderlich.|
|Primärer Domänenname|Der primäre Domänenname des Portals, dem dieser Websitedatensatz hinzugefügt wird.|
|Übergeordnete Website|Die übergeordnete Website der Website. Dieses Feld kann im Allgemeinen ignoriert werden, außer in bestimmten erweiterten Portalkonfigurationen, bei denen eine einzelne Portal-Anwendung am Anwendungsstammpfad an eine Master-Website gebunden ist, wobei mindestens eine untergeordnete Website an bestimmten Unterpfaden verfügbar ist.|
|Teil-URL|Das URL-Stammpfadsegment für alle URLs pfadsegment URLs, die für die mit dieser Website verknüpften Portalentitäten generiert wurden.<br>Wenn beispielsweise eine Portal-Anwendung bereitgestellt wird, um am Stamm der Domäne example.com verfügbar zu sein, wird dieses Attribut über keinen Wert verfügt, wird die Start-Webseite einer Anwendungs-Webseite durch eine Anforderung an `http://example.com/` gerendert (da die Teil-URL einer Start-Webseite auf "/" festgelegt sein muss).<br>Wenn dieses Attribut auf den Wert "my-website" festgelegt wird, wird die Start-Webseite stattdessen die URL `http://example.com/my-website/` aufweisen und alle Sieten der Website verfügen über denselben "/my-website/ "Pfad-Präfix.<br>In den meisten Portalkonfigurationen kann dieses Feld ignoriert und leer gelassen werden.<br>Partielle URL-Werte werden als URL-Pfadsegmente verwendet. Daher sollten sie keine ungültigen URL-Pfadzeichen enthalten, wie "?", "#", "!", "%". Da Portal-URLs generiert werden, indem Teil-URL-Werte mit Schrägstrichen ("/") verknüpft werden, sollten sie diese Schrägstriche grundsätzlich nicht enthalten.<br>Die empfohlene Vorgehensweise ist, partielle URL-Werte auf Buchstaben, Zahlen und Bindestriche oder Unterstriche zu beschränken. Zum Beispiel: "Pressemitteilungen", "Users_Guide", "product1".|
|||

### <a name="see-also"></a>Siehe auch
[Websitebindungen](website-bindings.md)
