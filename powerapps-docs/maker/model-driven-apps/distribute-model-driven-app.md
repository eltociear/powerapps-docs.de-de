---
title: Verteilen einer modellgesteuerten Anwendung mit einer Lösung | MicrosoftDocs
description: 'Erfahren Sie, wie Sie eine modellgesteuerte Anwendung mit Hilfe von Lösungen verteilen.'
keywords: ''
ms.date: 08/06/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: e82e7f64-37ad-41e5-acd7-16309881c6a2
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 9
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="distribute-a-model-driven-app-using-a-solution"></a>Verteilen einer modellgesteuerten Anwendung mit einer Lösung

Modellgesteuerte Apps werden als Lösungskomponenten verteilt. Nachdem Sie eine modellgesteuerte App erstellt haben, können Sie diese für andere Umgebungen zur Verwendung verfügbar machen, indem Sie die App in eine Lösung verpacken und dann in eine ZIP-Datei exportieren. Wenn die Lösung (ZIP-Datei) erfolgreich in die Zielumgebung importiert wurde, kann die verpackte App verwendet werden. 
  
## <a name="add-an-app-to-a-solution"></a>Eine App zu einer Lösung hinzufügen
Um Ihre App zu verteilen, erstellen Sie eine Lösung, damit die Anwendung für den Export verpackt werden kann.

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

2. Wählen Sie **Lösungen** und dann **Neue Lösung** aus.
3. Füllen Sie die Felder auf der Seite **Neue Lösung** aus und wählen Sie dann **Speichern**. Weitere Informationen: [Erstellen einer Lösung](../common-data-service/create-solution.md)
4. Die Seite **Lösung** wird angezeigt. Wählen Sie **Vorhandenes Element hinzufügen**, wählen Sie **App**, wählen Sie die App, die Sie der Lösung hinzufügen möchten, und wählen Sie dann **OK**. 

    ![Lösungskomponenten auswählen](media/select-solution-components.png)

5. Wenn eine Seite **Fehlende erforderliche Komponenten** erscheint, empfehlen wir, dass Sie **Ja, erforderliche Komponenten einschließen** wählen und die erforderlichen Komponenten wie Entitäten, Ansichten, Formulare, Diagramme und Sitemap, die Teil der App sind, hinzufügen. Wählen Sie **OK** aus.
6. Wählen Sie auf der Seite **Lösung** **Speichern und Schließen** aus.

## <a name="export-a-solution"></a>Exportieren einer Lösung
Um Ihre Anwendung so zu verteilen, dass sie in eine andere Umgebung importiert oder auf [Microsoft AppSource](https://appsource.microsoft.com/) zur Verfügung gestellt werden kann, exportieren Sie die Lösung in eine Zip-Datei. Anschließend kann die ZIP-Datei, die die Anwendung und die Komponenten enthält, in andere Umgebungen importiert werden.

1. Öffnen Sie die [Lösungsseite](advanced-navigation.md#solutions). 
2. Wählen Sie die zu exportierende Lösung aus und wählen Sie in der Symbolleiste **Exportieren**. 
3. Auf der Seite **Anpassungen veröffentlichen** wählen Sie **Weiter**.
4. Wenn die Seite **Fehlende erforderliche Komponenten** erscheint, wählen Sie **Weiter**. 
5. Wählen Sie auf der Seite **Systemeinstellungen exportieren** die optionalen Funktionen aus, die Sie einbinden möchten, und wählen Sie dann **Weiter**. 
6. Auf der Seite **Pakettyp** wählen Sie **Nicht verwaltet** oder **Verwaltet** und dann **Exportieren**. Weitere Informationen zu Lösungspakettypen finden Sie unter [Lösungsübersicht](../common-data-service/solutions-overview.md).
7. Abhängig von Ihrem Browser und Ihren Einstellungen wird eine.zip-Paketdatei erstellt und in den Standarddownload-Ordner kopiert. Der Dateiname des Pakets basiert auf dem eindeutigen Namen der mit Unterstrichen versehenen Lösung und der Versionsnummer der Lösung.

    > [!NOTE]
    > Wenn Sie eine App mittels einer Lösung exportieren, wird die App URL nicht exportiert.
  
## <a name="import-a-solution"></a>Importieren einer Lösung  
Wenn Sie eine Lösungs-ZIP-Datei erhalten, die die App enthält, die Sie importieren möchten, öffnen Sie die Lösungskomponentenseite und importieren Sie die Lösung. Wenn die Lösung erfolgreich importiert wurde, kann die App in Ihrer Umgebung verwendet werden.

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

2. Wählen Sie **Lösungen** und dann in der Symbolleiste **Importieren**.
3. Wählen Sie die Datei aus, die Sie importieren möchten, und klicken Sie dann auf **Weiter**.
4. Klicken Sie auf **Importieren**.

## <a name="see-also"></a>Siehe auch
[Ändern des Lösungsherausgeberpräfix](../common-data-service/change-solution-publisher-prefix.md)
