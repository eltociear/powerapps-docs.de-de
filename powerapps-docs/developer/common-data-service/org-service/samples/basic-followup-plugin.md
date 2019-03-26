---
title: 'Beispiel: Erstellen Sie ein Basis-Plugin (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie man ein einfaches Plug-in schreibt, das eine Folgeaktivität erstellt.'
ms.custom: ''
ms.date: 1/29/2019
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
# Beispiel: Erstellen eines grundlegenden Plug-Ins

Dieses Beispiel zeigt, wie man ein einfaches Plug-in schreibt, das eine Folgeaktivität erstellt. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/FollowupPlugin) herunterladen.

## Wie man dieses Beispiel ausführt

1. Um eine lokale Kopie zu erhalten, laden Sie den [Beispielbericht](https://github.com/Microsoft/PowerApps-Samples) herunter, oder klonen Sie ihn. Dieses Beispiel befindet sich unter PowerApps-Samples-master\cds\orgsvc\C#\FollowupPlugin.
2. Öffnen Sie die Beispiellösung in Visual Studio, navigieren Sie zu den Eigenschaften des Projekts und vergewissern Sie sich, dass die Assembly während des Build signiert wird. Drücken Sie F6, um die Assembly des Samples zu erstellen (FollowupPlugin.dll).
3. Führen Sie das Plug-in-Registrierungstool aus und registrieren Sie die Assembly des Samples in der Sandbox und Datenbank des D365-Servers. Wenn Sie einen Schritt registrieren, geben Sie die Option Nachricht erstellen, Kontoentität und asynchronen Modus an.
4. Führen Sie mit der D365-Anwendung den entsprechenden Vorgang aus, um die Nachricht und Entitätsanforderung aufzurufen, auf der Sie das Plug-in registriert haben (Erstellen eines Kontos).
5. Nach dem Ausführen des Plugins sollten Sie einen neuen Trace-Log-Eintrag "FollowupPlugin: Erfolgreich die Aufgabe Aktivität" und eine neue Aktivität mit dem Betreff "E-Mail an den neuen Kunden senden" angelegt. die in 7 Tagen aktiviert werden soll.
6. Wenn Sie mit dem Testen fertig sind, heben Sie die Registrierung der Assembly auf und gehen Sie wie folgt vor.

## Funktionsweise:

Wenn es bei der Erstellung eines Kontos ausgeführt wird, erstellt das Plug-in eine Aktivität, um den Benutzer daran zu erinnern, innerhalb von 7 Tagen mit dem Kunden des Kontos zu kommunizieren.

## Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### Demonstrieren

1. So erstellen Sie eine Aufgabenaktivität und planen sie für ein zukünftiges Datum ein.
2. Wie man den Tracing-Service verwendet, um Laufzeitinformationen zu protokollieren.
3. Wie man Ausnahmen vom Webservice abfangen und verarbeiten kann.

### Siehe auch
[[Schreiben eines Plug-Ins](../../write-plug-in.md)](../../write-plug-in.md)  
[[Registrieren eines Plug-Ins](../../register-plug-in.md)](../../register-plug-in.md)