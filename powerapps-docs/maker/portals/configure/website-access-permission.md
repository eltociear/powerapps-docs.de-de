---
title: Erstellen einer Websitezugriffsberechtigungen in Power Apps-Portalen | MicrosoftDocs
description: Erfahren Sie, wie Sie Websitezugriffsberechtigungen erstellen und Elementen in einem Portal zuordnen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ab85eb4feca871089366c8675305b4f6c741f0af
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873460"
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

    
