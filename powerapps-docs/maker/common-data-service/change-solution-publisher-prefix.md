---
title: Ändern des Präfix für den Lösungsherausgeber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/11/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: ece684h8-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
ms.openlocfilehash: 5881dd6742dd441d135768d3a96fd36dbef9e700
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39685746"
---
# <a name="change-the-solution-publisher-prefix"></a>Ändern des Präfix für den Lösungsherausgeber

Jede Anpassung, die Sie vornehmen, ist Teil einer Lösung. Jede Lösung hat es einen Herausgeber. Standardmäßig ist die Lösung, mit der Sie in PowerApps arbeiten werden, die **Standardlösung für Common Data Services**, die dem **CDS-Standardherausgeber** zugeordnet ist.

Das Standardpräfix für die Anpassung wird dem Herausgeber nach dem Zufallsprinzip zugewiesen, und könnte z.B. `cr8a3` sein. Dies bedeutet, dass dieser dem Name jedes neuen Metadatenelements, das für Ihre Organisation erstellt wird, vorangestellt wird, der zur eindeutigen Identifizierung der Elemente verwendet werden. Wenn Sie eine neue Entität mit dem Namen **Tier** erstellen, lautet der von CDS für Apps verwendete eindeutige Namen `cr8a3_animal`. Dasselbe gilt für alle neuen Felder (Attribute), Beziehungen oder Optionset-Optionen.

Wenn Sie Ihre Lösung nicht so verteilen, dass sie zusammen mit Metadatenelementen installiert wird, die für einen anderen Lösungsanbieter erstellt wurden, ist es nicht wichtig, wie das Präfix für die Anpassung lautet. Sie ist für die meisten Personen nicht sichtbar, die Ihren Apps verwenden. Aber es ist Entwicklern und anderen technische Mitarbeiter sichtbar, die beispielsweise Berichte erstellen. Es bietet eine schnelle Möglichkeit, zu verstehen, welche Lösung das Element hinzugefügt hat.

Aus diesem Grund ändern viele Benutzer gern das Präfix des Lösungsherausgebers, damit es aussagekräftiger wird, insbesondere bei der Anzeige von Metadatenelementen, die auch die aus anderen Lösungen importierten Elemente enthalten. 

> [!NOTE]
> Wenn Sie das Präfix des Lösungsherausgebers ändern, sollte dies vor dem Erstellen eines neuen Metadatenelements erfolgen. Sie können die Namen der Metadatenelemente nicht ändern.
> Wenn Sie den Präfixwert für die Anpassung ändern, stellen Sie sicher, dass Sie ins nächste Feld tippen. Das **Optionswertpräfix** generiert automatisch eine Zahl basierend auf dem Anpassungspräfix. Diese Nummer wird verwendet, wenn Sie Optionen zu Optionssets hinzufügen und gibt einen Hinweis darauf, welche Lösung zum Hinzufügen der Option verwendet wurde. 

## <a name="change-the-solution-publisher-prefix-for-the-cds-default-publisher"></a>Ändern des Präfix des Lösungsherausgebers für den CDS-Standardherausgeber  

 1. Wählen Sie im PowerApps-Portal **Modellgesteuert** unten links.
 2. Klicken Sie im linken Navigationsbereich auf **Erweitert**, um die **Common Data Services-Standardlösung** zu öffnen.
 3. Wählen Sie im Projektmappen-Explorer den Bereich **Informationen** im linken Navigationsbereich.
 4. Klicken Sie auf den Link **Verleger**, um das Formular **CDS-Standardverleger** zu öffnen.
 5. Bearbeiten Sie den Feldwert **Präfix** hinsichtlich des gewünschten Anpassungspräfix.
 6. Klicken Sie auf **Speichern und schließen**.
  
## <a name="change-the-solution-publisher-prefix-for-any-publisher"></a>Ändern des Präfix des Lösungsherausgebers für einen beliebigen Herausgeber

Benutzer, die ihre Lösungen verteilen, arbeiten in der Regel innerhalb einer von ihnen erstellten Lösung und nicht innerhalb der **Common Data Services-Standardlösung**. In der Regel wird das Anpassungspräfix festgelegt, wenn sie die Lösung erstellen. Sie können das Anpassungspräfix für eine andere nicht verwaltete Lösung, mit der Sie arbeiten, ändern, indem Sie diese Schritte ausführen: 

 1. Wählen Sie im PowerApps-Portal **Modellgesteuert** unten links.
 2. Klicken Sie im linken Navigationsbereich auf **Erweitert**, um die **Common Data Services-Standardlösung** zu öffnen.
 3. Bearbeiten Sie die URL der Seite, um alles nach `dynamics.com` zu entfernen und die Seite neu zu laden.
 4. Navigieren Sie zu **Einstellungen** > **Anpassung** > **Anpassungen**. 
 5. Klicken Sie auf **Verleger**. Sie sehen nun eine Liste der verfügbaren Verleger.
 6. Klicken Sie auf den Verleger, den Sie bearbeiten möchten, um das Formular für den Verleger zu öffnen.
 7. Bearbeiten Sie den Feldwert **Präfix** hinsichtlich des gewünschten Anpassungspräfix.
 6. Klicken Sie auf **Speichern und schließen**.
  