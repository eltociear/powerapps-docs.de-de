---
title: Übersicht über Buildtools für Azure DevOps| Microsoft Docs
description: Bei PowerApps build tools handelt es sich um eine Sammlung von PowerApps-spezifischen Azure DevOps-Buildaufgaben, die vermeiden, dass Skripts manuell heruntergeladen werden müssen, um die Entwicklung von PowerApps zu verwalten.
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
ms.openlocfilehash: bf3e34dde090b616687e597dc7df099d9559b0ce
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748438"
---
# <a name="powerapps-build-tools-for-azure-devops-overview"></a>Übersicht über PowerApps build tools für Azure DevOps


[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Verwenden Sie PowerApps build tools, um allgemeine Build- und Bereitstellungsaufgaben in Verbindung mit PowerApps zu automatisieren. Dazu gehören die Synchronisierung von Lösungsmetadaten (a.k.a. Lösungen) zwischen Entwicklungsumgebungen und Quellsteuerelement, die Generierung von Build-Artefakten, die Bereitstellung von Downstreamumgebungen, die Bereitstellung und Aufhebung der Bereitstellung von Umgebungen und die Möglichkeit, statistische Analyseprüfungen der Lösung mithilfe des PowerApps-Prüfdienstes durchzuführen.

> [!IMPORTANT]
>
> - PowerApps build tools sind eine Vorschaufunktion.
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

  
## <a name="what-are-powerapps-build-tools"></a>Was sind PowerApps build tools?

Bei PowerApps build tools handelt es sich um eine Sammlung von PowerApps-spezifischen Azure DevOps-Buildaufgaben, die vermeiden, dass benutzerdefinierte Tools und Skripts manuell heruntergeladen werden müssen, um den Anwendungslebenszyklus von PowerApps zu verwalten. Die Aufgaben können einzeln verwendet werden, um eine einfache Aufgabe durchzuführen, z. B. Importieren einer Lösung in eine Downstreamumgebung, oder zusammen in einer der Pipeline verwendet werden, um ein Szenario zu orchestrieren, z. B. „Buildartefakt generieren“, „Für Tests bereitstellen“ oder „Änderungen von Entwicklern sammeln“. Die Buildaufgaben können größtenteils in folgende Typen kategorisiert werden:

- Helfer 
- Qualitätsprüfung 
- Lösung 
- Umgebungsverwaltung 

## <a name="get-the-powerapps-build-tools"></a>Beschaffen der PowerApps build tools 
Die PowerApps build tools können in Ihre Azure DevOps-Organisation vom [Azure Marketplace](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerApps-BuildTools) installiert werden. Wenn sie installiert sind, sind alle Aufgaben, die in den PowerApps build tools enthalten sind, verfügbar, um in einer neuen oder vorhandenen Pipeline hinzugefügt zu werden, und können auf einfache Weise gefunden werden, indem Sie nach **PowerApps** suchen.

![Beschaffen von Buildtools](media/build-tools-download.png)
 
## <a name="next-step"></a>Nächster Schritt

[Aufgaben von Buildtools](build-tools-tasks.md)
