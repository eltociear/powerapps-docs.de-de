---
title: Hinzufügen eines benutzerdefinierten Domänen Namens | MicrosoftDocs
description: Anweisungen zum Hinzufügen eines benutzerdefinierten Domänen Namens.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cd015b656c90ec2707f3654e02b4e1a5ef65e7d2
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543110"
---
# <a name="add-a-custom-domain-name"></a>Hinzufügen eines benutzerdefinierten Domänennamens

Eine benutzerdefinierte Domäne kann Ihren Kunden dabei helfen, Ihre Support Ressourcen leichter zu finden und Ihre Marke zu verbessern. Einem Portal kann nur ein benutzerdefinierter Domänen Name hinzugefügt werden. Nachdem Sie Ihr Portal bereitgestellt und ihren Domänen Namen erworben haben, benötigen Sie ein SSL-Zertifikat, um einen benutzerdefinierten Hostnamen einzurichten. Sie können das erworbene SSL-Zertifikat für Ihre Domäne verwenden, um Ihr Portal mithilfe eines Assistenten mit einer benutzerdefinierten Domäne zu verknüpfen.

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wechseln Sie zu **Portal Aktionen** , > **einen benutzerdefinierten Domänen Namen hinzuzufügen**. Ein Assistent wird geöffnet, um das SSL-Zertifikat auszuwählen.

3. Wählen Sie auf der Seite **Wählen Sie ein SSL-Zertifikat** aus eine der folgenden Optionen aus:
   - **Neues Zertifikat hochladen**: Wählen Sie diese Option aus, um die PFX-Datei hochzuladen, wenn Sie Sie noch nicht in die Organisation hochgeladen haben. Wählen Sie unterhalb der **Datei** die Schaltfläche Hochladen aus, um die PFX-Datei auszuwählen. Nachdem Sie die Datei ausgewählt haben, geben Sie im Feld **Kennwort** das Kennwort für das SSL-Zertifikat ein.
   - **Vorhandenes Zertifikat verwenden**: Wählen Sie diese Option aus, um in der Dropdown Liste das richtige Zertifikat auszuwählen.

     > [!Note]
     > Das SSL-Zertifikat muss die folgenden Anforderungen erfüllen:
     > - Von einer vertrauenswürdigen Zertifizierungsstelle signiert
     > - Exportiert als Kenn Wort geschützte PFX-Datei
     > - Enthält einen privaten Schlüssel mit mindestens 2048 Bits.
     > - Enthält alle zwischen Zertifikate in der Zertifikat Kette.
     > - Muss SHA2 aktiviert sein; SHA1-Unterstützung wird aus gängigen Browsern entfernt

4. Wählen Sie **Weiter**.

5. Wählen Sie auf der Seite **Wählen Sie einen Hostnamen** aus eine der folgenden Optionen aus:
    - **Neuen Hostnamen hinzufügen**: Wählen Sie diese Option aus, um eine neue benutzerdefinierte Domäne zu erstellen. Geben Sie den gewünschten Domänen Namen in das Feld **Domänen Name** ein.
    - **Vorhandenen Hostnamen verwenden**: Wählen Sie diese Option aus, um einen Hostnamen aus der Dropdown Liste auszuwählen. 
   
   > [!Note]
   > - Sie können nur einen benutzerdefinierten Domänen Namen für ein Portal haben. 
   > - Um einen benutzerdefinierten Hostnamen zu erstellen, müssen Sie einen CNAME mit Ihrem Domänen Anbieter erstellen, der Ihre Domäne auf die URL Ihres Portals verweist. Wenn Sie dem Domänen Anbieter soeben einen CNAME hinzugefügt haben, dauert es einige Zeit, bis alle DNS-Server verteilt werden. Wenn der Name nicht weitergegeben wird und Sie ihn hier hinzufügen, wird die folgende Fehlermeldung angezeigt: Fügen Sie diesem Domänen Namen einen CNAME-Datensatz hinzu. Versuchen Sie es nach einiger Zeit noch mal.

6. Überprüfen Sie die eingegebenen Informationen, und klicken Sie dann auf **weiter** , um mit dem Erstellen der SSL-Bindung zu beginnen. Es sollte angezeigt werden, dass der benutzerdefinierte Domänen Name für dieses Portal erfolgreich konfiguriert wurde. Sie können jetzt "{Custom Domain Name}" aufrufen, um auf dieses Portal zuzugreifen. {Custom Domain Name} ist ein Link zur benutzerdefinierten Portal-URL, die soeben konfiguriert wurde.

7. Wählen Sie **Fertig** stellen aus, um den Assistenten zu schließen.

    > [!Note]
    > Wenn Sie den vorhandenen benutzerdefinierten Domänen Namen ändern möchten, müssen Sie ein neues SSL-Zertifikat hochladen und die in diesem Abschnitt beschriebenen Schritte ausführen.
    

