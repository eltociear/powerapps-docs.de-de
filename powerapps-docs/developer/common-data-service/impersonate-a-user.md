---
title: Wechsel der Identität eines Benutzers mithilfe der Web API (Common Data Service for Apps) | Microsoft Docs
description: 'Erfahren Sie, wie Sie Plugin-Code schreiben, um im Namen eines bestimmten Benutzers zu handeln.'
ms.custom: ''
ms.date: 1/24/2019
ms.reviewer: ''
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
---
# Die Identität eines Benutzers annehmen

Manchmal benötigen Sie den Code in einem Plug-in, um ihn im Kontext eines anderen Benutzers auszuführen, z. B. um eine Operation in dessen Namen durchzuführen.

Es gibt zwei Möglichkeiten, Identitätswechsel in Plug-Ins anzuwenden: Bei der Registrierung oder der Ausführung.

## Bei der Plug-In-Registrierung

Wenn Sie einen Plug-In-Schritt registrieren, können Sie ein Benutzerkonto angeben, das benutzt werden soll, wenn der Code ausgeführt wird, indem Sie von der Option **Im Kontext des Benutzers ausführen** auswählen. Standardmäßig ist diese auf die Nutzung von **Aufrufender Benutzer** festgelegt. Das ist das Benutzerkonto, durch das die Aktion initiiert wurde. Wenn diese Standardoption angewendet ist, wird die [SdkMessageProcessingStep.ImpersonatingUserId](reference/entities/sdkmessageprocessingstep.md#BKMK_ImpersonatingUserId) auf null oder <xref:System.Guid.Empty> festgelegt.

Weitere Informationen: [Plug-In-Schritt registrieren](register-plug-in.md#register-plug-in-step).

## Während der Plug-In-Ausführung

Sie können die Einstellung überschrieben, die bei der Registrierung zur Laufzeit angegeben wurde, nämlich durch Festlegen vom <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>.<xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})><xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})> `userId` `userId`-Parameter.

Dies wird in der Regel festgelegt auf den <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.UserId><xref:Microsoft.Xrm.Sdk.IExecutionContext.UserId> -Werte, wodurch das Benutzerkonto angewendet wird, das durch die Plug-In-Schrittregistrierung definiert wurde.

```csharp
(IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    IOrganizationService service = serviceFactory.CreateOrganizationService(context.UserId);
```

Wenn Sie die Schrittregistrierung überschreiben möchten, können Sie den Wert übergeben von <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InitiatingUserId><xref:Microsoft.Xrm.Sdk.IExecutionContext.InitiatingUserId> um einen Service zu haben, bei dem das Benutzerkonto verwendet wird, durch das die Aktion initiiert wurde, die die Ausführung des Plug-Ins verursacht hat.

Sie können auch die [SystemUser.SystemUserId](reference/entities/systemuser.md#BKMK_SystemUserId) von einem gültigen Benutzerkonto bereitstellen. Dies funktioniert, solange dieser Benutzer über die erforderlichen Berechtigungen verfügt, um die Vorgänge im Plug-In auszuführen.

### Siehe auch

[[Plug-Ins](plug-ins.md)](plug-ins.md)  
[[Schreiben eines Plug-Ins](write-plug-in.md)](write-plug-in.md)