---
title: 'Tutorial: Aktualisieren eines Plug-Ins (Common Data Service) | Microsoft-Dokumentation'
description: 'Dieses Lernprogramm ist das dritte in der Serie, in der Ihnen gezeigt wird, wie Sie mit Plug-Ins arbeiten. '
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f00c30c25c1038edbd444bfdfffc5b6597f67f42
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155234"
---
# <a name="tutorial-update-a-plug-in"></a>Lernprogramm: Aktualisieren eines Plug-Ins

Dieses Lernprogramm ist das dritte in der Serie, in der Ihnen gezeigt wird, wie Sie mit Plug-Ins arbeiten. 

- [Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md)
- [Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md)
- Lernprogramm: Aktualisieren eines Plug-Ins (Dieses Lernprogramm)

Eine detaillierte Erläuterung der unterstützenden Konzepte und technischen Details finden Sie unter:

- [Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen](plug-ins.md)
- [Schreiben eines Plug-Ins](write-plug-in.md)
- [Registrieren eines Plug-Ins](register-plug-in.md)
- [Debuggen von Plug-Ins](debug-plug-in.md)

## <a name="goal"></a>Ziel

In diesem Lernprogramm werden zusätzliche allgemeinen Optionen beschrieben, die Sie mit Plug-Ins ausführen können. In diesem Lernprogramm werden Sie:

 - Eine Plug-In-Assembly aktualisieren.
 - Ein synchrones Plug-In erstellen und registrieren
 - Konfigurationsdaten im Plug-In verwenden
 - Einen Fehler auslösen, der dem Benutzer angezeigt wird
 - Ein Vor-Entitätsbild in Ihrem Code konfigurieren und verwenden
 - Die Registrierung einer Assembly, eines Plug-Ins oder Schritts aufheben


Ziel des Lernprogramms ist:

- Erstellen Sie ein synchrones Plug-In, das in der Vorüberprüfungsphase der Updatenachricht der Firmenentität registriert ist. 
- Das Plug-In wertet einen Satz von Zeichenfolgewerten aus, der mithilfe der Konfigurationsdaten festgelegt wurde, als das Plug-In registriert wurde. 
- Wenn der Name der Firma zu einem dieser Werte geändert wurde und der vorherige Wert den neuen Namen nicht enthielt, brechen Sie den Vorgang ab und senden Sie eine Fehlermeldung an den Benutzer.


## <a name="prerequisites"></a>Voraussetzungen

- Schließen Sie [Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md) ab
- [Lernprogramm: Debuggen eines Plug-In](tutorial-debug-plug-in.md) wird empfohlen, ist aber nicht erforderlich.

> [!NOTE]
> Da viele grundlegender Schritte in [Lernprogramm: Schreiben und Sie ein Plug-In registrieren](tutorial-write-plug-in.md) detailliert beschrieben wurden, werden dieselben Schritte in diesem Lernprogramm nicht so ausführlich behandelt.

## <a name="create-a-new-plug-in-class"></a>Erstellen einer neuen Plug-In-Klasse

1. Fügen Sie in Visual Studio dem **BasicPlugin**-Projekt eine neue Klasse namens `ValidateAccountName.cs` hinzu.
1. Fügen Sie der Klasse den folgenden Code hinzu und erstellen Sie die Assembly neu.


