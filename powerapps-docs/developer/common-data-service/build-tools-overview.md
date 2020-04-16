---
title: Übersicht über Buildtools für Azure DevOps| Microsoft Docs
description: Bei Power Apps build tools handelt es sich um eine Sammlung von Power Apps-spezifischen Azure DevOps-Buildaufgaben, die vermeiden, dass Skripts manuell heruntergeladen werden müssen, um die Entwicklung von Power Apps zu verwalten.
ms.custom: ''
ms.date: 07/21/2019
ms.reviewer: pehecke
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
ms.openlocfilehash: 111169c35463ba082a734082ea5eca1f4bab5c21
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156418"
---
# <a name="power-apps-build-tools-for-azure-devops-overview"></a>Übersicht über Power Apps build tools für Azure DevOps


[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Verwenden Sie Power Apps build tools, um allgemeine Build- und Bereitstellungsaufgaben in Verbindung mit Power Apps zu automatisieren. Dazu gehören die Synchronisierung von Lösungsmetadaten (a.k.a. Lösungen) zwischen Entwicklungsumgebungen und Quellsteuerelement, die Generierung von Build-Artefakten, die Bereitstellung von Downstreamumgebungen, die Bereitstellung und Aufhebung der Bereitstellung von Umgebungen und die Möglichkeit, statistische Analyseprüfungen der Lösung mithilfe des Power Apps-Prüfdienstes durchzuführen.

> [!IMPORTANT]
>
> - Power Apps build tools sind eine Vorschaufunktion.
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

  
## <a name="what-are-power-apps-build-tools"></a>Was sind Power Apps build tools?

Bei Power Apps build tools handelt es sich um eine Sammlung von Power Apps-spezifischen Azure DevOps-Buildaufgaben, die vermeiden, dass benutzerdefinierte Tools und Skripts manuell heruntergeladen werden müssen, um den Anwendungslebenszyklus von Power Apps zu verwalten. Die Aufgaben können einzeln verwendet werden, um eine einfache Aufgabe durchzuführen, z. B. Importieren einer Lösung in eine Downstreamumgebung, oder zusammen in einer der Pipeline verwendet werden, um ein Szenario zu orchestrieren, z. B. „Buildartefakt generieren“, „Für Tests bereitstellen“ oder „Änderungen von Entwicklern sammeln“. Die Buildaufgaben können größtenteils in folgende Typen kategorisiert werden:

- Helfer 
- Qualitätsprüfung 
- Lösung 
- Umgebungsverwaltung 

## <a name="get-the-power-apps-build-tools"></a>Beschaffen der Power Apps build tools 
Die Power Apps build tools können in Ihre Azure DevOps-Organisation vom [Azure Marketplace](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerApps-BuildTools) installiert werden. Wenn sie installiert sind, sind alle Aufgaben, die in den Power Apps build tools enthalten sind, verfügbar, um in einer neuen oder vorhandenen Pipeline hinzugefügt zu werden, und können auf einfache Weise gefunden werden, indem Sie nach **PowerApps** suchen.

![Beschaffen von Buildtools](media/build-tools-download.png)
 
## <a name="next-step"></a>Nächster Schritt

[Aufgaben von Buildtools](build-tools-tasks.md)
