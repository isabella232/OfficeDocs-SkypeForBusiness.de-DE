---
title: Einschränkungen für ausgehende Anrufe – Audiokonferenzen & PSTN-Anrufe
ms.reviewer: ''
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection:
- M365-voice
audience: Admin
appliesto:
- Skype for Business
- Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Audio Conferencing
- seo-marvel-mar2020
description: Administratoren können die Art von Audiokonferenzen und PSTN-Anrufen für Endbenutzer steuern, die von Benutzern vorgenommen werden können.
ms.openlocfilehash: fe63a29bf4cde46ee881d7a425839073ed4b4b7f
ms.sourcegitcommit: 15e90083c47eb5bcb03ca80c2e83feffe67646f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2021
ms.locfileid: "58730324"
---
# <a name="outbound-calling-restriction-policies-for-audio-conferencing-and-user-pstn-calls"></a>Einschränkungsrichtlinien für ausgehende Anrufe für Audiokonferenzen und PSTN-Anrufe

Als Administrator können Sie Steuerelemente für ausgehende Anrufe verwenden, um die Art von Audiokonferenzen und PSTN-Anrufen (Public Switched Telephone Network) für Endbenutzer einzuschränken, die von Benutzern in Ihrer Organisation vorgenommen werden können.

Steuerelemente für ausgehende Anrufe können pro Benutzer oder auf Mandantenbasis angewendet werden und stellen die folgenden beiden Steuerelemente zur unabhängigen Beschränkung der einzelnen Arten von ausgehenden Anrufen zur Verfügung. Standardmäßig sind beide Steuerelemente so eingestellt, dass sie internationale und ausgehende Anrufe im Inland zulassen.

|Steuerelement|Beschreibung|Steuerelementoptionen|
|:-----|:-----|:-----|
|PSTN-Anrufe für Audiokonferenzen|Schränkt den Ausgehenden Typ ein. </br>Aufrufe, die von innerhalb </br>von einem Benutzer organisierte Besprechungen.|Beliebiges Ziel (Standard)</br>Im selben Land oder in derselben Region wie der Organisator </br> [Nur Länder oder Regionen in](audio-conferencing-zones.md) Zone A </br>Nicht zulassen|
|PSTN-Anrufe durch Endbenutzer|Beschränkt die Art der Anrufe </br>die von einem Benutzer vorgenommen werden können.|International und Inland (Standard)</br>Inlandsanruf</br>Keine|

Wenn Sie herausfinden müssen, welche Länder und Regionen als Zone A gelten, lesen Sie Länder- und [Regionszonen für Audiokonferenzen.](audio-conferencing-zones.md)

   > [!NOTE]
   > Ein Anruf gilt als Inlandsnummer, wenn sich die gewählte Nummer in demselben Land befindet, in dem Microsoft 365 oder Office 365 für den Organisator der Besprechung (bei Audiokonferenzen) oder für den Endbenutzer (bei PstN-Anrufen des Endbenutzers) eingerichtet wurde.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## <a name="restrict-audio-conferencing-outbound-calls"></a>Einschränken ausgehender Anrufe bei Audiokonferenzen

![das Microsoft Teams Logo.](media/teams-logo-30x30.png) **Verwenden des Microsoft Teams Admin Centers**

1. Wählen Sie im linken Navigationsbereich **Benutzer** aus, und wählen Sie dann den Anzeigenamen des Benutzers aus der Liste der verfügbaren Benutzer aus.

3. Wählen Sie **neben Audiokonferenz die** Option **Bearbeiten aus.**

4. Wählen **Sie unter Auswahl aus Besprechungen** die Option zum Einwählen aus, die Sie verwenden möchten.

5. Klicken Sie auf **Speichern**.

![Ein Symbol mit dem Skype for Business Logo.](media/sfb-logo-30x30.png) **Verwenden des Skype for Business Admin Centers**

1. Wechseln Sie **Skype for Business Admin Center** in der linken Navigationsleiste zu Audio **conferencing** Users , und wählen Sie dann den Benutzer aus der Liste  >  der verfügbaren Benutzer aus.

2. Wählen Sie im Aktionsbereich Bearbeiten **aus.**

3.  Wählen **Sie unter Einschränkungen für Das Auswählen** aus Besprechungen dieses Benutzers die option zum Einwahleinschränkungsoption aus.

      ![Die Einschränkungen für Auswahloptionen.](media/restrictions-to-dial-outs.png)

4. Klicken Sie auf **Speichern**.

> [!Note]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

**Verwendung von PowerShell**

