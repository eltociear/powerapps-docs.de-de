---
title: 'Beispiel: Berichte veröffentlichen (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel zeigt, wie Sie Berichte veröffentlichen können.
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: 0dc52a0cd6cdc45c15327b1f1b2bf9c5c1848153
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155702"
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