---
title: 'Beispiel: Berichte veröffentlichen (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel zeigt, wie Sie Berichte veröffentlichen können.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: dbf928c13e80ed0f95e1b0c84b4e51452d6f8607
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956318"
---
# <a name="publish-reports"></a>Veröffentlichen von Berichten

Dieses Beispiel zeigt, wie man einen Bericht veröffentlicht, indem man einen **Bericht** Datensatz und die Bezugsdatensätze erstellt, die ihn sichtbar machen. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/PublishReport) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das oben beschriebene Beispiel zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `Report`-Methode instanziiert das Berichtsobjekt.
2. Die `ReportCategory`-Methode legt die Berichtskategorie fest, zu der der Bericht gehören soll.
3. Die `ReportEntity`-Methode definiert, welche Entität dieser Bericht verwendet.
4. Die `ReportVisibility`-Methode legt die Sichtbarkeit des Berichts fest.

### <a name="clean-up"></a>Bereinigung

Für diese Beispiel ist keine Bereinigung erforderlich.