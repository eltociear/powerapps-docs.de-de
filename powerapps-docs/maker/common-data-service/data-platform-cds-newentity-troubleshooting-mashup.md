---
title: Fehlerbehebung bei Power Query | Microsoft Docs
description: Beheben Sie Probleme mit Power Query, um eine benutzerdefinierte Entität in Common Data Service zu erstellen.
author: mllopis
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/16/2018
ms.author: millopis
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9b1f0152782a31b13d6209fe3911ed10792652af
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2864254"
---
# <a name="troubleshoot-power-query"></a>Probleme mit Power Query beheben
Wenn Sie Power Query for Excel verwenden, um eine benutzerdefinierte Entität zu erstellen, die Daten aus externen Quellen enthält, wird möglicherweise dieser Fehler angezeigt:

>"Ihr Azure Active Directory-Administrator hat eine Richtlinie festgelegt, die verhindert, dass Sie diese Funktionen verwenden. Wenden Sie sich an Ihren Administrator, der Berechtigungen für diese Funktionalität in Ihrem Auftrag gewähren kann."

Dieser Fehler wird angezeigt, wenn Power Query nicht auf die Daten der Organisation in Power Apps oder Common Data Service zugreifen kann. Diese Situation entsteht unter zwei Umständen:

* Ein Azure Active Directory (Azure AD)-Mandantenadministrator hat die Möglichkeit der Benutzer Apps zuzustimmen, die in deren Namen auf Unternehmensdaten zugreifen, nicht zugelassen.
* Verwenden eines nicht verwalteten Active Directory-Mandanten. Ein nicht verwalteter Mandanten ist ein Verzeichnis ohne einen globalen Administrator, der erstellt wurde, um ein Self-Service-Verpflichtungsangebot abzuschließen. Um dieses Szenario zu beheben, müssen Benutzer zunächst in eine verwaltetes Mandat konvertieren und dann eine von zwei Lösungen für dieses Problem befolgen. Die Lösungen finden Sie im nächsten Abschnitt.

Um dieses Problem zu beheben, muss der Azure Active Directory-Administrator eine der Vorgehensweisen befolgen, die weiter unten in diesem Artikel präsentiert werden.

## <a name="allow-users-to-consent-to-apps-that-access-company-data"></a>Zulassen, dass Benutzer Apps zuzustimmen, die auf Unternehmensdaten zugreifen
Diese Methode ist ggf. einfacher als die nächste, aber sie ermöglicht breite Berechtigungen.

1. Öffnen Sie im [Azure-Portal](https://portal.azure.com) den Bereich **Azure Active Directory**, und wählen Sie dann **Benutzereinstellungen** aus.
2. Wählen Sie neben **Benutzer können Apps zustimmen, in ihrem Namen auf Unternehmensdaten zuzugreifen** die Option **Ja** und anschließend **Speichern** aus.

## <a name="allow-power-query-to-access-company-data"></a>Zulassen, dass Power Query auf Unternehmensdaten zugreift
Alternativ kann der Mandantenadministrator Power Query zulassen, ohne mandantenweite Berechtigungen zu ändern.

1. Installieren Sie [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps).
2. Führen Sie die folgenden PowerShell-Befehle aus:
   * Login-AzureRmAccount (und melden Sie sich als Mandantenadministrator an)
   * Neu-AzureRmADServicePrincipal - ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128

Der Vorteil bei dieser Methode (im Gegensatz zur mandantenweiten Lösung) ist, dass diese Lösung gezielt ist. Er stellt nur das **Power Query**-Dienstprinzipal bereit, aber es werden keine anderen Berechtigungsänderungen am Mandanten vorgenommen.

## <a name="update-personal-data"></a>Personendaten aktualisieren

Benutzer können Mashups und andere Informationen (z. B. Abfragenamen und Mashup-Metadaten) über den Abfrage-Editor und über das Dialogfeld **Optionen** aktualisieren, auf das aus dem Abfrage-Editor heraus zugegriffen werden kann.

In Power Apps greifen Sie auf den Abfrage-Editor zu, indem Sie folgende Schritte ausführen:
1. Wechseln Sie zum Bereich **Daten**, erweitern Sie ihn und wählen Sie dann **Entitäten** aus. 
2. Wählen Sie die Ellipse (...) aus, und wählen Sie dann **Abfragen bearbeiten** aus.
3. Wählen Sie im Menüband die Schaltfläche **Optionen** und dann die Schaltfläche **Diagnose exportieren** aus.


## <a name="delete-personal-data"></a>Personendaten löschen

Die meisten Daten werden innerhalb von 30 Tagen automatisch gelöscht. Für Daten und Metadaten zu Mashups müssen Benutzer alle ihre Mashups über Power Apps entfernen. Alle zugeordneten Daten und Metadaten werden innerhalb von 30 Tagen entfernt.

So entfernen Sie Mashups aus Power Apps:
1. Entfernen Sie den Data Integrator-Projekte, die aus der Registerkarte "namesake" entfernt werden können.
2. Wählen Sie die Auslassungspunkte (...) aus, und wählen Sie dann die Option **Löschen** aus.

Wenn Sie ein Mashup über die Funktion"Neue Entitäten aus Daten (Technische Vorschau)" erstellt haben, können Sie sie entfernen, indem Sie folgende Schritte ausführen:
1. Wählen Sie die Ellipse (...) aus, und wählen Sie dann **Abfragen bearbeiten** aus.
2. Wählen Sie im Menüband die Schaltfläche **Optionen** aus.
3. Wählen Sie die Schaltfläche **Alle Abfragen entfernen** aus.  
    Nachdem Sie bestätigen, dass Sie Ihre Abfragen löschen möchten, werden sie gelöscht.

## <a name="export-personal-data"></a>Persönliche Daten exportieren

Zum Exportieren persönlicher Daten können Benutzer folgende Schritte ausführen:
1. Öffnen Sie den Abfrage-Editor.
2. Wählen Sie im Menüband die Schaltfläche **Optionen** aus.
3. Wählen Sie die Schaltfläche **Diagnose exportieren** aus.

In Power Apps können Sie auf den Abfrage-Editor zugreifen, indem Sie folgende Schritte ausführen:
1. Wechseln Sie zum Bereich **Daten**, erweitern Sie ihn und wählen Sie dann **Entitäten** aus.
2. Wählen Sie die Ellipse (...) aus, und wählen Sie dann **Abfragen bearbeiten** aus. 
3. Wählen Sie im Menüband die Schaltfläche **Optionen** und dann die Schaltfläche **Diagnose exportieren** aus.

Sie können im Azure-Portal auf die vom System generierten Protokolle zu Benutzeraktionen auf der Benutzeroberfläche (UI) zugreifen.



