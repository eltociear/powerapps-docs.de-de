---
title: " Festlegen und Abrufen von Entitätsbildern (Common Data Service) | Microsoft Docs"
description: Dieses Beispiel zeigt, wie Daten für Entitätsbilder eingerichtet und abgerufen werden.
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 79a2b18db60afa9f487f4313116c9600c72a13c0
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155574"
---
# <a name="set-and-retrieve-entity-images"></a>Festlegen und Abrufen von Entitätsbildern

Dieses Beispiel zeigt, wie Daten für Entitätsbilder eingerichtet und abgerufen werden. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SetRetrieveImages) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Dieses Beispiel zeigt, wie eine Verbindungsrolle erstellt wird, die für Firmen und Kontakte verwendet werden kann.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

Prüft die aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Nutzen Sie die CreateImageAttributeDemoEntity Methode, um eine benutzerdefinierten Entität mit den Schemanamen `sample_ImageAttributeDemo` und eines primären Attributs mit dem Schemanamen`sample_Name` zu erstellen.
2. Erstellen eines Bildattributs mit dem Schemanamen `EntityImage`. Alle Bildattribute verwenden diesen Namen.

3. Rufen Sie das Hauptformular für die `sample_ImageAttributeDemo` Entität ab, und legen Sie das `showImage` auf true,  damit das Bild in dem Formular angezeigt wird.

4. Veröffentlichen der `sample_ImageAttributeDemo`-Entität.

5. Erstellt fünf neue Datensätze für die `sample_ImageAttributeDemo` Entität mihilfe von fünf unterschiedlich großen Bilder, die sich im Bildordner befinden wie hier abgebildet. Nachdem jeder Datensatz erstellt ist, haben Sie die Chance, den Datensatz im Webbroser mithilfe der `ShowEntityFormInBrowser` Methode anzuzeigen, damit Sie sehen können, wie die Größe der Quellbilder an den verfügbaren Platz im Formular angepasst wird.
6. Ruft die Datensätze mit dem `entityimage`-Attribut ab und speichert die Dateien mit der veränderten Größe. Nachdem Sie sich das Beispiel ausgeführt haben, können Sie die Dateien im `\bin\Debug`-Ordner finden.
7. Ruft die Datensätze mit dem Attribut `entityimage_url` ab und zeigt die Werte der relativen URL an, die in der Anwendung eingeschlossen werden können, um auf die Bilder zuzugreifen. Diese Abfrage sollte besser reagieren, da die Menge der übertragenen Daten geringer ist.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze in [Einrichtung](#setup) zu löschen. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
