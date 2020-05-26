---
title: Aktuelisieren der Lösung für Notfallmaßnahmen und Überwachung der regionalen Behörden | Microsoft-Dokumentation
description: Bietet detaillierte Anweisungen für regionale IT-Administratoren, um die Lösung für Notfallmaßnahmen und Überwachung der regionalen Behörden für ihre Organisation zu aktualisieren.
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/06/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: f50cf7a7ae839cd22632bb4f5e1281ad585eb2a6
ms.sourcegitcommit: 2e186321d124dd6c0a4b51df5e8bc94a83ccf1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "3342201"
---
# <a name="upgrade-the-regional-governmentemergency-response-and-monitoring-solution"></a>Aktuelisieren der Lösung für Notfallmaßnahmen und Überwachung der regionalen Behörden

Führen Sie die Schritte in diesem Artikel aus, um Ihre *bestehende* Installation der Lösung für Notfallmaßnahmen und Überwachung der regionalen Behörden auf die neueste Version zu aktualisieren.

Wenn Sie diese Lösung zum ersten Mal installieren, lesen Sie [Lösung bereitstellen](deploy.md).

## <a name="prerequisites"></a>Voraussetzungen

- Stellen Sie sicher, dass Sie über die Anmeldeinformationen und Umgebungsdetails des globalen Administrators verfügen, auf denen Lösung für Notfallmaßnahmen und Überwachung der regionalen Behörden derzeit bereitgestellt wird.

-   Stellen Sie sicher, dass alle Benutzer von Ihrer Umgebung getrennt sind, bevor Sie ein Upgrade durchführen. Möglicherweise müssen Sie den Aktualisierungsprozess zu einem Zeitpunkt planen, an dem Ihre Benutzer nur minimale Hindernisse haben.   

## <a name="step-1-download-the-upgrade-deployment-package"></a>Schritt 1: Das Upgrade-Bereitstellungspaket herunterladen

Holen Sie sich das neueste Bereitstellungspaket (.zip) von <https://aka.ms/rer-solution>. Es ist dasselbe Bereitstellungspaket wie das, das Sie während des neuen Bereitstellungsschritts heruntergeladen haben.

**WICHTIG:** Stellen Sie vor dem Extrahieren der ZIP-Datei sicher, dass Sie sie entsperren.

1.  Klicken Sie mit der rechten Maustaste auf die .zip-Datei und wählen Sie **Eigenschaften**.

2.  Wählen Sie im Dialogfeld „Eigenschaften“ die Option **Entsperren** aus und wählen Sie dann **Anwenden**, gefolgt von **OK** aus.

Extrahieren Sie nach dem Entsperren der Datei die ZIP-Datei, um im extrahierten Ordner Folgendes anzuzeigen:

Wenn Sie die .zip-Datei extrahieren, sehen Sie in dem extrahierten Ordner Folgendes

