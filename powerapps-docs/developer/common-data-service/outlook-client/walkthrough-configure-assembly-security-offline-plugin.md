---
title: 'Exemplarische Vorgehensweise: Konfigurieren von Assembly-Sicherheit für ein Offline-Plug-In (Common Data Service) | Microsoft Docs'
description: Dieses Thema enthält eine exemplarische Vorgehensweise für das Konfigurieren einer Assemblysicherheit für ein Offline-Plug-In.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="walkthrough-configure-assembly-security-for-an-offline-plug-in"></a>Exemplarische Vorgehensweise: Assemblysicherheit für ein Offline-Plug-In konfigurieren

Die Common Data Service-Plattform wendet eine zusätzliche Sicherheitsauflage auf registrierte Offline-Plug-In-Assemblys an. Wenn Dynamics 365 for Microsoft Office Outlook mit Offlinezugriff installiert wird, wird ein AllowList-Schlüssel der Systemregistrierung im Clientcomputer hinzugefügt. Für jede Assembly mit einem von Ihnen registrierten Offline-Plug-In müssen Sie einen Registrierungsunterschlüssel unter dem AllowList-Schlüssel registrieren, wobei der Schlüsselname vom öffentlichen Schlüsseltoken der Assembly abgeleitet wird. Wird der Schlüssel nicht hinzugefügt, kann das Offline-Plug-In von der Plattform nicht ausgeführt werden, auch wenn das Plug-In registriert ist. In dieser exemplarischen Vorgehensweise wird beschrieben, wie Sie diesen Unterschlüssel für eine Plug-In-Assembly hinzufügen.  
  
### <a name="get-the-public-key-token"></a>Öffentliches Schlüsseltoken abrufen  
  
1.  Laden Sie die Assembly mit dem Offline-Plug-In in das Plug-In-Registrierungstool. Weitere Informationen finden Sie unter [Ein Plug-in registrieren](../register-plug-in.md).  
  
2.  Wählen Sie die Plug-In-Assembly in der Strukturansicht des Tools aus.  
  
3.  Kopieren (Strg+C) Sie den Wert im Feld **Token für öffentlichen Schlüssel** in den Einfügepuffer.  
  
### <a name="add-an-allowlist-key"></a>AllowList-Schlüssel hinzufügen  
  
1.  Führen Sie den Registrierungs-Editor aus. Wählen Sie dazu **Start** und **Ausführen** aus, und geben Sie `regedit.exe` ein.  
  
2.  Navigieren Sie im Strukturansichtsbereich zum Schlüssel **AllowList**. Der vollständige Pfad des Schlüssels ist `HKEY_CURRENT_USER\Software\Microsoft\MSCRMClient\AllowList`.  
  
3.  Wählen Sie den Schlüssel **AllowList** aus, und klicken Sie mit der rechten Maustaste, um das Kontextmenü anzuzeigen.  
  
4.  Wählen Sie **Neu** aus, und klicken Sie dann auf **Schlüssel**, um einen neuen Unterschlüssel zu erstellen.  
  
5.  Fügen Sie den öffentlichen Schlüsseltokenwert in den Namen des neuen Unterschlüssels ein.  
  
6.  Schließen Sie den Registrierungs-Editor.  
  
### <a name="see-also"></a>Siehe auch  
 [Plug-In-Entwicklung](/dynamics365/customer-engagement/developer/plugin-development)   
 [Beispiel: Erstellen eines grundlegenden Plug-Ins](../org-service/samples/basic-followup-plugin.md)   
 [Registrieren und Bereitstellen von Plug-Ins](/dynamics365/customer-engagement/developer/register-deploy-plugins)