---
title: Erstellen oder Bearbeiten modellgesteuerter App-Webressourcen in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie eine Webressource erstellt oder bearbeitet wird.
ms.custom: ''
ms.date: 06/02/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ef4ba8df-9ba9-4066-b40d-def9761c7de2
caps.latest.revision: 21
ms.author: matp
manager: kvivek
ms.openlocfilehash: 8d9414ba4c900f98ac26010e4e6d7240b336e2d7
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39687993"
---
# <a name="create-or-edit-model-driven-app-web-resources-to-extend-an-app"></a>Erstellen oder Bearbeiten modellgesteuerter App-Webressourcen zum Erweitern einer App

Webressourcen werden in der Regel von Entwicklern genutzt, um eine App mithilfe von Dateien zu erweitern, die bei der Webentwicklung verwendet werden. App-Benutzer müssen möglicherweise Webressourcen verwalten, die von einem Entwickler oder Designer bereitgestellt werden.  

> [!TIP]
> Eine ausführliche Erläuterung von Webressourcen finden Sie unter [Dokumentation für Entwickler: Webressourcen für Customer Engagement](/dynamics365/customer-engagement/developer/web-resources).<br /> Informationen zu Abhängigkeiten von Webressourcen, die in PowerApps hinzugefügt werden, finden Sie unter [Dokumentation für Entwickler: Abhängigkeiten von Webressourcen](/dynamics365/customer-engagement/developer/web-resources).
   
<a name="BKMK_WhatAreWebResources"></a>

## <a name="what-are-web-resources"></a>Was sind Webressourcen?  

Webressourcen sind virtuelle Dateien, die im System gespeichert sind. Jede Webressource verfügt über einen eindeutigen Namen, der in einer URL verwendet werden kann, um die Datei abzurufen. Betrachten Sie sie auf diese Weise: Wenn Sie Zugriff auf den tatsächlichen Webserver hätten, auf dem die Web-App ausgeführt wird, könnten Sie Dateien auf diese Website kopieren. Aber bei den meisten Onlinediensten ist dies nicht möglich.  Stattdessen können Sie Webressourcen zum Hochladen von Dateien in das System verwenden und dann anhand des Namens darauf verweisen, als hätten Sie sie als Dateien auf den Webserver kopiert.  
  
Wenn Sie z.B. eine HTML-Seite als Webressource mit dem Namen „new_myWebResource.htm“ erstellen, können Sie diese Seite in einem Browser über folgende URL öffnen:  
 
`<base URL>/WebResources/new_myWebResource.htm   `
  
Dabei ist *\<base URL>* der Teil der URL, den Sie zum Anzeigen von Apps verwenden, die auf `dynamics.com` enden. Da Webressourcen Daten im System sind, können nur lizenzierte Benutzer für Ihre Organisation auf diese Weise darauf zugreifen. In der Regel sind Webressourcen in Formularen enthalten, und es wird nicht direkt auf sie verwiesen. Die häufigste Verwendung ist das Bereitstellen von JavaScript-Bibliotheken für Formularskripts.  
    
Da Webressourcen Daten im System und lösungsabhängig sind, können Sie sie in andere Organisationen verschieben, indem Sie sie als Teil einer Lösung exportieren und die Lösung in eine andere Organisation importieren. Sie müssen zum Arbeiten mit Webressourcen den Projektmappen-Explorer verwenden.
  
## <a name="open-solution-explorer"></a>Öffnen des Projektmappen-Explorers

Ein Teil des Namens einer Webressource, die Sie erstellen, ist das Anpassungspräfix. Dieses wird basierend auf dem Lösungsherausgeber für die Lösung festgelegt, in der Sie momentan arbeiten. Wenn das Anpassungspräfix für Sie im Mittelpunkt steht, stellen Sie sicher, dass Sie in einer nicht verwalteten Lösung mit dem von Ihnen bevorzugten Anpassungspräfix für diese Webressource arbeiten. Weitere Informationen finden Sie unter [Ändern des Präfix für den Lösungsherausgeber](../common-data-service/change-solution-publisher-prefix.md). 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-web-resources"></a>Anzeigen von Webressourcen

Wählen Sie im geöffneten Projektmappen-Explorer unter **Komponenten** die Option **Webressourcen** aus.

![Anzeigen von Webressourcen](media/view-web-resources-solution-explorer.png)

<a name="BKMK_CreateAndEditWebResources"></a>

## <a name="create-or-edit-web-resources"></a>Erstellen oder Bearbeiten von Webressourcen  

