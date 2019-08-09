---
title: Eine eingebettete Canvas-App freigeben | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="share-an-embedded-canvas-app"></a>Freigeben einer eingebetteten Canvas-App
In diesem Thema wird erklärt, wie Sie eine eingebettete Canvas-App freigeben, die Sie bereits erstellt haben.

Nachdem Sie eine eingebettete Canvas-App erstellt und einem modellgestützten Formular hinzugefügt haben, müssen Sie sicherstellen, dass alle Benutzer, die Zugriff auf das modellgestützte Formular haben, auch über Zugriff auf die Canvas-App und von ihr verwendeten Daten verfügen. Informationen halten die folgenden Richtlinien bereit:
-   Geben Sie die eingebettete Canvas-App für alle Benutzern in der Organisation oder einer Sicherheitsgruppe oder für bestimmte Benutzer frei. Weitere Informationen: [Freigeben einer App](../canvas-apps/share-app.md#share-an-app).
-   Stellen Sie sicher, dass alle Benutzer über die entsprechenden Berechtigungen für die Common Data Service-Entitäten verfügen, die von der eingebetteten Canvas-App verwendet werden. Weitere Informationen: [Verwalten von Entitätsberechtigungen](../canvas-apps/share-app.md#manage-entity-permissions)
-   Stellen Sie sicher, dass Benutzer über die entsprechende Berechtigung für Daten auf allen Cloudservices verfügen, die von der eingebetteten Canvas-App verwendet werden, z. B. SharePoint oder OneDrive. Die Freigabeschritte sind für jeden Cloudservice unterschiedlich und liegen außerhalb des Rahmens von PowerApps.

> [!NOTE]
> Aktuell können Sie das **Canvas-App**-Recht in einer Sicherheitsrolle nicht verwenden, um App-Benutzern Zugriff auf eine eingebettete oder eigenständige Canvas-App zu gewähren.

Eingebettete Canvas-Apps sind auch lösungsfähig. Standardmäßig werden eingebettete Canvas-Apps in derselben Lösung wie das modellgestützte Formular des Hosts erstellt. Um die eingebettete Canvas-App von einer Umgebung in eine andere zu verschieben, exportieren und importieren Sie eingebettete Canvas-Apps als Teil einer Lösung wie jede andere Komponente.

## <a name="see-also"></a>Siehe auch
[Einbetten einer Canvas-App in einem modellgesteuerten Formular](embed-canvas-app-in-form.md) <br />
[Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular](embedded-canvas-app-add-classic-designer.md) <br />
[Bearbeiten einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-edit-classic-designer.md) <br />
[Anpassen der Bildschirmgröße und Ausrichtung einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-customize-screen.md) <br />
[Führen Sie vordefinierte Aktionen aus einer eingebetteten Canvas-App auf dem Hostformular aus](embedded-canvas-app-actions.md) <br />
[Eigenschaften und Aktionen des ModelDrivenFormIntegration-Steuerelements](embedded-canvas-app-properties-actions.md) <br />
[Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps](embedded-canvas-app-guidelines.md) <br />
[Migrieren von eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion als die neueste Version erstellt wurden](embedded-canvas-app-migrate-from-preview.md) <br />
