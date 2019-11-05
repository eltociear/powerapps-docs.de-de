---
title: Erstellen von Website Zugriffsberechtigungen in Dynamics 365-Portalen | MicrosoftDocs
description: Erfahren Sie, wie Sie den Elementen in einem Portal Website Zugriffsberechtigungen erstellen und zuordnen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0ac02992498204efc42a52e736284ea134ed42f5
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551023"
---
# <a name="create-website-access-permissions"></a>Zugriffsberechtigungen für Websites erstellen

Zugriffsberechtigungen für Websites sind ein Berechtigungs Satz, der einer [webrolle](create-web-roles.md)zugeordnet ist, der die gleichzeitige Bearbeitung der verschiedenen Inhalts verwalteten Elemente innerhalb des Portals als nur Webseiten zulässt. Mit den Berechtigungseinstellungen wird festgelegt, welche Komponenten im Portal verwaltet werden können.

| Name                         | Beschreibung                                                                                      |
|------------------------------|--------------------------------------------------------------------------------------------------|
| Verwalten von Inhalts Ausschnitten      | Ermöglicht die Bearbeitung von Ausschnitt Steuerelementen.                                                          |
| Site Marker verwalten          | Ermöglicht die Bearbeitung von Hyperlinks, die Site Marker verwenden                                           |
| Verwalten von weblinksets         | Ermöglicht das Bearbeiten von [weblinksets](manage-web-links.md), einschließlich des Hinzufügens von Weblinks aus einem weblinksatz. |
| Vorschau der nicht veröffentlichten enti | Ermöglicht das Anzeigen von im Portal verfügbar gemachten Entitäten mit dem Veröffentlichungsstatus Draft.             |
|||

So erstellen Sie eine Website Zugriffsberechtigung und fügen Sie einer webrolle hinzu:

1. Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2. Wechseln Sie zu **Portale** > **Website Zugriffsberechtigungen**.

3. Wählen Sie **Neu** aus.

4. Geben Sie unter **Allgemein**den Namen Name und Website ein, und wählen Sie die erforderlichen Berechtigungen aus.

5. Wählen Sie unter **Webrollen**die webrolle aus, und fügen Sie Sie hinzu, um die Berechtigung zuzuordnen.

6. Speichern Sie die Änderungen.

    ![Zugriffsberechtigung für Website erstellen](../media/website-access-permission.png "Zugriffsberechtigung für Website erstellen")  
