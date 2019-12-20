---
title: 'Beispiel: Schnellstart für XRM Tooling API (Common Data Service) | Microsoft Docs'
description: ''
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Dynamics 365 (online)
ms.assetid: 060d45bb-b7fd-48bd-ab8f-629c1b8bc1dc
caps.latest.revision: 20
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6e4991ce913cf5812b1405321619df84759b1cb0
ms.sourcegitcommit: 8f4b2c070ff57bf6ceac8d694b264bff163c6eab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "2804384"
---
# <a name="sample-quick-start-for-xrm-tooling-api"></a>Beispiel: Schnellstart für XRM Tooling API

Das QuickStart-Beispiel ist ein verwaltetes .NET-Framework-Codebeispiel, das zeigt, wie eine Verbindung zu einer Common Data Service-Instanz hergestellt wird, indem die XRM Tooling APIs verwendet werden, und grundlegende Erstellungs-, Aktualisierungs-, Abruf- und Löschvorgänge für eine Entität ausgeführt werden. Weitere Informationen zur XRM-Tooling finden Sie unter [Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md).

Laden Sie das Beispiel: [Arbeiten mit der XRM Tooling-API](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/Xrm%20Tooling/Quick%20start%20for%20XRM%20Tooling%20API) herunter.

## <a name="how-to-run-the-sample"></a>Wie das Beispiel ausgeführt wird

1. Um eine lokale Kopie zu erhalten, laden Sie den Beispielbericht herunter und extrahieren Sie ihn.  
2. Öffnen Sie die Datei `Quick start for XRM Tooling\C#\QuickStartXRMToolingWPFClient.sln` in Visual Studio.  
3. Drücken Sie **F5**, um das Programm zu kompilieren und auszuführen.  


## <a name="demonstrates"></a>Demonstriert

- Der Beispielcode wird mithilfe der **WPF-Anwendung für CRM**-SDK-Vorlage erstellt, die ein allgemeines Anmeldungssteuerelement mit integrierter Unterstützung für Zwischenspeicherung und Wiederverwendung von Authentifizierungs- und Anmeldeinformationen bietet. Weitere Informationen zum allgemeinen Anmeldungssteuerelement und wie die SDK-Vorlage in Visual Studioverwendet wird, finden Sie in [Verwendung des allgemeinen XRM Tooling-Anmeldungssteuerelements](use-xrm-tooling-common-login-control-client-applications.md).  
- Zum Einrichten einer Verbindung mit Common Data Service wird kein Hilfscode verwendet.  
- Nach der Verbindung mit Common Data Service führt das Beispiel grundlegende Erstellungs-, Aktualisierungs-, Abruf- und Löschvorgänge an einer Firmenentität aus.  
- Speichert Benutzeranmeldeinformationen in einer Konfigurationsdatei (`Default_QuickStartXRMToolingWPFClient.exe.config`) im Ordner `c:\Users\`*`<username>`*`\AppData\Roaming\Microsoft\QuickStartXRMToolingWPFClient`, wenn das Beispiel zum ersten Mal ausgeführt wird, und fordert danach den Benutzer auf, entweder die gespeicherten Anmeldeinformationen zu verwenden oder in der Laufzeit neue anzugeben, um sich bei Common Data Service anzumelden.  
- Generiert, wenn Probleme auftreten, die folgenden Protokolldateien, um die Problembehandlung zu unterstützen:  
- Login_ErrorLog.log: Um Anmeldungsfehler zu melden. Diese Datei ist unter `C:\Users\`*`<username>`*`\AppData\Roaming\Microsoft\QuickStartXRMToolingWPFClient` verfügbar.  
- QuickStartXRMToolingWPFClient.log: Um Betriebsfehler zu melden. Diese Datei ist am gleichen Ort verfügbar wie die ausführbare Datei, d. h. im Ordner "Debuggen" Ihres Visual Studio-Projekts.  

### <a name="see-also"></a>Siehe auch

[Verwenden Sie das allgemeine XRM Toolinng-Anmeldungssteuerelement](use-xrm-tooling-common-login-control-client-applications.md)<br />
[Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md)<br />