|**Ordner**  |**Beschreibung**  |
|---------|---------|
|**Paket**     |  Der Ordner enthält das Package Deployer-Tool und das Paket, das Sie später importieren, um die Lösung in Ihrer Umgebung einzurichten.       |
|**Power BIVorlage**     | Enthält die Power BI-Berichtsvorlagendatei (.pbit), die Sie zur Konfiguration der Berichterstattung verwenden werden. Weitere Information: [Schritt 3: Das neueste Power BI-Dashboard veröffentlichen](#step-3-publish-the-latest-power-bi-dashboard)        |
|**SampleData**     |   Enthält die Beispielstammdatendateien (.xlsx), mit denen Sie Beispieldaten importieren können.       |

## <a name="step-2-install-the-upgrade-package"></a>Schritt 2: Das Upgrade-Bereitstellungspaket installieren

Installieren Sie das Upgrade-Paket in der **gleichen Umgebung**, in der Sie die vorhandene Lösung installiert haben. Sie können das Upgrade-Paket auf eine der folgenden drei Arten installieren, genau wie bei der Bereitstellung der Lösung für das **erstes Mal**.

- Microsoft AppSource (nur für Power Apps US Govt-Kunden). Siehe [Option A: Installieren der App über Microsoft AppSource (Kunden der US-Regierung)](deploy.md#option-a-install-the-app-from-microsoft-appsource-us-govt-customers) im Thema „Bereitstellung“

- Microsoft AppSource (für Power Apps Kunden der kommerziellen Version). Siehe [Option B: Installieren der App über Microsoft AppSource](deploy.md#option-b-install-the-app-from-microsoft-appsource) im Thema „Bereitstellung“

- Bereitstellungspaket, das Sie zuvor heruntergeladen haben. Siehe [Option C: Installieren der App über das Bereitstellungspaket](deploy.md#option-c-install-the-app-from-the-deployment-package) im Thema „Bereitstellung“

## <a name="step-3-publish-the-latest-power-bi-dashboard"></a>Schritt 3: Das neueste Power BI-Dashboard veröffentlichen

Verwenden Sie die .pbit-Datei im Upgrade-Paket, um das neueste Power BI-Dashboard zu konfigurieren und zu veröffentlichen. 

Die Schritte zur Verwendung der .pbit-Datei entsprechen denen der ursprünglichen Bereitstellung. Stellen Sie sicher, dass Sie denselben Arbeitsbereich verwenden, um das vorhandene Power BI-Dashboard zu überschreiben, wenn Sie die Power BI-Berichts-URL erhalten möchten, die zum Einbetten in das Power Apps-Portal verwendet wird. 

Weitere Information: [Schritt 5: Das neueste Power BI-Dashboard konfigurieren und veröffentlichen](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard)

## <a name="step-4-verify-the-power-bi-report-url-in-your-portal"></a>Schritt 4: Überprüfen der Power BI-Bericht-URL in Ihrem Portal

Dieser Schritt ist nur erforderlich, wenn Ihre Power BI-Berichts-URL sich im vorherigen Schritt geändert hat, da Sie das Dashboard in einem neuen Arbeitsbereich veröffentlicht haben. Verifizieren Sie die Websiteeinstellung **PowerBI-Pfad** in Ihrem Portal und aktualisieren Sie den Wert mit der neuesten Power BI-Berichts-URL.

Ausführliche Schritte finden Sie unter [Power BI-Bericht im Portal einbetten](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#the-process-1)

Stellen Sie sicher, dass Sie unser Portal neu starten, damit die Änderungen wirksam werden. Weitere Informationen: [Portal neu starten](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#restart-the-portal)

## <a name="step-5-verify-the-send-invitation-and-send-password-reset-to-contact-processes"></a>Schritt 5: Prozesse „Einladung senden“ und „Kennwortzurücksetzung an Kontakt senden“

Stellen Sie sicher, dass die Prozesse **Einladung senden** und **Kennwortzurücksetzung an Kontakt senden** noch gültig sind, d. h. sie haben ein Konto im Feld **Von**, das E-Mails senden kann, und der Rest der Details sind in Ordnung.

Ausführliche Informationen zum Beheben dieser Prozesse finden Sie unter:

-   [Schritt 10: Prozess „Einladung senden“ beheben](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-10-fix-the-send-invitation-process)

-   [Schritt 11: Prozess „Kennwortrücksetzung an Kontakt senden“ beheben](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-11-fix-the-send-password-reset-to-contact-process)

## <a name="step-6-verify-the-flow-supply-tracking-flow-is-enabled"></a>Schritt 6: Sicherstellen, dass der Flow der Versorgungsnachverfolgung aktiviert ist

Dieser Flow ermöglicht es dem Frontline-Benutzer, Verbrauchsmaterialien über das Portal hinzuzufügen, der in Common Data Service gespeichert wird.

Einzelheiten zum Beheben dieser Prozesse finden Sie unter [Schritt 13: Sicherstellen, dass der Flow der Versorgungsnachverfolgung aktiviert ist](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-13-verify-the-flow-supply-tracking-flow-is-enabled).

## <a name="step-7-verify-and-update-the-details-of-flows-for-sending-emails"></a>Schritt 7: Details der Flows zum Senden von E-Mails überprüfen und aktualisieren

In diesem Schritt werden wir Folgendes tun:

|Flowname|Änderungen|
|--|--|
|**Portalbenutzeranforderung: E-Mail an Administratoren bei Ablehnung der Anforderung senden**|Aktualisieren Sie die Verbindung, mit der eine Verbindung zu Common Data Service hergestellt wird, und legen Sie dann ein Benutzerkonto zum Senden von E-Mails fest.|
|**Portalbenutzeranforderung: E-Mail an Administratoren bei Erstellung der Anforderung senden**|Aktualisieren Sie die Verbindung, mit der eine Verbindung zu Common Data Service hergestellt wird, und legen Sie dann ein Benutzerkonto zum Senden von E-Mails fest. Aktualisieren Sie außerdem die Portal-URL im E-Mail-Text gemäß Ihrer Portal-URL.| 

Detaillierte Informationen hierzu finden Sie unter [Schritt 14: Details der Flows zum Senden von E-Mails aktualisieren](deploy.md#step-14-update-the-details-of-flows-for-sending-emails)

