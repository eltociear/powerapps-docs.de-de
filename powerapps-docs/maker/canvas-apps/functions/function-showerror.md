---
title: ShowError-Funktion | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die ShowError-Funktion in PowerApps
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: gregli
ms.openlocfilehash: 7c1d5a8c7b35d316a2720d564977170029e28359
ms.sourcegitcommit: a9d33322228c398d29964429602dc3fe19fa67d2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="showerror-function-in-powerapps"></a>ShowError-Funktion in PowerApps
Zeigt dem Benutzer eine Fehlermeldung an.

## <a name="description"></a>Beschreibung
Die **ShowError**-Funktion zeigt dem Benutzer eine Fehlermeldung an.  Die Meldungen werden beim Erstellen der App und beim Verwenden der App durch die Endbenutzer angezeigt.

**ShowError** kann ausschließlich in [Verhaltensformeln eingesetzt werden](../working-with-formulas-in-depth.md).

**ShowError** gibt immer *TRUE* zurück.

**ShowError** kann zusammen mit der [**IfError**](function-iferror.md)-Funktion verwendet werden. Dadurch können Fehler erkannt und mit einer benutzerdefinierten Fehlernachricht gemeldet werden.

## <a name="syntax"></a>Syntax
**ShowError** ( *Meldung* )

* *Meldung*: erforderlich.  Meldung, die dem Benutzer angezeigt wird. 

## <a name="examples"></a>Beispiele

### <a name="step-by-step"></a>Schritt für Schritt

1. Fügen Sie der Anzeige ein **Schaltflächen-Steuerelement** („Button“) hinzu.

2. Legen Sie die Eigenschaft **OnSelect** der **Schaltfläche** auf die folgende Formel fest:

    **ShowError ("Hello, World")**

3. Klicken Sie auf die Schaltfläche, oder tippen Sie darauf.  

    Hierbei wird dem Benutzer jedes Mal die Meldung **Hello, World** angezeigt.

    ![Anzeige der Schaltfläche in der Erstellungsumgebung. Durch OnSelect wird ShowError aufgerufen, wodurch die Meldung „Hello, World“ auf einem roten Banner für den Benutzer angezeigt wird.](media/function-showerror/hello-world.png)
