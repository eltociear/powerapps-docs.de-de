---
title: Reagieren auf DSR-Anforderungen für vom System generierte Protokolle in PowerApps, Microsoft Flow und Common Data Service (CDS) für Apps | Microsoft-Dokumentation
description: Hier finden Sie ein exemplarische Vorgehensweise zum Reagieren auf DSR-Anforderungen für vom System generierte Protokolle in PowerApps, Microsoft Flow und Common Data Service (CDS) für Apps.
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: 18bba11ce747b1e04be6013bf41419c34232865a
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37897246"
---
# <a name="responding-to-dsr-requests-for-system-generated-logs-in-powerapps-microsoft-flow-and-common-data-service-for-apps"></a>Reagieren auf DSR-Anforderungen für vom System generierte Protokolle in PowerApps, Microsoft Flow und Common Data Service für Apps
Microsoft bietet Ihnen die Möglichkeit, auf vom System generierte Protokolle zuzugreifen, die gemäß der Datenschutz-Grundverordnung (DSGVO) der Europäischen Union nach der weitgefassten Definition der *personenbezogenen Daten* als personenbezogen gelten könnten, und diese zu exportieren und zu löschen. Zu den Beispielen für vom System generierte Protokolle, die gemäß der DSGVO als persönlich gelten könnten, zählen die folgenden:
* Produkt- und Dienstnutzungsdaten, wie z.B. Aktivitätsprotokolle von Benutzern
* Suchanforderungen und Abfragedaten von Benutzern
* Von Produkten und Diensten als Ergebnis der Systemfunktionalität und Interaktion von Benutzern oder anderen Systemen generierte Daten

Beachten Sie, dass die Möglichkeit zur Einschränkung oder Berichtigung von Daten in vom System generierten Protokollen nicht unterstützt wird. Daten in vom System generierten Protokollen stellen auf Fakten beruhende Aktionen dar, die innerhalb der Microsoft-Cloud durchgeführt werden. Diagnostische Daten &mdash;einschließlich der an solchen Daten vorgenommenen Änderungen&mdash; würden den historischen Datensatz von Aktionen umfassen und Betrugs- und Sicherheitsrisiken erhöhen.

## <a name="prerequisites"></a>Voraussetzungen
In diesem Artikel werden passende Reaktionen auf DSR-Anforderungen für Protokolle in verwalteten und nicht verwalteten Mandanten thematisiert, die von einem System generiert werden. Wenn Sie überprüfen möchten, ob Sie einem verwaltetem oder einem nicht verwalteten Mandanten angehören, finden Sie nachfolgend weitere Informationen im Abschnitt **Bestimmen des Mandantentyps**.

## <a name="accessing-and-exporting-system-generated-logs-for-managed-tenants"></a>Zugreifen auf und Exportieren der vom System generierten Protokolle für verwaltete Mandanten
Administratoren können auf vom System generierte Protokolle zugreifen, die mit der Verwendung von Diensten und Anwendungen in PowerApps, Microsoft Flow und Common Data Service (CDS) for Apps durch einen Benutzer verbunden sind.

So greifen Sie auf vom System generierte Protokolle zu und exportieren diese:

