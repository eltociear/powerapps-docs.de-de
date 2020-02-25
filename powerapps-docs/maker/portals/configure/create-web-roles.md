---
title: Erstellen von Webrollen für ein Portal | MicrosoftDocs
description: Anweisungen zum Erstellen von Webrollen für ein Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: ccaf34d6ea0789ae1216ab5a240d85e58f701e41
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977795"
---
# <a name="create-web-roles-for-portals"></a>Internet-Rollen für Portale erstellen

Nachdem ein Kontakt konfiguriert wurde, der das Portal verwenden soll, muss ihm eine oder mehrere Webrollen zugewiesen werden, um allfällige Sonderaktionen vorzunehmen oder auf geschützte Portalinhalte zuzugreifen. Wenn Sie beispielsweise auf eine eingeschränkte Seite zugreifen, muss dem Kontakt für die Seite, für die der Zugriff eingeschränkt ist, eine Rolle zugewiesen werden. Wenn Sie neue Inhalte zu veröffentlichen, muss dem Kontakt eine Rolle zugewiesen werden, die über Veröffentlichungsberechtigungen verfügt.

Um einen neue Internetrolle zu erstellen:

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Gehen Sie zu **Portale** > **Webrollen**.
    Als Alternative können Sie auch im Bereich **Webrollen** die Seite des Bereichs [Freigeben](../manage-existing-portals.md#share) öffnen. 

3. Wählen Sie **Neu** aus.

4. Hinzufügen der entsprechenden Werte zu den Feldern.

5. Wählen Sie **Speichern** aus.

## <a name="attributes-and-relationships"></a>Attribute und Beziehungen

Die Tabelle unten erklärt die Attribute für Webrollen, die von Portalen verwendet werden.

| Name                     | Beschreibung                                                                                                                                                                                                                                     |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                     | Der beschreibende Name der Internetrolle                                                                                                                                                                                                            |
| Website                  | Die zugeordnete Website                                                                                                                                                                                                                          |
| Beschreibung              | Eine Erklärung zum Zwecke der Internetrolle. (Optional).                                                                                                                                                                                             |
| Authentifizierte Benutzerrolle | Boolescher Wert Wenn der Wert auf "True" festgelegt ist, ist dies die standardmäßige Internetrolle für authentifizierte Benutzer (siehe unten). Es sollte nur eine Internet-Rolle mit dem authentifizierten Benutzerrollenattribute mit dem Wert "True" für eine bestimmte Website vorhanden sein. Dies ist die standardmäßige Internetrolle für authentifizierte Benutzer, denen keine Internet-Rolle zugewiesen wurde. |
| Anonyme Benutzerrolle     | Boolescher Wert Wenn der Wert auf "True" festgelegt ist, ist dies die standardmäßige Internetrolle für nicht authentifizierte Benutzer (siehe unten). Es sollte nur eine Internet-Rolle mit dem Benutzerrollenattribute "Anonym" mit dem Wert "True" für eine bestimmte Website vorhanden sein. Dies ist die standardmäßige Internetrolle für nicht authentifizierte Benutzer. Die anonyme Benutzer-Rolle respektiert nur Entitätsberechtigungen.| 
|| 

Nachdem die Internet-Rolle erstellt wurde, sind Sie in der Lage, diese so konfigurieren, dass sie Ihre Anforderungen über verschiedene Regeln, Berechtigungen und Zuordnungen erfüllt.

- **Optionale Standardwebrolle für authentifizierte Benutzer**: Durch Aktivierung der **Authentifizierte Benutzerrolle** wird dieser zur Standardwebrolle für alle Benutzer. Diese Rolle wird allgemein verwendet, um Benutzern, die keinen anderen Rollen zugeordnet sind, vordefinierte Zugriffsrechte zu gewähren. Beachten Sie, dass Benutzer mehrere Internetrollen haben können, aber es gibt nur eine authentifizierte Benutzer-Internetrolle für authentifizierte Benutzer.
- **Optionale standardmäßige Internetrolle für nicht authentifizierte Benutzer**: Die **Anonyme Benutzerrolle** soll mit Entitäts-Berechtigungen verwendet werden. Sie respektiert keine anderen Regeln oder Berechtigungen. Durch die Aktivierung der Rolle "Anonyme Benutzerrolle" wird sie zur standardmäßigen Internetrolle für alle Benutzer. Es gibt nur eine Anonyme Internet-Benutzerrolle für nicht authentifizierte Benutzer.

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md) <br>
[Steuern des Webseitenzugriffs für Portale](webpage-access-control.md)  
[Hinzufügen von datensatzbasierter Sicherheit durch Verwendung von Entitätsberechtigungen für Portale](assign-entity-permissions.md) <br>