Einschränkungen für ausgehende Anrufe werden durch eine einzelne Richtlinie mit dem Namen OnlineDialOutPolicy gesteuert, die jeweils über ein Einschränkungsattribut verfügt. Die Richtlinie kann nicht angepasst werden, sondern es gibt vordefinierte Richtlinieninstanzen für jede Kombination der Einstellungen.

Mit dem cmdlet Get-CSOnlineDialOutPolicy ausgehende Anrufe können Sie die Richtlinien für ausgehende Anrufe anzeigen und den folgenden Befehl für das Setup verwenden.

**Legen Sie die Richtlinie auf Benutzerebene mit dem folgenden Cmdlet festgelegt.** (Das Cmdlet "Grant" enthält nicht wie das Cmdlet "Get" das Wort "Online".)

```
Grant-CsDialoutPolicy -Identity <username> -PolicyName <policy name>    
```

**Legen Sie die Richtlinie auf Mandantenebene mit dem folgenden Cmdlet festgelegt.**

```
Grant-CsDialoutPolicy  -Tenant <guid> -PolicyName <policy name>  -Global 
```

Alle Benutzer des Mandanten, denen keine Wählrichtlinie zugewiesen ist, erhalten diese Richtlinie. Andere Benutzer bleiben bei ihrer aktuellen Richtlinie.

Die folgende Tabelle enthält eine Übersicht über die einzelnen Richtlinien.

|PowerShell-Cmdlet|Beschreibung|
|:-----|:-----|
|Identity='tag:DialoutCPCandPSTNInternational'    |    Benutzer in der Konferenz können internationale und inlandsnummern anrufen, und dieser Benutzer kann auch ausgehende Anrufe an internationale nummern und Nummern im Inland anrufe.    |
|Identity='tag:DialoutCPCDomesticPSTNInternational'  |    Nutzer der Konferenz können nur Inlandsnummern anrufen, und dieser Benutzer kann ausgehende Anrufe an internationale und inlandsnummern abwählen.    |
|    Identity='tag:DialoutCPCDisabledPSTNInternational'    |    Die Nutzer der Konferenz können keine Verbindungen aus einer Konferenz herausrufen. Dieser Benutzer kann ausgehende Anrufe an internationale und Inlandsnummern anrufe.    |
|    Identity='tag:DialoutCPCInternationalPSTNDomestic'    |    Benutzer in der Konferenz können internationale und Inlandsnummern anrufen, und dieser Benutzer kann nur ausgehende Anrufe an die PSTN-Nummer im Inland anrufe.    |
|    Identity='tag:DialoutCPCInternationalPSTNDisabled'    |    Benutzer in der Konferenz können internationale und inlandsnummern anrufen, und dieser Benutzer kann neben den Notrufnummern auch keine ausgehenden Anrufe an die PSTN-Nummer abwählen.    |
|    Identity='tag:DialoutCPCandPSTNDomestic'    |    Benutzer in der Konferenz können nur Nummern im Inland anrufen, und dieser Benutzer kann nur ausgehende Anrufe an PSTN-Nummern im Inland erstellen.    |
|    Identity='tag:DialoutCPCDomesticPSTNDisabled'    |    Benutzer in der Konferenz können nur Inlandsnummer anrufen, und dieser Benutzer kann neben den Notrufnummern auch keine ausgehenden Anrufe an die PSTN-Nummer abwählen.    |
|    Identity='tag:DialoutCPCDisabledPSTNDomestic'    |    Der Benutzer in der Konferenz kann keine ausgehenden Anrufe erstellen, und dieser Benutzer kann nur ausgehende Anrufe an PSTN-Nummern im Inland erstellen.    |
|    Identity='tag:DialoutCPCandPSTNDisabled'    |    Der Benutzer in der Konferenz kann keine ausgehenden Anrufe mehr an die PSTN-Nummer und zusätzlich zu den Notrufnummern abwählen.    |
|    Identity='tag:DialoutCPCZoneAPSTNInternational'    |    Der Benutzer der Konferenz kann nur Länder und Regionen der [Zone A](audio-conferencing-zones.md)anrufen, und dieser Benutzer kann ausgehende Anrufe an internationale und inlands nummerieren.    |
|    Identity='tag:DialoutCPCZoneAPSTNDomestic'    |    Nutzer der Konferenz können nur Länder und Regionen der [Zone A](audio-conferencing-zones.md)anrufen, und dieser Benutzer kann nur ausgehende Anrufe an die PSTN-Nummer im Inland erstellen.    |
|    Identity='tag:DialoutCPCZoneAPSTNDisabled'    |    Nutzer der Konferenz können nur Länder und Regionen der Zone [A](audio-conferencing-zones.md)anrufen, und dieser Benutzer kann neben den Notrufnummern auch keine ausgehenden Anrufe an die PSTN-Nummer mehr abwählen.    |