Wählen Sie beim [Anzeigen von Webressourcen](#view-web-resources) die Option **Neu** aus, um eine neue Webressource zu erstellen, oder doppelklicken Sie auf eine vorhandene Webressource, um sie zu bearbeiten.

![Formular für neue Webressourcen](media/new-web-resource-form.png)

Füllen Sie das Formular zum Erstellen oder Bearbeiten der Webressource aus:
  
|Feld|Beschreibung|  
|-----------|-----------------|  
|**Name**|*Erforderlich*. Dies ist der eindeutige Name für diese Webressource. Sie können ihn nicht ändern, nachdem Sie die Webressource gespeichert haben.<br />&bull; Dieser Name darf nur Buchstaben, Zahlen, Punkte und nicht aufeinander folgende Schrägstriche (/) enthalten.<br /> &bull; Das Anpassungspräfix des Lösungsherausgebers wird dem Namen der Webressource vorangestellt.|  
|**Anzeigename**|Der Name, der angezeigt wird, wenn Sie eine Liste von Webressourcen anzeigen.|  
|**Description** (Beschreibung)|Eine Beschreibung der Webressource.|  
|**Typ**|*Erforderlich*. Dies ist der Typ der Webressource. Sie können ihn nicht ändern, nachdem Sie die Webressource gespeichert haben.|  
|**Text-Editor**|Wenn der Typ der Webressource eine Art von Textdatei darstellt, wählen Sie diese Schaltfläche aus, um eine Seite zum Bearbeiten der Inhalte mit dem Text-Editor zu öffnen.<br />Weitere Informationen finden Sie unter [Geeignetes Verwenden des Text-Editors](#use-the-text-editor-appropriately)| 
|**Sprache**|Ermöglicht die Auswahl einer Sprache. Mit dieser Option wird lediglich der Datensatz, in dem die Webressourcendaten speichert werden, mit Tags versehen. Sie ändert das Verhalten der Webressource nicht.|  
|**Datei hochladen**|Wählen Sie die Schaltfläche **Durchsuchen** aus, um eine Datei auszuwählen, die als Webressource hochgeladen werden soll.<br />&bull; Sie können eine Datei hochladen, wenn Sie eine neue Webressource erstellen. Sie können so aber auch eine vorhandene Webressource überschreiben.<br />&bull; Die Dateinamenerweiterung der Datei muss mit den zulässigen Erweiterungen übereinstimmen.<br />&bull; Standardmäßig ist die maximale Dateigröße, die als Webressource hochgeladen werden kann, 5 MB. Dieser Wert kann in Dynamics 365 Customer Engagement mit **Systemeinstellungen** >  Registerkarte **E-Mail** > Einstellung **Begrenzung der Dateigröße für Anlagen festlegen** geändert werden. Weitere Informationen finden Sie unter [Dialogfeld „Systemeinstellungen“ – Registerkarte „E-Mail“](https://docs.microsoft.com/dynamics365/customer-engagement/admin/system-settings-dialog-box-email-tab) |  
|**URL**|Nachdem Sie die Webressource gespeichert haben, wird hier die URL der Webressource angezeigt. Wählen Sie diesen Link aus, um die Webressource in Ihrem Browser anzuzeigen.|  
  
Nachdem Sie Ihre Änderungen hinzugefügt haben, wählen Sie **Speichern** und dann **Veröffentlichen** aus.  

> [!NOTE]
> Änderungen an einer Webressource sind erst in der Anwendung sichtbar, wenn Sie sie veröffentlicht haben.
  
<a name="BKMK_UsingTextEditor"></a>
   
### <a name="use-the-text-editor-appropriately"></a>Geeignetes Verwenden des Text-Editors

Der in der Anwendung für Webressourcen bereitgestellte Text-Editor sollte nur für einfache Änderungen an Textdateien verwendet werden. Sie können damit HTML-Webressourcen erstellen und bearbeiten, Sie sollten aber nur HTML-Webressourcen bearbeiten, die mit dem Texteditor erstellt wurden. Der Text-Editor ist für ganz einfache HTML-Inhalte vorgesehen. 

> [!IMPORTANT]
> Wenn der Inhalt einer HTML-Webressource nicht mit dem Text-Editor erstellt wurde, verwenden Sie zum Bearbeiten nicht den Text-Editor.  
> Der Text-Editor verwendet ein Steuerelement, das die HTML-Quelle so ändert, dass sie bearbeitet werden kann. Diese Änderungen können dazu führen, dass sich die Seite im Browser anders verhält und dass komplexerer Code nicht mehr funktioniert. Durch das Öffnen einer HTML-Webressource mit dem Text-Editor und das anschließende Speichern, ohne Änderungen vorzunehmen, können einige HTML-Webressourcen beschädigt werden.  Weitere Informationen finden Sie unter [Dokumentation für Entwickler: Text-Editor für HTML-Webressourcen verwenden](/dynamics365/customer-engagement/developer/webpage-html-web-resources#use-the-text-editor-for-html-web-resources)
  
Es wird empfohlen, dass Sie einen externen Editor zum Bearbeiten von Textdateien verwenden und diese lokal speichern, bevor Sie sie mit der Schaltfläche **Datei hochladen** hochladen. Auf diese Weise können Sie eine Kopie der Webressource behalten, falls Sie zu einer früheren Version zurückkehren müssen. Sie können einen einfachen Editor wie Editor verwenden, aber ein Text-Editor mit erweiterten Funktionen wird dringend empfohlen. [Visual Studio Community](https://www.visualstudio.com/vs/community/) und [Visual Studio Code](https://code.visualstudio.com/) sind kostenlos und verfügen über leistungsstarke Funktionen zum Bearbeiten von textbasierten Dateien, die von Webressourcen verwendet werden.  

<a name="BKMK_CreateAndEditFormWebResources"></a>
 
## <a name="create-and-edit-a-web-resource-on-a-form"></a>Erstellen und Bearbeiten einer Webressource in einem Formular

Sie können Webressourcen in einem Formular hinzufügen oder bearbeiten, um es für Benutzer ansprechender oder nützlicher zu machen. 

> [!NOTE]
> Sie können Webressourcen nicht in die Kopf- oder Fußzeile eines Formulars einfügen.  

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="navigate-to-a-form"></a>Navigieren zu einem Formular
Erweitern Sie im geöffneten Projektmappen-Explorer unter **Komponenten** den Eintrag **Entitäten**, und erweitern Sie dann die Entität, die Sie bearbeiten möchten.

Wählen Sie **Formulare** aus, suchen Sie in der Liste nach einem Formular vom Typ „Haupt“, und doppelklicken oder tippen Sie dann auf den Eintrag, um das Formular zu öffnen und zu bearbeiten.

### <a name="add-or-edit-web-resource-in-a-form"></a>Hinzufügen oder Bearbeiten einer Webressource in einem Formular

Unter [Webressourceneigenschaften](web-resource-properties-legacy.md) finden Sie Informationen zu den Eigenschaften, die Sie für Webressourcen in einem Formular festlegen können.

### <a name="preview"></a>Vorschau

So zeigen Sie eine Vorschau des Hauptformulars und der Funktionsweise der Ereignisse an
- Wählen Sie auf der Registerkarte **Start** die Option **Vorschau** und dann **Formular erstellen**, **Formular aktualisieren** oder **Schreibgeschütztes Formular** aus.
- Um das Vorschauformular zu schließen, wählen Sie im Menü **Datei** die Option **Schließen** aus.

### <a name="save"></a>Speichern

Wenn Sie die Bearbeitung des Formulars abgeschlossen haben, wählen Sie auf der Registerkarte **Start** die Option **Speichern und schließen** aus, um das Formular zu schließen. 

### <a name="publish"></a>Veröffentlichen

Wenn Ihre Anpassungen abgeschlossen sind, veröffentlichen Sie sie:
- Um Anpassungen nur für die Komponente zu veröffentlichen, die Sie gerade bearbeiten, wählen Sie im Navigationsbereich die Entität aus, an der Sie gearbeitet haben, und wählen Sie dann **Veröffentlichen** aus.
- Um Anpassungen für alle nicht veröffentlichten Komponenten gleichzeitig zu veröffentlichen, wählen Sie im Navigationsbereich **Entitäten** aus, und wählen Sie dann auf der Symbolleiste **Aktionen** die Option **Alle Anpassungen veröffentlichen**  aus.
   
  
### <a name="see-also"></a>Siehe auch  

[Webressourceneigenschaften](web-resource-properties-legacy.md) <br /> 
[Erstellen und Entwerfen von Formularen](create-design-forms.md) <br />
[Erste Schritte mit Anpassungen](getting-started-customization.md) <br /> 
[Dokumentation für Entwickler: Webressourcen für Customer Engagement](/dynamics365/customer-engagement/developer/web-resources)