```csharp
using Microsoft.Xrm.Sdk;
using System;
using System.Collections.Generic;
using System.Linq;

namespace BasicPlugin
{
  public class ValidateAccountName : IPlugin
  {
    //Invalid names from unsecure configuration
    private List<string> invalidNames = new List<string>();

    // Constructor to capture the unsecure configuration
    public ValidateAccountName(string unsecure)
    {
      // Parse the configuration data and set invalidNames
      if (!string.IsNullOrWhiteSpace(unsecure))
        unsecure.Split(',').ToList().ForEach(s =>
        {
          invalidNames.Add(s.Trim());
        });
    }
    public void Execute(IServiceProvider serviceProvider)
    {

      // Obtain the tracing service
      ITracingService tracingService =
      (ITracingService)serviceProvider.GetService(typeof(ITracingService));
      try
      {

        // Obtain the execution context from the service provider.  
        IPluginExecutionContext context = (IPluginExecutionContext)
            serviceProvider.GetService(typeof(IPluginExecutionContext));

        // Verify all the requirements for the step registration
        if (context.InputParameters.Contains("Target") && //Is a message with Target
            context.InputParameters["Target"] is Entity && //Target is an entity
            ((Entity)context.InputParameters["Target"]).LogicalName.Equals("account") && //Target is an account
            ((Entity)context.InputParameters["Target"])["name"] != null && //account name is passed
            context.MessageName.Equals("Update") && //Message is Update
            context.PreEntityImages["a"] != null && //PreEntityImage with alias 'a' included with step
            context.PreEntityImages["a"]["name"] != null) //account name included with PreEntityImage with step
        {
          // Obtain the target entity from the input parameters.  
          var entity = (Entity)context.InputParameters["Target"];
          var newAccountName = (string)entity["name"];
          var oldAccountName = (string)context.PreEntityImages["a"]["name"];

          if (invalidNames.Count > 0)
          {
            tracingService.Trace("ValidateAccountName: Testing for {0} invalid names:", invalidNames.Count);

            if (invalidNames.Contains(newAccountName.ToLower().Trim()))
            {
              tracingService.Trace("ValidateAccountName: new name '{0}' found in invalid names.", newAccountName);

              // Test whether the old name contained the new name
              if (!oldAccountName.ToLower().Contains(newAccountName.ToLower().Trim()))
              {
                tracingService.Trace("ValidateAccountName: new name '{0}' not found in '{1}'.", newAccountName, oldAccountName);

                string message = string.Format("You can't change the name of this account from '{0}' to '{1}'.", oldAccountName, newAccountName);

                throw new InvalidPluginExecutionException(message);
              }

              tracingService.Trace("ValidateAccountName: new name '{0}' found in old name '{1}'.", newAccountName, oldAccountName);
            }

            tracingService.Trace("ValidateAccountName: new name '{0}' not found in invalidNames.", newAccountName);
          }
          else
          {
            tracingService.Trace("ValidateAccountName: No invalid names passed in configuration.");
          }
        }
        else
        {
          tracingService.Trace("ValidateAccountName: The step for this plug-in is not configured correctly.");
        }
      }
      catch (Exception ex)
      {
        tracingService.Trace("BasicPlugin: {0}", ex.ToString());
        throw;
      }
    }
  }
}
```

### <a name="about-the-code"></a>Infos zum Code
- Diese Klasse umfasst einen Konstruktor, um die unsichere Konfiguration zu erfassen, die festgelegt wird, wenn ein Schritt konfiguriert wird.
- Diese Klasse benötigt bestimmte Schrittkonfiguration, um ordnungsgemäß zu funktionieren:
    - Update-Nachricht
    - Bei der Firmenentität
    - Beim Firmenname, der in den Attributen enthalten ist
    - Bei PreEntityImage bei Verwendung des bestimmten Alias "a"
    - Bei PreEntityImage, einschließlich des Namensattributs.
- Wenn die Schrittkonfiguration nicht zutrifft, schreibt das Plug-In nur in die Ablaufverfolgung, dass sie nicht ordnungsgemäß konfiguriert wurde.
- Wenn keine ungültigen Namen in der Konfiguration festgelegt wurden, schreibt das Plug-In nur in die Ablaufverfolgung, dass keine ungültigen Namen an die Konfiguration übergeben wurden
- Wenn der neue Name einem der ungültigen Namen entspricht, die mit der Konfiguration festgelegt wurden UND der Originalname den neuen Namen nicht enthält, wird eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> ausgelöst und dem Benutzer wird die Meldung ausgegeben, dass der Vorgang nicht zulässig ist.

