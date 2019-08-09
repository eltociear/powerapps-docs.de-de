---
title: 'Exemplarische Vorgehensweise: Azure-fähiges Plug-In mit Plug-In-Registrierungstool registrieren (Common Data Service) | Microsoft Docs'
description: 'Diese exemplarische Vorgehensweise veranschaulicht, wie Sie einen Service-Endpunktschritt mithilfe des Plug-In-Registrierungstools registrieren. '
keywords: ''
ms.date: 06/01/2019
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: b5ef50fa-8085-f425-3968-804d012fc840
author: brandonsimons
ms.author: jdaly
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-register-an-azure-aware-plug-in-using-the-plug-in-registration-tool"></a>Tutorial: Azure-fähiges Plug-In mit Plug-In-Registrierungstool registrieren

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/walkthrough-register-azure-aware-plug-in-using-plug-in-registration-tool -->

Diese exemplarische Vorgehensweise veranschaulicht, wie Sie einen Dienstendpunktschritt konfigurieren und mithilfe des Plug-In-Registrierungstools registrieren. Nachdem er konfiguriert ist, kann Common Data Service (CDS) den Ausführungskontext des aktuellen Vorgang zu einem Azure-Lösungsendpunkt stellen. Bei diese exemplarische Vorgehensweise wird der Schritt zum Bereitstellen des Ausführungskontexts der <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>-Nachricht für eine `Account`-Entität des Azure Service Bus registriert.  
  
Die folgenden Voraussetzungen müssen erfüllt sein, bevor Sie diese exemplarische Vorgehensweise starten:  
  
- Zugriff auf das Plug-In-Registrierungstool. [!INCLUDE[proc-download-plugin-registration-tool](../../includes/proc-download-plugin-registration-tool.md)]
- Ihre CDS-Systembenutzerfirma muss über die Rolle „Systemadministrator” oder „Systemanpasser” verfügen. 
- Erhalten Sie Zugang zu einem Azure-Plattformservice-Namespace, das für die SAS-Autorisierung konfiguriert ist, zu der CDS eine Message postet.  
- Wenn Sie planen, irgendeine andere Azure-Messageentität als eine Warteschlange zu benutzen, zum Beispiel eine Weiterleitung, muss es eine Listener-Anwendung geben, die aktiv auf den spezifizierten Lösungsendpunkt für CDS lauscht, um erfolgreich an den Azure Service Bus bereitzustellen. Weitere Informationen finden Sie unter [Listener für eine Microsoft Azure-Lösung schreiben](write-listener-application-azure-solution.md).  
- Ein konfigurierter Service-Endpunkt mit SAS-Autorisierung ist in der Zielorganisation verfügbar. Weitere Informationen: [Exemplarische Vorgehensweise: Konfigurieren von Microsoft Azure (SAS) für die Integration mit CDS](walkthrough-configure-azure-sas-integration.md).  
  
## <a name="steps"></a>Schritte

Diese exemplarische Vorgehensweise enthält die folgenden Schritte:  
  
1. [Verbindung mit CDS herstellen](#BKMK_Connect)  
1. [Registrieren Sie einen Dienstendpunktschritt für ein Ereignis](#BKMK_Register)  
1. [Testen Sie die Endpunktregistrierung](#BKMK_Test)
  
<a name="BKMK_Connect"></a>

## <a name="connect-to-cds"></a>Verbindung mit CDS herstellen
 
Führen Sie die unten angegebenen Schritte aus, um mithilfe des Registrierungstools Plug-Ins eine Verbindung mit CDS herzustellen.  
  
1. Führen Sie das Plug-In-Registrierungstool aus.  
1. Klicken Sie auf **Create New Connection** (Neue Verbindung erstellen).  
1. Wählen Sie im Dialogfeld **Anmelden** die Option **Office 365** aus.

    ![Anmeldeformular für eine Online-Bereitstellung](media/crm-v6s-pr.png "Anmeldeformular für eine Online-Bereitstellung")

1. Wenn Sie **Liste der verfügbaren Organisationen anzeigen** aktivieren, wird eine Liste von Organisationen angezeigt, denen Sie angehören, nachdem Sie auf **Anmeldung** klicken. Dadurch können Sie die Organisation auswählen, mit der Sie den Dienstendpunkt registrieren möchten. Andernfalls wird die standardmäßige Organisation verwendet.  
1. Geben Sie die angegebenen Informationen zum Server und der Firma ein und klicken Sie dann auf **Anmeldung**.  
  
<a name="BKMK_Register"></a>

## <a name="register-a-service-endpoint-step-for-an-event"></a>Registrieren Sie einen Dienstendpunktschritt für ein Ereignis

Führen Sie die unten angegebenen Schritte aus, um auf dem Dienstendpunkt einen Schritt für ein Ereignis zu registrieren.  
  
1. Wählen Sie in der Registerkarte der Organisationsregisterkarte einen Dienstendpunkt aus.  
1. Navigieren Sie zum Menü **Registrieren**, oder klicken Sie auf **Neuen Schritt registrieren**.  
1. Füllen Sie das Dialogfeld **Neuen Schritt registrieren** für ein Ereignis zum Erstellen einer Firma aus, wie in der folgenden Abbildung gezeigt.

    ![Erstellen eines Dienstendpunktschrittes](media/crm-v6s-pr-service-endpoint-step.png "Erstellen eines Dienstendpunktschrittes")
  
1. Klicken Sie auf **Neuen Schritt registrieren**.  
  
CDS postet jetzt die aktuelle Meldung, die den Ausführungskontext für den Servicebus enthält, sobald eine Firma erstellt wird. Der Post wird asynchron ausgeführt und wird nicht sofort ausgeführt.  
  
<a name="BKMK_Test"></a>

## <a name="test-the-endpoint-registration"></a>Testen Sie die Endpunktregistrierung

Nachdem der Endpunkt registrieren ist, können Sie diesen testen. Ein Listener muss ausgeführt werden, oder eine Warteschlange für den Zielendpunkt für den Servicebuspost, damit der Plug-In durchgeführt werden kann.  
  
1. Öffnen Sie eine Canvas- oder modellgesteuerte Anwendung für dieselbe Organisation, unter der Sie den Dienstendpunkt registriert haben.  
1. Erstellen Sie einen neuen Firmenentitätsdatensatz.
1. Geben Sie einen Firmennamen, beispielsweise „Adventure Works Cycle” in das Feld **Firmenname** ein und klicken Sie dann auf **Speichern**.  
1. Warten Sie etwa 10 Minuten, damit der Azure Service Bus-Beitrag erfolgen kann.  
1. Wählen Sie in der modellgesteuerte App **Dynamics 365 – benutzerdefiniert** **Einstellungen > System > Systemaufträge**.  
1. Öffnen Sie den Systemauftrag, der denselben Namen hat, den Sie auch für Ihren Dienstendpunkt angegeben haben. Überprüfen Sie den Status, um zu sehen, ob der Post erfolgreich war, wartet oder fehlerhaft war.  
  
Sie können die Registrierung des Endpunkts jetzt aufheben, wenn Sie das wünschen, indem Sie ihn in der Strukturansicht des Tools auswählen und auf **Registrierung aufheben** klicken.  
  
### <a name="see-also"></a>Siehe auch

[Azure-Integration für CDS](azure-integration.md)<br />
[Einführung in die Microsoft Azure-Integration mit CDS](azure-integration.md)
