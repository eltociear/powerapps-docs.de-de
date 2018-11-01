---
title: Zugriff auf modellgesteuerte App-Formulare in PowerApps steuern | MicrosoftDocs
description: 'Erfahren Sie, wie Zugriff auf Hauptformulare gesteuert wird'
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 15d123e0-b604-45dd-ab34-0b37787a04bb
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="control-access-to-model-driven-app-forms"></a>Zugriff auf modellgesteuerte App-Formulare in PowerApps steuern

 Es gibt zwei Möglichkeiten , um den Zugriff auf Hauptformulare zu steuern:  
  
- **Ein Hauptformular inaktiv machen**  
  
     Sie können eine aktive oder inaktive Eigenschaft für Hauptformulare festlegen. Diese Funktion dient hauptsächlich dazu, neue Formulare zu verwalten, wenn Dynamics 365 Customer Engagement Organisationen eine Aktualisierung durchführen, Sie können damit aber verhindern, dass Benutzer ein bestimmtes Hauptformular verwenden.   
  
- **Zuweisen von Sicherheitsrollen zum Hauptformular**  
  
     Verwenden Sie dies, um ein Hauptformular bestimmten Gruppen zur Verfügung zu stellen.  
  
 Verschiedene Personen in Ihrer Organisation können mit denselben Daten in unterschiedlicher Weise interagieren. Manager müssen möglicherweise schnell Informationen in einem Datensatz erfassen, und Servicemitarbeiter benötigen ein Formular, das die Dateneingabe optimiert. Sie können verschiedener Anforderungen berücksichtigen, indem Sie Formulare den Sicherheitsrollen zuweisen, zu denen verschiedene Mitarbeitergruppen gehören.  
  
 Genaue Anweisungen finden Sie unter [Zuweisen von Sicherheitsrollen zu Formularen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form).  
  
 Sind mehrere Haupt- oder Mobilformulare für eine Entität definiert, können Sie auswählen, welche Formulare Benutzer aufgrund ihrer Sicherheitsrollen verwenden können. Da jede Entität in der Lage sein muss, ein Formular für beliebige Benutzer anzuzeigen, muss mindestens ein Formular als "Fallback"-Formular festgelegt werden - ein Formular, das für die Benutzer sichtbar ist, deren Sicherheitsrollen keine spezifischen Formulare zugewiesen wurden.  
  
> [!NOTE]
>  Schnellerfassungs- und Schnellansichtsformulare können keinen Sicherheitsrollen zugewiesen werden.  
  
 Sie können im Formular-Editor oder aus dem Formulareraster einem Formular Sicherheitsrollen zuweisen. Solange jedoch nur ein Formular für die Entität vorhanden ist, können Sie die Option **Für Fallback aktiviert** im Dialogfeld **Sicherheitsrollen zuweisen** nicht löschen. Obwohl Sie dem Formular Sicherheitsrollen zugewiesen haben, können in diesem Fall alle Benutzer, die einer beliebigen Sicherheitsrolle zugeordnet sind, das Formular weiterhin anzeigen, da es als Ausweichformular aktiviert wurde.  
  
 Nachdem Sie ein zweites Haupt- oder Mobilformular für die Entität erstellt haben, können Sie die Option **Für Fallback aktiviert** für eines der Formulare deaktivieren. Über das System wird immer sichergestellt, dass immer mindestens ein Formular als Ausweichformular ("Fallback") aktiviert ist.  
  
 Wenn Sie mehr als ein Hauptformular haben, können Sie eine Formularreihenfolge angeben, die steuert, welches der Formulare, die ein Benutzer anzeigen kann, das Standardformular ist. Falls mehrere Formulare vorhanden sind, die sie verwenden können, können sie Formulare wechseln, und das ausgewählte Formular wird dann das Standardformular, bis sie wieder ein anderes wählen. Diese Einstellung wird in ihrem Browser gespeichert. Wenn Sie einen anderen Browser oder einen anderen Computer verwenden, sehen sie das ursprüngliche Standardformular.  
  
## <a name="strategies-to-manage-the-fallback-form"></a>Strategien zum Verwalten des Ausweichformulars  
 Strategien zum Verwalten des Ausweichformulars sind etwa:  
  
