---
title: Steuern des Zugriffs auf Formulare modellgesteuerter Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie den Zugriff auf Hauptformulare steuern können
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
tags: ''
ms.openlocfilehash: a895bd9ea0257585f942840924a7044a4dcc23fb
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683122"
---
# <a name="control-access-to-model-driven-app-forms"></a>Steuern des Zugriffs auf Formulare modellgesteuerter Apps

 Es gibt zwei Möglichkeiten, den Zugriff auf Hauptformulare zu steuern:  
  
- **Ein Hauptformular inaktiv machen**  
  
     Sie können einen aktiven oder inaktiven Status für Hauptformulare festlegen. Diese Funktion sollte eigentlich dazu dienen, neue Formulare zu verwalten, wenn Organisationen, die Dynamics 365 Customer Engagement verwenden, eine Aktualisierung durchführen; Sie können damit aber verhindern, dass Benutzer ein Hauptformular verwenden können.   
  
- **Zuweisen von Sicherheitsrollen für das Hauptformular**  
  
     Verwenden Sie diese Option, um ein Hauptformular bestimmten Gruppen zur Verfügung zu stellen.  
  
 Andere Personen in Ihrer Organisation können mit denselben Daten auf unterschiedliche Weise interagieren. Manager müssen möglicherweise schnell Informationen in einem Datensatz erfassen, und Servicemitarbeiter benötigen ein Formular, das die Dateneingabe optimiert. Sie können verschiedener Anforderungen berücksichtigen, indem Sie Formulare den Sicherheitsrollen zuweisen, zu denen verschiedene Mitarbeitergruppen gehören.  
  
 Schrittweise Anleitungen finden Sie unter [Sicherheitsrollen zu einem Formular zuweisen für einen genaueren Zugriff](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form).  
  
 Sind mehrere Haupt- oder Mobilformulare für eine Entität definiert, können Sie auswählen, welche Formulare Benutzer aufgrund ihrer Sicherheitsrollen verwenden können. Da jede Entität in der Lage sein muss, ein Formular für beliebige Benutzer anzuzeigen, muss mindestens ein Formular als "Fallback"-Formular festgelegt werden – ein Formular, das für die Benutzer sichtbar ist, deren Sicherheitsrollen keine spezifischen Formulare zugewiesen wurden.  
  
> [!NOTE]
>  Schnellerfassungs- und Schnellansichtsformulare können nicht Sicherheitsrollen zugewiesen werden.  
  
 Sie können im Formular-Editor oder aus dem Formulareraster einem Formular Sicherheitsrollen zuweisen. Solange jedoch nur ein Formular für die Entität vorhanden ist, können Sie die Option **Für Fallback aktiviert** im Dialogfeld **Sicherheitsrollen zuweisen** nicht löschen. Obwohl Sie dem Formular Sicherheitsrollen zugewiesen haben, können in diesem Fall alle Benutzer, die einer beliebigen Sicherheitsrolle zugeordnet sind, das Formular weiterhin anzeigen, da es als Ausweichformular aktiviert wurde.  
  
 Nachdem Sie ein zweites Haupt- oder Mobilformular für die Entität erstellt haben, können Sie die Option **Für Fallback aktiviert** für eines der Formulare deaktivieren. Über das System wird immer sichergestellt, dass immer mindestens ein Formular als Ausweichformular aktiviert ist.  
  
 Wenn Sie mehr als ein Hauptformular haben, können Sie eine Formularreihenfolge angeben, die steuert, welches der Formulare, die ein Benutzer anzeigen kann, das Standardformular ist. Falls mehrere Formulare vorhanden sind, die Benutzer verwenden können, können sie Formulare wechseln, und das ausgewählte Formular wird dann das Standardformular, bis sie wieder ein anderes auswählen. Diese Einstellung wird in ihrem Browser gespeichert. Wenn Sie einen anderen Browser oder einen anderen Computer verwenden, sehen sie das ursprüngliche Standardformular.  
  
## <a name="strategies-to-manage-the-fallback-form"></a>Strategien zum Verwalten des Ausweichformulars  
 Zu den Strategien zum Verwalten des Ausweichformulars zählen die folgenden:  
  
