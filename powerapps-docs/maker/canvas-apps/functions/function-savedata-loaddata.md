---
title: Funktionen „SaveData“ und „LoadData“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax für die Funktionen SaveData und LoadData in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/31/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3fb23fec6f6885a55b054889b90fed0c5efafd5e
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61520488"
---
# <a name="savedata-and-loaddata-functions-in-powerapps"></a>Funktionen SaveData und LoadData in PowerApps
Speichert eine [Sammlung](../working-with-data-sources.md#collections) und lädt diese erneut.

## <a name="description"></a>Beschreibung
Die Funktion **SaveData** speichert eine Sammlung für die spätere Verwendung unter einem Namen.  

Die Funktion **LoadData** lädt eine Sammlung über den Namen, über den diese zuvor mit **SaveData** gespeichert wurde, erneut. Sie können diese Funktion nicht dazu verwenden, eine Sammlung aus einer anderen Quelle zu laden.  

Mit diesen Funktionen können beim Start der app-Leistung verbessern, indem das Zwischenspeichern von Daten in die **[App.OnStart](../controls/control-screen.md#additional-properties)** Formel auf die Willkommensseite, und klicken Sie dann den lokalen Cache bei nachfolgenden Ausführungen erneut laden. Sie können diese Funktionen auch verwenden, um hinzuzufügen [einfache Offlinefunktionen](../offline-apps.md) zu Ihrer app.

Sie können nicht diese Funktionen in einem Browser, wenn die app in PowerApps Studio erstellen oder beim Ausführen der app in der webplayer verwenden. Um Ihre app zu testen, führen Sie es in PowerApps Mobile auf einem iPhone oder Android-Gerät aus.

Diese Funktionen werden durch die Größe des verfügbaren app-Speichers begrenzt, da sie in einer in-Memory-Sammlung ausgeführt werden. Verfügbare Arbeitsspeicher kann variieren, je nach Gerät und Betriebssystem, Arbeitsspeicher, den den PowerApps-Player verwendet und die Komplexität der app im Hinblick auf Bildschirme und Steuerelemente. Wenn Sie länger als einige Megabyte an Daten speichern, testen Sie Ihre app mit erwarteten Szenarien auf den Geräten, die auf denen Sie die Ausführung die Anwendung erwarten. Sie erwarten, in der Regel zwischen 30 und 70 MB an verfügbarem Arbeitsspeicher haben.  

**LoadData** erstellt die Sammlung nicht; die Funktion füllt nur eine vorhandene Sammlung aus. Zunächst müssen Sie die Sammlung mit den richtigen [Spalten](../working-with-tables.md#columns) erstellen, indem Sie **[Collect](function-clear-collect-clearcollect.md)** verwenden. Die geladenen Daten werden an die Auflistung angefügt werden; Verwenden Sie die **[löschen](function-clear-collect-clearcollect.md)** zuerst ausgeführt werden, wenn Sie mit einer leeren Auflistung starten möchten.

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

