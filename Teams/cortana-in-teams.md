---
title: Cortana Sprachunterstützung in Microsoft Teams
author: cichur
ms.author: v-cichur
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: akshbhat
search.appverid: MET150
description: Erfahren Sie, wie Cortana-Sprachunterstützung bei Teams
ms.localizationpriority: medium
ms.custom:
- Teams-upgrade-guidance
f1.keywords:
- NOCSH
ms.collection:
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
ms.openlocfilehash: 10d42d2cd2f876f27153336695e4639830c5bb91
ms.sourcegitcommit: 15e90083c47eb5bcb03ca80c2e83feffe67646f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2021
ms.locfileid: "58726144"
---
# <a name="cortana-voice-assistance-in-teams"></a>Cortana Sprachunterstützung in Teams

> [!Note]
> Cortana Sprachunterstützung wird in mobilen Microsoft Teams-Apps für iOS und Android und Microsoft Teams-Anzeigen für Benutzer in den USA, Großbritannien, Kanada, Indien und Australien unterstützt. Microsoft Teams-Räume auf Windows wird nur für Benutzer in den USA unterstützt. Cortana Sprachunterstützung für Mandanten von GCC, GCC-High, DoD und anderen Bildungsorganisationen als den USA ist derzeit nicht verfügbar. Cortana Sprachunterstützung in der mobilen Teams-App ist jetzt für EDU-Kunden in en-US verfügbar. Die Erweiterung auf weitere Sprachen und Regionen wird im Rahmen zukünftiger Versionen sein.

> [!Note]
> Cortana Sprachunterstützung in Microsoft Teams-Räume wird unter Preview veröffentlicht. In der Preview-Version wird Cortana in den USA nur mit der Sprache EN-US auf Geräten mit angeschlossenen Mikrofonen von Usa unterstützt.

Cortana Sprachunterstützung in der mobilen Teams-App, auf Microsoft Teams-Räume auf Windows und auf Microsoft Teams-Anzeigegeräten ermöglicht es Microsoft 365 Enterprise-Benutzern, die Kommunikation, Zusammenarbeit und Besprechungsaufgaben mithilfe gesprochener natürlicher Sprache zu optimieren. Benutzer können mit Cortana sprechen, indem sie die Mikrofonschaltfläche auswählen, die sich oben rechts in der mobilen Teams-App befindet, oder indem sie &#8220;Cortana&#8221; im Microsoft Teams Room sagen oder eine Microsoft Teams verwenden. Um schnell freihändig mit dem Team in Verbindung zu gehen und unterwegs zu sein, können Benutzer Abfragen wie &#8220;Megan&#8221; oder &#8220;eine Nachricht an meine nächste Besprechungs-E-Mail senden&#8221;. Benutzer können an Besprechungen teilnehmen, indem sie sagen&#8220;an meiner nächsten Besprechung teilnehmen&#8221; und mithilfe von Sprachunterstützung Dateien freigeben, ihren Kalender überprüfen und vieles mehr. Diese Sprachunterstützungserfahrungen werden mithilfe von [Cortana-Diensten](/microsoft-365/admin/misc/cortana-integration?view=o365-worldwide) auf Unternehmensklasse übermittelt, die gemäß den Bedingungen für [Onlinedienste (OST)](https://www.microsoft.com/licensing/product-licensing/products?rtc=1)vollständig den Datenschutz-, Sicherheits- und Compliance-Zusagen von Office 365 entsprechen.

## <a name="admin-control-and-limitations"></a>Administratorkontrolle und -beschränkungen

Cortana Sprachunterstützung in Teams wird mithilfe von Diensten übermittelt, die gemäß den Bedingungen für Onlinedienste (OST) vollständig den Zusagen auf Office 365 Unternehmensebene hinsichtlich Datenschutz, Sicherheit und Compliance entsprechen. Das Feature wird für Mandanten standardmäßig aktiviert.

Mandantenadministratoren können mithilfe einer Richtlinie (TeamsCortanaPolicy) steuern, wer in ihrem Mandanten Cortana Sprachunterstützung in Teams verwenden kann. Diese Richtlinie wird entweder auf Benutzerkonto- oder Mandantenebene festgelegt. Administratoren können das Feld CortanaVoiceInvocationMode innerhalb dieses Richtliniensteuerelements verwenden, um festzustellen, ob Cortana deaktiviert ist, ob es nur über den Aufruf von Schaltflächen oder auch über den Aufruf eines Reaktivierungsworts aktiviert ist (gilt für Geräte, die dies unterstützen, z. B. die Microsoft Teams-Anzeige).

