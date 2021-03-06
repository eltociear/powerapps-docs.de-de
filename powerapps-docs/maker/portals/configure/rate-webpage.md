---
title: Webseite oder Blogbeitrag im Portal bewerten bzw. darüber abstimmen | MicrosoftDocs
description: Anweisungen zum Aktivieren und Verwalten von Bewertungen auf einer Webseite auf einem Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 0dd86fde3ed867c68f2ca773c14b7656980436cc
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980655"
---
# <a name="rate-or-vote-on-a-webpage-on-a-portal"></a>Webseite oder Blogbeitrag im Portal bewerten bzw. darüber abstimmen

Mithilfe von Bewertungen können Benutzer eine Website bewerten bzw. darüber abstimmen. Bewertungen können auch für Kommentare zu Seiten aktiviert werden. Standardmäßig ist diese Funktion deaktiviert, kann aber seitenweise aktiviert werden.

Bewertungen sind benutzerdefinierte Aktivitäten und können daher wie jede andere Aktivität wie E-Mails, Telefonate usw. verwendet werden. Da Bewertungen Aktivitäten sind, ist es möglich, mit Anpassungen Bewertungen für beliebige Entitäten anzuzeigen, die angezeigt und im Portal gerendert werden sollen, einschließlich benutzerdefinierter Entitäten.

## <a name="enable-ratings-for-pages"></a>Seitenbewertungen aktivieren

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Gehen Sie zu **Portale** > **Webseiten**.

3. Wählen Sie die **Webseite** aus, für die Sie Bewertungen aktivieren möchten.

4. Auf der Registerkarte **Allgemein** unter **Seitenoptionen** legen Sie **Bewertungen aktivieren** auf **Ja** fest.

5. Klicken Sie auf **Speichern und schließen**.

## <a name="use-ratings"></a>Verwendung von Bewertungen

Benutzer können bei Webseiten, für die Seitenbewertungen aktiviert wurden und der Entwickler das Steuerelement für die Vorlage angewendet hat, mithilfe einer Bewertungsskala oder Abstimmung die Seiten bewerten, je nach ausgewähltem Typ beim Hinzufügen des Steuerelements zur Seitenvorlage.

### <a name="rating-type"></a>Bewertungstyp

![Bewertungstyp](../media/rating-type.png "Bewertungstyp")  

### <a name="vote-type"></a>Abstimmungstyp

![Abstimmungstyp](../media/vote-type.png "Abstimmungstyp")  

## <a name="manage-ratings"></a>Verwalten von Bewertungen

Die Bewertungen für Webseiten können in Power Apps-Portalen angezeigt, geändert oder gelöscht werden.

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Navigieren Sie zu der **Webseite**, deren Bewertungen Sie anzeigen möchten.

3. Wählen Sie auf der Registerkarte **Verknüpft** die Option **Aktivitäten** aus. In der zugeordneten Ansicht werden die Bewertungen für die ausgewählte Webseite aufgelistet. Innerhalb dieser Ansicht können Benutzer vorhandene Bewertungen ändern oder löschen.
