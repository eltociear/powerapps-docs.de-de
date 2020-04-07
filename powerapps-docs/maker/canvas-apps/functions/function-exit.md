---
title: Funktion „Exit“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktion "Exit" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/02/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e0ed91cc66f5b42bbea769443ad086476245029c
ms.sourcegitcommit: 49b69129262a9b530e69508e84c3822b742066df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759804"
---
# <a name="exit-function-in-power-apps"></a>Exit-Funktion in powerapps
Beendet die derzeit ausgelaufende APP und meldet optional den aktuellen Benutzer ab.

## <a name="description"></a>Beschreibung
Die **Exit**-Funktion beendet die derzeit ausgeführte App. Der Benutzer wird zur Liste der apps zurückgegeben. Der Benutzer kann dann eine andere zu öffnende App auswählen.  

**Exit** beendet jede weitere Formel Auswertung. Alle Funktionsaufrufe, die nach dem **Beenden** mit einem [Semikolon-Operator](operators.md) verkettet sind, werden nicht ausgeführt.   

Verwenden Sie das optionale *SignOut* -Argument, um den aktuellen Benutzer von powerapps zu signieren. *SignOut* ist nützlich, wenn Geräte freigegeben werden, um die Benutzersicherheit sicherzustellen.

Beim Erstellen der APP wird der Benutzer durch Aufrufen von **Exit** nicht beendet oder abgemeldet.  Die Auswertung der restlichen Formel wird jedoch beendet.

**Exit** kann nur in [Verhaltens Formeln](../working-with-formulas-in-depth.md)verwendet werden.

> [!NOTE]
> Die Abmeldung mit der **Exit** -Funktion wird nicht unterstützt, wenn die app in einem Webbrowser ausgeführt wird.

## <a name="syntax"></a>Syntax
**Exit**([*SignOut*])

* *SignOut* – optional. Ein boolescher Wert, der bei " *true* " den aktuellen Benutzer von powerapps signiert.  Der Standardwert ist *false* , und der Benutzer bleibt angemeldet.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | 
| --- | --- | 
| **Exit ()** | Beendet die aktuelle APP und lässt den Benutzer angemeldet.  Der Benutzer wird zur Liste der apps zurückgegeben.  |
| **Exit (&nbsp;true&nbsp;)** | Beendet die aktuelle APP, und der Benutzer wird abgemeldet.  Der Benutzer muss sich mit seinen Anmelde Informationen wieder anmelden, bevor er eine APP ausführen kann. | 


