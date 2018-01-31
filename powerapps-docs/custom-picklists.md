---
title: Erstellen benutzerdefinierter Auswahllisten | Microsoft-Dokumentation
description: Erstellen Sie eine benutzerdefinierte Auswahlliste.
services: powerapps
documentationcenter: na
author: pvillads
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/09/2017
ms.author: kfend
ms.openlocfilehash: cfa00b804df884ff9c5f1b4a96e0e8b4dc2088ba
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="create-custom-picklists"></a>Benutzerdefinierte Auswahllisten erstellen
Es ist nun möglich, zusätzlich zu den sofort verfügbaren Auswahllisten eigene Auswahllisten zu erstellen. Auswahllisten, bei denen es sich im Prinzip um eine benannte Liste von Elementen mit Name und Beschreibungen handelt, sind ein einfaches Konzept. Wenn die Auswahllistenfelder gerendert werden, wird ein Dropdownmenü mit den Anzeigenamen der Elemente angezeigt. 

Auswahllisten werden im Menü **Entitäten** auf der Registerkarte **Common Data Service** über das Menüelement **Auswahllisten** hinzugefügt. Klicken Sie auf das Menü, um alle Auswahllisten anzuzeigen, die derzeit in Ihrer Umgebung definiert sind. Einige häufig verwendete Auswahllisten sind bereits für Sie definiert und können problemlos anhand ihres Typs **Standard** identifiziert werden. Die Auswahllisten, die Sie selbst erstellen, sind vom Typ **Benutzerdefiniert**.

1. Klicken Sie zum Erstellen einer neuen Auswahlliste am oberen Rand der Seite auf **Neue Auswahlliste**. Definieren Sie die Auswahlliste auf der Seite, die geöffnet wird, indem Sie den Namen, Anzeigenamen und eine Beschreibung eingeben.
   > [!IMPORTANT]
> Der Name der Auswahlliste kann nach dem Erstellen nicht mehr geändert werden. Es gibt einige Anforderungen an den Namen der Auswahlliste. Der Name muss einfach sein und darf keine Sonderzeichen enthalten. Darüber hinaus können Sie einen bestimmten Namen nur für eine Auswahlliste verwenden. Wenn Sie versuchen, eine weitere Auswahlliste mit demselben Namen zu erstellen, erhalten Sie einen Fehler. Diese Einschränkungen gelten nicht für die **Anzeigenamen**.
   
    In diesem Thema erstellen wir eine Auswahlliste, die verwendet werden kann, um einen Transportmodus auszuwählen.
2. Nennen Sie die Auswahlliste **Transport**, und fügen Sie die Informationen für die erforderlichen Felder hinzu.
3. Klicken Sie auf **Weiter**, und geben Sie auf der nächsten Seite die verschiedenen Elemente der Auswahlliste an, in diesem Beispiel die Transportanbieter. Wenn die Seite geöffnet wird, sehen Sie, dass bereits ein einzelnes Element erstellt wurde. Aktualisieren Sie das Zeilenelement mit Informationen, die Sie für die Auswahlliste benötigen, die Sie erstellen. Die Bearbeitung erfolgt in der Zeile. Es gibt nicht für jedes Auswahllistenelement eine separate Seite. Klicken Sie in das Feld **NewItem**, um das erste Element hinzuzufügen. Klicken Sie jedes Mal, wenn Sie ein neues Auswahllistenelement benötigen, am oberen rechten Rand des Bildschirms auf **Element hinzufügen**, um eine neue Zeile hinzuzufügen. 

Sie können ein Element löschen, indem Sie ganz rechts in jeder Elementzeile auf das Papierkorb-Symbol klicken. Wenn alle erforderlichen Elemente hinzugefügt wurden, klicken Sie auf **Erstellen**, um die Liste zu erstellen und Sie an den Server zu senden. Sie können sehen, dass die Auswahlliste zur Liste der vorhandenen Auswahllisten hinzugefügt wurde.

Sie können die Auswahlliste nun verwenden, um Felder auf Ihren Entitäten zu definieren, indem Sie einen Feldtyp **Auswahlliste** hinzufügen und dann den **Anzeigenamen** im Bereich **Eigenschaften** für das Feld verwenden. 