1. Wechseln Sie zum [Microsoft Service Trust Portal](https://servicetrust.microsoft.com/), und melden Sie sich mit den Anmeldeinformationen eines globalen Office 365-Administrators an.

2. Wählen Sie oben auf der Seite aus der Dropdownliste **Datenschutz** den Eintrag **Data Subject Request** (Datensubjektanforderung) aus.

3. Wählen Sie auf der Seite **Data Subject Request** (Datensubjektanforderung) unter **Vom System generierte Protokolle** die Option **Datenprotokollexport** aus. Die Seite „Datenprotokollexport“ wird angezeigt. Sie enthält eine Liste mit Anforderungen zum Exportieren von Daten, die von Ihrer Organisation übermittelt wurden.

4. Klicken Sie auf **Create Export Data Request** (Anforderung zum Exportieren von Daten erstellen), um eine neue Anforderung für einen Benutzer zu erstellen.

    Nachdem Sie eine neue Anforderung erstellt haben, wird die Anforderung auf der Seite **Datenprotokollexport** aufgeführt. Dort können Sie den Status nachverfolgen. Nach Abschluss einer Anforderung können Sie über einen Link auf die vom System generierten Protokolle zugreifen, die innerhalb von 30 Tagen nach Erstellung der Anforderung in den Azure-Speicherort Ihrer Organisation exportiert werden. Die Daten werden in gängigen, maschinenlesbaren Dateiformaten gespeichert, wie z.B. XML, CSV oder JSON. Wenn Sie nicht über ein Azure-Konto und einen Azure-Speicherort verfügen, müssen Sie für Ihre Organisation ein Azure-Konto und/oder einen Azure-Speicherort erstellen, damit das Tool für den Datenprotokollexport die vom System generierten Protokolle exportieren kann. Weitere Informationen finden Sie unter [Einführung in Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Die folgende Tabelle enthält eine Übersicht über den Zugriff auf vom System generierte Protokolle für verwaltete Mandanten und den Export solcher Protokolle:

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

## <a name="deleting-system-generated-logs-for-managed-tenants"></a>Löschen der vom System generierten Protokolle für verwaltete Mandanten
Wenn Sie vom System generierte Protokolle löschen möchten, die über eine Zugriffsanforderung abgerufen wurden, müssen Sie den Benutzer aus dem Dienst entfernen und sein Azure Active Directory-Konto unwiderruflich löschen. Anweisungen zum unwiderruflichen Löschen eines Benutzers finden Sie im Abschnitt **Löschen eines Benutzers** in der *Dokumentation zur DSGVO für Azure-Datensubjektanforderungen* im [Office 365 Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/GDPRDSR). Beachten Sie, dass das widerrufliche Löschen eines Benutzerkontos nicht umkehrbar ist, sobald dieser Vorgang eingeleitet wurde.

Durch das widerrufliche Löschen eines Benutzerkontos werden die Benutzerdaten aus den vom System generierten Protokollen für die Dienste von PowerApps, Microsoft Flow und CDS für Apps innerhalb von 30 Tagen entfernt.


## <a name="accessing-and-exporting-system-generated-logs-for-unmanaged-tenants"></a>Zugreifen auf die und Exportieren der vom System generierten Protokolle für nicht verwaltete Mandanten

Benutzer können auf vom System generierte Protokolle zugreifen, die mit ihrer Verwendung von Diensten und Anwendungen in PowerApps, Microsoft Flow und Common Data Service (CDS) für Apps verbunden sind.

So greifen Sie auf vom System generierte Protokolle zu und exportieren diese:
1. Navigieren Sie zum [Work and School Privacy portal (Datenschutzportal für Geschäfts-, Schul- oder Unikonten)](https://go.microsoft.com/fwlink/?linkid=873123).
1. Auf der Seite **Meine Datenanforderungen** können Benutzer einen Datenexport anfordern, indem sie auf die Schaltfläche **Neue Exportanforderung** klicken.
1. Wenn Sie auf diese Schaltfläche klicken, werden Sie aufgefordert, Ihre Anforderung zu bestätigen. Klicken Sie auf **Ja**, um fortzufahren.
1. Es kann bis zu einem Monat dauern, bis neue Exportanforderungen abgeschlossen werden. In der Zwischenzeit wird der Status **Wird ausgeführt** angezeigt.
1. Wenn der Vorgang abgeschlossen wurde, wird die Spalte **Datum der Fertigstellung** aufgefüllt, und Sie erhalten einen Link zu Ihren **vom System generierten** Protokollen.
1. Klicken Sie auf diesen Link, um Ihre Daten herunterzuladen. Sie können auch einen Text-Editor verwenden, um diese Daten abzurufen.
1. Beachten Sie außerdem, dass das **Ablaufdatum** für diesen Inhalt in der Spalte „Ablaufdatum“ aufgefüllt wird. Sie haben bis zu diesem Datum Zeit, Ihre vom System generierten Protokolle abzurufen.

Die folgende Tabelle enthält eine Übersicht über den Zugriff auf vom System generierte Protokolle für nicht verwaltete Mandanten und den Export solcher Protokolle:

| Frage | Antwort |
| --- | --- |
| Wie lange dauert es, bis das Microsoft-Tool für den Datenprotokollexport eine Anforderung abgeschlossen hat? |    Dies hängt von mehreren Faktoren ab. In den meisten Fällen müsste die Anforderung innerhalb von einem oder zwei Tagen abgeschlossen sein, es kann jedoch bis zu 30 Tage dauern.
| Welches Format hat die Ausgabe? | Die Ausgabe weist ein strukturiertes, maschinenlesbares Dateiformat auf, wie z.B. XML, CSV oder JSON.
| Wer hat Zugriff auf das Tool für den Datenprotokollexport, um Zugriffsanforderungen für vom System generierte Protokolle zu übermitteln? | Ein Benutzer, der Mitglied eines nicht verwalteten Mandanten ist, kann Anforderungen übermitteln.
| Welche Daten gibt das Tool für den Datenexport zurück? | Das Tool für den Datenexport gibt vom System generierte Protokolle zurück, die von Microsoft gespeichert werden. Die exportierten Daten erstrecken sich über verschiedene Microsoft-Dienste, einschließlich Office 365, Azure, Dynamics, PowerApps, Microsoft Flow und CDS für Apps.
| Wie werden die Daten an den Benutzer zurückgegeben? |   Daten werden in eine Microsoft-Website exportiert. Dabei wird dem Benutzer, der die DSR-Anforderung gesendet hat, ein sicherer Link zur Verfügung gestellt.
| Wie sehen Daten in vom System generierten Protokollen aus? |  Beispiel für einen vom System generierten Protokolldatensatz im JSON-Format: <br> [{ <br>"DateTime": "2017-04- 28T12:09:29-07:00",  <br> "AppName": "SharePoint", <br> "Action": "OpenFile", "IP": "154.192.13.131", <br> "DevicePlatform": "Windows 1.0.1607" <br>}]

> [!NOTE]
>  Aus Sicherheits- und Überwachungsgründen können Sie bei einigen Features keine vom System generierten Protokolle exportieren oder löschen. Dadurch wird die Integrität von personenbezogenen Daten gewährleistet.
>
>

## <a name="deleting-system-generated-logs-for-unmanaged-tenants"></a>Löschen der vom System generierten Protokolle für nicht verwaltete Mandanten
Wenn Sie vom System generierte Protokolle löschen möchten, die über eine Zugriffsanforderung abgerufen werden, müssen Sie Ihr Konto schließen. Dadurch werden Ihre vom System generierten Protokolle gelöscht und Ihre Daten aus PowerApps, Microsoft Flow und CDS für App-Dienste innerhalb von 30 Tagen gelöscht.

So löschen Sie vom System generierte Protokolle:
1. Navigieren Sie zum [Work and School Privacy portal (Datenschutzportal für Geschäfts-, Schul- oder Unikonten)](https://go.microsoft.com/fwlink/?linkid=873123).
1. Auf der Seite **Meine Datenanforderungen** können Benutzer anfordern, dass ihre Daten gelöscht werden, indem sie auf die Schaltfläche **Konto schließen** klicken.
1. Wenn Sie auf diese Schaltfläche klicken, werden Sie aufgefordert, Ihre Anforderung zu bestätigen. Klicken Sie auf **Ja**, um fortzufahren.
1. Sobald das Konto geschlossen wird, haben Sie keinen Zugriff mehr auf PowerApps, Microsoft Flow und CDS.

## <a name="determining-tenant-type"></a>Bestimmen des Mandantentyps
Wenn Sie überprüfen möchten, ob Sie Benutzer eines verwalteten oder eines nicht verwalteten Mandanten sind, müssen Sie die folgenden Aktionen durchführen:
1. Öffnen Sie die folgende URL in einem Browser. Fügen Sie dabei Ihre E-Mail-Adresse in die URL ein: [https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1](https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1).

2. Wenn Sie Mitglied eines **nicht verwalteten Mandanten** sind, wird der Wert `"IsViral": true` in der Antwort angezeigt.
   ```
      {
      ...
      "Login": "foobar@unmanagedcontoso.com",
      "DomainName": "unmanagedcontoso.com",
      "IsViral": **true**,
      ...
      }
   ```

3. Wenn dies nichts der Fall ist, sind Sie Teil eines verwalteten Mandanten.
