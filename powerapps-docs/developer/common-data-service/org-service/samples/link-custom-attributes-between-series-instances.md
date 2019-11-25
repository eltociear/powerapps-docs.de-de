---
title: 'Beispiel: Verknüpfen von benutzerdefinierten Attributen zwischen Reihen und Instanzen (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie benutzerdefinierte Attributen zwischen Reihen und Instanzen verknüpft werden.
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
ms.openlocfilehash: fc884a2e4ee1118cef35bdfa4838f4343f061d84
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748741"
---
# <a name="sample-link-custom-attributes-between-series-and-instances"></a>Beispiel: Verknüpfen von benutzerdefinierten Attributen zwischen Reihen und Instanzen

Dieses Beispiel zeigt, wie ein benutzerdefiniertes Attribut, das für eine Terminserie (`RecurringAppointmentMaster`) erstellt wird, mit einem benutzerdefiniertes Attribut, das für die Termininstanzen (`Appointment`) erstellt wird, verknüpft wird. Sie können das Beispiel herunterladen von[hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/LinkAttributes)

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `CreateAttributeRequest`-Message ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie Daten enthält, um benutzerdefinierte Attribute zu erstellen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `StringAttributeMetadata` Message erstellt benutzerdefinierte Zeichenfolgenattributen für Serientermininstanz und Termininstanz.
2. Die `LinkedAttributeId` verknüpft das benutzerdefinierte Attribut mit dem benutzerdefinierten Attributs des Termins.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um Datensätze zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
