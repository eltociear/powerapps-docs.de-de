---
title: 'Beispiel: Erstellen einer E-Mail mit einer Vorlage (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie ein E-Mail-Datensatz instanziiert wird.
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
ms.openlocfilehash: 17074439d81c60b4d51a6f5e91dc5465f8ee5327
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748379"
---
# <a name="sample-create-an-email-using-a-template"></a>Beispiel: Erstellen einer E-Mail mithilfe einer Vorlage

Dieses Beispiel zeigt, wie ein E-Mail-Datensatz unter Verwendung der [InstantiateTemplateRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.instantiatetemplaterequest?view=dynamics-general-ce-9)-Nachricht instanziiert werden kann. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/EmailTemplate) herunterladen. 

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `InstantiateTemplateRequest`-Nachricht ist für die Verwendung in einem Szenario vorgesehen, in dem sie einen E-Mail-Datensatzinstanziiert.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Erstellt einen Firmendatensatz. 
2. Definiert den Text und den Betreff der E-Mail-Vorlage im **XML**-Format.
3. Erstellt eine E-Mail-Vorlage.

### <a name="demonstrate"></a>Demonstrieren

1. Die `InstantiateTemplateRequest` Nachricht wird verwendet, um eine E-Mail-Nachricht mithilfe einer Vorlage zu erstellen. 
2. Serialisieren Sie die E-Mail-Nachricht an **XML** und speichern Sie in einer Datei.


### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um den Datensatz zu löschen, der in [Einrichtung](#setup)erstellt wurde.
    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
