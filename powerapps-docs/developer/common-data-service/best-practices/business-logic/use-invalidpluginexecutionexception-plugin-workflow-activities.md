---
title: InvalidPluginExecutionExceptionException in Plugins und Workflow-Aktivitäten verwenden | MicrosoftDocs
description: Verwenden Sie InvalidPluginExecutionExceptionException, wenn Sie im Rahmen einer Plug-in- oder Workflow-Aktivität Fehler melden.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c4ccc11cf09c00a2430e736d6e8ab6f532dee8e6
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748240"
---
# <a name="use-invalidpluginexecutionexception-in-plug-ins-and-workflow-activities"></a>InvalidPluginExecutionExceptionException in Plugins und Workflow-Aktivitäten verwenden

**Kategorie**: Supportabilität, Benutzerfreundlichkeit

**Wirkungspotential**: Mittel

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Wenn ein synchrones Plug-in eine andere Ausnahme als <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> an die Plattform zurückgibt, wird dem Benutzer das Fehlerdialogfeld mit der Meldung der Ausnahme <xref:System.Exception.Message> und der Stapelverfolgung angezeigt. Dies bietet eine unfreundliche Benutzererfahrung in einer wahrscheinlich bereits frustrierenden Situation.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Wir empfehlen, dass Plugins aus folgenden Gründen nur eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> zurück zur Plattform schicken:

- Auftauchen einer freundlichen Nachricht an den Benutzer
- Vermeiden von Event Log/Trace File Blähungen

Unbehandelte Ausnahmen anderer Typen sollten nur dann auftreten, wenn zur Laufzeit unerwartete Fehler auftreten. Im Folgenden finden Sie Beispiele für gültige Ansätze.

- Ungeschützte InvalidPluginExecutionException auslösen

    ```csharp
    public void Execute(IServiceProvider serviceProvider)
    {
        // Invocation of a valid scenario that throws an appropriate exception type
        ThrowPluginException();
    }
    
    private void ThrowPluginException()
    {
        throw new InvalidPluginExecutionException("Throwing a plug-in exception in a member method body");
    }
    ```

- Geschützt Ausnahmen, die als neue InvalidPluginExecutionException behandelt oder ausgelöst werden.

    ```csharp
    public void Execute(IServiceProvider serviceProvider)
    {
        try
        {
            ThrowGuardedMemberException();
        }
        catch (CustomException ex)
        {
            throw new InvalidPluginExecutionException("Unable to save the contact. This is likely caused by..."), ex);
        }
    
        // Invocation of a valid scenario in a member method
        HandleMemberException();
    }
    
    private void HandleMemberException()
    {
        try
        {
            // Invocation of a scenario where CustomException is thrown
            ThrowGuardedMemberException();
        }
        catch (CustomException ex)
        {
            // Handle the exception.
            // Note - Debug.WriteLine is likely not the appropriate way to handle the exception. This is for demonstration purposes only
            Debug.WriteLine(ex.Message);
        }
    }
    
    private void ThrowGuardedMemberException()
    {
        throw new CustomException("Throwing a custom exception in a guarded member");
    }
    ```

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

> [!WARNING]
> Diese Muster sollten vermieden werden.

- Ungeschützte Ausnahme ausgelöst

    ```csharp
    public void Execute(IServiceProvider serviceProvider)
    {
        // Invocation of a scenario where violation occurs during an unguarded throw
        UnguardedMemberThrowException();
    }
    
    private void UnguardedMemberThrowException()
    {
        throw new CustomException("Throwing an unguarded custom exception in a member method body");
    }
    ```

- Geschützt Ausnahme ausgelöst mit ungeschützer Neuauslösung

    ```csharp
    public void Execute(IServiceProvider serviceProvider)
    {
        // Invocation of a scenario where violation occurs during an unguarded rethrow
        UnguardedMemberRethrowException();
    }
    
    private void UnguardedMemberRethrowException()
    {
        try
        {
            // Guarded invoking of a method member that throws a custom exception
            GuardedMemberThrowException();
        }
        catch (CustomException ex)
        {
            // Handle and rethrow
            Debug.WriteLine(ex.Message);
    
            // This is where the issue occurs
            throw;
        }
    }
    
    private void GuardedMemberThrowException()
    {
        throw new CustomException("Throwing a guarded custom exception in a member method body");
    }
    ```

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Abbrechen eines Vorgangs](../../handle-exceptions.md#cancelling-an-operation)<br/>
[Workflowaktivitäten debuggen](../../workflow/workflow-extensions.md#debug-workflow-activities)<br/>