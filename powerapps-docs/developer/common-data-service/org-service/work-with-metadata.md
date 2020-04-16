---
title: Arbeiten mit Metadaten mithilfe des Organisationsdiensts (Common Data Service) | Microsoft-Dokumentation
description: Beschreibt, wie Sie mithilfe des Organisationsdiensts programmatisch auf das Metadatenmodell zuzugreifen und es ändern
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c63626828296ecd9e3a618390ede0f126e8d24fc
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155414"
---
# <a name="work-with-metadata-using-the-organization-service"></a>Arbeiten mit Metadaten mithilfe des Organisationsdiensts

Metadaten beziehen sich auf die Struktur von Entitäten, die verwendet werden, um Daten in Common Data Service zu verwalten. <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase> ist die Basisklasse für Klassen, die Metadateninformationen enthalten. In diesem Abschnitt wird beschrieben, wie Sie mithilfe des Organisationsdiensts programmatisch auf das Metadatenmodell zuzugreifen und es ändern.

> [!IMPORTANT]
> Das Hinzufügen, Entfernen oder Ändern von Entitäten, Alternativschlüsseln, Attributen oder Beziehungen können den regulären Systemvorgang behindern. Wenn Sie Änderungen an einem Produktionssystem anwenden, empfehlen wir, Sie planen diese Vorgänge, wenn es für die Benutzer am wenigsten Unterbrechung bedeutet.

## <a name="see-also"></a>Siehe auch

[Verwenden der Web-API mit Metadaten](../webapi/use-web-api-metadata.md)

[Arbeiten mit Metadaten mithilfe von Code](../metadata-services.md)