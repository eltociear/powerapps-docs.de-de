---
title: Übersicht über Buildtools für Azure DevOps| Microsoft Docs
description: 'Bei PowerApps-Buildtools handelt es sich um eine Sammlung von PowerApps-spezifischen Azure DevOps-Buildaufgaben, die vermeiden, dass Skripts manuell heruntergeladen werden müssen, um die Entwicklung von PowerApps zu verwalten.'
ms.custom: ''
ms.date: 07/21/2019
ms.reviewer: Dean-Haas
ms.service: powerapps
ms.topic: article
author: mikkelsen2000
ms.author: pemikkel
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="powerapps-build-tools-for-azure-devops-overview"></a>Übersicht über PowerApps-Buildtools für Azure DevOps


[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Die Verwendung von PowerApps-Buildtools, um allgemeine Build- und Bereitstellungsaufgaben in Verbindung mit PowerApps zu automatisieren. Dazu gehören die Synchronisierung von Lösungsmetadaten (a.k.a. Lösungen) zwischen Entwicklungsumgebungen und Quellsteuerelement, die Generierung von Build-Artefakten, die Bereitstellung von Downstreamumgebungen, die Bereitstellung und Aufhebung der Bereitstellung von Umgebungen und die Möglichkeit, statistische Analyseprüfungen der Lösung mithilfe des PowerApps-Prüfungsdienst durchzuführen.

> [!IMPORTANT]
>
> - PowerApps-Buildtools sind eine Vorschaufunktion.
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

  
## <a name="what-are-powerapps-build-tools"></a>Was sind PowerApps-Buildtools?

Bei PowerApps-Buildtools handelt es sich um eine Sammlung von PowerApps-spezifischen Azure DevOps-Buildaufgaben, die vermeiden, dass benutzerdefinierte Tools und Skripts manuell heruntergeladen werden müssen, um den Anwendungslebenszyklus von PowerApps zu verwalten. Die Aufgaben können einzeln verwendet werden, um eine einfache Aufgabe durchzuführen, z. B. Importieren einer Lösung in eine Downstreamumgebung, oder zusammen in einer der Pipeline verwendet werden, um ein Szenario zu orchestrieren, z. B. „Buildartefakt generieren“, „Für Tests bereitstellen“ oder „Änderungen von Entwicklern sammeln“. Die Buildaufgaben können größtenteils in folgende Typen kategorisiert werden:

- Helfer 
- Qualitätsprüfung 
- Lösung 
- Umgebungsverwaltung 

## <a name="get-the-powerapps-build-tools"></a>Beschaffen der PowerApps-Buildtools 
Die PowerApps-Buildtools können in Ihrer Azure DevOps-Organisation über den [Azure Marketplace](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerApps-BuildTools) installiert werden. Wenn sie installiert sind, sind alle Aufgaben, die in den PowerApps-Buildtools enthalten sind, verfügbar, um in einer neuen oder vorhandenen Pipeline hinzugefügt zu werden, und können auf einfache Weise gefunden werden, indem Sie nach **PowerApps** suchen.

![Beschaffen von Buildtools](media/build-tools-download.png)
 
## <a name="next-step"></a>Nächster Schritt

[Aufgaben von Buildtools](build-tools-tasks.md)
