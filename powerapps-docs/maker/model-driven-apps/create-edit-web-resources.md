---
title: Erstellen oder bearbeiten von Webressourcen für modellgesteuerte Apps in PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie Sie eine Webressouce erstellen oder bearbeiten'
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-model-driven-app-web-resources-to-extend-an-app"></a>Erstellen oder Bearbeiten von Webressourcen für modellgesteuerte Apps, um eine App zu erweitern

Webressourcen werden in der Regel von Entwicklern verwendet, um eine App mithilfe von Dateien zu erweitern, die in der Webentwicklung verwendet werden. App-Benutzer müssen möglicherweise Webressourcen verwalten, die von einem Entwickler oder Designer bereitgestellt werden.  

> [!TIP]
> Eine ausführliche Diskussion zu Webressourcen finden Sie unter [Entwicklerdokumentation: Webressourcen für Customer Engagement](/dynamics365/customer-engagement/developer/web-resources).<br /> Informationen zu den Abhängigkeiten von Webressourcen, die in PowerApps hinzugefügt wurden, finden Sie unter [Abhängigkeiten von Webressourcen](/dynamics365/customer-engagement/developer/web-resources).
   
<a name="BKMK_WhatAreWebResources"></a>

## <a name="what-are-web-resources"></a>Was sind Webressourcen?  

Webressourcen sind virtuelle Dateien, die im System gespeichert werden. Jede Webressource hat einen eindeutigen Namen, der in einer URL verwendet werden kann, um die Datei abzurufen. Stellen Sie sich dies folgendermaßen vor: Wenn Sie auf den eigentlichen Webserver zugreifen könnten, auf dem die Web-App ausgeführt wird, könnten Sie Dateien zu dieser Website kopieren. Aber mit den meisten Onlinediensten ist dies nicht möglich.  Stattdessen können Sie Webressourcen verwenden, um Dateien zum System hochzuladen und diese dann per Name zu referenzieren, als ob Sie diese als Dateien zum Webserver kopiert hätten.  
  
Wenn Sie beispielsweise eine HTML-Seite als Webressource erstellen, die den Namen "new_myWebResource.htm" hat, könnten Sie diese Seite in einem Browser über eine URL wie die folgende öffnen:  
 
`<base URL>/WebResources/new_myWebResource.htm   `
  
wo *\<Basis-URL>* der Teil der URL ist, den Sie verwenden, um Apps anzuzeigen, die mit `dynamics.com` enden. Da die Webressource Daten im System sind, können nur lizenzierte Benutzer Ihrer Organisation auf diese auf diese Art zugreifen. Normalerweise sind Webressourcen in Formularen enthalten und werden nicht direkt referernziert. Die häufigste Verwendung besteht in der Bereitstellung von JavaScript-Bibliotheken für Formularskripts.  
    
Da Webressourcen Daten im System und lösungsabhängig sind, können Sie diese zu unterschiedlichen Organisationen verschieben, indem Sie sie im Rahmen einer Lösung exportieren und die Lösung in eine andere Organisation importieren. Sie müssen den Projektmappen-Explorer verwenden, um mit Webressourcen zu arbeiten.
  
## <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Ein Teil des Namens jeder Webressource, die Sie erstellen, ist das Anpassungspräfix. Dieser Satz basiert auf dem Lösungsherausgeber für die Lösung, in der Sie arbeiten. Wenn Ihnen das Anpassungspräfix wichtig ist, achten Sie darauf, dass Sie in einer nicht verwalteten Lösung oder der Standardlösung arbeiten, in der das Anpassungspräfix Ihren Wünschen für diese Webressource entspricht. Weitere Informationen [Lösungsherausgeberpräfix ändern](../common-data-service/change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-web-resources"></a>Webressourcen anzeigen

Öffnen Sie im Projektmappen-Explorer unter **Komponenten** die Option **Webressourcen**.

![Webressourcen anzeigen](media/view-web-resources-solution-explorer.png)

<a name="BKMK_CreateAndEditWebResources"></a>

## <a name="create-or-edit-web-resources"></a>Webressourcen erstellen oder bearbeiten  

