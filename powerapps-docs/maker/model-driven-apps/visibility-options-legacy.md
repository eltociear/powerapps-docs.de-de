---
title: Anzeigen oder Ausblenden von Formularelementen in einer modellgesteuerten App mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Formularelemente wie Registerkarten, Abschnitte oder Felder anzeigen bzw. ausblenden.
ms.custom: ''
ms.date: 06/11/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 86fafe70ae3bc04eff5e85a4baf3682c32427149
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39689266"
---
# <a name="show-or-hide-model-driven-app-form-elements"></a>Anzeigen oder Ausblenden von Formularelementen in einer modellgesteuerten App

 Mehrere Typen von Formularelementen können standardmäßig angezeigt oder ausgeblendet werden. Diese Möglichkeit besteht für Registerkarten, Abschnitte, Felder, iFrames und Webressourcen. Mithilfe von Formularskripts oder Geschäftsregeln kann die Sichtbarkeit dieser Elemente gesteuert werden, um ein dynamisches Formular zu erstellen und eine Benutzeroberfläche bereitzustellen, die sich an die Bedingungen im Formular anpasst.  
  
> [!NOTE]
>  Das Ausblenden von Formularelementen ist keine Methode, um die Sicherheit der Daten zu gewährleisten. Es gibt mehrere Möglichkeiten, wie Benutzer alle Elemente und Daten im Formular anzeigen können, wenn diese ausgeblendet sind. 
  
 Anstatt von Skripts abhängige Formulare zu entwerfen, um die Sichtbarkeit von Optionen zu steuern, sollten Sie überlegen, ob ein Geschäftsprozessfluss, ein Dialogfeld oder der Wechsel zu einem anderen Formular Ihre Anforderungen besser erfüllt. Stellen Sie beim Verwenden von Skripts sicher, dass jedes Element, das ausgeblendet sein könnte, standardmäßig ausgeblendet ist. Zeigen Sie es nur mit Skripts an, wenn es die Logik verlangt. Auf diese Weise wird es nicht in Darstellungen angezeigt, die keine Skripts unterstützen.  

## <a name="next-steps"></a>Nächste Schritte

[Überblick über die Benutzeroberfläche des Formular-Editors](form-editor-user-interface-legacy.md)