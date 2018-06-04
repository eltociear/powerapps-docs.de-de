---
title: Problembehandlung in Power Query | Microsoft-Dokumentation
description: Beheben Sie mithilfe von Power Query Probleme, um eine benutzerdefinierte Entität in Common Data Service (CDS) für Apps zu erstellen.
author: mllopis
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/16/2018
ms.author: millopis
ms.openlocfilehash: b89d7a59406d19759b84c34dbda84b98b10d5e58
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34445727"
---
# <a name="troubleshooting-power-query"></a>Problembehandlung in Power Query
Wenn Sie Power Query zum Erstellen einer benutzerdefinierten Entität verwenden, die Daten aus externen Quellen enthält, wird möglicherweise folgender Fehler angezeigt:

`Your Azure Active Directory administrator has set a policy that prevents you from using this feature. Please contact your administrator, who can grant permissions for this feature on your behalf.`

Der Fehler wird angezeigt, wenn Power Query nicht auf die Daten der Organisation in PowerApps oder Common Data Service für Apps (CDS) zugreifen kann. Diese Situation tritt in zwei Fällen auf:

* Ein AAD-Mandantenadministrator (Azure Active Directory) hat den Benutzern die Möglichkeit verweigert, den Zugriff von Apps auf Unternehmensdaten in ihrem Namen zu gestatten.
* Es wird ein nicht verwalteter Active Directory-Mandant verwendet. Ein nicht verwalteter Mandant ist ein Verzeichnis ohne globalen Administrator, das erstellt wurde, um ein Angebot mit Self-Service-Registrierung abzuschließen. Um dieses Problem zu beheben, muss für Benutzer zuerst die Konvertierung in einen verwalteten Mandanten ausgeführt werden. Anschließend muss einer der beiden Lösungsansätze für das Problem verfolgt werden, die im folgenden Abschnitt beschrieben werden.

Um dieses Problem zu beheben muss der Azure Active Directory-Administrator die Schritte für eines der Verfahren befolgen, die später in diesem Artikel aufgegriffen werden.

## <a name="allow-users-to-consent-to-apps-that-access-company-data"></a>Benutzern ermöglichen, Apps den Zugriff auf Unternehmensdaten zu gestatten
Diese Vorgehensweise ist womöglich einfacher als die nächste. Damit werden jedoch umfassendere Berechtigungen gewährt.

1. Öffnen Sie in [https://portal.azure.com](https://portal.azure.com) das Blatt **Azure Active Directory**, und wählen Sie **Benutzereinstellungen** aus.
2. Wählen Sie neben **Benutzer können Apps den Zugriff auf Unternehmensdaten in ihrem Namen gestatten** die Option **Ja** aus, und wählen Sie dann **Speichern** aus.

## <a name="allow-power-query-to-access-company-data"></a>Power Query den Zugriff auf Unternehmensdaten gestatten
Eine Alternative besteht darin, dass der Mandantenadministrator Power Query seine Zustimmung erteilt, ohne mandantenweite Berechtigungen zu ändern.

1. Installieren Sie [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps).
2. Führen Sie die folgenden PowerShell-Befehle aus:
   * Login-AzureRmAccount (und melden Sie sich als Mandantenadministrator an)
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128

Der Vorteil dieses Ansatzes (im Gegensatz zur mandantenweiten Lösung) besteht darin, dass dieser Ansatz sehr zielgerichtet ist. Dabei wird lediglich der **Power Query**-Dienstprinzipal bereitgestellt, für den Mandanten werden jedoch keine sonstigen Änderungen an Berechtigungen vorgenommen.

## <a name="updating-personal-data"></a>Aktualisieren von persönlichen Daten

Benutzer können Mashups und andere Informationen wie Abfragenamen und Mashup-Metadaten über den Abfrage-Editor und das Dialogfeld `Options`, auf das über den Abfrage-Editor zugegriffen werden kann, aktualisieren.

In PowerApps erreichen Sie den Abfrage-Editor über den Bereich „Daten“. Erweitern Sie diesen, und klicken Sie dann auf das Menüelement des Bereichs „Entitäten“. Sobald dies geöffnet wird, klicken Sie auf das Menü mit den Auslassungspunkten „...“, und wählen Sie „Abfragen bearbeiten“ aus. Klicken Sie anschließend auf die `Options`-Schaltfläche auf dem Menüband und dann auf die Schaltfläche `Export Diagnostics`.


## <a name="deleting-personal-data"></a>Löschen von persönlichen Daten

Der Großteil der Daten wird automatisch innerhalb von 30 Tagen gelöscht. Dies gilt nicht für Daten und Metadaten um Mashups: Der Benutzer muss alle Mashups über PowerApps entfernen. Alle zugeordneten Daten und Metadaten werden innerhalb von 30 Tagen gelöscht.

Mashups können durch Entfernen der Datenintegratorprojekte aus PowerApps entfernt werden. Diese Projekte können von der Namensregisterkarte entfernt werden, indem Sie auf die Schaltfläche „...“ klicken und die Option `Delete` auswählen.

Wenn Sie einen Mashup über das Feature „Neue Entitäten aus Daten (Technische Vorschau)“ erstellt haben, können Sie ihn entfernen, indem Sie auf die Schaltfläche „...“ klicken, „Abfragen bearbeiten“ auswählen und anschließend auf dem Menüband „Optionen“ auswählen. Klicken Sie schließlich auf die Schaltfläche „Alle Abfragen entfernen“. Sobald Sie bestätigen, dass Sie Ihre Abfragen löschen möchten, werden diese gelöscht.


## <a name="exporting-personal-data"></a>Exportieren von persönlichen Daten

Benutzer können den Abfrage-Editor öffnen und dann auf die `Options`-Schaltfläche auf dem Menüband und anschließend auf die Schaltfläche `Export Diagnostics` klicken.

In PowerApps erreichen Sie den Abfrage-Editor über den Bereich „Daten“. Erweitern Sie diesen, und klicken Sie dann auf das Menüelement des Bereichs „Entitäten“. Sobald dies geöffnet wird, klicken Sie auf das Menü mit den Auslassungspunkten „...“, und wählen Sie „Abfragen bearbeiten“ aus. Klicken Sie anschließend auf die `Options`-Schaltfläche auf dem Menüband und dann auf die Schaltfläche `Export Diagnostics`.

Der Zugriff auf vom System generierte Protokolle bezüglich Benutzeraktionen auf der Benutzeroberfläche kann über das Azure-Portal erfolgen.


