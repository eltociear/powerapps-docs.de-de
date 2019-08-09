---
title: Einschränkungen des PowerApps-Komponentenframeworks | MicrosoftDocs
description: Einschränkungen bei der Verwendung des PowerApps-Komponentenframeworks
author: nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
---

# <a name="limitations-of-powerapps-component-framework"></a>Einschränkungen des PowerApps-Komponentenframeworks

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Mit der Version des PowerApps-Komponentenframeworks können Sie jetzt eigene benutzerdefinierte Komponenten erstellen, um die Benutzerfreundlichkeit in modellgesteuerten Apps zu verbessern. Obwohl Sie eigene Komponenten erstellen können, gibt es einige Einschränkungen, die Entwickler beschränken, die einige Funktionen in benutzerdefinierten Komponenten implementieren. Es folgen einige der Einschränkungen:

## <a name="support-for-external-libraries"></a>Support für externe Bibliotheken

Für eine öffentliche Vorschau können Komponenten allen Code einschließlich externer Bibliotheksinhalte im primären Codepaket bündeln. Wenn Sie ein Beispiel dafür sehen möchten, wie die PowerApps-Befehlszeilenschnittstelle beim Packen Ihres externen Bibliotheksinhalts in ein Komponentenspezifisches Paket helfen kann, sehen Sie sich das Beispiel [Angular-Kippkomponente](sample-controls/angular-flip-control.md) an

> [!NOTE]
> Unterstützung für freigegebene Bibliotheken mittels Bibliotheksknoten im Komponentenmanifest wird für öffentliche Vorschau nicht unterstützt. Es prüfen dies und werden diese Funktion in einer zukünftigen Versionen hinzufügen.

## <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)
