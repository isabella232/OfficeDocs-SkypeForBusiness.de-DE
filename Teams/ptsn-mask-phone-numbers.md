---
title: Maskieren von Telefonnummern in Microsoft Teams Besprechungen
author: cichur
ms.author: v-cichur
manager: serdars
ms.reviewer: moakram
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection:
- M365-collaboration
- Teams_ITAdmin_Help
f1.keywords:
- NOCSH
appliesto:
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Erfahren Sie, wie Sie Telefonnummern in Besprechungen Microsoft Teams maskieren.
ms.openlocfilehash: f9e7fd76f0b9afa9776e554cbde87a0b302c7011
ms.sourcegitcommit: 15e90083c47eb5bcb03ca80c2e83feffe67646f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2021
ms.locfileid: "58733764"
---
# <a name="mask-phone-numbers-in-microsoft-teams-meetings"></a>Maskieren von Telefonnummern in Microsoft Teams Besprechungen

Für den zusätzlichen Datenschutz werden den internen Teilnehmern die Telefonnummern der Teilnehmer, die sich Teams audio conferencing (Audiokonferenz) einwählen, vollständig angezeigt. Die Nummern werden für Teilnehmer außerhalb Ihrer Organisation maskiert. Diese Einstellung ist die Standardeinstellung für alle Organisationen. Die maskierte Nummer wird wie in der folgenden Abbildung dargestellt angezeigt:

![Beispiel für eine maskierte Telefonnummer.](media/hiddenPhoneNum.png)

Bei bestimmten Branchen-Nutzungsfällen haben Administratoren die Möglichkeit zu wählen, wie die Telefonnummern der Audiokonferenzteilnehmer in Besprechungen angezeigt werden, die in ihrem Mandanten organisiert sind. Die Administratoren haben die Wahl zwischen drei Optionen:

- Telefon Nummern werden nur von externen Teilnehmern maskiert. Die Teilnehmer, die zum Mandanten des Besprechungsorganisators gehören, sehen weiterhin die vollständige Telefonnummer.
- Telefon Nummern sind für alle Besprechungsorganisatoren maskiert.
- Telefon Nummern werden maskiert, wodurch sie für jeden in der Besprechung sichtbar sind.

Diese Einstellung wird auf alle Oberflächen in der Besprechung angewendet, auf denen Telefonnummern verfügbar gemacht werden.

## <a name="use-microsoft-powershell-to-set-phone-number-masking"></a>Verwenden von Microsoft PowerShell zum Festlegen der Telefonnummernformatierung

Wenn Sie die Maskierungseinstellung für das Public Switched Telephone Network (PSTN) ändern möchten, legen Sie den Parameter des **`MaskPstnNumbersType`** [Cmdlets Set-CsOnlineDialInConferencingTenantSettings](/powershell/module/skype/set-csonlinedialinconferencingtenantsettings?view=skype-ps) auf eine der verfügbaren Optionen fest.

Führen Sie den folgenden Befehl aus, um Telefonnummern nur von externen Teilnehmern zu maskieren:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -MaskPstnNumbersType "MaskedForExternalUsers"
```

Führen Sie zum Maskieren von Telefonnummern aller Teilnehmer an der Besprechung (mit Ausnahme des Organisators) den folgenden Befehl aus:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -MaskPstnNumbersType "MaskedForAllUsers"
```

Führen Sie zum Deaktivieren der Telefonnummernmaskierung den folgenden Befehl aus:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -MaskPstnNumbersType "NoMasking"
```