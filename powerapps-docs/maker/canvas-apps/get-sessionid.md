---
title: Abrufen einer Sitzungs-ID oder einer Canvas-App-ID | Microsoft-Dokumentation
description: Schritte zum Abrufen einer Sitzungs-ID oder einer Canvas-App-ID für die Problembehandlung in PowerApps
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 81c1db4ab44f3ca8517c6154f0516ca9dad5f825
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74676514"
---
# <a name="get-a-session-id-or-a-canvas-app-id"></a>Abrufen einer Sitzungs-ID oder einer Canvas-App-ID
Wenn ein Problem mit einer Canvas-App auftritt, die in powerapps erstellt wurde, können Sie Microsoft dabei helfen, das Problem wesentlich effektiver zu beheben, wenn Sie Ihnen eine Sitzungs-ID, eine APP-ID oder beides für dieses Problem bereitstellen.

## <a name="get-the-session-id"></a>Abrufen einer Sitzungs-ID

### <a name="when-editing-an-app"></a>Beim Bearbeiten einer App
1. Wählen Sie oben links **Datei** aus.

1. Wählen Sie **Konto** aus.

1. Wählen Sie unter **Diagnose** die Option **Sitzungsdetails** aus.

    ![Eine Sitzungs-ID aus Power apps Studio erhalten](media/get-sessionid/studio.png)

### <a name="when-running-an-app-in-a-browser"></a>Beim Ausführen einer App in einem Browser
1. Wählen Sie oben rechts das Zahnradsymbol aus.

1. Wählen Sie **Sitzungsdetails** aus.

    ![Abrufen einer Sitzungs-ID aus einem Browser](media/get-sessionid/browser.png)

### <a name="when-running-an-app-on-a-phone-or-a-tablet"></a>Beim Ausführen einer App auf einem Telefon oder Tablet
1. Wischen Sie nach rechts.

1. Tippen Sie auf **Sitzungsdetails**.

    ![Abrufen einer Sitzungs-ID aus einem Browser](media/get-sessionid/mobile.png)

### <a name="when-running-an-embedded-app-or-form"></a>Beim Ausführen einer eingebetteten App oder eines eingebetteten Formulars
1. Führen Sie einen der folgenden Schritte aus:

    - Halten Sie die ALT-TASTE gedrückt, und klicken Sie mit der rechten Maustaste auf die App oder das Formular.
    - Tippen Sie mit zwei Fingern für 1 bis 2 Sekunden auf die App oder das Formular, und lassen Sie dann los.

1. Wählen Sie **Sitzungsdetails** aus.

    ![Abrufen einer Sitzungs-ID aus einer eingebetteten App](media/get-sessionid/embedded.png)

## <a name="get-an-app-id"></a>Abrufen einer App-ID
1. [Melden Sie sich bei PowerApps an](https://powerapps.microsoft.com).

1. Wählen Sie am linken Rand **Apps** aus.

1. Wählen Sie die Auslassungspunkte ( **. . .** ) für die App aus, für die Sie die Problembehandlung durchführen, und wählen Sie dann **Details** aus.

    ![Wechseln zu den App-Details](./media/get-sessionid/details.png)

    Die App-ID wird unten im Bereich **Details** für die App angezeigt.

    ![Kopieren der App-ID aus den Detailinformationen](./media/get-sessionid/app-id.png)
