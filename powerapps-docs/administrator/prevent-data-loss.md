---
title: Verwalten von Richtlinien zur Verhinderung von Datenverlust (DLP) | Microsoft-Dokumentation
description: Exemplarische Vorgehensweise zum Verwalten von Richtlinien zur Verhinderung von Datenverlust für PowerApps.
services: powerapps
suite: powerapps
documentationcenter: na
author: manasmams
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: manasma
ms.openlocfilehash: f02e9023deb2bc0d11e9d94414f9e78651cab2b5
ms.sourcegitcommit: aa2d0166dccb38100183c093f293233b46f3669d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2018
---
# <a name="manage-data-loss-prevention-dlp-policies"></a>Verwalten von Richtlinien zur Verhinderung von Datenverlust (DLP)
Die Daten einer Organisation sind wichtig für deren Erfolg. Die Daten müssen zur Verwendung bereitstehen, damit Entscheidungen schnell getroffen werden können. Sie müssen jedoch auch geschützt werden, damit sie nicht für Parteien freigegeben werden können, die keinen Zugriff darauf haben sollten. Mithilfe von PowerApps können Sie zum Schutz dieser Daten Richtlinien zur Verhinderung von Datenverlust (DLP) erstellen und erzwingen, in denen definiert wird, für welche Verbraucherconnectors bestimmte Geschäftsdaten freigegeben werden können. Beispielsweise möchte eine Organisation, die PowerApps verwendet, möglicherweise nicht, dass ihre in SharePoint gespeicherten Unternehmensdaten automatisch in Ihrem Twitter-Feed veröffentlicht werden.

Damit Sie DLP-Richtlinien erstellen, bearbeiten oder löschen können, müssen Sie entweder über Umgebungsadministratorrechte oder über Azure Active Directory Mandantenadministratorrechte verfügen. Weitere Informationen finden Sie unter [Environments administration in PowerApps (Verwalten von Umgebungen in PowerApps)](environments-administration.md).

Anleitungen zum Erstellen einer DLP-Richtlinie finden Sie unter [Quickstart: Create a data loss prevention (DLP) policy (Schnellstart: Erstellen einer Richtlinie zur Verhinderung von Datenverlust (DLP))](create-dlp-policy.md).

## <a name="find-a-dlp-policy"></a>Suchen einer DLP-Richtlinie
1. Melden Sie sich unter [https://admin.poweraps.com]([https://admin.powerapps.com) im Admin Center an.
2. Klicken oder tippen Sie im Navigationsbereich auf **Datenrichtlinien**. Wenn Sie über eine lange Liste von Richtlinien verfügen, können Sie über das **Suchfeld** einzelne DLP-Richtlinien suchen.

    ![](./media/prevent-data-loss/data-policies.png)

## <a name="edit-a-dlp-policy"></a>Bearbeiten einer DLP-Richtlinie
1. Klicken oder tippen Sie in der Liste mit den DLP-Richtlinien neben der Richtlinie, die Sie gerne ändern möchten, auf das Stiftsymbol.

    ![Anmelden](./media/prevent-data-loss/3.png)
2. Nehmen Sie die gewünschten Änderungen vor, und klicken oder tippen Sie dann auf **Richtlinie speichern**.

    > [!NOTE]
    > DLP-Richtlinien für Umgebungen können mandantenweite DLP-Richtlinien nicht überschreiben.
    >
    >

    Wenn Sie die Änderungen überprüfen möchten, suchen Sie die DLP-Richtlinie in der Liste mit den Richtlinien zur Verhinderung von Datenverlust, und klicken oder tippen Sie darauf, um die Eigenschaften zu überprüfen.

## <a name="delete-a-dlp-policy"></a>Löschen einer DLP-Richtlinie
1. Klicken oder tippen Sie in der Liste mit den DLP-Richtlinien neben der Richtlinie, die Sie löschen möchten, auf das Papierkorbsymbol.

    ![Anmelden](./media/prevent-data-loss/3-delete.png)
4. Klicken oder tippen Sie im Bestätigungsdialogfeld auf **Löschen**.

    Dann wird die Richtlinie gelöscht und wird nicht mehr in der Liste der DLP-Richtlinien angezeigt.

## <a name="next-steps"></a>Nächste Schritte
* [Erfahren Sie mehr über Umgebungen](environments-administration.md)
* [Erfahren Sie mehr über Microsoft PowerApps](../maker/canvas-apps/getting-started.md)
