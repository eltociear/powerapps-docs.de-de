---
title: Erstellen von Webrollen für ein Portal | MicrosoftDocs
description: Anweisungen zum Erstellen von Webrollen für ein Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3e8bb144ad338131cccd1be774e8c3f8000f510b
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552886"
---
# <a name="create-web-roles-for-portals"></a>Erstellen von Webrollen für Portale

Nachdem ein Kontakt für die Verwendung des Portals konfiguriert wurde, muss ihm eine oder mehrere Webrollen zugewiesen werden, um spezielle Aktionen auszuführen oder auf geschützte Inhalte im Portal zuzugreifen. Um z. b. auf eine eingeschränkte Seite zuzugreifen, muss der Kontakt einer Rolle zugewiesen werden, auf die der Lesevorgang für diese Seite beschränkt ist. Um neuen Inhalt zu veröffentlichen, muss der Kontakt in einer Rolle abgelegt werden, der Berechtigungen zum Veröffentlichen von Inhalten erteilt werden.

So erstellen Sie eine webrolle:

1. Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2. Wechseln Sie zu **Portale** > **Webrollen**.
    Alternativ dazu können Sie auch die Seite " **Webrollen** " im Bereich " [Freigeben](../manage-existing-portals.md#share) " öffnen. 

3. Wählen Sie **Neu** aus.

4. Geben Sie entsprechende Werte in die Felder ein.

5. Wählen Sie **Speichern**.

## <a name="attributes-and-relationships"></a>Attribute und Beziehungen

In der folgenden Tabelle werden die Webrollen Attribute erläutert, die von Portalen verwendet werden.

| Name                     | Beschreibung                                                                                                                                                                                                                                     |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                     | Der beschreibende Name der webrolle.                                                                                                                                                                                                            |
| Website                  | Die zugehörige Website                                                                                                                                                                                                                          |
| Beschreibung              | Eine Erläuterung des Zwecks der webrolle. Optional.                                                                                                                                                                                             |
| Rolle "authentifizierte Benutzer" | Booleschen. Wenn diese Einstellung auf "true" festgelegt ist, ist dies die Standardweb Rolle für authentifizierte Benutzer (siehe unten). Für eine bestimmte Website sollte nur eine webrolle vorhanden sein, bei der das Rollen Attribut authentifizierte Benutzer auf true festgelegt ist. Dies ist die Standardweb Rolle für authentifizierte Benutzer, denen keine webrolle zugewiesen wurde. |
| Rolle "anonyme Benutzer"     | Booleschen. Wenn diese Einstellung auf "true" festgelegt ist, ist dies die Standardweb Rolle für nicht authentifizierte Benutzer (siehe unten). Für eine bestimmte Website sollte nur eine webrolle vorhanden sein, bei der das Rollen Attribut anonyme Benutzer auf true festgelegt ist. Dies ist die Standardweb Rolle für nicht authentifizierte Benutzer. Die Rolle "anonyme Benutzer" berücksichtigt nur Entitäts Berechtigungen.| 
|| 

Nachdem die webrolle erstellt wurde, können Sie Sie so konfigurieren, dass Sie Ihren Anforderungen über verschiedene Berechtigungen, Regeln und Zuordnungen entspricht.

- **Optionale Standardweb Rolle für authentifizierte Benutzer**: durch Aktivieren der **Rolle "authentifizierte Benutzer**" wird Sie zur Standard webrolle für alle Benutzer. Diese Rolle wird häufig verwendet, um einen vordefinierten Zugriff für Benutzer bereitzustellen, die keiner anderen Rolle zugeordnet sind. Denken Sie daran, dass Benutzer mehrere Webrollen haben können, aber es kann nur eine webrolle für authentifizierte Benutzer für authentifizierte Benutzer vorhanden sein.
- **Optionale Standardweb Rolle für nicht authentifizierte Benutzer**: die **Rolle "anonyme Benutzer** " ist für die Verwendung mit Entitäts Berechtigungen vorgesehen. Andere Regeln oder Berechtigungen werden dabei nicht berücksichtigt. Durch Aktivieren der Rolle "anonyme Benutzer" wird Sie zur Standard webrolle für alle Benutzer. Für nicht authentifizierte Benutzer kann nur eine webrolle für anonyme Benutzer vorhanden sein.

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Portals](configure-portal.md) <br>
[Steuern des Webseiten Zugriffs für Portale](webpage-access-control.md)  
[Hinzufügen von Daten Satz basierter Sicherheit mithilfe von Entitäts Berechtigungen für Portale](assign-entity-permissions.md) <br>