<a name="BKMK_DoNotUseMultipleForms"></a>   
### <a name="all-users-view-the-same-form"></a>Alle Benutzer sehen dasselbe Formular  
 Wenn Sie nicht mehrere Formulare für eine Entität benötigen, benötigen Sie kein Ausweichformular.  
  
<a name="BKMK_Contingecyform"></a>   
### <a name="create-a-contingency-form"></a>Erstellen eines Notfallformular  
 Wenn Sie rollenbasierte Formulare verwenden, um die Informationen einzuschränken, die Benutzer anzeigen oder bearbeiten können, können Sie ein Formular erstellen, das nur ein Minimum von Informationen anzeigt. Wählen Sie dann im Dialogfeld **Sicherheitsrollen zuweisen** die Option **Nur für diese ausgewählten Sicherheitsrollen anzeigen** aus, wählen Sie jedoch keine Rollen außer "Systemadministrator", und wählen Sie **Als Ausweichformular aktiviert** aus. Das Ergebnis ist, dass das Formular nur vom Systemadministrator und von Benutzern, dessen Sicherheitsrollen nicht einem bestimmten Formular zugewiesen wurden, angezeigt werden kann. Sie können eine HTML-Webressource in das Formular einfügen, die angibt, warum das Formular so wenig Informationen anzeigt, sowie einen Link zu Informationen dazu, wie Benutzer eine Sicherheitsrolle anfragen können, die mit einem Formular verbunden ist.  
  
> [!NOTE]
>  Sie können keine Webressource in einer Formularkopf- oder -fußzeile mit einschließen.  
  
<a name="BKMK_CreateGenericForm"></a>   
## <a name="create-a-generic-form"></a>Erstellen eines generischen Formulars  
 Wenn Sie rollenbasierte Formulare verwenden, um eine benutzerdefinierte Umgebung aufgrund der Rolle eines Benutzers innerhalb der Organisation bereitzustellen, können Sie das am wenigsten spezialisierte Formular als Ausweichformular einrichten und es so konfigurieren, dass es allen Benutzern angezeigt wird. Erstellen Sie dann benutzerdefinierte Formulare für bestimmte Sicherheitsrollen, und konfigurieren Sie diese so, dass sie nur für Sicherheitsrollen angezeigt werden, die sie benötigen. Aktivieren Sie diese Formulare nicht als Ausweichformular. Verwenden Sie schließlich die Liste **Formulare** im Dialogfeld **Formularreihenfolge**, um anzugeben, welche Formulare angezeigt werden - angeordnet von dem am wenigsten exklusiven bis zum exklusivsten Formular. Ihr Ausweichformular befindet sich am unteren Rand der Liste. Dadurch sehen Benutzer das Formular, das für ihre Rolle angepasst wurde, als Standardformular, können aber mit der Formularauswahl nach Wunsch das verbreitetste Formular auswählen. Das von Ihnen gewählte Formular bleibt ihr Standardformular, bis sie ein anderes auswählen.  
  
<a name="BKMK_UseFormScripting"></a>   
## <a name="use-form-scripting"></a>Verwenden von Formularskripts  

 Schließlich ist es in der Webanwendung möglich, jedoch nicht empfohlen, dass ein Entwickler im Formularereignis Onload Skripts verwendet, um die [Xrm.Page.ui.formSelector.items-Sammlung](http://go.microsoft.com/fwlink/p/?LinkID=513300) zu nutzen, um verfügbare Formulare abzufragen und Benutzer per Navigation zu einem bestimmten Formular zu führen. Denken Sie daran, dass das [Navigationsverfahren](http://go.microsoft.com/fwlink/p/?LinkID=513301) dazu führt, dass das Formular erneut geladen wird (und das Onload-Ereignis erneut ausgeführt wird). Ihre Logik im Ereignishandler sollte immer nach Bedingungen sehen, bevor Sie das Navigationsverfahren verwenden, um eine Endlosschleife zu vermeiden oder damit Benutzer nicht in unnötiger Weise daran gehindert werden, zwischen Formularen zu navigieren.  
  
 Diese Methode funktioniert nicht für Dynamics 365 for tablets, da nicht mehrere Formulare zur Auswahl verfügbar sind.  

### <a name="next-steps"></a>Nächste Schritte  

[Zuweisen von Sicherheitsrollen zu Formularen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)