## <a name="update-the-plug-in-assembly-registration"></a>Plug-In-Assembly-Registrierung aktualisieren

Die vorhandene Assembly aus [Lernprogramm: Schreiben und Registrieren eines Plug-Ins](tutorial-write-plug-in.md) sollte bereits registriert sein. Um das neue **ValidateAccountName**-Plug-In hinzuzufügen, ohne die Registrierung der vorhandene Assembly aufzuheben, müssen Sie es aktualisieren.

1. Wählen Sie das **(Assembly) Basis-Plug-In** aus und wählen Sie **Aktualisieren** aus.

    ![Wählen Sie Aktualisieren aus.](media/tutorial-update-plug-in-update.png)

1. Im Dialog **Update-Assembly: Grundlegendes Plug-In** geben Sie den Speicherort der Assemblys an, indem Sie auf die Auslassungspunkte (**…**) klicken, und die Assembly wird geladen.

    ![Dialog "Update-Assembly: Grundlegendes Plug-In"](media/tutorial-update-plug-in-update-assembly.png)

1. Überprüfen, dass die Assembly und beide Plug-Ins ausgewählt sind, und klicken Sie auf **Ausgewählte Plug-Ins aktualisieren**.

## <a name="configure-a-new-step"></a>Einen neuen Schritt konfigurieren

Konfigurieren Sie das **ValidateAccountName**-Plug-In mithilfe dieser Einstellungen:

|Einstellung|Value|
|--|--|
|Meldung|Update|
|Primäre Entität|account|
|Filterattribute|Name|
|Ereignis-Pipeline-Phase der Ausführung|PreValidation|
|Ausführungsmodus|Synchron|
|Unsichere Konfiguration|test,<br />foo,<br />bar|

![Neuen Schritt registrieren](media/tutorial-update-plug-in-register-new-step.png)

## <a name="add-an-image"></a>Hinzufügen eines Bilds

1. Klicken Sie mit der rechten Maustaste auf den Schritt, den Sie soeben registriert haben, und wählen Sie **Neues Bild registrieren** aus.

    ![Neues Bild registrieren](media/tutorial-update-plug-in-register-new-image.png)

1. Konfigurieren Sie im das Bild mit diesen Einstellungen **Neues Bild registrieren**-Dialogfeld:

    |Einstellung|Value|
    |--|--|
    |Bildtyp|Vorbild|
    |Name|account|
    |Alias der Entität|a|
    |Parameter|Name|

    ![Neues Bild-Dialog registrieren](media/tutorial-update-plug-in-register-new-image-dialog.png)

1. Wenn das Bild registriert ist, wird es im Plug-In-Registrierungstool angezeigt.

    ![Das Registrierungsbild](media/tutorial-update-plug-in-image-added.png)

## <a name="test-the-plug-in"></a>Plug-In testen

1. Öffnen Sie die Anwendung und versuchen Sie, einen vorhandenen Firmennamen zu `test`, `foo`oder `bar` zu aktualisieren.
1. Wenn Sie versuchen, zu speichern, sollte die folgende Fehlermeldung angezeigt werden:

    ![Fehlermeldung](media/tutorial-update-plug-in-error-message.png)

1. Wenn Sie eine vorhandene Firma mit einem Namen aktualisiert, der `test`, `foo` oder `bar` enthält, dann die Firma auf `test`, `foo` oder `bar` aktualisieren, sollten keine Nachricht angezeigt werden.

## <a name="unregister-assembly-plug-in-and-step"></a>Die Registrierung einer Assembly, eines Plug-Ins und eines Schritts aufheben

Verwenden Sie das Plug-In-Registrierungstool, wählen Sie **Registrierung aufheben** (löschen) aus, um eine Assembly, ein Plug-In oder einen Schritt zu löschen. Das löschen einer Assembly löscht alle Plug-Ins und Schritte für diese Assembly.

![Registrierung einer Assembly aufheben](media/tutorial-update-plug-in-unregister.png)
