---
title: Verwalten von Voice Routing-Richtlinien für Direct Routing
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
f1.keywords:
- NOCSH
ms.collection:
- M365-voice
appliesto:
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Erfahren Sie, wie Sie Voice Routing-Richtlinien in Ihrem Microsoft Teams.
ms.openlocfilehash: 1717f1b0400f67346034bd9e92bd698305fdd324
ms.sourcegitcommit: 15e90083c47eb5bcb03ca80c2e83feffe67646f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2021
ms.locfileid: "58727094"
---
# <a name="manage-voice-routing-policies-for-direct-routing"></a>Verwalten von Voice Routing-Richtlinien für Direct Routing

Wenn Sie Telefonsystem [Direct Routing](direct-routing-landing-page.md) in Ihrer Organisation bereitgestellt haben, verwenden Sie Voice Routing-Richtlinien, um Teams- und Skype for Business Online-Benutzern das Empfangen und Anrufen bei dem öffentlichen Telefonnetz (Public Switched Telephone Network, PSTN) mithilfe Ihrer lokalen Telefonieinfrastruktur zu ermöglichen.

Eine Voice Routing-Richtlinie ist ein Container für PSTN-Nutzungsdatensätze. Sie erstellen und verwalten Voice Routing-Richtlinien, indem Sie zu **Voice Voice** Routing policies im Microsoft Teams Admin Center oder mithilfe von  >   Windows PowerShell.

Sie können die globale (organisationsweite Standard-) Richtlinie verwenden oder benutzerdefinierte Richtlinien erstellen und zuweisen. Benutzer erhalten die globale Richtlinie automatisch, es sei denn, Sie erstellen und weisen eine benutzerdefinierte Richtlinie zu. Beachten Sie, dass Sie die Einstellungen in der globalen Richtlinie bearbeiten, aber nicht umbenennen oder löschen können.

Es ist wichtig zu wissen, dass benutzer beim Zuweisen einer Sprachroutingrichtlinie nicht in der Lage sind, pstN-Anrufe in Teams. Darüber hinaus müssen Sie den Benutzer für das direkte Routing Telefonsystem und andere Konfigurationsschritte ausführen. Weitere Informationen finden Sie unter [Konfigurieren von Direct-Routing.](direct-routing-configure.md)

## <a name="create-a-custom-voice-routing-policy"></a>Erstellen einer benutzerdefinierten Voice Routing-Richtlinie

### <a name="using-the-microsoft-teams-admin-center"></a>Verwenden des Microsoft Teams Admin Centers

1. Navigieren Sie in der linken Navigationsleiste Microsoft Teams Admin Center zu **Voice Voice** Voice  >  **Routing Policies**, und klicken Sie dann auf **Hinzufügen**.<br>
    ![Screenshot der Seite "Voice Routing Policy hinzufügen" im Microsoft Teams Admin Center.](media/manage-voice-routing-policies.png) 
2. Geben Sie einen Namen und eine Beschreibung für die Richtlinie ein.
3. Klicken **Sie unter PSTN-Nutzungsdatensätze** auf **PSTN-Nutzung hinzufügen**, und wählen Sie dann die Einträge aus, die Sie hinzufügen möchten. Wenn Sie einen neuen PSTN-Nutzungsdatensatz erstellen müssen, klicken Sie auf **Hinzufügen**.
4. Wenn Sie mehrere PSTN-Nutzungsdatensätze hinzugefügt haben, ordnen Sie diese in der von Ihnen verwendeten Reihenfolge an.
5. Wenn Sie fertig sind, klicken Sie auf **Übernehmen**.
6. Klicken Sie auf **Speichern**.

### <a name="using-powershell"></a>Verwendung von PowerShell

Weitere [Informationen finden Sie unter New-CsOnlineVoiceRoutingPolicy.](/powershell/module/skype/new-csonlinevoiceroutingpolicy)

## <a name="edit-a-voice-routing-policy"></a>Bearbeiten einer Voice Routing-Richtlinie

### <a name="using-the-microsoft-teams-admin-center"></a>Verwenden des Microsoft Teams Admin Centers

Sie können die globale Standardrichtlinie bearbeiten oder eine von Ihnen erstellte, benutzerdefinierte Richtlinie zuweisen.

1. Navigieren Sie in der linken Navigationsleiste Microsoft Teams Admin Center zu **Voice Voice**  >  **Routing Policies**.
2. Wählen Sie die Richtlinie aus, indem Sie zunächst links neben die Richtlinienbezeichnung und dann auf **Bearbeiten** klicken.
3. Klicken **Sie auf PSTN-Nutzungsdatensätze hinzufügen/entfernen**, nehmen Sie die von Ihnen vorgenommenen Änderungen vor, und klicken Sie dann auf **Speichern.**

### <a name="using-powershell"></a>Verwendung von PowerShell

Weitere [Informationen finden Sie unter Set-CsOnlineVoiceRoutingPolicy.](/powershell/module/skype/set-csonlinevoiceroutingpolicy)

## <a name="assign-a-custom-voice-routing-policy-to-users"></a>Zuweisen einer benutzerdefinierten Voice Routing-Richtlinie zu Benutzern

[!INCLUDE [assign-policy](includes/assign-policy.md)]

Siehe auch [Grant-CsOnlineVoiceRoutingPolicy.](/powershell/module/skype/grant-csonlinevoiceroutingpolicy)

## <a name="related-topics"></a>Verwandte Themen

[Übersicht über PowerShell für Microsoft Teams](teams-powershell-overview.md)

[Konfigurieren von Voice Routing für Direct Routing](direct-routing-voice-routing.md)

[Aktivieren des standortbasierten Routings für direktes Routing](location-based-routing-enable.md)

[Zuweisen von Richtlinien zu Benutzern in Teams](assign-policies.md)