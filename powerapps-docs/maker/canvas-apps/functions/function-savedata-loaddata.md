---
title: Funktionen „SaveData“ und „LoadData“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax für die Funktionen "SaveData" und "LoadData" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/31/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8ad9eee5230d46e67f3a0c5370fd0960e0c6787b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730269"
---
# <a name="savedata-and-loaddata-functions-in-power-apps"></a>Funktionen "SaveData" und "LoadData" in powerapps
Speichert eine [Sammlung](../working-with-data-sources.md#collections) und lädt diese erneut.

## <a name="description"></a>Beschreibung
Die Funktion **SaveData** speichert eine Sammlung für die spätere Verwendung unter einem Namen.  

Die Funktion **LoadData** lädt eine Sammlung über den Namen, über den diese zuvor mit **SaveData** gespeichert wurde, erneut. Sie können diese Funktion nicht dazu verwenden, eine Sammlung aus einer anderen Quelle zu laden.  

Verwenden Sie diese Funktionen, um die Leistung beim APP-Start zu verbessern, indem Sie Daten in der **[app. OnStart](../controls/control-screen.md#additional-properties)** -Formel bei einer ersten Ausführung zwischenspeichern und dann bei nachfolgenden Ausführungen den lokalen Cache erneut laden. Sie können diese Funktionen auch verwenden, um Ihrer APP [einfache Offline Funktionen](../offline-apps.md) hinzuzufügen.

Diese Funktionen können nicht in einem Browser verwendet werden, wenn Sie die app in powerapps Studio erstellen oder wenn Sie die APP im Web Player ausführen. Um Ihre APP zu testen, führen Sie Sie in powerapps Mobile auf einem iPhone-oder Android-Gerät aus.

Diese Funktionen sind durch die Menge des verfügbaren APP-Speichers beschränkt, da Sie für eine Auflistung im Arbeitsspeicher ausgeführt werden. Der verfügbare Arbeitsspeicher kann je nach Gerät und Betriebssystem, dem vom Power apps-Player verwendeten Arbeitsspeicher und der Komplexität der app in Bezug auf Bildschirme und Steuerelemente variieren. Wenn Sie mehr als ein paar Megabyte Daten speichern, testen Sie Ihre APP mit den erwarteten Szenarien auf den Geräten, auf denen die app ausgeführt werden soll. Sie sollten im Allgemeinen zwischen 30 und 70 Megabyte verfügbarem Arbeitsspeicher erwarten.  

**LoadData** erstellt die Sammlung nicht; die Funktion füllt nur eine vorhandene Sammlung aus. Zunächst müssen Sie die Sammlung mit den richtigen [Spalten](../working-with-tables.md#columns) erstellen, indem Sie **[Collect](function-clear-collect-clearcollect.md)** verwenden. Die geladenen Daten werden an die Sammlung angefügt. Verwenden Sie zuerst die **[Clear](function-clear-collect-clearcollect.md)** -Funktion, wenn Sie mit einer leeren Auflistung beginnen möchten.

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

