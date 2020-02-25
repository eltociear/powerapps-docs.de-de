---
title: Erstellen einer Websitezugriffsberechtigungen in Power Apps-Portalen | MicrosoftDocs
description: Erfahren Sie, wie Sie Websitezugriffsberechtigungen erstellen und Elementen in einem Portal zuordnen.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: c333039eddb7e0e8bb376a8b6850b18f9d1a46ad
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977839"
---
# <a name="create-website-access-permissions"></a>Erstellen von Websitezugriffsberechtigungen

Websitezugriffsberechtigungen sind ein Berechtigungsset, das einer [Webrolle](create-web-roles.md) zugeordnet ist, die die Frontside-Bearbeitung verschiedener Elemente mit verwaltetem Inhalt innerhalb des Portals zulässt, die keine Webseiten sind. Die Berechtigungseinstellungen bestimmen, welche Komponenten im Portal verwaltet werden können.

| Name                         | Beschreibung                                                                                      |
|------------------------------|--------------------------------------------------------------------------------------------------|
| Inhaltsausschnitte verwalten      | Ermöglicht das Bearbeiten der Snippet-Steuerelemente.                                                          |
| Websitemarkierungen verwalten          | Ermöglicht das Bearbeiten von Links, die Websitemarkierungen verwenden.                                           |
| Weblinksätze verwalten         | Ermöglicht das Bearbeiten von [Weblinksätzen](manage-web-links.md), einschließlich des Hinzufügens und Entfernens von Links aus einem Weblinksatz. |
| Unveröffentlichte Entitäten als Vorschau anzeigen | Ermöglicht die Anzeige von im Portal verfügbaren Entitäten, deren Veröffentlichungsstatus Entwurf ist.             |
|||

So erstellen Sie eine Websitezugriffsberechtigung und fügen Sie einer Webrolle hinzu:

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Wechseln Sie zu **Portale** > **Websitezugriffsberechtigungen**.

3. Wählen Sie **Neu** aus.

4. Geben Sie unter **Allgemein** den Namen und die Website ein, und wählen Sie die erforderlichen Berechtigungen aus.

    ![Erstellen von Websitezugriffsberechtigungen](../media/website-access-permission.png "Erstellen von Websitezugriffsberechtigungen")

5. Wählen Sie unter **Webrollen** die Option **Vorhandene Webrolle hinzufügen** aus, der die Berechtigung zugeordnet werden soll, und fügen Sie sie hinzu.

6. Speichern Sie die Änderungen.

    