Beim [Anzeigen von Webressourcen](#view-web-resources) wählen Sie **Neu** aus, um eine neue Webressource zu erstellen oder doppelklicken Sie auf eine vorhandene Webressource, um sie zu bearbeiten.

![Neues Webressourcenformular](media/new-web-resource-form.png)

Füllen Sie das Formular aus, um die Webressource zu erstellen oder zu bearbeiten:
  
|Feld|Beschreibung|  
|-----------|-----------------|  
|**Name**|*Erforderlich* Dies ist der eindeutige Name für diese Webressource. Sie können diesen nach dem Speichern der Webressource nicht mehr ändern.<br />&bull; Dieser Name darf nur Buchstaben, Zahlen, Punkte und einzelne Schrägstriche (“/”) enthalten.<br /> &bull; Das Anpassungspräfix für den Lösungsherausgeber wird dem Namen der Webressource vorangestellt.|  
|**Anzeigename**|Der angezeigte Name, wenn Sie eine Liste von Webressourcen anzeigen.|  
|**Beschreibung**|Eine Beschreibung der Webressource.|  
|**Typ**|*Erforderlich* Dies ist der Typ der Webressource. Sie können diesen nach dem Speichern der Webressource nicht mehr ändern.|  
|**Text-Editor**|Wenn der Typ der Webressource eine Art von Textdatei ist, wählen Sie diese Schaltfläche aus, um eine Seite zu öffnen und den Inhalt mittels des Texteditors zu bearbeiten.<br />Weitere Informationen: [Korrekte Verwendung des Texteditors](#use-the-text-editor-appropriately)| 
|**Sprache**|Ermöglicht die Auswahl einer Sprache. Diese Option kennzeichnet nur den Datensatz, in dem die Webressourcedaten gespeichert sind. Sie ändert nicht das Verhalten der Webressource.|  
|**Datei hochladen**|Wählen Sie das **Durchsuchen…** aus um eine Datei für den Upload als Webressource auszuwählen.<br />&bull; Sie können eine Datei hochladen, wenn Sie eine neue Webressource erstellen oder eine vorhandene Webressource überschreiben.<br />&bull; Die Dateinamenerweiterung der Datei muss den zulässigen Erweiterungen entsprechen.<br />&bull;Die maximale Größe einer Datei, die als Webressource hochgeladen werden soll, beträgt 5 MB. Dieser Wert kann in Dynamics 365 Customer Engagement mithilfe der Einstellung **Systemeinstellungen** > **E-Mail**-Registerkarte > **Begrenzung der Dateigröße für Anlagen festlegen** geändert werden. Weitere Informationen: [Dialogfeld Systemeinstellungen – Registerkarte E-Mail](https://docs.microsoft.com/dynamics365/customer-engagement/admin/system-settings-dialog-box-email-tab) |  
|**URL**|Nachdem Sie die Webressource gespeichert haben, wird die URL für die Webressource hier angezeigt. Wählen Sie diesen Link aus, um die Webressource in Ihrem Browser anzuzeigen.|  
  
Nachdem Sie Ihre Änderungen hinzugefügt haben, wählen Sie **Speichern** und dann **Veröffentlichen**.  

> [!NOTE]
> Änderungen an einer Webressource werden nicht in der Anwendung angezeigt, nachdem sie veröffentlicht wurden.
  
<a name="BKMK_UsingTextEditor"></a>
   
### <a name="use-the-text-editor-appropriately"></a>Korrekte Verwendung des Texteditors

Der Texteditor in der Anwendung für Webressourcen sollte nur für die einfache Bearbeitung von Textdateien verwendet werden. Sie können ihn zur Erstellung und Bearbeitung von HTML-Webressourcen verwenden. Sie sollten jedoch nur HTML-Webressourcen bearbeiten, die mithilfe des Text-Editors erstellt wurden. Der Texteditor wurde für sehr einfache HTML-Inhalte entworfen. 

> [!IMPORTANT]
> Wenn der Inhalt einer HTML-Webressource nicht mithilfe des Texteditors erstellt wurde, verwenden Sie den Texteditor nicht zur Bearbeitung.  
> Der Texteditor verwendet ein Steuerelement, das die HTML-Quelle so verändert, dass sie bearbeitet werden kann. Diese Änderungen können dazu führen, dass sich die Seite im Browser anders verhält, und komplexerer Code nicht mehr funktioniert. Das Öffnen und Speichern einer HTML-Webressource mit dem Texteditor, ohne Änderungen vorzunehmen, kann einige HTML-Webressourcen beschädigen.  Weitere Informationen: [Entwicklerdokumentation: Verwenden des Text-Editors für HTML Webressourcen](/dynamics365/customer-engagement/developer/webpage-html-web-resources#use-the-text-editor-for-html-web-resources).
  
Es wird empfohlen, einen externen Editor für die Bearbeitung von Textdateien zu verwenden und diese lokal zu speichern, bevor sie über die Schaltfläche **Datei hochladen** hochgeladen werden. So können Sie eine Kopie der Webressource behalten, wenn Sie zu einer früheren Version zurückkehren müssen. Sie können einen einfachen Editor wie Editor verwenden. Es wird jedoch ein Texteditor mit erweiterter Funktionalität empfohlen. [Visual Studio Community](https://www.visualstudio.com/vs/community/) und [Visual Studio Code](https://code.visualstudio.com/) sind kostenlos und stellen leistungsfähige Funktionen für die Bearbeitung von Dateien bereit, die von textbasierten Webressourcen verwendet werden.  

<a name="BKMK_CreateAndEditFormWebResources"></a>
 
## <a name="create-and-edit-a-web-resource-on-a-form"></a>Erstellen und Bearbeiten einer Webressource in einem Formular

Webressourcen können Sie in einem Formular hinzufügen oder bearbeiten, um sie für mehr Benutzer anziehend oder nützlich zu gestalten. 

> [!NOTE]
> Sie können keine Webressource in einer Formularkopf- oder -fußzeile mit einschließen.  

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="navigate-to-a-form"></a>Zu einem Formular navigieren
Bei geöffnetem Projektmappen-Explorer erweitern Sie unter **Komponenten** den Ordner **Entitäten**, und erweitern Sie dann die gewünschte Entität.

Wählen Sie **Formulare** aus, suchen Sie in der Liste ein Formular des Typs „Haupt“, und doppelklicken oder tippen Sie dann auf den Eintrag, um das Formular zu öffnen und zu bearbeiten.

### <a name="add-or-edit-web-resource-in-a-form"></a>Hinzufügen oder Bearbeiten einer Webressource in einem Formular

Siehe [Webressourceneigenschaften](web-resource-properties-legacy.md) für Informationen zu den Eigenschaften, die Sie für Webressourcen in einem Formular festlegen können.

### <a name="preview"></a>Vorschau

So prüfen Sie in einer Vorschau die Darstellung des Hauptformulars und die Funktionsweise der Ereignisse:
- Wählen Sie auf der Registerkarte **Startseite** die Option **Vorschau** aus, und wählen Sie dann **Formular erstellen**, **Formular aktualisieren** oder **Schreibgeschütztes Formular** aus.
- Wählen Sie zum Schließen des Formulars „Vorschau” im Menü **Datei** die Option **Schließen** aus.

### <a name="save"></a>Speichern

Wenn Sie die Bearbeitung des Formulars abgeschlossen haben, wählen Sie zum Schließen des Formulars auf der Registerkarte **Startseite** die Option **Speichern und schließen** aus. 

### <a name="publish"></a>Veröffentlichen

Sind die Anpassungen vollständig, können sie veröffentlicht werden:
- Wenn Sie Anpassungen für ausschließlich die Komponente veröffentlichen möchten, die Sie gerade bearbeiten, wählen Sie im Navigationsbereich die Entität aus, an der Sie gearbeitet haben, und wählen Sie dann **Veröffentlichen** aus.
- Um Anpassungen für alle nicht veröffentlichten Komponenten gleichzeitig zu veröffentlichen, wählen Sie im Navigationsbereich die Option **Entitäten** und dann auf der Symbolleiste **Aktionen** die Option **Alle Anpassungen veröffentlichen** aus.
   
  
### <a name="see-also"></a>Siehe auch  

[Webressourceneigenschaften](web-resource-properties-legacy.md) <br /> 
[Erstellen und Gestalten von Formularen](create-design-forms.md) <br />
[Grundlegendes zu Komponenten modellgestützter Apps](model-driven-app-components.md) <br /> 
[Entwickler Documenttion: Webressourcen für Customer Engagement](/dynamics365/customer-engagement/developer/web-resources)
