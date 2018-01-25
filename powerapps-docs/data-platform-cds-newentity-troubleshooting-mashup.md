---
title: "Problembehandlung – Ein Mashup für diese Datenbank kann nicht erstellt oder abgerufen werden | Microsoft-Dokumentation"
description: "Beheben Sie Probleme beim Erstellen einer benutzerdefinierten Entität mithilfe von CDS und Power Query, indem Sie mit Administratorrechten Änderungen an AAD-Einschränkungen vornehmen."
services: 
suite: powerapps
documentationcenter: na
author: mllopis
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/18/2017
ms.author: millopis
ms.openlocfilehash: b534400317e39dffec30f185c180de34098a378f
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="troubleshooting---unable-to-create-or-retrieve-a-mashup-for-this-database"></a>Problembehandlung – Ein Mashup für diese Datenbank kann nicht erstellt oder abgerufen werden
Bei Verwendung der Funktion **Neue Entitäten aus Daten (Technische Vorschau)** kann ein Fehler wie der Folgende auftreten:

    *Unable to create or retrieve a mashup for the current database*

Dies kann der Fall sein, wenn Sie die Funktion zum Erstellen von *benutzerdefinierten Entitäten* im **Common Data Service (CDS)** mit Daten aus externen Datenquellen unter Verwendung von **Power Query** verwenden. Der Fehler wird ausgelöst, wenn **Power Query** nicht auf die Daten der Organisation in **PowerApps oder CDS** zugreifen kann. Es gibt zwei Szenarien, in denen dies der Fall sein kann:

* Ein AAD-Mandantenadministrator (**Azure Active Directory**) hat den Benutzern die Möglichkeit verweigert, den Zugriff von Apps auf Unternehmensdaten in ihrem Namen zu gestatten.
* Es wird ein nicht verwalteter Active Directory-Mandant verwendet. Ein nicht verwalteter Mandant ist ein Verzeichnis ohne globalen Administrator, das erstellt wurde, um ein Angebot mit Self-Service-Registrierung abzuschließen. Um dieses Problem zu beheben, muss für Benutzer *zuerst* die Konvertierung in einen verwalteten Mandanten ausgeführt werden, anschließend muss einer der beiden Lösungsansätze für das Problem verfolgt werden, die im folgenden Abschnitt beschrieben werden.

Es gibt zwei Möglichkeiten, das oben beschriebene Problem zu beheben:

* Der AAD-Administrator führt die erforderlichen Schritte aus, mit denen Benutzern ermöglicht wird, Apps den Zugriff auf Unternehmensdaten zu gestatten.
* Der AAD-Administrator gestattet **Power Query** den Zugriff auf Daten.

Die erforderlichen Schritte für diese Lösungen werden im Folgenden beschrieben.

## <a name="allowing-users-to-give-apps-consent-to-access-company-data"></a>Benutzern ermöglichen, Apps den Zugriff auf Unternehmensdaten zu gestatten

Sie können den AAD-Mandantenadministrator bitten, die folgenden Schritte auszuführen, um Benutzern zu ermöglichen, beliebigen Apps den Zugriff auf Unternehmensdaten zu gestatten:

1. Besuchen Sie [https://portal.azure.com](https://portal.azure.com).
2. Öffnen Sie das Blatt **Azure Active Directory**.
3. Wählen Sie **Benutzereinstellungen** aus.
4. Wählen Sie neben **Benutzer können Apps den Zugriff auf Unternehmensdaten in ihrem Namen gestatten** die Option **Ja** aus, und wählen Sie dann **Speichern** aus.
5. Nach Abschluss dieses Vorgangs ist das Problem behoben.

Dies ist möglicherweise die einfachste Vorgehensweise, damit werden jedoch umfassendere Berechtigungen als mit der nächsten Option gewährt.

## <a name="allowing-power-query-to-access-company-data"></a>Power Query den Zugriff auf Unternehmensdaten gestatten
Eine andere Lösung besteht darin, dass der Mandantenadministrator **Power Query** seine Zustimmung erteilt, ohne mandantenweite Berechtigungen zu ändern. Lassen Sie den Mandantenadministrator hierzu die folgenden Schritte ausführen:

1. Installieren von [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps)
2. Führen Sie die folgenden PowerShell-Befehle aus:
   * Login-AzureRmAccount (und melden Sie sich als Mandantenadministrator an)
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128

Der Vorteil dieses Ansatzes (im Gegensatz zur mandantenweiten Lösung) besteht darin, dass dieser Ansatz sehr zielgerichtet ist. Dabei wird lediglich der **Power Query**-Dienstprinzipal bereitgestellt, für den Mandanten werden jedoch keine sonstigen Änderungen an Berechtigungen vorgenommen.