Administratoren können diese Richtlinie mithilfe der folgenden PowerShell-Cmdlets verwalten (die Richtlinie ist Microsoft Teams Admin Center derzeit nicht verfügbar).

- [New-CsTeamsCortanaPolicy](/powershell/module/skype/New-CsTeamsCortanaPolicy)

- [Get-CsTeamsCortanaPolicy](/powershell/module/skype/Get-CsTeamsCortanaPolicy)

- [Grant-CsTeamsCortanaPolicy](/powershell/module/skype/Grant-CsTeamsCortanaPolicy)

- [Set-CsTeamsCortanaPolicy](/powershell/module/skype/Set-CsTeamsCortanaPolicy)

- [Remove-CsTeamsCortanaPolicy](/powershell/module/skype/Remove-CsTeamsCortanaPolicy)

Mit dem folgenden Befehl wird beispielsweise eine neue Richtlinie mit dem Namen &#8220;EmployeeCortanaPolicy&#8221; erstellt, Cortana die Sprachunterstützung in Microsoft Teams deaktiviert ist.  

```PowerShell
PS C:\> New-CsTeamsCortanaPolicy -Identity EmployeeCortanaPolicy -CortanaVoiceInvocationMode Disabled
```

Dieses Beispiel zeigt das Aktualisieren einer vorhandenen Richtlinie mit dem Namen &#8220;EmployeeCortanaPolicy&#8221; und das Aktivieren von Cortana-Sprachunterstützung in Microsoft Teams nur durch Aufruf der Schaltflächen. Benutzer können Ihr Mikrofon Cortana, indem sie die Schaltfläche Cortana Mikrofons im Teams. Der Reaktivierungsaufruf &#8220;Hey Cortana&#8221; oder &#8220;Cortana&#8221;) wird deaktiviert.  

```PowerShell
PS C:\> Set-CsTeamsCortanaPolicy -Identity EmployeeCortanaPolicy -CortanaVoiceInvocationMode PushToTalkUserOverride
```

In diesem Beispiel wird gezeigt, wie die Richtlinie aktualisiert und Cortana Sprachunterstützung sowohl über die Schaltfläche als auch durch den Reaktivierungsaufruf aktiviert wird.

```PowerShell
PS C:\> Set-CsTeamsCortanaPolicy -Identity EmployeeCortanaPolicy -CortanaVoiceInvocationMode WakeWordPushToTalkUserOverride
```

Zum Zeitpunkt der ersten Version für benutzer Microsoft 365 Enterprise in den USA in Englisch sind die folgenden Funktionen verfügbar:

- Die Teams mobilen App unterstützt nicht die Aktivierung von Reaktivierungsworten, wird aber in Zukunft unterstützt.  

- Microsoft Teams-Räume auf Windows und Microsoft Teams-Anzeigegeräten unterstützt die Aktivierung von Reaktivierungsworten.

## <a name="user-control"></a>Benutzersteuerelement

Einzelne Benutzer können versuchen, Cortana Sprachunterstützung auf verschiedenen Geräten zu erhalten:

- Wählen Sie in der mobilen Teams Mikrofonschaltfläche aus.

- Wählen Sie die Mikrofonschaltfläche aus, oder sagen Cortana Mikrofon", Microsoft Teams-Räume.

- Sagen Sie "Cortana", wenn Microsoft Teams geräte anzeigt.

Sie können steuern, Cortana in Teams Gerät aktiviert ist, indem Sie eine Einstellung auf dem Gerät verwenden.

![zeigt die Entwicklung mobiler Fenster an, wenn Sie Cortana.](media/cortana-mobile-sequence.png)

### <a name="microsoft-teams-rooms-on-windows"></a>Microsoft Teams-Räume auf Windows

Das Vornehmen von Änderungen auf Geräteebene ist verfügbar, Cortana auf Mandantenebene aktiviert ist. Cortana wird standardmäßig AUS freigegeben.

Um die Cortana auf Geräteebene zu aktivieren, müssen die folgenden XML-Attribute in der SkypeSettings-XML-Datei hinzugefügt werden:

```xml
<SkypeSettings>  

        <CortanaEnabled>true</CortanaEnabled>  

        <CortanaWakewordEnabled>true</CortanaWakewordEnabled>  

</SkypeSettings> 
```

Das Vornehmen von Änderungen auf Besprechungsebene ist verfügbar, Cortana auf Geräteebene aktiviert ist.

Um während einer Cortana Sprachunterstützung zu aktivieren, verschieben Sie die Umschalt auf **Ein** oder **Aus.** Nachdem die Besprechung beendet wurde, Cortana Sie zu den auf Geräteebene festgelegten Einstellungen zurück.
