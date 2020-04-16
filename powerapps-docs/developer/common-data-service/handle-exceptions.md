---
title: Behandlung von Ausnahmen in einem Plug-In (Common Data Service) | Microsoft Docs
description: Verstehen Sie das Systemverhalten, wenn ein Plug-in eine Ausnahme an den Aufrufer zurückgibt.
ms.custom: ''
ms.date: 09/20/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 22593751c4eb580e978a0a561f26034f6fd6e9da
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156186"
---
# <a name="handle-exceptions-in-plug-ins"></a>Behandlung von Ausnahmen in Plug-ins

Es gibt zwei mögliche Ergebnisse, wenn ein Plug-in die Rückgabe einer Ausnahme an das D365-System ermöglicht: Informationen über die Ausnahme werden protokolliert oder dem Benutzer angezeigt, und die aktuell bearbeitete Nachrichtenanforderung wird abgebrochen. Das genaue Verhalten, wie im Folgenden beschrieben, hängt davon ab, wie das Plug-in ausgeführt wird: in der Sandbox oder nicht, synchron oder asynchron.

<a name='cancelling-an-operation'></a>

## <a name="cancelling-the-current-operation"></a>Abbrechen des laufenden Vorgangs

Ihr Code kann dazu führen, dass der aktuelle Verarbeitungsvorgang der Nachrichtenanforderung abgebrochen wird, indem eine Ausnahme ausgelöst oder eine nicht abgefangene Ausnahme an das D365-System zurückgegeben wird. Jede Ausnahme, die an den Plugin-Aufrufer zurückgegeben wird, führt dazu, dass die aktuelle Operation abgebrochen wird. Daher ist es wichtig, dass Sie die besten Coding-Verfahren anwenden, um alle ausgelösten Ausnahmen zu verwalten und zu bestimmen, ob die Ausnahme die aktuelle Operation abbrechen darf oder nicht.

Wenn Ihre Geschäftslogik vorschreibt, dass der Vorgang abgebrochen werden soll, sollten Sie eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException>-Ausnahme auslösen und eine Nachricht bereitstellen, um zu erklären, warum der Vorgang abgebrochen wurde.

Idealerweise sollten Sie nur Vorgänge mithilfe synchroner Plug-Ins abbrechen, die in der Phase **PreValidation** registriert wurden. Diese Phase erfolgt *gewöhnlich* außerhalb der Hauptdatenbanktransaktion. Das Abbrechen eines Vorgangs, bevor er die Transaktion erreicht, ist sehr erwünscht, da der abgebrochene Vorgang zurückgesetzt werden muss. Der Rollback des Vorgangs erfordert beträchtliche Ressourcen und wirkt sich auf die Systemleistung aus. Vorgänge in den Phasen **PreOperation** und **PostOperation** befinden sich immer innerhalb der Datenbanktransaktion.

Manchmal sind **PreValidation**-Phasen innerhalb einer Transaktion, wenn sie von Logik in einem anderen Vorgang initiiert sind. Wenn Sie beispielsweise einen Aufgabenentitätsdatensatz in der Phase **PreOperation** der Erstellung einer Firma erstellen, wird die Aufgabenerstellung durch die Ereignisausführungspipeline übergeben und wird innerhalb der Phase **PreValidation** erfolgen. Sie wird aber ein Bestandteil der Transaktion sein, durch den der Firmaenentitätsdatensatz erstellt wird. -Sie können feststellen, ob sich ein Vorgang innerhalb einer Transaktion befindet anhand des Werts der <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.IsInTransaction> -Eigenschaft verfügbar.

## <a name="how-the-system-handles-plug-in-exceptions"></a>Wie das System Plugin-Ausnahmen behandelt

Wenn Sie eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException>-Ausnahme innerhalb eines synchronen Plug-In auslösen, wird dem Benutzer ein Fehlerdialog mit Ihrer Nachricht angezeigt. Wenn Sie keine Meldung bereitstellen, wird dem Benutzer ein generischer Fehlerdialog angezeigt. Wenn irgendein anderer Ausnahmetyp ausgelöst wird, wird der Benutzer einen Fehlerdialog mit einer generischen Nachricht sehen, und die Ausnahmemeldung sowie Stapelüberwachung werden in die [PluginTraceLog-Entität](reference/entities/plugintracelog.md) geschrieben.

Die Ausnahmemeldung für asynchrone registrierte Plug-Ins wird einem Datensatz des Systemauftrags [AsyncOperation Entity](reference/entities/asyncoperation.md) geschrieben, der im **Systemauftragsbereich** der Webanwendung angezeigt werden kann. Dem Benutzer wird kein Dialog angezeigt. Async-Plugins nehmen nicht an der Datenbanktransaktion teil, die sie in die Warteschlange gestellt hat, daher können sie die Transaktion nicht abbrechen.

> [!NOTE]
> In der Einheitlichen Oberfläche unterstützt der Fehlerdialog weder HTML-codierten Inhalt noch Messaging.
