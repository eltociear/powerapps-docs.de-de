---
title: Portalfehlerprotokolle anzeigen und in Azure Blob Storage speichern | MicrosoftDocs
description: Erfahren Sie, wie Sie Portalfehlerprotokolle anzeigen und sie in Ihrem Azure Blob Storage-Konto speichern.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7989c15b0c5c4cf50d4b55f518244758afc067e1
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756650"
---
# <a name="view-portal-error-logs"></a>Portalfehlerprotokolle anzeigen

Als Portaladministrator oder -entwickler können Sie mit PowerApps-Portalen eine Website für Ihre Kunden erstellen. Eine allgemeine Aufgabe für einen Entwickler besteht darin, Probleme zu debuggen, während das Portal entwickelt wird. Zur Unterstützung beim Debuggen, können Sie auf detaillierte Fehlerprotokolle für jegliche Probleme auf Ihrem Portal zugreifen. Es gibt mehrere Möglichkeiten, wie Sie Fehlerprotokolle für Ihre Portale abrufen können.

## <a name="custom-error"></a>Benutzerdefinierter Fehler

Wenn irgendeine serverseitige Ausnahme in Ihrem Portal auftritt, wird standardmäßig eine benutzerdefinierte Seite mit einer benutzerfreundlichen Fehlermeldung angezeigt. Um die Fehlermeldung zu konfigurieren, finden Sie hier Informationen: [Eine benutzerdefinierte Fehlermeldung anzeigen](#display-a-custom-error-message).

Es ist jedoch besser, die detaillierte Fehlerseite von ASP.NET für Debugzwecke anzuzeigen, auch bekannt als „Gelber Bildschirm des Todes” (Yellow Screen of Death = YSOD). Die ausführliche Fehlerseite hilft Ihnen dabei, den vollständigen Stapel von Serverfehlern abzurufen.

> [!div class=mx-imgBorder]
> ![Gelber Bildschirm des Todes](../media/ysod.png "Gelber Bildschirm des Todes")

Um den YSOD zu aktivieren, müssen Sie auf Ihrem Portal [benutzerdefinierte Fehler deaktivieren](#disable-custom-error).

> [!NOTE]
> Es ist ratsam, benutzerdefinierte Fehler nur zu deaktivieren, wenn Sie sich in der Entwicklungsphase befinden und benutzerdefinierte Fehler zu aktivieren, sobald sie live schalten.

Weitere Informationen zu benutzerdefiniertem Fehler: [Eine benutzerdefinierte Fehlerseite anzeigen](https://docs.microsoft.com/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### <a name="disable-custom-error"></a>Benutzerdefinierten Fehler deaktivieren

Sie können benutzerdefinierte Fehler für Portale deaktivieren, um die detaillierte Ausnahmemeldung anzuzeigen, wenn irgendeine serverseitige Ausnahme in Ihrem Portal auftritt.

1. Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2. Wechseln Sie zu **Portalaktionen** > **Benutzerdefinierte Fehler deaktivieren**.

   > [!div class=mx-imgBorder]
   > ![Benutzerdefinierten Fehler deaktivieren](../media/disable-custom-errors.png "Benutzerdefinierten Fehler deaktivieren")

3. Wählen Sie in der Bestätigungsmeldung **Deaktivieren** aus. Während benutzerdefinierte Fehler deaktiviert werden, startet das Portal neu und wird nicht verfügbar sein. Eine Meldung wird angezeigt, wenn benutzerdefinierte Fehler deaktiviert werden.

### <a name="enable-custom-error"></a>Benutzerdefinierten Fehler aktivieren

Sie können benutzerdefinierte Fehler auf Portalen aktivieren, um eine professional aussehende Seite anstatt des YSOD anzuzeigen. Diese Seite bietet aussagekräftige Informationen, wenn eine Ausnahme in der Anwendung auftritt.

1. Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2. Wechseln Sie zu **Portalaktionen** > **Benutzerdefinierte Fehler aktivieren**.

   > [!div class=mx-imgBorder]
   > ![Benutzerdefinierten Fehler aktivieren](../media/enable-custom-errors.png "Benutzerdefinierten Fehler aktivieren")

3. Wählen Sie in der Bestätigungsmeldung **Aktivieren** aus. Während benutzerdefinierte Fehler aktiviert werden, startet das Portal neu und wird nicht verfügbar sein. Eine Meldung wird angezeigt, wenn benutzerdefinierte Fehler aktiviert werden.

> [!NOTE]
> - Wenn Sie die Instanz ändern, mit der Ihr Portal verbunden ist, wird die Einstellung für benutzerdefinierte Fehler auf aktiviert gesetzt. Sie müssen die benutzerdefinierten Fehler nach Bedarf erneut deaktivieren.
> - Sie dürfen benutzerdefinierte Fehler nicht aktivieren oder deaktivieren, wenn die Instanz, mit der Ihr Portal verbunden ist, geändert wird; andernfalls erscheint eine Fehlermeldung.

### <a name="display-a-custom-error-message"></a>Eine benutzerdefinierte Fehlermeldung anzeigen

Sie können das Portal so konfigurieren, dass ein professionell aussehender benutzerdefinierter Fehler anstelle eines generischen Fehlers angezeigt wird.

Um einen benutzerdefinierten Fehler zu definieren, verwenden Sie den Inhaltsausschnitt `Portal Generic Error`. Der in diesem Ausschnitt definierte Inhalt wird auf der Fehlerseite angezeigt. Dieser Inhaltsausschnitt ist nicht vorkonfiguriert verfügbar, und Sie müssen ihn erstellen. Der Inhaltsausschnitt **Typ** kann **Text** oder **HTML** sein. Wenn Sie den Inhaltsausschnitt erstellen oder bearbeiten, siehe [Anpassen von Inhalt mit Inhaltsausschnitten](../configure/customize-content-snippets.md).

> [!NOTE]
> Wenn Liquid-Code im Inhaltsausschnitt geschrieben wird, wird er übersprungen und nicht gerendert.

Wenn Sie benutzerdefinierte Fehler aktivieren, wird die Meldung in der folgenden Struktur auf der Fehlerseite angezeigt:

<Content Snippet> 
<Error ID >
<Date and time>
<Portal ID>

Im Anschluss finden Sie ein Beispiel einer benutzerdefinierten Fehlermeldung, mithilfe eines Inhaltsausschnitts vom Typ HTML:

Dies ist ein benutzerdefinierter, bitte übermitteln Sie ein Supportticket mit dem Bildschirmfoto des Fehlers, indem Sie hier klicken

> [!div class=mx-imgBorder]
> ![Benutzerdefinierte Fehlermeldung](../media/custom-error-message.png "Benutzerdefinierte Fehlermeldung")

> [!NOTE]
> Wenn vom Portal kein Inhaltsausschnitt abgerufen werden kann, da es keine Verbindung mit Common Data Service herstellen kann, oder wenn der Ausschnitt nicht in Common Data Service verfügbar ist, wird eine Fehlermeldung angezeigt.

## <a name="access-portal-error-logs"></a>Auf Portalfehlerprotokolle zugreifen

Nachdem Sie das Portal entwickelt und veröffentlicht haben, müssen Sie immer noch dazu in der Lage sein, auf Portalprotokolle zuzugreifen, um Probleme zu debuggen, die von Ihrem Kunden gemeldet werden. Um auf die Protokolle zuzugreifen, können Sie Ihr Portal so konfigurieren, dass alle Anwendungsfehler an ein Azure Blob Storage-Konto, das Sie besitzen, übermittelt werden. Indem Sie auf Portalfehlerprotokolle zugreifen, können Sie auf Kundenanfragen effiziente reagieren, da Sie Details des Problems haben. Um Portalfehlerprotokolle im Azure-Blobspeicher abzurufen, müssen Sie die Diagnoseprotokollierung vom PowerApps-Portaladministratorcenter aktivieren.

> [!NOTE]
> Wenn Sie die Common Data Service-Instanz ändern, mit der Ihr Portal verbunden ist, wird die Diagnoseprotokollierung deaktiviert. Sie müssen die Diagnoseprotokollieren erneut aktivieren.

### <a name="enable-diagnostic-logging"></a>Diagnoseprotokollierung aktivieren

1. Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2. Wechseln Sie zu **Portalaktionen** > **Diagnoseprotokollierung aktivieren**.

   > [!div class=mx-imgBorder]
   > ![Diagnoseprotokollierung aktivieren](../media/enable-diagnostic-logging.png "Diagnoseprotokollierung aktivieren")

3. Geben Sie im Fenster **Diagnoseprotokollierung aktivieren** die folgenden Werte ein:

   - **Verbindungszeichenfolge des Azure Blob Storage-Diensts**: URL des Azure Blob Storage-Diensts, um die Portalfehlerprotokolle zu speichern. Die maximale Länge der URL beträgt 2048 Zeichen. Wenn die URL länger als 2048 Zeichen ist, wird eine Fehlermeldung angezeigt. Weitere Informationen zur Verbindungszeichenfolge: [Azure Storage-Verbindungszeichenfolgen konfigurieren](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **Beibehaltungsdauer auswählen**: Die Dauer, während der Portalfehlerprotokolle im BLOB-Speicher aufbewahrt werden. Die Fehlerprotokolle werden nach der ausgewählten Dauer gelöscht. Sie können einen der folgenden Werte auswählen:
     - 1 Tag
     - 7 Tage
     - 30 Tage
     - 60 Tage
     - 90 Tage
     - 180 Tage
     - Immer

   Standardmäßig beträgt die Beibehaltungsdauer 30 Tage.
  
   > [!div class=mx-imgBorder]
   > ![Diagnoseprotokollierungsfenster aktivieren](../media/enable-diagnostic-logging-window.png "Diagnoseprotokollierungsfenster aktivieren")

4. Klicken Sie auf **Konfigurieren**.

Sobald die Diagnoseprotokollierung konfiguriert ist, wird ein neuer Blobcontainer für **Telemetrieprotokolle** in Ihrem Azure Storage-Konto erstellt, und die Protokolle werden in die Blobdateien geschrieben, die im Container gespeichert werden. Im folgenden Bildschirmfoto wird der **Telemetrieprotokolle**-Blobcontainer im Azure Storage Explorer angezeigt:

> [!div class=mx-imgBorder]
> ![Azure-Blobspeicherkonto](../media/azure-blob-storage.png "Azure-Blobspeicherkonto")

Wenn die Diagnoseprotokollierung erfolgreich aktiviert ist, wird die folgende Aktion verfügbar:
- **Diagnoseprotokollierungskonfiguration aktivieren**: Ermöglicht es Ihnen, die Diagnoseprotokollierungskonfiguration für das Portal zu aktualisieren oder zu entfernen.
- **Diagnoseprotokollierung deaktivieren**: Ermöglicht es Ihnen, die Diagnoseprotokollierungskonfiguration für das Portal zu deaktivieren.
 
### <a name="update-diagnostic-logging"></a>Diagnoseprotokollierung aktualisieren

1. Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2. Wechseln Sie zu **Portalaktionen** > **Diagnoseprotokollierungskonfiguration aktualisieren**.

   > [!div class=mx-imgBorder]
   > ![Konfiguration der Diagnoseprotokollierung aktualisieren](../media/update-diagnostic-logging.png "Konfiguration der Diagnoseprotokollierung aktualisieren")

3. Geben Sie im Fenster „Diagnoseprotokollierungskonfiguration aktualisieren” die folgenden Werte ein:
   - **Möchten Sie die Verbindungszeichenfolge des Azure Blob Storage-Diensts aktualisieren?**: Ermöglicht es Ihnen anzugeben, ob die Verbindungszeichenfolge des Azure Blob Storage-Diensts aktualisiert werden soll. Standardmäßig ist sie ausgewählt.
   - **Verbindungszeichenfolge des Azure Blob Storage-Diensts**: URL des Azure Blob Storage-Diensts, um die Portalfehlerprotokolle zu speichern. Die maximale Länge der URL kann 2048 Zeichen betragen. Wenn die URL länger als 2048 Zeichen ist, wird eine Fehlermeldung angezeigt. Dieses Feld wird nur angezeigt, wenn das Kontrollkästchen **Möchten Sie die Verbindungszeichenfolge des Azure Blob Storage-Diensts aktualisieren?** aktiviert ist. Weitere Informationen zur Verbindungszeichenfolge: [Azure Storage-Verbindungszeichenfolgen konfigurieren](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **Beibehaltungsdauer auswählen**: Die Dauer, während der Portalfehlerprotokolle im BLOB-Speicher aufbewahrt werden. Die Fehlerprotokolle werden nach der ausgewählten Dauer gelöscht. Sie können einen der folgenden Werte auswählen:
     - 1 Tag
     - 7 Tage
     - 30 Tage
     - 60 Tage
     - 90 Tage
     - 180 Tage
     - Immer

   Standardmäßig beträgt die Beibehaltungsdauer 30 Tage.

   > [!div class=mx-imgBorder]
   > ![Konfigurationsfenster der Diagnoseprotokollierung aktualisieren](../media/update-diagnostic-logging-window.png "Konfigurationsfenster der Diagnoseprotokollierung aktualisieren")

4. Klicken Sie auf **Aktualisieren**.

### <a name="disable-diagnostic-logging"></a>Diagnoseprotokollierung deaktivieren

1. Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2. Wechseln Sie zu **Portalaktionen** > **Diagnoseprotokollierung deaktivieren**.

   > [!div class=mx-imgBorder]
   > ![Diagnoseprotokollierung deaktivieren](../media/disable-diagnostic-logging.png "Diagnoseprotokollierung deaktivieren")

3. Klicken Sie in der Bestätigungsmeldung auf **Deaktivieren**.

## <a name="display-plugin-error"></a>Plugin-Fehler anzeigen

Ein weiteres Szenario, das beim Entwickeln eines Portals oft auftritt, ist ein Fehler, der durch benutzerdefinierte Plug-Ins und Geschäftslogik, die in Ihrer Common Data Service-Umgebung geschrieben wurden, generiert wird. Auf diese Fehler kann im allgemeinen durch [Benutzerdefinierte Fehler deaktivieren](#disable-custom-error) oder [Diagnoseprotokollierung aktivieren](#enable-diagnostic-logging) zugegriffen werden. In einigen Fällen ist es jedoch schneller, diese Fehler direkt im Portal anzuzeigen, um das Problem schneller zu diagnostizieren. Dazu können Sie Ihr Portal so konfigurieren, dass benutzerdefinierte Plug-In-Fehler aus Common Data Service in Ihrem Portalbildschirm angezeigt werden.

Um benutzerdefinierte Plug-In-Fehler anzuzeigen, erstellen Sie die Website-Einstellung `Site/EnableCustomPluginError`, und legen sie deren Wert auf „True” fest. Die benutzerdefinierten Plug-In-Fehler werden im Bildschirm statt eines generischen Fehlers angezeigt. Der Fehler wird nur als Nachrichtenteil des Plug-In-Fehlers angezeigt und nicht als vollständige Stapelüberwachung angezeigt.

Im Anschluss folgen die Bildschirme, in denen benutzerdefinierte Plug-In-Fehler angezeigt werden: 
- Entitätsliste 
    - Abruf von Datensätzen 
- Entitätsformular 
    - Abrufen 
    - Erstellen/Aktualisieren usw. 
- Webformulare 
    - Abrufen 
    - Erstellen/Aktualisieren usw.

Wenn die Website-Einstellung nicht vorhanden ist, wird sie standardmäßig als falsch behandelt und Plug-In-Fehler werden nicht gerendert.
