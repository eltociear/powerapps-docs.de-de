---
title: Hinzufügen eines benutzerdefinierten Domänennamens | Microsoft-Dokumentation
description: Anweisungen zum Hinzufügen eines benutzerdefinierten Domänennamens.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c36a077233a83b6246634cfc456d51deec14cf40
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867366"
---
# <a name="add-a-custom-domain-name"></a>Einen benutzerdefinierten Domänennamen hinzufügen

Eine benutzerdefinierte Domäne kann Ihren Kunden helfen, die Supportressource einfacher zu finden und Ihre Marke sichtbarer zu machen. Nur ein benutzerdefinierter Domänenname kann einem Portal hinzugefügt werden. Nachdem Sie Ihr Portal bereitgestellt haben und Ihren Domänennamen erhalten haben, brauchen Sie ein SSL-Zertifikat, um einen benutzerdefinierten Hostnamen zu installieren. Sie können das erworbene SSL-Zertifikat für Ihre Domäne verwenden, um das Portal mit einer benutzerdefinierten Domäne mithilfe des Assistenten zu verknüpfen.

1. Öffnen Sie das [Admin Center für Power Apps-Portale](admin-overview.md).

2. Gehen Sie zu **Portalaktionen** > **Benutzerdefinierten Domänenamen hinzufügen**. Ein Assistent wird geöffnet, um das SSL-Zertifikat auszuwählen.

3. Wählen Sie auf der Seite **SSL-Zertifikat auswählen** eine der folgenden Optionen aus:
   - **Ein neues Zertifikat hochladen**: Wählen Sie diese Option, um die .pfx-Datei hochzuladen, falls Sie sie noch nicht zur Organisation hochgeladen haben. Klicken Sie auf die Schaltfläche „Hochladen” unter **Datei** und wählen Sie die .pfx-Datei aus. Nach dem Auswählen der Datei, geben Sie das Kennwort für das SSL-Zertifikat im Feld **Kennwort** ein.
   - **Ein vorhandenes Zertifikat verwenden**: Wählen Sie diese Option, um das richtige Zertifikat von der Dropdownliste auszuwählen.

     > [!Note]
     > Das SSL-Zertifikat muss alle folgenden Voraussetzungen erfüllen:
     > - Unterzeichnet von einer vertrauenswürdigen Zertifizierungsstelle
     > - Exportiert als eine kennwortgeschützte PFX-Datei
     > - Enthält privaten Schlüssel mindestens 2048 Bits lang
     > - Enthält alle Zwischenzertifikate in der Zertifikatskette
     > - SHA2 muss aktiviert sein; SHA1-Unterstüzungen wird aus gängigen Browsern entfernt

4. Wählen Sie **Weiter**.

5. Wählen Sie auf der Seite **Host-Namen auswählen** eine der folgenden Optionen aus:
    - **Einen neuen Hostnamen hinzufügen**: Wählen Sie diese Option, um eine neue benutzerdefinierte Domäne zu erstellen. Geben Sie den gewünschten Domänennamen in das Feld **Domänenname** ein.
    - **Einen vorhandenen Hostnamen verwenden**: Wählen Sie diese Option, um einen Hostnamen aus der Dropdownliste auszuwählen. 
   
   > [!Note]
   > - Sie können nur einen benutzerdefinierten Domänennamen für ein Portal haben. 
   > - Um einen benutzerdefinierten Hostnamen zu erstellen, müssen Sie ein CNAME mit Ihrem Domänenanbieter erstellen, der Ihre Domäne auf die URL von Ihrem Portal leitet. Wenn Sie nur einen CNAME bei Ihrem Domänenanbieter hinzugefügt haben, kann die Verteilung an alle DNS-Servern einige Zeit dauern. Wenn der Name nicht verteilt wird, und Sie ihn hier hinzufügen, wird folgende Fehlermeldung angezeigt: „Fügen Sie diesem Domänennamen einen CNAME-Datensatz hinzu”. Versuchen Sie es nach einiger Zeit erneut.

6. Überprüfen Sie die Informationen, die Sie eingegeben haben, und klicken Sie dann auf **Weiter**, um mit dem Erstellen der SSL-Bindung zu beginnen. Sie sollten die Nachricht sehen: Der benutzerdefinierte Domänenname wurde für dieses Portal erfolgreich konfiguriert. Sie können jetzt zu {Custom Domain Name} gehen, um auf dieses Portal zuzugreifen." {Custom Domain Name} wird ein Hyperlink zur URL des benutzerdefinierten Portals sein, die gerade konfiguriert wurde.

7. Klicken Sie auf **Fertig stellen**, um den Assistenten zu beenden.

    > [!Note]
    > Wenn Sie Ihren vorhandenen benutzerdefinierten Domänennamen ändern möchten, müssen Sie ein neues SSL-Zertifikat hochladen und die Schritte in diesem Abschnitt befolgen.
    

