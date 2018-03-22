---
title: Funktionen „SaveData“ und „LoadData“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax für die Funktionen SaveData und LoadData in PowerApps
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
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: aa62882841ee4d585720a2241dff8b9f35c88059
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="savedata-and-loaddata-functions-in-powerapps"></a>Funktionen SaveData und LoadData in PowerApps
Speichert eine [Sammlung](../working-with-data-sources.md#collections) und lädt diese erneut.

## <a name="description"></a>Beschreibung
Die Funktion **SaveData** speichert eine Sammlung für die spätere Verwendung unter einem Namen.  

Die Funktion **LoadData** lädt eine Sammlung über den Namen, über den diese zuvor mit **SaveData** gespeichert wurde, erneut. Sie können diese Funktion nicht dazu verwenden, eine Sammlung aus einer anderen Quelle zu laden.  

**LoadData** erstellt die Sammlung nicht; die Funktion füllt nur eine vorhandene Sammlung aus. Zunächst müssen Sie die Sammlung mit den richtigen [Spalten](../working-with-tables.md#columns) erstellen, indem Sie **[Collect](function-clear-collect-clearcollect.md)** verwenden.

Speicher wird verschlüsselt und befindet sich an einem privaten Speicherort auf dem lokalen Gerät, isoliert von anderen Benutzern und anderen Apps.  

## <a name="syntax"></a>Syntax
**SaveData**( *Sammlung*, *Name* )<br>**LoadData**( *Sammlung*, *Name* [, *NichtVorhandeneDateiIgnorieren* ])

* *Sammlung*: Erforderlich.  Die zu speichernde oder zu ladende Sammlung.
* *Name*: Erforderlich.  Der Name des Speichers. Sie müssen den gleichen Namen verwenden und den gleichen Satz von Daten laden. Der Namespace wird nicht für andere Apps oder Benutzer freigegeben.
* *NichtVorhandeneDateiIgnorieren*: optional. Boolescher Wert (**WAHR**/**FALSCH**), der angibt, ob die Funktion **LoadData** Fehler anzeigen oder ignorieren soll, wenn keine passende Datei gefunden werden kann. Wenn Sie **FALSCH** angeben, werden Fehler angezeigt. Wenn Sie **WAHR** angeben, werden Fehler ignoriert, was in Offlineszenarien nützlich ist. **SaveData** erstellt möglicherweise eine Datei, wenn das Gerät offline betrieben wird (also der Status von **Connection.Connected** **FALSCH** ist).

## <a name="examples"></a>Beispiele
| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **If(Connection.Connected, ClearCollect(LocalTweets, Twitter.SearchTweet("PowerApps", {maxResults: 100})),LoadData(LocalTweets, "Tweets", true))** |Wenn das Gerät verbunden ist, laden Sie die LocalTweets-Sammlung vom Twitter-Dienst; laden Sie andernfalls die Sammlung aus dem lokalen Dateicache. |Der Inhalt wird wiedergegeben, gleich, ob das Gerät online oder offline ist. |
| **SaveData(LocalTweets, "Tweets")** |Speichern Sie die LocalTweets-Sammlung als lokalen Dateicache auf dem Gerät. |Die Daten werden lokal gespeichert, sodass **LoadData** sie in eine Sammlung laden kann. |

