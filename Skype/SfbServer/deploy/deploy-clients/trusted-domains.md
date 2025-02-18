---
title: Skype Vertrauenswürdige Domänen des Raumsystems
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 9fb63ad4-6eda-4724-be63-10bf5e65cb2b
description: In diesem Thema erfahren Sie, wie Sie vertrauenswürdige Domänen für Skype Room System und Skype for Business konfigurieren.
ms.openlocfilehash: fae745d1380e8d75d88e446275d7073e92ae5632
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58583269"
---
# <a name="skype-room-system-trusted-domains"></a>Skype Vertrauenswürdige Domänen des Raumsystems
 
In diesem Thema erfahren Sie, wie Sie vertrauenswürdige Domänen für Skype Room System und Skype for Business konfigurieren.
  
## <a name="trusted-domains"></a>Vertrauenswürdige Domänen

Der Skype for Business Client zeigt ein Dialogfeld an, in dem Benutzer das Zertifikat aus dem Skype for Business Server akzeptieren können, wenn sich die SIP-Domäne des Benutzerkontos, das sich anmeldet, von dem Namen unterscheidet, der im Antragsteller- oder Antragsteller-ALT-Namen auf dem Zertifikat angezeigt wird. Wenn das für Skype for Business Server in Ihrer Organisation konfigurierte Zertifikat nicht über einen SIP-Domänennamen Skype Raumsystemkontos im Antragsteller- oder Antragsteller-ALT-Namen verfügt, müssen Sie diese Domänen konfigurieren, die auf dem Zertifikat unter dem Registrierungsschlüssel "Vertrauenswürdige Domänen" auf dem Konsolencomputer Skype Raumsystem angezeigt werden. In ihrem Skype vom Hersteller bereitgestellten Skype Handbuch des Raumsystemadministrators wird erläutert, wie und wo vertrauenswürdige Domänen im Skype for Business-Client hinzugefügt werden. 
  
Nehmen wir beispielsweise an, dass die in Skype for Business Server konfigurierten Zertifikate den Altnamen "Subject/Subject Alt" "CONTOSO" aufweisen. LOCAL" und eine der SIP-Domänen, die einem Benutzer für die Skype Room System-Anmeldeadresse zugewiesen sind, lautet "confrm1@contoso.net". Da sich contoso.net nicht im Zertifikat befindet, müssen Sie auf dem Skype Raumsystemcomputer "contoso.local" als vertrauenswürdige Domäne in der Registrierung konfigurieren, wie im Skype vom Hersteller bereitgestellten Skype Handbuch des Raumsystemadministrators erläutert. 
  

