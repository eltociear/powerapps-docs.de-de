---
title: InvalidPluginExecutionExceptionException in Plugins und Workflow-Aktivitäten verwenden | MicrosoftDocs
description: Verwenden Sie InvalidPluginExecutionExceptionException, wenn Sie im Rahmen einer Plug-in- oder Workflow-Aktivität Fehler melden.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 3/5/2020
ms.author: JimDaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0657e9b39713f4f11d68daac1c60fa144dc6ab08
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109139"
---
# <a name="use-invalidpluginexecutionexception-in-plug-ins-and-workflow-activities"></a>InvalidPluginExecutionExceptionException in Plugins und Workflow-Aktivitäten verwenden

**Kategorie**: Supportabilität, Benutzerfreundlichkeit

**Wirkungspotential**: Mittel

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Wenn ein synchrones Plug-in eine andere Ausnahme als <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> an die Plattform zurückgibt, wird dem Benutzer in einem Power Apps Client das Fehlerdialogfeld mit der Meldung der Ausnahme <xref:System.Exception.Message> und der Stapelverfolgung angezeigt. Dies bietet eine unfreundliche Benutzererfahrung in einer wahrscheinlich bereits frustrierenden Situation.

Wenn Sie <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> verwenden, um den Vorgang absichtlich aufgrund eines Problems mit der Datenvalidierungslogik abzubrechen, sollten Sie dem Anwendungsbenutzer eine Anleitung geben, damit er das Problem beheben und fortfahren kann.

Wenn der Fehler unerwartet ist, wird dennoch empfohlen, den Fehler abzufangen und in einen <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> zu konvertieren, damit Anwendungen eine benutzerfreundliche Fehlermeldung mit Anleitungen anzeigen können, damit ein Benutzer oder technisches Personal das Problem schnell erkennen kann.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Plug-Ins sollten nur eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> zurückgeben, und zwar aus den folgenden Gründen:

- Zeigt dem Benutzer ein nützliches Meldungsfeld an
- Vermeiden von Event Log/Trace File Blähungen

Fehler beim Konvertieren der Nachricht in eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> führt zu einem `IsvUnExpected` Fehler ohne Meldung des Benutzers von einem Power Apps Client.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

> [!WARNING]
> Diese Muster sollten vermieden werden.

Verwenden Sie kein HTML in der Fehlermeldung. 

Webanwendungen, die auf CDS-Daten zugreifen, sollten den Text einer Fehlermeldung in HTML codieren, bevor sie einem Benutzer angezeigt werden. Dadurch wird verhindert, dass der HTML-Code in Ihrer Nachricht wie beabsichtigt gerendert wird. Es wird nur der HTML-Code angezeigt.


<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Abbrechen eines Vorgangs](../../handle-exceptions.md#cancelling-an-operation)<br/>
[Workflowaktivitäten debuggen](../../workflow/workflow-extensions.md#debug-workflow-activities)<br/>