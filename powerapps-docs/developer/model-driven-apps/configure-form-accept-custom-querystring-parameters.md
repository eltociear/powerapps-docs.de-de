---
title: Konfigurieren Sie ein Formular, um benutzerdefinierte Querystring-Parameter (modellgesteuerte Apps) zu akzeptieren | Microsoft Docs
description: Erfahren Sie über das Konfigurieren eines Formulars, um benutzerdefinierte Abfragezeichenfolgenparameter zu akzeptieren. Verwenden Sie diese Parameter, um Standardwerte festzulegen, wenn Sie in der Anwendung einen neuen Datensatz erstellen.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 89287d32-0d16-8f7d-e0b6-8cc208212cff
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 518cae90216c8178c1ef46c3613a6613f9895527
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275842"
---
# <a name="configure-a-form-to-accept-custom-querystring-parameters"></a>Ein Formular konfigurieren, um benutzerdefinierte Abfragezeichenfolgenparameter zu akzeptieren.

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/configure-form-accept-custom-querystring-parameters -->

Werte an eine Webseite mithilfe von Abfragenzeichenfolgen zu übergeben, stellt ein Sicherheitsrisiko dar. Modellgesteuerte Apps arbeiten nach der bewährten Verfahrensweise, bei der alle in einer Abfragenzeichenkette übergebenen Parameter mit einer Liste der erwarteten Parameternamen und Datentypen verglichen werden.  
  
 Standardmäßig erlaubt modellbasierte Apps die Übergabe eines bestimmten Satzes von Abfragezeichenfolgenparametern an ein Formular. Verwenden Sie diese Parameter, um Standardwerte festzulegen, wenn Sie in der Anwendung einen neuen Datensatz erstellen. Jeder Parameter muss eine Standardnamenskonvention verwenden, die einen Verweis auf den logischen Namen des Attributs enthält. Weitere Informationen finden Sie unter [Legen Feldwerte unter Verwendung der Parameter festgelegt, die an ein Formular übergeben wurden](set-field-values-using-parameters-passed-form.md).  
  
 Möglicherweise möchten Sie in Ihrer Anwendung die Abfragezeichenfolgenparameter an ein Entitätsformular übermitteln. In diesem Thema finden Sie Informationen dazu, wie Sie eine Reihe von benutzerdefinierten Parameternamen und Datentypen definieren können, die für ein bestimmtes Entitätsformular angenommen werden können.  
  
## <a name="define-allowed-query-string-parameters"></a>Erlaubte Abfragezeichenfolgenparameter definieren.  
 Es gibt zwei Möglichkeiten zu definieren, welche Abfragezeichenfolgenparameter vom Formular akzeptiert werden:  
  
- Bearbeiten von Formulareigenschaften  
  
- XML-Formular bearbeiten  
  
### <a name="edit-form-properties"></a>Bearbeiten von Formulareigenschaften  
 Wenn Sie ein Entitätsformular bearbeiten, klicken Sie auf der Registerkarte **Start** unter **Formular** auf **Formulareigenschaften**. Klicken Sie im Dialogfeld **Formulareigenschaften** auf die Registerkarte **Parameter**.  
  
 Verwenden Sie diese Registerkarte, um den Namen und die Datentypen zu ändern, die das Formular zulässt.  
  
### <a name="edit-formxml"></a>XML-Formular bearbeiten  
 Innerhalb der exportierten Datei Anpassungen.xml, das dem Fußzeilenelement direkt folgt, können Sie ein Element `<formparameters>` hinzufügen. Im `<formparameters>` Element fügen Sie `<querystringparameter>` Elemente hinzu, um anzugeben, welche Parameter zulässig sind.  
  
 Im Folgenden werden die `querystringparameter` Attributelemente `name` und `type` beschrieben:  
  
- **Name**. Jedes Namensattribut muss mindestens einen Unterstrich ("\_") enthalten, aber der Name des Abfragezeichenfolgenparameters darf nicht mit einem Unterstrich starten. Der Name darf nicht mit „crm\_” starten. Es wird dringend empfohlen, das Sie den Anpassungspräfix des Lösungsherausgebers als Namenskonvention verwenden. Ein gültiger `querystringparameter` Namenattributwert ist "myISV_contact_specialvalue".  
  
    > [!IMPORTANT]
    >  Falls ein `querystringparameter`-Elementname nicht einzigartig ist, kann er mit einer anderen Parameterdefinition mithilfe eines anderen Datentyps überschrieben werden.  
  
- **Typ**: Passen Sie die Datentypwerte mit den Parameterwerten an, damit keine ungültigen Daten an den Parameter übergeben werden. Nachfolgend sind gültige Datentypen:  
  
    -   Boolean  
  
    -   DateTime  
  
    -   Double  
  
    -   EntityType  
  
    -   Integer  
  
    -   Long  
  
    -   PositiveInteger  
  
        > [!NOTE]
        >  PositiveInteger enthält „0” im Bereich der gültigen Werte.  
  
    -   SafeString  
  
    -   UniqueId  
  
    -   UnsignedInt  
  
### <a name="see-also"></a>Siehe auch  
 [Festlegen von Feldwerten mithilfe von Parametern, die an ein Formular übergeben werden](set-field-values-using-parameters-passed-form.md)   
 [Öffnen von Formularen und Ansichten mit einer URL](open-forms-views-dialogs-reports-url.md)
