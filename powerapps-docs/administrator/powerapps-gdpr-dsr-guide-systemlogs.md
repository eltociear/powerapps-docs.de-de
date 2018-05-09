---
title: Reagieren auf DSR-Anforderungen für vom System generierte Protokolle in PowerApps, Microsoft Flow und Common Data Service for Apps | Microsoft-Dokumentation
description: Schritt-für-Schritt-Anleitung zum Reagieren auf DSR-Anforderungen für vom System generierte Protokolle in PowerApps, Microsoft Flow und Common Data Service for Apps
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms-topic: article
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/23/2018
ms.author: jamesol
ms.openlocfilehash: c3086ce05ba748b5387ec4ae5a1e794658b5677a
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="responding-to-dsr-requests-for-system-generated-logs-in-powerapps-microsoft-flow-and-common-data-service-for-apps"></a>Reagieren auf DSR-Anforderungen für vom System generierte Protokolle in PowerApps, Microsoft Flow und Common Data Service für Apps
Microsoft bietet Ihnen die Möglichkeit, auf vom System generierte Protokolle zuzugreifen, die gemäß der Datenschutz-Grundverordnung (DSGVO) der Europäischen Union nach der weitgefassten Definition der *personenbezogenen Daten* als personenbezogen gelten könnten, und diese zu exportieren und zu löschen. Zu den Beispielen für vom System generierte Protokolle, die gemäß der DSGVO als persönlich gelten könnten, zählen die folgenden:
* Produkt- und Dienstnutzungsdaten, wie z.B. Aktivitätsprotokolle von Benutzern
* Suchanforderungen und Abfragedaten von Benutzern
* Von Produkten und Diensten als Ergebnis der Systemfunktionalität und Interaktion von Benutzern oder anderen Systemen generierte Daten

Beachten Sie, dass die Möglichkeit zur Einschränkung oder Berichtigung von Daten in vom System generierten Protokollen nicht unterstützt wird. Daten in vom System generierten Protokollen stellen auf Fakten beruhende Aktionen dar, die innerhalb der Microsoft-Cloud durchgeführt werden. Diagnostische Daten &mdash;einschließlich der an solchen Daten vorgenommenen Änderungen&mdash; würden den historischen Datensatz von Aktionen umfassen und Betrugs- und Sicherheitsrisiken erhöhen.

## <a name="accessing-and-exporting-system-generated-logs"></a>Zugreifen auf die und Exportieren der vom System generierten Protokolle
Administratoren können auf vom System generierte Protokolle zugreifen, die mit der Verwendung von Diensten und Anwendungen in PowerApps, Microsoft Flow und Common Data Service (CDS) for Apps durch einen Benutzer verbunden sind.

So greifen Sie auf vom System generierte Protokolle zu und exportieren diese:

