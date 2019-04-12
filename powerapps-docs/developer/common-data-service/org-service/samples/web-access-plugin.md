---
title: 'Beispiel: Webzugriff aus einem Plug-in (Common Data Service) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie man ein Plug-in schreibt, das auf Ressourcen im Web (Netzwerk) zugreifen kann.'
ms.custom: ''
ms.date: 1/16/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-web-access-from-a-plug-in"></a>Beispiel: Webzugriff von einem Plug-in aus

Dieses Beispiel zeigt, wie man ein Plug-in schreibt, das auf Web-(Netzwerk-)Ressourcen wie einen Webservice oder Feed zugreifen kann. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WebAccessPlugin) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

1. Um eine lokale Kopie zu erhalten, laden Sie den [Beispielbericht](https://github.com/Microsoft/PowerApps-Samples) herunter, oder klonen Sie ihn. Dieses Beispiel befindet sich unter PowerApps-Samples-master\cds\orgsvc\C#\WebAccessPlugin.
2. Öffnen Sie die Beispiellösung in Visual Studio, navigieren Sie zu den Eigenschaften des Projekts und vergewissern Sie sich, dass die Assembly während des Build signiert wird. Drücken Sie F6, um die Assembly des Samples zu erstellen (WebAccessPlugin.dll).
3. Führen Sie das Plug-in-Registrierungstool aus und registrieren Sie die Assembly des Samples in der Sandbox und Datenbank des D365-Servers. Wenn Sie einen Schritt registrieren, geben Sie eine Web-URI-Zeichenfolge an (z. B. http://www.microsoft.com) im unsicheren Konfigurationsfeld.
4. Führen Sie mit der D365-Anwendung den entsprechenden Vorgang aus, um die Nachricht und Entitätsanforderung aufzurufen, auf der Sie das Plug-in registriert haben.
5. Wenn das Plugin ausgeführt wird, löst der Code auf Zeile 63 eine Ausnahme aus. Dies führt dazu, dass in der D365-Applikation ein ISV-Fehlerdialog angezeigt wird. Wählen Sie in diesem Dialogfeld **Download file**, um das Fehlerprotokoll anzuzeigen, das die Ausgabe des Plug-Ins einschließlich der Webservice-Antwort enthält.
6. Wenn Sie mit dem Testen fertig sind, heben Sie die Registrierung der Assembly auf und gehen Sie wie folgt vor.

## <a name="what-this-sample-does"></a>Funktionsweise:

Wenn das Plug-in ausgeführt wird, lädt es Webseiten-Daten von der angegebenen Webservice-Adresse (oder der Standardadresse) herunter und schreibt diese Daten dann in eine Fehlerprotokolldatei oder den Suchdienst.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Überprüft den unsicheren Konfigurationsparameter des Assemblies auf einen Webadressenwert, ansonsten wird der Standardwert verwendet.
2. Die Klasse `System.Net.WebClient` wird von der Methode `Execute` des Plugins verwendet, um Webseiten-Daten herunterzuladen.
3. Es wird eine Ausnahme ausgelöst, um die Antwort des Webdienstes über eine Fehlerprotokoll-Downloaddatei zu Testzwecken verfügbar zu machen.

### <a name="demonstrate"></a>Demonstrieren

1. Die `WebClient.DownloadData`-Methode lädt Webseiten-Daten über eine Webservice-Anfrage herunter.
2. Diese Antwortdaten werden in ein Ausnahmefehlerprotokoll oder (optional) in den Tracing-Service zur späteren Ansicht in der D365-App geschrieben.
3. Der Plugin-Code zeigt auch, wie man eine WebException vom Webservice abfangen und verarbeiten kann.

### <a name="see-also"></a>Siehe auch
[Zugriff auf externe Web-Ressourcen](../../access-web-services.md)<br/>
[Registrieren eines Plug-Ins](../../register-plug-in.md)