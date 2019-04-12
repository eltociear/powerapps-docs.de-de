---
title: So ändern Sie das Lösungsherausgeberpräfix | MicrosoftDocs
ms.custom: ''
ms.date: 05/11/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="change-the-solution-publisher-prefix"></a>Ändern des Lösungsherausgeberpräfix

Alle Anpassungen, die Sie vornehmen, ist Teil einer Lösung. Jede Lösung hat einen Herausgeber. Standardmäßig wird die Lösung, mit der Sie in PowerApps arbeiten, die **Common Data Services-Standardlösung** sein, die dem **Common Data Service-Standardherausgeber** zugeordnet ist.

Das Standardanpassungspräfix wird zufällig für diesen Herausgeber zugewiesen, und ist beispielsweise`cr8a3`. Das bedeutet, dass der Name jedes neuen Artikels der Metadaten, die für die Organisation erstellt wurden, diese Endung im Namen hat, um die Elemente eindeutig zu identifizieren. Wenn Sie eine neue Entität **Tier** erstellen, lautet der eindeutige Name, der von Common Data Service verwendet wird `cr8a3_animal`. Dasselbe gilt für alle neuen Felder (Attribute), Beziehungen oder optionset Optionen.

Ausgenommen Sie werden die Lösung verteilen, so dass sie zusammen mit Metadatenelementen installiert wird, die für einen anderen Lösungsherausgeber erstellt wurden, ist es nicht wichtig, wie der Anpassungspräfix lautet. Es ist für die meisten Benutzer nicht sichtbar, die Ihre Apps verwenden. Aber er ist für Entwickler und andere technische Personen verfügbar, die beispielsweise Berichte erstellen. Damit kann schnell nachvollzogen werden, welche Lösung dem Element hinzugefügt wurde.

Aus diesem Grund werden viele Benutzer das Lösungsherausgeberpräfix ändern, sodass es mehr aussagt, besonders wenn Metadatenelemente angezeigt werden, die auch diese wichtigen Informationen von anderen Lösungen enthalten. 

> [!NOTE]
> Wenn Sie das Lösungsherausgeberpräfix ändern, sollten Sie diese Schritte ausführen, bevor Sie neue Metadatenelemente erstellen. Sie können die Namen von Metadaten-Elementen ändern.
> Wenn Sie den Wert ändern, gehen Sie zum nächsten Feld weiter. Die Option **Wert Präfix** generiert automatisch eine Nummer auf der Grundlage des Anpassungspräfixes. Diese Nummer wird verwendet, wenn Sie Optionen zu Optionssätzen hinzufügen, und zeigt an, welche Lösung zum Hinzufügen der Option verwendet wurde. 

## <a name="change-the-solution-publisher-prefix-for-the-common-data-service-default-publisher"></a>Ändern Sie das Lösungsherausgeberpräfix für den Common Data Service-Standardherausgeber  

 1. Im PowerApps-Portal wählen Sie **Modell-angetrieben** in der unteren linken Ecke.
 2. Klicken Sie auf **Erweitert** in der linken Navigation, um **Allgemeine Datendienst-Standardlösung** zu öffnen
 3. Klicken Sie im Lösungsexplorer und wählen Sie **Informationen** im linken Navigationsbereich aus.
 4. Klicken Sie auf den Link **Herausgeber**, um das Formular **Common Data Service-Standardherausgeber** zu öffnen.
 5. Bearbeiten Sie den **Präfix** Feldwer zum Anpassungspräfix, den Sie verwenden möchten.
 6. Klicken Sie auf **Speichern und schließen**.
  
## <a name="change-the-solution-publisher-prefix-for-any-publisher"></a>So ändern Sie das Lösungsherausgeberpräfix für einen Herausgeber

Personen, die Ihre Lösungen verteilen, arbeiten in der Regel in einer Lösung, die sie erstellen und weniger die **Common Data Services Standardlösung**. Der Anpassungspräfix wird in der Regel festgelegt, wenn sie die Lösung erstellen. Sie können das Anpassungspräfix für eine andere nicht verwaltete Lösung ändern, mit der Sie Arbeiten mit folgenden Schritten: 

 1. Im PowerApps-Portal wählen Sie **Modell-angetrieben** in der unteren linken Ecke.
 2. Klicken Sie auf **Erweitert** in der linken Navigation, um **Allgemeine Datendienst-Standardlösung** zu öffnen
 3. Bearbeiten Sie die URL der Seite, um alles nach zu `dynamics.com` entfernen und laden Sie die Seite erneut.
 4. Navigieren Sie auf **Einstellungen** > **Anpassung** > **Anpassungen**. 
 5. Klicken Sie auf **Veröffentlichen**. Sie können eine Liste der verfügbaren Herausgeber sehen.
 6. Doppelklicken Sie in der Liste auf das entsprechende Feld, um das zu bearbeitende Formular zu öffnen.
 7. Bearbeiten Sie den **Präfix** Feldwer zum Anpassungspräfix, den Sie verwenden möchten.
 6. Klicken Sie auf **Speichern und schließen**.
  
