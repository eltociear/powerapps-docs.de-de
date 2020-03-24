---
title: Funktion „Exit“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktion "Exit" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/21/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1e66c9a6c079baef3b7f67631c4a21cda6334478
ms.sourcegitcommit: 1b29cd1fa1492037ef04188dd857a911edeb4985
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80122783"
---
# <a name="exit-function-in-power-apps"></a>Exit-Funktion in powerapps
Beendet die derzeit ausgelaufende APP und meldet optional den aktuellen Benutzer ab.

## <a name="description"></a>Beschreibung
Die **Exit**-Funktion beendet die derzeit ausgeführte App. Der Benutzer wird zur Liste der apps zurückgegeben. Der Benutzer kann dann eine andere zu öffnende App auswählen.  

**Exit** beendet jede weitere Formel Auswertung. Alle Funktionsaufrufe, die nach dem **Beenden** mit einem [Semikolon-Operator](operators.md) verkettet sind, werden nicht ausgeführt.   

Verwenden Sie das optionale *SignOut* -Argument, um den aktuellen Benutzer von powerapps zu signieren. *SignOut* ist nützlich, wenn Geräte freigegeben werden, um die Benutzersicherheit sicherzustellen.

Beim Erstellen der APP wird der Benutzer durch Aufrufen von **Exit** nicht beendet oder abgemeldet.  Die Auswertung der restlichen Formel wird jedoch nicht beendet.

**Exit** kann nur in [Verhaltens Formeln](../working-with-formulas-in-depth.md)verwendet werden.

> [!NOTE]
> Die Abmeldung wird nicht unterstützt, wenn die app in einem Webbrowser ausgeführt wird.

## <a name="syntax"></a>Syntax
**Exit**([*SignOut*])

* *SignOut* – optional. Ein boolescher Wert, der bei " *true* " den aktuellen Benutzer von powerapps signiert.  Der Standardwert ist *false* , und der Benutzer bleibt angemeldet.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | 
| --- | --- | 
| **Exit ()** | Beendet die aktuelle APP und lässt den Benutzer angemeldet.  Der Benutzer wird zur Liste der apps zurückgegeben.  |
| **Exit (&nbsp;true&nbsp;)** | Beendet die aktuelle APP, und der Benutzer wird abgemeldet.  Der Benutzer muss sich mit seinen Anmelde Informationen wieder anmelden, bevor er eine APP ausführen kann. | 


