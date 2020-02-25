---
title: 'Beispiel: Arbeiten mit Optionssätzen (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel zeigt, wie man mit einem globalen Optionssatz arbeitet
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
ms.openlocfilehash: d9319235820f973a760784c140e445f0835b0356
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956316"
---
# <a name="work-with-option-sets"></a>Arbeit mit Optionssätzen

Dieses Beispiel zeigt, wie man mit Optionssätzen arbeitet. Normalerweise können Sie mithilfe von globalen Optionssätzen Felder festzulegen, sodass andere Felder denselben Satz von Optionen nutzen können, die an einem Ort verwaltet werden. Anders als lokale Optionssätze, die nur für ein bestimmtes Attribut definiert werden, können Sie Globale Optionssätze wiederverwenden. Sie können auch in Anforderungsparametern auf eine ähnliche Weise wie eine Enumeration verwendet werden.

Wenn Sie ein globales Optionsset mit [CreateOptionSetRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createoptionsetrequest?view=dynamics-general-ce-9) definieren, empfehlen wir, dass Sie das System einen Wert zuweisen lassen. Sie tun dies, indem Sie beim Erstellen der neuen `OptionMetadata`-Instanz einen Nullwert übergeben. Wenn Sie eine Option definieren, enthält sie ein für den Kontext des Herausgebers spezifisches Optionswertpräfix, festgelegt für die Lösung, in der der Optionssatz erstellt wird. Dieses Präfix hilft, die Möglichkeit der Erstellung von doppelten Optionssätzen für eine verwaltete Lösung zu verringern, sowie in allen Optionssätzen, die in Organisationen definiert werden, in denen die verwaltete Lösung installiert ist. Weitere Informationen finden Sie unter [Zusammenführung von Optionssatz-Optionen](https://docs.microsoft.com/powerapps/developer/common-data-service/understand-managed-solutions-merged#merge-option-set-options).

Verwenden Sie die folgenden Nachrichtenanforderungsklassen, um mit globalen Optionssätzen zu arbeiten:

- [CreateOptionSetRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createoptionsetrequest?view=dynamics-general-ce-9)
- [DeleteOptionSetRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.deleteoptionsetrequest?view=dynamics-general-ce-9)
- [RetrieveAllOptionSetsRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrievealloptionsetsrequest?view=dynamics-general-ce-9)
- [RetrieveOptionSetRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieveoptionsetrequest?view=dynamics-general-ce-9)
- [UpdateOptionSetRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.updateoptionsetrequest?view=dynamics-general-ce-9)

Verwenden Sie die folgenden Nachrichtenanforderungsklassen sowohl mit globalen als auch mit lokalen Optionssätzen:

- [DeleteOptionValueRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.deleteoptionvaluerequest?view=dynamics-general-ce-9)
- [InsertOptionValueRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.insertoptionvaluerequest?view=dynamics-general-ce-9)
- [InsertStatusValueRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.insertstatusvaluerequest?view=dynamics-general-ce-9)
- [OrderOptionRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.orderoptionrequest?view=dynamics-general-ce-9)
- [UpdateOptionValueRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.updateoptionvaluerequest?view=dynamics-general-ce-9)
- [UpdateStateValueRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.updatestatevaluerequest?view=dynamics-general-ce-9)

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkWithOptionSets) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `CreateOptionSetRequest`-, `DeleteOptionSetRequest`-, `RetrieveOptionSetRequest`- und `UpdateOptionSetRequest`-Nachrichten sollen in einem Szenario verwendet werden, in dem sie die Daten enthalten, die für die Arbeit mit Optionssätzen erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `CreateOptionSetRequest`-Methode erstellt einen globalen Optionssatz. Sie müssen den Parameter `IsGlobal=true` einstellen.  
2. Die `CreateAttributeRequest`-Methode erstellt eine Auswahlliste, die mit dem Optionssatz verknüpft ist.
3. Die `UpdateOptionSetRequest`-Methode aktualisiert die grundlegenden Informationen eines Optionssatzes.
4. Die `PublishXmlRequest`-Methode veröffentlicht den Optionssatz.
5. Die `InsertOptionValueRequest`-Methode fügt eine neue Option in einen globalen Optionssatz ein.
6. Die `RetrieveOptionSetRequest`-Methode ruft die durch ihren Namen festgelegte globale Option ab.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
