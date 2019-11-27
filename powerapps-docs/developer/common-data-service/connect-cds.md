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
ms.openlocfilehash: 82616711b47a2f14d32e7ee327b21e27df919a9b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748429"
---
# <a name="create-client-applications"></a>Erstellen von Client-Anwendungen

Sie können Client-Anwendungen erstellen, ohne Code zu schreiben, indem Sie Canvas und modellgesteuerte Anwendungen verwenden.
Mehr Informationen: [Übersicht über die Erstellung von Apps in PowerApps](../../maker/index.md)

Wenn die PowerApps-Optionen nicht Ihren Anforderungen entsprechen, können Sie eine Client-Anwendung mit Code erstellen.

## <a name="connecting-to-common-data-service"></a>Herstellen einer Verbindung mit Common Data Service

Um eine Verbindung zu einer Common Data Service-Umgebung herzustellen, benötigen Sie die URL zur Umgebung und Anmeldeinformationen für ein Benutzerkonto mit Zugriff auf diese Umgebung. Welche Strategie Sie verwenden werden, hängt davon ab, ob Sie diese Informationen haben oder ob Sie sie vom Benutzer Ihrer Anwendung erhalten müssen. 

### <a name="discovery-service"></a>Suchdienst

Benutzer können Zugang zu mehreren Common Data Service-Umgebungen haben. Wenn sich Ihre Anwendung nicht nur mit einer bestimmten Umgebung verbindet, können Sie dem Benutzer die Wahl lassen, mit welcher Umgebung er sich verbinden möchte, indem Sie seine Anmeldeinformationen verwenden, um *festzustellen*, welche Umgebungen seine Anmeldeinformationen zur Verwendung berechtigen. 

Um den Suchdienst nutzen zu können, müssen Sie den Benutzer für den Suchdienst authentifizieren und die für ihn verfügbaren Umgebungen abrufen. Normalerweise müssen Sie eine Möglichkeit implementieren, damit sie wählen können, mit welcher Umgebung sie sich verbinden möchten. Der nächste Schritt besteht darin, die Informationen über diese Umgebung zu verwenden, um sie ein zweites Mal zu authentifizieren, damit sie Zugang zu dieser spezifischen Umgebung erhalten.

Weitere Informationen: [Suchdienste](discovery-service.md)

### <a name="authentication"></a>Authentifizierung

Wenn Sie wissen, mit welcher Umgebung Sie den Benutzer verbinden wollen, müssen Sie ihn mit dieser Umgebung authentifizieren.

Weitere Informationen: [Authentifizierung mit Common Data Service-Webdiensten](authentication.md)