1. Wechseln Sie zum [Microsoft Service Trust Portal](https://servicetrust.microsoft.com/), und melden Sie sich mit den Anmeldeinformationen eines globalen Office 365-Administrators an.

2. Wählen Sie oben auf der Seite aus der Dropdownliste **Datenschutz** den Eintrag **Data Subject Request** (Datensubjektanforderung) aus.

3. Wählen Sie auf der Seite **Data Subject Request** (Datensubjektanforderung) unter **Vom System generierte Protokolle** die Option **Datenprotokollexport** aus. Die Seite „Datenprotokollexport“ wird angezeigt. Sie enthält eine Liste mit Anforderungen zum Exportieren von Daten, die von Ihrer Organisation übermittelt wurden.

4. Klicken Sie auf **Create Export Data Request** (Anforderung zum Exportieren von Daten erstellen), um eine neue Anforderung für einen Benutzer zu erstellen.

    Nachdem Sie eine neue Anforderung erstellt haben, wird die Anforderung auf der Seite **Datenprotokollexport** aufgeführt. Dort können Sie den Status nachverfolgen. Nach Abschluss einer Anforderung können Sie über einen Link auf die vom System generierten Protokolle zugreifen, die innerhalb von 30 Tagen nach Erstellung der Anforderung in den Azure-Speicherort Ihrer Organisation exportiert werden. Die Daten werden in gängigen, maschinenlesbaren Dateiformaten gespeichert, wie z.B. XML, CSV oder JSON. Wenn Sie nicht über ein Azure-Konto und einen Azure-Speicherort verfügen, müssen Sie für Ihre Organisation ein Azure-Konto und/oder einen Azure-Speicherort erstellen, damit das Tool für den Datenprotokollexport die vom System generierten Protokolle exportieren kann. Weitere Informationen finden Sie unter [Einführung in Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Die folgende Tabelle enthält eine Übersicht über den Zugriff auf vom System generierte Protokolle und den Export solcher Protokolle:

| Frage | Antwort |
| --- | --- |
| Wie lange dauert es, bis das Microsoft-Tool für den Datenprotokollexport eine Anforderung abgeschlossen hat? |    Dies hängt von mehreren Faktoren ab. In den meisten Fällen müsste die Anforderung innerhalb von einem oder zwei Tagen abgeschlossen sein, es kann jedoch bis zu 30 Tage dauern.
| Welches Format hat die Ausgabe? | Die Ausgabe weist ein strukturiertes, maschinenlesbares Dateiformat auf, wie z.B. XML, CSV oder JSON.
| Wer hat Zugriff auf das Tool für den Datenprotokollexport, um Zugriffsanforderungen für vom System generierte Protokolle zu übermitteln? | Auf das Tool des DSGVO-Protokollmanagers haben globale Office 365-Administratoren Zugriff.
| Welche Daten gibt das Tool für den Datenprotokollexport zurück? | Das Tool für den Datenprotokollexport gibt vom System generierte Protokolle zurück, die von Microsoft gespeichert werden. Die exportierten Daten erstrecken sich über verschiedene Microsoft-Dienste, einschließlich Office 365, Azure, Dynamics, PowerApps, Microsoft Flow und CDS für Apps.
| Wie werden die Daten an den Benutzer zurückgegeben? |   Die Daten werden in den Azure-Speicherort Ihrer Organisation exportiert; die Administratoren in Ihrer Organisation können bestimmen, wie Benutzern diese Daten angezeigt werden bzw. wie sie an sie zurückgegeben werden.
| Wie sehen Daten in vom System generierten Protokollen aus? |  Beispiel für einen vom System generierten Protokolldatensatz im JSON-Format: <br> [{ <br>"DateTime": "2017-04- 28T12:09:29-07:00",  <br> "AppName": "SharePoint", <br> "Action": "OpenFile", "IP": "154.192.13.131", <br> "DevicePlatform": "Windows 1.0.1607" <br>}]

> [!NOTE]
>  Aus Sicherheits- und Überwachungsgründen können Sie bei einigen Features keine vom System generierten Protokolle exportieren oder löschen. Dadurch wird die Integrität von personenbezogenen Daten gewährleistet.
>
>

## <a name="deleting-system-generated-logs"></a>Löschen der vom System generierten Protokolle
Wenn Sie vom System generierte Protokolle löschen möchten, die über eine Zugriffsanforderung abgerufen wurden, müssen Sie den Benutzer aus dem Dienst entfernen und sein Azure Active Directory-Konto unwiderruflich löschen. Anweisungen zum unwiderruflichen Löschen eines Benutzers finden Sie im Abschnitt **Löschen eines Benutzers** in der *Dokumentation zur DSGVO für Azure-Datensubjektanforderungen* im [Office 365 Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/GDPRDSR). Beachten Sie, dass das widerrufliche Löschen eines Benutzerkontos nicht umkehrbar ist, sobald dieser Vorgang eingeleitet wurde.

Durch das widerrufliche Löschen eines Benutzerkontos werden die Benutzerdaten aus den vom System generierten Protokollen für die Dienste von PowerApps, Microsoft Flow und CDS für Apps innerhalb von 30 Tagen entfernt.