---
title: Erstellen von Clientanwendungen (Common Data Service) | Microsoft Docs
description: Stellt die Konzepte vor, die zur Erstellung benutzerdefinierter Client-Anwendungen, die sich per Code mit Common Data Service verbinden, erforderlich sind.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 29f6cca10ca81eacc9f70c589b8dc12f0e0cd466
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883532"
---
# <a name="create-client-applications"></a>Erstellen von Client-Anwendungen

Sie können Client-Anwendungen erstellen, ohne Code zu schreiben, indem Sie Canvas und modellgesteuerte Anwendungen verwenden.
Mehr Informationen: [Übersicht über die Erstellung von Apps in Power Apps](../../maker/index.md)

Wenn die Power Apps-Optionen nicht Ihren Anforderungen entsprechen, können Sie eine Client-Anwendung mit Code erstellen.

## <a name="connecting-to-common-data-service"></a>Herstellen einer Verbindung mit Common Data Service

Um eine Verbindung zu einer Common Data Service-Umgebung herzustellen, benötigen Sie die URL zur Umgebung und Anmeldeinformationen für ein Benutzerkonto mit Zugriff auf diese Umgebung. Welche Strategie Sie verwenden werden, hängt davon ab, ob Sie diese Informationen haben oder ob Sie sie vom Benutzer Ihrer Anwendung erhalten müssen. 

### <a name="discovery-service"></a>Suchdienst

Benutzer können Zugang zu mehreren Common Data Service-Umgebungen haben. Wenn sich Ihre Anwendung nicht nur mit einer bestimmten Umgebung verbindet, können Sie dem Benutzer die Wahl lassen, mit welcher Umgebung er sich verbinden möchte, indem Sie seine Anmeldeinformationen verwenden, um *festzustellen*, welche Umgebungen seine Anmeldeinformationen zur Verwendung berechtigen. 

Um den Suchdienst nutzen zu können, müssen Sie den Benutzer für den Suchdienst authentifizieren und die für ihn verfügbaren Umgebungen abrufen. Normalerweise müssen Sie eine Möglichkeit implementieren, damit sie wählen können, mit welcher Umgebung sie sich verbinden möchten. Der nächste Schritt besteht darin, die Informationen über diese Umgebung zu verwenden, um sie ein zweites Mal zu authentifizieren, damit sie Zugang zu dieser spezifischen Umgebung erhalten.

Weitere Informationen: [Suchdienste](discovery-service.md)

### <a name="authentication"></a>Authentifizierung

Wenn Sie wissen, mit welcher Umgebung Sie den Benutzer verbinden wollen, müssen Sie ihn mit dieser Umgebung authentifizieren.

Weitere Informationen: [Authentifizierung mit Common Data Service-Webdiensten](authentication.md)