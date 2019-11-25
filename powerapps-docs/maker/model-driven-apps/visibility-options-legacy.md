---
title: Anzeigen oder Verbergen von modellgesteuerten App-Formularelementen mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie der Elemente wie Registerkarten, Abschnitte oder Felder anzeigen oder ausblenden
ms.custom: ''
ms.date: 06/11/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 7b9e8dc2-229c-455f-ae18-49e8d879ff71
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6004aab267da345dc1681dd920913e7858986d9d
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2710241"
---
# <a name="show-or-hide-model-driven-app-form-elements"></a>Anzeigen oder verbergen von modellgesteuerten App-Formularelementen

 Einige Arten von Formularelementen können standardmäßig ein- oder ausgeblendet werden. Felder, Abschnitte, Registerkarten, iFrames und Webressourcen bieten alle diese Option. Das Verwenden von Skripts oder Geschäftsregeln steuert die Sichtbarkeit diese Elemente, um ein dynamisches Formular erstellen, das eine Oberfläche bietet, die sich an die Bedingungen in dem Formular anpasst.  
  
> [!NOTE]
>  Das Ausblenden von Formularelementen ist keine empfohlene Möglichkeit zur Durchsetzung von Sicherheitsprinzipien. Es gibt verschiedene Möglichkeiten, mit denen Benutzer alle Elemente und Daten im Formular anzeigen können, wenn Elemente ausgeblendet werden. 
  
 Anstatt Formulare zu entwerfen, die von Skripts für die Sichtbarkeit von Optionen abhängen, sollten Sie überlegen, ob ein Geschäftsprozessfluss, ein Dialogfeld oder der Wechsel zu einem anderen Formular für Ihre Anforderungen die bessere Lösung sein könnte. Wenn Sie Skripts verwenden, sollten Sie sicherstellen, dass jedes Element, das möglicherweise ausgeblendet wird, standardmäßig ausgeblendet ist. Es sollte nur durch Skripte angezeigt werden, wenn Ihre Logik dies verlangt. Auf diese Weise wird es nicht in Präsentationen angezeigt, die keine Skripts unterstützen.  

## <a name="next-steps"></a>Nächste Schritte

[Übersicht zur Formular-Editor-Benutzeroberfläche](form-editor-user-interface-legacy.md)