<a name="BKMK_DoNotUseMultipleForms"></a>   
### <a name="all-users-view-the-same-form"></a>Alle Benutzer sehen dasselbe Formular  
 Wenn Sie nicht mehrere Formulare für eine Entität benötigen, benötigen Sie kein Ausweichformular.  
  
<a name="BKMK_Contingecyform"></a>   
### <a name="create-a-contingency-form"></a>Erstellen eines Notfallformulars  
 Wenn Sie rollenbasierte Formulare verwenden, um die Informationen einzuschränken, die Benutzer anzeigen oder bearbeiten können, können Sie ein Formular erstellen, das nur ein Minimum von Informationen anzeigt. Wählen Sie dann im Dialogfeld **Sicherheitsrollen zuweisen** die Option **Nur für diese ausgewählten Sicherheitsrollen anzeigen** aus, wählen Sie jedoch keine Rollen außer „Systemadministrator“, und wählen Sie **Als Ausweichformular aktiviert** aus. Das Ergebnis ist, dass das Formular nur vom Systemadministrator und von Benutzern, deren Sicherheitsrollen nicht einem bestimmten Formular zugewiesen wurden, angezeigt werden kann. Sie können eine HTML-Webressource in das Formular einfügen, die angibt, warum das Formular so wenig Informationen anzeigt, sowie einen Link zu Informationen dazu, wie Benutzer eine Sicherheitsrolle anfragen können, die mit einem Formular verbunden ist, oder wie eine neue Sicherheitsrolle für ein Formular einbezogen werden kann.  
  
> [!NOTE]
>  Sie können Webressourcen nicht in die Kopf- oder Fußzeile eines Formulars einfügen.  
  
<a name="BKMK_CreateGenericForm"></a>   
## <a name="create-a-generic-form"></a>Erstellen eines generischen Formulars  
 Wenn Sie rollenbasierte Formulare verwenden, um eine benutzerdefinierte Umgebung aufgrund der Rolle eines Benutzers innerhalb der Organisation bereitzustellen, können Sie das am wenigsten spezialisierte Formular als Ausweichformular einrichten und es so konfigurieren, dass es allen Benutzern angezeigt wird. Erstellen Sie dann benutzerdefinierte Formulare für bestimmte Sicherheitsrollen, und konfigurieren Sie diese so, dass sie nur für Sicherheitsrollen angezeigt werden, die sie benötigen. Aktivieren Sie diese Formulare nicht als Ausweichformular. Verwenden Sie schließlich die Liste **Formulare** im Dialogfeld **Formularreihenfolge**, um anzugeben, welche Formulare angezeigt werden – beginnend mit dem am wenigsten exklusiven bis zum exklusivsten Formular. Ihr Ausweichformular befindet sich am Ende der Liste. So sehen Benutzer das Formular, das für ihre Rolle angepasst wurde, als Standardformular, können aber mit der Formularauswahl nach Wunsch das gängigste Formular auswählen. Das von ihnen ausgewählte Formular bleibt ihr Standardformular, bis sie ein anderes auswählen.  
  
<a name="BKMK_UseFormScripting"></a>   
## <a name="use-form-scripting"></a>Verwenden von Formularskripts  

 Schließlich ist es in der Webanwendung möglich, jedoch nicht empfohlen, dass ein Entwickler im Formularereignis Onload Skripts verwendet, um die [Xrm.Page.ui.formSelector.items](http://go.microsoft.com/fwlink/p/?LinkID=513300)-Sammlung zu nutzen, um verfügbare Formulare abzufragen und Benutzer per Navigation zu einem bestimmten Formular zu führen. Denken Sie daran, dass das [Navigationsverfahren](http://go.microsoft.com/fwlink/p/?LinkID=513301) dazu führt, dass das Formular erneut geladen wird (und das Onload-Ereignis erneut ausgeführt wird). Ihre Logik im Ereignishandler sollte immer nach Bedingungen sehen, bevor Sie das Navigationsverfahren verwenden, um eine Endlosschleife zu vermeiden, oder damit Benutzer nicht unnötigerweise daran gehindert werden, zwischen Formularen zu navigieren.  
  
 Diese Methode funktioniert nicht für Dynamics 365 für Tablets, da nicht mehrere Formulare zur Auswahl verfügbar sind.  

### <a name="next-steps"></a>Nächste Schritte  

[Zuweisen von Sicherheitsrollen zu Formularen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)
