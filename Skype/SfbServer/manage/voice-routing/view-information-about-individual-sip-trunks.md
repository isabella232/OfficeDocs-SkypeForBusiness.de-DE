---
title: Skype for Business Server – Anzeigen von Informationen zu einzelnen SIP-Trunks
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
description: In Skype for Business Server können einem einzelnen PSTN-Gateway mehrere Trunks zugewiesen werden. Gateways und Trunks sind nicht identisch, und Administratoren müssen das Cmdlet Get-CsTrunk verwenden, um Informationen zu einem einzelnen SIP-Trunk anzuzeigen.
ms.openlocfilehash: 2c39a35ee0a42e2f54e87541cec857b3d90cd2c6
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58617801"
---
# <a name="skype-for-business-server---view-information-about-individual-sip-trunks"></a>Skype for Business Server – Anzeigen von Informationen zu einzelnen SIP-Trunks

In Skype for Business Server können einem einzelnen PSTN-Gateway mehrere Trunks zugewiesen werden. Dies bedeutet, dass Gateways und Trunks nicht identisch sind und Dass Administratoren das Cmdlet ["Get-CsTrunk"](/powershell/module/skype/Get-CsTrunk) verwenden müssen, um Informationen zu einem einzelnen SIP-Trunk anzuzeigen.

Das cmdlet Get-CsTrunk kann entweder über die Skype for Business Server-Verwaltungsshell oder über eine Remotesitzung von Windows PowerShell ausgeführt werden.

**So zeigen Sie Informationen für alle SIP-Trunks an**

Der folgende Befehl gibt Informationen zu allen in Ihrer Organisation verwendeten SIP-Trunks zurück:

`Get-CsTrunk`

**So zeigen Sie Informationen zu einem bestimmten SIP-Trunk an**

Dieser Befehl gibt nur für den SIP-Trunk mit dem Identitätswert "PstnGateway:192.168.0.240" Informationen zurück:

`Get-CsTrunk -Identity "PstnGateway:192.168.0.240"`

**Anzeigen von Informationen für alle einem Pool zugeordneten SIP-Trunks**

In diesem Beispiel werden für alle SIP-Trunks Informationen zurückgegeben, die dem Pool "atl-cs-001.litwareinc.com" zugeordnet sind:

`Get-CsTrunk -PoolFqdn "atl-cs-001.litwareinc.com"`
