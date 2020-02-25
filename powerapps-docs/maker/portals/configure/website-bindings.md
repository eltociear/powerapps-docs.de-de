---
title: Erstellen und Verwalten von Website-Bindungen in Portalen | MicrosoftDocs
description: Erfahren Sie, wie Sie Website-Bindungen in Portalen erstellen und verwalten.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/12/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 294e1040f79ed5a25521ae2a861ccd30cdbfaf3e
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977550"
---
# <a name="create-and-manage-website-bindings"></a>Erstellen und verwalten von Website-Bindungen

In einem Portal ist die Standardmethode zum Auswählen einer Website das Auffinden einer Website durch Übereinstimmen mit dem Namen der Website, die in der Datei web.config dieses bestimmten Portale definiert ist. Website-Bindungen bieten alternative Methoden zur Auswahl einer Website unter Verwendung des Hostnamens beim Laden eines Portale oder des Pfades der Anfrage zur Auswahl der entsprechenden Website. Dadurch entfällt die Notwendigkeit, separate web.config-Dateien für jede Version einer bestimmten Website zu ändern. So wird die Bereitstellung der Portale zu verschiedenen Entwicklungs-, Staging- und Produktionsumgebungen optimiert. Darüber hinaus ist so eine allgemeinen Portal-Codebasis möglich, um mehrere Websites auszuführen.

## <a name="manage-website-bindings"></a>Verwalten von Websitebindungen

Website-Bindungen können innerhalb von Power Apps-Portalen erstellt, bearbeitet oder gelöscht werden. 

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Öffnen Sie **Portale** > **Websitebindungen**.

3. Klicken Sie auf **Neu**, um eine neue Website-Bindung zu erstellen.

4. Zur Bearbeitung einer vorhandenen Website-Bindung wählen Sie den Namen der Website-Bindung aus.

5. Hinzufügen der entsprechenden Werte zu den Feldern.

6. Klicken Sie auf **Speichern und schließen**.

### <a name="website-binding-attributes"></a>Attribute von Website-Bindungen

Dies sind die Attribute, die bei allen Bindungen gebräuchlich sind.

|Name|Beschreibung|
|-----|----------|
|Name| Ein Titel zur Identifizierung der Website-Bindung beim Betrachten der Datensätze.|
|Website|Die [Website](websites.md), die über das Portal ausgwewählt werden soll.|
|Veröffentlichungsdatum|Ein Datum, das bestimmt, wann die Website ausgewählt werden darf.|
|Ablaufdatum|Ein Datum, das bestimmt, wann die Website nicht mehr ausgewählt ist.|
|||

#### <a name="application-settings"></a>Anwendungseinstellungen

Geben Sie für eine Bindung auf Anwendungsebene Werte für diese Attribute an. Diese Bindung ordnet auf Grundlage der IIS-Website oder -Anwendung zu.

|Name|Beschreibung|
|-----|----------|
|Websitename|Der Namen der IIS-Website.|
|Virtueller Pfad|Der Name der IIS-Anwendung unter der Website.|
|||

Für Azure-Websites und -Cloudservices werden die Werte für den Standortsnamen und die virtuellen Werte von den Knoten <Site> und <VirtualApplication> der Datei **ServiceDefinition.csdef** bestimmt.

```
<ServiceDefinition>
  <WebRole>
    <Sites>
      <Site name=Dynamics Portals>
        <VirtualApplication name=customer-portal/>
```

### <a name="see-also"></a>Siehe auch
[Erstellen und verwalten von Websites](websites.md)
