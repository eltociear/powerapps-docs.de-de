---
title: 'Beispiel: Arbeiten mit Suchdienst (Common Data Service) | Microsoft Docs'
description: Dieser Beispielcode zeigt, wie Sie mit Suchdiensten arbeiten
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6099f304e62092dd63dd35472b80d3c22471de8e
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155482"
---
# <a name="work-with-discovery-service"></a>Arbeiten mit Suchdiensten

Dieser Beispielcode zeigt, wie Sie den Suchdienst mit SDK-Assemblies verwenden können. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/Nava_samplecode/cds/orgsvc/C%23/DiscoveryService) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

Dieses Beispiel öffnet keinen Dialog, um Sie nach Verbindungsinformationen zu fragen.

Sie müssen zuerst `username` und `password` Variablen in der `SampleProgram.Main` Methode einstellen, bevor Sie dieses Beispiel erstellen können.

## <a name="what-this-sample-does"></a>Funktionsweise:

Dieses Beispiel verwendet die SDK Assembly `DiscoveryServiceProxy`, um den Suchdienst mit den Anmeldeinformationen eines Benutzers abzufragen, um festzustellen, mit welchen Umgebungen er sich verbinden kann.

Wenn eine oder mehrere Umgebungen zurückgegeben werden, fordert das Beispiel den Benutzer auf, eine auszuwählen und verwendet dann ein `WhoAmIRequest`, um das `SystemUser.UserId` für diese Umgebung zurückzugeben.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Dieses Beispiel erfordert keine spezielle Konfiguration, außer dass es einen gültigen Benutzernamen und ein gültiges Passwort für die Benutzeranmeldung gibt.

Wenn Sie das regionale Rechenzentrum kennen, in dem sich Ihre Umgebungen befinden, wird das Beispiel schneller laufen, wenn Sie diesen Wert in Zeile 40 der Datei SampleProgram.cs festlegen.

In SampleMethods.cs gibt es eine `DataCenter` Enumeration für jedes der bekannten Rechenzentren. Jedes Enumerationsmitglied ist mit einer `Description`-Notation versehen. Alle diese Mitglieder mit Ausnahme von `Unknown` haben die URL für den regionalen Suchdienst als Beschreibung. 


### <a name="demonstrate"></a>Demonstrieren

1. Unter Verwendung der Benutzer-Anmeldeinformationen und des `dataCenter`-Wertes verwendet das Programm die statische `GetAllOrganizations`-Methode, um alle bekannten Umgebungen für den Benutzer abzurufen.
1. Das `GetAllOrganizations`-Verfahren erkennt, ob der `dataCenter`-Wert auf `DataCenter.Unknown` gesetzt ist. Wenn es auf dieses Element gesetzt ist, wird diese Methode alle anderen Elemente in der `DataCenter`-Enumeration durchlaufen und alle Umgebungen abrufen, die mit der statischen `GetOrganizationsForDataCenter`-Methode gefunden werden.

    Wenn ein bestimmtes Rechenzentrum festgelegt ist, ruft `GetAllOrganizations` einfach `GetOrganizationsForDataCenter` mit diesen Werten an.

1. Die `GetOrganizationsForDataCenter`-Methode extrahiert die Rechenzentrum-Suchdienst-Url aus der Mitglied `Description`-Dekoration und verwendet sie zusammen mit den Benutzer-Anmeldeinformationen, um die `RetrieveOrganizationsRequest`-Suchdienstmeldung auszuführen.

    Ein `System.ServiceModel.Security.SecurityAccessDeniedException` wird erwartet, wenn der Benutzer keine Umgebungen in einem bestimmten Rechenzentrum hat.

1. Wenn Umgebungen nach der `GetAllOrganizations`-Methode zurückgegeben werden, werden sie in der Konsole aufgelistet und Sie werden aufgefordert, eine durch Eingabe einer Zahl auszuwählen. Wenn Ihre Auswahl gültig ist, werden die ausgewählten Umgebungsdaten verwendet, um einen `WhoAmIRequest` auszuführen und den `SystemUser.UserId` für den Benutzer in dieser Umgebung zurückzugeben.

### <a name="clean-up"></a>Bereinigung

Dieses Beispiel erstellt keine Datensätze. Keine Bereinigung erforderlich
