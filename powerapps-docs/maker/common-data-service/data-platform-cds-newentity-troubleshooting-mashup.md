---
title: Problembehandlung in Power Query | Microsoft-Dokumentation
description: Beheben Sie mithilfe von Power Query Probleme, um eine benutzerdefinierte Entität in Common Data Service für Apps zu erstellen.
services: ''
suite: powerapps
documentationcenter: na
author: mllopis
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/18/2017
ms.author: millopis
ms.openlocfilehash: dafed76565a4bd3fb3e2822319d344f49376b4fc
ms.sourcegitcommit: d7ed5144f96d1ecc17084c30ed0e2ba3c6b03c26
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="troubleshooting-power-query"></a>Problembehandlung in Power Query
Wenn Sie Power Query zum Erstellen einer benutzerdefinierten Entität verwenden, die Daten aus externen Quellen enthält, wird möglicherweise folgender Fehler angezeigt:

`Your Azure Active Directory administrator has set a policy that prevents you from using this feature. Please contact your administrator, who can grant permissions for this feature on your behalf.`

Der Fehler wird angezeigt, wenn Power Query nicht auf die Daten der Organisation in PowerApps oder Common Data Service zugreifen kann. Diese Situation tritt in zwei Fällen auf:

* Ein AAD-Mandantenadministrator (Azure Active Directory) hat den Benutzern die Möglichkeit verweigert, den Zugriff von Apps auf Unternehmensdaten in ihrem Namen zu gestatten.
* Es wird ein nicht verwalteter Active Directory-Mandant verwendet. Ein nicht verwalteter Mandant ist ein Verzeichnis ohne globalen Administrator, das erstellt wurde, um ein Angebot mit Self-Service-Registrierung abzuschließen. Um dieses Problem zu beheben, muss für Benutzer zuerst die Konvertierung in einen verwalteten Mandanten ausgeführt werden. Anschließend muss einer der beiden Lösungsansätze für das Problem verfolgt werden, die im folgenden Abschnitt beschrieben werden.

Um dieses Problem zu beheben muss der AAD-Administrator die Schritte für eines der Verfahren, die später in diesem Artikel aufgegriffen werden, befolgen.

## <a name="allow-users-to-consent-to-apps-that-access-company-data"></a>Benutzern ermöglichen, Apps den Zugriff auf Unternehmensdaten zu gestatten
Diese Vorgehensweise ist womöglich einfacher als die nächste. Damit werden jedoch umfassendere Berechtigungen gewährt.

1. Öffnen Sie in [https://portal.azure.com](https://portal.azure.com) das Blatt **Azure Active Directory**, und wählen Sie **Benutzereinstellungen** aus.
1. Wählen Sie neben **Benutzer können Apps den Zugriff auf Unternehmensdaten in ihrem Namen gestatten** die Option **Ja** aus, und wählen Sie dann **Speichern** aus.

## <a name="allow-power-query-to-access-company-data"></a>Power Query den Zugriff auf Unternehmensdaten gestatten
Eine Alternative besteht darin, dass der Mandantenadministrator Power Query seine Zustimmung erteilt, ohne mandantenweite Berechtigungen zu ändern.

1. Installieren Sie [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps).
2. Führen Sie die folgenden PowerShell-Befehle aus:
   * Login-AzureRmAccount (und melden Sie sich als Mandantenadministrator an)
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128

Der Vorteil dieses Ansatzes (im Gegensatz zur mandantenweiten Lösung) besteht darin, dass dieser Ansatz sehr zielgerichtet ist. Dabei wird lediglich der **Power Query**-Dienstprinzipal bereitgestellt, für den Mandanten werden jedoch keine sonstigen Änderungen an Berechtigungen vorgenommen.

